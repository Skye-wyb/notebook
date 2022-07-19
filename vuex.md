vuex

#### 1、vuex概念

Vuex 是一个专为 Vue.js 应用程序开发的**<font color='red'>状态管理</font>模式**。它采用集中式存储管理应用的所有组件的状态，并

以相应的规则保证状态以一种可预测的方式发生变化。Vuex 也集成到 Vue 的官方调试工具 devtools 

extension，提供了诸如零配置的 time-travel 调试、状态快照导入导出等高级调试功能。 

**Vuex是[vue](http://www.javanx.cn/tag/vue/)框架中状态管理。** 

> **<font color='hotpink'>vuex是专门在vue中实现集中式状态（数据）管理的一个vue插件</font>**，对vue应用中多个组件的共享状态进行
>
> 集中式的管理（读、写）也是一种组件间通信的方式，且适用于任意组件间通信。 

#### 2、vuex的使用

使用场景：<font color='green'>**多个组件依赖于同一个状态 、来自不同组件的行为需要变更同一状态** </font>

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20210104110854783.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzYzODk2OA==,size_16,color_FFFFFF,t_70) 

#### 3、vuex的组成

> state：数据
>
> actions：可以包含异步操作
>
> mutations：唯一可以修改state数据的场所
>
> getters：类似于vue组件中的计算属性，对state数据进行计算（会被缓存）
>
> modules：模块化管理store（仓库），每个模块拥有自己的 state、mutation、action、getter

#### 4、vuex使用：

##### 安装

![1651454028918](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651454028918.png)

##### 创建store仓库

src/store/index.js

![1651454330143](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651454330143.png)

##### 全局注册仓库

main.js

![1651454398079](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651454398079.png)



##### 案例

![1651455390867](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651455390867.png)

Count.vue

![1651455430470](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651455430470.png)

store/index.js

![1651455460868](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651455460868.png)

**注意：如果在action中没有什么业务逻辑，可以直接在组件的方法中通过this.$store.commit()直接commit和mutations对话**

#### getters配置项

相当于计算属性

![1651457267937](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651457267937.png)

使用：

**读取getters：$store.getters.bigCount**

![1651457299406](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651457299406.png)

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651457323944.png" alt="1651457323944" style="zoom:50%;" />

**（state相当于vue组件中的data，getters相当于vue组件中的computed）**

> **<font color='hotpink'>组件中读取vuex中的数据：$store.state.count</font>**
>
> **组件中修改vuex中的数据：`$store.dispatch('action中的方法名',数据)`或`$store.commit('mutations中的方法名'),数据)`**

#### mapState,mapGetters

![1651458280495](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651458280495.png)

1. mapState方法：用于帮助我们映射state中的数据作为计算属性

   ![1651459542186](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651459542186.png)

2. mapGetters方法：用于帮助我们映射getters中的数据作为计算属性

   ![1651459553870](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651459553870.png)

3. mapActions方法：用于帮助我们生成与action对话的方法，即：包含$store.dispatch(xxx)的函数

   ![1651459570260](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651459570260.png)

4. mapMutations方法：用于帮助我们生成与mutations对话的方法，即：包含$store.commit(xxx)的函数

   ![1651459586125](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651459586125.png)





































store-->index.js

![1648783484450](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648783484450.png)

home.vue

![1648783520710](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648783520710.png)

## vuex的安装

~~~
npm install vuex@next --save
~~~

> 1. Vuex 的状态存储是响应式的。当 Vue 组件从 store 中读取状态的时候，若 store 中的状态发生变化，那么相应的组件也会相应地得到高效更新。
> 2. 你不能直接改变 store 中的状态。改变 store 中的状态的唯一途径就是显式地**提交 (commit) mutation**。这样使得我们可以方便地跟踪每一个状态的变化，从而让我们能够实现一些工具帮助我们更好地了解我们的应用。

## state

<font color='red'>state存放状态，</font>**在组件里获取状态使用this.$store.state获取**，count是state里面的属性名，也可以使用辅助函数

mapstate

![1648783906911](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648783906911.png)

## getter

getter是 **store 的计算属性**，getter 的返回值会根据它的依赖被缓存起来，且只有当它的依赖值发生了改变才

会被重新计算。接受state作为第一个参数，**通过this.$store.getters调用**，也可以使用辅助函数mapgetters将 

store 中的 getter 映射到局部计算属性

![1648783958387](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648783958387.png)

## mutation

mutation类似于事件，可以改变state的状态，必须同步操作，在组件中改变状态时通过**this.$store.commit('事**

**件名'，传递的参数)调用mutation里面的事件** 

![1648784008596](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648784008596.png)

## action

action和mutation类似，只不过action提交的是mutation，包含异步操作，action通过this.$store.dispatch()调用 

![1648784034535](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648784034535.png)

## module

module可以将store分割成不同的模板，每个模板里面包含state、getter、mutation、action 

![1648784102109](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648784102109.png)

#### 示例代码

结构：

![1648784592028](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648784592028.png)

cart.js

![1648784416658](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648784416658.png)

store.js中将其挂载：

![1648784481418](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648784481418.png)

user.js

![1648784554414](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648784554414.png)



