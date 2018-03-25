#### JQuery的源码看过吗？能不能简单概况一下它的实现原理？

```
原理就是对常用操作的封装，顺便解决了兼容性问题
```

#### jQuery 库中的 $\(\) 是什么？

```
$() 函数是 jQuery() 函数的别称。$() 函数用于将任何对象包裹成 jQuery 对象，接着你就被允许调用定义在 jQuery 对象上的多个不同方法。你可以将一个选择器字符串传入 $() 函数，它会返回一个包含所有匹配的 DOM 元素数组的 jQuery 对象。
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

#### 谈一下Jquery事件委托方法中的bind\(\),live\(\),delegate\(\),on\(\)的区别？

```
bind() 方法为被选元素添加一个或多个事件处理程序，并规定事件发生时运行的函数。
on() 方法事件处理程序到当前选定的jQuery对象中的元素。
delegate() 方法为指定的元素（属于被选元素的子元素）添加一个或多个事件处理程序，并规定当这些事件发生时运行的函数。
live() 方法为被选元素附加一个或多个事件处理程序，并规定当这些事件发生时运行的函数

(1)、bind 【jQuery 1.3之前】

定义和用法：主要用于给选择到的元素上绑定特定事件类型的监听函数；

语法：bind(type,[data],function(eventObject))；

特点：

　　(1)、适用于页面元素静态绑定。只能给调用它的时候已经存在的元素绑定事件，不能给未来新增的元素绑定事件。

　　(2)、当页面加载完的时候，你才可以进行bind()，所以可能产生效率问题。

实例如下：$( "#members li a" ).bind( "click", function( e ) {} );

(2)、live 【jQuery 1.3之后】

定义和用法：主要用于给选择到的元素上绑定特定事件类型的监听函数；

语法：live(type, [data], fn);

特点：

　　(1)、live方法并没有将监听器绑定到自己(this)身上，而是绑定到了this.context上了。

　　(2)、live正是利用了事件委托机制来完成事件的监听处理，把节点的处理委托给了document，新添加的元素不必再绑定一次监听器。

　　(3)、使用live（）方法但却只能放在直接选择的元素后面，不能在层级比较深，连缀的DOM遍历方法后面使用，即$(“ul”").live...可以，但$("body").find("ul").live...不行； 

实例如下：$( document ).on( "click", "#members li a", function( e ) {} );

(3)、delegate 【jQuery 1.4.2中引入】

定义和用法：将监听事件绑定在就近的父级元素上

语法：delegate(selector,type,[data],fn)

特点：

　　(1)、选择就近的父级元素，因为事件可以更快的冒泡上去，能够在第一时间进行处理。

　　(2)、更精确的小范围使用事件代理，性能优于.live()。可以用在动态添加的元素上。

实例如下：

$("#info_table").delegate("td","click",function(){/*显示更多信息*/});

$("table").find("#info").delegate("td","click",function(){/*显示更多信息*/});

(4)、on 【1.7版本整合了之前的三种方式的新事件绑定机制】

定义和用法：将监听事件绑定到指定元素上。

语法：on(type,[selector],[data],fn)

实例如下：$("#info_table").on("click","td",function(){/*显示更多信息*/});参数的位置写法与delegate不一样。

说明：on方法是当前JQuery推荐使用的事件绑定方法，附加只运行一次就删除函数的方法是one()。

总结：.bind(), .live(), .delegate(),.on()分别对应的相反事件为：.unbind(),.die(), .undelegate(),.off()


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

#### 如何找到所有 HTML select 标签的选中项？

```
$('[name=selectname] :selected')
```

#### $\(this\) 和 this 关键字在 jQuery 中有何不同？

```
$(this) 返回一个 jQuery 对象，你可以对它调用多个 jQuery 方法，比如用 text() 获取文本，用val() 获取值等等。

而 this 代表当前元素，它是 JavaScript 关键词中的一个，表示上下文中的当前 DOM 元素。你不能对它调用 jQuery 方法，直到它被 $() 函数包裹，例如 $(this)
```

#### jquery怎么移除标签onclick属性？

```js
获得a标签的onclick属性: $("a").attr("onclick")

删除onclick属性：$("a").removeAttr("onclick");

设置onclick属性：$("a").attr("onclick","test();");
```

#### jquery中addClass,removeClass,toggleClass的使用

```js
$(selector).addClass(class)：为每个匹配的元素添加指定的类名

$(selector).removeClass(class)：从所有匹配的元素中删除全部或者指定的类，删除class中某个值；

$(selector).toggleClass(class)：如果存在（不存在）就删除（添加）一个类

$(selector).removeAttr(class);删除class这个属性；
```

#### JQuery有几种选择器?

```js
(2)、层次选择器：parent > child，prev + next ，prev ~ siblings

(3)、基本过滤器选择器：:first，:last ，:not ，:even ，:odd ，:eq ，:gt ，:lt

(4)、内容过滤器选择器： :contains ，:empty ，:has ，:parent

(5)、可见性过滤器选择器：:hidden ，:visible

(6)、属性过滤器选择器：[attribute] ，[attribute=value] ，[attribute!=value] ，[attribute^=value] ，[attribute$=value] ，[attribute*=value]

(7)、子元素过滤器选择器：:nth-child ，:first-child ，:last-child ，:only-child

(8)、表单选择器： :input ，:text ，:password ，:radio ，:checkbox ，:submit 等；

(9)、表单过滤器选择器：:enabled ，:disabled ，:checked ，:selected
```

#### jQuery中的Delegate\(\)函数有什么作用？

```
delegate()会在以下两个情况下使用到：

1、如果你有一个父元素，需要给其下的子元素添加事件，这时你可以使用delegate()了，代码如下：

$("ul").delegate("li", "click", function(){ $(this).hide(); });

2、当元素在当前页面中不可用时，可以使用delegate()
```

#### $\(document\).ready\(\)方法和window.onload有什么区别？

```
(1)、window.onload方法是在网页中所有的元素(包括元素的所有关联文件)完全加载到浏览器后才执行的。

(2)、$(document).ready() 方法可以在DOM载入就绪时就对其进行操纵，并调用执行绑定的函数。
```

#### 如何用jQuery禁用浏览器的前进后退按钮？

```js
实现代码如下：

<script type="text/javascript" language="javascript">
　　$(document).ready(function() {
　　　　window.history.forward(1);
  　　　　//OR window.history.forward(-1);
　　});
</script>
```

#### jquery中$.get\(\)提交和$.post\(\)提交有区别吗？

```
相同点：都是异步请求的方式来获取服务端的数据；

异同点：

1、请求方式不同：$.get() 方法使用GET方法来进行异步请求的。$.post() 方法使用POST方法来进行异步请求的。
2、参数传递方式不同：get请求会将参数跟在URL后进行传递，而POST请求则是作为HTTP消息的实体内容发送给Web服务器的，这种传递是对用户不可见的。
3、数据传输大小不同：get方式传输的数据大小不能超过2KB 而POST要大的多
4、安全问题： GET 方式请求的数据会被浏览器缓存起来，因此有安全问题。
```

#### 写出一个简单的$.ajax\(\)的请求方式？

```js
$.ajax({
    url:'http://www.baidu.com',
    type:'POST',
    data:data,
    cache:true,
    headers:{},
    beforeSend：function(){},
    success:function(){},
    error:function(){},
    complete:function(){}
});
```



