---
date: 2017-04-22 13:34:56+00:00
layout: post
title: Java中Socket操作
categories: Emulate
tags: Emulate Java
---

### 目录

1. [Socket类](#step1)
2. [ServerSocket类](#step2)
3. [ServerSocket类服务多个客户端](#step3)

---
#### <span id="step1">Socket类</span>
> 客户端Socket

```
import java.io.*;
import java.net.*;
import java.util.*;
public class SocketTest{
	public static void main(String[] args){
		try(Socket s = new Socke("www.baidu.com",8080)){
			InputStream inStream = s.getInputStream();
			Scanner in = new Scanner(inStream);

			while(in.hasNextLine()){
				String line =in.nextLine();
				System.out.println(line);
			}
		}
	}
}
```

> 常用方法：<br />
> Socket(String host ,int port)<br />
> InputStream getInputStream()<br />
> OutputStream getOutputStream()<br />
> void connect(SocketAddress address)<br />
> void connect(SocketAddress address,int timeoutInMilliseconds)<br />
> void setTimeout(int timeoutInMilliseconds)<br />
> boolean isConnected()<br />
> boolean isClose()<br />

#### <span id="step2">ServerSocket类</span>
> 服务端ServerSocket

```
import java.io.*;
import java.net.*;
import java.util.*;
public class EchoServer{
	public static void main(String[] args){
		try(ServerSocket s = new ServerSocket(8189)){
			try(Socket incoming = s.accept()){
				InputStream inStream = incoming.getInputStream();
				OutputStream outStream = incoming.getOutputStream();
	
				try(Scanner in = new Scanner(inStream)){
					PrintWriter out = new PrintWriter(outStream , true /*atuo flush*/);
					out.println("hello, Enter BYE to exit");

					boolean done = false;
					while(!done && in.hasNextLine()){
						Stromg line = in.nextLine();
						out.println("Echo" + line);
						if(line.trim().equals("BYE")) done = true;
					}
				}
			}
		}
	}
}
```

>　

#### <span id="step3">ServerSocket类服务多个客户端</span>
> 通过为每个请求新建一个线程服务多个客户端

```
class ThreadEchoHolder implements Runnable{
	... ...
	public void run(){
		try{
			InputStream inStream = incoming.getInputStream();
			OutputStream outStream = incoming.getOutputStream();
			... ...
			incoming.close();
		}catch(OIException e){
			//处理异常
		}
	}
}

//监听端口
ServerSocket s = new ServerSocket(8189);
while(true){
	Socket incoming = s.accept();
	Runnable r = new ThreadEchoHandler(incoming);
	Thread t = new Thread(r);
	t.start();
}
```
