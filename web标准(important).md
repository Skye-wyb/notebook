##web标准(important)

+  **<font color='blue'>Web 标准是由 W3C 组织和其他标准化组织制定的一系列标准的集合。W3C（万维网联盟）是国际最著名的标准化组织。</font>**

###为什么需要Web标准：

+ 浏览器不同，它们显示页面或者排版就有些许差异
  ![](C:/Users/86186/Desktop/前端开发笔记/images/web标准.png)

+ **遵循 Web 标准除了可以让不同的开发人员写出的页面更标准、更统一外**，还有以下优点：

  > 1. 让 Web 的发展前景更广阔。 
  > 2. 内容能被更广泛的设备访问。
  > 3. 更容易被搜寻引擎搜索。
  > 4. 降低网站流量费用。
  > 5. 使网站更易于维护。
  > 6. 提高页面浏览速度。

##web标准的构成：

主要包括<font color='red'>结构（Structure） 、表现（Presentation）和行为（Behavior）</font>三个方面。

![](C:/Users/86186/Desktop/前端开发笔记/images/图片45.png)
Web 标准提出的最佳体验方案：**结构、样式、行为相分离**。  
简单理解：**<font color='green'>结构写到 HTML 文件中， 表现写到 CSS 文件中， 行为写到 JavaScript 文件中</font>**
![](C:/Users/86186/Desktop/前端开发笔记/images/鸟.png)

1.结构类似身体

2.表现类似外观装饰

3.行为类似行为动作

4.相比较而言, 三者中结构最重要.

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200528091021219.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1NhdGFuX0Rldmls,size_16,color_FFFFFF,t_70#pic_center) 

**介绍一下你对浏览器内核的理解？常见的浏览器内核有哪些？**

浏览器内核包括两部分，渲染引擎和js引擎。渲染引擎负责读取网页内容，整理讯息，计算网页的显示方式并显示页面，js引擎是解析执行js获取网页的动态效果。 后来 JS 引擎越来越独立，内核就倾向于只指渲染引擎。

> IE：Trident
>
> firefox：Gecko
>
> chrome、safari：webkit
>
> Opera：Presto
>
> Microsoft Edge：EdgeHTML

# table

## 表格基本标签

 ![img](https://img-blog.csdnimg.cn/20200528105253736.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1NhdGFuX0Rldmls,size_16,color_FFFFFF,t_70#pic_center) 

 **创建表格的基本语法：** 

![1650419293195](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650419293195.png)

> 1. table用于定义一个表格标签。
> 2. tr标签：用于定义表格中的行，必须嵌套在 table标签中。
> 3. td 用于定义表格中的单元格，必须嵌套在标签中。
> 4. th用于定义表头单元格
> 5. 字母 td 指表格数据（table data），即数据单元格的内容，现在我们明白，表格最合适的地方就是用来存储数据的

 ![img](https://img-blog.csdnimg.cn/2020052810541352.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1NhdGFuX0Rldmls,size_16,color_FFFFFF,t_70#pic_center) 

**总结：**

- 表格的主要目的是用来显示特殊数据的
- 一个完整的表格有表格标签（table），行标签（tr），单元格标签（td）组成，没有列的标签

- 中只能嵌套 类的单元格
- 标签，他就像一个容器，可以容纳所有的元素

 ![img](https://img-blog.csdnimg.cn/20200528105429377.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1NhdGFuX0Rldmls,size_16,color_FFFFFF,t_70#pic_center) 

 ![img](https://img-blog.csdnimg.cn/20200528105445841.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1NhdGFuX0Rldmls,size_16,color_FFFFFF,t_70#pic_center) 

## 表格标题caption

![1650419417736](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650419417736.png)

**注意：**

1. caption 元素定义**表格标题**，通常这个标题会被居中且显示于表格之上。
2. caption 标签必须紧随 table 标签之后。
3. 这个标签只存在在表格里面才有意义。

### 合并单元格2种方式

- 跨行合并：rowspan=“合并单元格的个数”
- 跨列合并：colspan=“合并单元格的个数”

### 合并单元格顺序

> **合并的顺序我们按照 先上 后下 先左 后右 的顺序**

### 合并单元格三步曲

1. 先确定是跨行还是跨列合并
2. 根据 先上 后下 先左 后右的原则找到目标单元格 然后写上 合并方式 还有 要合并的单元格数量 比如 ：
3. 删除多余的单元格 单元格

## 表格总结

![1650419508889](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650419508889.png)

