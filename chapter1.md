# 1.HTML&其他基础

#### XHTML和HTML有什么区别？

```
最主要的不同：
XHTML 元素必须被正确地嵌套。
XHTML 元素必须被关闭。
标签名必须用小写字母。
XHTML 文档必须拥有根元素。
```

#### 前端页面有哪三层构成，分别是什么?作用是什么?

```
结构层：HTML 表现层：CSS 行为层 JS
```

#### 介绍一下你对浏览器内核的理解？常见的浏览器内核？

```
主要分成两部分：渲染引擎(layout engineer或Rendering Engine)和JS引擎。
渲染引擎：负责取得网页的内容（HTML、XML、图像等等）、整理讯息（例如加入CSS等），以及计算网页的显示方式，然后会输出至显示器或打印机。浏览器的内核的不同对于网页的语法解释会有不同，所以渲染的效果也不相同。所有网页浏览器、电子邮件客户端以及其它需要编辑、显示网络内容的应用程序都需要内核。
JS引擎则：解析和执行javascript来实现网页的动态效果。
最开始渲染引擎和JS引擎并没有区分的很明确，后来JS引擎越来越独立，内核就倾向于只指渲染引擎。
1,使用Trident的是internet explorer，国产的绝大部分浏览器。Trident是就是ie内核
2,使用Gecko的是Mozilla Firefox，使用 Gecko 内核的浏览器也有不少，如 Netscape MozillaSuite/SeaMonkey 等
3,使用Presto的是opera，这是目前公认网页浏览速度最快的浏览器内核
```

#### 什么是语义化的HTML?

```
直观的认识标签 对于搜索引擎的抓取有好处，用正确的标签做正确的事情！
html语义化就是让页面的内容结构化，便于对浏览器、搜索引擎解析；
在没有样式CCS情况下也以一种文档格式显示，并且是容易阅读的。搜索引擎的爬虫依赖于标记来确定上下文和各个关键字的权重，利于 SEO。
使阅读源代码的人对网站更容易将网站分块，便于阅读维护理解。
```

#### HTML5 为什么只需要写 !DOCTYPE HTML？

```
HTML5 不基于 SGML，因此不需要对DTD进行引用，但是需要doctype来规范浏览器的行为（让浏览器按照它们应该的方式来运行）；
而HTML4.01基于SGML,所以需要对DTD进行引用，才能告知浏览器文档所使用的文档类型
```

#### Doctype作用？标准模式\(严格模式\)与兼容模式各有什么区别?

```
!DOCTYPE声明位于位于HTML文档中的第一行，处于html 标签之前。告知浏览器的解析器用什么文档标准解析这个文档。DOCTYPE不存在或格式不正确会导致文档以兼容模式呈现。
标准模式的排版 和JS运作模式都是以该浏览器支持的最高标准运行。在兼容模式中，页面以宽松的向后兼容的方式显示,模拟老式浏览器的行为以防止站点无法工作。
```

#### html5有哪些新特性、移除了那些元素？如何处理HTML5新标签的浏览器兼容问题？如何区分 HTML 和HTML5？

```
HTML5 现在已经不是 SGML 的子集，主要是关于图像，位置，存储，多任务等功能的增加。
绘画 canvas
用于媒介回放的 video 和 audio 元素
本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失；
sessionStorage 的数据在浏览器关闭后自动删除
语意化更好的内容元素，比如 article、footer、header、nav、section
表单控件，calendar、date、time、email、url、search
新的技术webworker, websockt, Geolocation
移除的元素
纯表现的元素：basefont，big，center，font, s，strike，tt，u；
对可用性产生负面影响的元素：frame，frameset，noframes；
支持HTML5新标签：
IE8/IE7/IE6支持通过document.createElement方法产生的标签，
可以利用这一特性让这些浏览器支持HTML5新标签，
浏览器支持新标签后，还需要添加标签默认的样式：
```

#### HTML5的离线储存怎么使用，工作原理能不能解释一下？

```
原理：HTML5的离线存储是基于一个新建的.appcache文件的，通过这个文件上的解析清单离线存储资源，这些资源就会像cookie一样被存储了下来。之后当网络在处于离线状态下时，浏览器会通过被离线存储的数据进行页面展示。
```

#### 请描述一下 cookies，sessionStorage 和 localStorage 的区别？

```
答案一：

cookie在浏览器和服务器间来回传递。 sessionStorage和localStorage不会
sessionStorage和localStorage的存储空间更大；
sessionStorage和localStorage有更多丰富易用的接口；
sessionStorage和localStorage各自独立的存储空间；

答案二：

 共同点：用于浏览器端存储的缓存数据

不同点：

(1)、存储内容是否发送到服务器端：当设置了Cookie后，数据会发送到服务器端，造成一定的宽带浪费；

     web storage,会将数据保存到本地，不会造成宽带浪费；

(2)、数据存储大小不同：Cookie数据不能超过4K,适用于会话标识；web storage数据存储可以达到5M;

(3)、数据存储的有效期限不同：cookie只在设置了Cookid过期时间之前一直有效，即使关闭窗口或者浏览器；

     sessionStorage,仅在关闭浏览器之前有效；localStorage,数据存储永久有效；

(4)、作用域不同：cookie和localStorage是在同源同窗口中都是共享的；sessionStorage不在不同的浏览器窗口中共享，即使是同一个页面；
```

#### 请你谈谈Cookie的弊端

    cookie虽然在持久保存客户端数据提供了方便，分担了服务器存储的负担，但还是有很多局限性的。
    第一：每个特定的域名下最多生成20个cookie

    1.IE6或更低版本最多20个cookie
    2.IE7和之后的版本最后可以有50个cookie。
    3.Firefox最多50个cookie
    4.chrome和Safari没有做硬性限制

    IE和Opera 会清理近期最少使用的cookie，Firefox会随机清理cookie。
    cookie的最大大约为4096字节，为了兼容性，一般不能超过4095字节。

    IE 提供了一种存储可以持久化用户数据，叫做uerData，从IE5.0就开始支持。每个数据最多128K，每个域名下最多1M。这个持久化数据放在缓存中，如果缓存没有清理，那么会一直存在。

    优点：极高的扩展性和可用性
    1.通过良好的编程，控制保存在cookie中的session对象的大小。
    2.通过加密和安全传输技术（SSL），减少cookie被破解的可能性。
    3.只在cookie中存放不敏感数据，即使被盗也不会有重大损失。
    4.控制cookie的生命期，使之不会永远有效。偷盗者很可能拿到一个过期的cookie。

    缺点：
    1.`Cookie`数量和长度的限制。每个domain最多只能有20条cookie，每个cookie长度不能超过4KB，否则会被截掉。
    2.安全性问题。如果cookie被人拦截了，那人就可以取得所有的session信息。即使加密也与事无补，因为拦截者并不需要知道cookie的意义，他只要原样转发cookie就可以达到目的了。
    3.有些状态不可能保存在客户端。例如，为了防止重复提交表单，我们需要在服务器端保存一个计数器。如果我们把这个计数器保存在客户端，那么它起不到任何作用。

#### Web Storage与Cookie相比存在的优势：

```
(1)、存储空间更大：IE8下每个独立的存储空间为10M，其他浏览器实现略有不同，但都比Cookie要大很多。

(2)、存储内容不会发送到服务器：当设置了Cookie后，Cookie的内容会随着请求一并发送的服务器，这对于本地存储的数据是一种带宽浪费。而Web Storage中的数据则仅仅是存在本地，不会与服务器发生任何交互。

(3)、更多丰富易用的接口：Web Storage提供了一套更为丰富的接口，如setItem,getItem,removeItem,clear等,使得数据操作更为简便。cookie需要自己封装。

(4)、独立的存储空间：每个域（包括子域）有独立的存储空间，各个存储空间是完全独立的，因此不会造成数据混乱。
```

#### 如何实现浏览器内多个标签页之间的通信?

```
调用localstorge、cookies等本地存储方式
```

#### 行内元素有哪些？块级元素有哪些？ 空\(void\)元素有那些？

```
1.CSS规范规定，每个元素都有display属性，确定该元素的类型，每个元素都有默认的display值， 比如div默认display属性值为―block，成为块级元素; span默认display属性值为―inline，是行内元素。
2.行内元素有：a b span img input select strong(强调的语气) 块级元素有：div ul ol li dl dt dd h1 h2 h3 h4 p 
3.知名的空元素：<br> <hr> <img> <input> <link> <meta>
4.鲜为人知的是：<area> <base> <col> <command> <embed> <keygen> <param> <source> <track> <wbr>
```

#### 页面导入样式时，使用link和@import有什么区别？

```
（1）link属于XHTML标签，除了加载CSS外，还能用于定义RSS, 定义rel连接属性等作用；而@import是CSS提供的，只能用于加载CSS;
（2）页面被加载的时，link会同时被加载，而@import引用的CSS会等到页面被加载完再加载;
（3）import是CSS2.1 提出的，只在IE5以上才能被识别，而link是XHTML标签，无兼容问题。
```

#### **Label的作用是什么？是怎么用的？（加for或包裹）**

```
元素定义标注（标记）。
label 元素不会向用户呈现任何特殊效果。不过，它为鼠标用户改进了可用性。如果您在 label 元素内点击文本，就会触发此控件。就是说，当用户选择该标签时，浏览器就会自动将焦点转到和标签相关的表单控件上。<label> 标签的 for 属性应当与相关元素的 id 属性相同。
```

#### **HTML5的form如何关闭自动完成功能？**

```
<form autocomplete="on|off">
```

#### 如何实现浏览器内多个标签页之间的通信? \(阿里\)

```
调用 localstorge、cookies 等本地存储方式
```

#### webSocket 如何兼容低浏览器？

```
Adobe Flash Socket 、 ActiveX HTMLFile (IE) 、 基于 multipart 编码发送 XHR 、 基于长轮询的 XHR
```

#### 页面可见性（Page Visibility）API 可以有哪些用途？

```
该API一个很好的用处就是能够在页面切换到不可见状态时暂停执行一些不必要的操作,以减少资源的浪费.
```

#### 浏览器本地存储

```
html5中的Web Storage包括了两种存储方式：sessionStorage和localStorage。

sessionStorage用于本地存储一个会话（session）中的数据，这些数据只有在同一个会话中的页面才能访问并且当会话结束后数据也随之销毁。因此sessionStorage不是一种持久化的本地存储，仅仅是会话级别的存储。

而localStorage用于持久化的本地存储，除非主动删除数据，否则数据是永远不会过期的。
```

#### web storage和cookie的区别

```
Web Storage的概念和cookie相似，区别是它是为了更大容量存储设计的。Cookie的大小是受限的，并且每次你请求一个新的页面的时候Cookie都会被发送过去，这样无形中浪费了带宽，另外cookie还需要指定作用域，不可以跨域调用。

除此之外，Web Storage拥有setItem,getItem,removeItem,clear等方法，不像cookie需要前端开发者自己封装setCookie，getCookie。

但是Cookie也是不可以或缺的：Cookie的作用是与服务器进行交互，作为HTTP规范的一部分而存在 ，而Web Storage仅仅是为了在本地“存储”数据而生

浏览器的支持除了IE７及以下不支持外，其他标准浏览器都完全支持(ie及FF需在web服务器里运行)，值得一提的是IE总是办好事，例如IE7、IE6中的UserData其实就是javascript本地存储的解决方案。通过简单的代码封装可以统一到所有的浏览器都支持web storage。

localStorage和sessionStorage都具有相同的操作方法，例如setItem、getItem和removeItem等
```

#### 你如何对网站的文件和资源进行优化？

```
期待的解决方案包括：
文件合并
文件最小化/文件压缩
使用 CDN 托管
缓存的使用（多个域名来提供缓存）
其他
```

#### 请说出三种减少页面加载时间的方法。

```
1.优化图片
2.图像格式的选择（GIF：提供的颜色较少，可用在一些对颜色要求不高的地方）
3.优化CSS（压缩合并css，如margin-top,margin-left...)
4.网址后加斜杠（如www.campr.com/目录，会判断这个“目录是什么文件类型，或者是目录。）
5.标明高度和宽度（如果浏览器没有找到这两个参数，它需要一边下载图片一边计算大小，如果图片很多，浏览器需要不断地调整页面。这不但影响速度，也影响浏览体验。
当浏览器知道了高度和宽度参数后，即使图片暂时无法显示，页面上也会腾出图片的空位，然后继续加载后面的内容。从而加载时间快了，浏览体验也更好了。）
6.减少http请求（合并文件，合并图片）。
```

#### 你都使用哪些工具来测试代码的性能？

```
可以使用Firefox developer Edition，也可以使用firebug配合Yslow使用，或者使用chrome的plugins
```

#### 简述一下src与href的区别

```
href 是指向网络资源所在位置，建立和当前元素（锚点）或当前文档（链接）之间的链接，用于超链接。

src是指向外部资源的位置，指向的内容将会嵌入到文档中当前标签所在位置；在请求src资源时会将其指向的资源下载并应用到文档内，例如js脚本，img图片和frame等元素。

当浏览器解析到该元素时，会暂停其他资源的下载和处理，直到将该资源加载、编译、执行完毕，图片和框架等元素也如此，类似于将所指向资源嵌入当前标签内。这也是为什么将js脚本放在底部而不是头部。
```

#### 请指出document load和document ready的区别？

```
共同点：这两种事件都代表的是页面文档加载时触发。

异同点：

ready 事件的触发，表示文档结构已经加载完成（不包含图片等非文字媒体文件）。

onload 事件的触发，表示页面包含图片等文件在内的所有元素都加载完成。
```



