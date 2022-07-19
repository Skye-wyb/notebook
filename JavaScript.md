# 计算机编程基础

## 一、编程语言

### 1、编程

<font color='red'>编程：就是让计算机为解决某个问题而使用某种程序设计语言编写程序代码，并最终得到结果的过程。</font>

<font color='red'>计算机程序</font>：**就是计算机所执行的一系列的指令集合，**而程序全部都是用我们所掌握的语言来编写的，所以人们要控制计算机一定要通过计算机语言向计算机发出命令。

注意：上面所定义的<font color='red'>计算机指的是任何能够执行代码的设备，可能是智能手机、ATM机、黑莓PI、服务器等等。</font>

### 2、计算机语言

> <font color='red'>计算机语言指用于人与计算机之间通讯的语言，它是人与计算机之间传递信息的媒介。</font>
>
> 计算机语言的种类非常的多，总的来说可以分成<font color='blue'>机器语言，汇编语言和高级语言三大类。</font>
>
> 实际上计算机最终所执行的都是 机器语言，它是由“0”和“1”组成的二进制数，<font color='green'>二进制是计算机语言的基础。</font>

![1649468557979](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649468557979.png)

### 3、编程语言

**可以通过类似于人类语言的 ”语言”来控制计算机，让计算机为我们做事情，这样的语言就叫做编程语言（Programming Language）。**

**<font color='red'>编程语言是用来控制计算机的一系列指令，它有固定的格式和词汇（不同编程语言的格式和词汇不一样），必须遵守。</font>**

如今通用的编程语言有两种形式：<font color='orange'>汇编语言和高级语言。</font>

<font color='red'>汇编语言</font>和机器语言实质是相同的，都是直接对硬件操作，只不过指令采用了英文缩写的标识符，容易识别和记忆。

<font color='red'>高级语言</font>主要是相对于低级语言而言，它并不是特指某一种具体的语言，而是包括了很多编程语言，常用的有C语言、C++、Java、C#、Python、PHP、JavaScript、Go语言、Objective-C、Swift等。

![1649468636485](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649468636485.png)

### 4、翻译器

> 1. 高级语言所编制的程序不能直接被计算机识别，必须经过转换才能被执行，为此，我们需要一个翻译器。
> 2. <font color='red'>翻译器可以将我们所编写的源代码转换为机器语言，这也被称为二进制化。 记住1和 0。</font>

![1649468710170](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649468710170.png)

### 5、编程语言和标记语言的区别

> 1. **编程语言有很强的逻辑和行为能力。**在编程语言里, 你会看到很多 if else 、for 、while等具有逻辑性和行为能力的指令，<font color='red'>这是主动的。</font>
> 2. **标记语言（html）不用于向计算机发出指令，常用于格式化和链接。**<font color='red'>标记语言的存在是用来被读取的, 他是被动的。</font>

### 总结

> 1. 计算机可以帮助人类解决某些问题
> 2. <font color='red'>程序员利用编程语言编写程序发出指令控制计算机来实现这些任务</font>
> 3. **编程语言有机器语言、汇编语言、高级语言**
> 4. 高级语言需要一个翻译器转换为计算机识别的机器语言
> 5. <font color='blue'>编程语言是主动的有很强的逻辑性</font>

## 二、计算机基础

### 1、计算机组成

![1649468852519](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649468852519.png)

![1649468873473](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649468873473.png)

### 2、数据存储

> 1. <font color='red'>计算机内部使用二进制 0 和 1来表示数据。</font>
> 2. <font color='blue'>所有数据，包括文件、图片等最终都是以二进制数据（0 和 1）的形式存放在硬盘中的。</font>
> 3. 所有程序，包括操作系统，本质都是各种数据，也以二进制数据的形式存放在硬盘中。平时我们所说的安装
> 4. <font color='orange'>软件，其实就是把程序文件复制到硬盘中。</font>
> 5. 硬盘、内存都是保存的二进制数据。

### 3、数据存储单位

> - bit < byte < kb < GB < TB<.....
> - 位(bit)：   1bit 可以保存一个 0 或者 1 （最小的存储单位）
> - 字节(Byte)：1B = 8b
> - 千字节(KB)：1KB = 1024B
> - 兆字节(MB)：1MB = 1024KB
> - 吉字节(GB):  1GB = 1024MB
> - 太字节(TB):  1TB = 1024GB

### 4、程序运行

![1649468973052](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649468973052.png)

> 1. <font color='red'>打开某个程序时，先从硬盘中把程序的代码加载到内存中</font>
> 2. **CPU执行内存中的代码**

注意：之所以要内存的一个重要原因，是因为 cpu 运行太快了，<font color='purple'>如果只从硬盘中读数据，会浪费cpu性能，所以，才使用存取速度更快的内存来保存运行时的数据。（内存是电，硬盘是机械）</font>

# 初始JavaScript

![1649469090134](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649469090134.png)

## 一、初始JavaScript

### 1、JavaScript是什么

> JavaScript 是世界上最流行的语言之一，是一种<font color='blue'>运行在客户端的脚本语言 </font>（Script 是脚本的意思）
>
> <font color='red'>脚本语言：不需要编译，运行过程中由 js 解释器( js 引擎）逐行来进行解释并执行</font>
>
> 现在也可以基于 Node.js 技术进行服务器端编程

![1649469171420](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649469171420.png)

### 2、JavaScript的作用

> - 表单动态校验（密码强度检测）  （ JS 产生最初的目的 ）
>
> - 网页特效
> - 服务端开发(Node.js)
> - 桌面程序(Electron)
> - App(Cordova) 
> - 控制硬件-物联网(Ruff)
> - 游戏开发(cocos2d-js)

### 3、html/css/javascript的关系

![1649469248642](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649469248642.png)

### 4、浏览器执行JS

**<font color='red'>浏览器分成两部分：渲染引擎和 JS 引擎</font>**

1. <font color='green'>渲染引擎：用来解析HTML与CSS，俗称内核，比如 chrome 浏览器的 blink ，老版本的 webkit</font>
2. JS 引擎：也称为 JS 解释器。 用来读取网页中的JavaScript代码，对其处理后运行，比如 chrome  浏览器的 V8

> **浏览器本身并不会执行JS代码，而是通过内置 JavaScript 引擎(解释器) 来执行 JS 代码 。**JS 引擎执行代码时逐行解释每一句源码（转换为机器语言），然后由计算机去执行，所以<font color='red'> JavaScript 语言归为脚本语言，会逐行解释执行。</font>

![1649469344578](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649469344578.png)

### 5、JS的组成

![1649469365530](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649469365530.png)

#### 5.1 ECMAScript

> ECMAScript 是由ECMA 国际（ 原欧洲计算机制造商协会）进行标准化的一门编程语言，这种语言在万维网上应用广泛，**它往往被称为 JavaScript 或 JScript，但实际上后两者是 ECMAScript 语言的实现和扩展。**

![1649469414220](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649469414220.png)

ECMAScript：ECMAScript 规定了JS的编程语法和基础核心知识，是所有浏览器厂商共同遵守的一套JS语法工业标准。

#### 5.2 DOM-文档对象模型

> <font color='red'>文档对象模型（Document Object Model，简称DOM）</font>：是W3C组织推荐的处理可扩展标记语言的标准编程接口。<font color='blue'>通过 DOM 提供的接口可以对页面上的各种元素进行操作（大小、位置、颜色等）。</font>

#### 5.3 BOM-浏览器对象模型

> <font color='red'>BOM (Browser Object Model，简称BOM) 是指浏览器对象模型：</font>它提供了独立于内容的、<font color='blue'>可以与浏览器窗口进行互动的对象结构。</font><font color='orange'>通过BOM可以操作浏览器窗口，比如弹出框、控制浏览器跳转、获取分辨率等。</font>

### 6、JS初体验

> JS 有3种书写位置，分别为<font color='red'>行内、内嵌和外部。 </font>

#### 1、行内式JS

![1649469582687](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649469582687.png)

> 1. 可以将单行或少量 JS 代码写在HTML标签的事件属性中（以 on 开头的属性），如：onclick
> 2. 注意单双引号的使用：在HTML中我们推荐使用双引号, **JS 中我们推荐使用单引号**
> 3. 可读性差， 在html中编写JS大量代码时，不方便阅读；
> 4. 引号易错，引号多层嵌套匹配时，非常容易弄混；
> 5. 特殊情况下使用

#### 2、内嵌JS

![1649469640808](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649469640808.png)

> 1. 可以将多行JS代码写到 <script> 标签中
> 2. 内嵌 JS 是学习时常用的方式

#### 3、外部JS文件

![1649469678270](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649469678270.png)

> 1. 利于HTML页面代码结构化，把大段 JS代码独立到 HTML 页面之外，既美观，也方便文件级别的复用
> 2. 引用外部 JS文件的 script 标签中间不可以写代码
> 3. 适合于JS 代码量比较大的情况

## 二、JavaScript注释

### 1、单行注释

为了提高代码的可读性，JS与CSS一样，也提供了注释功能。JS中的注释主要有两种，分别是单行注释和多行注释。

单行注释的注释方式如下：

![1649469750743](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649469750743.png)

**快捷键：ctrl+/**

### 2、多行注释

![1649469781555](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649469781555.png)

> /* */  用来注释多行文字（ 默认快捷键  alt +  shift  + a ） 
>
> 快捷键修改为：   ctrl + shift  +  /  
>
> vscode -> 首选项按钮  ->  键盘快捷方式 ->  查找 原来的快捷键  -> 修改为新的快捷键 -> 回车确认

## 3、JavaScript输入输出语句

![1649469876337](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649469876337.png)

> 注意：<font color='red'>alert() 主要用来显示消息给用户，console.log() 用来给程序员自己看运行时的消息。</font>

# 变量

## 一、变量概述

### 1、什么是变量

> 白话：变量就是一个装东西的盒子。
>
> <font color='red'>通俗：变量是用于存放数据的容器。 我们通过 变量名 获取数据，甚至数据可以修改。</font>

### 2、变量在内存中的存储

> <font color='blue'>本质：变量是程序在内存中申请的一块用来存放数据的空间。</font>
>
> 类似我们酒店的房间，一个房间就可以看做是一个变量。  

![1649470014251](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649470014251.png)

## 二、变量的使用

> 变量在使用时分为两步： <font color='red'>1. 声明变量   2. 赋值 </font>

### 1、声明变量

![1649470075767](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649470075767.png)

- <font color='blue'>var 是一个 JS关键字，用来声明变量( variable 变量的意思 )。</font>使用该关键字声明变量后，计算机会自动为变量分配内存空间，不需要程序员管
- age 是程序员定义的变量名，我们要通过变量名来访问内存中分配的空间

### 2、赋值

![1649470107977](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649470107977.png)

- = 用来**把右边的值赋给左边的变量空间中   此处代表赋值的意思**
- 变量值是程序员保存到变量空间里的值

### 3、变量的初始化

![1649470147924](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649470147924.png)

<font color='red'>声明一个变量并赋值， 我们称之为变量的初始化。</font>

## 三、变量语法扩展

### 1、更新变量

> **一个变量被重新复赋值后，它原有的值就会被覆盖，变量值将以最后一次赋的值为准。**

![1649470263225](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649470263225.png)

### 2、同时声明多个变量

> 同时声明多个变量时，只需要写一个 var， 多个变量名之间使用英文逗号隔开。

![1649470289224](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649470289224.png)

### 3、声明变量特殊情况

![1649470314218](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649470314218.png)

## 四、变量命名语法规范

> 1. 由字母(A-Za-z)、数字(0-9)、下划线(_)、美元符号( $ )组成，如：usrAge, num01, _name
> 2. <font color='red'>严格区分大小写。</font>var app; 和 var App; 是两个变量
> 3. 不能以数字开头。  18age   是错误的
> 4. 不能是关键字、保留字。例如：var、for、while
> 5. 变量名必须有意义。 MMD   BBD        nl   →     age  
> 6. 遵守驼峰命名法。首字母小写，后面单词的首字母需要大写。 myFirstName
> 7. 推荐翻译网站： 有道    爱词霸

## 小结：

![1649470408062](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649470408062.png)

# 数据类型

## 一、数据类型简介

### 1、为什么需要数据类型

> <font color='red'>在计算机中，不同的数据所需占用的存储空间是不同的，为了便于把数据分成所需内存大小不同的数据，充分利用存储空间，于是定义了不同的数据类型。</font>
>
> 简单来说，数据类型就是数据的类别型号。比如姓名“张三”，年龄18，这些数据的类型是不一样的。

### 2、变量的数据类型

变量是用来存储值的所在处，它们有名字和数据类型。<font color='blue'>变量的数据类型决定了如何将代表这些值的位存储到计算机的内存中。</font>JavaScript 是一种弱类型或者说动态语言。这意味着不用提前声明变量的类型，在程序运行过程中，类型会被自动确定。

![1649470538994](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649470538994.png)

> <font color='red'>在代码运行时，变量的数据类型是由 JS引擎 根据 = 右边变量值的数据类型来判断 的，运行完毕之后， 变量就确定了数据类型。</font>
>
> <font color='blue'>JavaScript 拥有动态类型，同时也意味着相同的变量可用作不同的类型：</font>

![1649470572900](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649470572900.png)

### 3、数据类型分类

> JS 把数据类型分为两类：
>
> 1. 简单数据类型 （Number,String,Boolean,Undefined,Null）
>
> 2. 复杂数据类型 （object)

## 二、简单数据类型

![1649470625726](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649470625726.png)

### 1、数字型-Number

> **JavaScript 数字类型既可以用来保存整数值，也可以保存小数(浮点数）。**  

![1649470658764](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649470658764.png)

#### 1.1 数字型进制

最常见的进制有二进制、八进制、十进制、十六进制。

![1649470680662](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649470680662.png)

现阶段我们只需要记住，在JS中<font color='blue'>八进制前面加0，十六进制前面加 0x  </font>

#### 1.2 数字型范围

JavaScript中数值的最大和最小值

![1649470732117](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649470732117.png)

> 1. 最大值：Number.MAX_VALUE，这个值为： 1.7976931348623157e+308
> 2. 最小值：Number.MIN_VALUE，这个值为：5e-32

#### 1.3 数字型的特殊值

![1649470764790](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649470764790.png)

> - Infinity ，代表无穷大，大于任何数值
> - -Infinity ，代表无穷小，小于任何数值
> - NaN ，Not a number，代表一个非数值

#### 1.4 isNaN()

<font color='red'>用来判断一个变量是否为非数字的类型，返回 true 或者 false</font>

![1649470817541](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649470817541.png)

![1649470822908](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649470822908.png)

### 2、字符串类型-String

> 字符串型可以是引号中的任意文本，其语法为 双引号 "" 和 单引号''

![1649470863484](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649470863484.png)

#### 2.1 字符串引号嵌套

<font color='red'>JS 可以用单引号嵌套双引号 ，或者用双引号嵌套单引号 (外双内单，外单内双)</font>

![1649470894713](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649470894713.png)

#### 2.2 字符串转义符

> 类似HTML里面的特殊字符，<font color='red'>字符串中也有特殊字符，我们称之为转义符。</font>
>
> 转义符都是 \ 开头的，常用的转义符及其说明如下：

![1649470932452](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649470932452.png)

#### 2.3 字符串长度！！！

字符串是由若干字符组成的，这些字符的数量就是字符串的长度。**<font color='red'>通过字符串的 length 属性可以获取整个字符串的长度。</font>**

![1649471000949](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649471000949.png)

#### 2.4 字符串拼接

> 1. <font color='red'>多个字符串之间可以使用 + 进行拼接，其拼接方式为 字符串 + 任何类型 = 拼接之后的新字符串</font>
> 2. 拼接前会把与字符串相加的任何类型转成字符串，再拼接成一个新的字符串

![1649471048470](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649471048470.png)

**注意：字符串拼接可用于将任意类型转为字符串类型，如 str = 1 + ""**

**字符串拼接加强**

![1649471813703](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649471813703.png)

>  我们经常会将字符串和变量来拼接，因为变量可以很方便地修改里面的值
>
> 变量是不能添加引号的，因为加引号的变量会变成字符串
>
> 如果变量两侧都有字符串拼接，口诀“引引加加 ”，删掉数字，变量写加中间

#### 2.5 Boolean型

> **布尔类型有两个值：true 和 false ，其中 true 表示真（对），而 false 表示假（错）**。
>
> 布尔型和数字型相加的时候， true 的值为 1 ，false 的值为 0。

![1649471871451](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649471871451.png)

#### 2.6 undefined和null

> 一个声明后没有被赋值的变量会有一个默认值 undefined ( 如果进行相连或者相加时，注意结果）

![1649471897484](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649471897484.png)

> 一个声明变量给 null 值，里面存的值为空（学习对象时，我们继续研究null)

![1649471911868](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649471911868.png)

## 三、获取变量数据类型

> <font color='red'>typeof 可用来获取检测变量的数据类型</font>

![1649471950480](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649471950480.png)

**不同类型的返回值：**

![1649471965999](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649471965999.png)

#### 字面量

> 字面量是在源代码中一个固定值的表示法，通俗来说，就是字面量表示如何表达这个值。
>
> 数字字面量：8, 9, 10
>
> 字符串字面量：'黑马程序员', "大前端"
>
> 布尔字面量：true，false

## 四、数据类型转换

### 1、定义

> <font color='red'>使用表单、prompt 获取过来的数据默认是字符串类型的，</font>此时就不能直接简单的进行加法运算，而需要转换变量的数据类型。通俗来说，**<font color='green'>就是把一种数据类型的变量转换成另外一种数据类型。</font>**
>
> 我们通常会实现3种方式的转换：
>
> 1. 转换为<font color='orange'>字符串类型</font>
> 2. 转换为<font color='orange'>数字型</font>
> 3. 转换为<font color='orange'>布尔型</font>

### 2、转换为字符串

![1649472079234](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649472079234.png)

> toString() 和 String()  使用方式不一样。
>
> 三种转换方式，我们更喜欢用第三种加号拼接字符串转换方式， **这一种方式也称之为隐式转换。**

### 3、转换为数字型！！！

![1649472132574](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649472132574.png)

> - 注意 parseInt 和 parseFloat 单词的大小写，这2个是重点
> - 隐式转换是我们在进行算数运算的时候，JS 自动转换了数据类型

### 4、转换为Boolean型

![1649472169299](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649472169299.png)

> **代表空、否定的值会被转换为 false  ，如 ''、0、NaN、null、undefined**  
>
> 其余值都会被转换为 true

![1649472195496](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649472195496.png)

# 扩展

## 1、解释型语言、编译型语言

计算机不能直接理解任何除机器语言以外的语言，所以必须要把程序员所写的程序语言翻译成机器语言才能执行程序。程序语言翻译成机器语言的工具，被称为翻译器。

![1649472634050](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649472634050.png)

> 1. 翻译器翻译的方式有两种：一个是编译，另外一个是解释。两种方式之间的区别在于翻译的时间点不同
> 2. <font color='red'>编译器是在代码执行之前进行编译，生成中间代码文件</font>
> 3. <font color='red'>解释器是在运行时进行及时解释，</font>并立即执行(当编译器以解释方式运行的时候，也称之为解释器)

### 执行过程

![1649472673717](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649472673717.png)

## 2、标识符

标识(zhi)符：就是指开发人员为变量、属性、函数、参数取的名字。

标识符不能是关键字或保留字。

## 3、关键字

关键字：是指 JS本身已经使用了的字，不能再用它们充当变量名、方法名。

包括：break、case、catch、continue、default、delete、do、else、finally、for、function、if、in、instanceof、new、return、switch、this、throw、try、typeof、var、void、while、with 等。

## 4、保留字

保留字：实际上就是预留的“关键字”，意思是现在虽然还不是关键字，但是未来可能会成为关键字，同样不能使用它们当变量名或方法名。

包括：boolean、byte、char、class、const、debugger、double、enum、export、extends、fimal、float、goto、implements、import、int、interface、long、mative、package、private、protected、public、short、static、super、synchronized、throws、transient、volatile 等。

注意：如果将保留字用作变量名或函数名，那么除非将来的浏览器实现了该保留字，否则很可能收不到任何错误消息。当浏览器将其实现后，该单词将被看做关键字，如此将出现关键字错误。

# JavaScript运算符

## 一、运算符

<font color='red'>运算符（operator）也被称为操作符，是用于实现赋值、比较和执行算数运算等功能的符号。</font>

> JavaScript中常用的运算符有：
>
> 1. 算数运算符
> 2. 递增和递减运算符
> 3. 比较运算符
> 4. 逻辑运算符
> 5. 赋值运算符

## 二、算术运算符

概念：算术运算使用的符号，<font color='red'>用于执行两个变量或值的算术运算。</font>

![1649472856855](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649472856855.png)

### 浮点数精度问题

> 浮点数值的最高精度是 17 位小数，但在进行算术计算时其精确度远远不如整数。

![1649472892726](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649472892726.png)

> 所以：<font color='red'>不要直接判断两个浮点数是否相等 !  </font>

![1649472914606](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649472914606.png)

### 表达式和返回值

> <font color='red'>表达式：是由数字、运算符、变量等以能求得数值的有意义排列方法所得的组合</font>
>
> 简单理解：是由数字、运算符、变量等组成的式子

## 三、递增和递减运算符

> 如果需要反复给数字变量添加或减去1，<font color='red'>可以使用递增（++）和递减（ -- ）运算符来完成。</font>
>
> 在 JavaScript 中，<font color='blue'>递增（++）和递减（ -- ）既可以放在变量前面，也可以放在变量后面。放在变量前面时，我们可以称为前置递增（递减）运算符，放在变量后面时，我们可以称为后置递增（递减）运算符。</font>
>
> **注意：递增和递减运算符必须和变量配合使用。** 

### 1、递增运算符

#### 1.1 前置递增运算符

> ++num 前置递增，就是自加1，类似于 num =  num + 1，但是 ++num 写起来更简单。
>
> 使用口诀：<font color='red'>先自加，后返回值</font>

![1649473031038](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649473031038.png)

#### 1.2 后置递增运算符

> num++ 后置递增，就是自加1，类似于 num =  num + 1 ，但是 num++ 写起来更简单。
>
> 使用口诀：<font color='red'>先返回原值，后自加 </font>

![1649473083153](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649473083153.png)

#### 小结：

> - 前置递增和后置递增运算符可以简化代码的编写，让变量的值 + 1  比以前写法更简单
> - 单独使用时，运行结果相同
> - 与其他代码联用时，执行结果会不同 
> - <font color='red'>后置：先原值运算，后自加（先人后己） </font>
> - <font color='red'>前置：先自加，后运算（先已后人）</font>
> - 开发时，大多使用后置递增/减，并且代码独占一行，例如：num++; 或者 num--;

## 四、比较运算符

> 概念：**比较运算符（关系运算符）是两个数据进行比较时所使用的运算符，**比较运算后，会返回一个布尔值（true / false）作为比较运算的结果。

![1649473171503](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649473171503.png)

### =符号

![1649473185227](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649473185227.png)

![1649473190324](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649473190324.png)

## 五、逻辑运算符

### 1、概述

概念：<font color='red'>逻辑运算符是用来进行布尔值运算的运算符，其返回值也是布尔值。</font>后面开发中经常用于多个条件的判断

![1649473235977](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649473235977.png)

### 2、逻辑与 && 

> <font color='orange'>两边都是 true才返回 true，否则返回 false</font>

![1649473266371](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649473266371.png)

### 3、逻辑或 ||

> <font color='red'>两边都为 false 才返回 false，否则都为true</font>

![1649473300548](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649473300548.png)

### 4、逻辑非 ！

> 逻辑非（!）也叫作取反符，用来取一个布尔值相反的值，如 true 的相反值是 false

![1649473355274](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649473355274.png)

### 5、短路运算（逻辑中断）

> 短路运算的原理：当有多个表达式（值）时，左边的表达式值可以确定结果时，就不再继续运算右边的表达式的值；

#### 5.1 逻辑与

> 语法： <font color='red'>表达式1 && 表达式2</font>
>
> 如果第一个表达式的值为真，则返回表达式2
>
> 如果第一个表达式的值为假，则返回表达式1

![1649473442655](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649473442655.png)

#### 5.2 逻辑或

> 语法： <font color='red'>表达式1 || 表达式2</font>
>
> 如果第一个表达式的值为真，则返回表达式1
>
> 如果第一个表达式的值为假，则返回表达式2

![1649473478097](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649473478097.png)

## 六、赋值运算符

**概念：用来把数据赋值给变量的运算符。**

![1649473510375](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649473510375.png)

![1649473517690](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649473517690.png)

## 七、运算符优先级

![1649473534577](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649473534577.png)

> - 一元运算符里面的逻辑非优先级很高
> - <font color='red'>逻辑与比逻辑或优先级高</font>

# JavaScript流程控制-分支

## 一、流程控制

> 在一个程序执行的过程中，各条代码的执行顺序对程序的结果是有直接影响的。很多时候<font color='red'>我们要通过控制代码的执行顺序来实现我们要完成的功能。</font>
>
> 简单理解： **<font color='orange'>流程控制就是来控制我们的代码按照什么结构顺序来执行</font>**
>
> <font color='blue'>流程控制主要有三种结构，分别是**顺序结构**、**分支结构**和**循环结构**，这三种结构代表三种代码执行的顺序。</font>

![1649473658050](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649473658050.png)

## 二、顺序流程控制

> 顺序结构是程序中最简单、最基本的流程控制，它没有特定的语法结构，程<font color='blue'>序会按照代码的先后顺序，依次执行，程序中大多数的代码都是这样执行的。</font>

![1649473696031](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649473696031.png)

## 三、分支流程控制-if语句

### 1、分支结构

> 由上到下执行代码的过程中，**根据不同的条件，执行不同的路径代码（执行代码多选一的过程），从而得到不同的结果**

![1649473741244](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649473741244.png)

> JS 语言提供了两种分支结构语句
>
> 1. if 语句
> 2. switch 语句

### 2、if语句

1、语法结构

![1649473779885](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649473779885.png)

> 语句可以理解为一个行为，循环语句和分支语句就是典型的语句。一个程序由很多个语句组成，一般情况下，会分割成一个一个的语句。

2、执行流程

![1649473818190](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649473818190.png)

### 3、if-else语句

1、语法结构

![1649473846759](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649473846759.png)

2、执行流程

![1649473856373](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649473856373.png)

### 4、if-else-if语句（多分支）

1、语法结构

![1649473893489](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649473893489.png)

2、执行流程

![1649473904527](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649473904527.png)

## 四、三元表达式

三元表达式也能做一些简单的条件选择。 有三元运算符组成的式子称为三元表达式

**1、语法结构**

![1649473950510](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649473950510.png)

2、执行思路

> <font color='red'>如果表达式1为 true ，则返回表达式2的值，如果表达式1为 false，则返回表达式3的值</font>
>
> 简单理解： 就类似于  if  else （双分支） 的简写

## 五、分支流程控制-switch语句

### 1、语法结构

> switch 语句也是多分支语句，<font color='red'>它用于基于不同的条件来执行不同的代码。</font>当要针对变量设置一系列的特定值的选项时，就可以使用 switch。

![1649474120458](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649474120458.png)

> 1. switch ：开关 转换  ， case ：小例子   选项
>
> 2. **关键字 switch 后面括号内可以是表达式或值， 通常是一个变量**
>
> 3. 关键字 case , 后跟一个选项的表达式或值，<font color='red'>后面跟一个冒号</font>
>
> 4. <font color='red'>switch 表达式的值会与结构中的 case 的值做比较 </font>
>
> - 如果存在匹配全等(===) ，则与该 case 关联的代码块会被执行，并在遇到 break 时停止，整个 switch 语句代码执行结束
> - 如果所有的 case 的值都和表达式的值不匹配，则执行 default 里的代码

<font color='red'>**注意： 执行case 里面的语句时，如果没有break，则继续执行下一个case里面的语句。**</font>

### 2、switch语句和if-else-if语句的区别

> 1. 一般情况下，它们两个语句可以相互替换
> 2. switch...case 语句通常处理 case为比较确定值的情况， 而 if…else…语句更加灵活，常用于范围判断(大于、等于某个范围)
> 3. switch 语句进行条件判断后直接执行到程序的条件语句，效率更高。而if…else 语句有几种条件，就得判断多少次。
> 4. 当分支比较少时，if… else语句的执行效率比 switch语句高。
> 5. 当分支比较多时，switch语句的执行效率比较高，而且结构更清晰。 

# JavaScript流程控制-循环

## 一、循环

#### 1、循环的目的

> 在实际问题中，有许多具有规律性的重复操作，因此在程序中要完成这类操作就需要重复执行某些语句

#### 2、JS中的循环

> 在Js 中，主要有三种类型的循环语句：
>
> 1. for 循环
> 2. while 循环
> 3. do...while 循环

## 二、for循环

> <font color='red'>在程序中，一组被重复执行的语句被称之为循环体，能否继续重复执行，取决于循环的终止条件。</font>
>
> <font color='red'>**由循环体及循环的终止条件组成的语句，被称之为循环语句**</font>

#### 1、语法结构

> **<font color='blue'>for 循环主要用于把某些代码循环若干次，</font>通常跟计数有关系。其语法结构如下：**

![1649474500552](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649474500552.png)

> 1. 初始化变量：通常被用于初始化一个计数器，该表达式可以<font color='red'>使用 var 关键字声明新的变量</font>，这个变量帮我们来<font color='red'>记录次数。</font>
> 2. 条件表达式：<font color='red'>用于确定每一次循环是否能被执行</font>。如果结果是 true 就继续循环，否则退出循环。
> 3. 操作表达式：每次循环的最后都要执行的表达式。通常被用于更新或者递增计数器变量。当然，递减变量也是可以的。

#### 2、执行过程

> 1. 初始化变量，**初始化操作在整个 for 循环只会执行一次。**
> 2. **执行条件表达式，如果为true，则执行循环体语句，否则退出循环，循环结束。**
> 3. 执行操作表达式，此时第一轮结束。
> 4. 第二轮开始，直接去执行条件表达式（不再初始化变量），如果为 true ，则去执行循环体语句，否则退出循环。
> 5. 继续执行操作表达式，第二轮结束。
> 6. 后续跟第二轮一致，直至条件表达式为假，结束整个 for 循环。

##### 断点调试

> 断点调试是指自己在程序的某一行设置一个断点，调试时，程序运行到这一行就会停住，然后你可以一步一步往下调试，调试过程中可以看各个变量当前的值，出错的话，调试到出错的代码行即显示错误，停下。
>
> **断点调试可以帮我们观察程序的运行过程**
>
> 浏览器中按 F12--> sources -->找到需要调试的文件-->在程序的某一行设置断点
>
> Watch: 监视，通过watch可以监视变量的值的变化，非常的常用。
>
> F11: 程序单步执行，让程序一行一行的执行，这个时候，观察watch中变量的值的变化。

#### 3、for循环重复相同的代码

for循环可以重复相同的代码 ，比如我们要输出10句“媳妇我错了”

![1649474685756](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649474685756.png)

#### 4、for循环重复不同的代码

for 循环还可以重复不同的代码，这主要是因为使用了计数器 ，计数器在每次循环过程中都会有变化。

例如，求输出一个人1到100岁：

![1649474794836](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649474794836.png)

![1649474807126](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649474807126.png)

**for 循环因为有了计数器的存在，我们还可以重复的执行某些操作，比如做一些算术运算。 **

### 求1-100之间所有整数的累加和

分析：

> - 需要循环100次，我们需要一个计数器  i  
> - 我们需要一个存储结果的变量 sum ，但是初始值一定是 0
> - 核心算法：1 + 2 + 3 + 4 ....   ，sum  =  sum + i;

代码实现：

![1649474870825](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649474870825.png)

> 1. 求1-100之间所有数的平均值
> 2. 求1-100之间所有偶数和奇数的和
> 3. 求1-100之间所有能被3整除的数字的和

## 三、双重for循环

![1649474966222](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649474966222.png)

> <font color='red'>循环嵌套是指在一个循环语句中再定义一个循环语句的语法结构，</font>例如在for循环语句中，可以再嵌套一个for 循环，这样的 for 循环语句我们**称之为双重for循环。**

#### 1、双重循环语法

![1649474997959](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649474997959.png)

> 1. 内层循环可以看做外层循环的语句
> 2. 内层循环执行的顺序也要遵循 for 循环的执行顺序 
> 3. <font color='blue'>外层循环执行一次，内层循环要执行全部次数</font>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649475080941.png" alt="1649475080941" style="zoom:150%;" />

![1649475096951](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649475096951.png)

#### 打印倒三角形

![1649475123636](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649475123636.png)

> 1. 一共有10行，但是每行的星星个数不一样，因此需要用到双重 for 循环
> 2. 外层的 for 控制行数 i ，循环10次可以打印10行  
> 3. 内层的 for 控制每行的星星个数 j  
> 4. 核心算法： 每一行星星的个数   j = i ;    j <= 10;   j++
> 5. 每行打印完毕后，都需要重新换一行 

![1649475143306](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649475143306.png)

#### 打印正三角形

![1649475159189](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649475159189.png)

> 1. 一共有9行，但是每行的个数不一样，因此需要用到双重 for 循环
> 2. 外层的 for 循环控制行数 i ，循环9次 ，可以打印 9 行  
> 3. 内层的 for 循环控制每行公式  j  
> 4. 核心算法：每一行 公式的个数正好和行数一致， j <= i;
> 5. 每行打印完毕，都需要重新换一行 
> 6. 把公式用 i 和 j 替换

![1649475189279](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649475189279.png)

### for循环小结

> - for 循环可以重复执行某些相同代码
> - for 循环可以重复执行些许不同的代码，因为我们有计数器
> - for 循环可以重复执行某些操作，比如算术运算符加法操作
> - 随着需求增加，双重for循环可以做更多、更好看的效果
> - <font color='red'>双重 for 循环，外层循环一次，内层 for 循环全部执行</font>
> - for 循环是循环条件和数字直接相关的循环

## 四、while循环

> <font color='red'>while 语句可以在条件表达式为真的前提下，循环执行指定的一段代码，直到表达式不为真时结束循环。</font>
>
> while语句的语法结构如下：

![1649475263441](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649475263441.png)

> **执行思路：**
>
> - 先执行条件表达式，如果结果为 true，则执行循环体代码；如果为 false，则退出循环，执行后面代码
> - 执行循环体代码
> - 循环体代码执行完毕后，程序会继续判断执行条件表达式，如条件仍为true，则会继续执行循环体，直到循环条件为 false 时，整个循环过程才会结束

> <font color='red'>**注意：**</font>
>
> 1. 使用 while 循环时一定要注意，它<font color='blue'>必须要有退出条件，否则会成为死循环</font>
> 2. while 循环和 for 循环的不同之处在于 while 循环可以做较为复杂的条件判断，比如判断用户名和密码

## 五、do-while循环

> <font color='blue'>do... while 语句其实是 while 语句的一个变体。**该循环会先执行一次代码块，**然后对条件表达式进行判断，如果条件为真，就会重复执行循环体，否则退出循环。</font>
>
> do... while 语句的语法结构如下：

![1649475478493](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649475478493.png)

> **执行思路：**
>
> - 先执行一次循环体代码 
> - 再执行条件表达式，如果结果为 true，则继续执行循环体代码，如果为 false，则退出循环，继续执行后面代码

<font color='red'>注意：先再执行循环体，再判断，我们会发现 do…while 循环语句**至少会执行一次循环体代码**</font>

### 循环小结：

> - JS 中循环有 for 、while 、 do while 
> - 三个循环很多情况下都可以相互替代使用
> - 如果是用来计次数，跟数字相关的，三者使用基本相同，但是我们更喜欢用 for
> - while 和 do…while 可以做更复杂的判断条件，比 for 循环灵活一些 
> - **while 和 do…while 执行顺序不一样，while 先判断后执行，do…while 先执行一次，再判断执行**
> - **while 和 do…while 执行次数不一样，do…while 至少会执行一次循环体， 而 while 可能一次也不执行**
> - 实际工作中，我们更常用for 循环语句，它写法更简洁直观， 所以这个要重点学习

## 六、continue、break

### 1、continue关键字

> <font color='red'>continue 关键字用于立即跳出本次循环，继续下一次循环</font>（本次循环体中 continue 之后的代码就会少执行一次）。
>
> 例如，吃5个包子，第3个有虫子，就扔掉第3个，继续吃第4个第5个包子，其代码实现如下：

![1649475612691](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649475612691.png)

### 2、break关键字

> <font color='red'>break 关键字用于立即跳出整个循环（循环结束）。</font>
>
> 例如，吃5个包子，吃到第3个发现里面有半个虫子，其余的不吃了，其代码实现如下：

![1649475638861](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649475638861.png)

# JavaScript 命名规范以及语法格式

### 1、标识符命名规范

> 1. 变量、函数的命名必须要有意义
>
> 2. 变量的名称一般用名词  
>
> 3. 函数的名称一般用动词  

### 2、操作符规范

![1649475795845](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649475795845.png)

### 3、单行注释规范

![1649475813747](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649475813747.png)

# JavaScript数组

## 一、数组的概念

> <font color='red'>数组是指一组数据的集合，其中的每个数据被称作元素，在数组中可以存放任意类型的元素。</font>
>
> 数组是一种将一组数据存储在单个变量名下的优雅方式。

![1649475937912](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649475937912.png)

## 二、创建数组

### 1、数组的创建方式

> 1. 利用  new 创建数组  
>
> 2. 利用数组字面量创建数组

#### 1.1 利用new创建数组

![1649476016283](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649476016283.png)

#### 1.2 利用数组字面量创建数组

![1649483469185](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649483469185.png)

> 1. <font color='red'>数组的字面量是方括号 [ ] </font>
> 2. **声明数组并赋值称为数组的初始化**
> 3. 这种字面量方式也是我们以后最多使用的方式  

#### 1.3 数组元素的类型

数组中可以**存放任意类型的数据**，例如字符串，数字，布尔值等。

![1649483703908](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649483703908.png)

## 三、获取数组中的元素

### 1、数组的索引

> **索引 (下标) ：用来访问数组元素的序号（数组下标从 0 开始）。**

![1649483981199](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649483981199.png)

<font color='red'>数组可以通过索引来访问、设置、修改对应的数组元素，我们可以通过“**数组名[索引]**”的形式来获取数组中的元素。</font>

这里的访问就是**获取得到**的意思

![1649484050617](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649484050617.png)

## 四、遍历数组

![1649484174935](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649484174935.png)

问：怎么把数组里面的元素全部取出来？

> 规律：
>
> 从代码中我们可以发现，从数组中取出每一个元素时，代码是重复的，有所不一样的是索引值在递增
>
> 答案就是 **循环**

#### 1、遍历的概念

<font color='red'>遍历：就是把数组中的每个元素从头到尾都访问一次</font>（类似我们每天早上学生的点名）。

我们可以**通过 for 循环索引遍历数组中的每一项**

![1649484302903](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649484302903.png)

#### 2、数组长度

> <font color='red'>**使用“数组名.length”可以访问数组元素的数量（数组长度）。**  </font>

![1649484351652](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649484351652.png)

<font color='red'>**注意：**</font>

此处**数组的长度是数组元素的个数** ，不要和数组的索引号混淆。

当我们数组里面的元素个数发生了变化，这个 length 属性跟着一起变化。

遍历案例：

![1649484455657](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649484455657.png)

##### 数组求和及平均值

>  求数组 [2,6,1,7, 4] 里面所有元素的和以及平均值。

思路分析：

> 1. 声明一个求和变量 sum。
> 2. 遍历这个数组，把里面每个数组元素加到 sum 里面。
> 3. 用求和变量 sum 除以数组的长度就可以得到数组的平均值。

![1649484552071](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649484552071.png)

##### 数组最大值

>  求数组[2,6,1,77,52,25,7]中的最大值。

思路分析：

> 1. 声明一个保存最大元素的变量 max。
> 2. 默认最大值可以取数组中的第一个元素。
> 3. 遍历这个数组，把里面每个数组元素和 max 相比较。
> 4. 如果这个数组元素大于max 就把这个数组元素存到 max 里面，否则继续下一轮比较。
> 5. 最后输出这个 max。

![1649484594095](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649484594095.png)

##### 数组转为字符串！！！

> 要求：将数组 ['red', 'green', 'blue', 'pink'] 里面的元素转换为字符串
>
> 输出： 'redgreenbluepink'

思路分析：

> 1. 就是把里面的元素相加就好了，但是注意保证是字符相加。
> 2. 需要一个新变量 str 用于存放转换完的字符串。
> 3. 遍历原来的数组，分别把里面数据取出来，加到字符串变量 str 里面。

![1649484650732](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649484650732.png)

##### 数组转换为分割字符串！！！

> 要求：将数组 ['red', 'green', 'blue', 'pink'] 转换为字符串，并且用 | 或其他符号分割
>
> 输出： 'red|green|blue|pink'

思路分析：

> 1. 需要一个新变量用于存放转换完的字符串 str。
> 2. 遍历原来的数组，分别把里面数据取出来，加到字符串里面。
> 3. 同时在后面多加一个分隔符。

![1649484732501](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649484732501.png)

## 五、数组中新增元素

### 1、通过修改 length 长度新增数组元素

> 1. 可以通过<font color='red'>修改 length 长度来实现数组扩容的目的</font>
>
> 2. length 属性是可读写的

![1649484799789](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649484799789.png)

其中索引号是 4，5，6 的空间没有给值，就是声明变量未给值，默认值就是 undefined。

![1649484810712](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649484810712.png)

### 2、通过修改数组索引新增数组元素

> 1. <font color='red'>可以通过修改数组索引的方式追加数组元素</font>
> 2. 不能直接给数组名赋值，否则会覆盖掉以前的数据

![1649484873248](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649484873248.png)

#### 筛选数组

> 要求：将数组 [2, 0, 6, 1, 77, 0, 52, 0, 25, 7] 中大于等于 10 的元素选出来，放入新数组。

思路分析：

> 1. 声明一个新的数组用于存放新数据。
> 2. 遍历原来的数组，找出大于等于 10 的元素。
> 3. 依次追加给新数组 newArr。

**实现代码1：**

![1649484957445](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649484957445.png)

**实现代码2：**

![1649484995991](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649484995991.png)

## 六、数组案例

### 1、删除指定数组元素

> 要求：将数组[2, 0, 6, 1, 77, 0, 52, 0, 25, 7]中的 0 去掉后，形成一个不包含 0 的新数组。

**思路分析：**

> - 需要一个新数组用于存放筛选之后的数据。
> - 遍历原来的数组，把不是 0 的数据添加到新数组里面( 此时要注意采用数组名+索引的格式接收数据)。
> - 新数组里面的个数，用 length 不断累加。

![1649485149878](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649485149878.png)

### 2、翻转数组

> 要求: 将数组 ['red', 'green', 'blue', 'pink', 'purple'] 的内容反过来存放。
> 输出： ['purple', 'pink', 'blue', 'green', 'red']

![1649485181693](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649485181693.png)

实现代码：

![1649485195500](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649485195500.png)

### 3、数组排序（冒泡排序）

> <font color='red'>冒泡排序：是一种算法，把一系列的数据按照一定的顺序进行排列显示(从小到大或从大到小）。</font>
>
> 例如，我们可以将数组 [5, 4, 3, 2, 1]中的元素按照从小到大的顺序排序，输出： 1，2，3，4，5

![1649485239057](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649485239057.png)

![1649485249334](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649485249334.png)

# JavaScript函数

## 一、函数的概念

> 在 JS 里面，可能会定义非常多的相同代码或者功能相似的代码，这些代码可能需要大量重复使用。
>
> 虽然 for循环语句也能实现一些简单的重复操作，但是比较具有局限性，此时我们就可以使用 JS 中的函数。
>
> <font color='red'>**函数：就是封装了一段可被重复调用执行的代码块。通过此代码块可以实现大量代码的重复使用。**  </font>

## 二、函数的使用

> 函数在使用时分为两步：<font color='red'>声明函数和调用函数。</font>

### 1、声明函数

![1649513142474](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649513142474.png)

> - **function 是声明函数的关键字,必须小写**
> - 由于函数一般是为了实现某个功能才定义的， 所以通常我们将函数名命名为动词，比如 getSum  

### 2、调用函数

![1649513188357](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649513188357.png)

> - 调用的时候千万不要忘记添加小括号
> - 口诀：**函数不调用，自己不执行。**

<font color='blue'>注意：声明函数本身并不会执行代码，只有调用函数时才会执行函数体代码。</font>

### 3、封装函数

> <font color='red'>**函数的封装是把一个或者多个功能通过函数的方式封装起来，对外只提供一个简单的函数接口**</font>
>
> 简单理解：封装类似于将电脑配件整合组装到机箱中 ( 类似快递打包）  

![1649513287710](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649513287710.png)

#### 案例：利用函数计算1-100之间的累加和 

![1649513311059](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649513311059.png)

## 三、函数的参数

### 1、形参和实参

在<font color='red'>声明函数</font>时，可以**在函数名称后面的小括号中添加一些参数，这些参数被称为<font color='blue'>形参</font>，**而<font color='green'>**在调用该函数时，同样也需要传递相应的参数，这些参数被称为实参。**</font>

![1649513382414](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649513382414.png)

> **参数的作用：在函数内部某些值不能固定，我们可以通过参数在调用函数时传递不同的值进去。**

![1649513426670](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649513426670.png)

#### 案例：利用函数求任意两个数的和 

![1649513446370](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649513446370.png)

### 2、函数参数的传递过程

![1649513467509](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649513467509.png)

> 1. <font color='red'>调用的时候实参值是传递给形参的</font>
> 2. 形参简单理解为：不用声明的变量
> 3. **实参和形参的多个参数之间用逗号（,）分隔**

### 3、函数形参和实参个数不匹配问题

![1649513537893](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649513537893.png)

![1649513546428](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649513546428.png)

<font color='red'>注意：在JavaScript中，形参的默认值是**undefined**。</font>

#### 小结

> 1. 函数可以带参数也可以不带参数
> 2. <font color='red'>声明函数的时候，函数名括号里面的是形参，形参的默认值为 undefined</font>
> 3. <font color='blue'>调用函数的时候，函数名括号里面的是实参</font>
> 4. 多个参数中间用逗号分隔
> 5. 形参的个数可以和实参个数不匹配，但是结果不可预计，我们尽量要匹配

## 四、函数的返回值

### 1、return

有的时候，我们会希望函数将值返回给调用者，此时通过使用 return 语句就可以实现。

return 语句的语法格式如下：

![1649513684366](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649513684366.png)

> 1. <font color='red'>在使用 return 语句时，函数会停止执行，并返回指定的值</font>
> 2. 如果函数没有 return ，返回的值是 undefined

例如，声明了一个sum()函数，该函数的返回值为666，其代码如下：

![1649513722240](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649513722240.png)

#### 案例 1：利用函数求任意两个数的最大值 

![1649513736436](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649513736436.png)

#### 案例 2：利用函数求任意一个数组中的最大值 

求数组 [5,2,99,101,67,77] 中的最大数值。

![1649513758950](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649513758950.png)

### 2、return终止函数

<font color='red'>return 语句之后的代码不被执行。</font>

![1649513809763](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649513809763.png)

> <font color='green'>return 只能返回一个值。如果用逗号隔开多个值，以最后一个为准。</font>

![1649513831233](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649513831233.png)

#### 案例：创建一个函数，实现两个数之间的加减乘除运算，并将结果返回 

![1649513843537](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649513843537.png)

> 函数都是有返回值的
>
> 1. 如果有return 则返回 return 后面的值
> 2. <font color='blue'>**如果没有return 则返回 undefined** </font>

### 3、break ,continue ,return 的区别

> - break ：**结束当前的循环体**（如 for、while）
> - continue ：**跳出本次循环，继续执行下次循环**（如 for、while）
> - return ：<font color="purple">不仅可以退出循环，还能够返回 return 语句中的值，同时还可以结束当前的函数体内的代码</font>

## 五、arguments的使用！！！

当我们**不确定有多少个参数传递的时候**，**可以用 arguments 来获取**。<font color='red'>在 JavaScript 中，arguments 实际上它是当前函数的一个内置对象。</font><font color='blue'>**所有函数都内置了一个 arguments 对象，arguments 对象中存储了传递的所有实参。**</font>

> arguments展示形式是一个伪数组，因此可以进行遍历。**伪数组具有以下特点：**
>
> 1. 具有 length 属性
> 2. 按索引方式储存数据
> 3. **不具有数组的 push , pop 等方法**

#### 案例：利用函数求任意个数的最大值 

![1649514061548](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649514061548.png)

## 六、函数案例

案例 1： 利用函数封装方式，翻转任意一个数组

![1649514109543](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649514109543.png)

案例 2： 利用函数封装方式，对数组排序 -- 冒泡排序

![1649514121561](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649514121561.png)

**案例 3： 判断闰年**

要求：输入一个年份，判断是否是闰年（闰年：能被4整除并且不能被100整数，或者能被400整除）

![1649514157893](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649514157893.png)

#### 函数可以调用另外一个函数

> 因为每个函数都是独立的代码块，用于完成特殊任务，因此经常会用到函数相互调用的情况。

![1649514191228](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649514191228.png)

案例 4： 用户输入年份，输出当前年份2月份的天数

如果是闰年，则2月份是 29天， 如果是平年，则2月份是 28天

## 七、函数的两种声明方式

### 1、自定义函数方式(命名函数)

<font color='red'>利用函数关键字 function 自定义函数方式。</font>

![1649514266807](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649514266807.png)

> - 因为有名字，所以也被称为命名函数
> - <font color='red'>调用函数的代码既可以放到声明函数的前面，也可以放在声明函数的后面</font>

### 2、函数表达式方式(匿名函数）

利用函数表达式方式的写法如下： 

![1649514310143](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649514310143.png)

> 1. **因为函数没有名字，所以也被称为匿名函**数
> 2. 这个<font color='green'>fn 里面存储的是一个函数 </font>
> 3. 函数表达式方式原理跟声明变量方式是一致的
> 4. <font color='blue'>**函数调用的代码必须写到函数体后面**</font>

# JavaScript作用域

## 一、作用域

通常来说，一段程序代码中所用到的名字并不总是有效和可用的，而限定这个名字的可用性的代码范围就是这个名字的作用域。<font color='red'>作用域的使用提高了程序逻辑的局部性，增强了程序的可靠性，减少了名字冲突。</font>

> JavaScript（es6前）中的作用域有两种：
>
> 1. 全局作用域
> 2. 局部作用域（函数作用域）

### 1、全局作用域

> <font color='hotpink'>作用于所有代码执行的环境(整个 script 标签内部)或者一个独立的 js 文件。</font>

### 2、局部作用域（函数作用域）

> <font color='green'>作用于函数内的代码环境，就是局部作用域。 因为跟函数有关系，所以也称为函数作用域。</font>

### 3、JS没有块级作用域

> <font color='blue'>**块作用域由 { } 包括。**</font>
>
> 在其他编程语言中（如 java、c#等），在 if 语句、循环语句中创建的变量，仅仅只能在本 if 语句、本循环语句中使用，如下面的Java代码：

![1649514629696](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649514629696.png)

**JS没有块级作用域（在ES6之前）**

![1649514677455](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649514677455.png)

## 二、变量的作用域

### 1、分类

> 在JavaScript中，根据作用域的不同，变量可以分为两种：
>
> 1. 全局变量
> 2. 局部变量

### 2、全局变量

- **在全局作用域下声明的变量叫做全局变量（在函数外部定义的变量）。**
- <font color='blue'>全局变量在代码的任何位置都可以使用</font>
- <font color='red'>在全局作用域下 var 声明的变量是全局变量</font>
- 特殊情况下，在函数内不使用 var 声明的变量也是全局变量（不建议使用）

### 3、局部变量

- **在局部作用域下声明的变量叫做局部变量（在函数内部定义的变量）**
- <font color='blue'>局部变量只能在该函数内部使用</font>
- <font color='red'>在函数内部 var 声明的变量是局部变量</font>
- 函数的形参实际上就是局部变量

### 4、全局变量和局部变量的区别

> 1. 全局变量：在任何一个地方都可以使用，<font color='red'>只有在浏览器关闭时才会被销毁，</font>因此比较占内存
> 2. 局部变量：<font color='red'>只在函数内部使用，当其所在的代码块被执行时，会被初始化；</font><font color='blue'>当代码块运行结束后，就会被销毁，因此更节省内存空间</font>

## 三、作用域链

- 只要是代码，就至少有一个作用域
- 写在函数内部的局部作用域
- 如果函数中还有函数，那么在这个作用域中就又可以诞生一个作用域
- <font color='red'>根据在内部函数可以访问外部函数变量的这种机制，</font><font color='green'>**用链式查找决定哪些数据能被内部函数访问，就称作作用域链**</font>

![1649515444217](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649515444217.png)

![1649515453736](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649515453736.png)

> <font color='orange'>**作用域链：采取就近原则的方式来查找变量最终的值。**</font>

# JavaScript预解析

## 一、预解析

![1649515646304](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649515646304.png)

<font color='red'>JavaScript 代码是由浏览器中的 JavaScript 解析器来执行的。</font>JavaScript 解析器在运行 JavaScript 代码的时候分为两步：**预解析和代码执行。**

> 1. <font color='orange'>预解析：在当前作用域下, JS 代码执行之前，浏览器会默认把带有 var 和 function 声明的变量在内存中进行提前声明或者定义。</font>
> 2. 代码执行： 从上到下执行JS语句。
>
> <font color='green'>**预解析只会发生在通过 var 定义的变量和 function 上。**</font>学习预解析能够让我们知道为什么在变量声明之前访问变量的值是 undefined，为什么在函数声明之前就可以调用函数。

## 二、变量预解析和函数预解析

### 1、变量预解析

<font color='red'>**预解析也叫做变量、函数提升。**</font>

<font color='purple'>变量提升： 变量的声明会被提升到当前作用域的最上面，变量的赋值不会提升。</font>

![1649515880580](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649515880580.png)

**结果为：undefined**

<font color='red'>原因：此时num会做预解析即变量提升，num的声明会提升到当前作用域的最上面，但变量赋值不会提升，为undefined</font>

### 2、函数预解析（函数提升）

<font color='blue'>函数提升： 函数的声明会被提升到当前作用域的最上面，但是不会调用函数。</font>

![1649515990523](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649515990523.png)

#### 解决函数表达式声明调用问题

![1649516016943](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649516016943.png)

#### 案例 1： 结果是几？

![1649516120750](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649516120750.png)

**输出：undefined**

#### 案例 2： 结果是几？

![1649516200549](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649516200549.png)

**输出：undefined、20**

#### 案例 3

![1649516268219](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649516268219.png)

**输出：undefined、9**

# JavaScript对象

## 一、对象

<font color='red'>对象是一个具体的事物</font>

> 在 JavaScript 中，<font color='red'>对象是一组无序的相关属性和方法的集合，</font>所有的事物都是对象，例如字符串、数值、数组、函数等。
>
> 对象是由属性和方法组成的。
>
> - 属性：**事物的特征**，在对象中用属性来表示（常用名词）
> - 方法：**事物的行为**，在对象中用方法来表示（常用动词）

![1649599347733](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649599347733.png)

### 为什么需要对象

<font color='red'>保存一个值时，可以使用变量，保存多个值（一组值）时，可以使用数组。</font>如果要保存一个人的完整信息呢？

例如，将“张三疯”的个人的信息保存在数组中的方式为：

![1649599423949](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649599423949.png)

**JS 中的对象表达结构更清晰，更强大。张三疯的个人信息在对象中的表达结构如下：**

![1649599446042](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649599446042.png)

## 二、创建对象

> 在 JavaScript 中，现阶段我们可以<font color='blue'>采用三种方式创建对象（object）</font>：
>
> 1. <font color='green'>利用字面量创建对象 </font>
> 2. <font color='blue'>利用 new Object 创建对象 </font>
> 3. <font color='orange'>利用构造函数创建对象</font> 

### 1、利用字面量创建对象

> <font color='purple'>对象字面量：就是花括号 { } 里面包含了表达这个具体事物（对象）的属性和方法。</font>
>
> <font color='red'>**{ } 里面采取键值对的形式表示** </font>
>
> - 键：相当于<font color='green'>属性名</font>
> - 值：相当于<font color='green'>属性值</font>，可以是任意类型的值（数字类型、字符串类型、布尔类型，函数类型等）

![1649599577527](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649599577527.png)

#### 对象的调用

> <font color='blue'>**对象里面的属性调用 : 对象.属性名**</font> ，这个小点 . 就理解为“ 的 ”  
>
> <font color='green'>对象里面属性的另一种调用方式 : **对象[‘属性名’]**，注意方括号里面的属性必须加引号</font>，我们后面会用      
>
> <font color='orange'>对象里面的方法调用：**对象.方法名()** </font>，注意这个方法名字后面一定加括号 

![1649599645646](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649599645646.png)

#### 变量、属性、函数、方法总结

> - 变量：单独声明赋值，单独存在
> - 属性：对象里面的变量称为属性，不需要声明，用来描述该对象的特征
> - 函数：单独存在的，通过“函数名()”的方式就可以调用
> - 方法：对象里面的函数称为方法，方法不需要声明，使用“对象.方法名()”的方式就可以调用，方法用来描述该对象的行为和功能。 

### 2、利用new Object创建对象

![1649599738247](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649599738247.png)

> **Object() ：第一个字母大写**   
>
> <font color='red'>**new Object() ：需要 new 关键字**</
>
> 使用的格式：<font color='orange'>对象.属性 =  值;   </font>  

### 3、利用构造函数创建对象

> **构造函数 ：是一种特殊的函数，主要用来初始化对象，即为对象成员变量赋初始值，**它总与 new 运算符一起使用。我们<font color='blue'>可以把对象中一些公共的属性和方法抽取出来，然后封装到这个函数里面。</font>
>
> 在 js 中，使用构造函数要时要注意以下两点：
>
> - 构造函数用于创建某一类对象，<font color='green'>其首字母要大写</font>
> - 构造函数要和 new 一起使用才有意义

![1649599841197](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649599841197.png)

注意：

1. 构造函数约定首字母大写。
2. <font color='red'>函数内的属性和方法前面需要添加 this，表示当前对象的属性和方法。</font>
3. <font color='orange'>构造函数中不需要 return 返回结果。</font>
4. 当我们创建对象的时候，必须用 new 来调用构造函数。

#### 构造函数和对象

> - 构造函数，如 Stars()，抽象了对象的公共部分，封装到了函数里面，它<font color='orange'>泛指某一大类（class）</font>
> - 创建对象，如 new Stars()，<font color='green'>特指某一个</font>，<font color='blue'>**通过 new 关键字创建对象的过程我们也称为对象实例化** </font>

## 三、new关键字

> <font color='red'>**new 在执行时会做四件事情：**</font>
>
> 1. <font color='red'>在内存中创建一个新的空对象。</font>
> 2. <font color='red'>让 this 指向这个新的对象。</font>
> 3. <font color='green'>执行构造函数里面的代码，给这个新对象添加属性和方法。</font>
> 4. <font color='blue'>返回这个新对象（所以构造函数里面不需要return）。</font>

## 四、遍历对象属性

> <font color='red'>**for...in 语句用于对数组或者对象的属性进行循环操作。**</font>
>
> 其语法如下：

![1649600106556](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649600106556.png)

语法中的变量是自定义的，它需要符合命名规范，通常我们会<font color='green'>将这个变量写为 k 或者 key。</font>

![1649600129160](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649600129160.png)

#### 小结：

> 1. 对象可以让代码结构更清晰
> 2. <font color='blue'>对象复杂数据类型object。</font>
> 3. <font color='red'>本质：对一组无序的相关属性和方法的集合。</font>
> 4. <font color='green'>构造函数泛指某一大类，</font>比如苹果，不管是红色苹果还是绿色苹果，都统称为苹果。
> 5. <font color='green'>对象实例特指一个事物，</font>比如这个苹果、正在给你们讲课的pink老师等。
> 6. <font color='orange'>**for...in 语句用于对对象的属性进行循环操作。**</font>

# JavaScript内置对象

## 一、内置对象

> - <font color='red'>**JavaScript 中的对象分为3种：自定义对象 、内置对象、 浏览器对象**</font>
> - **前面两种对象是JS 基础 内容，属于 ECMAScript；**  第三个浏览器对象属于我们JS 独有的， 我们JS API 讲解
> - <font color='green'>**内置对象就是指 JS 语言自带的一些对象，这些对象供开发者使用，并提供了一些常用的或是最基本而必要的功能（属性和方法）**</font>
> - 内置对象最大的优点就是帮助我们快速开发
> - <font color='red'>JavaScript 提供了多个内置对象：**Math、 Date 、Array、String**等</font>

## 二、Math对象

<font color='green'>Math 对象不是构造函数，它具有数学常数和函数的属性和方法。</font>跟数学相关的运算（求绝对值，取整、最大值等）可以使用 Math 中的成员。

![1649600443752](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649600443752.png)

<font color='purple'>注意：上面的方法必须带括号</font>

### 1、随机数方法 random()

> <font color='orange'>random() 方法可以随机返回一个小数，其取值范围是 [0，1)，左闭右开 0 <= x < 1 </font>
>
> <font color='blue'>得到一个两数之间的随机整数，包括两个数在内</font>

![1649600549037](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649600549037.png)

## 三、日期对象

> 1. <font color='red'>Date 对象</font>和 Math 对象不一样，他**是一个构造函数，所以我们需要实例化后才能使用**
> 2. <font color='orange'>Date 实例用来处理日期和时间</font>

#### 1、Date方法的使用

#### 1.1 获取当前时间必须实例化

![1649600662095](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649600662095.png)

#### 1.2 Date() 构造函数的参数

> **如果括号里面有时间，就返回参数里面的时间。**
>
> 例如日期格式字符串为‘2019-5-1’，可以写成new Date('2019-5-1')  或者 new Date('2019/5/1')
>
> 1. <font color='green'>如果Date()不写参数，就返回当前时间</font>
> 2. <font color='blue'>如果Date()里面写参数，就返回括号里面输入的时间 </font>

### 2、日期格式化

![1649600739155](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649600739155.png)

### 3、获取日期的总的毫秒形式

- Date 对象是基于1970年1月1日（世界标准时间）起的毫秒数
- 为什么计算机起始时间从1970年开始?
- 我们经常利用总的毫秒数来计算时间，因为它更精确

![1649600787294](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649600787294.png)

#### 案例：倒计时效果

![1649600814630](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649600814630.png)

1. 核心算法：输入的时间减去现在的时间就是剩余的时间，即倒计时 ，但是不能拿着时分秒相减，比如 05 分减去25分，结果会是负数的。
2. 用时间戳来做。**用户输入时间总的毫秒数减去现在时间的总的毫秒数，得到的就是剩余时间的毫秒数。**
3. **把剩余时间总的毫秒数转换为天、时、分、秒 （时间戳转换为时分秒）**

> 转换公式如下： 
>
> - d = parseInt(总秒数/ 60/60 /24);    //  计算天数
> - h = parseInt(总秒数/ 60/60 %24)   //   计算小时
> - m = parseInt(总秒数 /60 %60 );     //   计算分数
> - s = parseInt(总秒数%60);               //   计算当前秒数 

## 四、数组对象

### 1、数组对象的创建

创建数组对象的两种方式

1. 字面量方式
2. <font color='red'>new Array()</font>

### 2、检测是否为数组

> <font color='blue'>**instanceof 运算符，可以判断一个对象是否属于某种类型**</font>
>
> <font color='green'>Array.isArray()用于判断一个对象是否为数组</font>，isArray() 是 HTML5 中提供的方法	 

![1649600977726](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649600977726.png)

### 3、数组的方法

![1649600996173](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649600996173.png)

#### 3.1 筛选数组

有一个包含工资的数组[1500, 1200, 2000, 2100, 1800]，要求把数组中工资超过2000的删除，剩余的放到新数组里面

![1649601034053](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649601034053.png)

#### 3.2 数组排序

![1649601056900](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649601056900.png)

![1649601061746](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649601061746.png)

#### 3.3 数组的索引方法

![1649601076603](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649601076603.png)

##### 数组去重（重点案例）

> 有一个数组[‘c’, ‘a’, ‘z’, ‘a’, ‘x’, ‘a’, ‘x’, ‘c’, ‘b’]，要求去除数组中重复的元素。

案例分析：

- 目标：把旧数组里面不重复的元素选取出来放到新数组中，重复的元素只保留一个，放到新数组中去重。
- 核心算法：我们遍历旧数组，然后拿着旧数组元素去查询新数组，如果该元素在新数组里面没有出现过，我们就添加，否则不添加。
- 我们怎么知道该元素没有存在？  <font color='green'>利用新数组.indexOf(数组元素)  如果返回时 -1 就说明新数组里面没有该元素  </font>

![1649601229192](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649601229192.png)

#### 3.4 数组转换为字符串

![1649601242602](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649601242602.png)

#### 3.5 其他方法

![1649601267178](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649601267178.png)

slice() 和 splice()  目的基本相同，建议同学们重点看下 splice()

### splice()

1. 删除-用于删除元素，两个参数，第一个参数（要删除第一项的位置），第二个参数（要删除的项数） 

2. 插入-向数组指定位置插入任意项元素。三个参数，第一个参数（插入位置），第二个参数（0），第三个参数（插入的项） 

3. 替换-向数组指定位置插入任意项元素，同时删除任意数量的项，三个参数。第一个参数（起始位置），第二个参数（删除的项数），第三个参数（插入任意数量的项）
   示例：

1、<font color='hotpink'>删除功能，第一个参数为第一项位置，第二个参数为要删除几个。</font>

array.splice(index,num)，返回值为删除内容，array为结果值。

![1650706195996](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650706195996.png)

 2、插入功能， 第一个参数（插入位置），<font color='hotpink'>**第二个参数（0）**</font>，第三个参数（插入的项）

array.splice(index,0,insertValue)，返回值为空数组，array值为最终结果值 

![1650706271072](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650706271072.png)

 3、<font color='hotpink'>替换功能， 第一个参数（起始位置），**第二个参数（删除的项数）**，第三个参数（插入任意数量的项）</font>

array.splice(index,num,insertValue)，返回值为删除内容，array为结果值。 

![1650706339525](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650706339525.png)

#### 检查JavaScript数组是否为空的方法

使用**Array.isArray()方法**和**array.length属性**

### reduce

reduce() 方法接收一个函数作为累加器，reduce 为数组中的每一个元素依次执行回调函数，不包括数组中被删除或从未被赋值的元素。 

> 语法：**arr.reduce(callback,[initialValue])**
>
> callback:函数中包含四个参数
>
> - previousValue （上一次调用回调返回的值，或者是提供的初始值（initialValue））
> - currentValue （数组中当前被处理的元素）
> - index （当前元素在数组中的索引)
> - array （调用的数组）
> - initialValue （作为第一次调用 callback 的第一个参数。）

![1651235660932](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651235660932.png)

<font color='hotpink'>0表示的是默认第一次调用回调函数的初始参数。</font>如果是1的话结果就会变成16。

![1651235797551](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651235797551.png)

## 五、字符串对象

### 1、基本包装类型

> 为了方便操作基本数据类型，<font color='red'>JavaScript 还提供了三个特殊的引用类型：String、Number和 Boolean。</font>
>
> <font color='blue'>基本包装类型就是把简单数据类型包装成为复杂数据类型，这样基本数据类型就有了属性和方法。</font>

按道理<font color='green'>基本数据类型是没有属性和方法的，而对象才有属性和方法，</font>但上面代码却可以执行，这是因为 js 会把基本数据类型包装为复杂数据类型，其执行过程如下：

![1649601380215](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649601380215.png)

### 2、字符串的不可变

> <font color='red'>**指的是里面的值不可变**</font>，虽然看上去可以改变内容，但其实是地址变了，<font color='green'>内存中新开辟了一个内存空间。</font>

![1649601487338](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649601487338.png)

### 3、根据字符返回位置

> **字符串所有的方法，都不会修改字符串本身(字符串是不可变的)，操作完成会返回一个新的字符串。**

![1649601525425](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649601525425.png)

#### 案例：返回字符位置

> 查找字符串"abcoefoxyozzopp"中所有o出现的位置以及次数

> 1. 核心算法：先查找第一个o出现的位置
> 2. 然后，只要indexOf 返回的结果不是 -1 就继续往后查找
> 3. 因为indexOf 只能查找到第一个，所以后面的查找，利用第二个参数，当前索引加1，从而继续查找 

### 4、根据位置返回字符！！！

![1649601624944](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649601624944.png)

#### 案例：返回字符位置

> 判断一个字符串 'abcoefoxyozzopp' 中出现次数最多的字符，并统计其次数。

> - 核心算法：利用 charAt(）遍历这个字符串
> - 把每个字符都存储给对象， 如果对象没有该属性，就为1，如果存在了就 +1
> - 遍历对象，得到最大值和该字符 

判断一个字符串 'abcoefoxyozzopp' 中出现次数最多的字符，并统计其次数。

对象 o {  }

### 5、字符串操作方法！！！

![1649601700861](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649601700861.png)

### 6、replace()

> <font color='red'>**replace() 方法用于在字符串中用一些字符替换另一些字符。**</font>

其使用格式如下：  

![1649601763802](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649601763802.png)

### 7、split()

> <font color='blue'>**split()方法用于切分字符串，它可以将字符串切分为数组。在切分完毕之后，返回的是一个新数组。**</font>

例如下面代码：  

![1649601831719](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649601831719.png)

#### 其他方法

> 1. toUpperCase() 	//转换大写
> 2. toLowerCase() 	//转换小写

# JavaScript 简单类型与复杂类型

## 一、简单类型与复杂类型

> <font color='red'>简单类型又叫做基本数据类型或者值类型，复杂类型又叫做引用类型。</font>
>
> - 值类型：简单数据类型/基本数据类型，<font color='blue'>在存储时变量中存储的是值本身，因此叫做值类型  </font><font color='red'>string ，number，boolean，undefined，null</font>
>
> - <font color='green'>引用类型：复杂数据类型，**在存储时变量中存储的仅仅是地址（引用），因此叫做引用数据类型**</font>
> - **通过 new 关键字创建的对象（系统对象、自定义对象），如 Object、Array、Date等**

### 堆和栈

<font color='blue'>堆栈空间分配区别：</font>

- 1、栈（操作系统）：由操作系统自动分配释放存放函数的参数值、局部变量的值等。其操作方式类似于数据结构中的栈；

<font color='green'>简单数据类型存放到栈里面</font>

- 2、堆（操作系统）：存储复杂类型(对象)，一般由程序员分配释放，若程序员不释放，由垃圾回收机制回收。

<font color='green'>复杂数据类型存放到堆里面</font>

![1649602073425](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649602073425.png)

<font color='red'>注意：JavaScript中没有堆栈的概念，通过堆栈的方式，可以让大家更容易理解代码的一些执行方式，便于将来学习其他语言。</font>

### 简单类型的内存分配

> - **值类型（简单数据类型）： string ，number，boolean，undefined，null**
> - <font color='blue'>**值类型变量的数据直接存放在变量（栈空间）中**</font>

![1649602203328](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649602203328.png)

### 复杂类型的内存分配

> - <font color='red'>引用类型（复杂数据类型）：通过 new 关键字创建的对象（系统对象、自定义对象），如 Object、Array、Date等</font>
> - <font color='blue'>**引用类型变量（栈空间）里存放的是地址，真正的对象实例存放在堆空间中**</font>

![1649602260037](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649602260037.png)

### 简单类型传参

函数的形参也可以看做是一个变量，**当我们把一个值类型变量作为参数传给函数的形参时，其实是把变量在栈空间里的值复制了一份给形参，那么在方法内部对形参做任何修改，都不会影响到的外部变量。**

![1649602298300](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649602298300.png)

### 复杂类型传参

**函数的形参也可以看做是一个变量，当我们把引用类型变量传给形参时，其实是把变量在栈空间里保存的<font color='red'>堆地址</font>复制给了形参，<font color='blue'>形参和实参其实保存的是同一个堆地址，所以操作的是同一个对象。</font>**

![1649602360232](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649602360232.png)

# 表单验证

为了保证用户提交的信息都是正确的，保证系统的安全性，验证是必不可少的，验证一般分为两种方式。

- 客户端验证：<font color='red'>直接在客户端执行JS进行验证，验证的过程中和服务器端没有任何的交互</font>
- 服务器端验证：页面将验证信息传回服务器端，服务器端进行验证，并将验证的结果发送回客户端

> /**
>
> ​    \* 判断是否是正整数
>
> ​    \* @param value 需要判断的值
>
> ​    \* @return {boolean} 返回true是正整数,false则不是正整数
>
> ​    */
>
>    function isInteger(value) {
>
> ​    // 判断是否是整数，最好不要使用isNaN方法，因为该方法会把数后面加一个小数点也判断为数字
>
> ​    var reg = /^([0-9]?||[1-9][0-9]*)$/
>
> ​    return reg.test(value)
>
>    }
>
> 
>
>    /**
>
> ​    \* 判断是否超出count位小数
>
> ​    \* @param value 需要判断的值
>
> ​    \* @param count 小数位数,count最小值为1,如果传入的count小于1,则默认为1
>
> ​    \* @return {boolean} 返回true未超出count位小数,返回false则是超出了count小数
>
> ​    */
>
>    function isDecimal(value, count) {
>
> ​    var scope = count < 1 ? 1 : '1,' + count
>
> ​    var reg
>
> ​    if (value.indexOf('.') > 0) {
>
> ​     // 当使用构造函数创造正则对象时，需要常规的字符转义规则（在前面加反斜杠 \）
>
> ​     // 当n = 2时,以下等价于:var reg=/^([1-9]\d+||[0-9])[.]\d{1,2}$/;
>
> ​     reg = new RegExp('^([1-9]\\d+||[0-9])[.]\\d{' + scope + '}$')
>
> ​    } else {
>
> ​     reg = new RegExp('^\\d+$')
>
> ​    }
>
> ​    return reg.test(value)
>
>    }
>
> 
>
>    /**
>
> ​    \* 判断是否是邮箱格式
>
> ​    \* @param value 需要判断的值
>
> ​    \* @return {boolean} 返回true是邮箱格式,返回false则不是
>
> ​    */
>
>    function isEmail(value) {
>
> ​    var reg = /^\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*$/
>
> ​    return reg.test(value)
>
>    }
>
> 
>
>    /**
>
> ​    \* 校验是否中文名称组成
>
> ​    \* @param str 需要判断的字符串
>
> ​    \* @return {boolean} 返回true表示str是由中文名称组成,返回false则不是
>
> ​    */
>
>    function isChina(str) {
>
> ​    var reg = /^[\u4E00-\u9FA5]{2,4}$/
>
> ​    return reg.test(str)
>
>    }
>
> 
>
>    /**
>
> ​    \* 检测浏览器是否支持svg
>
> ​    \* @return {boolean} 返回true支持,返回false不支持
>
> ​    */
>
>    function isSupportSVG() {
>
> ​    var SVG_NS = 'http://www.w3.org/2000/svg'
>
> ​    return (
>
> ​     !!document.createElementNS &&
>
> ​     !!document.createElementNS(SVG_NS, 'svg').createSVGRect
>
> ​    )
>
>    }
>
> 
>
>    /**
>
> ​    \* 检测浏览器是否支持canvas
>
> ​    \* @return {boolean} 返回true支持,返回false不支持
>
> ​    */
>
>    function isSupportCanvas() {
>
> ​    return !!document.createElement('canvas').getContext
>
>    }
>
> 
>
>    /**
>
> ​    \* 检测是否是微信浏览器
>
> ​    \* @return {boolean} 返回true是,返回false不是
>
> ​    */
>
>    function isWeiXinClient() {
>
> ​    var ua = navigator.userAgent.toLowerCase
>
> ​    var res = !!ua.match(/MicroMessenger/i) == 'micromessenger'
>
> ​    return res
>
>    }
>
> 
>
>    /**
>
> ​    \* 检测是否移动端及浏览器内核
>
> ​    */
>
>    var browser = {
>
> ​    versions: function () {
>
> ​     var u = navigator.userAgent
>
> ​     return {
>
> ​      trident: u.indexOf('Trident') > -1, //IE内核
>
> ​      presto: u.indexOf('Presto') > -1, //opera内核
>
> ​      webKit: u.indexOf('AppleWebKit') > -1, //苹果、谷歌内核
>
> ​      gecko: u.indexOf('Firefox') > -1, //火狐内核
>
> ​      Geckomobile: !!u.match(/AppleWebKit.*Mobile.*/), //是否移动终端
>
> ​      ios: !!u.match(/\(i[^;]+;( U;)? CPU.+Mac OS X/), //ios
>
> ​      android: u.indexOf('Android') > -1 || u.indexOf('Linux') > -1, //android
>
> ​      iPhone: u.indexOf('iPhone') > -1, //iPhone
>
> ​      iPad: u.indexOf('iPad') > -1, //iPad
>
> ​      webApp: u.indexOf('Safari') > -1, //Safari
>
> ​     }
>
> ​    },
>
>    }
>
> 
>
>    /**
>
> ​    \* 检测是否电脑端/移动端
>
> ​    *
>
> ​    */
>
>    var browser = {
>
> ​    versions: function () {
>
> ​     var u = navigator.userAgent,
>
> ​      app = navigator.appVersion
>
> ​     var sUserAgent = navigator.userAgent
>
> ​     return {
>
> ​      trident: u.indexOf('Trident') > -1,
>
> ​      presto: u.indexOf('Presto') > -1,
>
> ​      isChrome: u.indexOf('chrome') > -1,
>
> ​      isSafari: !u.indexOf('chrome') > -1 && /webkit|khtml/.test(u),
>
> ​      isSafari3:
>
> ​       !u.indexOf('chrome') > -1 &&
>
> ​       /webkit|khtml/.test(u) &&
>
> ​       u.indexOf('webkit/5') != -1,
>
> ​      webKit: u.indexOf('AppleWebKit') > -1,
>
> ​      gecko: u.indexOf('Gecko') > -1 && u.indexOf('KHTML') == -1,
>
> ​      mobile: !!u.match(/AppleWebKit.*Mobile.*/),
>
> ​      ios: !!u.match(/\(i[^;]+;( U;)? CPU.+Mac OS X/),
>
> ​      android: u.indexOf('Android') > -1 || u.indexOf('Linux') > -1,
>
> ​      iPhone: u.indexOf('iPhone') > -1,
>
> ​      iPad: u.indexOf('iPad') > -1,
>
> ​      iWinPhone: u.indexOf('Windows Phone') > -1,
>
> ​     }
>
> ​    },
>
>    }
>
> 
>
>    /**
>
> ​    \* 检测浏览器内核
>
> ​    */
>
>    function getInternet() {
>
> ​    if (navigator.userAgent.indexOf('MSIE') > 0) {
>
> ​     return 'MSIE' //IE浏览器
>
> ​    }
>
> ​    if ((isFirefox = navigator.userAgent.indexOf('Firefox') > 0)) {
>
> ​     return 'Firefox' //Firefox浏览器
>
> ​    }
>
> ​    if ((isSafari = navigator.userAgent.indexOf('Safari') > 0)) {
>
> ​     return 'Safari' //Safan浏览器
>
> ​    }
>
> ​    if ((isCamino = navigator.userAgent.indexOf('Camino') > 0)) {
>
> ​     return 'Camino' //Camino浏览器
>
> ​    }
>
> ​    if ((isMozilla = navigator.userAgent.indexOf('Gecko/') > 0)) {
>
> ​     return 'Gecko' //Gecko浏览器
>
> ​    }
>
>    }

