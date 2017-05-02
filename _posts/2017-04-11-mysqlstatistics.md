---
date: 2017-04-11 13:47:17+00:00
layout: post
title: MySQL中常用统计函数
categories: Emulate
tags: Emulate MySQL
---

### 目录

1. [count](#step1)
2. [avg](#step2)
3. [sum](#step3)
4. [max and min](#step4)
5. [使用注意事项](#step5)

---
#### <span id="step1">count</span>
> 使用count统计条数
>> select count(*) from tablename

#### <span id="step2">avg</span>
> 使用avg计算字段的平均值
>> select avg(字段名) from tablename

### <span id="step3">sum</span>
> 使用sum求和
>> select sum(字段名) from tablename

### <span id="step4">max and min</span>
> 使用max和min求最大值和最小值
>> select max(字段名) from tablename
>>
>> select min(字段名) from tablename

### <span id="step5">使用注意事项</span>
> 使用上述函数时，如果数据库中没有数据时，count函数返回0，其他函数返回NULL