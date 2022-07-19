# JS模块化

当项目功能越来越多，代码量便也会越来越多，后期的维护难度会增大，此时在JS方面就会考虑使用模块化规范去管理。

* 模块化的理解

* 什么是模块?

  * 将一个复杂的程序依据一定的规则(规范)封装成几个块(文件), 并进行组合在一起
  * 块的内部数据/实现是私有的, 只是向外部暴露一些接口(方法)与外部其它模块通信

* 一个模块的组成

  * 数据--->内部的属性
  * 操作数据的行为--->内部的函数

* 模块化

  * 编码时是按照模块一个一个编码的, 整个项目就是一个模块化的项目

* 模块化的进化过程

  * 全局function模式 : 

    * 编码: 全局变量/函数
    * 问题: 污染全局命名空间, 容易引起命名冲突/数据不安全

  * namespace模式 : 

    * 编码: 将数据/行为封装到对象中
    * 解决: 命名冲突(减少了全局变量)
    * 问题: 数据不安全(外部可以直接修改模块内部的数据)

  * IIFE模式/增强

    * IIFE : 立即调用函数表达式--->匿名函数自调用

    * 编码: 将数据和行为封装到一个函数内部, 通过给window添加属性来向外暴露接口

    * 引入依赖: 通过函数形参来引入依赖模块

      ```
      (function(window, module2){
        var data = 'atguigu.com'
        function foo() {
           module2.xxx()
           console.log('foo()'+data)
        }
        function bar() {
           console.log('bar()'+data)
        }
        
        window.module = {foo}
      })(window, module2)
      ```

* 模块化规范

  * CommonJS

    * Node.js : 服务器端

    * Browserify : 浏览器端    也称为js的打包工具

    * 基本语法:

      * 定义暴露模块 : exports

        ```
        exports.xxx = value
        module.exports = value
        ```

        引入模块 : require

        ```
        var module = require('模块名/模块相对路径')
        ```

    * 引入模块发生在什么时候?

      * Node : 运行时, 动态同步引入
      * Browserify : 在运行前对模块进行编译/转译/打包的处理(已经将依赖的模块包含进来了), 
            运行的是打包生成的js, 运行时不存在需要再从远程引入依赖模块

  * AMD : 浏览器端

    * require.js

    * 基本语法

      * 定义暴露模块: define([依赖模块名], function(){return 模块对象})

      * 引入模块: require(['模块1', '模块2', '模块3'], function(m1, m2){//使用模块对象})

      * 配置: 

        ```
        require.config({
          //基本路径
          baseUrl : 'js/',
          //标识名称与路径的映射
          paths : {
            '模块1' : 'modules/模块1',
            '模块2' : 'modules/模块2',
            'angular' : 'libs/angular',
            'angular-messages' : 'libs/angular-messages'
          },
          //非AMD的模块
          shim : {
            'angular' : {
                exports : 'angular'
            },
            'angular-messages' : {
                exports : 'angular-messages',
                deps : ['angular']
            }
          }
        })
        ```

  * CMD : 浏览器端

    * sea.js

    * 基本语法

      * 定义暴露模块: 

        ```
        define(function(require, module, exports){
          通过require引入依赖模块
          通过module/exports来暴露模块
          exports.xxx = value
        })
        ```

      * 使用模块seajs.use(['模块1', '模块2'])

  * ES6

    * ES6内置了模块化的实现

    * 基本语法

      * 定义暴露模块 : export

        * 暴露一个对象: 

          ```
          export default 对象
          ```

        * 暴露多个: 

          ```
          export var xxx = value1
          export let yyy = value2
          
          var xxx = value1
          let yyy = value2
          export {xxx, yyy}
          ```

      * 引入使用模块 : import

        * default模块:

          ```
          import xxx  from '模块路径/模块名'
          ```

        * 其它模块

          ```
          import {xxx, yyy} from '模块路径/模块名'
          import * as module1 from '模块路径/模块名'
          
          ```

    * 问题: 所有浏览器还不能直接识别ES6模块化的语法  

    * 解决:

      * 使用Babel将ES6--->ES5(使用了CommonJS) ----浏览器还不能直接支行
      * 使用Browserify--->打包处理----浏览器可以运行

    







# 



# 



# 



## 模块化进化史教程

1. 全局function模式

   * module1.js

     ![1651713013012](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651713013012.png)

   * module2.js

     ![1651713102713](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651713102713.png)

   * test1.html

     ![1651713120845](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651713120845.png)

    * 说明:

      * 全局函数模式: 将不同的功能封装成不同的全局函数
      * 问题: Global被污染了, 很容易引起命名冲突

2. namespace模式

   * module1.js

     ![1651713156103](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651713156103.png)

   * module2.js

     ![1651713172197](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651713172197.png)

   * test2.html

     ![1651713189023](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651713189023.png)

   * 说明

     * namespace模式: 简单对象封装
     * 作用: 减少了全局变量
     * 问题: 不安全

3. IIFE模式

   * module3.js

     ![1651713225541](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651713225541.png)

   * test3.html

     ![1651713245642](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651713245642.png)

   * 说明:

     * IIFE模式: 匿名函数自调用(闭包)
     * IIFE : immediately-invoked function expression(立即调用函数表达式)
     * 作用: 数据是私有的, 外部只能通过暴露的方法操作
     * 问题: 如果当前这个模块依赖另一个模块怎么办?

4. IIFE模式增强

   * 引入jquery到项目中

   * module4.js

     ![1651713267925](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651713267925.png)

   * test4.html

     ![1651713283902](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651713283902.png)

   * 说明

     * IIFE模式增强 : 引入依赖
     * 这就是现代模块实现的基石

5. 页面加载多个js的问题

   * 页面:

     ![1651713297840](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651713297840.png)

   * 说明

     * 一个页面需要引入多个js文件
     * 问题:
       * 请求过多
       * 依赖模糊
       * 难以维护
     * 这些问题可以通过现代模块化编码和项目构建来解决

## CommonJS

### 规范

#### 说明

1. 每一个文件都可以当作一个模块
2. 在服务器端：模块的加载是运行时同步加载的
3. 在浏览器端：模块需要提前编译打包处理

#### 基本语法

##### 1、暴露模块

![1651713697461](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651713697461.png)

**module.exports或者exports.xxx暴露的都是exports对象。**

##### 2、引入模块

![1651713766125](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651713766125.png)

- 第三方模块：xxx为模块名
- 自定义模块：xxx为模块文件路径

#### 实现

##### 1、服务端实现

Node.js

http://nodejs.cn/

##### 2、浏览器端实现

Browserify

http://browserify.org/

也称之为CommonJS的浏览器端打包工具

##### 3、区别Node与Browserify

### Node.js模块化教程

1. 下载安装node.js

2. 创建项目结构

   ![1651713346901](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651713346901.png)

   快速创建package.json，打开根目录文件的终端，执行npm init，快速生成package.json文件

   ![1651714356779](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651714356779.png)

   **此处设置包名时，不能存在大写**

3. 下载第三方模块

   **uniq包向外暴露的是一个function**

   ![1651713374076](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651713374076.png)

4. 模块化编码

   **module.exports或者exports.xxx暴露的都是exports对象。**

   * module1.js

     ![1651713392315](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651713392315.png)

   * module2.js

     ![1651713406508](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651713406508.png)

   * module3.js

     ![1651713421339](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651713421339.png)

   * app.js 

     ![1651713461336](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651713461336.png)

5. 通过node运行app.js

   * 命令: node app.js
   * 工具: 右键-->运行

## AMD

### 规范

#### 说明

Asynchronous Module Definition（异步模块定义）

https://github.com/amdjs/amdjs-api/wiki/AMD

专门用于浏览器端，模块的加载是异步的

#### 语法

##### 定义暴露模块

![1651715968827](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651715968827.png)

#### 引入使用模块

![1651716024937](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651716024937.png)

### require.js使用教程

1. 下载require.js, 并引入

   * 官网: http://www.requirejs.cn/
   * github : https://github.com/requirejs/requirejs
   * 将require.js导入项目: js/libs/require.js 

2. 创建项目结构

   ![1651716083426](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651716083426.png)

3. 定义require.js的模块代码

   * dataService.js

     ![1651716098101](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651716098101.png)

   * alerter.js

     ![1651716112524](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651716112524.png)

4. 应用主(入口)js: main.js

   ![1651716126710](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651716126710.png)

5. 页面使用模块:

   ![1651716174322](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651716174322.png)

6. 使用第三方基于require.js的框架(jquery)

   * 将jquery的库文件导入到项目: 

     * js/libs/jquery-1.10.1.js

   * 在main.js中配置jquery路径

     ![1651716191858](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651716191858.png)

   * 在alerter.js中使用jquery

     ![1651716207191](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651716207191.png)

------------------------------------------------------------------------

7. 使用第三方不基于require.js的框架(angular/angular-messages)

   * 将angular.js和angular-messages.js导入项目

     * js/libs/angular.js
     * js/libs/angular-messages.js

   * 在main.js中配置

     ![1651716250353](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651716250353.png)

   * 页面:

     ![1651716274021](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651716274021.png)

## ES6-Babel-Browserify使用教程

1. 定义package.json文件

   ![1651716379036](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651716379036.png)

2. 安装babel-cli, babel-preset-es2015和browserify

   ![1651716403534](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651716403534.png)

3. 定义.babelrc文件

   ![1651716415775](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651716415775.png)

4. 编码

   * js/src/module1.js

     ![1651716429695](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651716429695.png)

   * js/src/module2.js

     ![1651716445040](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651716445040.png)

   * js/src/module3.js

     ![1651716457463](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651716457463.png)

   * js/src/app.js

     ![1651716470980](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651716470980.png)

5. 编译

   * 使用Babel将ES6编译为ES5代码(但包含CommonJS语法) : babel js/src -d js/lib
   * 使用Browserify编译js : browserify js/lib/app.js -o js/lib/bundle.js

6. 页面中引入测试

   ![1651716484971](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651716484971.png)

7. 引入第三方模块(jQuery)

   下载jQuery模块: 

     * npm install jquery@1 --save

    在app.js中引入并使用

   ![1651716530040](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651716530040.png)