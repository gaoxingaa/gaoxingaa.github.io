---
layout: post
title: Java线程
categories: []
tags: []
lang: zh-hans

---
# A first-level heading
To open IntelliJ IDEA's built-in Thread Dump Analyzer, you can follow these steps: Debugger -> Get Thread Dump


## "DestroyJavaVM@13886" prio=5 tid=0x6a nid=NA runnable
- "DestroyJavaVM": This thread represents the shutdown process of the Java Virtual Machine. It is responsible for terminating the JVM and releasing associated resources.

- "prio=5": "prio" refers to the priority of the thread. In this case, the priority is set to 5, which is considered normal priority.

- "tid=0x6a": "tid" stands for "thread ID", and "0x6a" represents the hexadecimal value of the thread's ID. It provides a unique identifier for the thread.

- "nid=NA": "nid" stands for "native thread ID", which represents the thread ID at the operating system level. In this case, "NA" indicates that the native thread ID is not available or not applicable.

- "runnable": The thread is in the "runnable" state, meaning it is currently eligible to run but may or may not be executing at that particular moment. In the case of the "DestroyJavaVM" thread, it is in the process of shutting down the JVM.

## "Attach Listener@13812" daemon prio=5 tid=0x4 nid=NA runnable
- "Attach Listener": This thread is the Attach Listener thread, which is responsible for listening to requests to attach or detach a debugger to the JVM. It enables dynamic debugging and profiling capabilities for the JVM.

- "daemon": The thread is marked as a daemon thread. Daemon threads are background threads that do not prevent the JVM from exiting when all non-daemon threads have completed.

- "prio=5": "prio" refers to the priority of the thread. In this case, the priority is set to 5, which is considered normal priority.

- "tid=0x4": "tid" stands for "thread ID", and "0x4" represents the hexadecimal value of the thread's ID. It provides a unique identifier for the thread.

- "nid=NA": "nid" stands for "native thread ID", which represents the thread ID at the operating system level. In this case, "NA" indicates that the native thread ID is not available or not applicable.

- "runnable": The thread is in the "runnable" state, meaning it is currently eligible to run but may or may not be executing at that particular moment. In the case of the "Attach Listener" thread, it is ready and waiting for requests related to attaching or detaching a debugger.

## "Scanner-0@13828" daemon prio=5 tid=0x20 nid=NA waiting
```  
java.lang.Thread.State: WAITING
	  at java.lang.Object.wait(Unknown Source:-1)
	  at java.util.TimerThread.mainLoop(Unknown Source:-1)
	  at java.util.TimerThread.run(Unknown Source:-1)
```    
- Based on the information provided in the thread dump snippet, the "Scanner-0" thread is associated with a TimerThread that is executing the run() method. The TimerThread is a background thread created by the Java Timer class to execute tasks at specified intervals.

- The Timer class in Java allows you to schedule tasks to be executed at specific times or intervals. It internally uses a background thread (in this case, the "Scanner-0" thread) to execute those tasks.

## "Finalizer@13811" daemon prio=8 tid=0x3 nid=NA waiting
- "Finalizer": This thread is the Finalizer thread, which is responsible for executing the finalize() method of objects that are eligible for garbage collection. The finalize() method is called by the JVM before an object is garbage collected, allowing it to perform any necessary cleanup or resource releasing.

## "Reference Handler@13810" daemon prio=10 tid=0x2 nid=NA runnable
- "Reference Handler": This thread is the Reference Handler thread, which is responsible for processing reference objects that have been enqueued by the garbage collector. Reference objects are objects that are created to implement various reference types (e.g., weak references, soft references) and are used for implementing advanced memory management strategies.

## "Common-Cleaner@13813" daemon prio=8 tid=0xd nid=NA waiting
- Based on the available information, it appears that the "Common-Cleaner" thread is associated with the Java Cleaner mechanism, which is responsible for performing cleanup operations on objects that require finalization. 




