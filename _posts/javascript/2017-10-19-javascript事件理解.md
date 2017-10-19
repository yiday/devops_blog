---
layout: default
title: vue-resource参数怎么添加？
---

# {{ page.title }}

## 为什么要单线程？
为了避免产生复杂的同步问题（核心特征）

HTML5通过Web Worker标准，允许Javascript创建多个线程，但子线程完全受主线程控制，且不得操作DOM。

## 任务的总类
### 同步任务(synchronous)
在主线程上排队执行的任务，只有前一个任务完成后，才能执行后一个任务

### 异步任务(asynchronous)
不进入主线程、而进入“任务队列(task queue)”的任务，只有"任务队列"通知主线程，某个异步任务可以执行了，该任务才会进入主线程执行。

### 任务执行示意图
![任务](http://image.beekka.com/blog/2014/bg2014100801.jpg)
只要主线程空了，就会去读取"任务队列"，这就是JavaScript的运行机制。这个过程会不断重复。
