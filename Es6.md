## ES6面试题

#### es5和es6的区别

#### let、const、var区别

```javascript
// 块级作用域
let和const具有块级作用域，var不存在块级作用域,块级作用域解决了ES5中的两个问题:
1.内层变量可能覆盖外层变量
2.用来计数的循环变量泄露为全局变量

// 变量提升
var存在变量提升，let和const不存在变量提升，变量只能在声明之后使用，否则会报错

// 重复声明
var可以重复声明变量，后同名变量覆盖前面的变量,const和let不允许重复声明变量

// 暂时性死区
var声明变量不存在暂时性死区,let、const在未声明变量前不可使用 ,称为暂时性死区

// 初始值设置
var、let 声明时可不设置初始值，const声明时必设初始值

// 指针指向
var、let 声明的值可以修改，const声明常量不能修改

```

#### 箭头函数



##### 特点

1.this是静态的，始终指向函数声明时所在作用域下的this的值

2.不能作为构造函数实例化对象(不能new),否则会抛出一个错误

3.不能使用arguments变量



##### 适用场景

适合与this无关的回调，定时器，数组方法回调

不适合与this有关的dom事件回调、对象的方法



#### 模板字符串

#### 解构赋值

#### for of循环

#### Set、Map

set:唯一值的集合，类似于数组,数据去重

map:键值对的结构，用于解决以往不能用对象做为键的问题

weakMap:键名是对象的弱引用,所对应的对象可能会被自动回收

```javascript
//Set
new Set([]).add(1)    //添加值
new Set([]).delete(2);//删除值
new Set([]).size      //长度
new Set([]).has(1)    //返回布尔值，表示该值是否为Set的成员
new Set([]).clear()   //清除所有项
//遍历
new Set(['red']);
keys()      //'red'
values()    //'red'
entries()   //['red' 'red']
forEach()

//Map
var map=new Map()
map.set('name','dw')    //set key:value
map.get('name')         
map.delete()
map.has('name')         //返回布尔值,判断是否有key为name项
map.size
map.clear()


//遍历方法 
const map = new Map([
  ['F', 'no'],
  ['T',  'yes'],
]);

for (let key of map.keys()) {
  console.log(key);  //"F"  "T"
}

for (let value of map.values()) {
  console.log(value);  //"no" "yes"
}

for (let item of map.entries()) {
  console.log(item[0], item[1]);  // "F","no"   "T","yes"
}

for (let [key, value] of map.entries()) {
  console.log(key, value);  //// "F","no"   "T","yes"
}



//WeakMap 与Map区别
1、WeakMap只接受对象作为key，如果设置其他类型的数据作为key，会报错
2、WeakMap的key所引用的对象都是弱引用，只要对象的其他引用被删除，垃圾回收机制就会释放该对象占用的内存，从而避免内存泄漏
3、由于WeakMap的成员随时可能被垃圾回收机制回收，成员的数量不稳定，所以没有size属性
4、没有clear()方法
5、不能遍历



//Set、Map区别
Set：成员不能重复；只有键值没有键名，类似数组；可以遍历，方法有add, delete,has
Map：本质上是健值对的集合，类似集合；可以遍历，可以跟各种数据格式转换

//Object、Map区别
1.key的数据类型
Object:key只能是number、string、symbol
Map:key可以是任意类型

2.创建方式
Object:字符串创建、new Object()
Map:new Map()

3.新增数据
Object:obj[key]=''
Map:map.set()

4.删除数据
Object:delete obj.name
Map:map.delete()

5.读取数据
Object:obj[name]
Map:map.get()



```



#### ... 展开运算符

#### 修饰器 @

#### class 类的继承

#### Symbol

#### Proxy代理







#### import、export导入导出

```javascript
//import
import {a,b,c} from "./exportExample.js"  //导入一个或多个
import * as a from "./exportExample.js"   //导入整个模块


//export
特点：1.需加{}，可以导出一个或多个
     2.对应import语句需要使用大括号
     3.一个模块只能有多个export
export {a,b};


//export default
特点：1.不需要{},只能导出一个
     2.对应的import语句不需要使用大括号
     3.一个模块只能有一个export default
export default a  
```



#### forEach、for in、for of区别

- forEach更多的用来遍历数组
- for in 一般常用来遍历对象或json
- for of数组对象都可以遍历，遍历对象需要通过和Object.keys()
- for in循环出的是key，for of循环出的是value

#### 将for循环改成for of形式

```javascript
let arr = [11,22,33,44,55];
let sum = 0;
for(let i=0;i<arr.length;i++)
{
    sum += arr[i];
}



转换


let arr = [11,22,33,44,55];
let sum = 0;
for(k of arr){
    sum+=k
}

```



#### 对promise理解

##### 定义

```javascript
Promise是异步编程的一种解决方案，简单说就是一个容器，里面保存着某个未来才会结束的事件（通常是一个异步操作）的结果
```



##### 特点

```javascript
1. 对象的状态不受外界影响

  promise有三种状态：pending、fulfilled和rejected,只有异步操作的结果，可以决定当前是哪一种状态，任何其他操作都无法改变这个状态

2. 一旦状态改变，就不会再变，任何时候都可以得到这个结果

  Promise对象的状态改变，只有两种可能：从pending变为fulfilled和从pending变为rejected。只要这两种情况发生，状态就凝固了，不会再变了，会一直保持这个结果
```



##### 作用

```javascript
ES6 规定，Promise对象是一个构造函数，用来生成Promise实例
```

###### resolve函数作用

将Promise对象的状态从“未完成”变为“成功”（即从 `pending` 变为 `resolved`），在异步操作成功时调用，并将异步操作的结果，作为参数传递出去

###### reject函数作用

将`Promise`对象的状态从“未完成”变为“失败”（即从 `pending` 变为`rejected`），在异步操作失败时调用，并将异步操作报出的错误，作为参数传递出去

##### 缺点

```javascript
1.promise一旦执行无法取消
2.如果不设置回调函数promise内部抛出的错误，不会反映到外部
3.当处于pending（进行中）的状态时，无法得知进行到那一阶段（刚开始或者即将完成）
```



##### promise三种状态

```javascript
1.Pending:promise对象刚被创建后的初始化状态(执行中)
2.Fulfilled:成功时时会调用 onFulfilled
3.Rejected:失败时此时会调用 onRejected
```

##### promise的方法

###### 1.then()

执行状态改变时的成功回调或失败回调

```javascript
let p = new Promise(function(reslove,reject){
    reslove('成功')  //状态由等待变为成功，传的参数作为then函数中成功函数的实参
    reject('失败')  //状态由等待变为失败，传的参数作为then函数中失败函数的实参
})
```



###### 2.catch()

可以实现错误的捕获

```javascript
let p = new Promise(function(resolve,reject){
    reject('失败')
});

p.then((res)=>{},(err)=>{
    throw Error('错误')    //有err执行err,没有err执行catch
}).catch(e=>{
    console.log(e+'公共的err')   //执行catch
})
```



###### 3.finally()

用于指定不管 Promise 对象最后状态如何，都会执行的操作

###### 4.all()

返回的依旧是promise, all两个全成功才表示成功

```javascript
function read(content) {
    return new Promise(function (resolve, reject) {
        setTimeout(function () {
            resolve(content)
        }, 1000)
    })
}

let result = Promise.all([read(1), read(2)]);
result.then((data) => {
    console.log(data) //[ 1, 2 ]
})
```



###### 5.race()

如果先成功了那就成功了, 如果先失败了那就失败了

```javascript
function read(content) {
    return new Promise(function (resolve, reject) {
        setTimeout(function () {
            if(content>4){
                resolve(content)
            }else{
                reject(content)
            }
        }, 1000*content)
    })
}

let result = Promise.all([read(5), read(2)]);
result.then((data) => {
    console.log('成功'+data)
},(err)=>{
    console.log('失败'+err) //失败2
})
```



###### 6.any()

有一个成功就算成功，全部失败才算失败



##### race、all和any的区别

all所有Promise的结果都返回resolve才会执行then，返回结果为一个存放所有结果的数组里，如果有任何一个返回reject，则执行catch，如果第一个Promise是有延迟执行的 则会等待执行完才继续

可实现发送多个请求，参数不一定是数组，只要有iterable接口就行，函数返回的是一个数组



race的方法执行结果取决于第一个Promise的返回结果，reject则执行catch，resolve则执行then，不会等待定时器的执行，会将定时器时间执行时间短的结果返回











### async,await

ES7提出的基于promise的解决异步的最终方案

#### async

async是一个加在函数前的修饰符，被async定义的函数会默认返回一个Promise对象resolve的值。因此对async函数可以直接then，返回值就是then方法传入的函数。

#### await

await 也是一个修饰符，只能放在async定义的函数内。可以理解为等待,修饰的如果是Promise对象：可以获取Promise中返回的内容,且取到值后语句才会往下执行；如果不是Promise对象：把这个非promise的东西当做await表达式的结果。



#### 使用场景

多个请求中，后面请求参数需要前面请求返回数据



```javascript
async submit(type) {
     var res = await salesCheck(this.form)
}
```



