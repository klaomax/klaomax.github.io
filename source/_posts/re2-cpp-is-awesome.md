---
title: re2-cpp-is-awesome
date: 2021-01-24 02:11:24
tags: Reverse
categories: CTF
---

XCTF reverse

ida打开，shift+f12找到关键字符串并找到main函数

![](re2-cpp-is-awesome/1%E6%8D%95%E8%8E%B7.PNG)

简单分析就知道得出flag的地方为![](re2-cpp-is-awesome/2%E6%8D%95%E8%8E%B7.PNG)

这里就是数组套数组，里面那个数组的值为外面数组的下标。根据名字，我们把里面数组的数据类型改为dd。

![](re2-cpp-is-awesome/3%E6%8D%95%E8%8E%B7.PNG)

![](re2-cpp-is-awesome/4%E6%8D%95%E8%8E%B7.PNG)

wp：

```python
a='L3t_ME_T3ll_Y0u_S0m3th1ng_1mp0rtant_A_{FL4G}_W0nt_b3_3X4ctly_th4t_345y_t0_c4ptur3_H0wev3r_1T_w1ll_b3_C00l_1F_Y0u_g0t_1t'
b=[0x24,0x00,0x05,0x36,0x65,0x07,0x27,0x26,0x2d,0x01,0x03,0x00,0x0d,0x56,0x01,0x03,0x65,0x03,0x2d,0x16,0x02,0x15,0x03,0x65,0x00,0x29,0x44,0x44,0x01,0x44,0x2b]
for i in range(len(b)):
    print(a[b[i]],end='')
```

运行得

ALEXCTF{W3_L0v3_C_W1th_CL45535}