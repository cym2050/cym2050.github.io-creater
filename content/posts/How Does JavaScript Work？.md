---
title: "How Does JavaScript Work？"
date: 2020-08-07T22:03:02+08:00
draft: false
---

在最基本的形式中，JavaScript是一种同步的、阻塞的、单线程的语言，在这种语言中，一次只能执行一个操作。但web浏览器定义了函数和API，允许我们当某些事件发生时不是按照同步方式，而是异步地调用函数(比如，时间的推移，用户通过鼠标的交互，或者获取网络数据)。这意味着您的代码可以同时做几件事情，而不需要停止或阻塞主线程。

异步还是同步执行代码，取决于我们要做什么。

有些时候，我们希望事情能够立即加载并发生。例如，当将一些用户定义的样式应用到一个页面时，您希望这些样式能够尽快被应用。

但是，如果我们正在运行一个需要时间的操作，比如查询数据库并使用结果填充模板，那么最好将该操作从主线程中移开使用异步完成任务。随着时间的推移，您将了解何时选择异步技术比选择同步技术更有意义。

单线程意味着只有一个call stack，所以一次只能做一件事情

#### 什么是程序
1. 分配内存
2. 解析并执行每一行代码

#### JavaScript引擎
每个浏览器都实现了JavaScript引擎，在Google chrome中是V8引擎读取并执行js代码。引擎由两个部分组成：memory heap和call stack

memory heap是分配内存的地方,如下a,b,c存储在memory heap

```
const a = 1;
const b = 2;
const c = [1, 2];
```
call stack是读取并执行代码的地方，如下一行一行读取并执行：
```
console.log('1');
console.log('2');
console.log('3');
//result:
1
2
3
```

#### 单线程阻塞情况
假设：
```
function longtime () {发送http请求};
console.log('1');
longtime();
console.log('2');
console.log('3');

```
其中longtime要花很长时间才能执行完毕，程序不就会阻塞在这里，用户界面会卡死掉吗？


#### JavaScript运行时环境

![image-20200807231719301](..\..\static\images\image-20200807231719301.png)

JavaScript是单线程的，或者说JavaScript运行在单线程中，但JavaScript是工作在浏览器中的，而浏览器不只是JavaScript，其有以下线程：
- JavaScript引擎线程
- GUI渲染线程
- Event Loop线程（负责其他线程与主线程的通信，如网络IO，数据库IO，文件IO）
- 时间触发线程
- 定时器线程
- 网络请求线程
其次浏览器还提供了Web APIs（DOM，AJAX和 time　out），callback queue，event loop机制

参考：　[event loop](https://juejin.im/post/6844903606466904078)
