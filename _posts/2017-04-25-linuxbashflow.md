---
date: 2017-04-25 16:13:56+00:00
layout: post
title: Bash流程控制语句
categories: Emulate
tags: Emulate Linux
---

### 目录

1. [if语句](#item1)
2. [if-else语句](#item2)
3. [if-elseif-else语句](#item3)
4. [for语句](#item4)
5. [while语句](#item5)
6. [util语句](#item6)
7. [case语句](#item7)
8. [跳出循环-break](#item8)
9. [跳出当前循环-continue](#item9)
10. [几种无限循环](#item10)

---
#### <span id="item1">if语句</span>
> 
> 命令格式
```
if condition
then
    command1 
    command2
    ...
    commandN 
fi
```
> 命令例子
```
#!/bin/bash
a=9
b=10
if [ $a -lt $b ]
then
        echo "a小于b"
fi
```
> 单行命令
```
if [ $a -lt $b ]; then echo "a小于b";fi 
```

#### <span id="item2">if-else语句</span>
> 
> 命令格式
```
if condition
then
    command1 
    command2
    ...
    commandN
else
    command
fi
```
> 命令例子
```
a=9
b=10
if [ $a -lt $b ]
then
        echo "a小于b"
else
	echo "a大于b"
fi
```
#### <span id="item3">if-else-if-else语句</span>
> 
> 命令格式
```
if condition1
then
    command1
elif condition2 
then 
    command2
else
    commandN
fi
```
> 命令例子
```
#!/bin/bash
a=9
if [ $a -eq 9 ]
then
        echo "a等于9"
elif [ $a -lt 9]
then
        echo "a小于9"
else
        echo "a大于9"
fi
```

#### <span id="item4">for语句</span>
> 
> 命令格式
```
for var in item1 item2 ... itemN
do
    command1
    command2
    ...
    commandN
done
```
> 写成一行
```
for var in item1 item2 ... itemN; do command1; command2… done;
```
> 命令例子
```
#!/bin/bash
dirs=`ls`
for dir in $dirs
do
        echo "列举每个文件:$dir"
done
```

#### <span id="item5">while语句</span>
> 
> 命令格式
```
while condition
do
    command
done
```
> 命令例子
```
#!/bin/bash
int=1
while(( $int<=5 ))
do
        echo $int
        let "int++"
        #let命令用于执行一个或多个表达,变量计算中不需要加$式
done
```

#### <span id="item6">util语句</span>
> 
> 命令格式
```
until condition
do
    command
done
```

#### <span id="item7">case语句</span>
>　
> 命令格式
```
case 值 in
模式1)
    command1
    command2
    ...
    commandN
    ;;
模式2）
    command1
    command2
    ...
    commandN
    ;;
esac
```
> 命令例子
```
#!/bin/bash
echo '输入 1 到 4 之间的数字:'
echo '你输入的数字为:'
read aNum
case $aNum in
    1)  echo '你选择了 1'
    ;;
    2)  echo '你选择了 2'
    ;;
    3)  echo '你选择了 3'
    ;;
    4)  echo '你选择了 4'
    ;;
    *)  echo '你没有输入 1 到 4 之间的数字'
    ;;
esac
```

#### <span id="item8">跳出循环-break</span>
> 在循环结构，for,while和util循环中，如果想在循环体中结束循环，就使用break命令跳出循环

#### <span id="item9">跳出当前循环-continue</span>
> 在循环结构，for,while和util循环中，如果想要在循环体中结束当前循环体，快速进入下一次循环，就使用continue命令

#### <span id="item10">几种无限循环</span>
> 使用while无限循环
```
while :
do
    command
done
```
> 另外一种while无限循环
```
while true
do
    command
done
```
> 使用for无限循环
```
for (( ; ; ))
```