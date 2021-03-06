BigO (for beginner)
=======
ในหมวด algorithm นี้หลายๆคนอาจจะเห็นตัว O อยู่ แล้วข้างในก็มีอะไรก็ไม่รู้ ไม่รู้ความหมายคืออะไร เช่น O(N) O(1) O(nlogn) อะไรเช่นนี้

Loop
--------
```cpp
int n = 50000;
for(int i = 0;i < n;i++) {
printf("Hello");
}
```
loop ข้างบนนั้น ถามว่าคำสั่ง `printf("Hello")` จะถูกเรียกกี่รอบ ? คำตอบก็คือ n รอบนั่นเอง (n = 50000 ในที่นี้) หรือพูดแบบภาษาง่ายๆ คือต้องใช้เวลาประมวลผล 50000 หน่วย (คิดหยาบๆ ให้ printf เป็น 1 หน่วย)

```cpp
int n = 50000;
for(int i = 0;i < n;i++) {
for(int j = 0;j < n;j++) {
printf("Hello");
}
}
```
ถ้าเป็นแบบนี้ ก็จะใช้เวลาประมวลผล n*n (n^2) ครั้ง (หรือใช้เวลาประมวลผล 2500000000 หน่วย)

Big O ก็คือสิ่งที่บอกเวลาประมวลผลแบบในลูปพวกนี้ ดังนั้นอันบน ก็จะเป็น O(n) และอันล่างก็จะเป็น O(n^2)

Rule
------------
```cpp
int n = 50000;
for(int i = 0;i < n;i++) {
printf("Hello");
printf("Hello");
printf("Hello");
}
```
loop ข้างบน หลายๆคนจะคิดว่าเป็น O(3n) แต่เรื่องของ BigO ให้ตัดค่าคงตัวพวกนี้ทิ้ง เหมือนกับว่าเราพยายามหาอัตราการเติบโตอยู่ (เอาเป็นว่ามันตัดทิ้งไปละกันนะ ไม่รู้จะอธิบายยังไง 555)

```cpp
int n = 50000;
for(int i = 0;i < n*n;i++) {
printf("Hello");
}
for(int i = 0;i < n;i++) {
printf("Hello");
}
```
อันนี้ก็ควรจะเป็น O(n^2+n) แต่ให้ตัดตัวน้อยทิ้งไปเลย (คือเหมือนเราพยายามจะทำให้ง่ายที่สุด สมมติเก็บผักมาได้ 500000 กำ กับเศษอีก 10 กำ เราก็บอกง่ายๆว่าเก็บได้ 500000 เอาค่าเยอะสุดมาบอก)

```cpp
int n = 50000;
int m = 20000;
for(int i = 0;i < n;i++) {
for(int j = 0;j < m;j++) {
printf("Hello");
}
}
```
อย่างนี้ก็ O(nm) นะ

```cpp
int n = 50000;
for(int i = 0;i < n;i++) {
for(int j = 0;j < n/2;j++) {
printf("Hello");
}
}
```
ควรจะเป็น O(n^2/2) แต่เพื่อความง่าย ก็บอกไปว่า O(n^2)


คือจริงๆ BigO บอกเวลาที่แย่ที่สุด เราจะบอกมันเป็น O(n^999999) มันก็ถูก แต่เราก็ควรเอาให้มันใกล้ที่สุดไว้ก่อน (แต่ถ้าเรียนสูงๆไป จะเริ่มมีการวิเคราะห์ BigO ที่แม่นยำและยากมากขึ้น)
