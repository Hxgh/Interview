# 3.JavaScript基础

#### 介绍js的基本数据类型

```
Undefined、Null、Boolean、Number、String
```

#### 介绍js有哪些内置对象？

```
Object 是 JavaScript 中所有对象的父对象

数据封装类对象：Object、Array、Boolean、Number 和 String
其他对象：Function、Arguments、Math、Date、RegExp、Error
```

#### 说几条写JavaScript的基本规范？

```
1.不要在同一行声明多个变量。
2.请使用 ===/!==来比较true/false或者数值
3.使用对象字面量替代new Array这种形式
4.不要使用全局函数。
5.Switch语句必须带有default分支
6.函数不应该有时候有返回值，有时候没有返回值。
7.For循环必须使用大括号
8.If语句必须使用大括号
9.for-in循环中的变量 应该使用var关键字明确限定作用域，从而避免作用域污染。
```

#### JavaScript原型，原型链 ? 有什么特点？

```
每个对象都会在其内部初始化一个属性，就是prototype(原型)，当我们访问一个对象的属性时，
如果这个对象内部不存在这个属性，那么他就会去prototype里找这个属性，这个prototype又会有自己的prototype，
于是就这样一直找下去，也就是我们平时所说的原型链的概念。
关系：instance.constructor.prototype = instance.__proto__

特点：
JavaScript对象是通过引用来传递的，我们创建的每个新对象实体中并没有一份属于自己的原型副本。当我们修改原型时，与之相关的对象也会继承这一改变。


 当我们需要一个属性的时，Javascript引擎会先看当前对象中是否有这个属性， 如果没有的话，
 就会查找他的Prototype对象是否有这个属性，如此递推下去，一直检索到 Object 内建对象。
    function Func(){}
    Func.prototype.name = "Sean";
    Func.prototype.getInfo = function() {
      return this.name;
    }
    var person = new Func();//现在可以参考var person = Object.create(oldObject);
    console.log(person.getInfo());//它拥有了Func的属性和方法
    //"Sean"
    console.log(Func.prototype);
    // Func { name="Sean", getInfo=function()}
```

#### JavaScript有几种类型的值？，你能画一下他们的内存图吗？

```
栈：原始数据类型（Undefined，Null，Boolean，Number、String） 
堆：引用数据类型（对象、数组和函数）

两种类型的区别是：存储位置不同；
原始数据类型直接存储在栈(stack)中的简单数据段，占据空间小、大小固定，属于被频繁使用数据，所以放入栈中存储；
引用数据类型存储在堆(heap)中的对象,占据空间大、大小不固定,如果存储在栈中，将会影响程序运行的性能；引用数据类型在栈中存储了指针，该指针指向堆中该实体的起始地址。当解释器寻找引用值时，会首先检索其
在栈中的地址，取得地址后从堆中获得实体

这里有个解析堆和栈的链接：https://www.zhihu.com/question/19729973
```

#### javascript对象的几种创建方式

```
1，工厂模式
2，构造函数模式
3，原型模式
4，混合构造函数和原型模式
5，动态原型模式
6，寄生构造函数模式
7，稳妥构造函数模式
```

#### Javascript 继承方法

```
答案一：
1，原型链继承
2，借用构造函数继承
3，组合继承(原型+借用构造)
4，原型式继承
5，寄生式继承
6，寄生组合式继承

答案二：
http://www.jb51.net/article/81766.htm

答案三：
1、构造继承
2、原型继承
3、实例继承
4、拷贝继承

原型prototype机制或apply和call方法去实现较简单，建议使用构造函数与原型混合方式。

 function Parent(){
        this.name = 'wang';
    }

    function Child(){
        this.age = 28;
    }
    Child.prototype = new Parent();//继承了Parent，通过原型

    var demo = new Child();
    alert(demo.age);
    alert(demo.name);//得到被继承的属性
  }

答案四：

javascript创建对象简单的说,无非就是使用内置对象或各种自定义对象，当然还可以用JSON；但写法有很多种，也能混合使用。


1、对象字面量的方式   

    person={firstname:"Mark",lastname:"Yun",age:25,eyecolor:"black"};

2、用function来模拟无参的构造函数

    function Person(){}
    var person=new Person();//定义一个function，如果使用new"实例化",该function可以看作是一个Class
    person.name="Mark";
    person.age="25";
    person.work=function(){
    alert(person.name+" hello...");
    }
    person.work();

3、用function来模拟参构造函数来实现（用this关键字定义构造的上下文属性）

    function Pet(name,age,hobby){
       this.name=name;//this作用域：当前对象
       this.age=age;
       this.hobby=hobby;
       this.eat=function(){
          alert("我叫"+this.name+",我喜欢"+this.hobby+",是个程序员");
       }
    }
    var maidou =new Pet("麦兜",25,"coding");//实例化、创建对象
    maidou.eat();//调用eat方法


4、用工厂方式来创建（内置对象）

     var wcDog =new Object();
     wcDog.name="旺财";
     wcDog.age=3;
     wcDog.work=function(){
       alert("我是"+wcDog.name+",汪汪汪......");
     }
     wcDog.work();


5、用原型方式来创建

    function Dog(){

     }
     Dog.prototype.name="旺财";
     Dog.prototype.eat=function(){
     alert(this.name+"是个吃货");
     }
     var wangcai =new Dog();
     wangcai.eat();


5、用混合方式来创建

    function Car(name,price){
      this.name=name;
      this.price=price; 
    }
     Car.prototype.sell=function(){
       alert("我是"+this.name+"，我现在卖"+this.price+"万元");
      }
    var camry =new Car("凯美瑞",27);
    camry.sell();
```

#### javascript里面的继承怎么实现，如何避免原型链上面的对象共享

```
用构造函数和原型链的混合模式去实现继承，避免对象共享可以参考经典的extend()函数，很多前端框架都有封装的，就是用一个空函数当做中间变量
```

#### Javascript作用链域?

```
全局函数无法查看局部函数的内部细节，但局部函数可以查看其上层的函数细节，直至全局细节。
当需要从局部函数查找某一属性或方法时，如果当前作用域没有找到，就会上溯到上层作用域查找，
直至全局函数，这种组织形式就是作用域链。
```

#### 谈谈This对象的理解

```
1.this总是指向函数的直接调用者（而非间接调用者）；
2.如果有new关键字，this指向new出来的那个对象；
3.在事件中，this指向触发这个事件的对象，特殊的是，IE中的attachEvent中的this总是指向全局对象Window；
4.this引用的是函数所执行的环境对象（在全局作用域中this对象就是window）
```

#### eval是做什么的？

```
它的功能是把对应的字符串解析成JS代码并运行；
应该避免使用eval，不安全，非常耗性能（2次，一次解析成js语句，一次执行）。
由JSON字符串转换为JSON对象的时候可以用eval，var obj =eval('('+ str +')');
```

#### 什么是window对象? 什么是document对象?

```
https://blog.csdn.net/jcx5083761/article/details/41243697
```

#### null，undefined 的区别？

```
null        表示一个对象被定义了，值为“空值”，null是空对象指针
undefined   表示不存在这个值，未声明和未定义的对象会返回undefined


typeof undefined
    //"undefined"
    undefined :是一个表示"无"的原始值或者说表示"缺少值"，就是此处应该有一个值，但是还没有定义。当尝试读取时会返回 undefined； 
    例如变量被声明了，但没有赋值时，就等于undefined

typeof null
    //"object"
    null : 是一个对象(空对象, 没有任何属性和方法)；
    例如作为函数的参数，表示该函数的参数不是对象；

注意：
    在验证null时，一定要使用　=== ，因为 == 无法分别 null 和　undefined
    null ==　undefined ，返回true
    null ==　undefined ，返回false
```

#### 写一个通用的事件侦听器函数

```
// event(事件)工具集，来源：github.com/markyun
    markyun.Event = {
        // 页面加载完成后
        readyEvent : function(fn) {
            if (fn==null) {
                fn=document;
            }
            var oldonload = window.onload;
            if (typeof window.onload != 'function') {
                window.onload = fn;
            } else {
                window.onload = function() {
                    oldonload();
                    fn();
                };
            }
        },
        // 视能力分别使用dom0||dom2||IE方式 来绑定事件
        // 参数： 操作的元素,事件名称 ,事件处理程序
        addEvent : function(element, type, handler) {
            if (element.addEventListener) {
                //事件类型、需要执行的函数、是否捕捉
                element.addEventListener(type, handler, false);
            } else if (element.attachEvent) {
                element.attachEvent('on' + type, function() {
                    handler.call(element);
                });
            } else {
                element['on' + type] = handler;
            }
        },
        // 移除事件
        removeEvent : function(element, type, handler) {
            if (element.removeEventListener) {
                element.removeEventListener(type, handler, false);
            } else if (element.datachEvent) {
                element.detachEvent('on' + type, handler);
            } else {
                element['on' + type] = null;
            }
        },
        // 阻止事件 (主要是事件冒泡，因为IE不支持事件捕获)
        stopPropagation : function(ev) {
            if (ev.stopPropagation) {
                ev.stopPropagation();
            } else {
                ev.cancelBubble = true;
            }
        },
        // 取消事件的默认行为
        preventDefault : function(event) {
            if (event.preventDefault) {
                event.preventDefault();
            } else {
                event.returnValue = false;
            }
        },
        // 获取事件目标
        getTarget : function(event) {
            return event.target || event.srcElement;
        },
        // 获取event对象的引用，取到事件的所有信息，确保随时能使用event；
        getEvent : function(e) {
            var ev = e || window.event;
            if (!ev) {
                var c = this.getEvent.caller;
                while (c) {
                    ev = c.arguments[0];
                    if (ev && Event == ev.constructor) {
                        break;
                    }
                    c = c.caller;
                }
            }
            return ev;
        }
    };
```

#### \["1", "2", "3"\].map\(parseInt\) 答案是多少？

```
[1, NaN, NaN]
因为 parseInt 需要两个参数 (val, radix)，
其中 radix 表示解析时用的基数。
map 传了 3 个 (element, index, array)，对应的 radix 不合法导致解析失败。
```

#### 事件是？IE与火狐的事件机制有什么区别？ 如何阻止冒泡？

```
1. 我们在网页中的某个操作（有的操作对应多个事件）。例如：当我们点击一个按钮就会产生一个事件。是可以被 JavaScript 侦测到的行为。
2. 事件处理机制：IE是事件冒泡、Firefox同时支持两种事件模型，也就是：捕获型事件和冒泡型事件；
3. ev.stopPropagation();（旧ie的方法 ev.cancelBubble = true;）
```

#### 什么是闭包（closure），为什么要用它？

```
闭包是指有权访问另一个函数作用域中变量的函数，创建闭包的最常见的方式就是在一个函数内创建另一个函数，通过另一个函数访问这个函数的局部变量,利用闭包可以突破作用链域，将函数内部的变量和方法传递到外部。

闭包的特性：

1.函数内再嵌套函数
2.内部函数可以引用外层的参数和变量
3.参数和变量不会被垃圾回收机制回收
4.使用闭包可以访问函数中的变量。
5.可以使变量长期保存在内存中，生命周期比较长。

//li节点的onclick事件都能正确的弹出当前被点击的li索引
 <ul id="testUL">
    <li> index = 0</li>
    <li> index = 1</li>
    <li> index = 2</li>
    <li> index = 3</li>
</ul>
<script type="text/javascript">
    var nodes = document.getElementsByTagName("li");
    for(i = 0;i<nodes.length;i+= 1){
        nodes[i].onclick = function(){
            console.log(i+1);//不用闭包的话，值每次都是4
        }(i);
    }
</script>



执行say667()后,say667()闭包内部变量会存在,而闭包内部函数的内部变量不会存在
使得Javascript的垃圾回收机制GC不会收回say667()所占用的资源
因为say667()的内部函数的执行需要依赖say667()中的变量
这是对闭包作用的非常直白的描述

  function say667() {
    // Local variable that ends up within closure
    var num = 666;
    var sayAlert = function() {
        alert(num);
    }
    num++;
    return sayAlert;
}

 var sayAlert = say667();
 sayAlert()//执行结果应该弹出的667
```

#### 变量的作用域

```
要理解闭包，首先必须理解Javascript特殊的变量作用域。

变量的作用域分类：全局变量和局部变量。

特点：

1、函数内部可以读取函数外部的全局变量；在函数外部无法读取函数内的局部变量。

2、函数内部声明变量的时候，一定要使用var命令。如果不用的话，你实际上声明了一个全局变量！

 5、使用闭包的注意点

1）滥用闭包，会造成内存泄漏：由于闭包会使得函数中的变量都被保存在内存中，内存消耗很大，所以不能滥用闭包，否则会造成网页的性能问题，在IE中可能导致内存泄露。解决方法是，在退出函数之前，将不使用的局部变量全部删除。

2）会改变父函数内部变量的值。所以，如果你把父函数当作对象（object）使用，把闭包当作它的公用方法（Public Method），把内部变量当作它的私有属性（private value），这时一定要小心，不要随便改变父函数内部变量的值。
```

#### javascript 代码中的"use strict";是什么意思 ? 使用它区别是什么？

```
use strict是一种ECMAscript 5 添加的（严格）运行模式,这种模式使得 Javascript 在更严格的条件下运行,

使JS编码更加规范化的模式,消除Javascript语法的一些不合理、不严谨之处，减少一些怪异行为。
默认支持的糟糕特性都会被禁用，比如不能用with，也不能在意外的情况下给全局变量赋值;
全局变量的显示声明,函数必须声明在顶层，不允许在非函数代码块内声明函数,arguments.callee也不允许使用；
消除代码运行的一些不安全之处，保证代码运行的安全,限制函数中的arguments修改，严格模式下的eval函数的行为和非严格模式的也不相同;

提高编译器效率，增加运行速度；
为未来新版本的Javascript标准化做铺垫。
```

#### 如何判断一个对象是否属于某个类？

```
使用instanceof （待完善）
if(a instanceof Person){
   alert('yes');
}
```

#### new操作符具体干了什么呢?

```
1、创建一个空对象，并且 this 变量引用该对象，同时还继承了该函数的原型。
2、属性和方法被加入到 this 引用的对象中。
3、新创建的对象由 this 所引用，并且最后隐式的返回 this 。

var obj  = {};
obj.__proto__ = Base.prototype;
Base.call(obj);
```

#### Javascript中，有一个函数，执行时对象查找时，永远不会去查找原型，这个函数是？

```
hasOwnProperty

javaScript中hasOwnProperty函数方法是返回一个布尔值，指出一个对象是否具有指定名称的属性。此方法无法检查该对象的原型链中是否具有该属性；该属性必须是对象本身的一个成员。
使用方法：
object.hasOwnProperty(proName)
其中参数object是必选项。一个对象的实例。
proName是必选项。一个属性名称的字符串值。

如果 object 具有指定名称的属性，那么JavaScript中hasOwnProperty函数方法返回 true，反之则返回 false。
```

#### JSON 的了解？

```
JSON(JavaScript Object Notation) 是一种轻量级的数据交换格式。
它是基于JavaScript的一个子集。数据格式简单, 易于读写, 占用带宽小
如：{"age":"12", "name":"back"}

JSON字符串转换为JSON对象:
var obj =eval('('+ str +')');
var obj = str.parseJSON();
var obj = JSON.parse(str);

JSON对象转换为JSON字符串：
var last=obj.toJSONString();
var last=JSON.stringify(obj);
```

#### js延迟加载的方式有哪些？

```
defer和async、动态创建DOM方式（用得最多）、按需异步载入js
```

#### Ajax 是什么? 如何创建一个Ajax？

```js
ajax的全称：Asynchronous Javascript And XML。
异步传输+js+xml。
所谓异步，在这里简单地解释就是：向服务器发送请求的时候，我们不必等待结果，而是可以同时做其他的事情，等到有了结果它自己会根据设定进行后续操作，与此同时，页面是不会发生整页刷新的，提高了用户体验。

(1)创建XMLHttpRequest对象,也就是创建一个异步调用对象.

(2)创建一个新的HTTP请求,并指定该HTTP请求的方法、URL及验证信息.

(3)设置响应HTTP请求状态变化的函数.

(4)发送HTTP请求.

(5)获取异步调用返回的数据.

(6)使用JavaScript和DOM实现局部刷新.

var xmlHttp = new XMLHttpRequest();

  xmlHttp.open('GET','demo.php','true');

  xmlHttp.send()

  xmlHttp.onreadystatechange = function(){

      if(xmlHttp.readyState === 4 & xmlHttp.status === 200){

      }

  }

使用promise封装

function getJSON(url) { 
    return new Promise(function(resolve, reject) { 
        var XHR = new XMLHttpRequest(); 
        XHR.open('GET', url, true); 
        XHR.send(); 

        XHR.onreadystatechange = function() { 
            if (XHR.readyState == 4) { 
                if (XHR.status == 200) { 
                    try { 
                        var response = JSON.parse(XHR.responseText); 
                        resolve(response); 
                    } catch (e) { 
                        reject(e); 
                    } 
                } else { 
                    reject(new Error(XHR.statusText)); 
                } 
            } 
        } 
    }) 
} 

getJSON(url).then(res => console.log(res)); 
　　
当前状态readystate

0 代表未初始化。 还没有调用 open 方法
1 代表正在加载。 open 方法已被调用，但 send 方法还没有被调用
2 代表已加载完毕。send 已被调用。请求已经开始
3 代表交互中。服务器正在发送响应
4 代表完成。响应发送完毕

常用状态码status

404 没找到页面(not found)
403 禁止访问(forbidden)
500 内部服务器出错(internal service error)
200 一切正常(ok)
304 没有被修改(not modified)(服务器返回304状态，表示源文件没有被修改）
```

#### Ajax的优缺点及工作原理？

```
定义和用法:

AJAX = Asynchronous JavaScript and XML（异步的 JavaScript 和 XML）。Ajax 是一种用于创建快速动态网页的技术。Ajax 是一种在无需重新加载整个网页的情况下，能够更新部分网页的技术。

传统的网页（不使用 Ajax）如果需要更新内容，必须重载整个网页页面。

优点：

1.减轻服务器的负担,按需取数据,最大程度的减少冗余请求

2.局部刷新页面,减少用户心理和实际的等待时间,带来更好的用户体验

3.基于xml标准化,并被广泛支持,不需安装插件等,进一步促进页面和数据的分离

缺点：

1.AJAX大量的使用了javascript和ajax引擎,这些取决于浏览器的支持.在编写的时候考虑对浏览器的兼容性.

2.AJAX只是局部刷新,所以页面的后退按钮是没有用的.

3.对流媒体还有移动设备的支持不是太好等

AJAX的工作原理：

1.创建ajax对象（XMLHttpRequest/ActiveXObject(Microsoft.XMLHttp)）

2.判断数据传输方式(GET/POST)

3.打开链接 open()

4.发送 send()

5.当ajax对象完成第四步（onreadystatechange）数据接收完成，判断http响应状态（status）200-300之间或者304（缓存）执行回调函数
```

#### 同步和异步的区别?

```
同步的概念应该是来自于OS中关于同步的概念:不同进程为协同完成某项工作而在先后次序上调整(通过阻塞,唤醒等方式).同步强调的是顺序性.谁先谁后.异步则不存在这种顺序性.

同步：浏览器访问服务器请求，用户看得到页面刷新，重新发请求,等请求完，页面刷新，新内容出现，用户看到新内容,进行下一步操作。

异步：浏览器访问服务器请求，用户正常操作，浏览器后端进行请求。等请求完，页面不刷新，新内容也会出现，用户看到新内容。

（待完善）
```

#### 如何解决跨域问题?

```
概念：只要协议、域名、端口有任何一个不同，都被当作是不同的域。
解决方案：
    跨域资源共享（CORS）
    通过jsonp跨域
    JSONP的优缺点
    CORS和JSONP对比
    通过修改document.domain来跨子域
    使用window.name来进行跨域
    使用HTML5的window.postMessage方法跨域

详解：https://segmentfault.com/a/1190000000718840
```

#### 模块化开发怎么做？

```
未解决问题！

详解：https://segmentfault.com/a/1190000000733959
```

#### AMD（Modules/Asynchronous-Definition）、CMD（Common Module Definition）规范区别？

```
AMD 规范在这里：https://github.com/amdjs/amdjs-api/wiki/AMD

CMD 规范在这里：https://github.com/seajs/seajs/issues/242

Asynchronous Module Definition，异步模块定义，所有的模块将被异步加载，模块加载不影响后面语句运行。所有依赖某些模块的语句均放置在回调函数中。

 区别：

    1. 对于依赖的模块，AMD 是提前执行，CMD 是延迟执行。不过 RequireJS 从 2.0 开始，也改成可以延迟执行（根据写法不同，处理方式不同）。CMD 推崇 as lazy as possible.
    2. CMD 推崇依赖就近，AMD 推崇依赖前置。看代码：

// CMD
define(function(require, exports, module) {
    var a = require('./a')
    a.doSomething()
    // 此处略去 100 行
    var b = require('./b') // 依赖可以就近书写
    b.doSomething()
    // ...
})

// AMD 默认推荐
define(['./a', './b'], function(a, b) { // 依赖必须一开始就写好
    a.doSomething()
    // 此处略去 100 行
    b.doSomething()
    // ...
})
```

#### 谈谈你对 JavaScript 中的模块规范 CommonJS、AMD、CMD 的了解？

```
//个人拙见
|   CommonJS   |   AMD   |   CMD   |
|--------------|---------|---------|
|    Node.js   |RequireJS|  SeaJS  |

详解：
    浅析JS中的模块规范（CommonJS，AMD，CMD）：https://www.2cto.com/kf/201411/348276.html
    关于 CommonJS AMD CMD UMDrequireJS的核心原理是什么？：https://my.oschina.net/felumanman/blog/263330?p=1
```

#### 异步加载JS的方式有哪些？

```
答案一：

(1) defer，只支持IE

(2) async：

(3) 创建script，插入到DOM中，加载完毕后callBack

答案二：

https://segmentfault.com/a/1190000008473682
```

#### documen.write和 innerHTML的区别？

```
document.write只能重绘整个页面

innerHTML可以重绘页面的一部分
```

#### DOM操作——怎样添加、移除、移动、复制、创建和查找节点?

```
（1）创建新节点
  createDocumentFragment()    //创建一个DOM片段
  createElement()   //创建一个具体的元素
  createTextNode()   //创建一个文本节点
（2）添加、移除、替换、插入
  appendChild()
  removeChild()
  replaceChild()
  insertBefore() //在已有的子节点前插入一个新的子节点
（3）查找
  getElementsByTagName()    //通过标签名称
  getElementsByName()    //通过元素的Name属性的值(IE容错能力较强，会得到一个数组，其中包括id等于name值的)
  getElementById()    //通过元素Id，唯一性
```

#### .call\(\) 和 .apply\(\) 的区别？

```
答案一：

例子中用 add 来替换 sub，add.call(sub,3,1) == add(3,1) ，所以运行结果为：alert(4);

注意：js 中的函数其实是对象，函数名是对 Function 对象的引用。

function add(a,b)
{
    alert(a+b);
}

function sub(a,b)
{
    alert(a-b);
}

add.call(sub,3,1);

答案二：

apply()
    接收两个参数
        在其中运行的函数的作用域
        参数数组：可以是Array的实例，也可以是arguments
    在严格模式下，this值不会转型为window，除非明确把函数添加到某个对象或者apply()或call()，否则this的值将是undefined
call()
    和apply()作用相同，但是从第二个参数开依次列举出来
```

#### JS 数组和对象有哪些原生方法，列举一下？

```
答案一：
参考mindnode文件，object，array，data，function等不同的方式

答案二：
http://www.jb51.net/article/84164.htm
```

#### **JavaScript 数组\(Array\)对象**

```
Array 对象属性

constructor 返回对创建此对象的数组函数的引用。
length 设置或返回数组中元素的数目。
prototype 使您有能力向对象添加属性和方法。

Array 对象方法

concat() 连接两个或更多的数组，并返回结果。
join() 把数组的所有元素放入一个字符串。元素通过指定的分隔符进行分隔。
pop() 删除并返回数组的最后一个元素。  
shift() 删除并返回数组的第一个元素
push() 向数组的末尾添加一个或更多元素，并返回新的长度。
unshift() 向数组的开头添加一个或更多元素，并返回新的长度。
reverse() 颠倒数组中元素的顺序。
slice() 从某个已有的数组返回选定的元素
sort() 对数组的元素进行排序
splice() 删除元素，并向数组添加新元素。
toSource() 返回该对象的源代码。
toString() 把数组转换为字符串，并返回结果。
toLocaleString() 把数组转换为本地数组，并返回结果。
valueOf() 返回数组对象的原始值


详细：http://www.w3school.com.cn/jsref/jsref_obj_array.asp
```

#### JS实现数组去重

```js
方法一：
双层循环，外层循环元素，内层循环时比较值
如果有相同的值则跳过，不相同则push进数组
Array.prototype.distinct = function(){
 var arr = this,
  result = [],
  i,
  j,
  len = arr.length;
 for(i = 0; i < len; i++){
  for(j = i + 1; j < len; j++){
   if(arr[i] === arr[j]){
    j = ++i;
   }
  }
  result.push(arr[i]);
 }
 return result;
}
var arra = [1,2,3,4,4,1,1,2,1,1,1];
arra.distinct();    //返回[3,4,2,1]

方法二：利用splice直接在原数组进行操作
双层循环，外层循环元素，内层循环时比较值
值相同时，则删去这个值
注意点:删除元素之后，需要将数组的长度也减1.
Array.prototype.distinct = function (){
 var arr = this,
  i,
  j,
  len = arr.length;
 for(i = 0; i < len; i++){
  for(j = i + 1; j < len; j++){
   if(arr[i] == arr[j]){
    arr.splice(j,1);
    len--;
    j--;
   }
  }
 }
 return arr;
};
var a = [1,2,3,4,5,6,5,3,2,4,56,4,1,2,1,1,1,1,1,1,];
var b = a.distinct();
console.log(b.toString()); //1,2,3,4,5,6,56
优点：简单易懂
缺点：占用内存高，速度慢

方法三：利用对象的属性不能相同的特点进行去重
Array.prototype.distinct = function (){
 var arr = this,
  i,
  obj = {},
  result = [],
  len = arr.length;
 for(i = 0; i< arr.length; i++){
  if(!obj[arr[i]]){ //如果能查找到，证明数组元素重复了
   obj[arr[i]] = 1;
   result.push(arr[i]);
  }
 }
 return result;
};
var a = [1,2,3,4,5,6,5,3,2,4,56,4,1,2,1,1,1,1,1,1,];
var b = a.distinct();
console.log(b.toString()); //1,2,3,4,5,6,56

方法四：数组递归去重
运用递归的思想
先排序，然后从最后开始比较，遇到相同，则删除
Array.prototype.distinct = function (){
 var arr = this,
  len = arr.length;
 arr.sort(function(a,b){  //对数组进行排序才能方便比较
  return a - b;
 })
 function loop(index){
  if(index >= 1){
   if(arr[index] === arr[index-1]){
    arr.splice(index,1);
   }
   loop(index - 1); //递归loop函数进行去重
  }
 }
 loop(len-1);
 return arr;
};
var a = [1,2,3,4,5,6,5,3,2,4,56,4,1,2,1,1,1,1,1,1,56,45,56];
var b = a.distinct();
console.log(b.toString());  //1,2,3,4,5,6,45,56

方法五：利用indexOf以及forEach
Array.prototype.distinct = function (){
 var arr = this,
  result = [],
  len = arr.length;
 arr.forEach(function(v, i ,arr){  //这里利用map，filter方法也可以实现
  var bool = arr.indexOf(v,i+1);  //从传入参数的下一个索引值开始寻找是否存在重复
  if(bool === -1){
   result.push(v);
  }
 })
 return result;
};
var a = [1,1,1,1,1,1,1,1,1,2,2,2,2,2,2,3,3,3,3,3,3,3,2,3,3,2,2,1,23,1,23,2,3,2,3,2,3];
var b = a.distinct();
console.log(b.toString()); //1,23,2,3

方法六：利用ES6的set
Set数据结构，它类似于数组，其成员的值都是唯一的。
利用Array.from将Set结构转换成数组
function dedupe(array){
 return Array.from(new Set(array));
}
dedupe([1,1,2,3]) //[1,2,3]
拓展运算符(...)内部使用for...of循环
let arr = [1,2,3,3];
let resultarr = [...new Set(arr)]; 
console.log(resultarr); //[1,2,3]

详解：http://www.jb51.net/article/118657.htm
```

#### JavaScript中的作用域与变量声明提升？

```
https://segmentfault.com/a/1190000003114255
```

#### 如何编写高性能的Javascript？

```
答案一：https://segmentfault.com/a/1190000003908314
答案二：http://developer.51cto.com/art/200906/131335.htm
```

#### 那些操作会造成内存泄漏？

```
内存泄漏：指一块被分配的内存既不能使用，又不能回收，直到浏览器进程结束。

1）意外的全局变量引起的内存泄露
2）闭包引起的内存泄露
3）没有清理的DOM元素引用
4）被遗忘的定时器或者回调
5）子元素存在引起的内存泄露
6）IE7/8引用计数使用循环引用产生的问题

怎样避免内存泄露？

1）减少不必要的全局变量，或者生命周期较长的对象，及时对无用的数据进行垃圾回收；
2）注意程序逻辑，避免“死循环”之类的；
3）避免创建过多的对象  原则：不用了的东西要及时归还。
```

#### 什么是“前端路由”?什么时候适合使用“前端路由”?“前端路由”有哪些优点和缺点

```
简单的说，我们打开一个页面，这个页面是个单页应用：http://www.this-is-a-spa.com/
所以它仅仅只有一个页面，不过作者却做了好几个 URL：

http://www.this-is-a-spa.com/a
http://www.this-is-a-spa.com/b
http://www.this-is-a-spa.com/c
...
这些 URL 不会直接传给服务器，而是会被浏览器消化处理掉.

这样做，我们可以：

当浏览器读取到其中一个注册到前端路由中的 URL 请求时，比如 http://www.this-is-a-spa.com/a 时，可以触发预先写好的事件 A，所以当访问到这个 URL 后就可以直接触发到事件。在编写的时候可以用 <a href="/a">Event A</a> 来触发事件，而可以不用 addEventListener("click", ...) 这种写法，当项目逻辑比较复杂的时候，这种组织方式比写一大堆事件注册要好很多.（当然上 SPA 一般都用到了框架，这种方式只是一种选择）
用户可以收藏 http://www.this-is-a-spa.com/a 至收藏夹，打开后直接触发 /a 的事件（然后就自动加载数据或是什么别的事情），而没有做前端路由的 SPA 则达不到这样的效果，其 URL 从头到尾都是不变的.
所以~

什么是前端路由：路由交给浏览器处理就算是吧？有没有教科书式的标准定义？
什么时候适合用：SPA 就可以用，其实还是看产品需求.
优点：如上；
缺点：前端开发麻烦？还需要学习一个？如果也算缺点吧.
```

#### 怎样用js实现千位分隔符？

```
正则 + replace

function commafy(num) {
    num = num + '';
    var reg = /(-?d+)(d{3})/;
    if (reg.test(num)) {
        num = num.replace(reg, '$1,$2');
    }
    return num;
}
```

#### 检测浏览器版本有哪些方式？

```
答案一：功能检测、userAgent 特征检测
比如：navigator.userAgent
//"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_2) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/41.0.2272.101 Safari/537.36"

答案二：https://blog.csdn.net/oscar999/article/details/8272798
```

#### **如何获取UA？**

```
　function whatBrowser() {

　　document.Browser.Name.value=navigator.appName;

　　document.Browser.Version.value=navigator.appVersion;

　　document.Browser.Code.value=navigator.appCodeName;

　　document.Browser.Agent.value=navigator.userAgent;

　　}
```

#### 例举3种强制类型转换和2种隐式类型转换?

```
强制：（parseInt,parseFloat,number）
隐式：（== – ===）

详解：https://blog.csdn.net/sinat_29454619/article/details/74075216
```

#### JavaScript中如何检测一个变量是一个String类型？请写出函数实现

```
typeof(obj) === "string"
typeof obj === "string"
obj.constructor === String
```

### 请用js去除字符串空格？

```
方法一：使用replace正则匹配的方法

去除所有空格: str = str.replace(/\s*/g,"");      
去除两头空格: str = str.replace(/^\s*|\s*$/g,"");
去除左空格： str = str.replace( /^\s*/, “”);
去除右空格： str = str.replace(/(\s*$)/g, "");

str为要去除空格的字符串，实例如下：

var str = " 23 23 ";
var str2 = str.replace(/\s*/g,"");
console.log(str2); // 2323
方法二：使用str.trim()方法

str.trim()局限性：无法去除中间的空格，实例如下：

var str = "   xiao  ming   ";
var str2 = str.trim();
console.log(str2);   //xiao  ming 
同理，str.trimLeft()，str.trimRight()分别用于去除字符串左右空格。

方法三：使用jquery,$.trim(str)方法

$.trim(str)局限性：无法去除中间的空格，实例如下：

var str = "   xiao  ming   ";
var str2 = $.trim(str)
console.log(str2);   //  xiao  ming
```

#### 你如何获取浏览器URL中查询字符串中的参数？

```
调用JS BOM方法：Location对象

function showWindowHref(){
    var sHref = window.location.href;
    var args = sHref.split('?');
    if(args[0] == sHref){
        return "";
    }
    var arr = args[1].split('&');
    var obj = {};
    for(var i = 0;i< arr.length;i++){
        var arg = arr[i].split('=');
        obj[arg[0]] = arg[1];
    }
    return obj;
}
var href = showWindowHref(); // obj
console.log(href['name']); // xiaoming

其他：
    http://www.w3school.com.cn/jsref/dom_obj_location.asp
```

#### 简要说明JS**字符串操作函数**

```
简要举例：

concat() – 将两个或多个字符的文本组合起来，返回一个新的字符串。
indexOf() – 返回字符串中一个子串第一处出现的索引。如果没有匹配项，返回 -1 。
charAt() – 返回指定位置的字符。
lastIndexOf() – 返回字符串中一个子串最后一处出现的索引，如果没有匹配项，返回 -1 。
match() – 检查一个字符串是否匹配一个正则表达式
substr() 函数 -- 返回从string的startPos位置，长度为length的字符串
substring() – 返回字符串的一个子串。传入参数是起始位置和结束位置。
slice() – 提取字符串的一部分，并返回一个新字符串。
replace() – 用来查找匹配一个正则表达式的字符串，然后使用新字符串代替匹配的字符串。
search() – 执行一个正则表达式匹配查找。如果查找成功，返回字符串中匹配的索引值。否则返回 -1 。
split() – 通过将字符串划分成子串，将一个字符串做成一个字符串数组。
length – 返回字符串的长度，所谓字符串的长度是指其包含的字符的个数。
toLowerCase() – 将整个字符串转成小写字母。
toUpperCase() – 将整个字符串转成大写字母。


详细说明：http://www.w3school.com.cn/jsref/jsref_obj_string.asp
```

#### 写出3个使用this的典型应用

```
（1）在html元素事件属性中使用，如：

    <input type=”button” onclick=”showInfo(this);” value=”点击一下”/>

（2）构造函数

    function Animal(name, color) {
    　　this.name = name;
    　　this.color = color;
    }

（3）input点击，获取值

    <input type="button" id="text" value="点击一下" />
    <script type="text/javascript">
        var btn = document.getElementById("text");
        btn.onclick = function() {
            alert(this.value);    //此处的this是按钮元素
        }
    </script>

(4)apply()/call()求数组最值

    var  numbers = [5, 458 , 120 , -215 ]; 
    var  maxInNumbers = Math.max.apply(this, numbers);  
    console.log(maxInNumbers);  // 458
    var maxInNumbers = Math.max.call(this,5, 458 , 120 , -215); 
    console.log(maxInNumbers);  // 458
```

#### **比较typeof与instanceof？**

```js
相同点：JavaScript 中 typeof 和 instanceof 常用来判断一个变量是否为空，或者是什么类型的。

typeof的定义和用法：返回值是一个字符串，用来说明变量的数据类型。

细节：

(1)、typeof 一般只能返回如下几个结果：number,boolean,string,function,object,undefined。

(2)、typeof 来获取一个变量是否存在，如 if(typeof a!="undefined"){alert("ok")}，而不要去使用 if(a) 因为如果 a 不存在（未声明）则会出错。

(3)、对于 Array,Null 等特殊对象使用 typeof 一律返回 object，这正是 typeof 的局限性。

Instanceof定义和用法：instanceof 用于判断一个变量是否属于某个对象的实例。

实例演示：

a instanceof b?alert("true"):alert("false"); //a是b的实例？真:假

var a = new Array(); 
alert(a instanceof Array);  // true
alert(a instanceof Object)  // true
如上，会返回 true，同时 alert(a instanceof Object) 也会返回 true;这是因为 Array 是 object 的子类。

function test(){};
var a = new test();
alert(a instanceof test)   // true
细节：

(1)、如下，得到的结果为‘N’,这里的 instanceof 测试的 object 是指 js 语法中的 object，不是指 dom 模型对象。

if (window instanceof Object){ alert('Y')} else {  alert('N');}  // 'N'
```

#### 请解释一下 JavaScript 的同源策略。

```
概念:同源策略是客户端脚本（尤其是Javascript）的重要的安全度量标准。它最早出自Netscape Navigator2.0，其目的是防止某个文档或脚本从多个不同源装载。

这里的同源策略指的是：协议，域名，端口相同，同源策略是一种安全协议。
指一段脚本只能读取来自同一来源的窗口和文档的属性。

为什么要有同源限制？
我们举例说明：比如一个黑客程序，他利用Iframe把真正的银行登录页面嵌到他的页面上，当你使用真实的用户名，密码登录时，他的页面就可以通过Javascript读取到你的表单中input中的内容，这样用户名，密码就轻松到手了。
```



