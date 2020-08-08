---
title: "React的virtual Dom对于重排与重绘的优化"
date: 2020-08-08T15:36:51+08:00
draft: true
---

- virtual dom与real dom进行diff比较，获取实际变化的dom，这一切在内存中发生速度很快，得出diff后把更改批量的应用于real dom
维护两棵virtual dom，对两棵virtual dom的查询减少了real dom的查询，也就减少了DOM的重排
每当调用setState()方法时，ReactJS都会从头开始创建整个Virtual DOM。创建整棵树非常快，因此不会影响性能。
在任何给定时间，ReactJS维护两个Virtual DOM，一个具有更新的状态Virtual DOM，另一个具有先前的状态Virtual DOM。
和 DOM 操作比起来，js 计算是非常廉价的。Virtual DOM render + diff 显然比渲染 html 字符串要慢，但是，它依然是纯 js 层面的计算，比起后面的 DOM 操作来说，依然好了太多。

- 批量修改DOM元素的的核心思想是：
    - 让该元素脱离文档流
    - 对其进行多重修改
    - 将元素带回文档中

- JavaScript优化dom操作
    1. 隐藏元素，进行修改后，然后再显示该元素
    ```
    let ul = document.querySelector('#list');
    ul.style.didsplay = 'none';
    //appendNode是自己写的函数，由于ul被抽出文档流了，所有函数里面修改dom节点不会频繁的引起dom重排
    apendChild(ul, data);
    ul.style.display = 'block';
    ```
    以上操作会造成两次重排，分别是元素的隐藏与显示
    2. 使用文档片段创建一个子树，然后拷贝到文档流中
    ```
    let fragment = document.createDocumentFragment();
    appendNode(fragment, data);
    ul.appendChild(fragment);
    ```
    文档片段是一个轻量级的document对象，它设计的目的就是用于更新，移动节点之类的任务；以上方法并不会是元素短暂消失，造成逻辑问题，且只涉及了一次重排
    3. 将原始元素拷贝到一个独立的节点中，操作这个节点，然后覆盖原始元素
    ```
    let old = document.querySelector('#list');
    let clone = old.cloneNode(true);
    appendNode(clone, data);
    old.parentNode.replaceChild(clone, old);
    ```
    上述只引发了一次重排

- 浏览器优化：队列化修改并批量执行，需实时反馈给用户的属性浏览器优化会失效

- 最小化重绘和重排：使用cssText代替单个样式修改，使用类修改样式

参考： https://juejin.im/post/6844903902689656845