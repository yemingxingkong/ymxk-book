<!-- GFM-TOC -->
# Vue

* [一、环境配置](#一环境配置)
  * [NVM](#NVM)
  * [Node.js](#Node.js)
  * [NPM](#NPM)
  * [Yarn](#Yarn)
* [二、模块基础](#二模块基础)
* [三、Webpack](#二Webpack)
  * [Webpack概念](#Webpack概念)
* [四、JavaScript基础](#三JavaScript基础)
  * [JavaScript概念](#JavaScript概念)
  * [JavaScript引用类型](#JavaScript引用类型)
* [五、文件系统](#四文件系统)
  * [分区与文件系统](#分区与文件系统)
  * [组成](#组成)
  * [文件读取](#文件读取)
  * [磁盘碎片](#磁盘碎片)
  * [block](#block)
  * [inode](#inode)
  * [目录](#目录)
  * [日志](#日志)
  * [挂载](#挂载)
  * [目录配置](#目录配置)
* [六、压缩与打包](#六压缩与打包)
  * [压缩文件名](#压缩文件名)
  * [压缩指令](#压缩指令)
  * [打包](#打包)
* [七、Bash](#七bash)
  * [特性](#特性)
  * [变量操作](#变量操作)
  * [指令搜索顺序](#指令搜索顺序)
  * [数据流重定向](#数据流重定向)
* [八、管道指令](#八管道指令)
  * [提取指令](#提取指令)
  * [排序指令](#排序指令)
  * [双向输出重定向](#双向输出重定向)
  * [字符转换指令](#字符转换指令)
  * [分区指令](#分区指令)
* [九、正则表达式](#九正则表达式)
  * [grep](#grep)
  * [printf](#printf)
  * [awk](#awk)
* [十、进程管理](#十进程管理)
  * [查看进程](#查看进程)
  * [进程状态](#进程状态)
  * [SIGCHLD](#sigchld)
  * [wait()](#wait)
  * [waitpid()](#waitpid)
  * [孤儿进程](#孤儿进程)
  * [僵尸进程](#僵尸进程)
* [参考资料](#参考资料)
<!-- GFM-TOC -->

# 一、环境配置

## NVM

### 1. NVM安装

Linux下的安装
[nvm](https://github.com/nvm-sh/nvm#install--update-script)

windows下的安装
[nvm-windows](https://github.com/coreybutler/nvm-windows)
nvm 的windows下载地址：[nvm-windows](https://github.com/coreybutler/nvm-windows/releases) , 选择第二个nvm-setup.zip，这样安装方便些。
将下载的文件进行解压：nvm-setup.exe，单击开始安装，直接点击下一步解可以，当然我们需要注意一下两个界面：
设置nvm路径(相当于setting.txt中的root:)：
设置nvm路径(相当于setting.txt中的path:)：
这样我们就在windows下面的nvm安装完成了！

安装完成以后需要进行配置
/**
*node下载源
*/
nvm node_mirror https://npm.taobao.org/mirrors/node/
/**
*npm下载源
*/
nvm npm_mirror  https://npm.taobao.org/mirrors/npm/

### 2. NVM命令

windows下nvm的命令([]中的参数可有可无)：
|              命令              |                                             意义                                             |
| :----------------------------: | :------------------------------------------------------------------------------------------: |
|            nvm arch            |                             查看当前系统的位数和当前nodejs的位数                             |
| nvm install < version > [arch] |                安装制定版本的node 并且可以指定平台 version 版本号  arch 平台                 |
|      nvm list [available]      |                                                                                              |
|           - nvm list           |                                      查看已经安装的版本                                      |
|      - nvm list installed      |                                      查看已经安装的版本                                      |
|      - nvm list available      |                                    查看网络可以安装的版本                                    |
|             nvm on             |                                      打开nodejs版本控制                                      |
|            nvm off             |                                      关闭nodejs版本控制                                      |
|        nvm proxy [url]         |                                        查看和设置代理                                        |
|     nvm node_mirror [url]      |      设置或查看setting.txt中的node_mirror，如果不设置的默认是 https://nodejs.org/dist/       |
|      nvm npm_mirror [url]      | 设置或查看setting.txt中的npm_mirror,如果不设置的话默认：https://github.com/npm/npm/archive/. |
|   nvm uninstall < version >    |                                        卸载制定的版本                                        |
|    nvm use [version] [arch]    |                                   切换制定的node版本和位数                                   |
|        nvm root [path]         |                                      设置和查看root路径                                      |
|          nvm version           |                                        查看当前的版本                                        |
下面是安装和使切换nodejs的几个简单的命令使用：
nvm install 10.16.0 64-bit
nvm use 10.16.0
nvm list //查看以己经安装的。

## Node.js

### 1. Node安装

nvm install 10.16.0 64-bit

## NPM

### 1. NPM查看安装信息

查看所有全局安装的模块：npm list -g
查看某个模块的版本号：npm list grunt

### 2. package.json

package.json 位于模块的目录下，用于定义包的属性。接下来让我们来看下 express 包的 package.json 文件，位于 node_modules/express/package.json 内容

```json
{
  "name": "express",
  "version": "4.13.3",
  "description": "Fast, unopinionated, minimalist web framework",
  "homepage": "http://expressjs.com/",
  "author": {
    "name": "TJ Holowaychuk",
    "email": "tj@vision-media.ca"
  },
  "contributors": [
    {
      "name": "Aaron Heckmann",
      "email": "aaron.heckmann+github@gmail.com"
    },
    {
      "name": "Ciaran Jessup",
      "email": "ciaranj@gmail.com"
    }
  ],
  "license": "MIT",
  "repository": {
    "type": "git",
    "url": "git+https://github.com/strongloop/express.git"
  },
  "homepage": "http://expressjs.com/",
  "keywords": [
    "express",
    "framework"
  ],
  "dependencies": {
    "accepts": "~1.2.12",
    "array-flatten": "1.1.1"
  }
}
```

Package.json 属性说明
name - 包名。
version - 包的版本号。
description - 包的描述。
homepage - 包的官网 url 。
author - 包的作者姓名。
contributors - 包的其他贡献者姓名。
dependencies - 依赖包列表。如果依赖包没有安装，npm 会自动将依赖包安装在 node_module 目录下。
repository - 包代码存放的地方的类型，可以是 git 或 svn，git 可在 Github 上。
main - main 字段指定了程序的主入口文件，require('moduleName') 就会加载这个文件。这个字段的默认值是模块根目录下面的 index.js。
keywords - 关键字

### 3.使用淘宝 NPM 镜像

$ npm install -g cnpm --registry=https://registry.npm.taobao.org

## Yarn

### 1.yarn命令

安装yarn
npm install -g yarn

下载依赖
yarn install

启动
yarn run serve

编译项目
yarn run build

整理和修复文件
yarn run lint

# 二、模块基础

# 三、Webpack

## Webpack概念

### 1. webpack是什么

1.webpack构建工具
2.自带模块化(commonjs规范)
3.编译：es6 -> es5 , jsx -> es5 , ts(typescript) ->  js
4.gulp所做的事情，webpack都可以做到
5.自带服务器，服务器也是基于Node（webpack-dev-server）
6.那些环境经常使用到webpack：react 、 vue
7.webpack版本：1.x 、2.x 、3.x 、4.x版本

### 2. 安装webpack3.x

1.安装全局webpack
  npm install -g webpack@3.x
2.项目初始化package.json
  npm init -y
3.安装项目依赖的webpack
  npm install -D webpack@3.x
4.项目根目录创建两个文件夹src和dist
  src:源码文件
  dist：编译之后的文件
5.编写代码
  app.js:document.write("hello webpack");
6.执行webpack
  webpack 路径/入口文件  路径/出口文件
  webpack src/app.js    dist/bundle.js
7.编写代码
  hello.js：
  module.exports = function(){
    var hello = document.createElement("div");
    hello.textContent = "hello Webpack3.x";
    return hello;
  }

安装webpack4.x
1.安装全局webpack
  npm install --global webpack
  npm install --global webpack-cli
2.项目初始化package.json
  npm init -y
3.安装项目依赖的webpack
  npm install --save-dev webpack
  npm install --save-dev webpack@3.x

### 3. 生成webpack.config.js文件

配置入口和出口
module.exports = {
  entry:__dirname +"/src/app.js",
  output:{
    path:__dirname + "/dist",
    filename:"bundle.js"
  }
}

### 4. webpack执行的快捷方案

在package.json文件中代替webpack的执行
"scripts": {
  "build":"webpack"
}
执行：npm run build

### 5. webpack调试

生成错误信息文件
  配置webpack.config.js文件
  添加devtool:"eval-source-map"
      devtool:
        eval
        source-map
        hidden-source-map
        inline-source-map
        eval-source-map
        cheap-source-map
        cheap-module-source-map


6.服务器
  1.全局安装服务器
    npm install -g webpack-dev-server@2.x
  2.安装项目依赖
    npm install -D webpack-dev-server@2.x
  3.运行webpack服务器
    webpack-dev-server
  4.配置服务器的快捷执行方案
    "scripts": {
      "build": "webpack",
      "dev":"webpack-dev-server"
    }
    执行：npm run dev
  5.修改服务器根路径
    "dev":"webpack-dev-server --content-base dist"
  6.热更新
    "dev":"webpack-dev-server --content-base dist --inline --hot"
  7.服务器配置
      --content-base：指定服务器运行根目录
      --inline：在线更新
      --port: 修改端口

7.module
  loaders(use)
  loader是webpack可以通过配置脚本，或者外部依赖来执行一些功能
  例如：es6 -> es5  jsx -> js  less -> css
  1.配置loaders
      1.test：一个匹配loader要做操作的文件的一个正则表达式（必须）
      2.loader(use)：loader要执行的任务的名字（必须）
      3.options:为loader提供一些外部选项配置(可选项)
  2.json格式的数据转化成js的对象
    注意：当前的json-loader只是为了测试，我们当前安装的webpack的版本3.x
          事实上，在当前版本中，已经集成了json-loader,不需要单独安装了
    1.安装json-loader
      npm install -D json-loader
    2.编写配置文件代码
      {
        test:/\.json$/,
        use:"json-loader"
      }

# 四、JavaScript基础

## VueDevtools插件的安装

github下载插件，npm包安装依赖，拖入浏览器扩展程序

具体操作：
1.下载chrome扩展插件。
  在github上下载压缩包并解压到本地，github下载地址：https://github.com/vuejs/vue-devtools
2.npm install
  下载完成后打开命令行cmd进入vue-devtools-master文件夹，
  1.npm install，安装依赖包；如果安装太慢，请参照文章末尾说明进行操作。
  2.npm run build
  npm run build 执行完，会在shells>chrome下的src文件夹里生产如上图所示的几个js文件；
  若不执行以上命令会报错，无法加载背景脚本"build/background.js"，如下图：
3.打开shells>chrome>manifest.json并把json文件里的"persistent":false改成true
4.扩展chrome插件
  1.打开chrome浏览器，打开更多工具>扩展程序；
  2.再点击加载已解压的扩展程序，然后把shells>chrome文件夹放入
5.测试安装成功
在插件的目录下执行npm run dev，这个时候我们的插件就可以运行了,打开localhost:8080可以看到插件已经安装并运行了。

### 1. 数据类型

typeof操作数：number数值，object对象或null，function函数，typeof(message)。

Undefined：undefined未定义。

Null：空对象指针。

Boolean：var messageAsBoolean=Boolean(message);，message转换为Boolean值。空字符串，0，null，NaN，undefined：返回false。

Number：浮点数值，计算精度不准。数值范围：最小值5e-324，最大值1.797693e+308，-Infinity(负无穷)，Infinity(正无穷)。NaN：Not a Number非数值，alert(isNaN("bl"));//不是数值返回true。数值转换：Number()用于任何类型，parseInt()用于字符串转换为整型，parseFloat()字符串转换为小数。

String：字符字面量，转义字符。特点，不可变，var lang="Java"; lang=lang+"Script";。转换为字符串：toString()，可传参表示进制；String()，不知转化的值null或undefined。

Object：var o=new Object();对象就是一组数据和功能的集合。

### 2. 操作符

位

|     格式      |        损失         |      透明       |
| :-----------: | :-----------------: | :-------------: |
|     位与&     |     9&15  得到9     | 1001&1111=1001  |
|  位或&#124;   | 1001&#124;1111=1111 |                 |
|    位异或^    |   1001^1111=0110    |                 |
|    位非！     |     6转化为 -7      |                 |
|    左移<<     |     9<<2 得到36     | 1001得到 100100 |
|    右移>>     |     1001得到10      |                 |
| 无符号右移>>> |                     |                 |

逻辑

!非：alert(!false);alert(!!"blue");//true。返回true：空字符串，0，null，NaN，undefined。
&&与：第一个值为false时，返回false；第一个值为对象，返回第二个值；第一个为true，第二个为对象，返回对象；有一个为null，返回null；有一个为NaN，返回NaN；有一个为undefined，返回undefined。||
&#124;&#124;或：有一个不是布尔值；第一个为对象，返回第一个值；第一个为false，返回第二个值；都为对象，返回第一个值；都为null，返回null；都为NaN，返回NaN；都为undefined，返回undefined。

相等

先转换在比较，==相等，！=不等。仅比较不转换，===等同，！==不等同。

### 3. 语句

条件执行
if
if...else
switch

循环语句
while
do   whele
for
for-in
  for(var propName in window){}

跳转语句
break，跳出当前循环
continue，跳出本次循环
return
throw

label：在代码中添加标签

with：将代码作用域设置到一个特定对象中，推荐（不使用），with(location){var qs=serch.substring(1);var hostName=hostname;}

函数
function sayHi(name,message){alert("hellow"+name+message);}
sayHi("lgc","你好")
推荐：始终有返回值或始终不要返回值

参数
参数在内部是一个数组来表示的
函数体内可通过arguments对象访问每一个元素
function sayHi(){alert("hellow"+arguments[0]+arguments[1]);}
function doAdd(num1,num2){  if(arguments.length==1){alert(num1+10);}  else if(arguments.length==2){alert(arguments[0]+num2);}  }

没有重载：后定义函数覆盖先定义函数

### 4. 作用域

引用类型

```javascript
var person=new Object();
person.name="Nicholas";
```

传递参数
  值类型
    复制值
  引用类型
    形参同样指向实参的栈

检测对象

```javascript
result=variable instanceof constructor
alert(person instanceof Object);
//变量person是Object吗
```

执行环境

全局执行环境(window对象)，函数执行环境
当执行流进入一个函数时，函数的环境就会被推入一个环境栈中。而在函数执行之后，栈将其环境弹出，把控制权返回给之前的执行环境
作用域链
活动对象
延长作用域链，try-catch中catch块，with语句。

没有块级作用域

变量声明
  var最接近的环境是函数的局部环境
查询标识符
  搜索过程从作用域链的前端开始，向上逐级查询与给定名字匹配的标识符。如果在局部环境中找到
  了该标识符，搜索过程停止，变量就绪。如果在局部环境中没有找到该变量名，则继续沿作用域链向上
  搜索。搜索过程将一直追溯到全局环境的变量对象。

垃圾收集

标记清除
引用计数
性能问题，周期性运行
管理内存，解除引用，将值设为null

## JavaScript引用类型

对象的方法
toLocaleString()
  分别调用toLocaleString()
toString()
  得到以,分割的字符串
valueOf()
检测类型
  value instanceof Array

### 1. Object

Object
对象字面量

```javascript
var person = {
  name : "Nicholas",
  age : 29 };
person.name;
person["name"];
var propertyName = "name";
alert(person[propertyName]);
```

### 2. Array

数组

```javascript
var colors = new Array();
var colors = new Array(20);
var colors = new Array("red", "blue", "green");
var colors = ["red", "blue", "green"];              colors[3] = "brown"; // 新增第四项
var names = [];
```

检测数组
value instanceof Array
ES5      if (Array.isArray(value)){}

继承方法
  toLocaleString()     取得每一项的值，调用的是每一项的 toLocale-String() 方法
  toString()      得到以,分割的字符串
  valueOf()       返回的还是数组

转换
  join()    重现了toString()

栈方法
  数组可表现像栈，LIFO后进先出。
  push()      插入(推入)可推入多项
  pop()       移除(弹出)后面项

队列方法
  FIFO先进先出
  shift()        移除第一项
  unshift();     插入，前面插入

重排序
  sort()排序      根据toString()之后升序排列

```javascript
// 代码示例
function compare(value1, value2) {
  if (value1 < value2) {
    return -1;
  } else if (value1 > value2) {
      return 1;
    } else {
      return 0;
    }
}
var values = [0, 1, 5, 10, 15];
values.sort(compare);
alert(values); // 0,1,5,10,15
// 调用示例
function compare(value1, value2){
  return value2 - value1;
}
```

  reverse()反转

操作方法
  concat();     复制当前数组，并向后面添加元素或数组，返回新数组
  slice();      返回指定位置到结束位置的所有项数组
  splice(2,1,"red","green");        在2的位置删除1项再插入两个字符串

位置方法
  indexOf(4,3);         查找4从第3项开始，返回索引
  lastIndexOf(4,4);     查找4从倒数第4项开始

迭代方法
  every();    对数组中每一项运行给定函数，若每一项返回true，则true
  filter();   该函数会返回true项组成的数组
  forEach();  没有返回值
  map();      返回每次函数调用结果组成的数组
  some();     任意一项返回true，则true

```javascript
var numbers = [1,2,3,4,5,4,3,2,1];
var everyResult = numbers.every(function(item, index, array){
  return (item > 2);
});
```

  传入这些方法中的函数会接收三个参数：数组项的值、该项在数组中的位置和数组对象本身

归并方法
  reduce()        从数组的第一项开始，逐个遍历到最后
  reduceRight()   从数组的最后一项开始，向前遍历到第一项
  函数接收 4 个参数：前一个值、当前值、项的索引和数组对象。这个函数返回的任何值都会作为第一个参数自动传给下一项。

### 3.Data

日期

```javascript
var now = new Date();
var some= new Date(Date.parse("May 25, 2004"));       // 如 6/13/2004
var allFives = new Date(Date.UTC(2005, 4, 5, 17, 55, 55));
// UTC（Coordinated Universal Time，国际协调时间）1970 年 1 月 1 日午夜（零时）开始经过的毫秒数来保存日期
```

Data.now() 方法   当前时间

继承方法
  toLocaleString()        按照与浏览器设置的地区相适应的格式        返回日期和时间
  toString()      返回带有时区信息的日期和时间
  valueOf()      返回日期的毫秒表示

格式化方法
  toDateString()    格式显示星期几、月、日和年
  toTimeString()    格式显示时、分、秒和时区
  toLocaleDateString()      特定于地区
  toLocaleTimeString()
  toUTCString()     格式完整的 UTC 日期

组件方法
  getTime()    setTime( 毫秒 )    getFullYear()   等等...

### 4.RegExp

RegExp
支持正则表达式  var expression = / pattern / flags ;
（pattern）部分可以是任何简单或复杂的正则表达式

可带有一或多个标志（flags)
  g ：表示全局（global）模式
  i ：不区分大小写（case-insensitive）模式
  m ：表示多行（multiline）模式
RegExp 实例属性
RegExp 实例方法
RegExp 构造函数属性
模式的局限性

### 5.Function

Function
函数实际上是对象，“函数是对象，函数名是指针”

```javascript
  // 声明语法
  function sum (num1, num2) {
    return num1 + num2;
  }
  // 函数表达式
  var sum = function(num1, num2){
    return num1 + num2;
  };
```

没有重载（深入理解），后定义函数覆盖先定义函数。

作为值的函数

```javascript
  var data = [{name: "Zachary", age: 28}, {name: "Nicholas", age: 29}];
  data.sort(createComparisonFunction("name"));
  console.log(data[0].name);  //Nicholas
  function createComparisonFunction(propertyName) {
    return function(object1, object2){
      var value1 = object1[propertyName];
      var value2 = object2[propertyName];
      if (value1 < value2){
        return -1;
      } else if (value1 > value2){
        return 1;
      } else {
        return 0;
      }
    };
  }
```

函数内部属性
  arguments：类数组对象，包含着传入函数中的所有参数；callee 的属性，指向拥有这个 arguments 对象的函数。
  this：函数据以执行的环境对象。当在网页的全局作用域中调用函数时，this 对象引用的就是 window
  caller，    ES5，       保存着调用当前函数的函数的引用

属性
  length：函数希望接收的命名参数的个数
  prototype：保存它们所有实例方法的真正所在

方法
  扩充作用域
  apply()，在特定的作用域中调用函数；接收两个参数：一个是在其中运行函数的作用域，另一个是参数数组。
  call()：作用同上，第二个参数都直接传递给函数
  bind()：创建一个函数的实例，其 this 值会被绑定到传给 bind() 函数的值

### 6.基本包装类型

操作基本类型值的语句一经执行完毕，就会立即销毁新创建的包装对象
Boolean，   推荐：不适用
Number，    继承方法之外，提供了将数值格式化为字符串的方法    推荐：不适用
String：字符方法，字符串操作，字符位置，trim()，大小写转换，模式匹配，localeCompare()，fromCharCode()。

### 7.单体内置对象

Global
  （全局）对象
  URI 编码方法
  eval()，    完整的 ECMAScript 解析器
  属性，    例，特殊的值，所有原生引用类型
  window 对象

Math
  属性
  min() 和 max() 方法
  舍入方法
  random() 方法
  其他方法

# 五、文件系统

## 分区与文件系统

对分区进行格式化是为了在分区上建立文件系统。一个分区通常只能格式化为一个文件系统，但是磁盘阵列等技术可以将一个分区格式化为多个文件系统。

## 组成

最主要的几个组成部分如下：

- inode：一个文件占用一个 inode，记录文件的属性，同时记录此文件的内容所在的 block 编号；
- block：记录文件的内容，文件太大时，会占用多个 block。

除此之外还包括：

- superblock：记录文件系统的整体信息，包括 inode 和 block 的总量、使用量、剩余量，以及文件系统的格式与相关信息等；
- block bitmap：记录 block 是否被使用的位图。

<div align="center"> <img src="pics/BSD_disk.png" width="800"/> </div><br>

## 文件读取

对于 Ext2 文件系统，当要读取一个文件的内容时，先在 inode 中查找文件内容所在的所有 block，然后把所有 block 的内容读出来。

<div align="center"> <img src="pics/12a65cc6-20e0-4706-9fe6-3ba49413d7f6.png" width="500px"> </div><br>

而对于 FAT 文件系统，它没有 inode，每个 block 中存储着下一个 block 的编号。

<div align="center"> <img src="pics/5b718e86-7102-4bb6-8ca5-d1dd791530c5.png" width="500px"> </div><br>

## 磁盘碎片

指一个文件内容所在的 block 过于分散，导致磁盘磁头移动距离过大，从而降低磁盘读写性能。

## block

在 Ext2 文件系统中所支持的 block 大小有 1K，2K 及 4K 三种，不同的大小限制了单个文件和文件系统的最大大小。

|     大小     |  1KB  |  2KB  |  4KB  |
| :----------: | :---: | :---: | :---: |
| 最大单一文件 | 16GB  | 256GB |  2TB  |
| 最大文件系统 |  2TB  |  8TB  | 16TB  |

一个 block 只能被一个文件所使用，未使用的部分直接浪费了。因此如果需要存储大量的小文件，那么最好选用比较小的 block。

## inode

inode 具体包含以下信息：

- 权限 (read/write/excute)；
- 拥有者与群组 (owner/group)；
- 容量；
- 建立或状态改变的时间 (ctime)；
- 最近读取时间 (atime)；
- 最近修改时间 (mtime)；
- 定义文件特性的旗标 (flag)，如 SetUID...；
- 该文件真正内容的指向 (pointer)。

inode 具有以下特点：

- 每个 inode 大小均固定为 128 bytes (新的 ext4 与 xfs 可设定到 256 bytes)；
- 每个文件都仅会占用一个 inode。

inode 中记录了文件内容所在的 block 编号，但是每个 block 非常小，一个大文件随便都需要几十万的 block。而一个 inode 大小有限，无法直接引用这么多 block 编号。因此引入了间接、双间接、三间接引用。间接引用让 inode 记录的引用 block 块记录引用信息。

<div align="center"> <img src="pics/inode_with_signatures.jpg" width="600"/> </div><br>

## 目录

建立一个目录时，会分配一个 inode 与至少一个 block。block 记录的内容是目录下所有文件的 inode 编号以及文件名。

可以看到文件的 inode 本身不记录文件名，文件名记录在目录中，因此新增文件、删除文件、更改文件名这些操作与目录的写权限有关。

## 日志

如果突然断电，那么文件系统会发生错误，例如断电前只修改了 block bitmap，而还没有将数据真正写入 block 中。

ext3/ext4 文件系统引入了日志功能，可以利用日志来修复文件系统。

## 挂载

挂载利用目录作为文件系统的进入点，也就是说，进入目录之后就可以读取文件系统的数据。

## 目录配置

为了使不同 Linux 发行版本的目录结构保持一致性，Filesystem Hierarchy Standard (FHS) 规定了 Linux 的目录结构。最基础的三个目录如下：

- / (root, 根目录)
- /usr (unix software resource)：所有系统默认软件都会安装到这个目录；
- /var (variable)：存放系统或程序运行过程中的数据文件。

<div align="center"> <img src="pics/linux-filesystem.png" width=""/> </div><br>

# 六、压缩与打包

## 压缩文件名

Linux 底下有很多压缩文件名，常见的如下：

| 扩展名     | 压缩程序                              |
| ---------- | ------------------------------------- |
| \*.Z       | compress                              |
| \*.zip     | zip                                   |
| \*.gz      | gzip                                  |
| \*.bz2     | bzip2                                 |
| \*.xz      | xz                                    |
| \*.tar     | tar 程序打包的数据，没有经过压缩      |
| \*.tar.gz  | tar 程序打包的文件，经过 gzip 的压缩  |
| \*.tar.bz2 | tar 程序打包的文件，经过 bzip2 的压缩 |
| \*.tar.xz  | tar 程序打包的文件，经过 xz 的压缩    |

## 压缩指令

### 1. gzip

gzip 是 Linux 使用最广的压缩指令，可以解开 compress、zip 与 gzip 所压缩的文件。

经过 gzip 压缩过，源文件就不存在了。

有 9 个不同的压缩等级可以使用。

可以使用 zcat、zmore、zless 来读取压缩文件的内容。

```HTML
$ gzip [-cdtv#] filename
-c ：将压缩的数据输出到屏幕上
-d ：解压缩
-t ：检验压缩文件是否出错
-v ：显示压缩比等信息
-# ： # 为数字的意思，代表压缩等级，数字越大压缩比越高，默认为 6
```

### 2. bzip2

提供比 gzip 更高的压缩比。

查看命令：bzcat、bzmore、bzless、bzgrep。

```HTML
$ bzip2 [-cdkzv#] filename
-k ：保留源文件
```

### 3. xz

提供比 bzip2 更佳的压缩比。

可以看到，gzip、bzip2、xz 的压缩比不断优化。不过要注意的是，压缩比越高，压缩的时间也越长。

查看命令：xzcat、xzmore、xzless、xzgrep。

```HTML
$ xz [-dtlkc#] filename
```

## 打包

压缩指令只能对一个文件进行压缩，而打包能够将多个文件打包成一个大文件。tar 不仅可以用于打包，也可以使用 gzip、bzip2、xz 将打包文件进行压缩。

```HTML
$ tar [-z|-j|-J] [cv] [-f 新建的 tar 文件] filename...  ==打包压缩
$ tar [-z|-j|-J] [tv] [-f 已有的 tar 文件]              ==查看
$ tar [-z|-j|-J] [xv] [-f 已有的 tar 文件] [-C 目录]    ==解压缩
-z ：使用 zip；
-j ：使用 bzip2；
-J ：使用 xz；
-c ：新建打包文件；
-t ：查看打包文件里面有哪些文件；
-x ：解打包或解压缩的功能；
-v ：在压缩/解压缩的过程中，显示正在处理的文件名；
-f : filename：要处理的文件；
-C 目录 ： 在特定目录解压缩。
```

| 使用方式 | 命令                                                  |
| :------: | ----------------------------------------------------- |
| 打包压缩 | tar -jcv -f filename.tar.bz2 要被压缩的文件或目录名称 |
|  查 看   | tar -jtv -f filename.tar.bz2                          |
|  解压缩  | tar -jxv -f filename.tar.bz2 -C 要解压缩的目录        |

# 七、Bash

可以通过 Shell 请求内核提供服务，Bash 正是 Shell 的一种。

## 特性

- 命令历史：记录使用过的命令
- 命令与文件补全：快捷键：tab
- 命名别名：例如 ll 是 ls -al 的别名
- shell scripts
- 通配符：例如 ls -l /usr/bin/X\* 列出 /usr/bin 下面所有以 X 开头的文件

## 变量操作

对一个变量赋值直接使用 =。

对变量取用需要在变量前加上 \$ ，也可以用 \${} 的形式；

输出变量使用 echo 命令。

```bash
$ x=abc
$ echo $x
$ echo ${x}
```

变量内容如果有空格，必须使用双引号或者单引号。

- 双引号内的特殊字符可以保留原本特性，例如 x="lang is \$LANG"，则 x 的值为 lang is zh_TW.UTF-8；
- 单引号内的特殊字符就是特殊字符本身，例如 x='lang is \$LANG'，则 x 的值为 lang is \$LANG。

可以使用 \`指令\` 或者 \$(指令) 的方式将指令的执行结果赋值给变量。例如 version=\$(uname -r)，则 version 的值为 4.15.0-22-generic。

可以使用 export 命令将自定义变量转成环境变量，环境变量可以在子程序中使用，所谓子程序就是由当前 Bash 而产生的子 Bash。

Bash 的变量可以声明为数组和整数数字。注意数字类型没有浮点数。如果不进行声明，默认是字符串类型。变量的声明使用 declare 命令：

```HTML
$ declare [-aixr] variable
-a ： 定义为数组类型
-i ： 定义为整数类型
-x ： 定义为环境变量
-r ： 定义为 readonly 类型
```

使用 [ ] 来对数组进行索引操作：

```bash
$ array[1]=a
$ array[2]=b
$ echo ${array[1]}
```

## 指令搜索顺序

- 以绝对或相对路径来执行指令，例如 /bin/ls 或者 ./ls ；
- 由别名找到该指令来执行；
- 由 Bash 内置的指令来执行；
- 按 \$PATH 变量指定的搜索路径的顺序找到第一个指令来执行。

## 数据流重定向

重定向指的是使用文件代替标准输入、标准输出和标准错误输出。

|           1           | 代码  |   运算符   |
| :-------------------: | :---: | :--------: |
|   标准输入 (stdin)    |   0   |  < 或 <<   |
|   标准输出 (stdout)   |   1   | &gt; 或 >> |
| 标准错误输出 (stderr) |   2   | 2> 或 2>>  |

其中，有一个箭头的表示以覆盖的方式重定向，而有两个箭头的表示以追加的方式重定向。

可以将不需要的标准输出以及标准错误输出重定向到 /dev/null，相当于扔进垃圾箱。

如果需要将标准输出以及标准错误输出同时重定向到一个文件，需要将某个输出转换为另一个输出，例如 2>&1 表示将标准错误输出转换为标准输出。

```bash
$ find /home -name .bashrc > list 2>&1
```

# 八、管道指令

管道是将一个命令的标准输出作为另一个命令的标准输入，在数据需要经过多个步骤的处理之后才能得到我们想要的内容时就可以使用管道。

在命令之间使用 | 分隔各个管道命令。

```bash
$ ls -al /etc | less
```

## 提取指令

cut 对数据进行切分，取出想要的部分。

切分过程一行一行地进行。

```HTML
$ cut
-d ：分隔符
-f ：经过 -d 分隔后，使用 -f n 取出第 n 个区间
-c ：以字符为单位取出区间
```

示例 1：last 显示登入者的信息，取出用户名。

```HTML
$ last
root pts/1 192.168.201.101 Sat Feb 7 12:35 still logged in
root pts/1 192.168.201.101 Fri Feb 6 12:13 - 18:46 (06:33)
root pts/1 192.168.201.254 Thu Feb 5 22:37 - 23:53 (01:16)

$ last | cut -d ' ' -f 1
```

示例 2：将 export 输出的信息，取出第 12 字符以后的所有字符串。

```HTML
$ export
declare -x HISTCONTROL="ignoredups"
declare -x HISTSIZE="1000"
declare -x HOME="/home/dmtsai"
declare -x HOSTNAME="study.centos.vbird"
.....(其他省略).....

$ export | cut -c 12-
```

## 排序指令

**sort**  用于排序。

```HTML
$ sort [-fbMnrtuk] [file or stdin]
-f ：忽略大小写
-b ：忽略最前面的空格
-M ：以月份的名字来排序，例如 JAN，DEC
-n ：使用数字
-r ：反向排序
-u ：相当于 unique，重复的内容只出现一次
-t ：分隔符，默认为 tab
-k ：指定排序的区间
```

示例：/etc/passwd 文件内容以 : 来分隔，要求以第三列进行排序。

```HTML
$ cat /etc/passwd | sort -t ':' -k 3
root:x:0:0:root:/root:/bin/bash
dmtsai:x:1000:1000:dmtsai:/home/dmtsai:/bin/bash
alex:x:1001:1002::/home/alex:/bin/bash
arod:x:1002:1003::/home/arod:/bin/bash
```

**uniq**  可以将重复的数据只取一个。

```HTML
$ uniq [-ic]
-i ：忽略大小写
-c ：进行计数
```

示例：取得每个人的登录总次数

```HTML
$ last | cut -d ' ' -f 1 | sort | uniq -c
1
6 (unknown
47 dmtsai
4 reboot
7 root
1 wtmp
```

## 双向输出重定向

输出重定向会将输出内容重定向到文件中，而  **tee**  不仅能够完成这个功能，还能保留屏幕上的输出。也就是说，使用 tee 指令，一个输出会同时传送到文件和屏幕上。

```HTML
$ tee [-a] file
```

## 字符转换指令

**tr**  用来删除一行中的字符，或者对字符进行替换。

```HTML
$ tr [-ds] SET1 ...
-d ： 删除行中 SET1 这个字符串
```

示例，将 last 输出的信息所有小写转换为大写。

```HTML
$ last | tr '[a-z]' '[A-Z]'
```

  **col**  将 tab 字符转为空格字符。

```HTML
$ col [-xb]
-x ： 将 tab 键转换成对等的空格键
```

**expand**  将 tab 转换一定数量的空格，默认是 8 个。

```HTML
$ expand [-t] file
-t ：tab 转为空格的数量
```

**join**  将有相同数据的那一行合并在一起。

```HTML
$ join [-ti12] file1 file2
-t ：分隔符，默认为空格
-i ：忽略大小写的差异
-1 ：第一个文件所用的比较字段
-2 ：第二个文件所用的比较字段
```

**paste**  直接将两行粘贴在一起。

```HTML
$ paste [-d] file1 file2
-d ：分隔符，默认为 tab
```

## 分区指令

**split**  将一个文件划分成多个文件。

```HTML
$ split [-bl] file PREFIX
-b ：以大小来进行分区，可加单位，例如 b, k, m 等
-l ：以行数来进行分区。
- PREFIX ：分区文件的前导名称
```

# 九、正则表达式

## grep

g/re/p（globally search a regular expression and print)，使用正则表示式进行全局查找并打印。

```HTML
$ grep [-acinv] [--color=auto] 搜寻字符串 filename
-c ： 统计个数
-i ： 忽略大小写
-n ： 输出行号
-v ： 反向选择，也就是显示出没有 搜寻字符串 内容的那一行
--color=auto ：找到的关键字加颜色显示
```

示例：把含有 the 字符串的行提取出来（注意默认会有 --color=auto 选项，因此以下内容在 Linux 中有颜色显示 the 字符串）

```HTML
$ grep -n 'the' regular_express.txt
8:I can't finish the test.
12:the symbol '*' is represented as start.
15:You are the best is mean you are the no. 1.
16:The world Happy is the same with "glad".
18:google is the best tools for search keyword
```

因为 { 和 } 在 shell 是有特殊意义的，因此必须要使用转义字符进行转义。

```HTML
$ grep -n 'go\{2,5\}g' regular_express.txt
```

## printf

用于格式化输出。它不属于管道命令，在给 printf 传数据时需要使用 $( ) 形式。

```HTML
$ printf '%10s %5i %5i %5i %8.2f \n' $(cat printf.txt)
    DmTsai    80    60    92    77.33
     VBird    75    55    80    70.00
       Ken    60    90    70    73.33
```

## awk

是由 Alfred Aho，Peter Weinberger, 和 Brian Kernighan 创造，awk 这个名字就是这三个创始人名字的首字母。

awk 每次处理一行，处理的最小单位是字段，每个字段的命名方式为：\$n，n 为字段号，从 1 开始，\$0 表示一整行。

示例：取出最近五个登录用户的用户名和 IP

```HTML
$ last -n 5
dmtsai pts/0 192.168.1.100 Tue Jul 14 17:32 still logged in
dmtsai pts/0 192.168.1.100 Thu Jul 9 23:36 - 02:58 (03:22)
dmtsai pts/0 192.168.1.100 Thu Jul 9 17:23 - 23:36 (06:12)
dmtsai pts/0 192.168.1.100 Thu Jul 9 08:02 - 08:17 (00:14)
dmtsai tty1 Fri May 29 11:55 - 12:11 (00:15)
```

```HTML
$ last -n 5 | awk '{print $1 "\t" $3}'
```

可以根据字段的某些条件进行匹配，例如匹配字段小于某个值的那一行数据。

```HTML
$ awk '条件类型 1 {动作 1} 条件类型 2 {动作 2} ...' filename
```

示例：/etc/passwd 文件第三个字段为 UID，对 UID 小于 10 的数据进行处理。

```text
$ cat /etc/passwd | awk 'BEGIN {FS=":"} $3 < 10 {print $1 "\t " $3}'
root 0
bin 1
daemon 2
```

awk 变量：

| 变量名称 | 代表意义                     |
| :------: | ---------------------------- |
|    NF    | 每一行拥有的字段总数         |
|    NR    | 目前所处理的是第几行数据     |
|    FS    | 目前的分隔字符，默认是空格键 |

示例：显示正在处理的行号以及每一行有多少字段

```HTML
$ last -n 5 | awk '{print $1 "\t lines: " NR "\t columns: " NF}'
dmtsai lines: 1 columns: 10
dmtsai lines: 2 columns: 10
dmtsai lines: 3 columns: 10
dmtsai lines: 4 columns: 10
dmtsai lines: 5 columns: 9
```

# 十、进程管理

## 查看进程

### 1. ps

查看某个时间点的进程信息。

示例一：查看自己的进程

```sh
# ps -l
```

示例二：查看系统所有进程

```sh
# ps aux
```

示例三：查看特定的进程

```sh
# ps aux | grep threadx
```

### 2. pstree

查看进程树。

示例：查看所有进程树

```sh
# pstree -A
```

### 3. top

实时显示进程信息。

示例：两秒钟刷新一次

```sh
# top -d 2
```

### 4. netstat

查看占用端口的进程

示例：查看特定端口的进程

```sh
# netstat -anp | grep port
```

## 进程状态

| 状态  | 说明                                                                                                                                 |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------ |
|   R   | running or runnable (on run queue)<br>正在执行或者可执行，此时进程位于执行队列中。                                                   |
|   D   | uninterruptible sleep (usually I/O)<br>不可中断阻塞，通常为 IO 阻塞。                                                                |
|   S   | interruptible sleep (waiting for an event to complete) <br> 可中断阻塞，此时进程正在等待某个事件完成。                               |
|   Z   | zombie (terminated but not reaped by its parent)<br>僵死，进程已经终止但是尚未被其父进程获取信息。                                   |
|   T   | stopped (either by a job control signal or because it is being traced) <br> 结束，进程既可以被作业控制信号结束，也可能是正在被追踪。 |
<br>

<div align="center"> <img src="pics/2bab4127-3e7d-48cc-914e-436be859fb05.png" width="490px"/> </div><br>

## SIGCHLD

当一个子进程改变了它的状态时（停止运行，继续运行或者退出），有两件事会发生在父进程中：

- 得到 SIGCHLD 信号；
- waitpid() 或者 wait() 调用会返回。

其中子进程发送的 SIGCHLD 信号包含了子进程的信息，比如进程 ID、进程状态、进程使用 CPU 的时间等。

在子进程退出时，它的进程描述符不会立即释放，这是为了让父进程得到子进程信息，父进程通过 wait() 和 waitpid() 来获得一个已经退出的子进程的信息。

<div align="center"> <!-- <img src="pics/flow.png" width=""/> --> </div><br>

## wait()

```c
pid_t wait(int *status)
```

父进程调用 wait() 会一直阻塞，直到收到一个子进程退出的 SIGCHLD 信号，之后 wait() 函数会销毁子进程并返回。

如果成功，返回被收集的子进程的进程 ID；如果调用进程没有子进程，调用就会失败，此时返回 -1，同时 errno 被置为 ECHILD。

参数 status 用来保存被收集的子进程退出时的一些状态，如果对这个子进程是如何死掉的毫不在意，只想把这个子进程消灭掉，可以设置这个参数为 NULL。

## waitpid()

```c
pid_t waitpid(pid_t pid, int *status, int options)
```

作用和 wait() 完全相同，但是多了两个可由用户控制的参数 pid 和 options。

pid 参数指示一个子进程的 ID，表示只关心这个子进程退出的 SIGCHLD 信号。如果 pid=-1 时，那么和 wait() 作用相同，都是关心所有子进程退出的 SIGCHLD 信号。

options 参数主要有 WNOHANG 和 WUNTRACED 两个选项，WNOHANG 可以使 waitpid() 调用变成非阻塞的，也就是说它会立即返回，父进程可以继续执行其它任务。

## 孤儿进程

一个父进程退出，而它的一个或多个子进程还在运行，那么这些子进程将成为孤儿进程。

孤儿进程将被 init 进程（进程号为 1）所收养，并由 init 进程对它们完成状态收集工作。

由于孤儿进程会被 init 进程收养，所以孤儿进程不会对系统造成危害。

## 僵尸进程

一个子进程的进程描述符在子进程退出时不会释放，只有当父进程通过 wait() 或 waitpid() 获取了子进程信息后才会释放。如果子进程退出，而父进程并没有调用 wait() 或 waitpid()，那么子进程的进程描述符仍然保存在系统中，这种进程称之为僵尸进程。

僵尸进程通过 ps 命令显示出来的状态为 Z（zombie）。

系统所能使用的进程号是有限的，如果产生大量僵尸进程，将因为没有可用的进程号而导致系统不能产生新的进程。

要消灭系统中大量的僵尸进程，只需要将其父进程杀死，此时僵尸进程就会变成孤儿进程，从而被 init 进程所收养，这样 init 进程就会释放所有的僵尸进程所占有的资源，从而结束僵尸进程。

# 参考资料

- 鸟哥. 鸟 哥 的 Linux 私 房 菜 基 础 篇 第 三 版[J]. 2009.
- [Linux 平台上的软件包管理](https://www.ibm.com/developerworks/cn/linux/l-cn-rpmdpkg/index.HTML)
- [Linux 之守护进程、僵死进程与孤儿进程](http://liubigbin.github.io/2016/03/11/Linux-%E4%B9%8B%E5%AE%88%E6%8A%A4%E8%BF%9B%E7%A8%8B%E3%80%81%E5%83%B5%E6%AD%BB%E8%BF%9B%E7%A8%8B%E4%B8%8E%E5%AD%A4%E5%84%BF%E8%BF%9B%E7%A8%8B/)
- [What is the difference between a symbolic link and a hard link?](https://stackoverflow.com/questions/185899/what-is-the-difference-between-a-symbolic-link-and-a-hard-link)
- [Linux process states](https://idea.popcount.org/2012-12-11-linux-process-states/)
- [GUID Partition Table](https://en.wikipedia.org/wiki/GUID_Partition_Table)
- [详解 wait 和 waitpid 函数](https://blog.csdn.net/kevinhg/article/details/7001719)
- [IDE、SATA、SCSI、SAS、FC、SSD 硬盘类型介绍](https://blog.csdn.net/tianlesoftware/article/details/6009110)
- [Akai IB-301S SCSI Interface for S2800,S3000](http://www.mpchunter.com/s3000/akai-ib-301s-scsi-interface-for-s2800s3000/)
- [Parallel ATA](https://en.wikipedia.org/wiki/Parallel_ATA)
- [ADATA XPG SX900 256GB SATA 3 SSD Review – Expanded Capacity and SandForce Driven Speed](http://www.thessdreview.com/our-reviews/adata-xpg-sx900-256gb-sata-3-ssd-review-expanded-capacity-and-sandforce-driven-speed/4/)
- [Decoding UCS Invicta – Part 1](https://blogs.cisco.com/datacenter/decoding-ucs-invicta-part-1)
- [硬盘](https://zh.wikipedia.org/wiki/%E7%A1%AC%E7%9B%98)
- [Difference between SAS and SATA](http://www.differencebetween.info/difference-between-sas-and-sata)
- [BIOS](https://zh.wikipedia.org/wiki/BIOS)
- [File system design case studies](https://www.cs.rutgers.edu/\~pxk/416/notes/13-fs-studies.HTML)
- [Programming Project #4](https://classes.soe.ucsc.edu/cmps111/Fall08/proj4.sHTML)
- [FILE SYSTEM DESIGN](http://web.cs.ucla.edu/classes/fall14/cs111/scribe/11a/index.HTML)




# 微信公众号


更多精彩内容将发布在微信公众号 CyC2018 上，你也可以在公众号后台和我交流学习和求职相关的问题。另外，公众号提供了该项目的 PDF 等离线阅读版本，后台回复 "下载" 即可领取。公众号也提供了一份技术面试复习大纲，不仅系统整理了面试知识点，而且标注了各个知识点的重要程度，从而帮你理清多而杂的面试知识点，后台回复 "大纲" 即可领取。我基本是按照这个大纲来进行复习的，对我拿到了 BAT 头条等 Offer 起到很大的帮助。你们完全可以和我一样根据大纲上列的知识点来进行复习，就不用看很多不重要的内容，也可以知道哪些内容很重要从而多安排一些复习时间。


<br><div align="center"><img width="510px" src="https://cs-notes-1256109796.cos.ap-guangzhou.myqcloud.com/githubio/公众号海报7.png"></img></div>
