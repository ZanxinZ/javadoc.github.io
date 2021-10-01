---
title: "7.补充"
date: 2021-10-01T14:19:38+08:00
draft: true
---

## 线程组 ThreadGroup 

>`ThreadGroup thredGroup = Thread.currentThread().getThreadGroup()`

***

## SimpleDateFormat 非线程安全

解决方法：
1. 使用静态方法生成多个 SimpleDateFormat 实例。
2. 使用 ThreadLocal 使得不同对象绑定到不同线程。
>`public static ThreadLocal<SimpleDateFormat> = new ThreadLocal<SimpleDateFormat>();`

## 线程异常的处理

```java
thread.setUncaughtExceptionHandler(new UncaughtExceptionHandler(){
    @Override
    public void uncaughtException(Thread t, Throwable w){
        System.out.println("线程出现异常");
    }
});
```

***

## 线程组异常
线程组内一个线程出现异常，不会影响其他线程的运行。

如果需要 ThreadGroup 捕获组内线程的异常，则重写 ThreadGroup 的 uncaughtException 即可。 

异常只能被捕获一次，线程组内如果有线程已经 catch 了异常，那么 ThreadGroup 无法捕获异常。

## 异常捕获的先后
先是线程对象，然后是静态类，再是线程组对象。