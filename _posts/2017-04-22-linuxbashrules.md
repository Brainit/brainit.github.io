---
date: 2017-04-22 15:24:56+00:00
layout: post
title: Linux变量的设置规则
categories: Emulate
tags: Emulate Linux
---

### Linux变量的设置规则

1. 变量与变量内容以一个等号来联接
```
myname=brainit
```
2. 等号两边不能直接接空格符
```
#正确示例
myname=brainit
#错误示例
myname=brainit brainit
```
3. 变量名只能是英文字母与数字，但是开头字符不能是数字
```
#错误示例
2myname=brainit
```
4. 变量名若有空格符可以使用双引号""或单引号''将变量内容结合起来<br />
双引号内的特殊符号，如$，可以保有原来的特性<br />
```
var="show the path: $PATH"
```
单引号内的特殊符号仅为一般字符（纯文本）
```
var='show the charator &'
```
5. 可用转义字符'\'将特殊符号（如[Enter],$,\,空格符,!等）变成一般字符
6. 在一串命令中，还需要通过其他的命令提供的信息，可以使用单反引号``或则$(命令)。
```
var=$(ls)
var=`ls`
#先执行ls命令，再将命令结果作为变量内容赋值给var变量
```
7. 若变量为了增加变量内容时，则可用"$变量名称"或${变量名称}累加内容
```
PATH=${PATH}:/home/bin
PATH="$PATH":/home/bin
```
8. 若变量需要在其他子进程执行，则需要以export来使变量变成环境变量
```
export PATH
```
9. 通常大写字符为系统默认变量，自行设置变量可以使用小写字符。
10. 取消变量的方法可以使用unset　变量名称
```
unset myname
```