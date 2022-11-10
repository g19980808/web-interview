# 自我介绍

##### 面试官你好，我叫张文博，来自陕西省西安市。毕业于西南科技大学城市学院， 最近在做的项目是大方智能Ai管

##### 理平台,它主要针对主要是针对电子产品的销售；机械设备租赁情况的集中式管理和客户信息收集，项目中我主要

##### 负责的是代理商模块以及项目的更新迭代。还有一个大屏项目 ，主要负责商品详情页的模块的开发，登录注册页

##### 面的布局以及逻辑的处理，还有就是负责年度总结模块的数据可视化。关于技术栈的话我熟练掌握并且可以运用 

##### vue框架，能够使用webpack、axios、vuex、vue-router等vue全家桶进行组件化与模块化开发。同时也了解

##### 闭包，面向对象编程等es6的知识可以熟练使用Element,vant，Echart,Datav等组件库和类库。熟练使用 

##### sass，less 等 CSS 预处理器，可以使用uniapp进行小程序的开发，同时在工作中我具备良好的逻辑分析能力,以

##### 及独立思考解决问题的能力,即便真的碰到难以解决的问题，也会和同事进行有效的沟通,在工作之余我也会学习前

##### 沿技术,并尽可能的抽出时间去看一些大牛博客和官方网站，让自己对于先有的技术又更近一步的了解，我的自我

##### 介绍完毕，谢谢。



自我介绍
		面试官您好,我叫张文博,来自陕西西安,毕业于西南科技大学城市学院,从事web前端开发工作已有3年
任职于2家公司,熟练掌握Vue技术栈,能够熟练运用Vue全家桶以及第三方UI组件库(element,vant,echars,Datav等)，有良好的代码规范和封装意识,能够有效的和后端,Ui,以及根据客户需求合理沟通完善解决问题,对新的技术有强烈的追求和较强的学习能力,可以快速的适应公司环境,
 最近在做的项目是大方智能Ai管理平台,这个项目主要是针对电子产品销售；机械设备租赁情况的集中式管理和客户信息收集,主要的板块又项目管理,设备管理，代理商管理，常见问题反馈，权限管理，日志管理等，我主要负责的是代理商管理,以及用户常见问题反馈功能的开发与展示

还有一个与之相结合的大方智能数据可视化平台，是一个大屏项目，我主要负责商品详情页列表页的组件开发，登录注册页面的布局以及逻辑的处理，还有就是负责年度总结模块的数据可视化
在工作中我具备良好的逻辑分析能力,以及独立思考解决问题的能力,即便真的碰到难解决的问题，也能与同事有效的沟通与团队协作,在工作之余我也会学习前沿技术,并尽可能的抽出时间去看一些博客和官方网站，让自己对于先有的技术更上一层楼,

我的介绍完毕，

# html和CSS

![image-20220212145934226](C:\Users\张文博\AppData\Roaming\Typora\typora-user-images\image-20220212145934226.png)

## flex布局  

flex弹性布局，可以简便、完整、响应式地实现各种页面布局, 容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis）

（1）flex-direction：决定主轴的方向

​			row（默认值）：主轴为水平方向，起点在左端。

​			row-reverse：主轴为水平方向，起点在右端。

​			column：主轴为垂直方向，起点在上沿。

​			column-reverse：主轴为垂直方向，起点在下沿。

（2）flex-wrap：换行

​			nowrap（默认）：不换行。

​			wrap：换行，第一行在上方。

​			wrap-reverse：换行，第一行在下方。

（3）flex-flow：flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap。

（4）justify-content：主轴对齐方式

​			flex-start（默认值）：左对齐

​			flex-end：右对齐

​			center： 居中

​			space-between：两端对齐，项目之间的间隔都相等。

​			space-around：每个项目两端的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。

​           space-evenly:   每个间隔相等

​	5）align-items：侧轴对齐方式

​			flex-start：交叉轴的起点对齐。

​			flex-end：交叉轴的终点对齐。

​			center：交叉轴的中点对齐。

​			baseline: 项目的第一行文字的基线对齐。

​			stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。

## 清除浮动的方法 

1. 在标签尾部添加空块级标签，设置样式属性为：clear：both；缺点：如果页面浮动布局多，就要增加很多空div，不利于页面的优化。 

2. 父级定义伪类after和zoom，.box:after{display:block; clear:both; content:""; visible:hidden; height:0;}  .box{ zoom: 1 } 
3. 简单粗暴，父级设置overflow:hidden，缺点是不能和position配合使用 
4. 直接给父元素单独设置高度（height）；缺点：只适合高度固定的布局，要给出精确的高度，如果高度和父级div不一样时，会产生问题。对于响应式布局会有很大影响。

## 元素垂直居中

1、通过verticle-align:middle实现CSS垂直居中。

2、通过display:flex实现CSS垂直居中。

3、定位到垂直居中的位置。

4、通过line-height实现CSS垂直居中。

## 如何垂直居中一个浮动元素

1、给父元素设置一个相对定位，然后把浮动元素设置margin：auto、绝对定位并且设置left:0,right:0,top:0,bottom:0;

2、给父元素设置一个相对定位，然后给这个浮动元素设置绝对定位并设置top：50%，left：50%，margin-top和margin-left为二分之一的宽和高

## 盒子水平垂直居中方法

①定位：（常用方法,推荐）

position:absolute;

position:relative;

left:值;

top:值;

②display:table-cell;

③外边距：margin-left:值;

margin-top:值;

④margin:auto;（不兼容低版本的IE浏览器）

⑤弹性盒模型：display:flex;（常用方法,推荐）

justify-content:conter;

align-itens:center;

⑥用transform的属性translate平移，不仅能实现绝对居中同样的效果，也

支持联合可变高度方式使用。

使用top:50%; left:50%;时，是以盒子的左上角为原点定位，是左上角的原

点居中，但是元素本身并不居中。

transform：translate(-50%，-50%):分别向左向上移动自身长宽的

50%，使其位于中心。

transform: translate(-50%,-50%)导致的像素模糊问题解决办

法：

/** 这 0.5px加或者减都可以 */

transform: translat(calc(-50% + 0.5 px), calc(-50% +

0.5 px))；

⑦用calc计算

## 说下盒模型

content、border、padding、margin

~~~
盒模型是有两种标准的，一个是标准模型，一个是IE模型。

content，而IE盒模型的宽高是content+padding+border。
~~~



~~~
CSS如何设置这两种模型 
	使用CSS3 的属性 box-sizing 属性来区分：content-box(标准)、border-box(IE)。
~~~



~~~
JS如何设置获取盒模型对应的宽和高
	window.getComputedStyle(dom).width/height  
	dom.offsetWidth/offsetHeight    最常用的，也是兼容最好的。
~~~



## BFC

~~~
BFC是什么：  
		他是一个独立的渲染区域,通俗点说就是BFC就是页面上的一个隔离的独立容器,容器里面的元素布局和外面的元素互不影响
		
如何触发BFC：
		float的值不为none时触发
		Positon值不为absolute和fixed时触发
		Overflow值不为visible时触发
		display值为 inline-block table-cell时触发

BFC的用途：
		（1）防止margin重叠
		（2）清除内部浮动
		（3）消除文本环绕做出自适应两栏布局
~~~

## 响应式布局

​		响应式布局指的是同一页面在不同屏幕尺寸下有不同的布局。传统的开发方式是PC端开发一套，手机端再开发一套，而使用响应式布局只要开发一套就够，缺点就是`CSS`比较多



## 重绘和回流

**什么是重绘？**

由于几何属或样式发生改变不影响布局而需要重新渲染的过程，就叫重绘。

**什么是回流？**

由于布局发生改变需要重建就叫做回流

**什么原因会导致回流**

添加或者删除可见的DOM元素；

元素位置改变；

元素尺寸改变——边距、填充、边框、宽度和高度

页面渲染初始化；

浏览器窗口尺寸改变——resize事件发生时；

回流必将引起重绘，而重绘不一定会引起回流。

## HTML5 新特性 

1.语义化标签

2.增强型表单

3.视频和音频

4.Canvas绘图

5.SVG绘图

6.地理定位

7.拖放API

8.WebWorker

9.WebStorage

10.WebSocket

# css和js性能优化问题

## css性能优化

~~~
（1）内联首屏关键CSS
		指页面的重要内容出现在屏幕上的时间（这会影响用户看到页面所需等待的时间）
		通过通过link标签引用外部CSS文件，使用外部CSS文件时，需要在HTML文档下载完成后才知道所要引用的CSS文件，然后才下载它们，内联CSS能够使浏览器开始页面渲染的时间提前，因为在HTML下载完成之后就能渲染了。
（2）文件压缩  使用webpack、gulp等对css进行压缩
（3）去除没用的css代码
（4）减少使用昂贵的属性
~~~



## js性能优化

#### 垃圾收集

​	对象相互引用会导致引用计数始终为2，所以用完对象后应将引用设为null
​	当数据不再有用时，需要通过将值设为null来解除引用

#### 在js中尽量减少闭包的使用(闭包不会释放栈内存)

​	循环进行事件绑定时，尽可能使用自定义属性，而不用创建闭包来存储信息

​	在最外层形成一个闭包，把一些后期需要的公共信息进行存储，而不是每一个方法都创建一个闭包（例如单例模式）。

​	尽可能手动释放掉不需要的内存。

#### 进行js和css文件的合并，减少http请求的次数，尽可能将文件进行压缩，减少请求资源的大小

webpack这种自动化构建工具，可以帮我们实现代码的合并和压缩（工程化开发）

#### js避免“嵌套循环”（会额外增加很多次循环次数）和“死循环”（浏览器会死机）



#### 采用图片“懒加载”，加快第一次加载的速度，实际并没有减少请求次数

​		步骤：开始加载页面是，所有的真实图片都不去发送请求，而是给一张占位的背景图，当页面加载完后，并且图片出现在可是区域再去做图片加载

#### 减少对DOM的操作（主要是减少DOM的重绘和回流（重排）） 





# js

## JS数据类型：

基本数据类型：**Number、String、Boolean、Null、 Undefined、Symbol（ES6），**这些类型可以直接操作保存在变量中的实际值。

引用数据类型：Object（在JS中除了基本数据类型以外的都是对象，数据是对象，函数是对象，正则表达式是对象）。  

基本数据类型是指存放在栈中的简单数据段，数据大小确定，内存空间大小可以分配，它们是直接按值存放的，所以可以直接按值访问。

引用数据类型也叫对象数据类型，包括function,object,array,date,RegExp等可以可以使用new创建的数据，又叫对象类型，他们是存放在堆(heap)内存中的数据。       

## JS中的作用域：

在ES5中，没有块级作用域，JS的作用域分为函数作用域和全局作用域两种。内部环境可以通 过作用域链访问所有的外部环境，但是外部环境不可以访问内部环境中的任何变量和函数。这些环境的访问顺序是线性有次序的。在ES6中，新增了let和const，这两个类型的变量只存在于块级作用域中，并且不存在变量提升。         

## 原型和原型链：

原型：每个函数都有 prototype 属性，该属性指向原型对象；使用原型对象的好处是所有对象实例共享它所包含的属性和方法。

原型链：主要解决了继承的问题；每个对象都拥有一个原型对象，通过__proto__ 指针指向其原型对象，并从中继承方法和属性，同时原型对象也可能拥有原型，这样一层一层，最终指向 null。

## 判断数据类型的方法

#### 1.typeof：    检测基本数据类型

  不能判断object和Array

  不能判断null和object    

   typeof null;      //object 无效    

   typeof [] ;         //object 无效  

   typeof new RegExp();      //object 无效 

#### 2.instanceof    检测引用数据类型

  instanceof 是用来判断 A 是否为 B 的实例，表达式为：A instanceof B，如果 A 是 B 的实例，则返回 true,否则返回 false。        

  在这里需要特别注意的是：instanceof 检测的是原型 

#### 3.object.prototype.toString.call()    精准判断数据类型

是 Object 的原型方法，调用该方法，默认返回当前对象的 [[Class]] 。这是一个内部属性，其格式为 [object Xxx] ，其中 Xxx 就是对象的类型



##  数组 添加与删除 的方法？ 

​    添加 删除：unshift,push ; pop,shift，splice         

​	其他方法：indexof()  concat()   slice()   reduce()数组相加求和                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  

## 数组去重

1.双层循环，外层循环元素，内层循环时比较值，如果有相同的值则跳过，不相同则push进数组

2.双层循环，外层循环元素，内层循环时比较值，值相同时，则删去这个值，注意点:删除元素之后，需要将数组的长度也减1.

3.利用对象的属性不能相同的特点进行去重

4.数组递归去重：运用递归的思想，先排序，然后从最后开始比较，遇到相同，则删除

5.利用indexOf以及forEach

6.利用ES6的set：Set数据结构，它类似于数组，其成员的值都是唯一的。利用Array.from将Set结构转换成数组

## 判断对象是否为数组或者函数的方法

方法一： instanceof: var arr=[]; console.log(arr instanceof Array) //返回true

 方法二： constructor: console.log(arr.constructor == Array); //返回true

 方法三： Array.isArray() console.log(Array.isArray(arr)); //返回true



## 深拷贝和浅拷贝                                  以及深浅拷的实现：

浅拷贝只复制指向某个对象的指针而不复制对象本身，新旧对象还是共享同一块内存。但深拷贝会另外创造一个一模一样的对象，新对象跟原对象不共享内存，修改新对象不会改到原对象 （在某些引用类型值不更新的情况下用深拷贝）

	深浅拷贝的实现 :  使用ES6 assign 也可以实现数据的快速浅拷贝  
	 	定义一个obj对象
	 	var obj3 = Object.assign(obj)



~~~
深拷贝的实现:  
	（1）使用JSON 对象实现深拷贝   
		var obj3 = JSON.parse(JSON.stringify(obj))   
    	obj.friends.push('lisi')
    （2）通过jQuery的extend方法实现深拷贝
    （3）最常用的是手写一个递归进行数据的深拷贝
~~~



9. 

## 防抖节流

防抖节流就是使用定时器来实现我们的目的。

防抖(debounce)：

在事件被触发n秒后再执行回调，如果在这n秒内又被触发，则重新计时。

典型的案例就是输入框搜索：输入结束后n秒才进行搜索请求，n秒内又输入的内容，则重新计时。

节流(throttle)：

规定在一个单位时间内，只能触发一次函数，如果这个单位时间内触发多次函数，只有一次生效。

典型的案例就是鼠标不断点击触发，规定在n秒内多次点击只生效一次。购物车提交按钮

## 为什么要掌握防抖和节流

函数节流与函数防抖都是可以限制函数的执行频次，根据不同的场景来对

执行频率进行限制，避免了函数触发频率过高导致的响应速度跟不上触发频率，出现延迟，假死或卡顿的现象。

##  forEach和for in 和for of的区别？

​    forEach更多用来遍历数据

​	for in 一般用来遍历对象或者json

​	for of 数组对象都可以便利，遍历对象需要通过和object.key()

​	for in 循环出的是key , for of 循环出来的时value

## this

#### this的指向问题

1.普通函数中，this指向window

2.在构造函数中，this指向创建的对象（指向构造函数的实例，原型对象里的this，指向的也是实例对象）

3.在方法生命中，this指向调用者

4.在定时器中，this指向window

5.在事件中，this指向事件源

6.在立即执行函数中，this指向window

7.在对象的方法中，this指向的是对象

#### 改变this指向的方法

1.call()     

2.apply()  

3.bind()   

#### 改变this指向方法的区别

1.call、apply与bind区别：前两个可以自动执行，bind不会自动执行，需要手动调用

2.call、bind与apply区别：前两个都有无数个参数，apply只有两个参数，而且第二个参数为数组

## 继承有哪些方式

1、call 、apply:不建议使⽤浪费内存

2、原型对象继承

3、原型拷⻉继承

4、原型链继承

5、混合继承

6、继承继承

7、ES6 类继承

## js如何更改对象的属性

  replace函数

## 箭头函数和普通函数的区别         

1. 相比普通函数更简洁的语法 

2. 没有this,捕获其所在上下文的 this 值，作为自己的 this 值 

3. .不能使用new,箭头函数作为匿名函数,是不能作为构造函数的,不能使用new 

4. 不绑定arguments，用rest参数...解决    let test3=(...a)=>{console.log(a[1])} //22

5. . 使用call()和apply()调用:由于 this 已经在词法层面完成了绑定，通过 call() 或 apply() 方法调用一个函数时，只是传入了参数而已，对 this 并没有什么影响： 

6. 箭头函数没有原型属性 

7. 不能简单返回对象字面量    let fun5 = ()=>({ foo: x })   //如果x => { foo: x }  //则语法出错 

8. 箭头函数不能当做Generator函数,不能使用yield关键字 

9. 箭头函数不能换行

   

## 回调地狱

多个回调函数嵌套出现的代码书写结构叫做 回调地狱 + 代码的阅读性和维护性要低了, 代码书写的不是不对, 是不好



## http和https的区别

HTTP的URL由 http://起始且默认使用端口80，而HTTPS的URL由https://起始且默认使用端口443

HTTP是超文本传输协议，信息是明文传输，HTTPS则是具有安全性的 SSL 加密传输协议

HTTP的连接很简单，是无状态的，HTTPS 协议是由 SSL+HTTP 协议构建的可进行加密传输、身份认证的网络协议，比 http 协议安全



## 跨域问题如何解决

CORS

服务器代理

nginx

jsonp



## 跨域解决方法

1、JSONP 使用简单且兼容性不错，但是只限于 get 请求。利用 src 不受同源策略的影响 => 利用 script 标签会把所有内容当作 JS 代码来执行 => 我们就绕开了浏览器同源策略的影响

2、CORS(跨域资源共享) 需要浏览器和后端同时支持。IE 8 和 9 需要通过 XDomainRequest 来实现。

3、服务器代理(常用) 切换到 nginx 服务器, 使用 nginx 服务器进行代理配置 -> 配置好以后, 请求的时候只要请求代理标识符就可以了



## Cookie,sessionStorage和localStorage

相同点:  cookie,sessionStorage和localStorage都是用与客户端存储数据，每一个都有自己的存储大小和到期时间

不同点:   1.存储大小不同

​					cookie数据存储大小不能大于4k

​					sessionStorage和localStorage存储大小可以达到5M

​				2.有效时间不同

​					cookie在设置的有效期内一直有效

​					localStorage存储持久数据,只要不动手清楚则一直存在

​					sessionStorage数据在当前浏览器关闭后就会自动清除

​				3.数据与服务器之间的交互方式不同

​					cookie的数据会自动传递到服务器端,服务器端也可以写cookie到客户端

​					sessionStorage和localStorage不会吧数据自动传到服务器端,仅在本地存储                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      



## get 和 post区别

Get的参数拼接到URL的后面，他的参数大小受限于浏览器url大小，一般不会超过32k，服务器数据接收只接收一次，参数携带在url中，安全性低

Post的参数是在请求体中，他的参数大小是1G，服务器数据接收次数会根据数据大小，可多次接收，相比Get请求，post请求安全性更高

## 虚拟DOM

~~~
虚拟 dom 和原生 dom

（1）原生dom是浏览器通过dom树渲染的复杂对象，属性非常多；\****

（2）虚拟dom是存在于内存中的js对象，属性远少于原生的dom对象，它用来描述真实的dom，并不会直接在浏览器中显示；

（3）原生dom操作、频繁排版与重绘的效率是相当低的，虚拟dom则是利用了计算机内存高效的运算性能减少了性能的损耗；

（4）虚拟DOM进行频繁修改，然后一次性比较并修改真实DOM中需要改的部分，最后并在真实DOM中对修改部分进行排版与重绘，减少过多DOM节点排版与重绘损耗

~~~



~~~
虚拟DOM的优劣如何？实现原理？
		虚拟dom是用js模拟一颗dom树,放在浏览器内存中，相当于在js和真实dom中加了一个缓存，利用dom diff算法避免了没有必要的dom操作，从而提高性能。

优点：
（1）虚拟DOM具有批处理和高效的Diff算法,最终表现在DOM上的修改只是变更的部分，可以保证非常高效的渲染,优化性能；
（2）虚拟DOM不会立马进行排版与重绘操作，对虚拟DOM进行频繁修改，最后一次性比较并修改真实DOM中需要改的部分；
（3）虚拟 DOM 有效降低大面积真实 DOM 的重绘与排版，因为最终与真实 DOM 比较差异，可以只渲染局部；

缺点：
（1）首次渲染大量DOM时，由于多了一层虚拟DOM的计算，会比innerHTML插入慢；
~~~

## diff算法

~~~
diff算法是一种通过同层的树节点进行比较的高效算法，避免了对树进行逐层搜索遍历，所以时间复杂度只有 O(n)。、

diff算法有两个比较显著的特点：
1、比较只会在同层级进行, 不会跨层级比较。
2、在diff比较的过程中，循环从两边向中间收拢。

diff流程： 首先定义 oldStartIdx、newStartIdx、oldEndIdx 以及 newEndIdx 分别是新老两个 VNode 的两边的索引。
~~~



## 闭包

~~~
概念:
	当一个函数内部嵌套另一个函数，子函数可以访问到父级函数中的变量。(闭包的最典型的应用是实现回调函数）
	
条件: 必须是嵌套关系    内部函数访问其所在的作用域  在所在作用域外被调用

闭包的作用：
	使变量在内存中保存不被销毁。
	延长了函数内局部变量的作用范围。
	
闭包的使用场景:
	1.setTimeout:原生的setTimeout传递的第一个函数不能带参数，通过闭包可以实现传参效果。
	2.函数防抖:在事件被触发n秒后再执行回调，如果在这n秒内又被触发，则重新计时。
	实现的关键就在于setTimeOut这个函数，由于还需要一个变量来保存计时，考虑维护全局纯净，可以借助闭包来实现
	3.封装私有变量
	4.回调
	
	
闭包的缺点：占用内层空间 大量使用闭包会造成 栈溢出

闭包的优化:
	由于闭包会一直占用内存空间，直到页面销毁，我们可以主动将已使用的闭包销毁：将闭包函数赋值为null 可以销毁闭包
~~~



## 微任务和宏任务

~~~
 宏任务：当前栈中执行的代码是宏任务
 微任务：当前宏任务执行完，在下一个宏任务开始之前需要执行的任务，就是微任务，又被称为回调事件。 promise 	nextTick
 
~~~



## 缓存                           (强缓存和协商缓存。) 

缓存分为强缓存和协商缓存。

强缓存不过服务器，协商缓存需要过服务器，协商缓存返回的状态码是304。两类缓存机制可以同时存在，强缓存的优先级高于协商缓存。当执行强缓存时，如若缓存命中，则直接使用缓存数据库中的数据，不再进行缓存协商。



## Axios和Ajax

	Axios 是一个基于 promise 的 HTTP 库，可以用在浏览器和 node.js 中。
	特点：
	1.从浏览器中创建 XMLHttpRequests
	2.从 node.js 创建 http 请求
	3.支持 Promise API
	4.自动转换 JSON 数据
~~~
AJAX 是与服务器交换数据并更新部分网页的，在不重新加载整个页面的情况下。
Ajax = 异步 JavaScript 和 XML（标准通用标记语言的子集）。
~~~





## 第二次打开网页为什么比第一次快？

​       主要是因为第一次加载页面过程中，缓存了一些数据，之后再加载就直接从缓存中获取而不用请求服务器，所以速度更快，也减轻了服务器的压力

# ES6

##  let const var的区别

var声明变量可以重复声明，而let不可以重复声明

var是不受限于块级的，而let是受限于块级

var会与window相映射（会挂一个属性），而let不与window相映射

var可以在声明的上面访问变量，而let有暂存死区，在声明的上面访问变量会报错

const声明之后必须赋值，否则会报错

const定义不可变的量，改变了就会报错

const和let一样不会与window相映射、支持块级作用域、在声明的上面访问变量会报错

## 模版字符串

## es6新增判断数组的方法：Array.isArray()                                                                                                            

## es6中set和map方法：

ES6 提供了新的数据结构 Set。它类似于数组，但是成员的值都是唯一的，没有重复的值。Set 本身是一个构造函数，用来生成 Set 数据结构。

ES6 提供了 Map 数据结构。它类似于对象，也是键值对的集合，但是“键”的范围不限于字符串，各种类型的值（包括对象）都可以当作键   

## ES6新增数组方法

    forEach  
    	循环数组，无返回值，不改变原数组
    	不支持return操作输出，return只用于控制循环是否跳出当前循环

~~~js
filter
使用return操作输出，会循环数组每一项，并在回调函数中操作
返回满足条件的元素组成的数组，不改变原数组
~~~

~~~json
map
输出的是return什么就输出什么新数组
原数组被“映射”成对应新数组，返回新数组，不改变原数组
~~~

~~~json
find
查找数组中第一个满足条件的项，找不到返回undefined
输出的是一旦判断为true则跳出循环输出符合条件的数组元素
~~~

~~~
some
返回布尔值，遇到满足条件变跳出循环
~~~

~~~
every
返回布尔值，遇到不满足条件跳出循环
~~~

~~~
reduce  [1,[1,2],3]===> [1][1]
累加器，输出的是return叠加什么就输出什么
回调函数参数四个
pre: 初始值（之后为上一操作的结果）
cur: 当前元素之
index: 当前索引
arr: 数组本身
主要有以下几种用法：
1.数组求和
[1,2,3,4].reduce((pre, cur) => pre + cur)//10
2.二维数组转为一维数组
[[1, 2], [3, 4], [5, 6]].reduce(( acc, cur ) => [...acc, ...cur], [])//[1, 2, 3, 4, 5, 6]
3.计算数组中每个元素出现的次数
const arraySum = (arr, val) => arr.reduce((acc, cur) => {
return cur == val ? acc + 1 : acc + 0
}, 0);
let arr = [1, 2, 3, 4, 5];
arraySum(arr, 0) //3
4.代替filter和map的组合
const characters = [
{ name: 'ironman', env: 'marvel' },
{ name: 'black_widow', env: 'marvel' },
{ name: 'wonder_woman', env: 'dc_comics' },
];
console.log(characters.filter(character => character.env === 'marvel').map(character => Object.assign({}, character, { alsoSeenIn: ['Avengers'] })));

console.log(characters.reduce((acc, character) => {
return character.env === 'marvel'
? acc.concat(Object.assign({}, character, { alsoSeenIn: ['Avengers'] }))
: acc;
}, [])
)
~~~



~~~
includes   判断数组是否包含某个元素，不用return，不用回调函数，返回布尔值
~~~

## map和forEach区别

 forEach()方法不会返回执行结果，而是undefined。也就是说，forEach()会修改原来的数组。 map()方法会得到一个新的数组并返回。

## 箭头函数的this指向

由于箭头函数不绑定this， 它会捕获其所在（即定义的位置）上下文的this值， 作为自己的this值 

1. 所以 call() / apply() / bind() 方法对于箭头函数来说只是传入参数，对它的 this 毫无影响。 
2. 考虑到 this 是词法层面上的，严格模式中与 this 相关的规则都将被忽略 作为方法的箭头函数this指向全局window对象，而普通函数则指向调用它的对象

## Promise   

简单来说可以把promise当作一个装着异步操作结果的容器。从语法上说，

Promise 是一个对象，从它可以获取异步操作的消息。Promise 提供统一的

API，各种异步操作都可以用同样的方法进行处理。它将异步函数以同步的方式

书写，也解决了回调地狱问题

特点：（1）对象状态不受外界影响

​           （2）一旦状态改变，就不会再变，任何时候都可以得到这个结果

缺点：（1），无法取消promise，一旦新建它就会立即执行，无法中途取消

​           （2），如果不设置回调函数，promise内部抛出的错误，不会反应到外部

​           （3）无法得知目前进展到哪一个阶段（刚刚开始还是即将结束）

三个状态：进行中、已成功、以失败









## async和await

async、await 优缺点

async 和 await 相比直接使用 Promise 来说，

优势在于处理 then 的调用链，能够更清晰准确的写出代码。

缺点在于滥用 await 可能会导致性能问题，因为 await 会阻塞代码，也许之后的异步代码并不依赖于前者，但仍然需要等待前者完成，导致代码失去了并发性。

**注意:   async和await  使用try  catch捕获异常**



## 并发和并行

- 并发他是一个宏观概念，假如有两个任务有任务A和B ，在一段时间内通过任务间的切换完成了这两个任务，这种情况就可以称之为并发。（在一段时间内分别完成两个任务叫并发）
- 并行是微观概念，假设 CPU 中存在两个核心，那么我就可以同时完成任务 A、B。同时完成多个任务的情况就可以称之为并行。（在同一时间完成了多个任务叫做并行）



## Promise中reject和catch处理上有什么区别

reject时用来抛出异常,catch是用来处理异常

reject时Promise的方法,而catch是Promise实例的方法

reject后的东西，一定会进入then中的第二个回调，如果then中没有写第二个回调,则进入catch网络异常，会直接进入catch而不会进入then的第二个回调

## 自己实现promise的大体思路

1. 首先需要一个异步的操作方法,满足异步回调。所以选择加入setTimeout 作为实现的基础， 让函数实现延迟触发。
2. 然后就是需要保持一个原则，控制 promise 改变状态的只有 promise 构造函数里的 reslove 、 reject 函数。
3.  链式调用的原理， 类似jQuery，它会在调用方法后， return this. 从而形成链式调用。所以我们采用在调用then(fn)、 catch(fn) 后 会返回一个新的 promise 对象， 然而 这个 promise 对象 受到 它的上级promise 对象的状态结果 和 fn 运行结果的控制。



# VUE

## 对前后端分离的理解

​		前后端分离就是他给开发工作带来了很多好处，在以前还没有前后端分离这个概念的时候，

​		使用的是一种经典的设计模式MVC模式，前端开发不盛行，很多后端开发人员还需要兼顾前端开发的工作，前后端的耦合性特别强，

​		在jsp时代，前端写好的页面最后要和后端实现交互，需要程序员手动的更改代码，这是很大的一个工作量，前端和后端人员都不愿意去做这件事。

​		**前后端分离过后，通过前后端预先定义好接口规范，前后端进行独立部署和开发，后端只需要提供接口供前端调用就可以了，这样一来使得解耦的效果变强了，这对工作效率的提升是巨大的，对于后期的维护只需要前后端单独完成就可以了！**

## MVVM    说一下你的理解

m->model,v->view,vm->viewModel。dom通过监听事件操作vue里的data，反之vue中的data通过指令操作dom，也就是用数据更新视图，我的理解就是这样的。

## 为什么使用Vue开发

1.单项数据流

2.数据双向绑定

3.单页面开发应用

4.单页面路由

## vue中的组件通讯  

1、props （父传子）和$emit（子传父）

父组件向子组件传递数据是通过prop传递的，子组件传递数据给父组件是通过$emit触发事件

2、$attrs （父传子）和$listeners（子传父）

3、中央事件总线 bus

上面两种方式处理的都是父子组件之间的数据传递，而如果两个组件不是父子关系呢？这种情况下可以使用全局事件总线的方式。新建一个Vue事件bus对象，然后通过bus.$emit触发事件，用bus.$on监听触发的事件。

4、provide和inject

父组件中通过provider来提供变量，然后在子组件中通过inject来注入变量。不论子组件有多深，只要调用了inject那么就可以注入provider中的数据。而不是局限于只能从当前父组件的prop属性来获取数据，只要在父组件的生命周期内，子组件都可以调用。

6、$parent和$children

7、boradcast和dispatch

8、vuex处理组件之间的数据交互 如果业务逻辑复杂，很多组件之间需要同时处理一些公共的数据，这个时候才有上面这一些方法可能不利于项目的维护，vuex的做法就是将这一些公共的数据抽离出来，然后其他组件就可以对这个公共数据进行读写操作，这样达到了解耦的目的。

## vue父子组件传值？

​    父传子：子用props接父传过来的值，详细说：父组件注册子组件时候，给子组件绑定一个自定义属性，子用props接

​    子传父：子组件向父组件传值是通过$emit触发事件做到。详细说：在父组件中注册子组件，给子组件绑定并监听一个自定义事件，在子组件中使用$emit触发刚才的自定义事件，$emit(事件名，参数)，父组件中的自定义事件对应的回调函数就能接收到子组件传来的数据

## vue页面级组建之间传值

1.使用vue-router通过跳转链接带参传值  

2.使用本地存储localStorge

3.使用vuex对数据进行管理传值

## v-model 双向数据绑定的实现原理

​    vue内部使用object.defineProperty方法给所有数据加上getter和setter方法，数据有变化时，通知订阅者watcher，watcher会触发它的update方法，对视图进行更新。也就是说数据发生变化时，视图跟着变化。

​	v-model是vue的双向绑定的指令，它可以将页面上输入的值同步更新到绑定的data属性当中去， 同时也会在更新data绑定属性时候，更新页面上输入控件的值。

## watch中能不能使用箭头函数

不能使用箭头函数定义watcher（回调）函数，因为箭头函数的this是指向定义函数时所在的作用域(window)，所以里面的 this 将不会按照期望指向 Vue 实例

如果非要使用箭头函数也是可以的，我们通常的一个做法是在组件data函数中中定义var _self = this然后再组件中用_self引用vue实例。

## computed和watch区别

computed：计算属性是基于它们的依赖进行缓存的，只有在它的相关依赖发生改变时才会重新求值。

watch监听对象需要深度监听，默认是浅监听    // 开启深度监听用     deep: true  //借助computed计算属性监听

当页面中有某些数据依赖其他数据进行变动的时候，可以使用计算属性computed。

watch用于观察和监听页面上的vue实例，如果要在数据变化的同时进行异步操作或者是比较大的开销，那么watch为最佳选择。

## v-if和v-show什么区别

v-show通过css display控制显示和隐藏，v-if组件真正的渲染和销毁，而不是显示和隐藏，频繁切换状态使用v-show 否则v-if

v-if 常用于一次性改变，如根据权限决定是否显示

v-show 用于 tabs 切换

v-if 可与 templete块连用 ，v-show 不支持 

## V-if v-for 优先级         

v-for和v-if不应该一起使用，必要情况下应该替换成computed属性。原因：v-for比v-if优先，如果每一次都需要遍历整个数组，将会影响速度，尤其是当之需要渲染很小一部分的时候。   

## Vue中v-for 中的 key 设置的值 

快速查找到节点，减少渲染次数，提升渲染性能

## 有了解过key为什么不能使用index

当数据长度发生改变时，原来对应key的绑定关系会发生改变，所以被重新渲染，影响应能

## Vue响应式原理

1.描述监听data变化

监听对象变化：vue2.0核心api是Object.defineProperty，vue3.0是启用proxy实现响应式

监听数组变化：重写数组的push.pop.shift.unshift.splice.sort.reverse方法

## vue的生命周期  

1、beforeCreate():组件实例刚刚被创建 (el 和 data 并未初始化)

2、created():组件创建完成,属性已绑定,但 DOM 还未生成,$el属性还不存在(完成 data 数据的初始化)

3、beforeMount():模板编译/挂载之前(完成了 el 和 data 初始化)

4、Mounted():模板编译/挂载之后(完成挂载)      (接口请求一般放在这里)

5、beforeUpdate():组件更新之前

6、updated()：组件更新之后

7、beforedestroy():组件销毁之前

8、destroyed():组件销毁之后 

另外还有 `keep-alive` 独有的生命周期，分别为 `activated` 和 `deactivated` 。用 `keep-alive` 包裹的组件在切换时不会进行销毁，而是缓存到内存中并执行 `deactivated` 钩子函数，命中缓存渲染后会执行 `activated` 钩子函数。

## Vue 子组件和父组件执行顺序

**加载渲染过程：**

1. 父组件 beforeCreate
2. 父组件 created
3. 父组件 beforeMount
4. 子组件 beforeCreate
5. 子组件 created
6. 子组件 beforeMount
7. 子组件 mounted
8. 父组件 mounted

**更新过程：**

1. 父组件 beforeUpdate
2. 子组件 beforeUpdate
3. 子组件 updated
4. 父组件 updated

**销毁过程：**

1. 父组件 beforeDestroy
2. 子组件 beforeDestroy
3. 子组件 destroyed
4. 父组件 destoryed

## 路由

### 	Vue-Router 的懒加载如何实现

​			方案一(常用)：使用箭头函数+import动态加载

~~~
const List = () => import('@/components/list.vue')
const router = new VueRouter({
  routes: [
    { path: '/list', component: List }
  ]
})
~~~

​			方案二：使用箭头函数+require动态加载

~~~
const router = new Router({
  routes: [
   {
     path: '/list',
     component: resolve => require(['@/components/list'], resolve)
   }
  ]
})
~~~

### 路由模式    Hash和history区别

####   Hash:

Url：有#，不好看

回车刷新：可以加载到hash值对应页面

支持版本：支持低版本浏览器和IE浏览器

#### History：

Url：无#，好看

缺点:  在刷新页面的时候，如果没有相应的路由或资源，就会刷出404来。

​		 history模式需要后台配置支持。如果后台没有正确配置，访问时会返回404

支持版本：HTML5新推出的API



### 如何获取页面的hash变化

（1）监听$route的变化

~~~
// 监听,当路由发生变化的时候执行
watch: {
  $route: {
    handler: function(val, oldVal){
      console.log(val);
    },
    // 深度观察监听
    deep: true
  }
},
~~~

（2）window.location.hash读取#值 window.location.hash 的值可读可写，读取来判断状态是否改变

### $route 和$router 的区别

- $route 是“路由信息对象”，包括 path，params，hash，query，fullPath，matched，name 等路由信息参数
- $router 是“路由实例”对象包括了路由的跳转方法，钩子函数等。

### 路由传参两种形式  params和query

	注意:
	2、path只能和query使用；
	3、使用params传参 刷新后不会保存，使用query刷新后可以保存；
	4、params不会在地址栏显示，query会在地址栏显示；
	5、params能和动态路由一起使用，而query不能

### 如何定义动态路由？如何获取传过来的动态参数？

**（1）param方式**                 参数获取 通过 `$route.params.参数名称` 获取传递的值

- 配置路由格式：`/router/:id`
- 传递的方式：在path后面跟上对应的值
- 传递后形成的路径：`/router/123`
- 优点： params在浏览器地址栏中不显示参数名称

**（2）query方式 **                  通过`$route.query.参数名称`获取传递的值

- 配置路由格式：`/router`，也就是普通配置
- 传递的方式：对象中使用query的key作为传递方式
- 传递后形成的路径：`/route?id=123`
- 缺点： query在浏览器地址栏中显示参数名称

### vue-router 怎么实现的

~~~
vue-router 就是作为'窗口'的存在，来渲染需要展示的组件
vue-router 是通过 vue.use 的方法被注入进 vue 实例中，在使用的时候我们需要全局用到 vue-router 和 router-link 组件，以及 this.$router/$route 这样的实例对象
~~~

### Vue-router 路由钩子在生命周期的体现

最常见的登录权限验证，当用户满足条件时，才让其进入导航，否则就取消跳转，并跳到登录页面让其登录

vue-router全局有三个路由钩子;

- router.beforeEach 全局前置守卫 进入路由之前   （判断是否登录了，没登录就跳转到登录页）
- router.beforeResolve 全局解析守卫（2.5.0+）在 beforeRouteEnter 调用之后调用
- router.afterEach 全局后置钩子 进入路由之后 （跳转之后滚动条回到顶部）

### vue-router有哪些方法

1. router-link标签
2. this.$router.push()
3. this.$router.replace()
4. this.$router.go(n)

###  Vue-router跳转和location.href有什么区别

`location.href= /url `来跳转，简单方便，但是刷新了页面

`history.pushState( /url )` ，无刷新页面，静态跳转；

### vue.use

在用 Vue 使用别人的组件时，会用到 Vue.use()

## vuex 

vuex 可以理解为是一个仓库，它是一个专门为 vue 构建的状态管理工具，主要是为了解决 多组间之间状态共享问题。强调的是集中式管理，（组件与组件之间的关系变成了组件与仓库之间的关系）

vuex的核心: state(存放状态)，mutations（同步的更改状态），actions(发送异步请求,拿到数据), getters（根据之前的状态派发新的状态）, modules（模块划分）   

​	vuex的流程：state发布一条新的数据，在getters里面根据状态派发新的状态，actions发送异步请求获取数据，然后在mutations里面同步更新的数据

​	应用场景: 购物车的数据分享，登录注册

### vuex是如何使用的

我会先创建一个store文件夹，并且在文件夹下面创建一个store.js文件，然后分别引入Vue和Vuex，然后使用Vue.use(Vuex)进行全局配置

再然后将这个store文件引入到入口文件main.js里面去

最后将store挂载到Vue实力当中 

### 如何在页面中获取store中的数据

使用 this.$store.state.你想获取的数据名

### 如何在页面中修改store中的数据

使用 this.$store.commit('mutations的方法名','可带参数')

### vuex中的mutation的调用方法

​	1.直接通过$store.commit调用   //  @clcik='$store.commit('mutations的方法名','可带参数')

​	2.通过在methods中注册方法调用

### **Actions** (发送异步请求,拿到数据)

**Action 类似于 mutation，不同在于：**

- **Action 提交的是 mutation，而不是直接变更状态。**
- **Action 可以包含任意异步操作。**

### **Actions** 中如何修改store的数据

this.$store.dispatch()

### 为什么使用vuex 

vuex可以实现数据响应，而sessionstorage是不可以的，我们使用vuex 的主要目的是为了各个组件之间的传参，通过数据改变视图。而sessionstorage是做不到这一点的

### vuex刷新丢失内容  改怎么解决这个bug

问题：F5页面刷新，页面销毁之前的资源，重新请求，因此写在生命周期里的

原因：因为store里的数据是保存在运行内存中的,当页面刷新时，页面会重新加载vue实例，store里面的数据就会被重新赋值初始化

解决思路1：

将state的数据保存在localstorage、sessionstorage或cookie中，这样即可保证页面刷新数据不丢失且易于读取。

**注意：** 对于不变的数据确实可以用localstorage可以代替vuex，但是当两个组件共用一个数据源（对象或数组）时，如果其中一个组件改变了该数据源，希望另一个组件响应该变化时，localstorage无法做到，原因就是区别1。

解决方法2:

插件vuex-persistedstate

vuex-persistedstate默认持久化所有state，可以指定需要持久化的state



## $set 如何使用

​	当我们直接给一个对象进行赋值操作的时候，虽然可以新增属性，但是不会触发视图层的更新

​	原因：Vue.js 不能检测到对象属性的添加或删除。因为 Vue.js 在初始化实例时将属性转为 getter/setter，所以属性必须在 data 对象上才能让 Vue.js 转换它，才能让它是响应的。

​	解决方案：使用$set()方法，既可以新增属性,又可以触发视图更新。  this.$set(this.data,”key”,value')

## keep-alive

keep-alive缓存vue实例，提高性能是 Vue 内置的一个组件，可以使被包含的组件保留状态，避免重新渲染 ，

提供 include 和 exclude 属性，两者都支持字符串或正则表达式，

include 表示只有名称匹配的组件会被缓存，exclude 表示任何名称匹配的

组件都不会被缓存 ，其中 exclude 的优先级比 include 高；

对应两个钩子函数 activated 和 deactivated ，当组件被激活时，触发钩子函数 activated，当组件被移除时，触发钩子函数 deactivated。



## nextTick是什么，什么时候调用

作用：在下一次 DOM 更新结束后执行其指定的回调。

场景：vue是异步渲染的框架，react也是，data改变之后，dom不会立刻渲染，$nextTick会在dom渲染之后被触发，以获取最新dom节点

## Vue.nextTick()

​		定义：在下次 DOM 更新循环结束之后执行延迟回调。在修改数据之后立即使用这个方法，获取更新后的 DOM。所以就衍生出了这个获取更新后的DOM的Vue方法。所以放在Vue.nextTick()回调函数中的执行的应该是会对DOM进行操作的 js代码；

​		理解：nextTick()，是将回调函数延迟在下一次dom更新数据后调用，**简单的理解是：当数据更新了，在dom中渲染后，自动执行该函数，**

## Vue组件封装过程

● 首先，使用Vue.extend()创建一个组件

● 然后，使用Vue.component()方法注册组件

● 接着，如果子组件需要数据，可以在props中接受定义

● 最后，子组件修改好数据之后，想把数据传递给父组件，可以使用emit()方法



## 创建自定义组件

​	vue-cli中的所有组件都是存放在components文件夹下面的。

​	首先先在components文件夹下面创建一个自定义组件，

​	然后 export 表示导出，在自定义组件里面使用export default导出 

​	

## sass和scss的区别

~~~
	scss是sass的一个升级，他在sass智商又新增了一些功能。语法形式上有些许不同，最主要的就是sass是靠缩进表示嵌套关系，scss是花括号
	scss功能很强大的样子，能做运算、写函数啥的，但是我只是作为语法糖用而已，只看了些基础功能
	我个人常用的功能有：
		嵌套
		变量 $color : #111111;
		混入 @mixin
		继承 @extend
~~~



## vue和react的区别

react是通过js来生成html，通过js才操作css，而vue是响应式的，用各自的处理方式，vue有单文件组件，可以把html、js和css写在一个文件中
react做的事情很少，很多都是交给社区去做，vue很多东西都是内置的，写起来方便一些
设计思想不同

## vue初始化页面闪动问题

在vue初始化之前，盒子不归vue管理，所以可能会出现会出现花屏问题  eg:  {{name}}的字样

解决:    

		1. 在css里加入   **[v-cloak] {display:none}**
		1. 如果没有彻底解决   在根元素加上  **style="display: none;" :style="{display: 'block'}"**

​    

## Vue中的优化

**（1）编码阶段**

- 尽量减少data中的数据，data中的数据都会增加getter和setter，会收集对应的watcher
- v-if和v-for不能连用
- 如果需要使用v-for给每项元素绑定事件时使用事件代理
- SPA 页面采用keep-alive缓存组件
- 在更多的情况下，使用v-if替代v-show
- key保证唯一
- 使用路由懒加载、异步组件
- 防抖、节流
- 第三方模块按需导入
- 长列表滚动到可视区域动态加载
- 图片懒加载

**（2）打包优化**

- 压缩代码
- 使用cdn加载第三方模块

## vue项目下载子文件有哪些

![image-20220214220122882](C:\Users\张文博\AppData\Roaming\Typora\typora-user-images\image-20220214220122882.png)

# Vue项目问题

## 登录中权限的设定

#### 两种验证机制

~~~
登录验证方案一： 会话机制
   后端提供的接口采用会话保存用户登陆状态.前端调用登录接口成功时,接口响应头通知浏览器记录会话cookie，在发起受限资源的接口时，浏览器在请求头自带改会话cookie到后端，通过这种方式判断用户是否已经登录。
   会话机制方案,登录状态完全由后端维护。前端只需要在请求相应加入拦截，判断接口响应是否未登录或过期登录，如果是就重定向到登陆页面
   
   
登录验证方案二： Token机制
	登录接口成功时相应token，前端收到token后保存到浏览器本地存储localStorage
访问需要权限的信息是，前端再从本地存储中读取token，携带token参数访问接口（可以在请求拦截全局处理）
前端判断接口响应是否未登录或者是登录过期，如果是，重定向到登陆页面（可在请求相应拦截全局处理）
~~~

#### 路由导航守卫    

~~~
vue-router 提供对应全局前置和后置回调函数，可以加入业务逻辑控制路由跳转或或取消导航。
~~~

#### 请求拦截

~~~
前端框架使用 axios 类库进行http请求，支持全局 对请求发送前（request）与 响应后（response）进行注入拦截逻辑。可对发送数据与响应数据进行适配。

// 请求拦截器 对请求进行预处理 为请求头加上token令牌 有令牌才能放行
 axios.interceptors.request.use(function (config) {
    // 在这里实现对请求前的处理
    //config.headers.Authorization = window.sessionStorage.getItem('token')将token携带到
    return config
  })


 //在axios接收响应数据之前，进行判断是否响应未登录、如果未登录重定向到登录页面
	axios.interceptors.response.use(function (res) {
	 // 在这里实现响应后的处理
	return res
  })
~~~

## 封装一个简单的组件

~~~vue
//对input 文本框进行封装
Vue.component("tc-input", {
    props: ['value', 'label'],
    methods: {
        updateVal: function (val) {
            console.log("子控件组件：" + val);
            this.$emit("input", val);
        },
    },
    template: '<span v-if="label">{{label}}</span><input v-model="value" v-on:input="updateVal($event.target.value)" />'
});

插槽==>
~~~



## 项目中的挑战

#### 解决关键词高亮问题

​		原理和字符串敏感词替换一样，但是用在关键词高亮上算是一个技术亮点吧

~~~
	用户配置一堆关键词，在页面上将这些关键词高亮，也许你会觉得这有什么难度？用正则匹配一下出来高亮不就行了吗？但是，一开始，用户的词不多，我确实使用的是遍历，时间复杂度为n2。后来用户会配置100w量级的词，使用遍历就会使页面卡死崩溃。解决的方法就是：优化性能，高亮分三步，生成字典树，遍历页面文字，取出文字进行匹配。使用字典树代替遍历，整个页面100w量级的词绘制可以实现在1秒以内。
~~~

#### 使用缓存处理

​		 在做Vue开发时，有个页面比较常见，左边是对所有管理品类的展示，右边是对对应菜谱的展示，一开始在开发的时候没注意，就直接在mounted()前面使用async,里面使用await调了两边接口后，又通过watch监听了品类索引变化，调了一遍接口。后面发现每次切换品类时，页面都有一闪而过的感觉，发现每次都调了一遍接口，这对性能消耗挺大。所以就尝试的走了Vuex做缓存处理。当时解决这个缓存问题用了一些巧妙的方法，首先缓存的数据，采用的是对象形式，不是数组。这样写起来更快，因为用品类的下标直接做缓存数据的key值，非常好写。不过后面又有点坑，就是我监听的是引用数据类型，可是在vue中，引用数据类型发生变化时，页面可能不会更新。后面又在mutation中对vuex中的数据更新时，做了一下深复制，就做好了缓存处理。因为我是根据判断这个对象中有没有数据去调接口的，如果存在，就不调接口。现在做了缓存，那如果以后后台的数据发生了变化的话，那我这里也不调接口了，后台数据就没有在页面上实现更新，所以在跳出这个页面的时候还要清下缓存。清缓存要在生命周期结束的时候清，如果碰到了动态组件把页面下的 Tap 栏包住的时候， Keep-alive。就不能用 destroyed 生命周期清除，要用 deactivated 生命周期去清除。这样才有始有终，完成缓存处理。



#### element中的上传组建 upload

问题：我在上传图片的时候，页面显示上传成功并切展示到了页面，但是在控制台Network中发现报错:出现无效的token值，既没有权限。

分析：在上传图片时，<el-upload>在发送请求时，没有使用到axios，所以没有携带token值，而是<el-upload>的内部自己封装了一套ajax，他自带的ajax是没有携带Authorization字段

解决：<el-upload>中有一个header属性用来设置上传的请求头部 

~~~vue
:header='headerObj'
headerObj:{
Authorization: window.sessionStorage.getItem('token')
}
~~~



# React

## react 中的ref是什么

获取dom元素 this.$refs.box

获取子组件中的data this.$refs.box.msg

调用子组件中的方法 this.$refs.box.open()

## react:props和state有什么区别

1.state是组件自身数据的管理对象而props是别的组件传递来的数据的管理对象

2.state是可以修改的，而props是不能修改的

3.state只能在类组件中使用，而props既可以在类组件中使用也可以在函数组件中使用

## react diff 原理（常考，大厂必考）

把树形结构按照层级分解，只比较同级元素。

给列表结构的每个单元添加唯一的 key 属性，方便比较。

React 只会匹配相同 class 的 component（这里面的 class 指的是组件的名字）

合并操作，调用 component 的 setState 方法的时候, React 将其标记为 dirty.到每一个事件循环结束, React 检查所有标记 dirty 的component 重新绘制.

选择性子树渲染。开发人员可以重写 shouldComponentUpdate 提高diff 的性能。

## reacte生命周期

初始化阶段：

getDefaultProps:获取实例的默认属性

getInitialState:获取每个实例的初始化状态

componentWillMount：组件即将被装载、渲染到页面上

render:组件在这里生成虚拟的 DOM 节点

componentDidMount:组件真正在被装载之后

运行中状态：

componentWillReceiveProps:组件将要接收到属性的时候调用

shouldComponentUpdate:组件接受到新属性或者新状态的时候（可以返回 false，接收数据后不更新，阻止 render 调

用，后面的函数不会被继续执行了）

componentWillUpdate:组件即将更新不能修改属性和状态

render:组件重新描绘

componentDidUpdate:组件已经更新

销毁阶段：

componentWillUnmount:组件即将销毁

## 路由钩子及应用场景

beforeRouteEnter 使用场景：登录验证

beforeRouteUpdate 使用场景：路由更新的时候

beforeRouteLeave 使用场景：路由离开的时候

## $route和$router的区别

$route用来获取路由信息的，它是路由信息的一个对象，里面包含路由的一些基本信息，包括name、meta、path、hash、query、params、fullPath、matched、redirectedFrom等。而$router主要是用来操作路由的，它是VueRouter的实例，包含了一些路由的跳转方法，钩子函数等

## defer与async的区别是：

defer要等到整个页面在内存中正常渲染结束（DOM结构完全生成，以及其他脚本执行完成），才会执行；
async一旦下载完，渲染引擎就会中断渲染，执行这个脚本以后，再继续渲染
一句话，defer是“渲染完再执行”，async是“下载完就执行”

## 高阶组件

高阶组件是一个以组件为参数并返回一个新组件的函数。HOC运行重用代码、逻辑和引导抽象。最常见的可能是Redux的connect函数。除了简单分享工具库和简单的组合，HOC最好的方式是共享React组件之间的行为。如果你发现你在不同的地方写了大量代码来做同一件事时，就应该考虑将代码重构为可重用的HOC

# 小程序

## 小程序的生命周期：

​    1：小程序注册完成后，加载页面，触发onLoad方法。

​    2：页面载入后触发onShow方法，显示页面。

​    3：首次显示页面，会触发onReady方法，渲染页面元素和样式，一个页面只会调用一次。

​    4：当小程序后台运行或跳转到其他页面（使用wx.navigateTo）时，触发onHide方法。

​    5：当小程序有后台进入到前台运行或重新进入页面时，触发onShow方法。

​    6：当使用重定向方法wx.redirectTo(OBJECT)或关闭当前页返回上一页wx.navigateBack()，触发onUnload

## 小程序和vue有什么不同

1、生命周期：

小程序的钩子函数要简单得多 。 vue的钩子函数在跳转新页面时，钩子函数都会触发，但是小程序的钩子函数，页面不同的跳转方式，触发的钩子并不一样。

在页面加载请求数据时，两者钩子的使用有些类似，vue一般会在created或者mounted中请求数据，而在小程序，会在onLoad或者onShow中请求数据。

2、数据绑定：

vue动态绑定一个变量的值为元素的某个属性的时候，会在变量前面加上冒号：

![img]()"imgSrc"/>

小程序 绑定某个变量的值为元素属性时，会用两个大括号括起来，如果不加括号，为被认为是字符串

![img](</span)"{{imgSrc}}">

3、列表循环

4、显示与隐藏元素

vue中，使用v-if 和v-show控制元素的显示和隐藏

小程序中，使用wx-if和hidden控制元素的显示和隐藏

5、事件处理

vue：使用v-on:event绑定事件，或者使用@event绑定事件

小程序中，全用bindtap(bind+event)，或者catchtap(catch+event)绑定事件

6、数据的双向绑定

在vue中,只需要再表单元素上加上v-model,然后再绑定data中对应的一个值，当表单元素内容发生变化时，data中对应的值也会相应改变 。

当表单内容发生变化时，会触发表单元素上绑定的方法，然后在该方法中，通过this.setData({key:value})来将表单上的值赋值给data中的对应值 。

7、绑定事件传参

在vue中，绑定事件传参挺简单，只需要在触发事件的方法中，把需要传递的数据作为形参传入就可以了

在小程序中，不能直接在绑定事件的方法中传入参数，需要将参数作为属性值，绑定到元素上的data-属性上，然后在方法中，通过e.currentTarget.dataset.*的方式获取

8、父子组件通信

父组件向子组件传递数据，只需要在子组件通过v-bind传入一个值，在子组件中，通过props接收，即可完成数据的传递

父组件向子组件通信和vue类似，但是小程序没有通过v-bind，而是直接将值赋值给一个变量 在子组件properties中，接收传递的值

# webpack

## 知道webpack吗

webpack 是一个现代 JavaScript 应用程序的静态模块打包器(modugle bundler)。

先理解四个核心概念：

· 入口(entry)

· 出口(output)

· loader

· 插件(pluins)        

## webpack 与 grunt,gulp的不同

​		1.三者都是前端构建工具，grunt和gulp在早期比较流行，现在webpack相对来说比较主流，不过一些轻量级的任务还是会用gulp来处理，比如单独打包CSS文件等。

​		2.grunt和gulp是基于任务和流(Task、 Stream) 的。类似jQuery,找到一个(或一 类)文件，对其做一系列链式操作，更新流上的数据，整条链式操作构成了一 个任务，多个任务就构成了整个web的构建流程。
​		3.webpack是基于入口的。webpack会 自动地递归解析入口所需要加载的所有资源文件，然后用不同的Loader来处理不同的文件，用Plugin来扩 展webpack功能。

## webpack类似的工具还有哪些?谈谈你为什么最终选择(或放弃)使用webpack?

同样是基于入口的打包工具还有以下几个主流的:
webpack
rollup
parcel

从应用场景上来看:
webpack适用于大型复杂的前端站点构建
●rollup适用于基础库的打包，如vue、 react
●parcel适用于简单的实验性项目，他可以满足低i门槛的快速看到效果

●由于parce|在打包过程中给出的调试信息十分有限，所以一旦打包出错难以调试，所以不建议复杂的项目使用parcel

## 有哪些常见的Loader?他们是解决什么问题的?

●file-loader: 把文件输出到一个文件夹中，在代码中通过相对URL去引用输出的文件
●furl-loader:和file-loader类似，但是能在文件很小的情况下以base64的方式把文件内容注入到代码中去
●fsource-map-loader:加载额外的Source Map文件，以方便断点调试
●image-loader: 加载并且压缩图片文件
●fbabel-loader:把ES6转换成ES5
●css-loader: 加载CSS,支持模块化、压缩、文件导入等特性
●fstyle-loader:把CSS代码注入到JavaScript中，通过DOM操作去加载CSS。
●eslint-loader: 通过ESLint检查JavaScript代码

## 有哪些常见的Plugin?他们是解决什么问题的?

●html-webpack-plugin:可以复制一个有结构的html文件，并自动引入打包输出的所有资源(S/CSS)
●clean-webpack-plugin:重新打包自动清空dist 目录
●mini-css-extract-plugin:提取js中的CSS成单独文件
●optimize-css-assets-webpack-plugin:压缩CSS
●uglifyjs-webpack-plugin:压缩js
●commons-chunk-plugin:提取公共代码

## Loader和Plugin的不同?

#### 	不同的作用

​		●Loader直译为加载器"。Webpack将一 切文件视为模块，但是webpack原生是只能解析js文件，如果想将其他文件也打包的话，就会用到loader。所以Loader的作用是让webpack拥有 了加载和解析非JavaScript文件的能力。
​		●Plugin直译为"插件"。 Plugin可以扩 展webpack的功能，让webpack具有更多的灵活性。在Webpack运行的生命周期中会广播出许多事件，Plugin 可以监听这些事件，在合适的时机通过Webpack提供的API改变输出结果。

#### 	不同的用法

​		●Loader在module.rules中配置， 也就是说他作为模块的解析规则而存在。 类型为数组，每-项都是一个Object,里面描述了对于什么类型的文件(test) ， 使用什么加载(loader)和使用的参数(options)
​	●Plugin在plugins中单独配置。 类型为数组， 每项是一个plugin的实例， 参数都通过构造函数传入。

## 如何利用webpack来优化前端性能?(提高性能和体验)

~~~
用webpack优化前端性能是指优化webpack的输出结果，让打包的最终结果在浏览器运行快速高效。
~~~

​		●压缩代码。删除多余的代码、注释、简化代码的写法等等方式。可以利用webpack的
UuglifyjsPlugin和ParallelUglifyPlugin来压缩JS文件，利用Sssnano (css-loader?minimize) 来压缩CSS
​		●利用CDN加速。在构建过程中，将引用的静态资源路径修改为CDN上对应的路径。可以利用webpack对于output参数和各loader的publicPath参数来修改资源路径

​		●删除死代码(Tree Shaking) 。将代码中永远不会走到的片段删除掉。可以通过在启动webpack时追加参数--optimize-minimize来实现

​		●提取公共代码。

# 兼容性问题

##  常见兼容问题

~~~
不同浏览器的标签默认的外补丁( margin )和内补丁(padding)不同。在不加样式的情况下，margin 和 padding 差异较大。这是最常见的浏览器兼容性问题，但也是最好解决的一个。

如何解决： css 里增加通配符 * { margin: 0; padding: 0; }
~~~



~~~
块属性标签设置了 float , 同时又设置 margin , 在 IE6 运行中，后面那一块会被顶到下一行。

如何解决：在 float 样式标签中加入 ​display:inline​ 将其转化为行内属性。
~~~



~~~
当标签的高度设置小于 10px，在 IE6、IE7 中会超出自己设置的高度。

如何解决：给超出高度的标签设置 overflow：hidden，或者设定 line-height 的值小于你设置的高度。

~~~



~~~
图片默认有间距。当几个 img 标签放在一起的时候，有的浏览器会有默认间距，即使加了通配符也不起任何作用。

如何解决：使用 float 为 ​img​布局
~~~



~~~
边距重叠问题；当相邻两个元素都设置了 margin 边距时，margin 将取最大值，舍弃最小值；

如何解决：为了不让边重叠，可以给子元素增加一个父级元素，并将父级元素设置为​overflow:hidden​
~~~

# XXX



## 在浏览器中输入url发生了什么？ 

第一步：DNS域名解析。

第二步：建立TCP连接(三次握手)。

​              客户端发送一个带有SYN标志的数据包给服务端，服务端收到后，回传一个带有SYN/ACK标志的数据包以示传达确认信息，最后客户端再回传一个带ACK标志的数据                                         			  包，代表握手结束，连接成功。

第三步：发起HTTP请求。

第四步：接受响应结果。

第五步： 浏览器解析html。

第六步：浏览器布局渲染。

![image-20220217172252313](C:\Users\86153\AppData\Roaming\Typora\typora-user-images\image-20220217172252313.png)





## export与export default的区别

1.export与export default均可用于导出常量、函数、文件、模块等

2.在一个文件或模块中，export、import可以有多个，export default仅有一个

3.通过export方式导出，在导入时要加{ }，export default则不需要

(1) 输出单个值，使用export default
(2) 输出多个值，使用export
(3) export default与普通的export不要同时使用
出现问题：当使用export default {a, b, c, d} 容易造成嵌套多层；

结果：{a: {a, b, c, d}, b:{a, b, c, d}, c:{a, b, c, d}, d:{a, b, c, d}} //error



## 跨域的时机

请求已经发出去了，服务端也接收到并处理了，但是返回的响应结果不是浏览器想要的结果，浏览器将服务端返回的结果拦截掉





## token的流程

![image-20220222180500341](C:\Users\86153\AppData\Roaming\Typora\typora-user-images\image-20220222180500341.png)

## promise原理

## promise状态可逆吗？

不可逆

## promise的方法

#### 1、Promise.resolve()

　返回一个给定值解析后的Promise对象。如果参数本身就是一个`Promise`对象，则直接返回这个`Promise`对象

#### 2、Promise.all（）

​    将多个Promise封装成一个新的Promise，成功时返回的是一个结果数组，失败时，返回的是最先rejected状态的值。

​    使用场景：一次发送多个请求并根据请求顺序获取和使用数据

#### 3、Promise.reject()

　返回一个带有拒绝原因的`Promise`对象。

#### 4、Promise.race()

　　返回一个 promise，一旦迭代器中的某个promise解决或拒绝，返回的 promise就会解决或拒绝。

　　简单来说，就是多个Promise中，哪个状态先变为成功或者失败，就返回哪个Promise的值

## watch怎么去监听一个对象

## 高阶函数

  定义：  把函数作为参数或者返回值的一类函数

## 微任务、宏任务

## vue自定义指令

## 路由模式

## 图片懒加载实现

## 原型、原型链的理解

## 继承了解哪些

## this指向

## es6新特性

## 本地存储

## 支付、分享功能

## 怎么实现移动端适配

var提升为什么undefined

