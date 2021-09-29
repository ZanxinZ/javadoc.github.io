---
title: "4.Lock"
date: 2021-09-29T15:52:34+08:00
draft: true
---

## 可重入锁
- ReentrantLock 与 Condition 配合实现互斥同步。
- await/signal 等待通知模式
- 生产者消费者模式
  - 多个消费者多个生产者：一个生产者通知所有消费者，一个消费者通知所有生产者。『signalAll()』
  - 一个生产者一个消费者：一个生产者通知一个消费者，一个消费者通知一个生产者。『signal()』
