Grader Client Protocol
====================
Protocol ที่จะใช้ google drive (หรือ file storage อื่นๆ ที่รองรับระบบ permission แต่ละ user คือบาง user เข้าถึงบางไฟล์ได้แบบมี write permission และเข้าถึงไฟล์ที่เหลือได้แบบ read only) และใช้ client side ในการตรวจล้วนๆ โดยมีความปลอดภัยเท่ากับการใช้ server ตรวจเลย (มั้งนะ)

ยังไม่เสร็จสมบูรณ์ แต่เชื่อว่าน่าจะใช้ได้

File structure
---------

- ProblemKey เป็นไฟล์ที่เก็บ decryption key ของ problem ทุกๆ problem ไว้ (1 key ต่อ 1 problem) (read only)
- ProblemTestcase เป็นไฟล์ที่เก็บ testcase และ key ของ problem ไว้ (1 problem 1 ไฟล์) (read only)
- ProblemFlag เก็บ flag ของ problem ไว้ (1 problem 1 ไฟล์) (read only)
- Scoreboard เก็บคะแนนของแต่ละ user ไว้ (1 user 1 ไฟล์) (สำหรับ user นั้นได้ read-write access , คนอื่นทุกคนได้ read only)

ProblemKey
----------
เก็บ decryption key ของ problem ไว้ เพื่อเช็คว่า user นั้นได้ flag ที่ถูกต้องมาจาก ProblemFlag จริงๆ
```
prob1 => SCOREBOARD_PROB1_DECRYPT_KEY_aaaabbbbccccdddd
prob2 => SCOREBOARD_PROB2_DECRYPT_KEY_eeeeffffgggghhhh
prob3 => SCOREBOARD_PROB3_DECRYPT_KEY_iiiijjjjkkkk1234
```

ProblemTestcase
---------------
เป็น testcase ของ problem
```
3
1 5
3 87
9 10
```

สมมติได้คำตอบเป็น
```
6
90
19
```

เมื่อนำคำตอบที่ถูกมา decrypt กับ `ENCRYPTED_PRIVATE_KEY` จาก flag (ยังไม่รู้อัลกอ แต่หาดูไม่น่ายาก) จะได้ `PRIVATE_KEY` ซึ่งจะนำไป decrypt ProblemFlag ได้

ProblemFlag
-----------
เป็น flag ของ problem แต่ละข้อ โดยเมื่อนำคำตอบที่ถูกมา decrypt กับ `ENCRYPTED_PRIVATE_KEY` จะได้ `PRIVATE_KEY` ที่ถูกต้องมา เพื่อ decrypt ENCRYPT_DATA อีก จะได้เป็นข้อความ `PROBLEM_ACCEPT` และจะได้ `SCOREBOARD_PROB_ENCRYPT_KEY` มาเพื่อใส่ scoreboard

```
ENCRYPTED_PRIVATE_KEY_112233445566778899
ENCRYPT_DATA_asdf123456789012345678901234567890asdfasdfasdfasdfasdfasdf
```
เมื่อนำคำตอบ `6 90 19` มา decrypt กับ `ENCRYPTED_PRIVATE_KEY_112233445566778899` จะได้ private key ที่ถูกต้องมา เช่น `PRIVATE_KEY_abcdefghijklmnop`

เมื่อนำ `PRIVATE_KEY` ที่นั้นมา decrypt `ENCRYPT_DATA` จะได้ flag เช่น เอา `PRIVATE_KEY_abcdefghijklmnop` (จากข้างบน) มา decrypt `ENCRYPT_DATA_asdf123456789012345678901234567890asdfasdfasdfasdfasdfasdf` จะได้ `PROBLEM1_ACCEPT SCOREBOARD_PROB1_ENCRYPT_KEY_ppppppppqqqqqqqqrrrrrrrrssssssss` ซึ่งเมื่อ client เห็นคำว่า `PROBLEM1_ACCEPT` จะรู้ได้ว่านี่เป็น flag ที่ถูกต้องจริงๆ

Scoreboard
-------
ให้แต่ละ user สามารถเก็บว่าเราแก้ข้อนี้ไปหรือยัง และเพื่อไม่ให้ user โกง หรือให้คนอื่นๆที่เห็น scoreboard ก๊อบไปได้ เราจะเข้ารหัสแต่ละ user โดยสร้างข้อความ `SCOREBOARD_user1_PROB1_SOLVED` ขึ้นมา และนำมา encrypt ด้วย `SCOREBOARD_PROB1_ENCRYPT_KEY_ppppppppqqqqqqqqrrrrrrrrssssssss` จะได้เป็น `ENCRYPTED_wtfwtfwtfwtf` ซึ่งข้อความนี้ เมื่อนำมา decrypt ด้วย decryption key ของ problem นั้นจะได้ข้อความเดิมกลับมา (`SCOREBOARD_user1_SOLVE_PROB1`) เมื่อทำแบบนี้ คนอื่นจะเอา `ENCRYPTED_wtfwtfwtfwtf` ไปใส่ใน scoreboard ตัวเองไม่ได้ และจะ user จะเอา `SCOREBOARD_user1_SOLVE_PROB1` ไปใส่เฉยๆเลยก็ไม่ได้ ต้องรู้ flag ก่อน

Problem | Solved ?
--------|---------
prob1|`ENCRYPTED_wtfwtfwtfwtf`
prob2|
prob3|`ENCRYPTED_qwertyqwertyqwerty`
prob4|

Problem Judging
------
สมมติเราเป็น user2 จะแก้ปัญหา prob3

เริ่มจากโหลดไฟล์ testcase มาก่อน
```
3
9 15
6 4
7 20
```
> ไฟล์ testcase_prob3.txt

เมื่อ user โหลดไฟล์มาแล้วได้ output แล้ว ก็ส่งเข้า client ให้ทำการตรวจสอบ สมมติคำตอบเป็น
```
15
6
20
```
ก็นำคำตอบพวกนี้มารวมกันเป็นก้อนเดียวกัน (ด้วยอัลกออะไรสักอย่าง) เช่น `15 6 20` (ตัด spacebar ที่เกินกับบรรทัดใหม่ออก)

จากนั้นโหลด ProblemFlag มา เพื่อเช็คว่าคำตอบถูกหรือไม่

```
aaaaaaaaaaaaaaaabbbbbbbbbbbbbbccccccccccddddddddddd
eeeeeeeeeeeeffffffffffgggggggggghhhhhhhhhiiiiiiiiiiijjjjjjj1234567890
```
> ไฟล์ flag_prob3.txt

เริ่มจากนำ `aaaaaaaaaaaaaaaabbbbbbbbbbbbbbccccccccccddddddddddd` มารวมกับ `15 6 20` ด้วยอัลกออะไรสักอย่าง ได้เป็น `AAAAAAAAAAAAAAAAAADDDDDDDDDBBBBBBCCCCCCCC` ซึ่งเป็น private key (ยังไม่รู้ว่าถูกรึเปล่า) จากนั้นให้นำ private key นั้นมา decrypt `eeeeeeeeeeeeffffffffffgggggggggghhhhhhhhhiiiiiiiiiiijjjjjjj1234567890` จะได้เป็น `PROBLEM3_ACCEPT aaaaaaaa111111111bbbbbbbbb2222222222cccccccc3333333333` ซึ่ง client เห็นคำว่า `PROBLEM3_ACCEPT` ก็รู้ได้ทันทีว่าถูก ถ้าไม่เห็นแสดงว่าผิด เมื่อถูก ก็ให้นำ `aaaaaaaa111111111bbbbbbbbb2222222222cccccccc3333333333` เก็บไว้เป็น scoreboard encrypt key เพื่อไปอัพ scoreboard ต่อไป

Problem Judging - Security
--------------------------

- user รู้ผลการตรวจได้ทันที ไม่ต้องรอใครมาตรวจให้
- user สามารถตรวจคำตอบได้ว่าถูกหรือไม่ โดยที่ไม่รู้ว่า ans จริงๆคืออะไร

ปัญหาความปลอดภัย

1. การส่ง private key ที่ถูกต้องให้คนอื่น / การส่ง scoreboard encrypt key ให้คนอื่น เทียบเท่ากับการส่ง output ที่ถูกให้คนอื่นใน grader ทั่วไป
2. การ brute-force private key จนกว่าจะได้ ACCEPT เทียบเท่ากับการ brute-force output

Scoreboard Updating
-------------------

จากข้างบน สมมติเราเป็น user2 จะแก้ปัญหา prob3 ตอนนี้เราได้ `aaaaaaaa111111111bbbbbbbbb2222222222cccccccc3333333333` ซึ่งเป็น scoreboard encrypt key มาแล้ว

เริ่มจากโหลด scoreboard_user2 มาแก้ไข
```
prob1 =>
prob2 =>
prob3 =>
prob4 =>
```
> scoreboard_user2.txt

จากนั้น สร้างข้อความ `SCOREBOARD_user2_prob3_SOLVED` ขึ้นมา มาเข้ารหัสด้วย `aaaaaaaa111111111bbbbbbbbb2222222222cccccccc3333333333` จะได้เป็น data ที่จะใส่ใน scoreboard ` zzzzzzzzzzzzzzxxxxxxxxxxxxxxyyyyyyyyyyyyywwwwwwwwwww`

```
prob1 =>
prob2 =>
prob3 => zzzzzzzzzzzzzzxxxxxxxxxxxxxxyyyyyyyyyyyyywwwwwwwwwww
prob4 =>
```
> scoreboard_user2.txt

จากนั้นก็อัพไฟล์นี่ขึ้นไป

Scoreboard Checking
-------------------
เมื่อเราจะดู scoreboard เราจะโหลด scoreboard ของทุก user มาให้หมด
```
prob1 =>
prob2 => wwwwwwwwttttttttttfffffffffffff
prob3 => 444444444455555555555666666666
prob4 => 99999999888888888877777777777
```
> scoreboard_user1.txt

```
prob1 =>
prob2 =>
prob3 => zzzzzzzzzzzzzzxxxxxxxxxxxxxxyyyyyyyyyyyyywwwwwwwwwww
prob4 =>
```
> scoreboard_user2.txt

```
prob1 => ooooooookkkkkkkkkkkooooooookkkkkkkkkkk
prob2 => this_key_is_wrong
prob3 => i'm_cheating
prob4 =>
```
> scoreboard_user3.txt

จากนั้น เราโหลด problemKey มาด้วย

```
prob1 => iiiiiiiiiiiiiiiiiiiiiiii
prob2 => lllllllllloooooooooooooo
prob3 => vvvvvvvvvveeeeeeeeeeeeee
prob4 => rrrrrrrrssssssssssaaaaaa
```
> problemKey.txt

จากนั้น เราก็เอา problemKey ของแต่ละข้อ ไป decrypt scoreboard ของทุกคนตามข้อ ซึ่งก็จะได้เป็น

```
prob1 =>
prob2 => SCOREBOARD_user1_prob2_SOLVED
prob3 => SCOREBOARD_user1_prob3_SOLVED
prob4 => SCOREBOARD_user1_prob4_SOLVED
```
> scoreboard_user1.txt

```
prob1 =>
prob2 =>
prob3 => SCOREBOARD_user2_prob3_SOLVED
prob4 =>
```
> scoreboard_user2.txt

```
prob1 => SCOREBOARD_user3_prob1_SOLVED
prob2 => awjrgvasnorfnjaslernhojkerngjawr
prob3 => lkmmoihjmofymhofyjofqwedqa146546
prob4 =>
```
> scoreboard_user3.txt

เมื่อเราทำแบบนี้เราจะรู้ได้เลยว่าใครที่ผ่านจริงๆ และใครที่ไม่ผ่าน เราก็มาสร้าง scoreboard บน client เราได้เลย


User | Score
-----|------
user1|3
user2|1
user3|1


Scoreboard - Security
--------------------------

- user จะต้องได้ scoreboard encrypt key มาจริงๆ เพื่อมาเข้ารหัสคำว่า SOLVED นั้น
- user แต่ละ user จะมีข้อความบน scoreboard ไม่เหมือนกัน เพื่อไม่ให้ user อื่นๆดูข้อความแล้วก๊อบมาเป็นของตัวเองเลย

ปัญหาความปลอดภัย

1. การเอา SCOREBOARD_userX_probY_SOLVED มาทำให้คนอื่น เทียบเท่ากับการส่งคำตอบให้ account คนอื่น

ปัญหา
----
1. จะทำยังไง ให้เมื่อนำคำตอบ มารวมกับ `ENCRYPTED_PRIVATE_KEY` และจะได้เป็น `PRIVATE_KEY` ออกมา (UPD ข้างล่าง)
2. ปลอดภัยจริงหรือไม่ (แต่จากระบบแล้ว ถ้าจะแฮกได้ ก็ต้อง brute-force RSA ซึ่งไม่ง่าย แต่ยังไม่รู้มีช่องโหว่อื่นอีกรึเปล่า)
3. จริงๆตรง PROBLEM_ACCEPT ไม่จำเป็นก็ได้ เอาแค่ scoreboard encrypt key มาพอ และไปเช็คที่ scoreboard เลยว่า `decrypt(encrypt("SCOREBOARD_user1_prob1_SOLVED",scoreboard encrypt key), problem decrypt key) == "SCOREBOARD_user1_prob1_SOLVED"` รึเปล่า

คำตอบ + ENCRYPTED_PRIVATE_KEY -> PRIVATE_KEY
--------------------------------------------

ถ้าคำตอบมันสั้น อาจทำให้ไม่ปลอดภัยเท่าไหร่

คิดว่า เอาคำตอบ มาทำ checksum หลายๆแบบ และเอาคำตอบนี่ต่อท้ายไปด้วย กลายเป็น key ที่ยาวมากๆและ brute-force ไม่ได้ และเอาไปเข้ารหัส PRIVATE_KEY แบบ symmetric คือ key เดียวใช้ ไป-กลับ น่าจะโอเค แบบ ตอบ `Hello World` ก็ทำ checksum ซะหน่อย (อะไรก็ได้ให้ยาวๆ หลายๆอันต่อกันก็ได้) เป็น `0a4d55a8d778e5022fab701977c5d840bbc486d0Hello World` ก็เอาเป็น key ซะ ทำแบบนี้จะ brute-force key ได้ยาก

ช่องโหว่ก็จะเหลือแค่การ brute-force คำตอบ ซึ่งยังไงซะต่อให้ใช้ server ก็กันไม่ได้ 555
