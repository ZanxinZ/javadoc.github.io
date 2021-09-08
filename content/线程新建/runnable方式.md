---
title: "Runnable方式"
date: 2021-09-08T17:54:12+08:00
draft: true
---

因为 Runnable 接口中只有 run 方法，无法启动一个新的线程。所以借由 Thread 的构造，从而可以新建线程。

Runnable.java

```java
package threadTest;

public class MyRunnable implements Runnable{
    @Override
    public void run(){
        System.out.println("Runnable");
    }
}
```

Run.java

```java
package threadTest;

public class Run {
    public static void main(String[] args) {
        Runnable runnable = new MyRunnable();
        Thread thread = new Thread(runnable);   //runnable has no 'start' method, so use thread to decorate(compact).
        thread.start();
        System.out.println("done");
    }
}
```