---
title: Hear-with-yours-Eyes
date: 2021-01-11 12:14:36
tags: Misc
categories: CTF
author: miracle
---

XCTF misc Hear-your-Eyes

下载得到一个二进制文件

![](Hear-with-yours-Eyes/%E6%8D%95%E8%8E%B7.PNG)

sounds.wav应该是个音频文件，改文件为压缩包，解压就能得到这个音频文件。

![](Hear-with-yours-Eyes/%E6%8D%95%E8%8E%B72.PNG)

这个文件直接打开，是一段刺耳的高频，再根据题目信息，可能是需要我们分析频谱，这里需要用到软件

`Audacity`

打开后，`sound->频谱图`，就能得到flag

![](Hear-with-yours-Eyes/3%E6%8D%95%E8%8E%B7.PNG)

