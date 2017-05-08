---
date: 2017-04-18 15:12:56+00:00
layout: post
title: Java中IO流的总结
categories: Emulate
tags: Emulate Java
---

### 目录

1. [知识点一览](#item1)
2. [流的概念和作用](#item2)
3. [IO流的分类](#item3)
4. [常用java流对象](#item4)


---
#### <span id="item1">知识点一览</span>
> Java流类图结构：<br />
![Java流类图](http://pic002.cnblogs.com/images/2012/384764/2012031413373126.jpg 'Java流类图')<br />
> 

#### <span id="item2">流的概念和作用</span>
> **流**是一组有顺序的，有七点和终点的字节集合，是对数据传输的总称或抽象。即数据在两设备间的传输称为流。**流的本质是数据传输，根据数据传输特性将流抽象为各种类，方便更直观的进行数据操作。**
> 

#### <span id="item3">IO流的分类</span>
> 根据处理数据类型的不同：字符流和字节流<br />
>> **字符流**
>>> 由于数据编码的不同，而有了对字符进行高效操作的流对象。本质其实就是给予字节流读取时，查了指定的码表。<br />
>> 
>> **字符流与字节流区别**
>>> 1. 读取单位不同：字节流以字节为单位，字符流以字符为单位，根据码表映射字符，一次可能读多个字节。
>>> 2. 根据对象不同：字节流处理所有类型的数据（如图片，AVI等），而字符流只能处理字符类型的数据。<br />
>> 
>> **结论**
>>> 只要是处理村文本数据，就有限考虑使用字符流。除此之外都使用字节流。<br />
>> 
> 
> 根据数据流向不同分为：输入流和输出流<br />
>> 对输入流只能进行读操作，对输出流只能进行写操作，程序中需要根据待传数据的不同特性而使用不同的流。
> 

#### <span id="item4">Java IO流对象</span>
> 1. 输入字节流InputStream
>> * InputStream是所有的输入字节流的父类，他是一个抽象类
>> * ByteArratInputStream,StringBufferInputStream,FileInputStream是三种基本的介质流，他们分别是从Byte数组，StringBuffer，和本地文件中读取数据。
>> * ObjectInputStream和所有FilterInputStream的子类都是装饰流（装饰器模式的主角）。
> 2. 输出字节流OutputStream
>> * OutputStream是所有的输出字节流的父类，他是一个抽象类
>> * ByteArrayOutputStream,FileOutputStream是两种基本的介质流，他们分别从Byte数组，和本地文件中写入数据。
>> * ObjectOutputStream和所有FilterOutputStream的子类都是装饰流。
> 3. 字节流的输入与输出的对应
>> ![字节流的输入域输出的对应](http://pic002.cnblogs.com/images/2012/384764/2012031413383430.png '字节流的输入域输出的对应')
> 4. 字符输入流Reader
>> * Reader是所有的输入字符流的父类，他是一个抽象类
>> * CharReader,StringReader是两种基本的介质流，他们分别将Char数组，String中读取数据
>> * BufferedReader很明显就是一个装饰器，它和其子类负责装饰其他Reader对象。
>> * FilterReader是所有自定义具体装饰流的父类。
>> * InputStreamReader是一个连接字节流和字符流的桥梁，他将字节流装换成字符流，FileReader可以说是一个达到此功能，常用的工具类，在其源代码中明显使用了FileInputStream转变成Reader的方法。Reader中个各类的用途和使用方法基本和InputStream中的类使用一致。
> 5. 字符输出流Writer
>> * Writer是所有输出字符流的父类，他是一个抽象类
>> * CharArrayWriter，StringWriter是两种基本的介质流，他们分别从Char数组，String中写入数据
>> * BufferedWriter是一个装饰器为Writer提供缓冲功能。
>> * PrintWriter和PrintStream极其类似，功能和使用也非常相似。
>> * OutputStreamWriter是OutputStream到Writer转换的桥梁，他的子类FileWriter其实就是一个实现此功能的具体类。
> 6. 字符流的输入与输出的对应
>> ![字符流的输入与输出的对应](http://pic002.cnblogs.com/images/2012/384764/2012031413390861.png '字符流的输入与输出的对应')
> 7. 字符流与字节流的转换
>> InputStreamReader：字节到字符的桥梁<br />
>> OutputStreamWriter：字符到字节的桥梁<br />
> 8. File类
>> File类是对文件系统中文件以及文件夹进行封装的对象，可以通过对象的思想来操作文件和文件夹。 File类保存文件或目录的各种元数据信息，包括文件名、文件长度、最后修改时间、是否可读、获取当前文件的路径名，判断指定文件是否存在、获得当前目录中的文件列表，创建、删除文件和目录等方法。  

