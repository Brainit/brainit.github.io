---
date: 2017-05-08 20:06:56+00:00
layout: post
title: 正则表达式-基础正则表达式字符
categories: Emulate
tags: Emulate Linux
---


#### 基础正则表达式字符
```
^word	:待查找的字符串在行首
		'^word':将匹配	word*
word$	:待查找的字符串在行尾
		'word$':将匹配	sdfsdword
.		:代表一定有一个任意字符的字符
		'go.d':将匹配	go1d,goad,... ...
\		:转义字符，将特殊符号的特殊意义去除
*		:重复0个或无穷多个前一个字符
		'go*d':将匹配	gd,god,good,... ...
[list]	:从字符集合的RE字符里面找出想要选取的字符
		'[gzl]oo':将匹配		goo,zoo,loo
[n1-n2]	:从字符集合的RE字符里面找出想要选取的字符范围
		'[a-z]':将匹配所有小写字符
[^list]	:从字符集和的RE字符里面找出不要的字符串或范围
		'[^abc]d':将匹配		所有非abc和d的组合
\[n,m\]	:连续n到m个前一个RE字符，若为\[n\]则是连续n个前一个RE字符，若为\[n,\]则是连续n个以上的前一个RE字符
		'go\[1,2\]d':将匹配	god,good
```
