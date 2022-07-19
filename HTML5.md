# HTML5概念

HTML5 将成为 HTML、XHTML 以及 HTML DOM 的新标准；

HTML5 仍处于完善之中。然而，大部分现代浏览器已经具备了某些 HTML5 支持。

（1）<font color='red'>HTML5 是 W3C（World Wide Web Consortium，万维网联盟） 与 WHATWG 合作的结果</font>

（2）为 HTML5 建立的一些规则：

> - <font color='red'>新特性应该基于 HTML、CSS、DOM 以及 JavaScript</font>
> - **减少对外部插件的需求（比如 Flash）**
> - 更优秀的错误处理
>
> - 更多取代脚本的标记
>
> - <font color='blue'>HTML5 应该独立于设备</font>
> - 开发进程应对公众透明

### 新特性

（1）用于绘画的 canvas 元素

（2）<font color='red'>用于媒介回放的 video 和 audio 元素</font>

（3）对本地离线存储的更好的支持

（4）新的特殊内容元素，比如 article、footer、header、nav、section

（5）新的表单控件，比如 calendar、date、time、email、url、search

# HTML5视频：

### web上的视频：

（1）**大多数视频是通过插件（比如 Flash）来显示的，**然而，并非所有浏览器都拥有同样的插件

（2）<font color='red'>HTML5 规定了一种通过 video 元素来包含视频的标准方法</font>

### 视频格式：

（1）Ogg格式：

> 带有 Theora 视频编码和 Vorbis 音频编码的 Ogg 文件
>

（2）MPEG4格式：

> 带有 H.264 视频编码和 AAC 音频编码的 MPEG 4 文件
>

（3）WebM格式：

> 带有 VP8 视频编码和 Vorbis 音频编码的 WebM 文件

### 语法

![1650280827238](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650280827238.png)

1. <font color='red'>controls 属性供添加播放、暂停和音量控件</font>，可加入宽度和高度， 与 之间插入的内容是供不支持 video 元素的浏览器显示的
2. video 元素允许多个 source 元素。source 元素可以链接不同的视频文件。浏览器将使用第一个可识别的格式

![1650280881355](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650280881355.png)

| 属性     | 值       | 概述                                                         |
| -------- | -------- | ------------------------------------------------------------ |
| autoplay | autoplay | 如果出现该属性，则视频在加载就绪后，会自动播放               |
| controls | controls | 如果出现该属性，则向用户显示控件（例：播放按钮）             |
| height   | pixels   | 设置视频播放器的高度                                         |
| loop     | loop     | 循环播放                                                     |
| preload  | preload  | 视频在页面加载时进行加载，并预备播放。如使用了autoplay，则忽略该属性 |
| src      | url      | 待播放视频的URL                                              |
| width    | pixels   | 设置视频播放器的宽度                                         |

# HTML 5 Video + DOM

### 使用 DOM 进行控制

（1）HTML5 元素同样拥有方法、属性和事件；

（2）方法用于播放、暂停以及加载等。其中的属性（比如时长、音量等）可以被读取或设置。其中的 DOM 事件能够通知您，比方说， 元素开始播放、已暂停，已停止，等等

### 方法、属性以及事件

| 方法        | 属性        | 事件           |
| ----------- | ----------- | -------------- |
| play()      | currentSrc  | play           |
| pause()     | currentTime | pause          |
| load()      | videoWidth  | progress       |
| canPlayType | videoHeight | error          |
|             | duration    | timeupdate     |
|             | ended       | ended          |
|             | error       | abort          |
|             | paused      | empty          |
|             | muted       | emptied        |
|             | seeking     | waiting        |
|             | volumn      | loadedmetadata |
|             | height      |                |
|             | width       |                |

**在所有属性中，只有 videoWidth 和 videoHeight 属性是立即可用的。在视频的元数据已加载后，其他属性才可用** 

# HTML5 音频

## web上的音频

（1）大多数音频是通过插件（比如 Flash）来播放的。然而，并非所有浏览器都拥有同样的插件

（2）HTML5 规定了一种通过 audio 元素来包含音频的标准方法

（3）<font color='red'>audio 元素能够播放声音文件或者音频流</font>

### 语法

![1650281485722](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650281485722.png)

- <font color='red'>control 属性供添加播放、暂停和音量控件</font>， 与 之间插入的内容是供不支持 audio 元素的浏览器显示的
- audio 元素允许多个 source 元素。source 元素可以链接不同的音频文件。浏览器将使用第一个可识别的格式

![1650281521199](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650281521199.png)

### 属性

| 属性     | 值       | 描述                                                         |
| -------- | -------- | ------------------------------------------------------------ |
| autoplay | autoplay | 自动播放                                                     |
| controls | controls | 显示控件                                                     |
| loop     | loop     | 循环播放                                                     |
| preload  | preload  | 音频在页面加载时加载，并预备播放；若使用autoplay则忽略该属性 |
| src      | url      | 音频的URL                                                    |

# HTML5 拖放

## 拖放（Drag 和 drop）是 HTML5 标准的组成部分

（1）<font color='red'>拖放是一种常见的特性，即抓取对象以后拖到另一个位置</font>

（2）在 HTML5 中，拖放是标准的一部分，**任何元素都能够拖放**

## 拖动相关设置

（1）设置元素为可拖放：

> 首先，<font color='red'>为了使元素可拖动，把 draggable 属性设置为 true</font> ：

![1650281743572](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650281743572.png)

（2）规定拖动元素：

> <font color='red'>ondragstart 和 setData()</font>
>
> ondragstart 属性调用了一个函数，**drag(event)，它规定了被拖动的数据**
>
> <font color='red'>dataTransfer.setData() 方法设置被拖数据的数据类型和值：</font>

![1650281788956](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650281788956.png)

 数据类型是 “Text”，值是可拖动元素的 id (“drag1”) 

（3）放到何处 - ondragover：

> <font color='red'>ondragover 事件规定在何处放置被拖动的数据；</font>
>
> 默认地，无法将数据/元素放置到其他元素中。如果需要设置允许放置，我们必须阻止对元素的默认处理方式。
>
> 调用 ondragover 事件的 event.preventDefault() 方法：

（4）进行放置 - ondrop：

> <font color='red'>当放置被拖数据时，会发生 drop 事件；</font>
>
> ondrop 属性调用了一个函数，drop(event)：

![1650281843004](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650281843004.png)

> - 调用 preventDefault() 来避免浏览器对数据的默认处理（drop 事件的默认行为是以链接形式打开）
>
> - 通过 dataTransfer.getData(“Text”) 方法获得被拖的数据。该方法将返回在 setData() 方法中设置为相同类型的任何数据
>
> - 被拖数据是被拖元素的 id (“drag1”)
>
> - 把被拖元素追加到放置元素（目标元素）中

~~~
	<!DOCTYPE HTML>
	<html>
	<head>
	<script type="text/javascript">
	function allowDrop(ev)
	{
		ev.preventDefault();
	}

	function drag(ev)
	{
		ev.dataTransfer.setData("Text",ev.target.id);
	}

	function drop(ev)
	{
		ev.preventDefault();
		var data=ev.dataTransfer.getData("Text");
		ev.target.appendChild(document.getElementById(data));
	}
	</script>
	</head>
	<body>

	<div id="div1" ondrop="drop(event)" ondragover="allowDrop(event)"></div>
	<img id="drag1" src="img_logo.gif" draggable="true"
	ondragstart="drag(event)" width="336" height="69" />

	</body>
	</html>
~~~

# Canvas

## 什么是Canvas

（1）<font color='red'>HTML5 的 canvas 元素使用 JavaScript 在网页上绘制图像</font>

（2）画布是一个矩形区域，您可以控制其每一像素

（3）canvas 拥有多种绘制路径、矩形、圆形、字符以及添加图像的方法

## 创建canvas元素

![1650281945444](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650281945444.png)

## 通过 JavaScript 来绘制

 （1）canvas 元素本身是没有绘图能力的。所有的绘制工作必须在 JavaScript 内部完成： 

![1650281997161](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650281997161.png)

**getContext("2d") 对象是内建的 HTML5 对象，拥有多种绘制路径、矩形、圆形、字符以及添加图像的方法 **

（2）<font color='red'>使用 id 来寻找 canvas 元素，然后，创建 context 对象，然后进行绘制</font>

（3）fillRect 方法拥有参数 (0,0,150,75)：

- 在画布上绘制 150x75 的矩形，从左上角开始 (0,0)


（4）可以通过canvas绘制出点、线条、圆、渐变背景、图像

# 内联 SVG

## 什么是SVG

（1）<font color='red'>SVG 指可伸缩矢量图形 (Scalable Vector Graphics)</font>

（2）SVG 用于定义用于网络的基于矢量的图形

（3）<font color='red'>SVG 使用 XML 格式定义图形</font>

（4）SVG 图像在放大或改变尺寸的情况下其图形质量不会有损失

（5）**SVG 是万维网联盟的标准**

## SVG 的优势

（1）SVG 图像可通过文本编辑器来创建和修改

（2）SVG 图像可被搜索、索引、脚本化或压缩

（3）SVG 是可伸缩的

（4）SVG 图像可在任何的分辨率下被高质量地打印

（5）SVG 可在图像质量不下降的情况下被放大

## 把 SVG 直接嵌入 HTML 页面

![1650282110729](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650282110729.png)

# Canvas vs SVG

## SVG

（1）SVG 是一种使用 XML 描述 2D 图形的语言

（2）SVG 基于 XML，这意味着 SVG DOM 中的每个元素都是可用的。您可以为某个元素附加 JavaScript 事件处理器

（3）**在 SVG 中，每个被绘制的图形均被视为对象。如果 SVG 对象的属性发生变化，那么浏览器能够自动重现图形**

## Canvas

（1）Canvas 通过 JavaScript 来绘制 2D 图形

（2）Canvas 是逐像素进行渲染的。

（3）在 canvas 中，一旦图形被绘制完成，它就不会继续得到浏览器的关注。如果其位置发生变化，那么整个场景也需要重新绘制，包括任何或许已被图形覆盖的对象

## Canvas 与 SVG 的比较

（1）Canvas：

- <font color='red'>依赖分辨率</font>
- <font color='blue'>不支持事件处理器</font>
- 弱的文本渲染能力

- 能够以 .png 或 .jpg 格式保存结果图像

- 最适合图像密集型的游戏，其中的许多对象会被频繁重绘


（2）SVG：

- <font color='red'>不依赖分辨率</font>
- <font color='blue'>支持事件处理器</font>
- 最适合带有大型渲染区域的应用程序（比如谷歌地图）

- 复杂度高会减慢渲染速度（任何过度使用 DOM 的应用都不快）

- 不适合游戏应用

# 地理定位

## 定位用户的位置

（1）HTML5 Geolocation API 用于获得用户的地理位置

（2）鉴于该特性可能侵犯用户的隐私，除非用户同意，否则用户位置信息是不可用的

## 使用地理定位

（1）<font color='red'>使用 getCurrentPosition() 方法来获得用户的位置</font>

（2）返回用户位置的经度和纬度的代码示例

~~~
		<script>
			var x=document.getElementById("demo");
			function getLocation()
			{
			 if (navigator.geolocation)
			  {
					navigator.geolocation.getCurrentPosition(showPosition);
			  }
			else{x.innerHTML="Geolocation is not supported by this browser.";}
			 }
			function showPosition(position)
			{
			x.innerHTML="Latitude: " + position.coords.latitude +
			"<br />Longitude: " + position.coords.longitude;
			}
		</script>
~~~

解释：

1. 检测是否支持地理定位

2. **如果支持，则运行 getCurrentPosition() 方法。如果不支持，则向用户显示一段消息**
3. <font color='red'>如果getCurrentPosition()运行成功，则向参数showPosition中规定的函数返回一个coordinates对象</font>
4. <font color='blue'>showPosition() 函数获得并显示经度和纬度</font>

## 处理错误和拒绝

（1）getCurrentPosition() 方法的第二个参数用于处理错误。它规定当获取用户位置失败时运行的函数

（2）示例代码：

~~~
		function showError(error)
		  {
			switch(error.code)
				  {
					case error.PERMISSION_DENIED:
 					 x.innerHTML="User denied the request for Geolocation."
  					 break;
					case error.POSITION_UNAVAILABLE:
 					 x.innerHTML="Location information is unavailable."
 					 break;
				 case error.TIMEOUT:
  					  x.innerHTML="The request to get user location timed out."
					  break;
					case error.UNKNOWN_ERROR:
  					  x.innerHTML="An unknown error occurred."
					  break;
			 }
		}
~~~

> Permission denied - 用户不允许地理定位
>
> Position unavailable - 无法获取当前位置
>
> Timeout - 操作超时

## getCurrentPosition() 方法 - 返回数据

（1）若成功，则 getCurrentPosition() 方法返回对象。始终会返回 latitude、longitude 以及 accuracy 属性。如果可用，则会返回其他下面的属性

（2）属性：

| 属性                    | 描述                   |
| ----------------------- | ---------------------- |
| coords.latitude         | 十进制数的纬度         |
| coords.longitude        | 十进制的经度           |
| coords.accuacy          | 位置精度               |
| coords.altitude         | 海拔，海平面以上以米记 |
| coords.altitudeAccuracy | 位置的海拔精度         |
| coords.heading          | 方向，正北开始以度计   |
| coords.speed            | 速度，以米/每秒计数    |
| timestamp               | 响应的日期/时间        |

## Geolocation 对象 - 其他有趣的方法

（1）watchPosition() - 返回用户的当前位置，并继续返回用户移动时的更新位置（就像汽车上的 GPS）

（2）clearWatch() - 停止 watchPosition() 方法

# Web 存储

## 在客户端存储数据

（1）HTML5 提供了<font color='red'>两种在客户端存储数据的新方法：</font>

> - <font color='red'>**localStorage** </font>- 没有时间限制的数据存储（本地存储关闭页面依然存在）
> - <font color='blue'>**sessionStorage**</font> - 针对一个 session 的数据存储（关闭页面则丢失）

（2）之前，**这些都是由 cookie 完成的。但是 cookie 不适合大量数据的存储，因为它们由每个对服务器的请求来传递，这使得 cookie 速度很慢而且效率也不高**

（3）在 HTML5 中，数据不是由每个服务器请求传递的，而是<font color='red'>只有在请求时使用数据</font>。<font color='blue'>它使在不影响网站性能的情况下存储大量数据成为可能。</font>

（4）<font color='red'>对于不同的网站，数据存储于不同的区域，并且一个网站只能访问其自身的数据</font>

（5）<font color='green'>**HTML5 使用 JavaScript 来存储和访问数据**</font>

## localStorage 方法

（1）<font color='red'>**localStorage 方法存储的数据没有时间限制。第二天、第二周或下一年之后，数据依然可用**</font>

（2）如何创建和访问 localStorage：

![1650282722040](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650282722040.png)

 （3）对用户访问页面的次数进行计数的例子： 

![1650282758732](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650282758732.png)

## sessionStorage 方法

（1）sessionStorage 方法针对一个 session 进行数据存储。当用户关闭浏览器窗口后，数据会被删除

（2）如何创建并访问一个 sessionStorage

![1650282785987](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650282785987.png)

 （3）对用户在当前 session 中访问页面的次数进行计数的例子 

![1650282806842](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650282806842.png)

# HTML 5 应用程序缓存

## 什么是应用程序缓存

（1）HTML5 引入了应用程序缓存，这意味着 w<font color='red'>eb 应用可进行缓存，并可在没有因特网连接时进行访问</font>

（2）应用程序缓存为应用带来三个优势：

> - 离线浏览 - 用户可在应用离线时使用它们
>
> - 速度 - 已缓存资源加载得更快
>
> - 减少服务器负载 - 浏览器将只从服务器下载更新过或更改过的资源。
>

（3）<font color='red'>使用 HTML5，通过创建 cache manifest 文件，可以轻松地创建 web 应用的离线版本</font>

## HTML5 Cache Manifest 实例

 带有 cache manifest 的 HTML 文档（供离线浏览）的示例： 

![1650282885248](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650282885248.png)

## Cache Manifest 基础

（1）如需启用应用程序缓存，在文档的 标签中包含 manifest 属性

（2）manifest 文件的建议的文件扩展名是：".appcache"

（3）manifest 文件需要配置正确的 MIME-type，即 “text/cache-manifest”。必须在 web 服务器上进行配置

## Manifest 文件

（1）<font color='red'>manifest 文件是简单的文本文件，它告知浏览器被缓存的内容（以及不缓存的内容）</font>

（2）manifest 文件可分为三个部分：

> - <font color='red'>CACHE MANIFEST - 在此标题下列出的文件将在首次下载后进行缓存</font>
> - <font color='green'>**NETWORK - 在此标题下列出的文件需要与服务器的连接，且不会被缓存**</font>
> - <font color='blue'>FALLBACK - 在此标题下列出的文件规定当页面无法访问时的回退页面（比如 404 页面）</font>

（3）CACHE MANIFEST:

![1650282970201](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650282970201.png)

 manifest 文件列出了三个资源：一个 CSS 文件，一个 GIF 图像，以及一个 JavaScript 文件。当 manifest 文件加载后，浏览器会从网站的根目录下载这三个文件。然后，无论用户何时与因特网断开连接，这些资源依然是可用的 

（4）NETWORK：

NETWORK 小节规定文件 “login.asp” 永远不会被缓存，且离线时是不可用的：

![1650283003278](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650283003278.png)

 可以使用星号来指示所有其他资源/文件都需要因特网连接： 

![1650283015630](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650283015630.png)

（5）FALLBACK：

FALLBACK 小节规定如果无法建立因特网连接，则用 “offline.html” 替代 /html5/ 目录中的所有文件：

![1650283029219](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650283029219.png)

 <font color='green'>第一个 URI 是资源，第二个是替补 </font>

## 更新缓存

（1）一旦应用被缓存，它就会保持缓存直到发生下列情况：

> - <font color='red'>**用户清空浏览器缓存**</font>
> - manifest 文件被修改（参阅下面的提示）
> - <font color='blue'>由程序来更新应用缓存</font>

（2）完整的 Manifest 文件：

![1650283100712](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650283100712.png)

（3）以 “#” 开头的是注释行，但也可满足其他用途。应用的缓存会在其 manifest 文件更改时被更新

（4）如果您编辑了一幅图片，或者修改了一个 JavaScript 函数，这些改变都不会被重新缓存。更新注释行中的日期和版本号是一种使浏览器重新缓存文件的办法。

## 关于应用程序缓存的注释

（1）<font color='red'>一旦文件被缓存，则浏览器会继续展示已缓存的版本，即使您修改了服务器上的文件。为了确保浏览器更新缓存，您需要更新 manifest 文件</font>

（2）浏览器对缓存数据的容量限制可能不太一样

# Web Workers

## 什么是 Web Worker

（1）<font color='red'>web worker 是运行在后台的 JavaScript，不会影响页面的性能</font>

（2）当在 HTML 页面中执行脚本时，<font color='red'>页面的状态是不可响应的，直到脚本已完成</font>

（3）web worker 是运行在后台的 JavaScript，独立于其他脚本，不会影响页面的性能。您可以继续做任何愿意做的事情：点击、选取内容等等，而此时 web worker 在后台运行

## HTML5 Web Workers 实例

（1）检测 Web Worker 支持：

- 在创建 web worker 之前，请检测用户的浏览器是否支持它

![1650283212523](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650283212523.png)

（2）创建 web worker 文件：

- 在一个外部 JavaScript 中创建我们的 web worker
- 我们创建了计数脚本。该脚本存储于 “demo_workers.js” 文件中

![1650283226038](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650283226038.png)

 （3）创建 Web Worker 对象：

下面的代码检测是否存在 worker，如果不存在，它会创建一个新的 web worker 对象，然后运行 “demo_workers.js” 中的代码：

![1650283257133](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650283257133.png)

然后我们就可以从 web worker 发生和接收消息了。向 web worker 添加一个 “onmessage” 事件监听器：

![1650283277006](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650283277006.png)

（4）终止 Web Worker：

当我们创建 web worker 对象后，它会继续监听消息（即使在外部脚本完成之后）直到其被终止为止。

如需终止 web worker，并释放浏览器/计算机资源，请使用 terminate() 方法：

![1650283291929](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650283291929.png)

## Web Workers 和 DOM

 由于 web worker 位于外部文件中，它们无法访问下例 JavaScript 对象 

![1650283326101](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650283326101.png)

# 服务器发送事件

## Server-Sent 事件 - 单向消息传递

（1）<font color='red'>Server-Sent 事件指的是网页自动获取来自服务器的更新</font>

（2）以前也可能做到这一点，前提是网页不得不询问是否有可用的更新。通过服务器发送事件，更新能够自动到达。

例子：Facebook/Twitter 更新、估价更新、新的博文、赛事结果等。

（3）<font color='red'>HTML5 服务器发送事件（server-sent event）允许网页获得来自服务器的更新</font>

## 接收 Server-Sent 事件通知

 （1）EventSource 对象用于接收服务器发送事件通知： 

![1650283380554](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650283380554.png)

（2）例子解释：

- 创建一个新的 EventSource 对象，然后规定发送更新的页面的 URL（本例中是 “demo_sse.php”）

- 每接收到一次更新，就会发生 onmessage 事件

- 当 onmessage 事件发生时，把已接收的数据推入 id 为 “result” 的元素中

## 检测 Server-Sent 事件支持

 检测服务器发送事件的浏览器支持情况： 

![1650283409697](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650283409697.png)

## 服务器端代码实例

（1）为了让上面的例子可以运行，您<font color='red'>还需要能够发送数据更新的服务器（比如 PHP 和 ASP）</font>

（2）服务器端事件流的语法是非常简单的。把 “Content-Type” 报头设置为 “text/event-stream”

## EventSource 对象

| 事件      | 描述                     |
| --------- | ------------------------ |
| onopen    | 当通往服务器的连接被打开 |
| onmessage | 当接收到消息             |
| onerror   | 当错误发生               |

# Input 类型

## 新的 Input 类型

 email、url、number、range、Date pickers (date, month, week, time, datetime, datetime-local)、search、color 

## Input 类型 - email

（1）<font color='red'>email 类型用于应该包含 e-mail 地址的输入域，在提交表单时，会自动验证 email 域的值</font>

（2）代码示例：

![1650283557343](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650283557343.png)

## Input 类型 - url

（1）<font color='red'>url 类型用于应该包含 URL 地址的输入域。在提交表单时，会自动验证 url 域的值</font>

（2）代码示例：

![1650283581328](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650283581328.png)

## Input 类型 - number

（1）<font color='red'>number 类型用于应该包含数值的输入域。您还能够设定对所接受的数字的限定</font>

（2）示例代码：

![1650283596993](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650283596993.png)

**属性：**

| 属性  | 值     | 描述                                                  |
| ----- | ------ | ----------------------------------------------------- |
| max   | number | 规定允许的最大值                                      |
| min   | number | 规定允许的最小值                                      |
| step  | number | 规定合法的数字间隔（如step=3，合法的数字为-3，0，3... |
| value | number | 规定默认值Input 类型 - range                          |

## Input 类型 - range

（1）range 类型用于应该包含一定范围内数字值的输入域，range 类型显示为滑动条，您还能够设定对所接受的数字的限定

（2）代码示例：

![1650283793344](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650283793344.png)

## Input 类型 - Date Pickers（日期选择器）

（1）<font color='red'>HTML5 拥有多个可供选取日期和时间的新输入类型：</font>

> 1. date - 选取日、月、年
>
> 2. month - 选取月、年
>
> 3. week - 选取周和年
>
> 4. time - 选取时间（小时和分钟）
>
> 5. datetime - 选取时间、日、月、年（UTC 时间）
>
> 6. datetime-local - 选取时间、日、月、年（本地时间）
>

（2）代码示例：

![1650283843669](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650283843669.png)

## Input 类型 - search

（1）<font color='red'>search 类型用于搜索域，比如站点搜索或 Google 搜索。</font>

（2）search 域显示为常规的文本域

# HTML5 表单元素

## HTML5 的新的表单元素

<font color='red'> datalist、keygen、output </font>

## datalist 元素

（1）<font color='red'>datalist 元素规定输入域的选项列表，列表是通过 datalist 内的 option 元素创建的；</font>

（2）<font color='red'>如需把 datalist 绑定到输入域，请用输入域的 list 属性引用 datalist 的 id：</font>

![1650283923887](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650283923887.png)

 （3）option 元素永远都要设置 value 属性 

## keygen 元素

（1）<font color='red'>keygen 元素的作用是提供一种验证用户的可靠方法</font>

（2）**keygen 元素是密钥对生成器（key-pair generator）。**当提交表单时，会生成两个键，一个是私钥，一个公钥。<font color='red'>**私钥（private key）存储于客户端，公钥（public key）则被发送到服务器。**</font>公钥可用于之后验证用户的客户端证书（client certificate）。

（3）目前，浏览器对此元素的糟糕的支持度不足以使其成为一种有用的安全标准。

（4）代码示例：

![1650283987840](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650283987840.png)

## output 元素

（1）<font color='red'>output 元素用于不同类型的输出，比如计算或脚本输出：</font>

（2）代码示例：

![1650284004074](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650284004074.png)

# HTML5 表单属性

## HTML5 的新的表单属性

（1）新的 form 属性：

> - autocomplete、novalidate
>

（2）新的 input 属性：

> - autocomplete、autofocus、form、form overrides (formaction, formenctype, formmethod, formnovalidate, formtarget)、height 和 width、list、min, max 和 step、multiple、pattern (regexp)、placeholder、required

## autocomplete 属性

（1）autocomplete 属性规定 form 或 input 域应该拥有自动完成功能

（2）autocomplete 适用于 标签，以及以下类型的 标签：text, search, url, telephone, email, password, datepickers, range 以及 color

（3）当用户在自动完成域中开始输入时，浏览器应该在该域中显示填写的选项：

![1650284067061](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650284067061.png)

## autofocus 属性

（1）autofocus 属性规定在页面加载时，域自动地获得焦点。

（2）autofocus 属性适用于所有 标签的类型

（3）代码示例：

![1650284088423](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650284088423.png)

## form 属性

（1）form 属性规定输入域所属的一个或多个表单

（2）form 属性适用于所有 标签的类型

（3）form 属性必须引用所属表单的 id

（4）代码示例：

![1650284107093](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650284107093.png)

## 表单重写属性

（1）<font color='red'>表单重写属性（form override attributes）允许您重写 form 元素的某些属性设定</font>

（2）表单重写属性有：

> - formaction - 重写表单的 action 属性
>
> - formenctype - 重写表单的 enctype 属性
>
> - formmethod - 重写表单的 method 属性
>
> - formnovalidate - 重写表单的 novalidate 属性
>
> - formtarget - 重写表单的 target 属性
>

（3）表单重写属性适用于以下类型的 标签：submit 和 image

（4）代码示例：

![1650284141925](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650284141925.png)

## height 和 width 属性

（1）<font color='blue'>height 和 width 属性规定用于 image 类型的 input 标签的图像高度和宽度</font>

（2）height 和 width 属性只适用于 image 类型的 标签

（3）代码示例：

![1650284171554](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650284171554.png)

## list 属性

（1）<font color='red'>list 属性规定输入域的 datalist。datalist 是输入域的选项列表</font>

（2）list 属性适用于以下类型的 标签：text, search, url, telephone, email, date pickers, number, range 以及 color。

（3）代码示例：

![1650284194690](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650284194690.png)

## min、max 和 step 属性

（1）<font color='red'>min、max 和 step 属性用于为包含数字或日期的 input 类型规定限定（约束）</font>

（2）

> - max 属性规定输入域所允许的最大值。
> - min 属性规定输入域所允许的最小值。
>
> - step 属性为输入域规定合法的数字间隔（如果 step=“3”，则合法的数是 -3,0,3,6 等）
>

（3）min、max 和 step 属性适用于以下类型的 标签：date pickers、number 以及 range

（4）代码实例：

![1650284232290](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650284232290.png)

## multiple 属性

（1）multiple 属性规定输入域中可选择多个值

（2）multiple 属性适用于以下类型的 标签：email 和 file

（3）代码实例：

![1650284251395](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650284251395.png)

## novalidate 属性

（1）novalidate 属性规定在提交表单时不应该验证 form 或 input 域

（2）novalidate 属性适用于 以及以下类型的 标签：text, search, url, telephone, email, password, date pickers, range 以及 color.

（3）代码示例：

![1650284272463](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650284272463.png)

## pattern 属性

（1）pattern 属性规定用于验证 input 域的模式（pattern）

（2）模式（pattern） 是正则表达式

（3）pattern 属性适用于以下类型的 标签：text, search, url, telephone, email 以及 password

（4）下面的例子显示了一个只能包含三个字母的文本域（不含数字及特殊字符）

![1650284291883](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650284291883.png)

## placeholder 属性

（1）<font color='blue'>placeholder 属性提供一种提示（hint），描述输入域所期待的值</font>

（2）placeholder 属性适用于以下类型的 标签：text, search, url, telephone, email 以及 password。

（3）提示（hint）会在输入域为空时显示出现，会在输入域获得焦点时消失：

![1650284313870](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650284313870.png)

## required 属性

（1）required 属性规定必须在提交之前填写输入域（不能为空）

（2）required 属性适用于以下类型的 标签：text, search, url, telephone, email, password, date pickers, number, checkbox, radio 以及 file

（3）代码示例：

![1650284338878](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650284338878.png)

