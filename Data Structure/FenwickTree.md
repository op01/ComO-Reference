Fenwick Tree
============
Fenwick Tree หรือเรียกอีกชื่อนึงว่า ต้นมะนาว เป็นโครงสร้างข้อมูลที่ใช้แก้ปัญหา cumulative frequency ได้อย่างมีประสิทธิภาพ
Code
-----
```cpp
int update(int idx,int val)
{
  for(;idx<=n;idx+=idx&-idx)tree[idx]+=val;
}
```
int read(int idx)
{
  for(;idx;idx-=idx&-idx)ret+=tree[idx];
  return ret;
}
Just remember and use it
Compare
-------
Behind the Tree
================
Two's complement
----------------
Least Significant bit
---------------------
