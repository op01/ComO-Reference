Calculator !
====================
Tags : `Input/Output` `Variable` `Operator` `loop` `Recursive` `Dynamic programming` `GCJ`<br>
Difficulty #1 : &#9733;&#9733;&#9734;&#9734;&#9734;&#9734;&#9734;&#9734;&#9734;&#9734;<br>
Difficulty #2 : &#9733;&#9733;&#9733;&#9734;&#9734;&#9734;&#9734;&#9734;&#9734;&#9734;<br>
Difficulty #3 : &#9733;&#9733;&#9733;&#9733;&#9734;&#9734;&#9734;&#9734;&#9734;&#9734;<br>
Difficulty #4 : &#9733;&#9733;&#9733;&#9733;&#9733;&#9734;&#9734;&#9734;&#9734;&#9734;<br>
Difficulty #5 : &#9733;&#9733;&#9733;&#9733;&#9733;&#9733;&#9734;&#9734;&#9734;&#9734;<br>
Difficulty #6 : &#9733;&#9733;&#9733;&#9733;&#9733;&#9733;&#9734;&#9734;&#9734;&#9734;<br>
Estimated time solve : 1 hr<br>

- - -

คุณกำลังจะได้ทำเครื่องคิดเลขที่มหัศจรรย์ที่สุดในโลก ซึ่งมีฟังก์ชันมากมาย โดยเครื่องคิดเลขจะรับค่าได้ 2 แบบ คือ
`op [num 1] [num 2]` หรือสำหรับบางตัวจะใช้ `op [num 1]` ซึ่ง op นั้นมีได้มากมาย แบ่งเป็นหลายระดับ ได้แก่
- `+ [num1] [num2]` คือนำ num1 + num2
- `- [num1] [num2]` คือนำ num1 - num2
- `* [num1] [num2]` คือนำ num1 คูณ num2
- `/ [num1] [num2]` คือนำ num1 หาร num2 (ปัดเศษทิ้ง และรับประกันว่า num2 != 0)
- `^ [num1] [num2]` คือหา num1 ยกกำลัง num2 (รับประกันว่า num2 >= 0)
- `! [num1]` คือนำ num1 มาหา factorial (1 &#42; 2 &#42; ... &#42; num1) เช่น ` ! 3 = 1*2*3 = 6 `
- `f [num1]` คือให้หาลำดับ fibonacci ตัวที่ num1 ( `fib(n) = fib(n-1)+fib(n-2) , fib(1) = fib(2) = 1` )
- `C [num1] [num2]` ให้หา combination ของ (num1,num2) โดย combination คือ `num1!/num2!(num1-num2)!`
- `P [num1] [num2]` หา permutation = `num1!/(num1-num2)!`

Input
-----
บรรทัดแรกรับจำนวน testcase **T** (**T** <= 100)

แต่ละ testcase จะเป็นการคำนวณตามข้างบน คือ op ตามด้วยจำนวนเต็ม 1-2 ตัวตาม op ตัวนั้น

Output
------
แต่ละ testcase แสดงคำตอบของการคำนวณนั้นๆ

Limits
------
Subtask #1 (5 pts) : **T** = 1 และ op จะมีแค่ `+` จำนวนเต็มทุกตัวมีค่าตั้งแต่ 0-1000<br>
Subtask #2 (10 pts) : op จะมีแค่ `+ - * /` จำนวนเต็มทุกตัวมีค่าตั้งแต่ 0-1000<br>
Subtask #3 (10 pts) : op จะมี `+ - * / ^ !` และรับประกันว่าจำนวนเต็มทุกตัวรวมถึงคำตอบมีค่าตั้งแต่ -10^9 ถึง 10^9<br>
Subtask #4 (15 pts) : op จะมี `+ - * / ^ ! f C P` และจำนวนเต็มทุกตัวมีค่าตั้งแต่ 1 ถึง 10<br>
Subtask #5 (20 pts) : op จะมี `+ - * / ^ ! f` และรับประกันว่าจำนวนเต็มทุกตัวรวมถึงคำตอบมีค่าตั้งแต่ -10^18 ถึง 10^18<br>
Subtask #6 (40 pts) : ไม่มีเงื่อนไขเพิ่มเติมจากโจทย์ รับประกันว่าจำนวนเต็มทุกตัวรวมถึงคำตอบมีค่าตั้งแต่ -10^18 ถึง 10^18<br>

Example Input
-------
```
9
+ 5 8
- 4 7
* 9 9
/ 9 4
^ 6 3
! 10
f 10
C 8 4
P 7 3
```

Example Output
-------------
```
13
-3
81
2
216
3628800
55
70
210
```

Note
----
Subtask #1 ทดสอบการรับค่าเบื้องต้น
Subtask #2 ทดสอบการรับค่าแบบเป็น testcase
Subtask #3 ทดสอบการใช้ loop
Subtask #4 ทดสอบการใช้ recursive
Subtask #5 ทดสอบการใช้ Dynamic Programming 1 มิติ
Subtask #6 ทดสอบการใช้ Dynamic Programming 2 มิติ

ปล. อยากให้โจทย์นี้เป็นโจทย์วัดถึงทักษะทุกอย่าง ซึ่ง subtask 1-2 ทุกคนน่าจะได้ ส่วน subtask 3-4 จะเป็น สอวน. ค่าย 1 ซึ่งไม่ยากมาก และ subtask 5-6 จะเป็น สอวน. ค่าย 2 ซึ่งต้องใช้ทักษะเพิ่มอีกนิด