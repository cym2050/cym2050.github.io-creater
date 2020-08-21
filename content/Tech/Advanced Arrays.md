---
title: "Advanced Arrays"
date: 2020-08-06T21:53:29+08:00
draft: false
---

##### 1.forEach

forEach不返回任何值
对参数里的每一项作为参数执行函数
对象(参数).forEach(函数(对象的属性，索引))
```
const array = [1, 2, 3, 4];
array.forEach((num) => {
  console.log(num);
})
```

##### map
不修改原数组本省，必须用retur显式返回值，不然会返回undefined
对每个数组元素执行一遍所给函数后返回新数组

##### filter
必须用retur显式返回值，不然会返回undefined
过滤符合函数条件的item，并返回一个新数组



