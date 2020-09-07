<!-- GFM-TOC -->
# 前端

* [一、HTML基础](#一HTML基础)
  * [HTML概念](#HTML概念)
* [二、CSS基础](#二CSS基础)
  * [CSS概念](#CSS概念)
  * [CSS选择器](#CSS选择器)
  * [CSS动画](#CSS动画)
  * [CSS公共](#CSS公共)
* [三、JavaScript基础](#三JavaScript基础)
  * [JavaScript概念](#JavaScript概念)
  * [JavaScript引用类型](#JavaScript引用类型)
* [四、JavaScript面向对象](#四JavaScript面向对象)
  * [理解对象](#理解对象)
  * [创建对象](#创建对象)
  * [继承](#继承)
* [五、文件](#五文件)
  * [文件属性](#文件属性)
  * [文件与目录的基本操作](#文件与目录的基本操作)
  * [修改权限](#修改权限)
  * [默认权限](#默认权限)
  * [目录的权限](#目录的权限)
  * [链接](#链接)
  * [获取文件内容](#获取文件内容)
  * [指令与文件搜索](#指令与文件搜索)
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

# 一、HTML基础

## HTML概念

### 1. 块元素

display: block；块元素 div , address , blockquote , center , dir , dl , fieldset , form , h1 , h2 , h3 , h4 , h5 , h6 , hr , isindex , menu , noframes , noscript , ol , p , pre , table , ul , li。

### 2. 内联元素

display:inline；内联元素 em , img , q , a , abbr , acronym , b , bdo , big , br , cite , code , dfn , em , font , i, input , kbd , label, s , samp , select , small , span , strike , strong , sub , sup ,textarea , tt , u , var。

display:none隐藏元素或visibility:hidden可见性。

### 3. 图片

| 格式  | 损失  |  透明  |    特有    | 透明  |
| :---: | :---: | :----: | :--------: | :---: |
|  GIF  | 无损  |  透明  |    256     | 动画  |
| JPEG  | 有损  | 不透明 | 1000万以上 |       |
|  PNG  | 无损  |  透明  | 1000万以上 |       |

## 求助

* [MDN](https://developer.mozilla.org/zh-CN/)
* [菜鸟教程](https://www.runoob.com/)
* [W3school](https://www.w3school.com.cn/)
* [踏得](https://techbrood.com/h5b2a)
* [压缩图片 https://tinypng.com/](https://tinypng.com/)
* [压缩图片 https://www.picdiet.com/zh-cn](https://www.picdiet.com/zh-cn)

# 二、CSS基础

## CSS概念

### 1. @media

语法 @media mediatype and|not|only (media feature) { CSS-Code; }。

外部<link rel="stylesheet" media="mediatype and|not|only (media feature)" href="mystylesheet.CSS"><link rel="stylesheet" media="only screen and (max-width: 600px)" href="mystylesheet.CSS">。

适配

```css
/* 超小型设备(手机, 600px and down) */
@media only screen and (max-width: 600px) {
  .example {background: red;}
}
/* 小型设备 (纵向平板电脑 and 大型手机, 600px and up) */
@media only screen and (min-width: 600px) {
  .example { background: green; }
}
```

## CSS选择器

### 1. 优先级

权重：相互之间叠加  标记选择器：1 类选择器：10  id选择器：100

特殊情况 继承样式的权重都为0 行内样式优先，在本行中使用的 权重相同，就近原则

!important命令 被赋予最大优先级 #header{color:red!important;}。

### 2. 伪类

伪元素

:before 被选元素的内容前面插入内容，必须配合content指定插入内容 可为文本也可图片 <元素>:before{content:文字/url()} <p>:before{content:"夜明星空"; color:#c06;}
:after 在某个元素之后插入内容

链接伪类

a:link{} 未访问时超链接状态
a:visited 访问后
a:hover 鼠标经过，悬停
a:active 鼠标单击不动时。

### 3. 盒子模型

box-sizing盒子宽度和高度是否包含内边距和边框

content-box:不包含border和padding
border-box:包含border和padding

### 4. 浮动定位

浮动

浮动float 设置浮动元素的属性会脱离标准文档流控制 float：属性值 left向左浮动right右none默认
清除浮动
1after伪元素清除浮动（推荐使用）
.clearfix:after{/*伪元素是行内元素 正常浏览器清除浮动方法*/
content: "";
display: block;
height: 0;
clear:both;
visibility: hidden;
}
.clearfix{
*zoom: 1;/*ie6清除浮动的方式 *号只有IE6-IE7执行，其他浏览器不执行*/
}
2父级div定义 height
3结尾处加空div标签 clear:both
4父级div定义 overflow:hidden
5父级div定义 overflow:auto

定位position

静态定位static 默认值，无法通过边偏移来改变位置
相对relative 相对定位后，位置改变，但是它在文档流中的位置仍然保留
绝对absolute 依据最近的已经定位的父元素进行定位， 若所有父元素都未定位，则依靠body元素定位
固定fixed 始终依据浏览器窗口来显示位置
z-index层叠等级属性 取值正整数，负整数和0.默认为0，取值越大，定位属性在层叠元素中越居中

## CSS动画

过渡，变形，动画

## CSS公共

逻辑区
页面上彼此相关的一组元素
1找出逻辑区
2使用div标记逻辑区
3标出div id="cats"
4增加一些样式
5展现更多结构
6在结构上增加结构

# 三、JavaScript基础

## JavaScript概念

组成：核心(ECMAScript)，提供核心语言功能； 文档对象模型(DOM)，提供访问和操作网页内容的方法和接口；浏览器对象模型(BOM)，提供与浏览器交互的方法和接口。

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

## JavaScript模块化

### 1.模块基础

闭包:因作用域问题,使用闭包

```javascript
function Demo() {
  var hello = "hello";
  return function () {
    // 闭包！！！
    //
  }
}
Demo();
```

模块：设计模式规范：开闭原则：对扩展开放，对修改关闭

```javascript
// 作用域独立
// 自执行
(function(){
  function userInfo(){
    var name = "iwen";
    var age = 20;
    return {
      name:name,
      age:age
    }
  }
  console.log(userInfo().age);
  var info = userInfo()
  console.log(info.name);
})();

// 模块!
var module = (function () {
  var Demo = {

  }
  var hello = "hello";
  function userInfo() {
    var name = "iwen";
    var age = 20;
    console.log(name);
  }
  return {
    userInfo: userInfo,
    hello: hello
  }
})();
console.log(module.hello);
module.userInfo();
```

私有和公有的属性和方法

```javascript
// 私有与公有
var module = (function () {
  var infoObj = {
    name: 'iwen',
    age: 20
  }

  function getName() {
    if (!infoObj.name) {
      return;
    }
    return infoObj.name;
  }

  function getAge() {
    if (!infoObj.age) {
      return;
    }
    return infoObj.age
  }

  function setAge(age) {
    if (age) {
      infoObj.age = age;
    }
  }

  function setName(name) {
    infoObj.name = name
  }
  // 公有方法： getName,getAge,setAge,setName
  // 私有方法： infoObj
  return {
    getName: getName,
    getAge: getAge,
    setAge: setAge,
    setName: setName
  }
})();
console.log(module.getName());
console.log(module.getAge());
module.setAge(30);
console.log(module.getAge());
// module.setName("ice");
```

模块扩展

```javascript
/*
  扩展(放大模式)
*/
var module1 = (function () {
  function Demo1() {
    console.log("Demo1");
  }

  function Demo2() {
    console.log("Demo2");
  }
  return {
    Demo1: Demo1,
    Demo2: Demo2
  }
})()
// 对于程序而言，一个module肯定不能完成所有的事情
// 如果现在需要扩展？
var module2 = (function (module1) {
  function Demo3() {
    console.log(module1.Demo1())
  }

  function M2Demo() {
    console.log("M2Demo")
  }
  // 直接挂载到module1身上
  module1.Demo4 = function () {
    console.log("M2M1Demo4")
  }
  return {
    Demo3: Demo3,
    M2Demo: M2Demo,
    module1: module1
  }
})(module1);
module2.Demo3()
module2.M2Demo()
module2.module1.Demo4();
```

模块扩展(放大模式)

```javascript
/*
  扩展(放大模式)
*/
var module1 = (function () {
  function Demo1() {
    console.log("Demo1");
  }

  function Demo2() {
    console.log("Demo2");
  }
  return {
    Demo1: Demo1,
    Demo2: Demo2
  }
})()
// 对于程序而言，一个module肯定不能完成所有的事情
// 如果现在需要扩展？
var module2 = (function (module1) {
  function Demo3() {
    console.log(module1.Demo1())
  }

  function M2Demo() {
    console.log("M2Demo")
  }
  // 直接挂载到module1身上
  module1.Demo4 = function () {
    console.log("M2M1Demo4")
  }
  return {
    Demo3: Demo3,
    M2Demo: M2Demo,
    module1: module1
  }
})(module1);
module2.Demo3()
module2.M2Demo()
module2.module1.Demo4();
```

Commonjs规范
  文件与文件之间的隔离

```javascript
/*
  demo1.js中
*/
var demo = "demo"
//导出
module.exports = demo;
```

```javascript
/*
  demo2.js中
*/
// 引入
var demo = require("./demo1.js");
console.log(demo);
```

### 2.Require

requirejs:
应用场景：1.后端渲染：require（路由）；2.某个页面或者主页面具有很多js文件引入
  1.require介绍：
    1.模块化
    2.帮我们管理文件依赖
    3.管理引入js文件
  2.引入require
    <script data-main="js/main.js" src="js/libs/require.js"></script>
  3.配置main.js
    requirejs.config({
      baseUrl: 'js/',
      paths:{
        "index":"apps/index",
        "getname":"apps/getname",
        "jquery":"libs/jquery-3.2.1"
      }
    })
    requirejs(["index","getname","jquery"],function(index,getname,$){
    })

src 资源文件夹
  app 自己的js index.js getname.js
  lib 第三方引用的js require.js jquery-3.2.1.js
  main.js
index.html

```javascript
// 配置文件
requirejs.config({
  // 基础路径
  baseUrl: 'js/',
  // 映射
  // .js可以省略
  paths: {
    "index": "apps/index",
    "getname": "apps/getname",
    "jquery": "libs/jquery-3.2.1"
  }
})
requirejs(["index", "getname", "jquery"], function (index, getname, $) {
  // 主入口文件
  // 调用
  index.init();
})
```

定义模块 index.js文件

```javascript
// 定义模块
// define({
//   name:"iwen",
//   age:20
// })

// 函数式定义
// define(function(){
//   var demo = 10;
//   function demo(){
//
//   }
// })

// // 存在依赖的函数式定义
// define(["jquery"],function($){
//   console.log($ );
// })

// 依赖注入
define(["getname","jquery"],function(getname,$){
  function init(){
    $("#root").html(getname.text());
  }
  return {
    init:init
  }
})
```

getname.js文件

```javascript
define(function(){
  function text(){
    return "我是一个文本"
  }
  return {
    text:text
  }
})
```

require使用方式

```javascript
// 主页面
<script data-main="js/main.js" src="js/lib/require.js"></script>
<div class="root"></div>
// main.js文件
requirejs.config({
  baseUrl:"js/",
  paths:{
    "jquery":"lib/jquery-3.2.1",
    "data":"app/data",
    "index":"app/index",
    "view":"app/view"
  }
})
requirejs(["jquery","data","index","view"],function($,data,index,view){
  index.init();
})
// index.js文件
define(["data", "view"], function (data, view) {
  function init() {
    view.setView(data.data);
  }
  return {
    init:init
  }
})
// data.js文件
define(function(){
  return{
    data:"hello requirejs"
  }
})
// view.js文件
define(["jquery"], function ($) {
  // 获取视图
  /*
    set和get
    set：设置
    get：获取
  */
  function getView() {
    return $(".root");
  }

  function setView(data) {
    getView().html(data);
  }

  return {
    setView: setView
  }
})
```

require需要去遵循defind规范
若是第三方不遵循define模块定义规范,得导出为遵循的方案进行shim

```javascript
requirejs.config({
  baseUrl:"js/",
  paths:{
    "jquery":"lib/jquery-3.2.1",
    "swiper":"lib/swiper.min",
    "index":"app/index"
  },
  // 为那些没有使用define()来声明依赖关系、设置
  // 模块的"浏览器全局变量注入"型脚本做依赖和导出配置
  shim:{
    "swiper":{
      // 依赖的库
      deps:["jquery"],
      // 导出为swiper
      exports:"swiper"
    }
  }
})
requirejs(["jquery","swiper","index"],function($,swiper,index){

})
```

```javascript
```

### 3.Require实战

# 四、JavaScript面向对象

## 理解对象

## 创建对象

## 继承

对分区进行格式化是为了在分区上建立文件系统。一个分区通常只能格式化为一个文件系统，但是磁盘阵列等技术可以将一个分区格式化为多个文件系统。

# 五、函数表达式

## 文件属性

用户分为三种：文件拥有者、群组以及其它人，对不同的用户有不同的文件权限。

使用 ls 查看一个文件时，会显示一个文件的信息，例如 `drwxr-xr-x 3 root root 17 May 6 00:14 .config`，对这个信息的解释如下：

- drwxr-xr-x：文件类型以及权限，第 1 位为文件类型字段，后 9 位为文件权限字段
- 3：链接数
- root：文件拥有者
- root：所属群组
- 17：文件大小
- May 6 00:14：文件最后被修改的时间
- .config：文件名

常见的文件类型及其含义有：

- d：目录
- -：文件
- l：链接文件

9 位的文件权限字段中，每 3 个为一组，共 3 组，每一组分别代表对文件拥有者、所属群组以及其它人的文件权限。一组权限中的 3 位分别为 r、w、x 权限，表示可读、可写、可执行。

文件时间有以下三种：

- modification time (mtime)：文件的内容更新就会更新；
- status time (ctime)：文件的状态（权限、属性）更新就会更新；
- access time (atime)：读取文件时就会更新。

## 文件与目录的基本操作

### 1. ls

列出文件或者目录的信息，目录的信息就是其中包含的文件。

```HTML
# ls [-aAdfFhilnrRSt] file|dir
-a ：列出全部的文件
-d ：仅列出目录本身
-l ：以长数据串行列出，包含文件的属性与权限等等数据
```

### 2. cd

更换当前目录。

```
cd [相对路径或绝对路径]
```

### 3. mkdir

创建目录。

```
# mkdir [-mp] 目录名称
-m ：配置目录权限
-p ：递归创建目录
```

### 4. rmdir

删除目录，目录必须为空。

```HTML
rmdir [-p] 目录名称
-p ：递归删除目录
```

### 5. touch

更新文件时间或者建立新文件。

```HTML
# touch [-acdmt] filename
-a ： 更新 atime
-c ： 更新 ctime，若该文件不存在则不建立新文件
-m ： 更新 mtime
-d ： 后面可以接更新日期而不使用当前日期，也可以使用 --date="日期或时间"
-t ： 后面可以接更新时间而不使用当前时间，格式为[YYYYMMDDhhmm]
```

### 6. cp

复制文件。如果源文件有两个以上，则目的文件一定要是目录才行。

```HTML
cp [-adfilprsu] source destination
-a ：相当于 -dr --preserve=all
-d ：若来源文件为链接文件，则复制链接文件属性而非文件本身
-i ：若目标文件已经存在时，在覆盖前会先询问
-p ：连同文件的属性一起复制过去
-r ：递归复制
-u ：destination 比 source 旧才更新 destination，或 destination 不存在的情况下才复制
--preserve=all ：除了 -p 的权限相关参数外，还加入 SELinux 的属性, links, xattr 等也复制了
```

### 7. rm

删除文件。

```HTML
# rm [-fir] 文件或目录
-r ：递归删除
```

### 8. mv

移动文件。

```HTML
# mv [-fiu] source destination
# mv [options] source1 source2 source3 .... directory
-f ： force 强制的意思，如果目标文件已经存在，不会询问而直接覆盖
```

## 修改权限

可以将一组权限用数字来表示，此时一组权限的 3 个位当做二进制数字的位，从左到右每个位的权值为 4、2、1，即每个权限对应的数字权值为 r : 4、w : 2、x : 1。

```HTML
# chmod [-R] xyz dirname/filename
```

示例：将 .bashrc 文件的权限修改为 -rwxr-xr--。

```HTML
# chmod 754 .bashrc
```

也可以使用符号来设定权限。

```HTML
# chmod [ugoa]  [+-=] [rwx] dirname/filename
- u：拥有者
- g：所属群组
- o：其他人
- a：所有人
- +：添加权限
- -：移除权限
- =：设定权限
```

示例：为 .bashrc 文件的所有用户添加写权限。

```HTML
# chmod a+w .bashrc
```

## 默认权限

- 文件默认权限：文件默认没有可执行权限，因此为 666，也就是 -rw-rw-rw- 。
- 目录默认权限：目录必须要能够进入，也就是必须拥有可执行权限，因此为 777 ，也就是 drwxrwxrwx。

可以通过 umask 设置或者查看默认权限，通常以掩码的形式来表示，例如 002 表示其它用户的权限去除了一个 2 的权限，也就是写权限，因此建立新文件时默认的权限为 -rw-rw-r--。

## 目录的权限

文件名不是存储在一个文件的内容中，而是存储在一个文件所在的目录中。因此，拥有文件的 w 权限并不能对文件名进行修改。

目录存储文件列表，一个目录的权限也就是对其文件列表的权限。因此，目录的 r 权限表示可以读取文件列表；w 权限表示可以修改文件列表，具体来说，就是添加删除文件，对文件名进行修改；x 权限可以让该目录成为工作目录，x 权限是 r 和 w 权限的基础，如果不能使一个目录成为工作目录，也就没办法读取文件列表以及对文件列表进行修改了。

## 链接

<div align="center"> <img src="pics/1e46fd03-0cda-4d60-9b1c-0c256edaf6b2.png" width="450px"> </div><br>


```HTML
# ln [-sf] source_filename dist_filename
-s ：默认是实体链接，加 -s 为符号链接
-f ：如果目标文件存在时，先删除目标文件
```

### 1. 实体链接

在目录下创建一个条目，记录着文件名与 inode 编号，这个 inode 就是源文件的 inode。

删除任意一个条目，文件还是存在，只要引用数量不为 0。

有以下限制：不能跨越文件系统、不能对目录进行链接。

```HTML
# ln /etc/crontab .
# ll -i /etc/crontab crontab
34474855 -rw-r--r--. 2 root root 451 Jun 10 2014 crontab
34474855 -rw-r--r--. 2 root root 451 Jun 10 2014 /etc/crontab
```

### 2. 符号链接

符号链接文件保存着源文件所在的绝对路径，在读取时会定位到源文件上，可以理解为 Windows 的快捷方式。

当源文件被删除了，链接文件就打不开了。

因为记录的是路径，所以可以为目录建立符号链接。

```HTML
# ll -i /etc/crontab /root/crontab2
34474855 -rw-r--r--. 2 root root 451 Jun 10 2014 /etc/crontab
53745909 lrwxrwxrwx. 1 root root 12 Jun 23 22:31 /root/crontab2 -> /etc/crontab
```

## 获取文件内容

### 1. cat

取得文件内容。

```HTML
# cat [-AbEnTv] filename
-n ：打印出行号，连同空白行也会有行号，-b 不会
```

### 2. tac

是 cat 的反向操作，从最后一行开始打印。

### 3. more

和 cat 不同的是它可以一页一页查看文件内容，比较适合大文件的查看。

### 4. less

和 more 类似，但是多了一个向前翻页的功能。

### 5. head

取得文件前几行。

```HTML
# head [-n number] filename
-n ：后面接数字，代表显示几行的意思
```

### 6. tail

是 head 的反向操作，只是取得是后几行。

### 7. od

以字符或者十六进制的形式显示二进制文件。

## 指令与文件搜索

### 1. which

指令搜索。

```HTML
# which [-a] command
-a ：将所有指令列出，而不是只列第一个
```

### 2. whereis

文件搜索。速度比较快，因为它只搜索几个特定的目录。

```HTML
# whereis [-bmsu] dirname/filename
```

### 3. locate

文件搜索。可以用关键字或者正则表达式进行搜索。

locate 使用 /var/lib/mlocate/ 这个数据库来进行搜索，它存储在内存中，并且每天更新一次，所以无法用 locate 搜索新建的文件。可以使用 updatedb 来立即更新数据库。

```HTML
# locate [-ir] keyword
-r：正则表达式
```

### 4. find

文件搜索。可以使用文件的属性和权限进行搜索。

```HTML
# find [basedir] [option]
example: find . -name "shadow*"
```

**① 与时间有关的选项**

```HTML
-mtime  n ：列出在 n 天前的那一天修改过内容的文件
-mtime +n ：列出在 n 天之前 (不含 n 天本身) 修改过内容的文件
-mtime -n ：列出在 n 天之内 (含 n 天本身) 修改过内容的文件
-newer file ： 列出比 file 更新的文件
```

+4、4 和 -4 的指示的时间范围如下：

<div align="center"> <img src="pics/658fc5e7-79c0-4247-9445-d69bf194c539.png" width=""/> </div><br>

**② 与文件拥有者和所属群组有关的选项**

```HTML
-uid n
-gid n
-user name
-group name
-nouser ：搜索拥有者不存在 /etc/passwd 的文件
-nogroup：搜索所属群组不存在于 /etc/group 的文件
```

**③ 与文件权限和名称有关的选项**

```HTML
-name filename
-size [+-]SIZE：搜寻比 SIZE 还要大 (+) 或小 (-) 的文件。这个 SIZE 的规格有：c: 代表 byte，k: 代表 1024bytes。所以，要找比 50KB 还要大的文件，就是 -size +50k
-type TYPE
-perm mode  ：搜索权限等于 mode 的文件
-perm -mode ：搜索权限包含 mode 的文件
-perm /mode ：搜索权限包含任一 mode 的文件
```

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
