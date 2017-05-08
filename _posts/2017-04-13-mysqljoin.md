---
date: 2017-04-13 12:48:56+00:00
layout: post
title: MySQL内联接（自然连接），左联接，右链接，完全链接
categories: Emulate
tags: Emulate MySQL
---

### 目录

1. [内联接](#item1)
2. [外联接](#item2)
3. [左联接](#item3)
4. [右联接](#item4)
5. [完全联接](#item5)

---
#### <span id="item1">内联接</span>
> 内联接（典型的联接运算，使用像=或<>之类的比较运算符）
> 
> 包括相等联接和自然联接。
> 
> 内联接使用比较运算符根据每个表共有的列的值匹配两个表中的列
>> select A.*,B.* from A inner join B on A.字段1=B.字段2;
> 
> 
>> 使用自然联接对内联接进行转换：
>> 
>> select A.*,B.* from A,B where A.字段1=B.字段2;
> 
>> 自然联接等价于使用cross join(笛卡尔积)：
>> 
>> select * from A cross join B;


#### <span id="item2">外联接</span>
> 外联接可以是左向外联接（left join或则left outer join）、右向外联接(right join或则right outer join)或完整外部联接(full join或则full outer join)。


#### <span id="item3">左联接</span>
> 返回左边表中所有被查询的字段+右边表中符合条件的字段
> 
> A表包容B表，左联接左表的所有记录被保留
>> select A.*,B.* from A left join B on A.字段1=B.字段2;

#### <span id="item4">右联接</span>
> 返回右边表中所有被查询字段+左边表中符合条件的字段。
> 
> B表保留A表，右联接右表的所有记录被保留。
>> select A.*,B.* from A right join B on A.字段1=B.字段2;

#### <span id="item5">完全联接</span>
> 返回参与联接的两个数据集的全部数据，无论它们是否具有与之相匹配的行。
> 
> 等价于：对这两个数据集合分别进行左外联和右外联，然后再使用消去重复行的并操作将上述两个结果集合合并为一个结果集
>> select * from A full join B;
> 
> 注：MySQL不支持完全联接