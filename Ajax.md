# 服务器的基本概念与初识Ajax

## 一、客户端与服务器

上网的本质目的：<font color='red'>**通过互联网的形式来获取和消费资源**</font>

### 1、服务器

<font color='orange'>**上网过程中，负责存放和对外提供资源的电脑，叫做服务器。**</font>

![1649902528754](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649902528754.png)

### 2、客户端

<font color='blue'>**上网过程中，负责获取和消费资源的电脑，叫做客户端。**</font>

![1649902563382](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649902563382.png)

## 二、URL地址

### 1、URL概念

<font color='red'>URL（全称是UniformResourceLocator）中文叫统一资源定位符，用于标识互联网上每个资源的唯一存放位置。</font>

<font color='blue'>浏览器只有通过URL地址，才能正确定位资源的存放位置，从而成功访问到对应的资源。</font>

常见的URL举例：

http://www.baidu.com

http://www.taobao.com

http://www.cnblogs.com/liulongbinblogs/p/11649393.html

### 2、URL地址组成

> URL地址一般由三部分组成：
>
> 1. <font color='red'>客户端与服务器之间的通信协议</font>
> 2. <font color='red'>存有该资源的服务器名称</font>
> 3. <font color='red'>资源在服务器上具体的存放位置</font>

![1649902685211](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649902685211.png)

## 三、网页的打开过程

### 1、客户端与服务器的通信过程

![1649902733814](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649902733814.png)

<font color='red'>注意：</font>

客户端与服务器之间的通信过程，分为 <font color='red'>请求 – 处理 – 响应</font> 三个步骤。

**网页中的每一个资源，都是通过 请求 – 处理 – 响应 的方式从服务器获取回来的。**

![1649902768237](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649902768237.png)

## 四、服务器对外提供的资源

![1649902799947](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649902799947.png)

### 1、数据也是资源

<font color='red'>网页中的数据，也是服务器对外提供的一种资源。</font>例如股票数据、各行业排行榜等。

![1649902816885](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649902816885.png)

![1649902839460](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649902839460.png)

### 2、网页中请求数据

<font color='red'>数据，也是服务器对外提供的一种资源。</font>只要是资源，必然要通过 <font color='red'>请求 – 处理 – 响应</font> 的方式进行获取。

![1649902896843](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649902896843.png)

<font color='blue'>如果要在网页中请求服务器上的数据资源，则需要用到 XMLHttpRequest 对象。</font>

<font color='green'>**XMLHttpRequest（简称 xhr）是浏览器提供的 js 成员，通过它，可以请求服务器上的数据资源。**</font>

最简单的用法 <font color='red'>var xhrObj = new XMLHttpRequest()</font>

### 3、资源的请求方式

> <font color='red'>客户端请求服务器时，请求的方式有很多种，最常见的两种请求方式分别为 get 和 post 请求。</font>
>
> 1. <font color='orange'>get 请求通常用于获取服务端资源（向服务器要资源）</font>
>
>    例如：根据 URL 地址，从服务器获取 HTML 文件、css 文件、js文件、图片文件、数据资源等
>
> 2. <font color='blue'>post 请求通常用于向服务器提交数据（往服务器发送资源）</font>
>
>    例如：登录时向服务器提交的登录信息、注册时向服务器提交的注册信息、添加用户时向服务器提交的用户信息等各种数据提交操作

## 五、Ajax

### 1、Ajax概述

**Ajax 的全称是 Asynchronous Javascript And XML（异步 JavaScript 和 XML）。**

通俗的理解：<font color='red'>在网页中利用 XMLHttpRequest 对象和服务器进行数据交互的方式，就是Ajax。</font>

Ajax能让我们轻松实现**网页与服务器之间的数据交互。**

![1649903110275](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903110275.png)

### 2、Ajax应用

![1649903144710](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903144710.png)

![1649903156129](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903156129.png)

![1649903163896](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903163896.png)

![1649903177215](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903177215.png)

### XMLHttpRequest对象

Ajax的原理是通过XmlHttpRequest对象向服务器发出异步请求，从服务器获得所需要的数据，然后用JavaScript来操作DOM而更新页面。

#### 1、初始化XMLHttpRequest对象

浏览器有内置的XMLHttpRequest。

**创建XMLHttpRequest对象的语法：**

![1650511085383](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650511085383.png)

**XMLHttpRequest对象的常用属性和事件：**

##### 1.1 readyState属性

当一个XMLHttpRequest对象被创立后，readyState属性表示当前对象处于什么状态，可以通过对该属性的访问来判此次请求的状态，然后做出对应的操作。具体属性值如下：

> 1. 0：未初始化状态。已创建了一个XMLHttpRequest对象，但未初始化
> 2. 1：准备发送状态。已调用了XMLHttpRequest对象的open()方法，并且XMLHttpRequest对象已经准备将一个请求发送到服务器。
> 3. 2：已发送状态。已经通过send()方法将一个请求发送到了服务器，等待响应。
> 4. 3：正在接收状态。此时已经接收到HTTP响应的头部信息，但是消息体部分还没有完全接收到。
> 5. 4：完成响应状态。此时已经完成了HttpResponse响应的接收。

##### 1.2 responseText属性

responseText属性包含客户端接收到的HTTP响应的文本内容。当readyState为0、1、2时，responseText属性包含一个空字符串。当readyState为3时，响应中包含客户端还没有完成的响应信息。当readyState为4时，responseText属性包含完整的响应信息。

##### 1.3 responseXML属性

只有当readyState为4，并且响应头部的Content-Type的MIME类型被指定为XML（text/xml或application/xml）时，该属性才会有值并被解析为一个XML文档，否则该属性为null。

##### 1.4 status属性

买哦书了HTTP状态的代码。仅当readyState为3（正在接收中）或4（已加载）时，才能对此属性进行访问！否则会产生异常。

##### 1.5 onreadystatechange事件

当readyState属性发生改变时，XMLHttpRequest对象调用 onreadystatechange事件。

![1650512088433](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650512088433.png)

#### 2、XMLHttpRequest对象的常用方法

##### open()方法

用于设置异步请求目标的URL、请求方法以及其他参数信息

> open("method","URL"[,asyncFlag[,"username"[,"password"]]])

| 参数      | 说明                                                         |
| --------- | ------------------------------------------------------------ |
| method    | 用于指定请求类型，一般为GET和POST                            |
| URL       | 用于指定请求地址，可以使用绝对地址和相对地址，并且可以传递查询字符串 |
| asyncFlag | 可选参数，用于指定请求方式，异步请求为true（默认），同步请求为false |
| userName  | 可选参数，用于指定请求用户名                                 |
| password  | 可选参数，用于指定请求密码                                   |

##### send()方法

> 调用send()方法后，就可以按照open()方法设定的参数发送请求。当open()方法中async属性设置为true时，send()方法调用后立即返回，否则将会中断，直到请求返回。需要注意的是，send()方法必须在readyState属性为1时才能调用；在调用send( )方法以后到接收响应信息之间的时间内，readyState属性值将被设成2；一旦接收到响应信息，readyState属性将被设为3；当响应接收完成时，readyState属性值才会被设定为4。如果send(data)方法中data参数的类型为DOMString，数据将被编码成UTF-8；如果是Document类型,将使用由data.xmlEncoding指定的编码来串行化该数据。

##### abort()方法

该方法可以暂停一个HttpRequest的发送或者HttpResponse的接收，并且将XMLHttpRequest对象设置为初始化状态。

##### setRequestHeader()方法

在调用send()方法之前，应该先使用setRequestHeader()方法设置请求的Content-Type头部信息。当readyState属性为1时，在调用open()方法后再调用这个方法，否则将得到一个异常。setRequestHeader(header,value)方法包含两个参数，第一个参数是header键名称，第二个参数是键值。

##### getResponseHeader方法

该方法用于检索响应的头部值。仅当readyState属性是3或者4(既响应头部可用以后)时才可以调用该方法，否则返回一个空字符串。此外，还可以通过getAllResponseHeader()方法获取所有的HttpResponse的头部信息。

## 传统Ajax的工作流程

### 1、发送请求

Ajax可以通过XMLHttpRequest对象实现用异步方式在后台发送请求。通常情况下，Ajax发送请求有两种，一种是GET请求，一种是POST请求。都具有以下四个步骤：

#### 1.初始化XMLHttpRequest对象

创建一个跨浏览器的XMLHttpRequest对象，并且判断XMLHttpRequest对象的实例是否成功，若不成功则给出提示。

#### 2.为XMLHttpRequest对象指定一个返回结果处理函数（回调函数）

#### 3.创建一个与服务器的连接

在创建时，需要指定发送请求的方式（GET或POST），以及设置是否采用异步方式发送请求。

#### 4.向服务器发送请求

XMLHttpRequest对象的send()方法可以实现向服务器发送请求，该方法需要传递一个参数，如果发送的是GET请求，可以将该参数设为null。

![1650591970896](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650591970896.png)

**注意：如果发起的是post请求，需要调用setRequestHeader()设置请求头，否则无法获取参数**

![1650592294131](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650592294131.png)

## 六、jQuery中的Ajax

浏览器中提供的 XMLHttpRequest 用法比较复杂，所以 jQuery 对 XMLHttpRequest 进行了封装，提供了一系列 Ajax 相关的函数，极大地降低了 Ajax 的使用难度。

<font color='red'>jQuery 中发起 Ajax 请求最常用的三个方法如下：</font>

1. $.get()
2. $.post()

3. $.ajax()

### 1、$.get()函数的语法

<font color='red'>jQuery 中 $.get() 函数的功能单一，专门用来发起 get 请求，从而将服务器上的资源请求到客户端来进行使用。</font>

$.get() 函数的语法如下：

![1649903271439](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903271439.png)


其中，三个参数各自代表的含义如下：

![1649903292327](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903292327.png)

#### $.get()发起不带参数的请求

<font color='red'>使用 $.get() 函数发起不带参数的请求时，直接提供请求的 URL 地址和请求成功之后的回调函数即可，</font>示例代码如下：

![1649903350006](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903350006.png)

![1649903355459](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903355459.png)

#### $.get()发起带参数的请求

使用 $.get() 函数发起带参数的请求时，示例代码如下：

![1649903397583](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903397583.png)

![1649903401489](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903401489.png)

### 2、$.post()函数的语法

<font color='red'>jQuery 中 $.post() 函数的功能单一，专门用来发起 post 请求，从而向服务器提交数据。</font>

$.post() 函数的语法如下：

![1649903437733](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903437733.png)


其中，三个参数各自代表的含义如下：

![1649903447715](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903447715.png)

#### $.post()向服务器提交数据

使用 $post() 向服务器提交数据的示例代码如下：

![1649903470516](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903470516.png)

![1649903484137](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903484137.png)

### 3、$.ajax()函数的语法

<font color='blue'>jQuery 中提供的 $.ajax() 函数，是一个功能比较综合的函数，它允许我们对 Ajax 请求进行更详细的配置。</font>

$.ajax() 函数的基本语法如下：

![1650592752086](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650592752086.png)

**常用参数说明：**

1. url：请求数据的地址

2. type：当前Ajax向服务器发送数据采用的是get还是post方法。get方法会将前端上传的数据直接与地址链接起来，一般用于查询操作。get方法有缓存，会被浏览器缓存起来，能传输的数据最大为1024B。post方法比较安全，一般用于新增、删除、修改等操作，传输数据的大小为2MB

3. data：发送到服务器的数据。get请求可以直接将其附加在URL后。

4. dataType：设置服务器返回数据的数据类型。包括以下几种类型：

   "xml"：返回XML文档，可用jQuery处理

   "html"：返回纯文本HTML信息，包含的script标签会插入在DOM时执行。

   "script"：返回纯文本JavaScript代码

   "json"：返回JSON数据格式

   "jsonp"：返回JSONP格式的数据

   "text"：返回纯文本字符串

5. async：同步与异步标志，默认为true，（异步）。同步时会阻塞程序的运行，请求完成后才能继续运行脚本代码，异步时请求的过程不会阻塞代码。
6. success：请求成功后调用的回调函数，该会回调函数所带参数主要包括：服务器返回数据和返回状态。
7. error：请求失败时所调用的回调函数。该函数所带的参数主要包括：XMLHttpRequest对象错误信息、（可能）捕获的错误对象。

![1649903557041](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903557041.png)

#### 使用$.ajax()发起GET请求

<font color='red'>使用 $.ajax() 发起 GET 请求时，只需要将 type 属性的值设置为 'GET' 即可：</font>

![1649903586103](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903586103.png)

#### 使用$.ajax()发起POST请求

<font color='blue'>使用 $.ajax() 发起 POST 请求时，只需要将 type 属性的值设置为 'POST' 即可：</font>

![1649903611615](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903611615.png)

## 七、接口

<font color='red'>**使用 Ajax 请求数据时，被请求的 URL 地址，就叫做数据接口（简称接口）。同时，每个接口必须有请求方式。**</font>

例如：

http://www.liulongbin.top:3006/api/getbooks  获取图书列表的接口(GET请求)

http://www.liulongbin.top:3006/api/addbook   添加图书的接口（POST请求）

### 1. 通过GET方式请求接口的过程

![1649903669171](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903669171.png)

### 2. 通过POST方式请求接口的过程

![1649903686156](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903686156.png)

### 3、接口测试工具

为了验证接口能否被正常被访问，我们常常需要使用接口测试工具，来对数据接口进行检测。

好处：接口测试工具能让我们在不写任何代码的情况下，对接口进行调用和测试。

![1649903715761](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903715761.png)

### 4、接口说明文档

接口文档，顾名思义就是接口的说明文档，它是我们调用接口的依据。好的接口文档包含了对接口URL，参数以及输出内容的说明，我们参照接口文档就能方便的知道接口的作用，以及接口如何进行调用。

#### 接口文档组成

> 接口文档可以包含很多信息，也可以按需进行精简，不过，一个合格的接口文档，应该包含以下6项内容，从而为接口的调用提供依据：
>
> 1. 接口名称：用来标识各个接口的简单说明，如登录接口，获取图书列表接口等。
>
> 2. 接口URL：接口的调用地址。
>
> 3. 调用方式：接口的调用方式，如 GET 或 POST。
>
> 4. 参数格式：接口需要传递的参数，每个参数必须包含参数名称、参数类型、是否必选、参数说明这4项内容。
>
> 5. 响应格式：接口的返回值的详细描述，一般包含数据名称、数据类型、说明3项内容。
>
> 6. 返回示例（可选）：通过对象的形式，例举服务器返回数据的结构。

![1649903790250](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903790250.png)

![1649903800820](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903800820.png)

![1649903809788](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903809788.png)

## 案例-图书管理

### UI结构

![1649903845809](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903845809.png)

### 核心代码

#### 渲染图书列表

![1649903860505](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903860505.png)

#### 删除图书

![1649903883213](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903883213.png)

#### 添加图书

![1649903897905](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903897905.png)

## 案例-聊天机器人

![1649903927514](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903927514.png)

### 渲染输入内容到聊天窗口

![1649903946598](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903946598.png)

### 发起请求获取聊天消息

![1649903965974](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903965974.png)

### 将机器人的聊天内容转为语音

![1649903987782](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649903987782.png)

### audio播放语音

![1649904005430](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649904005430.png)

### 回车发送消息

![1649904019948](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649904019948.png)

# form表单与模板引擎

## 一、form表单的基本使用

### 1、表单的概念

表单在网页中主要负责数据采集功能。**HTML中的<form>标签，就是用于采集用户输入的信息，并通过<form>标签的提交操作，把采集到的信息提交到服务器端进行处理。**

![1649904099570](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649904099570.png)

### 2、表单的组成

![1649904119475](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649904119475.png)

> 表单由三个基本部分组成：
>
> 1. 表单标签
> 2. 表单域
> 3. 表单按钮

<font color='red'>表单域：包含了文本框、密码框、隐藏域、多行文本框、复选框、单选框、下拉选择框和文件上传框等。</font>

### 3、<form>标签属性

**form标签用来采集数据**

<font color='red'>form标签的属性则是用来规定如何把采集到的数据发送到服务器。</font>

![1649904257179](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649904257179.png)

#### 1、action

action 属性用来规定当提交表单时，<font color='red'>向何处发送表单数据。</font>

action 属性的值应该是后端提供的一个 URL 地址，这个 URL 地址专门负责接收表单提交过来的数据。

当 <form> <font color='red'>表单在未指定 action 属性值的情况下，action 的默认值为当前页面的 URL 地址。</font>

<font color='blue'>**注意：当提交表单后，页面会立即跳转到 action 属性指定的 URL 地址**</font>

#### 2、target

target 属性用来规定在何处打开 action URL。

<font color='red'>它的可选值有5个，默认情况下，target 的值是 _self，表示在相同的框架中打开 action URL。</font>

![1649904351143](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649904351143.png)

#### 3、method

<font color='orange'>method 属性用来规定以何种方式把表单数据提交到 action URL。</font>

它的可选值有两个，分别是 get 和 post。

<font color='red'>默认情况下，method 的值为 get，表示通过URL地址的形式，把表单数据提交到 action URL。</font>

注意：

1. get 方式适合用来提交少量的、简单的数据。
2. post 方式适合用来提交大量的、复杂的、或包含文件上传的数据。
3. 在实际开发中，<form> 表单的 post 提交方式用的最多，很少用 get。例如登录、注册、添加数据等表单操作，都需要使用 post 方式来提交表单。

#### 4、enctype

<font color='red'>enctype 属性用来规定在发送表单数据之前如何对数据进行编码。</font>

它的可选值有三个，<font color='blue'>默认情况下，enctype 的值为 application/x-www-form-urlencoded，表示在发送前编码所有的字符。</font>

![1649904486470](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649904486470.png)

注意：

1. <font color='green'>在涉及到文件上传的操作时，必须将 enctype 的值设置为 multipart/form-data</font>
2. 如果表单的提交不涉及到文件上传操作，则直接将 enctype 的值设置为 application/x-www-form-urlencoded 即可！

### 4、表单的同步提交

<font color='red'>通过点击 submit 按钮，触发表单提交的操作，从而使页面跳转到 action URL 的行为，叫做表单的同步提交。</font>

#### 缺点：

- form表单同步提交后，整个页面会发生跳转，跳转到 action URL 所指向的地址，用户体验很差。
- **form表单同步提交后，页面之前的状态和数据会丢失。**


思考：如何解决上述两个问题？

<font color='red'>**表单只负责采集数据，Ajax 负责将数据提交到服务器。**</font>

## 二、通过Ajax提交表单数据

### 1、监听表单提交事件

在 jQuery 中，可以使用如下两种方式，监听到表单的提交事件：

![1649904644771](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649904644771.png)

### 2、阻止表单默认提交行为

<font color='red'>当监听到表单的提交事件以后，可以调用事件对象的 event.preventDefault() 函数，来阻止表单的提交和页面的跳转，</font>示例代码如下：

![1649904681743](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649904681743.png)

### 3、快速获取表单中的数据

#### 1. serialize()函数

为了简化表单中数据的获取操作，jQuery 提供了 serialize() 函数，其语法格式如下：

![1649904730168](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649904730168.png)

<font color='red'>serialize() 函数的好处：**可以一次性获取到表单中的所有的数据。**</font>

##### 示例：

![1649904756161](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649904756161.png)

![1649904771657](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649904771657.png)

注意：在使用 serialize() 函数快速获取表单数据时，**必须为每个表单元素添加 name 属性！**

## 案例-评论列表

#### UI结构

![1649905071583](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649905071583.png)

#### 获取评论列表

![1649905086435](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649905086435.png)

#### 发表评论

![1649905142745](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649905142745.png)

## 三、模板引擎的基本概念

![1649905195705](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649905195705.png)上述代码是通过字符串拼接的形式，来渲染UI结构。

**如果UI结构比较复杂，则拼接字符串的时候需要格外注意引号之前的嵌套。且一旦需求发生变化，修改起来也非常麻烦。**

### 1、概念

<font color='red'>模板引擎，顾名思义，它可以根据程序员指定的模板结构和数据，自动生成一个完整的HTML页面。</font>

![1649905232403](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649905232403.png)

模板引擎好处：

> 1. 减少了字符串的拼接操作
> 2. 使代码结构更清晰
> 3. 使代码更易于阅读与维护

## 四、art-template模板引擎

art-template 是一个简约、超快的模板引擎。中文官网首页为 http://aui.github.io/art-template/zh-cn/index.html

### 1、art-template安装

在浏览器中访问 http://aui.github.io/art-template/zh-cn/docs/installation.html 页面，找到下载链接后，鼠标右键，选择“链接另存为”，将 art-template 下载到本地，然后，通过 <script> 标签加载到网页上进行使用。

![1649905340156](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649905340156.png)

### 2、art-template模板引擎的基本使用

#### 1. 使用传统方式渲染UI结构

![1649905390377](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649905390377.png)

#### 2. art-template的使用步骤

> - 导入 art-template
> - 定义数据
> - 定义模板
> - 调用 template 函数
> - 渲染HTML结构

### 标准语法

art-template 提供了 {{ }} 这种语法格式，<font color='red'>在 {{ }} 内可以进行变量输出，或循环数组等操作，这种 {{ }} 语法在 art-template 中被称为标准语法。</font>

#### 标准语法-输出

![1649905455096](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649905455096.png)

<font color='red'>在 {{ }} 语法中，可以进行变量的输出、对象属性的输出、三元表达式输出、逻辑或输出、加减乘除等表达式输出。</font>

#### 标准语法-原文输出

![1649905504305](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649905504305.png)

<font color='blue'>**如果要输出的 value 值中，包含了 HTML 标签结构，则需要使用原文输出语法，才能保证 HTML 标签被正常渲染。** </font>

#### 标准语法-条件输出

如果要实现条件输出，则可以在 {{ }} 中使用 if … else if … /if 的方式，进行按需输出。

![1649905565312](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649905565312.png)

#### 标准语法-循环输出

如果要实现循环输出，则可以在 {{ }} 内，通过 each 语法循环数组

1. <font color='red'>当前循环的索引使用 $index 进行访问</font>
2. <font color='red'>当前的循环项使用 $value 进行访问。</font>

![1649905612855](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649905612855.png)

#### 标准语法-过滤器

![1649905638645](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649905638645.png)

**过滤器的本质，就是一个 function 处理函数。**

![1649905654666](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649905654666.png)

过滤器语法类似管道操作符，它的上一个输出作为下一个输入。

定义过滤器的基本语法如下：

![1649905670256](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649905670256.png)

##### 示例：

![1649905687893](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649905687893.png)

**格式化时间的过滤器**

![1649905703684](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649905703684.png)

## 五、模板引擎的实现原理

### 1、正则与字符串操作

#### 基本语法

<font color='red'>**exec() 函数用于检索字符串中的正则表达式的匹配。**</font>

如果字符串中有匹配的值，则返回该匹配值，否则返回 null。

![1649905762769](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649905762769.png)

示例：

![1649905772086](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649905772086.png)

#### 分组

<font color='red'>正则表达式中 ( ) 包起来的内容表示一个分组，可以通过分组来提取自己想要的内容，示例代码如下：</font>

![1649905826843](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649905826843.png)

#### 字符串的replace函数

<font color='blue'>replace() 函数用于在字符串中用一些字符替换另一些字符，语法格式如下：</font>

![1649905850516](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649905850516.png)

示例：

![1649905874704](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649905874704.png)

#### 多次replace

![1649905892292](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649905892292.png)

#### 使用while循环replace

![1649905907076](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649905907076.png)

#### replace替换为真值

![1649905924287](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649905924287.png)

### 2、实现简易的模板引擎

### 1. 实现步骤

1. 定义模板结构
2. 预调用模板引擎
3. 封装 template 函数
4. 导入并使用自定义的模板引擎

### 2、定义模板结构

![1649906005580](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649906005580.png)

### 3、预调用模板引擎

![1649906048190](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649906048190.png)

### 4、封装template函数

![1649906088428](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649906088428.png)

### 5、导入并使用自定义的模板引擎

![1649906133028](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649906133028.png)

# Ajax加强

## 一、XMLHttpRequest的基本使用

### 1、XMLHttpRequest概念

XMLHttpRequest（简称 xhr）是浏览器提供的 Javascript 对象，通过它，可以请求服务器上的数据资源。之前所学的 jQuery 中的 Ajax 函数，就是基于 xhr 对象封装出来的。

![1649906243392](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649906243392.png)

### 2、使用xhr发起GET请求

步骤：

1. 创建 xhr 对象
2. 调用 xhr.open() 函数
3. 调用 xhr.send() 函数
4. 监听 xhr.onreadystatechange 事件

![1649906354171](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649906354171.png)

#### 使用xhr发起带参数的GET请求

使用 xhr 对象发起带参数的 GET 请求时，<font color='red'>只需在调用 xhr.open 期间，为 URL 地址指定参数即可：</font>

![1649906466877](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649906466877.png)

<font color='blue'>这种在 URL 地址后面拼接的参数</font>，叫做<font color='blue'>查询字符串。</font>

#### 查询字符串

> 定义：<font color='red'>查询字符串（URL 参数）是指在 URL 的末尾加上用于向服务器发送信息的字符串（变量）。</font>
>
> 格式：<font color='blue'>将英文的 ? 放在URL 的末尾，然后再加上 参数＝值 ，想加上多个参数的话，使用 & 符号进行分隔。</font>以这个形式，可以将想要发送给服务器的数据添加到 URL 中。

![1649912323594](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649912323594.png)

##### GET请求携带参数的本质

无论使用 $.ajax()，还是使用 get()，又或者直接使用 xhr 对象发起 GET 请求，<font color='red'>当需要携带参数的时候，本质上，都是直接将参数以查询字符串的形式，追加到 URL 地址的后面，发送到服务器的。</font>

![1649912380305](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649912380305.png)

### 3、xhr对象的readyState属性

<font color='blue'>XMLHttpRequest 对象的 readyState 属性，用来表示当前 Ajax 请求所处的状态。</font>每个 Ajax 请求必然处于以下状态中的一个：

![1649906416541](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649906416541.png)

### 4、URL编码与解码

> URL 地址中，只允许出现英文相关的字母、标点符号、数字，因此，在 URL 地址中不允许出现中文字符。
>
> **如果 URL 中需要包含中文这样的字符，则必须对中文字符进行编码（转义）。**
>
> **URL编码的原则：使用安全的字符（没有特殊用途或者特殊意义的可打印字符）去表示那些不安全的字符。**
>
> URL编码原则的通俗理解：使用英文字符去表示非英文字符。

![1649912440999](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649912440999.png)

<font color='red'>**浏览器提供了 URL 编码与解码的 API，分别是：**</font>

- encodeURI()  编码的函数
- decodeURI()  解码的函数

![1649912493934](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649912493934.png)

由于浏览器会自动对 URL 地址进行编码操作，因此，大多数情况下，程序员不需要关心 URL 地址的编码与解码操作。

### 5、使用xhr发起POST请求

步骤：

1. 创建 xhr 对象
2. 调用 xhr.open() 函数
3. 设置 Content-Type 属性（固定写法）
4. 调用 xhr.send() 函数，同时指定要发送的数据
5. 监听 xhr.onreadystatechange 事件

![1649912588947](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649912588947.png)

## 二、数据交换格式

<font color='orange'>**数据交换格式，就是服务器端与客户端之间进行数据传输与交换的格式。**</font>

前端领域，经常提及的**两种数据交换格式分别是 XML 和 JSON。**其中 XML 用的非常少，所以，我们重点要学习的数据交换格式就是 JSON。

![1649912678983](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649912678983.png)

### 1、XML

XML 的英文全称是 EXtensible Markup Language，即<font color='blue'>可扩展标记语言</font>。因此，XML 和 HTML 类似，也是一种标记语言。

![1649912713920](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649912713920.png)

#### XML和HTML的区别

1. XML 和 HTML 虽然都是标记语言，但是，它们两者之间没有任何的关系。
2. <font color='red'>HTML 被设计用来描述网页上的内容，是网页内容的载体</font>
3. <font color='hotpink'>**XML 被设计用来传输和存储数据，是数据的载体**</font>

![1649912782575](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649912782575.png)

#### XML缺点

![1649912804877](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649912804877.png)

### 2、JSON

> 概念：**JSON 的英文全称是 JavaScript Object Notation，即“JavaScript 对象表示法”。**简单来讲，<font color='red'>JSON 就是 Javascript 对象和数组的字符串表示法，它使用文本表示一个 JS 对象或数组的信息，因此，JSON 的本质是字符串。</font>
>
> 作用：JSON 是一种轻量级的文本数据交换格式，在作用上类似于 XML，<font color='blue'>专门用于存储和传输数据，</font>但是 JSON 比 XML 更小、更快、更易解析。
>
> 现状：JSON 是在 2001 年开始被推广和使用的数据格式，到现今为止，JSON 已经成为了主流的数据交换格式。
>
> JSON可以将JavaScript对象中表示的一组数据转换为字符串，可以在网络或程序之间轻松的传递这个字符串，并在需要的时候将其还原为各编程语言所支持的数据格式。

#### 1. JSON的两种结构

<font color='red'>JSON 就是用字符串来表示 Javascript 的对象和数组。</font>所以，JSON 中包含<font color='blue'>对象和数组两种结构</font>，通过这两种结构的相互嵌套，可以表示各种复杂的数据结构。

#### 2. 对象结构

**对象结构：**对象结构在 JSON 中表示为 { } 括起来的内容。<font color='red'>数据结构为 { key: value, key: value, … } 的键值对结构。</font>其中，<font color='red'>key 必须是使用英文的双引号包裹的字符串</font>，value 的数据类型可以是<font color='blue'>数字、字符串、布尔值、null、数组、对象</font>6种类型。

![1649913001119](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649913001119.png)

#### 3. 数组结构

**数组结构：**数组结构在 JSON 中表示为 [ ] 括起来的内容。<font color='red'>数据结构为 [ "java", "javascript", 30, true … ]</font> 。数组中数据的类型可以是<font color='blue'>数字、字符串、布尔值、null、数组、对象</font>6种类型。

![1649913042169](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649913042169.png)

#### 4. JSON语法注意事项

- 属性名必须使用双引号包裹
- 字符串类型的值必须使用双引号包裹
- JSON 中不允许使用单引号表示字符串
- **JSON 中不能写注释**
- JSON 的最外层必须是对象或数组格式
- 不能使用 undefined 或函数作为 JSON 的值
- <font color='red'>**JSON 的作用：在计算机与网络之间存储和传输数据。**</font>
- <font color='blue'>**JSON 的本质：用字符串来表示 Javascript 对象数据或数组数据**</font>

#### 5. JSON和JS对象的关系

**JSON 是 JS 对象的字符串表示法，它使用文本表示一个 JS 对象的信息，本质是一个字符串。**例如：

![1649913140656](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649913140656.png)

#### 6. JSON和JS对象相互转化

<font color='green'>**要实现从 JSON 字符串转换为 JS 对象，使用 JSON.parse() 方法：**</font>

![1649913170073](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649913170073.png)

<font color='hotpink'>**要实现从 JS 对象转换为 JSON 字符串，使用 JSON.stringify() 方法：**</font>

![1649913179296](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649913179296.png)

### 3、序列化和反序列化

把<font color='red'>数据对象转换为字符串的过程，叫做序列化</font>，例如：调用 JSON.stringify() 函数的操作，叫做 JSON 序列化。

把<font color='blue'>字符串转换为数据对象的过程，叫做反序列化，</font>例如：调用 JSON.parse() 函数的操作，叫做 JSON 反序列化。

## 三、封装Ajax函数

![1649913320157](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649913320157.png)

### 1、定义options参数选项

itheima() 函数是我们自定义的 Ajax 函数，<font color='red'>它接收一个配置对象作为参数</font>，配置对象中可以配置如下属性：

- method   请求的类型
- url           请求的 URL 地址
- data        请求携带的数据
- success   请求成功之后的回调函数

### 2、处理data参数

需要把 <font color='red'>data 对象，转化成查询字符串的格式</font>，从而提交给服务器，因此提前定义 resolveData 函数如下：

![1649913397529](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649913397529.png)

### 3、定义itheima函数

在 itheima() 函数中，需要创建 xhr 对象，并监听 onreadystatechange 事件：

![1649913432921](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649913432921.png)

### 4、判断请求的类型

不同的请求类型，对应 xhr 对象的不同操作，因此需要对请求类型进行 if … else … 的判断：

![1649913459279](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649913459279.png)

## 四、XMLHttpRequest Level2的新特性

### 1、旧版XMLHttpRequest的缺点

- 只支持文本数据的传输，无法用来读取和上传文件
- 传送和接收数据时，没有进度信息，只能提示有没有完成

### 2、XMLHttpRequest Level2的新功能

- 可以设置 HTTP 请求的时限
- 可以使用 FormData 对象管理表单数据
- 可以上传文件
- 可以获得数据传输的进度信息

### 3、设置HTTP请求时限

有时，Ajax 操作很耗时，而且无法预知要花多少时间。如果网速很慢，用户可能要等很久。新版本的 XMLHttpRequest 对象，<font color='red'>增加了 timeout 属性，可以设置 HTTP 请求的时限：</font>

![1649913592965](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649913592965.png)

上面的语句，将最长等待时间设为 3000 毫秒。过了这个时限，就自动停止HTTP请求。与之配套的还有一个 timeout 事件，用来指定回调函数：

![1649913607123](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649913607123.png)

### 4、FormData对象管理表单数据

Ajax 操作往往用来提交表单数据。为了方便表单处理，HTML5 新增了一个 FormData 对象，可以模拟表单操作：

![1649913638537](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649913638537.png)

#### FormData对象也可以用来获取网页表单的值

示例代码如下：

![1649914493073](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649914493073.png)

### 5、上传文件

新版 XMLHttpRequest 对象，不仅可以发送文本信息，还可以上传文件。

实现步骤：

1. 定义 UI 结构
2. 验证是否选择了文件
3. 向 FormData 中追加文件
4. 使用 xhr 发起上传文件的请求
5. 监听 onreadystatechange 事件

#### 1.定义UI结构

![1649914548738](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649914548738.png)

#### 2.验证是否选择了文件

![1649914565371](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649914565371.png)

#### 3.向FormData中追加文件

![1649914592581](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649914592581.png)

#### 4.使用xhr发起上传文件的请求

![1649914619495](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649914619495.png)

#### 5.监听onreadystatechange事件

![1649914669656](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649914669656.png)

### 6、显示文件上传进度

新版本的 XMLHttpRequest 对象中，<font color='red'>可以通过监听 xhr.upload.onprogress 事件，来获取到文件的上传进度</font>。语法格式如下：

![1649914703942](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649914703942.png)

#### 1. 导入需要的库

![1649914719718](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649914719718.png)

#### 2. 基于Bootstrap渲染进度条

![1649914732448](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649914732448.png)

#### 3. 监听上传进度的事件

![1649914745243](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649914745243.png)

#### 4. 监听上传完成的事件

![1649914757910](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649914757910.png)

## 五、jQuery高级用法

### 1、jQuery实现文件上传

#### 1. 定义UI结构

![1649914804136](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649914804136.png)

#### 2. 验证是否选择了文件

![1649914814681](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649914814681.png)

#### 3. 向FormData中追加文件

![1649914825919](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649914825919.png)

#### 4. 使用jQuery发起上传文件的请求

![1649914840072](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649914840072.png)

### 2、jQuery实现loading效果

#### 1. ajaxStart(callback)

<font color='red'>Ajax 请求开始时，执行 ajaxStart 函数。</font>可以在 ajaxStart 的 callback 中显示 loading 效果，示例代码如下：

![1649914896523](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649914896523.png)

注意： <font color='red'>$(document).ajaxStart() 函数会监听当前文档内所有的 Ajax 请求。</font>

#### 2. ajaxStop(callback)

<font color='blue'>Ajax 请求结束时，执行 ajaxStop 函数。</font>可以在 ajaxStop 的 callback 中隐藏 loading 效果，示例代码如下：

![1649914953395](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649914953395.png)

## 六、axios

Axios 是专注于网络数据请求的库。

相比于原生的 XMLHttpRequest 对象，axios 简单易用。

相比于 jQuery，axios 更加轻量化，只专注于网络数据请求。

### 1、axios发起GET请求

![1649915000519](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649915000519.png)

![1649915006007](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649915006007.png)

### 2、axios发起POST请求

![1649915021183](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649915021183.png)

![1649915027606](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649915027606.png)

### 3、直接使用axios发起请求

类似于jQuery中的$.ajax()

![1649915042947](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649915042947.png)

#### 1. 直接使用axios发起GET请求

![1649915077102](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649915077102.png)

#### 2. 直接使用axios发起POST请求

![1649915089041](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649915089041.png)

# 跨域与JSONP

## 一、同源策略和跨域

### 1、同源策略

<font color='red'>如果两个页面的协议，域名和端口都相同，则两个页面具有相同的源。</font>

例如，下表给出了相对于 http://www.test.com/index.html 页面的同源检测：

![1649915236401](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649915236401.png)

<font color='blue'>同源策略（英文全称 Same origin policy）是浏览器提供的一个安全功能。</font>

MDN 官方给定的概念：**同源策略限制了从同一个源加载的文档或脚本如何与来自另一个源的资源进行交互。这是一个用于隔离潜在恶意文件的重要安全机制。**

> 通俗的理解：**浏览器规定，A 网站的 JavaScript，不允许和非同源的网站 C 之间，进行资源的交互，**例如：
>
> - 无法读取非同源网页的 Cookie、LocalStorage 和 IndexedDB
> - 无法接触非同源网页的 DOM
> - 无法向非同源地址发送 Ajax 请求

### 2、跨域

<font color='red'>同源指的是两个 URL 的协议、域名、端口一致，反之，则是跨域。</font>

出现跨域的根本原因：<font color='blue'>浏览器的同源策略不允许非同源的 URL 之间进行资源的交互。</font>

网页：http://www.test.com/index.html

接口：http://www.api.com/userlist

#### 1. 浏览器对跨域请求的拦截

![1649915360648](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649915360648.png)

#### 2. 实现跨域数据请求

现如今，<font color='red'>实现跨域数据请求，最主要的两种解决方案，分别是 JSONP 和 CORS</font>

JSONP：出现的早，兼容性好（兼容低版本IE）。是前端程序员为了解决跨域问题，被迫想出来的一种临时解决方案。缺点是只支持 GET 请求，不支持 POST 请求。

CORS：出现的较晚，它是 W3C 标准，属于跨域 Ajax 请求的根本解决方案。支持 GET 和 POST 请求。缺点是不兼容某些低版本的浏览器。

## 二、JSONP

JSONP (JSON with Padding) 是 JSON 的一种“使用模式”，<font color='red'>可用于解决主流浏览器的跨域数据访问的问题。</font>

### 1、JSONP实现原理

由于浏览器同源策略的限制，网页中无法通过 Ajax 请求非同源的接口数据。**但是` <script> `标签不受浏览器同源策略的影响，可以通过 src 属性，请求非同源的 js 脚本。**

因此，**JSONP 的实现原理，就是通过 `<script> `标签的 src 属性，请求跨域的数据接口，并通过<font color='red'>函数调用</font>的形式，接收跨域接口响应回来的数据。**

定义一个 success 回调函数：

![1649915544273](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649915544273.png)

通过` <script> `标签，请求接口数据：

![1649915568820](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649915568820.png)

### 2、JSONP的缺点

由于 JSONP 是通过` <script>` 标签的 src 属性，**来实现跨域数据获取的**，所以，<font color='red'>JSONP 只支持 GET 数据请求，不支持 POST 请求。</font>

注意：JSONP 和 Ajax 之间没有任何关系，不能把 JSONP 请求数据的方式叫做 Ajax，因为 JSONP 没有用到 XMLHttpRequest 这个对象。

### 3、jQuery中的JSONP

jQuery 提供的 $.ajax() 函数，除了可以发起真正的 Ajax 数据请求之外，还能够发起 JSONP 数据请求，例如：

![1649915657174](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649915657174.png)

<font color='blue'>默认情况下，使用 jQuery 发起 JSONP 请求，会自动携带一个 callback=jQueryxxx 的参数，jQueryxxx 是随机生成的一个回调函数名称。</font>

在使用 jQuery 发起 JSONP 请求时，如果想要自定义 JSONP 的参数以及回调函数名称，可以通过如下两个参数来指定：

![1649915714220](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649915714220.png)

#### jQuery中JSONP的实现过程

jQuery 中的 JSONP，也是通过 <script> 标签的 <font color='red'>src 属性实现跨域数据访问的</font>，只不过，jQuery 采用的是动态创建和移除 <script> 标签的方式，来发起 JSONP 数据请求。

在发起 JSONP 请求的时候，动态向 <header> 中 append 一个 <script> 标签；

在 JSONP 请求成功以后，动态从 <header> 中移除刚才 append 进去的 <script> 标签；

## 案例-淘宝搜索

#### UI结构

![1649915804412](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649915804412.png)

#### 获取用户输入的搜索关键词

为了获取到用户每次按下键盘输入的内容，<font color='red'>需要监听输入框的 keyup 事件</font>，示例代码如下：

![1649915841323](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649915841323.png)

#### 封装getSuggestList函数

将获取搜索建议列表的代码，封装到 getSuggestList 函数中，示例代码如下：

![1649915869428](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649915869428.png)

#### 渲染建议列表的UI结构

##### 1. 定义搜索建议列表

![1649915894915](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649915894915.png)

##### 2. 定义模板结构

![1649915920897](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649915920897.png)

##### 3. 定义渲染模板结构的函数

![1649915943501](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649915943501.png)

##### 4. 搜索关键词为空时隐藏搜索建议列表

![1649915978060](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649915978060.png)

### 防抖

<font color='blue'>**防抖策略（debounce）是当事件被触发后，延迟 n 秒后再执行回调，如果在这 n 秒内事件又被触发，则重新计时。**</font>

![1649916030048](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649916030048.png)

应用场景

用户在输入框中连续输入一串字符时，可以通过防抖策略，只在输入完后，才执行查询的请求，这样可以有效减少请求次数，节约请求资源；

#### 实现输入框的防抖

![1649916077994](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649916077994.png)

#### 5. 缓存搜索的建议列表

##### 1. 定义全局缓存对象

![1649916643249](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649916643249.png)

##### 2. 将搜索结果保存到缓存对象中

![1649916662050](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649916662050.png)

##### 3. 优先从缓存中获取搜索建议

![1649916687396](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649916687396.png)

## 三、防抖和节流

<font color='red'>节流策略（throttle），顾名思义，可以减少一段时间内事件的触发频率。</font>

![1649916724872](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649916724872.png)

### 节流的应用

鼠标连续不断地触发某事件（如点击），只在单位时间内只触发一次；

懒加载时要监听计算滚动条的位置，但不必每次滑动都触发，可以降低计算的频率，而不必去浪费 CPU 资源；

### 节流阀的概念

高铁卫生间是否被占用，由红绿灯控制，红灯表示被占用，绿灯表示可使用。
假设每个人上卫生间都需要花费5分钟，则五分钟之内，被占用的卫生间无法被其他人使用。
上一个人使用完毕后，需要将红灯重置为绿灯，表示下一个人可以使用卫生间。
下一个人在上卫生间之前，需要先判断控制灯是否为绿色，来知晓能否上卫生间。

- <font color='red'>节流阀为空，表示可以执行下次操作；不为空，表示不能执行下次操作。</font>
- 当前操作执行完，必<font color='red'>须将节流阀重置为空</font>，表示可以执行下次操作了。
- 每次执行操作前，<font color='blue'>必须先判断节流阀是否为空。</font>

![1649916821034](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649916821034.png)

<font color='orange'>防抖：如果事件被频繁触发，防抖能保证只有最有一次触发生效！前面 N 多次的触发都会被忽略！</font>

<font color='red'>节流：如果事件被频繁触发，节流能够减少事件触发的频率，因此，节流是有选择性地执行一部分事件！</font>

# HTTP协议加强

## 一、HTTP协议

### 1、通信

> <font color='red'>通信，就是信息的传递和交换。</font>

**通信三要素：**

- 通信的<font color='orange'>主体</font>
- 通信的<font color='orange'>内容</font>
- 通信的<font color='orange'>方式</font>

![1650021427743](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650021427743.png)

互联网中的通信

![1650021442251](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650021442251.png)

### 2、通信协议

**通信协议（Communication Protocol）是指通信的双方完成通信所必须遵守的规则和约定。**

通俗的理解：通信双方采用约定好的格式来发送和接收消息，这种事<font color='red'>先约定好的通信格式，就叫做通信协议。</font>

**客户端与服务器之间要实现网页内容的传输，则通信的双方必须遵守网页内容的传输协议。**

> <font color='red'>**网页内容又叫做超文本，**</font>**因此<font color='blue'>网页内容的传输协议又叫做超文本传输协议</font>**（HyperText Transfer Protocol） ，**简称 HTTP 协议。**

### 3、HTTP

#### 3.1 HTTP协议

<font color='red'>HTTP 协议即超文本传送协议 (HyperText Transfer Protocol) ，</font>**它规定了客户端与服务器之间进行网页内容传输时，所必须遵守的传输格式。**

例如：

- 客户端要以HTTP协议要求的格式把数据提交到服务器

- 服务器要以HTTP协议要求的格式把内容响应给客户端

#### 3.2 HTTP协议的交互模型

**<font color='red'>HTTP 协议采用了 请求/响应 的交互模型。</font>**

![1650021600560](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650021600560.png)

## 二、HTTP请求消息

### 1、简介

由于 HTTP 协议属于客户端浏览器和服务器之间的通信协议。因此，<font color='red'>**客户端发起的请求叫做 HTTP 请求，客户端发送到服务器的消息，叫做 HTTP 请求消息。**</font>

<font color='blue'>注意：HTTP 请求消息又叫做 HTTP 请求报文。</font>

### 2、组成部分

> **HTTP 请求消息由<font color='blue'>请求行（request line）</font>、<font color='orange'>请求头部（ header ） </font>、<font color='green'>空行 </font>和 请求体 4 个部分组成。**

![1650021679724](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650021679724.png)

#### 请求行

<font color='red'>请求行由请求方式、URL 和 HTTP 协议版本 3 个部分组成，他们之间使用空格隔开。</font>

![1650021708402](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650021708402.png)

#### 请求头

<font color='red'>**请求头部用来描述客户端的基本信息，从而把客户端相关的信息告知服务器。**</font>

比如：

1. User-Agent 用来说明当前是什么类型的浏览器；
2. **Content-Type 用来描述发送到服务器的数据格式；**
3. Accept 用来描述客户端能够接收什么类型的返回内容；
4. Accept-Language 用来描述客户端期望接收哪种人类语言的文本内容。

<font color='blue'>请求头部由多行 键/值对 组成，每行的键和值之间用英文的冒号分隔。</font>

![1650021780688](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650021780688.png)

![1650021792329](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650021792329.png)

![1650021798996](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650021798996.png)

#### 空行

<font color='red'>最后一个请求头字段的后面是一个空行，通知服务器请求头部至此结束。</font>

请求消息中的空行，用来分隔请求头部与请求体。

![1650021847528](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650021847528.png)

#### 请求体！！！

<font color='red'>请求体中存放的，是要通过 POST 方式提交到服务器的数据。</font>

![1650021866318](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650021866318.png)

**注意：只有 POST 请求才有请求体，GET 请求没有请求体！**

## 三、HTTP响应消息

### 1、简介

<font color='red'>响应消息就是服务器响应给客户端的消息内容，也叫作响应报文。</font>

### 2、组成部分

<font color='blue'>HTTP响应消息由**状态行**、**响应头部**、空行 和 **响应体** 4 个部分组成，如下图所示：</font>

![1650021933865](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650021933865.png)

#### 状态行

<font color='red'>状态行由 HTTP 协议版本、状态码和状态码</font>的描述文本 3 个部分组成，他们之间使用空格隔开;

![1650021966893](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650021966893.png)

#### 响应头部

<font color='blue'>响应头部用来描述服务器的基本信息。响应头部由多行 键/值对 组成，每行的键和值之间用英文的冒号分隔。</font>

![1650021988294](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650021988294.png)

![1650021994250](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650021994250.png)

#### 空行

- 在最后一个响应头部字段结束之后，会紧跟一个空行，用来通知客户端响应头部至此结束。
- **响应消息中的空行，用来分隔响应头部与响应体。**

![1650022022715](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650022022715.png)

#### 响应体

> <font color='red'>响应体中存放的，是服务器响应给客户端的资源内容。</font>

![1650022047834](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650022047834.png)

## 四、HTTP请求方式

### 1、简介

> HTTP 请求方法，属于 HTTP 协议中的一部分，<font color='green'>**请求方法的作用是：用来表明要对服务器上的资源执行的操作。**</font><font color='orange'>最常用的请求方法是 GET 和 POST</font>。

![1650022096361](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650022096361.png)

## 五、HTTP响应状态代码

### 1、简介

> <font color='red'>HTTP 响应状态码（HTTP Status Code），也属于 HTTP 协议的一部分，用来标识响应的状态。</font>
>
> **响应状态码会随着响应消息一起被发送至客户端浏览器**，<font color='green'>浏览器根据服务器返回的响应状态码，就能知道这次 HTTP 请求的结果是成功还是失败了。</font>

![1650022142980](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650022142980.png)

### 2、状态码组成

<font color='green'>**HTTP 状态码由三个十进制数字组成，第一个十进制数字定义了状态码的类型，后两个数字用来对状态码进行细分。**</font>

HTTP 状态码共分为 5 种类型：

![1650022195471](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650022195471.png)

#### 2** 成功相关的响应状态码

> <font color='red'>2** 范围的状态码，表示服务器已成功接收到请求并进行处理。</font>常见的 2** 类型的状态码如下：

![1650022231593](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650022231593.png)

#### 3** 重定向相关的响应状态码

> <font color='orange'>3** 范围的状态码，表示服务器要求客户端重定向，需要客户端进一步的操作以完成资源的请求。</font>常见的 3**类型的状态码如下：

![1650022289567](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650022289567.png)

#### 4** 客户端错误相关的响应状态码

> <font color='blue'>4** 范围的状态码，表示客户端的请求有非法内容，从而导致这次请求失败。</font>常见的 4** 类型的状态码如下：

![1650022319914](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650022319914.png)

#### 5** 服务端错误相关的响应状态码

> <font color='orange'>5** 范围的状态码，表示服务器未能正常处理客户端的请求而出现意外错误。</font>常见的 5** 类型的状态码如下：

![1650022351355](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650022351355.png)

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
























































































































