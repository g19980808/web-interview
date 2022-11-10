## Typescript

介绍：微软开发，JavaScript的超集,浏览器不支持ts,需编译成js

安装 ：npm install -g typescript

输入tsc --init     自动生成 tsconfig.json 文件

### 1.typescript中数据类型：



#### 1.boolean 布尔类型

```typescript
var flag:boolean=true  //定义
flag=false             //赋值只能true  false
```



#### 2.number 数字类型(不区分整型与浮点型)

```typescript
var a:number=123
a=222
```



#### 3.string  字符串类型

#### 4.array  数组类型

```typescript
//第一种
var arr:number[]=[1,2,3]   //数组中只能数字类型
var arr:string[]=['1','2','3']   //数组中只能字符串
//第二种 泛型
var arr:Array<number>=[11,22]
var arr:Array<string>=['11','22']
//第三种
var arr:any[]=['1',33,true]
console.log(arr)
```



#### 5.tuple  元组类型(指定多种类型）

```typescript
var arr:[string,number,boolean]=['ts',33,true]
console.log(arr)
```



#### 6.enum  枚举类型(用于标识状态)

```typescript
enum flag {success=1,error=2}
consloe.log(flag.error)
//或者
var f:flag=flag.success
console.log(f)


enum color {red,blue=5,orage}
console.log(color.red)     //  0    red索引值
console.log(color.blue)    //  5    blue的值
console.log(color.orage)   //  6    orage索引值
```



#### 7.any  任意类型

```typescript
var num:any=123  //数字类型
num='str'        //字符串类型
```



#### 8.null和undefined(never类型的子类型)

```typescript
var num:number | undefined;
console.log(num)   //undefined
var num:number | undefined;
num=123
console.log(num)   //123
```



#### 9.void类型(表示定义方法时没有返回任何类型)

```typescript
function run():void{
    console,log('run')
}
run()  //无返回类型

function run():number{
    return 123
}
run()   //有返回类型
```



#### 10.never类型(从不会出现的类型)

### 2.定义函数

#### 1.函数声明法

```typescript
function run:string{
    return '333'
}
run()
```

#### 2.匿名函数法

```
var run=function():number{
	return 123
}
console.log(run())
```

#### 3.定义方法传参

```typescript
//函数声明传参
function fun(name:string,age:number):string{
    return `${name}--${age}`
}
consloe.log(fun('张三',12))
//匿名函数传参
var fun =function(name:string,age:number):string{
    return `${name}--${age}`
}
console.log(fun('张三',12))
```

#### 4.方法可选参数  (?)

```typescript
function fun(name:string,age?:number):string{
    if(age){
        return `${name}--${age}`
     }else {
         return `${name}`
     }
  
}
console.log(fun('张三'))
```

5.默认参数

```typescript
function fun(name:string,age?:number=20):string{
    if(age){
        return `${name}--${age}`
     }else {
         return `${name}`
     }
  
}
console.log(fun('张三'))
```

6.剩余参数

```typescript
function sum(a:number,b:number,){
    
}
```

