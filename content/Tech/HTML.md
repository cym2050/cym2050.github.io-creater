---
title: "HTML"
date: 2020-07-31T22:12:44+08:00
draft: false
---

##### HTML:超文本标记语言
1. HTML的版本、HTML 4.01、XTML、HTML5、HTML 5.1
2. 规范文档根据浏览器的实际情况总结，由W3C编写
3. DOCTYPE
用来选择文档类型
4. 常见标签
a、form、input、button、h1、p、ul、ol、small、strong、div、kbd、video、audio、svg，除了div和span，其他标签都有默认样式
5. 什么是空标签
没有闭合的标签称为空标签，如：`<br />`和`<img />`等。 他们不存在成对的情况,反之具有成对性质的例如：`<div></div>、 <form></form> `就不是空标签。在HTML中，在空标签上使用闭标签是无效的，例如： `</br>` 。
6. 什么是可替换标签
在 [CSS](https://developer.mozilla.org/zh-CN/docs/Web/CSS) 中，**可替换元素**（**replaced element**）的展现效果不是由 CSS 来控制的。这些元素是一种外部对象，它们外观的渲染，是独立于 CSS 的。简单来说，它们的内容不受当前文档的样式的影响。CSS 可以影响可替换元素的位置，但不会影响到可替换元素自身的内容。某些可替换元素，例如 [`<iframe>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/iframe "HTML内联框架元素 <iframe> 表示嵌套的浏览上下文，有效地将另一个HTML页面嵌入到当前页面中。") 元素，可能具有自己的样式表，但它们不会继承父文档的样式。
典型的可替换元素有：
*   [`<iframe>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/iframe "HTML内联框架元素 <iframe> 表示嵌套的浏览上下文，有效地将另一个HTML页面嵌入到当前页面中。")
*   [`<video>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/video "HTML <video> 元素 用于在HTML或者XHTML文档中嵌入媒体播放器，用于支持文档内的视频播放。")
*   [`<embed>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/embed "HTML <embed> 元素将外部内容嵌入文档中的指定位置。此内容由外部应用程序或其他交互式内容源（如浏览器插件）提供。")
*   [`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img "HTML Image 元素（ <img> ）代表文档中的一个图像。")

7. 学会查看MDN文档