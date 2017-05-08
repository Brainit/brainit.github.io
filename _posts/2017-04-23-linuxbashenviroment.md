---
date: 2017-04-23 19:34:56+00:00
layout: post
title: Linux中常见环境变量说明
categories: Emulate
tags: Emulate Linux
---

### 目录

1. [变量及内容查看](#item1)
2. [常见环境变量说明](#item2)

---
#### <span id="item1">变量内容查看</span>
> 通过env命令查看系统环境变量

```
brainit@brainit-HP-Mini:~$ env
XDG_VTNR=7
LC_PAPER=zh_CN.UTF-8
LC_ADDRESS=zh_CN.UTF-8
XDG_SESSION_ID=c2
XDG_GREETER_DATA_DIR=/var/lib/lightdm-data/brainit
... ...
```

> 通过set查看环境变量和自定义变量

```
brainit@brainit-HP-Mini:~$ set
```

#### <span id="item2">常见环境变量说明</span>

|环境变量|说明|
|:------------|:----------|
|HOME|代表用户主文件夹|
|SHELL|告知我们目前这个环境使用的ｓｈｅｌｌ是哪个程序|
|HISTSIZE|我们曾经执行过的命令可以被系统记录下来，而记录的条数则是这个值来设置的|
|MAIL|当我们使用mail命令在收信时系统会去读取邮件信箱文件(mailbox)|
|PATH|执行文件的查找目录，目录与目录中间以冒号分割，由于文件的查找是依序由变量内的目录来查询，所以目录的顺序也是重要的|
|LANG|语系数据|
|RANDOM|随机数变量。文件是/dev/random，通过这个随机数文件的变量(RANDOM)来随机取得随机数值，变量值介于０-３２７６７。|
|HISTFILE|历史命令记录文件|
|PS1|命令提示符的设置值。|
|$|目前这个shell所使用的PID|
|?|刚才执行完命令的回传码|