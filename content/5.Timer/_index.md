---
title: "5.Timer"
date: 2021-09-30T08:36:57+08:00
draft: true
---

## Timer 

Timer 类负责计划任务

可以使用抽象类 TimerTask的子类进行业务编写。

### Schedule(TimerTask task, Date date)

<details>
<summary>设置定时任务</summary>

Run.java
```java
public class Run {
    public static Timer timer = new Timer();
    public static class MyTask extends TimerTask{
        @Override
        public void run() {
            System.out.println("定时任务时间到");
        }
    }
    public static void main(String[] args) {

        try{
            MyTask task = new MyTask();
            SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
            Date date = sdf.parse("2021-09-30 09:14:00");
            timer.schedule(task, date);
        }catch (ParseException e){

        }
    }
}
```
运行结果：在设定的时间打印了“定时任务时间到”。

其中 timer 新启动了一个线程，主线程结束时，子线程仍然继续运行。为了使得子程序伴随主程序的结束而结束，可以将子线程设置为守护线程👇

` public static Timer timer = new Timer(true);`

</details>






<details>
<summary>当任务 task 有多个的时候，它们是按照与 schedule 的绑定顺序来进入计划队列的。</summary>

```java
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.Timer;
import java.util.TimerTask;

public class Run {
    public static Timer timer = new Timer();
    public static class MyTask extends TimerTask{
        @Override
        public void run() {
            System.out.println("定时任务1时间到 " + System.currentTimeMillis());
            try {
                Thread.sleep(6000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }

        }
    }
    public static class MyTask2 extends TimerTask{
        @Override
        public void run() {
            System.out.println("定时任务2时间到 " + System.currentTimeMillis());

        }
    }
    public static void main(String[] args) {

        try{
            MyTask task = new MyTask();
            MyTask2 task2 = new MyTask2();
            SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
            Date date = sdf.parse("2021-09-30 09:37:00");
            Date date2 = sdf.parse("2021-09-30 09:37:05");
            timer.schedule(task, date);
            timer.schedule(task2, date2);
        }catch (ParseException e){

        }

    }
}

```

运行结果
>定时任务1时间到 1632966052416<br>
>定时任务2时间到 1632966058433

其中，任务 1 执行耗时 6000ms，任务的优先级别是以加入 schedule 的早晚为标准的（task 加入 schedule 队列），而 timer 是单个线程，所以任务 2 需要等待任务 1 执行完毕才开始判断当前系统时间与设定的时间之间的关系，设定时间已到或者过期就执行，设定时间未到就等待。
</details>

### schedule(TimerTask task, Date time, long period)

