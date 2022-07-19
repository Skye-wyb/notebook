# CSS3

## 一、CSS3属性选择器

![1650023918521](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650023918521.png)

<font color='red'>类选择器、属性选择器、伪类选择器，权重为 10</font>

## 二、结构伪类选择器

![1650024006571](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650024006571.png)

### nth-child（n）

> n可以是数字，关键字和公式
>
> n如果是数字，就是选择第n个
>
> 常见的**关键词 even 偶数 odd 奇数**
>
> 常见的公式如下 ( 如果n是公式，则从0开始计算）
>
> 但是 第0个元素或者超出了元素的个数会被忽略 )

![1650024085387](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650024085387.png)

- <font color='red'>结构伪类选择器就是选择第n个</font>
- Nth-child从所有子级开始算的，可能不是同一种类型
- Nth-of-type 是指定同一种类型的子级，比如 ul li:nth-of-type(2) 是选择第2个li
- 关于nth-child（n） 我们要知道n从0开始计算的，要记住常用的公式
- 如果是无无序列表，我们肯定用 nth-child 更多

## 三、CSS3 伪元素选择器

![1650024134629](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650024134629.png)

> - <font color='red'>**before 和 after 必须有 content 属性**</font>
> - **before 在内容的前面，after 在内容的后面**
> - <font color='green'>before 和 after 创建一个元素，但是属于行内元素。</font>
> - <font color='blue'>因为在 dom 里面看不见刚才创建的元素，所以我们称为伪元素</font>
> - 伪元素和标签选择器一样，权重为 1

### 伪元素字体图标

![1650024197145](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650024197145.png)

## 四、CSS3 2D转换

转换（transform）是CSS3中具有颠覆性的特征之一，可以实现元素的位移、旋转、缩放等效果

> - 移动：translate
> - 旋转：rotate
> - 缩放：scale

### 1、二维坐标系

![1650024263535](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650024263535.png)

### 2、2D 转换之移动 translate

**2D移动是2D转换里面的一种功能，可以改变元素在页面中的位置，类似<font color='red'>定位。</font>**

#### 语法

![1650024305538](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650024305538.png)

> 1. <font color='red'>定义 2D 转换中的移动，沿着 X 和 Y 轴移动元素</font>
> 2. <font color='blue'>translate最大的优点：不会影响到其他元素的位置</font>
> 3. **translate中的百分比单位是相对于自身元素的 translate:(50%,50%);**
> 4. **对行内标签没有效果**

### 3、2D 转换之旋转 rotate

2D旋转指的是让元素在2维平面内顺时针旋转或者逆时针旋转。

#### 语法

![1650024374778](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650024374778.png)

> 1. rotate里面跟度数， 单位是 deg 比如 rotate(45deg)
> 2. <font color='red'>角度为正时，顺时针，负时，为逆时针</font>
> 3. <font color='blue'>默认旋转的中心点是元素的中心点</font>

![1650024406260](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650024406260.png)

### 4、2D 转换中心点 transform-origin

设置元素转换的中心点

#### 语法

![1650024430791](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650024430791.png)

> 1. 注意后面的参数 x 和 y 用空格隔开
> 2. <font color='red'>x y 默认转换的中心点是元素的中心点 (50% 50%)</font>
> 3. 还可以给x y 设置 像素 或者 方位名词 （top bottom left right center）

### 5、2D 转换之缩放scale

缩放，顾名思义，可以放大和缩小。<font color='red'> 只要给元素添加上了这个属性就能控制它放大还是缩小。</font>

#### 语法

![1650024483416](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650024483416.png)

> 1. 注意其中的x和y用逗号分隔
> 2. transform:scale(1,1) ：宽和高都放大一倍，相对于没有放大
> 3. transform:scale(2,2) ：宽和高都放大了2倍
> 4. transform:scale(2) ：只写一个参数，第二个参数则和第一个参数一样，相当于 scale(2,2)
> 5. transform:scale(0.5,0.5)：缩小
> 6. sacle缩放最大的优势：可以设置转换中心点缩放，默认以中心点缩放的，而且不影响其他盒子

### 2D转化综合写法

> 1. <font color='red'>**同时使用多个转换，其格式为：transform: translate() rotate() scale() ...等，**</font>
> 2. 其顺序会影转换的效果。（先旋转会改变坐标轴方向）
> 3. **当我们同时有位移和其他属性的时候，记得要将位移放到最前**

## 五、CSS3动画

**动画（animation）是CSS3中具有颠覆性的特征之一，可通过设置多个节点来精确控制一个或一组动画，常**
**用来实现复杂的动画效果。**

相比较过渡，动画可以实现更多变化，更多控制，连续自动播放等效果。

### 1、动画的基本使用

制作动画分为两步：

1. 先定义动画
2. 再使用（调用）动画

#### 1.1 用keyframes 定义动画（类似定义类选择器）

![1650024627862](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650024627862.png)

##### 动画序列

- <font color='red'>0% 是动画的开始，100% 是动画的完成。这样的规则就是动画序列。</font>
- 在 @keyframes 中规定某项 CSS 样式，就能创建由当前样式逐渐改为新样式的动画效果。
- 动画是使元素从一种样式逐渐变化为另一种样式的效果。您可以改变任意多的样式任意多的次数。
- 请用百分比来规定变化发生的时间，**或用关键词 "from" 和 "to"，等同于 0% 和 100%。**

#### 1.2 元素使用动画

![1650024689859](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650024689859.png)

### 2、动画常用属性

![1650024712160](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650024712160.png)

### 3、动画简写属性

<font color='blue'>**animation：动画名称 持续时间 运动曲线 何时开始 播放次数 是否反方向 动画起始或者结束的状态;**</font>

![1650024747489](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650024747489.png)

> 1. 简写属性里面不包含 animation-play-state
> 2. 暂停动画：animation-play-state: puased; 经常和鼠标经过等其他配合使用
> 3. 想要动画走回来 ，而不是直接跳回来：animation-direction ： alternate
> 4. 盒子动画结束后，停在结束位置： animation-fill-mode ： forwards

### 4、速度曲线细节

**animation-timing-function：规定动画的速度曲线，默认是“ease”**

![1650024814468](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650024814468.png)

## 六、CSS3 3D转换

![1650024838936](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650024838936.png)

### 1、三维坐标系

![1650024862026](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650024862026.png)

### 2、3D移动 translate3d

3D移动在2D移动的基础上多加了一个可以移动的方向，就是z轴方向。

1. translform:translateX(100px)：仅仅是在x轴上移动
2. translform:translateY(100px)：仅仅是在Y轴上移动
3. translform:translateZ(100px)：仅仅是在Z轴上移动（注意：translateZ一般用px单位）
4. transform:translate3d(x,y,z)：其中 x、y、z 分别指要移动的轴的方向的距离

**因为z轴是垂直屏幕，由里指向外面，所以默认是看不到元素在z轴的方向上移动**

### 3、透视 perspective

在2D平面产生近大远小视觉立体，但是只是效果二维的

- 如果想要在网页产生3D效果需要透视（理解成3D物体投影在2D平面内）。
- 模拟人类的视觉位置，可认为安排一只眼睛去看
- 透视我们也称为视距：视距就是人的眼睛到屏幕的距离
- 距离视觉点越近的在电脑平面成像越大，越远成像越小
- 透视的单位是像素

![1650024969324](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650024969324.png)

> 透视写在被观察元素的父盒子上面的
>
> 1. d：就是视距，视距就是一个距离人的眼睛到屏幕的距离。
> 2. z：就是 z轴，物体距离屏幕的距离，z轴越大（正值） 我们看到的物体就越大。

### 4、translateZ

translform:translateZ(100px)：仅仅是在Z轴上移动。

有了透视，就能看到translateZ 引起的变化了

> - translateZ：近大远小
> - translateZ：往外是正值
> - translateZ：往里是负值

### 5、3D旋转 rotate3d

**3D旋转指可以让元素在三维平面内沿着 x轴，y轴，z轴或者自定义轴进行旋转。**

#### 语法

1. transform:rotateX(45deg)：沿着x轴正方向旋转 45度
2. transform:rotateY(45deg) ：沿着y轴正方向旋转 45deg
3. transform:rotateZ(45deg) ：沿着Z轴正方向旋转 45deg
4. transform:rotate3d(x,y,z,deg)： 沿着自定义轴旋转 deg为角度（了解即可）

![1650025088301](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650025088301.png)

![1650025110635](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650025110635.png)

> transform:rotate3d(x,y,z,deg)： 沿着自定义轴旋转 deg为角度（了解即可）
>
> xyz是表示旋转轴的矢量，是标示你是否希望沿着该轴旋转，最后一个标示旋转的角度。
>
> - transform:rotate3d(1,0,0,45deg) 就是沿着x轴旋转 45deg
> - transform:rotate3d(1,1,0,45deg) 就是沿着对角线旋转 45deg

### 6、3D呈现 transfrom-style

> 控制子元素是否开启三维立体环境。。
>
> <font color='red'>transform-style: flat 子元素不开启3d立体空间 默认的</font>
>
> <font color='red'>transform-style: preserve-3d; 子元素开启立体空间</font>
>
>  **代码写给父级，但是影响的是子盒子**
>
> 这个属性很重要，后面必用

##### 案例-两面翻转的盒子

![1650025221574](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650025221574.png)

![1650025229424](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650025229424.png)

##### 案例-3D导航栏

![1650025250262](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650025250262.png)

![1650025257336](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650025257336.png)

![1650025264968](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650025264968.png)

##### 案例-旋转木马

![1650025286308](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650025286308.png)

![1650025295352](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650025295352.png)

![1650025302090](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650025302090.png)

## 七、浏览器私有前缀

浏览器私有前缀是为了兼容老版本的写法，比较新版本的浏览器无须添加。

## 1、私有前缀

1. -moz-：代表 firefox 浏览器私有属性
2. -ms-：代表 ie 浏览器私有属性
3. -webkit-：代表 safari、chrome 私有属性
4. -o-：代表 Opera 私有属性

![1650025365597](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650025365597.png)

