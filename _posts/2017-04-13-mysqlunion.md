---
date: 2017-04-13 14:48:56+00:00
layout: post
title: MySQL中UNION 与 UNION ALL用法简述
categories: Emulate
tags: Emulate MySQL
---

### 目录

1. [UNION语法](#item1)
2. [UNION 与 UNION ALL 的区别](#item2)
3. [MySQL UNION 用法实例](#item3)
4. [UNION 查询结果说明](#item4)
5. [效率分析](#item5)

---
#### <span id="item1">UNION语法</span>
> MySQL UNION 用于把来自多个 SELECT 语句的结果组合到一个结果集合中。
>> SELECT column,... FROM table1 
>> 
>> UNION [ALL]
>> 
>>SELECT column,... FROM table2
>>
>> ...
> 在多个 SELECT 语句中，对应的列应该具有相同的字段属性，且第一个 SELECT 语句中被使用的字段名称也被用于结果的字段名称。 


#### <span id="item2">UNION 与 UNION ALL 的区别</span>
> 当使用 UNION 时，MySQL 会把结果集中重复的记录删掉，而使用 UNION ALL ，MySQL 会把所有的记录返回，且效率高于 UNION。 

#### <span id="item3">MySQL UNION 用法实例</span>
> UNION 常用于数据类似的两张或多张表查询，如不同的数据分类表，或者是数据历史表等。
> 
>> select a,b from TA UNION select a,b from TB;

#### <span id="item4">UNION 查询结果说明</span>
> 
1. 重复记录是指查询中各个字段完全重复的记录，如上例，若 title 一样但 id 号不一样算作不同记录。
2. 第一个 SELECT 语句中被使用的字段名称也被用于结果的字段名称，如上例的 aid。
3. 各 SELECT 语句字段名称可以不同，但字段属性必须一致。
> 

#### <span id="item5">效率分析</span>
> 使用UNION ALL时，只是将所有的查询结果组合到一起，而不会去判断数据是否重复。
> 
> 因此当确定查询结果中不会右重复数据或则不需要去掉重复数据的时候，应当使用UNION ALL以提高查询效率