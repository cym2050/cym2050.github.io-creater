---
title: "Tachyons"
date: 2020-08-18T18:13:16+08:00
draft: true
---

链接：https://juejin.im/post/6844903633662771207

React拾遗：从10种现在流行的 CSS 解决方案谈谈我的最爱 （中）
上篇 介绍了 React 现在流行的 CSS 解决方案。本篇就直接进入主题详细讲讲我最喜欢的解决方式之一：tachyons

个人认为，tachyons 适合小的、样式不是重点的项目以及写 Demo， 但这不代表不能用 tachyons 完成大项目和漂亮的主页： 使用tachyons写的项目详见 tachyons.io/gallery/

0. 选择标准
当你兴奋地读完文档，在打算使用一个新 css 框架前，需要好好想清楚它是否在你的所有使用场景里圆满完成任务，我总结的几点：

是否解决了React开发的痛点：局部css，动态css？
是否支持所有css甚至是sass用法？伪类,嵌套，动画，媒体查询？
是否兼容你需要使用的第三方UI库？
是否能和纯css，或者是其他css框架很好共存，以备遇到特殊情况可以有方案B？
性能？大小？
1. tachyons
在我的经验，只是瞥一眼文档很少人会对 tachyons 上来就感冒的，真正感受到它的魅力是在使用中。我是看了一段现实使用 tachyons 的视频后 on board 的，和同事提起时，他们并不太热衷，但在看我现场使用后立马决定使用。

tachyons 不像之前所有的css框架，试图提供很多组件规模的css类，它甚至没有 btn 这样的类。bootstrap等作为css框架共享了框架的弊端：当你完全在框架提供的方案内使用时一切轻松愉快，但一旦你希望定制化，等待你的是无尽的痛。仿佛与之走上完全相反的道路，tachyons提供了极其细碎化的类，去看看 tachyons.io/components/，比如一个按钮：

按钮
代码如下：
<div class="ph3">
  <a class="f6 link dim br1 ba bw2 ph3 pv2 mb2 dib purple" href="#0">Button Text</a>
  <a class="f6 link dim br1 ba bw2 ph3 pv2 mb2 dib light-purple" href="#0">Button Text</a>
  <a class="f6 link dim br1 ba bw2 ph3 pv2 mb2 dib hot-pink" href="#0">Button Text</a>
  <a class="f6 link dim br1 ba bw2 ph3 pv2 mb2 dib dark-pink" href="#0">Button Text</a>
</div>
复制代码
拿第二行的class从左到右：分别为 font-size:.875rem,去掉link的丑陋默认样式，加上:hover淡化效果，border-radius 1 单位, 全border（border all），border宽度2单位，横向padding 3单位，纵向padding 2单位，margin bottom 2单位，display:block，紫色。

原子类：
这就是 tachyons 的基本概念，极细化的“原子类”，带来的好处是：

源代码极简且易读性极佳, 源代码。
14kB未压缩的大小。记得之前写项目管理系统，我试着用tachyons代替纯css，改好后不仅样式更加统一了，并且css文件更小了
定制化变得轻而易举：以上例，想边宽一点 bw3 即可。
永远不用担心命名冲突，永远不用担心样式覆盖，只要你写下一个类，UI必将随之变动；只要大家都使用tachyons，互相的工作永远不会影响对方。
写一次就会有体会，极大提高了开发速度。
简单的说，使用 tachyons 就好比用一种定义良好的极简的语言来写 inline css 的感觉。

为何可行
也许你想问如果 tachyons 这么好为啥之前从没有出现这样的 css 库呢？因为这种概念和inline css一样，只有在组件化开发浪潮中才真正变得可行。如果使用传统开发，每个按钮都如此书写想必不如使用一个btn类来的轻松。但在React等框架下，代码的重用这事儿已经被组件包干了。完全可以写一个Button组件：

const Button = ({ children, color }) => (
    <a className=`f6 link dim br1 ba bw2 ph3 pv2 mb2 dib ${color}` href="#0">{children}</a>
)
复制代码
使用如下

<Button color='hot-pink'> 注册 </Button>
复制代码
更多好处
使用模板字符串轻松完成动态css
样式的重用性会极大提高
tachyons > inline css
如果你认为 tachyons 只是 inline style 的话就错了，使用时你会在各个细节上爱上 tachyons：

优雅的媒体查询：
<div className="mw6 mw5-m mw4-l">
// 手机上max-width: 32rem, 中屏 16rem，大屏 8rem
<div className="w3 w5-ns">
// 手机上width: 4rem， 非手机 16rem
复制代码
使用 tachyons 开发可以先写手机的样式，然后加一通 -m，-l，-ns 几分钟就搞定适配。

自带良好的样式规范, 不仅仅是长度宽度和颜色，项目风格统一：
/* 比如shadow */
.shadow-1 { box-shadow: 0 0 4px 2px rgba( 0, 0, 0, .2 ); }
.shadow-2 { box-shadow: 0 0 8px 2px rgba( 0, 0, 0, .2 ); }
.shadow-3 { box-shadow: 2px 2px 4px 2px rgba( 0, 0, 0, .2 ); }
.shadow-4 { box-shadow: 2px 2px 8px 0 rgba( 0, 0, 0, .2 ); }
.shadow-5 { box-shadow: 4px 4px 8px 0 rgba( 0, 0, 0, .2 ); }
复制代码
debug 类。这几乎是我对tachyons最爱的一点，甚至不使用tachyons时也会在的代码里加入这两个类：
.debug * { outline: 1px solid gold; }
.debug-grid { background: transparent url( data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAgAAAAICAYAAADED76LAAAAFElEQVR4AWPAC97/9x0eCsAEPgwAVLshdpENIxcAAAAASUVORK5CYII= ) repeat top left; }
复制代码
debug-grid 会用网格描绘出现有元素盒子，debug 会给所有子元素盒子上金边。当样式没有按你想象排版时，给相应元素加一个debug、debug-grid类多半能找到原因。

细节上的便利
/* 纵向 vertical */
.pv2 {
    padding-top: .5rem;
    padding-bottom: .5rem;
}
/* 横行 horizontal */
.ph3 {
    padding-left: 1rem;
    padding-right: 1rem;
}
复制代码
和其他解决方法，三方库的兼容
三方库只要提供 className 的 props 就兼容，和其他 css 解决自然是完美兼容，因为它就是原生态的css。 所以tachyons不能很好处理的部分只需要使用其他解决方法或者原生css即可。值得一提的是，如果你不喜欢tachyons现有的类，自己写个新类就行。在我看来tachyons只是提供了一种思路，完全可以写一份适用你们团队的tachyons.css。

最后
先上一个 Demo 看看几行 tachyons 能做到的适配。

友情点名 tailwind.css 。它是一个受到 tachyons 启发，试图用 tachyons 的方式整合出一套能完成任何复杂度项目的 css 解决，比 tachyons 功能强大很多，需要一定学习。有兴趣的可以看看他们详细的文档。

下篇 styled-jsx，会谈谈个人最爱的大React项目css解决。