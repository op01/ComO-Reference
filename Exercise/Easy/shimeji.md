ชิเมจิ (Shimeji)
====================
Tags : `Easy`<br>
Difficulty : &#9733;&#9733;&#9733;&#9734;&#9734;&#9734;&#9734;&#9734;&#9734;&#9734;<br>
Estimated time solve : 10 min<br>

- - -

วันหนึ่ง คุณได้นำเจ้าตัวประหลาดแสนวิเศษตัวหนึ่งที่มีชื่อว่า ชิเมจิ (Shimeji) มาเลี้ยงในบ้านตามประสาคนที่ชอบของแปลก เจ้าชิเมจินี้มีสมบัติอย่างหนึ่งคือ เมื่อถึงวันถัดไป มันจะเพิ่มจำนวนเป็นสองเท่าของเดิม เช่น วันแรกมี 1 ตัว วันต่อมา จะมี 2 ตัว และวันต่อมาก็จะเพิ่มเป็น 4 ตัว เป็นต้น

ทว่า หลังจากที่คุณทำการศึกษาอย่างลึกซึ้ง ก็พบกับความจริงที่น่าตกตะลึงว่า จุดประสงค์ในการแบ่งตัวของมันก็เพื่อยึดครองบ้านของคุณและคุณก็จะกลายเป็นคนไร้ที่อยู่ไปโดยปริยาย สิ่งเดียวที่จะหยุดพวกมันได้ คือ ขนมช็อกโกแลตรูปก้อนหินที่มีจำนวนขนมอยู่ m ชิ้น หากชิเมจิได้กินขนมนี้เข้าไปเพียงชิ้นเดียว ก็จะหายไปทันที แต่ด้วยความที่ขนมชนิดนี้หาได้ค่อนข้างยาก คุณจึงซื้อได้แค่วันละห่อเท่านั้น และด้วยความที่คุณเป็นคนรอบคอบ จึงต้องทำการคำนวณเวลาที่ใช้ในการกำจัดเหล่าชิเมจิเหล่านี้ก่อนจะเริ่มดำเนินงานต่อไป

Credit : โจทย์จากน้องมิว โพสต์ในกรุ๊ป ComO-Suannon วันที่ 23/6/58 [ไฟล์ต้นฉบับ](https://word.office.live.com/wv/WordView.aspx?FBsrc=https%3A%2F%2Fwww.facebook.com%2Fattachments%2Ffile_preview.php%3Fid%3D1626227837618070%26time%3D1435228636%26metadata&access_token=100001552070876%3AAVJGN4bDWZx8_UlxAVVEm5w2nbSZCKa1kFWYvE0tfHGO3g&title=%E0%B8%8A_%E0%B9%80%E0%B8%A1%E0%B8%88_.docx)

งานของคุณ
---------
เขียนโปรแกรมหาระยะเวลาในการกำจัดชิเมจิให้หมดไปจากบ้าน

Input
-----
บรรทัดแรกรับจำนวน testcase **T** (**T** <= 10)

แต่ละเทสเคสมี 2 บรรทัด 

บรรทัดแรกประกอบด้วยจำนวนเต็ม **n** แทนจำนวนชิเมจิเริ่มแรก โดย 1 < **n** < 100

บรรทัดที่ 2 ประกอบด้วยจำนวนเต็ม **m** แทนจำนวนขนมช็อกโกแลตใน 1 ห่อ โดย 1 < **m** < 100

Output
------
แต่ละเทสเคสมี 1 บรรทัด แสดงจำนวนเต็มจำนวนเดียวแสดงระยะเวลาในการกำจัดชิเมจิ (เป็นวัน) ถ้าไม่สามารถกำจัดให้หมดได้ ให้แสดงคำว่า `R.I.P.`

Example Input
-------
```
3
3
5
12
7
12
2
```

Example Output
-------------
```
1
3
R.I.P
```