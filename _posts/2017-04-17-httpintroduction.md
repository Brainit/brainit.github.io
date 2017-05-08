---
date: 2017-04-17 16:30:56+00:00
layout: post
title: HTTP协议笔记
categories: Emulate
tags: Emulate HTTP
---

### 目录

1. [HTTP介绍](#item1)
2. [HTTP特性](#item2)
3. [HTTP协议---URL](#item3)
4. [URL和URI的区别](#item4)
5. [HTTP协议---Request请求](#item5)
6. [HTTP协议---Response请求](#item6)


---
#### <span id="item1">HTTP介绍</span>
> **HTTP协议**是Hyper Text Transfer Protocol（超文本传输协议）的缩写，是用于从万维网（WWW：World Wild Web）服务器传输超文本到本地浏览器的传送协议。
> 
> 目前使用广泛的HTTP协议版本为**HTTP/1.1**（最为广泛）和HTTP/1.0。
> 
> http（超文本传输协议）是一个基于请求与响应模式的、无状态的、应用层的协议，常基于TCP的连接方式，HTTP1.1版本中给出一种持续连接的机制，绝大多数的Web开发，都是构建在HTTP协议之上的Web应用。
> 
> HTTP/1.0和HTTP/1.1区别
>> 1. HTTP/1.0协议使用非持久联接，即在非持久连接下，一个TCP连接只传输一个web对象
>> 2. HTTP/1.1协议默认使用持久连接，不必为每个web对象的传送建立一个新的连接，一个连接中可以传输多个对象。

#### <span id="item2">HTTP特性</span>
> 1. 支持客户/服务器模式。
2. 简单快速：客户想服务器请求服务时，只需传送请求方法和路径。
3. 灵活：HTTP允许传输任意类型的数据对象，正在传输的类型由Content-Type加以标记。
4. 无连接：无连接的含义是限制每次连接只处理一个请求。服务器川里客户的请求，并收到客户的应答后，即断开连接。采用这种方式可以节省时间。
5. 无状态：HTTP协议是无状态连接。无状态是指协议对于事务处理没有记忆能力。缺少状态以为着如果后续处理需要前面的信息，则它必须重传，这样可能导致每次连接传送的数据增量达。另一方面，在服务器不需要先前信息时它的应答较快。
> 

#### <span id="item3">HTTP协议---URL</span>
> URL：是一种特殊类型的URI，包含了用于查找某个资源的足够的信息。
> 
> 默认格式：http://host[:port][abs_path]
>> * http：表示通过HTTP协议来定位网络资源；
* host：表示合法的网络主机域名或则IP地址；
* port：指定一个端口号，缺省端口80端口；
* abs_path：指定请求资源的URI，如果没有abs_path，那么当前作为请求URI时，必须以/形式给出。
>> 
> 
> 例如：
>> http://blog.brainit.cn/
>> 
>> http:192.168.0.1/index.html
> 

#### <span id="item4">URL和URI的区别</span>
> **URI**，uniform resource identifier，统一资源标识符，用来唯一的标识一个资源。
>> Web上可用的每种资源如HTML文档、图像、视频片段、程序等都是一个来URI来定位的<br />
URI一般由三部组成：<br />
①访问资源的命名机制<br />
②存放资源的主机名<br />
>> ③资源自身的名称，由路径表示，着重强调于资源。<br />
> 
> **URL**是**uniform resource locator**，统一资源定位器，它是一种具体的URI，即URL可以用来标识一个资源，而且还指明了如何locate这个资源。
>> URL是Internet上用来描述信息资源的字符串，主要用在各种WWW客户程序和服务器程序上，特别是著名的Mosaic。采用URL可以用一种统一的格式来描述各种信息资源，包括文件、服务器的地址和目录等。<br />
URL一般由三部组成：<br />
①协议(或称为服务方式)<br />
②存有该资源的主机IP地址(有时也包括端口号)<br />
>> ③主机资源的具体地址。如目录和文件名等<br />
> 
> **URN**， **uniform resource name**，统一资源命名，是通过名字来标识资源，比如mailto:brainit@qq.com。
> 

#### <span id="item5">HTTP协议---Request请求</span>
> HTTP请求由三部分组成，请求行（request line）、消息报头（header）、请求正文
>> 请求方法 URL 协议版本<br />
头部字段名1：值1<br />
... ...
头部字段名n：值n<br />
<br />
>>请求数据<br />
> 
> 请求行必须以方法符号开头，以空格分开，后面跟着请求的URI和协议的版本。
> 
> 例如：
>> GET /index.html HTTP/1.1<br />
>> host: localhost
> 
> 常用请求方法：
>> GET:请求获取URI所标示的资源<br />
POST：在URI所标识的资源后附加新的数据<br />
HEAD：请求获取URI所标识的资源的响应信息头<br />
PUT：请求服务器存储一个资源<br />
DELETE：请求服务删除URI标识的资源<br />
TRACE：请求服务器回收收到的请求信息，主要用于测试或诊断
>> 
> 

#### <span id="item6">HTTP协议---Response响应</span>
> HTTP响应也是由三部分组成，分别是：状态行、消息报头、响应正文
>> HTTP/1.1 200 OK（状态行）<br />
>> Content-Type: text/html;charset=utf-8(消息报头)<br />
>> Content-Length: 122（消息报头）<br />
>> <br />
>> (响应正文)
> 
> 状态行：
>> 由HTTP协议版本号，状态码，状态消息三部分组成。
>> * 状态码：
>>> 1xx：提示信息-表示请求已介绍，继续处理<br />
>>> 2xx：成功-表示请求已被成功接收，理解，接受<br />
>>> 3xx：重定向-要完成请求必须进行更新进一步的操作<br />
>>> 4xx：客户端错误-请求有语法错误或请求无法实现<br />
>>> 5xx：服务段错误-服务端未能实现合法的请求
>>
>> * 常见状态代码，状态描述，说明
>>> 200 OK：客户端请求成功<br />
>>> 400 Bad Request：客户端请求右语法错误，不能被服务器所理解<br />
>>> 401 Unauthorized：请求未经授权，这个状态代码必须和WWW-Authenticate报头域一起使用<br />
>>> 403 Forbidden：服务器收到请求，但是拒绝提供服务<br />
>>> 404 Not Found：请求资源不存在，eg-输入了错误的URL<br />
>>> 500 Internetal Server Error：服务器发生不可预期的错误<br />
>>> 503 Server Unavailable：服务器当前不能处理客户端的请求，一段时间后可能回复正常<br />
>>
> 
> 消息报头：
>> Content-Type：指定了MIME类型的HTML（text/html），编码类型是utf-8
> 
> 空行：
>> 消息报头后面的空行是必须的
> 
> 响应正文：
>> 服务器返回给客户端的文本信息
