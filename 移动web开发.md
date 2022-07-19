# 流式布局

## 一、移动端基础

![1650026014232](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650026014232.png)

![1650026023135](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650026023135.png)

### 1、视口

<font color='red'>视口（viewport）就是浏览器显示页面内容的屏幕区域。</font> <font color='blue'>**视口可以分为布局视口、视觉视口和理想视口**</font>

#### 布局视口 layout viewport

一般移动设备的浏览器都默认设置了一个布局视口，用于解决早期的PC端页面在手机上显示的问题。

iOS, Android基本都将这个视口分辨率设置为 980px，所以PC上的网页大多都能在手机上呈现，只不过元
素看上去很小，一般默认可以通过手动缩放网页。

![1650026131282](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650026131282.png)

#### 视觉视口 visual viewport

> 字面意思，<font color='red'>它是用户正在看到的网站的区域。注意：是网站的区域。</font>
>
> 我们可以通过缩放去操作视觉视口，但不会影响布局视口，布局视口仍保持原来的宽度。

![1650026160876](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650026160876.png)

#### 理想视口 ideal viewport

> 为了使网站在移动端有最理想的浏览和阅读宽度而设定
>
> 理想视口，对设备来讲，是最理想的视口尺寸
>
> <font color='red'>需要手动添写meta视口标签通知浏览器操作</font>
>
> meta视口标签的主要目的：**布局视口的宽度应该与理想视口的宽度一致，简单理解就是设备有多宽，我们布**
> **局的视口就多宽**

#### meta视口标签

![1650026233690](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650026233690.png)

![1650026273271](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650026273271.png)

##### 标准的viewpost设置

> - 视口宽度和设备保持一致
> - 视口的默认缩放比例1.0
> - 不允许用户自行缩放
> - 最大允许的缩放比例1.0
> - 最小允许的缩放比例1.0

## 二、二倍图

### 1、物理像素&物理像素比

物理像素点指的是屏幕显示的最小颗粒，是物理真实存在的。这是厂商在出厂时就设置好了,比如苹果6\7\8 是 750* 1334

我们开发时候的1px 不是一定等于1个物理像素的

PC端页面，1个px 等于1个物理像素的，但是移动端就不尽相同

<font color='blue'>**一个px的能显示的物理像素点的个数，称为物理像素比或屏幕像素比**</font>

PC端 和 早前的手机屏幕 / 普通手机屏幕: 1CSS像素 = 1 物理像素的

**Retina（视网膜屏幕）是一种显示技术，可以将把更多的物理像素点压缩至一块屏幕里，从**
**而达到更高的分辨率，并提高屏幕显示的细腻程度。**

![1650026413513](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650026413513.png)

### 2、多倍图

对于一张 50px * 50px 的图片,在手机 Retina 屏中打开，按照刚才的物理像素比会放大倍数，这样会造成图片模糊

<font color='red'>在标准的viewport设置中，使用倍图来提高图片质量，解决在高清设备中的模糊问题</font>

通常使用二倍图， 因为iPhone 6\7\8 的影响,但是现在还存在3倍图4倍图的情况，这个看实际开发公司需求

背景图片 注意缩放问题

![1650026457313](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650026457313.png)

### 3、背景缩放 background-size

> background-size 属性规定背景图像的尺寸

![1650026480042](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650026480042.png)

单位： 长度|百分比|cover|contain;

<font color='red'>**cover把背景图像扩展至足够大，以使背景图像完全覆盖背景区域。**</font>

**contain把图像图像扩展至最大尺寸，以使其宽度和高度完全适应内容区域**

## 三、移动端开发选择

### 1、移动端主流方案

![1650026564577](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650026564577.png)

#### 1.1 单独移动端页面（主流）

通常情况下，<font color='red'>网址域名前面加 m(mobile) 可以打开移动端</font>。通过判断设备，如果是移动设备打开，则跳到移动端页面。

![1650026631233](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650026631233.png)

#### 1.2 响应式兼容PC移动端

![1650026721171](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650026721171.png)

## 四、移动端技术解决方案

### 1、移动端浏览器

移动端浏览器基本以 webkit 内核为主，因此我们就考虑webkit兼容性问题。

我们可以放心使用 H5 标签和 CSS3 样式。

<font color='red'>同时我们浏览器的私有前缀我们只需要考虑添加 webkit 即可</font>

![1650026773391](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650026773391.png)

### 2、CSS初始化 normalize.css

![1650026791938](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650026791938.png)

**官网地址：http://necolas.github.io/normalize.css/**

### 3、CSS3 盒子模型 box-sizing!!!

**传统模式宽度计算：盒子的宽度 = CSS中设置的width + border + padding**

<font color='red'>CSS3盒子模型： 盒子的宽度 = CSS中设置的宽度width 里面包含了 border 和 padding</font>

也就是说，我们的<font color='orange'>**CSS3中的盒子模型， padding 和 border 不会撑大盒子了**</font>

![1650026874642](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650026874642.png)

![1650026882670](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650026882670.png)

#### 特殊样式

![1650026899923](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650026899923.png)

## 五、移动端常见布局

![1650026938088](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650026938088.png)

### 1、流式布局（百分比布局）

<font color='red'>**流式布局，就是百分比布局，也称非固定像素布局。**</font>

<font color='blue'>通过盒子的宽度设置成百分比来根据屏幕的宽度来进行伸缩，不受固定像素的限制，内容向两侧填充。</font>

流式布局方式是移动web开发使用的比较常见的布局方式。

![1650026977486](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650026977486.png)

> - max-width 最大宽度 （max-height 最大高度）
> - min-width 最小宽度 （min-height 最小高度）

![1650027158281](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650027158281.png)

![1650027165768](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650027165768.png)

![1650027172654](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650027172654.png)

![1650027180665](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650027180665.png)

![1650027188308](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650027188308.png)

![1650027194323](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650027194323.png)

![1650027206712](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650027206712.png)

# flex布局

## 一、flex布局体验

![1650027299277](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650027299277.png)

![1650027305537](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650027305537.png)

![1650027314540](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650027314540.png)

![1650027323161](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650027323161.png)

## 二、flex布局原理

**flex 是 flexible Box 的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性，任何一个容器都可以**
**指定为 flex 布局。**

<font color='red'>**当我们为父盒子设为 flex 布局以后，子元素的 float、clear 和 vertical-align 属性将失效。**</font>

<font color='blue'>**伸缩布局 = 弹性布局 = 伸缩盒布局 = 弹性盒布局 =flex布局**</font>

### 1、布局原理

<font color='red'>采用 Flex 布局的元素，称为 Flex 容器（flex container），简称"容器"。</font><font color='blue'>它的所有子元素自动成为容器成员，称为 Flex 项目（flex item），简称"项目"。</font>

![1650027430593](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650027430593.png)

> <font color='red'>**flex布局原理：就是通过给父盒子添加flex属性，来控制子盒子的位置和排列方式**</font>

## 三、flex 布局父项常见属性

> 1. <font color='red'>flex-direction：设置主轴的方向</font>
> 2. <font color='red'>justify-content：设置主轴上的子元素排列方式</font>
> 3. <font color='blue'>flex-wrap：设置子元素是否换行</font>
> 4. <font color='red'>align-content：设置侧轴上的子元素的排列方式（多行）</font>
> 5. <font color='orange'>align-items：设置侧轴上的子元素排列方式（单行）</font>
> 6. <font color='green'>flex-flow：复合属性，相当于同时设置了 flex-direction 和 flex-wrap</font>

### flex-direction 设置主轴的方向！！！

#### 1. 主轴与侧轴

在 flex 布局中，是分为主轴和侧轴两个方向，同样的叫法有 ： 行和列、x 轴和y 轴

1. 默认主轴方向就是 x 轴方向，水平向右
2. 默认侧轴方向就是 y 轴方向，水平向下

> <font color='red'>flex-direction 属性决定主轴的方向（即项目的排列方向）</font>
>
> 注意： 主轴和侧轴是会变化的，就看 flex-direction 设置谁为主轴，剩下的就是侧轴。而<font color='red'>我们的子元素是跟着主轴来排列的</font>

![1650027638371](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650027638371.png)

### justify-content 设置主轴上的子元素排列方式！！！

<font color='red'>justify-content 属性定义了项目在主轴上的对齐方式</font>

注意： 使用这个属性之前一定要确定好主轴是哪个

![1650027676521](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650027676521.png)

### flex-wrap 设置子元素是否换行！！！

默认情况下，项目都排在一条线（又称”轴线”）上。<font color='red'>flex-wrap属性定义，flex布局中默认是不换行的。</font>

![1650027775976](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650027775976.png)

### align-items 设置侧轴上的子元素排列方式（单行 ）！！！

**该属性是控制子项在侧轴（默认是y轴）上的排列方式 在子项为单项（单行）的时候使用**

![1650027806367](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650027806367.png)

### align-content 设置侧轴上的子元素的排列方式（多行）！！！

**设置子项在侧轴上的排列方式 并且只能用于子项出现 换行 的情况（多行），在单行下是没有效果的。**

![1650027844362](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650027844362.png)

### align-content 和 align-items 区别

> 1. align-items 适用于单行情况下， 只有上对齐、下对齐、居中和 拉伸
> 2. align-content 适应于换行（多行）的情况下（单行情况下无效）， 可以设置 上对齐、 下对齐、居中、拉伸以及平均分配剩余空间等属性值。
>
> 总结就是单行找 align-items 多行找 align-content

![1650027883481](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650027883481.png)

### flex-flow

<font color='red'>**flex-flow 属性是 flex-direction 和 flex-wrap 属性的复合属性**</font>

![1650027946506](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650027946506.png)

> - flex-direction：设置主轴的方向
> - justify-content：设置主轴上的子元素排列方式
> - flex-wrap：设置子元素是否换行
> - align-content：设置侧轴上的子元素的排列方式（多行）
> - align-items：设置侧轴上的子元素排列方式（单行）
> - flex-flow：复合属性，相当于同时设置了 flex-direction 和 flex-wrap

## 四、flex 布局子项常见属性

> - flex 子项目占的份数
> - align-self 控制子项自己在侧轴的排列方式
> - order属性定义子项的排列顺序（前后顺序）

### flex 属性！！！

<font color='red'>flex 属性定义子项目分配剩余空间，用flex来表示占多少份数。</font>

![1650028042364](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650028042364.png)

### align-self 控制子项自己在侧轴上的排列方式

<font color='red'>align-self 属性允许单个项目有与其他项目不一样的对齐方式，可覆盖 align-items 属性。</font>

**默认值为 auto，表示继承父元素的 align-items 属性，如果没有父元素，则等同于 stretch。**

![1650028077520](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650028077520.png)

### order 属性定义项目的排列顺序

<font color='red'>数值越小，排列越靠前，默认为0。</font>

注意：和 z-index 不一样。

![1650028142964](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650028142964.png)

####  背景线性渐变

![1650028182118](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650028182118.png)

##### 语法1：

![1650028197326](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650028197326.png)

> <font color='blue'>**背景渐变必须添加浏览器私有前缀**</font>
>
> 起始方向可以是： 方位名词 或者 度数 ， 如果省略默认就是 top

# rem适配布局

## 一、rem基础

**rem (root em)是一个相对单位，类似于em，em是父元素字体大小。**

不同的是<font color='red'>rem的基准是相对于html元素的字体大小。</font>

比如，根元素（html）设置font-size=12px; 非根元素设置width:2rem; 则换成px表示就是24px。

**rem的优势：父元素文字大小可能不一致， 但是整个页面只有一个html，可以很好来控制整个页面的元素大小**

![1650028331876](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650028331876.png)

## 二、媒体查询

媒体查询（Media Query）是CSS3新语法。

- <font color='red'>使用 @media 查询，可以针对不同的媒体类型定义不同的样式</font>
- <font color='blue'>@media 可以针对不同的屏幕尺寸设置不同的样式</font>
- 当你重置浏览器大小的过程中，页面也会根据浏览器的宽度和高度重新渲染页面

目前针对很多苹果手机、Android手机，平板等设备都用得到多媒体查询

### 1、语法规范

![1650028392407](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650028392407.png)

> 1. <font color='red'>用 @media 开头 注意@符号</font>
> 2. mediatype 媒体类型
> 3. 关键字 and not only
> 4. media feature 媒体特性 必须有小括号包含

![1650028665856](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650028665856.png)

#### 1.1 mediatype 查询类型

<font color='green'>**将不同的终端设备划分成不同的类型，称为媒体类型**</font>

![1650028455805](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650028455805.png)

#### 1.2 关键字

<font color='red'>**关键字将媒体类型或多个媒体特性连接到一起做为媒体查询的条件。**</font>

> 1. and：可以将多个媒体特性连接到一起，相当于“且”的意思。
> 2. not：排除某个媒体类型，相当于“非”的意思，可以省略。
> 3. only：指定某个特定的媒体类型，可以省略。

#### 1.3 媒体特性

每种媒体类型都具体各自不同的特性，根据不同媒体类型的媒体特性设置不同的展示风格。我们暂且了解三个。
注意他们要加小括号包含：

![1650028533542](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650028533542.png)

![1650028545747](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650028545747.png)

![1650028560701](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650028560701.png)

![1650028571226](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650028571226.png)

![1650028710388](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650028710388.png)

![1650028745592](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650028745592.png)

### 2、引入资源（理解）

当样式比较繁多的时候，我们可以针对不同的媒体使用不同 stylesheets（样式表）。

**原理：就是直接在link中判断设备的尺寸，然后引用不同的css文件。**

![1650028787096](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650028787096.png)

![1650028803122](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650028803122.png)

## 三、less基础

> CSS 是一门非程序式语言，没有变量、函数、SCOPE（作用域）等概念。
>
> - CSS 需要书写大量看似没有逻辑的代码，CSS 冗余度是比较高的。
> - 不方便维护及扩展，不利于复用。
> - CSS 没有很好的计算能力
> - 非前端开发工程师来讲，往往会因为缺少 CSS 编写经验而很难写出组织良好且易于维护的 CSS 代码项目。

### 1、less介绍

<font color='red'>Less （Leaner Style Sheets 的缩写） 是一门 CSS 扩展语言，也成为CSS预处理器。</font>

做为 CSS 的一种形式的扩展，它并没有减少 CSS 的功能，而是在现有的 CSS 语法上，为CSS加入程序式语言的
特性。

它在 CSS 的语法基础之上，引入了变量，Mixin（混入），运算以及函数等功能，大大简化了 CSS 的编写，并且
降低了 CSS 的维护成本，就像它的名称所说的那样，Less 可以让我们用更少的代码做更多的事情。

Less中文网址： http://lesscss.cn/

**常见的CSS预处理器：Sass、Less、Stylus**

一句话：<font color='blue'>**Less 是一门 CSS 预处理语言，它扩展了CSS的动态特性。**</font>

![1650028896837](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650028896837.png)

### 2、less使用

![1650028915864](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650028915864.png)

#### Less变量

**变量是指没有固定的值，可以改变的。因为我们CSS中的一些颜色和数值等经常使用。**

![1650028972335](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650028972335.png)

> 1. <font color='red'>必须有@为前缀</font>
> 2. 不能包含特殊字符
> 3. 不能以数字开头
> 4. 大小写敏感

![1650028999046](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650028999046.png)

![1650029008169](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650029008169.png)

#### Less 编译

本质上，Less 包含一套自定义的语法及一个解析器，用户根据这些语法定义自己的样式规则，这些规则
最终会通过解析器，编译生成对应的 CSS 文件。

所以，我们需要把我们的 less文件，编译生成为css文件，这样我们的html页面才能使用。

![1650029068534](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650029068534.png)

#### Less 嵌套

![1650029083371](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650029083371.png)

**Less嵌套**

![1650029093688](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650029093688.png)

如果遇见 （交集|伪类|伪元素选择器）

1. <font color='red'>内层选择器的前面没有 & 符号，则它被解析为父选择器的后代；</font>
2. <font color='green'>**如果有 & 符号，它就被解析为父元素自身或父元素的伪类。**</font>

![1650029136886](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650029136886.png)

#### Less 运算！！！

任何数字、颜色或者变量都可以参与运算。就是Less提供了加（+）、减（-）、乘（*）、除（/）算术运算。

![1650029165014](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650029165014.png)

> 注意：
>
> 1. 乘号（*）和除号（/）的写法
> 2. 运算符中间左右有个空格隔开 1px + 5
> 3. 对于两个不同的单位的值之间的运算，**运算结果的值取第一个值的单位**
> 4. **如果两个值之间只有一个值有单位，则运算结果就取该单位**

## 四、rem适配方案

![1650029236344](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650029236344.png)

![1650029243700](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650029243700.png)

![1650029256546](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650029256546.png)

### 1、rem适配方案技术

![1650029281179](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650029281179.png)

#### rem 实际开发适配方案1

<font color='red'>**rem + 媒体查询 + less 技术**</font>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650029315973.png" alt="1650029315973" style="zoom:200%;" />

##### 动态设置 html 标签 font-size 大小

> ① 假设设计稿是750px
>
> ② 假设我们把整个屏幕划分为15等份（划分标准不一可以是20份也可以是10等份）
>
> ③ 每一份作为html字体大小，这里就是50px
>
> ④ 那么在320px设备的时候，字体大小为320/15 就是 21.33px
>
> ⑤ 用我们页面元素的大小 除以不同的 html 字体大小会发现他们比例还是相同的
>
> ⑥ 比如我们以 750为标准设计稿
>
> ⑦ 一个100*100像素的页面元素 在 750屏幕下， 就是 100 / 50 转换为rem 是 2rem * 2 rem 比例是 1比1
>
> ⑧ 320屏幕下， html 字体大小为 21.33 则 2rem = 42.66px 此时宽和高都是 42.66 但是 宽和高的比例还是 1比1
>
> ⑨ 但是已经能实现不同屏幕下 页面元素盒子等比例缩放的效果

##### 元素大小取值方法

> ① 最后的公式：<font color='green'> **页面元素的rem值 = 页面元素值（px） / （屏幕宽度 / 划分的份数）**</font>
>
> ② <font color='red'>屏幕宽度/划分的份数 就是 html font-size 的大小</font>
>
> ③ 或者： <font color='red'>页面元素的rem值 = 页面元素值（px） / html font-size 字体大小</font>

### 苏宁网首页案例制作

![1650029417082](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650029417082.png)

![1650029424224](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650029424224.png)

![1650029440600](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650029440600.png)

![1650029446554](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650029446554.png)

![1650029455489](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650029455489.png)

![1650029466600](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650029466600.png)

### 2、rem适配方案2

#### rem适配方案flexible.js

![1650029493904](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650029493904.png)

![1650029501139](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650029501139.png)

![1650029507850](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650029507850.png)

![1650029519944](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650029519944.png)

![1650029526082](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650029526082.png)

![1650029534886](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650029534886.png)

# 响应式布局

## 一、响应式开发

### 1、响应式开发原理

<font color='red'>就是使用媒体查询针对不同宽度的设备进行布局和样式的设置，从而适配不同设备的目的。</font>

![1650030070267](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650030070267.png)

### 2、响应式布局容器

<font color='red'>响应式需要一个父级做为布局容器，来配合子级元素来实现变化效果。</font>

**原理就是在不同屏幕下，通过媒体查询来改变这个布局容器的大小，再改变里面子元素的排列方式和大小，从而实现不同屏幕下，看到不同的页面布局和样式变化。**

#### 案例-响应式导航

![1650030138084](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650030138084.png)

![1650030270060](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650030270060.png)

## 二、Bootstrap前端开发框架

### 1、Bootstrap简介

Bootstrap 来自 Twitter（推特），是目前最受欢迎的前端框架。Bootstrap 是基于 HTML、CSS 和 JAVASCRIPT 的，它简洁灵活，使得 Web 开发更加快捷。

<font color='red'>框架：顾名思义就是一套架构，它有一套比较完整的网页功能解决方案，而且控制权在框架本身，有预制样式库、组件和插件。使用者要按照框架所规定的某种规范进行开发。</font>

**Bootstrap官方中文文档**

 [Bootstrap v3 中文文档 · Bootstrap 是最受欢迎的 HTML、CSS 和 JavaScript 框架，用于开发响应式布局、移动设备优先的 WEB 项目。 | Bootstrap 中文网 (bootcss.com)](https://v3.bootcss.com/) 

![1650030391213](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650030391213.png)

![1650030399157](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650030399157.png)

### 2、Bootstrap使用

Bootstrap 使用四步曲： <font color='red'>1. 创建文件夹结构 2. 创建 html 骨架结构 3. 引入相关样式文件 4. 书写内容</font>

#### 创建文件夹结构

![1650030454052](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650030454052.png)

#### 创建html骨架结构

![1650030483711](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650030483711.png)

#### 引入相关样式

![1650030500296](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650030500296.png)

![1650030506696](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650030506696.png)

### 3、布局容器

<font color='red'>**Bootstrap 需要为页面内容和栅格系统包裹一个 .container 容器，它提供了两个作此用处的类。**</font>

![1650030540876](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650030540876.png)

## 三、Bootstrap栅格系统

栅格系统英文为“grid systems”,也有人翻译为“网格系统”，<font color='red'>它是指将页面布局划分为等宽的列，然后通过列数的定义来模块化页面布局。</font>

Bootstrap 提供了一套响应式、移动设备优先的流式栅格系统，随着屏幕或视口（viewport）尺寸的增加，系统会
自动分为最多12列。

### 1、栅格选项参数

栅格系统用于通过一系列的行（row）与列（column）的组合来创建页面布局，你的内容就可以放入这些创建好的布局中。

![1650070885789](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650070885789.png)

> - 按照不同屏幕划分为1~12 等份
> - 行（row） 可以去除父容器作用15px的边距
> - xs-extra small：超小； sm-small：小； md-medium：中等； lg-large：大；
> - 列（column）大于 12，多余的“列（column）”所在的元素将被作为一个整体另起一行排列
> - 每一列默认有左右15像素的 padding
> - 可以同时为一列指定多个设备的类名，以便划分不同份数 例如 class="col-md-4 col-sm-6"

### 2、列嵌套

栅格系统内置的栅格系统将内容再次嵌套。简单理解就是一个列内再分成若干份小列。我们可以通过添加一个新的 .row 元素和一系列 .col-sm-* 元素到已经存在的 .col-sm-* 元素内。

![1650070991673](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650070991673.png)

![1650071001394](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650071001394.png)

### 3、列偏移

<font color='red'>使用 .col-md-offset-* 类可以将列向右侧偏移。这些类实际是通过使用 * 选择器为当前元素增加了左侧的边距（margin）。</font>

![1650071043229](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650071043229.png)

### 4、列排序

通过使用 .col-md-push-* 和 .col-md-pull-* 类就可以很容易的改变列（column）的顺序。

![1650071140161](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650071140161.png)

### 5、响应式工具

为了加快对移动设备友好的页面开发工作，<font color='red'>利用媒体查询功能，</font>并使用这些工具类可以方便的针对不同设备展示
或隐藏页面内容。

![1650071265034](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650071265034.png)

