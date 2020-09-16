---
title: "JavaScript 总结-Web API-事件"
date: 2020-08-06T21:53:29+08:00
draft: false
---

> 发送 DOM 事件是为了将发生的相关事情通知代码。每个事件都是继承自`Event`接口的对象，可以包括自定义的成员属性及函数用于获取事件发生时相关的更多信息。事件可以表示任何从基本的用户交互、到发生在渲染模型自动通知的任何事情。

## 一、JavaScript事件模型

**1. 原始事件模型（DOM 0 级）**

这是一种被所有浏览器都支持的事件模型，对于原始事件而言，没有事件流，事件一旦发生将马上进行处理，有两种方式可以实现原始事件：

- 在 html 代码中直接指定属性值：

```text
<button id="demo" type="button" onclick="fn()" />　　
```

- 在 js 代码中为

```js
document.getElementsById("demo").onclick = fn()
```

优点：所有浏览器都兼容

缺点：

- 逻辑与显示没有分离；
- 相同事件的监听函数只能绑定一个，后绑定的会覆盖掉前面的，如：a.onclick = func1；a.onclick = func2；将只会执行func2中的内容。
- 无法通过事件的冒泡、委托等机制（后面会讲到）完成更多事情。

因为这些缺点，虽然原始事件类型兼容所有浏览器，但仍不推荐使用。

**2. DOM2事件模型**

此模型是W3C制定的标准模型，现代浏览器（IE6~8 除外）都已经遵循这个规范。W3C 制定的事件模型中，一次事件的发生包含三个过程：

![img](https://pic4.zhimg.com/80/v2-5a42f780f54b2084d94997bf3e6e5fbd_720w.jpg)

1. 事件捕获：当某个元素触发某个事件（如 onclick），顶层对象 document 就会发出一个事件流，随着 DOM 树的节点向目标元素节点流去，直到到达事件真正发生的目标元素。在这个过程中，事件相应的监听函数是不会被触发的。
2. 事件目标：当到达目标元素之后，执行目标元素该事件相应的处理函数。如果没有绑定监听函数，那就不执行。
3. 事件冒泡：从目标元素开始，往顶层元素传播。途中如果有节点绑定了相应的事件处理函数，这些函数都会被一次触发。

IE 5.5: div -> body -> document

IE 6.0: div -> body -> html -> document

Mozilla 1.0: div -> body -> html -> document -> window

所有的事件类型都会经历事件捕获但是只有部分事件会经历事件冒泡阶段,例如 submit 事件就不会被冒泡。

事件的传播是可以阻止的：
　　• 在 W3C 中，使用 stopPropagation() 方法
　　• 在 IE 下设置 eve.cancelBubble = true；

事件绑定与事件解除：

```
addEventListener("eventType","handler","true | false")；`其中 eventType 指事件类型，注意不要加‘on’前缀，与 IE 下不同。第二个参数是处理函数，第三个即用来指定是否在捕获阶段进行处理，一般设为 false 来与 IE 保持一致(默认设置)，除非你有特殊的逻辑需求。监听器的解除也类似：`removeEventListner("eventType","handler","true | false");
```

**3. IE 事件模型**

IE 不把该对象传入事件处理函数，由于在任意时刻只会存在一个事件，所以 IE 把它作为全局对象window 的一个属性，为求证其真伪，使用 IE8 执行代码 `alert(window.event)`，结果弹出是 null，说明该属性已经定义，只是值为 null（与 undefined 不同）。难道这个全局对象的属性是在监听函数里才加的？于是执行下面代码：

```js
window.onload = function (){alert(window.event);}
setTimeout(function(){alert(window.event);},2000);
```

结果第一次弹出【object event】，两秒后弹出依然是 null。由此可见 IE 是将 event 对象在处理函数中设为 window 的属性，一旦函数执行结束，便被置为 null 了。IE 的事件模型只有两步，先执行元素的监听函数，然后事件沿着父节点一直冒泡到 document。冒泡已经讲解过了，这里不重复。IE 模型下的事件监听方式也挺独特，绑定监听函数的方法是：attachEvent( "eventType","handler")，其中 evetType 为事件的类型，如 onclick，注意要加’on’。解除事件监听器的方法是 `detachEvent("eventType","handler" )`

IE的事件模型已经可以解决原始模型的三个缺点，但其自己的缺点就是兼容性，只有 IE 系列浏览器才可以这样写。

以上就是3种事件模型，在我们写代码的时候，为了兼容ie，通常使用以下写法：

```js
var demo = document.getElementById('demo');
if(demo.attachEvent){
  demo.attachEvent('onclick',func);
} else {
　demo.addEventListener('click',func,false);
}
```

## 二、事件对象

1. 原生事件

事件被封装成一个 event 对象，包含了该事件发生时的所有相关信息（event 的属性）以及可以对事件进行的操作（event 的方法）

打印一个鼠标点击事件：

![img](https://pic3.zhimg.com/80/v2-db0969d24bea3425718d36890abdedc5_720w.jpg)

![img](https://pic3.zhimg.com/80/v2-068d02517d3f28dd9b139764554f36c6_720w.jpg)

\2. 自定义事件

想要实现一个自定义事件，需要经过下面几步：

1）createEvent（eventType）

> eventType 共5种类型：
> Events ：包括所有的事件
> HTMLEvents：包括` 'abort', 'blur', 'change', 'error', 'focus', 'load', 'reset', 'resize', 'scroll', 'select', 'submit', 'unload' `事件
> UIEevents ：包括 `'DOMActivate', 'DOMFocusIn', 'DOMFocusOut', 'keydown', 'keypress', 'keyup'`间接包含 MouseEvents.
> MouseEvents：包括 `'click', 'mousedown', 'mousemove', 'mouseout', 'mouseover', 'mouseup'.`
> MutationEvents:包括 `'DOMAttrModified', 'DOMNodeInserted', 'DOMNodeRemoved'`'DOMCharacterDataModified', 'DOMNodeInsertedIntoDocument', 'DOMNodeRemovedFromDocument', 'DOMSubtreeModified'. 　`　　　

2）在 createEvent 后必须初始化

> HTMLEvents 和 通用 Events：initEvent( 'type', bubbles, cancelable )
>
> UIEvents：initUIEvent( 'type', bubbles, cancelable, windowObject, detail )
>
> MouseEvents： initMouseEvent( 'type', bubbles, cancelable, windowObject, detail, screenX, screenY, clientX, clientY, ctrlKey, altKey, shiftKey, metaKey, button, relatedTarget )
>
> MutationEvents ： initMutationEvent( 'type', bubbles, cancelable, relatedNode, prevValue, newValue, attrName, attrChange )

3）触发

```js
targetObj.dispatchEvent(event) 
```

## 三、事件代理

传统的事件处理中，我们为每一个需要触发事件的元素添加事件处理器，但是这种方法将可能会导致内存泄露或者性能下降（特别是通过 ajax 获取数据后重复绑定事件，总之，越频繁风险越大）。

通过事件代理，我们将事件处理器绑定到一个父级元素上，避免了频繁的绑定多个子级元素，依靠事件冒泡机制与事件捕获机制，子级元素的事件将委托给父级元素。

```js
// 将每个 li 的事件处理都绑定到 ul 父元素，通过事件对象判断属于哪个元素的事件，然后执行相关代码
<ul id="ul">
    <li>文字1</li>
    <li>文字2</li>
    <li>文字3</li>
    <li>文字4</li>
    <li>文字5</li>
</ul>

const ul = document.getElementById('ul')
ul.addEventListener('click',event => {
  const target = event.target
  if(target.nodeName === 'LI') {
    alert(target.innerHTML)
  }
})
```