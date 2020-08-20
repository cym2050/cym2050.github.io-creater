---
title: "CSS Grid"
date: 2020-08-04T20:45:28+08:00
draft: false
---

分清楚container与item

用Flex与Grid组合可能是一种比Bootstrap更好的方式

flex vs grid

#### grid作用于container子元素P
```
<div class="container">
  <p class="p1"></p>
  <p class="p2"></p>
</div>

对于整个容器
container {
  display: grid;
  //自动填充，每个网格不得小于200px
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  grid-template-rows: 1fr;
  //justify-items用于container
  justify-items: 
  align-items
}
对于容器内的单个元素
.p1 {
  //占用两列
  grid-column-start: 1;
  grid-column-end: 3;
  //与上面效果一样
  grid-column: 1/3;
  //占用所有列，也就是一行
  grid-column: 1/-1;
  //跨越2个gridbox
  grid-column: span 2;

  //行，与上述差不多
  grid-row: 

  //justify-self用于自己
  justify-self:
  align-self: start or end
}
```
都是对所有列或者所有行起作用
- grid-gap
- grid-template-columns: px,%,fr分数(更具响应性，随窗口自动变化)，auto
- grid-template-rows
- repeat(3, 1fr)重复3个1fr
- repeat(auto-fill, minmax(200px, 1fr)) 当水平收缩浏览器页面时，一旦一个Grid box小于200px就会自动流向下一行，gridbox自动变换大小，也就是说一行能容纳几个200px以上Gridbox就放几个，不行就放到下一行
- (水平)justify-items：stretch（默认，伸展），start（从头对齐，只占用box空间，剩下的grid空间透明），end
- (垂直)align-items:

- @Media queries
```
//当屏幕宽度小于600px时使用以下属性
@media only screen and (max-width: 600px) {
  
}
```