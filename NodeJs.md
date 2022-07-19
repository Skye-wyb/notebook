# Node.js和内置模块

## 一、Node.js

![1650071632208](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650071632208.png)

### 思考：为什么 JavaScript 可以在浏览器中被执行

![1650071657983](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650071657983.png)

### 思考：为什么 JavaScript 可以操作 DOM 和 BOM

![1650071695480](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650071695480.png)

### 浏览器中的 JavaScript 运行环境

<font color='red'>**运行环境是指代码正常运行所需的必要环境。**</font>

![1650071734529](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650071734529.png)

> 总结：
>
> - V8 引擎负责解析和执行 JavaScript 代码。
> - <font color='red'>内置 API 是由运行环境提供的特殊接口，只能在所属的运行环境中被调用。</font>

### 1、Node.js

Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine.

<font color='blue'>Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境。</font>

Node.js 的官网地址： https://nodejs.org/zh-cn/

#### Node.js 中的 JavaScript 运行环境

![1650071815556](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650071815556.png)

> 注意：
>
> 1. 浏览器是 JavaScript 的前端运行环境。
> 2. Node.js 是 JavaScript 的后端运行环境。
> 3. <font color='red'>Node.js 中无法调用 DOM 和 BOM 等浏览器内置 API。</font>

Node.js 作为一个 JavaScript 的运行环境，仅仅提供了基础的功能和 API。然而，基于 Node.js 提供的这些基础能，很多强大的工具和框架如雨后春笋，层出不穷，所以学会了 Node.js ，可以让前端程序员胜任更多的工作和岗位：

- 基于 Express 框架（http://www.expressjs.com.cn/），可以快速构建 Web 应用
- 基于 Electron 框架（https://electronjs.org/），可以构建跨平台的桌面应用
- 基于 restify 框架（http://restify.com/），可以快速构建 API 接口项目
- 读写和操作数据库、创建实用的命令行工具辅助前端开发、etc…

总之：Node.js 是大前端时代的“大宝剑”，有了 Node.js 这个超级 buff 的加持，前端程序员的行业竞争力会越来越强！

> 浏览器中的 JavaScript 学习路径：
>
> - JavaScript 基础语法 + 浏览器内置 API（DOM + BOM） + 第三方库（jQuery、art-template 等）
>
> Node.js 的学习路径：
>
> - JavaScript 基础语法 + Node.js 内置 API 模块（fs、path、http等）+ 第三方 API 模块（express、mysql 等）

### 2、Node.js环境安装

如果希望通过 Node.js 来运行 Javascript 代码，则必须在计算机上安装 Node.js 环境才行。

安装包可以从 Node.js 的官网首页直接下载，进入到 Node.js 的官网首页（https://nodejs.org/en/），点击绿色的按钮，下载所需的版本后，双击直接安装即可。

#### 1. 区分 LTS 版本和 Current 版本的不同

> - LTS 为长期稳定版，对于追求稳定性的企业级项目来说，推荐安装 LTS 版本的 Node.js。
> - Current 为新特性尝鲜版，对热衷于尝试新特性的用户来说，推荐安装 Current 版本的 Node.js。但是，Current 版本中可能存在隐藏的 Bug 或安全性漏洞，因此不推荐在企业级项目中使用 Current 版本的 Node.js。

> 打开终端，在终端输入命令 node –v 后，按下回车键，即可查看已安装的 Node.js 的版本号。
>
> Windows 系统快速打开终端的方式：
>
> - 使用快捷键（Windows徽标键 + R）打开运行面板，输入 cmd 后直接回车，即可打开终端。

#### 2. 终端

![1650071992608](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650071992608.png)

<font color='red'>终端（英文：Terminal）是专门为开发人员设计的，用于实现人机交互的一种方式。</font>

作为一名合格的程序员，我们有必要识记一些常用的终端命令，来辅助我们更好的操作与使用计算机。

### 3、在 Node.js 环境中执行 JavaScript 代码

1. 打开终端
2. <font color='red'>**输入 node 要执行的js文件的路径**</font>

#### 1. 终端中的快捷键

在 Windows 的 powershell 或 cmd 终端中，我们可以通过如下快捷键，来提高终端的操作效率：

1. 使用 ↑ 键，可以快速定位到上一次执行的命令
2. 使用 tab 键，能够快速补全路径
3. 使用 esc 键，能够快速清空当前已输入的命令
4. 输入 cls 命令，可以清空终端

## 二、fs 文件系统模块

### 1、概念

<font color='blue'>**fs 模块是 Node.js 官方提供的、用来操作文件的模块。它提供了一系列的方法和属性，用来满足用户对文件的操作需求。**</font>

例如：

1. <font color='red'>fs.readFile() 方法，用来读取指定文件中的内容</font>
2. <font color='green'>**fs.writeFile() 方法，用来向指定的文件中写入内容**</font>

如果要在 JavaScript 代码中，使用 fs 模块来操作文件，则需要使用如下的方式先导入它：

![1650072203509](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650072203509.png)

### 2、读取指定文件中的内容

#### 1. fs.readFile() 的语法格式

<font color='red'>**使用 fs.readFile() 方法，可以读取指定文件中的内容，语法格式如下：**</font>

![1650072259413](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650072259413.png)

> 参数解读：
>
> - 参数1：<font color='red'>必选参数，字符串，表示文件的路径。</font>
> - 参数2：可选参数，表示以<font color='green'>什么编码格式</font>来读取文件。
> - 参数3：<font color='blue'>必选参数，文件读取完成后，通过回调函数拿到读取的结果。</font>

##### 示例

以 utf8 的编码格式，读取指定文件的内容，并打印 err 和 dataStr 的值：

![1650072360619](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650072360619.png)

#### 2. 判断文件是否读取成功

<font color='blue'>可以判断 err 对象是否为 null，从而知晓文件读取的结果：</font>

![1650072409986](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650072409986.png)

### 3、向指定的文件中写入内容

#### 1. fs.writeFile() 的语法格式

<font color='red'>使用 fs.writeFile() 方法，可以向指定的文件中写入内容，语法格式如下：</font>

![1650072460837](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650072460837.png)

> 参数解读：
>
> - 参数1：<font color='red'>必选参数，需要指定一个文件路径的字符串，表示文件的存放路径。</font>
> - 参数2：<font color='blue'>必选参数，表示要写入的内容。</font>
> - 参数3：可选参数，表示以什么格式写入文件内容，默认值是 utf8。
> - 参数4：<font color='orange'>必选参数，文件写入完成后的回调函数。</font>

##### 示例

向指定的文件路径中，写入文件内容：

![1650072514259](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650072514259.png)

#### 2. 判断文件是否写入成功

可以判断 err 对象是否为 null，从而知晓文件写入的结果：

![1650072557661](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650072557661.png)

### 4、练习 - 考试成绩整理

使用 fs 文件系统模块，将素材目录下成绩.txt文件中的考试数据，整理到成绩-ok.txt文件中。

整理前，成绩.txt文件中的数据格式如下：

![1650072582023](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650072582023.png)

整理完成之后，希望得到的成绩-ok.txt文件中的数据格式如下：

![1650072590910](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650072590910.png)

实现步骤：

> 1. 导入需要的 fs 文件系统模块
> 2. 使用 fs.readFile() 方法，读取素材目录下的 成绩.txt 文件
> 3. 判断文件是否读取失败
> 4. 文件读取成功后，处理成绩数据
> 5. 将处理完成的成绩数据，调用 fs.writeFile() 方法，写入到新文件 成绩-ok.txt 中

![1650072680507](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650072680507.png)

### 5、fs 模块 - 路径动态拼接的问题

> 在使用 fs 模块操作文件时，如果提供的操作路径是以 ./ 或 ../ 开头的相对路径时，很容易出现路径动态拼接错误的问题。
>
> 原因：代码在运行的时候，会以执行 node 命令时所处的目录，动态拼接出被操作文件的完整路径。
>
> <font color='red'>解决方案：在使用 fs 模块操作文件时，直接提供完整的路径，不要提供 ./ 或 ../ 开头的相对路径，从而防止路径动态拼接的问题。</font>

![1650072788299](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650072788299.png)

![1650072814297](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650072814297.png)

## 三、path 路径模块

### 1、概念

<font color='red'>**path 模块是 Node.js 官方提供的、用来处理路径的模块。**</font>它提供了一系列的方法和属性，用来满足用户对路径的处理需求。

例如：

1. <font color='red'>**path.join() 方法，用来将多个路径片段拼接成一个完整的路径字符串**</font>
2. <font color='green'>**path.basename() 方法，用来从路径字符串中，将文件名解析出来**</font>

如果要在 JavaScript 代码中，使用 path 模块来处理路径，则需要使用如下的方式先导入它：

![1650072946908](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650072946908.png)

### 2、路径拼接

#### 1. path.join() 

<font color='red'>使用 path.join() 方法，可以把多个路径片段拼接为完整的路径字符串，</font>语法格式如下：

![1650072998712](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650072998712.png)

> 参数解读：
>
> - ...paths <string> 路径片段的序列
> - 返回值: <string>

##### 示例

![1650073885368](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650073885368.png)

![1650802502982](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650802502982.png)

### 3、获取路径中的文件名

#### 1. path.basename() 

<font color='red'>使用 path.basename() 方法，可以获取路径中的最后一部分，经常通过这个方法获取路径中的文件名，</font>语法格式如下：

![1650073940714](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650073940714.png)

> 参数解读：
>
> 1. path <string> 必选参数，表示一个路径的字符串
> 2. ext <string> 可选参数，<font color='red'>表示文件扩展名</font>
> 3. 返回: <string> 表示路径中的最后一部分

##### 示例

![1650073968762](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650073968762.png)

### 4、获取路径中的文件扩展名

#### 1. path.extname()

<font color='red'>**使用 path.extname() 方法，可以获取路径中的扩展名部分，**</font>语法格式如下：

![1650074019989](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650074019989.png)

> 参数解读：
>
> - path <string>必选参数，<font color='red'>表示一个路径的字符串</font>
> - 返回: <string> 返回得到的扩展名字符串

##### 示例

![1650802661114](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650802661114.png)

#### 时钟案例

![1650074060243](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650074060243.png)

实现步骤：

> 1. 创建两个正则表达式，分别用来匹配 <style> 和 <script> 标签
> 2. 使用 fs 模块，读取需要被处理的 HTML 文件
> 3. 自定义 resolveCSS 方法，来写入 index.css 样式文件
> 4. 自定义 resolveJS 方法，来写入 index.js 脚本文件
> 5. 自定义 resolveHTML 方法，来写入 index.html 文件

**步骤1 - 导入需要的模块并创建正则表达式**

![1650074101941](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650074101941.png)

**步骤2 - 使用 fs 模块读取需要被处理的 html 文件**

![1650074114064](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650074114064.png)

**步骤3 – 自定义 resolveCSS 方法**

![1650074126204](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650074126204.png)

**步骤4 – 自定义 resolveJS 方法 **

![1650074139080](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650074139080.png)

**步骤5 – 自定义 resolveHTML 方法 **

![1650074151060](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650074151060.png)

**注意：**

> 1. fs.writeFile() 方法只能用来创建文件，不能用来创建路径
> 2. <font color='red'>重复调用 fs.writeFile() 写入同一个文件，新写入的内容会覆盖之前的旧内容</font>

## 四、HTTP模块

### 1、HTTP简介

回顾：什么是客户端、什么是服务器？

**<font color='red'>在网络节点中，负责消费资源的电脑，叫做客户端；</font><font color='blue'>负责对外提供网络资源的电脑，叫做服务器。</font>**

<font color='red'>http 模块是 Node.js 官方提供的、用来创建 web 服务器的模块。</font><font color='blue'>通过 **http 模块提供的 http.createServer() 方法**，就能方便的把一台普通的电脑，变成一台 Web 服务器，从而对外提供 Web 资源服务。</font>

如果要希望使用 http 模块创建 Web 服务器，则需要先导入它：

![1650074341102](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650074341102.png)

> 服务器和普通电脑的区别在于，服务器上安装了 web 服务器软件，例如：IIS、Apache 等。通过安装这些服务器软件，就能把一台普通的电脑变成一台 web 服务器。
>
> 在 Node.js 中，我们不需要使用 IIS、Apache 等这些第三方 web 服务器软件。因为我们可以基于 Node.js 提供的 http 模块，通过几行简单的代码，就能轻松的手写一个服务器软件，从而对外提供 web 服务。

### 2、服务器相关概念

#### 1. IP 地址

> <font color='red'>IP 地址就是互联网上每台计算机的唯一地址，因此 IP 地址具有唯一性。</font>如果把“个人电脑”比作“一台电话”，那么“IP地址”就相当于“电话号码”，只有在知道对方 IP 地址的前提下，才能与对应的电脑之间进行数据通信。
>
> IP 地址的格式：通常用“点分十进制”表示成（a.b.c.d）的形式，其中，a,b,c,d 都是 0~255 之间的十进制整数。例如：用点分十进表示的 IP地址（192.168.1.1）
>
> 注意：
>
> - 互联网中每台 Web 服务器，都有自己的 IP 地址，例如：大家可以在 Windows 的终端中运行 ping www.baidu.com 命令，即可查看到百度服务器的 IP 地址。
> - 在开发期间，自己的电脑既是一台服务器，也是一个客户端，为了方便测试，可以在自己的浏览器中输入 127.0.0.1 这个 IP 地址，就能把自己的电脑当做一台服务器进行访问了。

#### 2. 域名和域名服务器

尽管 IP 地址能够唯一地标记网络上的计算机，但IP地址是一长串数字，不直观，而且不便于记忆，于是人们又发明了<font color='red'>**另一套字符型的地址方案，即所谓的域名（Domain Name）地址。**</font>

<font color='blue'>IP地址和域名是一一对应的关系，这份对应关系存放在一种叫做域名服务器(DNS，Domain name server)的电脑中。</font>使用者只需通过好记的域名访问对应的服务器即可，对应的转换工作由域名服务器实现。因此，<font color='green'>**域名服务器就是提供 IP 地址和域名之间的转换服务的服务器。**</font>

注意：

- 单纯使用 IP 地址，互联网中的电脑也能够正常工作。但是有了域名的加持，能让互联网的世界变得更加方便。
- 在开发测试期间， 127.0.0.1 对应的域名是 localhost，它们都代表我们自己的这台电脑，在使用效果上没有任何区别。

#### 3. 端口号

计算机中的端口号，就好像是现实生活中的门牌号一样。通过门牌号，外卖小哥可以在整栋大楼众多的房间中，准确把外卖送到你的手中。

同样的道理，在一台电脑中，可以运行成百上千个 web 服务。每个 web 服务都对应一个唯一的端口号。客户端发送过来的网络请求，通过端口号，可以被准确地交给对应的 web 服务进行处理。

![1650074562722](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650074562722.png)

### 3、创建最基本的 web 服务器

#### 1. 创建 web 服务器的基本步骤

1. 导入 http 模块
2. 创建 web 服务器实例
3. 为服务器实例绑定 request 事件，监听客户端的请求
4. 启动服务器

##### 步骤1-导入 http 模块

如果希望在自己的电脑上创建一个 web 服务器，从而对外提供 web 服务，则需要导入 http 模块：![1650074633144](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650074633144.png)

##### 步骤2-创建 web 服务器实例

<font color='red'>调用 http.createServer() 方法，即可快速创建一个 web 服务器实例：</font>

![1650074671971](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650074671971.png)

##### 步骤3-为服务器实例绑定 request 事件

<font color='blue'>为服务器实例绑定 request 事件，即可监听客户端发送过来的网络请求：</font>

![1650074700324](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650074700324.png)

##### 步骤4-启动服务器

<font color='green'>调用服务器实例的 .listen() 方法</font>，即可启动当前的 web 服务器实例：

![1650074731486](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650074731486.png)

![1650802818634](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650802818634.png)

#### 2. req 请求对象

只要服务器接收到了客户端的请求，就会<font color='red'>调用通过 server.on() 为服务器绑定的 request 事件处理函数。</font>

<font color='blue'>如果想在事件处理函数中，**访问与客户端相关的数据或属性，**</font>可以使用如下的方式：

![1650074769623](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650074769623.png)

![1650803134393](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650803134393.png)

#### 3. res 响应对象

<font color='green'>**在服务器的 request 事件处理函数中，如果想访问与服务器相关的数据或属性，**</font>可以使用如下的方式：![1650074826236](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650074826236.png)

![1650803268107](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650803268107.png)

### res.end()和res.send()区别

>  1. **<font color='blue'>如果服务器端没有数据要返回到客户端的话，就直接用res.end()。</font>**主要用于结束响应过程，也可以传递数据，但仅限于字符串和Buffer，否则会出现中文乱码！
>   2. **<font color='hotpink'>如果服务器需要有数据返回到客户端的话，就需要用res.send()。</font>**

#### 4. 解决中文乱码问题

<font color='red'>当调用 res.end() 方法，**向客户端发送中文内容的时候，会出现乱码问题**，此时，需要手动设置内容的编码格式：</font>

![1650074866647](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650074866647.png)

![1650803595236](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650803595236.png)

### 4、根据不同的 url 响应不同的 html 内容

> 1. 获取请求的 url 地址
> 2. 设置默认的响应内容为 404 Not found
> 3. 判断用户请求的是否为 / 或 /index.html 首页
> 4. 判断用户请求的是否为 /about.html 关于页面
> 5. 设置 Content-Type 响应头，防止中文乱码
> 6. 使用 res.end() 把内容响应给客户端

![1650803639118](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650803639118.png)

### 案例 - 实现 clock 时钟的 web 服务器

**核心思路**

<font color='red'>把文件的实际存放路径，作为每个资源的请求 url 地址。</font>

![1650074978383](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650074978383.png)

> 1. 导入需要的模块
> 2. 创建基本的 web 服务器
> 3. 将资源的请求 url 地址映射为文件的存放路径
> 4. 读取文件内容并响应给客户端
> 5. 优化资源的请求路径

#### 步骤1 - 导入需要的模块

![1650075007910](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650075007910.png)

#### 步骤2 - 创建基本的 web 服务器

![1650075018594](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650075018594.png)

#### 步骤3 - 将资源的请求 url 地址映射为文件的存放路径

![1650075033204](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650075033204.png)

#### 步骤4 - 读取文件的内容并响应给客户端

![1650075045665](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650075045665.png)

#### 步骤5 – 优化资源的请求路径

![1650075059450](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650075059450.png)

完整代码：

![1650803743555](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650803743555.png)

# 模块化

## 一、模块化基本概念

### 1、定义

<font color='red'>**模块化是指解决一个复杂问题时，自顶向下逐层把系统划分成若干模块的过程。**</font>对于整个系统来说，模块是可组合、分解和更换的单元。

> <font color='blue'>编程领域中的模块化，就是遵守固定的规则，把一个大文件拆成独立并互相依赖的多个小模块。</font>
>
> 把代码进行模块化拆分的好处：
>
> 1. 提高了代码的<font color='orange'>复用性</font>
> 2. 提高了代码的<font color='orange'>可维护性</font>
> 3. 可以实现<font color='orange'>按需加载</font>

### 2、模块化规范

<font color='red'>模块化规范就是对代码进行模块化的拆分与组合时，需要遵守的那些规则。</font>

例如：

1. 使用什么样的语法格式来引用模块
2. 在模块中使用什么样的语法格式向外暴露成员


模块化规范的好处：大家都遵守同样的模块化规范写代码，降低了沟通的成本，极大方便了各个模块之间的相互调用，利人利己。

## 二、Node.js 中模块化

### 1、Node.js中模块化的分类

Node.js 中根据模块来源的不同，将模块分为了 3 大类，分别是：

1. <font color='red'>内置模块（内置模块是由 Node.js 官方提供的，例如 fs、path、http 等）</font>
2. <font color='green'>自定义模块（用户创建的每个 .js 文件，都是自定义模块）</font>
3. 第三方模块（由第三方开发出来的模块，并非官方提供的内置模块，也不是用户创建的自定义模块，使用前需要先下载）

### 2、加载模块

使用强大的 <font color='red'>require() 方法，</font>可以<font color='blue'>加载需要的内置模块、用户自定义模块、第三方模块进行使用。</font>例如：

![1650075342744](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650075342744.png)

**注意：使用 require() 方法加载其它模块时，会执行被加载模块中的代码。**

### 3、Node.js 中的模块作用域

#### 1. 定义

和函数作用域类似，<font color='red'>在自定义模块中定义的变量、方法等成员，只能在当前模块内被访问，这种模块级别的访问限制，叫做模块作用域。</font>

![1650075427253](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650075427253.png)

#### 3. 模块作用域的好处

防止了全局变量污染的问题

![1650075460362](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650075460362.png)

### 4、向外共享模块作用域中的成员

#### 1. module 对象

在每个 .js 自定义模块中都有一个 module 对象，它<font color='red'>里面存储了和当前模块有关的信息</font>，打印如下：

![1650803884061](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650803884061.png)

![1650803861297](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650803861297.png)

#### 2. module.exports 对象

<font color='red'>在自定义模块中，可以使用 module.exports 对象，将模块内的成员共享出去，供外界使用。</font>

外界用 require() 方法导入自定义模块时，得到的就是 module.exports 所指向的对象。

##### 共享成员时的注意点

使用 <font color='red'>require() 方法导入模块时，导入的结果，永远以 module.exports 指向的对象为准。</font>

![1650075628731](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650075628731.png)

#### 4. exports 对象

由于 module.exports 单词写起来比较复杂，为了简化向外共享成员的代码，<font color='red'>Node 提供了 exports 对象。默认情况下，exports 和 module.exports 指向同一个对象。</font>**最终共享的结果，还是以 module.exports 指向的对象为准。**

![1650075689540](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650075689540.png)

##### exports 和 module.exports 的使用误区

<font color='blue'>时刻谨记，require() 模块时，得到的永远是 module.exports 指向的对象：</font>

![1650075740450](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650075740450.png)

注意：为了防止混乱，建议大家不要在同一个模块中同时使用 exports 和 module.exports

### 5、Node.js 中的模块化规范

<font color='red'>Node.js 遵循了 CommonJS 模块化规范，CommonJS 规定了模块的特性和各模块之间如何相互依赖。</font>

CommonJS 规定：

1. <font color='red'>每个模块内部，module 变量代表当前模块。</font>
2. <font color='blue'>module 变量是一个对象，它的 exports 属性（即 module.exports）是对外的接口。</font>
3. <font color='green'>加载某个模块，其实是加载该模块的 module.exports 属性。require() 方法用于加载模块。</font>

## 三、npm与包

### 1、包

#### 包的定义

<font color='red'>Node.js 中的第三方模块又叫做包。</font>

就像电脑和计算机指的是相同的东西，第三方模块和包指的是同一个概念，只不过叫法不同。

#### 包的来源

**不同于 Node.js 中的内置模块与自定义模块，包是由第三方个人或团队开发出来的，免费供所有人使用。**

注意：Node.js 中的包都是免费且开源的，不需要付费即可免费下载使用。

#### 为什么需要包

由于 Node.js 的内置模块仅提供了一些底层的 API，导致在基于内置模块进行项目开发的时，效率很低。

**包是基于内置模块封装出来的，提供了更高级、更方便的 API，极大的提高了开发效率。**

包和内置模块之间的关系，类似于 jQuery 和 浏览器内置 API 之间的关系。

#### 下载包

国外有一家 IT 公司，叫做 npm, Inc. 这家公司旗下有一个非常著名的网站： https://www.npmjs.com/ ，它是全球最大的包共享平台，你可以从这个网站上搜索到任何你需要的包，只要你有足够的耐心！

到目前位置，全球约 1100 多万的开发人员，通过这个包共享平台，开发并共享了超过 120 多万个包 供我们使用。

npm, Inc. 公司提供了一个地址为 https://registry.npmjs.org/ 的服务器，来对外共享所有的包，我们可以从这个服务器上下载自己所需要的包。

注意：
 从 https://www.npmjs.com/ 网站上搜索自己所需要的包

 从 https://registry.npmjs.org/  服务器上下载自己需要的包

> npm, Inc. 公司提供了一个包管理工具，我们可以使用这个包管理工具，从 https://registry.npmjs.org/ 服务器把需要的包下载到本地使用。
>
> 这个包管理工具的名字叫做 Node Package Manager（简称 npm 包管理工具），这个包管理工具随着 Node.js 的安装包一起被安装到了用户的电脑上。
>
> 大家可以**在终端中执行 npm -v 命令，来查看自己电脑上所安装的 npm 包管理工具的版本号：**

![1650078002148](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650078002148.png)

### 2、npm初体验

#### 1. 格式化时间的传统做法

dateFormat.js

![1650804103158](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650804103158.png)

![1650804045402](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650804045402.png)

1. 创建格式化时间的自定义模块
2. 定义格式化时间的方法
3. 创建补零函数
4. 从自定义模块中导出格式化时间的函数
5. 导入格式化时间的自定义模块
6. 调用格式化时间的函数

#### 2. 格式化时间的高级做法

> 1. 使用 npm 包管理工具，在项目中安装格式化时间的包 moment
> 2. 使用 require() 导入格式化时间的包
> 3. 参考 moment 的官方 API 文档对时间进行格式化

![1650078128498](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650078128498.png)

#### 3. 在项目中安装包的命令

如果想在项目中安装指定名称的包，需要运行如下的命令：

![1650078178073](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650078178073.png)

上述的装包命令，可以简写成如下格式：

![1650078187618](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650078187618.png)

初次装包完成后，在项目文件夹下多一个叫做 node_modules 的文件夹和 package-lock.json 的配置文件。

其中：

1. <font color='red'>node_modules 文件夹用来存放所有已安装到项目中的包。require() 导入第三方包时，就是从这个目录中查找并加载包。</font>
2. <font color='blue'>package-lock.json 配置文件用来记录 node_modules 目录下的每一个包的下载信息，例如包的名字、版本号、下载地址等。</font>

注意：程序员不要手动修改 node_modules 或 package-lock.json 文件中的任何代码，npm 包管理工具会自动维护它们。



#### 5. 安装指定版本的包

默认情况下，使用 npm install 命令安装包的时候，**会自动安装最新版本的包**。如果需要安装指定版本的包，可以在包名之后，通过<font color='red'> @ 符号指定具体的版本</font>，例如：

![1650078257623](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650078257623.png)

#### 6. 包的语义化版本规范

包的版本号是以“点分十进制”形式进行定义的，总共有三位数字，例如 2.24.0

其中每一位数字所代表的的含义如下：

- 第1位数字：大版本
- 第2位数字：功能版本
- 第3位数字：Bug修复版本

版本号提升的规则：只要前面的版本号增长了，则后面的版本号归零。

### 3、包管理配置文件

npm 规定，<font color='red'>在项目根目录中，必须提供一个叫做 package.json 的包管理配置文件。</font><font color='blue'>用来记录与项目有关的一些配置信息。</font>例如：

- 项目的名称、版本号、描述等
- 项目中都用到了哪些包
- 哪些包只在开发期间会用到
- 那些包在开发和部署时都需要用到

![1650078375335](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650078375335.png)

> 在项目根目录中，创建一个叫做 package.json 的配置文件，即可用来记录项目中安装了哪些包。从而方便剔除 node_modules 目录之后，在团队成员之间共享项目的源代码。
>
> <font color='red'>注意：今后在项目开发中，一定要把 node_modules 文件夹，添加到 .gitignore 忽略文件中。</font>

#### 1. 快速创建 package.json

<font color='red'>npm </font>包管理工具提供了一个快捷命令，可以在执行命令时所处的目录中，<font color='blue'>快速创建 package.json 这个包管理配置文件：</font>

![1650078423952](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650078423952.png)

注意：

1. 上述命令只能在英文的目录下成功运行！所以，项目文件夹的名称一定要使用英文命名，不要使用中文，不能出现空格。
2. 运行 npm install 命令安装包的时候，npm 包管理工具会自动把包的名称和版本号，记录到 package.json 中。

##### dependencies 节点

![1650078478151](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650078478151.png)

<font color='red'>package.json 文件中，有一个 dependencies 节点，专门用来记录您使用 npm install 命令安装了哪些包。</font>

#### 2. 一次性安装所有的包

当我们<font color='red'>拿到一个剔除了 node_modules 的项目之后，需要先把所有的包下载到项目中，才能将项目运行起来。</font>
否则会报类似于下面的错误：

![1650078526471](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650078526471.png)

可以运行 <font color='red'>npm install 命令（或 npm i）一次性安装所有的依赖包</font>：

![1650078546808](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650078546808.png)

#### 3. 卸载包

可以<font color='red'>运行 npm uninstall 命令，来卸载指定的包</font>：

![1650078572442](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650078572442.png)

注意：npm uninstall 命令执行成功后，会把卸载的包，自动从 package.json 的 dependencies 中移除掉。

##### devDependencies 节点

**如果某些包只在项目开发阶段会用到，在项目上线之后不会用到，则建议把这些包记录到 devDependencies 节点中。**

**与之对应的，如果某些包在开发和项目上线之后都需要用到，则建议把这些包记录到 dependencies 节点中。**

您可以使用如下的命令，将包记录到 devDependencies 节点中：

![1650078624303](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650078624303.png)

### 4、解决下包速度慢的问题

在使用 npm 下包的时候，默认从国外的 https://registry.npmjs.org/ 服务器进行下载，此时，网络数据的传输需要经过漫长的海底光缆，因此下包速度会很慢。

扩展阅读 - 海底光缆：
https://baike.baidu.com/item/%E6%B5%B7%E5%BA%95%E5%85%89%E7%BC%86/4107830
https://baike.baidu.com/item/%E4%B8%AD%E7%BE%8E%E6%B5%B7%E5%BA%95%E5%85%89%E7%BC%86/10520363
https://baike.baidu.com/item/APG/23647721?fr=aladdin

#### 淘宝 NPM 镜像服务器

![1650078689895](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650078689895.png)

#### 切换 npm 的下包镜像源

<font color='red'>下包的镜像源，指的就是下包的服务器地址。</font>

![1650804219884](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650804219884.png)

#### nrm

为了更方便的切换下包的镜像源，我们可以安装 nrm 这个小工具，**利用 nrm 提供的终端命令，可以快速查看和切换下包的镜像源。**

![1650804255087](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650804255087.png)

### 5、包的分类

使用 npm 包管理工具下载的包，共分为两大类，分别是：

1. <font color='red'>项目包</font>
2. <font color='red'>全局包</font>

#### 1. 项目包

<font color='red'>**那些被安装到项目的 node_modules 目录中的包，都是项目包。**</font>

项目包又分为两类，分别是：

1. 开发依赖包（被记录到 devDependencies 节点中的包，只在开发期间会用到）

2. 核心依赖包（被记录到 dependencies 节点中的包，在开发期间和项目上线之后都会用到）

![1650078825557](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650078825557.png)

#### 2. 全局包

<font color='blue'>在执行 npm install 命令时，如果提供了 -g 参数，则会把包安装为全局包。</font>

全局包会被安装到 C:\Users\用户目录\AppData\Roaming\npm\node_modules 目录下。

或者自己更改的文件夹：

![1650078942270](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650078942270.png)

注意：

1. 只有工具性质的包，才有全局安装的必要性。因为它们提供了好用的终端命令。
2. 判断某个包是否需要全局安装后才能使用，可以参考官方提供的使用说明即可。

#### 3. i5ting_toc

i5ting_toc 是一个可以把 md 文档转为 html 页面的小工具，使用步骤如下：

![1650078975271](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650078975271.png)

### 6、规范的包结构

在清楚了包的概念、以及如何下载和使用包之后，接下来，我们深入了解一下包的内部结构。

一个规范的包，它的组成结构，必须符合以下 3 点要求：

1. 包必须以单独的目录而存在
2. 包的顶级目录下要必须包含 package.json 这个包管理配置文件
3. package.json 中必须包含 name，version，main 这三个属性，分别代表包的名字、版本号、包的入口。

注意：以上 3 点要求是一个规范的包结构必须遵守的格式，关于更多的约束，可以参考如下网址：
https://yarnpkg.com/zh-Hans/docs/package-json

### 开发属于自己的包

#### 1. 需要实现的功能

1. 格式化日期

2. 转义 HTML 中的特殊字符
3. 还原 HTML 中的特殊字符

![1650080003848](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650080003848.png)

![1650080010709](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650080010709.png)

![1650080023005](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650080023005.png)

#### 2. 初始化包的基本结构

新建 itheima-tools 文件夹，作为包的根目录

在 itheima-tools 文件夹中，新建如下三个文件：

- package.json （包管理配置文件）
- index.js          （包的入口文件）
- README.md  （包的说明文档）

#### 3. 初始化 package.json

![1650080068994](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650080068994.png)

#### 4. 在 index.js 中定义格式化时间的方法

![1650080082148](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650080082148.png)

#### 5. 在 index.js 中定义转义 HTML 的方法

![1650080096194](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650080096194.png)

#### 6. 在 index.js 中定义还原 HTML 的方法

![1650080112135](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650080112135.png)

#### 7. 将不同的功能进行模块化拆分

1. 将格式化时间的功能，拆分到 src -> dateFormat.js 中
2. 将处理 HTML 字符串的功能，拆分到 src -> htmlEscape.js 中
3. 在 index.js 中，导入两个模块，得到需要向外共享的方法
4. 在 index.js 中，使用 module.exports 把对应的方法共享出去

#### 8. 编写包的说明文档

包根目录中的 <font color='red'>README.md 文件，是包的使用说明文档。</font>通过它，我们可以事先把包的使用说明，以 markdown 的格式写出来，方便用户参考。

README 文件中具体写什么内容，没有强制性的要求；只要能够清晰地把包的作用、用法、注意事项等描述清楚即可。

我们所创建的这个包的 README.md 文档中，会包含以下 6 项内容：

- 安装方式、导入方式、格式化时间、转义 HTML 中的特殊字符、还原 HTML 中的特殊字符、开源协议

### 发布包

#### 1. 注册 npm 账号

1. 访问 https://www.npmjs.com/ 网站，点击 sign up 按钮，进入注册用户界面
2. 填写账号相关的信息：Full Name、Public Email、Username、Password
3. 点击 Create an Account 按钮，注册账号
4. 登录邮箱，点击验证链接，进行账号的验证

#### 2. 登录 npm 账号

npm 账号注册完成后，可以在<font color='red'>终端中执行 npm login 命令</font>，依次输入用户名、密码、邮箱后，即可登录成功。

![1650080219054](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650080219054.png)

注意：在运行 npm login 命令之前，必须先把下包的服务器地址切换为 npm 的官方服务器。否则会导致发布包失败！

#### 3. 把包发布到 npm 上

将终端切换到包的根目录之后，<font color='red'>运行 npm publish 命令</font>，即可将包发布到 npm 上（**注意：包名不能雷同**）。

![1650080249100](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650080249100.png)

#### 4. 删除已发布的包

运行<font color='red'> npm unpublish 包名 --force 命令</font>，即可从 npm 删除已发布的包。

![1650080274122](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650080274122.png)

注意：

1. npm unpublish 命令只能删除 72 小时以内发布的包
2. npm unpublish 删除的包，在 24 小时内不允许重复发布
3. 发布包的时候要慎重，尽量不要往 npm 上发布没有意义的包！

## 四、模块的加载机制

### 1、优先从缓存中加载

<font color='red'>**模块在第一次加载后会被缓存。**</font> 这也意味着多次调用 require() 不会导致模块的代码被执行多次。

注意：不论是内置模块、用户自定义模块、还是第三方模块，它们<font color='blue'>都会优先从缓存中加载，从而提高模块的加载效率。</font>

### 2、内置模块的加载机制

<font color='red'>内置模块是由 Node.js 官方提供的模块，内置模块的加载优先级最高。</font>

例如，require('fs') 始终返回内置的 fs 模块，即使在 node_modules 目录下有名字相同的包也叫做 fs。

### 3、自定义模块的加载机制

<font color='orange'>**使用 require() 加载自定义模块时，必须指定以 ./ 或 ../ 开头的路径标识符。在加载自定义模块时，如果没有指定 ./ 或 ../ 这样的路径标识符，则 node 会把它当作内置模块或第三方模块进行加载。**</font>

同时，在使用 require() 导入自定义模块时，如果省略了文件的扩展名，则 Node.js 会按顺序分别尝试加载以下的文件：

1. 按照确切的文件名进行加载
2. 补全 .js 扩展名进行加载
3. 补全 .json 扩展名进行加载
4. 补全 .node 扩展名进行加载
5. 加载失败，终端报错

### 4、第三方模块的加载机制

<font color='red'>如果传递给 require() 的模块标识符不是一个内置模块，也没有以 ‘./’ 或 ‘../’ 开头，则 Node.js 会从当前模块的父目录开始，尝试从 /node_modules 文件夹中加载第三方模块。</font>

<font color='orange'>如果没有找到对应的第三方模块，则移动到再上一层父目录中，进行加载，直到文件系统的根目录。</font>

例如，假设在 'C:\Users\itheima\project\foo.js' 文件里调用了 require('tools')，则 Node.js 会按以下顺序查找：

1. C:\Users\itheima\project\node_modules\tools

2. C:\Users\itheima\node_modules\tools

3. C:\Users\node_modules\tools

4. C:\node_modules\tools

### 5、目录作为模块

当把目录作为模块标识符，传递给 require() 进行加载的时候，有三种加载方式：

1. 在被加载的目录下查找一个叫做 **package.json 的文件，并寻找 main 属性，作为 require() 加载的入口**
2. 如果目录里**没有 package.json 文件，或者 main 入口不存在或无法解析，则 Node.js 将会试图加载目录下的 index.js 文件。**
3. 如果以上两步都失败了，则 Node.js 会在终端打印错误消息，报告模块的缺失：Error: Cannot find module 'xxx'

# Express

## 一、初始Express

官方给出的概念：Express 是基于 Node.js 平台，快速、开放、极简的 Web 开发框架。

通俗的理解：Express 的作用和 Node.js 内置的 http 模块类似，是专门用来创建 Web 服务器的。

**Express 的本质：就是一个 npm 上的第三方包，提供了快速创建 Web 服务器的便捷方法。**

Express 的中文官网： http://www.expressjs.com.cn/

> 思考：不使用 Express 能否创建 Web 服务器？
> 答案：能，使用 Node.js 提供的原生 http 模块即可。
>
> 思考：既生瑜何生亮（有了 http 内置模块，为什么还有用 Express）？
> 答案：http 内置模块用起来很复杂，开发效率低；Express 是基于内置的 http 模块进一步封装出来的，能够极大的提高开发效率。
>
> 思考：http 内置模块与 Express 是什么关系？
> 答案：类似于浏览器中 Web API 和 jQuery 的关系。后者是基于前者进一步封装出来的。

对于前端程序员来说，最常见的两种服务器，分别是：

1. <font color='red'>Web 网站服务器：专门对外提供 Web 网页资源的服务器。</font>
2. <font color='blue'>API 接口服务器：专门对外提供 API 接口的服务器。</font>

使用 Express，我们可以方便、快速的创建 Web 网站的服务器或 API 接口的服务器。

### 1、基本使用

#### 1. 安装

在项目所处的目录中，运行如下的终端命令，即可将 express 安装到项目中使用：

![1650086515808](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650086515808.png)

#### 2. 创建基本的 Web 服务器

![1650086547148](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650086547148.png)

![1650804869524](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650804869524.png)

#### 3. 监听 GET 请求

<font color='red'>通过 app.get() 方法，可以监听客户端的 GET 请求</font>，具体的语法格式如下：

![1650086593633](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650086593633.png)

![1650804999491](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650804999491.png)

#### 4. 监听 POST 请求

<font color='blue'>通过 app.post() 方法，可以监听客户端的 POST 请求</font>，具体的语法格式如下：

![1650086638833](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650086638833.png)

![1650805036515](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650805036515.png)

#### 5. 把内容响应给客户端

<font color='red'>通过 res.send() 方法，可以把处理好的内容，发送给客户端</font>：

![1650086676636](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650086676636.png)

![1650805077704](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650805077704.png)

#### 6. 获取 URL 中携带的查询参数

<font color='blue'>通过 req.query 对象，可以访问到客户端通过查询字符串的形式，发送到服务器的参数</font>：

![1650086706406](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650086706406.png)

![1650805143362](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650805143362.png)

#### 7. 获取 URL 中的动态参数

<font color='red'>通过 req.params 对象，可以访问到 URL 中，通过 : 匹配到的动态参数</font>：

![1650086785430](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650086785430.png)

![1650805208905](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650805208905.png)

### 2、托管静态资源

#### 1. express.static()

<font color='red'>express 提供了一个非常好用的函数，叫做 express.static()，通过它，我们可以非常方便地创建一个静态资源服务器</font>，例如，通过如下代码就可以将 public 目录下的图片、CSS 文件、JavaScript 文件对外开放访问了：

![1650086822961](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650086822961.png)

> 现在，你就可以访问 public 目录中的所有文件了：
>
> http://localhost:3000/images/bg.jpg
>
> http://localhost:3000/css/style.css
>
> http://localhost:3000/js/login.js

<font color='red'>注意：Express 在指定的静态目录中查找文件，并对外提供资源的访问路径。</font>

<font color='green'>因此，存放静态文件的目录名不会出现在 URL 中。</font>

#### 2. 托管多个静态资源目录

<font color='red'>如果要托管多个静态资源目录，请多次调用 express.static() 函数</font>：

![1650086885767](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650086885767.png)

访问静态资源文件时，express.static() 函数会根据目录的添加顺序查找所需的文件。

![1650805389564](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650805389564.png)

#### 3. 挂载路径前缀

<font color='red'>如果希望在托管的静态资源访问路径之前，挂载路径前缀</font>，则可以使用如下的方式：

![1650086946619](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650086946619.png)

![1650805443130](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650805443130.png)

> 现在，你就可以通过带有 /public 前缀地址来访问 public 目录中的文件了：
>
> http://localhost:3000/public/images/kitten.jpg
>
> http://localhost:3000/public/css/style.css
>
> http://localhost:3000/public/js/app.js

### 3、nodemon

在编写调试 Node.js 项目的时候，如果修改了项目的代码，则需要频繁的手动 close 掉，然后再重新启动，非常繁琐。

现在，我们可以使用 nodemon（https://www.npmjs.com/package/nodemon） 这个工具，**它能够监听项目文件的变动，当代码被修改后，nodemon 会自动帮我们重启项目，极大方便了开发和调试。**

#### 1. 安装 nodemon

在终端中，运行如下命令，即可将 nodemon 安装为全局可用的工具：

![1650087008341](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650087008341.png)

#### 2. 使用 nodemon

当基于 Node.js 编写了一个网站应用的时候，传统的方式，是运行 node app.js 命令，来启动项目。这样做的坏处是：代码被修改之后，需要手动重启项目。

现在，我们可以将 node 命令替换为 nodemon 命令，使用 nodemon app.js 来启动项目。这样做的好处是：代码被修改之后，会被 nodemon 监听到，从而实现自动重启项目的效果。

![1650087030585](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650087030585.png)

## 二、Express路由

### 1、路由的概念

广义上来讲，<font color='red'>路由就是映射关系。</font>

<font color='red'>在 Express 中，路由指的是客户端的请求与服务器处理函数之间的映射关系。</font>

Express 中的路由分 3 部分组成，<font color='blue'>分别是请求的类型、请求的 URL 地址、处理函数</font>，格式如下：

![1650087099101](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650087099101.png)

##### 案例

![1650087107529](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650087107529.png)

![1650805598476](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650805598476.png)

#### 路由的匹配过程

<font color='red'>每当一个请求到达服务器之后，需要先经过路由的匹配，只有匹配成功之后，才会调用对应的处理函数。</font>

在匹配时，会按照路由的顺序进行匹配，**如果请求类型和请求的 URL 同时匹配成功，则 Express 会将这次请求，转交给对应的 function 函数进行处理。**

![1650087186691](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650087186691.png)

<font color='red'>路由匹配的注意点：</font>

1. 按照定义的先后顺序进行匹配
2. <font color='blue'>请求类型和请求的URL同时匹配成功，才会调用对应的处理函数</font>

### 2、路由的使用

#### 1. 直接挂载

在 Express 中使用路由最简单的方式，就是把路由挂载到 app 上，示例代码如下：

![1650087252673](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650087252673.png)

#### 2. 模块化路由

为了方便对路由进行模块化的管理，Express 不建议将路由直接挂载到 app 上，而是推荐将路由抽离为单独的模块。

将路由抽离为单独模块的步骤如下：

1. 创建路由模块对应的 .js 文件
2. 调用 express.Router() 函数创建路由对象
3. 向路由对象上挂载具体的路由
4. 使用 module.exports 向外共享路由对象
5. 使用 app.use() 函数注册路由模块

##### 3. 创建路由模块

![1650087334662](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650087334662.png)

##### 4. 注册路由模块

![1650087357890](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650087357890.png)

##### 5. 为路由模块添加前缀

类似于托管静态资源时，为静态资源统一挂载访问前缀一样，路由模块添加前缀的方式也非常简单：

![1650087406092](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650087406092.png)

router.js

![1650805792432](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650805792432.png)

![1650805759796](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650805759796.png)

## 三、Express中间件

### 1、中间件的概念

#### 1. 中间件

<font color='red'>中间件（Middleware ），特指业务流程的中间处理环节。</font>

现实生活中的例子：

在处理污水的时候，一般都要经过三个处理环节，从而保证处理过后的废水，达到排放标准。

![1650087509064](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650087509064.png)

处理污水的这三个中间处理环节，就可以叫做中间件。

#### 2. Express 中间件的调用流程

<font color='red'>当一个请求到达 Express 的服务器之后，可以连续调用多个中间件，从而对这次请求进行预处理。</font>

![1650087564479](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650087564479.png)

#### 3. Express 中间件的格式

<font color='blue'>**Express 的中间件，本质上就是一个 function 处理函数**</font>，Express 中间件的格式如下：

![1650087603305](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650087603305.png)

注意：<font color='red'>中间件函数的形参列表中，必须包含 next 参数。而路由处理函数中只包含 req 和 res。</font>

#### 4. next 函数的作用

<font color='red'>**next 函数是实现多个中间件连续调用的关键，它表示把流转关系转交给下一个中间件或路由。**</font>

![1650087660926](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650087660926.png)

### 2、中间件初体验

#### 1. 定义中间件函数

可以通过如下的方式，定义一个最简单的中间件函数：

![1650087704978](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650087704978.png)

![1650805873949](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650805873949.png)

#### 2. 全局生效的中间件

<font color='red'>客户端发起的任何请求</font>，<font color='blue'>到达服务器之后，都会触发的中间件，叫做全局生效的中间件。</font>

通过<font color='red'>调用 app.use(中间件函数)，即可定义一个全局生效的中间件</font>，示例代码如下：![1650087752387](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650087752387.png)

#### 3. 定义全局中间件的简化形式

![1650087765132](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650087765132.png)

#### 4. 中间件的作用

<font color='green'>**多个中间件之间，共享同一份 req 和 res。**</font>基于这样的特性，我们<font color='orange'>可以在上游的中间件中，统一为 req 或 res 对象添加自定义的属性或方法，供下游的中间件或路由进行使用。</font>

![1650087811965](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650087811965.png)

![1650805984963](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650805984963.png)

#### 5. 定义多个全局中间件

<font color='red'>可以使用 app.use() 连续定义多个全局中间件</font>。**客户端请求到达服务器之后，会按照中间件定义的先后顺序依次进行调用**，示例代码如下：

![1650087845837](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650087845837.png)

![1650806043875](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650806043875.png)

#### 6. 局部生效的中间件

<font color='red'>不使用 app.use() 定义的中间件，叫做局部生效的中间件</font>，示例代码如下：

![1650087887526](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650087887526.png)

![1650806399251](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650806399251.png)

#### 7. 定义多个局部中间件

可以在路由中，通过如下<font color='red'>两种等价的方式，使用多个局部中间件</font>：

![1650087926359](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650087926359.png)

![1650806434418](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650806434418.png)

### 中间件的五个使用注意事项

1. 一定要在路由之前注册中间件
2. 客户端发送过来的请求，可以连续调用多个中间件进行处理
3. **执行完中间件的业务代码之后，不要忘记调用 next() 函数**
4. 为了防止代码逻辑混乱，调用 next() 函数后不要再写额外的代码
5. <font color='red'>连续调用多个中间件时，多个中间件之间，共享 req 和 res 对象</font>

## 3、中间件的分类

为了方便大家理解和记忆中间件的使用，Express 官方把常见的中间件用法，分成了 5 大类，分别是：

1. <font color='red'>应用级别</font>的中间件
2. <font color='red'>路由级别</font>的中间件
3. <font color='red'>错误级别</font>的中间件
4. <font color='red'>Express 内置</font>的中间件
5. <font color='red'>第三方的</font>中间件

#### 1. 应用级别的中间件

<font color='red'>通过 app.use() 或 app.get() 或 app.post() ，绑定到 app 实例上的中间件，叫做应用级别的中间件</font>，代码示例如下：

![1650088836967](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650088836967.png)

#### 2. 路由级别的中间件

<font color='red'>绑定到 express.Router() 实例上的中间件，叫做路由级别的中间件。</font>它的用法和应用级别中间件没有任何区别。只不过，应用级别中间件是绑定到 app 实例上，路由级别中间件绑定到 router 实例上，代码示例如下：

![1650088896730](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650088896730.png)

#### 3. 错误级别的中间件

<font color='blue'>错误级别中间件的作用：专门用来捕获整个项目中发生的异常错误，从而防止项目异常崩溃的问题。</font>

格式：<font color='red'>错误级别中间件的 function 处理函数中，必须有 4 个形参，形参顺序从前到后，分别是 (err, req, res, next)。</font>

![1650088978527](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650088978527.png)

<font color='red'>**注意：错误级别的中间件，必须注册在所有路由之后！**</font>

![1650806529333](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650806529333.png)

#### 4. Express内置的中间件

自 Express 4.16.0 版本开始，Express 内置了 3 个常用的中间件，极大的提高了 Express 项目的开发效率和体验：

1. <font color='red'>express.static 快速托管静态资源的内置中间件，</font>例如： HTML 文件、图片、CSS 样式等（无兼容性）
2. <font color='blue'>express.json 解析 JSON 格式的请求体数据</font>（有兼容性，仅在 4.16.0+ 版本中可用）
3. <font color='red'>express.urlencoded 解析 URL-encoded 格式的请求体数据</font>（有兼容性，仅在 4.16.0+ 版本中可用）

![1650089077719](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650089077719.png)

![1650806576458](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650806576458.png)

###### body-parser中间件

![1650806661457](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650806661457.png)

#### 5. 第三方的中间件

非 Express 官方内置的，而是由第三方开发出来的中间件，叫做第三方中间件。在项目中，大家可以按需下载并配置第三方中间件，从而提高项目的开发效率。

例如：在 express@4.16.0 之前的版本中，经常使用<font color='red'> body-parser 这个第三方中间件，来解析请求体数据</font>。使用

步骤如下：

1. 运行 npm install body-parser 安装中间件
2. 使用 require 导入中间件
3. 调用 app.use() 注册并使用中间件

注意：**Express 内置的 express.urlencoded 中间件，就是基于 body-parser 这个第三方中间件进一步封装出来的。**

### 4、自定义中间件

#### 1. 需求描述与实现步骤

自己手动模拟一个类似于 express.urlencoded 这样的中间件，来解析 POST 提交到服务器的表单数据。

实现步骤：

1. 定义中间件
2. 监听 req 的 data 事件
3. 监听 req 的 end 事件
4. 使用 querystring 模块解析请求体数据
5. 将解析出来的数据对象挂载为 req.body
6. 将自定义中间件封装为模块

#### 2. 定义中间件

使用 app.use() 来定义全局生效的中间件，代码如下：

![1650089200493](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650089200493.png)

#### 3. 监听 req 的 data 事件

<font color='red'>在中间件中，需要监听 req 对象的 data 事件，来获取**客户端发送到服务器的数据**。</font>

**如果数据量比较大，无法一次性发送完毕，则客户端会把数据切割后，分批发送到服务器。所以 data 事件可能会触发多次，每一次触发 data 事件时，<font color='blue'>获取到数据只是完整数据的一部分，需要手动对接收到的数据进行拼接。</font>**

![1650089266427](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650089266427.png)

#### 4. 监听 req 的 end 事件

<font color='red'>当请求体数据接收完毕之后，会自动触发 req 的 end 事件。</font>

因此，我们可以在 req 的 end 事件中，**拿到并处理完整的请求体数据**。示例代码如下：

![1650089312131](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650089312131.png)

#### 5. 使用 querystring 模块解析请求体数据

Node.js <font color='red'>内置了一个 querystring 模块，专门用来处理查询字符串。</font>通过这个模块<font color='green'>**提供的 parse() 函数，可以轻松把查询字符串，解析成对象的格式。**</font>示例代码如下：

![1650089369399](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650089369399.png)

#### 6. 将解析出来的数据对象挂载为 req.body

<font color='red'>上游</font>的<font color='red'>中间件</font>和下<font color='blue'>游的中间件</font>及<font color='green'>路由之间</font>，<font color='red'>**共享同一份 req 和 res**</font>。因此，我们<font color='red'>可以将解析出来的数据，挂载为 req 的自定义属性，命名为 req.body，供下游使用。</font>示例代码如下：

## ![1650089426610](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650089426610.png)

#### 7. 将自定义中间件封装为模块

为了优化代码的结构，我们可以把自定义的中间件函数，封装为独立的模块，示例代码如下：

![1650089452198](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650089452198.png)

完整代码：

![1650806753176](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650806753176.png)

![1650806827553](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650806827553.png)

## 四、使用Express写接口

### 1、创建基本的服务器

![1650089724082](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650089724082.png)

### 2、创建 API 路由模块

![1650089752791](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650089752791.png)

### 3、编写 GET 接口

![1650089769220](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650089769220.png)

### 4、编写 POST 接口

![1650089793099](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650089793099.png)

完整代码：

![1650806904018](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650806904018.png)

### 5、CORS 跨域资源共享

#### 1. 接口的跨域问题

刚才编写的 GET 和 POST接口，存在一个很严重的问题：不支持跨域请求。

<font color='red'>解决接口跨域问题的方案主要有两种：</font>

1. CORS（主流的解决方案，推荐使用）

2. JSONP（有缺陷的解决方案：只支持 GET 请求）

#### 2. 使用 cors 中间件解决跨域问题

cors 是 Express 的一个第三方中间件。通过安装和配置 cors 中间件，可以很方便地解决跨域问题。

使用步骤分为如下 3 步：

1. <font color='red'>运行 npm install cors 安装中间件</font>
2. <font color='blue'>使用 const cors = require('cors') 导入中间件</font>
3. <font color='green'>在路由之前调用 app.use(cors()) 配置中间件</font>

#### 3. 什么是 CORS

<font color='red'>**CORS （Cross-Origin Resource Sharing，跨域资源共享）由一系列 HTTP 响应头组成，这些 HTTP 响应头决定浏览器是否阻止前端 JS 代码跨域获取资源。**</font>

<font color='blue'>**浏览器的同源安全策略默认会阻止网页“跨域”获取资源。但如果接口服务器配置了 CORS 相关的 HTTP 响应头，就可以解除浏览器端的跨域访问限制。**</font>

![1650089953972](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650089953972.png)

#### 4. CORS 的注意事项

1. <font color='red'>CORS 主要在服务器端进行配置。客户端浏览器无须做任何额外的配置，即可请求开启了 CORS 的接口。</font>
2. CORS 在浏览器中有兼容性。只有支持 XMLHttpRequest Level2 的浏览器，才能正常访问开启了 CORS 的服务端接口（例如：IE10+、Chrome4+、FireFox3.5+）。

#### 5. CORS 响应头部 - Access-Control-Allow-Origin 

<font color='red'>响应头部中可以携带一个 Access-Control-Allow-Origin 字段</font>，其语法如下:

![1650090028547](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650090028547.png)

其中，<font color='red'>origin 参数的值指定了允许访问该资源的外域 URL。</font>

例如，下面的字段值将只允许来自 http://itcast.cn 的请求：

![1650090055698](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650090055698.png)

<font color='green'>**如果指定了 Access-Control-Allow-Origin 字段的值为通配符 *，表示允许来自任何域的请求，示例代码如下：**</font>

![1650090080675](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650090080675.png)

#### 6. CORS 响应头部 - Access-Control-Allow-Headers

<font color='blue'>默认情况下，CORS 仅支持客户端向服务器发送如下的 9 个请求头：</font>

- Accept、Accept-Language、Content-Language、DPR、Downlink、Save-Data、Viewport-Width、Width 、**Content-Type （值仅限于 text/plain、multipart/form-data、application/x-www-form-urlencoded 三者之一）**

<font color='red'>如果客户端向服务器发送了额外的请求头信息，则需要在服务器端，通过 Access-Control-Allow-Headers 对额外的请求头进行声明，否则这次请求会失败！</font>

![1650090224204](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650090224204.png)

#### 7. CORS 响应头部 - Access-Control-Allow-Methods

默认情况下，CORS 仅支持客户端发起 GET、POST、HEAD 请求。

如果客户端希望通过 <font color='red'>PUT、DELETE 等方式请求服务器的资源，则需要在服务器端，通过 Access-Control-Alow-Methods来指明实际请求所允许使用的 HTTP 方法。</font>

示例代码如下：

![1650090254310](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650090254310.png)

#### 8. CORS请求的分类

客户端在请求 CORS 接口时，<font color='red'>根据请求方式和请求头的不同</font>，可以将 CORS 的请求分为两大类，分别是：

1. **简单请求**
2. **预检请求**

##### 简单请求

同<font color='red'>时满足以下两大条件的请求，就属于简单请求</font>：

1. **请求方式：GET、POST、HEAD 三者之一**
2. **HTTP 头部信息不超过以下几种字段**：无自定义头部字段、Accept、Accept-Language、Content-Language、DPR、Downlink、Save-Data、Viewport-Width、Width 、Content-Type（只有三个值application/x-www-form-urlencoded、multipart/form-data、text/plain）

##### 预检请求

<font color='blue'>只要符合以下任何一个条件的请求，都需要进行预检请求：</font>

1. **请求方式为 GET、POST、HEAD 之外的请求 Method 类型**
2. **请求头中包含自定义头部字段**
3. **向服务器发送了 application/json 格式的数据**

在浏览器与服务器正式通信之前，浏览器会先发送 <font color='red'>OPTION 请求进行预检，以获知服务器是否允许该实际请求，</font>所以这一次的 <font color='blue'>OPTION 请求称为“预检请求”</font>。服务器成功响应预检请求后，才会发送真正的请求，并且携带真实数据。

##### 简单请求和预检请求的区别

<font color='red'>**简单请求的特点：**</font><font color='blue'>客户端与服务器之间只会发生一次请求。</font>

<font color='red'>**预检请求的特点：**</font><font color='blue'>客户端与服务器之间会发生两次请求，OPTION 预检请求成功之后，才会发起真正的请求。</font>

### 6、jsonp接口

#### 1. 回顾 JSONP 的概念与特点

概念：**浏览器端通过 <script> 标签的 src 属性，请求服务器上的数据，同时，服务器返回一个函数的调用。这种请求数据的方式叫做 JSONP。**

特点：

1. JSONP 不属于真正的 Ajax 请求，因为它没有使用 XMLHttpRequest 这个对象。
2. **JSONP 仅支持 GET 请求，不支持 POST、PUT、DELETE 等请求。**

#### 2. 创建 JSONP 接口的注意事项

<font color='red'>如果项目中已经配置了 CORS 跨域资源共享，为了防止冲突，必须在配置 CORS 中间件之前声明 JSONP 的接口。否则 JSONP 接口会被处理成开启了 CORS 的接口。</font>示例代码如下：

![1650090897308](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650090897308.png)

#### 3. 实现 JSONP 接口的步骤

1. 获取客户端发送过来的回调函数的名字
2. 得到要通过 JSONP 形式发送给客户端的数据
3. 根据前两步得到的数据，拼接出一个函数调用的字符串
4. 把上一步拼接得到的字符串，响应给客户端的 <script> 标签进行解析执行

#### 4. 实现 JSONP 接口的具体代码

![1650090958486](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650090958486.png)

#### 5. 在网页中使用 jQuery 发起 JSONP 请求

<font color='red'>调用 $.ajax() 函数，提供 JSONP 的配置选项，从而发起 JSONP 请求，</font>示例代码如下：

![1650091020579](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650091020579.png)

# 数据库与身份认证

## 一、数据库的基本概念

### 1、简介

<font color='red'>数据库（database）是用来组织、存储和管理数据的仓库。</font>

当今世界是一个充满着数据的互联网世界，充斥着大量的数据。数据的来源有很多，比如出行记录、消费记录、浏览的网页、发送的消息等等。除了文本类型的数据，图像、音乐、声音都是数据。

为了方便管理互联网世界中的数据，就有了数据库管理系统的概念（简称：数据库）。用户可以对数据库中的数据进行新增、查询、更新、删除等操作。

### 2、分类

市面上的数据库有很多种，最常见的数据库有如下几个：

- MySQL 数据库（目前使用最广泛、流行度最高的开源免费数据库；Community + Enterprise）

- Oracle 数据库（收费）

- SQL Server 数据库（收费）

- Mongodb 数据库（Community + Enterprise）

其中，MySQL、Oracle、SQL Server 属于**传统型数据库**（又叫做：关系型数据库 或 SQL 数据库），这三者的设计理念相同，用法比较类似。

而 Mongodb 属于**新型数据库**（又叫做：非关系型数据库 或 NoSQL 数据库），它在一定程度上弥补了传统型数据库的缺陷。

### 3、传统型数据库的数据组织结构

在传统型数据库中，数据的组织结构分为<font color='red'>数据库(database)、数据表(table)、数据行(row)、字段(field)这 4 大部分组成。</font>

![1650091299572](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650091299572.png)

> 1. 数据库类似于 Excel 的工作簿
>
> 2. 数据表类似于 Excel 的工作表
> 3. 数据行类似于 Excel 的每一行数据
>
> 4. 字段类似于 Excel 的列
>
> 5. 每个字段都有对应的数据类型

在实际项目开发中，一般情况下，每个项目都对应独立的数据库。

- 不同的数据，要存储到数据库的不同表中，例如：用户数据存储到 users 表中，图书数据存储到 books 表中。
- 每个表中具体存储哪些信息，由字段来决定，例如：我们可以为 users 表设计 id、username、password 这 3 个字段。
- 表中的行，代表每一条具体的数据。

## 二、安装配置MySQL

对于开发人员来说，只需要安装 MySQL Server 和 MySQL Workbench 这两个软件，就能满足开发的需要了。

1. <font color='red'>MySQL Server：专门用来提供数据存储和服务的软件。</font>
2. MySQL Workbench：可视化的 MySQL 管理工具，通过它，可以方便的操作存储在 MySQL Server 中的数据。

**MySQL 在 Windows 环境下的安装**

在 Windows 环境下安装 MySQL，只需要运行 mysql-installer-community-8.0.19.0.msi 这个安装包，就能一次性将 MySQL Server  和 MySQL Workbench 安装到自己的电脑上。

具体的安装教程，可以参考 素材 -> MySQL for Windows ->安装教程 - Windows系统安装MySql -> README.md 

## 三、MySQL的基本使用

### 1、SQL

<font color='red'>SQL（英文全称：Structured Query Language）是结构化查询语言，专门用来访问和处理数据库的编程语言。能够让我们以编程的形式，操作数据库里面的数据。</font>

三个关键点：

1. **SQL 是一门数据库编程语言**
2. **使用 SQL 语言编写出来的代码，叫做 SQL 语句**
3. SQL 语言只能在关系型数据库中使用（例如 MySQL、Oracle、SQL Server）。非关系型数据库（例如 Mongodb）不支持 SQL 语言

##### SQL作用

> - 从数据库中查询数据
>
> - 向数据库中插入新的数据
> - 更新数据库中的数据
>
> - 从数据库删除数据
>
> - 可以创建新数据库
>
> - 可在数据库中创建新表
>
> - 可在数据库中创建存储过程、视图
>
> - etc…

<font color='red'>查询数据（select） 、插入数据（insert into） 、更新数据（update） 、删除数据（delete） </font>

额外需要掌握的 4 种 SQL 语法：

<font color='red'>where 条件、and 和 or 运算符、order by 排序、count(*) 函数</font>

### 2、SQL 的 SELECT 语句

SELECT 语句用于<font color='red'>从表中查询数据</font>。执行的结果被存储在一个结果表中（称为结果集）。语法格式如下：

![1650091543444](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650091543444.png)

注意：SQL 语句中的关键字对大小写不敏感。SELECT 等效于 select，FROM 等效于 from。

#### SELECT *示例

我们希望从 <font color='red'>users 表中选取所有的列，可以使用符号 * 取代列的名称</font>，示例如下：

![1650091558617](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650091558617.png)

#### SELECT 列名称 示例

如需获取名为 "username" 和 "password" 的列的内容（从名为 "users" 的数据库表），请使用下面的 SELECT 语句：

![1650091601237](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650091601237.png)

### 3、SQL 的 INSERT INTO 语句

<font color='red'>INSERT INTO 语句用于向数据表中插入新的数据行，语法格式如下：</font>

![1650091625356](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650091625356.png)

####  INSERT INTO 示例

向 users 表中，插入一条 username 为 tony stark，password 为 098123 的用户数据，示例如下：

![1650091640934](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650091640934.png)

### 4、SQL 的 UPDATE 语句

<font color='red'>Update 语句用于修改表中的数据。语法格式如下：</font>

![1650091667010](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650091667010.png)

#### UPDATE 示例 - 更新某一行中的一个列

把 users 表中 id 为 7 的用户密码，更新为 888888。示例如下：

![1650091687740](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650091687740.png)

#### UPDATE 示例 - 更新某一行中的若干列

把 users 表中 id 为 2 的用户密码和用户状态，分别更新为 admin123 和 1。示例如下：

![1650091711366](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650091711366.png)

### 5、SQL 的 DELETE 语句

<font color='red'>DELETE 语句用于删除表中的行。语法格式如下：</font>

![1650091757279](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650091757279.png)

#### DELETE 示例

从 users 表中，删除 id 为 4 的用户，示例如下：

![1650091772472](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650091772472.png)

### 6、SQL 的 WHERE 子句

<font color='red'>WHERE 子句用于限定选择的标准。在 SELECT、UPDATE、DELETE 语句中，皆可使用 WHERE 子句来限定选择的标准。</font>

![1650091794648](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650091794648.png)

#### 可在 WHERE 子句中使用的运算符

![1650091824034](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650091824034.png)

#### WHERE 子句示例

可以通过 WHERE 子句来限定 SELECT 的查询条件：

![1650091839113](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650091839113.png)

### 7、SQL 的 AND 和 OR 运算符

1. A**ND 和 OR 可在 WHERE 子语句中把两个或多个条件结合起来。**
2. <font color='red'>AND 表示必须同时满足多个条件，</font>相当于 JavaScript 中的 && 运算符，例如 if (a !== 10 && a !== 20) 
3. <font color='red'>OR 表示只要满足任意一个条件即可</font>，相当于 JavaScript 中的 || 运算符，例如 if(a !== 10 || a !== 20)

### 8、SQL 的 ORDER BY 子句

<font color='blue'>ORDER BY 语句用于根据指定的列对结果集进行排序。</font>

**ORDER BY 语句默认按照升序对记录进行排序。**

<font color='blue'>如果您希望按照降序对记录进行排序，可以使用 DESC 关键字。</font>

### 9、SQL 的 COUNT(*) 函数

<font color='red'>COUNT(*) 函数用于返回查询结果的总数据条数，语法格式如下：</font>

![1650091926977](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650091926977.png)

#### 使用 AS 为列设置别名

<font color='red'>如果希望给查询出来的列名称设置别名，可以使用 AS 关键字</font>，示例如下：

![1650091946434](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650091946434.png)

## 四、在项目中操作 MySQL

1. 安装操作 MySQL 数据库的第三方模块（mysql）
2. 通过 mysql 模块连接到 MySQL 数据库
3. 通过 mysql 模块执行 SQL 语句

![1650092029662](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650092029662.png)

#### 1. 安装 mysql 模块

mysql 模块是托管于 npm 上的第三方模块。它提供了在 Node.js 项目中连接和操作 MySQL 数据库的能力。
想要在项目中使用它，需要先运行如下命令，将 mysql 安装为项目的依赖包：

![1650092058803](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650092058803.png)

#### 2. 配置 mysql 模块

在使用 mysql 模块操作 MySQL 数据库之前，<font color='red'>必须先对 mysql 模块进行必要的配置</font>，主要的配置步骤如下：

![1650092126635](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650092126635.png)

#### 3. 测试 mysql 模块能否正常工作

<font color='red'>调用 db.query() 函数，指定要执行的 SQL 语句，通过回调函数拿到执行的结果：</font>

![1650092156119](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650092156119.png)

### 使用 mysql 模块操作 MySQL 数据库

#### 1. 查询数据

查询 users 表中所有的数据：

![1650092200042](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650092200042.png)

#### 2. 插入数据

向 users 表中新增数据， 其中 username 为 Spider-Man，password 为 pcc321。示例代码如下：

![1650092227343](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650092227343.png)

#### 3. 插入数据的便捷方式

向表中新增数据时，<font color='red'>如果数据对象的每个属性和数据表的字段一一对应，则可以通过如下方式快速插入数据</font>：

![1650092287317](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650092287317.png)

#### 4. 更新数据

可以通过如下方式，更新表中的数据：

![1650092332430](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650092332430.png)

#### 5. 更新数据的便捷方式

更新表数据时，<font color='red'>如果数据对象的每个属性和数据表的字段一一对应，则可以通过如下方式快速更新表数据</font>：

![1650092367944](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650092367944.png)

#### 6. 删除数据

在删除数据时，推荐根据 id 这样的唯一标识，来删除对应的数据。示例如下：

![1650092393834](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650092393834.png)

#### 7. 标记删除

使用 DELETE 语句，会把真正的把数据从表中删除掉。为了保险起见，推荐使用标记删除的形式，来模拟删除的动作。

<font color='red'>所谓的标记删除，就是在表中设置类似于 status 这样的状态字段，来标记当前这条数据是否被删除。</font>

当用户执行了删除的动作时，我们并没有执行 DELETE 语句把数据删除掉，而是执行了 UPDATE 语句，将这条数据对应的 status 字段标记为删除即可。

![1650092458049](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650092458049.png)

## 五、前后端的身份认证

### 1、web开发模式

目前主流的 Web 开发模式有两种，分别是：

1. <font color='red'>基于服务端渲染的传统 Web 开发模式</font>
2. <font color='blue'>基于前后端分离的新型 Web 开发模式</font>

#### 1. 服务端渲染的 Web 开发模式

<font color='red'>服务端渲染的概念：服务器发送给客户端的 HTML 页面，是在服务器通过字符串的拼接，动态生成的。</font>因此，客户端不需要使用 Ajax 这样的技术额外请求页面的数据。代码示例如下：

![1650092568592](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650092568592.png)

#### 2. 服务端渲染的优缺点

优点：

1. <font color='red'>前端耗时少</font>。因为服务器端负责动态生成 HTML 内容，浏览器只需要直接渲染页面即可。尤其是移动端，更省电。
2. <font color='red'>有利于SEO</font>。因为服务器端响应的是完整的 HTML 页面内容，所以爬虫更容易爬取获得信息，更有利于 SEO。

缺点：

1. <font color='red'>占用服务器端资源</font>。即服务器端完成 HTML 页面内容的拼接，如果请求较多，会对服务器造成一定的访问压力。
2. <font color='red'>不利于前后端分离</font>，开发效率低。使用服务器端渲染，则无法进行分工合作，尤其对于前端复杂度高的项目，不利于项目高效开发。

#### 3. 前后端分离的 Web 开发模式

前后端分离的概念：<font color='red'>前后端分离的开发模式，依赖于 Ajax 技术的广泛应用。</font>简而言之，前后端分离的 Web 开发模式，就<font color='red'>是后端只负责提供 API 接口，前端使用 Ajax 调用接口的开发模式。</font>

### 4. 前后端分离的优缺点

优点：

1. 开发体验好。前端专注于 UI 页面的开发，后端专注于api 的开发，且前端有更多的选择性。

2. 用户体验好。Ajax 技术的广泛应用，极大的提高了用户的体验，可以轻松实现页面的局部刷新。

3. 减轻了服务器端的渲染压力。因为页面最终是在每个用户的浏览器中生成的。

缺点：

1. <font color='red'>不利于 SEO。</font>因为完整的 HTML 页面需要在客户端动态拼接完成，所以爬虫对无法爬取页面的有效信息。（<font color='red'>解决方案：利用 Vue、React 等前端框架的 SSR （server side render）技术能够很好的解决 SEO 问题！</font>）

### 2、身份认证

#### 1. 简介

<font color='red'>身份认证（Authentication）又称“身份验证”、“鉴权”，是指通过一定的手段，完成对用户身份的确认。</font>

- 日常生活中的身份认证随处可见，例如：高铁的验票乘车，手机的密码或指纹解锁，支付宝或微信的支付密码等。
- 在 Web 开发中，也涉及到用户身份的认证，例如：各大网站的手机验证码登录、邮箱密码登录、二维码登录等。

#### 2. 不同开发模式下的身份认证

<font color='red'>对于服务端渲染和前后端分离这两种开发模式来说</font>，分别有着不同的身份认证方案：

1. <font color='red'>服务端渲染推荐使用 Session 认证机制</font>
2. <font color='blue'>前后端分离推荐使用 JWT 认证机制</font>

### 3、Session 认证机制

#### 1. HTTP 协议的无状态性

了解 HTTP 协议的无状态性是进一步学习 Session 认证机制的必要前提。

<font color='red'>HTTP 协议的无状态性，指的是客户端的每次 HTTP 请求都是独立的，连续多个请求之间没有直接的关系，服务器不会主动保留每次 HTTP 请求的状态。</font>

![1650093019132](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650093019132.png)

#### 2. 如何突破 HTTP 无状态的限制

Cookie

#### 3. Cookie

<font color='red'>Cookie 是存储在用户浏览器中的一段不超过 4 KB 的字符串。</font>它由一个名称（Name）、一个值（Value）和其它几个用于控制 Cookie 有效期、安全性、使用范围的可选属性组成。

**不同域名下的 Cookie 各自独立，每当客户端发起请求时，会自动把当前域名下所有未过期的 Cookie 一同发送到服务器。**

Cookie的几大特性：

1. 自动发送
2. 域名独立
3. 过期时限
4. 4KB 限制

#### 4. Cookie 在身份认证中的作用

<font color='red'>客户端第一次请求服务器的时候，服务器通过响应头的形式，向客户端发送一个身份认证的 Cookie，客户端会自动将 Cookie 保存在浏览器中。</font>

**随后，当客户端浏览器每次请求服务器的时候，浏览器会自动将身份认证相关的 Cookie，通过请求头的形式发送给服务器，服务器即可验明客户端的身份。**

![1650093150144](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650093150144.png)

#### 5. Cookie 不具有安全性

由于 <font color='red'>Cookie 是存储在浏览器中的，而且浏览器也提供了读写 Cookie 的 API</font>，因此 Cookie 很容易被伪造，不具有安全性。因此不建议服务器将重要的隐私数据，通过 Cookie 的形式发送给浏览器。

![1650093177697](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650093177697.png)

<font color='red'>注意：千万不要使用 Cookie 存储重要且隐私的数据！</font>比如用户的身份信息、密码等。

#### 6. 提高身份认证的安全性

这种“会员卡 + 刷卡认证”的设计理念，就是 Session 认证机制的精髓。

#### 7. Session 的工作原理！！

![1650093237780](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650093237780.png)

### 4、在 Express 中使用 Session 认证

#### 1. 安装 express-session 中间件

在 Express 项目中，只<font color='red'>需要安装 express-session 中间件，即可在项目中使用 Session 认证</font>：

![1650093279538](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650093279538.png)

#### 2. 配置 express-session 中间件

<font color='red'>express-session 中间件安装成功后，需要通过 app.use() 来注册 session 中间件，</font>示例代码如下：

![1650093310577](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650093310577.png)

#### 3. 向 session 中存数据

当 express-session 中间件配置成功后，即<font color='blue'>**可通过 req.session 来访问和使用 session 对象，从而存储用户的关键信息：**</font>

![1650093378519](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650093378519.png)

#### 4. 从 session 中取数据

<font color='blue'>可以直接从 req.session 对象上获取之前存储的数据</font>，示例代码如下：

![1650093425331](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650093425331.png)

#### 5. 清空 session

<font color='red'>调用 req.session.destroy() 函数，即可清空服务器保存的 session 信息</font>。

![1650093454892](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650093454892.png)

### 5、JWT 认证机制

#### 1. 了解 Session 认证的局限性

<font color='blue'>**Session 认证机制需要配合 Cookie 才能实现。由于 Cookie 默认不支持跨域访问，所以，当涉及到前端跨域请求后端接口的时候，需要做很多额外的配置，才能实现跨域 Session 认证。**</font>

注意：

1. 当前端请求后端接口<font color='red'>不存在跨域问题</font>的时候，<font color='red'>推荐使用 Session 身份认证机制。</font>
2. 当前端<font color='blue'>需要跨域请求后端接口的时候</font>，<font color='blue'>不推荐使用 Session 身份认证机制，推荐使用 JWT 认证机制。</font>

#### 2. JWT简介

JWT（英文全称：JSON Web Token）是目前最流行的**跨域认证解决方案。**

#### 3. JWT 的工作原理

![1650093634420](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650093634420.png)

总结：<font color='green'>**用户的信息通过 Token 字符串的形式，保存在客户端浏览器中。** **服务器通过还原 Token 字符串的形式来认证用户的身份。**</font>

#### 4. JWT 的组成部分

<font color='red'>JWT 通常由三部分组成，分别是 Header（头部）、Payload（有效荷载）、Signature（签名）。</font>

三者之间使用英文的“.”分隔，格式如下：

![1650093708929](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650093708929.png)

#### 5. JWT 的三个部分各自代表的含义

**JWT 的三个组成部分，从前到后分别是 Header、Payload、Signature。**

其中：

- <font color='red'>Payload 部分才是真正的用户信息，它是用户信息经过加密之后生成的字符串。</font>
- **Header 和 Signature 是安全性相关的部分，只是为了保证 Token 的安全性。**

![1650093785179](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650093785179.png)

#### 6. JWT 的使用方式

<font color='red'>客户端收到服务器返回的 JWT 之后，通常会将它储存在 localStorage 或 sessionStorage 中。</font>

**此后，客户端每次与服务器通信，都要带上这个 JWT 的字符串，从而进行身份认证。**推荐的做法是把 JWT 放在<font color='red'> HTTP 请求头的 Authorization 字段</font>中，格式如下：

![1650093834200](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650093834200.png)

### 6、在 Express 中使用 JWT

#### 1. 安装 JWT 相关的包

运行如下命令，安装如下两个 JWT 相关的包：

![1650093859474](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650093859474.png)

其中：

- <font color='red'>jsonwebtoken 用于生成 JWT 字符串</font>
- <font color='blue'>express-jwt 用于将 JWT 字符串解析还原成 JSON 对象</font>

#### 2. 导入 JWT 相关的包

使用 require() 函数，分别导入 JWT 相关的两个包：

![1650093901887](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650093901887.png)

#### 3. 定义 secret 密钥！！

<font color='red'>为了保证 JWT 字符串的安全性，防止 JWT 字符串在网络传输过程中被别人破解</font>，我们需要<font color='blue'>专门定义一个用于加密和解密的 secret 密钥</font>：

- 当生成 JWT 字符串的时候，需要使用 secret 密钥对用户的信息进行加密，最终得到加密好的 JWT 字符串
- 当把 JWT 字符串解析还原成 JSON 对象的时候，需要使用 secret 密钥进行解密

![1650093997245](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650093997245.png)

#### 4. 在登录成功后生成 JWT 字符串

<font color='blue'>**调用 jsonwebtoken 包提供的 sign() 方法，将用户的信息加密成 JWT 字符串，响应给客户端：**</font>

![1650094086571](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650094086571.png)

#### 5. 将 JWT 字符串还原为 JSON 对象

**客户端每次在访问那些有权限接口的时候，都需要主动通过请求头中的 Authorization 字段，将 Token 字符串发送到服务器进行身份认证。**

此时，<font color='blue'>服务器可以通过 express-jwt 这个中间件，自动将客户端发送过来的 Token 解析还原成 JSON 对象</font>：

![1650094131745](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650094131745.png)

#### 6. 使用 req.user 获取用户信息

<font color='red'>当 express-jwt 这个中间件配置成功之后，即可在那些有权限的接口中，使用 req.user 对象，来访问从 JWT 字符串中解析出来的用户信息了</font>，示例代码如下：

![1650094191096](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650094191096.png)

#### 7. 捕获解析 JWT 失败后产生的错误

当使用 express-jwt 解析 Token 字符串时，**如果客户端发送过来的 Token 字符串过期或不合法，会产生一个解析失败的错误，影响项目的正常运行。**<font color='blue'>我们可以通过 Express 的错误中间件，捕获这个错误并进行相关的处理</font>，示例代码如下：

![1650094253999](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650094253999.png)

