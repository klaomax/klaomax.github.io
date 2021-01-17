---
title: secret-galaxy-300
date: 2021-01-17 23:14:22
tags: Reverse
categories: CTF
---

XCTF re secret-galaxy-300

运行一下

![](secret-galaxy-300/1%E6%8D%95%E8%8E%B7.PNG)

ida查找字符串，发现有个有意义的字符串没有打印出来，

![](secret-galaxy-300/2%E6%8D%95%E8%8E%B7.PNG)

结合题目名字，猜测有关，进入交叉引用，进入一个函数

![](secret-galaxy-300/3%E6%8D%95%E8%8E%B7.PNG)

下断点动态调试，查看地址40dad4的内存信息，发现字符串

![](secret-galaxy-300/4%E6%8D%95%E8%8E%B7.PNG)



aliens_are_around_us