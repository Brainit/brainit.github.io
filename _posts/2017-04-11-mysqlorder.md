---
date: 2017-04-11 14:40:17+00:00
layout: post
title: MySQL中对字段进行排序order by
categories: Emulate
tags: Emulate MySQL
---

### 目录

1. [order by简单应用](#item1)
2. [多字段综合排序](#item2)

---
#### <span id="item1">order by简单应用</span>
> 使用order by对字段进行排序操作
>> 默认为升序
>> select 字段名1 from tablename order by 字段名2
>> 
>> 相当于select 字段名1 from tablename order by 字段名2 asc
> 使用DESC对字段进行降序排序
>> select 字段名1 from tablename order by 字段名2 DESC


#### <span id="item2">多字段综合排序</span>
> 很多时候需要同时考虑多个字段进行排序，如果字段1相同就按照字段2进行排序，这时候就需要使用多字段综合排序
>> select 字段名1 from tablename order by 字段名2，字段名3
>>
>> 先按照字段2进行排序，如果字段2的值相同，就按照字段3进行排序
>>
>> 多字段默认所有字段都为升序，如果需要指定每个字段的升降序，需要对每个字段单独指定
>>
>> select 字段名1 from tablename order by 字段名2 DESC, 字段名3 ASC,字段名4 DESC

