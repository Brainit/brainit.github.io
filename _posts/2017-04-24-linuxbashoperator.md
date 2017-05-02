---
date: 2017-04-24 15:34:56+00:00
layout: post
title: Linux运算符
categories: Emulate
tags: Emulate Linux
---

### 目录

1. [算数运算符](#step1)
2. [关系运算符](#step2)
3. [布尔运算符](#step3)
4. [字符串运算符](#step4)
5. [文件测试运算符](#step5)

---
#### <span id="step1">算术运算符</span>
> 
|运算符|说明|
|:-----|:-------|
|+|加法|
|-|减法|
|*|乘法|
|/|除法|
|%|取余|
|=|赋值|
|==|相等，用于比较两个数字|
|!=|不相等，用于比较两个数字|

```
#!/bin/bash
a=15;
b=2;
#a+b,expr 是一款表达式计算工具，使用它能完成表达式的求值操作
jiafa=`expr $a + $b`
#a-b
jianfa=`expr $a - $b`
#a*b，需要注意的是乘法需要进行转义操作
chengfa=`expr $a \* $b`
#a/b
chufa=`expr $a / $b`
#a%b
quyu=`expr $a % $b`
#判断,注意[]和表达式之间一定要有空格
if [ $a == $b ]
then
	echo "a等于b"
fi
```
#### <span id="step2">关系运算符</span>
> 
|运算符|说明|
|:-----|:-------|
|-eq|检测两个数是否相等，相等返回true|
|-ne|检测两个数是否相等，不相等返回true|
|-gt|检测左边的数是否大于右边的，如果是，则返回true|
|-lt|检测左边的数是否小于右边的，如果是，则返回true|
|-ge|检测左边的数是否大于等于右边的，如果是，则返回true|
|-le|检测左边的数是否小鱼等于右边的，如果是，则返回true|

```
#!/bin/bash
a=10
b=20
if [ $a -eq $b ]
then
   echo "$a -eq $b : a 等于 b"
else
   echo "$a -eq $b: a 不等于 b"
fi
#其他用法相同
```

#### <span id="step3">布尔运算符</span>
> 
|运算符|说明|
|:-----|:-------|
|!|非运算，表达式为true则返回false，否则返回true|
|-o|或运算，有一个表达式为true则返回true|
|-a|与运算，两个表达式都为true才返回true|
|&&|逻辑与|
|&#124;&#124;|逻辑或|

```
#!/bin/bash
a=10
b=20
if [ $a -lt 100 -a $b -gt 15 ]
then
	echo "true"
else
	echo "false"
fi
#其他用法同上述例子-a
```

#### <span id="step4">字符串运算符</span>
> 
|运算符|说明|
|:-----|:-------|
|=|双目运算符，检测两个字符串是否相等，相等返回true|
|!=|双目运算符，检测两个字符串是否相等，不相等则返回true|
|-z|单目运算符，检测字符串长度是否为０，为０则返回true|
|-n|单目运算符，检测字符串长度是否为０，不为０则返回true|
|str|单目运算符，检测字符串是否为空，不为空则返回true|


```
#!/bin/bash
a="234"
b="abc"
#比较运算符不再说明
if [ -z $a ]
then 
	echo "长度为０"
fi

if [ -n $a ]
then 
	echo "长度不为０"
fi

if [ $a ]
then 
	echo "字符串不为空"
fi
```

#### <span id="step5">文件测试运算符</span>
> 
|运算符|说明|
|:-----|:-------|
|-b file|检测文件是否是块设备文件，如果是就返回true|
|-c file|检测文件是否是设备文件，如果是就返回true|
|-d file|检测文件是否是目录，如果是就返回true|
|-f file|检测文件是否是普通文件（既不是目录也不是设备文件）|
|-g file|检测文件是否设置了SGID位，如果是就返回true|
|-k file|检测文件是否设置了粘着位(Sticky Bit)，如果是就返回true|
|-p file|检测文件是否是有名管道，如果是就返回true|
|-u file|检测文件是否设置了SUID,如果是就返回true|
|-r file|检测文件是否可读，如果是就返回true|
|-w file|检测文件是否可读，如果是就返回true|
|-x file|检测文件是否可执行，如果是就返回true|
|-s file|检测文件是否为空（如果文件大小为０，则为空）,不为空就返回true|
|-e file|检测文件（包括目录）是否存在，如果是就返回true|

```
#!/bin/bash
file="/root/test.sh"
if [ -r file ]
then 
	echo "可读文件"
fi
#其他测试同上
```