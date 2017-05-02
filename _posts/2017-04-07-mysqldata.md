---
date: 2017-04-07 17:16:17+00:00
layout: post
title: MySQL基本数据类型
categories: Emulate
tags: Emulate MySQL
---
* char(n)：固定长度的字符串，用户指定长度ｎ，也可以使用全称character
* varchar(n)：可变长度的字符串，用户指定最大长度ｎ，等价于全称character varying
* int：整数类型（和机器相关的整数的有限子集），等价于全称integer
* smallint：小整数类型（和机器相关的整数类型的子集）
* numeric(p,d)：定点数，精度由用户指定，这个数有ｐ位数字（加上一个符号位），其中ｄ位数字在小数点右边。所以在一个这种类型的字段上，numeric(3,1)可以精确存储44.5，但不能精确存储444.5或0.32这样的数字
* real,double precision：浮点数与双精度浮点数，精度与机器有关
* float(n)：精度至少为ｎ位的浮点数
* 每种类型都可能包含一个被称作空值的特殊值
> 空值表示一个缺失的值
