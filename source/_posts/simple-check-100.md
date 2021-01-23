---
title: simple_check_100
date: 2021-01-24 00:01:26
tags: Reverse
categories: CTF
---

XCTF re simple_check_100

先用ida打开

![](simple-check-100/1%E6%8D%95%E8%8E%B7.PNG)

看一下check_key函数和interesting_function

![](simple-check-100/2%E6%8D%95%E8%8E%B7.PNG)

![](simple-check-100/3%E6%8D%95%E8%8E%B7.PNG)

这个check_key函数怎么看也不像能对的样子....

另一个函数虽然可以通过静态分析解题，但是也很复杂。（看第一张图那一堆数就知道了）

所以我们采用动态分析，直接跳入check_key的正确判断



![](simple-check-100/5%E6%8D%95%E8%8E%B7.PNG)

看这里我们知道，通过测试eax的值是否为0来进行跳转，那我们运行到这里时直接让eax的值等于1就能进入正确的判断里。

在Linux下用gdb调试

![](simple-check-100/6%E6%8D%95%E8%8E%B7.PNG)

然后单步n运行到test处

![](simple-check-100/7%E6%8D%95%E8%8E%B7.PNG)

这里用 `i r eax` 指令可以看到eax寄存器的值为0x0，我们直接用`set $eax=0x1`让其等于1，然后c

![](simple-check-100/8%E6%8D%95%E8%8E%B7.PNG)

flag_is_you_know_cracking!!!