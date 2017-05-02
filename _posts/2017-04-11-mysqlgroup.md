---
date: 2017-04-11 14:20:17+00:00
layout: post
title: MySQL中group分组的使用
categories: Emulate
tags: Emulate MySQL
---

### 目录

1. [group by使用](#step1)
2. [组合使用](#step2)
3. [group by的条件](#step3)

---
#### <span id="step1">group by使用</span>
> 使用group by对数据进行分组
>> select 字段名1 from tablename group by 字段名2

#### <span id="step2">组合使用</span>
> 实际中常常将分组group by和排序，统计函数组合使用
>> select 字段名1 from tablename group by 字段名2 order by 字段名3 [desc/asc]
>> 
>> select 统计函数 from tablename group by 字段名1
>>
>> 以及排序和统计函数的组合使用

### <span id="step3">group by的条件</span>
> 如果在分组查询中加入条件，则必须使用having，而不是where
>> select 字段名1 from tablename group by 字段名2 having 条件
> 
> 如果要同时使用条件分组并排序，则order by必须位于having 之后
>> select 字段名1 from tablename group by 字段名2 having 条件 order by 字段名3 [desc/asc]
