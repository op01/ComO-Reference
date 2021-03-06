Introduction to Programming &#9733;&#9733;&#9734;&#9734;&#9734;
=====================
พื้นฐานของการเขียนโปรแกรมนั้นมีไม่มาก แต่เป็นสิ่งที่จำเป็นสำหรับทุกคนที่จะต้องรู้ไว้

Index Table
-----------
1. [Syntax - ไวยากรณ์พื้นฐาน](syntax.md)
2. [Variable Expression - ตัวแปร และการดำเนินการเกี่ยวกับตัวแปร](variable-expression.md)
3. [Input Output - การรับข้อมูลนำเข้า และแสดงข้อมูลส่งออก](input-output.md)
4. [Decision - การตัดสินใจ และการควบคุมการไหลของโปรแกรม (Program flow)](decision.md)
5. [Loop - การวนซ้ำ/ทำซ้ำ](loop.md)
6. [Array - ตัวแปรชุด](array.md)
7. [Function - ฟังก์ชัน](function.md)
8. [Conclude - สรุปและยกตัวอย่างการนำไปใช้](conclude.md)

Computer Program
---------------------------
โปรแกรมคอมพิวเตอร์คือลำดับของคำสั่งที่เขียนด้วยภาษาคอมพิวเตอร์ เพื่อให้คอมพิวเตอร์ทำงานบางอย่าง สมมติจะสั่งให้คอมพิวเตอร์ไปถ่ายเอกสาร (เพราะคนสั่งขี้เกียจลงไป) ก็ต้องสั่งคอมพิวเตอร์เป็นลำดับ เช่น

1. เดินไปที่ร้านถ่ายเอกสาร
2. ต่อคิว
3. เมื่อถึงคิว ยื่นเอกสารให้และบอกว่า "ถ่ายเอกสารชุดนึง"
4. เมื่อเสร็จแล้วก็ยื่นเงินให้ และเดินกลับมาเอาเอกสารให้คนสั่ง (ที่นั่งขี้เกียจอยู่)

Programming Language
----------------------------------
แต่เนื่องจากคอมพิวเตอร์นั้นไม่สามารถเข้าใจภาษามนุษย์ได้ (หรือเข้าใจได้แค่บางส่วน) เราจึงต้องมีภาษากลางเพื่อสั่งคอมพิวเตอร์ ซึ่งภาษาสากลนั้นคือภาษา Assembly

```asm
global  _start

        section .text
_start:
        mov     rax, 1                  
        mov     rdi, 1                  
        mov     rsi, message            
        mov     rdx, 13                 
        syscall                         

        mov     eax, 60                 
        xor     rdi, rdi                
        syscall                         
message:
        db      "Hello, World", 10
```
>**Code 1** : ตัวอย่างโปรแกรมภาษา Assembly โดยโปรแกรมจะแสดงผล "Hello world" ออกทางหน้าจอ

เพียงแต่ภาษา Assembly นั้นไม่สะดวก เขียนยาก และแต่ละ CPU / OS จะใช้คำสั่ง Assembly ที่แตกต่างกันไป ดังนั้นจึงไม่นิยมเขียน Assembly กันมากนัก

What is Compiler ?
------------------
ด้วยเหตุนี้ภาษาที่ใช้การ compile จึงเกิดขึ้นมา โดยการ compile นั้น จะนำภาษาคอมพิวเตอร์ภาษาหนึ่ง มาแปลงเป็นอีกภาษาหนึ่งผ่านโปรแกรมที่ชื่อ compiler ตัวอย่างเช่นภาษา C\++ เราก็เขียนโปรแกรมขึ้นมาด้วยภาษา C\++ แล้วพอเขียนเสร็จ เราก็เรียก compiler มาใช้ โดย compiler จะแปลงโปรแกรมนั้นเป็นภาษา Assembly ที่ถูกต้องกับ CPU/OS ที่เราใช้ได้โดยที่เราไม่ต้องมานั่งแยกเขียนเองเลย
```cpp
#include <cstdio>
int main() {
	printf("Hello World\n");
}
```
>**Code 2** : ตัวอย่างโปรแกรมภาษา C++ ซึ่งทำงานเหมือนกับ **Code1**

และเมื่อใช้ compiler ก็จะได้เป็น Assembly ที่สามารถรันได้เลย
```asm
	.file	"hello.cpp"
	.def	___main;	.scl	2;	.type	32;	.endef
	.section .rdata,"dr"
LC0:
	.ascii "Hello World\0"
	.text
	.globl	_main
	.def	_main;	.scl	2;	.type	32;	.endef
_main:
	pushl	%ebp
	movl	%esp, %ebp
	andl	$-16, %esp
	subl	$16, %esp
	call	___main
	movl	$LC0, (%esp)
	call	_puts
	movl	$0, %eax
	leave
	ret
	.def	_puts;	.scl	2;	.type	32;	.endef
```
>**Code 3** : Assembly ของ **Code 2** ที่ได้จาก compiler (g++ 4.7.1 สั่งด้วย option -S)

Why C++ ?
---------
ภาษา C\++ เป็นภาษาที่ต่อยอดมาจากภาษา C อีกที แต่เพิ่มความสามารถในหลายๆด้าน และลดข้อจำกัดบางส่วนออกไป จึงเขียนได้ง่ายกว่า C 

เหตุผลที่ใช้ภาษา C\++ เนื่องจากเป็นภาษาที่เขียนได้ครอบคลุมทุกอย่าง มี library ให้ครบถ้วน และประสิทธิภาพสูง จึงเป็นที่นิยมเป็นอย่างมาก โดยเฉพาะการแข่งขันแบบ Competitive Programming


| Language | Qualification | 1A | 1B | 1C | 2 | 3 | World Finals (26 คน) |
|----------|---------------|----|----|----|---|---|----------------------|
|C++|11504|2134|3677|2296|1867|319|21|
|Java|5616|584|1436|735|318|46|4|
|Python|4352|580|1191|755|255|19|0|
|C|1871|65|405|172|27|0|0|


>**Table 1** : สถิติของภาษา 4 อันดับแรกที่ใช้ในการแข่งขัน Google Code Jam 2014 จะเห็นได้ว่า C\++ มีผู้ใช้เยอะที่สุด ในขณะที่ C มีผู้ใช้น้อยกว่า C\++ มาก

What is IDE ?
-------------
สำหรับการเขียนโปรแกรมคอมพิวเตอร์นั้่น เราสามารถใช้โปรแกรม text editor ทั่วๆไปเขียนได้ (เช่น notepad , wordpad) แต่โปรแกรมพวกนี้จะไม่มี syntax highlighting ให้ และการใช้ compiler จะต้องเรียกใช้เอง ซึ่งไม่สะดวก จึงมี IDE ขึ้นมา ซึ่งเป็นโปรแกรมที่ไว้ใช้เขียนโปรแกรมโดยเฉพาะ
IDE ที่จะใช้กันคือ Code::Blocks 13.12 ซึ่งใช้ง่าย มี syntax highlighting ให้ และกดปุ่ม F9 ปุ่มเดียวเพื่อ compile และ run ได้เลย


Final Note
----------
การเขียนโปรแกรมคอมพิวเตอร์นั้น ผู้ที่มีความสามารถทางภาษาอังกฤษและคณิตศาสตร์ จะได้เปรียบ เนื่องจาก tutorial ที่ดีๆส่วนใหญ่จะเป็นภาษาอังกฤษ เราจึงพยายามรวบรวม tutorial และความรู้ต่างๆมาทำเป็นภาษาไทยใน reference นี้เพื่อให้ทุกคนได้อ่าน และความรู้ทางด้านคณิตศาสตร์นั้นจำเป็นเป็นอย่างมาก และคอมพิวเตอร์นั้นเป็นส่วนหนึ่งของคณิตศาสตร์ ทั้ง algorithm , data structure ต่างๆล้วนใช้ทฤษฎีทางคณิตศาสตร์สนับสนุน เราจึงพยายามทำ reference นี้ให้อ่านง่าย พยายามแปลศัพท์ที่เข้าใจยากๆให้เข้าใจง่าย และรวบรวมแหล่งเรียนรู้ต่างๆไว้ด้วยกัน ดังนั้น reference นี้จึงเหมาะกับผู้ที่สนใจการเขียนโปรแกรม ทั้งเบื้องต้น และระดับสูง
