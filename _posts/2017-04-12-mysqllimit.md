---
date: 2017-04-12 12:34:56+00:00
layout: post
title: MySQL中limit用法
categories: Emulate
tags: Emulate MySQL
---

### 目录

1. [limit双参数](#item1)
2. [limit单参数](#item2)

---
#### <span id="item1">limit双参数</span>
> limit 偏移量，最大数目
>> select * from tablename limit 5,6;
>> 
>> 取出第6到11条记录
> 
> limit 常与order by连用，先排序，再取出指定位置的记录
>> select * from tablename order by 字段名 limit 5,6;


#### <span id="item2">limit单参数</span>
> limit 最大数目
> 
> 等价于：limit 0,最大数目
>> select * from tablename limit 6;
>>
>> 取出前6条记录

