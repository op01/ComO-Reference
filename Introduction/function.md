Function
========
คำว่าฟังชั่นทุกคนคนนึกถึง ความสัมพันธ์และฟังชั่น ในวิชาคณิตศาสตร์ ฟังชั่นในการเขียนโปรแกรมนั้นก็คล้ายกัน สมมติเราจะเขียนโปรแกรมหาค่าของ `f(5)` โดย `f(x)=2x+1`

```cpp
int f(int x)
{
	return 2*x+1;
}
int result=f(5);
printf("%d",result);
```

- int f() คือฟังชั่นชื่อ f และคืนค่าเป็น int
- int x คือ argument ของฟังชั่น ชนิด int
- return ... คือการคืนค่าค่านั้น และจบฟังชั่นทันที
- result=f(5) คือการให้ตัวแปร result เท่ากับค่าที่ฟังชั่นคืนมา ในที่นี้คือ 11

ถ้าเราจะหาค่า `f(6)` ก็เรียกได้เลย ทำให้ไม่ต้องมาเขียน `6*2+1` ซ้ำๆ และแน่นอน ฟังชั่นในโปรแกรมสามารถทำได้ซับซ้อนกว่านั้น เราสามารถเขียนคำสั่งอื่นเพิ่มเติมให้ฟังชั่นได้เหมือนในฟังชั่น main
 
function input/output
---------------------
ฟังชั่นสามารถรับ input ได้หลายๆตัวผ่านทาง argument แต่คืนทางได้ตัวเดียวทาง return ถ้าต้องการผลลัพธ์หลายๆตัวอาจใช้ global variable,struct,pointer ช่วยได้ 

void function
-------------

Function and Array
------------------