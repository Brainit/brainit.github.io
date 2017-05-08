---
date: 2017-04-25 15:13:56+00:00
layout: post
title: Bash中echo命令
categories: Emulate
tags: Emulate Linux
---

### 目录

1. [显示普通字符串](#item1)
2. [显示转义字符](#item2)
3. [显示变量](#item3)
4. [显示换行](#item4)
5. [显示不换行](#item5)
6. [显示结果定向至文件](#item6)
7. [原样显示字符串，不进行转义或取变量（用单引号）](#item7)
8. [显示命令执行结果](#item8)

---
#### <span id="item1">显示普通字符串</span>
> 
```
echo "字符串"
```

#### <span id="item2">显示转义字符</span>
>　
```
echo "用转义字符显示\""
```

#### <span id="item3">显示变量</span>
> 
```
name="小脑IT"
echo "我的名字是$name"
```

#### <span id="item4">显示换行</span>
>　
```
firstline="这是第一行"
secondline="这是第二行"
#使用\n转义字符显示换行
echo "${firstline}\n${secondline}"
```

#### <span id="item5">显示不换行</span>
> 
```
firstline="这是第一行"
secondline="这是第二行"
#使用\c转义字符显示不换行
echo "${firstline}\c${secondline}"
```

#### <span id="item6">显示结果定向至文件</span>
>　
```
string="输出字符"
#输出到文件，如果filename.txt不存在就新建，并输出到文件
#如果filename.txt存在就清空文件，并输出
echo "$string" > filename.txt
#输出到文件，以追加的方式输出到文件
echo "$string" >> filename.txt
```

#### <span id="item7">原样显示字符串，不进行转义或取变量（用单引号）</span>
>　
```
name="小脑IT"
#使用单引号，将不会对转义字符进行转义，变量将不会取出变量
echo '$name　　\"  '
#输出结果为　$name　　\"  
```

#### <span id="item8">显示命令执行结果</span>
>　
```
#先执行date命令，再将结果输出
echo `date`
```