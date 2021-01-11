---
title: What-is-this
date: 2021-01-11 12:24:15
tags: Misc
categories: CTF
author: miracle
---

XCTF misc What-is-this

下载得到一个二进制文件，发现里面有图片，于是改后缀为压缩包，打开得到两张图片。

![]()![捕获](What-is-this/%E6%8D%95%E8%8E%B7.PNG)

![](What-is-this/2%E6%8D%95%E8%8E%B7.PNG)

打开两张图片发现很相似，于是用stegsolve打开，把两张图片重合。

![](What-is-this/4%E6%8D%95%E8%8E%B7.PNG)

analyse->image combiner

![](What-is-this/3%E6%8D%95%E8%8E%B7.PNG)

最后flag就是 `AZADI TOWER`(有一个空格)