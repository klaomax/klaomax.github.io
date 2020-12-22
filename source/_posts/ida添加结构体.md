---
title: IDA添加结构体
date: 2020-12-23 00:13:40
tags: IDA技巧
categories: CTF
---



接re-easyvm这题，里面有个这个

![5](ida添加结构体/5.PNG)

这三个变量我们分析之后发现，这应该是一个结构体里面的东西。那么下面介绍一下如何在ida里面新建一个结构体。

先来到structures页面（快捷键shift+f9）

![](ida添加结构体/ida1.PNG)

按insert键

![](ida添加结构体/ida2.PNG)

然后就出现这个

![](ida%E6%B7%BB%E5%8A%A0%E7%BB%93%E6%9E%84%E4%BD%93/ida3.PNG)

对着ends那一行按d键，就会添加一个结构体成员，然后对着它按d可以切换它的数据类型

因为题里三个变量都是int，所以选择dd

![](ida添加结构体/ida4.PNG)

因为我们需要三个成员变量，所以选中field_0，右键，选择expand

![](ida添加结构体/ida5.png)

因为按字节expand，所以扩充8个字节，再给每个变量重命名一下

最后就是这样

![](ida添加结构体/ida6.png)

然后在函数里面将v3的变量类型设为mystruct

![](ida添加结构体/ida7.png)

再把sub_4012f0那个函数里面的a1变成mystruct*

![](ida添加结构体/ida8.png)

这样逻辑就清晰特别多了。

