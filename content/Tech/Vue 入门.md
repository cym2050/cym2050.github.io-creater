---
title: "Vue 入门"
date: 2020-08-09T21:53:29+08:00
draft: false
---

### 一、基本介绍

1. 安装和引入

   直接引入： `<script>` 或 npm install Vue

   构建工具：Vue CLI，开箱即用，提供了一个优秀的构建配置

2. 实例

   ```javascript
   <div id="app">￼
     <h1>{{ title }}</h1>￼
   </div>￼
   <script src="https://cdn.jsdelivr.net/npm/vue@2.5.16/dist/vue.js"></￼script>￼
   <script type="text/javascript">￼
      var vm = new Vue({￼
      el: '#app', // 绑定（mount）到DOM上￼
      data () {￼
         return {￼
         title: 'Hello World'￼
         }￼
      }￼
    })￼
   </script>
   ```

3. 生命周期

   Vue 实例在初始化时需要经历一系列过程，比如模板编译、渲染虚拟 DOM、将实例挂载到 DOM 上、设置数据监听和数据绑定，过程中允许运行一些钩子函数

   beforeCreate()、created()、beforeMount()、mounted()、beforeUpdate()、updated()、beforeDestory()、destoryed()

4. 数据响应式原理

   - 数据链

     元数据 -> 衍生数据

   - 函数式编程

     核心是根据元数据生成新的衍生数据，提供唯一确定的输入，函数将返回唯一确定的输出，它并不会修改原有变量的值。**实际上函数式编程就是建立一条数据流的链路，开发者只需要关注输入和输出两端的内容就可以，这是封装复用的一种最佳实践**

   - Vue 中的数据链

     Vue 实例提供 computed 计算属性选项，供开发者生成衍生数据对象，计算属性以函数形式声明，但并不接受参数，也只能以属性的方式调用。由于计算属性的 this 指向 Vue 实例，所以可以获取实例上所有已挂载的可见属性

     ```javascript
     <style>￼
     #app {￼
       font-family: Roboto, sans-serif;￼
       color: #363e4f;￼
     }￼
     .data-label {￼
        display: inline-block;￼
        width: 160px;￼
     }￼
     </style>￼
     <div id="app">￼
      <p><strong class="data-label">A</strong><input type="text" v-model="a"></p >￼
      <p><strong class="data-label">B</strong><input type="text" v-model="b"></p >￼
      <p><strong class="data-label">C=A*2+2</strong>{{ c }}</p >￼
      <p><strong class="data-label">D=A+B*2</strong>{{ d }}</p >￼
      <p><strong class="data-label">E=B/2</strong>{{ e }}</p >￼
      <p><strong class="data-label">F=C+D</strong>{{ f }}</p >￼
      <p><strong class="data-label">G=D-E</strong>{{ g }}</p >￼
     </div>￼
     <script src="https://cdn.jsdelivr.net/npm/vue@2.5.16/dist/vue.min.js"></script>￼
     <script type="text/javascript">￼
       let vm = new Vue({￼
          el: '#app',￼
          data () {￼
            return {￼
              a: 3,￼
              b: 4￼
            }￼
          },￼
          computed: {  // 计算属性￼
            c () {￼
              return this.a * 2 + 2￼
            },￼
            d () {￼
              return Number(this.a) + this.b * 2￼
            },￼
            e () {￼
              return this.b / 2￼
            },￼
            f () {￼
              return Number(this.c) + Number(this.d)￼
            },￼
            g () {￼
              return this.d - this.e￼
            }￼
         }￼
       })￼
     </script>
     ```

   - 数据绑定视图

     对象、Object.defineProperty(obj, key, { element.innerText = value}) ，element.innerText 一改变，视图就会重新渲染，所以视图和数据 obj 绑定了

     一：改 innerText 反应到视图          二：用 store[] 存储好数据

     ```javascript
     <span id="harry" style="line-height: 32px;"></span><br>￼
     <input id="trigger" type="text">￼
     <script type="text/javascript">￼
            let harry = document.getElementById('harry')￼
            let trigger = document.getElementById('trigger')￼
            let key = 'pro file'  // 对象属性键名￼
            let store = {}      // 辅助get取值￼
            let obj = {         // 对象￼
              pro file: ''￼
            }￼
            Object.defineProperty(obj, key, {￼
              set (value) {￼
                 harry.innerText = value  // 重点：修改DOM节点视图￼
                 store[key] = value￼
              },￼
              get () {￼
                 return store[key]￼
              }￼
            })￼
            trigger.addEventListener('keyup', function () {￼
              obj[key] = this.value￼
              console.log(obj[key])￼
            })￼
          </script>
     ```

### 二、Vue 语法

1. 插值绑定

   - 文本插值：双大括号 {{}}
   - HTMl 插值：v-html

2. 属性绑定

   - 指令 v-bind:

3. 类名和样式绑定

   由于类名 class 和 style 在节点属性中是比较奇怪的存在（虽然他们可接受的类型都是字符串，但类名实际上是由数组拼接而成，而样式则是由对象键值对拼接而成），所以 Vue 在绑定类名和样式时也采用不一样的机制。

   - 类名绑定：字符串、数组、对象三种方式 

     ```javascript
     style>￼
            .color-gray { color: gray; }￼
            .size-18 { font-size: 18px; }￼
            .style-italic { font-style: italic; }￼
          </style>￼
          <div id="app">￼
            <p class="color-gray size-18 style-italic">《Vue2.0 从入门到实战》，用￼
          心良苦，伴你成长</p >￼
            <p :class="classStr">《Vue2.0 从入门到实战》，用心良苦，伴你成长</p >￼
            <p :class="classArr">《Vue2.0 从入门到实战》，用心良苦，伴你成长</p >￼
            <p :class="classObj1">《Vue2.0 从入门到实战》，用心良苦，伴你成长</p >￼
            <p :class="classObj2">《Vue2.0 从入门到实战》，用心良苦，伴你成长</p >￼
          </div>￼
          <script src="https://cdn.jsdelivr.net/npm/vue@2.5.16/dist/vue.min.￼
          js"></script>￼
          <script type="text/javascript">￼
            let vm = new Vue({￼
              el: '#app',￼
              data () {￼
                 return {￼
                   classStr: 'color-gray size-18 style-italic',  // 拼接字符串￼
                   classArr: ['color-gray', 'size-18', 'style-italic'],  // 数组￼
                   classObj1: {  // 对象，绑定类名￼
                      'color-gray': true,￼
                      'size-18': true,￼
                      'style-italic': true￼
                   },￼
                   classObj2: {  // 对象，未绑定类名￼
                      'color-gray': 0,￼
                      'size-18': '',￼
                      'style-italic': false￼
                   }￼
                 }￼
              }￼
            })￼
          </script>
     ```

   - 样式绑定：只能用字符串和对象

4. 事件绑定

   - 指令 v-on

   - 常见事件修饰符：

     .stop(阻止冒泡)、.prevent(阻止默认行为)、.capture(阻止事件捕获)、.self(限制事件仅作用于自身)、.once(事件被触发一次后即解除监听)、.passive(移动端，限制事件永不调用preventDefault() 方法)

     例：`@submit.prevent="fn"`

   - 按键修饰符：`@keyup.enter="fn"` 或 `@keyup.13 = "fn"`

     ![image-20200918145159584](C:\Users\Alan\AppData\Roaming\Typora\typora-user-images\image-20200918145159584.png)

   - 鼠标修饰符：.left、.right、.middle

   - 组合修饰符：.ctrl、.alt、.shift、.meta(win 键)

5. 双向绑定

   - 指令v-model：v-model 和 v-show 是 Vue 核心功能中内置的、开发者不可自定义的指令（其他指令可以被开发者自定义）

     我们可以使用 v-model 为可输入元素（input & textarea）创建双向数据绑定，它会根据元素类型自动选取正确的方法来更新元素

   - 修饰符：.lazy、.number、.trim

   - 自定义组件：不止原生的输入元素可以使用 v-model 进行双向数据绑定，可用于自定义组件

6. 条件渲染和列表渲染

   - v-if （不在 DOM 之中）和 v-show（简单的切换 css 属性 display，在 DOM 之中）

   - v-for（item in items）：使用数组或对象，Vue 会把数组当作被观察者加入响应式系统中，当调用一些方法修改数组时，对应的视图将会同步更新

     ![image-20200918151407296](C:\Users\Alan\AppData\Roaming\Typora\typora-user-images\image-20200918151407296.png)

     注意：直接使用 下标、键名、对象设置 成员时，Vue 不会将其加入响应式系统

   - 列表渲染中的 key、

     当使用 v-for 时，最好为每个迭代元素提供一个值不重复的 key。

     当列表渲染被重新执行时，如果不使用 key，Vue 会为数组成员就近复用已存在的 DOM 节点

     ![image-20200918151757945](C:\Users\Alan\AppData\Roaming\Typora\typora-user-images\image-20200918151757945.png)

     当使用 key 时，Vue 会根据 key 的变化重新排列节点顺序，并移除 key 不存在的节点。

     实质上，key 的存在是为 DOM 节点标注一个身份信息，让 Vue 能够有迹可循追踪到数据对应的节点。在实战开发中，是否使用 key 都不会影响功能的实现

### 三、Vue 选项

通过选项，可以为实例绑定数据和事件。

1. 数据和方法

   - 数据选项（data）

     data 选项可接受的类型有 对象 、函数，不过在定义一个组件时只能使用函数类型

     ```
     // 创建一个 Vue 组件
     Vue.component('button-counter', {
     	data() {
     	  return {  // 必须使用函数类型
     	    counter: 1
     	  }
     	},
     	template:'<div>{{counter}}</div>'
     })
     ```

     Vue 会递归的将 data 中的数据加入响应式系统，但这些数据应该是声明时即存在的。

     开发者可以使用 $set 方法为 data 选项动态绑定数据，但其也无法挂载响应式数据到 $data 根节点上。

     TODO：

   - 属性选项（props）

     **对于开发者来说，代码的可复用性十分重要。在某些场景中，虽然业务的大部分特性都是一致的，但往往会有部分差异使得代码复用变得十分困难。**

     **Vue　为组件开发提供了属性（props）选项，我们可以使用它为组件注册动态特性，以处理业务间的差异，是代码可以复用于相似的应用场景。**

     props 选项可以是 数组 或 对象 类型，用于接收从父组件传递过来的参数，并允许开发者为其设置默认值、类型检测、校验规则

     ```javascript
     <div id="app">￼
            <color-text text="Hello World"></color-text>￼
            <br>￼
            <color-text></color-text>￼
            <br>￼
            <color-text color="#f78" text="Hello World"></color-text>￼
            <br>￼
            <color-text color="#43dt" text="Hello World"></color-text>￼
            <br>￼
          </div>￼
          <script src="https://cdn.jsdelivr.net/npm/vue@2.5.16/dist/vue.min.￼
          js"></script>￼
          <script type="text/javascript">￼
            Vue.component('color-text', {￼
              props: {￼
                 text: String,￼
                 color: {￼
                   type: String,￼
                   default: '#000',  // 默认值黑色￼
                   required: true,￼
                   validator (value) {  // 校验规则，判断颜色值是否合法￼
                      return /^#([0-9a-fA-F]{6}|[0-9a-fA-F]{3})$/.test(value)￼
                   }￼
                 }￼
              },￼
              template: '<span :style="{ color: color}">{{ text }}</span>'￼
            })￼
            let vm = new Vue({￼
              el: '#app'￼
            })￼
          </script>
     
     ```

   - 方法选项（methods）

     不要用箭头函数在其中定义方法，methods 中的方法将被绑定到 Vue 实例上，方法中的 this 也将自动执行 Vue 实例，此时使用箭头函数，this 将无法正确指向 Vue 实例

   - 计算属性（computed）

     计算属性设计的初衷在于减轻模板上的业务负担，当数据链上出现复杂衍生数据时，我们期望以一种易维护的方式使用它。

     由于计算属性依赖于响应式属性，所以仅当响应式属性变化时，计算属性才会被重新计算，而且得到的结果会被缓存，一直到响应式属性再次被修改。相比于使用 methods 函数求值，这是更为高效的机制

     允许为 computed 属性赋值

     ```
     computed: {￼
                 noSpaceMsg: {￼
                   set (value) {￼
                      this.message = value￼
                   },￼
                   get () {￼
                      return this.message.replace(/\s/g, '')￼
                   }￼
                 }￼
              }￼
     ```

   - 侦听属性（watch）

     Vue 允许开发者使用侦听属性为实例添加被观察对象，**并在对象被修改时调用开发者自定义的方法**。

     ```javascript
     let vm = new Vue({￼
       el: '#app',￼
       data () {￼
       	return {￼
            message: 'WAS IT A CAR OR A CAT I SAW',￼
            // 如果允许被赋值，何不直接放在data中?￼
            noSpaceMsg: 'WASITACARORACATISAW'￼
         }￼
       },￼
       watch: {  // 使用watch实现：当元数据变化时，同步衍生数据的状态￼
          message (newValue, oldValue) {// newValue: 修改后的值； oldValue:￼修改前的值￼
            // wacth 比 computed 重要的是这里可以执行一些方法 
            this.noSpaceMsg = this.message.replace(/\s/g, '')￼
          }￼
       }￼
     })
     ```

     由于 watch 更注重处理数据变化时的业务逻辑，而 computed 更注重衍生数据，watch 还优于可以修改异步数据，**watch 里面可以执行一些异步方法，根据返回修改数据**

     ```javascript
     import axios from 'axios'￼
          let vm = new Vue({￼
            el: '#app',￼
            data () {￼
              return {￼
                 message: '书山有路勤为径，学海无涯苦做舟。',￼
                 remoteMsg: ''￼
              }￼
            },￼
            watch: {￼
              message (newValue, oldValue) {￼
                 axios({  // 发送ajax异步请求￼
                   method: 'GET',￼
                   url: '/someurl',￼
                   params: {￼
                      message: newValue￼
                   }￼
                 }).then(res => {￼
                   this.remoteMsg = res.data.message  // 接收响应后，异步修改数据值￼
                 })￼
              }￼
            }￼
          })
     ```

2. DOM 渲染

   - 指定被挂载元素：el 选项指定 Vue 实例挂载目标，属性值仅限于 CSS 选择器和 DOM 节点对象。

     也可以用 $mount() 来挂载实例，` vm.$mount('#app')`

   - 渲染函数 render

     ```
     render(createElement) {	//createElement 简写 h
     	return createElement('p', 'hello world')
     }
     ```

   - 选项的优先级：render、template、el

3. 封装复用

   - filters 过滤器

   - directives 自定义指令：

     Vue 为自定义指令提供了如下几个钩子函数

     ```
     ●bind：指令与元素绑定时调用。
     ●inserted：指令绑定的元素被挂载到父元素上时调用。
     ●update：指令所在VNode更新时调用，可能发生在其子VNode更新之前。
     ●componentUpdated：指令所在VNode及其子VNode全部更新后调用。
     ●unbind：指令与元素解绑时调用。
     同时，钩子函数会被传入以下参数：
     ●el：指令所绑定元素，可用于操作DOM。
     ●binding：包含指令相关属性的对象。binding包含以下属性：
     ●name：指令名称。
     ●value：指令绑定的值，如在v-some=“2*2”中，绑定值为4。
     ●oldValue：指令值改变前的值，仅在update和componentUpdated钩子函数中可用。
     ●expression：字符串类型的指令表达式，如在v-some=“2*2”中，值为“2*2”。
     ●arg：传给指令的参数，如在v-some:someValue中，值为“someValue”。
     ●modifiers：修饰符对象，如在v-some.upper中，值为{upper: true}。
     ●vnode：虚拟节点。
     ●oldNode：虚拟节点更新前的值，仅在update和componentUpdated钩子函数中可用。
     ```

   - components 组件的注册

     用于为组件注册从外部引入的组件，由于子组件并非在全局定义，因此不可以直接在父组件的作用域内使用。常用场景有引入第三方库和自定义组件

     ```javascript
          <div id="app">￼
            <easy-title></easy-title>￼
            <easy-wish></easy-wish>￼
            <easy-motto></easy-motto>￼
          </div>￼
          <script src="https://cdn.jsdelivr.net/npm/vue@2.5.16/dist/vue.js"></￼
          script>￼
          <script type="text/javascript">￼
            let EasyTitle = {  // EasyTitle组件￼
              name: 'EasyTitle',￼
              template: '<h1>大器当成</h1>'￼
            }￼
            let EasyMotto = {  // EasyMotto组件￼
              name: 'EasyMotto',￼
              template: '<p>过一方水土，历一番人事，方知天地不仁，万物刍狗</p >'￼
            }￼
            let EasyWish = {  // EasyWish组件￼
              name: 'EasyWish',￼
              template: '<p>白发渔樵隐深山，浮名穷利岂愿沾。</p >'￼
            }￼
            let vm = new Vue({  // Vue实例￼
              el: '#app',￼
              components: { EasyTitle, EasyMotto, EasyWish }￼
            })￼
          </script>
     ```

   - mixins 混入

     用于注册在外部封装好的代码，不过这些代码更加碎片化，不像组件成体系，混入的目的在于灵活的分发组件中一些可复用的功能

### 四、Vue 内置组件

1. 组件服务

   - 动态组件：在某些场景，往往需要我们动态切换页面部分区域的视图，使用内置组件很方便

     component 接受一个 is 属性，is 的值为父组件中注册过的组件的名称：
     `<component :is="view"></component> `

   - 使用插槽分发内容：具名插槽和默认插槽

     通过 props 选项，组件可以接受多态的数据，不过，如果我们希望组件也能接收多态的 DOM 结果呢

     可以通过使用 props 配合 v-html，Vue 提供了一种更简单的选择，使用内置组件 slot 插槽

   - 组件的缓存

   - keep-alive 是一个抽象组件，即它既不渲染任何 DOM 元素，也不会出现在组件结构树中。我们可以使用它缓存一些非动态的组件实例（没有或不需要数据变化），以保留组件状态或减少重新渲染的开销。

     keep-alive 应该出现在组件被移除之后需要再次挂载的地方，比如使用动态组件时

     ```
     <keep-alive>
     	<component :is="view"></component>
     </keep-alive>
     ```

     或者使用 v-if 时

     ```
     <keep-alive>
     	<one v-if="isone"></one>
     	<two v-else></two>
     </keep-alive>
     ```

     它还可以接受 include 和 exclude 两个属性：

     include ：字符串或正则表达式，只有被匹配的会被缓存

     exclude：字符串或正则表达式，被匹配的不会被缓存

     当组件在 keep-alive 内被切换时，它的 actived 和 deactived 这两个生命周期钩子函数会被执行

2. 过渡效果

   - 单节点的过渡

     Vue提供了标签为 transition 的内置组件，在下列情形中，我们可以给任何元素和组件添加进入／离开时的过渡动画：
     ●元素或组件初始渲染时
     ●元素或组件显示／隐藏时（使用v-if或v-show进行条件渲染时）
     ●元素或组件切换时
     Vue允许用户使用CSS和JS两种方式来定义过渡效果。
     在使用CSS过渡时，我们需要预置符合Vue规则的带样式的类名，这些类名用于定义过渡不同阶段时的样式：
     ●v-enter：定义进入过渡的开始状态。在元素被插入前生效，被插入后的下一帧移除。
     ●v-enter-active：定义进入过渡生效时的状态。在整个进入过渡阶段中应用，在元素被插入之前生效，在过渡／动画完成之后移除。这个类可以用来定义进入过渡的过程时间、延迟和曲线函数等。
     ●v-enter-to：（Vue 2.1.8及以上版本）定义进入过渡结束时的状态。在元素被插入后的下一帧生效（此时v-enter被移除），在过渡／动画完成之后移除。
     ●v-leave：定义离开过渡的开始状态。在离开过渡被触发时立刻生效，下一帧被移除。
     ●v-leave-active：定义离开过渡生效时的状态。在整个离开过渡的阶段中应用，在离开过渡被触发时立刻生效，在过渡／动画完成之后移除。这个类可以被用来定义离开过渡的过程时间、延迟和曲线函数。
     ●v-leave-to：（Vue 2.1.8版及以上版本）定义离开过渡的结束状态。在离开过渡被触发之后下一帧生效（此时v-leave被移除），在过渡／动画完成之后移除。
     当实例中存在多个不同的动画效果时，我们可以使用自定义前缀替换v-，比如使用slide-enter替换v-enter，不过这需要赋予transition元素name属性。

   - 多节点的过渡：transition-group

### 五、Vue 项目化

一个完整的前端开发环境应该具备预编译模板、注入依赖、合并压缩资源、分离开发和生产环境、提供一个模拟的服务端环境。

1. Vue 提供了 Vue CLI

2. 前端路由

   - 简单实现：根据 URL 分发视图，有两个核心操作：一是监听浏览器地址变化，二是动态加载视图

     ```javascript
          <script  src="https://cdn.jsdelivr.net/npm/vue@2.5.16/dist/vue.js"></￼
          script>￼
          <div id="app">￼
              <ul>￼
                  <li><router-link to="/">Home</router-link></li>￼
                  <li><router-link to="/about">About</router-link></li>￼
              </ul>￼
              <router-view></router-view>￼
          </div>￼
          <script type="text/javascript">￼
            let Home = {￼
              template: '<h1>This is Home!</h1>'￼
            }￼
            let About = {￼
              template: '<h1>This is About!</h1>'￼
            }￼
            let routes = [  // 定义路由规则￼
              {￼
                path: '/',￼
                component: Home￼
              },￼
              {￼
                path: '/about',￼
                component: About￼
              }￼
            ]￼
            let RouterLink = {￼
              props: ['to'],￼
              template: '<a :href="to"><slot name="default"></slot></ a>'￼
            }￼
            let RouterView = {￼
              data () {￼
                return {￼
                  url: window.location.pathname  // 获取浏览器地址￼
            }￼
              },￼
              computed: {￼
                ViewComponent () {  // 根据浏览器地址返回相应组件￼
                  return routes.ﬁnd(route => route.path === this.url).component￼
                }￼
              },￼
              render (h) {￼
                return h(this.ViewComponent)￼
              }￼
            }￼
            /* eslint-disable */￼
            let vm = new Vue({￼
              el: '#app',￼
              components: { RouterLink, RouterView }￼
            })￼
          </script>
     ```

   - 原生 JS 实现

     ```javascript
          <div>￼
            <ul>￼
              <li>< a href=" ">Home</ a></li>￼
              <li>< a href="#/about">About</ a></li>￼
            </ul>￼
            <!-- 动态视图被挂载的元素 -->￼
            <div id="view"></div>￼
          </div>￼
          <script type="text/javascript">￼
            let Home = '<h1>This is Home!</h1>'  // 视图模板Home￼
            let About = '<h1>This is About!</h1>'  // 视图模板About￼
            let Router = function (el) {  // 定义路由类￼
              let view = document.getElementById(el)￼
              let routes = []  // 路由规则列表￼
              let load = function (route) {  // 加载视图￼
                 route && (view.innerHTML = route.template)￼
              }￼
              let redirect = function () {  // 分发视图￼
                 let url = window.location.hash.slice(1) || '/'￼
                 for (let route of routes) {￼
                   url === route.url && load(route)￼
                 }￼
              }￼
              this.push = function (route) {  // 添加路由规则￼
                 routes.push(route)￼
              }￼
              window.addEventListener('load', redirect, false)  // 页面加载时￼
              window.addEventListener('hashchange', redirect, false)  // URL变化时￼
            }￼
            let router = new Router('view')  // 实例化路由￼
            router.push({  // 添加路由规则￼
              url: '/',￼
              template: Home￼
            })￼
            router.push({￼
              url: '/about',￼
              template: About￼
            })￼
          </script>
     ```

   - Vue Router

     基础路由、动态路由、嵌套路由、编程式路由、使用 Vue CLI 快速构建项目中的 router

3. 状态管理 Vuex

   Vuex 用于管理分散在各个组件中的数据

   每一个 Vuex 应用的核心都是一个 store，与普通的全局对象不同的是，基于 Vue 数据与视图绑定的特点，当 store 中的数据发生变化时，与之绑定的视图也会被重新渲染。

   这是一个单向的过程，因为 store 不允许被直接修改。改变 store 中的状态的唯一方法就是显示的提交 mutation

   Vuex 中 5 个重要概念：State、Getter、Mutation、Action、Module

   State的用法如下：

   ```javascript
   new Vuex.Store({  // 创建仓库￼
     state: {￼
        count: 1￼
     }￼
   })
   ```

   在组件中，我们可以直接使用 $store.state.count（前提是 store 已被注册到实例中），也可以先用mapState 辅助函数将其映射下来，代码如下：

   ```
   import { mapState } from 'vuex'￼
     export default {￼
        computed: {￼
          ...mapState(['count'])  // ...是ES6中的对象展开运算符￼
        }￼
   }
   ```

   

   Getter 维护由 State 派生的一些状态，这些状态随着 State 状态的变化而变化。与计算属性一样，Getter中的派生状态在被计算之后会被缓存起来，当重复调用时，如果被依赖的状态没有变化，那么 Vuex 不会重新计算派生状态的值，而是直接采用缓存值。
   Getter 的用法如下：

   ```
        new Vuex.Store({  // 创建仓库￼
          state: {￼
            count: 1￼
          },￼
          getters: {￼
            tenTimesCount (state) {  // Vuex为其注入state对象￼
               return state.count * 10￼
            }￼
          }￼
        })
   ```

   在组件中，我们可以直接使用$store.getters.tenTimesCount，也可以先用mapGetters辅助函数将其映射下来，代码如下：

   ```
        import { mapGetters } from 'vuex'￼
        export default {￼
          computed: {￼
            ...mapGetters(['tenTimesCount']) // ...是ES 6中的对象展开运算符￼
          }￼
        }
   ```

   

   Mutation提供修改State状态的方法。
   Mutation的用法如下：

   ```
        new Vuex.Store({  // 创建仓库￼
          state: {￼
            count: 0￼
          },￼
          mutations: {￼
            addCount (state, num) {￼
               state.count += num || 1￼
            }￼
          }￼
        })
   ```

   在组件中，我们可以直接使用 store.commit 来提交 mutation，代码如下：

   ```
        methods: {￼
          addCount () {￼
            this.$store.commit('addCount')  // store被注入到Vue实例中后可使用this.$store￼
          }￼
        }
   ```

   也可以先用mapMutation辅助函数将其映射下来，代码如下：

   ```
        import { mapState, mapMutations } from 'vuex'￼
        export default {￼
          computed: {￼
            ...mapState(['count'])  // ...是ES 6中的对象展开运算符￼
          },￼
          methods: {￼
            ...mapMutations(['addCount']),￼
            ...mapMutations({  // 为mutation赋别名，注意冲突，此方法不常用￼
               increaseCount: 'addCount'￼
            })￼
          }￼
        }
   ```

   

   Action 类似 Mutation，不同在于：

   - Action 不能直接修改状态，只能通过提交 mutation 来修改。
   - Action 可以包含异步操作。
   - Action 的用法如下：

   ```
        new Vuex.Store({  // 创建仓库￼
          state: {￼
            count: 0￼
          },￼
          mutations: {￼
            addCount (state, num) {￼
               state.count += num || 1￼
            }￼
          },￼
          actions: {￼
            // context 具有和 store 实例相同的属性和方法￼
            // 可以通过 context 获取 state 和 getters 中的值，或者提交 mutation 和分发其他的 action￼
            addCountAsync (context, num) {￼
               setInterval(function () {￼
                 if (context.state.count < 2000) {￼
                    context.commit('addCount', num || 100)￼
                 }￼
               }, num || 100)￼
            }￼
          }￼
        })
   ```

   在组件中，我们可以直接使用 store.dispatch 来分发 action，代码如下：

   ```
        methods: {￼
          addCountAsync (num) {￼
            this.$store.dispatch('addCountAsync', num)￼
          }￼
        }
   ```

   或者使用 mapActions 辅助函数先将其映射下来，代码如下：

   ```javascript
        import { mapState, mapActions } from 'vuex'￼
        export default {￼
          computed: {￼
            ...mapState(['count'])  // ...是ES 6中的对象展开运算符￼
          },￼
          methods: {￼
            ...mapActions(['addCountAsync']),￼
            ...mapActions({  // 为action赋别名，注意冲突，此方法不常用￼
               increaseCountAsync: 'addCountAsync'￼
            })￼
          }￼
        }
   ```

   

   

