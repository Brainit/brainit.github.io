---
date: 2017-04-05 14:16:17+00:00
layout: post
title: Linux文件权限
categories: Emulate
tags: Emulate Linux
---

### 目录
1. [Linux文件属性](#step1)
2. [文件权限与属性的修改](#step2)
3. [文件与目录权限的意义](#step3)

---
#### <span id="step1">Linux文件属性</span>

> * 文件属性查看
<code>
	brainit@brainit-HP-Mini:~$ ll
	总用量 308
	drwxr-xr-x 31 brainit brainit   4096 4月   5 12:07 ./
	drwxr-xr-x  3 root    root      4096 3月  25 14:13 ../
	-rw-------  1 brainit brainit  12091 4月   4 21:06 .bash_history
	-rw-r--r--  1 brainit brainit    220 3月  25 14:13 .bash_logout
	-rw-r--r--  1 brainit brainit   3771 3月  25 14:13 .bashrc
	drwx------ 13 brainit brainit   4096 4月   5 12:17 .cache/
	drwxrwxr-x  3 brainit brainit   4096 3月  29 15:47 Code/
	drwxr-xr-x 21 brainit brainit   4096 4月   5 12:49 .config/
	drwx------  3 brainit brainit   4096 4月   4 12:38 .dbus/
	drwxr-xr-x  2 brainit brainit   4096 4月   3 15:58 Desktop/
	-rw-r--r--  1 brainit brainit     26 3月  25 14:34 .dmrc
	drwxr-xr-x  2 brainit brainit   4096 4月   2 17:01 Documents/
	drwxr-xr-x  3 brainit brainit   4096 4月   4 12:24 Downloads/
	drwxrwxr-x  3 brainit brainit   4096 3月  26 14:38 .eclipse/
</code>
> * 文件属性讲解
>> * drwxrwxr-x：文件类型与权限
>> 第一个字符代表这个文件类型
>>
>>> [d]：代表当前文件为目录
>>>
>>> [-]：代表当前文件为文件
>>>
>>> [l]：代表当前文件为链接文件，类似于快捷方式
>>> 
>>> [b]：代表设备文件里面的可供存储的接口设备
>>>
>>> [c]：表示设备文件里面的串行端口设备，例如键盘，鼠标（一次性读取设备）
>> 
>>接下来的字符中，以三个为１组，且均为ｒｗｘ的三个参数的组合
>>
>>> r代表可读，ｗ代表可写，ｘ代表可执行
>>>
>>> 第一组代表文件所有者权限，第二组为同用户组权限，第三组为其他非本用户组的权限
>>
>>
>> * 3：链接数
>>
>> * brainit：文件所有者
>>
>> * brainit：文件所属用户组
>>
>> * 4096：文件大小
>>
>> * 3月  29 15:47：最后修改时间
>>
>> * Code/：文件名称



#### <span id="step2">文件权限与属性的修改</span>
> * chgrp：修改文件所属用户组
>> chgrp [-R] groupname dirname/filename
> * chown：修改所有者
>> chown [-R] username　文件或目录：修改用户组
>>
>> chown [-R] groupname:username 文件或目录：修改用户组的同事顺便修改文件所属用户组
> * chmod：修改权限
>> * 数字类型修改文件权限
>>> rwx:按照２进制方式分三组进行读取
>>>
>>> 例如：-rwxr-xr--：为111101100＝７５４
>>>
>>> chmod 754 文件名
>>
>> * 符号类型改变文件权限
>>>　９个权限分别为ｕｓｅｒ，ｇｒｏｕｐ，ｏｔｈｅｒｓ三种身份，通过ｕｇｏ来代表三种身份的权限，用ａ来代表全部身份，读写执行的权限用ｒｗｘ代表
>>>
>>> 通过+-进行增加减少权限，通过＝进行权限设定
>>> [u/g/o/a][+-=][rwx]
>>> 
>>> 例如：-rwxr-xr--时
>>>
>>> chmod u=rwx,g=rx,o=r 文件或文件夹
#### <span id="step3">文件与目录权限的意义</span>
> * 权限对文件的重要性
>> * r（ｒｅａｄ）：可读取此文件，的实际内从，如读取文本文件的文字内容等
>>
>> * ｗ（ｗｒｉｔｅ）：可以编辑，新增或则修改该文件的内容（但不含删除该文件）
>>
>> * ｘ（ｅｘｃｕｔｅ）：该文件具有可以被系统执行的权限
> 
> * 权限对目录的重要性
>> * ｒ（read conentes in directory）：表示具有读取目录结构的权限，可以读取该目录先的文件名数据，例如可以用ｌｓ读取目录下的数据
>>
>> * ｗ（modify contents of directory）：表示具有更改该目录结构列表的权限（新建新的文件与目录，删除已经存在的文件与目录（不论该文件的权限如何），重命名文件或目录，转移该目录内的文件，目录位置）
>>
>> * ｘ（access directory）：代表用户能否进入该目录成为工作目录（所谓的工作目录就是你目前所在的目录），也影响着ｃｄ当前目录能否成功

最后修改时间：星期四, 06. 四月 2017 03:01下午 
