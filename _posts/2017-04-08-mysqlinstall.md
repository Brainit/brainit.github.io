---
date: 2017-04-08 16:16:17+00:00
layout: post
title: Ｕｂｕｎｔｕ下MySQL安装及简单操作
categories: Emulate
tags: Emulate Linux MySQL
---

### 目录
1. [Ｕｂｕｎｔｕ下ＭｙＳＱＬ安装](#item1)
2. [查看ＭySQL监听状态](#item2)
3. [登录MySQL并查看数据库](#item3)

---
#### <span id="item1">Ｕｂｕｎｔｕ下ＭｙＳＱＬ安装</span>
> 1. sudo apt-get install mysql-server
> 2. sudo apt-get install mysql-client
> 3. sudo apt-get install libmysqlclient-dev
> 
> MySQL安装过程中需要输入ｒｏｏｔ用户密码作为登录密码

#### <span id="item2">查看ＭySQL监听状态</span>
> sudo netstat -tap | grep mysql
> 
> 通过查看ｍｙｓｑｌ网络监听状态，判断是否安装成功

#### <span id="item３">登录MySQL并查看数据库</span>
> mysql -h localhost -u root -p
>> 
>> -h参数为主机,-u参数为用户，-p参数为密码
>> 
>> 输入安装过程中设置的密码，就成功登录ｍｙｓｑｌ
> 
> show database
>>查看当前数据库
> 
> use databasename
>> 进入databasename 数据库
> 
> show tables
>> 查看databasename中的所有表