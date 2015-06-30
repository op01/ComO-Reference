Min Op
====================
Tags : `Medium`<br>
Difficulty : &#9733;&#9733;&#9733;&#9733;&#9733;&#9734;&#9734;&#9734;&#9734;&#9734;<br>
Estimated time solve : 20 min<br>

- - -

จากเลข 1 คุณสามารถทำให้เป็นเลข **X** ได้หรือไม่ โดยที่คุณสามารถทำกับเลขได้ 3 อย่าง คือ +3 *2 และ ^2(ยกกำลัง 2) เช่น จากเลข 1 ไปเลข 10 คุณสามารถใช้ +3 +3 +3 ก็จะเป็นเลข 10 ได้ ใช้การคำนวณ 3 ครั้ง โดยคุณอยากรู้ว่าจะใช้การคำนวณน้อยที่สุดได้กี่ครั้ง และถ้าไม่สามารถทำได้ (เช่นจาก 1 ไป 3 ไม่สามารถทำได้) ให้แสดงเลข -1 แทน

Input
-----
บรรทัดแรกรับจำนวน testcase **T** (**T** <= 5)

แต่ละ testcase รับจำนวนเต็ม 1 ตัวคือ **X** (1 <= **X** <= 10000000)

Output
------
แต่ละ testcase แสดงจำนวนเต็ม 1 ตัว แสดงถึงจำนวนการคำนวณที่น้อยที่สุด แต่ถ้าไม่สามารถทำได้ ให้แสดง -1 แทน

Example Input
-------
```
3
10
3
19
```

Example Output
-------------
```
3
-1
3
```

Note
--------
คำอธิบายเคสที่ 3 (**X** = 19)

เราสามารถใช้ +3 +3 +3 +3 +3 +3 ได้ แต่ใช้การคำนวณถึง 6 ครั้ง

ทางที่สั้นที่สุดคือ +3 ^2 +3 (1+3=4 , 4^2=16 , 16+3=19) ซึ่งใช้การคำนวณแค่ 3 ครั้ง