## JavaScript面试题

### 知识点

#### JS语言特性

运行在客户端浏览器上

弱类型语言，较为灵活

解释性语言，边执行边解释

不用预编译，直接解析执行代码



#### 数据类型&堆栈

##### 数据类型有哪些

JavaScript共有八种数据类型，分别是 Undefined、Null、Boolean、Number、String、Object、Symbol、BigInt。

- Symbol 代表创建后独一无二且不可变的数据类型，它主要是为了解决可能出现的全局变量冲突的问题

- BigInt 是一种数字类型的数据，它可以表示任意精度格式的整数，使用 BigInt 可以安全地存储和操作大整数，即使这个数已经超出了 Number 能够表示的安全整数范围。

数据可以分为原始数据类型和引用数据类型：

- 栈：原始数据类型（Undefined、Null、Boolean、Number、String）
- 堆：引用数据类型（对象、数组和函数）

##### 原始值和引用值的区别

存储位置：

- 原始数据类型直接存储在栈（stack）中的简单数据段，占据空间小、大小固定，属于被频繁使用数据，所以放入栈中存储；
- 引用数据类型存储在堆（heap）中的对象，占据空间大、大小不固定。如果存储在栈中，将会影响程序运行的性能；引用数据类型在栈中存储了指针，该指针指向堆中该实体的起始地址。当解释器寻找引用值时，会首先检索其在栈中的地址，取得地址后从堆中获得实体。

数据结构中：

- 在数据结构中，栈中数据的存取方式为先进后出。
- 堆是一个优先队列，是按优先级来进行排序的，优先级可以按照大小来规定。

在操作系统中，内存被分为栈区和堆区：

- 栈区内存由编译器自动分配释放，存放函数的参数值，局部变量的值等。其操作方式类似于数据结构中的栈。
- 堆区内存一般由开发着分配释放，若开发者不释放，程序结束时可能由垃圾回收机制回收





#### 检测数据类型

##### 1.typeof

```javascript
typeof null           // object
typeof []             // object  
typeof NaN            // number

NaN !==NaN            //true
NaN !=NaN             //true
```

只能检测基本数据类型，其中数组，对象，null都会判断为object



##### 2.instanceof

instanceof 用来判断左边对象是否是右边构造函数的实例对象

​     或者说 左边的对象能否通过  `__proto__`在原型链上找到右边构造函数的原型对象

```javascript
console.log(2 instanceof Number)  //false
console.log(function(){} instanceof Function);       // true
```

只能判断引用数据类型，不能判断基本数据类型

##### 3.constructor

作用 1.判断数据类型 2.对象实例通过constructor 对象访问它的构造函数(Person.prototype.constructor 指向构造函数)

```javascript
console.log((2).constructor === Number); // true
console.log(({}).constructor === Object); // true
```

如果创建一个对象来改变它的原型，就不能用来判断数据类型了



#####  4.Object.prototype.toString.call()

Object.prototype.toString() 返回  [object Object] 加上call()，改变this的指向

能够准确判断数据类型

```javascript
var a = Object.prototype.toString;
 
console.log(a.call(2));     //[object Number]
console.log(a.call(null));  //[object Null]

function fn(){
    console.log('')
}
console.log(a.call(fn))     //[object Function]

```

#### js的内置对象

##### 1.数据对象

###### Number

```javascript
var num =new Number()
var max =Number.MAX_VALUE 
```

属性

MAX_VALUE：最大数字

MIN_VALUE：最小数字

NEGATIVE_INFINITY：表示-Infinity负无穷

POSITIVE_INFINITY：表示Infinity正无穷



###### String

###### Boolean

##### 2.组合对象

Array

Math

Date

##### 3.高级对象

Object

Error

Global

Function

RegExp



#### 字符串

##### 1.声明字符串

1.构造函数形式

var str=new String(参数)

2.字面量形式

var str='aaa'

##### 2.常用方法

###### 1.charAt()

通过下标返回指定位置的字符

###### 2.concat()

连接字符串，返回新字符串

###### 3.replace()

在字符串中替换某些字符

###### 4.split()

通过某个字符分割成数组

###### 4.indexOf()

返回字符在字符串中首次出现的位置，不存在返回-1

###### 6.lastIndexOf()

返回字符在字符串中最后一次出现的位置，不存在返回-1

###### 7.match()

在字符串内检索指定的值或正则，不存在返回null,存在返回  数组

```javascript
var url="name=qwe&id=27"
var reg=/(^|&)id=([^&]*)(&|$)/
console.log( url.match(reg)) //["&id=27","&","27","",index:8,input:"name=qwe&id=27"]
```

###### 8.toLowerCase()

把字符串转小写

```javascript
console.log( str.toLowerCase() )
```

###### 9.toUpperCase()

字符串转大写

###### 10.substring(start,end)

start包含，end不包含   ，只传一个值，从当前开始直到结束

提取字符串中两个指定索引号之间的字符

```javascript
var str="123456789"
console.log( str.substring(0,4) )//1234

console.log( str.substring(4))  //56789
```



###### 11.slice(start,end)

提取字符串的某个部分，并以新的字符串返回被提取的部分

```javascript
var str="123456789"
console.log( str.slice(0,4) )//1234

```

###### 12.substr(start,length)

从start开始提取长度

```javascript
var str="123456789"
console.log( str.slice(0,4) )//1234
```







#### 日期

```javascript
//获取当前日期
let now = new Date()
```



##### 2.获取时间方法

###### getFullYear() 

```javascript
//获取年
let year=now.getFullYear() 
```

###### getMonth()

```javascript
//获取月
let month=now.getMonth()

```

###### getDate()

```javascript
//获取日
let date=now.getDate()
```

###### getHours()

```javascript
//获取小时
let hours=now.getHours()
```

###### getMintes()

```javascript
//获取分钟
let mintes=now.getMintes()
```

###### getSeconds()

```javascript
//获取秒
let seconds=now.getFullYear() 
```

###### 获取时间戳

```javascript
new Date().getTime()
//2
let time=Date.parse(new Date())
//3
let time=(new Date()).valueOf()
//4
let time=Date.now()

```



##### 3.设置时间方法

###### setFullYear()

```javascript
//设置年份

new Date().setFullYear(new Date().getFullYear()+5)  //加5年
```



###### setMonth()

```javascript
//设置月份
new Date().setMonth(new Date().getMonth()+2)
```



###### setDate()

```javascript
//设置天数
new Date().setDate()
```



###### setHours()

```javascript
//设置小时
new Date().setHours()
```



###### setMinutes()

```javascript
//设置分钟
new Date().setMinutes()
```

###### setSeconds()

```javascript
//设置秒
new Date().setSeconds()
```

###### setDay()

```javascript
//设置周(7天)
new Date().setDay()
```



###### setTime()

```javascript
//设置时间戳
new Date().setTime()
```



##### 4.动态获取年月日时分秒

```javascript
 var t=null
        t=setTimeout(time,1000)
        function time(){
            clearTimeout(t)
            dt=new Date()
            var y=dt.getFullYear()
            var mt=dt.getMonth()+1
            var day=dt.getDate()
            var h=dt.getHours()
            var m=dt.getMinutes()
            var s=dt.getSeconds()
            console.log(y);
            document.querySelector('.time').innerHTML='当前时间:'+y+'年'+mt+'月'+day+'-'+h+'时'+m+'分'+s+'秒'
            t=setTimeout(time,1000)
        }
```



#### 数组

##### 常用方法

###### push() 

数组末尾添加数据 ，改变原数组

```javascript
let arr=[1,2,3]
arr.push(4)

console.log(arr)  // [1,2,3,4]


```



###### unshift()

数组首位添加数据，改变原数组

```javascript
let arr=[1,2,3]
arr.unshift(4)

console.log(arr)  // [4，1,2,3]
```



###### pop()

删除数组最后一项，改变原数组

```javascript
let arr=[1,2,3]
arr.pop()

console.log(arr)  // [1,2]
```



###### shift()

删除数组第一项，改变原数组

```javascript
let arr=[1,2,3]
arr.shift()

console.log(arr)  // [2,3]
```



###### join()

用指定分隔符把数组拼接成字符串，不改变原数组

```javascript
let arr=[1,2,3]
let str=arr.join('-')

console.log(str)  // 1-2-3
```



###### concat()

用于连接两个或多个数组，不改变原数组

```javascript
let arr=[1,2]
let arr2=[3,4]
let newArr=arr.concat(arr2)

console.log(newArr)  // [1,2,3,4]
```



###### indexOf(item，start)

检索在数组中第一次出现索引,返回   索引 /-1，不改变原数组

item:查找的数据

start:开始检索的位置

```javascript
let arr=[1,2,3,4]
let index=arr.indexOf(2)

console.log(index)  // 1
```



###### includes()

判断数组是否包含某个字符，返回 true/false ,不改变原数组



```javascript
let arr=[1,2,3,4]
let isTrue=arr.includes(5)

console.log(isTrue)  // false
```



###### slice(start,end) 

查找符合数据，不改变原数组

start:开始查找位置，包括start

end:结束查找的位置，不包括end

只有start，从start开始查找到最后一项

start,end可以为负数，从最后一项算起，-1为最后一项，-2为倒数第二项

```javascript
let arr=[1,2,3,4]
let arr2=arr.slice(1,3) //索引为  1-3，不包括3
console.log(arr2) //[2,3]
console.log(arr.slice(0))  //[1,2,3,4]  原样输出
```



###### splice( index,len,[item])  

对数组进行增删改,改变原数组

index:数组开始下标

len:替换/删除的长度

item:替换的值，删除操作item为空

```javascript
//增加

let arr=['a','b','c']
arr.splice(1,0,'zz') 
console.log(arr)  //['a','zz','b','c']
//删除

let arr=['a','b','c']
arr.splice(1,1)  //删除index为1 长度为1
console.log(arr)  //['a','c']


//修改

let arr=['a','b','c']
arr.splice(1,2,'zz') //zz占两个长度
console.log(arr)  //['a','zz']




```



###### sort()

数组排序  ，改变原数组

默认从小到大排序

```javascript
let arr=[7,9,2,0]
arr.sort((a,b)=>{
    return a-b
})
console.log(arr)  //[0,2,7,9]

arr.sort((a,b)=>{
    return b-a
})
console.log(arr)  //[9,7,2,0]



```



###### reverse() 

 数组翻转，改变原数组

```javascript
let arr=['a','b','c']
let neW=arr.reverse()
console.log(arr) // ['c','b','a']  
```





##### 遍历方法

######  forEach(item,index,ary)  

不改变原数组，无返回值

ary:原数组

```javascript
let arr=['a','b','c']
arr.forEach((item,index)=>{
    console.log(item)  //a->b->c
    console.log(index) //0->1->2
})
```



###### map() 

改变原数组，使用return

```javascript
let arr=['a','b','c']
let res=arr.map(item=>item=='b')
console.log(res) //[false,true,false]
```



###### filter(item,index,self)  

​    self 指原数组

   返回新数组

```javascript
let arr=[1,2,3]
let res=arr.filter(item=>item>=2)
console.log(res) //[2,3]
```



###### find()  

检测符合条件的项

```javascript
let arr=[1,2,3]
let res=arr.find(item=>item>=2)
console.log(res) // 2

let arr=[{id:1,name:'a'},{id:2,name:'b'}]
let res=arr.find(item=>item.id==2)
console.log(res) //{id:2,name:'b'}

```



###### some()

检测只要有一个元素符合条件就返回true,全部不符合返回false

```javascript
let arr=[1,2,3]
let res=arr.some(item=>item>2)
console.log(res) //true

let res=arr.some(item=>item>3)
console.log(res) //false

```



###### every()

判断元素是否全部符合条件，全部符合返回true，否则false

```javascript
let arr=[1,2,3]
let res=arr.every(item=>item>2)
console.log(res) //false

let res=arr.every(item=>item>0)
console.log(res) //true
```



###### reduce()

```javascript

```



###### for...of  

可以直接获取键值

```javascript
let arr = ['a', 'b', 'c'];

for (let a of arr) {
  console.log(a); // a b c 
}



```



###### for...in  

 直接获取键名，不能直接获取键值

```javascript
let arr = ['a', 'b', 'c'];

for (let a in arr) {
  console.log(a); // 0 1 2 
}
```



#### 对象

##### Object 构造函数的方法

- `Object.assign()`

  通过复制一个或多个对象来创建一个新的对象。

- `Object.create()`

  使用指定的原型对象和属性创建一个新对象。

- `Object.defineProperty()`

  给对象添加一个属性并指定该属性的配置。

- `Object.defineProperties()`

  给对象添加多个属性并分别指定它们的配置。

- `Object.entries()`

  返回给定对象自身可枚举属性的 `[key, value]` 数组。

- `Object.freeze()`

  冻结对象：其他代码不能删除或更改任何属性。

- `Object.getOwnPropertyDescriptor()`

  返回对象指定的属性配置。

- `Object.getOwnPropertyNames()`

  返回一个数组，它包含了指定对象所有的可枚举或不可枚举的属性名。

- `Object.getOwnPropertySymbols()`

  返回一个数组，它包含了指定对象自身所有的符号属性。

- `Object.getPrototypeOf()`

  返回指定对象的原型对象。

- `Object.is()`

  比较两个值是否相同。所有 NaN 值都相等（这与==和===不同）。

- `Object.isExtensible()`

  判断对象是否可扩展。

- `Object.isFrozen()`

  判断对象是否已经冻结。

- `Object.isSealed()`

  判断对象是否已经密封。

- `Object.keys()`

  返回一个包含所有给定对象自身可枚举属性名称的数组。

- `Object.preventExtensions()`

  防止对象的任何扩展。

- `Object.seal()`

  防止其他代码删除对象的属性。

- `Object.setPrototypeOf()`

  设置对象的原型（即内部 `[[Prototype]]` 属性）。

- `Object.values()`

  返回给定对象自身可枚举值的数组。

#### 函数

判断是普通函数还是构造函数

```javascript
//在函数内部判断this是否为当前函数的实例来判断当前函数是否作为构造函数

function Fn(){
      if(this instanceof Fn){
         console.log('我是构造函数')
       }else{
           console.log('我是普通函数')
       }
}
Fn()       //我是普通函数
new Fn()   //我是构造函数
```









#### 正则



##### 1.正则符号

？代表0次或一次

*代表0次或多次

+代表至少一次

{m}匹配确定的m次

{m,}匹配至少m次

{m，n}匹配至少m次且最多n次

\s或 \S： 匹配任何空白字符或任何非空白字符

\d或\D:   匹配数字字符或匹配非数字字符

##### 2.正则方法

- test()

  匹配到返回true，否则返回false

  ```javascript
  var reg=/^a/
  var str="abc123"
  reg.test(str)  //true
  ```

  

- exec()

  匹配到返回数组，否则返回null

  ```javascript
  var reg=/^a/
  var str="abc123"
  reg.exec(str)  //['a',index:0,input:'abc123',group:undefined]
  ```

  

- search()

##### 3.常用正则

- 数字价格千分位分割

  ```javascript
  '123456789'.replace(/(?!^)(?=(\d{3})+$)/g, ',') // 123,456,789
  ```

  

- 手机号3-4-4分割

  ```javascript
  let mobile = '18379836654' 
  let mobileReg = /(?=(\d{4})+$)/g 
  
  console.log(mobile.replace(mobileReg, '-')) // 183-7983-6654
  ```

  

- 去除空格法和非空格

  ```javascript
  const trim = (str) => {
    return str.replace(/^\s*|\s*$/g, '')    
  }
  
  const trim = (str) => {
    return str.replace(/^\s*(.*?)\s*$/g, '$1')    
  }
  ```

- 手机号

  ```javascript
   /(^[1][3,5,6,7,8,9][0-9]{9}$)|^(999|666|888|11111)$/
  ```

- 邮编

  ```javascript
  /^[0-9]{6}$/
  ```

- 姓名( 中文,英文和空格)

  ```javascript
  /^[\u4e00-\u9fa5A-Za-z\s]*$/
  ```

  

- email地址

  ```javascript
  
  var str = "111@qq.com";
  var reg = /^\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*$/g;
   
  console.log(reg.test(str));
  ```

  

- url

  ```javascript
  
  var str = "http://www.baidu.com";
  var reg = /^((ht|f)tps?):\/\/[\w\-]+(\.[\w\-]+)+([\w\-\.,@?^=%&:\/~\+#]*[\w\-\@?^=%&\/~\+#])?$/g;
   
   
  console.log(reg.test(str));
  ```

- 年-月-日

  ```javascript
  /^(d{2}|d{4})-((0([1-9]{1}))|(1[1|2]))-(([0-2]([1-9]{1}))|(3[0|1]))$/
  ```

  

- 月/日/年

  ```javascript
  /^((0([1-9]{1}))|(1[1|2]))/(([0-2]([1-9]{1}))|(3[0|1]))/(d{2}|d{4})$/
  ```

  

#### js强制类型转换

null —>boolean   false

null —>number      0



undefined —>number   NaN

undefined —>boolean   false



NaN—>boolean   false

NaN—>number    NaN



##### 显示强制类型转换

###### 1.转字符串

​	String()

```javascript
String(null)  //'null'
```

​	toString()

```javascript
//null,undefined 不能使用会报错
true.toString()  //'true'
```

###### 2.转数字

   Number()

```javascript
Number('123')  //123
```

   parseInt() 转整数

```javascript
parseInt('123px')  //123
```

   parseFloat()转浮点数

```javascript
parseFloat('12.34.56')  //12.34
```

###### 3.转布尔

   Boolean()

```javascript
Boolean(-123) //true
```



##### 隐式强制类型转换

######    1.一元运算符 +

```javascript
1+true //2
```

######   2.一元运算符  - * %

```javascript
10 - '2'  // 8
10 * '2'  // 20

```

######   3.逻辑运算符 && || ！

```javascript
1 && true  // true
1 || true  // 1
! 1        // false

!! 会直接把非布尔转为布尔类型
```

######   4.条件判断 if

```javascript
if(null){
    console.log(1)
}
```

######   5.比较运算符  ==   >  <



#### js中的假值

  undefined 、null 、false 、 0 (+0、-0)  、NaN 、 ""

假值的布尔强制类型转换结果为 false



#### 0.1+0.2 !==0.3 ?

计算机是采用二进制方式存储数据的,0.1的二进制是`0.0001100110011001100...`,，0.2的二进制是：`0.00110011001100...`,两个二进制相加等于0.30000000000000004，所以不等于0.3

可以使用toFixed(num) 来四舍五入 转换为0.4



#### null和undefined区别

null 关键字，代表空对象，主要用于赋值给一些可能会返回对象的变量，作为初始化

undefined  不是关键字，代表未定义,



```javascript
== 为true,=== 为false

null ==  undefined   //true
null === undefined   //false
```



#### typeof null 的结果

在 JavaScript 第一个版本中，所有值都存储在 32 位的单元中，每个单元包含一个小的 **类型标签(1-3 bits)** 以及当前要存储值的真实数据。类型标签存储在每个单元的低位中，共有五种数据类型：

```javascript
000: object   - 当前存储的数据指向一个对象。
  1: int      - 当前存储的数据是一个 31 位的有符号整数。
010: double   - 当前存储的数据指向一个双精度的浮点数。
100: string   - 当前存储的数据指向一个字符串。
110: boolean  - 当前存储的数据是布尔值。
```

如果最低位是 1，则类型标签标志位的长度只有一位；如果最低位是 0，则类型标签标志位的长度占三位，为存储其他四种数据类型提供了额外两个 bit 的长度

有两种特殊数据类型：

- undefined的值是 (-2)30(一个超出整数范围的数字)；
- null 的值是机器码 NULL 指针(null 指针的值全是 0)

那也就是说null的类型标签也是000，和Object的类型标签一样，所以会被判定为Object



#### isNaN 和 Number.isNaN 区别

   isNaN 不是数字

- isNaN 会进行Number类型转换 ，能转成number 返回false,否则 true

-  Number.isNaN 不会转换，只有NaN才为true,否则都是false

  ```javascript
  isNaN(12)           //false
  Number.isNaN(NaN)   //true
  ```

  





#### 构造函数，原型

##### 实现继承的方式

###### 1.原型链继承

核心：创建父类实体对象作为子类原型

优点：可以复用父类方法或属性

缺点：1.子实例不能传父类构造函数传参

​           2.实例1里(对象，数组)修改会影响实例2



```javascript
function Person(){
	this.name='MC'
    this.list=['苹果']
    this.sleep=function(){
		console.log('睡觉')
    }
}
Person.prototype.eat=function(){
	console.log('吃饭')
}

function Student(){}
//关键 ：把Student的原型指向Person的实例对象
Student.prototype=new Person()

//实例1

var s1=new Student()
s1.name='DK' 
console.log(s1.name)  //DK   
s1.eat()   // 吃饭
s1.sleep() // 睡觉
s1.list.push('香蕉')
console.log(s1.list)  //['苹果','香蕉']



//实例2
var s2=new Student()
console.log(s2.name)  //MC   原始类型name   s1修改，s2不共享
s2.eat()   // 吃饭
s2.sleep() // 睡觉
console.log(s2.list)  //['苹果','香蕉'],引用数据类型list  s1修改,s2共享



```



###### 2.构造函数继承

核心：在子构造函数中调用父构造函数(修改父类构造函数的this为子类的this)

优点：父类的方法不会被子类共享，不会互相影响

缺点：子类无法访问父类原型中的方法和属性



```javascript
//可以继承
function Person(name){
    this.name=name
    this.sleep=function(){
        alert('睡觉')
    }
}

//原型里的eat无法继承
Person.prototype.eat=function(){
    alert('吃饭')
}

function Student(age){
    Person.call(this) //使Person的this指向Student
}

var s1=new Student(18)
alert(s1.name) //alert 18x
s1.sleep()  // alert 睡觉
s1.eat()    //报错 s1.eat is not a function

```



###### 3.构造函数+原型链组合继承

核心：使用原型链实现对原型属性和方法的继承，通过构造函数实现对实例属性的继承

缺点：调用两次父类构造函数，会有两份一样的属性和方法，影响性能



```javascript
function Person(name){
    this.name=name
    this.sleep=function(){
        alert('睡觉')
    }
    
}
Person.prototype.eat=function(){
    alert('吃饭')
}

// 构造函数继承
function Student(age){
    Person.call(this)
}
// 原型链继承 
Student.prototype=new Person('张三')

var s1=new Student(18)
s1.sleep()  //alert 睡觉
s1.eat()    //alert 吃饭

```



###### 4.寄生组合式继承(最优)

核心：在组合继承的基础上，解决了父类构造函数调用两次的问题

优点：解决了组合继承中的构造函数调用两次，构造函数引用类型共享，以及原型对象上存在多余属性的问题



```javascript
function Person(name){
    this.name=name
}
Person.prototype.eat=function(){
    alert('吃饭')
}
function Student(){
    Person.call(this)
}
//Fn 作为中转
const Fn =function(){}
Fn.prototype=Person.prototype

Student.prototype=new Fn()
var s1=new Student()
s1.eat()
```



###### 5.class类继承

```javascript
class Person {
    constructor(){
        this.name='ky'
        this.list=['苹果']
    }
}
```





#### 原型、原型链

![image-20220721052342078](C:\Users\g5988\AppData\Roaming\Typora\typora-user-images\image-20220721052342078.png)

```javascript

//  __proto__   实例对象的__.proto__ 指向   Person.prototype
// constructor  Person.prototype 的 constructor 指向构造函数
// instanceof   左边的对象是否是右边构造函数的实例对象 

class Person {
  
}
Person.prototype.name="dy"
Person.prototype.obj={
    age:18
}
Person.prototype.getName=()=>{
    return 'sy'
}

var p1 = new Person()
console.log(p1.__proto__ )                        // {name:'dy',getName:()=>{return 'sy'}}
console.log(p1.__proto__.getName() )              //  sy
console.log(p1.__proto__.obj.age )                //  18
console.log(Person.prototype.constructor)         // class Person {}
console.log(Person.prototype.__proto__)           //  {constructor:{...}}   等同于 Object.prototype
console.log(Person.prototype.__proto__.__proto__)    // null
console.log(p1 instanceof Person)                    // true


```





1.原型：在JavaScript中，每当定义一个普通函数或类时，都会天生自带一个prototype属性，这个属性指向函数的原型对象，并且这个属性是一个对象数据类型的值

2.原型链：每一个对象数据类型(普通的对象、实例、`prototype`......)也天生自带一个属性`__proto__`，属性值是当前实例所属类的原型(`prototype`)。原型对象中有一个属性`constructor`, 它指向函数对象

```javascript
function Person(name,age){
    this.name=name  //this指向实例对象person1
    this.age=age
    this.say:function(){
        alert(this.name)
    }
}

let person1=new Person('wang',18)
person1.contructor==Person  //true
```





#### js的包装类型？

 在 JavaScript 中，基本类型是没有属性和方法的，但是为了便于操作基本类型的值，JavaScript 底层使用 Object 构造函数“包装”，具有对象特征 如 str.length，str.toUpperCase()







#### js执行上下文理解

##### 1.执行上下文是什么

执行上下文就是当前JavaScript代码被解析和执行时存在的环境

##### 2.执行上下文的类型

- 全局执行上下文

  ​    1.不在函数内部的代码都位于全局执行上下文  

  ​    2.创建全局对象，window对象

  ​    3.使this指向这个全局对象

  ​    4.只有一个全局执行上下文

- 函数执行上下文：当函数被调用的时候会创建一个新的执行上下文,可以有无数个

- Eval函数执行上下文：运行eval函数中的代码时创建的执行上下文，少用且不建议使用

##### 3.执行上下文栈

在执行上下文创建好后，JavaScript引擎会将执行上下文压入到栈中，通常把这种用来管理执行上下文的栈称为执行上下文栈，又称调用栈

##### 4.执行上下文的生命周期：创建 -> 执行 -> 回收

######     1.创建阶段

- 创建变量对象：首先会初始化函数的参数arguments,提升函数声明和变量声明

- 创建作用域链：在执行上下文创建阶段，作用域链是在变量对象之后创建的，作用域链是在变量对象之后创建的，作用域链本身包含变量对象。作用域链用来解析变量

-  确定this的值

     1.在全局执行上下文时，this总是指向全局对象

     2.函数执行上下文中，this值取决于函数调用方式，被对象调用则指向对象，否则一般指向全局对象windows或undefined

   变量提升的主要原因：--创建阶段时var生命的变量赋值undefined值

 创建阶段对于var、let、const的赋值状态： let和const定义变量在创建阶段没有被赋值，var生命的变量在从创建阶段被赋值undefined。 

 原因：在创建阶段，代码处扫描变量和函数声明，然后将函数声明存储在环境中，单变量会被初始化成undefined（var声明时）和保持初始状态（let、const声明时）     

######     2. 执行阶段

- 执行变量赋值

- 代码执行

######     3. 回收阶段

- 执行上下文出栈

-  等待虚拟机回收上下文



#### this&箭头函数

##### this的指向



###### 1普通函数中，

​      this指向全局对象window

###### 2.作为对象的方法调用

​       this指向调用这个函数的对象

###### 3.作为事件的处理函数时，

​       this指向触发事件的元素

###### 4.构造函数中

​       this指向new出来的新对象

###### 5.定时器中

​       this指向window

###### 6.箭头函数中

​       this指向父级中的this

###### 7.严格模式中

​       this指向undefined

##### 改变this指向

###### 1.call 方法

语法：函数名.call(调用者, 参数1, …)
作用：函数被借用时，会立即执行，并且函数体内的this会指向借用者或调用者

```javascript
function fn(name, age) {
    this.name = name;
    this.age = age;
    console.log(this)
}
fn()  // this  => window
const obj = {}
fn.call(obj, '李四', 100)  //this => obj


```



###### 2.**apply方法**

语法：函数名.apply(调用者, [参数, …])
作用：函数被借用时，会立即执行，并且函数体内的this会指向借用者或调用者

```javascript
function fn(name, age) {
    this.name = name;
    this.age = age;
}
const obj = {}

fn.apply(obj, ['李四', 100])

```



###### 3.bind方法

语法：函数名.bind(调用者, 参数, …)
作用：函数被借用时，不会立即执行，而是返回一个新的函数。需要自己手动调用新的函数来改变this指向

```javascript
function fn(name, age) {
    this.name = name;
    this.age = age;
}
const obj = {}
fn.bind(obj, '李四', 100)()
```



###### 4.总结：

相同点： 三者都可以把一个函数应用到其他对象身上，注意不是自身对象
不同点：
      call，apply是直接执行函数调用。bind是绑定，执行需要再次调用
      call，bind接收逗号分隔的无限个参数列表；apply接收数组作为参数



##### 箭头函数

###### 1.箭头函数与普通函数

**（1）箭头函数比普通函数更加简洁**

- 如果没有参数，就直接写一个空括号即可
- 如果只有一个参数，可以省去参数的括号
- 如果有多个参数，用逗号分割
- 如果函数体的返回值只有一句，可以省略大括号
- 如果函数体不需要返回值，且只有一句话，可以给这个语句前面加一个void关键字。最常见的就是调用一个函数：

**（2）箭头函数没有自己的this**

箭头函数不会创建自己的this， 所以它没有自己的this，它只会在自己作用域的上一层继承this。所以箭头函数中this的指向在它在定义时已经确定了，之后不会改变。

**（3）箭头函数继承来的this指向永远不会改变**

**（4）call()、apply()、bind()等方法不能改变箭头函数中this的指向**

**（5）箭头函数不能作为构造函数使用**

构造函数在new的步骤在上面已经说过了，实际上第二步就是将函数中的this指向该对象。 但是由于箭头函数时没有自己的this的，且this指向外层的执行环境，且不能改变指向，所以不能当做构造函数使用。

**（6）箭头函数没有自己的arguments**

箭头函数没有自己的arguments对象。在箭头函数中访问arguments实际上获得的是它外层函数的arguments值。

**（7）箭头函数没有prototype**

**（8）箭头函数不能用作Generator函数，不能使用yeild关键字**



######  2.箭头函数的**this**指向

箭头函数并没有属于⾃⼰的this，它所谓的this是捕获其所在上下⽂的 this 值，作为⾃⼰的 this 值，并且由于没有属于⾃⼰的this，所以是不会被new调⽤的，这个所谓的this也不会被改变。



###### 3.new一个箭头函数的会怎样

箭头函数没有prototype，也没有自己的this指向，更不可以使用arguments参数，所以不能New一个箭头函数

###### 4.new操作符实现原理

1. 创建一个新的对象obj
2. 将对象与构建函数通过原型链连接起来
3. 将构建函数中的this绑定到新建的对象obj上
4. 根据构建函数返回类型作判断，如果是原始值则被忽略，如果是返回对象，需要正常处理

上面的第二、三步，箭头函数都是没有办法执行的





#### 异步编程

##### --对异步编程的理解

##### 怎么实现异步编程

###### 1.回调函数

解决了同步的问题，但回调地狱，每个任务只能指定一个回调函数,不能 return

###### 2.事件监听

###### 3.Promise

###### 4.Generator

######  5.async/await











#### --js的==和===区别

#### 浅拷贝和深拷贝

##### 浅拷贝定义

不会拷贝对象的继承属性；不会拷贝对象的不可枚举的属性；可以拷贝 Symbol 类型的属性

浅拷贝只复制某个对象的引用，而不复制对象本身，新旧对象还是共享同一个内存

-  对象属性是基本数据，对拷贝数据修改不会影响原对象数据
- 对象属性是引用数据，复制的是内存中的地址，对拷贝之后的数据修改，会影响到原对象数据



##### 浅拷贝方式

###### 1.Object.assign(目标对象，[来源对象1,来源对象2])

```javascript
let obj1 = { name: '张三', action: { say: 'hi'};
let obj2 = Object.assign({}, obj1);
obj2.name = '李四';  //基本数据类型不会影响原对象obj1
obj2.action.say = 'hello'  //引用数据类型会影响原对象obj1
console.log('obj1',obj1) // { name: '张三', action: { say: 'hello'}
console.log('obj2',obj2) // { name: '李四', action: { say: 'hello'}
```

###### 2....运算符

```javascript
//修改obj

let obj1={
    name:'df'  
}
let obj2={...obj1}
obj2.name="zb"
console.log(obj1.name)  //{name:'df'}
console.log(obj2.name) //{name:'zb'}



//修改source

let source={
    name:'df'
}
let obj={...source}
source.name="zb"
console.log(obj)  //{name:"df"}
console.log(source) //{name:"zb"}

```

###### 3.Array.prototype.concat

```javascript
const arr = [1, 2, {name: 'aa'}];
const newArr = arr.concat();
newArr[2].name = 'wy';
console.log(arr);     //[1,2,{name:'wy'}]
console.log(newArr);  //[1,2,{name:'wy'}]
```

###### 4.Array.prototype.slice

```javascript
const arr = [1, 2, {name: 'nordon'}];
const newArr = arr.slice();
newArr[2].name = 'wy';
```

##### 深拷贝定义

深拷贝会创造一个一样的对象，新对象和原对象不共享内存，对拷贝之后的数据进行修改不会影响到原数据

##### 深拷贝方式

###### 1.递归

不足：

- 时间和空间消耗比较大
- 栈溢出：每个进程的栈容量是有限的，由于递归需要系统堆栈，所以空间消耗要比非递归代码要大很多

```javascript
//定义函数，将要拷贝的数据 obj 以参数的形式传参
//声明一个变量 储存拷贝内容
//判断obj存在且是Object类型
//遍历obj
//判断obj是否存在key,再判断obj的key是否是Object类型，是Object递归复制，否则直接复制
//最后return 变量


function deepClone(obj){
    let objClone = Array.isArray(obj)?[]:{};  //创建新的数组或对象
    if(obj && typeof obj==="object"){
        for(key in obj){
            if(obj.hasOwnProperty(key)){
                //判断obj子元素是否为对象，如果是，递归复制
                if(obj[key]&&typeof obj[key] ==="object"){
                    objClone[key] = deepClone(obj[key]);
                }else{
                    //如果不是，简单复制
                    objClone[key] = obj[key];
                }
            }
        }
    }
    return objClone;
}    

//深拷贝数组
let a=[1,2,[3,4]]
let b=deepClone(a);
b[2]=[0,0];
console.log(a);  //[1,2,[3,4]]
console.log(b)   //[1,2,[0,0]]

//深拷贝对象
let obj={
    b:{
        c:1
    }
}
let obj2=deepClone(obj);
obj2.b.c=2
console.log(obj)  // {b:{c:1}}
console.log(obj2) // {b:{c:2}}



```

###### 2.JSON.parse(JSON.stringify())

不足： 

- 如果对象有函数，函数无法被拷贝下来
- 无法拷贝对象原型链上的属性和方法

```javascript
var obj = {
  a: {
    c: 2,
    d: [9, 8, 7]
  },
  b: 4
}
var jsontext = JSON.stringify(obj)
var obj1 =JSON.parse(jsontext) 
console.log(obj);
console.log(obj1);

obj.a.d[0] = 666

console.log(obj);
console.log(obj1);
```



#### --js怎么实现继承

#### 去重

###### 1.for+indexOf 

   把第一次出现的数据push到新数组

```javascript
const arr = [1, 2, 1, 2, 3, 5, 4, 5, 3, 4, 4, 4, 4];
const arr2 = [];
for(let i=0;i<arr.length;i++){
   if(arr.indexOf(arr[i])==i){
      arr2.push(arr[i])
   }
}
console.log(arr2)  //[1,2,3,5,4]
```

###### 2.filter高阶函数去重

```javascript
const arr = [1, 2, 1, 2, 3, 5, 4, 5, 3, 4, 4, 4, 4];
const arr2= arr.filter((item,index)=>{
   return arr.indexOf(item)===index
})
console.log(arr2)  //[1,2,3,5,4]
```

###### 3. new Set去重

```javascript
const arr = [1, 2, 1, 2, 3, 5, 4, 5, 3, 4, 4, 4, 4];
const arr2=[...new Set(arr)]
console.log(arr2)
```

###### 4.双重for循环 +splice[1]

```javascript
const arr = [1, 2, 1, 2, 3, 5, 4, 5, 3, 4, 4, 4, 4];
for(let i=0;i<arr.length;i++) {
    for (let j=0; j<i; j++) {
            if (arr[i] == arr[j]) {
                arr.splice(i, 1);
                 i--
        }
     }
  }
console.log(arr)
```

###### 5.双重for循环+splice[2]

```javascript
const arr = [1, 2, 1, 2, 3, 5, 4, 5, 3, 4, 4, 4, 4];
for(let i=0;i<arr.length;i++) {
    for (let j=i+1; j<arr.length; j++) {
            if (arr[i] == arr[j]) {
                arr.splice(j, 1);
                 j--
        }
     }
  }
console.log(arr)
```

###### 6.reduce()去重

```javascript
const arr = [1, 2, 1, 2, 3, 5, 4, 5, 3, 4, 4, 4, 4];
const arr2= arr.reduce((pre, cur) => {
    return pre.includes(cur) ? pre : pre.concat(cur);
}, []);
console.log(arr2)
```





#### 高阶函数

##### 1.定义：

​     是对其他函数操作的函数，他接收函数作为参数或将函数作为返回值输出

##### 2.使用

```javascript
1.
const array = [1, 2, 7, 4, 5]
function forEach (array, fn) {
    for (let index = 0; index < array.length; index++) {
        fn(array[index])
    }
}

forEach(array, function (item) {
    console.log(item)
})

2.
function add(a){
 function s(b){
    a =   a+b;
    return s;
 }
 s.toString = function(){return a;}
 return s;
}
console.log(add(1)(2)(3)(4));  //10



```

##### 3.数组高阶函数

###### 1.map()

```javascript
let num =[1,2,3]
let obj={val:5};
let newNum=num.map(function(item,index,array){
    return item+index+array[index]+this.val;
},obj)
console.log(newNum)   //[7,10,13]
```

###### 2.reduce()

###### 3.filter()

```javascript
let arr =[1,2,3]
let arr2=arr.filter((item)=>item%2)
console.log(arr2)   //[7,10,13]
```



#### 数组扁平化并去重排序

###### 1

```javascript
var arr=[ [1, 2, 2], [3, 4, 5, 5], [6, 7, 8, 9, [11, 12, [12, 13, [14] ] ] ], 10];
Array.from(new Set(arr.flat(Infinity))).sort((a,b)=>{ return a-b}) 

//[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]
```

###### 2

```javascript
var arr=[ [1, 2, 2], [3, 4, 5, 5], [6, 7, 8, 9, [11, 12, [12, 13, [14] ] ] ], 10];
function flatten(arr) {
    while (arr.some(item => Array.isArray(item))) {
        arr = [].concat(...arr);
    }
    return arr;
}
Array.from(new Set(flatten(arr))).sort((a, b) => {
 return a - b
})

// [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]
```

###### 3

```javascript
var arr=[ [1, 2, 2], [3, 4, 5, 5], [6, 7, 8, 9, [11, 12, [12, 13, [14] ] ] ], 10];
Array.from(new Set(arr.toString().split(',').map((v)=>{return parseInt(v,10)}))).sort((a,b)=>{ return a-b})

// [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]
```



#### 数组合并方法

##### concat()

```javascript
var arr = [1,2,3]
var arr2 =[3,4,5]
console.log(arr.concat(arr2))  // [1,2,3,3,4,5]
```



##### for+push()

```javascript
for(let i in arr2) {
    arr.push(arr2[i])
}
console.log(arr);  // [1,2,3,3,4,5]
```



##### ...运算符



```javascript
console.log([...arr,...arr2])
```



#### 对象合并方法

##### object.assign()

```javascript
let obj = {a:1}
let obj2 = {b: 2}

const newObj = Object.assign({}, obj1, obj2);
```



##### ...运算符

```javascript
var obj={a:1}
var obj2={b:2}
console.log({...obj,...obj2})
```



#### --回调函数

被作为参数传递到另一个函数的那个函数就叫做 回调函数(callback)

特点

不会立即执行

#### 闭包

##### 什么是闭包

一个内层函数可以访问外层函数中变量的函数称为闭包

##### --闭包的应用场景

##### --闭包怎么形成的

##### 闭包解决了什么问题

避免全局变量的污染；避免命名冲突；解决循环绑定引发的索引问题；可以使函数内的变量不被垃圾回收机制回收

##### 闭包会导致什么问题

因为当一段内存在内存空间一直存在，不被销毁，就会出现内存占用，当占用过多时，导致内存溢出，结果就容易造成内存泄漏。

##### 怎么解决内存泄漏

闭包不在使用时，要及时释放，将引用内层函数对象的变量赋值为null

##### 对内存泄漏的了解

###### 定义

程序中已在堆中分配的内存，因为某种原因未释放或无法释放的问题

###### 生命周期

分配期：js中自动分配所需要的内存

使用期：使用分配的内存(变量的操作)

释放期：程序运行完毕，未能释放的内存会导致内存泄漏



###### 出现内存泄漏的原因

1.意外全局变量

2.闭包

3.定时器

###### 避免内存泄漏

1.全局变量先声明后使用

2.避免过多使用闭包

3.清除定时器和时间监听



#### 事件捕获、冒泡

##### 三个阶段

1.捕获阶段

​          事件从文档的根节点流向目标对象节点，自上而下的去触发事件

2.目标阶段

​       在目标节点上触发

3.冒泡阶段

​       从目标节点流向根节点，自下而上的去触发事件



##### 事件监听

addEventListener(1,2,3)

​      1.监听事件名，click,dbclick,不需要加on

​      2.事件处理函数

​      3.boolean  false:冒泡阶段  true:捕获阶段  默认false

##### 移除事件监听

removeEventListener(1,2,3)

​      1.事件名

​      2.具名函数

​      3.绑定时的boolean

```javascript
 a.removeEventListener("click",function(ev){
     console.log("小明");
 },false);
```



##### 阻止事件冒泡

​      event.stopPropagation();

​      event.cancelBubble=true

```javascript
 a.addEventListener("click",function(ev){
    var event==e||window.event
     event.stopPropagation()
     event.cancelBubble=true    //支持IE
 },false);

```

##### 阻止默认行为

1.e.preventDefault()

2.e.returnValue=false  （IE）

3.return false （函数末尾）



#### 事件委托

##### 定义

把原本需要绑定在子元素上的事件委托给父元素，让父元素担当事件监听的职务，事件委托的原理是DOM元素的事件冒泡

##### 优点

1.可以大量节省内存占用，减少事件注册，比如在ul上代理所有li的click事件

2.可以实现当新增子元素时无需再次绑定

##### 实现

```javascript
//实现功能是划过变色
<ul class="list">
    <li>第一条</li>
    <li>第二条</li>	
    <li>第三条</li>
 </ul>

window.onload = function(){
   var list = document.getElementById("list");
   list.onmousemove= function(ev){
        var oEvent = ev || window.event;
　　　　var target = oEvent.target || oEvent.srcElement;
　　　　target.className="light";
    }
   list.onmouseout = function(ev){
        var oEvent = ev || window.event;
　　　　var target = oEvent.target || oEvent.srcElement;
　　　　target.className="";
    }
}
```







#### 怎么使对象属性不可修改

##### 1.Object.defineproperty()

```javascript
var obj={
    a:1,
    b:2
}
Object.defineProperty('obj',c,{
    value:888,
    writable:false,  //为true时可以修改
    configurable:false //为true是可以使用delete...
})
obj.c=999
console.log(obj.c) //888
```

##### 2.Object.preventExtensions()

不能新增对象属性，但可以修改

```javascript
var obj={
    a:1,
    b:2
}
Object.preventExtensions(obj)
obj.c=888
console.log(obj) //{a:1,b:2}
```





#### 宏任务、微任务

- 宏任务 ：HTML解析、鼠标事件、键盘事件、网络请求、执行主线程js代码和定时器
- 微任务 ：promise.then，dom渲染，async，process.nextTick

##### 理解进程和线程

进程：cpu分配的最小单位

现程：cpu最小的调度单位

##### js为什么是单线程

js主要实现浏览器与用户的交互以及dom的操作，如果js是多线程，如果一个线程要删除这个dom,另一个线程要修改这个dom,这是浏览器就没法操作了，为了避免复杂的操作，所以js是单线程的



##### 同步和异步





#### 异步执行

https://zhuanlan.zhihu.com/p/290841111

```javascript
setTimeout(() =>{
    console.log(0) 
 });


 new Promise(resolve => {
     console.log(1);
     setTimeout(() => {
         resolve();
         Promise.resolve().then(() => {
             console.log(2) ;
             setTimeout(() => console.log(3));
         });
     });
     Promise.resolve().then(() =>console.log(4) ) 
 }).then(() => {
     console.log(5) ;
     Promise.resolve() .then( () => console.log(6) )
 });

console.log(7);

//执行顺序
1、7、4、0、5、2、6、3
```



### Dom对象

#### dom创建

1.document.createElement('img') / document.createTextNode('a')   创建元素节点 / 文本节点

2.domA.appendChild(domB)  domA的末尾创建 domB元素

3.parentDom.insertBefore(domA,domB)  在父节点中domA插入domB前

4.dom.cloneNode(deep)   复制节点  deep:true  深复制  deep:false 浅复制



#### dom获取

##### 读取html元素

1.document.getElementById(’id‘)通过ID获取

2.document.getElementByTagName(’div‘)通过标签名获取

3.document.getElementByName()通过name属性获取

4.document.getElementByClassName('class')通过标类名获取，

5.document.querySelector('p')  所有的匹配第一个p

5.document.querySelectorAll('p')  匹配所有p



##### element 属性

1.dom.firstElementChild / dom.lastElementChild 第一个元素节点 /最后一个元素节点

2.dom.nextElementSibling  / dom.previousElementSibling  下一个元素节点 / 上一个元素节点



##### 节点属性

1.dom.parentNode   父节点

2.dom.childNodes / dom.children   所有子节点

3.dom.firstChild / dom.lastChild    第一个子节点 / 最后一个子节点

4.dom.nextSibling /dom.previousSibling   下一个子节点 / 上一个子节点

5.dom.getAttributeNode('class') 获取所有节点属性



##### 节点信息

1.dom.nodeName 节点名称

2.dom.nodeValue 节点的值

3.dom.nodeType  节点类型



##### 节点类型

element 元素节点  / text文本节点 / document文档节点 / attr属性节点 / comments注释节点



#### dom修改

###### 1.修改内容

dom.innerHTML

dom.innerText



#### dom替换

1.parentDom.replaceChild(newDom,oldDom)  在父节点中newDom替换oldDom

#### dom删除

1.dom.remove() 删除dom

2.parentDom.removeChild(dom)  在父节点中删除子节点



#### 属性操作

1.读取属性(4种)

　　　　dom.attributes[下标].value

　　　　dom.attributes['属性名']

　　　　dom.getAttributeNode('属性名').value

　　　　dom.getAttribute("属性名")

2.修改属性(2种)

　　       dom.setAttribute(name, value);//IE8不支持 只能：element.attributes['属性名']=value

　　　　dom.setAttributeNode(attrNode);//属性可以是属性节点

3.移除属性(2种)

　　　　dom.removeAttribute('属性名');

　　　　dom.removeAttributeNode(attrNode);

4.判断元素是否包含属性(2种)　

　　　　dom.hasAttribute('属性名') //true或false

　　　　dom.hasAttributes( );



#### 样式操作

设置样式

​       1.style

​               dom.style.color='red'

​        2.className

​                dom.className='样式名称'

读取样式

​        1.value=dom.style.color

​        2.getComputedStyle('样式名')

​        3.dom.currentStyle.样式名



### Bom对象

#### 定义：

Browser Object Model(浏览器对象模型) 提供了独立于内容与浏览器窗口进行交互的对象

#### 1.window对象 浏览器窗口

##### 属性：

   ie,chorome,fixfox,opera

window.innerHeight 浏览器窗口的内高度(不包括工具条，滚动条)

window.innerWidth 浏览器窗口的内宽度(像素)

   ie8,7,6,5

document.documentElement.clientHeight

document.documentElement.clientWidth

  所有浏览器

document.body.clientHeight

document.body.clientWidth



##### 方法：

- window.open( a，b  )打开新窗口

​         a ：  url打开的页面路径

​         b ： _self(自身窗口)/_blank(新的窗口)

- window.close();关闭当前窗口

- window.move( 100,100) 移动当前窗口

- window.resize(100,100) 调整当前窗口大小

  

#### 2.screen对象 屏幕对象

##### 属性：

获取屏幕信息

screen.width屏幕宽度

screen.height 屏幕高度

screen.availWidth 可用屏幕宽度

screen.availHeight 可用屏幕高度



#### 3.navigator 对象  浏览器信息

##### 属性：

navigator.appName 浏览器名称

navigator.appVersion 浏览器版本

navigator.language 浏览器设置的语言

navigator.platform 操作系统类型

navigator.userAgent 用户信息



#### 4.location对象

##### 属性：

location.protocol   url协议

location.host       主机，包括hostname和port

location.hostname      主机名

location.port       端口号

location.path   包括pathname和search

location.pathname 路径名称

location.search  参数 从’？‘开始的url部分

location.hash   从’#‘开始url部分

location.href   完整的url

##### 方法：

location.assign();   加载新页面，获取新的URL地址

location.reload();  重新加载当前页面

#### 5.history 历史对象

##### 属性：

length 返回浏览器历史列表中url数量

##### 方法：

history.back() ; 历史列表中前一个url

history.forward() ; 历史列表中后一个url

history.go(0 );具体某个url







### 手写



##### 节流防抖

1.防抖定义：在触发n秒后执行回调，n秒内再次触发则重新计时，避免多次点击导致触发多次请求

防抖函数：

```javascript
// 防抖
function debounce(fn, delay = 300) {
  //默认300毫秒
  let timer;
  return function () {
    const args = arguments;
    //还存在计时器，重新计时
    if (timer) {
      clearTimeout(timer);
        timer = null;
    }
      
    // n秒后的回调，设定时器计时  
    timer = setTimeout(() => {
      fn.apply(this, args); // 改变this指向为调用debounce所指的对象
    }, delay);
  };
}

window.addEventListener(
  "scroll",
  debounce(() => {
    console.log(111);
  }, 1000)
);

```

使用场景：**防抖**经常用在我们搜索框输入搜索，点击提交，防止等



2.节流定义：在一段时间内，被触发多次，只执行一次回调函数。节流可以使用在 scroll 函数的事件监听上，通过事件节流来降低事件调用的频率。

节流函数：

```javascript
function throttle(fn, delay) {
  let flag = true;
  return () => {
      
    //定时器在计时flag为true  
    if (!flag) return;
    flag = false;
      
     // 一段时间内执行一次函数flag为true可以执行回调函数
    timer = setTimeout(() => {
      fn();
      flag = true;  
    }, delay);
  };
}

window.addEventListener(
  "scroll",
  throttle(() => {
    console.log(111);
  }, 1000)
);

```

使用场景：节流一般在onresize、mousemove、滚动事件等事件中使用，防止过多的请求造成服务器压力



##### new操作符

```javascript
function myNew(fn, ...args) {
  let obj = Object.create(fn.prototype);
  let res = fn.call(obj, ...args);
  if (res && (typeof res === "object" || typeof res === "function")) {
    return res;
  }
  return obj;
}
//用法如下：
 function Person(name, age) {
   this.name = name;
   this.age = age;
 }
 Person.prototype.say = function() {
   console.log(this.age);
 };
 let p1 = myNew(Person, "lihua", 18);
 console.log(p1.name);
 console.log(p1);
 p1.say();

```





### HTTP

#### 是什么

HTTP(（HyperText Transfer Protocol）即超文本传输协议。是一个简单的请求-响应协议，它通常运行在TCP之上。运行于应用层。明文传输(无加密),它指定了客户端可能发送给服务器什么样的消息以及得到什么样的响应。请求和响应消息的头以ASCII码形式给出；而消息内容则具有一个类似MIME的格式。



#### 主要特点

1.简单快速：客户向服务器请求服务时，只需要传送请求方法和路径。请求方法规定了客户与服务器联系的类型不同。由于http服务器的程序规模小，因而通信速度很快。

2.灵活：http允许传输任意类型的数据对象。正在传输的类型由Content-Type加以标记。

3.无连接：限制每一次连接只处理一个请求。服务器处理完客户的请求，并受到客户的应答后，即断开连接，可以节省传输时间

4.无状态：协议对于事务处理没有记忆能力，如果后续需要处理前面的信息，必须重传，可能导致每次连接传送的数据量增大。

5.支持B/S及C/S模式。

#### HTTP工作原理

HTTP协议定义Web客户端如何从Web服务器请求Web页面，以及服务器如何把Web页面传送给客户端。HTTP协议采用了请求/响应模型。客户端向服务器发送一个请求报文，请求报文包含请求的方法、URL、协议版本、请求头部和请求数据。服务器以一个状态行作为响应，响应的内容包括协议的版本、成功或者错误代码、服务器信息、响应头部和响应数据。

##### HTTP 请求/响应的步骤

1.客户端连接到Web服务器
一个HTTP客户端，通常是浏览器，与Web服务器的HTTP端口（默认为80）建立一个TCP套接字连接。例如，http://www.luffycity.com。

2.发送HTTP请求
通过TCP套接字，客户端向Web服务器发送一个文本的请求报文，一个请求报文由请求行、请求头部、空行和请求数据4部分组成。

3.服务器接受请求并返回HTTP响应
Web服务器解析请求，定位请求资源。服务器将资源复本写到TCP套接字，由客户端读取。一个响应由状态行、响应头部、空行和响应数据4部分组成。

4.释放连接TCP连接
若connection 模式为close，则服务器主动关闭TCP连接，客户端被动关闭连接，释放TCP连接;若connection 模式为keepalive，则该连接会保持一段时间，在该时间内可以继续接收请求;

5.客户端浏览器解析HTML内容
客户端浏览器首先解析状态行，查看表明请求是否成功的状态代码。然后解析每一个响应头，响应头告知以下为若干字节的HTML文档和文档的字符集。客户端浏览器读取响应数据HTML，根据HTML的语法对其进行格式化，并在浏览器窗口中显示。

##### 浏览器地址栏键入URL，按下回车之后流程：

```javascript

1.DNS 解析:浏览器向 DNS 服务器请求解析 URL 中的域名所对应的 IP 地址
2.TCP 连接：TCP 三次握手
3.发送 HTTP 请求
4.服务器处理请求并返回 HTTP 报文
5.浏览器解析渲染页面
6.断开连接：TCP 四次挥手
```

#### HTTP请求

##### HTTP请求方法

get：请求指定的页面信息,并返回实体主体
head：类似于get请求，只不过返回的响应中没有具体的内容，用于获取报头
post：向指定资源提交数据进行处理请求〔例如提交表单或者上传文件)。数据被包含在请求体中。POST请求可能会导致新的资源的建立和或已有资源的修改。

put：从客户端向服务器传送的数据取代指定的文档的内容
delete：请求服务器删除指定的页面。
connect：HTTP/1.1协议中预留给能够将连接改为管道方式的代理服务器

options：允许客户端查看服务器的性能。
trace：回显服务器收到的请求，主要用于测试或诊断

##### HTTP请求消息

分为4个部分

1.请求行：用来说明请求类型，以一个方法符号开头，以空格分开，后面跟着请求的url和协议的版本

2.请求头部：用来说明服务器要使用的附加信息

3.空行：请求头部后面的空行是必须的

4.请求数据：可以是任意类型

##### HTTP请求状态码

#### HTTP响应

分为4个部分：

1.状态行：由http协议版本号，状态码，状态消息组成

2.消息报头：用来说明客户端要使用的一些附加信息

3.空行：消息报头后面的空行是必须的

4.响应正文：服务器返回给客户端的文本信息



##### HTTP响应状态码

1xx消息——请求已被服务器接收，继续处理
2xx成功——请求已成功被服务器接收、理解、并接受
3xx重定向——需要后续操作才能完成这一请求
4xx请求错误——请求含有词法错误或者无法被执行
5xx服务器错误——服务器在处理某个正确请求时发生错误

200：请求成功。

400：客户端请求有语法错误，不能被服务器理解。

401：请求未经授权，这个状态码必须和WWW-Authenticate报头域一起使用。

403：服务器收到请求，但拒绝提供服务。

404：请求资源不存在。

500：服务器发生不可预期的错误。

503：服务器当前不能处理客户端的请求，一段时间后可能恢复正常。

#### HTTP版本

截止到现在，IETF已经发布了5个HTTP协议了，包括HTTP0.9、HTTP1.0、HTTP1.1、HTTP2、HTTP3.

##### HTTP0.9

1991年发布， 没有header，功能非常简单，只支持GET。

##### HTTP1.0

1996年发布，明文传输安全性差，header特别大。它相对0.9有以下增强：

- 增加了header(使用元数据与数据解耦)
- 增加了status code，用于声明请求的结果。
- content-type可以传输其它文件。
- 请求头增加了http/1.0版本号。

缺点：每请求一次资源就新建一次tcp连接

##### HTTP1.1

1997发布，是现在使用最广泛的版本。它相对1.0有以下增强：

- 可以设置keepalive让http重用tcp连接(请求必需串行发送)
- 支持pipeline传输，请求发出后可以继续发送请求
- 增加了HOST头，让服务端知道用户请求的是哪个域名
- 增加了type、language、encoding等header

2014年更新了内容：

- 增加了TLS支持,即https传输
- 支持四种模型：短连接，可重用tcp的长链接，服务端push模型(服务端主动将数据推送到客户端cache中)，websocket模型

缺点：还是文本协议，客户端服务端都需要利用cpu解压缩

##### HTTP2

2015年发布，主要是提升安全性与性能。它相对1.1的增强有：

- 头部压缩(合并同时发出请求的相同部分)
- 二进制分帧传输，更方便头部只传输差异部分
- 流多路复用，同一服务下只需要用一个连接，节省了连接
- 服务器推送，一次客户端请求服务端可以多次响应。
- 可以在一个tcp连接中并发发送请求

缺点：基于tcp传输，会有队头阻塞问题(丢包停止窗口滑动)，tcp会丢包重传。tcp握手延时长，协议僵化问题。

##### HTTP3

2018年发布，基于谷歌的QUIC，底层使用udp代码tcp协议，

这样解决了队头阻塞问题，同样无需握手,性能大大地提升，默认使用tls加密。



#### get和post的区别

缓存：get会缓存，post不缓存

历史记录：get的

数据长度限制：get的url中最大限制2048个字符，post无限制

数据类型限制：get只支持ASCLL字符，post无限制

安全性：get的参数在url中相对post不安全，post相对安全参数不会在浏览器历史中

可见性：



#### put和post的区别

#### options 方法及使用场景











### TCP

https://www.zhihu.com/tardis/sogou/art/267520757

https://blog.csdn.net/weixin_45393094/article/details/104965561?utm_medium=distribute.wap_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-1.wap_blog_relevant_default&spm=1001.2101.3001.4242.2&utm_relevant_index=4

#### 是什么

主要解决数据如何在网络中传输

1、TCP（Transmission Control Protocol，传输控制协议）是一种面向连接的、可靠的、基于字节流的通信协议，数据在传输前要建立连接，传输完毕后还要断开连接。
2、客户端在收发数据前要使用 connect() 函数和服务器建立连接。建立连接的目的是保证IP地址、端口、物理链路等正确无误，为数据的传输开辟通道。
3、TCP建立连接时要传输三个数据包，俗称三次握手（Three-way Handshaking）

①序号：Seq（Sequence Number）序号占32位，用来标识从计算机A发送到计算机B的数据包的序号，计算机发送数据时对此进行标记。
②确认号：Ack（Acknowledge Number）确认号占32位，客户端和服务器端都可以发送，Ack = Seq + 1。
③标志位：每个标志位占用1Bit，共有6个，分别为 URG、ACK、PSH、RST、SYN、FIN，



```javascript
URG：紧急指针（urgent pointer）有效。
ACK：确认序号有效。
PSH：接收方应该尽快将这个报文交给应用层。
RST：重置连接。
SYN：建立一个新连接。
FIN：断开一个连接。
```

#### TCP三次握手

##### 过程

①客户端请求建立连接发送syn包到服务器，并进入SYN_SENT状态，等待服务器确认
②服务端收到syn包，确认客户的SYN，同时也发送一个SYN+ACK包，进入SYN_RECV状态
③客户端收到SYN+ACK包，向服务端发送确认包ACK，发送完毕TCP连接成功，完成三次握手

![image-20220801134750933](C:\Users\g5988\AppData\Roaming\Typora\typora-user-images\image-20220801134750933.png)

小结：三次握手的关键是要确认对方收到了自己的数据包，这个目标就是通过“确认号（Ack）”字段实现的。计算机会记录下自己发送的数据包序号Seq，待收到对方的数据包后，检测“确认号（Ack）”字段，看Ack = Seq + 1是否成立，如果成立说明对方正确收到了自己的数据包

##### 为什么要三次握手

为了防止已失效的连接请求报文段突然又传送到了服务端，因而产生错误

比如：client发出的第一个连接请求报文段并没有丢失，而是在某个网络结点长时间的滞留了，以致延误到连接释放以后的某个时间才到达server。本来这是一个早已失效的报文段，但是server收到此失效的连接请求报文段后，就误认为是client再次发出的一个新的连接请求，于是就向client发出确认报文段，同意建立连接。

假设不采用“三次握手”，那么只要server发出确认，新的连接就建立了，由于client并没有发出建立连接的请求，因此不会理睬server的确认，也不会向server发送数据，但server却以为新的运输连接已经建立，并一直等待client发来数据。所以没有采用“三次握手”，这种情况下server的很多资源就白白浪费掉了。

描述：

```javascript
1、在第一次通信过程中，A向B发送信息之后，B收到信息后可以确认自己的收信能力和A的发信能力没有问题。

2、在第二次通信中，B向A发送信息之后，A可以确认自己的发信能力和B的收信能力没有问题，但是B不知道自己的发信能力到底如何，所以就需要第三次通信。

3、在第三次通信中，A向B发送信息之后，B就可以确认自己的发信能力没有问题。

4、 小结：3次握手完成两个重要的功能，既要双方做好发送数据的准备工作(双方都知道彼此已准备好)，也要允许双方就初始序列号进行协商，这个序列号在握手过程中被发送和确认。
```



#### TCP的四次挥手

建立连接非常重要，它是数据正确传输的前提；断开连接同样重要，让计算机释放不再使用的资源，如果连接不能正常断开，不仅会造成数据传输错误，还会导致套接字不能关闭，持续占用资源，如果并发量高，服务器压力堪忧

##### 过程：

第一次挥手：客户端发送一个FIN报文，用来关闭客户端到服务端的数据传送，客户端进入FIN_WAIT_1状态

第二次挥手：服务端收到FIN后，发送一个ACK给客户端,服务端进入CLOSE_WAIT状态

第三次挥手： 服务端发送一个FIN，用来关闭服务端到客户端的数据传送，服务端进入LAST_ACK状态

第四次挥手：客户端收到FIN后，客户端进入TIME_WAIT状态，发送ACK给服务端，服务端进入CLOSED状态，完成四次握手

```javascript
A：“任务处理完毕，我希望断开连接。”
B：“哦，是吗？请稍等，我准备一下。”
等待片刻后……
B：“我准备好了，可以断开连接了。”
A：“好的，谢谢合作。”
```

![image-20220801135018131](C:\Users\g5988\AppData\Roaming\Typora\typora-user-images\image-20220801135018131.png)



##### 为什么连接的时候是三次握手，关闭的时候却是四次握手？

①因为当Server端收到Client端的SYN连接请求报文后，可以直接发送SYN+ACK报文。其中ACK报文是用来应答的，SYN报文是用来同步的。
②但是关闭连接时，当Server端收到FIN报文时，很可能并不会立即关闭SOCKET，所以只能先回复一个ACK报文，告诉Client端，“你发的FIN报文我收到了”。
③只有等到我Server端所有的报文都发送完了，我才能发送FIN报文，因此不能一起发送。故需要四步握手。

##### TCP的三次握手一定能保证传输可靠吗？不能

1.三次握手比两次更可靠，但也不是完全可靠，而追加更多次握手也不能使连接更可靠了。因此选择了三次握手。

2.世界上不存在完全可靠的通信协议。从通信时间成本空间成本以及可靠度来讲，选择了“三次握手”作为点对点通信的一般规则

#### HTTP与TCP的区别

TCP是传输层协议，主要解决数据如何在网络中传输，而HTTP是应用层协议，主要解决如何包装数据。

TCP/IP和HTTP协议的关系，从本质上来说，二者没有可比性，在传输数据时，可以只使用（传输层）TCP/IP协议，但是那样的话，如果没有应用层，便无法识别数据内容，如果想要使传输的数据有意义，则必须使用到应用层协议，应用层协议有很多，比如HTTP、FTP、TELNET 等，也可以自己定义应用层协议。WEB使用HTTP协议作应用层协议，以封装HTTP 文本信息，然后使用TCP/IP做传输层协议将它发到网络上。

##### 短连接：

客户端和服务端建立连接，发送完数据后立马断开连接。下次要取数据，需要再次建立连接。

短连接的操作步骤是：建立连接——数据传输——关闭连接…建立连接——数据传输——关闭连接

##### 多路复用：

通过单一的HTTP/2连接请求发起多重的请求-响应消息，多个请求stream共享一个TCP连接，实现多留并行而不是依赖建立多个TCP连接。

##### 长连接：

客户端和服务端建立连接后不进行断开，之后客户端再次访问这个服务器上的内容时，继续使用这一条连接通道。

##### Http长连接和TCP长连接的区别

Http长连接 和 TCP长连接的区别在于: TCP 的长连接需要自己去维护一套心跳策略。，而Http只需要在请求头加入keep-alive:true即可实现长连接。



### HTTPS

#### 是什么

以安全为目标的 HTTP 通道，简单讲是 HTTP 的安全版。即 HTTP 下加入 SSL 层，HTTPS 的安全基础是 SSL，因此加密的详细内容就需要 SSL。

#### 与 HTTPS 的区别

1.HTTP 是明文传输，HTTPS 通过 SSLTLS 进行了加密

2.HTTP 的端口号是 80，HTTPS 是 443

3.HTTPS 需要到 CA 申请证书，一般免费证书很少，需要交费

4.HTTPS 的连接很简单，是无状态的；HTTPS 协议是由 SSL+HTTP 协议构建的可进行加密传输、身份认证的网络协议，比 HTTP 协议安全。

#### HTTP 通信有什么问题

1.通信使用明文(不加密)，内容可能被窃听

2.不验证通信方的身份，因此有可能遭遇伪装

3.无法证明报文的完整性，所以可能遭篡改

#### HTTPS 如何解决上述三个问题

##### 1.解决内容可能被窃听的问题——加密

- 对称加密(加密和解密同用一个密钥)
- 非对称加密(公开密钥加密使用一对非对称的密钥)
- 对称加密+非对称加密

##### 2.解决报文可能遭篡改问题——数字签名

- 能确定消息确实是由发送方签名并发出来的，因为别人假冒不了发送方的签名。
- 数字签名能确定消息的完整性,证明数据是否未被篡改过。

##### 3.解决通信方身份可能被伪装的问题——认证

使用由数字证书认证机构(CA，Certificate Authority)和其相关机关颁发的公开密钥证书。

#### 为什么不一直使用 HTTPS

- 因为与纯文本通信相比，加密通信会消耗更多的 CPU 及内存资源。如果每次通信都加密，会消耗相当多的资源，所以只有在包含个人信息等敏感数据时，才利用 HTTPS 加密通信
- 节约购买证书的开销

### Ajax

#### 是什么

全称为“Asynchronous JavaScript and XML”（异步JavaScript和XML），是一种创建交互式网页应用的技术。Ajax是一种在无需重新加载整个网页的情况下，能够更新部分网页的技术。传统的网页(不使用Ajax)如果需要更新内容，需要重载整个网页。

#### 工作原理

Ajax的工作原理相当于在用户和服务器之间加了一个中间层(Ajax引擎)，使用户操作与服务器响应异步化。并不是所有用户请求都提交服务器。像一些数据验证和数据处理等都交给Ajax引擎自己来做，只有确定需要从服务器读取新数据时再由Ajax引擎代为向服务器提交请求。

#### 执行流程

- 创建XMLHttpRequest对象,也就是创建一个异步调用对象

- 创建一个新的HTTP请求,并指定该HTTP请求的方法、URL及验证信息

- 设置响应HTTP请求状态变化的函数(打开链接open())

- 发送HTTP请求(发送send())

- 数据接收完成，判断http响应状态(status) 200~300之间或304(缓存)执行回调函数

- 使用JavaScript和DOM实现局部刷新

#### 优点

- 局部刷新页面，减少用户心理和实际的等待时间，带来更好的用户体验
- 按需取数据，减轻服务器的负担，最大程度减少冗余请求
- 异步方式与服务器通信，不需要打断用户的操作，具有更加迅速地响应能力
- 基于xml标准化，并被广泛支持，不需要安装插件等，进一步促进页面和数据的分离

#### 缺点

- 本身是针对MVC编程，不符合前端MVVM的浪潮
- 基于原生XHR开发，XHR本身的架构不清晰
- 不符合关注分离（Separation of Concerns）的原则
- 配置和调用方式非常混乱，而且基于事件的异步模型不友好。

#### 适用场景

- 表单驱动的交互
- 深层次的树的导航

- 快速的用户与用户间的交流响应
- 类似投票，yes/no等无关痛痒的场景

- 对数据进行过滤和操纵相关数据的场景

- 普通的文本输入提示和自动完成的场景

#### 不适用场景

- 部分简单的表单

- 搜索
- 基本的导航

- 替换大量的文本

- 对呈现的操纵

### Axios

#### 定义

可以理解为ajax i/o system，这不是一种新技术，本质上还是对原生XMLHttpRequest的封装，可用于浏览器和nodejs的HTTP客户端，只不过它是基于Promise的，符合最新的ES规范

#### 特点

- 浏览器端发起XMLHtppRequests请求
- node端发起http请求
- 支持PromiseAPI
- 监听请求和返回
- 对请求和返回进行转化
- 取消请求
- 自动转换json数据
- 客户端支持抵御XSRF攻击

#### 请求方式

- axios(config)
- axios.request(config)
- axios.get(url [,config])
- axios.post(url [,data [,config]])
- axios.put(url [,data [,config]])
- axios.delete(url [,config])
- axios.patch(url [,data [,config]])
- axios.head(url [,config])





### Fetch

#### 定义

在es6中基于promise设计，不是ajax的进一步封装，而是原生js,没有使用XMLHttpRequest对象

#### 优点

- 语法简洁，更加语义化
- 基于标准Promise实现，支持async/await
- 更加底层，提供的API丰富
- 脱离了XHR,是ES规范里新的实现方式

#### 缺点

- fetch只对网络请求报错，对400，500都当作成功的请求，返回400，500时不会rejecte，只有网络错误这些导致请求不能完成，fetch才会被reject

- fetch默认不带cookie
- fetch不支持abort,不支持超时控制，使用setTimeout及promise.reject的实现的超时控制并不能阻止请求过程继续在后台运行，造成了流量的浪费
- fetch没有办法原生检测请求的进度，而XHR可以

### 浏览器

1.浏览器的缓存机制是什么

2.session、cookie和token区别及应用场景

3.meta viewport的作用

#### 跨域

##### 定义(原因)

因为js同源策略限制，浏览器不能执行其他网站的脚本，同源指的是同协议，同域名，同端口

##### 限制了哪些

1.无法读取非同源网页的Cookie,localStorage,indexedDB

2.无法接触非同源网页的dom

3.无法向非同源地址发送ajax请求，浏览器拒绝响应

##### 跨域解决方案

###### 1.jsonp

原理：利用script标签的src属性可以连接到不同源的js脚本，来达到跨域的目的

JSONP允许用户传递一个callback参数给服务器端，然后服务器端返回数据时会将这个callback参数作为函数名来包裹住JSON数据。这样客户端就可以随意定制自己的函数来自动处理返回的数据了。
JSONP只能解决get请求，不能解决post请求

```javascript
var url='http://www.baidu.com/jsonp_data'
//1.创建script标签
var script=document.creatElement('script')
//2.设置src属性
script.setAttribute('src',url)
//3.插入到head标签内
document.getElementsByTagName('head')[0].appendChild(script);

function callback(data){
    console.log(data) //{name:1}
}



//jsonp_data.js文件
callback({'name':1})

```

###### 2.ajax跨域

浏览器直接去访问其他网站内容会被拒绝，但可以浏览器通过url去请求服务器，服务器通过url去获取其他网站内容然后返回给浏览器



```javascript
$ajax({
    url:'http://localhost:80/?callback=callback',
    method:'get',
    dataType:'jsonp',
    success:(res)=>{
        console.log(res)
    }
})

function callback(data){
    console.log(data)
}
```

###### 3.CORS跨域资源共享

服务端设置res.setHeader(Access-Control-Allow-Origin：'*')就可以开启CORS

Access-Control-Allow-Origin//允许跨域的域名
Access-Control-Allow-Headers//允许的header类型
Access-Control-Allow-Methods//跨域允许的请求方式

###### 4.webpack

vue.config.js中设置

```javascript
 devServer: {
    proxy: {
      '/api': {
        target: process.env.VUE_APP_BASE_API,
        changeOrigin: true,//设置允许跨域
        pathRewrite: {
          '^/api': 'api'
        }
      }
    }
  },
```



###### 5.Nginx 反向代理

通过nginx配置一个代理服务器将客户机请求转发给内部网络上的目标服务器；并将服务器上返回的结果返回给客户端









## 谈谈对前后端分离的理解

