# 	VUE面试题

### 虚拟dom原理

#### 虚拟dom为什么能提高性能

#### 1.定义

虚拟dom其实就是用一个原生的js对象去描述一个dom节点，是对真实dom的抽象。状态变更时，记录新树和旧树的差异 最后把差异更新到真正的dom中，相当于在js和真实dom之间做了一个缓存，利用patch(diff算法)对比新旧虚拟dom记录到一个对象中按需更新，最后创建真实的dom

#### 2.原生DOM慢的原因

浏览器收到一个DOM操作，就会走一遍完整的渲染流程，像计算元素坐标的操作就会浪费掉，因为下次DOM操作可能会改变之前计算的坐标

#### 3.虚拟dom渲染方式

利用batching把所有的DOM操作收集起来，一次性提交给真实的DOM，diff算法通过对比新旧虚拟DOM,记录之间的差异

中心思想：在一个不在render tree的元素统一统计所有操作，再把节点加到render tree上，这样复杂的DOM操作最后就只进行一次layout



#### 4.虚拟DOM优点

 真实的DOM创建、更新、插⼊等操作会带来⼤量的性能损耗，从⽽极⼤的降低渲染效率

- 减少DOM的操作

​          减少DOM的操作的次数：虚拟DOM可以将多次操作合并为一次操作，比如添加1000个节点，却是一个一个操作的，虚拟DOM则是往数组中添加一千个文本，虚拟DOM可以合并为一次
​         减少DOM操作的范围：虚拟DOM借助DOM diff可以把多余的操作省掉，如果页面中990个节点，现在需要添加10个，虚拟DOM通过diff算法对比节点，只操作需要更新的10个节点就好了，而js是无法判断的，会对所有的DOM进行操作

- 跨平台

  虚拟DOM本质上是JavaScript对象,而DOM与平台强相关,相比之下虚拟DOM可以进行更方便地跨平台操作,例如服务器渲染、移动端开发等等

#### 5.虚拟DOM缺点

​    首次渲染大量DOM时，由于多了一层虚拟DOM的计算，会比innerHTML插入慢

#### 6.虚拟DOM基本步骤

- 用 JavaScript 对象模拟真实 DOM 树，对真实 DOM 进行抽象；

- `diff 算法` — 比较两棵虚拟 DOM 树的差异；

- `patch 算法` — 将两个虚拟 DOM 对象的差异应用到真正的 DOM 树

  1.首先在 `oldVnode`（老 VNode 节点）不存在的时候，相当于新的 VNode 替代原本没有的节点，所以直接用 `addVnodes` 将这些节点批量添加到 `parentElm` 上。------创建新增的节点

  2.然后同理，在 `vnode`（新 VNode 节点）不存在的时候，相当于要把老的节点删除，所以直接使用 `removeVnodes` 进行批量的节点删除即可。-----删除已经废弃的节点

  3.最后一种情况，当 `oldVNode` 与 `vnode` 都存在的时候，需要判断它们是否属于 `sameVnode`（相同的节点）。如果是则进行patchVnode（比对 VNode ）操作，否则删除老节点，增加新节点。--修改需要更新的节点



#### 7.虚拟dom如何转换真实dom

在⼀个组件实例⾸次被渲染时，它先⽣成虚拟dom树，然后根据虚拟dom树创建真实dom，并把真实dom挂载到页⾯中合适的位置，
此时，每个虚拟dom便会对应⼀个真实的dom。
如果⼀个组件受响应式数据变化的影响，需要重新渲染时，它仍然会重新调⽤render函数，创建出⼀个新的虚拟dom树，⽤新树和旧
树对⽐，通过对⽐，vue会找到最⼩更新量，然后更新必要的真实dom节点

这样⼀来，就保证了对真实dom达到最⼩的改动。



#### 8.diff算法

##### (1)diff算法的时间复杂度

两个树的完全的 diff 算法是一个时间复杂度为 O(n3) , Vue 进行了优化·O(n3) 复杂度的问题转换成 O(n) 复杂度的问题(只比较同级不考虑跨级问题)，因为在前端操作dom的时候了，不会把当前元素作为上一级元素或下一级元素，很少会跨越层级地移动Dom元素，常见的都是同级的比较。 所 以 Virtual Dom只会对同一个层级的元素进行对比。

##### (2)vue中diff算法的原理

在数据发生变化，vue是先根据真实DOM生成一颗 virtual DOM ，当 virtual DOM 某个节点的数据改变后会生成一个新的 Vnode ，然后 Vnode 和 oldVnode 作对比，发现有不一样的地方就直接修改在真实的DOM上，然后使 oldVnode 的值为 Vnode ，来实现更新节点。

对比过程：

- 判断`Vnode`和`oldVnode`是否相同，如果是，那么直接return；
- 如果他们都有文本节点并且不相等，那么将更新为`Vnode`的文本节点。
- 如果`oldVnode`有子节点而`Vnode`没有，则删除el的子节点
- 如果`oldVnode`没有子节点而`Vnode`有，则将`Vnode`的子节点真实化之后添加到el
- 如果两者都有子节点，则执行`updateChildren`函数比较子节点，而这个函数也是diff逻辑最多的一步



#### 9.不使用index作为for循环key值

主要是因为虚拟DOM的diff算法，当遍历一个数组的时候使用了index作为key值，如果这个数组中的数据进行打乱，因为diff算法是根据key值去进行新旧对比的，如果发现key所对应的数据不一致的情况下，就会进行重新渲染，删除原来的旧元素，重新生成新的元素。

而如果不是使用index作为key值，使用的是唯一data数据唯一标识的话，diff算法会根据key去对比发现原来的DOM元素只是调换了位置，就不会去删除旧元素而去生成新的元素了。

不使用index作为key值其实是方便了diff算法，使其更加高效，









### vue权限管理

#### 1.菜单权限管理(不同用户菜单权限不同)

​     根据用户登录返回菜单权限 ,使用vuex+本地存储数据，只使用vuex刷新页面数据丢失

​     退出登录需要清除sessionStoryage和vuex数据

​     sessionStorage.clear()    清除本地存取

​     window.location.reload()    刷新清除vuex

```javascript
  //store.js

   state:{
      rightList: JSON.parse( sessionStorage.getItem('rightList') ||  '[]')   
    }

   mutations:{
      setRightList(state.data){
	       state.rightList=data
	       sessionStorage.setItem('rightList',JSON.stringify(data))
      }
    }

  // login.vue
      login().then(res=>{
         let {data}=res 
            this.$store.commit('setRightList',data.rightList)
      })

  // home.vue
    //一级菜单
    <div v-for="(item,index) in menuList" :key="index">      
         {{ item}}
       //二级菜单
      <div v-for="(item2,index2) in item" :key="index2">{{item2}}</div>
    <div>
          
    import {mapState} form 'vuex'
     created(){
         this.menuList=this.rightList
     }
     computed:{
        ...mapState(['rightList'])
     }
```





#### 2.界面权限管理

#####   1.路由导航钩子，防止用户跳过登录进入其他页面



```javascript
   router.js
   
   router.beforeEach((to,from,next)=>{
        if(to.path=="/login"){
	        next()
         }else {
	        const token=sessionStorage.getItem('token')
	        if(!token){
	             next('/login')
	         }else {
	             next()
             }
         }
     })
```







#####      2.根据登录动态添加路由规则



```javascript
    // router.js
    import store form 'store.js'
    const userRule={path:'/user' ,component:User}
    const rolesRule={path:'/user' ,component:roles}
    const goodsRule={path:'/user' ,component:goods}
    const ruleMap={
       'use' :userRule,
       'roles':  rolesRule,
       'goods': goodsRule
     }
    export function addRouter(){
        // 根据二级路由权限，对路由规则进行动态添加
         const currentRoutes=router.options.routes
         const rightList= store.state.rightList
         rightList.forEach(item=>{
	          item.children.forEach(its=>{
	              const temp =ruleMap[item.path]
	              temp.meta=item.rights    添加路由元数据
                  currentRoutes[2].children.push(temp)
	           })
          })
          router.addRoutes(currentRoutes)               
      }



   // login.vue
     import { addRouter } form 'router'

     login(){
       addRouter ()    //登录动态添加二级路由
     }

     //登录完成刷新会丢失动态添加的路由
     // 在 APP.vue中
      import {addRouter } form 'router.js'
       created(){
           addRouter ()
      }



```





#### **3.按钮权限管理**

```javascript
   //通过自定义指令  自定义： action 删除   effect  禁用
   // permission.js
     import Vue form 'vue'
     import router form 'router.js'

      Vue.directive('permission',{
          inserted(el,binding){
             const action= binding.value.action   
	         const effect=binding.value.effect
              // 通过 添加路由元数据判断按钮权限

             if(router.currentRoute.meta.indexOf(action)==-1){
                   if(effect=='disabled'){  
                        el.disabled=true
	                    el.classList.add('is-disabled')
	                }else {
	                   el.parentNode.removeChild(el)
	                }
              }
          }

      })



    // main.js
     import 'permission.js'

    // user.vue
     <button v-permission="{action:'add',effect:'disabled'}">添加</button>
```





#### 4.请求和响应权限管理

#####    1.请求拦截

```javascript
   const actionMap={
       'get':'view',    
       'post':'add',
       'put':'edit',
       'delete':'delete'
   }

    axios.interceptors.request.use((request)=>{
        if(request.url!=='login'){
           // 1.除了登录请求都添加token
	         request.header.Authorization=sessionStorage.getItem('token')
	       //2.判断非权限范围内的请求   例如 非权限按钮删除
	         const action =actionMap[request.method]
	         const currentRight=router.currentRoute.meta
	         if( currentRight&&currentRight.indexOf(action)===-1){
	             aler('无权限')
	            return Promise.reject(new Error('无权限'))
	         }
         }
       return request
    })
```





#####     2.响应拦截

```javascript
   axios.interceptors.response.use(res=>{
       if(res.data.code===401){
	       router.push('/login')
	       sessionStorage.clear()
	       window.location.reload()
        }
        return res
    })
```







### 知识点



#### 对Vue的理解

Vue是由尤雨溪团队开发的在2014年正式发布的一款轻量级框架，用于构建用户界面，它的核心思想就是MVVM数据驱动，实现了dom监听和双向绑定，当模型层数据修改时，VM 层检测到通知视图层进行相应修改，视图变化也会更新模型层数据，而在2020年正式发布了3.0，使用proxy实现响应式代替了Vue2的Object.defineProperty，options Api也改成Composition Api

#### vue的优点和缺点

##### 优点：

1.vue最突出的优势在于对数据进行双向绑定，使用虚拟DOM

2.vue可以进行组件化开发，数据与结构相分离，使代码量减少，从而提升开发效率，易于理解

3.vue是单页面应用，页面局部刷新，不用每次跳转都请求数据，加快了访问速度，提升了用户体验

4.vue作为一款轻量级框架，门槛低，上手快，简单易学。

##### 缺点：

1.初次加载时耗时多

2.VUE不支持IE8



#### vue与react对比

不同：

监听数据变化的实现原理不同监听数据变化的实现原理不同

数据流不同

HoC 和 mixins

组件通信的区别

模板渲染方式的不同

Vuex 和 Redux 的区别



#### MVC、MVVM区别

##### MVC

MVC指Model-View-Controller,代表模型-视图-控制器

model:用于处理数据逻辑部分

view:用于显示视图部分

controller:用于处理用户交互部分，

MVC核心：controller负责将model的数据用view显示出来



##### MVVM

View：视图层，Model 数据模型，而 ViewModel 是把两者建立通信的桥梁，实现了dom监听和双向绑定。

在 MVVM 框架下，View 和 Model 之间没有直接的联系，而是通过 ViewModel 进行交互。View 和 ViewModel 之间以及 Model 和 ViewModel 之间的交互都是双向的，因此 view 数据的变化会同步到 Model 中，而 Model 数据的变化也会立即反映到 View 上。可以说它们两者是实时更新的，互相影响。 ViewModel 通过双向数据绑定把 View 层和 Model 层连接了起来，而 View 和 Model 之间的同步工作完全是自动的，因此开发者只需要关注业务逻辑，不需要手动操作 DOM，也不需要关注数据状态的同步问题，这些都由 MVVM 统一管理

###### 优点

1. 分离视图和模型,降低代码耦合
2. 独立开发，可以专注于业务逻辑和数据的开发（ViewModel）
3. 可复用性,可以把一些视图逻辑放在一个ViewModel里面，让很多view重用这段视图逻辑
4. 提可测试性： ViewModel的存在可以帮助开发者更好地编写测试代码 

###### 缺点

1.Bug很难被调试: 因为使⽤双向绑定的模式，当界⾯异常，有可能是View的代码有Bug，也可能是Model的代码有问题

2..虽然使用Model方便了保证数据一致性，但是大的模块中长期不释放内存就会造成花费更多的内存

3.对于⼤型的图形应⽤程序，视图状态较多，ViewModel的构建和维护的成本都会⽐较⾼



##### 区别(优势)

- 主要就是mvc中Controller演变成mvvm中的viewModel。 mvvm主要解决了mvc中大量DOM操作使页面渲染性能降低，加载速度变慢的问题 
- MVVM与MVC最大区别是实现了model与view的自动同步，当model的属性改变时，不用在手动操作dom元素，来改变view的显示,而是view层显示会自动修改
- 简化了业务与视图的依赖，还解决了数据频繁更新操作dom的问题

#### 双向绑定

##### 什么是双向绑定

单向绑定：把model绑定到view,当数据改变时，更新到view层

双向绑定：在单向绑定的基础上把view绑定到model上，用户操作视图同时也改变model数据

##### 双向绑定的原理

双向数据绑定是采用数据劫持结合发布者订阅者模式的方式，通过Object.defineProperty()来劫持各个属性的getter和setter,在数据变动时发布消息给订阅者，触发相应的监听回调，getter函数里面执行的任务是watcher订阅者，而setter函数执行的任务是发布者

- 实现一个数据监听器Observer,能够对数据对象的所有属性进行监听，当对象属性有变化时可拿到最新值并通知订阅者
- 实现一个指令解析器Compile,对每个元素节点的指令进行扫描和解析，根据指令模板替换数据，以及绑定相应的更新函数
- 实现一个Watcher,作为连接Observer和Compile的中间桥梁，能够订阅并收到每个数据对象属性变动的通知，执行指令绑定的相应回调函数，从而达到更新视图的目的
- mvvm入口函数，整合以上三者

数据属性

Configurable:能否通过delete删除属性，默认false,不能删除； true可以删除，设置为false后不能再改为true

Enumerable:属性可否被枚举(是否可以通过for in 循环)，默认false

Writable:是否可以修改，默认false

Value:属性的值，默认undefined



访问器属性

Configurable：delete 能否删除

Enumerable:是否可枚举

Get:读取属性时调用，默认undefined

Set:写入属性时调用，默认undefined

##### 怎么实现双向绑定





#### vue的响应式原理

##### 是什么：

响应式就是说，数据发生改变的时候，视图会重新渲染，匹配更新为最新的值

##### 原理：

Object.defineProperty 为对象中的每一个属性，设置 get 和 set 方法，每个声明的属性，都会有一个 专属的依赖收集器 subs，当页面使用到 某个属性时，触发 ObjectdefineProperty - get函数，页面的 watcher 就会被 放到 属性的依赖收集器 subs 中，在 数据变化时，通知更新；
当数据改变的时候，会触发Object.defineProperty - set函数，数据会遍历自己的 依赖收集器 subs，逐个通知 watcher，视图开始更新；





#### 生命周期

##### vue生命周期定义

Vue 实例从创建到销毁的过程，就是生命周期。也就是从开始创建、初始化数据、编译模板、挂载Dom→渲染、更新→渲染、卸载等一系列过程，称为 Vue 的生命周期。

##### 生命周期有哪些

8 个 ：beforeCreate, created, beforeMount, mounted,beforeUpdate,updated,beforeDestroy,destroyed

+2个：activated ，deactivated

##### 生命周期的作用

它的生命周期中有多个钩子函数，这些钩子函数能够让我们准确地控制数据流和其对DOM的操作，形成更好的逻辑

##### 第一次页面加载会触发哪几个钩子

beforeCreate, created, beforeMount, mounted

##### 在哪个阶段有$el,$data

beforeCreate   el无   data无

created             el无    data有

beforeMount   el无    data有

mounted           el有   data有

##### 父子组件钩子函数执行顺序

加载渲染过程

父beforeCreate ->父created ->父beforeMount ->子beforeCreate  ->子created  ->子beforeMount ->子mounted ->父mounted 

子组件更新过程

父beforeUpdate ->子beforeUpdate ->子updated ->父updated 

父组件更新过程

父beforeUpdate ->父updated

销毁过程

父beforeDestroy -> 子beforeDestroy -> 子destroyed -> 父destroyed

##### 每个周期具体适合哪些场景

beforecreate : 可以在这加个loading事件，页面加载完成之后将loading移除

created : 初始化完成时的事件写在这里，如在这结束loading事件，异步请求也适宜在这里调用

mounted : 挂载元素，获取到DOM节点

updated : 如果对数据统一处理，在这里写上相应函数

beforeDestroy : 可以做一个确认停止事件的确认框 nextTick : 更新数据后立即操作dom

destroyed:事件的解绑，监听的移除，定时器的清除等

##### 如果加入keep-alive 会增加两个生命周期

activated : keep-alive 组件激活时调用

deactivated:keep-alive 组件停用时调用

##### 如果加入keep-alive ，第一次会执行哪些生命周期

beforeCreate、created、beforeMount、mounted、activated 

##### 如果加入keep-alive ，第二次或第N次会执行哪些生命周期

只执行一个生命周期  activated 

##### 对 keep-alive 的了解

###### 是什么

  keep-alive是Vue的内置组件，当它包裹动态组件时，会缓存不活动的组件实例，而不是销毁它们。keep-alive是一个抽象组件，它自身不会渲染一个DOM元素，也不会出现在父组件中。

###### 作用

  在组件切换过程中 把切换出去的组件保留在内存中，防止重复渲染DOM，减少加载时间及性能消耗，提高用户体验性

###### 原理

  在 created钩子函数调用时将需要缓存的 VNode 节点保存在 this.cache 中／在 render（页面渲染） 时，如果 VNode 的 name 符合缓存条件（可以用 include 以及 exclude 控制），则会从 this.cache 中取出之前缓存的 VNode实例进行渲染。

###### 参数

- include - 字符串或正则表达式，只有名称匹配的组件会被缓存。
- exclude - 字符串或正则表达式，任何名称匹配的组件都不会被缓存，优先级比 include 高
- max - 数字，最多可以缓存多少组件实例，超出上限使用LRU的策略置换缓存数据

###### 生命周期变化

1.activated

- 在 keep-alive 组件激活时调用
- 该钩子函数在服务器端渲染期间不被调用

2.deactivated

- 在 keep-alive 组件停用时调用
- 该钩子在服务器端渲染期间不被调用
- 被包含在 keep-alive 中创建的组件，会多出两个生命周期的钩子: activated 与 deactivated
- 使用 keep-alive 会将数据保留在内存中，如果要在每次进入页面的时候获取最新的数据，需要在 activated 阶段获取数据，承担原来 created 钩子函数中获取数据的任务。

###### 用法

- 在动态组件中应用

  ```javascript
  <keep-alive :include="whiteList" :exclude="blackList" :max="amount">
       <component :is="currentComponent"></component>
  </keep-alive>
  ```

  

- 在vue-router中应用

  ```javascript
  <keep-alive :include="whiteList" :exclude="blackList" :max="amount">
      <router-view></router-view>
  </keep-alive>
  ```

  

- 结合router,缓存部分页面

  ```javascript
  //1、在App.vue中设置：（根据是否需要缓存切换模式）
  <keep-alive>
      <router-view v-if="$route.meta.keepAlive"></router-view>
  </keep-alive>
  <router-view v-if="!$route.meta.keepAlive"></router-view>
  
  //2、在router.js路由页设置：
  new Router({
    mode: 'history',
    routes: [
      {
        path: '/',
        name: 'home',
        component: Home,
        redirect: 'goods',
        children: [
          {
            path: 'goods',
            name: 'goods',
            component: Goods,
            meta: {
          	keepAlive: false // 不需要缓存
        	  }
          },
          {
            path: 'seller',
            name: 'seller',
            component: Seller,
            meta: {
          	keepAlive: true  // 需要缓存
        	  }
          }
        ]
      }
    ]
  })
  ```

  

#### --Vue template 到 render 的过程



#### new Vue()都做了什么

![image-20220711171129353](C:\Users\g5988\AppData\Roaming\Typora\typora-user-images\image-20220711171129353.png)

![image-20220711171107872](C:\Users\g5988\AppData\Roaming\Typora\typora-user-images\image-20220711171107872.png)



1. ```javascript
   //创建$options
   1.合并Vue.options
      一个是Vue的构造函数(vm.constructor)预先定义的
      一个是new Vue时传入的入参对象
   //initLifecycle(vm)
   2.初始化实例对象的生命周期状态，如：$parent、$children、$refs、$root、 
   //initEvents(vm)
   3.创建实例对象的_events成员，包含父组件绑定在当前组件的事件
   //initRender(vm)
   4.设置实例对象的$slots和$scopedSlots、$createElement、$attrs、$listeners
   //beforeCreate()
   5.触发beforeCreate 函数
   //initInjections(vm)
   6.初始化组件的inject；通过逐级查找，从父级provide中获取子级组件inject定义的属性值，并增加对该属性的监听。
   //initState(vm)
   7.初始化组件内的props、methods、data、computed、watch
   //initProvide
   8.初始化组件的provide
   //created()
   9.触发created 函数
   //mount(el)
   10.进入挂载阶段
   
    
   ```







#### 理解组件中data是一个函数

组件中的data写成函数，数据会以函数返回值的形式定义，每复用一次组件都会返回一个新的data,类似于给每个组件实例创建一个私有数据空间，每个组件实例维护各自的数据，如果写成对象形式，每个组件会共用一个data,如果要修改一个属性，都会随着改变



#### data中属性名可以与methods中的方法同名吗

可以同名，methods的方法名会被data的属性覆盖；调试台也会出现报错信息，但是不影响执行；

原因：源码定义的initState函数内部执行的顺序：props>methods>data>computed>watch



#### v-if和v-for为什么不建议一起使用

```javascript
vue2.x版本中，当 v-if 与 v-for 一起使用时，v-for 具有比 v-if 更高的优先级；
vue3.x版本中，当 v-if 与 v-for 一起使用时，v-if 具有比 v-for 更高的优先级。
官网明确指出：避免 v-if 和 v-for 一起使用，永远不要在一个元素上同时使用 v-if 和 v-for。

可以先对数据在计算数据中进行过滤，然后再进行遍历渲染；
操作和实现起来都没有什么问题，页面也会正常展示。但是会带来不必要的性能消耗；
```

vue2 

v-for 优先级高于v-if,每次渲染都会先循环再进行条件判断,，带来性能方面的浪费,并且控制台会报警告

如果遇到需要同时使用时可以嵌套一层元素  <template></template>

可以通过计算属性computed提前过滤掉那些不需要显示的项

![image-20220714142011737](C:\Users\g5988\AppData\Roaming\Typora\typora-user-images\image-20220714142011737.png)





vue3

v-if 优先级高于 v-for

![image-20220714142110061](C:\Users\g5988\AppData\Roaming\Typora\typora-user-images\image-20220714142110061.png)



#### src 目录每个文件夹和文件的用法

assets 文件夹是放静态资源；

 components 是放组件；

 router 是定义路由相关的配置; 

 view 视图；

 app.vue 是一个应用主组件；

 main.js 是入口文件



#### 组件name的作用

- 项目使用 keep-alive 时，可搭配组件的 name 进行缓存过滤。
- DOM 做递归组件时需要调用自身 name 
- vue-devtools 调试工具里显示的组件名称是由 vue 中组件 name 决定的

#### template 

##### 作用

1. 模板占位符，可帮助我们包裹元素.
2. 但在循环过程当中，template不会被渲染到页面上
3. template标签不支持v-show指令，
4. 即v-show="false"对template标签来说不起作用
5. template标签支持v-if、v-else-if、v-else、v-for这些指令

##### template和jsx区别

- ##### template

模板语法(html的扩展)

数据绑定使用Mustache语法(双大括号)

- ##### jsx

JavaScript的语法扩展

数据绑定使用单大括号



JSX相对于template而言，具有更高的灵活性，在复杂的组件中，更具有优势，而 template 虽然显得有些呆滞。但是 template 在代码结构上更符合视图与逻辑分离的习惯，更简单、更直观、更好维护。







#### 理解 Vue 的单向数据流

单向数据流就是从**一个组件单方向将数据流向它的内部组件**，也就是父组件的数据流向子组件中，但子组件不能将这个数据修改掉，如要返回到父组件中修改然后重新流向子组件，从而达到更新数据的原理

![image-20220710164527278](C:\Users\g5988\AppData\Roaming\Typora\typora-user-images\image-20220710164527278.png)

#### vue内置指令有哪些

v-model:value和input的语法糖,表单的数据绑定

v-bind: 绑定属性，动态更新HTML元素上的属性简写 ‘：’

v-on：绑定事件，简写‘@’

v-for: 遍历数组，要使用key,且保证唯一性

v-if/v-else/v-else-if ：判断条件，条件为真显示，否则隐藏

v-show：display 控制显示隐藏

v-html： 解析html

v-text: 解析文本

v-once：只执行一次

v-cloak：防止插值表达式里出现变量名



#### Vue修饰符有哪些

##### v-model 修饰符

.lazy 改变后触发，光标离开input 输入框的时值才会改变

.number 将输出字符串转为number 类型

.trim 自动过滤用户输入的首尾空格



##### 事件修饰符

.stop  阻止点击事件冒泡，相当于原生 js 中的event.stopPropagation()

.prevent 阻止标签默认行为，相当于原生js中event.preventDefault()

.capture 添加事件侦听器时使用事件捕获模式，就是谁有该事件修饰符，就先触发谁

.self 只会触发自己范围内的事件，不包括子元素

.once 事件只会触发一次

.passive 不阻止事件的默认行为



##### 键盘修饰符

.enter回车键

.tab 制表键

.esc 返回键

.space 空格键

.up 向上键

.down 向下键

.left 向左键

.right 向右键



##### 系统修饰符

.ctrl    .alt   .shift   .meta



#### v-on 可以绑定多个事件？

##### 1.绑定多个事件

​    键值对方式绑定多个事件

```javascript
<button v-on="{click: clickMethds, mousemove: mouseMethods}">按钮<button>
```

##### 2.一个事件绑定多个方法

​    逗号分隔

```javascript
<button @click="click1,click2"></button>
```



#### vue初始化页面闪动问题

在vue初始化之前，由于div是不归vue管的，所以代码在还没有解析的情况下会容易出现花屏现象，看到类似于{{message}}的字样，虽然一般情况下这个时间很短暂，但是还是有必要让解决这个问题的。

```javascript
//css
[v-cloak] {    display: none;}

//如果没有彻底解决问题，则在根元素加上
style="display: none;" :style="{display: 'block'}"


```



#### v-model 实现原理

`v-model` 在内部为不同的输入元素使用不同的 property 并抛出不同的事件

text 和 textarea 元素使用 value property 和 input 事件；
checkbox 和 radio 使用 checked property 和 change 事件；
select 字段将 value 作为 prop 并将 change 作为事件。
简单点来说就是表单 `input` 加 `value` 的语法糖

#### --computed,watch

优先级

原理

##### computed

- 它支持缓存，只有依赖的数据发生了变化，才会重新计算

- 不支持异步，当Computed中有异步操作时，无法监听数据的变化

- computed的值会默认走缓存，计算属性是基于它们的响应式依赖进行缓存的，也就是基于data声明过，或者父组件传递过来的props中的数据进行计算的。

- 如果一个属性是由其他属性计算而来的，这个属性依赖其他的属性，一般会使用computed

- 如果computed属性的属性值是函数，那么默认使用get方法，函数的返回值就是属性的属性值；在computed中，属性有一个get方法和一个set方法，当数据发生变化时，会调用set方法。

  

```javascript
<div>{{nameData('李')}}</div>

computed:{
    money(){
        get() {
             return 999
        },
        set(value) {
             var val = value.split("元")
             return val
         }
    },
    //传参
    nameData(){
        return function(val){
            return val
        }
    }
}
```



##### watch

- 它不支持缓存，数据变化时，它就会触发相应的操作

- 支持异步监听

- 监听的函数接收两个参数，第一个参数是最新的值，第二个是变化之前的值

- 当一个属性发生变化时，就需要执行相应的操作

- 监听数据必须是data中声明的或者父组件传递过来的props中的数据，当发生变化时，会触发其他操作，函数有两个的参数：

  ​    immediate：组件加载立即触发回调函数

  ​    deep：深度监听，发现数据内部的变化，在复杂数据类型中使用，例如数组中的对象发生变化。需要注意的是，deep无法监听到数组对象内部的变化。

  ```javascript
  watch:{
      table(newVal,oldVal){
          console.log(newVal)
      },
      form:{   
          handler(newVal,oldVal){
              console.log(newVal,oldVal)
          },
          immediate:true,//第一次绑定时不会监听，值变化才会执行，如果要立即执行设置immediate:true
          deep:true  //深度监听对象变化
      }
  }
  ```


应用场景：

当需要进行数值计算,并且依赖于其它数据时，应该使用 computed，因为可以利用 computed 的缓存特性，避免每次获取值时都要重新计算。

当需要在数据变化时执行异步或开销较大的操作时，应该使用 watch，使用 watch 选项允许执行异步操作 ( 访问一个 API )，限制执行该操作的频率，并在得到最终结果前，设置中间状态。这些都是计算属性无法做到的



#### computed、methods的区别

1. computed会基于响应数据缓存，methods不会缓存。

2. 调用方式不一样，computed是属性调用，methods是函数调用。

3. computed中的成员可以只定义一个函数作为属性，也可以定义get/set变成可读写的属性，这点是methods不可以做到的。

   

#### 过滤器

##### 作用 

用来过滤模型数据，在显示之前进行数据处理和筛选。

- 在插值表达式和 v-bind 中使用
- 局部过滤器优先于全局过滤器
- 一个表达式可以使用多个过滤器,过滤器之间需要用管道符“|”隔开。其执行顺序从左往右

##### 分类

- 全局过滤器

  Vue.filter(过滤器ID，过滤器函数)

  ```javascript
  <h3>{{8|addZero}}</h3>
  //如果data小于10，给十位补0，否则返回data
  Vue.filter('addZero',function(data){
       return data<10?'0'+data:data  
  });
  ```

  

- 局部过滤器

  filters:{

  ​     过滤器ID:(过滤器参数1，过滤器参数2...)=>{

  ​           函数回调

  ​        }

  }

  ```javascript
  <h3>{{12.3456789|number(3)}}</h3>
  
  filters:{
       number:(data,n)=>{
         return data.toFixed(n)
       }
   }
  ```

  

##### 使用场景

单位转换、数字打点、文本格式化、时间格式化之类,比如要实现将30000 => 30,000





#### vue组件间通信方式

1.props / $emit 适用 父子组件通信

2.ref 与 parent /children 适用 父子组件通信

-   ref：如果在普通的 DOM 元素上使用，引用指向的就是 DOM 元素；如果用在子组件上，引用就指向组件实例
-   parent /children：访问父 / 子实例

3.EventBus (emit/on） 适用于 父子、隔代、兄弟组件通信

```javascript
//eventBus.js
import Vue from 'vue'
export const bus =new Vue({})

//parent.vue

import {bus} from '@/tools/eventBus.js'
handleClick(val){
    bus.$emit('close',val)
}

//child.vue

mounted(){
    bus.$on('close',(val)=>{
        console.log(val)
    })
}



```

4.attrs/listeners 适用于 隔代组件通信

5.provide / inject 适用于 隔代组件通信

​     祖先组件中通过 provider 来提供变量，然后在子孙组件中通过 inject 来注入变量。provide / inject API 主要解决了跨级组件间的通信问题，不过它的使用场景，主要是子组件获取上级组件的状态，跨级组件间建立了一种主动提供与依赖注入的关系

6.Vuex 适用于 父子、隔代、兄弟组件通信



#### slot插槽

##### 定义：

实质是对子组件的扩展，通过`<slot>`插槽向子组件内部指定位置传递内容

##### 作用：

 使复用组件的内容结构和数据动态化，从而增强组件的可复用性

##### 分类：

###### 匿名插槽

```javascript
//child
<div>
    <slot></slot>
</div>

//parent
<Child>
    <p>插槽内容</p>
</Child>


```



具名插槽

v-slot: 可以简化成#

```javascript
//child
<div>
    <slot name="one">内容</slot>
</div>

//parent
<Child>
     <template #one>
         <p>插槽内容</p>
     </template>
      //或
     <template v-slot:one>
         <p>插槽内容</p>
     </template>
</Child>
```

作用域插槽

```javascript
//child
<div>
    <slot name="name" :a="1">内容</slot>
</div>

//parent
<Child>
     <template #one="scope">
         <p>{{scope.a}}</p>
     </template>
      //或
     <template v-slot:one="scope">
         <p>{{scope.a}}}</p>
     </template>
</Child>
```



#### v-if,v-show 区别

 1.渲染条件  v-if条件不成立时，删除dom元素，v-show通过display 控制显示隐藏

 2.性能区别  v-if有更高的切换开销，v-show有更高的初始渲染开销

 3.生命周期  v-if每切换一次会重新走一次生命周期，v-show只有页面初始化时走一次生命周期 

 4.v-show不支持<template> 语法：因为v-show是通过display来控制标签进行渲染的，但是template 标签在vue解析后是不会显示在页面上的 ，是虚拟Dom ，所以不可以，v-if是条件渲染，只要满足v-if后的条件就可以完成渲染

使用场景：需要频繁切换使用v-show,  运行时很少改变条件，不需要频繁切换条件的场景使用v-if



#### export 与export default 区别

1.export与export default均可用于导出常量、函数、文件、模块等 

2.在一个文件或模块中，export、import可以有多个，export default仅有一个

3.通过export方式导出，在导入时要加{ }，export default则不需要

4.输出单个值，使用export default；输出多个值，使用export
    export default与普通的export不要同时使用



#### extend 有什么作用

作用是扩展组件生成一个构造器,通常会与 `$mount` 一起使用。

```javascript
<div id="mount-point"></div>
// 创建构造器
var Profile = Vue.extend({
  template: <p>{{firstName}} {{lastName}} aka {{alias}}</p>
  data: function () {
    return {
      firstName: Walter,
      lastName: White,
      alias: Heisenberg
    }
  }
})
// 创建 Profile 实例，并挂载到一个元素上。
new Profile().$mount('#mount-point') //<p>Walter White aka Heisenberg</p>

```



#### assets和static的区别

##### 相同：

1. 都是用来放静态资源的
2. 项目中所需要的资源文件图片，字体图标，样式文件等都可以放在这两个文件下

##### 不同：

1、目录结构不同

2、assets中的资源会被webpack处理，打包后会在dist中合并成一个文件；static中的资源不会被webpack处理，打包后直接复制到dist（默认是dist/static）下

3、推荐assets中存放自己的资源（css、images、utils等），static中放第三方资源（pdf.js、iconfont等）

4、动态绑定中，assets的图片会加载失败，因为webpack使用commonJS规范，需要使用require引入图片（可以通过import的方式引入）





#### Vue中 $nextTick 原理及作用

$nextTick在下次DOM更新循环结束之后执行延迟回调。在修改数据之后立即使用这个方法，获取更新后的DOM。主要思路就是采用微任务优先的方式调用异步方法去执行 nextTick 包装的方法

只要观察到数据变化，Vue 将开启一个队列，并缓冲在同一事件循环中发生的所有数据改变。如果同一个 watcher 被多次触发，只会被推入到队列中一次。这种在缓冲时去除重复数据对于避免不必要的计算和 DOM 操作上非常重要。然后，在下一个的事件循环“tick”中，Vue 刷新队列并执行实际 (已去重的) 工作。Vue 在内部尝试对异步队列使用原生的 Promise.then 和MessageChannel，如果执行环境不支持，会采用 setTimeout(fn, 0)代替



使用场景：

要在更新完数据之后，需要对新DOM做一些操作，当时无法对新DOM进行操作，因为这时还没有重新渲染。



#### 对mixins的理解

##### 是什么

vue提供的一种混合机制，能够更好的实现组件功能复用，混合对象（mixins）可以包含任意组件选项（data、created、mounted、methods、filters等），组件引入后相关选项会进行合并，相当于引入后，父组件各属性进行扩充；

##### 合并

1. 对于data定义属性，组件中定义属性覆盖mixins中同名字段
2. 对于created、mounted等生命周期函数，mixins中生命周期函数优先执行（执行顺序按mixins中顺序），再执行组件中生命周期函数
3. 对于methods中的同名方法，组件内的方法覆盖mixins中的方法
4. 对于相同的computed属性，组件的computed属性覆盖mixins内的computed属性
5. 而对于相同的watch监听，mixins中的watch监听先执行

生命周期遵从“从外到内，再从内到外，mixins先于组件”的原则

##### 使用

```javascript
//mixin.js

const mixin = {
    data() {
        return {
　　　　　　　　test: 'mixins变量覆盖组件内变量',
        }
    },
    created() {
        console.log('created: from mixins');
    },
    mounted() {
        console.log('mounted: from mixins');
    }
}
export default mixin


//组件引入mixin
import mixin from '@/mixins/mixin';
　export default {
　　data(){
　　　　return {
　　　　　　test: '组件变量覆盖mixins变量'
　　　　}
　　},
　　mixins: [mixin],　
　　created() {
　　　　console.log(this.test)
　　　　console.log('created: from 当前组件')
　　},
　　mounted() {
　　　　console.log('mounted: from 当前组件')
　　},
　}

//打印顺序

created: from mixins
组件变量覆盖mixins变量
created: from 当前组件

mounted: from mixins
mounted: from 当前组件


```



#### 路由懒加载

##### 使用懒加载原因

在单页应用中，如果没有应用懒加载，运用 webpack 打包后的文件将会异常的大，造成进入首页时，需要加载的内容过多，延时过长，不利于用户体验，而运用懒加载则可以将页面进行划分，需要的时候加载页面，可以有效的分担首页所承担的加载压力，减少首页加载用时

非懒加载

```javascript
import List from '@/components/list.vue'
const router = new VueRouter({
  routes: [
    { path: '/list', component: List }
  ]
})
```



##### 1.箭头函数+require动态加载

​    1：vue-router配置路由，使用vue的异步组件技术，可以实现懒加载，此时一个组件会生成一个js文件。
​    2：component: resolve => require(['放入需要加载的路由地址'], resolve)

```javascript
{      
    path: '/problem',
    name: 'problem',
    component: resolve => require(['../pages/home/problemList'], resolve)    
}
```



##### 2.箭头函数+import动态加载

​     1：直接将组件引入的方式，import是ES6的一个语法标准，如果需要浏览器兼容，需要转化成es5的语法。

​	 2：上面声明导入，下面直接使用

```javascript
import Vue from 'vue';
import Router from 'vue-router';

const Foo = () => import('../components/Foo')


export default new Router({
    routes: [
        {
            path: '/Foo',
            name: 'Foo',
            component: Foo
        }
    ]
})

```

##### 3.webpack提供的require.ensure()实现懒加载

多个路由指定相同的chunkName，会合并打包成一个js文件。

```javascript
// r就是resolve
const List = r => require.ensure([], () => r(require('@/components/list')), 'list');
// 路由也是正常的写法  这种是官方推荐的写的 按模块划分懒加载 
const router = new Router({
  routes: [
  {
    path: '/list',
    component: List,
    name: 'list'
  }
 ]
}))
```



#### vue性能优化

##### 1.编码阶段

- ​    避免同时使用v-if,v-for,使用v-for时必须加上key，元素绑定事件时使用事件代理
- ​    图片懒加载
- ​    路由懒加载
- ​    防抖，节流
- ​    使用keep-alive 
- ​    UI框架按需加载
- 长列表滚动到可视区域动态加载

##### 2.SEO优化

- 预渲染
- 服务端渲染SSR

##### 3.打包优化

- 图片资源的压缩
- 压缩代码
- 使用cdn加载第三方模块



#### vue-router

##### 路由模式

###### hash

使用 URL hash 值来作路由。支持所有浏览器，包括不支持 HTML5 History Api 的浏览器；

###### history 

依赖 HTML5 History API 和服务器配置。具体可以查看 HTML5 History 模式；

###### abstract 

支持所有 JavaScript 运行环境，如 Node.js 服务器端。如果发现没有浏览器的 API，路由会自动强制进入这个模式.

##### 路由模式实现原理

###### hash实现原理

`location.hash`的值就是URL中`#`后面的内容

- URL中的hash值只是客户端的一种状态，当向服务器发送请求时，但不会被包含在 HTTP 请求中
- hash值的改变，都会在浏览器的访问历史中增加一个记录，因此在开发时，也可以通过浏览器的回退和前进按钮来控制hash的切换
- 也可以通过href属性来改变URL的hash值，或者使用`location.hash`进行赋值，改变URL的hash值

- 可以使用hashchange事件来监听hash值的变化，从而对页面进行跳转

###### history 实现原理

HTML5提供了History API来实现URL的变化，其中最主要的两个API有以下两个
history.pushState()和history.replaceState()。这两个API可以在不进行刷新的情况下，操作浏览器的历史记录。唯一不同的是，前者是新增一个历史记录，后者是直接替换当前的历史记录。

因为我们的应用是个单页客户端应用，如果后台没有正确的配置，会返回404，所以要在服务器增加一个覆盖所有情况的候选资源：如果URL匹配不到任何静态资源，则应该返回同一个index.html页面，这个页面就是app依赖的页面。



##### 路由跳转方式

###### 声明式

   使用router-link 标签跳转

###### 编程式

​    使用js方式 this.$router.push()

###### 路由中name的作用

1.组件自身的递归调用，就是在当前组件中，调用组件自己

2.使用vue.js官方提供的调试工具调试时，可以看到组件的名称，更好地定位

##### 路由传参

###### 方法 一：

```
 this.$router.push({
          path: `/describe/${id}`,
   })
// 路由配置         
  {
     path: '/describe/:id',
     name: 'Describe',
     component: Describe
   }
 //获取参数
 this.$route.params.id
```

###### 方法二：

```
this.$router.push({
          name: 'Describe',
          params: {
            id: id
          }
    })
 // 获取参数
this.$route.params.id
```

###### 方法三：(url拼接)

```
this.$router.push({
          path: '/describe',
          query: {
            id: id
       }
 })
 // 获取参数
 this.$route.query.id
```



##### route、router区别

###### route

route 是一个局部的路由信息对象，每一个路由都会有一个route对象，包含一些基本信息如name、meta、path、hash、query、params、fillPath、metched

###### router

router通过Vue.use(VueRouter)和VueRouter构造函数得到一个router的全局实例对象，包含一些属性和方法如 push、go、back、replace



##### vue-router钩子函数

###### 1.全局导航钩子

beforeEach(to,from,next)前置守卫

```javascript
router.beforeEach((to, from, next) => {
 let token =localStorage.getItem(token)// 判断是否登录的存储信息
    if (!token) {  
        if (to.path == '/') { 
            //如果是登录页面路径，就直接next()      
            next();    
        } else { 
            //不然就跳转到登录      
            Message.warning("请重新登录！");     
            window.location.href = Vue.prototype.$loginUrl;    
        }  
    } else {    
        return next();  
    }
})
```



afterEach(to,from)后置钩子

```javascript
router.afterEach((to,from) => {
  console.log(to);//到达的路由
  console.log(from);//离开的路由
})

```



###### 2.路由独享钩子

beforeEnter

```javascript
const router = new VueRouter({
  routes: [
    {
      path: '/foo',
      component: Foo,
      beforeEnter: (to, from, next) => {
        // ...
      }
    }
  ]
})
```

###### 3.组件内导航钩子

beforeRouteEnter

```javascript
beforeRouteEnter (to, from, next) {
  // 不能获取组件实例 `this`
  // 因为当守卫执行前，组件实例还没被创建
}
```

beforeRouteUpdate

```javascript
beforeRouteUpdate (to, from, next) {
  // 在当前路由改变，但是该组件被复用时调用
  // 可以访问组件实例 `this`
}
```

beforeRouteLeave

```javascript
beforeRouteLeave (to, from, next) {
  // 导航离开该组件的对应路由时调用
  // 可以访问组件实例 `this`
}
```



##### 完整的导航解析流程

1. 导航被触发。
2. 在失活的组件里调用 `beforeRouteLeave` 守卫。
3. 调用全局的 `beforeEach` 守卫。
4. 在重用的组件里调用 `beforeRouteUpdate` 守卫(2.2+)。
5. 在路由配置里调用 `beforeEnter`。
6. 解析异步路由组件。
7. 在被激活的组件里调用 `beforeRouteEnter`。
8. 调用全局的 `beforeResolve` 守卫(2.5+)。
9. 导航被确认。
10. 调用全局的 `afterEach` 钩子。
11. 触发 DOM 更新。
12. 调用 `beforeRouteEnter` 守卫中传给 `next` 的回调函数，创建好的组件实例会作为回调函数的参数传入。

#### Vuex

##### 对vuex的理解

vuexs是多个组件，共享，同一个数据的状态管理工具
vuex适用于大型单页应用，简单的应用使用 Vuex 可能是繁琐冗余的

Vuex主要用于解决组件之间同一状态的共享问题，它能把组件的共享状态抽取出来，当做一个全局单例模式进行管理。 这样不管你在何处改变状态，都会通知使用该状态的组件做出相应修改。即Vuex采用集中式存储管理应用的所有组件的状态 这里的关键在于集中式存储管理。 这意味着本来需要共享状态的更新是需要组件之间的通讯，而现在有了Vuex，组件就都和store通讯了



##### vuex优点

- 能够在vuex中,集中管理共享的数据,易于开发和后期维护；
- Vuex 的状态存储是响应式的，当 Vue 组件从 store中读取状态的时候，若 store 中的状态发生变化，能够触发响应式的渲染页面更新，那么相应的组件也会相应地得到高效更新。
- js 原生的数据对象写法, 比起 localStorage 不需要做转换, 使用方便
- 限定了一种可预测的方式改变数据, 避免大项目中, 数据不小心的污染

##### vuex缺点

刷新浏览器，vuex中的state会重新变为初始状态 

解决方案vuex-along ,`vuex-persistedstate`



##### vuex使用场景

登录状态，用户名称、头像、地理位置信息、商品的收藏、购物车中的物品等



##### 1 state(特性)

- state 用于存放状态
- state里的数据是响应式的，state中的数据改变，对应组件内的数据也会改变
- state通过mapState把全局的state和getter映射到当前组件的计算属性中

##### 2 mutation(特性)

同步的，修改状态的唯一方法是提交mutation

##### 3 action(特性)

类似于mutation,不同的是action提交的是mutation，不是直接变更状态，可以包含任意异步操作

##### 4 getter   

 不会修改state中的数据，只是读取操作，类似与计算属性

##### 5 module

模块化状态管理

##### 使用

```javascript
store.js

export defalut new Vuex.Store({
  state:{
     count:0
  },
//同步操作,使用commit
  mutations:{
    add(state,step){
      state.count+=step
   },
    sub(state,step){
      state.count-=step
    }
 },
//异步操作 1秒后修改使用dispatch
  actions:{
    subAsync(context,step){
      setTimout(()=>{
         context.commit('sub',step)
      },1000)
    }
 },
//读取操作
 getters:{
    showNum(state){
      return '最新数据'+state.count
    }
  }
})

```



```javascript
//组件内
//使用state
<div>{{$store.state.count}}</div>
<div>{{count}}</div>
//使用mutation
<button @click="handle">+4</button>
<button @click="add(3)">+4</button>
//使用actions
<button @click="handle2">+4</button>
<button @click="subAsync(3)">+4</button>
//使用getter



使用state中值方式

1.   this.$store.state.count

2.   import  { mapState }  from 'vuex'

       computed:{

       ...mapState (['count'])

      }
使用mutation中值方式
1. methods:{
        handle(){
            this.$store.commit('add',4)
        }
   }
2. import  { mapMutations }  from 'vuex'
   methods:{
       ...mapMutations(['add'])
   }
使用action中的方式
1. methods:{
        handle2(){
            this.$store.dispatch('subAsync',4)
        }
   }
2. import  { mapActions }  from 'vuex'
   methods:{
       ...mapActions(['subAsync'])
   }
使用getter中值方式
1. this.$store.getters.showNum
2. import  { mapActions }  from 'vuex'
   computed:{
       ...mapGetters(['showNum'])
   }
```



#### 对多页面的理解

##### 是什么

MPA  MultiPage Application，指有多个独立页面的应用(多个html),每个页面必须重复加载js,css等相关资源，多页应用跳转需要整页资源刷新



##### 对比

![image-20220718014454972](C:\Users\g5988\AppData\Roaming\Typora\typora-user-images\image-20220718014454972.png)

#### 对SPA单页面的理解

##### 是什么：

SPA（ single page application ）指只有一个主页面的应用(一个html页面)，一开始只需要加载一次js,css相关资源

##### 优点：

1.内容的改变不需要重新加载整个页面，避免了不必要的跳转和重复渲染，相对减轻了服务器的压力

2.前后端职责分离，架构清晰，前端进行交互逻辑，后端负责数据处理

##### 缺点：

1.初次加载耗时多

2.由于单页应用在一个页面中显示所有的内容，所以不能使用浏览器的前进后退功能

3.由于所有的内容都在一个页面中动态替换显示，所以不利于搜索引擎检索

#### SPA首屏加载速度慢？

首屏时间，指的是浏览器从响应用户输入网址地址，到首屏内容渲染完成的时间，此时整个网页不一定要全部渲染完成，但需要展示当前视窗需要的内容；

##### 加载慢的原因

- 网络延时问题
- 资源文件体积是否过大
- 资源是否重复发送请求去加载了
- 加载脚本的时候，渲染内容堵塞了

##### 常见的SPA首屏优化方式

- 减小入口文件积
- 静态资源本地缓存
- UI框架按需加载
- 图片资源的压缩
- 组件重复打包
- 开启GZip压缩
- 使用SSR



#### 对SSR的理解

##### 是什么

Server-Side-Rendering意为服务端渲染

指由服务侧完成页面的Html结构拼接的页面处理技术，发送到浏览器，然后为其绑定状态和事件，成为完全可交互页面的过程

##### web 3个阶段发展史

- 传统服务端渲染SSR

- 单页面应用SPA

- 服务端渲染SSR

  

###### 传统web开发

网页内容在服务端渲染完成，一次性传输到浏览器

![image-20220715120103557](C:\Users\g5988\AppData\Roaming\Typora\typora-user-images\image-20220715120103557.png)



单页面SPA

单页面应用页面内容由JS渲染出来，成为客户端渲染

![image-20220715120308836](C:\Users\g5988\AppData\Roaming\Typora\typora-user-images\image-20220715120308836.png)

服务端渲染SSR

SSR解决方案，后端渲染出完整的首屏dom结构返回，前端拿到的内容包括首屏及完整的spa结构，应用激活后依然按照spa方式运行



![image-20220715120339640](C:\Users\g5988\AppData\Roaming\Typora\typora-user-images\image-20220715120339640.png)



#### Vue如何检测数组变化

1. 数组考虑性能原因没有用 defineProperty 对数组的每一项进行拦截，
2. 而是选择对7种数组（push,shift,pop,splice,unshift,sort,reverse）方法进行重写（AOP切片思想）
3. 所以在 Vue 中修改数组的索引和长度无法监控到



#### Vue 框架怎么实现对象和数组的监听

#### Vue 中的 key 有什么作用

1. key 是 Vue中vnode的唯一标记，通过这个key，我们的[diff操作]可以[更准确]、[更快速]。
2. (我的理解:通过 sameNode函数对比key值，避免了就地复用的情况，所以会更加的准确)
3. 更快速：利用key的唯一性生成map对象，来获取对应节点，比遍历方式更快

#### 涉及视图更新，你会用什么方式来变更数组

1.Vue.set()

2.数组splice方法   Array.prototype.splice

3.this.$forceUpdate()强制刷新

4.es6 "…"扩展运算符

#### 为什么 Vue 数据改变页面也会同步更新

#### Vue 是如何追踪数据发生变化的

在 Vue 中当我们把一个普通的 JS 对象作为 data 传入 Vue 实例，Vue2.x 对这个数据初始化时将遍历这个对象所有的属性，并使用 JS 的原生特性 Object.defineProperty 把这些属性全部转为 getter\setter。这些 getter\setter 对用户来说是不可见的，他们可以在属性被访问和修改时通知变更。同时每个组件实例都对应一个 watcher 实例，它会在组件渲染的过程中把“接触”过的数据属性记录为依赖。之后当依赖项的 setter 触发时，会通知 watcher，从而使它关联的组件重新渲染

#### 为什么有些数组的数据变更不能被 Vue 监测到

简单来说，我们操作数组的一些动作 arr[2] = 'xxx' / arr.length = 2 或者是调用 Array.prototype 上挂载的部分方法并不能触发这个属性的 setter

#### 为什么 Splice 方法也可以触发状态更新

因为 Vue2.x 将数组的 7 个常用方法 push、pop、shift、unshift、splice、sort、reverse 进行了重写，所以通过调用包装之后的数组方法就能够被 Vue 监测到

#### 为什么 Object.defineProperty 明明能监听到数组值的变化，而 Vue 却没有实现

因为 Vue 是对数组元素进行了监听，而没有对数组本身的变化进行监听

- 性能原因的考量，给每一个数组元素绑定上监听，实际消耗很大而受益并不大

- 对数据的操作更常用的操作数组的方法是使用数组原型上的一些方法如 push、shift 等来操作数组。

- Object.defineProperty是对象上的方法，用来对数组的下标进行检测，会改变数据本来的性质

  

#### Vue2.x 监测数组变更的两条限制：不能监听利用索引直接设置一个数组项，不能监听直接修改数组的长度，是因为 defineProperty 的限制么

是的。Object.defineProperty 对于数组变化监听的表现与 Vue2.x 还是有不同的，比如 Object.defineProperty 可以监听到通过索引直接修改数组项，当然也不是说 Object.defineProperty 可以完全监听数组的变化，像直接修改数组的长度或者 push\pop 之类的方法还是不能触发 setter 的

#### Vue 为什么不能通过下标操作数组或者改变数组的长度来触发视图更新

数组的length不能设置getter和setter



#### 对于 Vue 监测对象变化有什么要注意的

#### vue3如何监听的

Vue3 不再采用 defineProperty 的方式来进行监听而是采用 Proxy 的方式， Proxy 对象用于创建一个对象的代理，从而实现基本操作的拦截和自定义（如属性查找、赋值、枚举、函数调用等）。 当异步触发 Model 里的数据变化时，都会经过 Proxy 这一层，在这里则可以监听数组以及各种数据类型的变化，无论是数组下标赋值引起变化还是数组方法引起变化，都可以被监听到，也可以避开监听数组每个属性下造成的性能问题



#### 如何保存当前页面的状态



## 