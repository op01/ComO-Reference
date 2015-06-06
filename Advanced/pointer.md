Pointer
=======
pointer เป็นตัวแปรอีกประเภทนึงที่เก็บค่าที่อยู่ของตัวแปรอื่น ก่อนอื่นเราต้องรู้จักที่อยู่ตัวแปรกันก่อน
Address
-------
ตัวแปรแต่ละตัวที่เราประกาศไว้จะอยู่ใน RAM ซึ่งก็ต้องมีที่อยู่ใน RAM เป็นของตัวเอง เวลาทำอะไรจะได้ทำถูกตัว
```cpp
int a=5;
printf("%p",&a);
```
จากโค้ดนี้ผลลัพธ์จะออกมาคล้ายๆ `000000000023fe48` ในระบบ 64bit หรือ `0023fe48` ในระบบ 32bit ซึ่งก็คือที่อยู่ใน RAM ของตัวแปร a นั้นเอง

- %p คือ format ของที่อยู่ (Memory address)
- &a คือ ที่อยู่ของตัวแปร a 
- & คือ Address-of operator

Declaring pointer
-------------
```cpp
int num;
int* ptr=&num;
printf("%p",ptr);
```
ประเภทของ pointer กับตัวแปรที่มันชี้ต้องตรงกัน ถึงแม้กว่า pointer จะมีขนาดเท่ากัน (เป็นเลขบอก memory address เหมือนกัน) แต่ก็ต้องรู้ว่าข้อมูลที่ pointer ตัวนี้ชี้มีขนาดกี่ byte
Dereference
-----------
เมื่อเราได้ pointer มาแล้ว ถ้าเราต้องการใช้ตัวที่ pointer ชี้อยู่ ไม่ใช้ตัว pointer เอง
```cpp
int num=1;
int* ptr=&num;
printf("num=%d\n",num); // => 1
*ptr = 5;
printf("num=%d\n",num);// => 5
// reference & dereference can be chained
printf("%d",*&*&*&num); // => 5 (เพื่ออะไร?)

struct Person
{
	char name[10];
    int age;
};
Person john;
john.age = 18;
Person* johnptr=&john // pointer of struct!
(*johnptr).age = 19; // dereferenced and access member
johnptr->age = 20; //struct pointer member can also be accessed this way
```
Pointer to pointer
------------------
แน่นอนว่า potiner ก็เป็นตัวแปรเหมือนกัน เพราะฉะนั้นก็อาจถูกชี้โดย pointer ตัวอื่นได้เช่นกัน การประกาศ pointer ชี้กันเองแบบนี้ทำโดย `*` ไปเรื่อยๆ
```cpp
int num;
int* pnum=&num;
int** ppnum=&pnum;
int*** pppnum=&ppnum'
```
Memory Allocation
-----------------
เรารู้มาแล้วว่าเวลาเราประกาศตัวแปรคอมพิวเตอร์จะไปจองพื้นที่สำหรับตัวแปรนั้นให้ และเมื่อหมด scope ของตัวแปรนั้นก็จะทำลายและคืนพื้นที่ให้ แต่ถ้าเราต้องการพื้นที่โดยไม่ขึ้นกับตัวแปร เราต้องใช้ `malloc(size)` ซึ่งอยู่ใน `stdlib.h`
```cpp
int* ptr=(int*)malloc(sizeof(int));
free(ptr);
```
- `sizeof(int)` คือขนาดของข้อมูลชนิด int
- `malloc(size)` คือจองพื้นที่ขนาด size byte(s) ซึ่งจะคืนค่าเป็นที่อยู่ที่จองให้
- `(int*)` คือการแปลง pointer ที่คืนเป็นรูปแบบ int\* (int pointer)
- `free(ptr)` คืนพื้นที่หลังใช้งานเสร็จ

Pointer and Array
-----------------
อาเรย์ที่เราเรียนมาแล้วนั้นที่จริงมันคือตัวแปร pointer นั้นเอง
```cpp
int *arr=(int*)malloc(sizeof(int)*n);
arr[0]=1000007;
```
Pass by value vs Pass by pointer
--------------------------------
สมมติเราต้องการเขียนฟังชั่น swap โดยทำหน้าที่สลับข้อมูล 2 ตัว
```cpp
void swap(int a,int b)
{
	int temp=a;
    a=b;
    b=tmp;
}
int x=10,y=20;
swap(x,y);
```
ถ้าเราเขียนแบบนี้เวลาใช้งาน  จะไม่เกิดอะไรขึ้น เพราะว่าที่ส่งเข้าไปในฟังชั่นคือ "ค่า"  ซึ่งเมื่อสลับค่าในฟังชั่นนั้นแล้วค่านั้นก็หายไป เราจึงต้องใช้ pointer มาช่วย
```cpp
void swap(int* a,int* b)
{
	int tmp=*a;
    *a=*b;
    *b=tmp;
}
int x=10,y=20;
swap(&x,&y);
```
นั้นก็คือส่งที่อยู่ของตัวแปรที่เราต้องการสลับไป ในฟังชั่นเราใช้ `*` dereference จึงได้ตัวแปร x,y จริงๆ แล้วเราก็ทำการสลับปกติ
