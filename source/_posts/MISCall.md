---
title: MISCall
date: 2021-01-24 02:54:22
tags: Misc
categories: CTF
---

XCTF misc

下载下来后在windows下不知道是什么文件，放进虚拟机的linux下发现是个压缩包，解压后发现有个flag，但是是假的。

使用`ls -a`发现有个隐藏的.git文件

![](MISCall/1%E6%8D%95%E8%8E%B7.PNG)

于是猜测这个题与git有关。事实上这个题考察的时git泄露。

`git stash show`校验列表中存储的文件

![](MISCall/2%E6%8D%95%E8%8E%B7.PNG)

`git stash apply`重新进行存储，复原上面的文件

![](MISCall/3%E6%8D%95%E8%8E%B7.PNG)

得到一个s.py，运行一下得到flag

![](MISCall/4%E6%8D%95%E8%8E%B7.PNG)

NCN4dd992213ae6b76f27d7340f0dde1222888df4d3