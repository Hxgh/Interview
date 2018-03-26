> # 代码题

题库一：[https://blog.csdn.net/gyq04551/article/details/55254359](https://blog.csdn.net/gyq04551/article/details/55254359)

题库二：[https://blog.csdn.net/wu\_xianqiang/article/details/78519147](https://blog.csdn.net/wu_xianqiang/article/details/78519147)

> # 实例

# [_webpack：_](https://www.jianshu.com/p/42e11515c10f)

#### 为什要使用WebPack

现今的网页应用，它们拥有着复杂的JavaScript代码和一大堆依赖包。为了简化开发的复杂度，前端社区涌现出了很多好的实践方法

* **模块化**，让我们可以把复杂的程序细化为小的文件;
* 类似于TypeScript这种在JavaScript基础上拓展的开发语言：使我们能够实现目前版本的JavaScript不能直接使用的特性，并且之后还能转换为JavaScript文件使浏览器可以识别；
* Scss，less等CSS预处理器
* ...

这些改进确实大大的提高了我们的开发效率，但是利用它们开发的文件往往需要进行额外的处理才能让浏览器识别,而手动处理又是非常繁琐的，这就为WebPack类的工具的出现提供了需求。

#### 什么是Webpack

WebPack可以看做是**模块打包机**：它做的事情是，分析你的项目结构，找到JavaScript模块以及其它的一些浏览器不能直接运行的拓展语言（Scss，TypeScript等），并将其转换和打包为合适的格式供浏览器使用。

#### WebPack和Grunt以及Gulp相比有什么特性

并没有太多的可比性！

Gulp/Grunt是一种能够优化前端的开发流程的工具，

而WebPack是一种模块化的解决方案，不过Webpack的优点使得Webpack在很多场景下可以替代Gulp/Grunt类的工具。

Grunt和Gulp的工作方式是：在一个配置文件中，指明对某些文件进行类似编译，组合，压缩等任务的具体步骤，工具之后可以自动替你完成这些任务。

_Grunt和Gulp的工作流程：_

![](https://upload-images.jianshu.io/upload_images/1031000-d0693c06bb3a00e3.png?imageMogr2/auto-orient/strip|imageView2/2/w/700)

Webpack的工作方式是：把你的项目当做一个整体，通过一个给定的主文件（如：index.js），Webpack将从这个文件开始找到你的项目的所有依赖文件，使用loaders处理它们，最后打包为一个（或多个）浏览器可识别的JavaScript文件。

![](https://upload-images.jianshu.io/upload_images/1031000-160bc667d3b6093a.png?imageMogr2/auto-orient/strip|imageView2/2/w/700)

如果实在要把二者进行比较，Webpack的处理速度更快更直接，能打包更多不同类型的文件。

#### 安装

Webpack可以使用npm安装，新建一个空的练习文件夹（此处命名为webpack sample project），在终端中转到该文件夹后执行下述指令就可以完成安装。

```
//全局安装

$ npm install -g webpack

//安装到你的项目目录

$ npm install --save-dev webpack
```

#### 正式使用Webpack前的准备

1.在上述练习文件夹中创建一个package.json文件，这是一个标准的npm说明文件，里面蕴含了包括当前项目的依赖模块，自定义的脚本任务等等。在终端中使用`npm init`命令可以自动创建这个package.json文件

```
$ npm init
```

输入这个命令后，终端会问你一系列诸如项目名称，项目描述，作者等信息，不过不用担心，如果你不准备在npm中发布你的模块，这些问题的答案都不重要，回车默认即可。

2.package.json文件已经就绪，我们在本项目中安装Webpack作为依赖包

```
// 安装Webpack

$ npm install --save-dev webpack
```

3.回到之前的空文件夹，并在里面创建两个文件夹,app文件夹和public文件夹，app文件夹用来存放原始数据和我们将写的JavaScript模块，public文件夹用来存放之后供浏览器读取的文件（包括使用webpack打包生成的js文件以及一个`index.html`文件）。接下来我们再创建三个文件:

* `index.html`
  --放在public文件夹中;
* `Greeter.js`
  -- 放在app文件夹中;
* `main.js`
  -- 放在app文件夹中;

_此时项目结构如下图所示：_

![](https://upload-images.jianshu.io/upload_images/1031000-976ba1a06fd0702f.png?imageMogr2/auto-orient/strip|imageView2/2/w/347)

我们在**index.html**文件中写入最基础的html代码，它在这里目的在于引入打包后的js文件（这里我们先把之后打包后的js文件命名为`bundle.js`，之后我们还会详细讲述）。

```js
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>Webpack Sample Project</title>
  </head>
  <body>
    <div id='root'>
    </div>
    <script src="bundle.js"></script>
  </body>
</html>
```

我们在`Greeter.js`中定义一个返回包含问候信息的`html`元素的函数,并依据CommonJS规范导出这个函数为一个模块：

```js
// Greeter.js
module.exports = function() {
  var greet = document.createElement('div');
  greet.textContent = "Hi there and greetings!";
  return greet;
};
```

`main.js`文件中我们写入下述代码，用以把`Greeter模块`返回的节点插入页面。

```js
//main.js 
const greeter = require('./Greeter.js');
document.querySelector("#root").appendChild(greeter());
```

#### 正式使用Webpack

webpack可以在终端中使用，在基本的使用方法如下：

```ruby
# {extry file}出填写入口文件的路径，本文中就是上述main.js的路径，
# {destination for bundled file}处填写打包文件的存放路径
# 填写路径的时候不用添加{}

$ webpack {entry file} {destination for bundled file}
```

指定入口文件后，webpack将自动识别项目所依赖的其它文件，不过需要注意的是如果你的webpack不是全局安装的，那么当你在终端中使用此命令时，需要额外指定其在node\_modules中的地址，继续上面的例子，在终端中输入如下命令

```ruby
# webpack非全局安装的情况

$ node_modules/.bin/webpack app/main.js public/bundle.js
```

_结果如下：_

![](https://upload-images.jianshu.io/upload_images/1031000-b9e69a58e3518ba7.png?imageMogr2/auto-orient/strip|imageView2/2/w/700)

可以看出`webpack`同时编译了`main.js`和`Greeter,js`,现在打开`index.html`,可以看到如下结果  
![](https://upload-images.jianshu.io/upload_images/1031000-6cf1ecc41ef8c31d.png?imageMogr2/auto-orient/strip|imageView2/2/w/700)

已经成功的使用`Webpack`打包了一个文件了。不过在终端中进行复杂的操作，其实是不太方便且容易出错的，接下来看看Webpack的另一种更常见的使用方法。

_更多详细参见标题地址！！！_

#### WebPack例子：[出自阮一峰](https://github.com/ruanyf/webpack-demos)

首先，install [Webpack](https://www.npmjs.com/package/webpack)和[webpack-dev-server](https://www.npmjs.com/package/webpack-dev-server)

```
$ npm i -g webpack webpack-dev-server
```

然后，clone这个项目

```
$ git clone https://github.com/ruanyf/webpack-demos.git
```

安装依赖

```
$ cd webpack-demos
$ npm install
```

接下来进行deme演示

```
$ cd demo01
$ npm run dev
```

哇！你的浏览器打开了：[http://127.0.0.1:8080](http://127.0.0.1:8080/)，成功了哎！哈喽什么玩得？什么？你最好再去看看例子。

_webpack类似于Browserify_

```
$ browserify main.js > bundle.js
 ＃相当于 
$ webpack main.js bundle.js
```

它的配置文件是`webpack.config.js`.

```js
// webpack.config.js
module.exports = {
  entry: './main.js',
  output: {
    filename: 'bundle.js'
  }
};
```

有了`webpack.config.js`,你可以不带参数使用webpack

```
$ webpack
```

_一些命令行选项：_

* `webpack`– 构建文件

* `webpack -p`– 发布

* `webpack --watch`– 监听项目

* `webpack -d`– 包含 source maps方便调试

* `webpack --colors`– 让打包界面更好看

去构建你的项目, 你可以把启动项写进package.json

```js
// package.json
{
  // ...
  "scripts": {
    "dev": "webpack-dev-server --devtool eval --progress --colors",
    "deploy": "NODE_ENV=production webpack -p"
  },
  // ...
}
```



