Fenwick Tree
============
Fenwick Tree หรือเรียกอีกชื่อนึงว่า ต้นมะนาว เป็นโครงสร้างข้อมูลที่ใช้แก้ปัญหา cumulative frequency ได้อย่างมีประสิทธิภาพ
Problem
-------
มีกล่องอยู่ n กล่อง แต่ละกล่องมีของอยู่ 0 ชิ้น มี 2 operation คือ

1. เพิ่มของใส่กล่องที่ i จำนวน v ชิ้น
2. นับจำนวนของตั้งแต่กล่องแรกถึงกล่องที่ i

Code
-----
```cpp
int update(int idx,int val)
{
  for(;idx<=n;idx+=idx&-idx)tree[idx]+=val;
}
int read(int idx)
{
  int ret=0;
  for(;idx;idx-=idx&-idx)ret+=tree[idx];
  return ret;
}
```
Just remember and use it
Compare
-------
Behind the Tree
================
Two's complement
----------------
Least Significant bit
---------------------
