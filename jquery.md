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



