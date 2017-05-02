---
date: 2017-04-13 16:48:56+00:00
layout: post
title: ubuntu下java开发环境安装
categories: Emulate
tags: Emulate MySQL Java
---

### 目录

1. [JDK安装](#step1)
2. [需要配置的环境变量](#step2)
3. [环境变量配置方法1](#step3)
4. [环境变量配置方法2](#step4)
5. [环境变量配置方法3](#step5)
6. [环境变量修改立即生效](#step6)

---
#### <span id="step1">JDK安装</span>
> sudo apt-get install openjdk-8-jdk


#### <span id="step2">需要配置的环境变量</span>
> 1. JAVA_HOME：指定jdk的安装目录，可通过whereis java查看jdk安装目录
2. PATH：指定命令的搜索路径
3. CLASSPATH：类的搜索路径

#### <span id="step3">环境变量配置方法1</span>
> 在终端下执行下列命令：
>> export JAVA_HOME=/usr/share/jdk
>> 
>> export PATH=$JAVA_HOME/bin:$PATH
>> 
>> export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar 
> 
> 缺点：临时生效，重启无效

#### <span id="step4">环境变量配置方法2</span>
> 修改~/.bash_profile文件，在文件末尾追加：
>> export JAVA_HOME=/usr/share/jdk
>> 
>> export PATH=$JAVA_HOME/bin:$PATH
>> 
>> export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar 
> 
> 只能针对当前用户生效

#### <span id="step5">环境变量配置方法3</span>
> 修改/etc/profile文件，在文件末尾追加：
>> export JAVA_HOME=/usr/share/jdk
>> 
>> export PATH=$JAVA_HOME/bin:$PATH
>> 
>> export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar 
> 
> 所有用户都可以使用这些环境变量

#### <span id="step6">环境变量修改立即生效</span>
> 修改完环境变量系统文件之后，环境变量并未立即生效
> 
> 通过使用source命令，让环境变量立即生效。
> 
> 例如上述[环境变量配置方法3](#step5)中，修改/etc/profile文件后，通过使用sudo source /etc/profile能让JDK环境变量立即生效