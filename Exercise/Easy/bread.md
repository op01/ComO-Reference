Bread
====================
Tags : `Easy`<br>
Difficulty : &#9733;&#9733;&#9733;&#9733;&#9734;&#9734;&#9734;&#9734;&#9734;&#9734;<br>
Estimated time solve : 15 min<br>

- - -

คุณมีขนมปังอยู่ก้อนนึง มีความยาว **X** เมตร แต่เพื่อนๆของคุณอยากกินขนมปังด้วย เนื่องจากคุณเป็นคนดีจึงอยากแบ่งขนมปังให้เพื่อนๆบ้าง คุณจึงจ้างคนตัดขนมปังมาช่วยแบ่งให้เพื่อนๆคุณ แต่คนตัดคนนี้เรื่องมาก ทุกครั้งที่เขาตัดขนมปัง 1 ชิ้น เขาจะขอขนมปังไปกินอีก 1 เมตรเป็นของเขาเอง 

เช่น เริ่มมามี 8 เมตร แบ่งเป็น 4 กับ 3 เมตร และอีกเมตรนึงเป็นของคนตัด หลังจากนั้นแบ่ง 4 เมตรเป็น 2 กับ 1 เมตร ก็จะได้ขนมปัง 3 ชิ้นคือ 1 2 3 เมตร (และอีก 2 เมตรเป็นของคนตัด)

เพื่อนๆของคุณมี **N** คน และแต่ละคนต้องการขนมปังขนาดต่างๆกันไป โดยขนมปังนั้นต้องเป็นชิ้นเดียวกัน (ห้ามเอา 2 ชิ้นมารวมกันให้เพื่อน) และต้องเป็นขนาดนั้นพอดีเท่านั้น และการแบ่งขนมปังห้ามแบ่งแบบ จาก 4 เมตร แบ่งเป็น 3 กับ 0 เพราะคนตัดนั้นเรื่องมาก

ถามว่าจากขนมปังตอนแรก สามารถตัดตามเงื่อนไขต่างๆ ให้เพื่อนของคุณได้ขนมปังตามที่เขาต้องการ และสุดท้ายไม่มีขนมปังเหลืออยู่เลยได้หรือไม่

Input
-----
บรรทัดแรกรับจำนวน testcase **T** (**T** <= 5)

แต่ละเทสเคสมี 2 บรรรทัด
- บรรทัดแรกรับ **X** (1 <= **X** <= 100) และ **N** (1 <= **N** <= 10) แทนขนาดขนมปังเริ่มต้นและจำนวนเพื่อนของคุณ
- บรรทัดที่สองมีจำนวนเต็ม **N** ตัว แสดงถึงขนาดขนมปังที่เพื่อนแต่ละคนต้องการ

Output
------
แต่ละ testcase แสดงคำว่า "YES" หรือ "NO" แสดงว่าสามารถแบ่งขนมปังได้พอดี และไม่มีเหลือได้หรือไม่

Example Input
-------
```
2
8 3
1 2 3
10 5
1 2 1 2 1
```

Example Output
-------------
```
YES
NO
```