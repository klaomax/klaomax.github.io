---
title: key
date: 2021-02-07 16:53:31
tags: Reverse
categories: CTF
---

题目地址：https://adworld.xctf.org.cn/task/answer?type=reverse&number=4&grade=1&id=5006&page=3

先打开看下

![](key/%E6%8D%95%E8%8E%B7.PNG)

然后拖入ida打开

![](key/1%E6%8D%95%E8%8E%B7.PNG)

shift+f12查看一下字符串，发现有个地址



![](key/2%E6%8D%95%E8%8E%B7.PNG)

猜测可能是在这个地址下需要打开这个文件，查看这个字符串的引用，发现是sub_802550

![](key/3%E6%8D%95%E8%8E%B7.PNG)

明显有打开的行为，于是在这个路径下创建这个文件，随便填点东西，再打开一下程序

![](key/4%E6%8D%95%E8%8E%B7.PNG)

在ida里找到这个字符串

![](key/5%E6%8D%95%E8%8E%B7.PNG)

关键点在v13和函数sub_8020c0

![](key/6%E6%8D%95%E8%8E%B7.PNG)

明显是一堆的判断，在这下个断点，进行动态调试

![](key/7%E6%8D%95%E8%8E%B7.PNG)

这里比较了this和v7，进一步发现this是我在txt文件里写的内容，那么合理猜测v7为flag

![](key/8%E6%8D%95%E8%8E%B7.PNG)

flag为`idg_cni~bjbfi|gsxb`