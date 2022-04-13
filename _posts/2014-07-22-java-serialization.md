---
layout: post
title: Java序列化学习笔记
categories: [技术]
tags: [Java, Serialization, TODO]
lang: zh-hans
---
First please look into this 
[5 things you didn't know about ... Java Object Serialization](http://www.ibm.com/developerworks/library/j-5things1/)
and this [怎样对带有不可序列化属性的Java对象进行序列化](http://www.importnew.com/10705.html)
and this [理解Java对象序列化](http://www.blogjava.net/jiangshachina/archive/2012/02/13/369898.html)

1. 影响序列化

  在现实应用中，有些时候不能使用默认序列化机制。比如，希望在序列化过程中忽略掉敏感数据，或者简化序列化过程。下面将介绍若干影响序列化的方法。

  1. transient关键字
  
  当某个字段被声明为transient后，默认序列化机制就会忽略该字段。此处将Person类中的age字段声明为transient，如下所示，
    ```    
    public class Person implements Serializable {
            
            transient private Integer age = null;
            
        }
    ```
  再执行SimpleSerial应用程序，会有如下输出：
    ```
    arg constructor
    [John, null, MALE]
    ```
  可见，age字段未被序列化。

//TODO
深入到序列化方案,eg:Google Protocol Buffer， thrift ， hessian
