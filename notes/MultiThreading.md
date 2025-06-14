![Thread Diagram](../images/L1-01.png)

One CPU/Computer can run multiple programs (processes) at a time, with multiple threads executing inside each process.

In the example above:
Thread 1 is processing an instruction.
While executing, it needs to perform an I/O (disk) operation.
During this I/O operation, Thread 1 is blocked, and the CPU would remain idle if there were no other work to do.
However, by using another thread (Thread 2) for a different process or task, the CPU can switch to executing Thread 2 while Thread 1 waits for the I/O to complete.

This approach leads to:
1) Improved performance

2) Better CPU utilization

3) Reduced idle time

Multithreading allows a system to make efficient use of CPU resources by handling multiple operations concurrently, especially when some threads are waiting on slower operations like disk I/O or network requests.

![image](https://github.com/user-attachments/assets/a99e5355-2d43-4d21-98c7-830eb009fb85)

There is various ways to create thread:

 **Method one:**

```java
public class thread1 {
    public static class Mythread extends Thread{
        @Override
        public void run(){
            System.out.println("thread is running");
            System.out.println("thread is stopped");;
        }

    }

    public static void main(String[] args) {
        Thread run = new Mythread();
        run.start();
    }

}
```
1) Thread is a built-in Java class used to create and manage threads.

2) It implements the Runnable interface, which defines the run() method.

3) In the example above, we override the run() method inside our class Mythread to provide the logic we want to execute in the thread.

4) Calling start() creates a new thread and invokes the overridden run() method on that thread.

**Method two:**

```java
public class Thread2 {
    public static class MyRunnable implements Runnable{
        @Override
        public void run(){
            System.out.println("thread started");
            System.out.println("thread stopped");
        }
        MyRunnable(Runnable runnable){

        }
        MyRunnable(){

        }
    }

    public static void main(String[] args) {
        Thread thread = new Thread(new MyRunnable());
        thread.start();
    }
}
```
We create a Runnable object:

```java
new MyRunnable()
```
We pass this Runnable to a Thread constructor:


```java
Thread thread = new Thread(new MyRunnable());
```
When we call thread.start(), Java internally creates a new thread of execution and calls:

```java
runnable.run();
```
which in this case is:
```java
MyRunnable.run()
```

**Method 3** 

By using lambda expression:
```java
public static void main(String[] args) {
        Runnable runnable = () ->{
            System.out.println("Thread is running");
            System.out.println("Thread is stopping");
        };

        Thread thread = new Thread(runnable);
        thread.start();
    }
```





