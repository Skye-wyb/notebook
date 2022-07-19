# Javascript算法

# 栈

**<font color='hotpink'>后进先出</font>**

入栈：添加数据，数组的push()

出栈：删除数据，数组的pop()

> 删除数组的最后一个元素，并返回删除的这个元素

例题：

**20-**给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串 s ，判断字符串是否有效。

> 有效字符串需满足：
>
> 左括号必须用相同类型的右括号闭合。
> 左括号必须以正确的顺序闭合。

> 输入：s = "()[]{}"
> 输出：true

![1650864751723](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650864751723.png)

**1047-**给出由小写字母组成的字符串 S，重复项删除操作会选择两个相邻且相同的字母，并删除它们。

> 在 S 上反复执行重复项删除操作，直到无法继续删除。
>
> 在完成所有重复项删除操作后返回最终的字符串。答案保证唯一。
>

> 输入："abbaca"
> 输出："ca"

![1650864798944](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650864798944.png)

**71-**简化路径

给你一个字符串 path ，表示指向某一文件或目录的 Unix 风格 绝对路径 （以 '/' 开头），请你将其转化为更加简洁的规范路径。

在 Unix 风格的文件系统中，一个点（.）表示当前目录本身；此外，两个点 （..） 表示将目录切换到上一级（指向父目录）；两者都可以是复杂相对路径的组成部分。任意多个连续的斜杠（即，'//'）都被视为单个斜杠 '/' 。 对于此问题，任何其他格式的点（例如，'...'）均被视为文件/目录名称。

请注意，返回的 规范路径 必须遵循下述格式：

> - 始终以斜杠 '/' 开头。
> - 两个目录名之间必须只有一个斜杠 '/' 。
> - 最后一个目录名（如果存在）不能 以 '/' 结尾。
> - 此外，路径仅包含从根目录到目标文件或目录的路径上的目录（即，不含 '.' 或 '..'）。
> - 返回简化后得到的 规范路径 。

> 输入：path = "/home/"
> 输出："/home"

> 输入：path = "/home//foo/"
> 输出："/home/foo"

![1650865589658](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650865589658.png)

# 链表

> **<font color='hotpink'>多个元素存储的链表</font>**

> **链表中的元素在内存中，不是顺序存储的，而是通过“next”指针联系在一起的**

> JS中的原型链原理就是链表结构

![1650865888105](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650865888105.png)

### 链表和数组的区别

1. 数组是按照顺序存储的，即有序存储的。在数组中删除第一位和第二位是很方便的。删除、添加中间元素的时候，会改变其他元素的位置。
2. 链表不是顺序存储的，是通过next指针连起来的。删除不存在移位。

### 链表的分类

#### 单向链表

单向链表只有一个next指针，指向下一个元素

> ![1650866515192](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650866515192.png)

1. 双向链表

   双向链表有一个next指针，指向下一个元素，还多了一个prev指针，指向上一个元素

2. 环形链表

#### instanceof原理

<font color='hotpink'>手写instanceof</font>

![1650866781297](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650866781297.png)

#### 环形链表

**141-**给你一个链表的头节点 head ，判断链表中是否有环。

<font color='hotpink'>如果链表中有某个节点，可以通过连续跟踪 next 指针再次到达，则链表中存在环。</font> 为了表示给定链表中的环，评测系统内部使用整数 pos 来表示链表尾连接到链表中的位置（索引从 0 开始）。注意：pos 不作为参数进行传递 。仅仅是为了标识链表的实际情况。

如果链表中存在环 ，则返回 true 。 否则，返回 false 。

![1650866897842](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650866897842.png)

![1650867230179](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650867230179.png)

标记法

![1655609415015](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655609415015.png)

### 链表的中间节点

给定一个头结点为 `head` 的非空单链表，返回链表的中间结点。

如果有两个中间结点，则返回第二个中间结点。

![1655610039356](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655610039356.png)

![1655610062807](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655610062807.png)

快慢指针：快指针走两步慢指针走一步，快指针走到末尾，慢指针正好走到中间

# 字典和哈希表

## 字典Map

> **<font color='hotpink'>字典：是键值对形式存储，类似于JavaScript的对象</font>**
>
> **<font color='red'>JavaScript对象中：键[key]都是字符串类型或者会转换为字符串类型</font>**

#### 面试题解析

![1650867774836](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650867774836.png)

原因：对象的key值都是字符串类型或都会被转换为字符串类型，对a的键赋值相当于：

![1650868028279](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650868028279.png)

所以前面的值会被后面的值覆盖掉

> **字典：map表示，map的键不会转换类型**

![1650868523179](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650868523179.png)

Map结构的实例有以下属性和操作方法。

**（1）size属性**

`size`属性返回Map结构的成员总数。

![1650868572605](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650868572605.png)

**（2）set(key, value)**

`set`方法设置`key`所对应的键值，然后返回整个Map结构。如果`key`已经有值，则键值会被更新，否则就新生成该键。

![1650868590742](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650868590742.png)

`set`方法返回的是Map本身，因此可以采用链式写法。

![1650868607374](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650868607374.png)

**（3）get(key)**

`get`方法读取`key`对应的键值，如果找不到`key`，返回`undefined`。

![1650868624450](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650868624450.png)

**（4）has(key)**

`has`方法返回一个布尔值，表示某个键是否在Map数据结构中。

![1650868640495](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650868640495.png)

**（5）delete(key)**

`delete`方法删除某个键，返回true。如果删除失败，返回false。

![1650868658319](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650868658319.png)

**（6）clear()**

`clear`方法清除所有成员，没有返回值。

![1650868679399](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650868679399.png)

### 遍历方法

Map原生提供三个遍历器生成函数和一个遍历方法。

- `keys()`：返回键名的遍历器。
- `values()`：返回键值的遍历器。
- `entries()`：返回所有成员的遍历器。
- `forEach()`：遍历Map的所有成员。

需要特别注意的是，Map的遍历顺序就是插入顺序。

下面是使用实例。

![1650868738169](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650868738169.png)

上面代码最后的那个例子，表示Map结构的默认遍历器接口（`Symbol.iterator`属性），就是`entries`方法。

![1650868754840](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650868754840.png)

Map结构转为数组结构，比较快速的方法是结合使用扩展运算符（`...`）。

![1650868774056](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650868774056.png)

结合数组的`map`方法、`filter`方法，可以实现Map的遍历和过滤（Map本身没有`map`和`filter`方法）。

![1650868792046](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650868792046.png)

此外，Map还有一个`forEach`方法，与数组的`forEach`方法类似，也可以实现遍历。

![1650868807612](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650868807612.png)

`forEach`方法还可以接受第二个参数，用来绑定`this`。

![1650868823006](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650868823006.png)

上面代码中，`forEach`方法的回调函数的`this`，就指向`reporter`。

## 哈希表

> 哈希表：也称为散列表；

> **<font color='hotpink'>它类似于数组，但是成员的值都是唯一的，没有重复的值。</font>**

> 字典是根据添加的顺序排列的
>
> 哈希表不是

![1650869938563](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650869938563.png)

**01-**两数之和

给定一个整数数组 nums 和一个整数目标值 target，请你在该数组中找出 和为目标值 target  的那 两个 整数，并返回它们的数组下标。

你可以假设每种输入只会对应一个答案。但是，数组中同一个元素在答案里不能重复出现。

你可以按任意顺序返回答案。

![1650870006933](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650870006933.png)

![1650870219642](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650870219642.png)

**217-**存在重复元素

给你一个整数数组 `nums` 。如果任一值在数组中出现 **至少两次** ，返回 `true` ；如果数组中每个元素互不相同，返回 `false` 。 

![1650870287973](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650870287973.png)

![1650870398047](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650870398047.png)

**349-**两个数组的交集

给定两个数组 `nums1` 和 `nums2` ，返回 *它们的交集* 。输出结果中的每个元素一定是 **唯一** 的。我们可以 **不考虑输出结果的顺序** 。 

![1650870457508](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650870457508.png)

方法一：纯map

![1650870893100](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650870893100.png)

方法二：Set，先去重

![1650871586711](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650871586711.png)

**1207-**独一无二的出现次数

> 给你一个整数数组 `arr`，请你帮忙统计数组中每个数的出现次数。
>
> 如果每个数的出现次数都是独一无二的，就返回 `true`；否则返回 `false`。

![1650871713115](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650871713115.png)

![1650874151846](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650874151846.png)

#### 面试题

判断一个字符串中出现次数最多的字符，并统计次数。

![1650871798894](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650871798894.png)

解决：

![1650872488710](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650872488710.png)



## Set集合

### Set实例的属性和方法

Set结构的实例有以下属性。

- `Set.prototype.constructor`：构造函数，默认就是`Set`函数。
- `Set.prototype.size`：返回`Set`实例的成员总数。

Set实例的方法分为两大类：操作方法（用于操作数据）和遍历方法（用于遍历成员）。下面先介绍四个操作方法。

- `add(value)`：添加某个值，返回Set结构本身。
- `delete(value)`：删除某个值，返回一个布尔值，表示删除是否成功。
- `has(value)`：返回一个布尔值，表示该值是否为`Set`的成员。
- `clear()`：清除所有成员，没有返回值。

上面这些属性和方法的实例如下。

![1650869147755](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650869147755.png)

下面是一个对比，看看在判断是否包括一个键上面，`Object`结构和`Set`结构的写法不同。

![1650869169434](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650869169434.png)

`Array.from`方法可以将Set结构转为数组。

![1650869185118](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650869185118.png)

这就提供了去除数组重复成员的另一种方法。

![1650869200075](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650869200075.png)

### 遍历操作

Set结构的实例有四个遍历方法，可以用于遍历成员。

- `keys()`：返回键名的遍历器
- `values()`：返回键值的遍历器
- `entries()`：返回键值对的遍历器
- `forEach()`：使用回调函数遍历每个成员

需要特别指出的是，`Set`的遍历顺序就是插入顺序。这个特性有时非常有用，比如使用Set保存一个回调函数列表，调用时就能保证按照添加顺序调用。

**（1）`keys()`，`values()`，`entries()`**

`key`方法、`value`方法、`entries`方法返回的都是遍历器对象（详见《Iterator对象》一章）。由于Set结构没有键名，只有键值（或者说键名和键值是同一个值），所以`key`方法和`value`方法的行为完全一致。

![1650869226715](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650869226715.png)

上面代码中，`entries`方法返回的遍历器，同时包括键名和键值，所以每次输出一个数组，它的两个成员完全相等。

Set结构的实例默认可遍历，它的默认遍历器生成函数就是它的`values`方法。

![1650869244246](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650869244246.png)

这意味着，可以省略`values`方法，直接用`for...of`循环遍历Set。

![1650869261913](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650869261913.png)

**（2）`forEach()`**

Set结构的实例的`forEach`方法，用于对每个成员执行某种操作，没有返回值。

![1650869276611](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650869276611.png)

上面代码说明，`forEach`方法的参数就是一个处理函数。该函数的参数依次为键值、键名、集合本身（上例省略了该参数）。另外，`forEach`方法还可以有第二个参数，表示绑定的this对象。

**（3）遍历的应用**

扩展运算符（`...`）内部使用`for...of`循环，所以也可以用于Set结构。

![1650869292041](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650869292041.png)

扩展运算符和Set结构相结合，就可以去除数组的重复成员。

![1650869309575](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650869309575.png)

而且，数组的`map`和`filter`方法也可以用于Set了。

![1650869324489](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650869324489.png)

因此使用Set可以很容易地实现并集（Union）、交集（Intersect）和差集（Difference）。

![1650869341977](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650869341977.png)

如果想在遍历操作中，同步改变原来的Set结构，目前没有直接的方法，但有两种变通方法。一种是利用原Set结构映射出一个新的结构，然后赋值给原来的Set结构；另一种是利用`Array.from`方法。

![1650869357160](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650869357160.png)

上面代码提供了两种方法，直接在遍历操作中改变原来的Set结构。

# 树

> **一种分层数据的抽象模型**
>
> 分层级关系的

## 深度优先遍历（搜索）

> - 前序遍历
> - 中序遍历
> - 后序遍历

从根节点出发，尽可能深的搜索树的结点。

> 1. 访问根节点
> 2. 对根节点的children依次进行深度优先遍历

![1650874882886](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650874882886.png)

## 广度优先遍历（搜索）

> - 层次遍历

从根节点出发，优先访问离根节点最近的节点

> 1. 新建一个队列，根节点入队
> 2. 把对头出队
> 3. 把对头的children依次入队
> 4. 重复2，3步骤，直到队列为空为止

![1650875274927](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650875274927.png)

## 二叉树

### 二叉树的结构

![1650876020806](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650876020806.png)

输出：

> ![1650876064399](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650876064399.png)

#### 以数组的形式存储二叉树-顺序存储

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651282817201.png" alt="1651282817201" style="zoom:67%;" />、

数组形式存储二叉树的遍历：

> **<font color='hotpink'>如果父节点的数组下表是i，那么它的左孩子就是i * 2 + 1，右孩子就是 i * 2 + 2。</font>**

### 二叉树的前序遍历

> **<font color='hotpink'>前序遍历&先序遍历：根节点->左子树根节点->右子树根节点</font>**

**144-**二叉树的前序遍历

**递归的形式**

![1650876896614](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650876896614.png)

**栈的形式**

![1650877431330](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650877431330.png)

### 二叉树的中序遍历

> **中序遍历：左子树->根节点->右子树**

**94-**二叉树的中序遍历

**递归的形式：**

![1650878179952](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650878179952.png)

**栈的形式：**

![1650878583649](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650878583649.png)

### 二叉树的后序遍历

> **后序遍历：左子树->右子树->根节点**

**145-**二叉树的后序遍历

**递归形式：**

![1650878938777](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650878938777.png)

**栈的形式：**

![1650879233976](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650879233976.png)

### 二叉树的层序遍历

二叉树的层次遍历

> 给你二叉树的根节点 `root` ，返回其节点值的 **层序遍历** 。 （即逐层地，从左到右访问所有节点）。 

![1650972226618](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650972226618.png)

![1651286137897](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651286137897.png)

**111-**二叉树的最小深度

> 给定一个二叉树，找出其最小深度。
>
> 最小深度是从根节点到最近叶子节点的最短路径上的节点数量。
>
> **说明：**叶子节点是指没有子节点的节点。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650879427331.png" alt="1650879427331" style="zoom:60%;" />

解答：

![1650879749994](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650879749994.png)

**104-**二叉树的最大深度

> 给定一个二叉树，找出其最大深度。
>
> 二叉树的深度为根节点到最远叶子节点的最长路径上的节点数。
>
> **说明:** 叶子节点是指没有子节点的节点。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650879825808.png" alt="1650879825808" style="zoom:80%;" />

解答：

![1650880119960](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650880119960.png)

递归解法：

![1655605769125](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655605769125.png)

**226-**翻转二叉树

**给你一棵二叉树的根节点 `root` ，翻转这棵二叉树，并返回其根节点。 **

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650880208693.png" alt="1650880208693" style="zoom:80%;" />

解答：

（1）**先翻转左右子树，再交换**

![1656740668866](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656740668866.png)

![1650880417313](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650880417313.png)

**层次遍历（BFS）**

![1651289110545](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651289110545.png)

**深度优先遍历（DFS）**

![1651289401005](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651289401005.png)

**100-**相同的树

> 给你两棵二叉树的根节点 `p` 和 `q` ，编写一个函数来检验这两棵树是否相同。
>
> 如果两个树在结构上相同，并且节点具有相同的值，则认为它们是相同的。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650880482556.png" alt="1650880482556" style="zoom:80%;" />

解答：

![1650880863244](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650880863244.png)

# 堆

## 堆的概念

堆都能用树来表示，并且一般树的实现都是利用链表。

**而二叉堆是一种特殊的堆，它用完全二叉树表示，却可以利用数组实现。**

平时使用最多的是二叉堆，它可以用完全二叉树表示，二叉堆易于存储，并且便于索引

**<font color='hotpink'>堆数据结构像树，但是，是通过数组来实现的，而不是通过链表实现。二叉堆</font>**

**最小堆：从小到大排序**

**最大堆：从大到小排序**

### 注意

在堆的实现时，需要注意：

> 因为是数组，所以父子节点的关系就不需要特殊的结构去维护了，索引之间通过计算就可以得到，省掉了很多的麻烦。如果是链表结构，就会复杂很多。
>
> 完全二叉树要求叶子节点从左往右填满，才能开始填充下一层，这就保证了不需要对数组整体进行大片的移动。这也是随机存储结构（数组）的短板；删除一个元素之后，整体往前移是比较费时的。这个特性也导致堆在删除元素的时候，要把最后一个叶子节点填充到树根节点的缘由。

二叉堆橡树的样子可以理解，但将它们安排在数组里的话，通过当前下标怎么能找到父结点和子节点呢？

1. 左子树：2*index+1

2. 右子树：2*index+2

3. 父节点：（index-1）/ 2

   > - 第 n 个元素的 左子节点 为 2*n+1
   > - 第 n 个元素的 右子节点 为 2*n+2
   > - 第 n 个元素的 父节点 为 (n-1)/2
   > - 最后一个非叶子节点为 Math.floor(arr.length/2)-1

**<font color='hotpink'>堆是具有以下性质的完全二叉树：</font>**

> 大顶堆：每个节点的值都 大于或等于 其左右孩子节点的值
>
>  ![image.png](https://pic.leetcode-cn.com/1624163681-hJGivE-image.png)
>
>  ![image.png](https://pic.leetcode-cn.com/1624163693-HYBERK-image.png) 
>
>  大顶堆特点：`arr[i] >= arr[2*i+1] && arr[i] >= arr[2*i+2]`，i 对应第几个节点，i 从 0 开始编号  

注：没有要求左右值的大小关系

> 小顶堆：每个节点的值都 小于或等于 其左右孩子节点的值
>
>  ![image.png](https://pic.leetcode-cn.com/1624163701-hqAboA-image.png)
>
>  小顶堆特点：`arr[i] <= arr[2*i+1] && arr[i] <= arr[2*i+2]`，i 对应第几个节点，i 从 0 开始  

### 排序说明

- 升序：一般采用大顶堆
- 降序：一般采用小顶堆

## 最小堆

![1650887416574](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650887416574.png)

**215-**数组中的第K个最大元素

> 给定整数数组 `nums` 和整数 `k`，请返回数组中第 `K` 个最大的元素。
>
> 请注意，你需要找的是数组排序后的第 `k` 个最大的元素，而不是第 `k` 个不同的元素。

#### 详细解答：

##### 基本思想

将待排序序列构造成一个大顶堆

注意：这里使用的是数组，而不是一颗二叉树

此时：整个序列的 最大值就是堆顶的根节点

将其 与末尾元素进行交换，此时末尾就是最大值

然后将剩余 n-1 个元素重新构造成一个堆，这样 就会得到 n 个元素的次小值。如此反复，便能的得到一个有序序列。

##### 堆排序步骤图解

对数组 `4,6,8,5,9` 进行堆排序，将数组升序排序。

##### 步骤一：构造初始堆

1. 给定无序序列结构 如下：注意这里的操作用数组，树结构只是参考理解

 ![image.png](https://pic.leetcode-cn.com/1624163715-VXPhZJ-image.png) 

 将给定无序序列构造成一个大顶堆。 

2. 此时从最后一个非叶子节点开始调整，从左到右，从上到下进行调整。

叶节点不用调整，第一个非叶子节点 arr.length/2-1 = 5/2-1 = 1 ，也就是 元素为 6 的节点。

>  比较时：先让 5 与 9 比较，得到最大的那个，再和 6 比较，发现 9 大于 6，则调整他们的位置。 

 ![image.png](https://pic.leetcode-cn.com/1624163724-QCfxWl-image.png) 

3. 找到第二个非叶子节点 4，由于 `[4,9,8]` 中，9 元素最大，则 4 和 9 进行交换 

 ![image.png](https://pic.leetcode-cn.com/1624163737-nWDnEx-image.png) 

4. 此时，交换导致了子根 `[4,5,6]` 结构混乱，将其继续调整。`[4,5,6]` 中 6 最大，将 4 与 6 进行调整。

 ![image.png](https://pic.leetcode-cn.com/1624163748-vVZNTN-image.png) 

 此时，就将一个无序序列构造成了一个大顶堆。 

##### 步骤二：将堆顶元素与末尾元素进行交换

将堆顶元素与末尾元素进行交换，使其末尾元素最大。然后继续调整，再将堆顶元素与末尾元素交换，得到第二大元素。如此反复进行交换、重建、交换。

1. 将堆顶元素 9 和末尾元素 4 进行交换

 ![image.png](https://pic.leetcode-cn.com/1624163757-rooMsP-image.png) 

2. 重新调整结构，使其继续满足堆定义

 ![image.png](https://pic.leetcode-cn.com/1624163766-WsYato-image.png) 

3. 再将堆顶元素 8 与末尾元素 5 进行交换，得到第二大元素 8

 ![image.png](https://pic.leetcode-cn.com/1624163783-IhXOJT-image.png) 

4. 后续过程，继续进行调整、交换，如此反复进行，最终使得整个序列有序

 ![image.png](https://pic.leetcode-cn.com/1624163793-fGUBxG-image.png) 

##### 总结思路

> 1. 将无序序列构建成一个堆，根据升序降序需求选择大顶堆
> 2. 将堆顶元素与末尾元素交换，将最大元素「沉」到数组末端
> 3. 重新调整结构，使其满足堆定义，然后继续交换堆顶与当前末尾元素，反复执行调整、交换步骤，直到整个序列有序。

![1650888670282](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650888670282.png)

# 排序搜索算法

排序：冒泡排序、快速排序、插入排序...

搜索：二分搜索、顺序搜索...

工具地址：https://visualgo.net/zh

## 插入排序

> 1. 从第一个元素开始，该元素可以被认为已经被排序
> 2. 取出下一个元素，在已经排序好的序列中，从后往前扫描
> 3. 直到找到小于或者等于该元素的位置
> 4. 将该位置后面的所有已经排序的元素从后往前移动
> 5. 将该元素插入到该位置
> 6. 重复步骤2-5

![1650889892828](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650889892828.png)

## 归并排序

![1648716401252](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1648716401252.png)

![1650891050206](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650891050206.png)

![1650891100842](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650891100842.png)

## 快速排序

![1650891675516](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650891675516.png)

![1650891688524](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650891688524.png)

## 分治

分治：一个大问题，分成多个小问题，递归解决小问题，将结果合并从而来解决原来的问题。

**374-**猜数字大小

> 猜数字游戏的规则如下：
>
> 每轮游戏，我都会从 1 到 n 随机选择一个数字。 请你猜选出的是哪个数字。
> 如果你猜错了，我会告诉你，你猜测的数字比我选出的数字是大了还是小了。
> 你可以通过调用一个预先定义好的接口 int guess(int num) 来获取猜测结果，返回值一共有 3 种可能的情况（-1，1 或 0）：
>
> - -1：我选出的数字比你猜的数字小 pick < num
> - 1：我选出的数字比你猜的数字大 pick > num
> - 0：我选出的数字和你猜的数字一样。恭喜！你猜对了！pick == num
>
> 返回我选出的数字。

![1650891865120](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650891865120.png)

**二分搜索的方法**

![1650892276520](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650892276520.png)

**分治的方法：用到递归**

![1650892864795](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650892864795.png)

# diff算法

**功能：提升性能**

> 把DOM转换为数据，方便操作，提高性能！

虚拟DOM：其实就是数据，把DOM数据化

![1650934354706](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650934354706.png)

### 主流：snabbdom、virtual-dom

### 搭建环境

snabbdom：https://www.npmjs.com/package/snabbdom

1. npm init -y

2. npm i webpack@5 webpack-cli@3 webpack-dev-server@3

3. npm i snabbdom -S

   > 修改package.json
   >
   > ![1650935934342](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650935934342.png)

4. 新建webpack.config.js

5. 配置webpack.config.js

> ![1650935878102](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650935878102.png)

在public/index.html中引入script文件：

引入的是webpack的出口文件：

![1650936128484](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650936128484.png)

# 字节跳动LeetCode

### 3

无重复字符的最长字串

 给定一个字符串 `s` ，请你找出其中不含有重复字符的 **最长子串** 的长度。 

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650949655599.png" alt="1650949655599" style="zoom:80%;" />

![1650949723959](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650949723959.png)



### 88

合并两个有序数组

给你两个按 非递减顺序 排列的整数数组 nums1 和 nums2，另有两个整数 m 和 n ，分别表示 nums1 和 nums2 中的元素数目。

请你 合并 nums2 到 nums1 中，使合并后的数组同样按 非递减顺序 排列。

注意：最终，合并后数组不应由函数返回，而是存储在数组 nums1 中。为了应对这种情况，nums1 的初始长度为 m + n，其中前 m 个元素表示应合并的元素，后 n 个元素为 0 ，应忽略。nums2 的长度为 n 。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650949759821.png" alt="1650949759821" style="zoom:80%;" />

![1650949869015](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650949869015.png)

### 165

比较版本号

给你两个版本号 version1 和 version2 ，请你比较它们。

版本号由一个或多个修订号组成，各修订号由一个 '.' 连接。每个修订号由 多位数字 组成，可能包含 前导零 。每个版本号至少包含一个字符。修订号从左到右编号，下标从 0 开始，最左边的修订号下标为 0 ，下一个修订号下标为 1 ，以此类推。例如，2.5.33 和 0.1 都是有效的版本号。

比较版本号时，请按从左到右的顺序依次比较它们的修订号。比较修订号时，只需比较 忽略任何前导零后的整数值 。也就是说，修订号 1 和修订号 001 相等 。如果版本号没有指定某个下标处的修订号，则该修订号视为 0 。例如，版本 1.0 小于版本 1.1 ，因为它们下标为 0 的修订号相同，而下标为 1 的修订号分别为 0 和 1 ，0 < 1 。

返回规则如下：

如果 version1 > version2 返回 1，
如果 version1 < version2 返回 -1，
除此之外返回 0。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650949923247.png" alt="1650949923247" style="zoom:80%;" />

![1650949951116](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650949951116.png)

### 53

最大子序和

给你一个整数数组 `nums` ，请你找出一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。

**子数组** 是数组中的一个连续部分。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650950034480.png" alt="1650950034480" style="zoom:80%;" />

![1650950089410](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650950089410.png)

### 55

跳跃游戏

给定一个非负整数数组 `nums` ，你最初位于数组的 **第一个下标** 。

数组中的每个元素代表你在该位置可以跳跃的最大长度。

判断你是否能够到达最后一个下标。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656215799319.png" alt="1656215799319" style="zoom:50%;" />

![1656215820864](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656215820864.png)



### 112

路径总和

给你二叉树的根节点 root 和一个表示目标和的整数 targetSum 。判断该树中是否存在 根节点到叶子节点 的路径，这条路径上所有节点值相加等于目标和 targetSum 。如果存在，返回 true ；否则，返回 false 。

**叶子节点 是指没有子节点的节点。**

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650950215162.png" alt="1650950215162" style="zoom:80%;" />

![1650950267341](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650950267341.png)

### 129

求根到叶子节点数字之和

给你一个二叉树的根节点 root ，树中每个节点都存放有一个 0 到 9 之间的数字。
每条从根节点到叶节点的路径都代表一个数字：

例如，从根节点到叶节点的路径 1 -> 2 -> 3 表示数字 123 。
计算从根节点到叶节点生成的 所有数字之和 。

叶节点 是指没有子节点的节点。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650950428974.png" alt="1650950428974" style="zoom:80%;" />

![1650950483266](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650950483266.png)

### 415

字符串相加

给定两个字符串形式的非负整数 num1 和num2 ，计算它们的和并同样以字符串形式返回。

你不能使用任何內建的用于处理大整数的库（比如 BigInteger）， 也不能直接将输入的字符串转换为整数形式。

![1650950528753](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650950528753.png)

![1650951824350](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650951824350.png)

### 2

两数相加

给你两个 非空 的链表，表示两个非负的整数。它们每位数字都是按照 逆序 的方式存储的，并且每个节点只能存储 一位 数字。

请你将两个数相加，并以相同形式返回一个表示和的链表。

你可以假设除了数字 0 之外，这两个数都不会以 0 开头。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650953248104.png" alt="1650953248104" style="zoom:80%;" />

![1650953276740](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650953276740.png)

### 206

反转链表

> 给你单链表的头节点 `head` ，请你反转链表，并返回反转后的链表。 

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650953413572.png" alt="1650953413572" style="zoom:80%;" />

解法1：

![1650953819386](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650953819386.png)

解法2：

**迭代**

假设链表为1→2→3→∅，我们想要把它改成∅←1←2←3。

在遍历链表时，将当前节点的next 指针改为指向前一个节点。由于节点没有引用其前一个节点，因此必须事先存储其前一个节点。在更改引用之前，还需要存储后一个节点。最后返回新的头引用。

![1650953915112](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650953915112.png)

**递归**

![1650954290989](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650954290989.png)

![1650954318616](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650954318616.png)

![1655613153443](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655613153443.png)

### 208

实现前缀树

Trie（发音类似 "try"）或者说 前缀树 是一种树形数据结构，用于高效地存储和检索字符串数据集中的键。这一数据结构有相当多的应用情景，例如自动补完和拼写检查。

请你实现 Trie 类：

1. Trie() 初始化前缀树对象。

2. void insert(String word) 向前缀树中插入字符串 word 。

3. boolean search(String word) 如果字符串 word 在前缀树中，返回 true（即，在检索之前已经插入）；否则，返回 false 。

4. boolean startsWith(String prefix) 如果之前已经插入的字符串 word 的前缀之一为 prefix ，返回 true ；否则，返回 false

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656740087642.png" alt="1656740087642" style="zoom:50%;" />

![1656740121826](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656740121826.png)



### 121

买卖股票的最佳时机

> 给定一个数组 prices ，它的第 i 个元素 prices[i] 表示一支给定股票第 i 天的价格。
>
> 你只能选择 某一天 买入这只股票，并选择在 未来的某一个不同的日子 卖出该股票。设计一个算法来计算你所能获取的最大利润。
>
> 返回你可以从这笔交易中获取的最大利润。如果你不能获取任何利润，返回 0 。
>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650954491305.png" alt="1650954491305" style="zoom:80%;" />

![1650955703083](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650955703083.png)

![1650955732024](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650955732024.png)

### 46

全排列

> 给定一个不含重复数字的数组 `nums` ，返回其 *所有可能的全排列* 。你可以 **按任意顺序** 返回答案。 

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650955799023.png" alt="1650955799023" style="zoom:80%;" />

回溯算法：

![1650957401465](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650957401465.png)

![1650956930997](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650956930997.png)

交换法：

![1650957422741](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650957422741.png)

![1650958010037](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650958010037.png)

### 200

岛屿数量

> 给你一个由 '1'（陆地）和 '0'（水）组成的的二维网格，请你计算网格中岛屿的数量。
>
> 岛屿总是被水包围，并且每座岛屿只能由水平方向和/或竖直方向上相邻的陆地连接形成。
>
> 此外，你可以假设该网格的四条边均被水包围。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650958081672.png" alt="1650958081672" style="zoom:80%;" />

![1650961847425](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650961847425.png)

### 15

三数之和

> 给你一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？请你找出所有和为 0 且不重复的三元组。
>
> 注意：答案中不可以包含重复的三元组。

![1650962853726](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650962853726.png)

![1650962881604](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650962881604.png)

### 5

最长回文串

> 给你一个字符串 `s`，找到 `s` 中最长的回文子串。 

![1650963006191](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650963006191.png)

> **<font color='hotpink'>中心扩散法</font>**
>
> 中心扩散法怎么去找回文串？
>
> 从每一个位置出发，向两边扩散即可。遇到不是回文的时候结束。
>
> 1. 首先往左寻找与当前位置相同的字符，直到遇到不相等为止。
> 2. 然后往右寻找与当前位置相同的字符，直到遇到不相等为止。
> 3. 最后左右双向扩散，直到左和右不相等。如下例子 + 过程讲解

![1650965143998](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650965143998.png)

### 695

岛屿的最大面积

> 给你一个大小为 m x n 的二进制矩阵 grid 。
>
> 岛屿 是由一些相邻的 1 (代表土地) 构成的组合，这里的「相邻」要求两个 1 必须在 水平或者竖直的四个方向上 相邻。你可以假设 grid 的四个边缘都被 0（代表水）包围着。
>
> 岛屿的面积是岛上值为 1 的单元格的数目。
>
> 计算并返回 grid 中最大的岛屿面积。如果没有岛屿，则返回面积为 0 。
>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650965417716.png" alt="1650965417716" style="zoom:67%;" />

![1650967100844](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650967100844.png)

### 



### 102

二叉树的层次遍历

> 给你二叉树的根节点 `root` ，返回其节点值的 **层序遍历** 。 （即逐层地，从左到右访问所有节点）。 

![1650972226618](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650972226618.png)

### 279

完全平方数

给你一个整数 n ，返回 和为 n 的完全平方数的最少数量 。

完全平方数 是一个整数，其值等于另一个整数的平方；换句话说，其值等于一个整数自乘的积。例如，1、4、9 和 16 都是完全平方数，而 3 和 11 不是。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656341737219.png" alt="1656341737219" style="zoom:50%;" />

![1656341784047](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656341784047.png)

### 120

三角形的最小路径



### 209

长度最小的子数组

> 给定一个含有 n 个正整数的数组和一个正整数 target 。
>
> 找出该数组中满足其和 ≥ target 的长度最小的 连续子数组 [numsl, numsl+1, ..., numsr-1, numsr] ，并返回其长度。如果不存在符合条件的子数组，返回 0 。
>

![1650972889333](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650972889333.png)

滑动窗口：

![1650973660491](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650973660491.png)

### 54

螺旋矩阵

> 给你一个 `m` 行 `n` 列的矩阵 `matrix` ，请按照 **顺时针螺旋顺序** ，返回矩阵中的所有元素。 

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650973737488.png" alt="1650973737488" style="zoom:67%;" />

 ![image.png](https://pic.leetcode-cn.com/42ee2ec6854ee79ac2b7c91259d2ad5db70522668d11fc691e9e14426918a666-image.png) 

四个边界

> 1. 上边界 top : 0
> 2. 下边界 bottom : matrix.length - 1
> 3. 左边界 left : 0
> 4. 右边界 right : matrix[0].length - 1

top < bottom && left < right 是循环的条件

无法构成“环”了，就退出循环，退出时可能是这 3 种情况之一：

> 1. top == bottom && left < right —— 剩一行
> 2. top < bottom && left == right —— 剩一列
> 3. top == bottom && left == right —— 剩一项（也算 一行/列）

处理剩下的单行或单列

> 因为是按顺时针推入结果数组的，所以
>
> - 剩下的一行，**从左至右** 依次推入结果数组
> - 剩下的一列，**从上至下** 依次推入结果数组

![1650975309572](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650975309572.png)

 ![image.png](https://pic.leetcode-cn.com/1636269896-zaGsTl-image.png) 

![1650975918614](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650975918614.png)

### 剑指22

链表中倒数第K个节点

> 输入一个链表，输出该链表中倒数第k个节点。为了符合大多数人的习惯，本题从1开始计数，即链表的尾节点是倒数第1个节点。
>
> 例如，一个链表有 6 个节点，从头节点开始，它们的值依次是 1、2、3、4、5、6。这个链表的倒数第 3 个节点是值为 4 的节点。
>

![1650976018108](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650976018108.png)

![1650976499849](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650976499849.png)

快慢指针法

![1655610718869](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655610718869.png)

### 42

接雨水

> 给定 `n` 个非负整数表示每个宽度为 `1` 的柱子的高度图，计算按此排列的柱子，下雨之后能接多少雨水。 

![1650976571997](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650976571997.png)

**动态规划**

![1650978914358](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650978914358.png)

![1655828282099](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655828282099.png)

### 155

最小栈

> 设计一个支持 push ，pop ，top 操作，并能在常数时间内检索到最小元素的栈。
>
> 实现 MinStack 类:
>
> - MinStack() 初始化堆栈对象。
> - void push(int val) 将元素val推入堆栈。
> - void pop() 删除堆栈顶部的元素。
> - int top() 获取堆栈顶部的元素。
> - int getMin() 获取堆栈中的最小元素。

![1650979701538](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650979701538.png)

![1650979727540](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650979727540.png)

### 146

LRU缓存机制

> 请你设计并实现一个满足  LRU (最近最少使用) 缓存 约束的数据结构。
>
> 实现 LRUCache 类：
>
> 1. LRUCache(int capacity) 以 正整数 作为容量 capacity 初始化 LRU 缓存
> 2. int get(int key) 如果关键字 key 存在于缓存中，则返回关键字的值，否则返回 -1 。
> 3. void put(int key, int value) 如果关键字 key 已经存在，则变更其数据值 value ；如果不存在，则向缓存中插入该组 key-value 。如果插入操作导致关键字数量超过 capacity ，则应该 逐出 最久未使用的关键字。
>
> 函数 get 和 put 必须以 O(1) 的平均时间复杂度运行。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650979833203.png" alt="1650979833203" style="zoom:50%;" />

![1650980284124](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650980284124.png)

### 230

二叉搜索树中第K小的元素

> 给定一个二叉搜索树的根节点 `root` ，和一个整数 `k` ，请你设计一个算法查找其中第 `k` 个最小元素（从 1 开始计数）。 

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650980355160.png" alt="1650980355160" style="zoom:50%;" />

自己解答：

![1651021331487](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651021331487.png)

优化解答：

> 因为是二叉搜索树，中序遍历后是一个有序数组，就可以得到第K小的元素。
>
> 所以中序遍历二叉搜索树，最后返回第`k-1`个元素。
>
> 具体有**递归版**和**非递归版**。

**递归版**

![1651021600963](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651021600963.png)

**非递归版**

![1651021874622](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651021874622.png)

### 234

回文链表

 给你一个单链表的头节点 `head` ，请你判断该链表是否为回文链表。如果是，返回 `true` ；否则，返回 `false` 。 

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656740764164.png" alt="1656740764164" style="zoom:50%;" />

![1656740788811](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656740788811.png)



### 剑指62

圆圈中最后剩下的数字

> 0,1,···,n-1这n个数字排成一个圆圈，从数字0开始，每次从这个圆圈里删除第m个数字（删除后从下一个数字开始计数）。求出这个圆圈里剩下的最后一个数字。
>
> 例如，0、1、2、3、4这5个数字组成一个圆圈，从数字0开始每次删除第3个数字，则删除的前4个数字依次是2、0、4、1，因此最后剩下的数字是3。出处。
>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651023014269.png" alt="1651023014269" style="zoom:80%;" />

> - n个人编号0,1,2,...,n-1，每数m次删掉一个人
> - 假设有函数f(n)表示n个人最终剩下人的编号
> - n个人删掉1个人后可以看做n-1的状态，不过有自己的编号。
> - n个人删掉的第一个人的编号是(m-1)%n，那么n个人时删掉第一个人的后面那个人(m-1+1)%n一定是n-1个人时候编号为0的那个人，即n个人时的编号m%n（这个编号是对于n个人来考虑的），n-1个人时编号为i的人就是n个人时(m+i)%n
> - 所以f(n)=(m+f(n-1))%n
> - f(1)=0，因为1个人时只有一个编号0。

 ![image.png](https://pic.leetcode-cn.com/1644049215-Hibleu-image.png) 

 ![image.png](https://pic.leetcode-cn.com/1644049077-YwnKvY-image.png) 

![1651025490609](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651025490609.png)

#### **约瑟夫环**

> N个人围成一圈，第一个人从1开始报数，报M的将被杀掉，下一个人接着从1开始报。如此反复，最后剩下一个，求最后的胜利者。 

下面这个例子是`N=8 m=3`的例子

我们定义`F(n,m)`表示最后剩下那个人的索引号，因此我们只关系最后剩下来这个人的索引号的变化情况即可。

 ![约瑟夫环1.png](https://pic.leetcode-cn.com/d7768194055df1c3d3f6b503468704606134231de62b4ea4b9bdeda7c58232f4-%E7%BA%A6%E7%91%9F%E5%A4%AB%E7%8E%AF1.png) 

从8个人开始，每次杀掉一个人，去掉被杀的人，然后把杀掉那个人之后的第一个人作为开头重新编号

> - 第一次C被杀掉，人数变成7，D作为开头，（最终活下来的G的编号从6变成3）
> - 第二次F被杀掉，人数变成6，G作为开头，（最终活下来的G的编号从3变成0）
> - 第三次A被杀掉，人数变成5，B作为开头，（最终活下来的G的编号从0变成3）

**<font color='hotpink'>以此类推，当只剩一个人时，他的编号必定为0！（重点！）</font>**

**最终活着的人编号的反推**

现在我们知道了G的索引号的变化过程，那么我们反推一下

从N = 7 到N = 8 的过程

如何才能将N = 7 的排列变回到N = 8 呢？

我们先把被杀掉的C补充回来，然后右移m个人，发现溢出了，再把溢出的补充在最前面

神奇了 经过这个操作就恢复了N = 8 的排列了！

 ![约瑟夫环2.png](https://pic.leetcode-cn.com/68509352d82d4a19678ed67a5bde338f86c7d0da730e3a69546f6fa61fb0063c-%E7%BA%A6%E7%91%9F%E5%A4%AB%E7%8E%AF2.png) 

**<font color='hotpink'>因此我们可以推出递推公式f(8,3) = [f(7, 3) + 3] \% 8</font>**

进行推广泛化，即f(n,m) = [f(n-1, m) + m] \% n

**递推公式的导出**

再把n=1这个最初的情况加上，就得到递推公式

![1651026112940](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651026112940.png)

![1651026146525](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651026146525.png)

### 103

二叉树的锯齿形层次遍历

> 给你二叉树的根节点 `root` ，返回其节点值的 **锯齿形层序遍历** 。（即先从左往右，再从右往左进行下一层遍历，以此类推，层与层之间交替进行）。 

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651026356513.png" alt="1651026356513" style="zoom:50%;" />

![1651027230289](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651027230289.png)

flag判断是从左向右还是从右向左

**官方解答：**

![1651027717209](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651027717209.png)

### 合并二叉树

![1655607149392](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655607149392.png)

合并过程必须从根节点开始

![1655607193916](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655607193916.png)

### 21

合并两个有序链表

> 将两个升序链表合并为一个新的 **升序** 链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。  

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651027852218.png" alt="1651027852218" style="zoom:50%;" />

![1651028508163](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651028508163.png)

方法2：

![1651028555529](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651028555529.png)

### 429

N叉树的层次遍历

> 给定一个 N 叉树，返回其节点值的*层序遍历*。（即从左到右，逐层遍历）。
>
> 树的序列化输入是用层序遍历，每组子节点都由 null 值分隔（参见示例）。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651029114249.png" alt="1651029114249" style="zoom:50%;" />

**广度优先搜索**

![1651029770334](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651029770334.png)

### 93

复原IP地址

> 有效 IP 地址 正好由四个整数（每个整数位于 0 到 255 之间组成，且不能含有前导 0），整数之间用 '.' 分隔。
>
> 例如："0.1.2.201" 和 "192.168.1.1" 是 有效 IP 地址，但是 "0.011.255.245"、"192.168.1.312" 和 "192.168@1.1" 是 无效 IP 地址。
>
> 给定一个只包含数字的字符串 s ，用以表示一个 IP 地址，返回所有可能的有效 IP 地址，这些地址可以通过在 s 中插入 '.' 来形成。你 不能 重新排序或删除 s 中的任何数字。你可以按 任何 顺序返回答案。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651035130968.png" alt="1651035130968" style="zoom:50%;" />

![1651035503248](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651035503248.png)

 ![image.png](https://pic.leetcode-cn.com/5276b1631cb1fc47d8d88dd021f1302213291bf05bfdfdc6209370ce9034be83-image.png) 

 ![image.png](https://pic.leetcode-cn.com/e3e3a6dac1ecb79da18740f7968a5eedaa80d5a0e0e45463c7096f663748e0fa-image.png) 

### 75

颜色分类

给定一个包含红色、白色和蓝色、共 n 个元素的数组 nums ，原地对它们进行排序，使得相同颜色的元素相邻，并按照红色、白色、蓝色顺序排列。

我们使用整数 0、 1 和 2 分别表示红色、白色和蓝色。

必须在不使用库的sort函数的情况下解决这个问题。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656224619087.png" alt="1656224619087" style="zoom:50%;" />

![1656224663453](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656224663453.png)

### 128

最长连续序列

给定一个未排序的整数数组 nums ，找出数字连续的最长序列（不要求序列元素在原数组中连续）的长度。

请你设计并实现时间复杂度为 O(n) 的算法解决此问题。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656604160358.png" alt="1656604160358" style="zoom:50%;" />

![1656604614299](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656604614299.png)

### 124

二叉树中的最大路径和

路径 被定义为一条从树中任意节点出发，沿父节点-子节点连接，达到任意节点的序列。同一个节点在一条路径序列中 至多出现一次 。该路径 至少包含一个 节点，且不一定经过根节点。

路径和 是路径中各节点值的总和。

给你一个二叉树的根节点 root ，返回其 最大路径和 。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656604652745.png" alt="1656604652745" style="zoom:50%;" />

![1656604680664](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656604680664.png)

### 136

只出现一次的数字

给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。

说明：

你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？

**异或：^**

**a^a=0**

**a^0=a**

**(a^b) ^ c = a ^ (b^c)**

![1656606258740](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656606258740.png)



### 78

子集

#### 回溯

> 给你一个整数数组 `nums` ，数组中的元素 **互不相同** 。返回该数组所有可能的子集（幂集）。
>
> 解集 **不能** 包含重复的子集。你可以按 **任意顺序** 返回解集。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651037571467.png" alt="1651037571467" style="zoom:50%;" />

 ![image.png](https://pic.leetcode-cn.com/1600557223-hvNyjD-image.png) 

![1651037844426](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651037844426.png)

### 48

旋转图像

> 给定一个 n × n 的二维矩阵 matrix 表示一个图像。请你将图像顺时针旋转 90 度。
>
> 你必须在 原地 旋转图像，这意味着你需要直接修改输入的二维矩阵。请不要 使用另一个矩阵来旋转图像。
>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651038000415.png" alt="1651038000415" style="zoom:50%;" />

![1656213391346](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656213391346.png)

### 49

字母异位词分组

给你一个字符串数组，请你将 字母异位词 组合在一起。可以按任意顺序返回结果列表。

字母异位词 是由重新排列源单词的字母得到的一个新单词，所有源单词中的字母通常恰好只用一次。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656213591958.png" alt="1656213591958" style="zoom:50%;" />

![1656213619267](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656213619267.png)



### 283

移动零

> 给定一个数组 `nums`，编写一个函数将所有 `0` 移动到数组的末尾，同时保持非零元素的相对顺序。
>
> **请注意** ，必须在不复制数组的情况下原地对数组进行操作。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651039871722.png" alt="1651039871722" style="zoom:50%;" />

![1651040558321](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651040558321.png)

![1651040722016](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651040722016.png)

### 287

寻找重复数

给定一个包含 n + 1 个整数的数组 nums ，其数字都在 [1, n] 范围内（包括 1 和 n），可知至少存在一个重复的整数。

假设 nums 只有 一个重复的整数 ，返回 这个重复的数 。

你设计的解决方案必须 不修改 数组 nums 且只用常量级 O(1) 的额外空间。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656747353056.png" alt="1656747353056" style="zoom:50%;" />

![1656747401578](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656747401578.png)



### 31

下一个排列

> 整数数组的一个 排列  就是将其所有成员以序列或线性顺序排列。
>
> 例如，arr = [1,2,3] ，以下这些都可以视作 arr 的排列：[1,2,3]、[1,3,2]、[3,1,2]、[2,3,1] 。
> 整数数组的 下一个排列 是指其整数的下一个字典序更大的排列。更正式地，如果数组的所有排列根据其字典顺序从小到大排列在一个容器中，那么数组的 下一个排列 就是在这个有序容器中排在它后面的那个排列。如果不存在下一个更大的排列，那么这个数组必须重排为字典序最小的排列（即，其元素按升序排列）。
>
> 例如，arr = [1,2,3] 的下一个排列是 [1,3,2] 。
> 类似地，arr = [2,3,1] 的下一个排列是 [3,1,2] 。
> 而 arr = [3,2,1] 的下一个排列是 [1,2,3] ，因为 [3,2,1] 不存在一个字典序更大的排列。
> 给你一个整数数组 nums ，找出 nums 的下一个排列。
>
> 必须 原地 修改，只允许使用额外常数空间。
>

![1651043680097](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651043680097.png)

### 236

二叉树的最近公共祖先

> 给定一个二叉树, 找到该树中两个指定节点的最近公共祖先。
>
> 百度百科中最近公共祖先的定义为：“对于有根树 T 的两个节点 p、q，最近公共祖先表示为一个节点 x，满足 x 是 p、q 的祖先且 x 的深度尽可能大（一个节点也可以是它自己的祖先）。”
>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651043907965.png" alt="1651043907965" style="zoom:50%;" />

![1656741004908](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656741004908.png)

### 238

除自身以外数组的乘积

给你一个整数数组 nums，返回 数组 answer ，其中 answer[i] 等于 nums 中除 nums[i] 之外其余各元素的乘积 

题目数据 保证 数组 nums之中任意元素的全部前缀元素和后缀的乘积都在  32 位 整数范围内。

请不要使用除法，且在 O(n) 时间复杂度内完成此题。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656742487934.png" alt="1656742487934" style="zoom:50%;" />

![1656742524992](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656742524992.png)

### 239

滑动窗口的最大值

给你一个整数数组 nums，有一个大小为 k 的滑动窗口从数组的最左侧移动到数组的最右侧。你只可以看到在滑动窗口内的 k 个数字。滑动窗口每次只向右移动一位。

返回 滑动窗口中的最大值 。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656743381155.png" alt="1656743381155" style="zoom:67%;" />

![1656743416044](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656743416044.png)

### 240

搜索二维矩阵

编写一个高效的算法来搜索 m x n 矩阵 matrix 中的一个目标值 target 。该矩阵具有以下特性：

每行的元素从左到右升序排列。
每列的元素从上到下升序排列。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656743952627.png" alt="1656743952627" style="zoom:50%;" />

从右上角开始寻找：

![1656743988646](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656743988646.png)



### 补充4

手撕快速排序



### 56

合并区间

> 以数组 intervals 表示若干个区间的集合，其中单个区间为 intervals[i] = [starti, endi] 。请你合并所有重叠的区间，并返回 一个不重叠的区间数组，该数组需恰好覆盖输入中的所有区间 。
>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651146597908.png" alt="1651146597908" style="zoom:50%;" />

![1651148095607](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651148095607.png)

### 113

路径总和2

> 给你二叉树的根节点 root 和一个整数目标和 targetSum ，找出所有 从根节点到叶子节点 路径总和等于给定目标和的路径。
>
> 叶子节点 是指没有子节点的节点。
>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651148196780.png" alt="1651148196780" style="zoom:50%;" />

#### 回溯算法

![1651151281714](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651151281714.png)

### 322

零钱兑换

> 给你一个整数数组 coins ，表示不同面额的硬币；以及一个整数 amount ，表示总金额。
>
> 计算并返回可以凑成总金额所需的 最少的硬币个数 。如果没有任何一种硬币组合能组成总金额，返回 -1 。
>
> 你可以认为每种硬币的数量是无限的。
>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651151364445.png" alt="1651151364445" style="zoom:50%;" />

![1651152723959](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651152723959.png)

### 53

最大子数组和

给你一个整数数组 `nums` ，请你找出一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。

**子数组** 是数组中的一个连续部分。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656213716076.png" alt="1656213716076" style="zoom:50%;" />

![1656214345300](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656214345300.png)

![1656214372084](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656214372084.png)

### 11 

**盛最多水的容器**

给定一个长度为 n 的整数数组 height 。有 n 条垂线，第 i 条线的两个端点是 (i, 0) 和 (i, height[i]) 。

找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水。

返回容器可以储存的最大水量。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655737274572.png" alt="1655737274572" style="zoom:40%;" />

![1655737335311](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655737335311.png)

### 17

**电话号码的字母组合**

给定一个仅包含数字 2-9 的字符串，返回所有它能表示的字母组合。答案可以按 任意顺序 返回。

给出数字到字母的映射如下（与电话按键相同）。注意 1 不对应任何字母。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655739371430.png" alt="1655739371430" style="zoom:50%;" />

![1655739500874](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655739500874.png)

### 19

删除链表的倒数第n个结点

给你一个链表，删除链表的倒数第 `n` 个结点，并且返回链表的头结点。 

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655740980688.png" alt="1655740980688" style="zoom:50%;" />

![1655741043418](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655741043418.png)

### 22

括号生成

 数字 `n` 代表生成括号的对数，请你设计一个函数，用于能够生成所有可能的并且 **有效的** 括号组合。 

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655820896229.png" alt="1655820896229" style="zoom:50%;" />

![1655821009172](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655821009172.png)

### 23

合并k个升序链表

给你一个链表数组，每个链表都已经按升序排列。

请你将所有链表合并到一个升序链表中，返回合并后的链表。

 <img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655821085376.png" alt="1655821085376" style="zoom:50%; margin:0 auto;" />

![1655821168413](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655821168413.png)

### 32

最长的有效括号

给你一个只包含 `'('` 和 `')'` 的字符串，找出最长有效（格式正确且连续）括号子串的长度。 

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655823796941.png" alt="1655823796941" style="zoom:50%;" />

![1655823820615](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655823820615.png)

### 34

在排序数组中查找元素的第一个和最后一个位置

给你一个按照非递减顺序排列的整数数组 nums，和一个目标值 target。请你找出给定目标值在数组中的开始位置和结束位置。

如果数组中不存在目标值 target，返回 [-1, -1]。

你必须设计并实现时间复杂度为 O(log n) 的算法解决此问题。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655825406794.png" alt="1655825406794" style="zoom:50%;" />

![1655825431374](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655825431374.png)

### 39

组合总和

给你一个 无重复元素 的整数数组 candidates 和一个目标整数 target ，找出 candidates 中可以使数字和为目标数 target 的 所有 不同组合 ，并以列表形式返回。你可以按 任意顺序 返回这些组合。

candidates 中的 同一个 数字可以 无限制重复被选取 。如果至少一个数字的被选数量不同，则两种组合是不同的。 

对于给定的输入，保证和为 target 的不同组合数少于 150 个。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655825958335.png" alt="1655825958335" style="zoom:50%;" />

![1655825984601](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1655825984601.png)



# 动态规划合集

**<font color='hotpink'>动态规划五部曲：</font>**

> 1. 确定dp数组及其下标的含义
> 2. 确定递推公式
> 3. dp数组如何初始化
> 4. 确定遍历顺序
> 5. 举例推导dp数组

## 基础题目

### 509

斐波那契数

> 斐波那契数 （通常用 F(n) 表示）形成的序列称为 斐波那契数列 。该数列由 0 和 1 开始，后面的每一项数字都是前面两项数字的和。也就是：
>
> - F(0) = 0，F(1) = 1
> - F(n) = F(n - 1) + F(n - 2)，其中 n > 1
>
> 给定 n ，请计算 F(n) 。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651028688004.png" alt="1651028688004" style="zoom:50%;" />

![1651029011596](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651029011596.png)

![1651211298352](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651211298352.png)

### 70

爬楼梯

> 假设你正在爬楼梯。需要 `n` 阶你才能到达楼顶。
>
> 每次你可以爬 `1` 或 `2` 个台阶。你有多少种不同的方法可以爬到楼顶呢？

![1650972578236](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650972578236.png)

![1650972599808](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650972599808.png)

动态规划：

本问题其实常规解法可以分成多个子问题，爬第n阶楼梯的方法数量，等于 2 部分之和

> 1. 爬上 n-1n−1 阶楼梯的方法数量。因为再爬1阶就能到第n阶
> 2. 爬上 n-2n−2 阶楼梯的方法数量，因为再爬2阶就能到第n阶

所以我们得到公式 dp[n] = dp[n-1] + dp[n-2]

同时需要初始化 dp[0]=1和 dp[1]=1

![1650972800424](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650972800424.png)

斐波那契方法：

![1650972689251](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650972689251.png)

![1650972714535](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1650972714535.png)

### 746

使用最小花费爬楼梯

> 给你一个整数数组 cost ，其中 cost[i] 是从楼梯第 i 个台阶向上爬需要支付的费用。一旦你支付此费用，即可选择向上爬一个或者两个台阶。
>
> 你可以选择从下标为 0 或下标为 1 的台阶开始爬楼梯。
>
> 请你计算并返回达到楼梯顶部的最低花费。
>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651211546132.png" alt="1651211546132" style="zoom:50%;" />

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651213176212.png" alt="1651213176212" style="zoom:50%;" />

![1651213387064](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651213387064.png)

![1651214203777](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651214203777.png)

### 62

不同路径

> 一个机器人位于一个 m x n 网格的左上角 （起始点在下图中标记为 “Start” ）。
>
> 机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为 “Finish” ）。
>
> 问总共有多少条不同的路径？,                   

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651021962138.png" alt="1651021962138" style="zoom:50%;" />

**<font color='red'>动态规划思想：</font>**

> 思路与算法
>
> 我们用 f(i, j) 表示从左上角走到 (i, j) 的路径数量，其中 ii 和 jj 的范围分别是 [0, m)和 [0, n)
>
> **<font color='red'>由于我们每一步只能从向下或者向右移动一步，因此要想走到 (i, j)，如果向下走一步，那么会从(i−1,j) 走过来；如果向右走一步，那么会从 (i,j−1) 走过来。因此我们可以写出动态规划转移方程：</font>**
>
> **<font color='hotpink'>f(i, j) = f(i-1, j) + f(i, j-1)</font>**
>
> 需要注意的是，如果 i=0，那么 f(i-1,j) 并不是一个满足要求的状态，我们需要忽略这一项；同理，如果 j=0，那么 f(i,j−1) 并不是一个满足要求的状态，我们需要忽略这一项。
>
> 初始条件为 f(0,0)=1，即从左上角走到左上角有一种方法。
>
> 最终的答案即为 f(m-1,n-1)。
>
> **细节**
>
> 为了方便代码编写，我们可以将所有的 f(0, j) 以及 f(i, 0) 都设置为边界条件，它们的值均为 11。

![4](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651022566098.png)

### 63

不同路径2

> 一个机器人位于一个 m x n 网格的左上角 （起始点在下图中标记为 “Start” ）。
>
> 机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为 “Finish”）。
>
> 现在考虑网格中有障碍物。那么从左上角到右下角将会有多少条不同的路径？
>
> 网格中的障碍物和空位置分别用 1 和 0 来表示。
>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651214251306.png" alt="1651214251306" style="zoom:33%;" />

![1651216865871](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651216865871.png)

### 64

最小路径和

给定一个包含非负整数的 `*m* x *n*` 网格 `grid` ，请找出一条从左上角到右下角的路径，使得路径上的数字总和为最小。

**说明：**每次只能向下或者向右移动一步。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656220140206.png" alt="1656220140206" style="zoom:50%;" />

![1656220167344](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656220167344.png)

### 72

编辑距离

给你两个单词 word1 和 word2， 请返回将 word1 转换成 word2 所使用的最少操作数  。

你可以对一个单词进行如下三种操作：

插入一个字符
删除一个字符
替换一个字符

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656223027826.png" alt="1656223027826" style="zoom:50%;" />

![1656223052069](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656223052069.png)



### 343

整数拆分

> 给定一个正整数 `n` ，将其拆分为 `k` 个 **正整数** 的和（ `k >= 2` ），并使这些整数的乘积最大化。
>
> 返回 你可以获得的最大乘积 。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651217046813.png" alt="1651217046813" style="zoom:50%;" />

![1651217903673](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651217903673.png)

### 96

不同的二叉搜索树

>  给你一个整数 `n` ，求恰由 `n` 个节点组成且节点值从 `1` 到 `n` 互不相同的 **二叉搜索树** 有多少种？返回满足题意的二叉搜索树的种数。 

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651229540458.png" alt="1651229540458" style="zoom:50%;" />

![1651229512431](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651229512431.png)

### 139

单词拆分

给你一个字符串 s 和一个字符串列表 wordDict 作为字典。请你判断是否可以利用字典中出现的单词拼接出 s 。

注意：不要求字典中出现的单词全部都使用，并且字典中的单词可以重复使用。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656727532055.png" alt="1656727532055" style="zoom:50%;" />

**利用动态规划解决问题：**

![1656727610582](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656727610582.png)

### 148

 给你链表的头结点 `head` ，请将其按 **升序** 排列并返回 **排序后的链表** 。 

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656731628388.png" alt="1656731628388" style="zoom:50%;" />

（1）二分法

![1656731670866](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656731670866.png)

自己的方法：

![1656731745740](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656731745740.png)

### 152

乘积最大子数组

给你一个整数数组 nums ，请你找出数组中乘积最大的非空连续子数组（该子数组中至少包含一个数字），并返回该子数组所对应的乘积。

测试用例的答案是一个 32-位 整数。

子数组 是数组的连续子序列。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656732583524.png" alt="1656732583524" style="zoom:50%;" />

![1656732607341](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656732607341.png)



## 背包问题

![1651229714495](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651229714495.png)

**完全背包的物品数量是无限的**

### 01背包

有N件物品和⼀个最多能背重量为W 的背包。第i件物品的重量是weight[i]，得到的价值是value[i] 。**每件物品只能用⼀次，**求解将哪些物品装⼊背包里物品价值总和最大。

![1651229900677](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651229900677.png)

### 二维dp数组-01背包

1. 确定dp数组以及下标的含义

   `dp[i][j]`<font color='hotpink'>表示从下标为[0-i]的物品里任意取，放进容量为j的背包，价值总和最大为多少</font>

   <img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651230029901.png" alt="1651230029901" style="zoom:50%;" />

2. 确定递推公式

   - 由dp[i-1]推出，即背包容量为j，里面不放物品i的最大价值，此时`dp[i][j]`就是`dp[i-1][j]`
   - 由`dp[i-1][j-weight[i]]`推出，`dp[i-1][j-weight[i]]`为背包容量为j-weight[i]的时候不放物品i的最大价值，那么`dp[i-1][j-weight[i]]+value[i]`，就是背包放物品i得到的最大价值
   - 状态转移方程
   - **递推公式：`dp[i][j] = Math.max(dp[i-1][j],dp[i-1][j-weight[i]]+value[i])`;**

3. dp数组如何初始化

   若背包容量j为0，则`dp[i][0]`，无论是选取哪些物品，背包价值总和一定为0；

   <img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651230606085.png" alt="1651230606085" style="zoom:50%;" />

   由状态转移方程`dp[i][j] = Math.max(dp[i-1][j],dp[i-1][j-weight[i]]+value[i])`可以看出i是由i-1推导出来的，那么i=0时，一定要初始化

   `dp[0][j]`，即i=0，存放编号0的物品的时候，各个容量的背包所能存放的最大价值。

   当j<weight[0]的时候，`dp[0][j]`应该为0，因为背包的容量小于了物品的重量。

   当j>weight[0]时，`dp[0][j]`应该是value[0]，因为背包容量大于物品0的重量。

   初始化如下：

   ![1651231015755](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651231015755.png)

   <img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651231029712.png" alt="1651231029712" style="zoom:50%;" />

   其他坐标统一初始化为0：

   <img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651231091936.png" alt="1651231091936" style="zoom:50%;" />

   **完整初始化代码为：**

   ![1651231219679](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651231219679.png)

4. 确定遍历顺序

   两个遍历的维度：物品和背包重量

   <img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651231264211.png" alt="1651231264211" style="zoom:50%;" />

   可以先遍历物品然后遍历背包重量：

   ![1651231469187](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651231469187.png)

5. 举例推导dp数组

   <img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651231524576.png" alt="1651231524576" style="zoom:50%;" />

    最终结果就是d`p[2][4]` 

![1651232593691](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651232593691.png)

### 滚动数组

就是把二维dp降为一维dp

![1651229900677](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651229900677.png)

#### 一维dp数组-滚动数组

在使用二维数组时，背包问题递推公式为：

`dp[i][j] = Math.max(dp[i-1][j],dp[i-1][j-weight[i]]+value[i])`

**如果把dp[i-1]那一层拷贝到dp[i]上，表达式为：**

`dp[i][j] = Math.max(dp[i][j],dp[i][j-weight[i]]+value[i])`

这样不如直接使用一维数组了：

`dp[j]`也可以理解为滚动数组

**<font color='hotpink'>滚动数组的由来：需要满足的条件是上一层可以重复利用，直接拷贝到当前层。</font>**

1. 确定dp数组的定义

   在一维dp数组中，dp[j]表示：**容量为j的背包，所背的物品价值最大可以为dp[j]**

2. 一维dp数组的递推公式

   dp[j]为容量为j的背包所背的最大价值

   dp[j]可以通过dp[j-weight[i]]推导出来：

   - dp[j-weight[i]]表示容量为j-weight[i]的背包所背的最大价值
   - dp[j-weight[i]]+value[i]表示容量为j-物品i重量的背包加上物品i的价值（也就是容量为j的背包，放入了物品i之后的价值，即：dp[j]）
   - 此时，dp[j]有两个选择，要选择更大的那一个
   - 递推公式为：`dp[j] = Math.max(dp[j],dp[j-weight[i]]+value[i])`

3. 一维数组如何初始化

   dp[j]表示容量为j的背包，所背的物品价值可以最大为dp[j]

   dp[0]=0;

   其余下标初始化为0；

4. 一维dp数组遍历顺序

   ![1651233595771](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651233595771.png)

   **为什么二维数组背包容量从小到大，一维数组背包容量从大到小呢**

   为了保证物品i只被放入一次

   <img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651233723136.png" alt="1651233723136" style="zoom:80%;" />

5. 举例推导dp数组

   <img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651233851230.png" alt="1651233851230" style="zoom:50%;" />

![1651234039745](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651234039745.png)

### 416

分割等和子集

> 给你一个 **只包含正整数** 的 **非空** 数组 `nums` 。请你判断是否可以将这个数组分割成两个子集，使得两个子集的元素和相等。 

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651234374017.png" alt="1651234374017" style="zoom:50%;" />

1. 背包的体积为sum/2
2. 背包要放入的商品（集合里的元素）重量为元素的数值，价值也为元素的数值
3. 背包如何正好装满，说明找到了总和为sum/2的子集
4. 背包中每一个元素是不可重复放入的

动规五部曲

1. 确定dp数组以及下标的含义

   dp[i]表示背包总容量为i，最大可以凑成i的子集总和为dp[i]

2. 确定递推公式

   物品i的重量为nums[i]，价值也为nums[i]

   `dp[i] = Math.max(dp[i],dp[i-nums[i]]+nums[i])`

3. dp数组如何初始化

   dp[0] = 0;

   非0下标元素初始化为0

   **题目说到：每个数组中的元素不会超过100，数组的大小不会超过200，所以总和不会大于20000，背包最大只需要其中一半，10001**

   ![1651234887341](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651234887341.png)

4. 确定遍历顺序

   <font color='hotpink'>如果使用一维dp数组，物品的for循环放在外层，遍历背包的for循环放在内层，且内层for循环倒序，保证一个物品只放了一次</font>

   ![1651235082400](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651235082400.png)

5. 举例推导dp数组

   dp[i]的数值一定是小于等于i的。

   **如果dp[i] == i 说明，集合中的子集总和正好可以凑成总和i** 

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651235196924.png" alt="1651235196924" style="zoom:50%;" />

![1651235905406](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651235905406.png)

# 

# 

### 剑指09

用两个栈实现队列

> 用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 appendTail 和 deleteHead ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，deleteHead 操作返回 -1 )
>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651236133602.png" alt="1651236133602" style="zoom:50%;" />

![1651236554588](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651236554588.png)

### 160

相交链表

> 给你两个单链表的头节点 headA 和 headB ，请你找出并返回两个单链表相交的起始节点。如果两个链表不存在相交节点，返回 null 。
>
> 图示两个链表在节点 c1 开始相交：
>
> 题目数据 **保证** 整个链式结构中不存在环。
>
> **注意**，函数返回结果后，链表必须 **保持其原始结构** 。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651236625579.png" alt="1651236625579" style="zoom:50%;" />

方法一：

![1651236975213](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651236975213.png)

方法二：

Set()

![1651237247995](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651237247995.png)

### 169

多数元素

给定一个大小为 n 的数组 nums ，返回其中的多数元素。多数元素是指在数组中出现次数 大于 ⌊ n/2 ⌋ 的元素。

你可以假设数组是非空的，并且给定的数组总是存在多数元素。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656736254799.png" alt="1656736254799" style="zoom:50%;" />

![1656736300057](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656736300057.png)

![1656736572430](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656736572430.png)



### 221

最大正方形

>  在一个由 `'0'` 和 `'1'` 组成的二维矩阵内，找到只包含 `'1'` 的最大正方形，并返回其面积。 

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651237314072.png" alt="1651237314072" style="zoom:50%;" />

> 定义状态：
> `dp[i][j] `表示以 `matrix[i][j] `为右下角顶点的最大正方形的边长。
>
> 状态转移方程：
>
> `dp[i][j] `= min(`dp[i-1][j]`, `dp[i][j-1]`, `dp[i-1][j-1]`) + 1;
>
> 由于` dp[i][j] `表示以 `matrix[i][j] `为右下角顶点的最大正方形的边长，所以我们要尽可能地向左向上扩展它的边长。
>
> 而扩展它边长的条件为：它内部格子全为 1。
>
> 这时候就可以复用前面计算过的状态了。
>
> - 以它上边一个格子为右下角顶点的最大边长(`dp[i-1][j]`)，
> - 以它左边一个格子为右下角顶点的最大边长(`dp[i][j-1]`)，
> - 以它左上一个格子为右下角顶点的最大边长(`dp[i-1][j-1]`)。
>
> 取它们的最小值。
>
> 初始状态：
>
> 初始 `dp[i][j]` 均为 0。

![1656740557632](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656740557632.png)



### 14

最长公共前缀

> 编写一个函数来查找字符串数组中的最长公共前缀。
>
> 如果不存在公共前缀，返回空字符串 `""`。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651239154680.png" alt="1651239154680" style="zoom:50%;" />

![1651239901073](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651239901073.png)

### 101

对称二叉树

>  给你一个二叉树的根节点 `root` ， 检查它是否轴对称。 

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651240035703.png" alt="1651240035703" style="zoom:50%;" />

定义一个check函数，通过两个指针分别指向左子树和右子树检查是否相等：

![1651280767350](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651280767350.png)

### 198

打家劫舍

你是一个专业的小偷，计划偷窃沿街的房屋。每间房内都藏有一定的现金，影响你偷窃的唯一制约因素就是相邻的房屋装有相互连通的防盗系统，如果两间相邻的房屋在同一晚上被小偷闯入，系统会自动报警。

给定一个代表每个房屋存放金额的非负整数数组，计算你 不触动警报装置的情况下 ，一夜之内能够偷窃到的最高金额。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656737850588.png" alt="1656737850588" style="zoom:67%;" />

**动态规划**

![1656737933643](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1656737933643.png)



### 199

二叉树的右视图

> 给定一个二叉树的 **根节点** `root`，想象自己站在它的右侧，按照从顶部到底部的顺序，返回从右侧所能看到的节点值。 

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651280889771.png" alt="1651280889771" style="zoom:40%;" />

**1.广度优先搜索**

利用广度优先搜索进行层次遍历

记录下每一层最后一个元素

![1651285159870](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651285159870.png)

### 637

二叉树的层平均值

> 给定一个非空二叉树的根节点 `root` , 以数组的形式返回每一层节点的平均值。与实际答案相差 `10-5` 以内的答案可以被接受。 

![1651286205571](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651286205571.png)

### 429

N叉树的层序遍历

> 给定一个 N 叉树，返回其节点值的层序遍历。（即从左到右，逐层遍历）。
>
> 树的序列化输入是用层序遍历，每组子节点都由 null 值分隔（参见示例）。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651286277355.png" alt="1651286277355" style="zoom:50%;" />

![1651286326608](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651286326608.png)

### 515

在每个树行中找最大值

> 给定一棵二叉树的根节点 `root` ，请找出该二叉树中每一层的最大值。 

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651286377585.png" alt="1651286377585" style="zoom:50%;" />

![1651286637249](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651286637249.png)

### 116

填充每个节点的下一个右侧节点指针

> 给定一个 完美二叉树 ，其所有叶子节点都在同一层，每个父节点都有两个子节点。二叉树定义如下：
>
> ![1651286738846](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651286738846.png)
>
> 填充它的每个 next 指针，让这个指针指向其下一个右侧节点。如果找不到下一个右侧节点，则将 next 指针设置为 NULL。
>
> 初始状态下，所有 next 指针都被设置为 NULL。
>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651286769294.png" alt="1651286769294" style="zoom:50%;" />

![1651287442654](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651287442654.png)

### 117

填充每个节点的下一个右侧节点指针Ⅱ

> 给定一个二叉树
>
> ![1651287529451](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651287529451.png)
>
> 填充它的每个 next 指针，让这个指针指向其下一个右侧节点。如果找不到下一个右侧节点，则将 next 指针设置为 NULL。
>
> 初始状态下，所有 next 指针都被设置为 NULL。
>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651287922723.png" alt="1651287922723" style="zoom:50%;" />

![1651288000408](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651288000408.png)

### 559

N叉树的最大深度

> 给定一个 N 叉树，找到其最大深度。
>
> 最大深度是指从根节点到最远叶子节点的最长路径上的节点总数。
>
> N 叉树输入按层序遍历序列化表示，每组子节点由空值分隔（请参见示例）。
>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651289643311.png" alt="1651289643311" style="zoom:50%;" />

**BFS**

![1651290272741](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651290272741.png)

**DFS**

![1651290541279](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651290541279.png)

### 222

完全二叉树的节点个数

> 给你一棵 完全二叉树 的根节点 root ，求出该树的节点个数。
>
> 完全二叉树 的定义如下：在完全二叉树中，除了最底层节点可能没填满外，其余每层节点数都达到最大值，并且最下面一层的节点都集中在该层最左边的若干位置。若最底层为第 h 层，则该层包含 1~ 2h 个节点。
>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651290806965.png" alt="1651290806965" style="zoom:50%;" />

**BFS**

![1651291017787](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651291017787.png)

**DFS**

![1651295120059](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651295120059.png)

### 43

字符串相乘

> 给定两个以字符串形式表示的非负整数 num1 和 num2，返回 num1 和 num2 的乘积，它们的乘积也表示为字符串形式。
>
> 注意：不能使用任何内置的 BigInteger 库或直接将输入转换为整数。
>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651295178660.png" alt="1651295178660" style="zoom:50%;" />

> 解题思路：
>
> 1. 0乘以任何数 = 0
>
> 2. 两数相乘，乘积的长度一定 <= 两数长度之和
>
> 3. 被乘数的一位 与 乘数的每一位相乘，乘积不会超过 9 x 9 = 81，不超过两位
>
> 4. 每次只考虑两位，乘积 与 个位 
>
>    -  相加个位保留余数
>
>    -  十位保留取整，取整直接舍弃小数点，用0 |效率，高于parseInt
>
> 5. while循环，删除多余的0

![1651296200519](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651296200519.png)

### 25

（困难）k个一组翻转链表

> 给你链表的头节点 head ，每 k 个节点一组进行翻转，请你返回修改后的链表。
>
> k 是一个正整数，它的值小于或等于链表的长度。如果节点总数不是 k 的整数倍，那么请将最后剩余的节点保持原有顺序。
>
> 你不能只是单纯的改变节点内部的值，而是需要实际进行节点交换。
>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651298071179.png" alt="1651298071179" style="zoom:50%;" />

![1651746481240](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651746481240.png)

### 394

字符串解码

> 给定一个经过编码的字符串，返回它解码后的字符串。
>
> 编码规则为: k[encoded_string]，表示其中方括号内部的 encoded_string 正好重复 k 次。注意 k 保证为正整数。
>
> 你可以认为输入字符串总是有效的；输入字符串中没有额外的空格，且输入的方括号总是符合格式要求的。
>
> 此外，你可以认为原始数据不包含数字，所有的数字只表示重复的次数 k ，例如不会出现像 3a 或 2[4] 的输入。
>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651746533717.png" alt="1651746533717" style="zoom:45%;" />

![1651747278779](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651747278779.png)

## 子序列问题

![1651752718966](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651752718966.png)

### 300

最长递增子序列

> 给你一个整数数组 nums ，找到其中最长严格递增子序列的长度。
>
> 子序列 是由数组派生而来的序列，删除（或不删除）数组中的元素而不改变其余元素的顺序。例如，[3,6,2,7] 是数组 [0,3,1,6,2,2,7] 的子序列。
>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651748105111.png" alt="1651748105111" style="zoom:50%;" />

> dp[i]可以由dp[j]推导出来(j<i)
>
> 1. dp[i]的定义
>
>    **dp[i]表示i之前包括i的最长递增子序列**
>
> 2. 状态转移方程
>
>     **位置i的最长升序子序列等于j从0到i-1各个位置的最长升序子序列 + 1 的最大值。** 
>
>    **if(nums[i]>nums[j]){ dp[i]=Math.max(dp[i],dp[j]+1);}**
>
> 3. dp[i]初始化
>
>    dp[i]至少为1
>
> 4. 确定遍历顺序
>
>    ![1651753164394](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651753164394.png)
>
> 5. 举例推导dp数组
>
>    <img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651753119864.png" alt="1651753119864" style="zoom:40%;" />

![1651752586898](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651752586898.png)

![1651753336328](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651753336328.png)

### 674

最长连续递增序列

> 给定一个未经排序的整数数组，找到最长且 连续递增的子序列，并返回该序列的长度。
>
> 连续递增的子序列 可以由两个下标 l 和 r（l < r）确定，如果对于每个 l <= i < r，都有 nums[i] < nums[i + 1] ，那么子序列 [nums[l], nums[l + 1], ..., nums[r - 1], nums[r]] 就是连续递增子序列。
>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651753649660.png" alt="1651753649660" style="zoom:50%;" />

**动态规划**

![1651753679207](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651753679207.png)

### 718

最长重复子数组

> 给两个整数数组 `nums1` 和 `nums2` ，返回 两个数组中 **公共的** 、长度最长的子数组的长度*。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651753757628.png" alt="1651753757628" style="zoom:50%;" />

> 动态规划
>
> 1. 确定dp数组及其下标的含义
>
>     `dp[i][j]` ：以下标i - 1为结尾的A，和以下标j - 1为结尾的B，最⻓重复⼦数组长度为`dp[i][j]`。 
>
> 2. 确定递推公式
>
>    根据`dp[i][j]`的定义，dp[i][j]的状态只能由`dp[i - 1][j - 1]`推导出来。 即当A[i - 1] 和B[j - 1]相等的时候，`dp[i][j] = dp[i - 1][j - 1] + 1`; 
>
> 3. 初始化
>
> 4. 确定遍历顺序
>
>    ![1651755154758](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651755154758.png)
>
> 5. 递推举例

![1651755175886](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651755175886.png)

### 1143

最长公共子序列

> 给定两个字符串 text1 和 text2，返回这两个字符串的最长 公共子序列 的长度。如果不存在 公共子序列 ，返回 0 。
>
> 一个字符串的 子序列 是指这样一个新的字符串：它是由原字符串在不改变字符的相对顺序的情况下删除某些字符（也可以不删除任何字符）后组成的新字符串。
>
> 例如，"ace" 是 "abcde" 的子序列，但 "aec" 不是 "abcde" 的子序列。
> 两个字符串的 公共子序列 是这两个字符串所共同拥有的子序列。

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651756313796.png" alt="1651756313796" style="zoom:50%;" />

> `dp[i][j]`：长度为[0, i - 1]的字符串text1与长度为[0, j - 1]的字符串text2的最长公共子序列为`dp[i][j] ` 
>
> 1. text1[i - 1] 与 text2[j - 1]相同
>    - 如果text1[i - 1] 与 text2[j - 1]相同，那么找到了一个公共元素，所以`dp[i][j] = dp[i - 1][j - 1] + 1`; 
>
> 2. text1[i - 1] 与 text2[j - 1]不相同 
>    - 如果text1[i - 1] 与 text2[j - 1]不相同，那就看看text1[0, i - 2]与text2[0, j - 1]的最长公共子序列 和 text1[0, i - 1]与text2[0, j - 2]的最长公共子序列，取最大的。 即：`dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])`; 

![1651756275310](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651756275310.png)

### 1035

不相交的线

> 在两条独立的水平线上按给定的顺序写下 nums1 和 nums2 中的整数。
>
> 现在，可以绘制一些连接两个数字 nums1[i] 和 nums2[j] 的直线，这些直线需要同时满足满足：
>
>  nums1[i] == nums2[j]
> 且绘制的直线不与任何其他连线（非水平线）相交。
> 请注意，连线即使在端点也不能相交：每个数字只能属于一条连线。
>
> 以这种方法绘制线条，并返回可以绘制的最大连线数。
>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651756650098.png" alt="1651756650098" style="zoom:50%;" />

> 1. 确定dp数组以及下标的含义
>
>    `dp[i][j]:长度为[0,i-1]的字符串nums1和长度为[0,j-1]的字符串nums2的最长公共子序列为dp[i][j]`

![1651800767096](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651800767096.png)

### 392

判断子序列

> 给定字符串 s 和 t ，判断 s 是否为 t 的子序列。
>
> 字符串的一个子序列是原始字符串删除一些（也可以不删除）字符而不改变剩余字符相对位置形成的新字符串。（例如，"ace"是"abcde"的一个子序列，而"aec"不是）。
>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651800883672.png" alt="1651800883672" style="zoom:50%;" />

> `dp[i][j]表示以下标i-1为结尾的字符串s和以下标j-1为结尾的字符串t，相同子序列的长度为dp[i][j]`
>
> **注意：是在t中匹配子序列s**
>
> 1. if (s[i - 1] == t[j - 1])，那么`dp[i][j] = dp[i - 1][j - 1] + 1`;因为找到了⼀个相同的字符，相同子序列长度自然要在`dp[i-1][j-1]`的基础上加1
> 2.  if (s[i - 1] != t[j - 1])，此时相当于t要删除元素，t如果把当前元素t[j - 1]删除，那么`dp[i][j] `的数值就是 看 s[i - 1]与 t[j - 2]的比较结果了，即：`dp[i][j] = dp[i][j - 1]`; 

![1651802053664](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651802053664.png)

### 115

不同的子序列

> 给定一个字符串 s 和一个字符串 t ，计算在 s 的子序列中 t 出现的个数。
>
> 字符串的一个 子序列 是指，通过删除一些（也可以不删除）字符且不干扰剩余字符相对位置所组成的新字符串。（例如，"ACE" 是 "ABCDE" 的一个子序列，而 "AEC" 不是）
>
> 题目数据保证答案符合 32 位带符号整数范围。
>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651802146140.png" alt="1651802146140" style="zoom:50%;" />

> `dp[i][j]:以i-1为结尾的s子序列中出现以j-1为结尾的t的个数为dp[i][j]`
>
> 1. 当s[i - 1] 与 t[j - 1]相等时，`dp[i`][j]可以有两部分组成。 一部分是用s[i - 1]来匹配，那么个数为`dp[i - 1][j - 1]`。 ⼀部分是不用s[i - 1]来匹配，个数为`dp[i - 1][j]`。 这⾥可能有同学不明白了，为什么还要考虑 不用s[i - 1]来匹配，都相同了指定要匹配啊。 例如： s：bagg 和 t：bag ，s[3] 和 t[2]是相同的，但是字符串s也可以不⽤s[3]来匹配，即⽤ s[0]s[1]s[2]组成的bag。 当然也可以⽤s[3]来匹配，即：s[0]s[1]s[3]组成的bag。 所以当s[i - 1] 与 t[j - 1]相等时，`dp[i][j] = dp[i - 1][j - 1] + dp[i - 1][j];`
>
> 2. 当s[i - 1] 与 t[j - 1]不相等时，`dp[i][j]`只有⼀部分组成，不用s[i - 1]来匹配，即：`dp[i - 1][j] `所以递推公式为：`dp[i][j] = dp[i - 1][j];`  

![1651803135647](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651803135647.png)

### 105

从前序与中序遍历序列构造二叉树

> 给定两个整数数组 preorder 和 inorder ，其中 preorder 是二叉树的先序遍历， inorder 是同一棵树的中序遍历，请构造二叉树并返回其根节点。
>

<img src="C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651803304319.png" alt="1651803304319" style="zoom:50%;" />

![1651804784715](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651804784715.png)

### 8

字符串转换整数

> 请你来实现一个 myAtoi(string s) 函数，使其能将字符串转换成一个 32 位有符号整数（类似 C/C++ 中的 atoi 函数）。
>
> 函数 myAtoi(string s) 的算法如下：
>
> 1. 读入字符串并丢弃无用的前导空格
> 2. 检查下一个字符（假设还未到字符末尾）为正还是负号，读取该字符（如果有）。 确定最终结果是负数还是正数。 如果两者都不存在，则假定结果为正。
> 3. 读入下一个字符，直到到达下一个非数字字符或到达输入的结尾。字符串的其余部分将被忽略。
> 4. 将前面步骤读入的这些数字转换为整数（即，"123" -> 123， "0032" -> 32）。如果没有读入数字，则整数为 0 。必要时更改符号（从步骤 2 开始）。
> 5. 如果整数数超过 32 位有符号整数范围 [−231,  231 − 1] ，需要截断这个整数，使其保持在这个范围内。具体来说，小于 −231 的整数应该被固定为 −231 ，大于 231 − 1 的整数应该被固定为 231 − 1 。
> 6. 返回整数作为最终结果。

![1653054284357](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1653054284357.png)

不适用parseInt()的写法：

**正则解析法**

![1653054440167](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1653054440167.png)

