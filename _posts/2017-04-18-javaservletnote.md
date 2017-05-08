---
date: 2017-04-18 15:12:56+00:00
layout: post
title: Linux下用文本编辑器写第一个servlet
categories: Emulate
tags: Emulate Java Linux
---

### 目录

1. [建立项目目录](#item1)
2. [编写Servlet](#item2)
3. [编译HelloServlet.java](#item3)
4. [建立web.xml](#item4)
5. [启动tomcat服务器](#item5)
6. [访问](#item6)


---
#### <span id="item1">建立项目目录</span>
> 在tomcat下的webapps目录下建立项目的目录，也可以在webapps下的ROOT目录中操作，我选择直接在ROOT中操作。<br />
> 并建立如下的目录结构
```text
└── WEB-INF
    ├── classes
    │   └── HelloServlet.java
    └── web.xml
```
> 在linux下，你可能需要使用root权限才能建立文件与目录

#### <span id="item2">编写Servlet</span>
> 编辑HelloServlet.java
> 

```
package com.firstServlet;

import javax.servlet.*;
import javax.servlet.http.*;
import java.io.*;

public class HelloServlet extends HttpServlet
{
    public void service(ServletRequest req,ServletResponse resp) throws ServletException,IOException{
            resp.getWriter().write("Hello Servlet");
        }
}
```
> 

#### <span id="item3">编译HelloServlet.java</span>
> 编译java文件需要导入servlet-api.jar文件,你可以使用如下命令查找servlet-api.jar
```
whereis servlet-api.jar
```
下面是编译文件的命令
```
javac -d . -cp /usr/share/tomcat8/lib/servlet-api.jar HelloServlet.java
```
编译完之后会出现出现如下文件结构
```
└── WEB-INF
    ├── classes
    │   ├── com
    │   │   └── firstServlet
    │   │       └── HelloServlet.class
    │   └── HelloServlet.java
    └── web.xml
```
> 

#### <span id="item4">修改web.xml</span>
> 修改WEB-INF目录下的web.xml文件

```
<?xml version="1.0" encoding="UTF-8"?>
<web-app version="2.5" 
    xmlns="http://java.sun.com/xml/ns/javaee" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
    xsi:schemaLocation="http://java.sun.com/xml/ns/javaee 
    http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd">
    <servlet>
        <servlet-name>HelloServlet</servlet-name>
        <servlet-class>com.firstServlet.HelloServlet</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>HelloServlet</servlet-name>
        <url-pattern>*.do</url-pattern>
    </servlet-mapping>
</web-app>
```
> 

#### <span id="item5">启动tomcat服务器</span>
> 启动tomcat服务器
```
sudo service tomcat8 start
```
如果你的服务器已经启动，可以通过重启服务器

```
sudo service tomcat8 restart
```
> 

#### <span id="item6">访问</span>
> 打开浏览器，通过访问服务器<br />
```
http://localhost:8080/helloservlet.do
```
如果你使用了自建的项目名称而没有使用ROOT，则需要使用

```
http://localhost:8080/项目名称/helloservlet.do
```
> 
