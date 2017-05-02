---
date: 2017-04-15 16:23:56+00:00
layout: post
title: MySQL视图及简单操作
categories: Emulate
tags: Emulate MySQL
---

### 目录

1. [视图](#step1)
2. [视图的作用](#step2)
3. [视图的创建](#step3)
3. [视图与表一对一](#step4)
4. [视图与表一对多](#step5)

---
#### <span id="step1">视图</span>
> 视图是从一个或多个表中导出来的表，是一种虚拟存在的表。
> 
> 通俗的讲，视图就是一条select语句执行后返回的结果集。所以我们在创建视图的时候，主要的工作就落在创建这条SQL查询语句上。

#### <span id="step2">视图的作用</span>
> 1. 使操作简单化，可以对经常使用的查询定义一个视图，使用户不必为同样的查询操作指定条件。
2. 增加数据的安全性，通过视图，用户只能查询和增删改指定的数据。
3. 提高表的逻辑独立性，视图可以屏蔽原来表结构变化带来的影响
> 

#### <span id="step3">视图的创建</span>
> 视图的创建语句：
>> CREATE [ALGORITHM]={UNDEFINED|MERGE|TEMPTABLE}]
>>
>> VIEW 视图名 [(属性清单)]
>>
>> AS SELECT语句
>>
>> [WITH [CASCADED|LOCAL] CHECK OPTION];
> 
> 1. 其中ALGORITHM表示视图选择的算法（可选参数）：
>> UNDEFINED：MySQL将自动选择所要使用的算法
>> 
>> MERGE：将视图的语句与视图定义合并起来，使得视图定义的某一部分取代语句的对应部分
>> 
>> TEMPTABLE：将视图的结果存入临时表，然后使用临时表执行语句
> 2. 视图名表示要创建的视图的名称
> 3. 属性清单表示视图中的列名，如果不指定，默认与select查询结果中的列名相同（可选参数）
> 4. WITH CHECK OPTION表示更新视图时要保证在该视图的权限范围之内（可选参数）
>> CASCADED： 更新视图时要满足所有相关视图和表的条件
>>
>> LOCAL：更新视图时，要满足视图本身定义的条件即可
> 
> TIPS：创建视图时最好加上WITH CASCAEDED CHECK OPTION参数，这种方式比较严格，可以保证数据的安全性


#### <span id="step4">视图与表一对一</span>
> 视图的select语句的数据来源于一张表，例如
>> create view view_user
>> 
>> as 
>> 
>> select name,password 
>> 
>> from user u
> 
> 视图与表是一对一关系情况：如果没有其他约束（如视图中没有的字段必须NOT NULL），能对视图进行**增删改**操作。
> 
> insert操作
>> insert into view_user values('name','123');
> 
> delete操作
>> delete from view_user where name='name';
> 
> update操作
>> update view_user set password='456' where name='name';

#### <span id="step5">视图与表一对多</span>
> 视图的select语句的数据来源与多张表，例如
>> create view view_user_comment
>>
>> as 
>> 
>> select user.name,user.password,comment.counter
>> 
>> from user left join comment on user.id=comment.id
> 
> 视图与表是一对多关系情况：如果值修改一张表的数据，且没有其他约束（如视图中没有的字段必须NOT NULL），是可以进行**改**操作的，其他操作(增删操作)都将失败
> 
> update操作
>> 成功执行：
>> 
>> update view_user_comment set password='456' where name='name';
>> 
>> 失败执行：
>> 
>> update view_user_comment set password='456',counter=0 where name='name';
>> 
>> 同时修改两张表（user和comment）的数据，所以操作失败
> 

