# 5.ECMAScript6

#### Object.is\(\) 与原来的比较操作符“ ===”、“ ==”的区别？

```
两等号判等，会在比较时进行类型转换；
三等号判等(判断严格)，比较时不进行隐式类型转换,（类型不同则会返回false）； 

Object.is 在三等号判等的基础上特别处理了 NaN 、-0 和 +0 ，保证 -0 和 +0 不再相同，
但 Object.is(NaN, NaN) 会返回 true.

Object.is 应被认为有其特殊的用途，而不能用它认为它比其它的相等对比更宽松或严格。
```

#### 谈一谈你对ECMAScript6的了解？

```
详解：http://wiki.jikexueyuan.com/project/es-six-deeply/an-introduction.html
```

#### ECMAScript6 怎么写class么，为什么会出现class这种东西?

```
详解：https://www.zhihu.com/question/29789315/answer/45624154
```

#### promise方法的理解和使用

```
https://www.jianshu.com/p/063f7e490e9a
```

#### JavaScript中var、let、const区别？

```
使用var声明的变量，其作用域为该语句所在的函数内，且存在变量提升现象；
使用let声明的变量，其作用域为该语句所在的代码块内，不存在变量提升；
使用const声明的是常量，在后面出现的代码中不能再修改该常量的值。

http://www.infoq.com/cn/articles/es6-in-depth-let-and-const
```

#### 平时用了es6的哪些特性，体验如何 和es5有什么不同

```
let const关键字 箭头函数 字符串模板 class类 模块化 promise

es5 require react.createclass
```



