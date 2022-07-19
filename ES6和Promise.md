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
> 2) 块儿级作用域
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
> 5) 块儿级作用域

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

# Promise深入 + 自定义Promise

## 1. 准备

### 1.1. 函数对象与实例对象

> 1. 函数对象: 将函数作为对象使用时, 简称为函数对象
> 2. 实例对象: new 函数产生的对象, 简称为对象

### 1.2. 回调函数的分类

> 1. 同步回调: 
>     理解: 立即执行, 完全执行完了才结束, 不会放入回调队列中
>     例子: 数组遍历相关的回调函数 / Promise的excutor函数
> 2. 异步回调: 
>     理解: 不会立即执行, 会放入回调队列中将来执行
>     例子: 定时器回调 / ajax回调 / Promise的成功|失败的回调

### 1.3. JS中的Error

> 1. 错误的类型
>     Error: 所有错误的父类型
>     ReferenceError: 引用的变量不存在
>     TypeError: 数据类型不正确的错误
>     RangeError: 数据值不在其所允许的范围内
>     SyntaxError: 语法错误
> 2. 错误处理
>     捕获错误: try ... catch
>     抛出错误: throw error
> 3. 错误对象
>     message属性: 错误相关信息
>     stack属性: 函数调用栈记录信息

## 2. Promise的理解和使用

### 2.1. Promise是什么?

> 1.抽象表达: 
>     Promise是JS中进行异步编程的新的解决方案(旧的是谁?)
> 2.具体表达:
>     从语法上来说: Promise是一个构造函数
>     从功能上来说: promise对象用来封装一个异步操作并可以获取其结果
> 3. promise的状态改变(只有2种, 只能改变一次)
>     pending变为resolved
>     pending变为rejected
> 4. promise的基本流程

![promise基本流程](http://vipkshttp1.wiz.cn/ks/share/resources/49c30824-dcdf-4bd0-af2a-708f490b44a1/92b8cbfb-a474-4859-943b-6048e9dc66f6/index_files/9b2b980e2959c4f996cafddb03fa5d4d.png)

### 2.2. 为什么要用Promise?

> 1. 指定回调函数的方式更加灵活: 可以在请求发出甚至结束后指定回调函数
> 2. 支持链式调用, 可以解决回调地狱问题

### 2.3. 如何使用Promise?

> 1. 主要API
>     Promise构造函数: Promise (excutor) {}
>     Promise.prototype.then方法: (onResolved, onRejected) => {}
>     Promise.prototype.catch方法: (onRejected) => {}
>     Promise.resolve方法: (value) => {}
>     Promise.reject方法: (reason) => {}
>     Promise.all方法: (promises) => {}
>     Promise.race方法: (promises) => {}
> 2. 几个重要问题
>     如何改变promise的状态?
>     一个promise指定多个成功/失败回调函数, 都会调用吗?
>     promise.then()返回的新promise的结果状态由什么决定?
>     改变promise状态和指定回调函数谁先谁后?
>     promise如何串连多个操作任务?
>     promise异常传(穿)透?
>     中断promise链

## 3. 自定义Promise

> 1. 定义整体结构
> 2. Promise构造函数的实现
> 3. promise.then()/catch()的实现
> 4. Promise.resolve()/reject()的实现
> 5. Promise.all/race()的实现
> 6. Promise.resolveDelay()/rejectDelay()的实现
> 7. ES6 class版本

## 4. async与await

> 1. async 函数
>     函数的返回值为promise对象
>     promise对象的结果由async函数执行的返回值决定
>    
> 2. await 表达式
>     await右侧的表达式一般为promise对象, 但也可以是其它的值
>     如果表达式是promise对象, await返回的是promise成功的值
>     如果表达式是其它值, 直接将此值作为await的返回值
>
> 3. 注意:
>     await必须写在async函数中, 但async函数中可以没有await
>     如果await的promise失败了, 就会抛出异常, 需要通过try...catch来捕获处理

## 5. JS异步之宏队列与微队列

![宏队列与微队列](http://vipkshttp1.wiz.cn/ks/share/resources/49c30824-dcdf-4bd0-af2a-708f490b44a1/92b8cbfb-a474-4859-943b-6048e9dc66f6/index_files/60b9ff398449db2dcfef9197e2187ae6.png)

> 1. 宏列队: 用来保存待执行的宏任务(回调), 比如: 定时器回调/DOM事件回调/ajax回调
>
> 2. 微列队: 用来保存待执行的微任务(回调), 比如: promise的回调/MutationObserver的回调
>
> 3. JS执行时会区别这2个队列
> 	
> 	- <font color='hotpink'>JS引擎首先必须先执行所有的初始化同步任务代码</font>
> 	
> 	- 每次准备取出第一个宏任务执行前, 都要将所有的微任务一个一个取出来执行

