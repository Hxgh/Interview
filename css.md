# 2.CSS及其相关

#### 标准的CSS盒子模型？与低版本IE的盒子模型有什么不同的？

```
1，有两种， IE 盒子模型、标准 W3C 盒子模型；IE的content部分包含了 border 和 pading;
2，盒模型： 内容(content)、填充(padding)、边界(margin)、 边框(border).
标准的CSS盒子模型和低端IE CSS盒子模型不同：宽高不一样
标准的css盒子模型宽高就是内容区宽高；
低端IE css盒子模型宽高 内边距﹢边界﹢内容区；
```

#### CSS 选择符有哪些？哪些属性可以继承？优先级算法如何计算？ CSS3新增伪类有那些？

```
1.id选择器（ # myid）
2.类选择器（.myclassname）
3.标签选择器（div, h1, p）
4.相邻选择器（h1 + p）
5.子选择器（ul > li）
6.后代选择器（li a）
7.通配符选择器（ * ）
8.属性选择器（a[rel = "external"]）
9.伪类选择器（a: hover, li:nth-child）

*   可继承的样式： font-size font-family color, text-indent;
*   不可继承的样式：border padding margin width height ;
*   优先级就近原则，同权重情况下样式定义最近者为准;
*   载入样式以最后载入的定位为准;

优先级为: !important >  id > class > tag
        important 比 内联优先级高,但内联比 id 要高

CSS3新增伪类举例：
p:first-of-type 选择属于其父元素的首个 <p> 元素的每个 <p> 元素。
p:last-of-type  选择属于其父元素的最后 <p> 元素的每个 <p> 元素。
p:only-of-type  选择属于其父元素唯一的 <p> 元素的每个 <p> 元素。
p:only-child    选择属于其父元素的唯一子元素的每个 <p> 元素。
p:nth-child(2)  选择属于其父元素的第二个子元素的每个 <p> 元素。
:enabled  :disabled 控制表单控件的禁用状态。
:checked        单选框或复选框被选中。
```

#### 如何居中div？如何居中一个浮动元素？如何让绝对定位的div居中？

```
给div设置一个宽度，然后添加margin:0 auto属性

div{
    width:200px;
    margin:0 auto;
 }
 
居中一个浮动元素
确定容器的宽高 宽500 高 300 的层
设置层的外边距

 .div {
      width:500px ; height:300px;//高度可以不设
      margin: -150px 0 0 -250px;
      position:relative;         //相对定位
      background-color:pink;     //方便看效果
      left:50%;
      top:50%;
 }
 
让绝对定位的div居中

position: absolute;
width: 1200px;
background: none;
margin: 0 auto;
top: 0;
left: 0;
bottom: 0;
right: 0;
```

#### display有哪些值？说明他们的作用。

```
block 象块类型元素一样显示。
none 缺省值。象行内元素类型一样显示。
inline-block 象行内元素一样显示，但其内容象块类型元素一样显示。
list-item 象块类型元素一样显示，并添加样式列表标记。
table 此元素会作为块级表格来显示
inherit 规定应该从父元素继承
```

#### display 属性的值，position的值relative和absolute定位原点是？  

```
absolute
生成绝对定位的元素，相对于值不为 static的第一个父元素进行定位。

fixed （老IE不支持）
生成绝对定位的元素，相对于浏览器窗口进行定位。

relative
生成相对定位的元素，相对于其正常位置进行定位。

static
默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right z-index 声明）。

inherit
规定从父元素继承 position 属性的值。CSS3有哪些新特性？
```

#### 新增各种CSS选择器？

```
1.CSS3实现圆角（border-radius），阴影（box-shadow），边框图片border-image
2.文字加特效（text-shadow、），强制文本换行（word-wrap），线性渐变（linear-gradient）
3.旋转,缩放,定位,倾斜：transform:rotate(90deg) scale(0.85,0.90) translate(0px,-30px) skew(-9deg,0deg);
4.增加了更多的CSS选择器、多背景、rgba()；
5.在CSS3中唯一引入的伪元素是 ::selection ；
6.媒体查询(@media)，多栏布局（flex）
```

请解释一下CSS3的Flexbox（弹性盒布局模型）,以及适用场景？

```
CSS3 弹性盒（ Flexible Box 或 flexbox），是一种当页面需要适应不同的屏幕大小以及设备类型时确保元素拥有恰当的行为的布局方式。
引入弹性盒布局模型的目的是提供一种更加有效的方式来对一个容器中的子元素进行排列、对齐和分配空白空间。
```

#### 用纯CSS创建一个三角形的原理是什么？

```
把上、左、右三条边隐藏掉（颜色设为 transparent）
#demo {
  width: 0;
  height: 0;
  border-width: 20px;
  border-style: solid;
  border-color: transparent transparent red transparent;
}
```

#### 一个满屏 品 字布局 如何设计?

```
简单的方式：

上面的div宽100%，

下面的两个div分别宽50%，

然后用float或者inline使其不换行即可
```

#### 经常遇到的浏览器的兼容性有哪些？原因，解决方法是什么，常用hack的技巧 ？

```
* png24位的图片在iE6浏览器上出现背景，解决方案是做成PNG8.
* 浏览器默认的margin和padding不同。解决方案是加一个全局的*{margin:0;padding:0;}来统一。
* IE6双边距bug:块属性标签float后，又有横行的margin情况下，在ie6显示margin比设置的大。
  浮动ie产生的双倍距离 #box{ float:left; width:10px; margin:0 0 0 100px;}
  这种情况之下IE会产生20px的距离，解决方案是在float的标签样式控制中加入 ——_display:inline;将其转化为行内属性。(_这个符号只有ie6会识别)
  渐进识别的方式，从总体中逐渐排除局部。
  首先，巧妙的使用“\9”这一标记，将IE游览器从所有情况中分离出来。
  接着，再次使用“+”将IE8和IE7、IE6分离开来，这样IE8已经独立识别。
  css
      .bb{
          background-color:#f1ee18;/*所有识别*/
          .background-color:#00deff\9; /*IE6、7、8识别*/
          +background-color:#a200ff;/*IE6、7识别*/
          _background-color:#1e0bd1;/*IE6识别*/
      }
*  IE下,可以使用获取常规属性的方法来获取自定义属性,
   也可以使用getAttribute()获取自定义属性;
   Firefox下,只能使用getAttribute()获取自定义属性。
   解决方法:统一通过getAttribute()获取自定义属性。

*  IE下,even对象有x,y属性,但是没有pageX,pageY属性;
   Firefox下,event对象有pageX,pageY属性,但是没有x,y属性。

*  解决方法：（条件注释）缺点是在IE浏览器下可能会增加额外的HTTP请求数。

*  Chrome 中文界面下默认会将小于 12px 的文本强制按照 12px 显示,
   可通过加入 CSS 属性 -webkit-text-size-adjust: none; 解决。

超链接访问过后hover样式就不出现了 被点击访问过的超链接样式不在具有hover和active了解决方法是改变CSS属性的排列顺序:
L-V-H-A :  a:link {} a:visited {} a:hover {} a:active {}
```

#### li与li之间有看不见的空白间隔是什么原因引起的？有什么解决办法？

```
行框的排列会受到中间空白（回车\空格）等的影响，因为空格也属于字符,这些空白也会被应用样式，占据空间，所以会有间隔，把字符大小设为0，就没有空格了。
```

#### 为什么要初始化CSS样式？

```
- 因为浏览器的兼容问题，不同浏览器对有些标签的默认值是不同的，如果没对CSS初始化往往会出现浏览器之间的页面显示差异。

- 当然，初始化样式会对SEO有一定的影响，但鱼和熊掌不可兼得，但力求影响最小的情况下初始化。

最简单的初始化方法： * {padding: 0; margin: 0;} （强烈不建议）

淘宝的样式初始化代码：
body, h1, h2, h3, h4, h5, h6, hr, p, blockquote, dl, dt, dd, ul, ol, li, pre, form, fieldset, legend, button, input, textarea, th, td { margin:0; padding:0; }
body, button, input, select, textarea { font:12px/1.5tahoma, arial, \5b8b\4f53; }
h1, h2, h3, h4, h5, h6{ font-size:100%; }
address, cite, dfn, em, var { font-style:normal; }
code, kbd, pre, samp { font-family:couriernew, courier, monospace; }
small{ font-size:12px; }
ul, ol { list-style:none; }
a { text-decoration:none; }
a:hover { text-decoration:underline; }
sup { vertical-align:text-top; }
sub{ vertical-align:text-bottom; }
legend { color:#000; }
fieldset, img { border:0; }
button, input, select, textarea { font-size:100%; }
table { border-collapse:collapse; border-spacing:0; }
```

#### absolute的containing block\(容器块\)计算方式跟正常流有什么不同？

```
无论属于哪种，都要先找到其祖先元素中最近的 position 值不为 static 的元素，然后再判断：
1、若此元素为 inline 元素，则 containing block 为能够包含这个元素生成的第一个和最后一个 inline box 的 padding box (除 margin, border 外的区域) 的最小矩形；
2、否则,则由这个祖先元素的 padding box 构成。
如果都找不到，则为 initial containing block。

补充：
1. static(默认的)/relative：简单说就是它的父元素的内容框（即去掉padding的部分）
2. absolute: 向上找最近的定位为absolute/relative的元素
3. fixed: 它的containing block一律为根元素(html/body)，根元素也是initial containing block
```

#### CSS里的visibility属性有个collapse属性值是干嘛用的？在不同浏览器下以后什么区别？

#### 

#### position跟display、margin collapse、overflow、float这些特性相互叠加后会怎么样？

#### 

#### 对BFC规范\(块级格式化上下文：block formatting context\)的理解？



（W3C CSS 2.1 规范中的一个概念,它是一个独立容器，决定了元素如何对其内容进行定位,以及与其他元素的关系和相互作用。）

 一个页面是由很多个 Box 组成的,元素的类型和 display 属性,决定了这个 Box 的类型。

 不同类型的 Box,会参与不同的 Formatting Context（决定如何渲染文档的容器）,因此Box内的元素会以不同的方式渲染,也就是说BFC内部的元素和外部的元素不会互相影响。

css定义的权重



以下是权重的规则：标签的权重为1，class的权重为10，id的权重为100，以下例子是演示各种定义的权重值：



/\*权重为1\*/

div{

}

/\*权重为10\*/

.class1{

}

/\*权重为100\*/

\#id1{

}

/\*权重为100+1=101\*/

\#id1 div{

}

/\*权重为10+1=11\*/

.class1 div{

}

/\*权重为10+10+1=21\*/

.class1 .class2 div{

}



如果权重相同，则最后定义的样式会起作用，但是应该避免这种情况出现

请解释一下为什么会出现浮动和什么时候需要清除浮动？清除浮动的方式



移动端的布局用过媒体查询吗？



使用 CSS 预处理器吗？喜欢那个？



SASS \(SASS、LESS没有本质区别，只因为团队前端都是用的SASS\)

CSS优化、提高性能的方法有哪些？



浏览器是怎样解析CSS选择器的？

