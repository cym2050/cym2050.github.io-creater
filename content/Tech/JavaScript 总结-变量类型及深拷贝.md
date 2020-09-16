---
title: "JavaScript 总结-变量类型及深拷贝"
date: 2020-07-18T17:32:25+08:00
draft: false

---

## 一、 值类型与引用类型

number、string、boolean、undefined、symbol，这 5 种数据类型是按值访问的，因为可以直接操作保存在变量中的实际的值，所以也被称为值类型。其占用空间固定，保存在栈中，保存与复制的是值本身。(注：很多资料把 null 看作值类型，其实 null 是特殊的引用类型，用typeof 判断结果是 Object）

```js
let a = 100
let b = a 
a = 200
cosole.log(b) //100
```

![img](https://pic1.zhimg.com/80/v2-ad425a1596e43a2c6d81b751db6dff70_1440w.png)

对象(Object)、数组(Array)、函数(Function)，是按引用地址访问的，被称为引用类型。占用空间不固定，保存在堆中，保存与复制的是指向对象的一个指针。

```js
let a = { age: 20 }
let b = a
b.age = 21
console.log(a.age) // 21
```

![img](https://picb.zhimg.com/80/v2-f01a7458c54bdabcc5a71c9fd023b208_1440w.jpg)

**思考： 为什么要分为值类型与引用类型？**

**主要考虑两个方面，性能与内存**。值类型数据量小，使用值拷贝的方式不会占用太多性能和存储空间，而对象类型可能会是一个很大数据量的结构，每次都直接全部拷贝会消耗很多性能和存储空间，而只复制一个存储对象的地址则可以解决这个问题。

但引用类型也有缺点，如果多个不同变量指向同一个对象，会导致改变一个变量，其他引用了此对象的变量也会改变，编程时要多加注意。

## 二、typeof 运算符

- 识别所有值类型

```js
let a;  typeof a //'undefined
const str = 'sdf';  typeof str //'string'
const num= 10;  typeof num //'number
const bool = true;  typeof bool //'boolean'
cosnt sym = Symbol('s')  typeof sym //'symbol'
```

- 识别函数

```js
typeof function() {}  //'function'
typeof console.log  //'function'
```

- 判断是否是引用类型

```js
typeof null  //'object'
typeof { age: 20 }  //'object'
typeof ['a', 'b']  //'object'
```

## 三、深拷贝

引用类型导致的深拷贝问题，由于对引用类型直接进行赋值操作，只是指向了同一个值的地址，当我们需要完整的将引用类型复制下来保存于另一个地址并进行操作时，就需要深拷贝。

方式 1：JSON方法

```js
var objCopy = JSON.parse(JSON.stringify(obj))
```

方式 2：递归

```js
function deepClone(obj = {}) {
    // obj 是 null ，或者不是对象和数组，直接返回
    if (typeof obj !== 'object' || obj == null) {
        return obj
    }
    // 初始化返回结果
    let result
    if (obj instanceof Array) {
        result = []
    } else {
        result = {}
    }

    for (let key in obj) {
        // 保证 key 不是原型的属性
        if (obj.hasOwnProperty(key)) {
            // 递归调用！！！
            result[key] = deepClone(obj[key])
        }
    }

    // 返回结果
    return result
}
```