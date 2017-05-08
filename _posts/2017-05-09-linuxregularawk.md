---
date: 2017-05-09 14:56:56+00:00
layout: post
title: 正则表达式-awk工具
categories: Emulate
tags: Emulate Linux
---

### 目录

1. [awk用法](#step1)
2. [awk执行过程](#step2)
3. [awk特殊变量说明](#step3)
4. [awk逻辑运算符](#step4)
5. [awk示例](#step5)

---
#### <span id="step1">awk用法</span>
awk是一个非常棒的数据处理工具，相比于sed常常作用于一整行的处理，awk则比较倾向于将一行分成数个字段来处理。
```script
awk '条件类型1{动作1}条件类型2{动作2}...' filename
```
awk主要是处理每一行的字段内的数据，而默认的字段的分隔符为空格键或[TAB]键
#### <span id="step2">awk执行过程</span>
```script
$0代表当前行
$1-$n代表
```
* 读入第一行，并将第一行的数据填入$0,$1,...等变量中
* 依据条件类型的限制，判断是否需要进行后面的动作
* 做完所有的动作与条件类型
* 若还有后面的行的数据，重复上面的三步，直到所有数据都读完为止

#### <span id="step3">awk特殊变量说明</span>
```script
NF	:每一行拥有的字段总数
NR	:目前akw所处理的是“第几行”的数据
FS	:目前的分隔符，默认是空格键
```

#### <span id="step4">awk逻辑运算符</span>
```script
>	:大于
<	:小于
>=	:大于等于
<=	:小于等于
==	:等于
!=	:不等于
```

#### <span id="step5">awk示例</span>
使用awk命令显示本机账户与登陆者IP
```script
last -n 5 | awk '{printf $1 "\t" $3}'
```
需要注意的是特殊变量使用过程不需要用$符号引用
```script
last -n 5 | awk '{printf "当前是第" NR "行。当前行的分隔符是：" FS }'
```
条件类型的使用
```script
last -n 5 | awk 'NR==1{printf "当前是第一行"}'
```
等同于
```script
last -n 5 | awk '{if(NR==1) printf "当前是第一行"}'
```
awk预设值
```script
cat /etc/passwd | awk '{FS=":"}'
默认的分隔符为空格，如果这样设置，分隔符设置为：需要在第二行才开始生效
cat /etc/passwd | awk 'BEGIN{FS=":"}'
使用BEGIN关键字，进行预设值，能让分隔符在第一行就生效
同样，还有END关键字
```

