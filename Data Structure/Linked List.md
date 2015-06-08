# Linked List

โครงสร้างข้อมูลแบบ Array เป็นโครงสร้างข้อมูลที่สามารถเก็บข้อมูลชนิดเดียวกันได้เป็นสายยาวๆ แต่ Array มีปัญหาเมื่อต้องเพิ่มหรือลบข้อมูลตรงกลาง ซึ่งจำเป็นต้องขยับข้อมูลทางขวาออกไปทั้งหมด แต่ Linked List จะมีความยืดหยุ่นกว่า ซึ่งจะเข้ามาช่วยแก้ปัญหาการเพิ่มหรือลบข้อมูลตรงกลางของ Array

Linked List จะแบ่งแยกได้ 2 แบบ

แบ่งแยกตามการย้อนกลับข้อมูลก่อนหน้าได้

1. Singly Linked List เป็น Linked List แบบที่มี Pointer ชี้ไปด้านหน้าได้อย่างเดียว
2. Doubly Linked List เป็น Linked List แบบที่มี Pointer ชี้ไปด้านหน้า และชี้กลับด้านหลัง

![Singly Linked List](https://github.com/op01/ComO-Reference/blob/master/Data%20Structure/Image/singly-linked-list.png)

Singly Linked List

![Doubly Linked List](https://github.com/op01/ComO-Reference/blob/master/Data%20Structure/Image/doubly-linked-list.png)

Doubly Linked List

แบ่งแยกตามการจบและไม่จบของข้อมูล

1. Circular Linked List เป็น Linked List ที่เมื่อจบชุดข้อมูลแล้วจะชี้กลับมายังตัวตั้งต้น หรือชี้วนกลับมาเป็นวงกลมนั่นเอง
2. Non-Circular Linked List เป็น Linked List ที่เมื่อจบชุดข้อมูลแล้วจะไม่ชี้กลับมายังตัวตั้งต้น

![Circular Linked List](https://github.com/op01/ComO-Reference/blob/master/Data%20Structure/Image/circular-linked-list.png)

Circular Linked List

![Doubly Linked List](https://github.com/op01/ComO-Reference/blob/master/Data%20Structure/Image/non-circular-linked-list.png)

Non-Circular Linked List

# ส่วนประกอบของ Linked List

สำหรับ Linked List แต่จะช่องจะเรียกว่า Node แต่ละ Node จะแบ่งเป็นส่วนประกอบ 2 ส่วนหลักๆ ดังนี้

1. ส่วนข้อมูล คือส่วนที่มีข้อมูลเก็บไว้ เราสามารถเก็บข้อมูลได้ทั้ง int, float, char, double หรืออื่นๆ ได้ตามต้องการ
2. ส่วนชี้ คือส่วนที่เก็บ pointer เพื่อชี้ไปยังที่อยู่ของ Node ถัดไป หรือ Node ก่อนหน้า เพื่อจะทำให้เราไปยัง Node ก่อนหน้าหรือ Node ถัดไปได้ถูกต้อง (ถ้าชี้ผิดก็บึ้มนะครัช)

ตามปกติแล้ว Linked List ในภาษา C มักจะเขียนเป็น Structure หรือ sturct ดังนี้

```cpp
struct list {
    list *previousNode;
    int data;
    list *nextNode;
};
```

sturct ข้างต้นเป็นเพียงตัวอย่างเท่านั้น ในการใช้งานจริง Linked List สามารถสร้างให้มีข้อมูลได้หลายแบบ หรืออาจไม่มี pointer ชี้ไปยัง node ก่อนหน้าก็ได้
