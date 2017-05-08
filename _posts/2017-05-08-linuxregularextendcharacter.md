---
date: 2017-05-08 21:06:56+00:00
layout: post
title: 正则表达式-拓展正则表达式
categories: Emulate
tags: Emulate Linux
---


#### 拓展正则表达式字符
```
+	:重复一个或一个以上的前一个RE字符
	'go+d':将匹配god,good,... ...
?	:零个或一个的前一个RE字符
	'goo?d':将匹配god,good
|	:用或的方式找出数个字符串
	'good|dog|god':将匹配good,dog,god
()	:找出"组"的字符串
	'g(oo|la)d':将匹配good,glad
()+	:多个重复组的判别
	'(abc)+':将匹配abc,abcabc,abcabcabc,... ...
```
