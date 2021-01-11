---
title: gametime
date: 2021-01-11 11:59:39
tags: Reverse
categories:	CTF
author: miracle
---

XCTF gametime

先运行一下

![](gametime/%E6%8D%95%E8%8E%B7.PNG)

大概知道个流程是当出现s时按空格，出现x时按x，出现m时按m，但是到后面的时候间隔时间根本不够来按下键，这里我们使用动态调试，在每次要输入的地方下断点。

拖进ida我们可以找到最关键的一个函数，sub_1c1507

![](gametime/%E6%8D%95%E8%8E%B72.PNG)

进入函数里面在判断的地方下断点。

![](gametime/%E6%8D%95%E8%8E%B73.PNG)

查看v6的值就知道每次该输入什么了。动态调试就f8一步一步跟进，玩的过程中就出现了flag

![](gametime/1.PNG)

