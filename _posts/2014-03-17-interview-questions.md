---
layout: post
title: Interview Questions
categories: Tech
tags: Interview
lang: zh-hans
---

DAY1：
===

1. double 的存储与计算都会丢失精度

2. 字符流与字节流

  流分类： 
  
  1.Java的字节流 
   InputStream是所有字节输入流的祖先，而OutputStream是所有字节输出流的祖先。 
   
  2.Java的字符流 
  
  [JavaIO](http://www.cnblogs.com/lich/tag/java%20IO/)
  
  Reader是所有读取字符串输入流的祖先，而writer是所有输出字符串的祖先。 
  InputStream，OutputStream,Reader,writer都是抽象类。所以不能直接new  


  字节流在操作的时候本身是不会用到缓冲区（内存）的，是与文件本身直接操作的，而字符流在操作的时候是使用到缓冲区的

  字节流在操作文件时，即使不关闭资源（close方法），文件也能输出，但是如果字符流不使用close方法的话，则不会输出任何内容，说明字符流用的是缓冲区，并且可以使用flush方法强制进行刷新缓冲区，这时才能在不close的情况下输出内容


3. Exception与Error

    Exceptions 
    
    1．可以是 可被控制(checked) 或 不可控制的(unchecked) 
    
    2．表示一个由程序员导致的错误 
    
    3．应该在应用程序级被处理 
    
    
    
    Errors 
    
    1．总是 不可控制的(unchecked) 
    
    2．经常用来用于表示系统错误或低层资源的错误 
    
    3．如何可能的话，应该在系统级被捕捉 


4. synchronized this 与 带码块， 线程状态， wait 与 sleep

  [link](http://www.cnblogs.com/GnagWang/archive/2011/02/27/1966606.html)
  
  sleep和wait的区别有：
  1，这两个方法来自不同的类分别是Thread和Object
  2，最主要是sleep方法没有释放锁，而wait方法释放了锁，使得其他线程可以使用同步控制块或者方法。
  3，wait，notify和notifyAll只能在同步控制方法或者同步控制块里面使用，而sleep可以在
    任何地方使用
   synchronized(x){
      x.notify()
     //或者wait()
   }
   4,sleep必须捕获异常，而wait，notify和notifyAll不需要捕获异常
 
    线程间的状态转换： 
    
    
    1. 新建(new)：新创建了一个线程对象。
    
    2. 可运行(runnable)：线程对象创建后，其他线程(比如main线程）调用了该对象的start()方法。该状态的线程位于可运行线程池中，等待被线程调度选中，获取cpu 的使用权 。
    
    3. 运行(running)：可运行状态(runnable)的线程获得了cpu 时间片（timeslice） ，执行程序代码。
    
    4. 阻塞(block)：阻塞状态是指线程因为某种原因放弃了cpu 使用权，也即让出了cpu timeslice，暂时停止运行。直到线程进入可运行(runnable)状态，才有机会再次获得cpu timeslice 转到运行(running)状态。阻塞的情况分三种： 
    
    (一). 等待阻塞：运行(running)的线程执行o.wait()方法，JVM会把该线程放入等待队列(waitting queue)中。
    
    (二). 同步阻塞：运行(running)的线程在获取对象的同步锁时，若该同步锁被别的线程占用，则JVM会把该线程放入锁池(lock pool)中。
    
    (三). 其他阻塞：运行(running)的线程执行Thread.sleep(long ms)或t.join()方法，或者发出了I/O请求时，JVM会把该线程置为阻塞状态。当sleep()状态超时、join()等待线程终止或者超时、或者I/O处理完毕时，线程重新转入可运行(runnable)状态。
    
    5. 死亡(dead)：线程run()、main() 方法执行结束，或者因异常退出了run()方法，则该线程结束生命周期。死亡的线程不可再次复生。

5. List与Set， TreeSet与HashSet

  List

  Is an Ordered grouping of elements.
  List is used to collection of elements with duplicates.
  New methods are defined inside List interface.
  
  Set
  
  Is an Unordered grouping of elements.
  Set is used to collection of elements without duplicates.
  No new methods are defined inside Set interface, so we have to use Collection interface methods only with Set   subclasses. 

