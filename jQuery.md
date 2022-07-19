# jQuery入门

## 一、jQuery概述

### 1、JavaScript库

仓库：可以把很多东西放到这个仓库里面。找东西只需要到仓库里面查找到就可以了。

> JavaScript库：即 library，是一个封装好的特定的集合（方法和函数）。从封装一大堆函数的角度理解库，就是在这个库中，封装了很多预先定义好的函数在里面，比如动画animate、hide、show，比如获取元素等。
>
> 简单理解： 就是一个JS 文件，里面对我们原生js代码进行了封装，存放到里面。这样我们可以快速高效的使用这些封装好的功能了。
>
> 比如 jQuery，就是为了快速方便的操作DOM，里面基本都是函数（方法）。

**常见的JavaScript库**

> - jQuery
> - Prototype
> - YUI
> - Dojo
> - Ext JS
> - 移动端的zepto

这些库都是对原生 JavaScript 的封装，内**部都是用 JavaScript 实现的**，我们主要学习的是 jQuery。

### 2、jQuery的概念

jQuery 是一个快速、简洁的 JavaScript 库，其设计的宗旨是“write Less，Do More”，即倡导写更少的代码，做更多的事情。

j 就是 JavaScript；   Query 查询； 意思就是查询js，**把js中的DOM操作做了封装，我们可以快速的查询使用里面的功能。**

> <font color='red'> jQuery 封装了 JavaScript 常用的功能代码，优化了 DOM 操作、事件处理、动画设计和 Ajax 交互。 </font>
>
> 学习jQuery本质： 就是学习调用这些函数（方法）。
>
> jQuery 出现的目的是加快前端人员的开发速度，我们可以非常方便的调用和使用它，从而提高开发效率。

![1649897937349](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649897937349.png)

### 3、jQuery的优点

1. 轻量级。核心文件才几十kb，不会影响页面加载速度
2. 跨浏览器兼容。基本兼容了现在主流的浏览器
3. 链式编程、隐式迭代
4. 对事件、样式、动画支持，大大简化了DOM操作
5. 支持插件扩展开发。有着丰富的第三方的插件，例如：树形菜单、日期控件、轮播图等
6. 免费、开源

## 二、jQuery的基本使用

官网地址： https://jquery.com/

各个版本的下载：https://code.jquery.com/

### 1、jQuery使用步骤

> 1. 引入 jQuery 文件
>
> 2. 使用即可

### 2、jQuery的入口函数

![1649898199582](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649898199582.png)

![1649898207811](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649898207811.png)

> 1. 等着 DOM 结构渲染完毕即可执行内部代码，不必等到所有外部资源加载完成，jQuery 帮我们完成了封装。
> 2. 相当于原生 js 中的 DOMContentLoaded。
> 3. 不同于原生 js 中的 load 事件是等页面文档、外部的 js 文件、css文件、图片加载完毕才执行内部代码。
> 4. 更推荐使用第一种方式。

![1650362651342](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650362651342.png)

### 3、jQuery的顶级对象$

> 1. <font color='red'>**$ 是 jQuery 的别称**</font>
>
>    <font color='red'>在代码中可以使用 jQuery 代替 $</font>
>
>    但一般为了方便，通常都直接使用 $ 。
>
> 2. <font color='red'>$ 是jQuery 的顶级对象， 相当于原生JavaScript中的 window。</font>
>
>    把元素利用$包装成jQuery对象，就可以调用jQuery 的方法。

### 4、jQuery对象和DOM对象

> 1. 用原生 JS 获取来的对象就是 DOM 对象
>
> 2. jQuery 方法获取的元素就是 jQuery 对象。
>
> 3. <font color='red'>jQuery 对象本质是： 利用$对DOM 对象包装后产生的对象（伪数组形式存储）。</font>

![1650362728618](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650362728618.png)

注意：

<font color='blue'>只有 jQuery 对象才能使用 jQuery 方法，DOM 对象则使用原生的 JavaScirpt 方法。</font>

> <font color='green'>DOM 对象与 jQuery 对象之间是可以相互转换的。</font>
>
> 因为原生js 比 jQuery 更大，原生的一些属性和方法 jQuery没有给我们封装。要想使用这些属性和方法需要把jQuery对象转换为DOM对象才能使用。

**1. DOM 对象转换为 jQuery 对象： $(DOM对象)**

![1649898415736](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649898415736.png)

**2. jQuery 对象转换为 DOM 对象（两种方式）**

![1649898428567](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649898428567.png)

![1649898432983](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649898432983.png)

![1650362755456](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650362755456.png)

# jQuery常用API

## 一、jQuery选择器

### 1、jQuery基础选择器

原生 JS 获取元素方式很多，很杂，而且兼容性情况不一致，因此 jQuery 给我们做了封装，使获取元素统一标准。

![1649898500529](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649898500529.png)

![1649898505256](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649898505256.png)

### 2、jQuery层级选择器

![1649898542909](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649898542909.png)

<font color='red'>**jQuery 设置样式**</font>

![1649898564175](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649898564175.png)

### 3、隐式迭代***

<font color='red'>遍历内部 DOM 元素（伪数组形式存储）的过程就叫做隐式迭代。</font>

简单理解：给匹配到的所有元素进行循环遍历，执行相应的方法，而不用我们再进行循环，简化我们的操作，方便我们调用。

### 4、jQuery筛选选择器

![1649898619126](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649898619126.png)

![1650362838253](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650362838253.png)

### 5、jQuery筛选方法

![1649898626962](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649898626962.png)

重点记住： parent()  children()  find()  siblings()  eq()

![1650362814470](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650362814470.png)

### 6、排他思想

> 想要多选一的效果，<font color='blue'>排他思想：当前元素设置样式，其余的兄弟元素清除样式。</font>

![1649898691393](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649898691393.png)

### 7、链式编程

链式编程是为了节省代码量，看起来更优雅。

![1649898722784](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649898722784.png)

**使用链式编程一定注意是哪个对象执行样式.**

## 二、jQuery样式操作

### 1、操作CSS方法

jQuery 可以使用 css 方法来修改简单元素样式； 也可以操作类，修改多个样式。

**1. 参数只写属性名，则是返回属性值**

![1649898775888](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649898775888.png)

**2.  <font color='red'>参数是属性名，属性值，逗号分隔</font>，是设置一组样式，属性必须加引号，值如果是数字可以不用跟单位和引号**

![1649898793898](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649898793898.png)

**3.  参数可以是对象形式，方便设置多组样式。属性名和属性值用冒号隔开， 属性可以不用加引号，**

![1649898814844](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649898814844.png)

![1650362867063](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650362867063.png)

### 2、设置类样式方法

作用等同于以前的 classList，可以操作类样式， 注意操作类里面的参数不要加点。

**1. 添加类**

![1649898871841](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649898871841.png)

**2.  移除类**

![1649898882840](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649898882840.png)

**3.  切换类**

![1649898893060](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649898893060.png)

### 3、类操作与className区别

> <font color='red'>原生 JS 中 className 会覆盖元素原先里面的类名。</font>
>
> <font color='blue'>jQuery 里面类操作只是对指定类进行操作，不影响原先的类名。</font>

## 三、jQuery效果

jQuery 给我们封装了很多动画效果，最为常见的如下：

![1649898962962](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649898962962.png)

### 1、显示隐藏效果

#### 1. 显示语法规范

![1649898985750](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649898985750.png)

##### 显示参数

> - 参数都可以省略， 无动画直接显示。
> - **speed：三种预定速度之一的字符串(“slow”,“normal”, or “fast”)或表示动画时长的毫秒数值(如：1000)。**
> - <font color='red'>easing：(Optional) 用来指定切换效果，默认是“swing”，可用参数“linear”。</font>
> - fn:  回调函数，在动画完成时执行的函数，每个元素执行一次。

#### 2. 隐藏语法规范

![1649899069847](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649899069847.png)

##### 隐藏参数

> - 参数都可以省略， 无动画直接显示。
> - speed：三种预定速度之一的字符串(“slow”,“normal”, or “fast”)或表示动画时长的毫秒数值(如：1000)。
> - easing：(Optional) 用来指定切换效果，默认是“swing”，可用参数“linear”。
> - fn:  回调函数，在动画完成时执行的函数，每个元素执行一次。

#### 3. 切换语法规范

![1649899130110](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649899130110.png)

##### 切换参数

> - <font color='red'>参数都可以省略， 无动画直接显示。</font>
> - speed：三种预定速度之一的字符串(“slow”,“normal”, or “fast”)或表示动画时长的毫秒数值(如：1000)。
> - easing：(Optional) 用来指定切换效果，默认是“swing”，可用参数“linear”。
> - fn:  回调函数，在动画完成时执行的函数，每个元素执行一次。
> - <font color='blue'>建议：平时一般不带参数，直接显示隐藏即可。</font>

### 2、滑动效果

#### 1. 下滑效果语法规范

![1649899198868](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649899198868.png)

##### 下滑效果参数

> - 参数都可以省略。
> - speed:三种预定速度之一的字符串(“slow”,“normal”, or “fast”)或表示动画时长的毫秒数值(如：1000)。
> - easing:(Optional) 用来指定切换效果，默认是“swing”，可用参数“linear”。
> - fn:  回调函数，在动画完成时执行的函数，每个元素执行一次。

#### 2. 上滑效果语法规范

![1649899241672](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649899241672.png)

##### 上滑效果参数

> - 参数都可以省略。
> - speed：三种预定速度之一的字符串(“slow”,“normal”, or “fast”)或表示动画时长的毫秒数值(如：1000)。
> - easing：(Optional) 用来指定切换效果，默认是“swing”，可用参数“linear”。
> - fn:  回调函数，在动画完成时执行的函数，每个元素执行一次。

#### 3. 滑动切换效果语法规范

![1649899289534](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649899289534.png)

##### 滑动切换效果参数

> - 参数都可以省略。
> - speed：三种预定速度之一的字符串(“slow”,“normal”, or “fast”)或表示动画时长的毫秒数值(如：1000)。
> - easing：(Optional) 用来指定切换效果，默认是“swing”，可用参数“linear”。
> - fn:  回调函数，在动画完成时执行的函数，每个元素执行一次。

### 3、事件切换

![1649899344933](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649899344933.png)

1. over：鼠标移到元素上要触发的函数（相当于mouseenter）
2. out：鼠标移出元素要触发的函数（相当于mouseleave）
3. <font color='red'>如果只写一个函数，则鼠标经过和离开都会触发它</font>

### 4、动画队列及其停止排队方法

#### 1. 动画或效果队列

动画或者效果一旦触发就会执行，如果多次触发，就造成多个动画或者效果排队执行。

#### 2. 停止排队

![1649899414327](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649899414327.png)

1. <font color='red'>stop() 方法用于停止动画或效果。</font>
2. **注意： stop() 写到动画或者效果的前面， 相当于停止结束上一次的动画。**

### 5、淡入淡出效果

#### 1. 淡入效果语法规范

![1649899455952](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649899455952.png)

##### 淡入效果参数

> - 参数都可以省略。
> - speed：三种预定速度之一的字符串(“slow”,“normal”, or “fast”)或表示动画时长的毫秒数值(如：1000)。
> - easing：(Optional) 用来指定切换效果，默认是“swing”，可用参数“linear”。
> - fn:  回调函数，在动画完成时执行的函数，每个元素执行一次。

#### 2. 淡出效果语法规范

![1649899509755](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649899509755.png)

##### 淡出效果参数

> - 参数都可以省略。
> - speed：三种预定速度之一的字符串(“slow”,“normal”, or “fast”)或表示动画时长的毫秒数值(如：1000)。
> - easing：(Optional) 用来指定切换效果，默认是“swing”，可用参数“linear”。
> - fn:  回调函数，在动画完成时执行的函数，每个元素执行一次。

#### 3. 淡入淡出切换效果语法规范

![1649899562238](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649899562238.png)

##### 淡入淡出切换效果参数

> - 参数都可以省略。
> - speed：三种预定速度之一的字符串(“slow”,“normal”, or “fast”)或表示动画时长的毫秒数值(如：1000)。
> - easing：(Optional) 用来指定切换效果，默认是“swing”，可用参数“linear”。
> - fn:  回调函数，在动画完成时执行的函数，每个元素执行一次。

#### 4. 渐进方式调整到指定的不透明度

![1649899605811](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649899605811.png)

##### 效果参数

> - <font color='red'>opacity 透明度必须写，取值 0~1 之间。</font>
> - <font color='orange'>speed：三种预定速度之一的字符串(“slow”,“normal”, or “fast”)或表示动画时长的毫秒数值(如：1000)。必须写</font>
> - easing：(Optional) 用来指定切换效果，默认是“swing”，可用参数“linear”。
> - fn:  回调函数，在动画完成时执行的函数，每个元素执行一次。

### 6、自定义动画 animate

#### 1、语法

![1649899674600](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649899674600.png)

#### 2、参数

> 1. <font color='red'>params：想要更改的样式属性，以对象形式传递，必须写。</font> 属性名可以不用带引号， 如果是复合属性则需要采取驼峰命名法 borderLeft。其余参数都可以省略。
> 2. speed：三种预定速度之一的字符串(“slow”,“normal”, or “fast”)或表示动画时长的毫秒数值(如：1000)。
> 3. easing：(Optional) 用来指定切换效果，默认是“swing”，可用参数“linear”。
> 4. fn:  回调函数，在动画完成时执行的函数，每个元素执行一次。

![1650362921670](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650362921670.png)

## 四、jQuery属性操作

### 1、设置或获取元素固有属性值 prop()

<font color="red">**所谓元素固有属性就是元素本身自带的属性，比如 <a> 元素里面的 href ，比如 <input> 元素里面的 type。** </font>

#### 1. 获取属性语法

![1649899835369](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649899835369.png)

#### 2. 设置属性语法

![1649899848676](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649899848676.png)

### 2、设置或获取元素自定义属性值 attr()

<font color='red'>用户自己给元素添加的属性，我们称为自定义属性。 比如给 div 添加 index =“1”。 </font>

#### 1. 获取属性语法

![1649899881589](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649899881589.png)

#### 2. 设置属性语法

![1649899892039](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649899892039.png)

<font color='green'>**该方法也可以获取 H5 自定义属性**</font>

### 3、数据缓存 data()

<font color='red'>data() 方法可以在指定的元素上存取数据，并不会修改 DOM 元素结构。一旦页面刷新，之前存放的数据都将被移除。 </font>

#### 1. 附加数据语法

![1649900723256](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649900723256.png)

#### 2. 获取数据语法

![1649900742499](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649900742499.png)

**同时，还可以读取 HTML5 自定义属性  data-index ，得到的是数字型**



## ![1650362974488](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650362974488.png)五、jQuery内容文本值

<font color='red'>主要针对元素的内容还有表单的值操作。</font>

### 1. 普通元素内容 html()（ 相当于原生inner HTML)

![1649900822105](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649900822105.png)

![1649900828282](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649900828282.png)

### 2. 普通元素文本内容 text()   (相当与原生 innerText)

![1649900840294](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649900840294.png)

![1649900844805](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649900844805.png)

### 3. 表单的值 val()（ 相当于原生value)

![1649900858739](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649900858739.png)

![1649900862845](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649900862845.png)

![1650362998893](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650362998893.png)

![1650363018612](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650363018612.png)

## 六、jQuery元素操作

<font color='orange'>主要是遍历、创建、添加、删除元素操作。</font>

### 1、遍历元素

jQuery 隐式迭代是对同一类元素做了同样的操作。<font color='red'> 如果想要给同一类元素做不同操作，就需要用到遍历。</font>

#### 语法1

![1649900927403](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649900927403.png)

> 1. <font color='blue'>each() 方法遍历匹配的每一个元素。主要用DOM处理。 each 每一个</font>
>
> 2. 里面的回调函数有2个参数：  index 是每个元素的索引号;  **demEle 是每个DOM元素对象，不是jquery对象**
>
> 3. <font color='red'>**所以要想使用jquery方法，需要给这个dom元素转换为jquery对象  $(domEle)**</font>

![1650363107516](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650363107516.png)

#### 语法2

![1649901019361](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649901019361.png)

> 1. <font color='red'>$.each()方法可用于遍历任何对象。主要用于数据处理，比如数组，对象</font>
>
> 2. 里面的函数有2个参数：  index 是每个元素的索引号;  element  遍历内容

![1650363128451](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650363128451.png)

### 2、创建元素

#### 语法

![1649901059974](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649901059974.png)

动态的创建了一个 `<li>  `

### 3、添加元素

#### 1. 内部添加

![1649901089054](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649901089054.png)

<font color='blue'>把内容放入匹配元素内部最后面，</font>类似原生 appendChild。

![1649901100545](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649901100545.png)

<font color='blue'>把内容放入匹配元素内部最前面。</font>

#### 2. 外部添加

![1649901128216](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649901128216.png)

![1649901134351](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649901134351.png)

> <font color='red'>内部添加元素，生成之后，它们是父子关系。</font>
>
> <font color='red'>外部添加元素，生成之后，他们是兄弟关系。</font>

### 4、删除元素

![1649901163151](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649901163151.png)

![1649901168673](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649901168673.png)

![1649901174190](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649901174190.png)

> <font color='red'>remove 删除元素本身。</font>
>
> <font color='blue'>empt() 和  html('''') 作用等价，都可以删除元素里面的内容，只不过 html 还可以设置内容。</font>

![1650363205171](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650363205171.png)

## 七、jQuery尺寸、位置操作

### 1、jQuery尺寸

![1649901239758](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649901239758.png)

> 1. <font color='red'>以上参数为空，则是获取相应值，返回的是数字型。</font>
> 2. <font color='blue'>如果参数为数字，则是修改相应值。</font>
> 3. 参数可以不必写单位。

![1650363231490](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650363231490.png)

### 2、jQuery位置

位置主要有三个： <font color='red'>offset()、position()、scrollTop()/scrollLeft()</font>

#### 1. offset() 设置或获取元素偏移

> 1. <font color='red'>offset() 方法设置或返回被选元素相对于文档的偏移坐标，跟父级没有关系。</font>
> 2. **该方法有2个属性 left、top 。offset().top  用于获取距离文档顶部的距离，offset().left 用于获取距离文档左侧的距离。**
> 3. <font color='blue'>可以设置元素的偏移：offset({ top: 10, left: 30 });</font>

#### 2. position() 获取元素偏移

> 1. <font color='red'>position() 方法用于返回被选元素相对于带有定位的父级偏移坐标，如果父级都没有定位，则以文档为准。</font>
> 2. **该方法有2个属性 left、top。position().top 用于获取距离定位父级顶部的距离，position().left 用于获取距离定位父级左侧的距离。**
> 3. <font color='blue'>该方法只能获取。</font>

#### 3. scrollTop()/scrollLeft() 设置或获取元素被卷去的头部和左侧

> 1. <font color='red'>scrollTop() 方法设置或返回被选元素被卷去的头部。</font>
> 2. 不跟参数是获取，参数为不带单位的数字则是设置被卷去的头部。



# jQuery事件

## 一、jQuery事件注册

### 1、单个事件注册

#### 语法：

![1649901496719](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649901496719.png)

![1649901501493](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649901501493.png)

其他事件和原生基本一致。

![1650363329242](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650363329242.png)

<font color='red'>比如mouseover、mouseout、blur、focus、change、keydown、keyup、resize、scroll 等</font>

## 二、jQuery事件处理

### 1、事件处理 on() 绑定事件

<font color='orange'>**on() 方法在匹配元素上绑定一个或多个事件的事件处理函数**</font>

#### 语法：

![1649901568452](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649901568452.png)

> 1. <font color='red'>events:一个或多个用空格分隔的事件类型，如"click"或"keydown" 。</font>
>
> 2. selector: 元素的子元素选择器 。
>
> 3. fn:回调函数 即绑定在元素身上的侦听函数。 

#### on()优势

<font color='red'>1、可以绑定多个事件，多个处理事件处理程序。 </font>

![1649901609372](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649901609372.png)

![1650363303239](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650363303239.png)

如果事件处理程序相同 

![1649901629801](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649901629801.png)

<font color='red'>2、可以事件委派操作 。**事件委派的定义就是，把原来加给子元素身上的事件绑定在父元素身上，就是把事件委派给父元素。**</font>

![1649901673575](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649901673575.png)

在此之前有bind(), live() delegate()等方法来处理事件绑定或者事件委派，最新版本的请用on替代他们。

##### 动态创建的元素用on()绑定事件

<font color='red'>3、**动态创建的元素，click() 没有办法绑定事件， on() 可以给动态生成的元素绑定事件** ！！！</font>

![1649901745732](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649901745732.png)

![1649901753309](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649901753309.png)

![1650363364466](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650363364466.png)

### 2、事件处理 off() 解绑事件

<font color='green'>off() 方法可以移除通过 on() 方法添加的事件处理程序。</font>

![1649901791342](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649901791342.png)

<font color='blue'>**如果有的事件只想触发一次， 可以使用 one() 来绑定事件。**</font>

![1650363394116](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650363394116.png)

### 3、自动触发事件 trigger() 

有些事件希望自动触发, 比如轮播图自动播放功能跟点击右侧按钮一致。<font color='red'>可以利用定时器自动触发右侧按钮点击事件，不必鼠标点击触发。</font>

![1649901829112](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649901829112.png)

![1649901893745](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649901893745.png)

![1649901898427](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649901898427.png)

![1649901921267](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649901921267.png)

<font color='red'>triggerHandler模式不会触发元素的默认行为，这是和前面两种的区别。</font>

### 4、one()事件

![1650363438195](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650363438195.png)

## 三、jQuery事件对象

事件被触发，就会有事件对象的产生。

![1649901965298](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649901965298.png)

> <font color='red'>阻止默认行为：event.preventDefault()   或者 return  false </font>
>
> <font color='blue'>阻止冒泡： event.stopPropagation()    </font>  

![1650363482249](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650363482249.png)

# jQuery其他方法

## 一、jQuery对象拷贝

<font color='red'>如果想要把某个对象拷贝（合并） 给另外一个对象使用，此时可以使用 **$.extend() 方法**</font>

#### 语法：

![1649902086029](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649902086029.png)

> 1. <font color='red'>deep：如果设为true 为深拷贝， 默认为false  浅拷贝 </font>
>
> 2. target：要拷贝的目标对象
>
> 3. object1：待拷贝到第一个对象的对象。 
>
> 4. objectN：待拷贝到第N个对象的对象。
>
> 5. <font color='red'>浅拷贝是把被拷贝的对象复杂数据类型中的地址拷贝给目标对象，修改目标对象会影响被拷贝对象。</font>
>
> 6. <font color='red'>深拷贝，前面加true， 完全克隆(拷贝的对象,而不是地址)，修改目标对象不会影响被拷贝对象。</font>

## 二、多库共存

jQuery使用$作为标示符

随着jQuery的流行,其他 js 库也会用这$作为标识符， 这样一起使用会引起冲突。

<font color='red'>需要一个解决方案，让jQuery 和其他的js库不存在冲突，可以同时存在，这就叫做多库共存。</font>

### jQuery解决方案

1. 把里面的 $ 符号 统一改为 jQuery。 比如 jQuery(''div'')

2. jQuery 变量规定新的名称：

   ~~~
   $.noConflict()   
   var xx = $.noConflict();
   ~~~

## 三、jQuery插件

jQuery 功能比较有限，想要更复杂的特效效果，可以借助于 jQuery 插件完成。 

**注意：这些插件也是依赖于jQuery来完成的，所以必须要先引入jQuery文件，因此也称为 jQuery 插件。**

jQuery 插件常用的网站：

1. jQuery 插件库  http://www.jq22.com/     

2. jQuery 之家   http://www.htmleaf.com/ 

jQuery 插件使用步骤：

1. 引入相关文件。（jQuery 文件 和 插件文件）    

2. 复制相关html、css、js (调用插件)。

jQuery 插件演示：

1. 瀑布流

2. 图片懒加载（图片使用延迟加载在可提高网页下载速度。它也能帮助减轻服务器负载）

   当我们页面滑动到可视区域，再显示图片。

   我们使用jquery 插件库  EasyLazyload。 注意，此时的js引入文件和js调用必须写到 DOM元素（图片）最后面

3. 全屏滚动（fullpage.js）
         gitHub： https://github.com/alvarotrigo/fullPage.js
         中文翻译网站： http://www.dowebok.com/demo/2014/77/

### boostrap

bootstrap JS 插件：

<font color='red'>bootstrap 框架也是依赖于 jQuery 开发的，因此里面的 js插件使用 ，也必须引入jQuery 文件。</font>

