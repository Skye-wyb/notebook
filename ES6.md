# ECMASript 相关介绍

## 1.1. 什么是 ECMA

ECMA（European Computer Manufacturers Association）中文名称为欧洲计算机制造商协会，这个组织的目标是评估、开发和认可电信和计算机标准。1994 年后该组织改名为 Ecma 国际。

## 1.2. 什么是 ECMAScript

![1650533955719](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650533955719.png)

![1650533995470](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650533995470.png)

# ECMASript 6 新特性

## 2.1. let 关键字

let 关键字用来声明变量，使用 let 声明的变量有几个特点：

> 1) 不允许重复声明
>
> 2) 块级作用域
>
> 3) 不存在变量提升
>
> 4) 不影响作用域链

用 应用场景：以后声明变量使用 let 就对了

## 2.2. const 关键字

<font color='red'>const 关键字用来声明常量，const 声明有以下特点</font>

> 1) 声明必须赋初始值
>
> 2) 标识符一般为大写
>
> 3) 不允许重复声明
>
> 4) 值不允许修改
>
> 5) 块级作用域

注意: 对象属性修改和数组元素变化不会出发 const 错误

应用场景：声明对象类型使用 const，非对象类型声明选择 let

## 2.3. 变量的解构赋值

ES6 允许按照一定模式，从数组和对象中提取值，对变量进行赋值，这被称为解构赋值。

> ![1650534140825](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650534140825.png)

> ![1650534154989](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650534154989.png)

## 2.4. 模板字符串

<font color='red'>模板字符串（template string）是增强版的字符串，用反引号（`）标识，特点：</font>

> 1. <font color='red'>字符串中可以出现换行符</font>
> 2. **可以使用 ${xxx} 形式输出变量**

> ![1650534318800](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650534318800.png)

**<font color='blue'>注意：当遇到字符串与变量拼接的情况使用模板字符串</font>**

## 2.5. 简化对象写法

<font color='red'>ES6 允许在大括号里面，直接写入变量和函数，作为对象的属性和方法。</font>这样的书写更加简洁。

> ![1650534422220](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650534422220.png)

<font color='red'>注意：对象简写形式简化了代码，所以以后用简写就对了</font>

## 2.6. 箭头函数

<font color='blue'>ES6 允许使用「箭头」（=>）定义函数。</font>

> ![1650534543465](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650534543465.png)

> 箭头函数的注意点:
>
> 1. <font color='red'>如果形参只有一个，则小括号可以省略</font>
> 2. <font color='blue'>函数体如果只有一条语句，则花括号可以省略，函数的返回值为该条语句的执行结果</font>
> 3. <font color='hotpink'>箭头函数 this 指向声明时所在作用域下 this 的值</font>
> 4. 箭头函数不能作为构造函数实例化
> 5. **不能使用 arguments**

> ![1650534672068](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650534672068.png)

<font color='hotpink'>注意：箭头函数不会更改 this 指向，用来指定回调函数会非常合适</font>

#### 函数形参赋初始值

![1650535713596](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650535713596.png)

## 2.7. rest 参数

**剩余参数**

<font color='hotpink'>**ES6 引入 rest 参数，用于获取函数的实参，用来代替 arguments**</font>

> ![1650534773915](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650534773915.png)

![1650534983166](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650534983166.png)

<font color='red'>**注意：rest 参数非常适合不定个数参数函数的场景**</font>

## 2.8. spread 扩展运算符

**扩展运算符（spread）也是三个点（...）。它好比 rest 参数的逆运算，<font color='hotpink'>将一个数组转为用逗号分隔的参数序列，对数组进行解包。</font>**

> ![1650535190411](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650535190411.png)

![1650535237135](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650535237135.png)

## 2.9. Symbol

### 2.9.1. Symbol 基本使用

<font color='hotpink'>ES6 引入了一种新的原始数据类型 Symbol，表示独一无二的值。</font>它是JavaScript 语言的第七种数据类型，是一种类似于字符串的数据类型。

<font color='red'>Symbol 特点</font>

> 1. <font color='hotpink'>Symbol 的值是唯一的，用来解决命名冲突的问题</font>
> 2. <font color='green'>**Symbol 值不能与其他数据进行运算**</font>
> 3. **Symbol 定义的对象属性不能使用 for…in 循环遍历，但是可以使用Reflect.ownKeys 来获取对象的所有键名**

> ![1650535391097](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650535391097.png)

![1650535402989](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650535402989.png)

****

<font color='red'>注：遇到唯一性的场景时要想到 Symbol</font>

### 2.9.2. Symbol 内置值

除了定义自己使用的 Symbol 值以外，<font color='red'>ES6 还提供了11个内置的Symbol值，指向语言内部使用的方法。</font>**可以称这些方法为魔术方法，因为它们会在特定的场景下自动执行。**

| 方法                                        | 解释                                                         |
| ------------------------------------------- | ------------------------------------------------------------ |
| Symbol.hasInstance                          | 当其他对象使用 instanceof 运算符，判断是否为该对象的实例时，会调用这个方法 |
| Symbol.isConcatSpreadable                   | 对象的 Symbol.isConcatSpreadable 属性等于的是一个布尔值，表示该对象用于 Array.prototype.concat()时，是否可以展开。 |
| Symbol.species                              | 创建衍生对象时，会使用该属性                                 |
| <font color='hotpink'>Symbol.match</font>   | 当执行 str.match(myObject) 时，如果该属性存在，会调用它，返回该方法的返回值。 |
| <font color='hotpink'>Symbol.replace</font> | 当该对象被 str.replace(myObject)方法调用时，会返回该方法的返回值。 |
| <font color='hotpink'>Symbol.search</font>  | 当该对象被 str. search (myObject)方法调用时，会返回该方法的返回值。 |
| <font color='hotpink'>Symbol.split</font>   | 当该对象被 str. split (myObject)方法调用时，会返回该方法的返回值。 |
| Symbol.iterator                             | 对象进行 for...of 循环时，会调用 Symbol.iterator 方法，返回该对象的默认遍历器 |
| Symbol.toPrimitive                          | 该对象被转为原始类型的值时，会调用这个方法，返回该对象对应的原始类型值。 |
| Symbol. toStringTag                         | 在该对象上面调用 toString 方法时，返回该方法的返回值         |
| Symbol. unscopables                         | 该对象指定了使用 with 关键字时，哪些属性会被 with环境排除。  |

## 2.10. 迭代器

<font color='hotpink'>**遍历器（Iterator）就是一种机制。它是一种接口，为各种不同的数据结构提供统一的访问机制。任何数据结构只要部署 Iterator 接口，就可以完成遍历操作。**</font>

1. <font color='blue'>ES6 创造了一种新的遍历命令 for...of 循环，Iterator 接口主要供 for...of 消费</font>

2. 原生具备 iterator 接口的数据(可用 for of 遍历)

> 1. Array
> 2. Arguments
> 3. Set
> 4. Map
> 5. String
> 6. TypedArray
> 7. NodeList

3. 工作原理

- 创建一个指针对象，指向当前数据结构的起始位置
- **第一次调用对象的 next 方法，指针自动指向数据结构的第一个成员**
- 接下来不断调用 next 方法，指针一直往后移动，直到指向最后一个成员

- <font color='red'>每调用 next 方法返回一个包含 value 和 done 属性的对象</font>

注: 需要自定义遍历数据的时候，要想到迭代器。

## 2.11. 生成器

**生成器函数是 ES6 提供的一种异步编程解决方案，语法行为与传统函数完全不同**

> ![1650536232558](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650536232558.png)

![1650536268891](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650536268891.png)

> 代码说明：
>
> * <font color='red'>*的位置没有限制</font>
> * <font color='hotpink'>生成器函数返回的结果是迭代器对象，调用迭代器对象的 next 方法可以得到yield 语句后的值</font>
> * **yield 相当于函数的暂停标记，也可以认为是函数的分隔符，每调用一次 next方法，执行一段代码**
> * **next 方法可以传递实参，作为 yield 语句的返回值**

## 2.12. Promise

Promise 是 ES6 引入的异步编程的新解决方案。语<font color='red'>法上 Promise 是一个构造函数，用来封装异步操作并可以获取其成功或失败的结果。</font>

> 1. <font color='hotpink'>Promise 构造函数：Promise (excutor) {  }</font>
> 2. <font color='hotpink'>Promise.prototype.then 方法</font>
> 3. <font color='hotpink'>Promise.prototype.catch 方法</font>

## 2.13. Set

ES6 提供了新的数据结构 Set（集合）。<font color='hotpink'>它类似于数组，但成员的值都是唯一的，集合实现了 iterator 接口，</font>所以可以使用『扩展运算符』和『for…of…』进行遍历，集合的属性和方法：

1. size 返回集合的元素个数
2. add 增加一个新元素，返回当前集合
3. delete 删除元素，返回 boolean 值
4. has 检测集合中是否包含某个元素，返回 boolean 值
5. clear 清空集合，返回 undefined

> ![1650536582217](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650536582217.png)

## 2.14. Map

ES6 提供了 Map 数据结构。它类似于对象，也是键值对的集合。但是“键”的范围不限于字符串，各种类型的值（包括对象）都可以当作键。Map 也实现了iterator 接口，所以可以使用『扩展运算符』和『for…of…』进行遍历。

> Map 的属性和方法：
>
> 1. size 返回 Map 的元素个数
> 2. set 增加一个新元素，返回当前 Map
> 3. get 返回键名对象的键值
> 4. has 检测 Map 中是否包含某个元素，返回 boolean 值
> 5. clear 清空集合，返回 undefined

> ![1650541469287](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650541469287.png)

## 2.15. class 类

ES6 提供了更接近传统语言的写法，引入了 Class（类）这个概念，作为对象的模板。通过 class 关键字，可以定义类。基本上，ES6 的 class 可以看作只是一个语法糖，它的绝大部分功能，ES5 都可以做到，新的 class 写法只是让对象原型的写法更加清晰、更像面向对象编程的语法而已。

知识点：

> 1. class 声明类
> 2. constructor 定义构造函数初始化
> 3. extends 继承父类
> 4. super 调用父级构造方法
> 5. static 定义静态方法和属性
> 6. 父类方法可以重写

> ![1650541654105](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650541654105.png)

## 2.16. 数值扩展

### 2.16.1. 二进制和八进制

ES6 提供了二进制和八进制数值的新的写法，分别用前缀 0b 和 0o 表示。

### 2.16.2. Number.isFinite() 与 与 Number.isNaN()

<font color='red'>Number.isFinite() 用来检查一个数值是否为有限的</font>

<font color='red'>Number.isNaN() 用来检查一个值是否为 NaN</font>

### 2.16.3. Number.parseInt() 与 与 Number.parseFloat()

**ES6 将全局方法 parseInt 和 parseFloat，移植到 Number 对象上面，使用不变。**

### 2.16.4. Math.trunc

<font color='blue'>用于去除一个数的小数部分，返回整数部分。</font>

### 2.16.5. Number.isInteger

Number.isInteger() 用来判断一个数值是否为整数

## 2.17. 对象扩展

ES6 新增了一些 Object 对象的方法

<font color='blue'>Object.is 比较两个值是否严格相等，与『===』行为基本一致（+0 与 NaN）</font>

Object.assign 对象的合并，将源对象的所有可枚举属性，复制到目标对象

<font color='red'>`__proto__`、setPrototypeOf、 setPrototypeOf 可以直接设置对象的原型</font>

## 2.18. 模块化

模块化是指将一个大的程序文件，拆分成许多小的文件，然后将小文件组合起来。

### 2.18.1. 模块化的好处

模块化的优势有以下几点：

- 防止命名冲突
- 代码复用
- 高维护性

### 2.18.2. 模块化规范 产品

ES6 之前的模块化规范有：

- CommonJS => NodeJS、Browserify
- AMD => requireJS
- CMD => seaJS

### 2.18.3. ES6 模块化语法

<font color='red'>模块功能主要由两个命令构成：export 和 import。</font>

1. <font color='blue'>export 命令用于规定模块的对外接口</font>
2. <font color='hotpink'>import 命令用于输入其他模块提供的功能</font>

# 第 3 章 ECMASript 7 新特性

## 3.1. Array.prototype.includes

<font color='red'>Includes 方法用来检测数组中是否包含某个元素，返回布尔类型值</font>

## 3.2. 指数操作符

在 ES7 中引入指数运算符「**」，用来实现幂运算，功能与 Math.pow 结果相同

# 第 4 章 ECMASript 8 新特性

## 4.1. async 和 和 await

<font color='red'>async 和 await 两种语法结合可以让异步代码像同步代码一样</font>

## 4.1.1. async 函数

1. <font color='hotpink'>**async 函数的返回值为 promise 对象，**</font>
2. **promise 对象的结果由 async 函数执行的返回值决定**

## 4.1.2. await 表达式

1. <font color='red'>await 必须写在 async 函数中</font>

2. **await 右侧的表达式一般为 promise 对象**

3. <font color='hotpink'>await 返回的是 promise 成功的值</font>
4. **await 的 promise 失败了, 就会抛出异常, 需要通过 try...catch 捕获处理**

## 4.2. Object.values 和 和 Object.entries

1. <font color='red'>Object.values()方法返回一个给定对象的所有可枚举属性值的数组</font>
2. <font color='blue'>Object.entries()方法返回一个给定对象自身可遍历属性 [key,value] 的数组</font>

## 4.3. Object.getOwnPropertyDescriptors

<font color='blue'>该方法返回指定对象所有自身属性的描述对象</font>

# 第 5 章 ECMASript 9 新特性

## 5.1. Rest/Spread 属性

Rest 参数与 spread 扩展运算符在 ES6 中已经引入，不过 ES6 中只针对于数组，在 ES9 中为对象提供了像数组一样的 rest 参数和扩展运算符。

> ![1650542105954](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650542105954.png)

## 5.2. 正则表达式命名捕获组

ES9 允许命名捕获组使用符号『?<name>』,这样获取捕获结果可读性更强

> ![1650542155597](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650542155597.png)

## 5.3. 正则表达式反向断言

ES9 支持反向断言，<font color='red'>通过对匹配结果前面的内容进行判断，对匹配进行筛选。</font>

> ![1650542223277](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650542223277.png)

## 5.4. 正则表达式 dotAll 模式

<font color='red'>正则表达式中点.匹配除回车外的任何单字符，标记『s』改变这种行为，允许行终止符出现</font>

> ![1650542337709](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650542337709.png)

# Promise

## 一、Promise概述

抽象表达:

- Promise 是一门新的技术(ES6 规范)
- <font color='hotpink'>Promise 是 JS 中进行异步编程的新解决方案</font>
- 备注：旧方案是单纯使用回调函数
- ![1650545193114](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650545193114.png)

具体表达:

- <font color='red'>从语法上来说: Promise 是一个构造函数</font>
- <font color='blue'>从功能上来说: promise 对象用来封装一个异步操作并可以获取其成功/失败的结果值</font>

### 1、promise 的状态改变

#### 实例对象中的一个属性 PromiseState

三种状态：pending（未决定的）、resolved（成功）、rejected（失败）

<font color='red'>pending 变为 resolved</font>

<font color='hotpink'>pending 变为 rejected</font>

- 说明：<font color='red'>**只有这 2 种变换, 且一个 promise 对象只能改变一次**</font>
- 无论变为成功还是失败, 都会有一个结果数据
- <font color='red'>**成功的结果数据一般称为 value, 失败的结果数据一般称为 reason**</font>

#### Promise对象的值  PromiseResult

保存着异步任务成功或失败的结果

- resolve
- reject

<font color='blue'>只有上面两个函数可以修改PromiseResult的值</font>

### 2、promise 的基本流程

![1650542569653](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650542569653.png)

### 3、promise 的基本使用

#### 使用 1: 基本编码流程

![1650542620343](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650542620343.png)

![1650542636068](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650542636068.png)

![1650547584252](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650547584252.png)

#### 使用 2: 使用 promise 封装基于定时器的异步

![1650542675399](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650542675399.png)

![1650542682781](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650542682781.png)

#### 使用 3: 使用 promise 封装 ajax 异步请求⭐⭐⭐

![1650542717746](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650542717746.png)

![1650542762168](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650542762168.png)

![1650590581760](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650590581760.png)

![1650548648319](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650548648319.png)

#### 使用Promise-fs模块

![1650547964489](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650547964489.png)

#### 使用Promise封装函数-fs模块

![1650589366177](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650589366177.png)

### util.promisify方法进行promise风格转化

简化过程，不必每一步单独封装，直接使用util.promisify进行Promise转化

![1650589758831](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650589758831.png)

## 二、为什么要用 Promise?

### 1.2.1. 指定回调函数的方式更加灵活

1. 旧的：**必须在启动异步任务前指定**
2. promise：启动异步任务 => 返回promie对象 => 给promise对象绑定回调函数(甚至可以在异步任务结束后指定/多个)

### 1.2.2.<font color='red'>支持链式调用, 可以解决回调地狱问题</font>

1. 什么是回调地狱?

   <font color='red'>回调函数嵌套调用, 外部回调函数异步执行的结果是嵌套的回调执行的条件</font>

   ![1650542923275](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650542923275.png)

2. 回调地狱的缺点?

   **不便于阅读**

   **不便于异常处理**

3. 解决方案?

   <font color='red'>promise 链式调用</font>

4. 终极解决方案?

   <font color='hotpink'>async/await</font>

![1650542943449](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650542943449.png)

![1650542952350](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650542952350.png)

![1650542969494](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650542969494.png)

![1650542976808](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650542976808.png)

## 三、如何使用 Promise

### 1.3.1. API

#### 1、Promise 构造函数: Promise (excutor) {}

<font color='red'>executor 函数: 执行器 (resolve, reject) => {}</font>

**resolve 函数: 内部定义成功时我们调用的函数 value => {}**

**reject 函数: 内部定义失败时我们调用的函数 reason => {}**

<font color='hotpink'>说明：executor 会在 Promise 内部立即同步调用,异步操作在执行器中执行</font>

![1650597037842](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650597037842.png)

#### 2、Promise.prototype.<font color='hotpink'>then </font>方法: (onResolved, onRejected) => {}

- <font color='blue'>onResolved 函数: 成功的回调函数 (value) => {}</font>
- <font color='blue'>onRejected 函数: 失败的回调函数 (reason) => {}</font>

说明: 指定用于得到成功 value 的成功回调和用于得到失败 reason 的失败回调返回一个新的 promise 对象

#### 3、Promise.prototype.<font color='hotpink'>catch </font>方法: (onRejected) => {}

- onRejected 函数: 失败的回调函数 (reason) => {}

说明：<font color='red'>then()的语法糖, 相当于: then(undefined, onRejected)</font>

![1650597592500](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650597592500.png)

#### 4、<font color='red'>Promise.resolve 方法: (value)</font> => {}

- **value: 成功的数据或 promise 对象**

说明: 返回一个成功/失败的 promise 对象

![1650598010480](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650598010480.png)

![1650598020075](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650598020075.png)

#### 5、Promise.reject 方法: (reason) => {}

- reason: 失败的原因

说明: 返回一个失败的 promise 对象

![1650598260627](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650598260627.png)

![1650598269728](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650598269728.png)

#### 6、Promise.all 方法: (promises) => {}

- <font color='red'>promises: 包含 n 个 promise 的数组</font>

说明: **返回一个新的 promise, 只有所有的 promise 都成功才成功, 只要有一个失败了就直接失败**

##### 1、Promise对象全为成功

![1650598465918](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650598465918.png)

![1650598480147](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650598480147.png)

##### 2、Promise对象有一个为失败

![1650602509809](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650602509809.png)

![1650602474916](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650602474916.png)

#### 7、Promise.race 方法: (promises) => {}

- <font color='hotpink'>promises: 包含 n 个 promise 的数组</font>

说明: 返回一个新的 promise, <font color='red'>第一个完成的 promise 的结果状态就是最终的结果状态</font>

![1650602749222](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650602749222.png)

![1650602759372](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650602759372.png)

![1650543318267](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650543318267.png)

![1650543334796](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650543334796.png)

![1650543352006](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650543352006.png)

### promise 的几个关键问题

#### 如何改变 promise 的状态?

> 1. <font color='red'>resolve(value): 如果当前是 pending 就会变为 resolved</font>
> 2. <font color='red'>reject(reason): 如果当前是 pending 就会变为 rejected</font>
> 3. <font color='red'>抛出异常: 如果当前是 pending 就会变为 rejected</font>

#### 一个 promise 指定多个成功/失败回调函数, 都会调用吗?

<font color='red'>当 promise 改变为对应状态时都会调用</font>

#### 改变 promise 状态和指定回调函数谁先谁后?

1. **<font color='hotpink'>都有可能, 正常情况下是先指定回调再改变状态, 但也可以先改状态再指定回调</font>**

2. ##### 如何先改状态再指定回调?

   ① 在执行器中直接调用 resolve()/reject()

   ② 延迟更长时间才调用 then()

3. #### 什么时候才能得到数据?

   ① **如果先指定的回调, 那当状态发生改变时, 回调函数就会调用, 得到数据**

   ②<font color='red'> 如果先改变的状态, 那当指定回调时, 回调函数就会调用, 得到数据</font>

#### promise.then()返回的新 promise 的结果状态由什么决定?

<font color='hotpink'>**简单表达: 由 then()指定的回调函数执行的结果决定**</font>

详细表达:

> ① 如果抛出异常, 新 promise 变为 rejected, reason 为抛出的异常
>
> ![1650603788336](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650603788336.png)
>
> ![1650603796233](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650603796233.png)
>
> ② 如果返回的是非promise的任意值, 新promise变为resolved, value为返回的值
>
> ![1650603891559](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650603891559.png)
>
> ![1650603897818](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650603897818.png)
>
> ③ 如果返回的是另一个新promise, 此promise的结果就会成为新promise的结果
>
> ![1650604030240](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650604030240.png)
>
> ![1650604037799](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650604037799.png)

#### promise 如何串连多个操作任务?

> - <font color='hotpink'>promise 的 then()返回一个新的 promise, 可以开成 then()的链式调用</font>
>
> - **通过 then 的链式调用串连多个同步/异步任务**
>
>   ![1650604336778](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650604336778.png)

#### promise 异常传透?

> - **当使用 promise 的 then 链式调用时, 可以在最后指定失败的回调**
>
>   ![1650604448696](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650604448696.png)
>
> - **前面任何操作出了异常, 都会传到最后失败的回调中处理**

#### 中断 promise 链?

> 1. **<font color='hotpink'>当使用 promise 的 then 链式调用时, 在中间中断, 不再调用后面的回调函数</font>**
>
> 2. 办法: <font color='hotpink'>在回调函数中返回一个 pendding 状态的 promise 对象</font>
>
>    ![1650604749745](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650604749745.png)

## 四、自定义( 手写)Promise

### 1、定义整体结构

![1650543668352](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650543668352.png)

![1650543674935](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650543674935.png)

![1650543691078](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650543691078.png)

![1650543697318](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650543697318.png)

### 2、Promise 构造函数的实现

![1650543719825](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650543719825.png)

![1650543736506](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650543736506.png)

![1650543742700](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650543742700.png)

### 3、promise.then()/catch()

![1650543765842](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650543765842.png)

![1650543785562](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650543785562.png)

![1650543792290](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650543792290.png)

### 4、Promise.resolve()/reject()

![1650543813674](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650543813674.png)

### 5、Promise.all/race() 的实现

![1650543838700](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650543838700.png)

![1650543854656](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650543854656.png)

### 6、Promise.resolveDelay()/rejectDelay()

![1650543868933](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650543868933.png)

![1650543883287](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650543883287.png)

### 完整代码：

![1650616666531](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650616666531.png)

#### 调用案例：

![1650613022016](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650613022016.png)

### resolve函数封装

![1650613668314](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650613668314.png)

![1650613638665](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650613638665.png)

### reject函数封装

![1650613952450](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650613952450.png)

![1650613929592](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650613929592.png)

### all方法的封装

![1650614835132](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650614835132.png)

![1650614861034](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650614861034.png)

### 封装race方法

![1650615574011](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650615574011.png)

![1650615548863](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650615548863.png)

### 回调函数异步执行

![1650616469282](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650616469282.png)

**给需要异步执行的函数添加定时器**

![1650616584356](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650616584356.png)

## 将自定义Promise封装为class

![1650617445416](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650617445416.png)

## 五、async 与 await

### 1、async函数

1. <font color='red'>函数的返回值为 promise 对象</font>
2. <font color='hotpink'>promise 对象的结果由 async 函数执行的返回值决定</font>

![1650676575270](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650676575270.png)

### 2、await 表达式

1. <font color='red'>await 右侧的表达式一般为 promise 对象, 但也可以是其它的值</font>

2. 如果表达式是 promise 对象, await 返回的是 promise 成功的值
3. 如果表达式是其它值, 直接将此值作为 await 的返回值

### 注意

1. <font color='red'>await 必须写在 async 函数中, 但 async 函数中可以没有 await</font>

2. **如果 await 的 promise 失败了, 就会抛出异常, 需要通过 try...catch 捕获处理**

   > ![1650677121798](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650677121798.png)

![1650544044240](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650544044240.png)

![1650544056026](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650544056026.png)

#### async和await结合读取文件

##### 读取文件普通方法：

![1650677493675](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650677493675.png)

##### async和await结合的方法：

![1650677836949](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650677836949.png)

#### async和await结合发送Ajax请求

![1650678310891](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650678310891.png)

