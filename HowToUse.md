How to use this reference ?
====================
ComO reference นี้จะรวบรวมความรู้ด้านโปรแกรมมิ่ง เอามาแบ่งเนื้อหาและเรียงลำดับตามที่เห็นสมควร และยังรวบรวมโจทย์ ทั้งที่มีแล้ว และโจทย์ที่แต่งขึ้นใหม่ เพื่อให้ทุกคนได้ฝึกฝน

New User
--------
สำหรับสมาชิกใหม่ของชุมนุม หรือผู้ที่ยังไม่เคยมีประสบการณ์การเขียนโปรแกรม หรือมีน้อย ให้เริ่มอ่านจากหมวด Introduction ที่จะรวมเนื้อหาระดับพื้นฐานที่สุดไว้ เช่น การรับค่า แสดงค่า การใช้ตัวแปร การใช้เครื่องหมายต่างๆ การตัดสินใจจากเงื่อนไข เป็นต้น

```cpp
#include <bits/stdc++.h>
using namespace std;
int main() {
    int a;
    scanf("%d",&a);
    if(a < 0) {
    	printf("Negative number\n");
        a *= -1;
    }
    else {
    	printf("Positive number\n");
    }
    a *= 2;
    printf("Loop %d times\n",a);
    int arr[a];
    for(int i = 0;i < a;i++)
    {
		scanf("%d",&arr[i]);
        if(arr[i] < 0) {
        	printf("Negative again !! I hate negative\n");
            break;
        }
        if(i>0 && arr[i] > arr[i-1]) {
        	printf("Number is increasing\n");
        }
    }
    printf("Yeah ! Introdution finished !");
}
```
>**Code 1** ตัวอย่างความรู้ทั้งหมดที่จะได้เรียนในหมวด Introduction ถ้าเข้าใจโค้ดข้างบนได้ทั้งหมดว่าอันไหนคืออะไร ก็ถือว่าโอเค

Old user
-------
สำหรับผู้ใช้เก่า ซึ่งอาจมีประสบการณ์มาบ้างแล้ว ทั้งค่าย สอวน สสวท ค่ายต่างๆ 

ในหมวด Advanced จะมีคำสั่งภาษา C++ แบบขั้นสูงอยู่ เช่น `struct` `FILE` `STL` เป็นต้น

ในหมวด Data structure จะรวบรวม data structure ที่น่าสนใจมาไว้ในนี้ ซึ่งมาทั้งยาก ง่ายปนกันไป เช่น `stack` `queue` `graph` `deque` เป็นต้น

ในหมวด Algorithm จะรวบรวม algorithm ต่างๆที่น่าสนใจ ทั้งง่ายและยากปนกันไป เช่น `Dijkstra` `Max flow` เป็นต้น

Creative
------
ในหมวด creative จะรวบรวมการเขียนโปรแกรมด้านอื่นๆ ที่น่าสนใจเช่น ด้าน `network` , `Mouse/Keyboard input` , `OpenGL` , `Apps` เป็นต้น ซึ่งอาจจะมีไม่เยอะ แต่จะพยายามรวบรวมพื้นฐาน และแหล่งข้อมูลที่น่าสนใจไว้ จะได้หาอ่านได้ง่ายๆ

Exercise
--------
ในหมวด exercise จะรวบรวมโจทย์ต่างๆไว้ ทั้งโจทย์คิดใหม่ และโจทย์เก่าที่ยังใช้ได้ดีอยู่ เพื่อฝึกความเข้าใจในเรื่องที่ได้อ่าน และได้รู้โจทย์ลักษณะใหม่ๆ

Exercise - Introduction , Advanced , Algorithm , Data Structure
---------------------------
สำหรับหมวดพวกนี้ จะเป็นโจทย์ค่อนข้างง่าย และจะค่อนข้างตรงกับเนื้อหาหมวดต่างๆ เป็นเหมือนโจทย์ฝึกว่าเราเข้าใจเรื่องที่อ่านไปจริงหรือไม่ หรือเป็นแบบฝึกหัดท้ายบทนั่นเอง

Exercise - Easy , Medium , Hard
-------------------------------
อันนี้จะรวมโจทย์ที่จะไม่บอกว่าใช้วิธีไหนทำ โดยจะพยายามหาโจทย์แปลกๆใหม่ๆมาให้ทำ และจะมีความยากง่ายต่างกันไป ซึ่งให้ความท้าทายกับผู้ทำได้ไม่น้อย

Exercise - GCJ
--------------
หมวดนี้เป็นหมวดใหม่ ที่ได้ไอเดียมาจาก Google Code Jam โดยโจทย์ในหมวดนี้จะมีการแบ่งเป็น subtask ต่างๆ เช่น แบ่งเป็น small / large หรือ subtask ย่อยๆเลย โดยเป็นโจทย์เดียวกัน แต่อาจต้องใช้วิธีที่ต่างกันในการทำ โดย small อาจจะเขียนแบบช้าๆได้ แต่ large อาจต้องคิดเพิ่มอีกหน่อยให้เร็วพอ

For teacher
-----------
สำหรับผู้สอน reference นี้จะใช้เป็นแนวทางการสอนได้ โดยมีเรื่องบอกว่าเรื่องไหนควรสอนต่อจากเรื่องไหน มีตัวอย่างให้ มีคำอธิบายให้ และมีโจทย์ให้ ซึ่งจะช่วยให้การสอนเป็นไปได้อย่างราบรื่น และรวดเร็วขึ้นให้ทันกับเวลาที่มีน้อยลง