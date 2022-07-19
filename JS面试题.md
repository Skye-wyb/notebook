# 1、js预编译

预编译是上下文创建之后，js代码执行前的一段时间，在这个时期，会对js代码进行预处理

全局上下文创建后，会生成**变量对象VO**，VO<font color='red'>首先寻找变量声明</font>，**将var声明的变量作为VO对象的属性名，值为undefined，然后寻找函数声明，属性值为函数本身，如果函数名与变量名冲突，函数声明会将变量声明覆盖。**

## 全局预编译

~~~
console.log(a);
var a = 100;
function a(){ }
console.log(a)
~~~

![1649726922573](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649726922573.png)

## 函数预编译

函数上下文创建后，会生成**变量对象AO**

- 寻找变量声明，变量名作为AO对象的属性名，属性值为undefined
- <font color='red'>寻找形参、形参名作为AO对象的属性名，属性值置为undefined</font>
- <font color='red'>将实参的值赋予形参，即替换AO对象中形参的属性值</font>
- 寻找函数声明，**函数名作为AO对象的属性名，属性值为函数本身**
- 如果函数名与变量名冲突，函数声明会将变量声明覆盖

![1650788813526](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650788813526.png)

![1649727034312](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649727034312.png)

### 面试题

![1650788850941](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650788850941.png)

**先进行全局预编译，再进行函数预编译**

<font color='red'>函数预编译过程</font>

![1649727604344](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649727604344.png)

![1649727320226](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649727320226.png)

# 2、js同源策略

### 什么是源（origin）

**Web内容的源由用于访问它的URL的方案（协议）、主机（域名）和端口定义；**<font color='red'>只有当方案，主机和端口都匹配时，两个对象具有相同的源。</font>

<font color='blue'>**同源策略是一个重要的安全策略，它定义了源之间资源的如何交互，减少可能被攻击的媒介。**</font>

### 跨域网络访问

- **跨域写操作（Cross-origin writes）一般是被允许的。**例如链接（links），重定向以及表单提交。特定少数的HTTP请求需要添加preflight。
- **跨域资源嵌入（Cross-origin embedding）一般是被允许的。**
- **跨域读操作（Cross-origin reads）一般是不被允许的，**但常可以通过内嵌资源来进行读取访问。

例如：

1. script标签嵌入跨域脚本。语法错误信息只能被同源脚本中捕获到。
2. link标签嵌入CSS。由于CSS的松散的语法规则，CSS的跨域需要一个设置正确的HTTP头部Content-Type。不同浏览器有不同的限制：IE、Firefox、Chrome、Safari部分和Opera。
3. 通过img展示的图片；支持的图片格式由PNG、JPEG、GIF、BMP、SVG...
4. 通过video和audio播放的多媒体资源
5. 通过object、embed和applet嵌入的插件
6. 通过@font-face引入的字体
7. 通过iframe载入的任何资源

### 如何解决跨域

> 1. 跨域资源共享（Cross-Origin Resource Sharing）简称CORS
> 2. JSONP

# 3、js作用域

**可以理解为执行环境中变量或函数的作用范围，作用域定义了变量或函数有权访问的其他数据，作用域都有一个变量对象。**

### 全局作用域

> 1. <font color='red'>全局作用域在页面打开时被创建，页面关闭时被销毁</font>
> 2. <font color='blue'>**编写在script标签中的变量和函数，作用域为全局，在页面的任意位置都可以访问**</font>
> 3. <font color='green'>全局作用域可以认为是Window，因为所有全局变量和函数都是作为window对象的属性和方法创建的</font>

### 局部（函数）作用域

> 1. **函数调用时，函数作用域被创建，函数执行完毕，函数作用域被销毁**
> 2. <font color='red'>每调用一次函数就会创建一个新的函数作用域，他们之间是相互独立的</font>
> 3. <font color='orange'>函数作用域可以访问上层作用域，但相邻函数作用域是相互独立的</font>

#### es6前没有块级作用域

![1650788873326](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650788873326.png)

![1649728892295](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649728892295.png)

### es6中的块级作用域

> <font color='red'>**通过let和const声明会形成块级作用域，与其他作用域一样，对外是不可见的。**</font>

![1650788891628](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650788891628.png)

![1649729231445](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649729231445.png)

# 4、作用域链⭐

<font color='red'>作用域链的用途：保证对执行环境有权访问的所有变量和函数的有序访问。</font>

示例：

![1650788908779](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650788908779.png)

### 从代码执行来看

首先在创建fn函数时，会创建**一个预先包含<font color='red'>全局变量对象</font>的作用域链，**这个作用域链被保存在内部的Scope属性中。<font color='blue'>当调用fn函数时，会为函数创建一个执行环境，然后通过复制函数的Scope属性中的对象构建起执行环境的作用域链，然后创建活动对象AO并推入执行环境的作用域。在fn执行完成后，作用域就会被销毁。</font>

~~~
console.dir(fn)
~~~

![1649729783464](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649729783464.png)

# 5、深拷贝和浅拷贝

## js的数据类型

在将一个值赋给变量时，解析器必须确定这个值是基本类型值还是引用类型值

> **基本数据类型**
>
> - string、number、boolean、null、undefined
>
> **引入数据类型**
>
> - object（Array、Object、Function、Map、Set）

![1649730473131](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649730473131.png)

## 深拷贝和浅拷贝

> 1、共同点：复制
>
> 2、浅拷贝：只复制引用而未赋值真正的值
>
> 3、深拷贝：复制真正的值（不同引用、相同值）

### 浅拷贝

<font color='red'>只复制引用而未赋值真正的值，引用类型</font>

![1649730837743](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649730837743.png)

![1649730828956](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649730828956.png)

更改arr1、arr2

![1649730906504](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649730906504.png)

![1649730894392](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649730894392.png)

<font color='red'>因为浅拷贝只复制了引用即栈中的地址，而未赋值真正的值，所以会相互影响</font>

### 深拷贝

<font color='red'>复制真正的值</font>

<font color='blue'>两者之间是独立的，修改其中一个值不会相互影响</font>

**json.parse**

![1649731255467](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649731255467.png)

![1649731262258](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649731262258.png)

**深拷贝修改数据，不会相互影响**

![1649731333657](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649731333657.png)

![1649731346713](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649731346713.png)

# 6、面试题：localstorage、sessionstorage、cookie的区别⭐⭐⭐

#### cookie

##### cookie技术

>  cookie是一种客户端技术（cookie 是保存在客户端的）。服务器把每个用户的数据以cookie的形式写给用户各自的浏览器，**浏览器把cookie数据保存在本地磁盘上。**当用户使用浏览器再去访问服务器中的web资源时，就会带着各自的数据去。这样，web资源处理的就是用户各自的数据了。 

##### cookie定义

> <font color='red'>服务器在客户端保存用户的数据，</font>比如用户登录名、密码等……就是 cookie。服务器端在需要的时候可以从客户端读取。 

##### cookie的基本使用

> 服务器将信息数据<font color='hotpink'>以键值对的形式设置到客户端的 cookie 中（通过http相应头信息传递给客户端）</font>。当再次访问同一服务器站点的资源时，就会自动携带 cookie 中的数据一起访问（通过http请求头信息传递给服务器）。在服务器的每个脚本中都可以接受 cookie 中的数据 

##### 服务端创建 cookie 信息

使用 setcookie() 函数创建一个cookie。通常三个参数，依次是：

1. cookie 名。
2. cookie 值。该值须是字符串类型。值是以明文方式保存的，所以不要存储敏感信息。
3. cookie 的过期时间。这是个 Unix 时间戳。所以，可以用 time() 函数的结果加上希望过期的秒数。time()+60*60*24*30 就是设置 Cookie 30 天后过期。如果设置成零，或者忽略参数，Cookie 会在会话结束时过期（也就是关掉浏览器时）。 

> - 如果要想客户端设置多个cookie，可以通过多次调用setcookie()函数来实现。
> - 要更新某 cookie 值时，只要再用 setcookie() 重新定义一下该 cookie 即可。
> - <font color='hotpink'>如果设置了cookie过期时间，则cookie存储在cookie文件中；</font>
> - **如果没有设置cookie过期时间，则cookie放在浏览器缓存中，关闭浏览器时，cookie即过期删除。**

##### 获取客户端cookie信息

任何从客户端发送过来的cookie信息，都被自动保存在 $_COOKIE 全局数组里，每个PHP脚本都可从该数组中获取cookie信息。

比如 cookie名是 'cookiename'，则可通过 $_COOKIE['cookiename'] 获取它的值。 

在设置cookie的脚本中，第一次获取它的信息并不会生效，必**须刷新或到下一个页面才可以看到cookie的值。因为cookie要先被设置到客户端，再次访问时才能被发送回来，这时才能获取（通过http协议Cookie属性，从客户端传递给服务器。 ）。**

##### 删除cookie信息

<font color='blue'>服务器端说要删除 cookie 信息，则浏览器收到指令将本地 cookie 删除。 </font>

##### 删除指定 cookie 键值对

只需将 setcookie() 中的过期时间戳 -1 即可（cookie 值设置为空""），即：time()-1。 

##### 删除所有 cookie 键值对

使用 foreach 遍历删除 $_COOKIE 数组即可 

![1650764920270](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650764920270.png)

### session技术

<font color='blue'>session 与 cookie 类似，都是用来存储用户信息数据。</font>**<font color='hotpink'>但二者最大的区别在于：cookie是将用户信息存储在客户端，而 session 将用户信息存储在服务器。</font>**

使用 session 跟踪一个用户，是通过在各个页面之间传递唯一的 sessionID，并通过 sessionID 提取该用户在服务器中保存的session变量。**同一个用户在 session 中注册的变量，在整个会话期间的各个页面中该用户都可以使用，每个用户使用自己的变量。**

<font color='red'>在客户端，仅需保存由服务器为用户创建的一个 sessionID，</font>而在服务器端保存 session 变量的值。sessionID 是一个唯一的长字符串，每个用户都不同。

sessionID 会保存在用户客户端的cookie里，如果客户端禁用了 cookie，则会将 sessionID 保存在用户请求的 URL 中传递。

##### 创建/初始化session

<font color='blue'>不同于 cookie 直接创建设置，session 有一个开关，必须先启动才可使用。</font>——**session_start() 函数**

> **session_start()  //创建 session，开始一个会话，进行 session 初始化。**

该函数无参数。

<font color='green'>当用户第一次访问网站时，服务器端会通过 session_start() 函数创建一个唯一的 sessionID，并自动通过 http 响应头，将这个 sessionID 保存到客户端的 cookie 中。</font>同时，**也在服务器端创建一个以这个 sessionID 命名的文件，用于保存这个用户的会话信息。**当同一用户再次访问网站时，**也会自动通过 http 的请求头将客户端 cookie 里的 sessionID 在携带过来，这时 session_start() 函数 就不会再去分配一个新的 sessionID 了，而是在服务器中查找与该 sessionID 同名的 session 文件，将之前该用户的会话信息读出加载到 $_SESSION，在当前脚本中应用，达到跟踪该用户会话的目的。**所以在会话期间，同一个用户在访问服务器上的任何一个页面时，都是使用同一个 sessionID。

类似于顾客在商场购物，只需要记住自己的会员卡号，凭此卡号调用商场的会员信息进行 shopping。

**注意：**<font color='red'>cookie中sessionID的默认有效期限值为0，即与浏览器共存亡，有效期直到浏览器关闭。</font>

##### 注册和读取session变量

<font color='red'>通过访问 $_SESSION 数组来完成注册和读取 session 变量。该数组必须在代用 session_start() 开启 session 之后才能使用。</font>

**注册的变量在页面间是持久保持的，并且变量的修改从一个页面到其他页面是可见的。**

注册和读取 session 的同时，也会在session文件里存取数据。所以，$_SESSION 数组就像是一个中介

虽然感觉像是直接操作 $_SESSION 中存取信息，事实上，读取时，**是先从 session 文件里把 session 数据放到** 

**$_SESSION 中，再调用的。**

##### 注销变量和销毁session

如果用户要退出web应用，需要为他提供一个注销的功能，把他的所有信息在服务器中销毁。

**<font color='hotpink'>使用 session_destroy() 函数销毁和当前 session 相关的所有信息，并清空会话中的所有资源。</font>**

**<font color='green'>该函数与 session_start() 作用相反，用来关闭session，删除 session 文件。</font>**

**<font color='blue'>session_destroy() 函数不会释放与当前session相关的变量，也不会删除保存在客户端cookie中的 sessionID。</font>**

**用unset()释放指定变量，或直接将 $_SESSION 赋值一个空数组以全部清除。**

**<font color='red'>sessionID 须用 setcookie() 进行删除。</font>**在 cookie 中，保存 sessionID 的 cookie 名称就是 session 名，而该 session 名是在 php.ini 中通过 session.name 属性指定的，php 中可以通过调用 session_name() 函数获取该 session 名称。

 **session注销4步骤：** 

![1650765412341](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650765412341.png)



### 共同点

> 在客户端存放数据

### 区别

> 1、数据存放期
>
> - <font color='red'>localstorage：是持久化存储，始终有效，浏览器关闭也一直保存。</font>
> - <font color='blue'>sessionstorage：是临时存储，仅在当前浏览器窗口关闭之前有效。【关闭浏览器就没有了】</font>
> - **cookie：cookie的使用必须要有线上环境，localhost、IP地址、www...**
>
> 可以设置过期时间

![1649731922822](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649731922822.png)

### 举例：

**cookie的HTTPOnly**

# Http中的Cookie

## Cookie

#### 1.Cookie 概念

> <font color='red'> Cookie ： **服务器** 发送给 **浏览器** 并 **保存在本地的一小块数据**，会在浏览器下次向同一服务器 **再次发起请求时** 被 **携带并发送到服务器上**。 </font>

通常，<font color='blue'>它用于告知服务端两个请求是否来自同一浏览器，</font>如保持用户的登录状态。Cookie使基于无状态的HTTP协议记录稳定的状态成为了可能。 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200820054823131.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjA1OTk3MQ==,size_16,color_FFFFFF,t_70#pic_center) 

#### 2.Cookie 作用域

**Domain**

Domain：指定那些主机可以接收Cookie；

不指定，则默认为当前主机；

指定 Domain ，一般包含子域名 （Domain=wos.com） 。

**Path**

Path：指定主机下的那些路径可以接受 Cookie，用 %x2F(/) 作为路径分隔；

#### 3.Cookie 有效期

- **会话期 Cookie**
  - **最简单的 Cookie。浏览器关闭后自动删除。（会话期不需要指定过期时间和有效时间）**
- **持久性 Cookie**
  - **制定一个特定的过期时间或有效期；**

#### 4.Cookie 应用

- **1.会话状态管理（用户登录、购物车、游戏分数）**
- **2.个性化设置（用户自定义设置、主题）**
- **3.浏览器行为跟踪（跟踪分析用户行为）**

## HTTP && Cookie

#### 创建 Cookie

![1650286120492](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650286120492.png)

 **Tip ：** **设置Cookie键值时，一次只能设置一个；** 

#### 读取 Cookie

![1650286153315](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650286153315.png)

#### 修改 Cookie

![1650286175422](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650286175422.png)

#### 删除 Cookie

<font color='red'> **Tip ：** **将名称设为空；或将其时间设置为过期时间** </font>

![1650286205036](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650286205036.png)

## 访问 && 更新 Cookie

- #### Set-Cookie 响应头

  `Set-Cookie: name=value`

- #### Cookie 请求头

  `cookie: name = value ; name = value`

 **Tip ：** **一般工况下Cookie值都是自动生成，但是我们可以手动修改** 

### cookie、localstorage、sessionstorage

 ![cookie、localStorage、sessionStorage之不同](https://img-blog.csdn.net/20180803193700323?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1NTg1NzAx/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70) 



# 7、延迟加载JS

### 延迟加载JS的方式

<font color='red'>async、defer</font>

![1649732458899](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649732458899.png)

HTML parsing：HTML解析

Script download：脚本下载

Script execution：脚本执行

![1649732807814](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649732807814.png)

#### defer

> <font color='red'>script的加载与HTML的解析同步执行的，script的执行是等HTML全部解析完成才会进行，顺次执行js脚本。</font>

#### async

> <font color='red'>script的加载是与HTML的解析同步进行的，script脚本加载完成后，停止HTML的解析，执行script脚本，js脚本的执行不是按顺序的，而是谁先加载完谁先执行。</font>

#### 例题1

> 下列选项描述正确的是：
>
> A，onload和DOMContentLoaded都是页面加载事件，没有区别
>
> B，DOMContentLoaded有浏览器兼容问题
>
> C，全局变量和函数都是window对象的属性和方法
>
> D， window对象的方法在调用时可以省略不写window
>
> 答案：BCD
>

解析：<font color='red'>onload是页面内容全部加载完触发。DOMContentLoaded是DOM元素加载完触发，且从IE9开始支持。</font>window对象是顶级对象，定义在全局作用域中的变量、函数都会变成 window 对象的属性和方法。

#### 例题2

> 关于定时器，描述正确的是：
>
> A，setTimeout()开启的定时器只会触发1次
>
> B，定时器一旦开启，不能清除
>
> C，清除定时器时需要传入定时器标识
>
> D，开启定时器时，单位是毫秒
>
> 答案：ACD
>

解析：setTimeou()相当于炸弹，只会触发1次。定时器都可以被清除，清除时需要指定清除哪个。

# 8、forEach()能不能改变原数组

<font color='orange'>**1、数组的元素是基本数据类型：无法改变原数组**</font>

![1650788949311](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650788949311.png)

<font color='orange'>**2、数组的元素是引用数据类型：直接修改整个元素对象时，无法改变原数组**</font>

![1650788965663](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650788965663.png)

<font color='orange'>**3、数组的元素是引用数据类型：修改元素对象里的某个属性时，可以改变原数组**</font>

![1650788983983](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650788983983.png)

**如果你需要通过forEach修改原数组，建议用forEach里面的参数2、参数3来做，具体代码如下：**

##### <font color='orange'>forEach()通过参数2、参数3修改原数组（标准做法）</font>

![1650457942611](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650457942611.png)

#### 总结：

如果只是遍历数组，那么可以使用forEach()方法

<font color='red'>但是，如果需要在遍历数组的同时，去改变数组里的元素内容，那么，最好是用map()方法，不要用forEach()方法，避免出现一些低级错误！</font>

# 9、sort()介绍

<font color='red'>sort()：对数组的元素进行从小到大来排序（会改变原数组）</font>

### 如果在使用sort()方法是不带参数

<font color='red'>默认排序顺序是在将元素转换为字符串按照Unicode编码，从小到大排序</font>

#### 举例1：

（当数组中的元素为字符串时）

![1650458466310](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650458466310.png)

![1650458487687](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650458487687.png)

<font color='red'>sort()会改变原数组，且方法的返回值也是同样的结果</font>

#### 举例2：

当数组中的元素为数字时

![1650458623788](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650458623788.png)

![1650458651853](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650458651853.png)

从上面可以得知：使用sort()排序后，因为是按Unicode编码排序的所以11会排在2，3，4，5的前面！！！

如果想让arr2里的元素完全按照从小到大的顺序排序，因如下操作：

### sort()方法：带参时，自定义排序规则

> <font color='red'>如果在sort()方法中带参，我们就可以目定义排序规则。</font>具体做法如下:
>
> <font color='blue'>我们可以在sort()添加一个回调函数，来指定排序规则。</font>
>
> 回调函数中需要定义两个形参，**浏览器将会分别使用数组中的元素作为实参去调用回调函数。**
>
> <font color='red'>浏览器根据回调函数的返回值来决定元素的排序：(重要)</font>
>
> 1. 如果compareFunction(a, b)小于0，那么a会被排列到b之前
> 2. 如果compareFunction(a,b)等于0，a和b的相对位置不变
> 3. 如果compareFunction(a,b)大于0，b会被排列到a之前
>
> 如果只是看上面的文字，可能不太好理解，我们来看下面的例子，你肯定就能明白

![1650459036511](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650459036511.png)

#### 举例：将数组中的数组按照从小到大的顺序排序

##### 写法1：

![1650459319085](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650459319085.png)

简化写法：

##### 写法2：

![1650459466045](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650459466045.png)

也可以写成ES6的形式，即将function改为箭头函数：

##### 写法3：箭头函数

![1650459542485](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650459542485.png)

下面这段代码，实际开发中经常用到要牢记：

![1650459855587](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650459855587.png)

![1650459863974](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650459863974.png)



## 变量提升

<font color='red'>**在提升过程中，函数声明和变量声明，函数声明优先于变量声明**</font>

![1650714260172](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650714260172.png)

**非匿名立即执行函数：函数变量是只读的，不允许修改，即a不能进行重新赋值**

# 数据类型

## 1、基本类型

## 2、引用类型

### 举例：Symbol的作用

# 判断变量的类型

## 1、typeof

## 2、instanceof及原理

## 3、Object.prototype.toString().call()及原理[[class]]

### 举例：

#### typeof null //'object'

#### 判断数组的方法

#### 判断空对象的方法

# 数据类型转换⭐⭐

## 1、相等== 和全等 ===

## 2、强制转换和隐式转换

## 3、包装类型

# 原型和原型链⭐⭐⭐

![1650691647143](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650691647143.png)

### 举例：

描述构造函数、实例和原型之间的关系

# 闭包⭐⭐⭐

## 1、优缺点

# call/apply/bind⭐⭐⭐

> 改变this指向的三种方法：
> call(newThis,arguments)、apply(newThis,arguments)、bind(newThis,arguments)
>
> call、apply会调用函数，bind不会

### 手写call()

**call()用法：**

![1650792603810](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650792603810.png)

输出：

![1650792613883](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650792613883.png)

**手写代码：**

![1650793581770](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650793581770.png)

输出：

![1650793596722](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650793596722.png)

### 手写apply()

<font color='hotpink'>注意：apply方法传入的第二个参数为数组，即是调用函数的参数所组成的数组</font>

**apply()用法：**

![1650798082500](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650798082500.png)

![1650798064794](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650798064794.png)

**手写代码：**

![1650798586692](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650798586692.png)

输出：

![1650798598567](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650798598567.png)

### 手写bind()

**bind()用法：**

![1650791207467](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650791207467.png)

![1650791223200](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650791223200.png)

**手写代码：**

![1650792345011](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650792345011.png)

输出：

![1650792357397](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650792357397.png)

# DOM事件流和事件委托⭐⭐⭐

## 1、捕获、冒泡

## 2、事件委托及好处

# 数据/对象的常见方法⭐⭐

## 1、Array：slice / splice / concat / filter / map / reduce

#### 修改器方法

> push、pop、unshift、shift、sort、reverse、splice

#### 访问方法

> concat、slice

#### 迭代方法

> forEach、filter、map、reduce

## 2、Object：keys / assign

### 举例：改变原数组的方法

# new对象时内部做了什么⭐

> 1、在内存中创建一个空对象
>
> 2、让this指向这个空对象
>
> 3、执行构造函数里的代码，给新对象添加属性和方法
>
> 4、返回这个新对象

# 防抖和节流⭐

## 1、防抖

> 防抖就是指触发事件后在 n 秒内函数只能执行一次，如果在 n 秒内又触发了事件，则会重新计算函数执行时间。 

![1650680242433](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650680242433.png)

### 防抖函数参数问题：

![1650680534270](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650680534270.png)

例如，你是一个肯德基外卖配送员，每天专门配送去学校的外卖（不考虑配送时间）。
如果每次只配送一单，肯定很划不来。
你接到一个配送订单，心里想在等3分钟，如果3分钟没有配送订单我就配送
如果又有一个配送订单，你就会想再等3分钟，
直到3分钟没有什么外卖订单，就开始配送 

**代码实现：**

![1650789961044](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650789961044.png)

## 2、节流

> 节流就是指连续触发事件但是在 n 秒中只执行一次函数。节流会稀释函数的执行频率。

例如你在打王者荣耀，你的技能在3秒能触发一次
触发一次后，3秒能将不能被触发。 

**代码实现：**

![1650789323987](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650789323987.png)

# JS动画-requestAnimationFrame⭐⭐

## 优势

# this指向⭐⭐

1. **constructor中的this指向的是new出来的实例对象**
2. <font color='red'>自定义的方法,一般也指向的new出来的实例对象</font>
3. <font color='red'>绑定事件之后this指向的就是触发事件的事件源</font>

改变this指向的三种方法：

> 1. call()
> 2. apply()
> 3. bing()

# let/var/const⭐⭐⭐

# 异步编程：Promise和async和await⭐⭐⭐

## 1、await、async、Promise

![1650679378250](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650679378250.png)

## 2、内部状态

## 3、Promise.race和Promise.all

# 箭头函数⭐⭐

# Javascript的运行机制⭐⭐⭐

## 1、单线程、解释性语言

## 2、事件循环（event loop）

## 3、宏任务/微任务

# 实现继承的方式⭐⭐

# 垃圾回收⭐

# webpack的常见配置

# 超长字符串截断如何设置css

# 如何实现遮罩弹窗布局组件

# 移动端如何实现自适应布局

# css3的动画

# 原生js读取cookie某个key的value

# js对象深拷贝

# 浏览器缓存原理

# 如何获取数组的最大值

# 各种排序的复杂度和实现方法

# Vue的响应式原理

# 父子组件通信的方式

# Vuex如何修改数据

# 双栏布局如何实现

# z-index属性

# 如何判断cjs、amd、esm规范的代码

# 图片防抖⭐⭐⭐

# node.js的event loop

# 常见的前端安全问题

## 1、什么是csrf、xss和解决方案

# 实现数组的slice方法

![1650691057229](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650691057229.png)

# 同步IO和异步IO以及应用场景

# Promise的状态

# 点击界面时打印什么

# 实现bfs返回树中值为value的节点 

bfs(root,value)

# 事件循环相关

**实现一个防抖函数，要求可以对一个事件循环内的所有调用进行防抖**

![1650691486129](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650691486129.png)

# 访问一个http请求的过程

# http1.1 http2的区别



# 字节

## 1

1、js实现[1,[2,3],[[4],[4,[4,5]]]].unique()-> [1,2,3,4,5]

2、给一段代码setTimeout和Promise的代码，写输出

3、递归多了会发生什么，怎么解决

![1650694388861](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650694388861.png)

**<font color='hotpink'>递归可能会导致递归栈溢出</font>**

改进1：

![1650694529037](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650694529037.png)

**调用栈不溢出了，但需要等待很久才有结果**<font color='red'>一次只执行一个任务</font>

**setTimeout的任务进入任务队列，当调用栈清空时，任务队列的任务进调用栈。**

改进2：

<font color='red'>一次执行part个任务</font>

![1650694850499](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650694850499.png)

4、浏览器访问一个url所展示页面的流程

5、域名服务器（DNS）的详细过程

6、TCP三次握手

7、UDP

8、网络分层

9、强缓存、协商缓存、缓存涉及的headers

10、script为什么放在页面的底部

二面

1、如何资源有了就不用请求了？缓存相关，如何减少传输体积？gzip相关

2、如果实现上传图片的功能，前后端分别怎么做

3、实现前端预览图片

4、前后端如何鉴别不同用户，cookie、session相关

5、leetcode394：字符串解码

三面

1、常见的设计模式，Vue中用到了哪些设计模式

2、小程序的工作原理

3、leetcode200：岛屿数量（额外求出每个岛屿的面积）

4、JS实现函数：并发多个请求，返回先得到response的，函数输入为url数组，输出为第一个返回的response的结果

## 2

### 1、输出结果？原因

![1650711381347](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650711381347.png)

输出：1，4

原因：<font color='hotpink'>**JS中空字符串与0相等**</font>、<font color='hotpink'>JS中空数组为true，空对象为true，但空对象！=空对象，空字符串为false，0为false</font>

<font color='red'>**对象和数组都是引用类型，两个单独的对象和数组永不相等，因为是引用类型，只有当它们引用同一个基对象时才相等**</font>

**任意值与布尔值比较，都会将两边的值转化为Number** 

#### 空数组判断：

<font color='hotpink'>**当空数组作为判断条件时，相当于true **</font>

![1650711850018](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650711850018.png)

#### 空对象的判断：

1、for...in遍历

![1650712437677](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650712437677.png)

2、JSON.stringify

![1650712490805](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650712490805.png)

![1650711940523](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650711940523.png)

3、Object.keys(obj).length

![1650712551115](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650712551115.png)

> **将其他数据类型转换为Number**
>
> 转换方式一：
>
> 1、使用Number()函数
>
> 1. 字符串 -->数字
>
> - **如果是纯数字的字符串,则直接将其转换为数字**
> - **如果字符串中有非数字内容,则转换为NaN**
> - <font color='red'>如果字符串是一个空串或者是一个全是空格的字符串，则转换为0</font>
>
> 2. 布尔 -->数字
>
> - true 转成1
> - false 转成0
>
> 3. null -->数字 0
>
> 4. undefind --> 数字NaN
>
> 转换方式二：
>
> 2、这种方式专门用于字符串
>
> - parseInt() 把一个字符串转换为一个整数
> - parseFloat() 把一个字符串转换为一个浮点数

### 2、闭包

![1650713282935](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650713282935.png)

存在问题：输出全为200

- 使用立即执行函数解决闭包

  #### 立即执行函数

  > 1. 定义 ： 此类的函数没有声明，**在一次执行过后释放（被销毁）**，适合做初始化工作，针对初始化功能的函数，只想让他执行一次的函数，立即执行函数也有参数，也有返回值，也能预编译。
  > 2. ![1650714538687](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650714538687.png)

  ![1650715179858](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650715179858.png)

- 使用promise解决闭包

  ![1650715537883](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650715537883.png)

### 3、输入url发生了什么

①输入URL后

②浏览器向服务器发起了一个请求，传输了一些数据。

③服务器接收到请求后

④作出了相应的处理，然后返回数据到浏览器。

⑤浏览器再做相应的处理，最后将页面展现在我们面前。 

>  1. DNS域名解析；
>   2. 建立TCP连接；
>   3. 发送HTTP请求；
>   4. 服务器处理请求；
>   5. 返回响应结果；
>   6. 关闭TCP连接；
>   7. 浏览器解析HTML；
>   8. 浏览器布局渲染；

##### 1.DNS域名解析

我们在浏览器输入网址，其实**就是要向服务器请求我们想要的页面内容**，<font color='red'>所有浏览器首先要确认的是域名所对应的服务器在哪里。</font>**<font color='hotpink'>将域名解析成对应的服务器IP地址这项工作，是由DNS服务器来完成的。</font>**

客户端收到你输入的域名地址后，它首先去找本地的hosts文件，检查在该文件中是否有相应的域名、IP对应关系，如果有，则向其IP地址发送请求，如果没有，再去找DNS服务器。一般用户很少去编辑修改hosts文件。

>  浏览器会对一些默认的东西进行补齐。例如：互联网url默认端口号为80，浏览器默认补齐功能会补齐协议http，有些还会直接在域名前面补上www。所以实际上，即使我们输入的是imooc.com，然而实际访问的却是http://www.imooc.com 

 ![图片描述](https://img1.sycdn.imooc.com/5a13cb8f0001416b11530480.png)

**dns解析**分为以下几个步骤：

1. 先查看**浏览器dns缓存**中是否有域名对应的ip。
2. 如果没有，则查看**操作系统dns缓存**中是否有对应的ip（例如windows的hosts文件）。
3. 依旧没有就对**本地区的dns服务器**发起请求，
4. 如果还是没有，就直接到Root Server域名服务器请求解析。
   - DNS在进行区域传输的时候使用TCP协议，其它时候则使用UDP协议；
   - 全球只有十三台逻辑根服务器 

 ![图片描述](https://img1.sycdn.imooc.com/5a13cba100011d3808050478.png) 

浏览器客户端向本地DNS服务器发送一个含有域名www.cnblogs.com的DNS查询报文。**本地DNS服务器把查询报文转发到根DNS服务器，**根DNS服务器注意到**其com后缀，于是向本地DNS服务器返回comDNS服务器的IP地址。**本地DNS服务器再次向comDNS服务器发送查询请求，comDNS服务器注意到其www.cnblogs.com后缀并用**负责该域名的权威DNS服务器的IP地址作为回应。**最后，本地DNS服务器将含有www.cnblogs.com的IP地址的响应报文发送给客户端。

> <font color='red'>从客户端到本地服务器属于递归查询，而DNS服务器之间的交互属于迭代查询。</font>
>
> 正常情况下，本地DNS服务器的缓存中已有comDNS服务器的地址，**因此请求根域名服务器这一步不是必需的。**

##### 2.建立TCP连接

 **<font color='hotpink'>通过ip寻址和arp，找到目标（服务器）地址，三次握手建立TCP连接</font>**

 ![图片描述](https://img1.sycdn.imooc.com/5a13cbf200019d0b05920331.png)

> 上图也可以这么理解：
>
> 客户端：“你好，在家不，有你快递。”
>
> 服务端：“在的，送来就行。”
>
> 客户端：“好嘞。” 

客户端发送一个带有SYN标志的数据包给服务端，服务端收到后，回传一个带有SYN/ACK标志的数据包以示传达确认信息，最后客户端再回传一个**带ACK标志的数据包，代表握手结束，连接成功。**

>  ip协议在第三层互联网层（网络层），arp协议在第四层网络访问层（链路层）。第2步获取到了ip，此时直接通过ip寻址找到ip对应的服务器，然后通过arp协议找到服务器的mac地址。
>
> **ip寻址**主要有两种方式，一种是同一网段，一种是不同网段。要判断两个IP地址是不是在同一个网段，就将它们的IP地址分别与子网掩码做与运算，得到的结果一网络号，如果网络号相同，就在同一子网，否则，不在同一子网。**arp就是地址转化协议，也就是把ip地址转化为mac地址。和dns很像，先查缓存，然后查路由器。**
>
> 为什么有了ip地址，还要mac地址？这个问题很关键，就像是我有驾驶证了你非要让我提供身份证。这个涉及一些历史问题，因为一开始没有互联网的时候就只有mac地址，还不存在ip地址。后来互联网越来越大之后，发现mac地址找起来太麻烦，并且耗时也越来越久，就发明了ip地址。并且mac地址在一个局域网中还是很有用的，所以就两个一起存在了。
>
> 第三步我们找到了目标ip，并获得了服务器ip的mac地址。此时浏览器就会请求和服务器连接，用来传输数据。**<font color='hotpink'>tcp 是稳定双向面向连接的，断开时也会分两边分别断开</font>**。面向连接不是说tcp一个双方一直开着的通道，而是维持一个连接的状态，让它看起来有连接。

##### 3.发送HTTP请求

与服务器建立了连接后，就可以向服务器发起请求了。这里我们先看下请求报文的结构（如下图）：

 ![图片描述](https://img1.sycdn.imooc.com/5a13cc3b0001155706290169.png) 

在浏览器中查看报文首部（以google浏览器为例）：

 ![图片描述](https://img1.sycdn.imooc.com/5a13cc510001e98103660273.png) 

<font color='red'>请求行包括请求方法、URI、HTTP版本。</font>**首部字段传递重要信息，包括请求首部字段、通用首部字段和实体首部字段。**我们可以从报文中看到发出的请求的具体信息。具体每个首部字段的作用，这里不做过多阐述。

> **<font color='hotpink'>主体：请求头部和主体之间有一个回车换行。如果是get请求，则没有主体部分，post请求有主体部分。</font>**

##### 4.服务器处理请求

服务器端收到请求后的由web服务器（准确说应该是http服务器）处理请求，诸如Apache、Ngnix、IIS等。web服务器解析用户请求，知道了需要调度哪些资源文件，再通过相应的这些资源文件处理用户请求和参数，并调用数据库信息，最后将结果通过web服务器返回给浏览器客户端。

 ![图片描述](https://img1.sycdn.imooc.com/5a13cc7b00011aef08080237.png) 

> 浏览器请求报文到达服务器之后，服务器接口会对请求报文进行处理，执行接口对应的代码，处理完成后响应客户端。**由于http是无状态的**，正常情况下，**客户端收到响应后就会直接断开连接，然后一次http事物就完成了。但是http1.0有一个keep-alive的请求字段，可以在一定时间内不断开连接（有时时间甚至很长）**。http1.1直接就默认开启了keep-alive选项。<font color='red'>这导致了一个后果是服务器已经处理完了请求，但是客户端不会主动断开连接，这就导致服务器资源一直被占用。</font>这时服务器就不得不自己主动断开连接，而主动断开连接的一方会出现TIME_WAIT，占用连接池，这就是产生SYN Flood攻击的原因。 

##### 5.返回响应结果

在HTTP里，有请求就会有响应，哪怕是错误信息。这里我们同样看下响应报文的组成结构：

 ![图片描述](https://img1.sycdn.imooc.com/5a13cc8b00017f7b06250168.png) 

在响应结果中都会有一个HTTP状态码，比如我们熟知的200、301、404、500等。**通过这个状态码我们可以知道服务器端的处理是否正常，并能了解具体的错误。**

<font color='red'>状态码由3位数字和原因短语组成。根据首位数字，状态码可以分为五类：</font>

 ![图片描述](https://img1.sycdn.imooc.com/5a13ccb6000139cd04170192.png) 

> 需要关注一个报文头--accept。<font color='red'>accept代表发送端（客户端）希望接受的数据类型，这是浏览器自动封装的请求头。</font>**如果服务器返回的content-type是accept中的任何一个，浏览器都能解析**，并直接展示在网页上。如果服务器返回的content-type是其他类型，此时浏览器有三种处理状态：
>
> 1. 正常显示。例如返回类型为text/javascript，浏览器能直接处理并展示。
> 2. 下载。例如返回类型为application/octet-stream（二进制流，不知道下载文件类型），这种浏览器不能直接处理的，会被下载。
> 3. 报错。当我们返回一个字符串hello world，却使用text/xml，格式时，浏览器不能正确解析，就会报错，并把报错信息呈现在网页中。
>
> 浏览器能直接处理很多种格式，并直接呈现在网页中，并不限于accept中规定的字段。

##### 6.关闭TCP连接

<font color='blue'>为了避免服务器与客户端双方的资源占用和损耗，当双方没有请求或响应传递时，任意一方都可以发起关闭请求。</font>与创建TCP连接的3次握手类似，关闭TCP连接，需要4次握手。

 ![图片描述](https://img1.sycdn.imooc.com/5a13ccc300011e4804890374.png) 

> 客户端：“兄弟，我这边没数据要传了，咱关闭连接吧。”
>
> 服务端：“收到，我看看我这边有木有数据了。”
>
> 服务端：“兄弟，我这边也没数据要传你了，咱可以关闭连接了。”
>
> 客户端：“好嘞。
>

##### 7.浏览器解析HTML

**准确地说，浏览器需要加载解析的不仅仅是HTML，还包括CSS、JS。以及还要加载图片、视频等其他媒体资源。**

浏览器通过解析HTML，生成DOM树，解析CSS，生成CSS规则树，然后通过DOM树和CSS规则树生成渲染树。渲染树与DOM树不同，渲染树中并没有head、display为none等不必显示的节点。

要注意的是，浏览器的解析过程并非是串连进行的，比如在解析CSS的同时，可以继续加载解析HTML，**<font color='hotpink'>但在解析执行JS脚本时，会停止解析后续HTML，这就会出现阻塞问题，</font>**关于JS阻塞相关问题，这里不过多阐述,后面会单独开篇讲解。

##### 8.浏览器布局渲染

根据渲染树布局，计算CSS样式，即每个节点在页面中的大小和位置等几何信息。**HTML默认是流式布局的，CSS和js会打破这种布局，改变DOM的外观样式以及大小和位置。这时就要提到两个重要概念：replaint和reflow。**

1. replaint：屏幕的一部分重画，不影响整体布局，比如某个CSS的背景色变了，但元素的几何尺寸和位置不变。
2. reflow： 意味着元件的几何尺寸变了，我们需要重新验证并计算渲染树。是渲染树的一部分或全部发生了变化。这就是Reflow，或是Layout。

所以我们应该尽量减少reflow和replaint，我想这也是为什么现在很少有用table布局的原因之一。

最后浏览器绘制各个节点，将页面展示给用户。



（下面三个小问题是说完后追问的）

- 对光栅化的深入了解
- Draw Quad了解多少
- 加载js阻塞 解决方案

## 浏览器渲染

**浏览器主要组件结构**

 ![img](http://blog.cnezsoft.com/file.php?f=201802/f_709ccf8878144f9619f62a141c816393&t=png&o=&s=&v=1518076672) 

**渲染引擎——webkit和Gecko**

Firefox使用Geoko——Mozilla自主研发的渲染引擎。

Safari和Chrome都使用webkit。Webkit是一款开源渲染引擎，它本来是为linux平台研发的，后来由Apple移植到Mac及Windows上。

主要以webkit渲染引擎来讲解，尽管webkit和Gecko使用的术语稍有不同，他们的主要流程基本相同。

**webkit渲染引擎流程： **

 ![img](http://blog.cnezsoft.com/file.php?f=201802/f_237cb519bf7f45b12da84484ee8bc561&t=png&o=&s=&v=1518145491) 

#### 关键渲染路径

<font color='hotpink'>关键渲染路径是指浏览器从最初接收请求来的HTML、CSS、javascript等资源，然后解析、构建树、渲染布局、绘制，最后呈现给客户能看到的界面这整个过程。</font>

所以浏览器的渲染过程主要包括以下几步：

1. 解析HTML生成DOM树。
2. 解析CSS生成CSSOM规则树。
3. 将DOM树与CSSOM规则树合并在一起生成渲染树。
4. 遍历渲染树开始布局，计算每个节点的位置大小信息。
5. 将渲染树每个节点绘制到屏幕。

##### 构建DOM树

当浏览器接收到服务器响应来的HTML文档后，会遍历文档节点，生成DOM树。

需要注意的是，DOM树的生成过程中可能会被CSS和JS的加载执行阻塞。渲染阻塞问题下文会讲。

##### 构建CSSOM规则树

 浏览器解析CSS文件并生成CSS规则树，每个CSS文件都被分析成一个StyleSheet对象，每个对象都包含CSS规则。<font color='red'>CSS规则对象包含对应于CSS语法的选择器和声明对象以及其他对象。 </font>

#### 渲染阻塞

<font color='blue'>当浏览器遇到一个 script 标记时，DOM 构建将暂停，直至脚本完成执行，然后继续构建DOM。</font>每次去执行JavaScript脚本都会严重地阻塞DOM树的构建，如果JavaScript脚本还操作了CSSOM，而正好这个CSSOM还没有下载和构建，浏览器甚至会延迟脚本执行和构建DOM，直至完成其CSSOM的下载和构建。 

所以，script 标签的位置很重要。实际使用时，可以遵循下面两个原则：

> 1. <font color='hotpink'>**CSS 优先：引入顺序上，CSS 资源先于 JavaScript 资源。**</font>
> 2. **<font color='green'>JS置后：我们通常把JS代码放到页面底部，且JavaScript 应尽量少影响 DOM 的构建。</font>**

当解析html的时候，会把新来的元素插入dom树里面，同时去查找css，然后把对应的样式规则应用到元素上**，查找样式表是按照从右到左的顺序去匹配的。**

例如： div p {font-size: 16px}，会先寻找所有p标签并判断它的父标签是否为div之后才会决定要不要采用这个样式进行渲染）。

所以，我们平时写CSS时，尽量用id和class，千万不要过渡层叠。

##### 构建渲染树

通过DOM树和CSS规则树我们便可以构建渲染树。浏览器会先从DOM树的根节点开始遍历每个可见节点。对每个可见节点，找到其适配的CSS样式规则并应用。

<font color='blue'>渲染树构建完成后，每个节点都是可见节点并且都含有其内容和对应规则的样式。</font>这也是渲染树与DOM树的最大区别所在。**渲染树是用于显示，那些不可见的元素当然就不会在这棵树中出现了，譬如。除此之外，display等于none的也不会被显示在这棵树里头，但是visibility等于hidden的元素是会显示在这棵树里头的。** 

##### 渲染树布局

布局阶段会从渲染树的根节点开始遍历，然后确定每个节点对象在页面上的确切大小与位置，布局阶段的输出是一个盒子模型，它会精确地捕获每个元素在屏幕内的确切位置与大小。 

##### 渲染树绘制

在绘制阶段，遍历渲染树，调用渲染器的paint()方法在屏幕上显示其内容。**渲染树的绘制工作是由浏览器的UI后端组件完成的。** 

###### reflow与repaint：

根据渲染树布局，计算CSS样式，即每个节点在页面中的大小和位置等几何信息。HTML默认是流式布局的，CSS和js会打破这种布局，改变DOM的外观样式以及大小和位置。这时就要提到两个重要概念：repaint和reflow。

> 1. repaint：屏幕的一部分重画，不影响整体布局，比如某个CSS的背景色变了，但元素的几何尺寸和位置不变。
> 2. reflow： 意味着元件的几何尺寸变了，我们需要重新验证并计算渲染树。是渲染树的一部分或全部发生了变化。这就是Reflow，或是Layout。 

display:none 会触发 reflow，visibility: hidden属性并不算是不可见属性，它的语义是隐藏元素，但元素仍然占据着布局空间，它会被渲染成一个空框，所以visibility:hidden 只会触发 repaint，因为没有发生位置变化。

<font color='blue'>有些情况下，比如修改了元素的样式，浏览器并不会立刻 reflow 或 repaint 一次，而是会把这样的操作积攒一批，然后做一次 reflow，这又叫异步 reflow 或增量异步 reflow。</font>

有些情况下，比如 resize 窗口，改变了页面默认的字体等。对于这些操作，浏览器会马上进行 reflow。

### 4、简述TCP三次握手、四次挥手

#### 1.TCP概念

<font color='red'>TCP是面向连接、可靠的进程到进程通信的协议。</font>TCP提供双全工服务，**即数据可在同一时间双向传输，每一个TCP都有发送缓存和接受缓存，用来临时存储数据。**

#### 2.TCP套接字

TCP协议规定，端口号拼接到IP地址即构成套接字——TCP连接的端点。

<font color='hotpink'>**套接字（socket)=[IP地址：端口号]**</font>

TCP连接用式子表示为

TCP连接::={socket1,socket2}={(IP1：port1) ，（IP2：port2)} 

#### 3.TCP中客户与服务器

在面向连接通信中，连接的建立和断开是非常频繁的过程。**TCP连接的建立采用客户服务器方式，主动发起连接建立的应用进程成为客户，而被动等待连接的应用进程成为服务器。** 

#### 4.TCP报文协议

 ![img](https://img-blog.csdn.net/20180717201939345?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4OTUwMzE2/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70) 

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200514165843513.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ3ODAyMDkw,size_16,color_FFFFFF,t_70) 

> 源端口号：数据发起者的端口号，16bit。
>
> 目的端口号：数据接收者的端口号，16bit。
>
> 序号：32bit的序列号，由发送方使用。
>
> 确认序号：32bit的确认号，**是接收数据方期望收到发送方的下一个报文段的序号，因此确认序号应当是上次已成功收到数据字节序号加1。**
>
> 首部长度：首部中32bit字的数目，可表示15*32bit=60字节的首部。一般首部长度为20字节
>
> 保留：6bit, 均为0
>
> 紧急URG：当URG=1时，表示报文段中有紧急数据，应尽快传送。
>
> **<font color='hotpink'>确认比特ACK：ACK = 1时代表这是一个确认的TCP包，取值0则不是确认包。</font>**
>
> 推送比特PSH：当发送端PSH=1时，接收端尽快的交付给应用进程。
>
> **<font color='hotpink'>复位比特（RST）：当RST=1时，表明TCP连接中出现严重差错，必须释放连接，再重新建立连接。</font>**
>
> **<font color='blue'>同步比特SYN：在建立连接是用来同步序号。SYN=1， ACK=0表示一个连接请求报文段。SYN=1，ACK=1表示同意建立连接。</font>**
>
> **<font color='green'>终止比特FIN：FIN=1时，表明此报文段的发送端的数据已经发送完毕，并要求释放传输连接。</font>**
>
> 窗口：用来控制对方发送的数据量，通知发放已确定的发送窗口上限。
>
> 检验和：该字段检验的范围包括首部和数据这两部分。由发端计算和存储，并由收端进行验证。
>
> 紧急指针：紧急指针在URG=1时才有效，它指出本报文段中的紧急数据的字节数。
>
> 选项：长度可变，最长可达40字节。

![1650768896038](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650768896038.png)

#### 5.TCP报文的序列号Seq和确认号Ack

> 1. 序列号（sequence number）：Seq序号，占32位，**用来标识从TCP源端向目的端发送的字节流，发起方发送数据时对此进行标记。**
> 2. 确认号（acknowledgement number）：Ack序号，占32位，只有ACK标志位为1时，确认序号字段才有效，<font color='red'>Ack=Seq+1。 </font>

### TCP连接建立三握手，连接断开四挥手

#### 1.连接三握手

> 1. 由客户端向服务器发送一段TCP报文：
>    - 控制位为SYN，SYN置为1，表示“请求建立新连接”
>    - 序号为Seq=X（X一般为0）
>
> ​       随后客户端进入SYN-SENT阶段
>
> 2. 服务器端接收到来自客户端的TCP报文之后，结束LISTEN阶段。并向客户端发送一段TCP报文：
>
>    - 控制位为SYN和ACK，SYN、ACK置为1，表示“确认客户端的报文Seq序列号为有效，服务器能正常接收客户端发送的数据，并同意创建新连接（即告诉客户端，服务器收到了你的数据）
>    - 序列号为Seq=y（y一般为0）
>    - 确认号为ACK=x+1，表示收到客户端的序列号Seq并将其值加一作为自己确认号ACK的值。
>
>    随后服务器端进去SYN-RCVD阶段
>
> 3. 客户端接收到来自服务器端的确认收到数据的TCP报文之后，明确了从客户端到服务器的数据传输是正常的，结束SYN-SENT阶段。并返回最后一段TCP报文：
>
>    - 控制位为ACK，ACK置为1，表示”确认收到服务器同意链接的信号“
>    - 序列号为Seq=x+1，表示收到服务器端发送的确认好ACK，并将其作为自己的序列号值。
>    - 确认号为ACK=y+1，表示收到服务器端序列号Seq，并将其值加1作为自己的确认号ACK的值
>
>    随后客户端进入ESTABLISHED阶段
>
>     ![img](https://img-blog.csdn.net/20180717202520531?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4OTUwMzE2/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70) 

**服务器收到来自客户端的“确认收到服务器数据”的TCP报文之后，明确了从服务器到客户端的数据传输是正常的。结束SYN-SENT阶段，进入ESTABLISHED阶段。**此后客户端和服务器端进行正常的数据传输。这就是“三次握手”的过程。 

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200514154724497.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ3ODAyMDkw,size_16,color_FFFFFF,t_70) 

#### 2.断开四挥手

> 1. 首先客户端想要断开连接，向服务器端发送一段TCP报文：
>
>    - 控制位为FIN，FIN置为1，表示”请求释放连接“
>    - 序列号为Seq=W;
>
>    随后客户端进入FIN-WAIT-1阶段，即半关闭阶段；并且停止在客户端到服务器端方向上发送数据，但是客户端仍然能接收从服务器端传输过来的数据。
>
> 2. 服务器端接收到从客户端发出的TCP报文之后，确认了客户端想要释放连接，随后服务器端结束ESTABLISHED阶段，进入CLOSE-WAIT阶段（半关闭阶段）并返回一段TCP报文。
>
>    - 控制位为ACK，ACK置为1，表示”接收到客户端发送的释放连接的请求“
>    - 序列号为Seq=Z;
>    - 确认号为ACK=W+1，表示是在收到客户端报文的基础上，将其序列号Seq值加1作为本段报文确认号ACK的值。
>
>    随后客户端结束FIN-WAIT-1阶段，进入FIN-WAIT-2阶段。
>
> 3. 服务器端自从发出ACK确认报文之后，再次向客户端发出一段TCP报文：
>
>    - 控制位为FIN、ACK，FIN、ACK置为1，表示”已经准备好释放连接了“，注意：这里的ACK并不是确认收到服务器端报文的确认报文。
>    - 序列号为Seq=Z;
>    - 确认号为ACK=W+1；表示是在收到客户端报文的基础上，将其序列号Seq值加1作为本段报文确认号ACK的值。
>
>    随后服务器端结束CLOSE-WAIT阶段，进入LAST-ACK阶段。
>
> 4. 客户端收到从服务器端发出的TCP报文，确认服务器端已做好释放连接的准备，结束FIN-WAIT-2阶段，进入TIME-WAIT阶段，并向服务器端发送一段报文：
>
>    - 控制位为ACK，ACK置为1，表示“接收到服务器准备好释放连接的信号”
>    - 序列号为Seq=W+1；表示是在收到了服务端报文的基础上，将其确认号ACK值作为本段报文序号的值。
>    - 确认号为ACK=Z+1；表示是在收到了服务器端报文的基础上，将其序号Seq值增加1作为本段报文确认号的值。
>
>    随后客户端结束TIME-WAIT阶段，进入CLOSED阶段，由此完成“四次挥手”
>
>     ![img](https://img-blog.csdn.net/20180717204202563?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4OTUwMzE2/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70) 

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200514161850932.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ3ODAyMDkw,size_16,color_FFFFFF,t_70) 

三次握手四次挥手完整图示：

![1650768844023](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650768844023.png)

### 常见面试题：

**1、为什么连接的时候是三次握手，关闭的时候却是四次挥手**

> 因为当服务器端收到客户端的SYN连接请求报文后，可以直接发送SYN+ACK报文。其中ACK报文是用来应答的，SYN报文是用来同步的。**但是关闭连接时，当服务器端收到FIN报文时，很可能并不会立即关闭SOCKET，所以只能先回复一个ACK报文，告诉客户端，"你发的FIN报文我收到了"。只有等到我服务器端所有的报文都发送完了，我才能发送FIN报文，**因此不能一起发送。故需要四步握手。

**2、为什么TIME-WAIT状态需要经过2MSL（最大报文段生存时间）才能返回到CLOSE状态**

> 虽然按道理，四个报文都发送完毕，我们可以直接进入CLOSE状态了，但是我们必须假想网络是不可靠的，有可以最后一个ACK丢失。<font color='blue'>所以TIME_WAIT状态就是用来重发可能丢失的ACK报文。</font>在客户端发送出最后的ACK回复，但该ACK可能丢失。<font color='red'>服务器端如果没有收到ACK，将不断重复发送FIN片段。</font>所以客户端不能立即关闭，它必须确认服务器端接收到了该ACK。**客户端会在发送出ACK之后进入到TIME_WAIT状态。客户端会设置一个计时器，等待2MSL的时间。如果在该时间内再次收到FIN，那么客户端会重发ACK并再次等待2MSL。**所谓的2MSL是两倍的MSL(Maximum Segment Lifetime)。MSL指一个片段在网络中最大的存活时间，<font color='blue'>2MSL就是一个发送和一个回复所需的最大时间。</font><font color='hotpink'>如果直到2MSL，客户端都没有再次收到FIN，那么客户端推断ACK已经被成功接收，则结束TCP连接。</font>

**3、为什么不能用两次握手进行连接？**

> 3次握手完成两个重要的功能，<font color='red'>既要双方做好发送数据的准备工作(双方都知道彼此已准备好)，也要允许双方就初始序列号进行协商，这个序列号在握手过程中被发送和确认。</font>
>
> 现在把三次握手改成仅需要两次握手，**死锁是可能发生的**。作为例子，考虑计算机Server和Client之间的通信，假定C给S发送一个连接请求分组，S收到了这个分组，并发送了确认应答分组。按照两次握手的协定，S认为连接已经成功地建立了，可以开始发送数据分组。**可是，C在S的应答分组在传输中被丢失的情况下，将不知道S 是否已准备好，不知道S建立什么样的序列号，C甚至怀疑S是否收到自己的连接请求分组。**在这种情况下，**C认为连接还未建立成功，将忽略S发来的任何数据分组，只等待连接确认应答分组。**而**S在发出的分组超时后，重复发送同样的分组。这样就形成了死锁。**<font color='hotpink'>两次握手无法确认客户端的接收能力</font>

**4、如果已经建立了连接，但是客户端突然出现故障了怎么办？**

> TCP设有一个保活计时器，显然，**客户端如果出现故障，服务器不能一直等下去，白白浪费资源。**<font color='red'>服务器每收到一次客户端的请求后都会重新复位这个计时器，时间通常是设置为2小时，若两小时还没有收到客户端的任何数据，服务器就会发送一个探测报文段，以后每隔75秒钟发送一次。若一连发送10个探测报文仍然没反应，服务器就认为客户端出了故障，接着就关闭连接。</font>

### 5、TCP建立连接的过程，为什么要三次握手，最后一次可以携带数据吗？为什么结束过程需要四次握手？

见上文。

#### 三次握手的目的：

<font color='hotpink'>**确认**双方的**发送能力**和**接受能力**。</font>

> 1. 第一次握手：最开始双方都处于CLOSED状态。然后服务端B开始监听某个端口，进入了LISTEN状态。客户端A发送SYN =1，初始序列seq=x。同时A进入SYN-SEN（同步已发送）状态。
> 2. 第二次握手：B收到连接请求报文段后，如同意建立连接，则向A发送SYN=1，ACK=1，确认号ack=x+1，同时也为自己选择一个初始序号seq=y。B同时进入SYN-RCVD（同步收到）状态。
> 3. 第三次握手：A收到B确认后，还要向B发送确认。确认报文ACK=1，自己序号seq = x+1，确认号ack=y+1，这时TCP已经建立连接。A进入ESTABLISHED(已经建立连接)状态。
>    B收到A确认后，也进入ESTABLISHED(已经建立连接)状态。

面试回答三次握手：

> - 从最开始双方都处于CLOSED状态。然后服务端开始监听某个端口，进入了LISTEN状态。
>
> - 然后客户端主动发起连接，发送 SYN , 自己变成了SYN-SENT状态。
>
> - 服务端接收到，返回SYN和ACK(对应客户端发来的SYN)，自己变成了SYN-REVD。
>
> - 之后客户端再发送ACK给服务端，自己变成了ESTABLISHED状态；服务端收到ACK之后，也变成了ESTABLISHED状态

前两次握手SYN报文不能携带数据，但要消耗掉一个序号。

<font color='red'>**第三次握手 ACK报文段可以携带数据，但如果不携带数据则不消耗序号。**</font>

凡是需要对端确认的，一定消耗TCP报文的序列号。 

> 首先，如果第一次握手可以携带数据，要是有人恶意攻击服务器，他每次都在第一次握手中的SYN报文中放入大量的数据，因为攻击者根本就不理服务器的接收发送功能是否正常，然后疯狂重复发送SYN报文的话，服务器就会花费很长时间、内存空间来接收这些报文。 所以第一次是不可以放数据的，<font color='red'>说简单点就是第一次握手会让服务器更容易受到攻击。</font>而第三次的话，此时的客户端已经处于ECTABLISHED状态，对于客户端来说，他已经建立起了连接，并且也已经知道服务器的接收、发送功能是正常的了，所以ACK包就能携带数据也是可行的。  

### 6、全连接队列和半连接队列

### 7、syn攻击

### 8、响应式原理、defineProperty缺点及改进

### 9、JavaScript中reduce方法的手动实现

## 3

### 1、js如何实现绑定

call、bind、apply

### 2、浏览器的存储机制

> **<font color='hotpink'>浏览器端包括三种本地存储机制，分别为cookie、localStorage、sessionStorage</font>**

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190905151836366.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dhbnRpbmd0cg==,size_16,color_FFFFFF,t_70) 

浏览器存储的数据类型都是字符串，通常需将对象序列化为字符串

#### cookie

> HTTP协议是一种无状态协议，在前端请求服务器对任何HTTP请求都需要携带cookie，其中包含着会话信息，用来辨别用户身份。
>
> 服务端生成，客户端进行维护和存储，cookie的本职工作并非本地存储，而是维持状态。

**原理及生成方式**

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190905151909510.png) 

**cookie的缺陷：**

> 1. 不够大，限制在4KB左右，某些浏览器会对cookie的数量做限制
> 2. 过多的cookie会带来性能浪费（同一域名下的所有请求都会携带Cookie）
>    -  对于静态文件的请求，携带cookie信息根本没有用，此时可以通过**cdn（存储静态文件的）的域名和主站的域名分开**来解决。 
> 3.  在HTTP请求中的Cookie是明文传递的, 不够安全，除非用HTTPS 
>    - 如果包含服务端 Session 信息的 Cookie 不想被客户端 JavaScript 脚本调用，那么就应该为其设置`HttpOnly`标记。否则，通过js的Document.cookie API可以直接访问和修改cookie, 出现XSS攻击 

**cookie与session的区别和联系**

session和cookie的区别：

- <font color='hotpink'>Cookie是浏览器端的存储对象</font>，有容量限制，通过HTTP报文与后端交互
- <font color='hotpink'>Session是服务端的存储对象</font>，实现的方式可以有文件系统、缓存系统、数据库。

session和cookie的联系

- Session和Cookie都是为了实现HTTP请求带上客户端状态的方法
- Session大多数情况下都是依赖Cookie来传递Session ID

<font color="red">手写Cookie</font>

![1650776318516](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650776318516.png)

**localStorage**

通过localStorage可以将数据存储在客户端，并且可以通过localStorage.setItem/localStorage.getItem调用。

> 1. localStorage用于将大量数据（最大5M）保存在浏览器中
> 2. 保存后永久存储，除非用JS手动清除
> 3. 不参与网路传输
> 4. 一般用于性能优化，主要用于保持大量数据

**sessionStorage**

通过sessionStorage.setItem/sessionStorage.getItem调用。

> - 建议存储一些当前页面刷新需要存储，且不需要在tab关闭时留下的信息
> - 可以用sessionStorage来检测用户是否是刷新进入的页面。

**sessionStorage和localStorage的区别：**

> 共同点：都是保存在浏览器端，且都遵循同源策略。

> 不同点：在于生命周期与作用域的不同
>
> - 作用域：localStorage只要在相同的协议、主机名、端口下，就能读取/修改到同一份localStorage数据。sessionStorage除此之外还要求在同一窗口。
> - 生命周期：localStorage是持久化的本地存储，不会过期，只能手动删除；而sessionStorage是临时性的本地存储

#### IndexedDB

Web Storage只能用来存储字符串，只能存储**较少量的数据**，<font color='hotpink'>遇到大规模且结构复杂的数据时，需要使用IndexedDB。</font>

IndexedDB用于**客户端存储大量结构化数据**。是一个**运行在浏览器上的非关系型数据库**。是没有存储上限，不仅可以存储字符串，还可以存储二进制数据。

###### cache

在进行第一次连接时，所有资源都需要客户端向服务端获取。并且浏览器会缓存一部分**资源**到**本地cache**， 当再次连接时，直接从浏览器获取即可。如果服务器更新了资源，再重新获取。怎样判断是否需要重新获取？就是下文的[浏览器缓存](https://so.csdn.net/so/search?q=浏览器缓存&spm=1001.2101.3001.7020)机制的作用了。 

![1650776925356](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650776925356.png)

#### 浏览器缓存机制

**缓存过程**

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190905152222296.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dhbnRpbmd0cg==,size_16,color_FFFFFF,t_70) 

> 1. 浏览器每次发起请求，都会**先在浏览器缓存中查找该请求的结果以及缓存标识**
> 2. 拿到返回的请求结果后，都会**将该结果和缓存标识存入浏览器缓存中**
> 3. 浏览器对于缓存的处理是**根据第一次请求资源时返回的响应头来确定的。**

**<font color='hotpink'>根据缓存机制的不同，分为强缓存与协商缓存。</font>**

- 强缓存之所以叫强缓存，是因为缓存有效与否，**只看时间**。只要已过期，缓存无效，需要重新请求。
- 协商缓存则现需与服务器交互一次，拿到最新的协商缓存响应头，比较**服务端的资源是否有更新**。

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190905152454739.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dhbnRpbmd0cg==,size_16,color_FFFFFF,t_70) 

##### 强缓存

**不会向服务器发送请求**，**直接从缓存中读取资源**

- 在chrome的Network中可以看到该请求返回200的状态码
- Size显示from disk cache或from memory cache。

通过设置两种 HTTP Header 实现：Expires 和 Cache-Control。

##### Expires(HTTP/1.0)

缓存过期时间，**用来指定资源到期的时间**，**是服务器端的具体的时间点**。

1. Expires=max-age + 请求时间，需要和Last-modified结合使用。
2. Web**服务器响应消息头字段**
3. 受限于本地时间，如果修改了本地时间，可能会造成缓存失效。

##### Cache-Control (HTTP/1.1)

Cache-Control 可以在请求头或者响应头中设置，并且可以组合使用多种指令：

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190905152814719.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dhbnRpbmd0cg==,size_16,color_FFFFFF,t_70) 

**区别：**

- `Expires` 是http1.0的产物 `Cache-Control`是http1.1的产物
- `Cache-Control`优先级高于`Expires`
- 在某些不支持HTTP1.1的环境下，才使用`Expires`。

##### 协商缓存

因为强缓存根据过期时间来判断是否需要重新请求，所以会出现在有效期内，服务器资源已经更新，但获取到的仍是旧资源。

**协商缓存就是强制缓存失效**(可能是cache-control设置了no-cache或no-store)后，**浏览器携带缓存标识向服务器发起请求**，**由服务器根据缓存标识决定是否使用缓存的过程**，主要有以下两种情况：

1. 协商缓存生效，返回304和Not Modified

2. 协商缓存失效，返回200和请求结果


协商缓存可以通过设置两种 服务端的响应头来实现：Last-Modified 和 ETag 。

### 3、宏任务和微任务

#### 面试题

![1650778296031](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650778296031.png)

**普通的异步函数执行过程：**

> 同步和异步任务分别进入不同的执行"场所"，<font color='red'>同步的进入主线程，异步的进入Event Table并注册函数。</font>当指定的事情完成时，<font color='red'>Event Table会将这个函数移入Event Queue。</font>**主线程内的任务执行完毕为空**，**会去**Event Queue**读取对应的函数**，进入主线程执行。上述过程会不断重复，也就是常说的<font color='hotpink'>**Event Loop(事件循环)。**</font>

 ![img](https://img-blog.csdn.net/2018041120124254?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xjMjM3NDIzNTUx/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70) 

**js异步有一个机制：遇到宏任务先执行宏任务，将宏任务放入event queue，然后再执行微任务，将微任务放入到event queue。这两个queue不是同一个queue，往外拿的时候，<font color='hotpink'>先从微任务里拿掉回调函数，然后再从宏任务的queue上拿宏任务的回调函数</font>。**

 ![img](https://img-blog.csdn.net/20180411202638415?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xjMjM3NDIzNTUx/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70) 

> 宏任务：整体代码：script、setTimeout、setInterval
>
> 微任务：Promise.then()、process.nextTick

> ⭐**<font color='hotpink'>Promise是宏任务（同步执行），但Promise的回调函数属于（微任务）异步任务，会在同步任务之后执行（then、catch、finally）</font>**

![1650782271925](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650782271925.png)

异步任务：setTimeout和promise.then()

#### javaScript的单线程

> - 应用场景决定了javascript的单线程的特性，假如javascript是多线程，同时进行：一个线程对某一个dom进行添加属性操作，另一个线程对该线程进行删除操作，那么浏览器该听哪一个。这就决定javascript必须是单线程。
> - web worker:是一个多线程。它出现的目的是当浏览器有大量密集的计算时候或者响应时间很长的运算时候，页面出现卡顿，可以起一个worker子线程，主线程和worker线程互不干预，这样页面就可以进行点击之类的操作，但这个子线程不能操作DOM元素。

>  **<font color='hotpink'>Js 中，有两类任务队列：宏任务队列（macro tasks）和微任务队列（microtasks）。宏任务队列可以有多个，微任务队列只有一个</font>** 

#### 宏任务（macrotask ）和微任务（microtask ）

>  macrotask 和 microtask 表示**异步任务的两种分类。** 

> 宏任务（task）：就是JS 内部（任务队列里）的任务，<font color='red'>严格按照时间顺序压栈和执行。</font>如 setTimeOut、setInverter、setImmediate 、 MessageChannel等
>
> 微任务（Microtask ）：通常来说就是**<font color='red'>需要在当前任务执行结束后立即执行的任务，</font>**例如需要对一系列的任务做出回应，或者是需要异步的执行任务而又不需要分配一个新的 任务 ，这样便可以减小一点性能的开销。

> 在挂起任务时，JS 引擎会将所有任务按照类别分到这两个队列中，首先在 macrotask 的队列（这个队列也被叫做 task queue）中取出第一个任务，执行完毕后取出 microtask 队列中的所有任务顺序执行；之后再取 macrotask 任务，周而复始，直至两个队列的任务都取完。

![1650778913588](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650778913588.png)

> 运行机制:
>
> 1. 在执行栈中执行一个宏任务。
>
> 2. 执行过程中遇到微任务，将微任务添加到微任务队列中。
>
> 3. 当前宏任务执行完毕，立即执行微任务队列中的任务。
>
> 4. 当前微任务队列中的任务执行完毕，检查渲染，GUI线程接管渲染。
>
> 5. 渲染完毕后，js线程接管，开启下一次事件循环，执行下一次宏任务（事件队列中取）。

![1650781707922](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650781707922.png)

> 1. 首先浏览器执行js进入第一个宏任务进入主线程, 直接打印console.log(‘1’)
> 2. 遇到 setTimeout 分发到宏任务Event Queue中
> 3. 遇到 process.nextTick 丢到微任务Event Queue中
> 4. 遇到 Promise， new Promise 直接执行 输出 console.log(‘7’);
> 5. 执行then 被分发到微任务Event Queue中``
> 6. 第一轮宏任务执行结束，开始执行微任务 打印 6,8
> 7. 第一轮微任务执行完毕，执行第二轮宏事件，执行setTimeout
> 8. 先执行主线程宏任务，在执行微任务，打印’2,4,3,5’
> 9. 在执行第二个setTimeout,同理打印 ‘9,11,10,12’
> 10. 整段代码，共进行了三次事件循环，完整的输出为1，7，6，8，2，4，3，5，9，11，10，12。

队列的优先级执行顺序为：同步任务、立即执行任务、微任务、宏任务

### 4、常见的HTTP状态码

**1. 2XX**

<font color='red'>表示请求成功的状态代码</font>

| 200（成功）       | 服务器已成功处理了请求。 通常，这表示服务器提供了请求的网页。 |
| ----------------- | ------------------------------------------------------------ |
| 201（已创建）     | 请求成功并且服务器创建了新的资源。                           |
| 202（已接受）     | 服务器已接受请求，但尚未处理。                               |
| 203（非授权信息） | 服务器已成功处理了请求，但返回的信息可能来自另一来源。       |
| 204（无内容）     | 服务器成功处理了请求，但没有返回任何内容。                   |
| 205（重置内容）   | 服务器成功处理了请求，但没有返回任何内容。                   |
| 206（部分内容）   | 服务器成功处理了部分 GET 请求。                              |

**2.3XX**

<font color='red'>表示要完成请求，需要进一步操作。通常用于重定向</font>

| 300（多种选择）     | 针对请求，服务器可执行多种操作。 服务器可根据请求者 (user agent) 选择一项操作，或提供操作列表供请求者选择。 |
| ------------------- | ------------------------------------------------------------ |
| 301（永久移动）     | 请求的网页已永久移动到新位置。 服务器返回此响应（对 GET 或 HEAD 请求的响应）时，会自动将请求者转到新位置。 |
| 302（临时移动）     | 服务器目前从不同位置的网页响应请求，但请求者应继续使用原有位置来进行以后的请求。 |
| 303（查看其它位置） | 请求者应当对不同的位置使用单独的 GET 请求来检索响应时，服务器返回此代码。 |
| 304（未修改）       | 自从上次请求后，请求的网页未修改过。 服务器返回此响应时，不会返回网页内容。 |
| 305（使用代理）     | 请求者只能使用代理访问请求的网页。 如果服务器返回此响应，还表示请求者应使用代理。 |
| 306（临时重定向）   | 服务器目前从不同位置的网页响应请求，但请求者应继续使用原有位置来进行以后的请求。 |

**3.4XX**

<font color='red'>表示可能出现错误，妨碍了服务器的处理</font>

| 400（错误请求）           | 服务器不理解请求的语法。                                     |
| ------------------------- | ------------------------------------------------------------ |
| 401（未授权）             | 请求要求身份验证。 对于需要登录的网页，服务器可能返回此响应。 |
| 403（禁止）               | 服务器拒绝请求。                                             |
| 404（未找到）             | 服务器找不到请求的网页。                                     |
| 405（方法禁用）           | 服务器找不到请求的网页。                                     |
| 406（不接受）             | 无法使用请求的内容特性响应请求的网页。                       |
| 407（需要代理授权）       | 此状态代码与 401（未授权）类似，但指定请求者应当授权使用代理。 |
| 408（请求超时）           | 服务器等候请求时发生超时。                                   |
| 409（冲突）               | 服务器在完成请求时发生冲突。 服务器必须在响应中包含有关冲突的信息。 |
| 410（已删除）             | 如果请求的资源已永久删除，服务器就会返回此响应。             |
| 411（需要有效长度）       | 服务器不接受不含有效内容长度标头字段的请求。                 |
| 412（未满足前提条件）     | 服务器未满足请求者在请求中设置的其中一个前提条件。           |
| 413（请求实体过大）       | 服务器无法处理请求，因为请求实体过大，超出服务器的处理能力。 |
| 414（请求的url过长）      | 请求的 URI（通常为网址）过长，服务器无法处理。               |
| 415（不支持的媒体类型）   | 请求的格式不受请求页面的支持。                               |
| 416（请求范围不符合要求） | 如果页面无法提供请求的范围，则服务器会返回此状态代码。       |
| 417（未满足期望值）       | 服务器未满足"期望"请求标头字段的要求。                       |

**4.5XX**

表示服务器在尝试处理请求时发生内部错误。 这些错误可能是服务器本身的错误，而不是请求出错。

| 500（服务器内部错误）   | 服务器遇到错误，无法完成请求。                               |
| ----------------------- | ------------------------------------------------------------ |
| 501（尚未实施）         | 服务器不具备完成请求的功能。 例如，服务器无法识别请求方法时可能会返回此代码。 |
| 502（错误网关）         | 服务器作为网关或代理，从上游服务器收到无效响应。             |
| 503（服务不可用）       | 服务器目前无法使用（由于超载或停机维护）。 通常，这只是暂时状态。 |
| 504（网关超时）         | 服务器作为网关或代理，但是没有及时从上游服务器收到请求。     |
| 505（HTTP版本不受支持） | 服务器不支持请求中所用的 HTTP 协议版本。                     |

### 5、http和https

#### HTTP

>  互联网上应用最为广泛的一种**网络协议**，**超文本传输协议**，**<font color='hotpink'>是一个基于请求与响应，无状态的，应用层的协议，常基于TCP/IP协议传输数据</font>**，是一个客户端和服务器端请求和应答的标准（TCP），用于从WWW服务器传输超文本到本地浏览器的传输协议，它可以使浏览器更加高效，使网络传输减少。 

#### HTTPS

> <font color='hotpink'>是以安全为目标的HTTP通道，简单讲是HTTP的安全版，即HTTP下加入SSL层，HTTPS的安全基础是SSL，因此加密的详细内容就需要SSL。</font>**HTTPS协议的主要作用可以分为两种：一种是建立一个信息安全通道，来保证数据传输的安全；另一种就是确认网站的真实性。** 

#### 区别：

HTTP协议传输的数据都是未加密的，也就是明文的，因此使用HTTP协议传输隐私信息非常不安全，为了保证这些隐私数据能加密传输，于是网景公司**设计了SSL协议用于对HTTP协议传输的数据进行加密，从而就诞生了HTTPS。**简单来说，**HTTPS协议是由SSL+HTTP协议构建的可进行加密传输、身份认证的网络协议，要比http协议安全。**

1. **<font color='green'>http是超文本传输协议，信息是明文传输，https则是具有安全性的ssl加密传输协议。</font>**
2. http和https使用的是完全不同的连接方式，用的端口也不一样，http是80，https是443。
3. **http的连接很简单，是无状态的**（可以通过cookie来解决）；
4. <font color='blue'>HTTPS协议是由SSL+HTTP协议构建的可进行加密传输、身份认证的网络协议，比http协议安全。</font>

#### HTTPS的工作原理

步骤：

1. 客户使用https的URL访问Web服务器，要求与Web服务器建立SSL连接。
2. Web服务器收到客户端请求后，会将网站的证书信息（证书中包含公钥）传送一份给客户端。
3. 客户端的浏览器与Web服务器开始协商SSL连接的安全等级，也就是信息加密的等级。
4. 客户端的浏览器根据双方同意的安全等级，建立会话密钥，然后利用网站的公钥将会话密钥加密，并传送给网站。
5. Web服务器利用自己的私钥解密出会话密钥。
6. Web服务器利用会话密钥加密与客户端之间的通信。

**原理分析：**实质上利用到了对称和非对称两种加密手段，<font color='red'> 通过对称加密对数据加密，通过非对称加密对对称加密的密钥加密。 </font>

 ![image-20210608161818224](https://img-blog.csdnimg.cn/img_convert/4bf1e948001a4bf22a24f1140737f487.png) 

> 1. 对称加密: 加密和解密的秘钥使用的是同一个。(常见：DES、3DES 、AES )
>    - 优：算法公开、计算量小、加密速度快、加密效率高
>    - 缺：不够安全
>
> 2. 非对称加密: 与对称加密算法不同，非对称加密算法需要两个密钥：公开密钥（publickey）和私有密钥（privatekey）。（常见： RSA、DSA（数字签名用））
>    - 优：安全
>    - 缺：速度慢

#### HTTPS的缺点

> - HTTPS协议多次握手，导致页面的加载时间延长近50%；
> - HTTPS连接缓存不如HTTP高效，会增加数据开销和功耗；
> - 申请SSL证书需要钱，功能越强大的证书费用越高。
> - SSL涉及到的安全算法会消耗 CPU 资源，对服务器资源消耗较大。

### 5、基本数据类型和引用类型在内存中怎么存储？

#### 1.引用数据类型在内存中的存储方式

**<font color='hotpink'>引用数据类型：数组、对象</font>**

Student student = new Student();

创建一个Student类型的变量，名称为student

1. **<font color='red'>栈中存储的是数据在堆内存中的首地址</font>**
2. **<font color='blue'>值在堆内存中</font>**

#### 2.基本数据类型和引用数据类型的不同

> 1. 声明方式不同，**只要有new关键字就是在堆中开辟空间**
> 2. **值存储位置不同：基本数据类型值存储在栈中**
>    - **引用数据类型在栈中存储的是数据在堆中的首地址**
>    - **引用数据类型的值存储在堆内存中**

#### 3.栈内存：作用域

1. 提供一个供JS 代码自上而下执行的环境（代码都是在栈内存中执行的）
2. 由于基本数据类型值比较简单，他们都是直接在栈内存中开辟一个位置，把值直接存储进去的

**当栈内存被销毁，存储的那些基本值也就跟着销毁了**。

#### 4.堆内存：引用值对应的空间

1. 存储引用类型值的（对象：键值对 函数：代码字符串）
2. 当前堆内存释放销毁，那么这个引用值彻底没了

堆内存的释放：**当堆内存没有被任何的变量或者其它东西所占用，浏览器会在空闲的时候，自主的进行内存回收，把所有不被占用的堆内存销毁掉（谷歌浏览器）**

xxx=null; 通过空对象指针null 可以让原始变量（或者其它东西）谁都不指向 那么原有被占用的堆内存就没有被东西占用了，浏览器会销毁它。

 ![栈内存与堆内存](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZS1zdGF0aWMuc2VnbWVudGZhdWx0LmNvbS8xNzEvNTA4LzE3MTUwODU5NTMtNWIwZmE4YTExYzIwY19hcnRpY2xleA?x-oss-process=image/format,png) 

### 6、TCP、UDP的区别

> 1. TCP是面向连接的，UDP是无连接的
> 2. TCP是可靠的，UDP是不可靠的
> 3. TCP是面向字节流的，UDP是面向数据报文的
> 4. TCP只支持点对点通信，UDP支持一对一，一对多，多对多
> 5. TCP报文首部20个字节，UDP首部8个字节
> 6. TCP有拥塞控制机制，UDP没有
> 7. TCP协议下双方发送接受缓冲区都有，UDP并无实际意义上的发送缓冲区，但是存在接受缓冲区

**<font color='blue'>TCP和UDP是传输层的两个协议</font>**

##### 1.UDP

UDP的包头：

 ![UDP 包头](https://static001.geekbang.org/resource/image/6d/bf/6d1313f51b9dfd7ab454b2cef1cb37bf.jpg) 

特点：

> - 沟通简单，不需要大量的数据结构，处理逻辑和包头字段
> - 轻信他人。它不会建立连接，但是会监听这个地方，谁都可以传给它数据，它也可以传给任何人数据，甚至可以同时传给多个人数据。
> - 愣头青，做事不懂变通。不会根据网络的情况进行拥塞控制，无论是否丢包，它该怎么发还是怎么发

应用场景：

> 1. 需要资源少，网络情况稳定的内网，或者对于丢包不敏感的应用，比如 DHCP 就是基于 UDP 协议的。
> 2. 不需要一对一沟通，建立连接，而是可以广播的应用。因为它不面向连接，所以可以做到一对多，承担广播或者多播的协议。
> 3. 需要处理速度快，可以容忍丢包，但是即使网络拥塞，也毫不退缩，一往无前的时候

实例：

> 1. 直播。直播对实时性的要求比较高，宁可丢包，也不要卡顿的，所以很多直播应用都基于 UDP 实现了自己的视频传输协议
> 2. 实时游戏。游戏的特点也是实时性比较高，在这种情况下，采用自定义的可靠的 UDP 协议，自定义重传策略，能够把产生的延迟降到最低，减少网络问题对游戏造成的影响
> 3. 物联网。一方面，物联网领域中断资源少，很可能知识个很小的嵌入式系统，而维护 TCP 协议的代价太大了；另一方面，物联网对实时性的要求也特别高。比如 Google 旗下的 Nest 简历 Thread Group，推出了物联网通信协议 Thread，就是基于 UDP 协议的

#### 2.TCP

TCP的包头：

 ![TCP 包头](https://static001.geekbang.org/resource/image/a7/bf/a795461effcce686a43f48e094c9adbf.jpg) 

> 1. 源端口和目标端口是不可少的。
> 2. 包的序号。主要是为了解决乱序问题。不编好号怎么知道哪个先来，哪个后到
> 3. 确认序号。发出去的包应该有确认，这样能知道对方是否收到，如果没收到就应该重新发送，这个解决的是不丢包的问题
> 4. 状态位。SYN 是发起一个链接，ACK 是回复，RST 是重新连接，FIN 是结束连接。因为 TCP 是面向连接的，因此需要双方维护连接的状态，这些状态位的包会引起双方的状态变更
> 5. 窗口大小，TCP 要做流量控制，需要通信双方各声明一个窗口，标识自己当前的处理能力。

TCP的三次握手

**<font color='hotpink'>TCP 的建立连接称为三次握手， TCP 的三次握手除了建立连接外，主要还是为了沟通 TCP 包的序号问题。 </font>** 

 ![状态变化时序图](https://static001.geekbang.org/resource/image/66/a2/666d7d20aa907d8317af3770411f5aa2.jpg) 

TCP 四次挥手

**<font color='skgreen'>TCP 断开连接，也被称为四次挥手</font>** 

 ![断开连接状态时序图](https://static001.geekbang.org/resource/image/1f/11/1f6a5e17b34f00d28722428b7b8ccb11.jpg) 

#### TCP如何实现可靠传输

累计确认

首先为了保证顺序性，每个包都有一个 ID。在建立连接的时候会商定起始 ID 是什么，然后按照 ID 一个个发送，为了保证不丢包，需要对发送的包都要进行应答，当然，**这个应答不是一个一个来的，而是会应答某个之前的 ID，表示都收到了，这种模式成为累计应答或累计确认。**

**为了记录所有发送的包和接收的包，TCP 需要发送端和接收端分别来缓存这些记录，<font color='red'>发送端的缓存</font>里是按照包的 ID 一个个排列，根据处理的情况分成四个部分：**

> - 发送并且确认的
> - 发送尚未确认的
> - 没有发送等待发送的（流量控制）
> - 没有发送并且暂时不会发送的（流量控制）

 ![发送端数据结构](https://static001.geekbang.org/resource/image/16/7b/16dcd6fb8105a1caa75887b5ffa0bd7b.jpg) 

**<font color='red'>接收端的缓存</font>**

> - 接收并且确认过的
> - 还没接收，但是马上就能接收的
> - 还没接收，但也无法接收的

 ![接收端的数据结构](https://static001.geekbang.org/resource/image/f7/a4/f7b1d3bc6b6d8e55f0951e82294c8ba4.jpg) 

#### 顺序问题和丢包问题

> 结合上面的图看，在发送端，1、2、3 已发送并确认；4、5、6、7、8、9 都是发送了还没确认；10、11、12 是还没发出的；13、14、15 是接收方没有空间，不准备发的。
>
> 在接收端来看，1、2、3、4、5 是已经完成 ACK 但是还没读取的；6、7 是等待接收的；8、9 是已经接收还没有 ACK 的。
>
> 发送端和接收端当前的状态如下：
>
> 1、2、3 没有问题，双方达成了一致
> 4、5 接收方说 ACK 了，但是发送方还没收到
> 6、7、8、9 肯定都发了，但是 8、9 已经到了，6、7 没到，出现了乱序，缓存着但是没办法 ACK。
> 根据这个例子可以知道顺序问题和丢包问题都有可能存在，所以我们先来看确认与重传机制。
>
> 假设 4 的确认收到了，5 的 ACK 丢了，6、7 的数据包丢了，该怎么办？
>
> 一种方法是超时重试，即对每一个发送了但是没有 ACK 的包设定一个定时器，超过了一定的事件就重新尝试。这个时间必须大于往返时间，但也不宜过长，否则超时时间变长，访问就变慢了。
>
> 如果过一段时间，5、6、7 都超时了就会重新发送。接收方发现 5 原来接收过，于是丢弃 5；6 收到了，发送 ACK，要求下一个是 7，7 不幸又丢了。当 7 再次超时的时候，TCP 的策略是超时间隔加倍。每当遇到一次超时重传的时候，都会讲下一次超时时间间隔设为先前值的两倍。
>
> 超时重传的机制是超时周期可能相对较长，是否有更快的方式呢？
>
> 有一个快速重传的机制，即当接收方接收到一个序号大于期望的报文段时，就检测到了数据流之间的间隔，于是发送三个冗余的 ACK，客户端接收到之后，知道数据报丢失，于是重传丢失的报文段。
>
> 例如，接收方发现 6、8、9 都接收了，但是 7 没来，所以肯定丢了，于是发送三个 6 的 ACK，要求下一个是 7。客户端接收到 3 个，就会发现 7 的确又丢了，不等超时，马上重发。

##### 流量控制的问题

> 在流量控制的机制里面，在对于包的确认中，会携带一个窗口的大小
>
> 简单的说一下就是接收端在发送 ACK 的时候会带上缓冲区的窗口大小，但是一般在窗口达到一定大小才会更新窗口，因为每次都更新的话，刚空下来就又被填满了

##### 拥塞控制的问题

也是通过窗口的大小来控制的，但是检测网络满不满是个挺难的事情，所以 TCP 发送包经常被比喻成往谁管理灌水，所以拥塞控制就是在不堵塞，不丢包的情况下尽可能的发挥带宽。 

 ![img](https://static001.geekbang.org/resource/image/db/e6/db8510541662281175803c7f9d1fcae6.jpg) 

> TCP 拥塞控制主要来避免两种现象，包丢失和超时重传，一旦出现了这些现象说明发送的太快了，要慢一点。
>
> 具体的方法就是发送端慢启动，比如倒水，刚开始倒的很慢，渐渐变快。然后设置一个阈值，当超过这个值的时候就要慢下来
>
> 慢下来还是在增长，这时候就可能水满则溢，出现拥塞，需要降低倒水的速度，等水慢慢渗下去。
>
> 拥塞的一种表现是丢包，需要超时重传，这个时候，采用快速重传算法，将当前速度变为一半。所以速度还是在比较高的值，也没有一夜回到解放前。

###### 总结：

> - **<font color='hotpink'>TCP 的顺序问题，丢包问题，流量控制都是通过滑动窗口来解决的</font>**
> - **<font color='red'> 拥塞控制时通过拥塞窗口来解决的</font>** 

#### 什么是面向连接什么是面向无连接

<font color='red'>在互通之前，面向连接的协议会先建立连接</font>，如 TCP 有三次握手，而 UDP 不会 

#### TCP为什么是可靠连接

> - **通过 TCP 连接传输的数据无差错，不丢失，不重复，且按顺序到达。**
> - TCP 报文头里面的序号能使 TCP 的数据按序到达
> - **报文头里面的确认序号能保证不丢包，累计确认及超时重传机制**
> - TCP 拥有流量控制及拥塞控制的机制

### 7、文件上传客户端判断大小

问题：大文件上传，服务的客户端怎么知道上传完成？

## 3

#### 1.CDN缓存、加速

> - Content Delivery Network，即内容分发网络
> - 各地部署多套静态存储服务，本质上是空间换时间
> - 自动选择最近的节点内容，不存在再请求原始服务器
> - 适合存储更新很少的静态内容，文件更新慢

CDN 的工作原理就是将您源站的资源缓存到位于全球各地的 CDN 节点上，用户请求资源时，就近返回节点上缓存的资源，而不需要每个用户的请求都回您的源站获取，避免网络拥塞、缓解源站压力，保证用户访问资源的速度和体验。 









#### 代码题：

1、反转链表

2、岛上有白、灰、黑三种颜色的变色龙，其中两种不同颜色的变色龙相遇会同时变成第三种颜色，问三种颜色的变色龙数量分别为10，14，15时可能变成同一种颜色的变色龙吗?

3、链表倒数第K个节点

4、二叉树反转

5、二叉树的最小深度

### 手写new

![1650787558442](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650787558442.png)

new操作符做了什么事情：

> 1. 创建一个空对象 将来会返回这个对象
>
> 2. 调用构造函数，并将构造函数的this指向新创建的对象obj
>
> 3. 把原型对象的方法给新创建的obj，把obj的__proto__指向构造函数的显式原型
>
> 4. 判断构造函数的返回值，来决定new的返回值（是构造函数的返回值还是实例化对象）

![1650788045294](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650788045294.png)

第二种方法：Object.create()

> 1. 创建对象
>
> 2. 将新创建的实例对象原型指向了构造函数

![1650788250935](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650788250935.png)

测试：

![1650788422111](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650788422111.png)

### sizeof和strlen的区别

> 1. strlen适用于计算字符串的长度，遇到第一个NULL（\0）为止，不包括'\0'
> 2. sizeof适用于计算变量或者对象、类型所占字节的多少
> 3. strlen是函数，sizeof是运算符

![1650788685912](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650788685912.png)

![1650788694136](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650788694136.png)

# 手写instanceof函数

**<font color='red'>instanceof函数：用于判断对象是否是某个类的实例</font>**

![1650798903122](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650798903122.png)

原型链如下：

![1650799413686](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650799413686.png)

**手写代码如下：**

利用原型链的知识点，根据对象的`__proto__`属性，一直在原型链上找，若找到pointer===className.prototype，则证明对象obj是className的一个实例。

![1650799773092](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650799773092.png)

# 手写深拷贝

**<font color='hotpink'>JS中对对象的拷贝为浅拷贝，一个对象的某个值改变另外一个对象对应的值也会改变。</font>**

浅拷贝示例：

![1650800136202](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650800136202.png)

输出：

![1650800157038](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650800157038.png)

#### 手写深拷贝：

![1650800935139](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650800935139.png)

**输出：**

![1650800950659](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650800950659.png)

# for...in和for...of

## for...in

**<font color='hotpink'>枚举的是对象的key值或数组的索引</font>**

1、对象

![1650873449524](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650873449524.png)

2、数组

![1650873532469](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650873532469.png)

## for...of

可枚举数组，不可枚举对象

**<font color='hotpink'>枚举的是数组的元素值，而非索引</font>**

![1650873686953](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650873686953.png)

> **可迭代字符串，枚举的字符串的每个字符**

![1650873753112](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650873753112.png)

> **可迭代arguments类数组对象**

![1650873805592](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650873805592.png)

> **可迭代map和set**

![1650873839585](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650873839585.png)

![1650873867352](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650873867352.png)

# 数组扁平化⭐⭐⭐

# 单例模式⭐⭐

# 模拟Object.create()的实现

Object.create()用于创建一个对象，与new操作符最明显的区别：对`__proto__`属性的操作不同

> 参数：
>
> 1、proto
>
> 必选的，新建对象的原型对象
>
> 2、propertiesObject
>
> 可选的，新建的实例对象上的属性

![1650948863232](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650948863232.png)

**new操作符创建的实例`_proto__`是指向构造函数的prototype的**

![1650949318939](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650949318939.png)

![1650949351409](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650949351409.png)

**Object.create()生成的实例没有默认原型**

# 千分位分隔符

# 实现三角形⭐⭐

# 实现三栏布局、双栏布局⭐⭐⭐

## 

## setTimeout和setInterval

1. **<font color='hotpink'>相同条件下，setTimeout() 只执行一次，setInterval() 则循环执行；</font>**
2. **setTimeout() 延迟执行一次**： setTimeout(fn, 1000); //延迟1秒，执行一次fn()；
3. **setInterval() 隔段时间循环执行**； setInterval(fn, 1000); //每隔1秒，循环执行fn()

> - window.setTimeout("function",time)；//设置一个超时对象，只执行一次,无周期
> - window.setInterval("function",time)；//设置一个超时对象，周期＝'交互时间'
>
> 停止定时：
>
> - window.clearTimeout(对象)：清除已设置的setTimeout对象
> - window.clearInterval(对象)：清除已设置的setInterval对象