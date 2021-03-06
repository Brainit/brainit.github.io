---
date: 2017-04-10 14:37:17+00:00
layout: post
title: MySQL中insert操作
categories: Emulate
tags: Emulate MySQL
---

### 目录

1. [insert指定列](#item1)
2. [insert所有列](#item2)
3. [数字与字符串](#item3)
4. [自增长属性值的指定](#item4)

---
#### <span id="item1">insert指定列</span>
> insert into 表名 (属性1,属性2,...) values (值1，值2，...); 
> 
> 增加一条记录，指定这条记录中属性1,属性2...，记录值为值1,值2,...

#### <span id="item2">insert所有列</span>
> insert into 表名 (属性1,属性2,...) values (值1,值2,...)
> 
> 增加一条记录，并为这条记录的所有属性添加值
> 
> 可以简写为insert into 表名 values (值1,值2,...)
> 
> 其中值的顺序必须与表结构相同

#### <span id="item３">数字与字符串</span>
> 在属性值为数字的时候，可以省略掉‘’，例如，年龄为数字，可以使用20，也可以使用'20';
> 
> 在属性值为字符的时候，不能省略掉'',例如姓名为字符串，必须使用'张三'，而不能使用张三;

#### <span id="item4">自增长属性值的指定</span>
> insert指定列的时候，自增长的属性可以不指定，也可以手动指定；
> 
> insert所有列的时候，如果声明了属性的时候，就必须指定自增至属性的值，可以省略自增至属性，insert指定列完成所有列的添加;
> 
> insert所有列的时候，如果使用简写（不声明属性）的时候，就必须指定自增长属性的值