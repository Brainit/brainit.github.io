---
date: 2017-04-20 19:20:56+00:00
layout: post
title: Java多线程
categories: Emulate
tags: Emulate Java
---

### 目录

1. [进程与线程](#item1)
2. [线程状态](#item2)
3. [线程属性](#item3)
4. [同步](#item4)

---
#### <span id="item1">进程与线程</span>
> 进程
>> **进程**是一块包含了某些资源的内存区域。操作系统利用进程把它的工作划分为一些功能单元。<br />
>> 进程拥有一个私有的虚拟地址空间。进程间不共享数据。
> 
> 线程
>> 一个程序同事执行多个任务，通常，每一个任务称为一个**线程**。<br />
>> 进程包含一个或多个线程。线程间共享数据。
> 
> 在单独线程中执行程序
>> 方法1：实现Runnable接口
```
class MyRunnable implements Runnable{
	public void run(){
		//执行程序
	}
}
//创建类对象
Runnable r = new MyRunnable();
//创建Thread对象
Thread t = new Thread(t);
//启动线程
t.start();
```
>> 
> 
>> 方法2：继承Thread类
```
class MyThread extends Thread{
	public void run(){
		//执行程序
	}
}
//创建对象
MyThread t = new MyThread();
//启动线程
t.start();
```
>> 不要调用Thread类或Runnable对象的run方法，直接调用run方法，只会执行同一个线程中的任务，而不会启动新线程。应该调用Thread的start方法，这个方法将创建一个执行run方法的新线程。

#### <span id="item2">线程状态</span>
> 线程状态：新创建，可运行，被阻塞，等待，计时等待，被终止。
>> * 新创建：new操作创建一个新线程<br />
>> * 可运行：一旦调用ｓｔａｒｔ方法，线程处于ｒｕｎｎａｂｌｅ状态。一个可运行的线程可能正在运行，也可能没有运行，这取决于操作系统给线程提供运行的时间。<br />
>> * 被阻塞：线程暂时不活动，不运行任何代码，且消耗最少的资源。当一个线程试图获取一个内部持有的对象锁，而该锁被其他线程持有，则该线程进入**阻塞状态**。<br />
>> * 等待：当线程等待另外一个线程通知调度器一个条件时，它自己进入等待状态。<br />
>> * 计时等待：有几个方法右一个超时参数，调用他们导致线程进入**计时等待**状态。这以状态将一致保持到超时期满或则介绍到适当的通知。带有超时参数的方法有Thread.Object.wait,Lock.tryLock，以及Condition.await的计时版。<br />
>> * 终止：终止情况１－因为ｒｕｎ方法正常退出而自然死亡。终止情况２－因为一个没有捕获的异常终止了ｒｕｎ方法而意外死亡。特别的，可以调用线程的stop方法杀死一个线程，该方法已过时。

#### <span id="item3">线程属性</span>
> * 线程优先级
>> 通过setPriority()方法设置优先级，可以将线程优先级设置为在MIN_PRIORITY和MAX_PRIORITY和NORM_PRIORITY。<br />
>> Thread类中静态yield()方法导致执行线程处于让步状态，如果有其他的可运行线程具有至少与此线程同样高的优先级，那么这些线程接下来会将被调度。<br />
> * 守护线程
>> 守护线程为其他线程提供服务。当值剩下守护线程时，虚拟机就退出了。线程通过t.setDaemon(true)设置为守护线程。

#### <span id="item4">同步</span>
> 多线程并发访问同一数据，可能造成数据不同步
>　* 锁
>> ReentrantLock类
```
//ReentrantLock类在Java SE 5.0引入ReentrantLock类
mLock.lock();//mLock是ReentrantLcok类的对象
try{
	//critical section
}finally{
	mLock.unlock();
	//make sure the lock is unlocked even if an exception is thrown
}
//这以结构确保任何时刻只有一个线程进入临界区
//一旦一个线程封锁了锁对象，其他任何线程都无法通过ｌｏｃｋ语句。
//当其他线程调用了lock时，他们被阻塞，知道第一个线程释放锁对象。
//把解锁操作包括在finally子句之内是至关重要的。
//如果在临界区的代码抛出异常，锁必须被释放。
//否则，其他线程将永远阻塞。
```
>> * Synchronized关键字
```
//一个方法用Synchronized关键字声明
public synchronized void method(){
	//method body
	//在方法中调用ｗａｉｔ等价于intrinsicCondition.await();
	//在方法中调用notifyAll等价于intrinsicCondigtion.signalAll();
}
//等价于
public void method(){
	this.intrinsilock.lcok();
	try{
		//method body
	}finally{
		this.intrinsilock.unlock();
	}
}
```
>>