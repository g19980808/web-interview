## react

#### 组件通信

```javascript
//父组件
const GlobalContext=React.createContext()

return (
    <GlobalContext.Provider value={{
    	name:'dy',
    	changeInfo:(val)=>{
    		console.log(val)
         }
    }}>
        <div>
        	<Child></Child>
        </div>
    </GlobalContext.Provider>
       
)

//子组件
const value=useContext(GlobalContext)

return (
    <GlobalContext.Consumer>
    	{
            (value)=>{
    			return <button onClick={()=>{
                            value.changeInfo(1)
                        }}></button>
            }
        }
    </GlobalContext.Consumer>
    
)

```





#### 生命周期

componentWillMount

componentDidMount

#### hooks

##### useState()保存组件状态

```javascript
import React,{useState} from 'react'
const [name,setName]=useState('xiaoming')    // name  => 'xiaoming'
const [list,setList]=useState(['a','b','c'])  //list  => ['a','b','c']
console.log(name)  //'ww'
console.log(setA) 


//清空name
setName('')
//push list
setList([...list,name])

<button onClick={()=>{
    setName('lisi')
}}></button>


```

##### useEffect() 处理副作用

useLayoutEffect()

一个组件可以使用多个useEffect()

```javascript
import React,{useEffect} from 'react'
useEffect(()=>{},[依赖的状态])

function Child (prop){
    
    useEffect(()=>{
        axios({}).then(res=>{})
    },[])

    useEffect(()=>{
        window.onresize =()=>{
            console.log('111')
        }
        
        var timer=setInterval(()=>{
            console.log('222')
        })
        
        return ()=>{
            //return函数无依赖时销毁调用
            //有依赖时更新调用
            
            window.onresize=null
            clearInterval(timer)
        }
    },[])
    
    
    return (
    	<div>Child</div>
    )  
}

```



##### useCallback()记忆函数

useCallback(fn,[])

防止因为组件重新渲染，导致方法被重新创建，起到缓存作用

```javascript
import React,{useCallback}
const handleClick= useCallback((event)=>{
    //操作
},[依赖])
```

##### useMeno()记忆组件

类似useCallback()

useMeno(()=>fn,[依赖])

```javascript
useMeno(()=>()=>{
    
},[])
```



##### useRef()

1.获取dom元素或组件实例  2.可以保存临时变量

```javascript
//绑定dom
const text =useRef()
<button ref="text" onClick={()=>{
    console.log(text.current.value)
    text.current.value=""
}}></button>

//保存临时变量
var count =useRef(0)
<button onClick={()=>{
    count.current++
}}></button>
```

##### useContext()

通信,减少组件层级

```javascript
//父组件
const GlobalContext=React.createContext()

return (
    <GlobalContext.Provider value={{
    	name:'dy',
    	changeInfo:(val)=>{
    		console.log(val)
         }
    }}>
         <div>
        	<Child></Child>
        </div>
    </GlobalContext.Provider>
    
    
)

//子组件
const value=useContext(GlobalContext)

return (
     <button onClick={()=>{
         value.changeInfo(1)
      }}></button> 
)

```

##### useReducer()

```javascript
import React,{useReducer} from 'react'

const reducer = (preState,action)=>{
    let newState={...preState}
    switch(action.type){
        case 'sub':
            newState.count--
            return newState
        case 'add':
            newState.count++
            return newState
        default:
            return preState
    }
    
}
const intialState = {
    count:0
}

export default function App(){
    const [state,dispatch] =useReducer(reducer,intialState)
    return (
        <div>
        	<button onClick={()=>{
        		dispatch({
                    type:"sub"
                })
             }}>-</button>
        		{state.count}
        	<button onClick={()=>{
        		dispatch({
                    type:"add"
                })
             }}>+</button>
        </div>
    )
}





```

```javascript
//App
import React,{useReducer} from 'react'

const reducer = (preState,action)=>{
    let newState={...preState}
    switch(action.type){
        case 'change-a':
            newState.a =action.value
            return newState
        case 'change-b':
            newState.b =action.value
            return newState
        default :
            return preState
    }
    
}
const intialState = {
    a:1,
    b:2
}


const GlobalContext =React.reactContext()
export default function App(){
    const [state,dispatch] =useReducer(reducer,intialState)
    return (
        <GlobalContext.Provider value={
        	{
        		state,
        		dispatch
             }
        }>
        	<div>
                <Child1 />
                <Child2 />
                <Child3 />
            </div>
        </GlobalContext.Provider>

    )
}


//Child1
function Child1(){
    const {dispatch} =useContext(GlobalContext)
    return (
    	  <div>
        <button onClick={()=>{
        		dispatch({
                    type:"change-a",
                    value:'222'
                })
             }}>改变a</button>
        <button onClick={()=>{
        		dispatch({
                    type:"change-b",
                    value:'333'
                })
             }}>改变b</button>
          </div>
    )
}

//Child2
function Child2(){
    const {state} =useContext(GlobalContext)
    return (
    	  <div>
		      {state.a}
          </div>
    )
}
//Child3
function Child3(){
    const {state} =useContext(GlobalContext)
    return (
    	  <div>
			{state.b}
          </div>
    )
}



```

##### 自定义hooks

   复用js逻辑

```javascript
function useCinemaList (list,id){
    const [cinemaList,setLinemaList] = useState([])
    const getCinemaList =  list.filter(item=>item==id)
    return {
        getCinemaList
    }
}

export default function App (){
    const {getCinemaList} =useCinemaList([1,2,3],2)
}
```



#### 路由

```javascript
npm i react-router-dom -S

import {HashRouter,Route} from 'react-router-dom'
import Films from'./Films'
import Cinemas from'./Cinemas'
import Center from'./Center'
return (
	<div>
    	<HashRouter>
    		<Route path="/films" component={Films}></Route>
			<Route path="/cinemas" component={Cinemas}></Route>
			<Route path="/center" component={Center}></Route>
    	</HashRouter>
    </div>
)
```

