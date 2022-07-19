## 面试题：computed、methods、watch有什么区别？

> 1、computed  vs methods区别
>
> - computed是有缓存的
> - methods没有缓存
>
> 2、computed vs watch区别
>
> - watch是监听，数据或路由发生了改变才可以响应（执行）
> - computed计算某一属性的改变，如果某个值发生了改变，计算属性会监听到并进行返回
> - watch是当前监听到数据改变了，才会执行内部代码

## 面试题：props和data谁的优先级更高？

> props --> methods --> data --> computed --> watch

## 面试题：双向绑定原理



## 面试题：diff算法



## 面试题：讲一下MVVM



## 面试题：介绍一下SPA以及SPA有什么缺点？



## 面试题：Vue路径传值



## 面试题：路由导航卫士有哪些？



## 面试题：Vue路由模式



## 面试题：SEO

### TDK三大标签SEO优化（★★）

#### SEO是什么

<font color='red'>**SEO（Search Engine Optimization）**汉译为搜索引擎优化，是一种利用搜索引擎的规则提高网站在有关搜索引擎内自然排名的方式。</font>

**SEO** 的目的是对网站进行深度的优化，从而帮助网站获取免费的流量，进而在搜索引擎上提升网站的排名，提高网站的知名度。

页面必须有三个标签用来符合 SEO 优化

![](C:/Users/86186/Desktop/前端开发笔记/images/SEO优化.png)

#### TDK是什么

##### T -- Title（网站标题）

**title** 具有不可替代性，是我们内页的第一个重要标签，是搜索引擎了解网页的入口和对网页主题归属的最佳判断点。

**建议：**网站名（产品名）- 网站的介绍  （尽量不要超过30个汉字）

**例如：**

- 京东(JD.COM)-综合网购首选-正品低价、品质保障、配送及时、轻松购物！
- 小米商城 - 小米5s、红米Note 4、小米MIX、小米笔记本官方网站

##### D -- description（网站描述）

简要说明我们网站主要是做什么的。

**我们提倡**，description 作为网站的总体业务和主题概括，多采用“我们是…”、“我们提供…”、“×××网作为…”、“电话：010…”之类语句。

**例如：**

`<meta name="description" content="京东JD.COM-专业的综合网上购物商城,销售家电、数码通讯、电脑、家居百货、服装服饰、母婴、图书、食品等数万个品牌优质商品.便捷、诚信的服务，为您提供愉悦的网上购物体验!" />`

##### K -- keywords （关键字）

**keywords 是页面关键词**，是搜索引擎的关注点之一。

keywords 最好限制为 6～8 个关键词，关键词之间用英文逗号隔开，采用 关键词1,关键词2 的形式

**例如：**

`<meta name= " keywords" content="网上购物,网上商城,手机,笔记本,电脑,MP3,CD,VCD,DV,相机,数码,配件,手表,存储卡,京东" />`

# 

## JavaScript

- 如何判断一个对象是不是空对象
- 0.1+0.2 == 0.3？？
- Number()的存储空间是多大，如果后台发送了一个超过最大字节的数字怎么办？
- Proxy
- 原型链问题（必问）

![1650692762607](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650692762607.png)

![1650692782679](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650692782679.png)

- 异步问题，说出输出结果顺序

![1650692802441](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650692802441.png)

![1650692825200](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650692825200.png)

## CSS

- 垂直居中如何实现
- align-center中适配iOS8（-webkit-align-item:center)
- rem的理解
- .div和 div > div > div的优先级
- display:none, visibility:hidden, opactiy:0 的区别
- BFC，如何形成BFC
- BFC与IFC的区别
- BFC会与float元素相互覆盖吗？为什么？举例说明

## 框架

### Vue

- vue@3.0中的preset配置
- 父组件A和其子组件B/子组件C，B/C进行通信的方式
- 组件中eventbus的实现
- 组件如何设置并被使用
- 如何来创建多个项目
- 多个组件$message如何实现最后触发的在最上面
- 如何实现在图片被加载之前的占位符一个image，宽高比位16:9

### React

- 为什么要使用Redux，是不是所有的项目都必须要使用Redux

## 运行环境

- 讲讲回流和重绘
- 如何解决页面卡顿（前端性能优化是一个永恒的话题，综合性很高的一个问题，尽可能回答）
- 浏览器从输入url到页面渲染的整个流程
- ssr和前后端分离的区别
- 如何实现list的无限滚动（节流？）
- 如何处理跨域
- git使用过吗？用过哪些指令？git具体的工作流是什么（git必问）
- git merge、git rebase的区别

## HTTP

- POST一般可以发送什么类型的文件
- HTTP缓存了解了哪些？
- post和put的区别
- Cookie中的操作以及httponly
- 如何判断一个IP是不是国内IP
- 说一说你了解的express中间件
- 浏览器请求数据问题，请求数据到请求结束与服务器进行了几次交互
- TCP为什么要四次握手
- cookie有哪些属性、大小、浏览器如何禁止别人访问cookie
- localstorage、sessionstorage的区别
- 在交互过程中如果数据传送完了，还不想断开连接怎么办，怎么维持
- websocket和ajax的区别
- fetch API和传统request的区别

## 手撕代码

- 实现一个tab组件
- 数组中数字出现的次数
- 反转链表，原地解法



# 2

### 一

线程和进程大概是什么样的关系

js是单线程还是多线程

js里实现异步有哪几种方式

用promise实现一个sleep函数，构造一个使用这个sleep函数的场景或函数



# Vue的生命周期

# 数据双向绑定的原理

# 

# SPA单页⭐⭐⭐

# 

# MVVM⭐⭐⭐

# 

# Vue的响应式原理⭐⭐⭐（双向数据绑定）

# 

# data为什么是函数⭐⭐

# 

# v-model的原理⭐

# 

# v-if和v-show的区别⭐⭐⭐

# 

# computed、watch和method⭐⭐

# 

# Vue的生命周期⭐⭐⭐

# 

# 父子组件生命周期顺序⭐⭐

# 

# Vue组件间通信的方式⭐⭐⭐

# 

# Vue的单向数据流⭐

# 

# keep-alive组件⭐

# 

# slot插槽⭐

# 

# Vue检测数组或对象的变化⭐⭐

# 

# 虚拟DOM⭐⭐⭐

# 

# Vue中key的作用⭐⭐

# 

# nextTick的原理⭐⭐

# 

# Vuex⭐⭐⭐

# 

# Vue-router的两种模式⭐⭐

# 

# vue-router有哪几种导航钩子⭐



# 

# 路由传参（对象写法）path是否可以结合params参数一起使用？

#### 介绍路由传参的对象写法

> **对象形式传参：需要给路由命名 **
>
> ![1651136194874](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651136194874.png)

### 不可以，原因：

![1651136364981](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651136364981.png)

无法实现相应的路由跳转，并且出现了警告！！！

**<font color='hotpink'>路由跳转传参时，对象的写法可以是name和path形式，但是需要注意：path写法不能与params参数一起使用，params只能通过name来引入路由！！！</font>**

> <font color='red'>params参数不能和path一起使用，params参数只能和name一起使用；query参数可以和name或path一起使用。 </font>

# 

# 如何指定params参数可传不可传

<font color='red'>当指定了params参数的占位后，如果不传递params参数，会导致URL路径发生错误。</font>

**<font color='blue'>解决方法：在指定占位时在最后加上问号（?），就可以解决不传递params，URL路径错误问题</font>** 

![1651137046379](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651137046379.png)

**但是如果params参数传递的是空的字符串。**<font color='green'>上述加问号的方式还是不能解决URL路径错误问题。</font>

**解决方法：<font color='red'>在跳转时，参数传递使用undefined</font>**

![1651137130021](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651137130021.png)

# 

# 路由组件能不能传递props参数

### 能

传递的props参数通过组件中配置props属性接收即可使用。有三种方式，需要在路由文件中配置 ：

在跳转后的页面中通过props接收参数：

![1651137400533](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651137400533.png)

> <font color='hotpink'>第一种：布尔值形式，默认只能接收params参数</font>
>
> ![1651137259867](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651137259867.png)

> <font color='red'>第二种：对象形式，可以给组件传递额外的值</font>
>
> ![1651137357806](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651137357806.png)

>  <font color='blue'>第三种：**函数形式（较常用），函数的参数可以获取到$route，进而可以获取params和query** </font>
>
> ![1651137549408](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651137549408.png)

# 

# 编程式路由导航跳转时（参数不变），为什么多次执行会抛出NavigationDuplicated异常？怎么解决？

![1651137679227](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651137679227.png)

原因：**<font color='hotpink'>在vue-router的底层使用了promise来处理异常，当多次点击时抛出异常是vue的设计。</font>**

声明式导航不存在这个问题，因为它的vue-router底层已经处理好了

this.$router.push/replace返回的是promise

![1651137849715](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651137849715.png)

![1651138516456](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651138516456.png)

### 解决方法1

因为返回的是Promise，可以在this.$router.push()时传递两个空箭头函数，代表成功的回调和失败的回调（resolve、reject），可以解决多次执行跳转时报错：

- 缺点：治标不治本
- 在其他组件中使用push/replace编程式导航时，还是会出现类似错误

![1651138867402](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651138867402.png)

### 解决方法2

**<font color='hotpink'>在配置路由信息（router/index.js）过程中，重写push和replace方法</font>**

> `this.$router`属性：当前组件的这个属性，属性值是VueRouter的一个实例，当注册路由时，给组件实例添加​`$router`和`$route`属性

> push/replace方法是VueRouter类的一个实例

![1651141440018](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651141440018.png)

# 



# `$router`和`$route`

1. **<font color='hotpink'>$router : 是路由操作对象，只写对象</font>**
2. **<font color='blue'>$route : 路由信息对象，只读对象</font>**

### $ router操作路由跳转

![1651136820076](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651136820076.png)

### $route读取路由参数接收

![1651136858165](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651136858165.png)

## scoped原理

防止各个组件之间样式冲突

### Vue中的样式穿透

#### scss

1. 下载

   ![1651710631134](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651710631134.png)

2. 设置

   ![1651710706905](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651710706905.png)

3. scss样式穿透

   <font color='hotpink'>父元素 /deep/ 子元素</font>

#### stylus

1. 下载

   ![1651710796215](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651710796215.png)

2. 设置

   ![1651710858329](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651710858329.png)

3. stylus样式穿透

   <font color='blue'>父元素 >>> 子元素</font>

## ref

> **<font color='hotpink'>快速获取DOM元素</font>**

使用：

![1651711020120](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651711020120.png)

## nextTick()

> **<font color='green'>获取更新后的DOM内容</font>**

使用：

![1651711172824](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651711172824.png)

此时获取到的DOM元素是更新后的DOM元素。