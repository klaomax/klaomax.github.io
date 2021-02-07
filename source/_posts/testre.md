---
title: testre
date: 2021-02-07 17:17:03
tags: Reverse
categories: CTF
---

题目地址：https://adworld.xctf.org.cn/task/answer?type=reverse&number=4&grade=1&id=5476&page=3

ida打开，找到main函数

![](testre/%E6%8D%95%E8%8E%B7.PNG)

sub_400d00分析一下发现就是读取输入，关键点是sub_400700，里面一大堆东西，比较复杂，先看关键的地方

![](testre/1%E6%8D%95%E8%8E%B7.PNG)



这里比较了字符串`D9cS9N9iHjMLTdA8YSMRMp`,顺着s变量往上看，发现相关的v11变量

![](testre/3%E6%8D%95%E8%8E%B7.PNG)

byte_400eb0是base58编码表，再往上看发现v11有个模58，除58的行为，然后发现这就是base58

![](testre/4%E6%8D%95%E8%8E%B7.PNG)

把上面的`D9cS9N9iHjMLTdA8YSMRMp`进行base58解码就得到flag

`base58_is_boring`（套上flag{}）

