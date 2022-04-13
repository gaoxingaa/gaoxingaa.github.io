---
layout: post
title: Java异常学习笔记
categories: Tech
tags: [Java, Exception]
lang: zh-hans
---

有效处理Java异常三原则 

1. 具体明确

```

   File prefsFile = new File(prefsFilename);
    
   try{
       readPreferences(prefsFile);
   }
   catch (FileNotFoundException e){
       // alert the user that the specified file
       // does not exist
   }
   catch (EOFException e){
       // alert the user that the end of the file
       // was reached
   }
   catch (ObjectStreamException e){
        // alert the user that the file is corrupted
   }
   catch (IOException e){
       // alert the user that some other I/O
       // error occurred
   }
   
```

2. 提早抛出

```
  public void readPreferences(String filename)
  throws IllegalArgumentException{
      if (filename == null){
           throw new IllegalArgumentException("filename is null");
      }  //if
   
     //...perform other operations...
   
     InputStream in = new FileInputStream(filename);
   
     //...read the preferences file...
  }
```

3. 延迟捕获

```
   public void readPreferences(String filename)
   throws IllegalArgumentException,
   FileNotFoundException, IOException{
       if (filename == null){
              throw new IllegalArgumentException("filename is null");
        }  //if
    
        //...
    
        InputStream in = new FileInputStream(filename);
    
   //...
   }
```

[Interview Questions](http://www.journaldev.com/2167/java-exception-interview-questions-and-answers)
===
1. What is Exception in Java?

   Exception is an error event that can happen during the execution of a program and disrupts it’s normal flow. Exception can arise from different kind of situations such as wrong data entered by user, hardware failure, network connection failure etc.
   
   Whenever any error occurs while executing a java statement, an exception object is created and then JRE tries to find exception handler to handle the exception. If suitable exception handler is found then the exception object is passed to the handler code to process the exception, known as catching the exception. If no handler is found then application throws the exception to runtime environment and JRE terminates the program.
   
   Java Exception handling framework is used to handle runtime errors only, compile time errors are not handled by exception handling framework.


2. What are the Exception Handling Keywords in Java?

   There are four keywords used in java exception handling.

   throw: Sometimes we explicitly want to create exception object and then throw it to halt the normal processing of the program. throw keyword is used to throw exception to the runtime to handle it.
   throws: When we are throwing any checked exception in a method and not handling it, then we need to use throws keyword in method signature to let caller program know the exceptions that might be thrown by the method. The caller method might handle these exceptions or propagate it to it’s caller method using throws keyword. We can provide multiple exceptions in the throws clause and it can be used with main() method also.
   try-catch: We use try-catch block for exception handling in our code. try is the start of the block and catch is at the end of try block to handle the exceptions. We can have multiple catch blocks with a try and try-catch block can be nested also. catch block requires a parameter that should be of type Exception.
   finally: finally block is optional and can be used only with try-catch block. Since exception halts the process of execution, we might have some resources open that will not get closed, so we can use finally block. finally block gets executed always, whether exception occurrs or not.

3. Explain Java Exception Hierarchy?

   Java Exceptions are hierarchical and inheritance is used to categorize different types of exceptions. Throwable is the parent class of Java Exceptions Hierarchy and it has two child objects – Error and Exception. Exceptions are further divided into checked exceptions and runtime exception.
   
   Errors are exceptional scenarios that are out of scope of application and it’s not possible to anticipate and recover from them, for example hardware failure, JVM crash or out of memory error.
   
   Checked Exceptions are exceptional scenarios that we can anticipate in a program and try to recover from it, for example FileNotFoundException. We should catch this exception and provide useful message to user and log it properly for debugging purpose. Exception is the parent class of all Checked Exceptions.
   
   Runtime Exceptions are caused by bad programming, for example trying to retrieve an element from the Array. We should check the length of array first before trying to retrieve the element otherwise it might throw ArrayIndexOutOfBoundException at runtime. RuntimeException is the parent class of all runtime exceptions.
   
   exception-hierarchy


4. What are important methods of Java Exception Class?

   Exception and all of it’s subclasses doesn’t provide any specific methods and all of the methods are defined in the base class Throwable.
   
   String getMessage() – This method returns the message String of Throwable and the message can be provided while creating the exception through it’s constructor.
   String getLocalizedMessage() – This method is provided so that subclasses can override it to provide locale specific message to the calling program. Throwable class implementation of this method simply use getMessage() method to return the exception message.
   synchronized Throwable getCause() – This method returns the cause of the exception or null id the cause is unknown.
   String toString() – This method returns the information about Throwable in String format, the returned String contains the name of Throwable class and localized message.
   void printStackTrace() – This method prints the stack trace information to the standard error stream, this method is overloaded and we can pass PrintStream or PrintWriter as argument to write the stack trace information to the file or stream.

5. Explain Java 7 ARM Feature and multi-catch block?

   If you are catching a lot of exceptions in a single try block, you will notice that catch block code looks very ugly and mostly consists of redundant code to log the error, keeping this in mind Java 7 one of the feature was multi-catch block where we can catch multiple exceptions in a single catch block. The catch block with this feature looks like below:

   ```
   catch(IOException | SQLException | Exception ex){
        logger.error(ex);
        throw new MyException(ex.getMessage());
   }
   ```
   
   Most of the time, we use finally block just to close the resources and sometimes we forget to close them and get runtime exceptions when the resources are exhausted. These exceptions are hard to debug and we might need to look into each place where we are using that type of resource to make sure we are closing it. So java 7 one of the improvement was try-with-resources where we can create a resource in the try statement itself and use it inside the try-catch block. When the execution comes out of try-catch block, runtime environment automatically close these resources. Sample of try-catch block with this improvement is:

   ```
   try (MyResource mr = new MyResource()) {
               System.out.println("MyResource created in try-with-resources");
           } catch (Exception e) {
               e.printStackTrace();
           }
   ```

   Read more about this at Java 7 ARM.


6. What is difference between Checked and Unchecked Exception in Java?

   Checked Exceptions should be handled in the code using try-catch block or else main() method should use throws keyword to let JRE know about these exception that might be thrown from the program. Unchecked Exceptions are not required to be handled in the program or to mention them in throws clause.
   Exception is the super class of all checked exceptions whereas RuntimeException is the super class of all unchecked exceptions.
   Checked exceptions are error scenarios that are not caused by program, for example FileNotFoundException in reading a file that is not present, whereas Unchecked exceptions are mostly caused by poor programming, for example NullPointerException when invoking a method on an object reference without making sure that it’s not null.
   
7. What is difference between throw and throws keyword in Java?
   
   throws keyword is used with method signature to declare the exceptions that the method might throw whereas throw keyword is used to disrupt the flow of program and handing over the exception object to runtime to handle it.


7. How to write custom exception in Java?
   
   We can extend Exception class or any of it’s subclasses to create our custom exception class. The custom exception class can have it’s own variables and methods that we can use to pass error codes or other exception related information to the exception handler.
   
   A simple example of custom exception is shown below.
   
   MyException.java

   ```
   package com.journaldev.exceptions;
    
   import java.io.IOException;
    
   public class MyException extends IOException {
    
       private static final long serialVersionUID = 4664456874499611218L;
        
       private String errorCode="Unknown_Exception";
        
       public MyException(String message, String errorCode){
           super(message);
           this.errorCode=errorCode;
       }
        
       public String getErrorCode(){
           return this.errorCode;
       }
        
    
   }
   ```

8. What is OutOfMemoryError in Java?

   OutOfMemoryError in Java is a subclass of java.lang.VirtualMachineError and it’s thrown by JVM when it ran out of heap memory. We can fix this error by providing more memory to run the java application through java options.
   
   $>java MyProgram -Xms1024m -Xmx1024m -XX:PermSize=64M -XX:MaxPermSize=256m
   
   
9. What are different scenarios causing “Exception in thread main”?
   
   Some of the common main thread exception scenarios are:
   
   Exception in thread main java.lang.UnsupportedClassVersionError: This exception comes when your java class is compiled from another JDK version and you are trying to run it from another java version.
   Exception in thread main java.lang.NoClassDefFoundError: There are two variants of this exception. The first one is where you provide the class full name with .class extension. The second scenario is when Class is not found.
   Exception in thread main java.lang.NoSuchMethodError: main: This exception comes when you are trying to run a class that doesn’t have main method.
   Exception in thread “main” java.lang.ArithmeticException: Whenever any exception is thrown from main method, it prints the exception is console. The first part explains that exception is thrown from main method, second part prints the exception class name and then after a colon, it prints the exception message.
   Read more about these at Java Exception in Thread main.


10. What is difference between final, finally and finalize in Java?
   
   final and finally are keywords in java whereas finalize is a method.
   
   final keyword can be used with class variables so that they can’t be reassigned, with class to avoid extending by classes and with methods to avoid overriding by subclasses, finally keyword is used with try-catch block to provide statements that will always gets executed even if some exception arises, usually finally is used to close resources. finalize() method is executed by Garbage Collector before the object is destroyed, it’s great way to make sure all the global resources are closed.
   
   Out of the three, only finally is related to java exception handling.
   

11. What happens when exception is thrown by main method?
   
   When exception is thrown by main() method, Java Runtime terminates the program and print the exception message and stack trace in system console.
   

12. Can we have an empty catch block?
   
   We can have an empty catch block but it’s the example of worst programming. We should never have empty catch block because if the exception is caught by that block, we will have no information about the exception and it wil be a nightmare to debug it. There should be at least a logging statement to log the exception details in console or log files.
   

13. Provide some Java Exception Handling Best Practices?
   
   Some of the best practices related to Java Exception Handling are:
   
   Use Specific Exceptions for ease of debugging.
   Throw Exceptions Early (Fail-Fast) in the program.
   Catch Exceptions late in the program, let the caller handle the exception.
   Use Java 7 ARM feature to make sure resources are closed or use finally block to close them properly.
   Always log exception messages for debugging purposes.
   Use multi-catch block for cleaner close.
   Use custom exceptions to throw single type of exception from your application API.
   Follow naming convention, always end with Exception.
   Document the Exceptions Thrown by a method using @throws in javadoc.
   Exceptions are costly, so throw it only when it makes sense. Else you can catch them and provide null or empty response.
   Read more about them in detail at Java Exception Handling Best Practices.
