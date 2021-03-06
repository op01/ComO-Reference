Algorithm
============

Algorithm คือวิธีการทำสิ่งต่างๆ อย่างเป็นแบบแผนแน่นอน เช่น วิธีไปกินข้าว

```
1. เดินไปโรงอาหาร
2. ถ้าร้านข้าวมันไก่เปิด ให้ทำข้อ 5 แต่ถ้าไม่ ให้ทำข้อ 3
3. ถ้าร้านก๋วยเตี๋ยวเปิด ให้ทำข้อ 5 แต่ถ้าไม่ ให้ทำข้อ 4
4. เดินไปร้านที่ใกล้จากตรงนี้ที่สุดและยังเปิดอยู่
5. ซื้อข้าว
```

จะมีการควบคุมคำสั่ง เงื่อนไขต่างๆอย่างเป็นรูปแบบแน่นอน (deterministic) คือถ้าข้อมูลนำเข้าเหมือนกัน ผลลัพธ์จะเหมือนกันแน่นอน เช่นวิธีข้างบน ถ้าร้านข้าวเปิดเหมือนกันหมดทุกวัน เราก็ทำเหมือนๆกันทุกวัน แต่ลองคิดถึงสมองคน ให้โจทย์ข้อเดิม บางทียังทำออกมาได้ไม่เท่ากันเลย (อาจจะลืม หรืออะไรสักอย่าง)

ในที่นี้จะแบ่งเป็นหมวดต่างๆดังนี้

Searching
----------
[Binary Search](binarySearch.md)  - ค้นหาข้อมูลใน array ที่เรียงแล้ว ด้วยเวลา O(log n)

String
----------
[String finding (Naive)](stringFindNaive.md) - ค้นหาคำ B ว่ามีอยู่ใน A มั้ย ด้วยเวลา O(AB)

Math
----------
[Exponential by Squaring](expBySquaring.md) - หาค่าของ x^n ได้ ด้วยเวลา O(log n)


ETC
-----------
[Big O](BigO.md)