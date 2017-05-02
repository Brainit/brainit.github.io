---
date: 2017-04-10 14:47:17+00:00
layout: post
title: MySQL中update操作
categories: Emulate
tags: Emulate MySQL
---

### 目录

1. [update核心](#step1)
2. [update命令](#step2)

---
#### <span id="step1">update核心</span>
> update是MySQL中进行记录更新操作的命令
> 
> 核心1： 需要更新的表名
> 
> 核心2： 需要更新的属性名（字段名）
> 
> 核心3： 这些属性的属性值
> 
> 核心4： 更改哪些列

#### <span id="step2">update命令</span>
> update 表名 set 字段1=值1,字段2=值2 where 条件;
