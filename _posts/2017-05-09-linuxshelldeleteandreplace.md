---
date: 2017-05-09 16:56:56+00:00
layout: post
title: shell变量内容的删除与替换
categories: Emulate
tags: Emulate Linux
---

### 目录

1. [shell变量内容的删除](#item1)
2. [shell变量内容的替换](#item2)

---
#### <span id="item1">shell变量内容的删除</span>
```
${var#str}　　 			# 从左向右，删除最小的匹配段
${var##str}　　			# 从左向右，删除最大的匹配段
${var%str}　　			# 从右往左，删除最小的匹配段
${var%%str}　　			# 从右往左，删除最大的匹配段
${var/oldStr/newStr}　　	# 从左向右，替换第一个匹配的oldstr为newstr
${var//oldStr/newstr}　　	# 从左向右，替换所有匹配的oldstr为newstr
```
常通过通配符匹配str进行删除操作

#### <span id="item2">shell变量内容的替换</span>
```
var=${str-content}　　	# 如果str没有设置值，var=content，否则var=str
var=${str:-content}　　	# 如果str没有设置值或者str为空，var=content，否则var=str
var=${str+content}　　	# 如果str没有设置值，var= ，否则var=content
var=${str:+content}　　	# 如果str没有设置值或者str为空，var= ，否则var=content
var=${str=content}　　	# 如果str没有设置值，var=str=content ，否则var=content
var=${str:=content}　　	# 如果str没有设置值或者str为空，var=str=content ，否则var=content
var=${str?content}　　	# 如果str没有设置值，content输出到stderr ，否则var=str
var=${str:?content}　　	#如果str没有设置值或者str为空，content输出到stderr ，否则var=str
```
