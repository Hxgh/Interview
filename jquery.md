#### JQuery的源码看过吗？能不能简单概况一下它的实现原理？

```
原理就是对常用操作的封装，顺便解决了兼容性问题
```

#### jQuery 遍历

```
parent() 方法返回被选元素的直接父元素。

parents() 方法返回被选元素的所有祖先元素，它一路向上直到文档的根元素 (<html>)     .parents("标签")的那个父

parentsUntil() 方法返回介于两个给定元素之间的所有祖先元素。
```

#### jQuery.fn的init方法返回的this指的是什么对象？为什么要返回this？

```
答案一：https://segmentfault.com/q/1010000003700711
答案二：https://stackoverflow.com/questions/4754560/help-understanding-jquerys-jquery-fn-init-why-is-init-in-fn
```

#### jquery中如何将数组转化为json字符串，然后再转化回来？

```
jQuery 中没有提供这个功能，所以需要先编写两个 jQuery 的扩展：
$.fn.stringifyArray = function(array) {
    return JSON.stringify(array)
}
$.fn.parseArray = function(array) {
    return JSON.parse(array)
}
//
然后调用:
$("").stringifyArray(array)
```

#### jQuery 的属性拷贝（extend）的实现原理是什么？如何实现深拷贝？

```
答案一：https://www.cnblogs.com/yuqingfamily/p/5813650.html
```

#### jquery.extend 与 jquery.fn.extend的区别？

```
答案一:http://www.jb51.net/article/69369.htm
```

#### 谈一下Jquery中的bind\(\),live\(\),delegate\(\),on\(\)的区别？

```
bind() 方法为被选元素添加一个或多个事件处理程序，并规定事件发生时运行的函数。
on() 方法事件处理程序到当前选定的jQuery对象中的元素。
delegate() 方法为指定的元素（属于被选元素的子元素）添加一个或多个事件处理程序，并规定当这些事件发生时运行的函数。
live() 方法为被选元素附加一个或多个事件处理程序，并规定当这些事件发生时运行的函数

http://www.jb51.net/article/120018.htm
```

#### JQuery一个对象可以同时绑定多个事件,这是如何实现的?

```
(未解决)
```

#### 是否了解针对 jQuery 性能的优化方法？

```
基于Class的选择性的性能相对于Id选择器开销很大，因为需遍历所有DOM元素。
//
频繁操作的DOM，先缓存起来再操作。用Jquery的链式调用更好。
 比如：var str=$("a").attr("href");
 //
for (var i = size; i < arr.length; i++) {}
for 循环每一次循环都查找了数组 (arr) 的.length 属性，在开始循环的时候设置一个变量来存储这个数字，可以让循环跑得更快：
for (var i = size, length = arr.length; i < length; i++) {}
```

#### jQuery 与 jQuery UI 有何区别？

    `jQuery`是一个js库，主要提供的功能是选择器，属性修改和事件绑定等等。
    `jQuery UI`则是在jQuery的基础上，利用jQuery的扩展性，设计的插件。提供了一些常用的界面元素，诸如对话框、拖动行为、改变大小行为等等

#### jQuery UI 如何自定义组件？

```
答案一：https://yq.aliyun.com/ziliao/138127
```



