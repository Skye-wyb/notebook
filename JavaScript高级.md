# JavaScript高级

## 一、面向对象编程

### 两大编程思想

- 面向过程
- 面向对象

#### 1.2 面向过程编程 POP(Process-oriented programming)

<font color='red'>面向过程就是分析出解决问题所需要的步骤，然后用函数把这些步骤一步一步实现，使用的时候再一个一个的依次调用就可以了。</font>

举个栗子：将大象装进冰箱，面向过程做法。

![1650420622447](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650420622447.png)

**面向过程，就是按照我们分析好了的步骤，按照步骤解决问题。**

#### 1.3 面向对象编程 OOP (Object Oriented Programming)

<font color='blue'>面向对象是把事务分解成为一个个对象，然后由对象之间分工与合作。</font>

举个栗子：将大象装进冰箱，面向对象做法。

先找出对象，并写出这些对象的功能：

1. 大象对象 

   进去

2. 冰箱对象

   打开

   关闭

3. 使用大象和冰箱的功能 

<font color='red'>**面向对象是以对象功能来划分问题，而不是步骤。**</font>

<font color='green'>**在面向对象程序开发思想中，每一个对象都是功能中心，具有明确分工。**</font>

面向对象编程具有灵活、代码可复用、容易维护和开发的优点，更适合多人合作的大型软件项目。

#### 面向对象的特性

> 1. 封装性 
> 2. 继承性
> 3. 多态性

![1650420769306](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650420769306.png)

#### 1.4 面向过程和面向对象的对比

![1650443108349](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650443108349.png)

##### <font color='red'>面向过程</font>

- 优点：<font color='green'>性能比面向对象高，适合跟硬件联系很紧密的东西，例如单片机就采用的面向过程编程。</font>
- 缺点：没有面向对象易维护、易复用、易扩展

##### <font color='red'>面向对象</font>

- 优点：<font color='blue'>易维护、易复用、易扩展，由于面向对象有封装、继承、多态性的特性，可以设计出低耦合的系统，使系统 更加灵活、更加易于维护 </font>
- 缺点：性能比面向过程低

**用面向过程的方法写出来的程序是一份蛋炒饭，而用面向对象写出来的程序是一份盖浇饭。**

## 二、ES6 中的类和对象

### 面向对象

面向对象更贴近我们的实际生活, 可以使用面向对象描述现实世界事物.  但是事物分为具体的事物和抽象的事物

1. 抽象的(泛指的)
2. 具体的(特指的)

<font color='red'>**面向对象的思维特点：**</font>

- <font color='blue'>抽取（抽象）对象共用的属性和行为组织(封装)成一个类(模板)</font>
- 对类进行实例化, 获取类的对象

<font color='red'>面向对象编程我们考虑的是有哪些对象，按照面向对象的思维特点,不断的创建对象,使用对象,指挥对象做事情.</font>

### 2.1 对象

现实生活中：万物皆对象，对象是一个具体的事物，看得见摸得着的实物。例如，一本书、一辆汽车、一个人可以是“对象”，一个数据库、一张网页、一个与远程服务器的连接也可以是“对象”。

<font color='red'>在 JavaScript 中，**对象是一组无序的相关属性和方法的集合，所有的事物都是对象，**例如字符串、数值、数组、函数等。</font>

<font color='blue'>对象是由属性和方法组成的：</font>

1. **属性：事物的特征，**在对象中用属性来表示（常用名词）
2. **方法：事物的行为，**在对象中用方法来表示（常用动词）

![1650443213885](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650443213885.png)

**创建对象**

![1650443244468](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650443244468.png)

### 2.2 类 class

在 ES6 中新增加了类的概念，可以<font color='red'>使用 class 关键字声明一个类</font>，之后以这个类来实例化对象。

- <font color='red'>**类抽象了对象的公共部分，它泛指某一大类（class）**</font>
- <font color='blue'>**对象特指某一个，通过类实例化一个具体的对象**   </font>

> 面向对象的思维特点: 
>
> 1. 抽取（抽象）对象共用的属性和行为组织(封装)成一个类(模板)
> 2. 对类进行实例化, 获取类的对象

### 2.3 创建类

**语法：**

![1650421195926](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650421195926.png)

**创建实例：**

![1650421208395](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650421208395.png)

<font color='red'>注意： 类必须使用 new 实例化对象</font>

示例：

![1650443281607](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650443281607.png)

#### 类创建添加属性和方法

![1650443322829](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650443322829.png)

### 2.4 类 constructor 构造函数

<font color='red'>constructor() 方法是类的构造函数(默认方法)，用于传递参数,返回实例对象，</font>通过 new 命令生成对象实例时，自动调用该方法。如果没有显示定义, 类内部会自动给我们创建一个constructor() 

**语法：**

![1650421257607](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650421257607.png)

**创建实例**

![1650421265943](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650421265943.png)

### 2.5 类添加方法

**语法：**

![1650421292643](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650421292643.png)

**创建实例**

![1650421306778](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650421306778.png)

<font color='blue'>**注意： 方法之间不能加逗号分隔，同时方法不需要添加 function 关键字。**</font>

## 三、类的继承

### 3.1 继承

现实中的继承：子承父业，比如我们都继承了父亲的姓。

<font color='red'>程序中的继承：子类可以继承父类的一些属性和方法。</font>

**语法：**

![1650421366236](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650421366236.png)

**实例：**

![1650421376842](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650421376842.png)

### 3.2  super 关键字

<font color='red'>super 关键字用于访问和调用对象父类上的函数。</font>**可以调用父类的构造函数，也可以调用父类的普通函数**

#### 可以调用父类的构造函数

**语法：**

![1650421424143](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650421424143.png)

 <font color='green'>注意: **子类在构造函数中使用super, 必须放到 this 前面  (必须先调用父类的构造方法,在使用子类构造方法)**</font>

**实例：**

![1650421487208](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650421487208.png)

#### 可以调用父类的普通函数

<font color='red'>super关键字 用于访问和调用对象父类上的函数。</font>可以调用父类的构造函数，也可以调用父类的普通函数。

**语法：**

![1650421565716](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650421565716.png)

> - 继承中,如果实例化子类输出一个方法,先看子类有没有这个方法,如果有就先执行子类的
>
> - 继承中,如果子类里面没有,就去查找父类有没有这个方法,如果有,就执行父类的这个方法(就近原则)
>
> - 如果子类想要继承父类的方法,同时在自己内部扩展自己的方法,利用super 调用父类的构造函数,super 必须在子类this之前调用

### 注意点：

> 1. <font color='red'>在 ES6 中类没有变量提升，所以必须先定义类，才能通过类实例化对象.</font>
>
>     ![[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-3FlROLe6-1595300861823)(images/img2.png)]](https://img-blog.csdnimg.cn/20200721111652882.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1NhdGFuX0Rldmls,size_16,color_FFFFFF,t_70#pic_center) 
>
> 2. 类里面的共有属性和方法一定要加this使用.
>
> 3. 类里面的this指向问题. 
>
> 4. <font color='blue'>constructor 里面的this指向实例对象, 方法里面的this 指向这个方法的调用者</font>

##### this指向

> 1. **constructor中的this指向的是new出来的实例对象**
> 2. <font color='red'>自定义的方法,一般也指向的new出来的实例对象</font>
> 3. <font color='red'>绑定事件之后this指向的就是触发事件的事件源</font>

![1650443656029](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650443656029.png)

### 实例：

#### 面向对象版 tab 栏切换

> 功能需求:
>
> 1. 点击 tab栏,可以切换效果.
> 2. 点击 + 号, 可以添加 tab 项和内容项.
> 3. 点击 x 号, 可以删除当前的tab项和内容项.
> 4. 双击tab项文字或者内容项文字,可以修改里面的文字内容.

> 抽象对象:  Tab 对象 
>
> - 该对象具有切换功能
> - 该对象具有添加功能
> - 该对象具有删除功能
> - 该对象具有修改功能

#### 切换功能

![1650443687240](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650443687240.png)

#### 添加功能

> 1. 点击 + 可以实现添加新的选项卡和内容
> 2. 第一步: 创建新的选项卡li 和 新的 内容 section
> 3. 第二步: 把创建的两个元素追加到对应的父元素中.
> 4. 以前的做法:  动态创建元素 createElement  , 但是元素里面内容较多, 需要innerHTML赋值,在 appendChild 追加到父元素里面.
> 5. 现在高级做法:  <font color='red'> 利用 insertAdjacentHTML() 可以直接把字符串格式元素添加到父元素中</font>
> 6. **appendChild 不支持追加字符串的子元素, insertAdjacentHTML 支持追加字符串的元素**
> 7. <font color='blue'>insertAdjacentHTML(追加的位置,‘要追加的字符串元素’)  </font>
> 8. 追加的位置有: beforeend  插入元素内部的最后一个子节点之后
> 9. 该方法地址:  https://developer.mozilla.org/zh-CN/docs/Web/API/Element/insertAdjacentHTML  

![1650443725121](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650443725121.png)

#### 删除功能

> 1. 点击 × 可以删除当前的li选项卡和当前的section
> 2. X是没有索引号的, 但是它的父亲li 有索引号, 这个索引号正是我们想要的索引号
> 3. 所以核心思路是: 点击 x 号可以删除这个索引号对应的 li 和 section
> 4. 但是,当我们动态删除新的li和索引号时,也需要重新获取 x 这个元素.  需要调用init 方法

![1650443739607](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650443739607.png)

#### 编辑功能

> 1. 双击选项卡li或者 section里面的文字,可以实现修改功能
> 2. 双击事件是:  ondblclick
> 3. 如果双击文字,会默认选定文字,此时需要双击禁止选中文字
> 4. window.getSelection ? window.getSelection().removeAllRanges() : document.selection.empty();
> 5. 核心思路:  双击文字的时候, 在 里面生成一个文本框, 当失去焦点或者按下回车然后把文本框输入的值给原先元素即可.

![1650443763047](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650443763047.png)

##### 代码实现：

HTML代码：

![1650434381492](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650434381492.png)

JS-面向对象代码

![1650434416723](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650434416723.png)

##### insertAdjacentHTML 方法：

<font color='red'>在指定的地方插入html标签语句 </font>

> 参数：
>
> - swhere: 指定插入html标签语句的地方，
>
> - stext:要插入的内容
>
> 有四种值可用：
>
> 1.     beforeBegin: 插入到标签开始前
>
> 2.     afterBegin:插入到标签开始标记之后
>
> 3.     beforeEnd:插入到标签结束标记前
>
> 4.     afterEnd:插入到标签结束标记后

##### insertAdjacentText方法

与 insertAdjacentHTML方法类似，<font color='red'>只不过只能插入纯文本，参数相同</font>

<font color='red'>方法名称：insertHtml(where,el,html)</font>

> 参数介绍：
>
> 1. where：插入位置。包括beforeBegin,beforeEnd,afterBegin,afterEnd。
> 2. el：用于参照插入位置的html元素对象
> 3. html：要插入的html代码

#### 双击事件

<font color='red'>**ondblclick()**</font>

![1650443814505](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650443814505.png)

# 构造函数和原型

## 一、构造函数和原型

### 1、概述

在典型的 OOP 的语言中（如 Java），都存在类的概念，**类就是对象的模板，对象就是类的实例，但在 ES6之前， JS 中并没用引入类的概念。**

<font color='red'>ES6， 全称 ECMAScript 6.0 ，2015.06 发版。但是目前浏览器的 JavaScript 是 ES5 版本，大多数高版本的浏览器也支持 ES6，不过只实现了 ES6 的部分特性和功能。</font>

在 ES6之前 ，对象不是基于类创建的，<font color='blue'>而是用一种称为构建函数的特殊函数来定义对象和它们的特征。</font>

##### 创建对象可以通过以下三种方式：

> 1. <font color='red'>对象字面量</font>
>
> 2. new Object()
>
> 3. 自定义构造函数

![1650443915891](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650443915891.png)

![1650434788323](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650434788323.png)

#### 1.2 构造函数

<font color='red'>**构造函数是一种特殊的函数，主要用来初始化对象，**</font><font color='blue'>即为对象成员变量赋初始值</font>，它总与 new 一起使用。我们可以把对象中一些公共的属性和方法抽取出来，然后封装到这个函数里面。

在 JS 中，使用构造函数时要注意以下两点：

1. <font color='blue'>构造函数用于创建某一类对象，其首字母要大写</font>
2. 构造函数要和 new 一起使用才有意义

##### new 在执行时会做四件事情：

> 1. 在内存中创建一个新的空对象。
> 2. 让 this 指向这个新的对象。
> 3. 执行构造函数里面的代码，给这个新对象添加属性和方法。
> 4. 返回这个新对象（所以构造函数里面不需要 return ）。

<font color='red'>JavaScript 的构造函数中可以添加一些成员，可以在构造函数本身上添加，也可以在构造函数内部的 this 上添加。通过这两种方式添加的成员，就分别称为静态成员和实例成员。</font>

- <font color='blue'>静态成员：在构造函数本身上添加的成员称为静态成员，只能由构造函数本身来访问 </font>

  ![1650443950248](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650443950248.png)

![1650435562642](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650435562642.png)

- <font color='red'>实例成员：在构造函数内部创建的对象成员称为实例成员，只能由实例化的对象来访问</font>

  ![1650443938086](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650443938086.png)

![1650435638735](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650435638735.png)

#### 1.3 构造函数的问题

构造函数方法很好用，<font color='red'>但是存在浪费内存的问题。</font>

![1650435695768](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650435695768.png)

![1650435710973](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650435710973.png)

<font color='red'>我们希望所有的对象使用同一个函数，这样就比较节省内存，那么我们要怎样做呢？</font>

#### 1.4 构造函数原型 prototype

<font color='red'>**构造函数通过原型分配的函数是所有对象所共享的。**</font>

<font color='orange'>**每一个构造函数都会有一个原型对象**</font>

<font color='blue'>JavaScript 规定，每一个构造函数都有一个 prototype 属性，指向另一个对象。</font>**注意这个 prototype 就是一个对象，这个对象的所有属性和方法，都会被构造函数所拥有。**

我们<font color='green'>**可以把那些不变的方法，直接定义在 prototype 对象上，这样所有对象的实例就可以共享这些方法。**</font>

![1650435997239](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650435997239.png)

> 问答？
>
> 1. <font color='red'>原型是什么 ？ </font>
>    - <font color='red'>一个对象，我们也称为 prototype 为原型对象。</font>
>
> 2. <font color='blue'>原型的作用是什么 ？ </font>
>    - <font color='blue'>共享方法。</font>

**一般情况下，公共属性定义到构造函数里面，公共的方法放到原型对象（prototype）上**

#### 1.5 对象原型  `__proto__`

<font color='red'>对象都会有一个属性 `__proto__` 指向构造函数的 prototype 原型对象，</font>**之所以我们对象可以使用构造函数 prototype 原型对象的属性和方法，就是因为对象有 `__proto__ `原型的存在。**

- `__proto__`对象原型和原型对象 prototype 是等价的
- `__proto__`对象原型的意义就在于为对象的查找机制提供一个方向，或者说一条路线，但是它是一个非标准属性，**因此实际开发中，不可以使用这个属性，它只是内部指向原型对象 prototype**

![1650436881856](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650436881856.png)

#### 1.6 constructor  构造函数

<font color='red'>对象原型（ __proto__）和**构造函数（prototype）原型对象**里面都有一个属性 constructor 属性 ，constructor 我们称为构造函数，因为**它指回构造函数本身**。</font>

<font color='blue'>constructor 主要用于记录该对象引用于哪个构造函数，它可以让原型对象重新指向原来的构造函数。</font>

一般情况下，对象的方法都在构造函数的原型对象中设置。如果有多个对象的方法，我们可以给原型对象采取对象形式赋值，但是这样就会覆盖构造函数原型对象原来的内容，这样修改后的原型对象 constructor  就不再指向当前构造函数了。此时，我们可以在修改后的原型对象中，添加一个 constructor 指向原来的构造函数。

![1650444026903](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650444026903.png)

![1650437033106](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650437033106.png)

![1650437046676](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650437046676.png)

**这种方式给原型对象添加方法不会改变原型对象，其上依然存在constructor构造函数**

![1650437395452](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650437395452.png)

**这种方式是赋值给原型对象，会覆盖到之前的内容，则constructor被覆盖了需要重新定义**

![1650437589412](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650437589412.png)

![1650437607594](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650437607594.png)

<font color='red'>constructor指回原来的构造函数</font>

![1650437670828](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650437670828.png)

![1650437728032](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650437728032.png)

##### 总结：

<font color='red'>**如果我们修改了原型对象且以对象的形式复制，则需要让constructor指向原来的构造函数！！！**</font>

#### 1.7 构造函数、实例、原型对象三者之间的关系

![1650437070786](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650437070786.png)

#### <font color='red'>1.8 原型链！！！</font>

**只要是一个对象都会有`__proto__`，无论是实例对象还是原型对象！**

![1650437204121](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650437204121.png)

#### 1.9 JavaScript 的成员查找机制(规则)

1. 当访问一个对象的属性（包括方法）时，首先查找这个对象自身有没有该属性。
2. <font color='red'>如果没有就查找它的原型（也就是 `__proto__`指向的 prototype 原型对象）。</font>
3. <font color='red'>如果还没有就查找原型对象的原型（Object的原型对象）。</font>
4. 依此类推一直找到 Object 为止（null）。
5. <font color='red'>**`__proto__`对象原型的意义就在于为对象成员查找机制提供一个方向，或者说一条路线。**</font>

#### 1.10 原型对象this指向

<font color='red'>**构造函数中的this 指向我们实例对象.**</font>

<font color='purple'>**原型对象里面放的是方法,  这个方法里面的this 指向的是 这个方法的调用者, 也就是这个实例对象.**</font>

#### 1.11 扩展内置对象

可以通过原型对象，对原来的内置对象进行扩展自定义的方法。比如给数组增加自定义求偶数和的功能。

<font color='red'>注意：数组和字符串内置对象不能给原型对象覆盖操作 Array.prototype = {} ，只能是 Array.prototype.xxx = function(){} 的方式。</font>

![1650439778262](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650439778262.png)

## 二、继承

ES6之前并没有给我们提供 extends 继承。<font color='red'>我们可以通过构造函数+原型对象模拟实现继承，被称为组合继承。</font>

### 2.1 call()

<font color='blue'>调用这个函数, 并且修改函数运行时的 this 指向   </font>

![1650439474928](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650439474928.png)

> - thisArg ：<font color='red'>当前调用函数 this 的指向对象</font>
> - arg1，arg2：传递的其他参数

![1650440734319](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650440734319.png)

### 2.2 借用构造函数继承父类型属性

<font color='blue'>核心原理： 通过 call() 把父类型的 this 指向子类型的 this ，这样就可以实现子类型继承父类型的属性。   </font>

![1650439568619](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650439568619.png)

![1650441241500](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650441241500.png)

![1650441251694](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650441251694.png)

### 2.3 借用原型对象继承父类型方法

一般情况下，<font color='red'>对象的方法都在构造函数的原型对象中设置，通过构造函数无法继承父类方法。  </font>

> 核心原理： 
>
> 1. 将子类所共享的方法提取出来，<font color='blue'>**让子类的 prototype 原型对象 = new 父类()**  </font>
> 2. 本质：<font color='red'>子类原型对象等于是实例化父类</font>，**因为父类实例化之后另外开辟空间，就不会影响原来父类原型对象**
> 3. <font color='red'>将子类的 constructor 从新指向子类的构造函数</font>：**这里相当于利用了对象的形式修改了原型对象，需要利用constructor指回原来的构造函数**

![1650442807433](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650442807433.png)

![1650442741870](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650442741870.png)

#### 注意：

此处采用的是子类.prototype = new 父类()，而不采用子类.prototype = 父类.prototype的原因：

<font color='red'>采用**子类.prototype = 父类.prototype**会导致改变父构造函数的原型对象！！！</font>这里相当于子构造函数指向了父构造函数，引用的是地址，其中一个改变会导致另一个也改变！！！

![1650441859939](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650441859939.png)

**问题所在：父构造函数中出现了子构造函数中专门的方法！**

![1650441900536](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650441900536.png)

## 类的本质

> 1. <font color='red'>class本质还是function.</font>
>
> 2. <font color='red'>**类的所有方法都定义在类的prototype属性上**</font>
>
> 3. 类创建的实例,里面也有`__proto__`指向类的prototype原型对象
>
> 4. **所以ES6的类它的绝大部分功能，ES5都可以做到，新的class写法只是让对象原型的写法更加清晰、更像面向对象编程的语法而已。**
>
> 5. 所以ES6的类其实就是语法糖.
>
> 6. 语法糖：语法糖就是一种便捷写法。简单理解, 有两种方法可以实现同样的功能, 但是一种写法更加清晰、方便,那么这个方法就是语法糖

## 三、ES5 中的新增方法

### 3.1 ES5 新增方法概述

> ES5 中给我们新增了一些方法，可以很方便的操作数组或者字符串，这些方法主要包括：
>
> 1. 数组方法
> 2. 字符串方法
> 3. 对象方法

### 3.2 数组方法

<font color='red'>迭代(遍历)方法：forEach()、map()、filter()、some()、every()；</font>

#### forEach()

![1650442960294](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650442960294.png)

> - currentValue：数组当前项的值
> - index：数组当前项的索引
> - arr：数组对象本身

**forEach没有返回值，为undefined**

![1650444094982](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650444094982.png)

#### map()

>  <font color='red'>map() 方法创建一个新数组，其结果是该数组中的每个元素都调用一个提供的函数后返回的结果。 </font>
>
> ![1650457309986](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650457309986.png)
>
> ![1650457338657](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650457338657.png)
>
> 

<font color='red'> map()方法创建了一个新数组，但新数组并不是在遍历完array1后才被赋值的，而是每遍历一次就得到一个值 </font>

#### filter()

![1650444138132](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650444138132.png)

> - <font color='red'>filter() 方法创建一个新的数组，新数组中的元素是通过检查指定数组中符合条件的所有元素,主要用于筛选数组</font>
> - <font color='blue'>注意它直接返回一个新数组</font>
> - currentValue: 数组当前项的值
>
> - index：数组当前项的索引
>
> - arr：数组对象本身

![1650444195647](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650444195647.png)

#### some()

![1650444212246](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650444212246.png)

> - <font color='red'>some() 方法用于检测数组中的元素是否满足指定条件.   通俗点 查找数组中是否有满足条件的元素 </font>
> - <font color='red'>注意它返回值是布尔值</font>, 如果查找到这个元素, 就返回true ,  如果查找不到就返回false.
> - <font color='blue'>**如果找到第一个满足条件的元素，则终止循环，不再继续查找。**</font>
> - currentValue: 数组当前项的值
> - index：数组当前项的索引
> - arr：数组对象本身

![1650444289573](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650444289573.png)

#### 查询商品案例

1. 把数据渲染到页面中 (forEach)
2. 根据价格显示数据 
3. 根据商品名称显示数据

##### 思路步骤：

![1650446305831](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650446305831.png)

![1650446318175](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650446318175.png)

##### 完整代码：

![1650446408127](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650446408127.png)

#### some和forEach的区别

- <font color='red'>如果查询数组中唯一的元素, 用some方法更合适,在some 里面 遇到 return true 就是终止遍历 迭代效率更高</font>
- 在forEach 里面 return 不会终止迭代
- filter也不会终止迭代

![1650446652136](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650446652136.png)

### 3.3 字符串方法

#### trim()

<font color='red'>trim()  方法会从一个字符串的两端删除空白字符。</font>

![1650446698328](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650446698328.png)

**trim() 方法并不影响原字符串本身，它返回的是一个新的字符串。**

![1650446749013](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650446749013.png)

### 3.4 对象方法

#### Object.keys()

1. <font color='blue'>**Object.keys() 用于获取对象自身所有的属性**</font>

![1650446789658](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650446789658.png)

- 效果类似 for…in
- <font color='red'>返回一个由属性名组成的**数组**</font>

![1650446815731](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650446815731.png)

![1650446961449](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650446961449.png)

#### Object.defineProperty() 

2. <font color='red'>Object.defineProperty() 定义对象中新属性或修改原有的属性。(了解)</font>

![1650446998579](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650446998579.png)

> - **obj：必需。目标对象** 
> - <font color='red'>prop：必需。需定义或修改的属性的名字</font>
> - <font color='red'>descriptor：必需。目标属性所拥有的特性</font>

 **Object.defineProperty()   <font color='red'>第三个参数 descriptor 说明： 以对象形式 { } 书写</font>** 

1. **value: 设置属性的值  默认为undefined**
2. writable: 值是否可以重写。true | false  默认为false

3. enumerable: 目标属性是否可以被枚举。true | false 默认为 false

4. configurable: 目标属性是否可以被删除或是否可以再次修改特性 true | false  默认为false

![1650447118379](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650447118379.png)

![1650447393668](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650447393668.png)

![1650447401709](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650447401709.png)

![1650447507617](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650447507617.png)

![1650447565646](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650447565646.png)

## 函数进阶

## 一、函数的定义和调用

### 1.1 函数的定义方式

1. <font color='red'>函数声明方式 function 关键字 (命名函数)</font>

2. <font color='blue'>函数表达式 (匿名函数)</font>

3. <font color='green'>new Function() </font>  

![1650447725789](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650447725789.png)

![1650447752945](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650447752945.png)

![1650447762829](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650447762829.png)

- <font color='red'>Function 里面参数都必须是字符串格式</font>
- 第三种方式执行效率低，也不方便书写，因此较少使用
- <font color='red'>所有函数都是 Function 的实例(对象)  </font>
- **函数也属于对象**

![1650447809959](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650447809959.png)

### 1.2 函数的调用方式

1. 普通函数

2. 对象的方法

3. **构造函数**

4. 绑定事件函数

5. 定时器函数

6. **立即执行函数**

![1650447875247](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650447875247.png)

## 二、This

### 2.1 函数内 this 的指向

这些 this 的指向，是当我们调用函数的时候确定的。 <font color='red'>调用方式的不同决定了this 的指向不同，一般指向我们的调用者。</font>

![1650447947106](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650447947106.png)

![1650448069459](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650448069459.png)

### 2.2 改变函数内部 this 指向

<font color='blue'>JavaScript 为我们专门提供了一些函数方法来帮我们更优雅的**处理函数内部 this 的指向问题，常用的有 bind()、call()、apply() 三种方法。**</font>

#### 1. call 方法

<font color='red'>**call() 方法调用一个对象。**简单理解为调用函数的方式，但是它可以改变函数的 this 指向。</font>

![1650448141970](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650448141970.png)

> - <font color='blue'>thisArg：在 fun 函数运行时指定的 this 值</font>
> - arg1，arg2：传递的其他参数
> - **返回值就是函数的返回值，因为它就是调用函数**
> - 因此当我们想改变 this 指向，同时想调用这个函数的时候，可以使用 call，比如继承

![1650448249309](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650448249309.png)

#### 2. apply 方法

<font color='blue'>**apply() 方法调用一个函数。**简单理解为调用函数的方式，但是它可以改变函数的 this 指向。</font>

![1650448272010](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650448272010.png)

> - <font color='red'>thisArg：在fun函数运行时指定的 this 值</font>
> - <font color='blue'>argsArray：传递的值，必须包含在数组里面</font>
> - 返回值就是函数的返回值，因为它就是调用函数
>
> - 因此 <font color='blue'>apply 主要跟数组有关系，比如使用 Math.max() 求数组的最大值</font>

![1650448322603](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650448322603.png)

#### 3. bind 方法

<font color='blue'>**bind() 方法不会调用函数。**但是能改变函数内部this 指向 </font>

![1650448382441](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650448382441.png)

> - <font color='orange'>thisArg：在 fun 函数运行时指定的 this 值</font>
> - arg1，arg2：传递的其他参数
> - <font color='red'>返回由指定的 this 值和初始化参数改造的原函数拷贝</font>
> - **因此当我们只是想改变 this 指向，并且不想调用这个函数的时候，可以使用 bind**

![1650448531204](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650448531204.png)

### 2.3 call  apply  bind 总结

<font color='red'>**相同点：**</font>

- 都可以改变函数内部的this指向.

<font color='red'>**区别点：**</font>

- **call 和 apply  会调用函数, 并且改变函数内部this指向.**
- <font color='blue'>call 和 apply 传递的参数不一样, call 传递参数 aru1, aru2..形式  apply 必须数组形式[arg]</font>
- **bind  不会调用函数, 可以改变函数内部this指向.**

<font color='red'>**主要应用场景：**</font>

- **call 经常做继承.** 
- **apply 经常跟数组有关系.  比如借助于数学对象实现数组最大值最小值**
- **bind  不调用函数，但是还想改变this指向。比如改变定时器内部的this指向。** 

## 三、严格模式

### 3.1 什么是严格模式

JavaScript 除了提供正常模式外，还提供了<font color='red'>严格模式（strict mode）。ES5 的严格模式是采用具有限制性JavaScript 变体的一种方式，即在严格的条件下运行 JS 代码。</font>

严格模式在 IE10 以上版本的浏览器中才会被支持，旧版本浏览器中会被忽略。

严格模式对正常的 JavaScript 语义做了一些更改： 

1. 消除了 Javascript 语法的一些不合理、不严谨之处，减少了一些怪异行为。
2. 消除代码运行的一些不安全之处，保证代码运行的安全。
3. **提高编译器效率，增加运行速度。**
4. 禁用了在 ECMAScript 的未来版本中可能会定义的一些语法，为未来新版本的 Javascript 做好铺垫。比如一些保留字如：class, enum, export, extends, import, super 不能做变量名

### 3.2 开启严格模式

**严格模式可以应用到<font color='red'>整个脚本或个别函数</font>中。因此在使用时，我们可以将严格模式分为<font color='blue'>为脚本开启严格模式</font>和<font color='green'>为函数开启严格模式</font>两种情况。**

#### 1. 为脚本开启严格模式

为整个脚本文件开启严格模式，需要<font color='red'>在所有语句之前放一个特定语句“use strict”;（或‘use strict’;）。</font>

![1650449278148](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650449278148.png)

因为"use strict"加了引号，所以老版本的浏览器会把它当作一行普通字符串而忽略。

有的 script 基本是严格模式，有的 script 脚本是正常模式，这样不利于文件合并，<font color='red'>所以可以将整个脚本文件放在一个立即执行的匿名函数之中。这样独立创建一个作用域而不影响其他 script 脚本文件。</font>

![1650452779077](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650452779077.png)

![1650453076746](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650453076746.png)

#### 2. 为函数开启严格模式

要给某个函数开启严格模式，需要<font color='red'>把“use strict”;  (或 'use strict'; ) 声明放在函数体所有语句之前。</font>

![1650452821919](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650452821919.png)

**将 "use strict" 放在函数体的第一行，则整个函数以 "严格模式" 运行。**

![1650453088399](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650453088399.png)

### 3.4 严格模式中的变化

严格模式对 Javascript 的语法和行为，都做了一些改变。

#### <font color='red'>1. 变量规定</font>

1. <font color='blue'>在正常模式中，如果一个变量没有声明就赋值，默认是全局变量。</font><font color='red'>严格模式禁止这种用法，**变量都必须先用var 命令声明，然后再使用。**</font>
2. 严禁删除已经声明变量。例如，delete x; 语法是错误的。

#### 2. 严格模式下 this 指向问题

> 1. 以前在全局作用域函数中的 this 指向 window 对象。
> 2. <font color='red'>严格模式下全局作用域中函数中的 this 是 undefined。</font>
> 3. 以前构造函数时不加 new也可以 调用,当普通函数，this 指向全局对象
> 4. <font color='red'>严格模式下,如果 构造函数不加new调用, this 指向的是undefined 如果给他赋值则 会报错</font>
> 5. <font color='blue'>new 实例化的构造函数指向创建的对象实例。</font>
> 6. <font color='blue'>定时器 this 还是指向 window 。</font>
> 7. <font color='green'>事件、对象还是指向调用者。</font>

#### 3. 函数变化

> 1. <font color='red'>函数不能有重名的参数。</font>
> 2. <font color='blue'>**函数必须声明在顶层。**</font>新版本的 JavaScript 会引入“块级作用域”（ ES6 中已引入）。为了与新版本接轨，不允许在非函数的代码块内声明函数。 

更多严格模式要求参考：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Strict_mode

![1650453119320](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650453119320.png)

## 四、高阶函数

<font color='red'>**高阶函数是对其他函数进行操作的函数，**它**接收函数作为参数或将函数作为返回值输出**。</font>

![1650453230451](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650453230451.png)

此时**fn 就是一个高阶函数**

**函数也是一种数据类型，同样可以作为参数，传递给另外一个参数使用。 最典型的就是作为回调函数。**

<font color='blue'>同理函数也可以作为返回值传递回来</font>

![1650453281587](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650453281587.png)

## 五、闭包

### 5.1 变量作用域

变量根据作用域的不同分为两种：<font color='red'>全局变量和局部变量。</font>

1. <font color='red'>函数内部可以使用全局变量。</font>

2. <font color='blue'>函数外部不可以使用局部变量。</font>

3. 当函数执行完毕，**本作用域内的局部变量会销毁。**

### 5.2 什么是闭包

<font color='red'>**闭包（closure）指有权访问另一个函数作用域中变量的函数。** </font> -----  JavaScript 高级程序设计

简单理解就是 ，<font color='blue'>**一个作用域可以访问另外一个函数内部的局部变量。** </font>

<font color='red'>**被访问的全局变量所在的函数就是闭包函数。**</font>

> <font color='hotpink'> **所谓闭包，简单来说就是函数内部的某个值被保存到函数外部。通常用return直接保存。** </font>
>
> ![1650714699438](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650714699438.png)
>
> **存在问题：输出全为10**
>
> 因为存在闭包，采用立即执行函数可以解决
>
> ![1650714881274](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650714881274.png)

![1650453372971](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650453372971.png)

![1650453421490](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650453421490.png)

#### 闭包的理解：

**<font color='hotpink'>JavaScript语言的特别之处：函数内部可以直接读取全局变量，但是在函数外部无法读取函数内部的局部变量</font>**

**<font color='red'>闭包就是能够读取其他函数内部变量的函数。</font>**

**在JavaScript中，只有函数内部的子函数才能读取局部变量，所以闭包可以简单地理解为：定义在一个函数内部的函数，在本质上，闭包是将函数内部和函数外部连接起来的桥梁。**

<font color='blue'>有时需要获取函数内部的局部变量，可以在函数内部再定义一个函数</font>

<font color='blue'>能够读取其他函数内部变量的函数：</font>

![1650718427705](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650718427705.png)

**这种方式也可以获取到局部变量a**

![1650719424225](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650719424225.png)

由于在JavaScript中，只有函数内部的子函数才能读取局部变量，所以说：<font color='hotpink'>**闭包可以简单理解为：“定义在一个函数内部的函数”**</font>

### 闭包的规范写法：

![1650719720433](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650719720433.png)

**简写形式：返回匿名函数**

![1650720887039](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650720887039.png)

这里相当于把局部变量赋给了全局变量f，这样局部变量变为全局变量就不会被回收了，下次使用的时候还是上一次的值。

<font color='red'>**返回的是一个函数，并且这个函数对于局部变量存在引用，这就形成了闭包。**</font>

**<font color='hotpink'>闭包的好处：既可以长久的保存变量又不会造成全局污染</font>**

##### 总结：

<font color='hotpink'>为什么需要闭包：局部变量无法共享和长久的保存，而全局变量可能造成变量污染，所以希望有一种机制既可以长久的保存变量又不会造成全局污染。</font>

#### 另一种解释

![1650715960640](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650715960640.png)

这里没有只是声明了函数但未执行函数，在全局执行上下文（环境）中没有声明book变量，所以会报错。

![1650716280518](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650716280518.png)

![1650716479172](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650716479172.png)

##### 经典面试题：

![1650716820710](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650716820710.png)

setTimeout会放到任务队列

**立即执行函数可解决问题：**

![1650717081088](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650717081088.png)

![1650717172931](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650717172931.png)

##### 阿里经典面试题：

![1652326389538](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1652326389538.png)

输出：1，4

##### 闭包封装原生XMLHttpRequest

![1650763002920](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650763002920.png)

Http()函数中才是真正的用到了闭包：则返回的request函数是一个闭包

### 5.3 在 chrome 中调试闭包

1. 打开浏览器，按 F12 键启动 chrome 调试工具。

2. 设置断点。

3. 找到<font color='red'> Scope 选项（Scope 作用域的意思）。</font>

4. 当我们重新刷新页面，会进入断点调试，Scope 里面会有两个参数（global 全局作用域、local 局部作用域）。

5. **当执行到 fn2() 时，Scope 里面会多一个 Closure 参数 ，这就表明产生了闭包。**

### 5.4 闭包的作用

**提问：我们怎么能在 fn() 函数外面访问 fn() 中的局部变量 num 呢 ？**

![1650453518333](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650453518333.png)

<font color='red'>**闭包作用：延伸变量的作用范围。**</font>

![1650453571768](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650453571768.png)

### 5.5 闭包案例

1、循环注册点击事件。

闭包应用-点击li输出当前li的索引号

![1650454428694](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650454428694.png)

2、循环中的 setTimeout()。

![1650454703104](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650454703104.png)

3、计算打车价格。

![1650455097714](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650455097714.png)

![1650455107224](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650455107224.png)

![1650460024525](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650460024525.png)

### 5.6 闭包总结

<font color='red'>1、闭包是什么？    </font>

- <font color='blue'>闭包是一个函数 （一个作用域可以访问另外一个函数的局部变量）</font>

<font color='red'>2、闭包的作用是什么？ </font>

- <font color='blue'>延伸变量的作用范围</font>

## 六、递归

### 6.1 什么是递归？

<font color='red'>如果一个函数在内部可以调用其本身，那么这个函数就是递归函数。</font>

**简单理解：函数内部自己调用自己, 这个函数就是递归函数**

递归函数的作用和循环效果一样

**由于递归很容易发生“栈溢出”错误（stack overflow），所以必须要<font color='red'>加退出条件 return。</font>**

![1650460305452](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650460305452.png)

### 6.2 利用递归求数学题

1. 求 1 * 2 *3 ... * n   阶乘。

2. 求斐波那契数列 。

3. 根据id返回对应的数据对象

#### 求 1 * 2 *3 ... * n   阶乘。

![1650460362307](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650460362307.png)

#### 求斐波那契数列

![1650460474507](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650460474507.png)

#### 根据id返回对应的数据对象

![1650460538339](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650460538339.png)

### 6.3 浅拷贝和深拷贝

> 1. 浅拷贝只是拷贝一层, <font color='red'>更深层次对象级别的只拷贝引用.</font>
> 2. <font color='red'>深拷贝拷贝多层, 每一级别的数据都会拷贝.</font>
> 3. <font color='blue'>Object.assign(target, ...sources)    es6 新增方法可以浅拷贝</font>

![1650460640022](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650460640022.png)

![1650460756924](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650460756924.png)

![1650460821862](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650460821862.png)

# 正则表达式

## 一、正则表达式概述

### 1.1 什么是正则表达式

<font color='red'>正则表达式（ Regular Expression ）是用于匹配字符串中字符组合的模式。在 JavaScript中，正则表达式也是对象。</font>

**正则表通常被用来检索、替换那些符合某个模式（规则）的文本，**例如验证表单：用户名表单只能输入英文字母、数字或者下划线， 昵称输入框中可以输入中文(匹配)。此外，正则表达式还常用于过滤掉页面内容中的一些敏感词(替换)，或从字符串中获取我们想要的特定部分(提取)等 。

其他语言也会使用正则表达式，本阶段我们主要是**利用 JavaScript 正则表达式完成表单验证。**

### 1.2 正则表达式的特点

> 1. <font color='red'>灵活性、逻辑性和功能性非常的强。</font>
>
> 2. **可以迅速地用极简单的方式达到字符串的复杂控制。**
>
> 3. 对于刚接触的人来说，比较晦涩难懂。比如： ^\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*$
>
> 4. 实际开发,一般都是直接复制写好的正则表达式. 但是要求会使用正则表达式并且根据实际情况修改正则表达式.   比如用户名:    /^[a-z0-9_-]{3,16}$/

## 二、正则表达式在 JavaScript 中的使用

### 2.1 创建正则表达式

<font color='red'>在 JavaScript 中，可以通过两种方式创建一个正则表达式。</font>

#### 1. 通过<font color='red'>调用 RegExp 对象</font>的构造函数创建

![1650461131029](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650461131029.png)

#### 2. 通过字面量创建

![1650461142877](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650461142877.png)

**// 注释中间放表达式就是正则字面量**

![1650461202228](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650461202228.png)

### 2.2 测试正则表达式 test

<font color='red'>**test() 正则对象方法**，**用于检测字符串是否符合该规则**，该对象会返回 true 或 false，其参数是测试字符串。</font>

![1650461226173](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650461226173.png)

> 1. <font color='red'>regexObj 是写的正则表达式</font>
> 2. str 我们要测试的文本
> 3. **就是检测str文本是否符合我们写的正则表达式规范.**

![1650461284366](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650461284366.png)



### 2.3 match()方法

> match()方法用于检索字符串，以找到一个或多个与正则表达式匹配的文本。
>
> <font color='red'>stringObj.match(regExp) </font>

## 三、正则表达式中的特殊字符

### 3.1 正则表达式的组成

<font color='red'>一个正则表达式可以由简单的字符构成，</font>比如 /abc/，<font color='red'>也可以是简单和特殊字符的组合，</font>比如 /ab*c/ 。<font color='blue'>其中特殊字符也被称为元字符，在正则表达式中是具有特殊意义的专用符号，如 ^ 、$ 、+ 等。</font>

> 特殊字符非常多，可以参考： 
>
> 1. MDN：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Regular_Expressions
> 2. jQuery 手册：正则表达式部分
> 3. 正则测试工具: http://tool.oschina.net/regex

### 元字符

#### 3.2 边界符

<font color='red'>正则表达式中的边界符（位置符）用来提示字符所处的位置，主要有两个字符。</font>

![1650461460407](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650461460407.png)

<font color='blue'>如果 ^ 和 $ 在一起，表示必须是精确匹配。</font>

![1650461622868](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650461622868.png)

#### 3.3 字符类

<font color='red'>字符类表示有一系列字符可供选择，**只要匹配其中一个就可以了。** **所有可供选择的字符都放在方括号内。**</font>

##### 1. []  方括号   

![1650461672139](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650461672139.png)

**后面的字符串只要包含 abc 中任意一个字符，都返回 true 。**

![1650461713845](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650461713845.png)

##### 2. [-]  方括号内部 范围符-   

![1650461742140](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650461742140.png)

<font color='blue'>方括号内部加上 - 表示范围，这里表示 a 到 z 26个英文字母都可以。</font>

##### 3. [^]  方括号内部 取反符^   

![1650461773497](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650461773497.png)

<font color='red'>方括号内部加上 ^ 表示取反，只要包含方括号内的字符，都返回 false 。</font>

<font color='blue'>**注意：和边界符 ^ 区别，边界符写到方括号外面。**  </font>

##### 4. 字符组合

![1650461830327](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650461830327.png)

<font color='blue'>方括号内部可以使用字符组合，这里表示包含 a 到 z 的26个英文字母和 1 到 9 的数字都可以。</font>

#### 3.4 量词符

<font color='green'>**量词符用来设定某个模式出现的次数。**</font>

![1650461873645](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650461873645.png)

![1650461928141](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650461928141.png)

### 案例：用户名验证

功能需求:

1. 如果用户名输入合法, 则后面提示信息为 :  用户名合法,并且颜色为绿色
2. 如果用户名输入不合法, 则后面提示信息为:  用户名不符合规范, 并且颜色为绿色

> 分析:
>
> 1. 用户名只能为英文字母,数字,下划线或者短横线组成, 并且用户名长度为 6~16位.
> 2. 首先准备好这种正则表达式模式 /$[a-zA-Z0-9-_]{6,16}^/
> 3. 当表单失去焦点就开始验证. 
> 4. 如果符合正则规范, 则让后面的span标签添加 right 类.
> 5. 如果不符合正则规范, 则让后面的span标签添加 wrong 类.

![1650462113367](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650462113367.png)

### 3.5 括号总结

1. <font color='red'>大括号  量词符.   里面表示重复次数</font>

2. <font color='red'>中括号 字符集合。匹配方括号中的任意字符. </font>

3. <font color='blue'>小括号 表示优先级</font>

   可以在线测试: https://c.runoob.com/

![1650462214168](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650462214168.png)

### 3.6 预定义类

<font color='red'>预定义类指的是某些常见模式的简写方式。</font>

**.**：**匹配除换行符以外的任意一个字符**

![1650462233895](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650462233895.png)

#### 案例

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200814231737531.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1NhdGFuX0Rldmls,size_16,color_FFFFFF,t_70#pic_center) 

#### 实现代码：

## 四、正则表达式中的替换

### 4.1 replace 替换

<font color='red'>replace() 方法可以实现替换字符串操作，用来替换的参数可以是一个字符串或是一个正则表达式。</font>

![1650503468658](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650503468658.png)

> 1. 第一个参数:   <font color='red'>被替换的字符串 或者  正则表达式</font>
> 2. 第二个参数:   替换为的字符串
> 3. 返回值是一个替换完毕的<font color='blue'>新字符串</font>

![1650503629046](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650503629046.png)

### 4.2 正则表达式参数

![1650503583754](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650503583754.png)

##### 修饰符

###### 忽略大小写和全局修饰符

> switch(也称为修饰符) 按照什么样的模式来匹配. 有三种值：
>
> - <font color='red'>g：全局匹配 </font>
> - <font color='green'>i：忽略大小写 </font>
> - <font color='blue'>gi：全局匹配 + 忽略大小写</font>

###### 换行修饰符

> m：检测字符串中的换行符

#### 案例：敏感词过滤

![1650503668787](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650503668787.png)

### search()方法

search()方法指明是否存在相应的匹配。返回这个匹配距离字符串开始的偏移位置。若无，则返回-1。

![1650503698618](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650503698618.png)

# ES6

## 一、ES6 简介

### 1、什么是 ES6 ?

<font color='red'>ES 的全称是 ECMAScript , 它是由 ECMA 国际标准化组织,制定的一项脚本语言的标准化规范。</font>

![1650503805921](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650503805921.png)

### 2、为什么使用 ES6 ?

每一次标准的诞生都意味着语言的完善，功能的加强。JavaScript语言本身也有一些令人不满意的地方。

- **变量提升特性增加了程序运行时的不可预测性**
- 语法过于松散，实现相同的功能，不同的人可能会写出不同的代码

## 二、ES6 的新增语法

### 1、let⭐⭐⭐

<font color='red'>**ES6中新增的用于声明变量的关键字。**</font>

- <font color='blue'>**let声明的变量只在所处于的块级有效**</font>

![1650503889749](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650503889749.png)

注意：<font color='blue'>在一个大括号中，使用let关键字声明的变量才具有块级作用域，使用var声明的变量不具备块级作用域特性。</font>

- <font color='red'>**不存在变量提升**</font>

![1650503927004](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650503927004.png)

- <font color='green'>**暂时性死区**</font>

**利用let声明的变量会绑定在这个块级作用域，不会受外界的影响 **

![1650503946769](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650503946769.png)

![1650504969158](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650504969158.png)

![1650504078253](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650504078253.png)

#### 经典面试题

![1650504125572](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650504125572.png)

![1650504130353](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650504130353.png)

**经典面试题图解：此题的关键点在于变量i是全局的，函数执行时输出的都是全局作用域下的i值。**

<font color='red'>输出：2，2</font>

![1650504451161](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650504451161.png)

![1650504458530](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650504458530.png)

**经典面试题图解：此题的关键点在于每次循环都会产生一个块级作用域，每个块级作用域中的变量都是不同的，函数执行时输出的是自己上一级（循环产生的块级作用域）作用域下的i值.**

<font color='red'>输出：0，1</font>

#### 小结

- <font color='red'>let关键字就是用来声明变量的</font>
- <font color='blue'>使用let关键字声明的变量具有块级作用域</font>
- 在一个大括号中使用let关键字声明的变量才具有块级作用域 var关键字是不具备这个特点的
- <font color='blue'>防止循环变量变成全局变量</font>
- <font color='green'>使用let关键字声明的变量没有变量提升</font>
- <font color='green'>使用let关键字声明的变量具有暂时性死区特性</font>

### 2、const⭐⭐⭐

<font color='red'>作用：**声明常量，常量就是值（内存地址）不能变化的量。**</font>

- <font color='red'>具有块级作用域</font>

- ![1650505251094](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650505251094.png)

- <font color='blue'>声明常量时必须赋值</font>

![1650505261166](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650505261166.png)

- 常量赋值后，值不能修改。

![1650505291865](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650505291865.png)

![1650505296944](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650505296944.png)

#### 小结

- const声明的变量是一个常量
- 既然是常量不能重新进行赋值，如果是基本数据类型，不能更改值，如果是复杂数据类型，不能更改地址值
- 声明 const时候必须要给定值

![1650505431236](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650505431236.png)

### 3、let、const、var 的区别

1. <font color='red'>使用 var 声明的变量，其作用域为该语句所在的函数内，且存在变量提升现象。</font>
2. <font color='blue'>使用 let 声明的变量，其作用域为该语句所在的代码块内，不存在变量提升。</font>

3. <font color='green'>使用 const 声明的是常量，在后面出现的代码中不能再修改该常量的值。</font>

![1650505930109](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650505930109.png)

### 4、解构赋值

<font color='red'>**ES6中允许从数组中提取值，按照对应位置，对变量赋值。对象也可以实现解构。**</font>

#### 数组解构

![1650505976453](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650505976453.png)

如果解构不成功，变量的值为undefined。

![1650505988010](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650505988010.png)

![1650506060612](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650506060612.png)

![1650506071119](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650506071119.png)

**<font color='red'>按照一定模式，从数组中或对象中提取值，将提取出来的值赋值给另外的变量。</font>**

#### 对象解构

![1650506136503](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650506136503.png)

![1650506141344](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650506141344.png)

#### 小结

- <font color='red'>**解构赋值就是把数据结构分解，然后给变量进行赋值**</font>
- **如果结构不成功，变量跟数值个数不匹配的时候，变量的值为undefined**
- <font color='hotpink'>**数组解构用中括号包裹，多个变量用逗号隔开，对象解构用花括号包裹，多个变量用逗号隔开**</font>
- 利用解构赋值能够让我们方便的去取对象中的属性跟方法

### 5、箭头函数

<font color='red'>ES6中新增的定义函数的方式。</font>

![1650506276768](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650506276768.png)

<font color='blue'>函数体中只有一句代码，且代码的执行结果就是返回值，可以省略大括号</font>

![1650506296485](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650506296485.png)

**如果形参只有一个，可以省略小括号**

![1650506313433](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650506313433.png)

**<font color='orange'>箭头函数不绑定this关键字，箭头函数中的this，指向的是函数定义位置的上下文this。</font>**

![1650506333738](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650506333738.png)

![1650506401304](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650506401304.png)

![1650506476790](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650506476790.png)

#### 小结

1. 箭头函数中不绑定this，箭头函数中的this指向是它所定义的位置，<font color='blue'>可以简单理解成，定义箭头函数中的作用域的this指向谁，它就指向谁。</font>
2. 箭头函数的优点在于解决了this执行环境所造成的一些问题。比如：**解决了匿名函数this指向的问题（匿名函数的执行环境具有全局性），包括setTimeout和setInterval中使用this所造成的问题**

![1650506578350](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650506578350.png)

#### 面试题

![1650506668092](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650506668092.png)

![1650506742649](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650506742649.png)

### 6、剩余参数⭐⭐

**<font color='red'>剩余参数语法允许我们将一个不定数量的参数表示为一个数组。</font>**

![1650506841406](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650506841406.png)

![1650506875614](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650506875614.png)

##### 剩余参数和解构配合使用

![1650506892766](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650506892766.png)

## 三、ES6 的内置对象扩展

### 1、Array 的扩展方法

#### 扩展运算符（展开语法）

<font color='red'>扩展运算符可以将数组或者对象转为用逗号分隔的参数序列。</font>

![1650507006887](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650507006887.png)

<font color='blue'>扩展运算符可以应用于合并数组。</font>

![1650507045874](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650507045874.png)

![1650507118890](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650507118890.png)

<font color='orange'>将类数组或可遍历对象转换为真正的数组</font>

![1650507157919](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650507157919.png)

![1650507181661](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650507181661.png)

#### <font color='blue'>构造函数方法：Array.from()</font>

<font color='red'>**将类数组或可遍历对象转换为真正的数组**</font>

![1650507241887](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650507241887.png)

<font color='green'>方法还可以接受第二个参数，作用类似于数组的map方法，用来对每个元素进行处理，将处理后的值放入返回的数组。</font>

![1650507277731](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650507277731.png)

**注意：如果是对象，那么属性需要写对应的索引 **

#### <font color='red'>实例方法：find()</font>

**用于找出第一个符合条件的数组成员，如果没有找到返回undefined**

![1650507356913](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650507356913.png)

![1650507506889](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650507506889.png)

#### 实例方法：findIndex()

<font color='green'>用于找出第一个符合条件的数组成员的位置，如果没有找到返回-1</font>

![1650507391942](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650507391942.png)

#### 实例方法：includes()

**表示某个数组是否包含给定的值，返回布尔值。**

![1650507561895](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650507561895.png)

### 2、String 的扩展方法

#### 模板字符串⭐⭐⭐

ES6新增的<font color='blue'>创建字符串的方式</font>，<font color='red'>使用反引号定义</font>。

![1650507588301](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650507588301.png)

**模板字符串中可以解析变量。**

![1650507641405](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650507641405.png)

![1650507685111](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650507685111.png)

<font color='blue'>模板字符串中可以换行</font>

![1650507699403](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650507699403.png)

**<font color='green'>在模板字符串中可以调用函数。</font>**

![1650507737877](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650507737877.png)

#### 实例方法：startsWith() 和 endsWith()

> 1. <font color='red'>startsWith()：表示参数字符串是否在原字符串的头部，返回布尔值</font>
> 2. <font color='blue'>endsWith()：表示参数字符串是否在原字符串的尾部，返回布尔值</font>

![1650507800463](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650507800463.png)

#### 实例方法：repeat()

<font color='blue'>repeat方法表示将原字符串重复n次，返回一个新字符串。</font>

![1650507834656](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650507834656.png)

### 3、Set 数据结构⭐⭐

<font color='red'>ES6 提供了新的数据结构  Set。它类似于数组，但是**成员的值都是唯一的，没有重复的值。**</font>

<font color='blue'>Set本身是一个构造函数，用来生成  Set  数据结构。</font>

![1650507903582](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650507903582.png)

<font color='green'>Set函数可以接受一个数组作为参数，用来初始化。</font>

![1650507911273](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650507911273.png)

#### 实例方法

> - <font color='orange'>add(value)：添加某个值，返回 Set 结构本身</font>
> - <font color='hotpink'>delete(value)：删除某个值，返回一个布尔值，表示删除是否成功</font>
> - <font color='red'>has(value)：返回一个布尔值，表示该值是否为 Set 的成员</font>
> - **clear()：清除所有成员，没有返回值**

![1650507975133](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650507975133.png)

#### 遍历

<font color='hotpink'>Set 结构的实例与数组一样，也拥有forEach方法，用于对每个成员执行某种操作，没有返回值。</font>

![1650508098433](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650508098433.png)

### ?.和??

#### ?.：可选链操作符

> 可以读取位于连接对象链深处属性的值，不必明确验证链中的每个引用是否有效
>
> 功能类似于“.” 链式操作符，不同之处在于，在引用为空null 或者 undefined 的情况下不会引起错误，该表达式短路返回值是 undefined
>
> 与函数调用一起使用时，如果给定的函数不存在，则返回 undefined。

![1651238816324](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651238816324.png)

#### ??：空值合并操作符

> 逻辑操作符，左侧为null和undefined时，才返回右侧的数

![1651238947812](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651238947812.png)

