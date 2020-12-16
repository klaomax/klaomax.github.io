---
title: 稳住我们能赢 WP
date: 2020-12-16 18:54:08
tags:Reverse
categories:CTF
author:miracle
---

学校靶场上的题，虽然讲过，记录一下我做的过程

第一步 拖入ida，直接f5  

![1](%E7%A8%B3%E4%BD%8F%E6%88%91%E4%BB%AC%E8%83%BD%E8%B5%A2-WP/1.PNG)

这一大段 sub_4024d9你点进去看一下，

![2](%E7%A8%B3%E4%BD%8F%E6%88%91%E4%BB%AC%E8%83%BD%E8%B5%A2-WP/2.PNG)

这个函数你点到底，发现就是一个strcpy

![3](%E7%A8%B3%E4%BD%8F%E6%88%91%E4%BB%AC%E8%83%BD%E8%B5%A2-WP/3.PNG)

这个过程没做什么其他操作，一堆混淆的代码

回到一开始

![1](%E7%A8%B3%E4%BD%8F%E6%88%91%E4%BB%AC%E8%83%BD%E8%B5%A2-WP/1.PNG)

下面的put函数就是输出那句提示语，再下面那个sub_402432也是个套了多个混淆的函数，点到最后就是一个scanf到v5，我们就知道了v5就是我们的输入

再下面那个sub_401B97，也是个套了很多层没用的，点到最后

![4](%E7%A8%B3%E4%BD%8F%E6%88%91%E4%BB%AC%E8%83%BD%E8%B5%A2-WP/4.PNG)

这就是返回了a1，即我们的输入的长度

再回到最外面

![1](%E7%A8%B3%E4%BD%8F%E6%88%91%E4%BB%AC%E8%83%BD%E8%B5%A2-WP/1.PNG)

v3=len(v5)

点开最后一个函数

发现是一层层根据输入的长度来进行判断的

我们依次点到最里面



<img src="%E7%A8%B3%E4%BD%8F%E6%88%91%E4%BB%AC%E8%83%BD%E8%B5%A2-WP/5.PNG" style="zoom: 75%;" />

<img src="%E7%A8%B3%E4%BD%8F%E6%88%91%E4%BB%AC%E8%83%BD%E8%B5%A2-WP/6.PNG" alt="6" style="zoom:75%;" />

<img src="%E7%A8%B3%E4%BD%8F%E6%88%91%E4%BB%AC%E8%83%BD%E8%B5%A2-WP/7.PNG" alt="7" style="zoom:75%;" />

<img src="%E7%A8%B3%E4%BD%8F%E6%88%91%E4%BB%AC%E8%83%BD%E8%B5%A2-WP/8.PNG" alt="8" style="zoom:70%;" />

也就知道了输入长度应该等于38，最后传入了*输入+5，然后判断

*a1+32=}，那么很明显了，我们输入的形式是flag{}，中间有32个字符。

然后把下面的函数依次点开分析的它的作用

第一个函数作用：大小写互换

<img src="%E7%A8%B3%E4%BD%8F%E6%88%91%E4%BB%AC%E8%83%BD%E8%B5%A2-WP/9.PNG" alt="9" style="zoom: 67%;" />

这里要对90和65敏感一点，90是Z的acsii码，65是A的acsii码，32是大小写字母之间acsii码的差

![3.1](%E7%A8%B3%E4%BD%8F%E6%88%91%E4%BB%AC%E8%83%BD%E8%B5%A2-WP/3.1.PNG)

回到前面，我们来到第二个函数

<img src="%E7%A8%B3%E4%BD%8F%E6%88%91%E4%BB%AC%E8%83%BD%E8%B5%A2-WP/10.PNG" alt="10" style="zoom:67%;" />

（首先看到一长串的连续的字符，记得改成char数组，就会自动变成字符串，就像这里的v4）

这个函数主要是做了一个变换，怎么变换我都写在了图里，同时也有点小坑，这个地方。

回到前面来到第三个函数

(还是要记着对一堆连续的字符串改成char数组)

<img src="%E7%A8%B3%E4%BD%8F%E6%88%91%E4%BB%AC%E8%83%BD%E8%B5%A2-WP/11.PNG" alt="11" style="zoom:67%;" />

出现了模3，最后也明显出现了=，可以判断是base64换表

回到前面，最后剩下一个大小写转换

脚本代码如下

```python
import base64
import string
def daxiaoxiezhuanhuan(s):
 def fn(x):
    if x.islower():
        return x.upper()
    elif x.isupper():
        return x.lower()
    else:
        return x
 result=''.join([fn(r) for r in list(s)])
 return(result)

s="CLrAXaMBYaXOYL@xYaLoSk@nXLrBX1qlhkSoYaXwXjS="
daxiaoxiezhuanhuan(s)
str1 = s  # 要解密的文本
string1 = "YZablmn9@STwxycrsHIJKtuvQR4567823#VABijkz0CDUpqFGLM1oNOPWXEdefgh"  # 换了之后的表
string2 = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/"
a = base64.b64decode(str1.translate(str.maketrans(string1, string2)))
print(a)

# test="7ea10b5233a85059a4feb250dc552703"
# a=daxiaoxiezhuanhuan(test)

a='8FB21C6344B9616AB50FC361ED663814'
a=list(a)
b=list("0123456789ABCDEF")
for i in range(len(a)):
    for j in range(len(b)):
        if a[i]==b[j]:
            a[i]=b[j-1]
            break
a=''.join(a)
print(a)
print(daxiaoxiezhuanhuan(a))

```

flag{7ea10b5233a85059a4feb250dc552703}

小结：

（1）base64

（2）记得对一长串的连续数据改成数组

（3）一些常见的acsii码