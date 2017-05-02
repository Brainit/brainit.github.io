---
date: 2017-04-10 15:07:17+00:00
layout: post
title: MySQL中select操作
categories: Emulate
tags: Emulate MySQL
---

### 目录

1. [sleect核心](#step1)
2. [select查询过程](#step2)
3. [select查询命令](#step3)


---
#### <span id="step1">update核心</span>
> select是MySQL中进行记录查找操作的命令
> 
> 核心1： 需要进行查找操作的表名
> 
> 核心2： 查找到的记录返回的结果中的字段名
> 
> 核心3： 查找哪些列，即条件，表达式的值为真假，特殊的1为真，0为假

#### <span id="step2">select查询过程</span>
> 针对每一条记录，如果当前记录满足条件，则将当前记录中字段按照需要查找的字段返回
> 
> 列是变量，变量能进行计算，即能对核心2进行操作并返回，例如对数字进行数学运算，对字符串进行追加等

#### <span id="step3">select查询命令</span>
> select * from 表名
>> 查询表中所有数据 
> 
> select * from 表名 where 条件
>> 查询表中指定条件的字段，并将这些记录的数据全部返回
> 
> select 字段1,字段2,... from 表名 where 条件
>> 查询表中指定条件下的数据，并将满足条件的记录中指定字段的数据返回
> 
> select 字段1/100，字段2+'追加',... from 表名 where 条件
>> 查询表中指定条件下的数据，并将满足条件的记录中指定字段的数据进行运算之后返回，注意，只能进行相应数据类型的运算
> 