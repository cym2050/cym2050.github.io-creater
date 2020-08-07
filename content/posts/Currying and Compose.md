---
title: "Currying and Compose"
date: 2020-08-07T18:07:14+08:00
draft: true
---
##### Closures
闭包 匿名立即执行函数 

##### Currying
将参数转化为函数
```
const curriedMultiply = (a) => (b) => a * b;
const multiplyBy5 = curriedMultiply(5);
```

##### Compose
接受函数作为参数，后面的函数为前面的函数的参数

```
const compose = (f, g) => (a) => f(g(a));

const sum = (num) => num + 1;

compose(sum, sum)(5); 结果为7
```
