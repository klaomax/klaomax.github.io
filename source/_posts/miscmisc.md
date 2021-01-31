---
title: miscmisc
date: 2021-01-31 13:57:00
tags: Misc
categories: CTF
---

题目地址 

https://adworld.xctf.org.cn/task/answer?type=misc&number=1&grade=1&id=5456&page=3

下载下来一个压缩包，压缩包里是一张png，用101editor打开发现有其他东西，改后缀为zip打开。

![](miscmisc/1%E6%8D%95%E8%8E%B7.PNG)

![](miscmisc/2%E6%8D%95%E8%8E%B7.PNG)

打开后又发一个jpg和一个zip

![](miscmisc/3%E6%8D%95%E8%8E%B7.PNG)

zip里面是加密的。

![](miscmisc/4%E6%8D%95%E8%8E%B7.PNG)

那么老规矩改jpg后缀为zip打开试试，得到一个flag.txt，但是是假的

这时候我们发现这两个压缩包里都有flag.txt并且两个文件的CRC32码一样，可以用明文攻击破解密码。

![](miscmisc/5%E6%8D%95%E8%8E%B7.PNG)

AZPR明文攻击

![](miscmisc/6%E6%8D%95%E8%8E%B7.PNG)

![](miscmisc/7%E6%8D%95%E8%8E%B7.PNG)

解压密码：`z$^58a4w`

又得到三个文件

![](miscmisc/8%E6%8D%95%E8%8E%B7.PNG)

zip是个加密的，密码估计和png和doc有关

png

![](miscmisc/9%E6%8D%95%E8%8E%B7.PNG)

怀疑用了隐写，zsteg打开

![](miscmisc/10%E6%8D%95%E8%8E%B7.PNG)

pass:z^ea但去试了下并不是密码又观察图片六个问号估计还差六个字符。我们打开doc，里面就一句话，估计隐藏了，我们`ctrl+A`->`字体`->取消隐藏。

![](miscmisc/11%E6%8D%95%E8%8E%B7.PNG)

![](miscmisc/12%E6%8D%95%E8%8E%B7.PNG)

然后我试了把这些加在z^ea后面或者前面，反正怎么试都不对，这时去看了下wp，发现是每个的最后一个字符........解压密码为z^ea4zaa3azf8（这谁想得到）

![](miscmisc/13%E6%8D%95%E8%8E%B7.PNG)

flag{12sad7eaf46a84fe9q4fasf48e6q4f6as4f864q9e48f9q4fa6sf6f48}