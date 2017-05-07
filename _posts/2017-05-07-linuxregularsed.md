---
date: 2017-04-25 16:13:56+00:00
layout: post
title: 正则表达式-sed工具
categories: Emulate
tags: Emulate Linux
---

### 目录

1. [sed用法](#step1)
2. [新增](#step2)
3. [替换-以行为单位](#step3)
4. [删除](#step4)
5. [插入](#step5)
6. [打印](#step6)
7. [替换-以字符为单位](#step7)
8. [直接修改文件](#step8)

---
#### <span id="step1">sed用法</span>
```bash
sed [-nefr] [动作]

参数
[-n]:使用安静模式，只有经过sed特殊处理的那一行才会被列出来
[-e]:直接在命令行模式上进行sed的动作编辑
[-f]:直接将sed的动作写在一个文件内，-f filename则可以执行filename内的sed动作
[-r]:sed的动作支持的是拓展型正则表达式的语法（默认是基础正则表达式语法）
[-i]:直接修改读写的文件内容，而不是由屏幕输出

动作说明 [n1[,n2]]function
n1,n2:不见得会存在，一般代表选择进行动作的行数，举例来说，如果我的动作需要在10-20行之间进行，则"10,20[动作行为]"

function说明
a:新增，a后面可以接字符串，而这些字符串会在新的一行出现（目前行的下一行）
c:替换，c的后面可以接字符串，替换n1到n2之间的行
d:删除，后面不需要接任何参数
i:插入，i的后面接字符串，而这些字符串会出新的一行出现（目前航的下一行）
p:打印，也就是将某个选择的数据打印出来，通常p会与参数sed -n一起运行
s:替换，可以直接进行替换工作，通常这个s的动作可以搭配正则表达式
```

#### <span id="step2">新增</span>
增加一行，在第二行后增加字符the word appened
```
nl /etc/passwd | sed '2a the word appened'
```
增加多行
```
nl /etc/passwd | sed '2a the first line appened \
the second line appened \
the third line appened'
```

#### <span id="step3">替换-以行为单位</span>
替换10-20行内容
```
nl /etc/passwd | sed '10,20c the word instead'
```

#### <span id="step4">删除</span>
删除10-20行的内容
```
nl /etc/passwd | sed '10,20d'
```

#### <span id="step5>插入</span>
```
nl /etdc/passwd | sed '3i the word inserted'
```

#### <span id="step6">打印</span>
在安静模式下打印3到5行
```
nl /etc/passwd | sed -n '3,5p'
```

#### <span id="step7">替换-以字符为单位</span>
基本格式
```
sed 's/要替换的字符串/新的字符串/g'
```

通过正则表达式取出ip
```
ifconfig eth0 | grep 'inet addr' | sed 's/^.*addr://g' | sed 's/Bcast.*$//g'
```

#### <span id="step8">直接修改文件</span>
sed中i参数能直接修改文件，例如在文末增加行
```
sed -i '$a 这是在文末增加的内容'
```
