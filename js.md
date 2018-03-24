#### 介绍js的基本数据类型。

* ```
   Undefined、Null、Boolean、Number、String

  ```

#### 介绍js有哪些内置对象？

```
Object 是 JavaScript 中所有对象的父对象

数据封装类对象：Object、Array、Boolean、Number 和 String
其他对象：Function、Arguments、Math、Date、RegExp、Error

```

* #### 说几条写JavaScript的基本规范？

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
* #### JavaScript原型，原型链 ? 有什么特点？

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
* #### JavaScript有几种类型的值？，你能画一下他们的内存图吗？

  ```
  栈：原始数据类型（Undefined，Null，Boolean，Number、String） 
  堆：引用数据类型（对象、数组和函数）

  两种类型的区别是：存储位置不同；
  原始数据类型直接存储在栈(stack)中的简单数据段，占据空间小、大小固定，属于被频繁使用数据，所以放入栈中存储；
  引用数据类型存储在堆(heap)中的对象,占据空间大、大小不固定,如果存储在栈中，将会影响程序运行的性能；引用数据类型在栈中存储了指针，该指针指向堆中该实体的起始地址。当解释器寻找引用值时，会首先检索其
  在栈中的地址，取得地址后从堆中获得实体
  ```



