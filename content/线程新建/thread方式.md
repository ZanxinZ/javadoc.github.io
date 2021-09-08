---
title: "Thread方式"
date: 2021-09-08T17:43:04+08:00
draft: true
---

Mythread.java

```java
package threadTest;

public class MyThread extends Thread{
    @Override
    public void run(){
        super.run();
        for (int i = 0; i < 100; i++){
            System.out.println("MyThread:" + i);
        }
    }
}
```

Main.java

```java
package threadTest;

public class main {
    public static void main(String[] args){
        MyThread myThread = new MyThread();
        myThread.start();
        MyThread myThread1 = new MyThread();
        myThread1.start();
        System.out.println("Has been ran");
    }
}
```