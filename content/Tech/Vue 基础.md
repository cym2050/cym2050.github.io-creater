---
title: "Vue 基础"
date: 2020-10-05T23:34:30+08:00
draft: true
---

## 一、Vue

1. 基本使用

   - computed 有缓存

   - watch 监听引用类型，拿不到 oldval，watch 如何深度监听

     ```javascript
     <template>
         <div>
             <input v-model="name"/>
             <input v-model="info.city"/>
         </div>
     </template>
     
     <script>
     export default {
         data() {
             return {
                 name: '双越',
                 info: {
                     city: '北京'
                 }
             }
         },
         watch: {
             name(oldVal, val) {
                 // eslint-disable-next-line
                 console.log('watch name', oldVal, val) // 值类型，可正常拿到 oldVal 和 val
             },
             info: {
                 handler(oldVal, val) {
                     // eslint-disable-next-line
                     console.log('watch info', oldVal, val) // 引用类型，拿不到 oldVal 。因为指针相同，此时已经指向了新的 val
                 },
                 deep: true // 深度监听,可以监听到里面值的变化，但还是拿不到oldval
             }
         }
     }
     </script>
     ```

   - class 和 style 属性赋值方式 字符串、数组、对象

   - v-show 使用 display：none，还在DOM中，频繁显隐就用 v-show

   - v-if 不在 DOM 结构中

   - 循环渲染：v-for 遍历数组和对象、key 的重要性、v-for 和 v-if 不能一起使用

   - 事件对象：event 是原生事件，事件被挂载在当前元素，$event 在有其他参数时的写法

   - 修饰符 exact

   - 表单：v-model、textarea、checkbox、radio、select、修饰符

     

2. 组件使用

   - props 和 $emit

     调用父组件传过来的事件：this.$emit('fn', value)

     调用自定义事件：event.$emit('fn', value)

   - 组件间通讯，自定义事件

     

     自定义组件 绑定在 event 对象上

     ```javascript
     //利用 Vue 实例完成发布订阅
     event.js
     import Vue from 'vue'
     export default new Vue()
     
     //导入
     import event from './event'
     
     // 绑定自定义事件
     mounted() {
       event.$on('onAddTitle', this.addTitleHandler)
     }
     
     // 调用自定义事件
     event.$emit('onAddTitle', this.title)
     ```

   - 组件生命周期

     创建、挂载、更新、销毁

     <img src="https://cn.vuejs.org/images/lifecycle.png" alt="Vue 实例生命周期" style="zoom:50%;" />

     单组件：

     beforeCreate、create、beforeMount、mounted、beforeUpdate、updated、beforeDestroy、destroyed

     父子组件：

     - 加载：父beforeCreate、父created、子beforeCreate、子created、子mounted、父mounted、
     - 更新：父beforeUpdate、子beforeUpdate、子updated、父updated
     - 销毁：父beforeDestroy、子beforeDestroy、子destroyed、父destroyed、

3. 高级特性

   - 自定义 v-model

     ```
     Vue.component('base-checkbox', {
       model: {
         prop: 'checked',
         event: 'change'
       },
       props: {
         checked: Boolean
       },
       template: `
         <input
           type="checkbox"
           :checked="checked"
           @change="$emit('change', $event.target.checked)"
         >
       `
     })
     ```

     使用：

     ```
     <base-checkbox v-model="lovingVue"></base-checkbox>
     ```

     

   - $nextTick() 

     - Vue 是异步渲染：就是说数据改变后还得等栈里的 JavaScript  代码执行完
     - data 改变后，DOM 不会立刻渲染
     - $nextTick 会在 DOM 渲染之后被触发，以获取最新的 DOM 节点

     ```
     template>
       <div id="app">
         <ul ref="ul1">
             <li v-for="(item, index) in list" :key="index">
                 {{item}}
             </li>
         </ul>
         <button @click="addItem">添加一项</button>
       </div>
     </template>
     
     <script>
     export default {
       name: 'app',
       data() {
           return {
             list: ['a', 'b', 'c']
           }
       },
       methods: {
         addItem() {
             this.list.push(`${Date.now()}`)
             this.list.push(`${Date.now()}`)
             this.list.push(`${Date.now()}`)
     
             // 1. 异步渲染，$nextTick 待 DOM 渲染完再回调
             // 3. 页面渲染时会将 data 的修改做整合，多次 data 修改只会渲染一次
             this.$nextTick(() => {
               // 获取 DOM 元素
               const ulElem = this.$refs.ul1
               // eslint-disable-next-line
               console.log( ulElem.childNodes.length )
             })
         }
       }
     }
     </script>
     ```

   - slot

     普通：

     ![image-20200927152929065](C:\Users\Alan\AppData\Roaming\Typora\typora-user-images\image-20200927152929065.png)

     ![image-20200927152956988](C:\Users\Alan\AppData\Roaming\Typora\typora-user-images\image-20200927152956988.png)

     作用域插槽：能拿到 slot 里面的值

     ![image-20200927153354899](C:\Users\Alan\AppData\Roaming\Typora\typora-user-images\image-20200927153354899.png)

     ![image-20200927153429363](C:\Users\Alan\AppData\Roaming\Typora\typora-user-images\image-20200927153429363.png)

     具名插槽：

     ![image-20200927153632481](C:\Users\Alan\AppData\Roaming\Typora\typora-user-images\image-20200927153632481.png)

   - 动态组件  :is = 'component-name'

     ![image-20200927153818392](C:\Users\Alan\AppData\Roaming\Typora\typora-user-images\image-20200927153818392.png)

   - 异步组件：在组件要显示时 用 http 请求

     - import() 函数

     - 按需加载，异步加载大组件

       ![image-20200927155100509](C:\Users\Alan\AppData\Roaming\Typora\typora-user-images\image-20200927155100509.png)

   - keep-alive

     缓存组件，频繁切换不需要重复渲染，用 keep-alive 包起来，就是组件v-if=false 时不 destroy

   - mixin：

     多个组件有相同的逻辑

     Vue 3 的 Composition API 旨在解决这些问题

     缺点：冲突，代码难以阅读

     ![image-20200927155957857](C:\Users\Alan\AppData\Roaming\Typora\typora-user-images\image-20200927155957857.png)

4. Vuex

   state、getter、action、mutation、modules

   dispatch、commit、mapState、mapGetters、mapActions、mapMutations

   ![image-20200919183113625](C:\Users\Alan\AppData\Roaming\Typora\typora-user-images\image-20200919183113625.png)

5. Vue-router

   - 路由模式（hash、H5 history）

     hash： 带 # 号，没有后端时使用

     H5 history：没有 #，需要后端支持

   - 路由配置（动态路由、懒加载）

     动态路由

     ![image-20200927160718539](C:\Users\Alan\AppData\Roaming\Typora\typora-user-images\image-20200927160718539.png)

     懒加载：通过 import() 函数，使用时才会 http 请求

     ![image-20200927160739110](C:\Users\Alan\AppData\Roaming\Typora\typora-user-images\image-20200927160739110.png)





### 三、Vue 3

1. Vue 3 升级内容
   - 全部用 ts 重写（响应式、vdom、模板编译）
   - 性能提示，代码量减少
   - 调整部分 API
2. Proxy 实现响应式
   - 基本使用
   - Reflect
   - 实现响应式