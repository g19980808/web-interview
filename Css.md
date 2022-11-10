## CSS面试题

#### **CSS选择器及优先级

![image-20220728215345542](C:\Users\g5988\AppData\Roaming\Typora\typora-user-images\image-20220728215345542.png)

标签，class，id，属性，伪元素，伪类，兄弟选择器，子选择器，后代选择器，通配符

##### 属性选择器

```javascript
div[v-aaa]{
    //样式
}
<div v-aaa></div>
```

##### 选择器优先级算法

!important >内联 >id >class >标签 >通配符

权重计算

1. 内联样式                                   权重：1000

2. id 选择器                                   权重：100

3. class、伪类、属性选择器        权重：10

4. 标签、伪元素选择器                权重 ：1

5. 通配、>、+                               权重：0

   

```javascript
ul li.list{}  //权重 1+1+10
.list         //权重 10

```



##### 可继承属性

文字：font-size、color、line-height、text-align、opacity  ....

##### 不可继承属性

border、padding、margin、rgba、display、visibility...



#### 回流和重绘

回流必将引起重绘，重绘不一定引起回流

- 回流

当渲染树中元素的尺寸、布局发生改变时会重新构建，称为回流

width、height、border、margin、padding、float、position、top、bottom、left、right、text-align、font-size

- 重绘

渲染树中元素外观属性发生改变，不影响布局的称为重绘

color、background、border-style、border-radius、box-shadow





#### **介绍css盒子模型

##### 标准(W3C)盒模型：

​    margin  、padding、border、 content，content 部分不包括其他部分

##### IE盒模型 ：

​    margin、content(border + padding + content) ，content 部分包含padding+border +content

##### css转换盒模型

```javascript
//box-sizing属性，默认content-box

box-sizing:content-box  //标准盒模型
box-sizing:border-box   //IE盒模型
```



#### **display的属性值及其作用

![image-20220728220021069](C:\Users\g5988\AppData\Roaming\Typora\typora-user-images\image-20220728220021069.png)



block：会独占一行，多个元素会另起一行，可以设置width、height、margin和padding属性；

inline： 元素不会独占一行，设置width、height属性无效。但可以设置水平方向的margin和padding属性，不能设置垂直方向的padding和margin；

inline-block：将对象设置为inline对象，但对象的内容作为block对象呈现，之后的内联对象会被排列在同一行内。




##### 行内元素

行内标签：a、img、span、input、label、textarea、select、b、big、

- 设置宽高无效
- 可以设置水平方向的margin和padding属性，不能设置垂直方向的padding和margin
- 不会自动换行

##### 块级元素

块级标签：div、p、ul、li、ol、dl、dt、dd、table、tr、td、th、hr、h1-h6、

- 可以设置宽高
- 设置margin和padding都有效
- 可以自动换行
- 多个块状，默认排列从上到下



####  transition和animation的区别

- **transition是过度属性**，强调过度，它的实现需要触发一个事件（比如鼠标移动上去，焦点，点击等）才执行动画，类似于flash的补间动画，设置一个开始关键帧，一个结束关键帧。
- **animation是动画属性**，它的实现不需要触发事件，设定好时间之后可以自己执行，且可以循环一个动画，类似于flash的补间动画，但是它可以设置多个关键帧（用@keyframe定义）完成动画





####  z-index什么情况下会失效

z-index值越大就越是在上层，z-index元素的position属性需要是relative，absolute或是fixed

- 父元素position为relative时，子元素的z-index失效 

    解决：父元素position改为absolute或static

- 元素没有设置position属性为非static属性

    解决：设置该元素的position属性为relative，absolute或是fixed中的一种

- 元素在设置z-index的同时还设置了float浮动

    解决：float去除，改为display：inline-block



#### 伪元素和伪类

伪元素：在内容元素的前后插入额外的元素或样式，但元素不在文档中生成

```javascript
p::before {content:"第一章：";}
```

伪类：用于选择DOM树上元素不同的状态（:visited :link），或者是DOM上无法用简单选择器选择的元素(:first-child)

```javascript
p:first-child {color: red}
```

常用伪元素

before

after



常用伪类选择器

:first-child

:last-child

:nth-child()

:nth-of-type(n)

:not()

:link 未访问

:visited  已访问

:hover  鼠标悬浮

:active  被点击的一刻



编写顺序为：link、visited、hover、active



#### 自适应布局/响应式布局

自适应布局：同一张网页自动适应不同大小的屏幕，根据屏幕宽度，自动调整网页内容大小。

响应式布局：可以自动识别屏幕宽度、并做出相应调整的网页设计，布局和展示的内容可能会有所变动。

区别：如果网页内容过多，整体会显得拥挤。所以响应式布局是自适应布局的改进，布局和展示的内容可能会有所变动。

响应式：

- 允许网页宽度自动调整

  ```javascript
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  // viewport是网页默认的宽度和高度
  // 网页宽度默认等于屏幕宽度（width=device-width），原始缩放比例（initial-scale=1）为1.0 
  // 即网页初始大小占屏幕面积的100%
  ```

- 尽量少使用绝对宽度：使用百分比进行布局

- 相对大小的字体：字体也不能使用绝对大小（px），而只能使用相对大小（em）或者高清方案（rem）,rem不局限于字体大小，前面的宽度width也可以使用，代替百分比

- 流动布局（fluid grid）：各个区块的位置都是浮动的，不是固定不变的

- 选择加载CSS：

  ```javascript
  <link rel="stylesheet" type="text/css" media="screen and (max-device-width: 400px)"
  　　href="tinyScreen.css" />
      或者：
      @import  url("tinyScreen.css") screen and (max-device-width: 400px);
  ```

  

- CSS的@media规则（媒体查询） 

  ```javascript
  @media  screen and (max-device-width: 400px) {
  　　　　.column {
  　　　　　　float: none;
  　　　　　　width:auto;
  　　　　}
  
  　　　　#sidebar {
  　　　　　　display:none;    
  　　　　}
  
  　　}
  ```

  

- 图片的自适应（fluid image）

  ```javascript
  img { max-width: 100%;}
  
  ```

  



#### **对BFC规范的理解

BFC 块级格式化上下文(Block Formatting Context)，就是页面上一个隔离的独立容器，容器内的子元素不会影响外面的元素

##### 作用：

- **解决margin的重叠问题**：由于BFC是一个独立的区域，内部的元素和外部的元素互不影响，将两个元素变为两个BFC，就解决了margin重叠的问题
- **解决高度塌陷的问题**：子元素设置浮动，父元素会发生高度塌陷，高度变为0    解决：把父元素变成一个BFC，给父元素设置`overflow:hidden`
- **创建自适应两栏布局**：可以用来创建自适应两栏布局：左边的宽度固定，右边的宽度自适应



##### 特性：

- 垂直方向上，自上而下排列，和文档流的排列方式一致
- 在BFC中上下相邻的两个容器的margin会重叠
- 计算BFC的高度时，需要计算浮动元素的高度
- BFC区域不会与浮动的容器发生重叠
- BFC是独立的容器，容器内部元素不会影响外部元素
- 每个元素的左margin值和容器的左border相接触



##### 形成条件:

- html 根元素

- float的值不是none

- position 值是 absolute、fixed，不是static或者relative

- display值是 inline-block,table-cell,table-caption,flex,inline-flex

- overflow值是   hidden、auto、scroll，不是visible



#### link和@import的区别

1. link属于XHTML标签，而@import是CSS提供的
2. 页面被加载时，link会同时被加载，而@import引用的CSS会等到页面被加载完再加载
3. import只在IE 5以上才能识别，而link是XHTML标签，无兼容问题
4. link方式的样式权重高于@import的权重
5. link支持使用Javascript控制DOM去改变样式；而@import不支持


#### 介绍一下 Sass 和 Less 是什么？它们有何区别？

Sass (Syntactically Awesome Stylesheets)是一种动态样式语言，语法跟css一样(但多了些功能)，比css好写，而且更容易阅读。Sass语法类似与Haml，属于缩排语法（makeup），用意就是为了快速写Html和Css

Less一种动态样式语言. 将CSS赋予了动态语言的特性，如变量，继承，运算， 函数. LESS 既可以在客户端上运行 (支持IE 6+, Webkit, Firefox)，也可一在服务端运行 (借助 Node.js)

##### 区别：

Less在JS上运行，Sass在Ruby上使用

变量符不一样，less是@，而Scss是$，而且变量的作用域也不一样

Sass可以遍历任何类型的数据，Less只能使用递归函数循环数值

Less没有输出设置，Sass提供4种输出选项：nested、compact、 compressed和 expanded

##### 相同：

1、混入（Mixins）：class中的class

2、参数混入：可以传递参数的class，就像函数一样

3、嵌套规则：class中嵌套class，从而减少重复的代码

4、运算：css中用上数学

5、颜色功能：可以编辑颜色

6、名字空间：分组样式，从而可以被调用

7、作用域：局部修改样式

8、JavaScript赋值：在css中使用JavaScript表达式赋值



#### script 标签的defer和async区别

defer 完全不会阻碍 HTML 的解析，解析完成之后再按照顺序执行脚本

async 解析 HTML 过程中进行脚本的异步下载，下载成功立马执行，有可能会阻断 HTML 的解析



#### html语义化

当页面样式加载失败时能够让页面呈现清晰的结构

有利于SEO优化被搜索引擎收录，便于项目的开发与维护，使代码更具可读性



#### css中常见长度单位

1.px像素：

   相对长度单位,像素px是相对于显示器屏幕分辨率而言的。

2.em与rem（相对长度单位）：

​    em  : 继承父级元素的字体大小

​    rem ：1,其值不是固定的

​                2,相对于HTML根元素的字体大小（font-size）来计算的长度单位,如果没有设置html的字体大小，会以浏览器默认字体大小，一般是16px

3.vw / vh

​     vw相对视口宽度而定的，长度等于视口宽度的`1/100`假如浏览器的宽度为200px，那么1vw就等于2px（200px/100）

​     vh相对视口高度而定的，长度等于视口高度的`1/100`假如浏览器的高度为500px，那么1vh就等于5px（500px/100）

4. %

   一般来说就是相对于父元素

   1、对于普通定位元素就是我们理解的父元素

   2、对于position: absolute;的元素是相对于已定位的父元素

   3、对于position: fixed;的元素是相对于ViewPort（可视窗口）

5. vmin / vmax：关于视口高度和宽度两者的最小值或者最大值

6. pt ：设备像素（物理像素）

   dpr ：dpr =设备像素 / 设备独立像素

   ppi ：每英寸像素，值越大，图像越清晰





####  **居中布局

##### 水平居中

1.  行内元素: `text-align:center`
2.  块级元素: `margin:0 auto`
3.  绝对定位和移动: `absolute + transform`
4.  绝对定位和负边距: `absolute + margin`
5.  flex布局: `flex + justify-content:center`

##### 垂直居中

1.子元素为单行文本: `line-height:height`

2.`absolute + transform`

3.`flex + align-items:center`

4.table: `display:table-cell; vertical-align: middle`

5.利用position和top和负margin

##### 水平垂直居中

已知宽高：1.absolute+margin:auto

​                    2.absolute+margin-top+margin-left

​                    3.absolute+transform

​                    4.flex + justify-content + align-items

未知宽高：1.absolute+top:50%+left50%  + translate(-50%,-50%)

​                    2.flex+ justify-content + align-items

​                     3.父元素display: table-cell





​         1已知元素宽高:绝对定位+margin:auto:

```javascript
 div{
      width: 200px;
      height: 200px;
      background: green;
      position:absolute;
      left:0;
      top: 0;
      bottom: 0;
      right: 0;
      margin: auto;
  }
```



​         2 已知元素宽高:  绝对定位+负margin

```javascript
 div{
    width: 150px;
	height: 100px;
	background-color: deepskyblue;
	position: absolute;
	left: 50%;
	top: 50%;
	margin-left: -75px;
	margin-top: -50px;

   }
```

​         3 absolute+transform

```javascript
 div{
     width: 200px;
     height: 200px;
     background: green;
 
     position:absolute;
     left:50%;    /* 定位父级的50% */
     top:50%;
     transform: translate(-50%,-50%); /*自己的50% */
   }
```

​         4 flex + justify-content + align-items

```javascript
.box{
   height:600px;
 
   display:flex;
   justify-content:center;  //子元素水平居中
   align-items:center;      //子元素垂直居中
     /* aa只要三句话就可以实现不定宽高水平垂直居中。*/
    }
  .box>div{
    background: green;
    width: 200px;
    height: 200px;
   }
```



###### 未知宽高

1.  display

   ```javascript
   
   div{
   	display:flex;
       justify-content:center;
       align-items:center
   }
   ```

   

2. position(父相子绝) +transform   

   ```javascript
   //父元素
   
   div{
       position:relative
   }
   
   
   //子元素
   div{
       position:absolute;
       left:50%;
       top:50%;
       transform:translate(-50%,-50%)
   }
   
   
   ```

   



#### 怎么实现两栏布局

1.BFC

  float+overflow

```javascript
left：设宽+左浮动
right：overflow:hidden
```

2.父相子绝加margin-left

```javascript
父元素 position: relative
left,right :absolute
left:width:200px;left:0
right:width:100%,margin-left:200px

```

3.flex

```javascript
父元素display：flex
left :width:200px
right:flex:1
```



#### flex布局 

flex弹性布局，可以简便、完整、响应式地实现各种页面布局, 容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis）

（1）flex-direction：决定主轴的方向

​			row（默认值）：主轴为水平方向，起点在左端

​			row-reverse：主轴为水平方向，起点在右端

​			column：主轴为垂直方向，起点在上沿

​			column-reverse：主轴为垂直方向，起点在下沿

（2）flex-wrap：换行

​			nowrap（默认）：不换行

​			wrap：换行，第一行在上方

​			wrap-reverse：换行，第一行在下方

（3）flex-flow：flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap

（4）justify-content：主轴对齐方式

​			flex-start（默认值）：左对齐

​			flex-end：右对齐

​			center： 居中

​			space-between：两端对齐，项目之间的间隔都相等。

​			space-around：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。

​	5）align-items：侧轴对齐方式

​			flex-start：交叉轴的起点对齐。

​			flex-end：交叉轴的终点对齐。

​			center：交叉轴的中点对齐。

​			baseline: 项目的第一行文字的基线对齐。

​			stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。



#### 元素隐藏的方法

##### 方法：     

 display:none 、 visibility:hidden 和 opacity:0

##### 区别:

###### 1.占据空间

display不占空间， visibility和opacity隐藏后仍占据空间

###### 2.子元素是否继承

display子元素不继承；visibility会继承,通过visibility:visible 来显示子元素；opacity会继承

###### 3.事件绑定

display 和visibility无法触发事件；opacity可以触发事件

###### 4.过度动画

display 和visibility 无效；opacity有效



#### xhtml 和 html 区别

##### 1.基础语言

- XHTML是基于可扩展标记语言（XML）
- HTML是基于标准通用标记语言（SGML）

##### 2.标签大小写敏感

- xhtml的所有标签都应该使用小写
- html大小写不敏感

##### 3.标签闭合

- xhtml元素必须闭合，空元素也不例外，如<br />
- html没有强制要求，浏览器同样可以解析

##### 4.属性写法

- xhtml所有属性必须带引号，所有属性必须有值，必须小写
- html的属性可以简写，比如说对于布尔类型的属性，可以直接简写成属性名
  如:
  <input type="text" disabled>

##### 5.元素嵌套

- xhtml元素之间必须正确嵌套
- html有些元素不正确嵌套，浏览器同样也可以解析

##### 6.注释书写

在xhtml中，注释中不能出现“--”,否则就会报错

##### 7.命名空间

在xhtml的doctype生命下面必须紧跟一个命名空间

```javascript
<html xmlns="http://www.w3.org/1999/xhtml"> 
```

#### 外边距重叠？重叠的结果是什么？

在CSS当中，相邻的两个盒子的外边距能够结合成一个单独的外边距，合并外边距的方式被称为折叠，所结合成的外边距称为折叠外边距

两个相邻的外边距都是正数时，折叠结果是它们二者之间较大的值

两个相邻的外边距都是负数时，折叠结果是二者绝对值的较大值

两个外边距一正一负时，折叠结果是二者的相加的和



####  rgba() 和 opacity 区别

rgba:只用于元素的颜色或其背景色，子元素不会继承，字体不会改变

opacity :用于元素的透明效果，子元素可以继承，字体也会透明





#### **reset.css，为什么使用重置样式文件，对normalize.css的理解

reset.css用于重置css样式，由于浏览器的兼容问题，不同的浏览器对标签的默认样式值不同，若不重置样式会造成不同浏览器之间的显示差异

normalize 重置样式库  ，没有重置全部的样式风格，提供了一套合理的默认样式值，不同浏览器显示不同的样式(跨浏览器)



#### 对WEB标准及W3C的理解

##### web标准

   分为 结构、表现、行为3部分

结构：由html标签组成

表现：由CSS样式组成

行为：用户的页面交互，由JS组成



##### W3C

标签闭合、标签小写、不乱嵌套 （XHTML）
提高搜索机器人搜索几率 （DOM）
使用外链 css 和 js 脚本 （结构行为表现的分离）
文件下载与页面速度更快、内容能被更多的用户所访问、内容能被更广泛的设备所访问
容易维护、改版方便
提高网站易用性





#### 对浏览器内核的理解

主要分为两部分：渲染引擎（Rendering Engine）和 JS 引擎

- 渲染引擎：负责取得网页的内容（HTML、XML、图像等等）、整理讯息（例如加入CSS等），以及计算网页的显示方式，而后会输出至显示器或打印机。浏览器的内核的不一样对于网页的语法解释会有不一样，因此渲染的效果也不相同。全部网页浏览器、电子邮件客户以及其余它所须要编辑、显示网络的应用程序都须要内核
- JS引擎：解析和执行JavaScript来实现网页的动态效果

最开始渲染引擎和JS引擎并没有区分的很明确，后来JS引擎越来越独立，内核就倾向于只指渲染引擎



#### 常见的浏览器内核

IE:Trident内核

Chrome:以前是kebkit,现在是Blink

Firefox:Gecko内核

Safari:webkit内核

Opera:presto->webkit->Blink



#### css的继承和重用

##### 继承

   一个元素的属性能够被子元素所使用，称为继承

##### 重用

​     一个样式文件能够被多个页面使用，便于公共样式的重构





#### Css Hack理解

是通过在CSS样式中加入一些特殊的符号，让不同的浏览器识别不同的符号以达到应用不同的CSS样式的目的



#### **CSS Sprites(雪碧图、精灵图)

CSS Sprites  把多个小图标合成一个大图片，利用CSS的 background-image，background- repeat，background-position 的组合进行背景定位

##### 优点：

减小网页的http请求，提升页面的性能



##### 劣势：

1.开发较麻烦，测量繁琐；

2.维护麻烦，背景少量改动有可能影响整张图片





#### overflow属性

 scroll   必会出现滚动条
 auto   子元素内容大于父元素时出现滚动条
 visible   溢出的内容出如今父元素以外
 hidden  溢出隐藏



#### before 中(:: 和 :)双冒号和单冒号区别

- 单冒号(:)用于CSS3伪类，双冒号(::)用于CSS3伪元素

对于IE6/7/8仅支持单冒号表示法，而现代浏览器同时支持这两种表示法



#### **浮动

float:left/right/inherit/none(默认)

 设置元素的浮动，浮动后的元素 1.脱离了文档的普通流，使得浮动的元素不占据文档的位置，其他元素可以覆盖其位置  2.移动到指定位置



##### 浮动带来的问题

1. 父元素的高度没法被撑开，影响与父元素同级的元素
2. 与浮动元素同级的非浮动元素（内联元素）会跟随其后
3. 若非第一个元素浮动，则该元素以前的元素也须要浮动，不然会影响页面显示的结构

##### 清除浮动的方式

1. 父级div定义height
2. 浮动元素的父标签添加 overflow 为 hidden 或 auto，触发BFC
3. 新加一个标签，并添加样式 clear:both
4. 用after伪元素清除浮动（用于非IE浏览器）
5. 父级 div 定义 zoom（空标签元素清除浮动而不得不增长无心义代码的弊端，使用zoom:1用于兼容IE）



```javascript
{
    height:0;        // 1.为父元素设置高度
    overflow:hidden  // 2.父元素添加overflow， 通过触发BFC方式，实现清除浮动
    clear:both;      // 3.添加标签,设置clear  让父级div能自动获取到高度
    visibility:hidden;

}

// 4.父元素添加after伪元素
div:after{
    content:'';      
    display:block;
    clear:both
}
```





#### 兼容性BUG  IE6 的解决方法

1. 双边距BUG float引发的 使用display

2. 3像素问题 使用float引发的 使用dislpay:inline -3px

3. 超连接hover 点击后失效 使用正确的书写顺序 link visited hover active

4. IE z-index问题 给父级添加position:relative

5. Png 透明 使用js代码 改

6. Min-height 最小高度 !Important 解决’

7. select 在ie6下遮盖 使用iframe嵌套

8. 为何没有办法定义1px左右的宽度容器(IE6默认的行高形成的，使用over:hidden,zoom:0.08 line-height:1px)

9. ie 6 不支持!important





#### **height和line-height区别

height是元素的高度，不会因为换行改变

line-height是每一行文字的高度，如果文字换行整个盒子会增大(行数*行高)





#### **用css画三角形

使用border

箭头向上

```javascript
div{
	width:0;
    height:0;
    border-bottom:50px solid red;
    border-top:50px solid transparent;
    border-left:50px solid transparent;
    border-right:50px solid transparent;
}
```

#### **在网页中应该使用奇数还是偶数的字体？

偶数，转换方便开发



#### **position属性

static 默认值，无定位

fixed 固定定位，根据浏览器窗口定位

relative  相对自身定位，不脱离文档流 ，如果同时有left、right、top、bottom =>left、bottom

absolute  相对于有relative的父元素定位，脱离文档流，如果同时有left、right、top、bottom =>left、right、top、bottom





#### **双飞翼布局

左中右布局占满全屏，左右各200px，中间自适应，要求先加载中间块，写出结构及样式

```javascript
.box{
    width:100%
    height:100vh
}
.box > div{
     float:left
     height:100vh
}

.l{
     width:200px;  
     margin-left:-100%
}
.c{
     width:100%
}
.r{
     width:200px; 
     margin-left:-200px
}

<div class="box">
    <div class="c"></div>
    <div class="l"></div>
    <div class="r"></div>
</div>
```







## CSS3面试题

#### css3选择器

属性选择器

```javascript
a[src^="https"] 选择的src属性值以“https”开头的每个<a>元素
a[src$=".pdf"]  选择的src属性以“.pdf”结尾的所有<a>元素
a[src*="abc"]   选择的src属性中包含"abc"子串的每个<a>元素
```



##### 伪类选择器

###### 动态伪类

```javascript
//1.锚点伪类
:link   
:visited

//2.用户行为伪类
:hover
:active
:focus

//3.目标伪类
:target
当我们点击锚点链接时，对应id的元素会显示在视口

//4.checked状态伪类

```



###### nth选择器

```javascript
:first-child/last-child
:nth-child(n)
:nth-last-child(n)
:nth-of-type(n)
:nth-last-of-type
:first-of-type/:last-of-type
:only-child
:only-of-type
:empty  匹配无子元素包括文本节点的元素
```

###### 否定选择器：not





##### 伪元素选择器

###### :before

被选元素前面插入内容

###### :after

被选元素后面插入内容





#### css3圆角与阴影

##### 1.border-radius圆角

属性：

border-top-left-radius 左上角

border-top-right-radius 右上角

border-bottom-right-radius 右下角

border-bottom-left-radius 左下角

复合属性：

  4个值  border-radius：左上  右上  右下  左下       

  3个值  border-radius：左上 （右上和左下） 右下  

  2个值  border-radius：左上和右下   右上和左下

  1个值  4个角都生效



##### 2.box-shadow 阴影

box-shadow: 水平偏移量   垂直偏移量   模糊距离   阴影尺寸   阴影颜色   内/外阴影

- 偏移量：

​    水平： 正值 --- 右 ，负值 --- 左

​    垂直： 正值 --- 下 ，负值 --- 上

- 模糊距离：

   边界模糊，但是边界线未动

   由边界线向外模糊多少像素

- 
  阴影尺寸：

​    盒子阴影，上下左右都向外扩展多少像素

-  内/外阴影：

   inset(默认没有，也就是默认是外阴影)
   加上inset,盒子的阴影为内阴影
   扩展程度可为负值，但是模糊程度不可以  



##### 3.border-image图片作为边框



#### css3背景与渐变

##### background背景

background-cilp裁剪区域

```javascript
background-cilp：border-box / padding-box / content-box
border-box：背景被裁剪到边框盒(默认)
padding-box：背景被裁剪到内边距框
content-box：背景被裁剪到内容框
```

background-origin背景图像原始起始位置

```javascript
background-origin：border-box / padding-box / content-box(背景图片坐标原点与这三个有关系)
border-box：相对于边框来定位
padding-box：相对于内边距来定位
content-box：相对于内容框来定位
```

background-repeat是否重复背景图像

```javascript
repeat 默认,垂直水平重复
repeat-x 水平重复
repeat-y 垂直重复
no-repeat 不重复
inherit 规定应该从父元素继承 background-repeat 属性的设置
```

background-size 图像大小

```javascript
background-size：number / % / cover / contain
number：宽度 高度
cover：等比缩放填满
contain：等比缩放至某一边紧贴容器边缘
```

background-break元素可以被分成几个独立的盒子

```javascript
continuous    默认值。忽略盒之间的距离
bounding-box  把盒之间的距离计算在内
each-box      为每个盒子单独重绘背景
```



复合属性

```javascript
background：color position size repeat origin clip attachment url1,url2...
```



##### 渐变

###### 线性渐变

```javascript
background:linear-gradient(方向，开始颜色，结束颜色)

//方向
background: linear-gradient(red,blue)  //默认从上到下
background: linear-gradient(to right,red,blue)  //从左到右
background: linear-gradient(to right bottom,red,blue)  //对角
background: linear-gradient(角度,red,blue)   //角度(deg)

//颜色结点  默认每个颜色均匀分布
background: linear-gradient(red 10%,blue 20%,green 30%,yellow 40%); //从0%到10%，为红色，从10%到20%为红色到蓝色的渐变，从20%到30%为蓝色到绿色的渐变，从30%到40%，为绿色到黄色的渐变,从40%到100%为黄色
background: linear-gradient(red 10%,blue) //从0%到10%，为红色，从10%到100%为红色到蓝色的渐变
background: linear-gradient(red,blue 30%) //从0%到30%，为红色到蓝色的渐变
background: lineargradient(rgba(255,0,0,0),rgba(255,0,0,1)) //由透明色变为不透明色
```

###### 径向渐变

```javascript
background:radial-gradient(形状尺寸，开始颜色，结束颜色)
//形状
circle 圆形
ellipse 椭圆形

//尺寸大小
closest-side最近边
farthest-side 最远边
closest-corner最近角
farthest-corner最远角
background: radial-gradient(closest-side circle,red , blue)//最近边
//颜色结点
background:radial-gradient(circle,red 50% ,blue 70%)
```



#### css3过渡transition



| css属性名                  | 含义             | 值                                                           |
| -------------------------- | ---------------- | ------------------------------------------------------------ |
| transition-property        | 哪些属性可以过渡 | none:无属性改变;all默认所以属性改变;property元素属性名(width,color)，多个使用逗号分隔 |
| transition-duration        | 过渡持续时间     | 时间单位 s、ms                                               |
| transition-delay           | 过渡延迟时间     | 时间单位 s、ms                                               |
| transition-timing-function | 过渡运动曲线     |                                                              |
| transition                 | 复合属性         | property duration timing-function delay；                    |
|                            |                  |                                                              |

transition-timing-function过渡运动曲线

```javascript

linear：直线匀速
ease：默认，低速开始，加快，在结束前减慢
ease-in：低速开始
ease-out：低速结束
ease-in-out：低速开始和结束
cubic-bezier(n,n,n,n)：在 cubic-bezier 函数中自己的值，可能的值是从 0 到 1 的数值
```





#### css3变换transform



##### 兼容

```javascript
{
	transform:translate(10,10)         // W3c标准
	-webkit-transform:translate(10,10) // Safari Chrome
	-moz-transform:translate(10,10)    // firefox
	-ms-transform:translate(10,10)     // IE9
	-o-transform:translate(10,10)      // opera
}
```



##### 2D

###### translate()位移

translateX(X)				水平位移
translateY(Y)				垂直位移
translate(X,Y)            水平垂直位移

###### scale()缩放

scaleX()				水平缩放
scaleY()				垂直缩放
scale()	               水平垂直缩放



###### rotate(deg)旋转

###### skew()倾斜

skewX(x)      

skewY(y)

skew(deg,deg)     





##### 3D

###### translate()位移

translateZ()				  z轴位移
translate3D(x,y,z)         x、y、z轴位移的距离，必须设置3个长度



###### scale()缩放

scaleZ()
scale3D(x,y,z)	   x、y、z轴的缩放，必须设置三个倍数

###### rotate()旋转

rotateX()				x轴旋转
rotateY()				y轴旋转
rotateZ()				z轴旋转，等同于2D旋转 rotate()
rotate3D()              x轴、y轴、z轴一起旋转，设置4个值，前三个都是0或者1，对应的轴是否旋转，第4个值设置角度





#### css3动画

使元素从一种样式逐渐变化到另外一种样式的效果

@keyframes

```javascript
@keyframes  aa{
    from{}
    50%{}
    100%{}
}
```

animation复合属性

```javascript
            名称   持续时间   过渡类型      动画延迟时间    运行次数     动画是否反向播放   动画运行或者暂停 
animation : name duration timing-function   delay    interation-count   direction       play-state

```

1. animation-name动画名称

2. animation-duration对象动画的持续时间

3. animation-timing-function 对象动画的过渡类型

   ```javascript
   linear：直线匀速
   ease：默认，低速开始，加快，在结束前减慢
   ease-in：低速开始
   ease-out：低速结束
   ease-in-out：低速开始和结束
   cubic-bezier(n,n,n,n)：在 cubic-bezier 函数中自己的值，可能的值是从 0 到 1 的数值
   ```

4. animation-delay动画的延迟时间

5. animation-iteration-count动画的循环次数

   ```javascript
   number为数字，其默认值是1
   infinite：无限循环次数
   ```

6. animation-direction动画是否反向运动

   ```javascript
   normal : 正常方向
   reverse :反向运动
   alternate ： 先正常运动在反向运动，并持续交替运行， 需要配合循环属性使用
   alternate-reverse ： 先反向运动在正常运动，并持续交替运行， 需要配合循环属性使用
   ```

7. animation-play-state动画是否正在运行或已暂停

   ```javascript
   paused ： 指定暂停动画
   running : 默认值，制定正在运行的动画
   ```

8. animation-fill-mode动画结束后的状态

   ```javascript
   none：默认值，不设置对象动画之外的状态，DOM未进行动画前状态
   forwards：设置对象状态为动画结束时的状态，100%或to时，当设置animation-direcdtion为reverse时动画结束后显示为keyframes第一帧
   backwards：设置对象状态为动画开始时的状态,（测试显示DOM未进行动画前状态）
   both：设置对象状态为动画结束或开始的状态，结束时状态优先
   ```

   



