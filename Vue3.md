### vue3

#### 1.获取dom

##### 1.获取单个dom

```js
<div ref="myRef">  vue3</div>
import {ref,onMounted} form 'vue'
setup(){
    const myRef=ref(null);
    onMounted(()=>{
        console.log(myRef.value)
    });
    return {
        myRef
    };
    
}

<h1 ref="color">color</h1>
import {ref,onMounted} form 'vue'
setup(){
    const color=ref(null);
    onMounted(()=>{
        color.value.style.color="red"
    })
}

```



2.获取多个dom

```js
<ul> 
    <li v-for="(item,index) in arr" :key="index" :ref="setRef">{{item}}</li>
</ul>
import {ref,nextTick} form 'vue'
setup(){
    const arr=ref([1,2,3]);
    const myRef=([]);
    const setRef=(el)=>{
        myRef.value.push(el)
    };
    nextTick(()=>{
        console.log(myRef.value)
    })
    return {
        arr,
        setRef,
    }
```

#### 2.父子传参

##### 1.父传子

```js
父组件
<Son :father="father"></Son>
import {ref} from 'vue'
setup(){
    const father=ref="父组件传过的值"
    return {
        father
    }
}

```

```js
子组件
<div>{{father}<div>
    props:[
        "father"
    ],
    setup(props,context){
        console.log(props)
    }

```



##### 2.子传父

```js
子组件

<button @click="handle">点击</button>
import {ref} form 'vue'
setup(props,{emit}){
    handle=()=>{
        emit('add',{title:'子传父'})
    };
    return {
        handle
    }
}


```

```js
父组件

<Son @add="receive"></Son>
setup(){
    cosnt receive=(e:any)=>{
        console.log(e)
    };
    return {
        receive
    }
}

```

#### 3.生命周期钩子函数







#### 4.props  ,context

##### 1.props

props 是响应式的。但不可以解构，否则会失去响应性

```js
setup(props,context){
    console.log(this)    //获取不到this  undefined
	console.log(props)   //获取父组件传过来的值
    console.log(context)  //上下文对象
}
```

##### 2.context

```
非响应式，可直接解构： setup(props, { attrs, slots, emit })
```

context可以访问的属性

root

parent

refs

attrs

listeners

isServer

ssrContext

emit





#### 5.怎么使用watch

watch有两个参数，1：要监听的值，2：回调函数，此回调有两个参数(newVal,oldVal)

##### 1.name为ref定义的变量时，第一个参数直接使用

```js
import {ref,reactive ,watch} form 'vue'
setup(){
    const name=ref('');
    watch(name,(newVal,oldVal)=>{
        console.log(newVal，oldVal)
    })
}

```

##### 2.data为reactive定义的变量需要没在监听时使用函数返回值的形式才能监听到

```js
import {ref,reactive ,watch} form 'vue'
setup(){
    const data=reactive({
        aa:['a','b'],
        bb:''
    })
    
    watch(()=>data.bb,(newVal,oldVal)=>{
        console.log(newVal，oldVal)
    })
}
```

##### 3.深度监听

```js
vm.$watch('data',callback,{
    deep:true
})
vm.data.cc=123
```

##### 4.监听多个变量

参数需要写成数组的形式，同时返回的参数也是数组

```js
setup(){
    const data=reactive({
        girls:['a','b','c'],
        selectGirl:'',
        selectGirlFun:(index)=>{
            data.selectGirl=data.girls[index]
        }
    });
    watch([()=>data.girls,()=>data.selectGirl],(newVal,oldVal)=>{
        console.log(newVal[1],oldVal[1])
    })
}
```



#### 6.怎么使用computed

##### 1.函数式写法

```js
import {ref,computed} form 'vue'

setup(){
    const num1=ref(1);
    const num2=ref(2);
    let sum=computed(()=>{
        return num1.value+num2.value
    });
    return {
        num1,
        num2,
        sum,
    }
}
```



##### 2.options写法

```js
import {ref,computed} form 'vue'

setup(){
    const num1=ref(1);
    const num2=ref(2);
    let mul=computed({
        get:()=>{
            return num1.value*10
        },
        set:(value)=>{
            return num1.value=value/10
        }
    })
    return {
        num1,
        num2,
        mul,
    }
}

```

##### 3.computed传参

```js
<div v-for="(item,index) in arr" :key="index" @click="handle(index)">
    {{item}}
</div>

import {ref,reactive,computed} form 'vue'
setup(){
    const arr=reactive([
        '哈哈','嘿嘿'
    ])
    const handle=computed(()=>{
        return function(index){
            console.log(index)
        }
    });
    return {
        arr,
        handle,
    }
}
```

#### 7.响应式api

##### 1.ref

  ref接收参数并将其包裹在一个带有 `value` property 的对象中返回，然后可以使用该 property 访问或更改响应式变量的值

```
const name=ref('')
return {
	name,
}
```

##### 2.reactive  

reactive  如果将对象分配为 ref 值，则通过 [reactive](https://v3.cn.vuejs.org/api/basic-reactivity.html#reactive) 方法使该对象具有高度的响应式

```js
 setup() {
     let name = ref('')
     let age = ref(0)
     let obj = reactive({
         name: name.value,
         age: age.value
      })
      return toRefs(obj)
  }
```

##### 3.toRef

  为 reactive 对象的属性创建一个 ref,这个 ref 可以被传递并且能够保持响应性

```js

setup(){
    const user=reactive({age:1});
    const age=toRef(user,'age');
    age.value++;
    console.log(user.age)  //2
    user.age++;
    console.log(age.value) //3
}

```

##### 4.toRefs

解构响应式对象数据

```js
<div>{{username}}<div>
<div>{{age}}<div>

import {reactive,toRefs} form 'vue'
setup(){
    const user=reactive({
        username:'hai',
        age:100
    })
    return {
        ...toRefs(user)
    }
}

```

##### 5.isRef、isProxy、isReactive、isReadonly

检查一个值/对象是否为一个 ref / proxy / reactive / readonly 对象



##### 6.readonly只读函数

被修改时会发出警告，但不会改变值

```js
import {readonly} from 'vue'
setup(){
    const info=readonly('只读');
    setTimeout(()=>{
        info='更新'     //只读，不会更改
    }，2000)
}
```



#### 8.组合式api

##### 1.setup  :在组件被创建之前，`props` 被解析之后执行。它是组合式 API 的入口

##### 2.生命周期钩子

created     ==>setup()

mounted   ==>onMounted,

updated     ==>onUpdated,

destroyed  ==>onUnmounted,

##### 3.provide,inject

provide 函数接收两个参数  provide (name,value)

​     name:定义提供property的name

​     value:property的值

inject函数有两个参数 inject(name,default)

​		name:接收provide提供的属性名

​		default:设置默认值，可选参数

使用ref,reactive添加响应式，在父组件或子组件都会修改 `info `的值

```js
//父组件
import {ref,provide} from 'vue'

setup(){
    let info=ref('aaa');
    setTimeout(()=>{
        info.value='bbb'
    },2000)
	provide('info',info);
    return {
        info
    }
}
```



```js
//子组件
<div>{{info}}</div>
import {inject} form 'vue'
setup(){
	const info=inject('info')
    setTimeout(()=>{
        info='ccc'
    },2000)
	return {
		info
	}
}
```

##### 4.h渲染函数

```js
import {h,ref,reactive} from 'vue'
setup(){
	const count=ref(0);
	const object=reactive({foo:'bar'});
	return ()=>h('div',[count.value,object.foo])
}
```

##### 5.getCurrentInstance 获取当前组价实例

```javascript
import {getCurrentInstance } form 'vue'

setup(){
	const { proxy }=getCurrentInstance ()
	proxy.$attrs
	proxy.$data
	proxy.$emit
	proxy.$data
}
```

