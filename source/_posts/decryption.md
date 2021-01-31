---
title: decryption
date: 2021-01-31 13:42:39
tags: Reverse	
categories: CTF
---

DSA比赛的re  decryption

下载附件后用ida打开

![](decryption/1%E6%8D%95%E8%8E%B7.PNG)

逻辑还是很清晰地，里面的关键之处是

![2捕获](decryption/2%E6%8D%95%E8%8E%B7.PNG)

`memcmp`的作用是比较Buf1和buf的0x20长度的数据，即32个字符。Buf1要经过上面那个函数，buf里面是一些字符，看样子是需要Buf1与buf的前0x20个字符相等。

encrypt函数

![](decryption/3%E6%8D%95%E8%8E%B7.PNG)

逻辑很简单，这里我采用的是爆破的做法，直接上wp吧。

```python
a1=[0x12,0x45,0x10,0x47,0x19,0x49,0x49,0x49,0x1a,0x4f,0x1c,0x1e,0x52,0x66,0x1d,0x52,0x66,0x67,0x68,0x67,0x65,0x6f,0x5f,0x59,0x58,0x5e,0x6d,0x70,0x0a1,0x6e,0x70,0x0a3]
v5=[]
for j in a1:
    v5.append(j^0x23)
str1=[]
for i in range(26):
    str1.append(ord('a')+i)
for i in range(26):
    str1.append(ord('A')+i)
for i in range(10):
    str1.append(ord('0')+i)
result=[]

for i in range(32):
    for k in str1:
        m=k
        v6=i
        while True:
            v4=2*(v6&m)
            m^=v6
            v6=v4
            if v4==0:
                break
        if m==v5[i]:
            result.append(chr(k))
            break
print(''.join(result))


```

flag为：1e1a6edc1c52e80b539127fccd48f05a