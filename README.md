Computer Programming
====================
```cpp
#include<cstdio>
int main()
{
	printf("Hello ComO !!!");
}
```
Competitive Programming
---------
การเขียนโปรแกรมเพื่อแข่งขันด้าน algorithm (หลักการคิด) , data structure (โครงสร้างข้อมูล) และอื่นๆ ซึ่งเป็นประเภทของการเขียนโปรแกรมที่ใช้ใน

1. ค่ายโอลิมปิกวิชาการสาขาคอมพิวเตอร์ (สอวน / สสวท) และการแข่งขันโอลิมปิกวิชาการคอมพิวเตอร์ระดับประเทศและระดับโลก (TOI / IOI)
2. การแข่งขัน online เช่น Google Code Jam , Facebook Hacker Cup (จัดปีละครั้ง)

การเขียนโปรแกรมแบบ Competitive Programming นี้เป็นจุดประสงค์หลักของชุมนุม ComO มาตั้งแต่ก่อตั้ง คือการฝึกฝนสมาชิก ให้สามารถแข่งขันในเวทีโอลิมปิกวิชาการคอมพิวเตอร์ โดยจะแบ่งเนื้อหาได้เป็น

1. หลักการเขียนโปรแกรม
2. การเขียนโปรแกรมพื้นฐาน (สอวน ค่าย 1)
3. การเขียนโปรแกรมขั้นกลาง (สอวน ค่าย 2)
4. การเขียนโปรแกรมขั้นสูง (TOI , สสวท และการแข่งขันอื่นๆ)

```cpp
#include <bits/stdc++.h>
using namespace std;
int main() {
    int t,tt;
    scanf("%d",&tt);
    for(t=0;t < tt;t++) {
        int n,mote,ans,pos = 0,time = 0;
        scanf("%d %d",&mote,&n);
        ans = n;
        int arr[n];
        for(int i = 0;i < n;i++) scanf("%d",&arr[i]);
        sort(&arr[0],&arr[n]);
        if(mote > 1) {
            while(pos < n) {
                while(mote > arr[pos] && pos < n)
                    mote += arr[pos++];
                ans = min(ans,time+ n-pos);
                time++;
                mote += mote-1;
            }
        }
        printf("Case #%d: %d\n",t+1,ans);
    }
}
```
>**Code 1** : solution ของ Google Code Jam 2013 รอบ 1B ข้อ osmos (22/100 คะแนน) ในภาษา C++
ประโยชน์ในด้านอื่นๆ
------
การเขียนโปรแกรมนั้น เมื่อรู้พื้นฐานแล้วจะสามารถนำไปสู่การเขียนโปรแกรมในภาษาอื่นๆได้ ซึ่งจะมีการใช้แตกต่างกันไป ตัวอย่างเช่น

1. HTML + Javascript + CSS ไว้เพื่อเขียนเว็บไซต์ต่างๆ
2. C++ และ OpenGL / DirectX การเขียนแอพพลิเคชัน 3 มิติที่มีประสิทธิภาพ ( Engine เกมแทบทุกเกมใช้ภาษา C++ เช่น Unreal engine (C++ , C#) / CryEngine (C++ , Lua) เป็นต้น
3. python ภาษานี้เขียนได้สั้นและเร็ว รวมถึงทำงานได้หลากหลาย แต่ประสิทธิภาพอาจจะด้อยกว่า C++ ในบางเรื่อง
4. PHP ไว้เขียน web server
