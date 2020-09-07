<!-- GFM-TOC -->
# Vue

* [一、环境配置](#一环境配置)
  * [NVM](#NVM)
  * [Node.js](#Node.js)
  * [NPM](#NPM)
  * [Yarn](#Yarn)
* [二、前端构建工具](#二前端构建工具)
  * [Webpack概念](#Webpack概念)
  * [Gulp概念](#Gulp概念)
* [三、Vue基础](#三Vue基础)
  * [VueDevtools插件安装](#VueDevtools插件安装)
  * [Vue基础知识](#Vue基础知识)
* [四、Vue网络请求](#四Vue网络请求)
  * [Vue生命周期](#Vue生命周期)
  * [Vue组件深入](#Vue组件深入)
  * [Vue-axios网络请求](#Vue-axios网络请求)
* [五、Vue路由](#五Vue路由)
  * [Vue路由相关](#Vue路由相关)
  * [Vue第三方库](#Vue第三方库)
  * [vue-element-admin学习](#vue-element-admin学习)
* [六、Vuex](#六Vuex)
  * [Vuex安装](#Vuex安装)
  * [状态管理模式](#状态管理模式)
  * [压缩指令](#压缩指令)
  * [打包](#打包)
* [七、中间件](#七中间件)
  * [koa2](#koa2)
* [八、Nuxt](#八Nuxt)
  * [Nuxt教程](#Nuxt教程)
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
nvm 的windows下载地址：[nvm-windows](https://github.com/coreybutler/nvm-windows/releases) ,

选择第二个nvm-setup.zip，这样安装方便些。
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

|                   命令                   |                              意义                              |
| :--------------------------------------: | :------------------------------------------------------------: |
|                 nvm arch                 |              查看当前系统的位数和当前nodejs的位数              |
|  nvm install < version >&#91;arch&#93;   |     安装制定版本的node并且可指定平台version版本号arch平台      |
|      nvm list &#91; available &#93;      |                                                                |
|                - nvm list                |                       查看已经安装的版本                       |
|           - nvm list installed           |                       查看已经安装的版本                       |
|           - nvm list available           |                     查看网络可以安装的版本                     |
|                  nvm on                  |                       打开nodejs版本控制                       |
|                 nvm off                  |                       关闭nodejs版本控制                       |
|         nvm proxy &#91;url&#93;          |                         查看和设置代理                         |
|      nvm node_mirror &#91;url&#93;       | 设置或查看setting.txt中node_mirror,默https://nodejs.org/dist/  |
|       nvm npm_mirror &#91;url&#93;       | 同上setting中npm_mirror,默https://github.com/npm/npm/archive/. |
|        nvm uninstall < version >         |                         卸载制定的版本                         |
| nvm use &#91;version&#93; &#91;arch&#93; |                    切换制定的node版本和位数                    |
|         nvm root &#91;path&#93;          |                       设置和查看root路径                       |
|               nvm version                |                         查看当前的版本                         |

下面是安装和使切换nodejs的几个简单的命令使用：
nvm install 10.16.0 64-bit
nvm use 10.16.0
nvm list //查看以己经安装的。

## Node.js

### 1. Node安装

nvm install 10.16.0 64-bit

## NPM

npm install --update-binary

### 1. NPM查看安装信息

查看所有全局安装的模块：`npm list -g`
查看某个模块的版本号：`npm list grunt`

pm2 start npm -- run start

#### 删除`node_modules`文件夹

第一种方法：（最方便，删除速度超快）
这个东西，在linux，mac上可能有bug，win可用
`npm install rimraf -g`
`rimraf node_modules`

第二种方法：
`rmdir /s/q your_app_dir`

第三种方法：
`rm -f /node_modules`

第四种方法：
`cnpm install -g dlf`
`dlf  C:\Users\92809\Desktop\12`

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

### 3. nrm切换包管理源

npm install -g nrm
nrm list
nrm use

$ npm install -g cnpm --registry=https://registry.npm.taobao.org

## Yarn

### 1.yarn命令

安装yarn
`npm install -g yarn`

下载依赖
yarn install

启动
yarn run serve

编译项目
yarn run build

整理和修复文件
yarn run lint

## ESLint

1：全局安装eslint
`npm install -g eslint`

2：打开vscode 点击  “文件”-----》“首选项”----》“设置”，在右侧“用户设置”里加入一下配置：
[参考文档](https://blog.csdn.net/yanzisu_congcong/article/details/82180348)

```json
{
  //eslint 代码自动检查相关配置
  "eslint.enable": true,
  "eslint.autoFixOnSave": true,
  "eslint.run": "onType",
  "eslint.options": {
    "extensions": [".js",".vue"]
  },
  "eslint.validate": [
    "javascriptreact",
    "vue",
    "javascript", {
        "language": "vue",
        "autoFix": true
    },
    "html", {
      "language": "html",
      "autoFix": true
    }
  ],
}
```

## Python

https://blog.csdn.net/qq_36558410/article/details/80450275

# 二、前端构建工具

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

### 6. webpack服务器

1.全局安装服务器
  npm install -g webpack-dev-server@2.x
2.安装项目依赖
  npm install -D webpack-dev-server@2.x
3.运行webpack服务器
  webpack-dev-server
4.配置服务器的快捷执行方案
  "scripts": {
    "build": "webpack",
    "dev":"webpack-dev-server --content-base dist --inline --hot --port=8088"
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

### 7. webpack-module

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

### 8.es6 -> es5

1.安装依赖
  npm install -D babel-core babel-loader babel-preset-es2015
2.配置webpack.config.js文件
  {
    test:/\.js$/,
    use:"babel-loader",
    options:{
        presets:["es2015"]
    }
  }

未知,自己尝试
npm install --save-dev @babel/preset-react
npm install --save-dev @babel/core @babel/cli @babel/preset-env
npm install --save @babel/polyfill

### 9.构建react环境(webpack+ES6+React)

1.安装react
  npm install --save react react-dom
  npm install --save-dev babel-preset-react
2.编写配置文件
  {
    test:/\.(js|jsx)$/,
    use:"babel-loader"
  }
  <!-- 可以不用
  增加.babelrc文件 -->
3.编写代码
  import React from "react"
  import ReactDOM from "react-dom"
  class App extends React.Component{
    render(){
      return(
        <div>React EVN</div>
      )
    }
  }
  ReactDOM.render(<App />,document.getElementById("root"))

### 10.CSS处理

1.安装css相关依赖
  npm install -D css-loader style-loader
2.添加配置
  {
    test:/\.css$/,
    use:[
      "style-loader",
      "css-loader"
    ]
  }

### 11.图片配置

1.安装依赖：
  npm install -D file-loader url-loader
2.添加配置
  {
    test:/\.(png|jpg|gif|jpeg|svg)$/,
    use:"url-loader?limit=2048" // 大于2M进行压缩
  }

### 12.Less和Sass

1.安装
  npm install --save-dev less less-loader
2.添加配置
  {
    test:/\.less$/,
    use:[
      "style-loader",
      "css-loader",
      "less-loader"
    ]
  }

### 13.插件(plugins)

1.打开浏览器
  安装：
    npm install -D open-browser-webpack-plugin
  配置：
2.HTML模板
  安装：
    npm install -D html-webpack-plugin
  配置：
3.内置插件（省略后缀名）
  resolve:{
    extensions:['.js','.jsx']
  }

### 14.生产环境的搭建

安装
  npm install -D cross-env
  npm install -D babel-plugin-react-transform
  npm install -D react-transform-hmr
  npm install -D babel-preset-stage-2

## Gulp概念

自动化。对于需要反复重复的任务，例如压缩（minification）、编译、单元测试、linting等，自动化工具可以减轻你的劳动，简化你的工作。
gulp或者grunt都仅仅是一个操作平台，他们本身做不了任何事情，要做事情需要通过插件

### 1.gulp的使用

全局安装：
  官网:npm install --global gulp-cli
  npm install --global gulp
创建项目：
  LearnGulp
项目依赖安装：
  npm install --save-dev gulp
在项目根目录下创建一个名为 gulpfile.js 的文件：
  var gulp = require('gulp');
  gulp.task('default', function() {
  // 将你的默认的任务代码放在这
  });
运行
  gulp

### 2.gulp的方法

gulp.task(str,fn)
  创建一个gulp任务
gulp.src(path)
  文件来源
gulp.dest(path)
  操作之后的文件到哪里去
.pipe(package)
  执行一个gulp功能
gulp.watch()
  监听
gulp.start()
  执行gulp任务

### 3.插件

1.压缩JavaScript文件
  1.安装插件
    npm install --save-dev gulp-uglify
    代码
    gulp.task("jsuglify",function(){
      gulp.src("src/js/demo.js")
          .pipe(jsUglify())
          .pipe(gulp.dest("dist/js"))
    })
2.压缩CSS文件
  1.安装
    npm install --save-dev gulp-minify-css
3.压缩HTML文件
  1.安装
    npm install --save-dev gulp-minify-html
4.图片压缩
  npm install --save-dev gulp-imagemin
5.代码检查
  npm install --save-dev gulp-jshint jshint
  公司learder自己编写代码规范，按照他的规范来写代码！！！
6.合并、重命名
  npm install --save-dev gulp-concat gulp-rename
7.Less编译为CSS文件
  npm install --save-dev gulp-less
8.监听
  gulp.task("watchLess",function(){
    gulp.watch("src/css/*.less",function(){
      gulp.run("reless")
    })
  })
9.热更新：
  1).命令：npm install gulp-livereload --save-dev
  2).全局服务器：npm install -g http-server
  3).浏览器打开：chrome://extensions/ 浏览器插件：LiveReload （直接点击启动）
  4).编写热更新的代码
  5).启动热更新
    (1).在项目根目录下启动http-server
    (2).启动热更新：hot
    (3).打开浏览器启动项目
    (4).启动浏览器（livereload）插件，将空心圆点成实心圆

# 三、Vue基础

## VueDevtools插件安装

github下载插件，npm包安装依赖，拖入浏览器扩展程序

具体操作：
1.下载chrome扩展插件。
  在github上下载压缩包并解压到本地，github下载地址：https://github.com/vuejs/vue-devtools

2.npm install
  下载完成后打开命令行cmd进入vue-devtools-master文件夹，
  1.npm install，安装依赖包；如果安装太慢，请参照文章末尾说明进行操作。
  2.npm run build
  npm run build 执行完，会在shells>chrome下的src文件夹里生产如上图所示的几个js文件；
  若不执行以上命令会报错，无法加载背景脚本"build/background.js"

3.打开shells>chrome>manifest.json并把json文件里的"persistent":false改成true

4.扩展chrome插件
  1.打开chrome浏览器，打开更多工具>扩展程序；
  2.再点击加载已解压的扩展程序，然后把shells>chrome文件夹放入

5.测试安装成功
在插件的目录下执行npm run dev，这个时候我们的插件就可以运行了,打开localhost:8080可以看到插件已经安装并运行了。

## Vue基础知识

### 1.安装Vue

注：node版本必须大于等于8.9

```javascript
npm install -g @vue/cli
// OR
yarn global add @vue/cli

// 拉取 2.x 模板
npm install -g @vue/cli-init
// `vue init` 的运行效果将会跟 `vue-cli@2.x` 相同
vue init webpack my-project
```

### 2.创建项目

vue create hello-world

vue init webpack my-project
注：安装依赖的时候，选择最后一个，就是自己安装
cd my-project
npm start/npm run dev

### 3.工程目录

### 4.基础指令

Mustache：{{ 变量 }}  只能存在单行语句
v-once:只能渲染一次
v-html:解析HTML结构
v-bind:指令（解析属性中的对象）
v-bind简写：(:)
v-if:条件渲染
v-show:条件渲染

### 5.v-if vs v-show

v-if 是“真正”的条件渲染，因为它会确保在切换过程中条件块内的事件监听器和子组件适当地被销毁和重建。
v-if 也是惰性的：如果在初始渲染时条件为假，则什么也不做——直到条件第一次变为真时，才会开始渲染条件块。
相比之下，v-show 就简单得多——不管初始条件是什么，元素总是会被渲染，并且只是简单地基于 CSS 进行切换。
一般来说，v-if 有更高的切换开销，而 v-show 有更高的初始渲染开销。因此，如果需要非常频繁地切换，则使用 v-show 较好；如果在运行时条件很少改变，则使用 v-if 较好。

### 6.列表渲染

v-for

### 7.事件处理

// 在 `methods` 对象中定义方法
1.事件改变data数据，data数据改变会引起视图的变化
2.事件传递参数
  $event
3.数组更新检测
  append，unshift
  最开始讲数组的时候：老师在讲一个方法的时候会说，返回一个原数组还是新数组
  变异方法：
    改变原数组，则可以引起视图更新
    不改变原数组，创建新数组，则无法引起视图更新

### 组件模板

```javascript
<template lang="html">
  <!-- 只能存在一个根容器 -->
  <div>
    {{ 40|rmb }}
  </div>
</template>

<script>
export default {
  name: '组件名称',
  data () {
    return {
      message: '组件数据'
    }
  },
  // 在 `methods` 对象中定义方法
  methods:{
    changeCss: function() {
      this.cssObj = {
        c1: false,
        c2: true
      };
    }
  },
  // 过滤器
  filters: {
    rmb: function(value) {
      if (!value) return;
      value = value.toString();
      return "￥" + value;
    }
  },
  // 计算属性
  computed: {
    getMessage: function() {
      // `this` 指向 vm 实例
      return this.message
        .split("")
        .reverse()
        .join("");
    }
  },
  // 实时监听数据变化
  watch: {
    inputmsg(data) {
      if (data == "100") {
        this.inputmsg = "符合条件";
      }
    }
  },
}
</script>
// class只在该组件使用
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="css" scoped>
</style>
```

### 8.计算属性

计算属性缓存 vs 方法
  我们可以将同一函数定义为一个方法而不是一个计算属性。两种方式的最终结果确实是完全相同的。然而，不同的是计算属性是基于它们的依赖进行缓存的。计算属性只有在它的相关依赖发生改变时才会重新求值。这就意味着只要 message 还没有发生改变，多次访问 reversedMessage 计算属性会立即返回之前的计算结果，而不必再次执行函数

### 9.Class与Style绑定

#### 绑定Class

对象语法

数组语法

用在组件

#### 绑定Style

当 `v-bind:style` 使用需要添加浏览器引擎前缀的 CSS 属性时，如 transform，Vue.js 会自动侦测并添加相应的前缀。

### 10.表单输入绑定

修饰符：
  .lazy
  .number
  .trim
watch:监听事件

### 11.组件传递数据props

### 12.自定义事件向父组件传递数据

// 接受参数的数据名称,传递的数据
$emit(自定义事件)

### 13.动态组件&异步组件

```javascript
<!-- 失活的组件将会被缓存！-->
<keep-alive>
  <component v-bind:is="currentComponent"></component>
</keep-alive>
```

# 四、Vue网络请求

## Vue生命周期

beforeCreate 创建前状态：在实例初始化之后，数据观测和事件配置之前被调用，此时组件的选项对象还未创建，el 和 data 并未初始化，因此无法访问methods， data， computed等上的方法和数据。

created 创建完毕状态：实例已经创建完成之后被调用，在这一步，实例已完成以下配置：数据观测、属性和方法的运算，watch/event事件回调，完成了data 数据的初始化，el没有。 然而，挂在阶段还没有开始, $el属性目前不可见，这是一个常用的生命周期，因为你可以调用methods中的方法，改变data中的数据，并且修改可以通过vue的响应式绑定体现在页面上，，获取computed中的计算属性等等，通常我们可以在这里对实例进行预处理，也有一些童鞋喜欢在这里发ajax请求，值得注意的是，这个周期中是没有什么方法来对实例化过程进行拦截的，因此假如有某些数据必须获取才允许进入页面的话，并不适合在这个方法发请求，建议在组件路由钩子beforeRouteEnter中完成

beforeMount 挂载前状态：挂在开始之前被调用，相关的render函数首次被调用（虚拟DOM），实例已完成以下的配置： 编译模板，把data里面的数据和模板生成html，完成了el和data 初始化，注意此时还没有挂在html到页面上。

mounted 挂载结束状态：挂在完成，也就是模板中的HTML渲染到HTML页面中，此时一般可以做一些ajax操作，mounted只会执行一次。

beforeUpdate 更新前状态：在数据更新之前被调用，发生在虚拟DOM重新渲染和打补丁之前，可以在该钩子中进一步地更改状态，不会触发附加地重渲染过程

updated 更新完成状态：在由于数据更改导致地虚拟DOM重新渲染和打补丁只会调用，调用时，组件DOM已经更新，所以可以执行依赖于DOM的操作，然后在大多是情况下，应该避免在此期间更改状态，因为这可能会导致更新无限循环，该钩子在服务器端渲染期间不被调用

beforeDestroy 销毁前状态：在实例销毁之前调用，实例仍然完全可用，1）这一步还可以用this来获取实例，2）一般在这一步做一些重置的操作，比如清除掉组件中的定时器 和 监听的dom事件

destroyed 销毁完成状态：在实例销毁之后调用，调用后，所以的事件监听器会被移出，所有的子实例也会被销毁，该钩子在服务器端渲染期间不被调用

### 1.nuxt生命周期

Incoming Request：浏览器发出一个请求

nuxtServerInit：服务端接收到请求，检查当前有没有nuxtServerInit这个配置项，如果有的化就先执行这个方法，这个方法是用来操作vuex的

middleware：这是一个中间件，跟路由相关，这里可以做任何想要的功能

validate()：验证，配合高级动态路由去做一些验证，比如A页面是否允许跳转到B页面去，如果没有验证通过可以跳转到别的页面之类的校验

asyncData()&fetch()：获取数据。asyncData()获取的数据是用来渲染vue组件的，fetch通常用来修改vuex的数据

Render：渲染

Naviage：如果发起了一个非Server  的路由，那么在执行一遍middleware——Render的过程

1、我怎么在组件中引入图片？

图片目录在src/assets下，在组件中引入方式如下：

```html
<img :src="reuqire('@/assets/img/demo.png')" alt="" />
```

2、我怎么无视层级导入css，或是引入图片？

```javascript
@import "~@/scss/_var.css";
@import "~@/assets/iconfont/iconfont.css";
background: url("~@/assets/img/xxx.png");
background: url("~/assets/img/xxx.png");
```

3、我想在本地和服务端调试怎么弄？

修改 vue.config.js 中的 proxy 为你的服务端地址即可，如：
proxy: 'http://xxx.com'

## Vue组件深入

### 1. Props的验证

`Prop` 的大小写 (camelCase vs kebab-case)

`Prop` 类型

传递静态或动态 `Prop`

`Prop` 验证

类型检查

### 2. 插槽

插槽内容：内容展示由父组件传递给子组件（UI是由父组件传递的）
UI上要显示的内容由子组件决定

编译作用域：

具名插槽：`<slot>` 元素有一个特殊的特性：name。这个特性可以用来定义额外的插槽：

后背内容：组件上的插槽给默认值

作用域插槽：（传递数据）展示内容由子组件决定,效果由调用方决定

在 2.5.0+，slot-scope 不再限制在 <template> 元素上使用，而可以用在插槽内的任何元素或组件上。

```javascript
// 调用组件
<slot-demo>
  <template v-slot:v1>
    <div class="v1Class">
      {{ v1info }}
    </div>
  </template>
  <template v-slot:v2>
    <div class="v2Class">
      插槽内容2
    </div>
  </template>
</slot-demo>
// 组件
<div class="slotdemo">
  <slot name="v1"></slot>
  <slot name="v2">
    我是v2默认信息
  </slot>
</div>
```

### 2. 处理边界问题

访问元素 & 组件

访问根元素（不推荐）

访问父级组件实例（不推荐）

访问子组件实例或子元素：原声操作，this.$refs.usernameInput

依赖注入

### 3. 过渡与动画

#### 过渡的类名

v-enter：定义进入过渡的开始状态。

v-enter-active：定义进入过渡生效时的状态。

v-enter-to: 2.1.8版及以上 定义进入过渡的结束状态

v-leave: 定义离开过渡的开始状态。

v-leave-active：定义离开过渡生效时的状态。

v-leave-to: 2.1.8版及以上 定义离开过渡的结束状态。

#### css动画

```css
.hello-enter-active {
  animation: bounce-in .5s;
}
.hello-leave-active {
  animation: bounce-in .5s reverse;
}
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(1);
  }
}
```

#### 自定义过渡的类名

Animate.css

使用动画一定要脱离文档流

### 4.自定义指令

全局指令

局部指令

钩子函数

钩子函数参数

```javascript
// 注册一个全局自定义指令 `v-focus`
Vue.directive('focus', {
  // 当前指令的生命周期 当被绑定的元素插入到 DOM 中时……
  inserted: function (el) {
    // 聚焦元素
    el.focus()
  }
})
```

### 5.过滤器

允许你自定义过滤器，可被用于一些常见的文本格式化。

## Vue-axios网络请求

中文参考站点：https://www.kancloud.cn/yunye/axios/234845
vue官网维护了一个网络请求：vue-resource,后期不维护了，推荐使用axios

### 1. axios基础

Axios 是一个基于 promise 的 HTTP 库，可以用在浏览器和 node.js 中。

安装：

`npm install --save axios`

引入：

`import Axios from "axios"`
`Vue.prototype.$axios = Axios`

使用：

```javascript
mounted(){
  this.$axios.get("http://www.wwtliu.com/sxtstu/blueberrypai/getChengpinInfo.php")
  .then(res => {
    console.log(res.data);
  })
  .catch(error => {
    console.log(error);
  })
}
```

### 2. 跨域处理

配置：

```javascript
proxyTable: {
  '/doubai_api':{
      target: 'http://api.douban.com',
      pathRewrite: {
              '^/doubai': ''
      },
      changeOrigin: true
    }
}
```

main.js：
  Vue.prototype.HOST = "/doubai_api"

访问：

```javascript
var url = this.HOST + "/v2/movie/top250";
  this.$axios({
    method: 'get',
    url: url
  })
  .then(res => {
    console.log(res.data);
  })
  .catch(error => {
    console.log(error);
  })
```

# 五、Vue路由

## Vue路由相关

注意：项目在初始化的时候不要集成`vue-router`

安装：`cnpm install vue-router --save`

### 1.路由基础

如果在一个模块化工程中使用它，必须要通过 Vue.use() 明确地安装路由功能：
import Vue from 'vue'
import VueRouter from 'vue-router'
Vue.use(VueRouter)

### 2.创建路由

```javascript
const router = new VueRouter({
  routes: [
    {
      path: '/user/:userId',
      name: 'user',
      component: User
    }
  ]
})
// 给出路由显示的位置
<router-view></router-view>
// 跳转路由
<router-link :to="{ name: 'user', params: { userId: 123 }}">User</router-link>
router.push({ name: 'user', params: { userId: 123 }})
```

### 3.给出路由显示的位置

`<router-view />`

### 4.将路由对象注入Vue实例中

`router`

### 5.路由跳转

`router-link`
属性：`tag`

### 6.动态路由匹配（参数传递）

`/:id`

```javascript
const User = {
  template: '<div>User</div>'
}

const router = new VueRouter({
  routes: [
    // 动态路径参数 以冒号开头
    { path: '/user/:id', component: User }
  ]
})

// 页面中使用
{{ this.$route.params.id }}
```

### 7.路由嵌套

```javascript
{
  path:"/learn",
  name:"LearnVue", // 跳转
  component:LearnVue,
  children:[
    {
      path:"base",
      component:Base
    },
    {
      path:"http",
      component:Http
    }
  ]
}
```

### 8.编程式的导航

`this.$router.push`跳转页面

`this.$router.replace`替换页面

`this.$router.go`回退页面

### 9.命名路由（参数传递）

```javascript
<router-link tag="li" :to="{name:'HelloWorld',params:{id:helloParams}}">Hello</router-link>

this.$router.push({ name: 'HelloWorld', params: { id: this.clickParams }})
```

### 10.重定向和别名

重定向

```javascript
{
  path:"*",
  component:NotFound
},
{
  path:"/",
  // 重定向
  redirect:"/learn"
},
```

### 11.HTML5 History模式

// mode:"history",

需要后台配置

### 12.路由高亮

```css
/* .router-link-active{
  color:red;
} */
.active{
  color: red;
}
/* .router-link-exact-active{
  border: 1px solid yellowgreen;
} */
.currentActive{
  border: 1px solid yellowgreen;
}
```

```javascript
linkActiveClass:"active",
linkExactActiveClass:"currentActive",
```

### 13.路由实例

新建container文件,再建home文件夹,mine文件夹

## Vue第三方库

### 1.Element使用

npm 安装

`npm i element-ui -S`

```javascript
// import ElementUI from 'element-ui';// ElementUI全局加载
import { Button, Row } from 'element-ui';// ElementUI按需加载
// import 'element-ui/lib/theme-chalk/index.css';// ElementUI全局加载

// ElementUI start
// Vue.use(ElementUI);// ElementUI全局加载
Vue.use(Button);// ElementUI按需加载
Vue.use(Row);
// ElementUI end
```

### 2.iview使用

### 3.swiper使用

安装

`npm install vue-awesome-swiper --save`

```javascript
import VueAwesomeSwiper from 'vue-awesome-swiper'
import 'swiper/dist/css/swiper.css'

Vue.use(VueAwesomeSwiper) /* { default global options } */
```

```html
<swiper :options="swiperOption">
  <swiper-slide>I'm Slide 1</swiper-slide>
  <swiper-slide>I'm Slide 2</swiper-slide>
  <swiper-slide>I'm Slide 3</swiper-slide>
  <div slot="pagination" class="swiper-pagination" />
  <div slot="button-prev" class="swiper-button-prev" />
  <div slot="button-next" class="swiper-button-next" />
  <div slot="scrollbar" class="swiper-scrollbar" />
</swiper>
```

```javascript
data(){
  return{
    swiperOption:{
      autoplay:true,
      delay:2000,
      pagination: {
        el: '.swiper-pagination'
      }
    }
  }
},
```

### 4.第三方组件

## Vue碰到报错

找不到`node-sass`

`Error: Cannot find module 'node-sass'`

`cnpm install node-sass --save`

## vue-element-admin学习

### 1.目录结构

```sh
├── build                      # 构建相关
├── mock                       # 项目mock 模拟数据
├── plop-templates             # 基本模板
├── public                     # 静态资源
│   │── favicon.ico            # favicon图标
│   └── index.html             # html模板
├── src                        # 源代码
│   ├── api                    # 所有请求
│   ├── assets                 # 主题 字体等静态资源
│   ├── components             # 全局公用组件
│   ├── directive              # 全局指令
│   ├── filters                # 全局 filter
│   ├── icons                  # 项目所有 svg icons
│   ├── lang                   # 国际化 language
│   ├── layout                 # 全局 layout
│   ├── router                 # 路由
│   ├── store                  # 全局 store管理
│   ├── styles                 # 全局样式
│   ├── utils                  # 全局公用方法
│   ├── vendor                 # 公用vendor
│   ├── views                  # views 所有页面
│   ├── App.vue                # 入口页面
│   ├── main.js                # 入口文件 加载组件 初始化等
│   └── permission.js          # 权限管理
├── tests                      # 测试
├── .env.xxx                   # 环境变量配置
├── .eslintrc.js               # eslint 配置项
├── .babelrc                   # babel-loader 配置
├── .travis.yml                # 自动化CI配置
├── vue.config.js              # vue-cli 配置
├── postcss.config.js          # postcss 配置
└── package.json               # package.json
```

### 2.布局

`@/layout`整体布局

### 3.路由和侧边栏

本项目侧边栏主要基于 element-ui 的 el-menu 改造

`@/views/layout/components/Sidebar`

### 4.权限验证

通过获取当前用户的权限去比对路由表，生成当前用户具的权限可访问的路由表，通过 `router.addRoutes` 动态挂载到 `router` 上。

逻辑修改：现在路由层面权限的控制代码都在 @/permission.js 中，如果想修改逻辑，直接在适当的判断逻辑中 next() 释放钩子即可

指令权限：封装了一个指令权限，能简单快速的实现按钮级别的权限判断。 v-permission

### 5.新增页面

新增完路由之后不要忘记在 @/views 文件下 创建对应的文件夹，一般性一个路由对应一个文件，该模块下的功能组件或者方法就建议在本文件夹下创建一个utils或components文件夹，各个功能模块维护自己的utils或components组件

`@/api` 文件夹下创建本模块对应的 api 服务

新增组件:拆分组件最大的好处不是公用而是可维护性！

在全局的 `@/components` 只会写一些全局的组件，如富文本，各种搜索组件，封装的日期组件等等能被公用的组件。每个页面或者模块特定的业务组件则会写在当前 `views` 下面。如：`@/views/article/components/xxx.vue`

### 6.样式

所有全局样式都在 `@/src/styles` 目录下设置

```sh
├── styles
│   ├── btn.scss                 # 按钮样式
│   ├── element-ui.scss          # 全局自定义 element-ui 样式
│   ├── index.scss               # 全局通用样式
│   ├── mixin.scss               # 全局mixin
│   ├── sidebar.scss             # sidebar css
│   ├── transition.scss          # vue transition 动画
│   └── variables.scss           # 全局变量
```

自定义 element-ui 样式

现在我们来说说怎么覆盖 element-ui 样式。由于 element-ui 的样式我们是在全局引入的，所以你想在某个页面里面覆盖它的样式就不能加 scoped，但你又想只覆盖这个页面的 element 样式，你就可在它的父级加一个 class，用命名空间来解决问题。

```css
.article-page {
  /* 你的命名空间 */
  .el-tag {
    /* element-ui 元素*/
    margin-right: 0px;
  }
}
```

### 7.和服务端进行交互

`import 'normalize.css/normalize.css' // a modern alternative to CSS resets`
其中，@/src/utils/request.js 是基于 axios 的封装

与`mock`联调

# 六、Vuex

## Vuex安装

```shell
npm install vuex --save
yarn add vuex
```

引入

```vue
import Vue from 'vue'
import Vuex from 'vuex'

Vue.use(Vuex)
```

## 状态管理模式

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

# 七、中间件

## koa2

### 1.koa2开始

安装

`npm install -g koa-generator`

创建项目

`koa2 project`

`koa2 -e koa2-learn`

```shell
install dependencies:
  $ cd koa2-learn && npm install

run the app:
  $ DEBUG=koa2-learn:* npm start
```

### 2.koa2异步

```javascript
// 测试接口
router.get('/testAsync',async (ctx)=>{
  // 异步函数 async
  global.console.log('start',new Date().getTime())
  // 异步函数可包含 await
  const a=await new Promise((resolve,reject)=>{
    setTimeout(() => {
      global.console.log('async a',new Date().getTime())
      resolve('aaa')
    }, 1000);
  })
  const b=await 123
  const c=await new Promise((resolve,reject)=>{
    setTimeout(() => {
      global.console.log('async c',new Date().getTime())
      resolve('ccc')
    }, 2000);
  })
  ctx.body={
    a,
    b,
    c
  }
})
```

### 3.koa2中间件

```javascript
function pv(ctx){
  // ctx 全局的对象，维持信息被各个中间件引用
  // ctx.session.count++
  global.console.log('pv',ctx.path)
}

// 导出
module.exports=function(){
  return async function(ctx,next){
    global.console.log('pv start')
    pv(ctx)
    // 当前中间件运行完毕，交个第二个中间件
    await next()
    global.console.log('pv end')
  }
}
```

```javascript
const pv = require('./middleware/koa-pv')
const m1 = require('./middleware/m1')
const m2 = require('./middleware/m2')
const m3 = require('./middleware/m3')

app.use(pv())
app.use(m1())
app.use(m2())
app.use(m3())
app.use(json())
```

### 4.koa2路由

```javascript
const router = require('koa-router')()

router.prefix('/users')

router.get('/', function (ctx, next) {
  ctx.body = 'this is a users response!'
})

router.get('/bar', function (ctx, next) {
  ctx.body = 'this is a users/bar response'
})

module.exports = router
```

`cookies`

```javascript
  ctx.cookies.set('pvid',Math.random())// 设置
  ctx.cookies.get('pvid')//读取
```

## `Mongoose`

### 1.`mongoose`安装

### 2.可视化`RoBo-3T`

## Redis

# 八、Nuxt

## Nuxt教程

### 1.nuxt流程图

vue 2
整合vue router
vuex
整合ssr   vue server render
meta

Incoming Request 请求
nuxt Server Init 初始化nuxt服务,配置项，操作vuex
middleware 中间件
validate 高级路由验证
asyncData()&fetch() 获取数据，渲染vue组件和修改vuex
Render 渲染

Navigate-->middleware

### 2.nuxt基础

`vue init nuxt-community/koa-template nuxt-learn`

`analyze`进行代码优化处理

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
