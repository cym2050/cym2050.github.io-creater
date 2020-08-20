---
title: "React"
date: 2020-08-08T11:10:46+08:00
draft: false
---

React既非框架也非编程语言，而是一个遵循某些原则的库，因为它依赖一些第三方库来提供一些核心功能（如路由）；它的开发人员之所以选择这些原则，是因为认为这些原则更适合用来构建响应式和函数式用户界面；它基于**声明式范式，而非命令式范式**。

声明范式：告诉程序what want
命令范式：告诉程序how to do

因为react native的出现，react抽离了react-dom
所有使用jsx的地方都要import react，因为jsx是React.creatElement()方法的语法糖
constructor主要用来初始化state和绑定this
setState不会立即更新state值，执行到shouldComponentUpdate，对比前后通过返回true、false更新state出发render
