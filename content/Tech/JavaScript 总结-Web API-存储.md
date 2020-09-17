---
title: "JavaScript 总结-Web API-存储"
date: 2020-08-08T21:53:29+08:00
draft: false
---

## 一、cookie

本身用于浏览器和 server 通讯

被借用来做本地存储

用 document.cookie = “ ”来修改

缺点：最大 4K，http 请求时需要发送到服务端，增加数据量

## 二、localStorage 和 sessionStorage

HTML5 专门为存储设计，最大可存 5M

API 简单易用 setItem getItem

不会随 http 请求发送出去

localStorage 数据会永久存储，除非用代码或手动删除

sessionstorage 数据只存在于当前会话，浏览器关闭则清空