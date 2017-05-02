---
date: 2017-04-12 14:48:56+00:00
layout: post
title: MySQL中子查询整理
categories: Emulate
tags: Emulate MySQL
---

### 目录

1. [什么是子查询](#step1)
2. [子查询的好处](#step2)
3. [where子查询](#step3)
4. [from子查询](#step4)
5. [exists子查询](#step5)

---
#### <span id="step1">什么是子查询</span>
> 当一个查询是另外一个查询的条件时，称之为子查询

#### <span id="step2">子查询的好处</span>
> 子查询可以使用几个简单命令构造功能强大的复合命令

#### <span id="step3">where子查询</span>
> where子查询就是将内层查询的结果当做外层查询你的条件
>> select * from tablename1 where 字段名=(**select max(字段名) from tablename2**); 

#### <span id="step4">from子查询</span>
> from子查询就是将内层查询的结果做外一张临时表，然后再对他进行处理
>> select tmp.字段名1,,tmp.字段名2 from (**select * from tablename**) as tmp;

#### <span id="step5">exists子查询</span>
> exists子查询就是对外层表进行循环，再对内标进行内层循环。
> 
> 和in()差不多，但是他们的还是有区别的。主要是看两张表大小差的程度。如果子查询表大则用exists(内层索引),子查询表小则用in（外层索引）。
> 
> exists用于检查子查询是否至少会返回一行数据，该子查询实际上并不返回数据，而是返回值true或false。
> exists指定一个子查询，检测行的存在。语法：exists subquery。参数subquery是一个受限的select语句（不允许compute子句和into关键字）。结果类型为boolean类型，如果子查询包含行，则返回true。
>> select * from tablename a where **exists( select 字段名 from tablename b where 条件)**;
>> 
>> 使用in进行转换: select * from tablename a where a.字段 **in(select b.字段 from tablename b where 条件)**;