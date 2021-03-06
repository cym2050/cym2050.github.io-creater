---
title: "Redux"
date: 2020-08-11T22:37:02+08:00
draft: true
---

理解 Redux
Redux 本身是一个很轻的库，解决 component -> action -> reducer -> state 的单向数据流转问题。

按我理解，他有两个非常突出的特点是：

predictable，可预测性
可扩展性
可预测性是由于他大量使用 pure function 和 plain object 等概念(reducer 和 action creator 是 pure function，state 和 action 是 plain object)，并且 state 是 immutable 的。这对于项目的稳定性会是非常好的保证。

可扩展性则让我们可以通过 middleware 定制 action 的处理，通过 reducer enhancer 扩展 reducer 等等。从而有了丰富的社区扩展和支持，比如异步处理、Form、router 同步、redu/undo、性能问题(selector)、工具支持。