# 2.CSS及其相关

#### 标准的CSS盒子模型？与低版本IE的盒子模型有什么不同的？

```
1，有两种， IE 盒子模型、标准 W3C 盒子模型；IE的content部分包含了 border 和 pading;
2，盒模型： 内容(content)、填充(padding)、边界(margin)、 边框(border).
标准的CSS盒子模型和低端IE CSS盒子模型不同：宽高不一样
标准的css盒子模型宽高就是内容区宽高；
低端IE css盒子模型宽高 内边距﹢边界﹢内容区；
```

#### 解释下 CSS sprites，以及你要如何在页面或网站中使用它。

    CSS Sprites其实就是把网页中一些背景图片整合到一张图片文件中，再利用CSS的“background-image”，“background- repeat”，“background-position”的组合进行背景定位，background-position可以用数字能精确的定位出背景图片的位置。这样可以减少很多图片请求的开销，因为请求耗时比较长；请求虽然可以并发，但是也有限制，一般浏览器都是6个。对于未来而言，就不需要这样做了，因为有了`http2`。

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

#### 请解释一下CSS3的Flexbox（弹性盒布局模型）,以及适用场景？

```
CSS3 弹性盒（ Flexible Box 或 flexbox），是一种当页面需要适应不同的屏幕大小以及设备类型时确保元素拥有恰当的行为的布局方式。
引入弹性盒布局模型的目的是提供一种更加有效的方式来对一个容器中的子元素进行排列、对齐和分配空白空间。

一个用于页面布局的全新CSS3功能，Flexbox可以把列表放在同一个方向（从上到下排列，从左到右），并让列表能延伸到占用可用的空间。
较为复杂的布局还可以通过嵌套一个伸缩容器（flex container）来实现。
采用Flex布局的元素，称为Flex容器（flex container），简称"容器"。
它的所有子元素自动成为容器成员，称为Flex项目（flex item），简称"项目"。
常规布局是基于块和内联流方向，而Flex布局是基于flex-flow流可以很方便的用来做局中，能对不同屏幕大小自适应。
在布局上有了比以前更加灵活的空间。
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

_visibility有如下属性值：_

| 属性值 | 属性值描述 |
| :--- | :--- |
| visible | 默认值。元素是可见的。 |
| hidden | 元素是不可见的，相当于`display：hidden；`，但此时仍占用页面空间 |
| collapse | 当在表格元素中使用时，此值可删除一行或一列，但是它不会影响表格的布局。被行或列占据的空间会留给其他内容使用。_如果此值被用在其他的元素上，会呈现为 “hidden”。_ |
| inherit | 规定应该从父元素继承 visibility 属性的值。 |

```
visibility的第三种值collapse：
对于一般的元素，它的表现跟display:hidden是一样的。
但例外的是，如果这个元素是table相关的元素，例如table行，table group，table列，table column group，它的表现却跟display: none一样，也就是说，它们占用的空间也会释放。

在不同浏览器下的区别：
在谷歌浏览器里，使用collapse值和使用hidden值没有什么区别。
在火狐浏览器、Opera和IE11里，使用collapse值的效果就如它的字面意思：table的行会消失，它的下面一行会补充它的位置。
```

#### position跟display、margin collapse、overflow、float这些特性相互叠加后会怎么样？

```
详细介绍：http://www.cnblogs.com/jackyWHJ/p/3756087.html
```

#### 对BFC规范\(块级格式化上下文：block formatting context\)的理解？

```
（W3C CSS 2.1 规范中的一个概念,它是一个独立容器，决定了元素如何对其内容进行定位,以及与其他元素的关系和相互作用。）
一个页面是由很多个 Box 组成的,元素的类型和 display 属性,决定了这个 Box 的类型。
不同类型的 Box,会参与不同的 Formatting Context（决定如何渲染文档的容器）,因此Box内的元素会以不同的方式渲染,也就是说BFC内部的元素和外部的元素不会互相影响。
```

#### 请解释下css定义的权重？

```
以下是权重的规则：标签的权重为1，class的权重为10，id的权重为100，以下例子是演示各种定义的权重值：
/*权重为1*/
div{
}
/*权重为10*/
.class1{
}
/*权重为100*/
#id1{
}
/*权重为100+1=101*/
#id1 div{
}
/*权重为10+1=11*/
.class1 div{
}
/*权重为10+10+1=21*/
.class1 .class2 div{
}
如果权重相同，则最后定义的样式会起作用，但是应该避免这种情况出现
```

#### 请解释一下为什么会出现浮动和什么时候需要清除浮动？清除浮动的方式？

```
为什么出现浮动？
浮动float最开始出现的意义是为了让文字环绕图片而已，但人们发现，如果想要三个块级元素并排显示，都给它们加个float来得会比较方便。

什么时候清除浮动？
如果想要实现三个块级元素并排显示，给三个块级元素都加上float属性后，问题出现了，父元素高度塌陷了
如果我们给上面的盒子设置display:inline-block也能达到让它们并排显示的效果。并且父元素的高度也不会塌陷。只不过无法控制是居左还是居右，display:inline-block只能从左往右。

清除浮动的方式？
我们说的清除浮动是指清除由于子元素浮动带来父元素高度塌陷的影响。

清除浮动的两大基本方法：

方法1：脚底插入clear:both;
方法2：父元素BFC(ie8+)或haslayout(ie6/ie7)移动端的布局用过媒体查询吗？

详细介绍URL：http://blog.csdn.net/sjinsa/article/details/70932804?utm_source=itdadao&utm_medium=referral

其他答案：
    (Q1)
　　       （1）父级div定义height。
　　       （2）结尾处加空div标签clear:both。
　　       （3）父级div定义伪类:after和zoom。
　　       （4）父级div定义overflow:hidden。
　　       （5）父级div定义overflow:auto。
　　       （6）父级div也浮动，需要定义宽度。
　　       （7）父级div定义display:table。
　　       （8）结尾处加br标签clear:both。

　　 (Q2) 比较好的是第3种方式，好多网站都这么用。
```

#### 什么是CSS 预处理器 / 后处理器？

```
预处理器例如：LESS、Sass、Stylus，用来预编译Sass或less，增强了css代码的复用性，
还有层级、mixin、变量、循环、函数等，具有很方便的UI组件模块化开发能力，极大的提高工作效率。
后处理器例如：PostCSS，通常被视为在完成的样式表中根据CSS规范处理CSS，让其更有效；目前最常做的
是给CSS属性添加浏览器私有前缀，实现跨浏览器兼容性的问题。
```

#### 使用 CSS 预处理器吗？喜欢那个？

`SASS (SASS、LESS没有本质区别，只因为团队前端都是用的SASS)`

#### CSS优化、提高性能的方法有哪些？

```
事实上大部分的复杂页面都可以在完全不修改 JavaScript 代码的情况下，通过 CSS 的优化大幅提升 render performance。

CSS 优化主要是四个方面：
1.加载性能
这个方面相关的 best practice 太多了，网上随便找一找就是一堆资料，比如不要用 import 啊，压缩啊等等，主要是从减少文件体积、减少阻塞加载、提高并发方面入手的，任何 hint 都逃不出这几个大方向。

2.选择器性能
可以参考 GitHub 的这个分享 https://speakerdeck.com/jonrohan/githubs-css-performance，但 selector 的对整体性能的影响可以忽略不计了，selector 的考察更多是规范化和可维护性、健壮性方面，很少有人在实际工作当中会把选择器性能作为重点关注对象的，但也像 GitHub 这个分享里面说的一样——知道总比不知道好。

3.渲染性能
渲染性能是 CSS 优化最重要的关注对象。页面渲染 junky 过多？看看是不是大量使用了 text-shadow？是不是开了字体抗锯齿？CSS 动画怎么实现的？合理利用 GPU 加速了吗？什么你用了 Flexible Box Model？有没有测试换个 layout 策略对 render performance 的影响？这个方面搜索一下 CSS render performance 或者 CSS animation performance 也会有一堆一堆的资料可供参考。

4.可维护性、健壮性
命名合理吗？结构层次设计是否足够健壮？对样式进行抽象复用了吗？优雅的 CSS 不仅仅会影响后期的维护成本，也会对加载性能等方面产生影响。这方面可以多找一些 OOCSS（不是说就要用 OOCSS，而是说多了解一下）等等不同 CSS Strategy 的信息，取长补短。

较为具体的优化方案： 
慎重使用高性属性：浮动、定位； 
去除空规则； 
属性值为0时，不加单位； 
属性值为浮点数0.**时，可以省略小数点前的0； 
标准化各种浏览器前缀，带浏览器前缀的在前，标准的在后； 
不使用@import前缀，它会影响css加载速度； 
充分利用css继承属性，减少代码量； 
抽象提取公用样式，减少代码量； 
选择器优化嵌套，尽量避免层级过深； 
将css文件放在页面的最上面；

关键选择器（key selector）。选择器的最后面的部分为关键选择器（即用来匹配目标元素的部分）；
如果规则拥有 ID 选择器作为其关键选择器，则不要为规则增加标签。过滤掉无关的规则（这样样式系统就不会浪费时间去匹配它们了）；
提取项目的通用公有样式，增强可复用性，按模块编写组件；增强项目的协同开发性、可维护性和可扩展性;
使用预处理工具或构建工具（gulp对css进行语法检查、自动补前缀、打包压缩、自动优雅降级）
```

```
按照从上到下，从右到左的顺序解析。
```

#### 在网页中的应该使用奇数还是偶数的字体？为什么呢？

```
偶数字体
1.为了兼容不同字体对页面带来的影响
2.为了满足设计
```

#### 抽离样式模块怎么写，说出思路，有无实践经验？\[阿里航旅的面试题\]

```
该题目中的“模块”指的是页面元素，例如网站通用按钮，通用选项卡，通用小图标，或是页面的一些固定框架结构等，即页面元素的模块化。
```

#### 元素竖向的百分比设定是相对于容器的高度吗？

```
元素竖向的百分比设定是相对于容器的宽度，而不是高度
```

#### 全屏滚动的原理是什么？用到了CSS的那些属性？

```
http://blog.csdn.net/rita_jing/article/details/78236768
```

#### 什么是响应式设计？响应式设计的基本原理是什么？如何兼容低版本的IE？

```
页面的设计和开发应当根据用户行为以及设备环境（系统平台、屏幕尺寸、屏幕定向等）进行相应的响应和调整。具体的实践方式由多方面组成，包括弹性网格和布局、图片、css media query的使用等。无论用户正在使用笔记本还是iPad，我们的页面都应该能够自动切换分辨率、图片尺寸及相关脚本功能等，以适应不同设备；换句话说，页面应该有能力去自动响应用户的设备环境。

响应式网页设计就是一个网站能够兼容多个终端——而不是为每个终端做一个特定的版本。这样，我们就可以不必为不断到来的新设备做专门的版本设计和开发了。

响应式设计的基本原理是通过媒体查询检测不同的设备屏幕尺寸做处理。页面头部必须有meta声明viewport：

<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no”>视差滚动效果，如何给每页做不同的动画？（回到顶部，向下滑动要再次出现，和只出现一次分别怎么做？）
```

#### ::before 和 :after中双冒号和单冒号 有什么区别？解释一下这2个伪元素的作用。

```
单冒号(:)用于CSS3伪类，双冒号(::)用于CSS3伪元素。（伪元素由双冒号和伪元素名称组成）

双冒号是在当前规范中引入的，用于区分伪类和伪元素。不过浏览器需要同时支持旧的已经存在的伪元素写法，

比如:first-line、:first-letter、:before、:after等，

而新的在CSS3中引入的伪元素则不允许再支持旧的单冒号的写法。

想让插入的内容出现在其它内容前，使用::before，否者，使用::after；

在代码顺序上，::after生成的内容也比::before生成的内容靠后。

如果按堆栈视角，::after生成的内容会在::before生成的内容之上
```

#### 如何修改chrome记住密码后自动填充表单的黄色背景 ？

```css
input:-webkit-autofill, textarea:-webkit-autofill, select:-webkit-autofill {
  background-color: rgb(250, 255, 189); /* #FAFFBD; */
  background-image: none;
  color: rgb(0, 0, 0);
}
```

#### 你对line-height是如何理解的？

```
http://www.cnblogs.com/raimonfuns/p/3921475.html
```

#### 设置元素浮动后，该元素的display值是多少？

```css
display:block;
```

#### 怎么让Chrome支持小于12px 的文字？

```
1、用图片：如果是内容固定不变情况下，使用将小于12px文字内容切出做图片，这样不影响兼容也不影响美观。

2、使用12px及12px以上字体大小：为了兼容各大主流浏览器，建议设计美工图时候设置大于或等于12px的字体大小，如果是接单的这个时候就需要给客户讲解小于12px浏览器不兼容等事宜。

3、继续使用小于12px字体大小样式设置：如果不考虑chrome可以不用考虑兼容，同时在设置小于12px对象设置-webkit-text-size-adjust:none，做到最大兼容考虑。

4、使用12px以上字体：为了兼容、为了代码更简单 从新考虑权重下兼容性。
```

#### 让页面里的字体变清晰，变细用CSS怎么做？

```css
-webkit-font-smoothing: antialiased;
```

#### font-style属性可以让它赋值为“oblique” oblique是什么意思？

```
倾斜
```

#### position:fixed;在android下无效怎么处理？

```
在手机页面中，fixed的元素是相对整个页面固定位置的，而不是fixed的元素相对手机屏幕固定的。
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0, user-scalable=no"/>
```

#### 如果需要手动写动画，你认为最小时间间隔是多久，为什么？（阿里）

`多数显示器默认频率是60Hz，即1秒刷新60次，所以理论上最小间隔为1/60＊1000ms ＝ 16.7ms`

#### display:inline-block 什么时候会显示间隙？\(携程\)

```
移除空格、使用margin负值、使用font-size:0、letter-spacing、word-spacing
```

#### overflow: scroll时不能平滑滚动的问题怎么处理？

```
没找到过标准答案！
我的理解是：
        1，可能盒子内的内容不够多不足以滚动
        2，浏览器或者有代码阻止了平滑滚动
```

#### 有一个高度自适应的div，里面有两个div，一个高度100px，希望另一个填满剩下的高度怎么实现呢？

```
如果外层div高度自适应于内部，就完全不需要额外写规则了，另外一个DIV绝对能撑高外层div，填得紧紧实实的。

如果是外层div自适应于它的父级，纯CSS的办法是有的。

为了方便演示，下面的demo都让外层元素100%适应于html和body，点Edit in JSFiddle之后可以看到，拖动窗口高度，均能自适应。

box-sizing方案
外层box-sizing: border-box; 同时设置padding: 100px 0 0；
内层100像素高的元素向上移动100像素，或使用absolute定位防止占据空间；
另一个元素直接height: 100%;
这就是两个方案了:
                http://jsfiddle.net/xq4rew3f/1/
                http://jsfiddle.net/xq4rew3f/3/

height: calc(100%-100px);

Js代码实现

absolute position
外层position: relative；
百分百自适应元素直接position: absolute; top: 100px; bottom: 0; left: 0
第三个方案：

http://jsfiddle.net/xq4rew3f/5/
```

#### png、jpg、gif 这些图片格式解释一下，分别什么时候用。有没有了解过webp？

```
WebP格式，谷歌（google）开发的一种旨在加快图片加载速度的图片格式。图片压缩体积大约只有JPEG的2/3，并能节省大量的服务器带宽资源和数据空间。Facebook Ebay等知名网站已经开始测试并使用WebP格式。
```

#### 什么是Cookie 隔离？（或者说：请求资源的时候不要让它带cookie怎么做）

```
如果静态文件都放在主域名下，那静态文件请求的时候都带有的cookie的数据提交给server的，非常浪费流量，
所以不如隔离开。

因为cookie有域的限制，因此不能跨域提交请求，故使用非主要域名的时候，请求头中就不会带有cookie数据，
这样可以降低请求头的大小，降低请求时间，从而达到降低整体请求延时的目的。

同时这种方式不会将cookie传入Web Server，也减少了Web Server对cookie的处理分析环节，
提高了webserver的http请求的解析速度。
```

#### style标签写在body后与body前有什么区别？

```
写在head标签中利于浏览器逐步渲染（resources downloading->CSSOM+DOM->RenderTree(composite)->Layout->paint）。具体渲染过程请参考
http://blog.csdn.net/wozaixia...
写在body标签后由于浏览器以逐行方式对html文档进行解析，当解析到写在尾部的样式表（外联或写在style标签）会导致浏览器停止之前的渲染，等待加载且解析样式表完成之后重新渲染，在windows的IE下可能会出现FOUC现象（即样式失效导致的页面闪烁问题）
```

#### rem布局的优点缺点有哪些？

```
https://segmentfault.com/q/1010000008952958
```

#### IE 8以下版本的浏览器中的盒模型有什么不同？

```
IE8以下浏览器的盒模型中定义的元素的宽高不包括内边距和边框
```

#### **box-sizing常用的属性有哪些？分别有什么作用？**

```
(Q1)box-sizing: content-box|border-box|inherit;

(Q2)content-box:宽度和高度分别应用到元素的内容框。在宽度和高度之外绘制元素的内边距和边框(元素默认效果)。

border-box:元素指定的任何内边距和边框都将在已设定的宽度和高度内进行绘制。通过从已设定的宽度和高度分别减去边框和内边距才能得到内容的宽度和高度。

详解：http://www.w3school.com.cn/cssref/pr_box-sizing.asp
```

#### 高度不固定的容器的上下左右的居中显示。\(重点是垂直居中\)

```css
1）将父级容器设置为：

display:table-cell;

vertical-align:middle;

text-align:center;
2)使用flex

display: flex;

justify-content:center;

align-items:Center;

记住上面两个，还有其他的具体的参考下面的链接地址：http://www.cnblogs.com/hutuzhu/p/4450850.html
```

#### margin塌陷的问题，以及margin重叠问题。

```
相信很多人都知道解决父容器不设置margin的值，只给里面的div设置一个margin-top，会有什么样的结果，就是父容器会margin-top == 子容器的margin-top值。

解决方案：

1）给父容器设置border：1px solid transparent;

2)padding>0

3)float

4)position:absolute;

5)display:inline-block;

6)overflow:hidden/auto;

另外一种情况：

两个div，上面的margin-bottom：30px;下面的：margin-top:10px;中间的间距是30px;取最大的。

解决办法：只设置一个的要么margin-top；要么margin-bottom
```



