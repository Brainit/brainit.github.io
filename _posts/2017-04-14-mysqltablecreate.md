---
date: 2017-04-14 14:48:56+00:00
layout: post
title: MySQL建表过程及完整性约束
categories: Emulate
tags: Emulate MySQL
---

### 目录

1. [MySQL建表过程](#step1)
2. [完整性约束-主键约束](#step2)
3. [完整性约束-外键约束](#step3)
4. [完整性约束-notNULL](#step4)
5. [完整性约束-唯一性约束](#step5)
6. [完整性约束-自动增加](#step6)
7. [完整性约束-默认值](#step7)

---
#### <span id="step1">MySQL建表</span>
> 用**create table**命令创建表。create table命令的通用形式:
>> create table **r**
(A1 D1,
A2 D2,
...,
An Dn,
完整性约束1,
...,
>> 完整性约束n);
> 
> 其中r是表名，每个A表示表的属性名，D是属性名的域，也就是说D指定了属性A的类型以及可选的约束，用于限制所允许的A取值的集合


#### <span id="step2">完整性约束-主键约束</span>
> 主键能够标识表中每条信息的唯一性，创建主键的目的在于快速查找表中的某一条信息。
使用primary key声明主键：primary key(A<sub>m1</sub>,A<sub>m2</sub>,...,A<sub>mn</sub>)
> 1. 单字段主键:
>> create table r
(A1 D1 **primary key**,
A2 D2,
...,
An Dn,
完整性约束1,
...,
>> 完整性约束n);
>> 
>> 声明字段A1为主键 
> 2. 多字段主键：
>> create table r
(A1 D1,
A2 D2,
...,
An Dn,
primary key(A<sub>m1</sub>,A<sub>m2</sub>,...,A<sub>mn</sub>),
完整性约束2,
...,
>> 完整性约束n);
>>
>> 声明字段A<sub>m1</sub>,A<sub>m2</sub>,...,A<sub>mn</sub>为主键,单字段主键也可以通过这种方式声明
> 
> 3. 主码必须是非空且唯一的。

#### <span id="step3">完整性约束-外键约束</span>
> 表的外键与主键是相对应的，比如表A的id是外键，表B中的id是主键，那么就可以称表B为父表，表A为子表。
设置表外键的作用在于建立与父表的联系，比如表B中id为123的学生删除后，表A中id为123的记录也随着消失。
建立外键使用foreign key声明
>> create table r
(A1 D1,
A2 D2,
...,
An Dn,
**constraint fk foreign key(id,course_id) references table2(id,course_id)**,
完整性约束2,
...,
>> 完整性约束n);
> 
> 创建表r，constraint后面的fk是外键别名，foreign key也就是设置外键的字段，referrences后面的内容表示父表，和父表中的主键
> 
> 需要注意的是父表中的主键不能为空，并且主键与外键的数据类型要一致


#### <span id="step4">完整性约束-notNULL</span>
> 一个属性上的not null约束表明在该属性上不允许空值
>> create table r
(A1 D1 **not null**,
A2 D2,
...,
An Dn,
完整性约束1,
...,
>> 完整性约束n);
> 
> 创建表r，申明A1字段not null表明A1字段不允许为空


#### <span id="step5">完整性约束-唯一性约束</span>
> 唯一性是指表中该字段的值不能重复出现，设置表的唯一性约束
> 申明字段的唯一性约束使用unique
>> create table r
(A1 D1 **unique**,
A2 D2,
...,
An Dn,
完整性约束1,
...,
>> 完整性约束n);
> 
> 创建表r，并声明字段A1不能重复


#### <span id="step6">完整性约束-自动增加</span>
> auto_increment主要用于为表中插入的新记录自动生成唯一的ID
> 
> 一个表只能有一个字段使用auto_increment约束
> 
> 并且该字段必须为主键的一部分
>> create table r
(A1 D1 **auto_increment**,
A2 D2,
...,
An Dn,
完整性约束1,
...,
>>完整性约束n);
> 
> 创建表r，并声明表中字段A1为自增


#### <span id="step7">完整性约束-默认值</span>
> 增加记录的时候，如果没增加某些字段的信息，就使用默认值，可以使用default修改某些字段的默认值
>> create table r
(A1 int **default 20**,
A2 D2,
...,
An Dn,
完整性约束1,
...,
>> 完整性约束n);
> 
> 创建表r，声明表中字段A1的类型为int类型，并且默认值为20，增加记录的时候如果没有A1字段的信息，将默认使用20。