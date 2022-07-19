# 前端工程化和webpack

> 模块化（js 的模块化、css 的模块化、资源的模块化）
>
> 组件化（复用现有的 UI 结构、样式、行为）
>
> 规范化（目录结构的划分、编码规范化、接口规范化、文档规范化、 Git 分支管理）
>
> 自动化（自动化构建、自动部署、自动化测试） 

![1648773842241](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648773842241.png)

## webpack

#### 1、webpack概念

 webpack 是前端项目工程化的具体解决方案。 

![1648773996499](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648773996499.png)

#### 2、安装webpack

![1651056547421](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651056547421.png)

#### 3、在项目中配置webpack

 1、在项目根目录中，创建名为 <font color='green'>webpack.config.js 的 webpack 配置文件，并初始化如下的基本配置：</font> 

![1648774078125](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648774078125.png)

2、在 package.json 的 scripts 节点下，新增 dev 脚本如下：  

![1648774106438](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648774106438.png)

3、在终端中运行 npm run dev 命令，启动 webpack 进行项目的打包构建 

#### 4、mode的可选值

>  mode 节点的可选值有两个，分别是： 
>
> ① development 
>
> 1. <font color='red'>开发环境 </font>
> 2. 不会对打包生成的文件进行代码压缩和性能优化 
> 3. 打包速度快，适合在开发阶段使用 
>
> ② production 
>
> 1. <font color='red'>生产环境 </font>
> 2. 会对打包生成的文件进行代码压缩和性能优化 
> 3. 打包速度很慢，仅适合在项目发布阶段使用 

![1648774198632](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648774198632.png)

![1648774209869](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648774209869.png)

#### 5、 自定义打包的入口与出口 

**在 webpack.config.js 配置文件中，通过 <font color='red'>entry 节点指定打包的入口。通过 output 节点指定打包的出口。</font>  **

![1648774258098](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648774258098.png)

### webpack插件

![1648774286648](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648774286648.png)

>  <font color='red'>**webpack-dev-server 可以让 webpack 监听项目源代码的变化，从而进行自动打包构建。** </font>

#####  安装 webpack-dev-server 

![1651056594378](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651056594378.png)

#####  配置 webpack-dev-server  

![1648774371262](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648774371262.png)

![1648774392147](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648774392147.png)

![1648774405399](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648774405399.png)

####  html-webpack-plugin  

html-webpack-plugin 是 <font color='red'>webpack 中的 HTML 插件</font>，可以通过此插件<font color='blue'>自定制 index.html 页面的内容</font>。 

需求：通过 html-webpack-plugin 插件，将 src 目录下的 index.html 首页，复制到项目根目录中一份！ 

#####  安装 html-webpack-plugin  

![1651056610868](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651056610868.png)

![1648774501783](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648774501783.png)

![1648774515585](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648774515585.png)

####  devServer 节点 

![1648774536970](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648774536970.png)

### loader

![1648774559649](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648774559649.png)

#### loader调用过程

![1648774584355](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648774584355.png)

##### 打包处理 css 文件  

① 运行 <font color='hotpink'>**npm i style-loader@3.0.0 css-loader@5.2.6 -D**</font> 命令，安装处理 css 文件的 loader 

② 在 webpack.config.js 的 module -> rules 数组中，添加 loader 规则如下：

![1648774627021](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648774627021.png)

其中，test 表示匹配的文件类型， use 表示对应要调用的 loader 

注意：

- use 数组中指定的 loader 顺序是固定的
- 多个 loader 的调用顺序是：从后往前调用   

##### 打包处理 less 文件 

① 运行 **npm i less-loader@10.0.1 less@4.1.1 -D** 命令

② 在 webpack.config.js 的 module -> rules 数组中，添加 loader 规则如下： 

![1648774700654](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648774700654.png)

##### 打包处理样式表中与 url 路径相关的文件 

① 运行 npm i url-loader@4.1.1 file-loader@6.2.0 -D 命令

② 在 webpack.config.js 的 module -> rules 数组中，添加 loader 规则如下： 

![1648774730687](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648774730687.png)

其中 ? 之后的是 loader 的参数项：

- limit 用来指定图片的大小，单位是字节（byte）
- 只有 ≤ limit 大小的图片，才会被转为 base64 格式的图片 

#####  打包处理 js 文件中的高级语法 

 webpack 只能打包处理一部分高级的 JavaScript 语法。对于那些 webpack 无法处理的高级 js 语法，需要借助

于 babel-loader 进行打包处理。例如 webpack 无法处理下面的 JavaScript 代码： 

![1648774782038](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648774782038.png)

####  安装 babel-loader 相关的包 

![1651056725186](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651056725186.png)

 在 webpack.config.js 的 module -> rules 数组中，添加 loader 规则如下： 

![1648774828632](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648774828632.png)

#####  配置 babel-loader 

![1648774845853](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648774845853.png)

### 打包发布

项目开发完成之后，需要使用 webpack 对项目进行打包发布，主要原因有以下两点： 

① 开发环境下，打包生成的文件存放于内存中，无法获取到最终打包生成的文件 

② 开发环境下，打包生成的文件不会进行代码压缩和性能优化 

为了让项目能够在生产环境中高性能的运行，因此需要对项目进行打包发布。 

####  1、配置 webpack 的打包发布 

![1648774906922](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648774906922.png)

#####  2、把 JavaScript 文件统一生成到 js 目录中 

![1648774942115](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648774942115.png)

##### 3、 把图片文件统一生成到 image 目录中 

![1648774974577](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648774974577.png)

##### 4、自动清理 dist 目录下的旧文件 

![1648774999045](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648774999045.png)

## Source Map

Source Map 就是一个信息文件，里面储存着位置信息。也就是说，Source Map 文件中存储着压缩混淆后的 

代码，所对应的转换前的位置。 有了它，出错的时候，除错工具将直接显示原始代码，而不是转换后的代

码，能够极大的方便后期的调试。 

![1648775056938](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648775056938.png)

![1648775071811](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648775071811.png)

####  解决默认 Source Map 的问题 

开发环境下，推荐在 webpack.config.js 中添加如下的配置，即可保证运行时报错的行数与源代码的行数 保持

一致： 

![1648775104149](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648775104149.png)

![1648775116001](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648775116001.png)

![1648775127225](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648775127225.png)

![1648775146085](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648775146085.png)

#### source Map 的最佳实践

![1648775170458](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648775170458.png)



# Vue2基础

### 推荐大家安装的 VScode 中的 Vue 插件

1. Vue 3 Snippets     https://marketplace.visualstudio.com/items?itemName=hollowtree.vue-snippets
2. Vetur                    https://marketplace.visualstudio.com/items?itemName=octref.vetur

## vue介绍

什么是vue

1. 构建用户界面
   + **用 vue 往 html 页面中填充数据，非常的方便**
2. 框架
   + 框架是一套现成的解决方案，程序员只能遵守框架的规范，去编写自己的业务功能！
   + 要学习 vue，就是在学习 vue 框架中规定的用法！
   + vue 的指令、组件（是对 UI 结构的复用）、路由、Vuex、vue 组件库
   + 只有把上面老师罗列的内容掌握以后，才有开发 vue 项目的能力！

### vue特性：

 vue 框架的特性，主要体现在如下两方面： 

<font color='red'>**① 数据驱动视图 ② 双向数据绑定** </font>

#### 1、数据驱动视图

在使用了 vue 的页面中，vue 会监听数据的变化，从而自动重新渲染页面的结构：

![1649043538489](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649043538489.png)

#### 2、双向数据绑定

在填写表单时，双向数据绑定可以辅助开发者在不操作 DOM 的前提下，自动把用户填写的内容同步到数据源中。 

![1649043582308](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649043582308.png)

**<font color='hotpink'>好处：开发者不再需要手动操作 DOM 元素，来获取表单元素最新的值！</font>** 

#### MVVM

MVVM 是 vue 实现数据驱动视图和双向数据绑定的核心原理。MVVM 指的是 Model、View 和 ViewModel， 它把每个 HTML 页面都拆分成了这三个部分，如图所示：  

![1649043704995](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649043704995.png)

> 在 MVVM 概念中： 
>
> 1. <font color='hotpink'>Model 表示当前页面渲染时所依赖的数据源。</font> 
> 2. <font color='red'>View 表示当前页面所渲染的 DOM 结构。 </font>
> 3. **ViewModel 表示 vue 的实例，它是 MVVM 的核心。** 

![1649043756146](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649043756146.png)

## vue2基本使用

> ① 导入 vue.js 的 script 脚本文件 
>
> ② 在页面中声明一个将要被 vue 所控制的 DOM 区域 
>
> ③ 创建 vm 实例对象（vue 实例对象）  

![1649043842199](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649043842199.png)

**基本代码与 MVVM 的对应关系：** 

![1649043889845](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649043889845.png)

![1651056955486](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651056955486.png)

## vue指令与过滤器

### 1、vue指令

**指令（Directives）是 vue 为开发者提供的模板语法，用于辅助开发者渲染页面的基本结构。** 

类型：

> ① 内容渲染指令 
>
> ② 属性绑定指令 
>
> ③ 事件绑定指令 
>
> ④ 双向绑定指令 
>
> ⑤ 条件渲染指令 
>
> ⑥ 列表渲染指令  

#### 1.内容渲染指令

内容渲染指令用来辅助开发者渲染 DOM 元素的文本内容。常用的内容渲染指令有如下 3 个：

**v-text、{{}}、v-html**

| v-text         | 缺点：会覆盖元素中的默认内容                 |
| -------------- | -------------------------------------------- |
| {{}}插值表达式 | 插值只能用在元素的内容节点，无法用在属性节点 |
| v-html         | 把带有HTML标签的字符串，渲染为真正的DOM元素  |

##### v-text

![1649044037935](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649044037935.png)

##### {{}}语法

vue 提供的 {{ }} 语法，专门用来解决 v-text 会覆盖默认文本内容的问题。这种 {{ }} 语法的专业名称是插值表达式（英文名为：Mustache）。 

![1649044076159](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649044076159.png)

##### v-html

v-text 指令和插值表达式只能渲染纯文本内容。如果要把包含 HTML 标签的字符串渲染为页面的 HTML 元素， 则需要用到 v-html 这个指令：  

![1649044099560](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649044099560.png)

![1651057145457](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651057145457.png)

#### 2.属性绑定指令

如果需要为元素的<font color='red'>**属性动态绑定属性值**</font>，则需要用到 v-bind 属性绑定指令。 

v-bind  简写：:

![1649044137630](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649044137630.png)

简写形式：

![1649044158522](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649044158522.png)

**在 vue 提供的模板渲染语法中，除了支持绑定简单的数据值之外，还支持 Javascript 表达式的运算： **

![1649044184208](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649044184208.png)

![1651057261968](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651057261968.png)

#### 3.事件绑定指令

**vue 提供了 v-on 事件绑定指令，用来辅助程序员为 DOM 元素绑定事件监听 。**

![1649044228995](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649044228995.png)

<font color='red'>v-on 简写：@</font>

> 注意：原生 DOM 对象有 onclick、oninput、onkeyup 等原生事件，替换为 vue 的事件绑定形式后， 分别为：v-on:click、v-on:input、v-on:keyup 

**通过 v-on 绑定的事件处理函数，需要在 <font color='red'>methods 节点</font>中进行声明： **

![1649044280631](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649044280631.png)

![1651057428165](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651057428165.png)

在原生的 DOM 事件绑定中，可以在事件处理函数的形参处，接收事件参数对象 event。同理，在 v-on 指令 （简写为 @ ）所绑定的事件处理函数中，同样可以接收到事件参数对象 event：

![1651057347045](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651057347045.png)

![1649044326177](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649044326177.png)

###### 绑定事件并传参

**在使用 v-on 指令绑定事件时，可以使用 ( ) 进行传参** 

<font color='green'>@click="show"和@click="show(传参)"</font>

![1649044377909](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649044377909.png)

###### $event

**<font color='green'>$event 是 vue 提供的特殊变量，用来表示原生的事件参数对象event</font>**

$event 可以解决事件参数对象 event 被覆盖的问题 

![1649044503854](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649044503854.png)

![1651057485680](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651057485680.png)

##### 事件修饰符

在事件处理函数中调用 event.preventDefault() 或 event.stopPropagation() 是非常常见的需求。因此， vue 提供了事件修饰符的概念，来辅助程序员更方便的对事件的触发进行控制。

###### 常用事件修饰符：

![1649044556667](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649044556667.png)

![1649044572952](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649044572952.png)

**事件修饰符：.prevent、.stop**

![1651057624913](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651057624913.png)

##### 按键修饰符

**<font color='orange'>在监听键盘事件时，我们经常需要判断详细的按键。此时，可以为键盘相关的事件添加按键修饰符</font>** 

![1649044628290](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649044628290.png)

**按键修饰符：.esc、.enter**

![1651057697736](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651057697736.png)

#### 4.双向数据绑定指令

<font color='blue'>**v-model 双向数据绑定指令，用来辅助开发者在不操作 DOM 的前提下，快速获取表单的数据**</font> 

**<font color='hotpink'>v-model：只能用在表单元素上</font>**

![1649044690252](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649044690252.png)

![1651057765646](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651057765646.png)

##### v-model指令的修饰符

![1649044717001](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649044717001.png)

**<font color='green'>修饰符：.number、.trim、.lazy</font>**

![1651057894196](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651057894196.png)

#### 5.循环渲染指令(列表渲染指令)

> vue 提供了 v-for 列表渲染指令，**<font color='green'>用来辅助开发者基于一个数组来循环渲染一个列表结构。</font>**v-for 指令需要使用 <font color='red'>item in items 形式的特殊语法</font>，其中： 
>
> 1. items 是待循环的数组 
> 2. item 是被循环的每一项 

v-for="(item,index) in 数组"

![1649044972784](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649044972784.png)

##### v-for索引

> v-for 指令还支持一个可选的第二个参数，即当前项的索引。语法格式为 (item, index) in items 
>
> 注意：<font color='blue'>v-for 指令中的 item 项和 index 索引都是形参，可以根据需要进行重命名。例如 (user, i) in userlist </font>

![1649045021176](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649045021176.png)

##### 使用 key 维护列表的状态 

> 当列表的数据变化时，默认情况下，vue 会尽可能的复用已存在的 DOM 元素，从而提升渲染的性能。但这种 默认的性能优化策略，会导致有状态的列表无法被正确更新。 为了给 vue 一个提示，以便它能跟踪每个节点的身份，从而在保证有状态的列表被正确更新的前提下，提升渲 染的性能。此时，需要为每项提供一个唯一的 key 属性： 

**需要为每项提供一个唯一的 key 属性， 从而在保证有状态的列表被正确更新的前提下，提升渲染的性能**  

：key="item.id"

![1649045073934](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649045073934.png)

拿索引当key值没有意义

![1651058151423](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651058151423.png)

###### key的注意事项

![1649045093373](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649045093373.png)

![1651058003691](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651058003691.png)

#### 6.条件渲染指令

**条件渲染指令用来辅助开发者按需控制 <font color='red'>DOM 的显示与隐藏</font>**

| v-if   | 动态的创建和移除元素（DOM） v-else-if、v-else |
| ------ | --------------------------------------------- |
| v-show | 动态的添加和移除 display:none;样式            |

![1649044790658](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649044790658.png)

###### v-if 和 v-show 的区别 

> <font color='red'>实现原理不同：</font> 
>
> 1. v-if 指令会动态地创建或移除 DOM 元素，从而控制元素在页面上的显示与隐藏；
> 2. v-show 指令会动态为元素添加或移除 style="display: none;" 样式，从而控制元素的显示与隐藏； 
>
> <font color='red'>性能消耗不同：</font> 
>
> v-if 有更高的切换开销，而 v-show 有更高的初始渲染开销。因此： 
>
> - 如果需要非常频繁地切换，则使用 v-show 较好
> - 如果在运行时条件很少改变，则使用 v-if 较好 

##### v-else

![1649044864741](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649044864741.png)

##### v-else-if

![1649044878640](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649044878640.png)

![1651058212153](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651058212153.png)

#### label的for属性

![1651058266779](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651058266779.png)

#### 7.过滤器

**过滤器（Filters）是 vue 为开发者提供的功能，常用于文本的格式化。过滤器可以用在两个地方：<font color='red'>插值表达式 和 v-bind 属性绑定</font>。** 

<font color='green'>过滤器应该被添加在 JavaScript 表达式的尾部，由“管道符”进行调用</font> 

![dingyiguolü](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649045155709.png)

![1651058317486](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651058317486.png)

##### 定义过滤器

**<font color='red'>私有过滤器：在创建 vue 实例期间，可以在 filters 节点中定义过滤器</font>** 

<font color='green'>只能在当前 vm 实例所控制的 el 区域内使用 </font>

![1649045221964](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649045221964.png)

**全局过滤器： 在多个 vue 实例之间共享过滤器**

![1649045322271](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649045322271.png)

**连续调用多个过滤器**

![1649045343982](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649045343982.png)

![1649045366037](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649045366037.png)

| 全局过滤器 | Vue.filter('名字',function(调用过滤器的值){ return 结果}) |
| ---------- | --------------------------------------------------------- |
| 私有过滤器 | 定义到组件的 filters节点之下                              |

##### 过滤器传参

![1649045388194](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649045388194.png)

![1649045395983](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649045395983.png)

**过滤器仅在 vue 2.x 和 1.x 中受支持，在 vue 3.x 的版本中剔除了过滤器相关的功能。**

**<font color='red'>调用：{{ message | dateFormat}}</font>**

**过滤器的注意点：**

> 1. 要定义到 filters 节点下，**本质是一个函数**
> 2. 在过滤器函数中，**一定要有 return 值**
> 3. 在过滤器的形参中，可以获取到“管道符”前面待处理的那个值
> 4. 如果全局过滤器和私有过滤器名字一致，此时按照“**就近原则**”，调用的是”私有过滤器“
>

![1651058420547](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651058420547.png)

## 1.watch侦听器

<font color='green'>watch 侦听器允许开发者监视数据的变化，从而针对数据的变化做特定的操作 </font>

![1649071696181](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649071696181.png)

![1651058590558](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651058590558.png)

<font color='red'>1、方法格式：username(newVal,oldVal){}</font>

<font color='red'>2、对象格式：</font> **如果 watch 侦听的是一个对象，如果对象中的属性值发生了变化，则无法被监听到。此时需要使用 deep 选项**

![1649071849583](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649071849583.png)

![1651058774199](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651058774199.png)

###### 监听对象单个属性的变化

如果只想监听对象中单个属性的变化，则可以按照如下的方式定义 watch 侦听器： 

![1649071909104](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649071909104.png)

##### immediate选项

![1649071810560](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649071810560.png)

![1651058860758](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651058860758.png)

##### watch检测用户名是否可用

监听 username 值的变化，并使用 axios 发起 Ajax 请求，检测当前输入的用户名是否可用：  

![1649071763574](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649071763574.png)

![1651058698855](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651058698855.png)

侦听器的格式：**

1. 方法格式的侦听器
   + 缺点1：无法在刚进入页面的时候，自动触发！！！
   + 缺点2：如果侦听的是一个对象，如果对象中的属性发生了变化，不会触发侦听器！！！
2. 对象格式的侦听器
   + 好处1：可以通过 **immediate** 选项，让侦听器自动触发！！！
   + 好处2：可以通过 **deep** 选项，让侦听器深度监听对象中每个属性的变化！！！

**侦听器的名称就是要监听的数据名**

## 2.计算属性

在定义的时候，要定义为function

在使用的时候，当作普通的属性使用即可

> **在methods方法中可以使用：this.计算属性名**
>
> 在template模板结构中可以使用

要return一个计算的结果

只要任何一个依赖的数据发生了变化，计算属性就会重新赋值

> 计算属性指的是通过一系列运算之后，最终得到一个属性值。 这个动态计算出来的属性值可以被模板结构或 methods 方法使用。示例代码如下： 

![1649071975567](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649071975567.png)

![1651058958483](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651058958483.png)

##### 计算属性的特点：

1. 虽然计算属性在声明的时候被定义为方法，但是计算属性的本质是一个属性
2. 计算属性会缓存计算的结果，只有计算属性依赖的数据变化时，才会重新进行运算 

## 数据代理

### Object.defineProperty

通过此方法定义的属性是不能枚举的（不参加遍历的）

![1651461376665](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651461376665.png)

### 理解数据代理

**通过一个对象代理对另一个对象中属性的操作（读/写）**

![1651461629079](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651461629079.png)

将obj1的x通过Object.defineProperty赋值给了obj2.x，在set中将obj1的x的值的改变代理给了obj2，当改变obj2.x时，obj1.x也会改变

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651461784535.png" alt="1651461784535" style="zoom:50%;" />

### vue中的数据代理

修改vm.name，vm._data.name也会相应发生改变

![1651463096858](C:\Users\86186\Desktop\1651463096858.png)

![1651463296655](C:\Users\86186\Desktop\1651463296655.png)

> 1. **<font color='hotpink'>Vue中的数据代理：</font>**
>
>    - 通过vm对象来代理data对象中属性的操作（读/写）
>
> 2. Vue中数据代理的好处：
>
>    - 更加方便的操作data中的数据
>
> 3. **<font color='hotpink'>基本原理：</font>**
>
>    - 通过Object.defineProperty()把data对象中所有属性添加到vm上
>
>    - 为每一个添加到vm上的属性，都指定一个getter/setter
>
>    - 在getter/setter内部去操作（读/写）data中对应的属性

# axios

> axios 是一个专注于网络请求的库！

#### axios的基本使用

1、发起GET请求：

![1651059070216](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651059070216.png)

![1651059259947](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651059259947.png)

2、发起POST请求：

![1651059099589](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651059099589.png)

![1651059288971](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651059288971.png)

#### 解构赋值

![1651059358854](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651059358854.png)

#### axios直接发起GET和POST请求

![1651059425576](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651059425576.png)

### vue的$mount()

![1651059504695](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651059504695.png)

# vue-cli

vue-cli 是 Vue.js 开发的标准工具。它简化了程序员基于 webpack 创建工程化的 Vue 项目的过程 

##### 全局安装：

![1651059137138](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651059137138.png)

##### 创建项目：

![1651059152571](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651059152571.png)

![1649072215238](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649072215238.png)

##### vue项目中src目录的构成：

> 1. assets 文件夹：存放项目中用到的静态资源文件，例如：css 样式表、图片资源
> 2. components 文件夹：程序员封装的、可复用的组件，都要放到components 目录下
> 3. main.js 是项目的入口文件。整个项目的运行，要先执行 main.js
> 4. App.vue 是项目的根组件。展现到浏览器的页面内容。

# 组件

## 组件化开发

组件化开发指的是：根据封装的思想，把页面上可重用的 UI 结构封装为组件，从而方便项目的开发和维护。 

![1649072331629](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649072331629.png)

结构：

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651059923386.png" alt="1651059923386" style="zoom:40%;" />

**App.vue**

![1651060001194](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651060001194.png)

入口文件main.js

![1651060281185](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651060281185.png)

public/index.html

![1651060368133](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651060368133.png)

组件的组成：

> - template：只能由唯一的根节点
> - script：export default{}、vue中的data必须是方法
> - style：启用less语法：lang="less"、防止组件之间样式冲突：scoped、如果给当前组件的 style 节点添加了 scoped 属性，则当前组件的样式对其子组件是不生效的。如果想让某些样式对子组件生效，可以使用 /deep/ 深度选择器。同时想改变第三方组件的样式也可以使用深度选择器。

**每个组件中必须包含 template 模板结构，而 script 行为和 style 样式是可选的组成部分 **

##### template

<font color='red'>vue 规定：每个组件对应的模板结构，需要定义到 <template>节点中</font>

![1649072423769](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649072423769.png)

> 注意：
>
> 1. template 是 vue 提供的容器标签，只起到包裹性质的作用，它不会被渲染为真正的 DOM 元素
> 2. template 中只能包含唯一的根节点 

##### script

<font color='orange'>vue 规定：开发者可以在 <script>节点中封装组件的JavaScript业务逻辑。</font>

![1649072526569](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649072526569.png)

###### data

**.vue组件中的data必须是函数**

> vue 规定：.vue 组件中的 data 必须是一个函数，不能直接指向一个数据对象 

##### style

<font color='blue'>vue 规定：组件内的` <style> `节点是可选的，开发者可以在 `<style>`节点中编写样式美化当前组件的UI结构。</font>

![1649072649371](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649072649371.png)

###### style中less语法

在 `<style> `标签上添加 lang="less" 属性，即可使用 less 语法编写组件的样式： 

![1649072696466](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649072696466.png)

![1651059714685](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651059714685.png)

#### 组件之间的父子关系

![1649072727220](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649072727220.png)

组件在被封装好之后，<font color='red'>彼此之间是相互独立的，</font>不存在父子关系 

在使用组件的时候，根据彼此的嵌套关系，形成了父子关系、兄弟关系 

#### 使用组件的三个步骤

![1649072773010](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649072773010.png)

##### 私有子组件

**<font color='blue'>通过components注册的是私有子组件</font>**

![1649072817966](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649072817966.png)

##### 注册全局组件

在 vue 项目的 <font color='green'>main.js 入口文件中，通过 Vue.component() 方法</font>，可以注册全局组件。示例代码如下： 

![1649072848279](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649072848279.png)

#### 1.自定义属性：props

极大的提高了组件的复用性

**语法格式：**

![1649072901296](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649072901296.png)

定义props有两种格式：**<font color='orange'>数组和对象</font>**

> **数组：props:["自定义属性",...]**
>
> **对象：props:{**
>
> ​	**自定义属性:{**
>
> ​		**<font color='red'>type: 通过 type 来定义属性的值类型</font>** 
>
> ​		**<font color='orange'> default: 通过 default 来定义属性的默认值</font>** 
>
> ​	 	**<font color='green'>required:通过 required 选项，将属性设置为必填项，强制用户必须传递属性的值 }</font>**
>
> **}**

props自定义属性是只读的，在项目开发中，**<font color='hotpink'>不要直接把props的值进行修改，可以转存到data中，然后进行读写操作：</font>**

![1649073066585](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649073066585.png)

![1649073080967](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649073080967.png)

![1649073093344](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649073093344.png)

![1651059836001](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651059836001.png)

**组件之间的样式冲突问题：** **

> 默认情况下，写在 .vue 组件中的样式会全局生效，因此很容易造成多个组件之间的样式冲突问题。 
>
> 导致组件之间样式冲突的根本原因是： 
>
> ① 单页面应用程序中，所有组件的 DOM 结构，都是基于唯一的 index.html 页面进行呈现的 
>
> ② 每个组件中的样式，都会影响整个 index.html 页面中的 DOM 元素 

##### 解决组件之间样式冲突的问题

![1649073204476](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649073204476.png)

![1649073216896](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649073216896.png)

![1649073239236](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649073239236.png)

# 生命周期

**概念：每个组件冲创建->运行->销毁的一个过程，强调的是一个时间段**

###### 3.生命周期函数

**概念：在生命周期的不同阶段，会按次序，依次执行的函数，叫做生命周期函数**

注意：生命周期强调的是时间段，生命周期函数强调的是时间点。 

![1649073469523](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649073469523.png)

![](D:\前端系统学习\Vue2\day4\讲义\lifecycle.png)

![1651060490367](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651060490367.png)

## 组件之间的数据共享

#### 父子组件之间传递数据（共享数据）

> 1. **父组件向子组件共享数据：使用自定义属性，在子组件中通过 props 自定义属性，在子组件中通过props来自定义属性，在父组件中，通过v-bind:绑定给子组件**
>
> 2. **<font color='hotpink'>子组件向父组件共享数据：使用自定义事件，在子组件中调用this.$emit()触发自定义事件</font>**
>    	参数1：字符串，表示自定义事件的名称
>    	参数2：值，要传递给父组件的数据
> 3. 在父组件中，通过v-on绑定自定义事件并提供一个事件处理函数，通过事件处理函数的形参接收到子组件传递过来的数据

**App.vue（父组件）**

![1651060724782](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651060724782.png)

**Left.vue**

![1651060809668](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651060809668.png)

**Right.vue**

![1651060912443](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651060912443.png)

**eventBus.js**

![1651060988559](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651060988559.png)

**面试问的较多的问题：Vue组件之间共享数据有哪些方法？过程是怎么样的**

##### 父组件向子组件共享数据

> 父组件向子组件共享数据需要使用自定义属性 

![1649073713114](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649073713114.png)

##### 子组件向父组件共享数据 

> 子组件向父组件共享数据使用自定义事件 

![1649073753861](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649073753861.png)

##### 兄弟组件之间传递数据：

![1649073791750](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649073791750.png)

 **EventBus 的使用步骤：** 

> 1. 创建 eventBus.js 模块，并向外共享一个 Vue 的实例对象
> 2. **<font color='hotpink'>在数据发送方，调用 bus.$emit('事件名称', 要发送的数据) 方法触发自定义事件</font>** 
> 3. **<font color='green'>在数据接收方，调用 bus.$on('事件名称', 事件处理函数) 方法注册一个自定义事件</font>** 
> 4. <font color='blue'>不能同时用this绑定$emit和on，因为虽然名字相同，但并不是同一个Vue实例对象</font>

## ref引用

> ref 用来辅助开发者在不依赖于 jQuery 的情况下，获取 DOM 元素或组件的引用。 
>
> 1. 每个 vue 的组件实例上，都包含一个 $refs 对象，里面存储着对应的 DOM 元素或组件的引用。
> 2. 默认情况下，<font color='red'> 组件的 $refs 指向一个空对象。 </font>

![1649074150329](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649074150329.png)

#### 使用 ref 引用 DOM 元素 

![1649074222863](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649074222863.png)

#### 使用 ref 引用组件实例 

![1649074264407](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649074264407.png)

![1651061204817](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651061204817.png)

**Yourref.vue**

![1651061262223](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651061262223.png)

##### 控制文本框和按钮的按需切换 

![1649074326553](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649074326553.png)

##### 让文本框自动获得焦点 

![1649074359760](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649074359760.png)

#### this.$nextTick(cb) 方法 

> **<font color='orange'>组件的 $nextTick(cb) 方法，会把 cb 回调推迟到下一个 DOM 更新周期之后执行。</font>**
>
> 通俗的理解是：等组件的 DOM 更新完成之后，再执行 cb 回调函数。从而能保证 cb 回调函数可以操作到最新的 DOM 元素。 

![1649074447691](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649074447691.png)

### Vue购物车案例

> 1.安装 axios，并在App.vue中导入axios
> 2.在methods方法中，定义initCartList函数发起axios请求列表数据
> 3.在create生命周期函数中，调用步骤2封装的initCartList函数

### 小结

> 能够知道 vue 中常用的生命周期函数
>
> 1. 创建阶段、运行阶段、销毁阶段
> 2. created、mounted
>
> 能够知道如何实现组件之间的数据共享
>
> 1. 父 -> 子（自定义属性）
> 2. 子 -> 父（自定义事件）
> 3. 兄弟组件（EventBus） 
>
> 能够知道如何使用 ref 引用 DOM 元素或组件
>
> 1. 给元素或组件添加 ref="xxx" 的引用名称
> 2. 通过 this.$refs.xxx 获取元素或组件的实例
> 3. $nextTick() 函数的执行时机 

# 动态组件 & 插槽 & 自定义指令 

## 动态组件

**<font color='red'>动态组件指的是动态切换组件的显示与隐藏。</font>** 

#### 1、实现动态组件渲染 

**vue 提供了一个内置的`<component>`组件，专门用来实现动态组件的渲染。** 

![1649074798294](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649074798294.png)

#### 2、keep-alive对应的生命周期函数

<font color='green'>默认情况下，切换动态组件时无法保持组件的状态。此时可以使用 vue 内置的`<keep-alive>`组件保持动态组件的状态。</font> 

![1649074893740](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649074893740.png)

> 1. 当组件被缓存时，会自动触发组件的 deactivated 生命周期函数。 
>
> 2. 当组件被激活时，会自动触发组件的 activated 生命周期函数。 

![1649074908201](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649074908201.png)

![1649074922566](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649074922566.png)

**Left.vue**

![1651061546944](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651061546944.png)

**Right.vue**

![1651061574791](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651061574791.png)

**App.vue**

![1651061638425](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651061638425.png)

### 实例：获取图书信息

#### main.js

![1651062325934](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651062325934.png)

#### App.vue

![1651062423766](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651062423766.png)

#### Left.vue

![1651062475870](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651062475870.png)

#### Right.vue

![1651062527110](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651062527110.png)

## 插槽

<font color='blue'>插槽（Slot）是 vue 为组件的封装者提供的能力。**允许开发者在封装组件时，把不确定的、希望由用户指定的部分定义为插槽。**</font>  

![1649075047255](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649075047255.png)

#### 插槽的基本用法

**<font color='green'>在封装组件时，可以通过`<slot>`元素定义插槽，从而为用户预留内容占位符</font>** 

![1649075102592](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649075102592.png)

###### 没有预留插槽的内容会被丢弃 

![1649075131390](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649075131390.png)

##### 后备内容 

> 封装组件时，可以为预留的`<slot>`插槽提供后备内容（默认内容）。如果组件的使用者没有为插槽提供任何 内容，则后备内容会生效。 

![1649075177000](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649075177000.png)

##### 具名插槽

> **<font color='orange'>如果在封装组件时需要预留多个插槽节点，则需要为每个`<slot>`插槽指定具体的 name 名称。这种带有具体名称的插槽叫做“具名插槽”</font>** 

![1649075242054](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649075242054.png)

**注意：没有指定 name 名称的插槽， 会有隐含的名称叫做 “default” **

###### 为具名插槽提供内容 

在向具名插槽提供内容的时候，我们**可以在一个` <template>`元素上使用 v-slot 指令，并以 v-slot 的参数的形式提供其名称。** 

![1649075349461](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649075349461.png)

###### 具名插槽的简写形式 

**v-slot 也有缩写，即把参数之前的所有内容 (v-slot:) 替换为字符 #。例如 v-slot:header 可以被重写为 #header** 

![1649075454471](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649075454471.png)

##### 作用域插槽

**<font color='blue'>在封装组件的过程中，可以为预留的`<slot>`插槽绑定 props 数据，这种带有 props 数据的`<slot>`叫做“作用域插槽”</font>**。 

![1649075549197](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649075549197.png)

###### 使用作用域插槽 

<font color='red'>可以使用 v-slot: 的形式，接收作用域插槽对外提供的数据 </font>

![1649075591586](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649075591586.png)

###### 解构插槽 Prop 

> <font color='green'>作用域插槽对外提供的数据对象，可以使用解构赋值简化数据的接收过程。</font> 

![1649075693172](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649075693172.png)

#### 实例：

##### main.js

![1651062680225](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651062680225.png)

##### App.vue

![1651062750823](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651062750823.png)

##### Article.vue

![1651062878698](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651062878698.png)

##### Left.vue

![1651062929102](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651062929102.png)

##### Right.vue

![1651063001935](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651063001935.png)

## 自定义指令

**分为两类：私有自定义指令、全局自定义指令**

> 1. **<font color='hotpink'>在directives节点下声明私有自定义指令</font>**
> 2. **<font color='red'>全局自定义指令需要通过“Vue.directive()”进行声明 </font>**

#### 1、私有自定义指令

在每个 vue 组件中，可以在 <font color='blue'>directives 节点下声明私有自定义指令。</font>

![1649075822110](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649075822110.png)

##### 使用自定义指令

在使用自定义指令时，需要加上 v- 前缀

![1649075869054](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649075869054.png)

##### 为自定义指令动态绑定参数值

<font color='blue'>在 template 结构中使用自定义指令时，可以通过等号（=）的方式，为当前指令动态绑定参数值：</font>

![1649075936383](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649075936383.png)

##### 通过 binding 获取指令的参数值

<font color='red'>在声明自定义指令时，可以通过形参中的第二个参数，来接收指令的参数值</font>

![1649075968088](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649075968088.png)

##### update 函数

**<font color='hotpink'>bind 函数只调用 1 次：当指令第一次绑定到元素时调用，当 DOM 更新时 bind 函数不会被触发。 update 函数会在每次 DOM 更新时被调用。</font>**

![1649076017874](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649076017874.png)

![1649076042588](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649076042588.png)

#### 2、全局自定义指令

**<font color='green'>全局共享的自定义指令需要通过“Vue.directive()”进行声明</font>**

![1649076084593](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649076084593.png)

#### 实例：

##### main.js

![1651063228541](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651063228541.png)

##### App.vue

![1651063288870](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651063288870.png)

##### Left.vue

![1651063360225](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651063360225.png)

##### Right.vue

![1651063390922](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651063390922.png)

### 小结

> ① 能够掌握 keep-alive 元素的基本使用
>
> - `<keep-alive> `标签、include 属性
>
> ② 能够掌握插槽的基本用
>
> - `<slot> `标签、具名插槽、作用域插槽、后备内容
>
> ③ 能够知道如何自定义指令
>
> - 私有自定义指令 directives: { }
> - 全局自定义指令 Vue.directive()

## 购物车案例

### 页面展示

![1651063671111](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651063671111.png)

#### main.js

![1651064011484](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651064011484.png)

#### App.vue

![1651064064342](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651064064342.png)

#### Counter.vue

![1651065173980](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651065173980.png)

#### Footer.vue

![1651065218488](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651065218488.png)

#### Goods.vue

![1651065279711](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651065279711.png)

#### Header.vue

![1651065313810](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651065313810.png)

#### eventBus.js

![1651065351641](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651065351641.png)

# SPA与前端路由

> SPA指的是一个web网站只有唯一的一个HTML页面， 所有组件的展示与切换都在这唯一的一个页面内完成。 此时，不同组件之间的切换需要通过前端路由来实现。 
>

## **前端路由**

**<font color='red'>指Hash地址和组件之间的对应关系</font>**

### 前端路由的工作方式

> ① 用户点击了页面上的路由链接
>
> ② 导致了 URL 地址栏中的 Hash 值发生了变化
>
> ③ 前端路由监听了到 Hash 地址的变化
>
> ④ 前端路由把当前 Hash 地址对应的组件渲染都浏览器中

![1649080084943](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649080084943.png)

#### 实现简单的前端路由

步骤1：通过` <component> `标签，结合 comName 动态渲染组件。

![1649080115558](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649080115558.png)

步骤2：在 App.vue 组件中，为 `<a> `链接添加对应的 hash 值：

![1649080147465](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649080147465.png)

步骤3：在 created 生命周期函数中，监听浏览器地址栏中hash 地址的变化，动态切换要展示的组件的名称：

![1649080167543](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649080167543.png)

## vue-router的基本使用

vue-router 是 vue.js 官方给出的路由解决方案。**它只能结合 vue 项目进行使用，能够轻松的管理 SPA 项目**
**中组件的切换。**

vue-router 的官方文档地址：https://router.vuejs.org/zh/

#### 1、vue-router 安装和配置的步骤

> ① 安装 vue-router 包
>
> ② 创建路由模块
>
> ③ 导入并挂载路由模块
>
> ④ 声明路由链接和占位符

##### **1. 安装vue-router**

![1649080364550](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649080364550.png)

##### 2.  创建路由模块

![1649080402399](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649080402399.png)

##### 3. 导入并挂载路由模块

![1649080441189](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649080441189.png)

##### 4. 声明路由链接和占位符

**<font color='orange'>在 src/App.vue 组件中，使用 vue-router 提供的 `<router-link> `和 `<router-view> `声明路由链接和占位符：</font>**

![1649080504003](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649080504003.png)

#### 声明路由的匹配规则

<font color='green'>**在 src/router/index.js 路由模块中，通过 routes 数组声明路由的匹配规则。**</font>

![1649080582931](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649080582931.png)

## vue-router常见用法

### 1、路由重定向

路由重定向指的是：**用户在访问地址 A 的时候，强制用户跳转到地址 C** ，从而展示特定的组件页面。<font color='blue'>通过路由规则的 redirect 属性，指定一个新的路由地址，可以很方便地设置路由的重定向：</font>

![1649080708559](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649080708559.png)

### 2、嵌套路由

**<font color='red'>通过路由实现组件的嵌套展示，叫做嵌套路由</font>**

![1649080746456](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649080746456.png)

#### 声明子路由链接和子路由占位符

在 About.vue 组件中，声明 tab1 和 tab2 的子路由链接以及子路由占位符。

![1649080779740](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649080779740.png)

#### 通过 children 属性声明子路由规则

在 src/router/index.js 路由模块中，导入需要的组件，并使用 children 属性声明子路由规则：

![1649080808855](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649080808855.png)

#### 动态匹配路由

![1649141887387](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649141887387.png)

### 动态路由

> **动态路由指的是：把 Hash 地址中可变的部分定义为参数项，从而提高路由规则的复用性。在 vue-router 中使用英文的冒号（:）来定义路由的参数项。**

![1649141967349](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649141967349.png)

#### $route.params 参数对象

<font color='red'>在动态路由渲染出来的组件中，可以使用 **this.$route.params 对象访问到动态匹配的参数值。**</font>

![1649142068527](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649142068527.png)

##### 使用 props 接收路由参数

![1649142402742](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649142402742.png)

#### Hash地址 

在URL地址中，从#开始后面的都称为Hash地址

#### Vue.use()函数

**Vue.use()函数是一个专门为Vue装插件的函数**

#### 路由重定向

路由重定向指的是：用户在访问地址 A 的时候，强制用户跳转到地址 C ，从而展示特定的组件页面。 通过路由规则的 redirect 属性，指定一个新的路由地址，可以很方便地设置路由的重定向 。

#### 嵌套路由

 通过路由实现组件的嵌套展示，叫做嵌套路由 

## <font color='green'>声明式导航 & 编程式导航 </font>

> 1、在浏览器中，点击链接实现导航的方式，叫做声明式导航。例如：
> 	普通网页中点击 <a> 链接、vue 项目中点击 <router-link> 都属于声明式导航
> 2、在浏览器中，调用 API 方法实现导航的方式，叫做编程式导航。例如：
>  	普通网页中调用 location.href 跳转到新页面的方式，属于编程式导航

#### 编程式导航API

##### $router.push()

![1649142547703](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649142547703.png)

##### $router.replace()

![1649142575318](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649142575318.png)

##### $router.go()

![1649142619928](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649142619928.png)

| this.$router.push('hash 地址')    | 跳转到指定 hash 地址，并增加一条历史记录       |
| --------------------------------- | ---------------------------------------------- |
| this.$router.replace('hash 地址') | 跳转到指定的 hash 地址，并替换掉当前的历史记录 |
| this.$router.go(数值 n)           | 实现导航历史前进、后退                         |

>  $router.back() ：在历史记录中，后退到上一个页面
>
> $router.forward() ：在历史记录中，前进到下一个页面 

### 导航守卫

![1648773712435](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648773712435.png)



#### 15.全局前置守卫

<font color='orange'>每次发生路由的导航跳转时，都会触发全局前置守卫。</font>因此，在全局前置守卫中，程序员可以对每个路由进行
访问权限的控制：

~~~
router.beforeEach(to,from,next)
~~~

![1649142690341](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649142690341.png)

**<font color='red'> 全局前置守卫的回调函数中接收 3 个形参</font>**

![1649142975612](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649142975612.png)

###### next 函数的 3 种调用方式

![1649143022734](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649143022734.png)

> 1. 当前用户拥有后台主页的访问权限，<font color='red'>直接放行：next()</font>
> 2. 当前用户没有后台主页的访问权限，<font color='red'>强制其跳转到登录页面：next('/login')</font>
> 3. 当前用户没有后台主页的访问权限，<font color='red'>不允许跳转到后台主页：next(false)</font>

**控制后台主页的访问权限**

![1649143104405](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649143104405.png)

**总结：**

> ① 能够知道如何在 vue 中配置路由
>
> - createRouter、app.use(router)
>
> ② 能够知道如何使用嵌套路由
>
> - 通过 children 属性进行路由嵌套
>
> ③ 能够知道如何实现动态路由匹配
>
> - 使用冒号声明参数项、this.$route.params、props: true
>
> ④ 能够知道如何使用编程式导航
>
> - this.$router.push
> - this.$router.go
>
> ⑤ 能够知道如何使用导航守卫
>
> - 路由实例.beforeEach((to, from, next) => { /* 必须调 next 函数 */ })



### 实例：

![1651065779264](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651065779264.png)

#### main.js

![1651065833297](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651065833297.png)

#### App.vue

![1651065876006](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651065876006.png)

#### App2.vue

![1651065922149](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651065922149.png)

#### router/index.js

![1651066445023](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651066445023.png)

#### Home.vue

![1651066487608](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651066487608.png)

#### Login.vue

![1651066514276](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651066514276.png)

#### Main.vue

![1651066540543](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651066540543.png)

#### Movie.vue

![1651066577424](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651066577424.png)

#### About.vue

![1651066618378](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651066618378.png)

#### Tab1.vue

![1651066648131](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651066648131.png)

#### Tab2.vue

![1651066675658](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651066675658.png)

### 实例：

![1651066807815](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651066807815.png)

![1651066817162](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651066817162.png)

#### main.js

![1651066846975](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651066846975.png)

#### App.vue

![1651066879254](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651066879254.png)

#### router/index.js

![1651066946881](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651066946881.png)

#### MyLogin.vue

![1651067000372](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651067000372.png)

#### MyHome.vue

![1651067043389](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651067043389.png)

#### menus/MyGoods.vue

![1651067072997](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651067072997.png)

#### menus/MyOrders.vue

![1651067105769](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651067105769.png)

#### menus/MyRights.vue

![1651067162245](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651067162245.png)

#### menus/MySettings.vue

![1651067187688](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651067187688.png)

#### menus/MyUsers.vue

![1651067218927](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651067218927.png)

#### subcomponents/MyAside.vue

![1651067259756](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651067259756.png)

#### subcomponents/MyHeader.vue

![1651067299241](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651067299241.png)

#### user/MyUserDetail.vue

![1651067334633](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651067334633.png)

