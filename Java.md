### What is java?
Java is a high-level programming language originally developed by Sun Microsystems and released in 1995. Java runs on a variety of platforms, such as Windows, Mac OS, and the various versions of UNIX.

### What are the supported platforms by java programming language?
Java runs on a variety of platforms, such as Windows, Mac OS, and the various versions of UNIX/Linux like HP-Unix, Sun Solaris, Redhat Linux, Ubuntu, CentOS, etc. 

### List features of java?
 1. **Abstraction**: Java hides some data from user who have no permission to see that and showing only the permitted data.
 2. **Encapsulation**: A class encapsulates the property (Variables) and features (Methods). It is the technique of making the fields in a
    class private and providing access to the fields via public methods.
    If a field is declared private, it cannot be accessed by anyone
    outside the class, thereby hiding the fields within the class.
    Therefore encapsulation is also referred to as data hiding.
 3. **Polymorphism**: Polymorphism is the ability of an object to take on many forms. The most common use of polymorphism in OOP occurs
    when a parent class reference is used to refer to a child class
    object..
 4. **Inheritance**: It is the process where one object acquires the properties of another. With the use of inheritance the information
    is made manageable in a hierarchical order.
 5. **Platform Independent**: Java can build in one OS and can run on any other OS with the help of JVM (Java Virtual Machine).
 6. **Security**: Java is more secure. It hides all confidential things and showing depends on the authority.

### What is the difference between object oriented programming language and object based programming language? 
Object based programming languages follow all the features of OOPs except Inheritance. JavaScript is an example of object based programming languages. 

### Which class is the super class for every class? 
The java.lang.Object class is the root of the class hierarchy. Every class has Object as a superclass. 

### Why is java architectural neutral?
Its compiler generates an architecture-neutral object file format (.class file format), which makes the compiled code to be executable on many OS, with the presence of JRE (Java Runtime Environment).

### How java enabled high performance? 
Java uses Just-In-Time compiler to enable high performance. Just-In-Time compiler is a program that turns Java byte code. 

### Why Java is considered dynamic?
It is designed to adapt to an evolving environment. Java programs can carry extensive amount of run-time information that can be used to verify and resolve accesses to objects on run-time. 

### Why multiple inheritance is not supported in java?
To reduce the complexity and simplify the language, multiple inheritance is not supported in Java in case of class.

### What is java virtual machine and how it is considered in context of java’s platform independent feature?
When Java is compiled, it is compiled into platform independent byte code. This byte code is distributed over the web and interpreted by virtual Machine (JVM) on whichever platform it is being run. 

### List two java IDE’s? 
- Netbeans 
- Eclipse

### What do you mean by Object?
A Java object is a combination of data and procedures working on the available data. An object has a state and behavior. The state of an object is stored in fields (variables), while methods (functions) display the object's behavior. Objects are created from templates known as classes. In Java, an object is created using the keyword "new".


### Abstract Class

Abstract class in Java is similar to interface except that it can contain normal method implementation. Abstract class in java can’t be instantiated. An abstract class is mostly used to extend abstract methods. The abstract method can define only inside abstract class. The abstract method should not have a body at the same time non-abstract method inside abstract class should have the body. While extending the abstract class , the abstract method should be overridden by the sub-class while the overriding of non-abstract method is not compulsory.

    public  abstract  class  Bus {    
	    public  abstract  void  onEngineStart();//Body not possible    
	    public  abstract  void  onEngineStop();//Body not possible
    
	    public  void  onNumberChanged(){//Must have a body
    
	    }
    
	    public  void  onColorChanged(){//Must have a body     
    
	    }    
    }
Here Bus is an abstract class have `onEngineStart()` and `onEngineStop()` as abstract method and `onNumberChanged()` and `onColorChanged()` as non-abstract method.


    public class MyVehicle extends Bus {
     @Override //Overriding necessary
     public void onEngineStart() {
    
     }
     @Override //Overriding necessary
     public void onEngineStop() {
    
     }
     @Override //Overriding not necessary
     public void onNumberChanged() {
      super.onNumberChanged();
     }
    }
Here MyVehicle extends the abstract class Bus, where two abstract method and one non-abstract method is override. Non-abstract override method can have the super keyword. 

### What is difference between abstract class and interface?

**Abstract Class** : An abstract class can have method body (non-abstract methods), instance variables, constructor and static methods. You can extends one abstract class.

**Interface** : Interface have only abstract methods. An interface do not have instance variables, constructor and static methods. You can implement multiple interfaces.

### What is abstraction?

Abstraction is a process of hiding the implementation details and showing only functionality to the user. 

### What is the difference between abstraction and encapsulation?

Abstraction hides the implementation details whereas encapsulation wraps code and data into a single unit.

### What is static import?
Static import is a feature introduced in the Java programming language that allows members which have been scoped within their container class as public static, to be used in Java code without specifying the class in which the field has been defined. 

    import static java.lang.Math.*;
    import static java.lang.System.out;
    
    public class HelloWorld {
     public static void main(String[] args) {
      out.println("a circumference of " + (PI * 5) + " cm");
     }
    }

### Error

Error is a subclass of the built-in class Throwable. Errors are the critical conditions that occur due to the lack of the system resources, and it can not be handled by the code of the program. Errors can not be recovered by any means because they can not be created, thrown, caught or replied. Errors are always of unchecked type, as compiler do not have any knowledge about its occurrence. Errors always occur in the run-time environment. The code is not responsible for such errors. The consequence of the occurrence of the error is that the program gets terminated abnormally. 

### Exception

Exception is a subclass of built-in class  Throwable. Exceptions are the exceptional conditions that occur in a runtime environment. Most of the times exceptions are caused due to the code of our program.But, exceptions can be handled by the program itself, as exceptions are recoverable. Exceptions are handled by using three keywords “try”, “catch”, “throw”.

### Key Differences in Error and Exception

 1. Error occur only when system resources are deficient whereas, an   
    exception is caused if a code has some problem.
 2.  An error can never be recovered whereas, an exception can be recovered by preparing the code to handle the exception.
 3.  An error can never be handled but, an exception can be handled by the code if the code throwing an exception is written inside a try and catch block.
 4.  If an error has occurred, the program will be terminated abnormally. On the other hand, If the exception occurs the program will throw an exception, and it is handled using the try and catch block.
 5.  Errors are of unchecked type i.e. error are not in the knowledge of compilers whereas, an exception is classified as checked and unchecked.
 6.  Errors are defined in java.lang.Error package whereas, an exception is defined java.lang.Exception.

### Thread

A thread, in the context of Java, is the path followed when executing a program. All Java programs have at least one thread, known as the main thread, which is created by the Java Virtual Machine (JVM) at the program's start, when the main() method is invoked with the main thread.

We use Threads to make Java application faster by doing multiple things at same time. Thread helps you to achieve parallelism in Java program. Since CPU is very fast and even contains multiple cores, just one thread is not able to take advantage of all the cores. By using multiple threads, you can take full advantage of multiple cores by serving more clients and serving them faster. Multi-threading is one way to exploiting huge computing power of CPU in Java application. Thread is also using for doing multiple tasks simultaneously. If you have lot of tasks to be done and If you are doing all this task in one thread, they would be executed sequentially. By using multiple threads in Java you can execute each of this task independently and parallelly.

### Multithreading

Multithreading in java is a process of executing multiple threads simultaneously. Java application contains at least one thread, that is called main thread which executes your main method. Instead of that you can also add new user threads to make your application faster and more efficient and it's called as multi-threading.  Multithreading is mostly used in games, animation, etc. The following are the reasons and scenarios to use multiple threads in Java.

-   To make a task run parallel to another task : By Using multi-threading we can execute multiple task at a time parallelly.
-   To take full advantage of CPU power : Another common reason for using multiple threads in Java is to improve throughput of the application by utilizing full CPU power.
-   For reducing response time : You can also use multiple threads to reduce response time by doing fast computation by dividing a big problem into smaller chunks and processing them by using multiple threads.
-   To sever multiple clients at the same time : One of the most common scenarios where using multiple threads significantly improve an application's performance is a client-server application. A single threaded application means only one client can connect to the server at a time, but a multi-threaded server means multiple clients can connect to the server at same time. This means next client don't have to wait until your application finish processing request of the previous client.

> Multiprocessing and multi-threading, both are used to achieve
> multitasking. However, we use multi-threading than multiprocessing
> because threads use a shared memory area. They don't allocate separate
> memory area so saves memory, and context-switching between the threads
> takes less time than process.

### Multiprocessing

A multiprocessing system is one which has more than two processors. The CPUs are added to the system to increase the computing speed of the system. Each CPU has its own set of registers and main memory. Just because CPUs are separate, it may happen that one CPU may not have anything to process and sit idle and the other may be overloaded with the processes. In such cases, the processes and the resources are shared dynamically among the processors.

Multiprocessing can be classified as symmetric multiprocessing and asymmetric multiprocessing. In symmetric multiprocessing, all processors are free to run any process in a system. In Asymmetric multiprocessing, there is a master-slave relationship among the processors. The master processor is responsible for allotting the process to slave processors.
