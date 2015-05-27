Decision
=======
การตัดสินใจว่าจะทำอะไรนั้นขึ้นอยู่กับเงื่อนไข เช่น เดือนนี้เงินเหลือก็ไปกินบุฟเฟ่ต์ ถ้าไม่อย่างนั้นก็นั่งกินมาม่ากันต่อไป
if
---
```cpp
if(condition)
{
    statements;
}
```

Condition
---------
condition เป็น expression เงื่อนไขของเรา อาจเป็น boolean หรือไม่ใช่ boolean ก็ได้ ถ้าไม่ใช่ boolean โปรแกรมจะทำการแปลงให้เป็น boolean ถ้า condition เป็น true โปรแกรมจะทำคำสั่งในบล็อค ถ้าเป็น false จะข้ามบล็อคนั้นไป
```cpp
int a=1,b=9;
if(a==1){printf("a equal 1\n");}        // => a equal 1
if(a<5){printf("a less than 5\n");}     // => a less than 5
if(a>b){printf("a greater than b\n");}  // => 
if(b!=9){printf("b not equal 1\n");}    // => b not equal 1
if(1){printf("true");}			// non-zero number will evaluate to true
```

if...else...
------------
บางกรณีเราต้องการที่จะทำอีกอย่างนึงเมื่อเงื่อนไขไม่เป็นจริงด้วย สามารถทำได้โดยใช้ else
```cpp
if(a==1)
{
	//a==1
}
else if(a<1)
{
	//a<1
}
else
{
	//a>1
}
```
> if...else... สามารถนำมาต่อกันได้

switch()case:
-------------
ถ้าเราต้องเขียน if...else... ติดต่อกันเยอะๆเช่น
```cpp
if(a==1)
{
	printf("ONE");
}
else if(a==2)
{
	printf("TWO");
}
else if(a==3)
{
	printf("THREE");
}
...
```
เราอาจใช้ switch case แทนได้จะทำให้โค้ดอ่านง่ายขึ้นมาก
```cpp
swtch(a)
{
	case 1:printf("ONE");
    	break;
	case 2:printf("TWO");
    	break;
    case 3:printf("THREE");
    	break;
    ...
    
}
```
> **อย่าลืม** ใส่ `break;` ทุกครั้งที่จบ case
