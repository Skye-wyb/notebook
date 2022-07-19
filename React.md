React基础

## 一、React概述

React 是一个用于构建用户界面的 JavaScript 库。

**React是一个将数据渲染为HTML视图的开源JavaScript库。**

- 用户界面：HTML页面（前端）
- <font color='red'>React 主要用来写HTML页面，或构建Web应用</font>

> 如果从 MVC 的角度来看，<font color='red'>React 仅仅是视图层（V），也就是只负责视图的渲染，而并非提供了
> 完整的 M 和 C 的功能。</font>
>
> React 起源于 Facebook 的内部项目，后又用来架设 Instagram 的网站，并于 2013 年 5 月开源

> 1. 发送请求获取数据
> 2. 处理数据（过滤、整理格式等）
> 3. **<font color='red'>操作DOM呈现页面</font>**

> 使用React好处：
>
> 1. 原生JavaScript操作DOM繁琐、效率低。**（DOM-API操作UI）**
> 2. 使用JavaScript直接操作DOM，浏览器会进行大量的**重绘重排**。
> 3. 原生JavaScript没有**组件化**编码方案，代码复用率低。

### React的特点

1. 声明式

   采用**<font color='red'>组件化模式、声明式编码，</font>**提高开发效率及组件复用率

2. 基于组件

3. 学习一次，随处使用

   在React Native中可以使用React语法进行移动端开发

   **<font color='hotpink'>使用虚拟DOM+Diff算法，尽量减少与真实DOM的交互</font>**

#### 1、声明式

你只需要描述 UI（HTML）看起来是什么样，就跟写HTML一样

<font color='red'>**React 负责渲染 UI，并在数据变化时更新 UI**</font>

![1650165454554](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650165454554.png)

#### 2、基于组件

> 1. <font color='blue'>组件是 React 最重要的内容</font>
> 2. 组件表示页面中的部分内容
> 3. 组合、复用多个组件，可以实现完整的页面功能

### 3、随地使用

- 使用 React 可以开发 Web 应用
- 使用 React 可以开发移动端原生应用（react-native）
- 使用 React 可以开发 VR（虚拟现实）应用（react 360）

## 二、React的基本使用

### 1、React的安装

> <font color='red'>安装命令：npm i react react-dom</font>

**react 包是核心，提供创建元素、组件等功能**

**react-dom 包提供 DOM 相关功能等**

### 2、React的使用

1. 引入 react 和 react-dom 两个 js 文件

   ![1650165599815](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650165599815.png)

2. 创建 React 元素

3. 渲染 React 元素到页面中

![1650171002283](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650171002283.png)

### 3、方法说明

#### React.createElement() 说明

![1650171048240](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650171048240.png)

#### ReactDOM.render() 说明！！

![1650171068555](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650171068555.png)

## 三、React 脚手架的使用

### 1、React脚手架意义

1. <font color='red'>脚手架是开发 现代Web 应用的必备。</font>

2. 充分利用 Webpack、Babel、ESLint 等工具辅助项目开发。
3. 零配置，无需手动配置繁琐的工具即可使用。
4. 关注业务，而不是工具配置。

### 2、使用 React 脚手架初始化项目

1. 初始化项目，命令：npx create-react-app my-app

![1650171157884](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650171157884.png)

2. 启动项目，在项目根目录执行命令：npm start![1650171184578](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650171184578.png)

##### npx 命令介绍

> npm v5.2.0 引入的一条命令
>
> <font color='red'>目的：提升包内提供的命令行工具的使用体验</font>
>
> - 原来：先安装脚手架包，再使用这个包中提供的命令
> - 现在：无需安装脚手架包，就可以直接使用这个包提供的命令

<font color='green'>**推荐使用：npx create-react-app my-app**</font>

- npm init react-app my-app
- yarn create react-app my-app

> 1. yarn 是 Facebook 发布的包管理器，可以看做是 npm 的替代品，功能与 npm 相同
> 2. yarn 具有快速、可靠和安全的特点
> 3. 初始化新项目：yarn init
> 4. 安装包： yarn add 包名称
> 5. 安装项目依赖项： yarn
> 6. 其他命令，请参考yarn文档

### 3、在脚手架中使用 React

1. 导入 react 和 react-dom 两个包

![1650171326939](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650171326939.png)

2. <font color='blue'>调用 React.createElement() 方法创建 react 元素。</font>
3. <font color='red'>调用 ReactDOM.render() 方法渲染 react 元素到页面中。</font>

## 总结

> <font color='red'>**React 基础**</font>
>
> 1. React是构建用户界面的JavaScript库
> 2. 使用 react 时，推荐使用脚手架方式。
> 3. 初始化项目命令：npx create-react-app my-app 。
> 4. 启动项目命令：yarn start（或 npm start）。
> 5. **React.createElement() 方法用于创建 react 元素（知道）。**
> 6. **ReactDOM.render() 方法负责渲染 react 元素到页面中。**

# JSX

## 一、JSX 的基本使用

### 1、createElement() 的问题

1. 繁琐不简洁。
2. 不直观，无法一眼看出所描述的结构。
3. 不优雅，用户体验不爽。

![1650171486641](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650171486641.png)

### 2、JSX 简介

<font color='red'>JSX 是 JavaScript XML 的简写，表示在 JavaScript 代码中写 XML（HTML） 格式的代码。</font>

优势：声明式语法更加直观、与HTML结构相同，降低了学习成本、提升开发效率

**JSX 是 React 的核心内容。**

### 3、使用步骤

1. 使用 JSX 语法创建 react 元素

![1650171562425](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650171562425.png)

2. <font color='blue'>使用 ReactDOM.render() 方法渲染 react 元素到页面中</font>

![1650171578783](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650171578783.png)

**JSX语法更能体现React的声明式特点（描述UI长什么样子）**

![1650171605656](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650171605656.png)

![1650171624675](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650171624675.png)

### 4、注意点

1. React元素的属性名使用驼峰命名法

2. <font color='green'>特殊属性名：class -> className、for -> htmlFor、tabindex -> tabIndex 。</font>
3. **没有子节点的React元素可以用 /> 结束** 。
4. **推荐：使用小括号包裹 JSX ，从而避免 JS 中的自动插入分号陷阱。**

![1650171695697](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650171695697.png)

## 二、JSX 中使用 JavaScript 表达式

### 1、嵌入 JS 表达式

<font color='red'>**数据存储在JS中**</font>

**语法：{ JavaScript表达式 }**

注意：语法中是单大括号，不是双大括号！

![1650171747593](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650171747593.png)

### 2、注意点

> 1. 单大括号中可以使用任意的 JavaScript 表达式
> 2. **JSX 自身也是 JS 表达式**
> 3. <font color='orange'>注意：JS 中的对象是一个例外，一般只会出现在 style 属性中</font>
> 4. <font color='red'>注意：不能在{}中出现语句（比如：if/for 等）</font>

![1650171806464](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650171806464.png)

## 三、JSX 的条件渲染

场景：loading效果

> 1. <font color='red'>**条件渲染：根据条件渲染特定的 JSX 结构**</font>
> 2. **可以使用if/else或三元运算符或逻辑与运算符来实现**

![1650171859055](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650171859055.png)

![1650171988468](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650171988468.png)

## 四、JSX 的列表渲染

<font color='red'>**如果要渲染一组数据，应该使用数组的map() 方法**</font>

![1650172032328](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650172032328.png)

> 如果要渲染一组数据，应该使用数组的map() 方法
>
> <font color='blue'>注意：渲染列表时应该添加 key 属性，key 属性的值要保证唯一</font>
>
> **原则：map() 遍历谁，就给谁添加 key 属性**
>
> 注意：尽量避免使用索引号作为 key

![1650172077886](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650172077886.png)

## 五、JSX 的样式处理

### 1. 行内样式 — style

![1650172134501](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650172134501.png)

### 2. 类名 — className（推荐）

![1650172166249](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650172166249.png)

## 总结

### JSX

> 1. JSX 是React 的核心内容。
> 2. **JSX 表示在JS代码中写HTML结构，是React声明式的体现。**
> 3. 使用 JSX 配合嵌入的 JS 表达式、条件渲染、列表渲染，可以描述任意 UI
> 结构。
> 4. **推荐使用 className 的方式给JSX添加样式。**
> 5. React 完全利用 JS 语言自身的能力来编写UI，而不是造轮子增强 HTML 功
> 能。

# React组件基础

## 一、React 组件介绍

**组件是 React 的一等公民，使用 React 就是在用组件**

组件表示页面中的部分功能

<font color='red'>组合多个组件实现完整的页面功能</font>

<font color='blue'>**特点：可复用、独立、可组合**</font>

## 二、React 组件的两种创建方式

1. <font color='red'>**使用函数创建组件**</font>

2. <font color='red'>**使用类创建组件**</font>

### 1、使用函数创建组件

> <font color='red'>函数组件：使用 JS 的函数（或箭头函数）创建的组件</font>
>
> 1. 约定1：**函数名称必须以大写字母开头**
> 2. 约定2：**函数组件必须有返回值，表示该组件的结构**
>
> 如果返回值为 null，表示不渲染任何内容

![1650172361567](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650172361567.png)

> <font color='red'>渲染函数组件：用函数名作为组件标签名</font>
>
> 组件标签可以是单标签也可以是双标签

![1650172393744](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650172393744.png)

> 使用JS中的函数创建的组件叫做：函数组件
>
> 函数组件必须有返回值
>
> <font color='red'>组件名称必须以大写字母开头， React 据此区分 组件 和 普通的React 元素</font>
>
> **使用函数名作为组件标签名**

### 2、使用类创建组件

> 类组件：使用 ES6 的 class 创建的组件
>
> 1. 约定1：**类名称也必须以大写字母开头**
> 2. 约定2：<font color='red'>类组件应该继承 React.Component 父类，从而可以使用父类中提供的方法或属性</font>
> 3. 约定3：<font color='red'>类组件必须提供 render() 方法</font>
> 4. 约定4：<font color='green'>**render() 方法必须有返回值，表示该组件的结构**</font>

![1650172521810](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650172521810.png)

### 3、抽离为独立 JS 文件

思考：项目中的组件多了之后，该如何组织这些组件呢？

1. 选择一：将所有组件放在同一个JS文件中
2. 选择二：将每个组件放到单独的JS文件中

**组件作为一个独立的个体，一般都会放到一个单独的 JS 文件中**

> 1. 创建Hello.js
> 2. 在 Hello.js 中导入React
> 3. 创建组件（函数 或 类）
> 4. 在 Hello.js 中导出该组件
> 5. 在 index.js 中导入 Hello 组件
> 6. 渲染组件

![1650172597406](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650172597406.png)

![1650172609177](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650172609177.png)

## 三、React 事件处理

1. <font color='red'>事件绑定</font>

2. <font color='blue'>事件对象</font>

### 1、事件绑定

<font color='red'>React 事件绑定语法与 DOM 事件语法相似</font>

<font color='blue'>**语法：on+事件名称={事件处理程序}，比如：onClick={() => {}}**</font>

注意：React 事件采用驼峰命名法，比如：onMouseEnter、onFocus

在类/函数组件中绑定事件：

![1650172699912](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650172699912.png)

### 2、事件对象

1. <font color='red'>可以通过事件处理程序的参数获取到事件对象</font>
2. **React 中的事件对象叫做：合成事件（对象）**
3. <font color='blue'>合成事件：兼容所有浏览器，无需担心跨浏览器兼容性问题</font>

![1650172801389](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650172801389.png)

## 四、有状态组件和无状态组件

1. <font color='red'>**函数组件又叫做无状态组件，类组件又叫做有状态组件**</font>
2. **状态（state）即数据**
3. **函数组件没有自己的状态，只负责数据展示（静）**
4. 类组件有自己的状态，负责更新 UI，让页面“动” 起来

![1650172845265](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650172845265.png)

## 五、组件中的 state 和 setState()

1. state的基本使用
2. setState()修改状态

### 1、state的基本使用

- <font color='blue'>状态（state）即数据，是组件内部的私有数据，只能在组件内部使用</font>
- <font color='red'>**state 的值是对象，表示一个组件中可以有多个数据**</font>

![1650172930923](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650172930923.png)

<font color='red'>**获取状态：this.state**</font>

![1650172973616](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650172973616.png)

> 1. 状态即数据
> 2. 状态是私有的，只能在组件内部使用
> 3. 通过 this.state 来获取状态

### 2、setState()修改状态

1. **状态是可变的**
2. <font color='red'>语法：this.setState({ 要修改的数据 })</font>
3. 注意：<font color='blue'>不要直接修改 state 中的值，这是错误的！！！</font>
4. <font color='orange'>**setState() 作用：1. 修改 state 2. 更新UI**</font>
5. <font color='blue'>思想：数据驱动视图</font>

![1650173056947](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650173056947.png)

### 3、从 JSX 中抽离事件处理程序

JSX 中掺杂过多 JS 逻辑代码，会显得非常混乱

**推荐：将逻辑抽离到单独的方法中，保证 JSX 结构清晰**

![1650173111950](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650173111950.png)

## 六、事件绑定 this 指向

1. <font color='red'>箭头函数</font>
2. Function.prototype.bind()
3. <font color='red'>class 的实例方法</font>

### 1、箭头函数

> 利用箭头函数自身不绑定this的特点
>
> <font color='red'>render() 方法中的 this 为组件实例，可以获取到 setState()</font>

![1650173188076](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650173188076.png)

### 2、Function.prototype.bind()

**利用ES5中的bind方法，将事件处理程序中的this与组件实例绑定到一起**

![1650173243407](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650173243407.png)

### 3、class 的实例方法

1. <font color='red'>利用箭头函数形式的class实例方法</font>
2. 注意：该语法是实验性语法，但是，由于babel的存在可以直接使用

![1650173286020](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650173286020.png)

### 总结

> 1. <font color='red'>推荐：使用class的实例方法</font>
> 2. 箭头函数
> 3. bind

![1650173336253](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650173336253.png)

## 七、表单处理

1. 受控组件
2. **非受控组件（DOM方式）**

### 1、受控组件

HTML 中的表单元素是可输入的，也就是有自己的可变状态

而，<font color='red'>React 中可变状态通常保存在 state 中，并且只能通过 setState() 方法来修改</font>

![1650173414562](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650173414562.png)

- HTML 中的表单元素是可输入的，也就是有自己的可变状态
- 而，<font color='red'>React 中可变状态通常保存在 state 中，并且只能通过 setState() 方法来修改</font>
- React将 state 与表单元素值value绑定到一起，由 state 的值来控制表单元素的值
- <font color='red'>**受控组件：其值受到 React 控制的表单元素**</font>

![1650173459729](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650173459729.png)

#### 步骤

1. <font color='red'>在 state 中添加一个状态，作为表单元素的value值（控制表单元素值的来源）</font>

![1650173487166](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650173487166.png)

2. <font color='blue'>给表单元素绑定 change 事件，将**表单元素的值**设置为 state 的值（控制表单元素值的变化）</font>

![1650173530899](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650173530899.png)

#### 示例

1. 文本框、富文本框、下拉框 操作value属性
2. 复选框 操作checked属性

![1650173639960](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650173639960.png)

#### 多表单元素优化！！！

> - 问题：每个表单元素都有一个单独的事件处理程序处理太繁琐
> - 优化：<font color='red'>使用一个事件处理程序同时处理多个表单元素</font>

> 1. <font color='red'>给表单元素添加name属性，名称与 state 相同</font>
> 2. 根据表单元素类型获取对应值
> 3. 在 change 事件处理程序中通过 [name] 来修改对应的state

![1650174269753](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650174269753.png)

### 2、非受控组件

说明：借助于 ref，使用原生 DOM 方式来获取表单元素值

<font color='red'>**ref 的作用：获取 DOM 或组件**</font>

#### 使用步骤：

1. 调用 React.createRef() 方法创建一个 ref 对象

![1650174451510](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650174451510.png)

2. 将创建好的 ref 对象添加到文本框中

![1650174503550](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650174503550.png)

3. 通过 ref 对象获取到文本框的值

![1650174524603](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650174524603.png)

![1650174547281](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650174547281.png)

### 案例：评论列表

> ① 渲染评论列表（列表渲染）
>
> ② 没有评论数据时渲染：暂无评论（条件渲染）
>
> ③ 获取评论信息，包括评论人和评论内容（受控组件）
>
> ④ 发表评论，更新评论列表（setState()）

#### 1. 渲染评论列表

> ① 在 state 中初始化评论列表数据
>
> ② 使用数组的map方法遍历state中的列表数据
>
> ③ 给每个被遍历的li元素添加key属性

![1650174671697](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650174671697.png)

#### 2. 渲染暂无评论

> ① 判断列表数据的长度是否为0
>
> ② 如果为0，则渲染暂无评论

#### 3. 获取评论信息

> ① 使用受控组件方式处理表单元素

#### 4. 发表评论

> ① 给按钮绑定单击事件
>
> ② 在事件处理程序中，通过state获取评论信息
>
> ③ 将评论信息添加到state中，并调用 setState() 方法更新state
>
> ④ 边界情况：清空文本框
>
> ⑤ 边界情况：非空判断

![1650174882770](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650174882770.png)

## React 组件基础总结

> 1. <font color='red'>组件的两种创建方式：函数组件和类组件</font>
> 2. **无状态（函数）组件，负责静态结构展示**
> 3. **有状态（类）组件，负责更新 UI ，让页面动起来**
> 4. 绑定事件注意 this 指向问题
> 5. 推荐使用受控组件来处理表单
> 6. 完全利用 JS 语言的能力创建组件，这是 React 的思想

# React 组件进阶

## 一、组件通讯介绍

<font color='red'>组件是独立且封闭的单元，</font>默认情况下，只能使用组件自己的数据。在组件化过程中，我们将一个完整的功能
拆分成多个组件，以更好的完成整个应用的功能。而在这个过程中，<font color='blue'>多个组件之间不可避免的要共享某些数据
。为了实现这些功能，就需要打破组件的独立封闭性，让其与外界沟通。这个过程就是组件通讯。</font>

## 二、组件的 props

> 1. <font color='red'>组件是封闭的，要接收外部数据应该通过props 来实现</font>
> 2. <font color='red'>props的作用：接收传递给组件的数据</font>
> 3. **传递数据：给组件标签添加属性**
> 4. <font color='blue'>接收数据：函数组件通过参数props接收数据，类组件通过 this.props 接收数据</font>

![1650175242366](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650175242366.png)

### 特点

1. <font color='red'>可以给组件传递任意类型的数据</font>
2. **props 是只读的对象，只能读取属性的值，无法修改对象**
3. <font color='blue'>注意：使用类组件时，如果写了构造函数，应该将 props 传递给 super()，否则，无法在构造函数中获取到 props！</font>

![1650175316355](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650175316355.png)

## 三、组件通讯的三种方式

组件之间的通讯分为 3 种：
1. 父组件 -> 子组件
2. 子组件 -> 父组件
3. 兄弟组件

### 1、父组件传递数据给子组件

> 1. <font color='red'>父组件提供要传递的state数据</font>
> 2. **给子组件标签添加属性，值为 state 中的数据**
> 3. <font color='blue'>**子组件中通过 props 接收父组件中传递的数据**</font>

![1650175415133](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650175415133.png)

### 2、子组件传递数据给父组件

> 思路：<font color='red'>**利用回调函数，父组件提供回调，子组件调用，将要传递的数据作为回调函数的参数。**</font>
> 1. <font color='blue'>父组件提供一个回调函数（用于接收数据）</font>
> 2. <font color='green'>**将该函数作为属性的值，传递给子组件**</font>
> 3. <font color='red'>子组件通过 props 调用回调函数</font>
> 4. <font color='orange'>**将子组件的数据作为参数传递给回调函数**</font>

![1650175562755](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650175562755.png)

**注意：回调函数中 this 指向问题！**

### 3、兄弟组件

> 1. <font color='red'>**将共享状态提升到最近的公共父组件中，由公共父组件管理这个状态**</font>思想：状态提升
> 2. <font color='green'>**公共父组件职责：1. 提供共享状态 2. 提供操作共享状态的方法**</font>
> 3. **要通讯的子组件只需通过 props 接收状态或操作状态的方法**

![1650175684698](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650175684698.png)

![1650175710186](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650175710186.png)

## 四、 Context

思考：App 组件要传递数据给 Child 组件，该如何处理？

- 处理方式：使用 props 一层层组件往下传递（繁琐）

更好的姿势：<font color='red'>**使用 Context**</font>

<font color='blue'>**作用：跨组件传递数据（比如：主题、语言等）**</font>

### 使用步骤

1. 调用 React. createContext() 创建 Provider（提供数据） 和 Consumer（消费数据） 两个组件。

![1650175858742](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650175858742.png)

2. **使用 Provider 组件作为父节点。**

![1650175873389](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650175873389.png)

3. <font color='blue'>设置 value 属性，表示要传递的数据。</font>

![1650175889286](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650175889286.png)

4. 调用 Consumer 组件接收数据。

![1650175915790](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650175915790.png)

### 总结

> 1. 如果两个组件是远方亲戚（比如，嵌套多层）可以使用Context实现组件通讯
> 2. <font color='red'>Context提供了两个组件：Provider 和 Consumer</font>
> 3. Provider组件：用来提供数据
> 4. Consumer组件：用来消费数据

![1650175984223](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650175984223.png)

## 五、props 深入

### 1、children 属性

- <font color='red'>children 属性：表示组件标签的子节点。当组件标签有子节点时，props 就会有该属性</font>
- children 属性与普通的props一样，值可以是任意值（文本、React元素、组件，甚至是函数）

![1650176037138](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650176037138.png)

![1650176078791](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650176078791.png)

### 2、props 校验

<font color='red'>对于组件来说，props 是外来的，无法保证组件使用者传入什么格式的数据</font>

**如果传入的数据格式不对，可能会导致组件内部报错**

**关键问题：组件的使用者不知道明确的错误原因**

![1650176112984](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650176112984.png)

<font color='red'>**props 校验：允许在创建组件的时候，就指定 props 的类型、格式等**</font>

**作用：捕获使用组件时因为props导致的错误，给出明确的错误提示，增加组件的健壮性**

![1650176141099](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650176141099.png)

> 使用步骤
> 1. 安装包 prop-types （yarn add prop-types / npm i props-types）
> 2. 导入 prop-types 包
> 3. <font color='blue'>使用组件名.propTypes = {} 来给组件的props添加校验规则</font>
> 4. <font color='blue'>校验规则通过 PropTypes 对象来指定</font>

![1650176184445](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650176184445.png)

#### 约束规则

1. <font color='red'>常见类型：array、bool、func、number、object、string</font>
2. React元素类型：element
3. <font color='red'>必填项：isRequired</font>
4. <font color='orange'>**特定结构的对象：shape({ })**</font>

![1650176283591](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650176283591.png)

![1650176314029](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650176314029.png)

### 3、props 的默认值

场景：分页组件  每页显示条数

<font color='red'>作用：给 props 设置默认值，在未传入 props 时生效</font>

![1650176338692](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650176338692.png)

![1650176380815](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650176380815.png)

## 六、组件的生命周期

### 1、组件的生命周期概述

1. 意义：组件的生命周期有助于理解组件的运行方式、完成更复杂的组件功能、分析组件错误原因等
2. <font color='blue'>组件的生命周期：组件从被创建到挂载到页面中运行，再到组件不用时卸载的过程</font>
3. <font color='green'>生命周期的每个阶段总是伴随着一些方法调用，这些方法就是生命周期的钩子函数。</font>
4. 钩子函数的作用：为开发人员在不同阶段操作组件提供了时机。

<font color='red'>只有**类组件** 才有生命周期。</font>

### 2、生命周期的三个阶段

> 1. 每个阶段的执行时机
> 2. 每个阶段钩子函数的执行顺序
> 3. 每个阶段钩子函数的作用

![1650176475141](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650176475141.png)

#### 1. 创建时（挂载阶段）

<font color='red'>执行时机：组件创建时（页面加载时）</font>

执行顺序：

![1650176507936](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650176507936.png)

![1650176947018](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650176947018.png)

#### 2. 更新时（更新阶段）

<font color='red'>执行时机：1. setState()  2. forceUpdate()  3. 组件接收到新的props</font>

说明：以上三者任意一种变化，组件就会重新渲染

执行顺序：

![1650176552154](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650176552154.png)

![1650176976739](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650176976739.png)

#### 3. 卸载时（卸载阶段）

**执行时机：组件从页面中消失**

![1650176569225](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650176569225.png)

![1650176597150](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650176597150.png)

![1650177003747](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650177003747.png)

## 七、render-props和高阶组件

### 1、React组件复用概述

> 思考：**如果两个组件中的部分功能相似或相同，该如何处理？**
>
> - 处理方式：复用相似的功能（联想函数封装）
>
> 复用什么？<font color='red'>1. state 2. 操作state的方法 （组件状态逻辑 ）</font>
>
> - 两种方式：<font color='blue'>**1. render props模式 2. 高阶组件（HOC）**</font>
>
> 注意：这两种方式不是新的API，而是利用React自身特点的编码技巧，演化而成的固定模式（写法）

### 2、render props 模式

#### 思路分析

1. 思路：将要复用的state和操作state的方法封装到一个组件中

2. <font color='red'>问题1：如何拿到该组件中复用的state？</font>

3. 在使用组件时，添加一个值为函数的prop，通过 **函数参数** 来获取（需要组件内部实现）

   ![1650176741153](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650176741153.png)

4. <font color='blue'>问题2：如何渲染任意的UI？</font>

5. 使用该函数的返回值作为要渲染的UI内容（需要组件内部实现）

   ![1650176752224](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650176752224.png)

#### 使用步骤

1. <font color='red'>创建Mouse组件，在组件中提供复用的状态逻辑代码（1. 状态 2. 操作状态的方法）</font>
2. <font color='blue'>将要复用的状态作为 props.render(state) 方法的参数，暴露到组件外部</font>
3. <font color='red'>使用 props.render() 的返回值作为要渲染的内容</font>

![1650176804809](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650176804809.png)

#### 演示Mouse组件的复用

- <font color='red'>Mouse组件负责：封装复用的状态逻辑代码（1. 状态 2. 操作状态的方法）</font>
- 状态：鼠标坐标（x, y）
- <font color='red'>操作状态的方法：鼠标移动事件</font>
- <font color='blue'>传入的render prop负责：使用复用的状态来渲染UI结构</font>

![1650177056055](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650177056055.png)

#### children代替render属性

> 1. 注意：并不是该模式叫 render props 就必须使用名为render的prop，<font color='red'>实际上可以使用任意名称的prop</font>
> 2. <font color='red'>**把prop是一个函数并且告诉组件要渲染什么内容的技术叫做：render props模式**</font>
> 3. **推荐：使用 children 代替 render 属性**

![1650177114412](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650177114412.png)

#### 代码优化

1. 推荐：给 render props 模式添加 props校验
2. 应该在组件卸载时解除 mousemove 事件绑定

![1650177136022](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650177136022.png)

### 3、高阶组件

<font color='red'>目的：实现状态逻辑复用</font>

采用 包装（装饰）模式 ，比如说：手机壳

手机：获取保护功能

手机壳 ：提供保护功能

**高阶组件就相当于手机壳，通过包装组件，增强组件功能**

#### 思路分析

<font color='red'>**高阶组件（HOC，Higher-Order Component）是一个函数，接收要包装的组件，返回增强后的组件**</font>

高阶组件内部创建一个类组件，**在这个类组件中提供复用的状态逻辑代码，通过prop将复用的状态传递给**
**被包装组件 WrappedComponent**

![1650177207052](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650177207052.png)

#### 使用步骤

1. 创建一个函数，名称约定以 with 开头![1650177233991](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650177233991.png)

2. 指定函数参数，参数应该以大写字母开头（作为要渲染的组件）

![1650177255135](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650177255135.png)

3. **在函数内部创建一个类组件，提供复用的状态逻辑代码，并返回**
4. 在该组件中，渲染参数组件，同时将状态通过prop传递给参数组件

![1650177278245](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650177278245.png)

5. 调用该高阶组件，传入要增强的组件，通过返回值拿到增强后的组件，并将其渲染到页面中

![1650177294458](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650177294458.png)

![1650177357504](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650177357504.png)

#### 设置displayName

> - 使用高阶组件存在的问题：得到的两个组件名称相同
> - **原因：默认情况下，React使用组件名称作为 displayName**
> - <font color='red'>**解决方式：为 高阶组件 设置 displayName 便于调试时区分不同的组件**</font>
> - <font color='red'>displayName的作用：用于设置调试信息（React Developer Tools信息）</font>
>
> 设置方式：

![1650177413364](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650177413364.png)

![1650177460583](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650177460583.png)

#### 传递props

> 问题：props丢失
>
> **原因：高阶组件没有往下传递props**
>
> <font color='blue'>解决方式：渲染 WrappedComponent 时，将 state 和 this.props 一起传递给组件</font>
>
> 传递方式：

![1650177493748](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650177493748.png)

![1650177528476](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650177528476.png)

## React组件进阶

> 1. 组件通讯是构建 React 应用必不可少的一环。
> 2. props 的灵活性让组件更加强大。
> 3. 状态提升是React组件的常用模式。
> 4. 组件生命周期有助于理解组件的运行过程。
> 5. 钩子函数让开发者可以在特定的时机执行某些功能。
> 6. render props模式和高阶组件都可以实现组件状态逻辑复用。
> 7. 组件极简模型： (state, props) => UI

# React原理解密

