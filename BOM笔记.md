# BOM（浏览器对象模型）

## 一、BOM概述

B<font color='red'>OM（Browser Object Model）即浏览器对象模型，它提供了独立于内容而与浏览器窗口进行交互的对象，其核心对象是 window。</font>

**BOM 由一系列相关的对象构成，并且每个对象都提供了很多方法与属性。**

BOM 缺乏标准，JavaScript 语法的标准化组织是 ECMA，DOM 的标准化组织是 W3C，BOM 最初是Netscape 浏览器标准的一部分。

![1649733547727](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649733547727.png)

### BOM的构成

![1649733571168](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649733571168.png)

> <font color='red'>window 对象是浏览器的顶级对象，它具有双重角色。</font>
>
> 1. 它是 JS 访问浏览器窗口的一个接口。
> 2. <font color='blue'>它是一个全局对象。定义在全局作用域中的变量、函数都会变成 window 对象的属性和方法。</font>
>
> 在调用的时候可以省略 window，前面学习的对话框都属于 window 对象方法，如 alert()、prompt() 等。
>
> 注意：window下的一个特殊属性 window.name

## 二、window对象的常见事件

### 1、窗口加载事件

![1649733646010](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649733646010.png)

> <font color='red'>**window.onload 是窗口 (页面）加载事件，当文档内容完全加载完成会触发该事件(包括图像、脚本文件、CSS 文件等)，就调用的处理函数。**</font>
>
> 注意：
> 1. 有了 window.onload 就可以把 JS 代码写到页面元素的上方，因为 **onload 是等页面内容全部加载完毕，再去执行处理函数。**
> 2. <font color='red'>window.onload 传统注册事件方式 只能写一次，如果有多个，会以最后一个 window.onload 为准。</font>
>
> 3. 如果使用 addEventListener 则没有限制

![1649733715793](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649733715793.png)

DOMContentLoaded 事件触发时，仅当DOM加载完成，不包括样式表，图片，flash等等。

Ie9以上才支持

如果页面的图片很多的话, 从用户访问到onload触发可能需要较长的时间, 交互效果就不能实现，必然影响用户的体验，此时用 DOMContentLoaded 事件比较合适。

### 2、调整窗口大小事件

![1649733742229](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649733742229.png)

> <font color='red'>window.onresize 是调整窗口大小加载事件，当触发时就调用的处理函数。</font>
>
> 注意：
>
> 1. 只要窗口大小发生像素变化，就会触发这个事件。
>
> 2. 我们经常利用这个事件完成响应式布局。<font color='blue'> window.innerWidth 当前屏幕的宽度</font>

## 三、定时器

window 对象给我们提供了 2 个非常好用的方法-定时器。

- setTimeout() 
- setInterval()  

### 1、setTimeout()定时器

![1649733814242](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649733814242.png)

> <font color='orange'>**setTimeout() 方法用于设置一个定时器，该定时器在定时器到期后执行调用函数。**</font>
>
> 注意：
>
> 1. **window 可以省略。**
> 2. 这个调用函数可以直接写函数，或者写函数名或者采取字符串‘函数名()'三种形式。第三种不推荐
> 3. 延迟的毫秒数省略默认是 0，如果写，必须是毫秒。
>
> 4. 因为定时器可能有很多，所以我们<font color='blue'>经常给定时器赋值一个标识符。</font>

<font color='red'>setTimeout()  这个调用函数我们也称为回调函数 callback</font>

**普通函数是按照代码顺序直接调用。而这个函数，需要等待时间，时间到了才去调用这个函数，因此称为回调函数。**

简单理解： 回调，就是回头调用的意思。上一件事干完，再回头再调用这个函数。

以前我们讲的   element.onclick = function(){}   或者  element.addEventListener(“click”, fn);   里面的 函数也是回调函数。

#### 停止setTimeout定时器

![1649733954033](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649733954033.png)

<font color='green'>clearTimeout()方法取消了先前通过调用 setTimeout() 建立的定时器。</font>

注意：

1. window 可以省略。

2. 里面的参数就是<font color='blue'>定时器的标识符 。</font>

### 2、setInterval()定时器

![1649734009629](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649734009629.png)

> <font color='red'>setInterval() 方法重复调用一个函数，**每隔这个时间**，就去调用一次回调函数。</font>
>
> 注意：
> 1. window 可以省略。
> 2. 这个调用函数可以直接写函数，或者写函数名或者采取字符串 '函数名()'  三种形式。
> 3. 间隔的毫秒数省略默认是 0，如果写，必须是毫秒，表示每隔多少毫秒就自动调用这个函数。
> 4. 因为定时器可能有很多，所以我们经常<font color='blue'>给定时器赋值一个标识符。</font>
>
> 5. <font color='red'>第一次执行也是间隔毫秒数之后执行，之后每隔毫秒数就执行一次。</font>

#### 停止setInterval定时器

![1649734079188](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649734079188.png)

> <font color='red'>clearInterval()方法取消了先前通过调用 setInterval()建立的定时器。</font>
>
> 注意：
>
> 1. window 可以省略。
>
> 2. 里面的参数就是定时器的标识符 。

### 3、this

this的指向在函数定义的时候是确定不了的，只有函数执行的时候才能确定this到底指向谁，<font color='red'>**一般情况下this的最终指向的是那个调用它的对象**</font>

现阶段，我们先了解一下几个this指向
- <font color='green'>全局作用域或者普通函数中this指向全局对象window</font>（<font color='blue'>注意定时器里面的this指向window</font>）
- <font color='red'>方法调用中谁调用this指向谁</font>
- <font color='orange'>构造函数中this指向构造函数的实例</font>

## 四、JS执行队列

### 1、JS是单线程

**JavaScript 语言的一大特点就是单线程，**也就是说，<font color='red'>同一个时间只能做一件事</font>。这是因为 Javascript 这门脚本语言诞生的使命所致——JavaScript 是为处理页面中用户的交互，以及操作 DOM 而诞生的。比如我们对某个 DOM 元素进行添加和删除操作，不能同时进行。 应该先进行添加，之后再删除。

<font color='orange'>单线程就意味着，所有任务需要排队，前一个任务结束，才会执行后一个任务。</font>这样所导致的问题是： 如果 JS 执行的时间过长，这样就会造成页面的渲染不连贯，导致页面渲染加载阻塞的感觉。

![1649734511337](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649734511337.png)

![1649734519832](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649734519832.png)

![1649734564716](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649734564716.png)

![1649734577249](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649734577249.png)

### 2、同步和异步

为了解决这个问题，利用多核 CPU 的计算能力，HTML5 提出 <font color='blue'>Web Worker </font>标准，<font color='red'>允许 JavaScript 脚本创建多个线程。于是，JS 中出现了同步和异步。</font>

#### 同步

> 前一个任务结束后再执行后一个任务，程序的执行顺序与任务的排列顺序是一致的、同步的。比如做饭的同步做法：我们要烧水煮饭，等水开了（10分钟之后），再去切菜，炒菜。

#### 异步

> 你在做一件事情时，因为这件事情会花费很长时间，在做这件事的同时，你还可以去处理其他事情。比如做饭的异步做法，我们在烧水的同时，利用这10分钟，去切菜，炒菜。

#### 同步任务

<font color='red'>同步任务都在主线程上执行，形成一个执行栈。</font>

#### 异步任务

<font color='orange'>**JS 的异步是通过回调函数实现的。**</font>

一般而言，异步任务有以下三种类型：

> 1、普通事件，如 click、resize 等
>
> 2、资源加载，如 load、error 等
>
> 3、定时器，包括 setInterval、setTimeout 等

<font color='red'>异步任务相关回调函数添加到任务队列中（任务队列也称为消息队列）。</font>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649734711407.png" alt="1649734711407" style="zoom:50%;" />

### 3、JS执行机制！！！

1. 先执行<font color='red'>执行栈中的同步任务。</font>
2. **异步任务（回调函数）放入任务队列中。**

3. <font color='green'>**一旦执行栈中的所有同步任务执行完毕，系统就会按次序读取任务队列中的异步任务，于是被读取的异步任务结束等待状态，进入执行栈，开始执行。**</font>

![1649734789539](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649734789539.png)

![1649734802976](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649734802976.png)

![1649734815915](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649734815915.png)

**由于主线程不断的重复获得任务、执行任务、再获取任务、再执行，所以这种机制被称为事件循环（ event loop）。**

## 五、location对象

**window 对象**给我们提供了一个 <font color='red'>location 属性用于获取或设置窗体的 URL，并且可以用于解析 URL 。 </font>**因为这个属性返回的是一个对象，所以我们将这个属性也称为 location 对象。**

### 1、URL

<font color='red'>统一资源定位符 (Uniform Resource Locator, URL) </font>是互联网上标准资源的地址。**互联网上的每个文件都有一个唯一的 URL，它包含的信息指出文件的位置以及浏览器应该怎么处理它。**

URL 的一般语法格式为：

![1649738951758](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649738951758.png)

![1649738957582](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649738957582.png)

### 2、location对象的属性

![1649739066678](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649739066678.png)

重点记住： href 和 search

### 3、location对象的方法

![1649739093797](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649739093797.png)

## 六、navigator对象

**navigator 对象包含有关浏览器的信息，它有很多属性，**我们<font color='red'>最常用的是 userAgent，该属性可以返回由客户机发送服务器的 user-agent 头部的值。</font>

下面前端代码可以判断用户那个终端打开页面，实现跳转

![1649739144136](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649739144136.png)

## 七、history对象

window 对象给我们提供了一个 history 对象，与浏览器历史记录进行交互。<font color='red'>该对象包含用户（在浏览器窗口中）访问过的 URL。</font>

![1649739177669](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649739177669.png)

# PC端网页特效

## 一、元素偏移量 offset 系列

### 1、offset概述

<font color='red'>**offset 翻译过来就是偏移量， 我们使用 offset 系列相关属性可以动态的得到该元素的位置（偏移）、大小等。**</font>

- 获得元素距离带有定位父元素的位置
- 获得元素自身的大小（宽度高度）
- **注意： 返回的数值都不带单位**

#### offset系列常用属性

![1649739327092](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649739327092.png)

![1649739377635](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649739377635.png)

#### offset和style的区别

![1649739359936](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649739359936.png)

#### 案例：获取鼠标在盒子内的坐标

> 1. 我们在盒子内点击，想要得到鼠标距离盒子左右的距离。
> 2. 首先得到鼠标在页面中的坐标（e.pageX, e.pageY）
> 3. 其次得到盒子在页面中的距离 ( box.offsetLeft, box.offsetTop)
> 4. 用鼠标距离页面的坐标减去盒子在页面中的距离，得到 鼠标在盒子内的坐标
> 5. 如果想要移动一下鼠标，就要获取最新的坐标，使用鼠标移动事件 mousemove

![1649739479608](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649739479608.png)

#### 案例：模态框拖拽

> - 弹出框，我们也称为模态框。
> - 点击弹出层， 会弹出模态框， 并且显示灰色半透明的遮挡层。
> - 点击关闭按钮，可以关闭模态框，并且同时关闭灰色半透明遮挡层。
> - 鼠标放到模态框最上面一行，可以按住鼠标拖拽模态框在页面中移动。
> - 鼠标松开，可以停止拖动模态框移动。

1. 点击弹出层， 模态框和遮挡层就会显示出来 display:block;
2. 点击关闭按钮，模态框和遮挡层就会隐藏起来 display:none;
3. 在页面中拖拽的原理： 鼠标按下并且移动， 之后松开鼠标
4. 触发事件是鼠标按下 mousedown， 鼠标移动mousemove 鼠标松开 mouseup
5. 拖拽过程:  鼠标移动过程中，获得最新的值赋值给模态框的left和top值， 这样模态框可以跟着鼠标走了
6. 鼠标按下触发的事件源是 最上面一行，就是  id 为 title 
7. 鼠标的坐标 减去 鼠标在盒子内的坐标， 才是模态框真正的位置。
8. 鼠标按下，我们要得到鼠标在盒子的坐标。
9. 鼠标移动，就让模态框的坐标  设置为  ： 鼠标坐标 减去盒子坐标即可，注意移动事件写到按下事件里面。
10. 鼠标松开，就停止拖拽，就是可以让鼠标移动事件解除  

## 二、元素可视区 client 系列

client 翻译过来就是客户端，我们使用 <font color='red'>client 系列的相关属性来获取元素可视区的相关信息。通过 client 系列的相关属性可以动态的得到该元素的边框大小、元素大小等。</font>

### client系列属性

![1649739584453](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649739584453.png)

![1649739614544](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649739614544.png)

#### 立即执行函数：

> <font color='red'>立即执行函数  (function() {})()  或者 (function(){}())</font>
>
> 主要作用： 创建一个独立的作用域。 避免了命名冲突问题

下面三种情况都会刷新页面都会触发 load 事件。

1. a标签的超链接
2. F5或者刷新按钮（强制刷新）
3. 前进后退按钮

但是 火狐中，有个特点，有个“往返缓存”，这个缓存中不仅保存着页面数据，还保存了DOM和JavaScript的状态；实际上是将整个页面都保存在了内存里。

所以此时后退按钮不能刷新页面。

此时可以**使用 pageshow事件来触发。，这个事件在页面显示时触发，无论页面是否来自缓存。在重新加载页面中，pageshow会在load事件触发后触发；根据事件对象中的persisted来判断是否是缓存中的页面触发的pageshow事件，注意这个事件给window添加。**

## 三、元素滚动 scroll 系列

scroll 翻译过来就是滚动的，我们<font color='red'>使用 scroll 系列的相关属性可以动态的得到该元素的大小、滚动距离等。</font>

### scroll系列属性

![1649739718379](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649739718379.png)

### 页面被卷去的头部

如果浏览器的高（或宽）度不足以显示整个页面时，会自动出现滚动条。<font color='blue'>当滚动条向下滚动时，页面上面被隐藏掉的高度，我们就称为页面被卷去的头部。滚动条在滚动时会触发 onscroll 事件。</font>

> <font color='red'>页面被卷去的头部：可以通过window.pageYOffset 获得  如果是被卷去的左侧 window.pageXOffset</font>
>
> <font color='green'>注意，**元素被卷去的头部是 element.scrollTop  ,** 如果是**页面被卷去的头部 则是 window.pageYOffset**</font>
>
> 其实这个值可以通过盒子的 offsetTop 可以得到，如果大于等于这个值，就可以让盒子固定定位了

需要注意的是，页面被卷去的头部，有兼容性问题，因此被卷去的头部通常有如下几种写法：

1. 声明了 DTD，使用 document.documentElement.scrollTop
2. 未声明 DTD，使用  document.body.scrollTop

3. **新方法 window.pageYOffset 和 window.pageXOffset，IE9 开始支持**

![1649739849900](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649739849900.png)

## 三大系列总结

![1649740007195](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649740007195.png)

![1649740022019](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649740022019.png)

> 他们主要用法：
>
> 1. <font color='red'>offset系列经常用于获得元素位置    offsetLeft  offsetTop</font>
> 2. <font color='blue'>client 经常用于获取元素大小  clientWidth  clientHeight</font>
> 3. <font color='green'>scroll 经常用于获取滚动距离  scrollTop  scrollLeft   </font>
>
> 注意页面滚动的距离通过 window.pageXOffset  获得

### mouseenter和mouseover的区别

#### mouseenter鼠标事件

- 当鼠标移动到元素上时就会触发 mouseenter 事件

- 类似 mouseover，它们两者之间的差别是

- <font color='red'>mouseover 鼠标经过自身盒子会触发，经过子盒子还会触发。 mouseenter  只会经过自身盒子触发</font>
- 之所以这样，就是因为mouseenter不会冒泡
- 跟mouseenter搭配 <font color='red'>鼠标离开 mouseleave  同样不会冒泡</font>

## 四、动画函数封装

### 1、动画实现原理

<font color='red'>核心原理：通过定时器 setInterval() 不断移动盒子位置。</font>

> 实现步骤：！！！
>
> 1. 获得盒子当前位置
> 2. 让盒子在当前位置加上1个移动距离
> 3. 利用定时器不断重复这个操作
> 4. 加一个结束定时器的条件
>
> 5. 注意此元素需要添加定位，才能使用element.style.left

![1649740559480](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649740559480.png)

### 2、动画函数简单封装

<font color='red'>注意函数需要传递2个参数，**动画对象和移动到的距离。**</font>

![1649740587763](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649740587763.png)

### 3、动画函数给不同元素记录不同定时器 

如果多个元素都使用这个动画函数，每次都要var 声明定时器。我们可以给不同的元素使用不同的定时器（自己专门用自己的定时器）。

核心原理：利用 JS 是一门动态语言，可以很方便的给当前对象添加属性。

![1649740658054](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649740658054.png)

### 4、缓动效果原理

缓动动画就是让元素运动速度有所变化，最常见的是让速度慢慢停下来

思路：

1. 让盒子每次移动的距离慢慢变小，速度就会慢慢落下来。
2. 核心算法： (目标值 - 现在的位置 )   /   10    做为每次移动的距离 步长
3. 停止的条件是： 让当前盒子位置等于目标位置就停止定时器  
4. 注意步长值需要取整   

![1649740723532](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649740723532.png)

### 5、动画函数多个目标值之间移动

可以让动画函数从 800 移动到 500。

当我们点击按钮时候，判断步长是正值还是负值

1. 如果是正值，则步长 往大了取整
2. 如果是负值，则步长 向小了取整

### 6、动画函数添加回调函数 

**回调函数原理：**函数可以作为一个参数。将这个函数作为参数传到另一个函数里面，当那个函数执行完之后，再执行传进去的这个函数，这个过程就叫做回调。

<font color='red'>回调函数写的位置：定时器结束的位置。</font>

### 7、动画函数封装到单独JS文件里面

因为以后经常使用这个动画函数，可以单独封装到一个JS文件里面，使用的时候引用这个JS文件即可。

1. 单独新建一个JS文件。
2. HTML文件引入 JS 文件。

## 案例：网页轮播图

> 轮播图也称为焦点图，是网页中比较常见的网页特效。
>
> 功能需求：
>
> 1. 鼠标经过轮播图模块，左右按钮显示，离开隐藏左右按钮。
> 2. 点击右侧按钮一次，图片往左播放一张，以此类推， 左侧按钮同理。
> 3. 图片播放的同时，下面小圆圈模块跟随一起变化。
> 4. 点击小圆圈，可以播放相应图片。
> 5. 鼠标不经过轮播图， 轮播图也会自动播放图片。
> 6. 鼠标经过，轮播图模块， 自动播放停止。

##### 思路分析

> - 因为js较多，我们单独新建js文件夹，再新建js文件， 引入页面中。
> - 此时需要添加 load 事件。
> - 鼠标经过轮播图模块，左右按钮显示，离开隐藏左右按钮。
> - 显示隐藏 display 按钮。

###### 动态生成小圆圈

核心思路：小圆圈的个数要跟图片张数一致

- 所以首先先得到ul里面图片的张数（图片放入li里面，所以就是li的个数）
- 利用循环动态生成小圆圈（这个小圆圈要放入ol里面）
- 创建节点 createElement(‘li’)
- 插入节点 ol. appendChild(li)
- 第一个小圆圈需要添加 current 类

###### 小圆圈的排他思想

- 点击当前小圆圈，就添加current类
- 其余的小圆圈就移除这个current类

注意： 我们在刚才生成小圆圈的同时，就可以直接绑定这个点击事件了。

###### 点击小圆圈滚动图片

此时用到animate动画函数，将js文件引入（注意，因为index.js 依赖 animate.js 所以，animate.js 要写到 index.js 上面）

使用动画函数的前提，该元素必须有定位

注意是ul 移动 而不是小li 

<font color='red'>滚动图片的核心算法： 点击某个小圆圈 ， 就让图片滚动小圆圈的索引号乘以图片的宽度做为ul移动距离</font>

此时需要知道小圆圈的索引号， 我们可以在生成小圆圈的时候，给它设置一个自定义属性，点击的时候获取这个自定义属性即可。

###### 点击右侧按钮一次，就让图片滚动一张。 

声明一个变量num， 点击一次，自增1， 让这个变量乘以图片宽度，就是 ul 的滚动距离。

图片无缝滚动原理

1. 把ul 第一个li 复制一份，放到ul 的最后面
2. 当图片滚动到克隆的最后一张图片时， 让ul 快速的、不做动画的跳到最左侧： left 为0
3. 同时num 赋值为0，可以从新开始滚动图片了

###### 克隆第一张图片

- 克隆ul 第一个li  cloneNode()   加true 深克隆 复制里面的子节点    false 浅克隆 
- 添加到 ul 最后面  appendChild

###### 点击右侧按钮， 小圆圈跟随变化

最简单的做法是再声明一个变量circle，每次点击自增1，注意，左侧按钮也需要这个变量，因此要声明全局变量。

但是图片有5张，我们小圆圈只有4个少一个，必须加一个判断条件

如果circle  ==  4 就 从新复原为 0

###### 自动播放功能

添加一个定时器

1. 自动播放轮播图，实际就类似于点击了右侧按钮
2. 此时我们使用手动调用右侧按钮点击事件  arrow_r.click()
3. 鼠标经过focus 就停止定时器 
4. 鼠标离开focus 就开启定时器

#### 节流阀

> <font color='red'>防止轮播图按钮连续点击造成播放过快。</font>
>
> <font color='green'>**节流阀目的：当上一个函数动画内容执行完毕，再去执行下一个函数动画，让事件无法连续触发。**</font>
>
> <font color='red'>核心实现思路：利用回调函数，添加一个变量来控制，锁住函数和解锁函数。</font> 
>
> 开始设置一个变量 var flag = true;
>
> If(flag) {flag = false; do something}       关闭水龙头
>
> 利用回调函数 动画执行完毕， flag = true     打开水龙头

> 滚动窗口至文档中的特定位置。
>
> window.scroll(x, y) 
>
> 注意，里面的x和y 不跟单位，直接写数字

# 移动端网页特效

## 一、触屏事件

### 1、触摸事件

移动端浏览器兼容性较好，我们不需要考虑以前 JS 的兼容性问题，可以放心的使用原生 JS 书写效果，但是移动端也有自己独特的地方。比如<font color='red'>触屏事件 touch（也称触摸事件）</font>，Android 和 IOS 都有。

<font color='blue'>touch 对象代表一个触摸点。触摸点可能是一根手指，也可能是一根触摸笔。触屏事件可响应用户手指（或触控笔）对屏幕或者触控板操作。</font>

常见的触屏事件如下：

![1649741754553](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649741754553.png)

### 2、触摸事件对象（TouchEvent）

<font color='red'>TouchEvent 是一类描述手指在触摸平面（触摸屏、触摸板等）的状态变化的事件。</font>这类事件用于描述一个或多个触点，使开发者可以检测触点的移动，触点的增加和减少，等等

touchstart、touchmove、touchend 三个事件都会各自有事件对象。

触摸事件对象重点我们看三个常见对象列表：

![1649741819022](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649741819022.png)

### 3、移动端拖动元素

1. touchstart、touchmove、touchend 可以实现拖动元素
2. <font color='red'>但是拖动元素需要当前手指的坐标值 我们可以使用  targetTouches[0] 里面的pageX 和 pageY </font>
3. 移动端拖动的原理：    手指移动中，计算出手指移动的距离。然后用盒子原来的位置 + 手指移动的距离
4. 手指移动的距离：   手指滑动中的位置 减去  手指刚开始触摸的位置

<font color='red'>拖动元素三步曲：</font>

- 触摸元素 touchstart：  获取手指初始坐标，同时获得盒子原来的位置
- 移动手指 touchmove：  计算手指的滑动距离，并且移动盒子
- 离开手指 touchend

<font color='red'>注意： 手指移动也会触发滚动屏幕所以这里要阻止默认的屏幕滚动 e.preventDefault();</font>

![1649742086069](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649742086069.png)

## 二、移动端常见特效

#### 案例：移动端轮播图

主要js代码：

~~~
window.addEventListener('load', function () {
    // alert(1);
    // 1. 获取元素 
    var focus = document.querySelector('.focus');
    var ul = focus.children[0];
    // 获得focus 的宽度
    var w = focus.offsetWidth;
    var ol = focus.children[1];
    // 2. 利用定时器自动轮播图图片
    var index = 0;
    var timer = setInterval(function () {
        index++;
        var translatex = -index * w;
        // 过渡效果
        ul.style.transition = 'all .3s';
        ul.style.transform = 'translateX(' + translatex + 'px)';
    }, 2000);
    // 等着我们过渡完成之后，再去判断 
    // 监听过渡完成的事件 transitionend 
    ul.addEventListener('transitionend', function () {
        // 无缝滚动
        if (index >= 3) {
            index = 0;
            // console.log(index);
            // 去掉过渡效果 这样让我们的ul 快速的跳到目标位置
            ul.style.transition = 'none';
            // 利用最新的索引号乘以宽度 去滚动图片
            var translatex = -index * w;
            ul.style.transform = 'translateX(' + translatex + 'px)';
        } else if (index < 0) {
            index = 2;
            ul.style.transition = 'none';
            // 利用最新的索引号乘以宽度 去滚动图片
            var translatex = -index * w;
            ul.style.transform = 'translateX(' + translatex + 'px)';
        }
        // 3. 小圆点跟随变化
        // 把ol里面li带有current类名的选出来去掉类名 remove
        ol.querySelector('.current').classList.remove('current');
        // 让当前索引号 的小li 加上 current   add
        ol.children[index].classList.add('current');
    });

    // 4. 手指滑动轮播图 
    // 触摸元素 touchstart： 获取手指初始坐标
    var startX = 0;
    var moveX = 0; // 后面我们会使用这个移动距离所以要定义一个全局变量
    var flag = false;
    ul.addEventListener('touchstart', function (e) {
        startX = e.targetTouches[0].pageX;
        // 手指触摸的时候就停止定时器
        clearInterval(timer);
    });
    // 移动手指 touchmove： 计算手指的滑动距离， 并且移动盒子
    ul.addEventListener('touchmove', function (e) {
        // 计算移动距离
        moveX = e.targetTouches[0].pageX - startX;
        // 移动盒子：  盒子原来的位置 + 手指移动的距离 
        var translatex = -index * w + moveX;
        // 手指拖动的时候，不需要动画效果所以要取消过渡效果
        ul.style.transition = 'none';
        ul.style.transform = 'translateX(' + translatex + 'px)';
        flag = true; // 如果用户手指移动过我们再去判断否则不做判断效果
        e.preventDefault(); // 阻止滚动屏幕的行为
    });
    // 手指离开 根据移动距离去判断是回弹还是播放上一张下一张
    ul.addEventListener('touchend', function (e) {
        if (flag) {
            // (1) 如果移动距离大于50像素我们就播放上一张或者下一张
            if (Math.abs(moveX) > 50) {
                // 如果是右滑就是 播放上一张 moveX 是正值
                if (moveX > 0) {
                    index--;
                } else {
                    // 如果是左滑就是 播放下一张 moveX 是负值
                    index++;
                }
                var translatex = -index * w;
                ul.style.transition = 'all .3s';
                ul.style.transform = 'translateX(' + translatex + 'px)';
            } else {
                // (2) 如果移动距离小于50像素我们就回弹
                var translatex = -index * w;
                ul.style.transition = 'all .1s';
                ul.style.transform = 'translateX(' + translatex + 'px)';
            }
        }
        // 手指离开的时候就重新开启定时器
        clearInterval(timer);
        timer = setInterval(function () {
            index++;
            var translatex = -index * w;
            ul.style.transition = 'all .3s';
            ul.style.transform = 'translateX(' + translatex + 'px)';
        }, 2000);
    });


    // 返回顶部模块制作
    var goBack = document.querySelector('.goBack');
    var nav = document.querySelector('nav');
    window.addEventListener('scroll', function () {
        if (window.pageYOffset >= nav.offsetTop) {
            goBack.style.display = 'block';
        } else {
            goBack.style.display = 'none';
        }
    });
    goBack.addEventListener('click', function () {
        window.scroll(0, 0);
    })
})
~~~

## 三、移动端常用开发插件

<font color='red'>JS 插件是 js 文件，它遵循一定规范编写，方便程序展示效果，拥有特定功能且方便调用。如轮播图和瀑布流插件。</font>

特点：它一般是为了解决某个问题而专门存在，其功能单一，并且比较小。比如移动端常见插件：iScroll、Swiper、SuperSlider 。

### 1、插件的使用

1. 引入 js 插件文件。
2. 按照规定语法使用。

### 2、Swiper 插件的使用

中文官网地址： https://www.swiper.com.cn/ 

superslide： http://www.superslide2.com/

iscroll： https://github.com/cubiq/iscroll

### 3、click 延时解决方案

<font color='red'>移动端 click 事件会有 300ms 的延时，原因是移动端屏幕双击会缩放(double tap to zoom) 页面。</font>

解决方案：

1. 禁用缩放。 浏览器禁用默认的双击缩放行为并且去掉 300ms 的点击延迟。

   ![1649742294591](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649742294591.png)

2. 使用插件。 fastclick 插件解决 300ms 延迟。 

   ![1649742312802](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649742312802.png)

#### 移动端视频插件 zy.media.js

H5 给我们提供了 video 标签，但是浏览器的支持情况不同。在移动端我们可以使用插件方式来制作。

## 四、移动端常用开发框架

框架，顾名思义就是一套架构，它会基于自身的特点向用户提供一套较为完整的解决方案。框架的控制权在框架本身，使用者要按照框架所规定的某种规范进行开发。

前端常用的框架有 Bootstrap、Vue、Angular 等。

### 1、Bootstrap

Bootstrap 是一个简洁、直观、强悍的前端开发框架，它让 web 开发更迅速、简单。

### 2、MUI 原生UI前端框架

MUI 是一个专门用于做手机 APP 的前端框架。

MUI 的 UI 设计理念是：以 IOS 为基础，补充 Android 平台特有的控件。因此 MUI 封装的控件，UI 上更符合app 的体验。

MUI 中文官网地址：http://dev.dcloud.net.cn/mui/

# 本地存储

## 一、window.sessionStorage

### 本地存储特性

1、数据存储在用户浏览器中

2、设置、读取方便、甚至页面刷新不丢失数据

3、容量较大，sessionStorage约5M、localStorage约20M

4、<font color='red'>只能存储字符串，可以将对象JSON.stringify() 编码后存储</font>

> 1. <font color='red'>生命周期为关闭浏览器窗口</font>
>
> 2. <font color='blue'>在同一个窗口(页面)下数据可以共享</font>
>
> 3. 以键值对的形式存储使用

#### 存储数据

![1649742643331](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649742643331.png)

#### 获取数据

![1649742651976](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649742651976.png)

#### 删除数据

![1649742669311](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649742669311.png)

#### 删除所有数据

![1649742680456](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649742680456.png)

## 二、window.localStorage

> 1. <font color='red'>声明周期永久生效，除非手动删除 否则关闭页面也会存在</font>
>
> 2. <font color='blue'>可以多窗口（页面）共享（同一浏览器可以共享）</font>
>
> 3. 以键值对的形式存储使用

#### 存储数据

![1649742789370](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649742789370.png)

#### 获取数据

![1649742805398](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649742805398.png)

#### 删除数据

![1649742833142](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649742833142.png)

#### 删除所有数据

![1649742837954](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649742837954.png)

