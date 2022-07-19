# vue3

## vue3新增特性

> - **Composition (组合) API**
> - setup
>   - ref 和 reactive
>   - computed 和 watch
>   - 新的生命周期函数
>   - provide与inject
>   - ...
> - 新组件
>   - Fragment - 文档碎片
>   - Teleport - 瞬移组件的位置
>   - Suspense - 异步加载组件的loading界面
> - 其它API更新
>   - 全局API的修改
>   - 将原来的全局API转移到应用对象
>   - 模板语法变化

## 创建vue3项目

#### 1、使用 vue-cli 创建

![1651047405569](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651047405569.png)

#### 2、使用 vite 创建

- vite 是一个由原生 ESM 驱动的 Web 开发构建工具。在开发环境下基于浏览器原生 ES imports 开发，
- 它做到了***本地快速开发启动***, 在生产环境下基于 Rollup 打包。
  - 快速的冷启动，不需要等待打包操作；
  - 即时的热模块更新，替换性能和模块数量的解耦让更新飞起；
  - 真正的按需编译，不再等待整个应用编译完成，这是一个巨大的改变。

![1651047462995](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651047462995.png)

### vue3---App.vue

> ![1651047535926](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651047535926.png)

**此处与vue2有所不同**

# Composition API(常用部分)

#### 1、setup

- 新的option, 所有的组合API函数都在此使用, <font color='red'>只在初始化时执行一次</font>
- 函数如果返回对象, 对象中的属性或方法, 模板中可以直接使用

**vue2 和 vue3 的区别**

![1651047568195](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651047568195.png)

![1651047588648](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651047588648.png)

#### 2、ref

- 作用: 定义一个数据的响应式
- 语法: const xxx = ref(initValue):
  - 创建一个包含响应式数据的引用(reference)对象
  - <font color='blue'>js中操作数据: xxx.value</font>
  - <font color='orange'>模板中操作数据: 不需要.value</font>
- 一般用来定义一个基本类型的响应式数据

![1651047634024](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1651047634024.png)

#### 3、reactive

- <font color='orange'>作用: 定义多个数据的响应式</font>
- c<font color='green'>onst proxy = reactive(obj): 接收一个普通对象然后返回该普通对象的响应式代理器对象</font>
- 响应式转换是“深层的”：会影响对象内部所有嵌套的属性
- <font color='green'>内部基于 ES6 的 Proxy 实现，通过代理对象操作源对象内部数据都是响应式的</font>

~~~
<template>
  <h2>name: {{state.name}}</h2>
  <h2>age: {{state.age}}</h2>
  <h2>wife: {{state.wife}}</h2>
  <hr>
  <button @click="update">更新</button>
</template>

<script>
/* 
reactive: 
    作用: 定义多个数据的响应式
    const proxy = reactive(obj): 接收一个普通对象然后返回该普通对象的响应式代理器对象
    响应式转换是“深层的”：会影响对象内部所有嵌套的属性
    内部基于 ES6 的 Proxy 实现，通过代理对象操作源对象内部数据都是响应式的
*/
import { reactive } from 'vue'

export default {
  setup () {
    /* 
    定义响应式数据对象
    */
    const state = reactive({
      name: 'tom',
      age: 25,
      wife: {
        name: 'marry',
        age: 22
      },
    })
    console.log(state, state.wife)

    const update = () => {
      state.name += '--'
      state.age += 1
      state.wife.name += '++'
      state.wife.age += 2
    }

    return {
      state,
      update,
    }
  }
}
</script>
~~~

> **操作代理对象时，会影响界面更新渲染**
>
> setup(){
>
> ​	const obj = {
>
> ​		name:'小明',
>
> ​		age:18,
>
> ​		cars:['奔驰','宝马','奥迪'],
>
> ​	},
>
> ​	// 把数据变为响应式的数据
>
> ​	// 返回的是一个Proxy代理对象，被代理的目标对象就是obj对象
>
> ​	const user = reactive(obj);
>
> ​	// 此时user为代理对象，obj为目标对象
>
> ​	**操作代理对象，目标对象中的数据也会随之变化，同时如果页面渲染的数据也会随之变化**
>
> }

## 比较Vue2与Vue3的响应式(重要)

### 响应式的原理

~~~
<script>
    // 目标对象
    const user={
      name:'王一博',
      age:20,
      songs:{
        name:'无感',
        time:2019
      }
    }
    // 把目标对象变为代理对象
    // 参数1：user--->target目标对象
    // 参数2：handler--->处理器对象，用来监视数据及数据的操作
    const proxyUser = new Proxy(user,{
      get(target,prop){
        // 通过代理对象获取目标对象的属性值
        console.log("get方法调用了~");
        return Reflect.get(target,prop);
      },
      set(target,prop,val){
        // 通过代理对象更新 / 添加目标对象的属性值
        console.log("set方法调用了~");
        return Reflect.set(target,prop,val);
      },
      deleteProperty(target,prop){
        // 删除目标对象的某个属性
        console.log("delete方法调用了~");
        return Reflect.deleteProperty(target,prop);
      }
    })
    // 通过代理对象获取目标对象中的某个属性值
    console.log(proxyUser.name);
    // 通过代理对象更新目标对象的某个属性值
    proxyUser.name='陈宇';
    // 通过代理对象向目标对象中添加一个新的属性
    proxyUser.gender="男";
    console.log(user);

    delete proxyUser.age;
    console.log(user);

    // 更新目标对象中某个属性对象的某个属性值
    proxyUser.songs.name='我的世界守则';
    console.log(user);
  </script>
~~~

#### 1、vue2的响应式

- 核心:
  - 对象: 通过defineProperty对对象的已有属性值的读取和修改进行劫持(监视/拦截)
  - 数组: 通过重写数组更新数组一系列更新元素的方法来实现元素修改的劫持

~~~
Object.defineProperty(data, 'count', {
    get () {}, 
    set () {}
})
~~~

- 问题
  - 对象直接新添加的属性或删除已有属性, 界面不会自动更新
  - 直接通过下标替换元素或更新length, 界面不会自动更新 arr[1] = {}

#### 2、vue3的响应式

- 核心:
  - 通过Proxy(代理): 拦截对data任意属性的任意(13种)操作, 包括属性值的读写, 属性的添加, 属性的删除等...
  - 通过 Reflect(反射): 动态对被代理对象的相应属性进行特定的操作
  - 文档:
    - https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Proxy
    - https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Reflect

```js
new Proxy(data, {
	// 拦截读取属性值
    get (target, prop) {
    	return Reflect.get(target, prop)
    },
    // 拦截设置属性值或添加新属性
    set (target, prop, value) {
    	return Reflect.set(target, prop, value)
    },
    // 拦截删除属性
    deleteProperty (target, prop) {
    	return Reflect.deleteProperty(target, prop)
    }
})

proxy.name = 'tom'
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Proxy 与 Reflect</title>
</head>
<body>
  <script>
    
    const user = {
      name: "John",
      age: 12
    };

    /* 
    proxyUser是代理对象, user是被代理对象
    后面所有的操作都是通过代理对象来操作被代理对象内部属性
    */
    const proxyUser = new Proxy(user, {

      get(target, prop) {
        console.log('劫持get()', prop)
        return Reflect.get(target, prop)
      },

      set(target, prop, val) {
        console.log('劫持set()', prop, val)
        return Reflect.set(target, prop, val); // (2)
      },

      deleteProperty (target, prop) {
        console.log('劫持delete属性', prop)
        return Reflect.deleteProperty(target, prop)
      }
    });
    // 读取属性值
    console.log(proxyUser===user)
    console.log(proxyUser.name, proxyUser.age)
    // 设置属性值
    proxyUser.name = 'bob'
    proxyUser.age = 13
    console.log(user)
    // 添加属性
    proxyUser.sex = '男'
    console.log(user)
    // 删除属性
    delete proxyUser.sex
    console.log(user)
  </script>
</body>
</html>
```

### setup细节

> - <font color='red'>setup执行的时机</font>
>   - 在beforeCreate之前执行(一次), 此时组件对象还没有创建
>   - 因此此时，<font color='green'>t</font><font color='green'>his是undefined, 不能通过this来访问data/computed/methods / props</font>
>   - 其实所有的composition API相关回调函数中也都不可以
> - <font color='red'>setup的返回值</font>
>   - 一般<font color='orange'>都返回一个对象</font>: **为模板提供数据**, 也就是模板中可以直接使用此对象中的所有属性/方法
>   - 返回对象中的属性会与data函数返回对象的属性合并成为组件对象的属性
>   - 返回对象中的方法会与methods中的方法合并成功组件对象的方法
>   - 如果有重名, setup优先
>   - 注意:
>   - 一般不要混合使用: methods中可以访问setup提供的属性和方法, 但在setup方法中不能访问data和methods
>   - setup不能是一个async函数: 因为返回值不再是return的对象, 而是promise, 模板看不到return对象中的属性数据
> - <font color='red'>setup的参数</font>
>   - setup(props, context) / setup(props, {attrs, slots, emit})
>   - props: 包含props配置声明且传入了的所有属性的对象
>   - attrs: 包含没有在props配置中声明的属性的对象, 相当于 this.$attrs
>   - slots: 包含所有传入的插槽内容的对象, 相当于 this.$slots
>   - emit: 用来分发自定义事件的函数, 相当于 this.$emit

```vue
<template>
  <h2>App</h2>
  <p>msg: {{msg}}</p>
  <button @click="fn('--')">更新</button>

  <child :msg="msg" msg2="cba" @fn="fn"/>
</template>

<script lang="ts">
import {
  reactive,
  ref,
} from 'vue'
import child from './child.vue'

export default {

  components: {
    child
  },

  setup () {
    const msg = ref('abc')

    function fn (content: string) {
      msg.value += content
    }
    return {
      msg,
      fn
    }
  }
}
</script>
```

```vue
<template>
  <div>
    <h3>{{n}}</h3>
    <h3>{{m}}</h3>

    <h3>msg: {{msg}}</h3>
    <h3>msg2: {{$attrs.msg2}}</h3>

    <slot name="xxx"></slot>

    <button @click="update">更新</button>
  </div>
</template>

<script lang="ts">

import {
  ref,
  defineComponent
} from 'vue'

export default defineComponent({
  name: 'child',

  props: ['msg'],

  emits: ['fn'], // 可选的, 声明了更利于程序员阅读, 且可以对分发的事件数据进行校验

  data () {
    console.log('data', this)
    return {
      // n: 1
    }
  },

  beforeCreate () {
    console.log('beforeCreate', this)
  },

  methods: {
    // update () {
    //   this.n++
    //   this.m++
    // }
  },

  // setup (props, context) {
  setup (props, {attrs, emit, slots}) {

    console.log('setup', this)
    console.log(props.msg, attrs.msg2, slots, emit)

    const m = ref(2)
    const n = ref(3)

    function update () {
      // console.log('--', this)
      // this.n += 2 
      // this.m += 2

      m.value += 2
      n.value += 2

      // 分发自定义事件
      emit('fn', '++')
    }

    return {
      m,
      n,
      update,
    }
  },
})
</script>
```

### reactive和ref细节

- 是Vue3的 composition API中2个最重要的响应式API
- <font color='red'>ref用来处理基本类型数据, reactive用来处理对象(递归深度响应式)</font>
- <font color='orange'>如果用ref对象/数组, 内部会自动将对象/数组转换为reactive的代理对象</font>
- **ref内部: 通过给value属性添加getter/setter来实现对数据的劫持**
- **reactive内部: 通过使用Proxy来实现对对象内部所有数据的劫持, 并通过Reflect操作对象内部数据**
- ref的数据操作: 在js中要.value, 在模板中不需要(内部解析模板时会自动添加.value)

```vue
<template>
  <h2>App</h2>
  <p>m1: {{m1}}</p>
  <p>m2: {{m2}}</p>
  <p>m3: {{m3}}</p>
  <button @click="update">更新</button>
</template>

<script lang="ts">
import {
  reactive,
  ref
} from 'vue'

export default {

  setup () {
    const m1 = ref('abc')
    const m2 = reactive({x: 1, y: {z: 'abc'}})

    // 使用ref处理对象  ==> 对象会被自动reactive为proxy对象
    const m3 = ref({a1: 2, a2: {a3: 'abc'}})
    console.log(m1, m2, m3)
    console.log(m3.value.a2) // 也是一个proxy对象

    function update() {
      m1.value += '--'
      m2.x += 1
      m2.y.z += '++'

      m3.value = {a1: 3, a2: {a3: 'abc---'}}
      m3.value.a2.a3 += '==' // reactive对对象进行了深度数据劫持
      console.log(m3.value.a2)
    }

    return {
      m1,
      m2,
      m3,
      update
    }
  }
}
</script>
```

## 计算属性与监视

- <font color='red'>computed函数:</font>
  - 与computed配置功能一致
  - 只有getter
  - 有getter和setter
- <font color='red'>watch函数</font>
  - 与watch配置功能一致
  - 监视指定的一个或多个响应式数据, 一旦数据变化, 就自动执行监视回调
  - **默认初始时不执行回调, 但可以通过配置immediate为true, 来指定初始时立即执行第一次**
  - **通过配置deep为true, 来指定深度监视**
- <font color='red'>watchEffect函数</font>
  - 不用直接指定要监视的数据, 回调函数中使用的哪些响应式数据就监视哪些响应式数据
  - 默认初始时就会执行第一次, 从而可以收集需要监视的数据
  - 监视数据发生变化时回调

```vue
<template>
  <h2>App</h2>
  fistName: <input v-model="user.firstName"/><br>
  lastName: <input v-model="user.lastName"/><br>
  fullName1: <input v-model="fullName1"/><br>
  fullName2: <input v-model="fullName2"><br>
  fullName3: <input v-model="fullName3"><br>

</template>

<script lang="ts">
/*
计算属性与监视
1. computed函数: 
  与computed配置功能一致
  只有getter
  有getter和setter
2. watch函数
  与watch配置功能一致
  监视指定的一个或多个响应式数据, 一旦数据变化, 就自动执行监视回调
  默认初始时不执行回调, 但可以通过配置immediate为true, 来指定初始时立即执行第一次
  通过配置deep为true, 来指定深度监视
3. watchEffect函数
  不用直接指定要监视的数据, 回调函数中使用的哪些响应式数据就监视哪些响应式数据
  默认初始时就会执行第一次, 从而可以收集需要监视的数据
  监视数据发生变化时回调
*/

import {
  reactive,
  ref,
  computed,
  watch,
  watchEffect
} from 'vue'

export default {

  setup () {
    const user = reactive({
      firstName: 'A',
      lastName: 'B'
    })

    // 只有getter的计算属性
    const fullName1 = computed(() => {
      console.log('fullName1')
      return user.firstName + '-' + user.lastName
    })

    // 有getter与setter的计算属性
    const fullName2 = computed({
      get () {
        console.log('fullName2 get')
        return user.firstName + '-' + user.lastName
      },

      set (value: string) {
        console.log('fullName2 set')
        const names = value.split('-')
        user.firstName = names[0]
        user.lastName = names[1]
      }
    })

    const fullName3 = ref('')

    /* 
    watchEffect: 监视所有回调中使用的数据
    */
    /* 
    watchEffect(() => {
      console.log('watchEffect')
      fullName3.value = user.firstName + '-' + user.lastName
    }) 
    */

    /* 
    使用watch的2个特性:
      深度监视
      初始化立即执行
    */
    watch(user, () => {
      fullName3.value = user.firstName + '-' + user.lastName
    }, {
      immediate: true,  // 是否初始化立即执行一次, 默认是false
      deep: true, // 是否是深度监视, 默认是false
    })

    /* 
    watch一个数据
      默认在数据发生改变时执行回调
    */
    watch(fullName3, (value) => {
      console.log('watch')
      const names = value.split('-')
      user.firstName = names[0]
      user.lastName = names[1]
    })

    /* 
    watch多个数据: 
      使用数组来指定
      如果是ref对象, 直接指定
      如果是reactive对象中的属性,  必须通过函数来指定
    */
    watch([() => user.firstName, () => user.lastName, fullName3], (values) => {
      console.log('监视多个数据', values)
    })

    return {
      user,
      fullName1,
      fullName2,
      fullName3
    }
  }
}
</script>
```

## 生命周期

**vue2生命周期**

 <img src="https://img-blog.csdnimg.cn/20210818115053154.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ExODc5MjYyNzE2OA==,size_16,color_FFFFFF,t_70" alt="img" style="zoom:35%;" />  

**vue3生命周期**

 ![img](https://img-blog.csdnimg.cn/20210818145640919.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ExODc5MjYyNzE2OA==,size_16,color_FFFFFF,t_70) 



> **与 2.x 版本生命周期相对应的组合式 API**
>
> - `beforeCreate` -> 使用 `setup()`
> - `created` -> 使用 `setup()`
> - `beforeMount` -> `onBeforeMount`
> - `mounted` -> `onMounted`
> - `beforeUpdate` -> `onBeforeUpdate`
> - `updated` -> `onUpdated`
> - `beforeDestroy` -> `onBeforeUnmount`
> - `destroyed` -> `onUnmounted`
> - `errorCaptured` -> `onErrorCaptured`

**新增的钩子函数**

组合式 API 还提供了以下调试钩子函数：

- onRenderTracked
- onRenderTriggered

```vue
<template>
<div class="about">
  <h2>msg: {{msg}}</h2>
  <hr>
  <button @click="update">更新</button>
</div>
</template>

<script lang="ts">
import {
  ref,
  onMounted,
  onUpdated,
  onUnmounted, 
  onBeforeMount, 
  onBeforeUpdate,
  onBeforeUnmount
} from "vue"

export default {
  beforeCreate () {
    console.log('beforeCreate()')
  },

  created () {
    console.log('created')
  },

  beforeMount () {
    console.log('beforeMount')
  },

  mounted () {
    console.log('mounted')
  },

  beforeUpdate () {
    console.log('beforeUpdate')
  },

  updated () {
    console.log('updated')
  },

  beforeUnmount () {
    console.log('beforeUnmount')
  },

  unmounted () {
     console.log('unmounted')
  },
  

  setup() {
    
    const msg = ref('abc')

    const update = () => {
      msg.value += '--'
    }

    onBeforeMount(() => {
      console.log('--onBeforeMount')
    })

    onMounted(() => {
      console.log('--onMounted')
    })

    onBeforeUpdate(() => {
      console.log('--onBeforeUpdate')
    })

    onUpdated(() => {
      console.log('--onUpdated')
    })

    onBeforeUnmount(() => {
      console.log('--onBeforeUnmount')
    })

    onUnmounted(() => {
      console.log('--onUnmounted')
    })
    
    return {
      msg,
      update
    }
  }
}
</script>
```

```vue
<template>
  <h2>App</h2>
  <button @click="isShow=!isShow">切换</button>
  <hr>
  <Child v-if="isShow"/>
</template>

<script lang="ts">
import Child from './Child.vue'
export default {

  data () {
    return {
      isShow: true
    }
  },

  components: {
    Child
  }
}
</script>
```

### 自定义hook函数

- 使用Vue3的组合API封装的可复用的功能函数

- 自定义hook的作用类似于vue2中的mixin技术

- 自定义Hook的优势: 很清楚复用功能代码的来源, 更清楚易懂

- 需求1: 收集用户鼠标点击的页面坐标

  hooks/useMousePosition.ts

```js
import { ref, onMounted, onUnmounted } from 'vue'
/* 
收集用户鼠标点击的页面坐标
*/
export default function useMousePosition () {
  // 初始化坐标数据
  const x = ref(-1)
  const y = ref(-1)

  // 用于收集点击事件坐标的函数
  const updatePosition = (e: MouseEvent) => {
    x.value = e.pageX
    y.value = e.pageY
  }

  // 挂载后绑定点击监听
  onMounted(() => {
    document.addEventListener('click', updatePosition)
  })

  // 卸载前解绑点击监听
  onUnmounted(() => {
    document.removeEventListener('click', updatePosition)
  })

  return {x, y}
}
```

```vue
<template>
<div>
  <h2>x: {{x}}, y: {{y}}</h2>
</div>
</template>

<script>

import {
  ref
} from "vue"
/* 
在组件中引入并使用自定义hook
自定义hook的作用类似于vue2中的mixin技术
自定义Hook的优势: 很清楚复用功能代码的来源, 更清楚易懂
*/
import useMousePosition from './hooks/useMousePosition'

export default {
  setup() {

    const {x, y} = useMousePosition()

    return {
      x,
      y,
    }
  }
}
</script>
```

- 利用TS泛型强化类型检查

- 需求2: 封装发ajax请求的hook函数

  hooks/useRequest.ts

```ts
import { ref } from 'vue'
import axios from 'axios'

/* 
使用axios发送异步ajax请求
*/
export default function useUrlLoader<T>(url: string) {

  const result = ref<T | null>(null)
  const loading = ref(true)
  const errorMsg = ref(null)

  axios.get(url)
    .then(response => {
      loading.value = false
      result.value = response.data
    })
    .catch(e => {
      loading.value = false
      errorMsg.value = e.message || '未知错误'
    })

  return {
    loading,
    result,
    errorMsg,
  }
}
```

```vue
<template>
<div class="about">
  <h2 v-if="loading">LOADING...</h2>
  <h2 v-else-if="errorMsg">{{errorMsg}}</h2>
  <!-- <ul v-else>
    <li>id: {{result.id}}</li>
    <li>name: {{result.name}}</li>
    <li>distance: {{result.distance}}</li>
  </ul> -->

  <ul v-for="p in result" :key="p.id">
    <li>id: {{p.id}}</li>
    <li>title: {{p.title}}</li>
    <li>price: {{p.price}}</li>
  </ul>
  <!-- <img v-if="result" :src="result[0].url" alt=""> -->
</div>
</template>

<script lang="ts">
import {
  watch
} from "vue"
import useRequest from './hooks/useRequest'

// 地址数据接口
interface AddressResult {
  id: number;
  name: string;
  distance: string;
}

// 产品数据接口
interface ProductResult {
  id: string;
  title: string;
  price: number;
}

export default {
  setup() {

    // const {loading, result, errorMsg} = useRequest<AddressResult>('/data/address.json')
    const {loading, result, errorMsg} = useRequest<ProductResult[]>('/data/products.json')

    watch(result, () => {
      if (result.value) {
        console.log(result.value.length) // 有提示
      }
    })

    return {
      loading,
      result, 
      errorMsg
    }
  }
}
</script>
```

#### toRefs

把一个响应式对象转换成普通对象，该普通对象的每个 property 都是一个 ref

应用：当从合成函数返回响应式对象时，toRefs 非常有用，这样消费组件就可以在不丢失响应式的情况下对返回的对象进行分解使用

问题: **reactive 对象取出的所有属性值都是非响应式的**

解决: **<font color='red'>利用 toRefs 可以将一个响应式 reactive 对象的所有原始属性转换为响应式的 ref 属性</font>**

```vue
<template>
  <h2>App</h2>
  <h3>foo: {{foo}}</h3>
  <h3>bar: {{bar}}</h3>
  <h3>foo2: {{foo2}}</h3>
  <h3>bar2: {{bar2}}</h3>


</template>

<script lang="ts">
import { reactive, toRefs } from 'vue'
/*
toRefs:
  将响应式对象中所有属性包装为ref对象, 并返回包含这些ref对象的普通对象
  应用: 当从合成函数返回响应式对象时，toRefs 非常有用，
        这样消费组件就可以在不丢失响应式的情况下对返回的对象进行分解使用
*/
export default {

  setup () {

    const state = reactive({
      foo: 'a',
      bar: 'b',
    })

    const stateAsRefs = toRefs(state)

    setTimeout(() => {
      state.foo += '++'
      state.bar += '++'
    }, 2000);

    const {foo2, bar2} = useReatureX()

    return {
      // ...state,
      ...stateAsRefs,
      foo2, 
      bar2
    }
  },
}

function useReatureX() {
  const state = reactive({
    foo2: 'a',
    bar2: 'b',
  })

  setTimeout(() => {
    state.foo2 += '++'
    state.bar2 += '++'
  }, 2000);

  return toRefs(state)
}

</script>
```

#### ref获取元素

<font color='blue'>利用ref函数获取组件中的标签元素</font>

功能需求: 让输入框自动获取焦点

```vue
<template>
  <h2>App</h2>
  <input type="text">---
  <input type="text" ref="inputRef">
</template>

<script lang="ts">
import { onMounted, ref } from 'vue'
/* 
ref获取元素: 利用ref函数获取组件中的标签元素
功能需求: 让输入框自动获取焦点
*/
export default {
  setup() {
    const inputRef = ref<HTMLElement|null>(null)

    onMounted(() => {
      inputRef.value && inputRef.value.focus()
    })

    return {
      inputRef
    }
  },
}
</script>
```

## shallowReactive 与 shallowRef

- shallowReactive : 只处理了对象内最外层属性的响应式(也就是浅响应式)
- shallowRef: 只处理了value的响应式, 不进行对象的reactive处理
- 什么时候用浅响应式呢?
  - 一般情况下使用ref和reactive即可
  - 如果有一个对象数据, 结构比较深, 但变化时只是外层属性变化 ===> shallowReactive
  - 如果有一个对象数据, 后面会产生新的对象来替换 ===> shallowRef

```vue
<template>
  <h2>App</h2>

  <h3>m1: {{m1}}</h3>
  <h3>m2: {{m2}}</h3>
  <h3>m3: {{m3}}</h3>
  <h3>m4: {{m4}}</h3>

  <button @click="update">更新</button>
</template>

<script lang="ts">
import { reactive, ref, shallowReactive, shallowRef } from 'vue'
/* 
shallowReactive与shallowRef
  shallowReactive: 只处理了对象内最外层属性的响应式(也就是浅响应式)
  shallowRef: 只处理了value的响应式, 不进行对象的reactive处理
总结:
  reactive与ref实现的是深度响应式, 而shallowReactive与shallowRef是浅响应式
  什么时候用浅响应式呢?
    一般情况下使用ref和reactive即可,
    如果有一个对象数据, 结构比较深, 但变化时只是外层属性变化 ===> shallowReactive
    如果有一个对象数据, 后面会产生新的对象来替换 ===> shallowRef
*/

export default {

  setup () {

    const m1 = reactive({a: 1, b: {c: 2}})
    const m2 = shallowReactive({a: 1, b: {c: 2}})

    const m3 = ref({a: 1, b: {c: 2}})
    const m4 = shallowRef({a: 1, b: {c: 2}})

    const update = () => {
      // m1.b.c += 1
      // m2.b.c += 1

      // m3.value.a += 1
      m4.value.a += 1
    }

    return {
      m1,
      m2,
      m3,
      m4,
      update,
    }
  }
}
</script>
```

## readonly 与 shallowReadonly

- readonly:
  - 深度只读数据
  - 获取一个对象 (响应式或纯对象) 或 ref 并返回原始代理的只读代理。
  - 只读代理是深层的：访问的任何嵌套 property 也是只读的。
- shallowReadonly
  - 浅只读数据
  - 创建一个代理，使其自身的 property 为只读，但不执行嵌套对象的深度只读转换
- 应用场景:
  - 在某些特定情况下, 我们可能不希望对数据进行更新的操作, 那就可以包装生成一个只读代理对象来读取数据, 而不能修改或删除

```vue
<template>
  <h2>App</h2>
  <h3>{{state}}</h3>
  <button @click="update">更新</button>
</template>

<script lang="ts">
import { reactive, readonly, shallowReadonly } from 'vue'
/*
readonly: 深度只读数据
  获取一个对象 (响应式或纯对象) 或 ref 并返回原始代理的只读代理。
  只读代理是深层的：访问的任何嵌套 property 也是只读的。
shallowReadonly: 浅只读数据
  创建一个代理，使其自身的 property 为只读，但不执行嵌套对象的深度只读转换 
应用场景: 
  在某些特定情况下, 我们可能不希望对数据进行更新的操作, 那就可以包装生成一个只读代理对象来读取数据, 而不能修改或删除
*/

export default {

  setup () {

    const state = reactive({
      a: 1,
      b: {
        c: 2
      }
    })

    // const rState1 = readonly(state)
    const rState2 = shallowReadonly(state)

    const update = () => {
      // rState1.a++ // error
      // rState1.b.c++ // error

      // rState2.a++ // error
      rState2.b.c++
    }
    
    return {
      state,
      update
    }
  }
}
</script>
```

## toRaw 与 markRaw

- toRaw
  - 返回由 `reactive` 或 `readonly` 方法转换成响应式代理的普通对象。
  - 这是一个还原方法，可用于临时读取，访问不会被代理/跟踪，写入时也不会触发界面更新。
- markRaw
  - 标记一个对象，使其永远不会转换为代理。返回对象本身
  - 应用场景:
    - 有些值不应被设置为响应式的，例如复杂的第三方类实例或 Vue 组件对象。
    - 当渲染具有不可变数据源的大列表时，跳过代理转换可以提高性能。

```vue
<template>
  <h2>{{state}}</h2>
  <button @click="testToRaw">测试toRaw</button>
  <button @click="testMarkRaw">测试markRaw</button>
</template>

<script lang="ts">
/* 
toRaw: 得到reactive代理对象的目标数据对象
*/
import {
  markRaw,
  reactive, toRaw,
} from 'vue'
export default {
  setup () {
    const state = reactive<any>({
      name: 'tom',
      age: 25,
    })

    const testToRaw = () => {
      const user = toRaw(state)
      user.age++  // 界面不会更新

    }

    const testMarkRaw = () => {
      const likes = ['a', 'b']
      // state.likes = likes
      state.likes = markRaw(likes) // likes数组就不再是响应式的了
      setTimeout(() => {
        state.likes[0] += '--'
      }, 1000)
    }

    return {
      state,
      testToRaw,
      testMarkRaw,
    }
  }
}
</script>
```

#### toRef

- 为源响应式对象上的某个属性创建一个 ref对象, 二者内部操作的是同一个数据值, 更新时二者是同步的
- 区别ref: 拷贝了一份新的数据值单独操作, 更新时相互不影响
- 应用: 当要将 某个prop 的 ref 传递给复合函数时，toRef 很有用

```vue
<template>
  <h2>App</h2>
  <p>{{state}}</p>
  <p>{{foo}}</p>
  <p>{{foo2}}</p>

  <button @click="update">更新</button>

  <Child :foo="foo"/>
</template>

<script lang="ts">
/*
toRef:
  为源响应式对象上的某个属性创建一个 ref对象, 二者内部操作的是同一个数据值, 更新时二者是同步的
  区别ref: 拷贝了一份新的数据值单独操作, 更新时相互不影响
  应用: 当要将某个 prop 的 ref 传递给复合函数时，toRef 很有用
*/

import {
  reactive,
  toRef,
  ref,
} from 'vue'
import Child from './Child.vue'

export default {

  setup () {

    const state = reactive({
      foo: 1,
      bar: 2
    })

    const foo = toRef(state, 'foo')
    const foo2 = ref(state.foo)

    const update = () => {
      state.foo++
      // foo.value++
      // foo2.value++  // foo和state中的数据不会更新
    }

    return {
      state,
      foo,
      foo2,
      update,
    }
  },

  components: {
    Child
  }
}
</script>
```

```vue
<template>
  <h2>Child</h2>
  <h3>{{foo}}</h3>
  <h3>{{length}}</h3>
</template>

<script lang="ts">
import { computed, defineComponent, Ref, toRef } from 'vue'

const component = defineComponent({
  props: {
    foo: {
      type: Number,
      require: true
    }
  },

  setup (props, context) {
    const length = useFeatureX(toRef(props, 'foo'))

    return {
      length
    }
  }
})

function useFeatureX(foo: Ref) {
  const lenth = computed(() => foo.value.length)

  return lenth
}

export default component
</script>
```

### customRef

- 创建一个自定义的 ref，并对其依赖项跟踪和更新触发进行显式控制
- 需求: 使用 customRef 实现 debounce 的示例

```vue
<template>
  <h2>App</h2>
  <input v-model="keyword" placeholder="搜索关键字"/>
  <p>{{keyword}}</p>
</template>

<script lang="ts">
/*
customRef:
  创建一个自定义的 ref，并对其依赖项跟踪和更新触发进行显式控制

需求: 
  使用 customRef 实现 debounce 的示例
*/

import {
  ref,
  customRef
} from 'vue'

export default {

  setup () {
    const keyword = useDebouncedRef('', 500)
    console.log(keyword)
    return {
      keyword
    }
  },
}

/* 
实现函数防抖的自定义ref
*/
function useDebouncedRef<T>(value: T, delay = 200) {
  let timeout: number
  return customRef((track, trigger) => {
    return {
      get() {
        // 告诉Vue追踪数据
        track()
        return value
      },
      set(newValue: T) {
        clearTimeout(timeout)
        timeout = setTimeout(() => {
          value = newValue
          // 告诉Vue去触发界面更新
          trigger()
        }, delay)
      }
    }
  })
}

</script>
```

### provide与inject

- provide和inject提供依赖注入，功能类似于vue2
- 实现跨层级组件(祖孙)间通信

```vue
<template>
  <h1>父组件</h1>
  <p>当前颜色: {{color}}</p>
  <button @click="color='red'">红</button>
  <button @click="color='yellow'">黄</button>
  <button @click="color='blue'">蓝</button>
  
  <hr>
  <Son />
</template>

<script lang="ts">
import { provide, ref } from 'vue'
/* 
- provide` 和 `inject` 提供依赖注入，功能类似 2.x 的 `provide/inject
- 实现跨层级组件(祖孙)间通信
*/

import Son from './Son.vue'
export default {
  name: 'ProvideInject',
  components: {
    Son
  },
  setup() {
    
    const color = ref('red')

    provide('color', color)

    return {
      color
    }
  }
}
</script>
```

```vue
<template>
  <div>
    <h2>子组件</h2>
    <hr>
    <GrandSon />
  </div>
</template>

<script lang="ts">
import GrandSon from './GrandSon.vue'
export default {
  components: {
    GrandSon
  },
}
</script>
```

```vue
<template>
  <div>
    <h2>子组件</h2>
    <hr>
    <GrandSon />
  </div>
</template>

<script lang="ts">
import GrandSon from './GrandSon.vue'
export default {
  components: {
    GrandSon
  },
}
</script>
```

## 响应式数据的判断

- isRef: 检查一个值是否为一个 ref 对象
- isReactive: 检查一个对象是否是由 `reactive` 创建的响应式代理
- isReadonly: 检查一个对象是否是由 `readonly` 创建的只读代理
- isProxy: 检查一个对象是否是由 `reactive` 或者 `readonly` 方法创建的代理

### 手写组合API

#### 1、shallowReactive 与 reactive

```js
const reactiveHandler = {
  get (target, key) {

    if (key==='_is_reactive') return true

    return Reflect.get(target, key)
  },

  set (target, key, value) {
    const result = Reflect.set(target, key, value)
    console.log('数据已更新, 去更新界面')
    return result
  },

  deleteProperty (target, key) {
    const result = Reflect.deleteProperty(target, key)
    console.log('数据已删除, 去更新界面')
    return result
  },
}

/* 
自定义shallowReactive
*/
function shallowReactive(obj) {
  return new Proxy(obj, reactiveHandler)
}

/* 
自定义reactive
*/
function reactive (target) {
  if (target && typeof target==='object') {
    if (target instanceof Array) { // 数组
      target.forEach((item, index) => {
        target[index] = reactive(item)
      })
    } else { // 对象
      Object.keys(target).forEach(key => {
        target[key] = reactive(target[key])
      })
    }

    const proxy = new Proxy(target, reactiveHandler)
    return proxy
  }

  return target
}


/* 测试自定义shallowReactive */
const proxy = shallowReactive({
  a: {
    b: 3
  }
})

proxy.a = {b: 4} // 劫持到了
proxy.a.b = 5 // 没有劫持到


/* 测试自定义reactive */
const obj = {
  a: 'abc',
  b: [{x: 1}],
  c: {x: [11]},
}

const proxy = reactive(obj)
console.log(proxy)
proxy.b[0].x += 1
proxy.c.x[0] += 1
```

#### 2、shallowRef 与 ref

```js
/*
自定义shallowRef
*/
function shallowRef(target) {
  const result = {
    _value: target, // 用来保存数据的内部属性
    _is_ref: true, // 用来标识是ref对象
    get value () {
      return this._value
    },
    set value (val) {
      this._value = val
      console.log('set value 数据已更新, 去更新界面')
    }
  }

  return result
}

/* 
自定义ref
*/
function ref(target) {
  if (target && typeof target==='object') {
    target = reactive(target)
  }

  const result = {
    _value: target, // 用来保存数据的内部属性
    _is_ref: true, // 用来标识是ref对象
    get value () {
      return this._value
    },
    set value (val) {
      this._value = val
      console.log('set value 数据已更新, 去更新界面')
    }
  }

  return result
}

/* 测试自定义shallowRef */
const ref3 = shallowRef({
  a: 'abc',
})
ref3.value = 'xxx'
ref3.value.a = 'yyy'


/* 测试自定义ref */
const ref1 = ref(0)
const ref2 = ref({
  a: 'abc',
  b: [{x: 1}],
  c: {x: [11]},
})
ref1.value++
ref2.value.b[0].x++
console.log(ref1, ref2)
```

#### 3、shallowReadonly 与 readonly

```js
const readonlyHandler = {
  get (target, key) {
    if (key==='_is_readonly') return true

    return Reflect.get(target, key)
  },

  set () {
    console.warn('只读的, 不能修改')
    return true
  },

  deleteProperty () {
    console.warn('只读的, 不能删除')
    return true
  },
}

/* 
自定义shallowReadonly
*/
function shallowReadonly(obj) {
  return new Proxy(obj, readonlyHandler)
}

/* 
自定义readonly
*/
function readonly(target) {
  if (target && typeof target==='object') {
    if (target instanceof Array) { // 数组
      target.forEach((item, index) => {
        target[index] = readonly(item)
      })
    } else { // 对象
      Object.keys(target).forEach(key => {
        target[key] = readonly(target[key])
      })
    }
    const proxy = new Proxy(target, readonlyHandler)

    return proxy 
  }

  return target
}

/* 测试自定义readonly */
/* 测试自定义shallowReadonly */
const objReadOnly = readonly({
  a: {
    b: 1
  }
})
const objReadOnly2 = shallowReadonly({
  a: {
    b: 1
  }
})

objReadOnly.a = 1
objReadOnly.a.b = 2
objReadOnly2.a = 1
objReadOnly2.a.b = 2
```

#### 4、isRef, isReactive 与 isReadonly

```js
/* 
判断是否是ref对象
*/
function isRef(obj) {
  return obj && obj._is_ref
}

/* 
判断是否是reactive对象
*/
function isReactive(obj) {
  return obj && obj._is_reactive
}

/* 
判断是否是readonly对象
*/
function isReadonly(obj) {
  return obj && obj._is_readonly
}

/* 
是否是reactive或readonly产生的代理对象
*/
function isProxy (obj) {
  return isReactive(obj) || isReadonly(obj)
}


/* 测试判断函数 */
console.log(isReactive(reactive({})))
console.log(isRef(ref({})))
console.log(isReadonly(readonly({})))
console.log(isProxy(reactive({})))
console.log(isProxy(readonly({})))
```

# Composition API VS Option API

#### 1、Option API的问题

 在传统的Vue OptionsAPI中，新增或者修改一个需求，就需要分别在data，methods，computed里修改  

#### 2、Composition API

 我们可以更加优雅的组织我们的代码，函数。让相关功能的代码更加有序的组织在一起 

## 新增组件

#### 1、Fragment(片断)

- 在Vue2中: 组件必须有一个根标签
- 在Vue3中: 组件可以没有根标签, 内部会将多个标签包含在一个Fragment虚拟元素中
- 好处: 减少标签层级, 减小内存占用

```vue
<template>
    <h2>aaaa</h2>
    <h2>aaaa</h2>
</template>
```

#### 2、Teleport(瞬移)

- Teleport 提供了一种干净的方法, 让组件的html在父组件界面外的特定标签(很可能是body)下插入显示

ModalButton.vue

```vue
<template>
  <button @click="modalOpen = true">
      Open full screen modal! (With teleport!)
  </button>

  <teleport to="body">
    <div v-if="modalOpen" class="modal">
      <div>
        I'm a teleported modal! 
        (My parent is "body")
        <button @click="modalOpen = false">
          Close
        </button>
      </div>
    </div>
  </teleport>
</template>

<script>
import { ref } from 'vue'
export default {
  name: 'modal-button',
  setup () {
    const modalOpen = ref(false)
    return {
      modalOpen
    }
  }
}
</script>


<style>
.modal {
  position: absolute;
  top: 0; right: 0; bottom: 0; left: 0;
  background-color: rgba(0,0,0,.5);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.modal div {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: white;
  width: 300px;
  height: 300px;
  padding: 5px;
}
</style>
```

App.vue

```vue
<template>
  <h2>App</h2>
  <modal-button></modal-button>
</template>

<script lang="ts">
import ModalButton from './ModalButton.vue'

export default {
  setup() {
    return {
    }
  },

  components: {
    ModalButton
  }
}
</script>
```

#### 3、Suspense(不确定的)

- 它们允许我们的应用程序在等待异步组件时渲染一些后备内容，可以让我们创建一个平滑的用户体验

```vue
<template>
  <Suspense>
    <template v-slot:default>
      <AsyncComp/>
      <!-- <AsyncAddress/> -->
    </template>

    <template v-slot:fallback>
      <h1>LOADING...</h1>
    </template>
  </Suspense>
</template>

<script lang="ts">
/* 
异步组件 + Suspense组件
*/
// import AsyncComp from './AsyncComp.vue'
import AsyncAddress from './AsyncAddress.vue'
import { defineAsyncComponent } from 'vue'
const AsyncComp = defineAsyncComponent(() => import('./AsyncComp.vue'))
export default {
  setup() {
    return {
     
    }
  },

  components: {
    AsyncComp,
    AsyncAddress
  }
}
</script>
```

- AsyncComp.vue

```vue
<template>
  <h2>AsyncComp22</h2>
  <p>{{msg}}</p>
</template>

<script lang="ts">

export default {
  name: 'AsyncComp',
  setup () {
    // return new Promise((resolve, reject) => {
    //   setTimeout(() => {
    //     resolve({
    //       msg: 'abc'
    //     })
    //   }, 2000)
    // })
    return {
      msg: 'abc'
    }
  }
}
</script>
```

- AsyncAddress.vue

```vue
<template>
<h2>{{data}}</h2>
</template>

<script lang="ts">
import axios from 'axios'
export default {
  async setup() {
    const result = await axios.get('/data/address.json')
    return {
      data: result.data
    }
  }
}
</script>
```

## 其他新的API

#### 全新的全局API

- createApp()
- defineProperty()
- defineAsyncComponent()
- nextTick()

#### 将原来的全局API转移到应用对象

- app.component()
- app.config()
- app.directive()
- app.mount()
- app.unmount()
- app.use()

#### 模板语法变化

- v-model的本质变化
  - prop：value -> modelValue；
  - event：input -> update:modelValue；
- .sync修改符已移除, 由v-model代替
- v-if优先v-for解析

![1649207407655](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649207407655.png)

![1649207453493](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649207453493.png)

![1649207495845](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649207495845.png)

![1649207517716](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649207517716.png)

## vue特性

> ① 数据驱动视图
>
> ② 双向数据绑定

![1649207598463](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649207598463.png)

![1649207612781](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649207612781.png)

### vue3基本使用步骤

![1649207672626](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649207672626.png)

![1649207696736](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649207696736.png)

# SPA单页面应用程序

**缺点：1.首屏加载慢**

​			解决方法：**路由懒加载、代码压缩、CDN加速、网络传输压缩**

​			**2.不利于SEO**

​			解决方法：**SSR服务端渲染**

![1649210714483](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649210714483.png)

#### 2.vite的基本使用

 基于 vite 创建 SPA 项目 ，仅支持Vue 3.x、不是基于webpack、运行速度快（不建议使用）

![1649210735135](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649210735135.png)

![1649210765079](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649210765079.png)

![1649210798667](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649210798667.png)

![1649210810355](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649210810355.png)

~~~
在工程化的项目中，vue 要做的事情很单纯：通过 main.js 把 App.vue 渲染到 index.html 的指定区域中。
其中：
    ① App.vue 用来编写待渲染的模板结构
    ② index.html 中需要预留一个 el 区域
    ③ main.js 把 App.vue 渲染到了 index.html 所预留的区域中
~~~

##### vite的基本使用

> 在 App.vue 中编写模板结构

![1649210915107](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649210915107.png)

> 在 index.html 中预留 el 区域

![1649210935837](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649210935837.png)

> 在 main.js 中进行渲染

![1649210956324](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649210956324.png)

#### 3.Vue组件的结构

 每个 .vue 组件都由 3 部分构成，分别是： 

​	 **template -> 组件的模板结构** 

​	 **script -> 组件的 JavaScript 行为** 

​	 **style -> 组件的样式** 

其中，**每个组件中必须包含 template 模板结构**，而 script 行为和 style 样式是可选的组成部分。 

> 1. 在 vue 2.x 的版本中，<template> 节点内的 DOM 结构仅支持单个根节点
> 2. 在 vue 3.x 的版本中，<template> 中支持定义多个根节点

##### template节点

![1649211049295](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649211049295.png)

**template中使用指令**

![1649211072765](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649211072765.png)

![1649211089235](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649211089235.png)

##### 组件的script节点

![1649211112220](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649211112220.png)

![1649211131964](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649211131964.png)

###### script中的data节点

![1649211162747](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649211162747.png)

> <font color='green'>vue 规定：组件中的 data 必须是一个函数，不能直接指向一个数据对象。</font>

###### script中的methods节点

![1649211210721](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649211210721.png)

##### 组件的style节点

![1649211232822](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649211232822.png)

###### 让style支持less语法

![1649211265933](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649211265933.png)











## 指令的概念

![1649207874106](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649207874106.png)

##### 1、内容渲染指令

> 内容渲染指令用来辅助开发者渲染 DOM 元素的文本内容。常用的内容渲染指令有如下 3 个：
>
> - v-text
> - {{ }}
> - v-html

###### v-text

![1649207973791](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649207973791.png)

###### {{}}语法

![1649207995181](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649207995181.png)

###### v-html

![1649208018835](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649208018835.png)

##### 2、属性绑定指令

![1649208069855](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649208069855.png)

**简写形式：：**

![1649208110511](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649208110511.png)

###### 使用JavaScript表达式

![1649208134024](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649208134024.png)

#### 3、事件绑定指令

![1649208170035](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649208170035.png)

![1649208187643](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649208187643.png)

**简写形式：**

![1649208208139](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649208208139.png)

##### 事件对象event

![1649208238200](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649208238200.png)

##### 绑定事件并传参

![1649208262005](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649208262005.png)

##### $event

![1649208299908](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649208299908.png)

##### 事件修饰符

![1649208329978](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649208329978.png)

##### 按键修饰符

![1649208379696](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649208379696.png)

#### 4、双向绑定指令

![1649208457857](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649208457857.png)

##### v-model指令的修饰符

![1649208500668](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649208500668.png)

#### 5、条件渲染指令

> 条件渲染指令用来辅助开发者按需控制 DOM 的显示与隐藏。条件渲染指令有如下两个，分别是：
>
> 1. v-if
> 2. v-show

![1649208563328](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649208563328.png)

##### v-else

![1649208578366](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649208578366.png)

##### v-else-if

![1649208598351](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649208598351.png)

#### 6、列表渲染指令

> vue 提供了 v-for 指令，用来辅助开发者基于一个数组来循环渲染相似的 UI 结构。
> v-for 指令需要使用 item in items 的特殊语法，其中：
>
> - items 是待循环的数组
> - item 是当前的循环项

![1649208663815](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649208663815.png)

##### v-for中的索引

![1649208694055](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649208694055.png)

##### 使用key维护列表的状态

> 当列表的数据变化时，默认情况下，vue 会尽可能的复用已存在的DOM 元素，从而提升渲染的性能。但这种
> 默认的性能优化策略，会导致有状态的列表无法被正确更新。
>
> 为了给 vue 一个提示，以便它能跟踪每个节点的身份，从而在保证有状态的列表被正确更新的前提下，提升渲染的性能。此时，需要为每项提供一个唯一的 key 属性：

![1649208778063](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649208778063.png)

###### key的注意事项

> ① <font color='red'>key 的值只能是字符串或数字类型</font>
> ② <font color='orange'>key 的值必须具有唯一性</font>（即：key 的值不能重复）
> ③ 建议把数据项 id 属性的值作为 key 的值（因为 id 属性的值具有唯一性）
> ④ 使用 index 的值当作 key 的值没有任何意义（因为index 的值不具有唯一性）
> ⑤ 建议使用 v-for 指令时一定要指定 key 的值（既提升性能、又防止列表状态紊乱）

# 过滤器

> 过滤器（Filters）常用于文本的格式化。例如：
> hello -> Hello

**过滤器应该被添加在 JavaScript 表达式的尾部，由“管道符”进行调用，示例代码如下：**

![1649208933941](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649208933941.png)

##### 定义过滤器

**在创建 vue 实例期间，可以在 filters 节点中定义过滤器，示例代码如下：**

![1649210378274](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649210378274.png)

![1649210392205](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649210392205.png)

##### 私有过滤器和全局过滤器

![1649210415925](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649210415925.png)

![1649210431120](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649210431120.png)

![1649210480611](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649210480611.png)

###### 过滤器传参

![1649210500564](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649210500564.png)

![1649210512936](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649210512936.png)

> ① 能够知道 vue 的基本使用步骤
>
> 1. 导入 vue.js 文件
> 2. new Vue() 构造函数，得到 vm 实例对象
> 3. 声明 el 和 data 数据节点
> 4. MVVM 的对应关系
>
> ② 掌握 vue 中常见指令的基本用法
>
> 1. 插值表达式、v-bind、v-on、v-if 和 v-else
> 2. v-for 和 :key、v-model
>
> ③ 掌握 vue 中过滤器的基本用法
>
> 1. 全局过滤器 Vue.filter('过滤器名称', function)
> 2. 私有过滤器 filters 节点





# 组件的基本使用

### 注册组件

> vue 中注册组件的方式分为“全局注册”和“局部注册”两种，其中：
>
> 1. 被全局注册的组件，可以在全局任何一个组件内使用
> 2. 被局部注册的组件，只能在当前注册的范围内使用

#### 1、全局注册组件

![1649211385732](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649211385732.png)

**使用全局注册的组件：**

![1649211431976](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649211431976.png)

#### 2、局部注册组件

![1649211466181](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649211466181.png)

#### 3、全局注册和局部注册的区别

![1649211510919](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649211510919.png)

### 通过 name 属性注册组件

> **<font color='orange'>在注册组件期间，除了可以直接提供组件的注册名称之外，还可以把组件的 name 属性作为注册后组件的名称</font>**

![1649211600759](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649211600759.png)

#### 组件之间的样式冲突

![1649211625953](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649211625953.png)

**vue 为 style 节点提供了 scoped 属性，从而防止组件之间的样式冲突问题**

![1649211743568](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649211743568.png)

##### deep样式穿透

> 如果<font color='blue'>给当前组件的 style 节点添加了 scoped 属性，则当前组件的样式对其子组件是不生效的。如果想让某些样式对子组件生效，</font>可以使用 /deep/ 深度选择器

![1649211793204](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649211793204.png)

## 组件的props

> 为了提高组件的复用性，在封装 vue 组件时需要遵守如下的原则：
>
> 1. 组件的 DOM 结构、Style 样式要尽量复用
> 2. 组件中要展示的数据，尽量由组件的使用者提供
>
> 为了方便使用者为组件提供要展示的数据，vue 组件提供了 props 的概念。

### props概念

> <font color='red'>**props 是组件的自定义属性，组件的使用者可以通过 props 把数据传递到子组件内部，供子组件内部进行使用。**</font>

![1649211980651](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649211980651.png)

### 在组件中声明props

> <font color='blue'>在封装 vue 组件时，可以**把动态的数据项声明为 props 自定义属性**。自定义属性可以在当前组件的模板结构中被直接使用。</font>

![1649212057554](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649212057554.png)

![1649212080284](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649212080284.png)

### 动态绑定props的值

> **<font color='orange'>可以使用 v-bind 属性绑定的形式，为组件动态绑定 props 的值</font>**

![1649212138226](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649212138226.png)

![1649212150570](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649212150570.png)

### class与style绑定

> **在实际开发中经常会遇到动态操作元素样式的需求。因此，vue 允许开发者<font color='blue'>通过 v-bind 属性绑定指令</font>，为元素动态绑定 class 属性的值和行内的 style 样式。**

#### 1、动态绑定 HTML 的 class

![1649212221599](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649212221599.png)

![1649212242851](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649212242851.png)

![1649212257656](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649212257656.png)

#### 2、动态绑定style

![1649212297889](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649212297889.png)

> ① 能够说出什么是单页面应用程序及组件化开发
>
> - SPA、只有一个页面、组件是对 UI 结构的复用
>
> ② 能够说出 .vue 单文件组件的组成部分
>
> - template、script、style（scoped、lang）
>
> ③ 能够知道如何注册 vue 的组件
>
> -  全局注册（app.component）、局部注册（components）
>
> ④ 能够知道如何声明组件的 props 属性
>
> - props 数组
>
> ④ 能够知道如何在组件中进行样式绑定
>
> - 动态绑定 class、动态绑定 style

## props验证

### props验证概念

> 指的是：<font color='green'>**在封装组件时对外界传递过来的props 数据进行合法性的校验，从而防止数据不合法的问题。**</font>

 ![1649212547993](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649212547993.png)**使用数组类型的 props 节点的缺点：无法为每个 prop 指定具体的数据类型。** 

#### 对象类型的props节点

![1649212623616](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649212623616.png)

<font color='red'>使用对象类型的 props 节点，可以对每个 prop 进行数据类型的校验 </font>

> 对象类型的 props 节点提供了多种数据验证方案，例如：
>
> ① 基础的类型检查
>
> ② 多个可能的类型
>
> ③ 必填项校验
>
> ④ 属性默认值
>
> ⑤ 自定义验证函数

##### 基础的类型检查

**<font color='green'>可以直接为组件的 prop 属性指定基础的校验类型，从而防止组件的使用者为其绑定错误类型的数据</font>**

##### prop属性一共有8种基本类型

![1649212818006](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649212818006.png)

**如果某个 props 属性值的类型不唯一，此时可以通过数组的形式，为其指定多个可能的类型** ：propA: [Number,String]

![1649212855593](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649212855593.png)

###### 4.1必填项校验

**如果组件的某个 prop 属性是必填项，必须让组件的使用者为其传递属性的值。**

> propB:{
>
> ​	type:String,
>
> ​	required:true
>
> }

![1649212892314](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649212892314.png)

###### 4.2属性默认值

 在封装组件时，可以**为某个 prop 属性指定默认值** ；

> propC:{
>
> ​	type:Number,
>
> ​	default:100
>
> }

![1649212909961](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649212909961.png)

###### 4.3自定义验证函数

 在封装组件时，可以为 prop 属性指定自定义的验证函数，从而对 prop 属性的值进行更加精确的控制；

![1649212936838](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649212936838.png)

## 计算属性

> **<font color='orange'>计算属性本质上就是一个 function 函数，它可以实时监听 data 中数据的变化，并 return 一个计算后的新值，供组件渲染 DOM 时使用。</font>**

监听数据变化

#### 声明计算属性

> **<font color='red'>计算属性需要以 function 函数的形式声明到组件的 computed 选项中</font>**

![1649213047182](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649213047182.png)

**计算属性注意点：**

> ① 计算属性必须定义在<font color='red'> computed 节点中</font>
> ② 计算属性必<font color='red'>须是一个 function 函数</font>
> ③ 计算属性必须<font color='red'>有返回值</font>
> ④ 计算属性必须<font color='red'>当做普通属性使用</font>

###### 计算属性和方法的区别：

相对于方法来说，计算属性会缓存计算的结果，只有计算属性的依赖项发生变化时，才会重新进行运算。因此计算属性的性能更好 。

![1649213142106](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649213142106.png)

## 自定义事件

![1649213163081](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649213163081.png)

> 自定义事件的 3 个使用步骤
>    <font color='red'> 在封装组件时：</font>
>
> ​	① 声明自定义事件
> ​    ② 触发自定义事件
> ​    
>
> ​	<font color='red'>在使用组件时：</font>
>
> ​	③ 监听自定义事件

1、声明自定义事件

**注意：必须在emits节点中声明自定义事件**

![1649213245039](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649213245039.png)

2、触发自定义事件

**在 emits 节点下声明的自定义事件，可以通过 this.$emit('自定义事件的名称') 方法进行触发**

![1649213270122](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649213270122.png)

3、监听自定义事件

**@自定义事件名称**（v-on）

![1649213284956](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649213284956.png)

#### 自定义事件传参：

**在调用 this.$emit() 方法触发自定义事件时，可以通过第 2 个参数为自定义事件传参 **

![1649213318377](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649213318377.png)

## 组件上的v-model

当需要**维护组件内外数据的同步时**，可以在组件上使用v-model指令

![1649213343350](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649213343350.png)

#### 组件时使用v-model的步骤

![1649213375766](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649213375766.png)

> ① 能够知道如何对 props 进行验证
>
> - 数组格式、对象格式
> - type、default、required、validator
>
> ② 能够知道如何使用计算属性
>
> - computed 节点、必须 return 一个结果、缓存计算结果
>
> ③ 能够知道如何为组件绑定自定义事件
>
> - v-on 绑定自定义事件、emits、$emit()
>
> ④ 能够知道如何在组件上使用 v-model
>
> - 应用场景：实现组件内外的数据同步
> - v-model:props名称、emits、$emit('update:props名称')



###### 4.6.1父向子同步数据

~~~
① 父组件通过 v-bind: 属性绑定的形式，把数据传递给子组件
② 子组件中，通过 props 接收父组件传递过来的数据
~~~

###### 4.6.2子向父同步数据

~~~
① 在 v-bind: 指令之前添加 v-model 指令
② 在子组件中声明 emits 自定义事件，格式为 update:xxx
③ 调用 $emit() 触发自定义事件，更新父组件中的数据
~~~

## watch侦听器

> **<font color='blue'>watch 侦听器允许开发者监视数据的变化，从而针对数据的变化做特定的操作。例如，监视用户名的变化并发起请求，判断用户名是否可用。</font>**

![1649213657627](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649213657627.png)

![1649213670457](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649213670457.png)

#### immediate选项

![1649213692399](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649213692399.png)

#### deep选项

![1649213740530](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649213740530.png)

#### 监听对象单个属性的变化

![1649213767265](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649213767265.png)

##### 面试题：侦听器和计算属性的区别

> 计算属性和侦听器侧重的应用场景不同：
>
> ​	计算属性侧重于监听多个值的变化，最终计算并返回一个新值
>
> ​	侦听器侧重于监听单个数据的变化，最终执行特定的业务处理，不需要有任何返回值

## 组件的生命周期

组件从创建--> 运行--> 销毁的整个过程，强调的是一个时间段

![1649213834928](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649213834928.png)

生命周期函数会伴随着组件的运行而自动调用

（1）当组件在内存中被创建完毕后，会自动调用 created 函数

（2）当组件被成功的渲染到页面上之后，会自动调用 mounted 函数

（3）当组件被重新渲染完毕之后，会自动调用 updated 生命周期函数

（4）当组件被销毁完毕之后，会自动调用 unmounted 函数

![1649213852234](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649213852234.png)

#### 监听组件的更新

![1649213874365](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649213874365.png)

#### 组件主要生命周期函数

![1649213901749](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649213901749.png)

#### 组件全部的生命周期函数

![1649213985316](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649213985316.png)

## 组件之间的数据共享

#### 组件之间的关系

 ① 父子关系

 ② 兄弟关系 

 ③ 后代关系 

#### 父子之间的数据共享

父——>子之间共享数据

子——>父之间共享数据

父——>子双向数据同步

#### 1.父组件向子组件共享数据

![1649214156134](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649214156134.png)

<font color='red'>**(1)父组件通过v-bind属性绑定向子组件共享数据，同时子组件需要使用props接收数据**</font>

#### 2、子组件向父组件共享数据

![1649214244111](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649214244111.png)

<font color='red'>**(2)子组件通过自定义事件向父组件共享数据，子组件通过emits节点，声明自定义事件，并在方法节点中，通过this.$emit注册自定义事件，父组件在子组件占位符处绑定自定义事件，并获取传递过来的数据**</font>

#### 3、父子组件之间数据的双向同步**

使用v-model指令维护组件内外数据的双向同步

![1649214312189](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649214312189.png)

#### 4、兄弟组件之间的数据共享

EventBus实现兄弟组件之间的数据共享

![1649214366791](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649214366791.png)

~~~
1.创建EventBus
	const bus = mitt()
	export default bus
2.数据接收方
	import bus from './eventBus.js'
	// 调用EventBus的on()方法，声明自定义事件，通过事件回调接收数据
	bus.on('自定义事件',(data)=>{
	
	})
3.数据发送方
	import bus from './eventBus.js'
	// 调用EventBus的emit()方法，向外发送数据
	bus.emit('自定义事件',要发送的数据)
~~~

**步骤：**

![1649214393087](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649214393087.png)

![1649214404932](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649214404932.png)

![1649214463792](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649214463792.png)

![1649214489370](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649214489370.png)

#### 5、后代关系组件之间的数据共享

指父节点的组件向其子孙组件共享数据

**使用provide和inject实现后代关系组件之间的数据共享**

![1649214521679](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649214521679.png)

##### 父节点通过provide共享数据

![1649214565756](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649214565756.png)

##### 子孙节点通过inject接收数据

![1649214602320](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649214602320.png)

##### 父节点向外共享响应式的数据

![1649214641614](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649214641614.png)

##### 子孙节点使用响应式的数据

![1649214673155](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649214673155.png)

![1649214691637](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649214691637.png)

## vuex

**<font color='red'>vuex 是终极的组件之间的数据共享方案</font>** 

#### 全局配置axios

![1649214771713](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649214771713.png)

> ① 能够掌握 watch 侦听器的基本使用
>
> 1. 定义最基本的 watch 侦听器
> 2. immediate、deep、监听对象中单个属性的变化
>
> ② 能够知道 vue 中常用的生命周期函数
>
> 1. 创建阶段、运行阶段、销毁阶段
> 2. created、mounted
>
> ③ 能够知道如何实现组件之间的数据共享
>
> 1. 父子组件、兄弟组件、后代组件
>
> ④ 能够知道如何在 vue3 的项目中全局配置 axios
>
> 1. main.js 入口文件中进行配置
> 2. app.config.globalProperties.$http = axios

## ref引用

> **<font color='red'>ref 用来辅助开发者在不依赖于jQuery 的情况下，获取 DOM 元素或组件的引用。</font>**
>
> 每个 vue 的组件实例上，<font color='green'>都包含一个$refs 对象，里面存储着对应的DOM 元素或组件的引用。</font>
>
> 默认情况下，组件的 $refs 指向一个空对象。

![1649214995176](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649214995176.png)

##### 使用 ref 引用 DOM 元素

![1649215017351](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215017351.png)

##### 使用 ref 引用组件实例

![1649215038176](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215038176.png)

![1649215055124](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215055124.png)

![1649215070877](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215070877.png)

##### this.$nextTick(cb) 方法

**注意：组件是异步执行DOM元素的更新的，所以当DOM元素更新过程中获取ref结果为空，组件的 $nextTick(cb) 方法，会把 cb 回调推迟到下一个 DOM 更新周期之后执行**

**通俗的理解是：等组件的DOM 异步地重新渲染完成后，再执行 cb 回调函数。从而能保证cb 回调函数可以操作到最新的 DOM 元素。**

![1649215113212](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215113212.png)

## 动态组件

> <font color='red'>动态组件指的是动态切换组件的显示与隐藏。vue 提供了一个内置的 <component> 组件，专门用来实现组件的动态渲染。</font>
>
> ① <component> 是组件的占位符
> ② 通过 is 属性动态指定要渲染的组件名称
> ③ <component is="要渲染的组件的名称"></component>

![1649215175077](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215175077.png)

##### keep-alive的作用

**keep-alive是用于保持组件的状态**

![1649215202350](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215202350.png)

举例：如组件一中 count 可以通过按钮+1，当切换到组件二，然后再切换回组件一时，如果不使用keep-alive，则组件一中的数据状态会变回其默认值，不会保留其状态，若加keep-alive，则组件一的状态会得到保留，从组件二回到组件一时，count值依旧为切换前的值。

## 插槽

插槽(slot)是vue为组件的封装者提供的能力，允许在封装组件时，把<font color='green'>不确定的、希望由用户指定的部分定义为插槽。</font>

**插槽可以认为为内容占位符**

![1649215259064](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215259064.png)

**没有预留插槽的内容会被丢弃**

![1649215288104](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215288104.png)

**注意：是在被使用的子组件中添加<slot></slot>插槽，并且在使用其的父组件中通过以下形式为其动态指定内容**

~~~
<my-left>
	// p标签就是要插入到子组件的插槽中的内容
	<p>第二个</p>
</my-left>
~~~

##### 1.插槽的后备内容---即默认内容

如果组件的使用者没有为插槽提供任何的内容，则后备内容会生效

![1649215317458](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215317458.png)

##### 2.具名插槽

如果在封装插件的时候，需要预留多个插槽节点，则需要为每个插槽指定**具体的name名称**，称为具名插槽

![1649215336496](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215336496.png)

封装组件：

~~~
<slot name="header"></slot>
// 默认内容，即未指定插槽的内容
// 注意：没有指定 name 名称的插槽，会有隐含的名称为 default
<slot></slot>
<slot name="footer"></slot>
~~~

使用组件：

~~~
在向具名插槽提供内容的时候，我们可以在一个 <template> 元素上使用 v-slot 指令，并以 v-slot 的参数的形式提供其名称。v-slot的简写形式为：#
	<template #footer>
	</template>
~~~

###### 为具名插槽提供内容

![1649215373273](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215373273.png)

**具名插槽的简写：**

![1649215398006](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215398006.png)

##### 3.作用域插槽

在封装组件的过程中，可以为预留的<slot>插槽绑定props数据，称之为“作用域插槽”；使用该组件的组件可以接收数据。

![1649215431801](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215431801.png)

**发送数据方：**

~~~
<slot :info="information"></slot>
~~~

**数据接收方**

~~~
<template v-slot:default="scoped">
	{{ scoped }}
</template>
~~~

**解构作用域插槽的Prop**

![1649215486322](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215486322.png)

1、声明作用域插槽

![1649215508373](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215508373.png)

2、使用作用域插槽

![1649215527605](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215527605.png)

## 自定义指令

##### 1、私有自定义指令

 在 directives 节点下声明私有自定义指令 ， 在使用自定义指令时，需要加上 v- 前缀 

![1649215563955](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215563955.png)

使用自定义指令

![1649215578510](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215578510.png)

##### 2、全局自定义指令

1、声明全局自定义指令

![1649215601201](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215601201.png)

###### update函数

![1649215666615](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215666615.png)

简写形式：

![1649215684667](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215684667.png)

##### 3、指令的参数值

在绑定指令时，可以通过“等号”的形式为指令绑定具体的参数值

![1649215706105](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215706105.png)

> ① 能够知道如何使用 ref 引用 DOM 和组件实例
>
> - 通过 ref 属性指定引用的名称、使用 this.$refs 访问引用实例
>
> ② 能够知道 $nextTick 的调用时机
>
> - 组件的 DOM 更新之后，才执行 $nextTick 中的回调
>
> ③ 能够说出 keep-alive 元素的作用
>
> - 保持动态组件的状态
>
> ④ 能够掌握插槽的基本用法
>
> - <slot> 标签、具名插槽、作用域插槽、v-slot: 简写为 #
>
> ⑤ 能够知道如何自定义指令
>
> - 私有自定义指令、全局自定义指令

## 路由

![1649215860909](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215860909.png)

##### 1.后端路由

指：请求方式、请求地址与function处理函数之间的对应关系

![1649215881059](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215881059.png)

##### 2.SPA与前端路由

不同组件之间的切换需要通过前端路由实现

指：**pash地址与组件之间的关系**

![1649215895688](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215895688.png)

#### 前端路由的工作方式

![1649215934957](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215934957.png)

#### 简易的前端路由示例

![1649215962762](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649215962762.png)

![1649216003347](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216003347.png)

![1649216015115](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216015115.png)

![1649216025128](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216025128.png)

## vue-router

> vue-router 是 vue.js 官方给出的路由解决方案。它只能结合 vue 项目进行使用，能够轻松的管理 SPA 项目
> 中组件的切换。

![1649216069299](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216069299.png)

###### 1、安装vue-router

~~~
npm install vue-router@next -S ：安装vue-router
~~~

###### 2、定义路由组件

![1649216127717](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216127717.png)

###### 3、声明路由链接和占位符

> 使用<router-link  to="">标签来声明路由链接，并使用<router-view>标签来声明路由占位符 

![1649216147736](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216147736.png)

###### 4、创建路由模块

![1649216182891](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216182891.png)

![1649216194376](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216194376.png)

![1649216213851](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216213851.png)

![1649216223862](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216223862.png)

![1649216233566](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216233566.png)

![1649216245537](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216245537.png)

## vue-router 的高级用法

### 路由重定向

> 路由重定向指的是：用户在访问地址 A 的时候，强制用户跳转到地址 C ，从而展示特定的组件页面。
> 通过路由规则的 redirect 属性，指定一个新的路由地址，可以很方便地设置路由的重定向：

![1649216324637](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216324637.png)

##### 3.路由高亮

> 可以通过如下的两种方式，将激活的路由链接进行高亮显示：
>
> ① 使用默认的高亮 class 类
>
> ② 自定义路由高亮的 class 类

###### 3.1默认的高亮class类

被激活的路由链接，默认会应用一个叫做 router-link-active 的类名。开发者可以使用此类名选择器，为激活 的路由链接设置高亮的样式 

![1649216347893](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216347893.png)

在index.css全局样式表中，为其设置高亮效果

###### 3.2 自定义路由高亮的 class 类  

 **可以基于 linkActiveClass 属性，自定义路由链接被激活时所应用的类名** 

![1649216395692](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216395692.png)

##### 4.嵌套路由

通过路由实现组件的嵌套展示，称为嵌套路由

> ① 声明子路由链接和子路由占位符
> ② 在父路由规则中，通过 children 属性嵌套声明子路由规则

![1649216412191](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216412191.png)

###### 1、声明子路由链接和子路由占位符

![1649216468382](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216468382.png)

###### 2、通过children属性声明子路由规则

![1649216499739](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216499739.png)

#### 动态路由

> 动态路由指的是：把 Hash 地址中可变的部分定义为参数项，从而提高路由规则的复用性。在 vue-router 中
> 使用英文的冒号（:）来定义路由的参数项。

![1649216532536](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216532536.png)

######   $route.params 参数对象 

>  **<font color='orange'>通过动态路由匹配的方式渲染出来的组件中，可以使用 $route.params 对象访问到动态匹配的参数值。</font>**

![1649216549171](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216549171.png)

**使用props接收路由参数**

![1649216617983](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216617983.png)

为了简化路由参数的获取形式，vue-router 允许在路由规则中开启 props 传参 

#### 编程式导航

> 通过调用 API 实现导航的方式，叫做编程式导航。与之对应的，通过点击链接实现导航的方式，叫做声明式导航。例如：
>
> - 普通网页中点击 <a> 链接、vue 项目中点击 <router-link> 都属于声明式导航
> - 普通网页中调用 location.href 跳转到新页面的方式，属于编程式导航

**编程式导航API**

> vue-router 提供了许多编程式导航的 API，其中最常用的两个 API 分别是：
> ① **<font color='red'>this.$router.push('hash 地址')</font>**
>
> - 跳转到指定 Hash 地址，从而展示对应的组件
>
> ② **<font color='red'>this.$router.go(数值 n)</font>**
>
> - 实现导航历史的前进、后退

##### $router.push()

![1649216749229](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216749229.png)

##### $router.go()

![1649216776212](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216776212.png)

##### 命名路由

**通过 name 属性为路由规则定义名称的方式，叫做命名路由**

![1649216795403](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216795403.png)

###### 1. 使用命名路由实现声明式导航 

**<font color='blue'>为<router-link>标签动态绑定 to 属性的值，并通过 name 属性指定要跳转到的路由规则。期间还可以用 params 属性指定跳转期间要携带的路由参数</font>** 

![1649216930132](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649216930132.png)

###### 2. 使用命名路由实现编程式导航

调用 push 函数期间指定一个配置对象，name是要跳转到的路由规则、params 是携带的路由参数

![1649217000473](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649217000473.png)

### 导航守卫

 **<font color='green'>导航守卫可以控制路由的访问权限</font>** 

![1649217024490](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649217024490.png)

###### 1. 全局导航守卫

> 全局导航守卫会拦截每个路由规则，从而对每个路由进行访问权限的控制。可以按照如下的方式定义全局导航守卫

![1649217088037](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649217088037.png)

##### 守卫方式的3个形参

![1649217147096](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649217147096.png)

> 注意： 
>
> ① 在守卫方法中如果<font color='red'>不声明 next 形参</font>，则默认允许用户访问每一个路由！ 
>
> ② 在守卫方法中如果<font color='red'>声明了 next 形参</font>，则必须调用 next() 函数，否则不允许用户访问任何一个路由！ 

##### next函数的3种调用方法

![1649217222324](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649217222324.png)

> 1. 直接放行：next()
> 2. <font color='red'>强制其停留在当前页面</font>：next(false)
> 3. <font color='red'>强制其跳转到登录页面</font>：next('/login')

![1649217285365](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649217285365.png)

总结：

> ① 能够知道如何在 vue 中配置路由
>
> - createRouter、app.use(router)
>
> ② 能够知道如何使用嵌套路由
>
> - 通过 children 属性进行路由嵌套、子路由的 hash 地址不要以 / 开头
>
> ③ 能够知道如何实现动态路由匹配
>
> - 使用冒号声明参数项、this.$route.params、props: true
>
> ④ 能够知道如何使用编程式导航
>
> 1. this.$router.push
> 2. this.$router.go(-1)
>
> ⑤ 能够知道如何使用全局导航守卫
>
> - 路由实例.beforeEach((to, from, next) => { })

## vue-cli

![1649226016114](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649226016114.png)

##### 1.安装vue-cli与创建项目

安装：

~~~
npm i -g @vue/cli
~~~

创建项目：

~~~
vue create 项目名称

# or

vue ui
~~~

###### 基于 vue ui 创建vue项目

 步骤1：在终端下运行 vue ui 命令，自动在浏览器中打开创建项目的可视化面板： 

![1647342912817](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647342912817.png)

 步骤2：在详情页面填写项目名称： 

![1647342945078](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647342945078.png)

 步骤3：在预设页面选择手动配置项目： 

![1647342965673](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647342965673.png)

 步骤4：在功能页面勾选需要安装的功能（Choose Vue Version、Babel、CSS 预处理器、使用配置文件）： 

![1647342988482](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647342988482.png)

 步骤5：在配置页面勾选 vue 的版本和需要的预处理器： 

![1647343004881](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647343004881.png)

 步骤6：将刚才所有的配置保存为预设（模板），方便下一次创建项目时直接复用之前的配置： 

![1647343022136](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647343022136.png)

 步骤7：创建项目并自动安装依赖包： 

 vue ui 的本质：通过可视化的面板采集到用户的配置信息后，在后台基于命令行的方式自动初始化项目： 

![1647343052776](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647343052776.png)

 项目创建完成后，自动进入项目仪表盘： 

![1647343069993](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647343069993.png)

######  基于命令行创建 vue 项目 

 步骤1：在终端下运行 vue create demo2 命令，基于交互式的命令行创建 vue 的项目： 

![1647343120758](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647343120758.png)

 步骤2：选择要安装的功能： 

![1647343140057](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647343140057.png)

 步骤3：使用上下箭头选择 vue 的版本，并使用回车键确认选择： 

![1647343158553](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647343158553.png)

 步骤4：使用上下箭头选择要使用的 css 预处理器，并使用回车键确认选择： 

![1647343171783](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647343171783.png)

 步骤5：使用上下箭头选择如何存储插件的配置信息，并使用回车键确认选择： 

![1647343185580](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647343185580.png)

 步骤6：是否将刚才的配置保存为预设： 

![1647343199053](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647343199053.png)

 步骤7：选择如何安装项目中的依赖包： 

![1647343213707](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647343213707.png)

 步骤8：开始创建项目并自动安装依赖包： 

![1647343228782](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647343228782.png)

 步骤9：项目创建完成： 

![1647343255718](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647343255718.png)

**vue2项目的基本结构：**

![1647343293992](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647343293992.png)

##### 2.vue项目使用路由注意事项

分析 main.js中的主要代码：

![1649226153861](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649226153861.png)

 在 vue2 的项目中，只能安装并使用 3.x 版本的 vue-router。 版本 3 和版本 4 的路由最主要的区别：**创建路由模块的方式不同** 

###### 1. 3.x 版本的路由如何创建路由模块 

 步骤1：在 vue2 的项目中安装 3.x 版本的路由： 

~~~
npm i vue-router@3.4.9 -S
~~~

 步骤2：在 src -> components 目录下，创建需要使用路由切换的组件： 

![1647345270241](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647345270241.png)

 **步骤3：在 src 目录下创建 router -> index.js 路由模块：** 

![1647345299846](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647345299846.png)

 **步骤4：在 main.js 中导入路由模块，并通过 router 属性进行挂载：** 

![1647345319891](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647345319891.png)

 步骤5：在 App.vue 根组件中，使用<router-view>声明路由的占位符： 

![1647345358261](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647345358261.png)

###### 2. 4.x 版本的路由如何创建路由模块 

![1647345391824](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647345391824.png)

### vue 组件库 

![1649226434113](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649226434113.png)

> ① PC 端
> 	Element UI（https://element.eleme.cn/#/zh-CN）
> 	View UI（http://v1.iviewui.com/）
> ② 移动端
> 	Mint UI（http://mint-ui.github.io/#!/zh-cn）
> 	Vant（https://vant-contrib.gitee.io/vant/#/zh-CN/）

###### 1.Element UI

~~~
Element UI 是饿了么前端团队开源的一套 PC 端 vue 组件库。支持在 vue2 和 vue3 的项目中使用：
	vue2 的项目使用旧版的 Element UI（https://element.eleme.cn/#/zh-CN）
	vue3 的项目使用新版的 Element Plus（https://element-plus.gitee.io/#/zh-CN）
~~~

  在 vue2 的项目中安装 element-u 

~~~
npm i element-ui -S
~~~

  引入 element-ui  

![1649226625784](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649226625784.png)

**完整引入**

![1649226664517](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649226664517.png)

**按需导入**

 步骤1，安装 babel-plugin-component： 

~~~
npm i babel-plugin-component -D
~~~

 步骤2，修改根目录下的 babel.config.js 配置文件，新增 plugins 节点如下： 

![1647347216123](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647347216123.png)

 步骤3，如果你只希望引入部分组件，比如 Button，那么需要在 main.js 中写入以下内容： 

![1647347257784](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647347257784.png)



### axios拦截器

**在vue3项目中全局配置 axios**

![1647348358186](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647348358186.png)





**在vue2项目中全局配置 axios**

 需要在 main.js 入口文件中，通过 Vue 构造函数的 prototype 原型对象全局配置 axios： 

![1647348418612](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647348418612.png)

#### 1.拦截器的定义

**拦截器（英文：Interceptors）会在每次发起 ajax 请求和得到响应的时候自动被触发。 **

![1647349149617](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647349149617.png)

#### 2.配置请求拦截器

 通过<font color='red'> **axios.interceptors.request.use(成功的回调, 失败的回调)** </font>可以配置请求拦截器 

![1647349196353](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647349196353.png)

 注意：失败的回调函数可以被省略 

#### 3.请求拦截器-Token认证

![1647349281964](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647349281964.png)

#### 4. 请求拦截器 – 展示 Loading 效果  

![1647349432899](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647349432899.png)

**Loading效果在Ajax请求结束后，并不会自动停止，需要配置响应拦截器关闭Loading效果**

#### 5. 配置响应拦截器  

 通过 **axios.interceptors.response.use(成功的回调, 失败的回调)** 可以配置响应拦截器 

![1647349654172](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647349654172.png)

失败的回调函数可以省略！

#### 6. 响应拦截器 – 关闭 Loading 效果 

 **调用 Loading 实例提供的 close() 方法即可关闭 Loading 效果** 

![1647350116770](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647350116770.png)

## proxy 跨域代理 

![1649226874450](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1649226874450.png)

接口跨域问题，通过代理解决

#### 在项目中配置proxy代理

 步骤1，在 main.js 入口文件中，把 axios 的请求根路径改造为当前 web 项目的根路径： 

![1647350831392](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647350831392.png)

 步骤2，在项目根目录下创建 vue.config.js 的配置文件，并声明如下的配置： 

![1647350848258](C:\Users\86186\AppData\Roaming\Typora\typora-user-images\1647350848258.png)

~~~
注意：
① devServer.proxy 提供的代理功能，仅在开发调试阶段生效
② 项目上线发布时，依旧需要 API 接口服务器开启 CORS 跨域资源共享
~~~

##### 6.总结

> ① 能够知道如何使用 vue-cli 创建项目
>
> - vue ui 、vue create 项目名称
>
> ② 能够知道如何在项目中安装和配置 element-ui
>
> - 完整引入、按需引入、参考官方文档进行配置
>
> ③ 能够知道 element-ui 中常见组件的用法
>
> - Table 表格、Form 表单、Dialog 对话框、Message 消息、MessageBox 弹框
>
> ④ 能够知道如何使用 axios 拦截器
>
> - axios.interceptors.request.use()、axios.interceptors.response.use()
>
> ⑤ 能够知道如何配置 proxy 代理
>
> - 修改请求根路径、vue.config.js、devServer.proxy

# Axios使用

axios框架的全称：ajax-I/O-system

是基于promise用于浏览器和node.js的http客户端，因此可以使用Promise API

> 说到axios我们就不得不说下Ajax。在旧浏览器页面在向服务器请求数据时，因为返回的是整个页面的数据，页面都会强制刷新一下，这对于用户来讲并不是很友好。并且我们只是需要修改页面的部分数据，但是从服务器端发送的却是整个页面的数据，十分消耗网络资源。而我们只是需要修改页面的部分数据，也希望不刷新页面，因此异步网络请求就应运而生。

**Ajax：异步网络请求**

Ajax能够让页面无刷新的请求数据。实现Ajax的方式有多种，如jQuery封装的Ajax，原生的XMLHttpRequest，以及axios。利弊如下：

> - 原生的XMLHttpRequest的配置和调用方式都很繁琐，实现异步请求十分麻烦
> - jQuery的ajax相对于原生的ajax是非常好用的，但是没有必要因为要用ajax异步网络请求而引用jQuery框架

**axios**

本质上还是对原生XMLHttpRequest的封装，可用于浏览器和Node.js的HTTP客户端， 只不过它是基于Promise的，符合最新的ES规范。具备以下特点 ：

> - 在浏览器中创建XMLHttpRequest请求
> - 在node.js中发送http请求
> - 支持Promise API
> - 拦截请求和响应
> - 转换请求和响应数据
> - 取消要求
> - 自动转换JSON数据
> - 客户端支持防止CSRF/XSRF(跨域请求伪造)

## axios常用语法

> 1. axios(config)-通用/最本质的发送任意类型的请求方式,config请求对象，可以包含请求方式/请求路径/请求数
> 2. axios.get(url,params)–get请求
> 3. axios.post(url,data)–向服务器添加数据
> 4. axios.put(url,data)–修改服务器中的数据
> 5. axios.delete(url,params)–删除服务器中的数据
> 6. axios.interceptors.request.use(config=>return config)//请求拦截器，一定要把请求对象config返回,可以在里面设置config的相关配置比如请求头的信息
> 7. axios.interceptors.response.use(res=>return res.data)//响应拦截器，可以对服务中的返回的数据做一定的处理返回
> 8. axios.create({})–创建一个axios实例,使用方法和axios一样，但是这个实例没有取消请求和执行多个异步请求的功能/没有axios.cancel()/axios.all(promise)/axios.spread()功能//它的里面可以接受一个对象，是axios的默认配置，包括baseURL,Timeout
> 9. axios.defaults.xxx–请求的默认全局配置(baseURl/method/timeout)
> 10. axios.cancel()–用于创建取消请求的错误对象
> 11. axios.CancelToken()–用于创建取消请求的token对象
> 12. axios.isCancel()–是否是一个取现请求的错误
> 13. axios.all(promise)–用于批量执行多个异步任务

## 常见的配置选项

~~~
{
   // `url` 是用于请求的服务器 URL
  url: '/user',

  // `method` 是创建请求时使用的方法
  method: 'get', // default

  // `baseURL` 将自动加在 `url` 前面，除非 `url` 是一个绝对 URL。
  // 它可以通过设置一个 `baseURL` 便于为 axios 实例的方法传递相对 URL
  baseURL: 'https://some-domain.com/api/',

  // `transformRequest` 允许在向服务器发送前，修改请求数据
  // 只能用在 'PUT', 'POST' 和 'PATCH' 这几个请求方法
  // 后面数组中的函数必须返回一个字符串，或 ArrayBuffer，或 Stream
  transformRequest: [function (data, headers) {
    // 对 data 进行任意转换处理
    return data;
  }],

  // `transformResponse` 在传递给 then/catch 前，允许修改响应数据
  transformResponse: [function (data) {
    // 对 data 进行任意转换处理
    return data;
  }],

  // `headers` 是即将被发送的自定义请求头
  headers: {'X-Requested-With': 'XMLHttpRequest'},

  // `params` 是即将与请求一起发送的 URL 参数
  // 必须是一个无格式对象(plain object)或 URLSearchParams 对象
  params: {
    ID: 12345
  },

   // `paramsSerializer` 是一个负责 `params` 序列化的函数
  // (e.g. https://www.npmjs.com/package/qs, http://api.jquery.com/jquery.param/)
  paramsSerializer: function(params) {
    return Qs.stringify(params, {arrayFormat: 'brackets'})
  },

  // `data` 是作为请求主体被发送的数据
  // 只适用于这些请求方法 'PUT', 'POST', 和 'PATCH'
  // 在没有设置 `transformRequest` 时，必须是以下类型之一：
  // - string, plain object, ArrayBuffer, ArrayBufferView, URLSearchParams
  // - 浏览器专属：FormData, File, Blob
  // - Node 专属： Stream
  data: {
    firstName: 'Fred'
  },

  // `timeout` 指定请求超时的毫秒数(0 表示无超时时间)
  // 如果请求话费了超过 `timeout` 的时间，请求将被中断
  timeout: 1000,

   // `withCredentials` 表示跨域请求时是否需要使用凭证
  withCredentials: false, // default

  // `adapter` 允许自定义处理请求，以使测试更轻松
  // 返回一个 promise 并应用一个有效的响应 (查阅 [response docs](#response-api)).
  adapter: function (config) {
    /* ... */
  },

 // `auth` 表示应该使用 HTTP 基础验证，并提供凭据
  // 这将设置一个 `Authorization` 头，覆写掉现有的任意使用 `headers` 设置的自定义 `Authorization`头
  auth: {
    username: 'janedoe',
    password: 's00pers3cret'
  },

   // `responseType` 表示服务器响应的数据类型，可以是 'arraybuffer', 'blob', 'document', 'json', 'text', 'stream'
  responseType: 'json', // default

  // `responseEncoding` indicates encoding to use for decoding responses
  // Note: Ignored for `responseType` of 'stream' or client-side requests
  responseEncoding: 'utf8', // default

   // `xsrfCookieName` 是用作 xsrf token 的值的cookie的名称
  xsrfCookieName: 'XSRF-TOKEN', // default

  // `xsrfHeaderName` is the name of the http header that carries the xsrf token value
  xsrfHeaderName: 'X-XSRF-TOKEN', // default

   // `onUploadProgress` 允许为上传处理进度事件
  onUploadProgress: function (progressEvent) {
    // Do whatever you want with the native progress event
  },

  // `onDownloadProgress` 允许为下载处理进度事件
  onDownloadProgress: function (progressEvent) {
    // 对原生进度事件的处理
  },

   // `maxContentLength` 定义允许的响应内容的最大尺寸
  maxContentLength: 2000,

  // `validateStatus` 定义对于给定的HTTP 响应状态码是 resolve 或 reject  promise 。如果 `validateStatus` 返回 `true` (或者设置为 `null` 或 `undefined`)，promise 将被 resolve; 否则，promise 将被 rejecte
  validateStatus: function (status) {
    return status >= 200 && status < 300; // default
  },

  // `maxRedirects` 定义在 node.js 中 follow 的最大重定向数目
  // 如果设置为0，将不会 follow 任何重定向
  maxRedirects: 5, // default

  // `socketPath` defines a UNIX Socket to be used in node.js.
  // e.g. '/var/run/docker.sock' to send requests to the docker daemon.
  // Only either `socketPath` or `proxy` can be specified.
  // If both are specified, `socketPath` is used.
  socketPath: null, // default

  // `httpAgent` 和 `httpsAgent` 分别在 node.js 中用于定义在执行 http 和 https 时使用的自定义代理。允许像这样配置选项：
  // `keepAlive` 默认没有启用
  httpAgent: new http.Agent({ keepAlive: true }),
  httpsAgent: new https.Agent({ keepAlive: true }),

  // 'proxy' 定义代理服务器的主机名称和端口
  // `auth` 表示 HTTP 基础验证应当用于连接代理，并提供凭据
  // 这将会设置一个 `Proxy-Authorization` 头，覆写掉已有的通过使用 `header` 设置的自定义 `Proxy-Authorization` 头。
  proxy: {
    host: '127.0.0.1',
    port: 9000,
    auth: {
      username: 'mikeymike',
      password: 'rapunz3l'
    }
  },

  // `cancelToken` 指定用于取消请求的 cancel token
  // （查看后面的 Cancellation 这节了解更多）
  cancelToken: new CancelToken(function (cancel) {
  })
}
~~~

## 响应结构

~~~
{
  // `data` 由服务器提供的响应
  data: {},

  // `status` 来自服务器响应的 HTTP 状态码
  status: 200,

  // `statusText` 来自服务器响应的 HTTP 状态信息
  statusText: 'OK',

  // `headers` 服务器响应的头
  headers: {},

   // `config` 是为请求提供的配置信息
  config: {},

  request: {}
}
~~~

## axios的默认发送数据格式

默认情况下，axios将JavaScript对象序列化为JSON。 要以application / x-www-form-urlencoded格式发送数据，您可以使用以下选项之一。

**浏览器**

在浏览器中，可以使用 URLSearchParams  API，如下所示：

~~~
const params = new URLSearchParams();
params.append('param1', 'value1');
params.append('param2', 'value2');
axios.post('/foo', params);
~~~

 或者，您可以使用qs库编码数据： 

~~~
const qs = require('qs');
axios.post('/foo', qs.stringify({ 'bar': 123 }));
~~~

 或者以另一种方式（ES6） 

~~~
import qs from 'qs';
const data = { 'bar': 123 };
const options = {
  method: 'POST',
  headers: { 'content-type': 'application/x-www-form-urlencoded' },
  data: qs.stringify(data),
  url,
};
axios(options);
~~~





## 1、安装

npm安装

~~~
npm install axios
~~~

bower安装

~~~
bower install axios
~~~

cdn引入

~~~
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
~~~

**在Vue2项目的main.js文件中引入axios**

~~~
import axios from 'axios'
// 配置请求根路径
axios.defaults.baseURL = 'https://www.escook.cn'
Vue.prototype.$axios = axios
~~~

**在Vue3项目的main.js文件中引入axios**

~~~
import axios from 'axios'

const app = createApp(App)
axios.defaults.baseURL = 'https://www.escook.cn'
app.config.globalProperties.$http=axios
~~~

**在组件中使用axios**

~~~
<script>
	export default {
		mounted(){
			this.$axios.get('/goods.json').then(res=>{
				console.log(res.data);
			})
		}
	}
</script>
~~~

## 2、axios请求方式

### 1、axios可以请求的方法：

> - get：获取数据，请求指定的信息，返回实体对象
> - post：向指定资源提交数据（例如表单提交或文件上传）
> - put：更新数据，从客户端向服务器传送的数据取代指定的文档的内容
> - patch：更新数据，是对put方法的补充，用来对已知资源进行局部更新
> - delete：请求服务器删除指定的数据

#### get请求

示例代码：

**方法一：**

~~~
 //请求格式类似于 http://localhost:8080/goods.json?id=1
this.$axios.get('/goods.json',{
    			params: {
                    id:1
                }
			}).then(res=>{
					console.log(res.data);
				},err=>{
					console.log(err);
			})
~~~

**方法二：**

~~~
this.$axios({
		method: 'get',
		url: '/goods.json',
    	params: {
            id:1
        }
	}).then(res=>{
		console.log(res.data);
	},err=>{
		console.log(err);
	})
~~~

#### post请求

> post请求一般分为两种类型
>
> 1. `form-data` 表单提交，图片上传、文件上传时用该类型比较多
> 2. `application/json` 一般是用于 ajax 异步请求

示例代码：
**方法一：**

~~~
this.$axios.post('/url',{
				id:1
			}).then(res=>{
				console.log(res.data);
			},err=>{
				console.log(err);
			})
~~~

**方法二：**

~~~
$axios({
	method: 'post',
	url: '/url',
	data: {
		id:1
	}
}).then(res=>{
	console.log(res.data);
},err=>{
	console.log(err);
})
~~~

**form-data请求**

~~~
let data = {
	//请求参数
}

let formdata = new FormData();
for(let key in data){
	formdata.append(key,data[key]);
}

this.$axios.post('/goods.json',formdata).then(res=>{
	console.log(res.data);
},err=>{
	console.log(err);
})
~~~

#### put和patch请求

示例代码：

**put请求：**

~~~
this.$axios.put('/url',{
				id:1
			}).then(res=>{
				console.log(res.data);
			})
~~~

**patch请求：**

~~~
this.$axios.patch('/url',{
				id:1
			}).then(res=>{
				console.log(res.data);
			})
~~~

#### delete请求

示例代码：

**参数以明文形式提交：**

~~~
this.$axios.delete('/url',{
				params: {
					id:1
				}
			}).then(res=>{
				console.log(res.data);
			})
~~~

**参数以封装对象的形式提交：**

~~~
this.$axios.delete('/url',{
				data: {
					id:1
				}
			}).then(res=>{
				console.log(res.data);
			})

//方法二
axios({
    method: 'delete',
    url: '/url',
    params: { id:1 }, //以明文方式提交参数
    data: { id:1 } //以封装对象方式提交参数
}).then(res=>{
	console.log(res.data);
})
~~~

#### 并发请求

> 并发请求：同时进行多个请求，并统一处理返回值

示例代码：

~~~
 this.$axios.all([
	this.$axios.get('/goods.json'),
	this.$axios.get('/classify.json')
]).then(
	this.$axios.spread((goodsRes,classifyRes)=>{
		console.log(goodsRes.data);
		console.log(classifyRes.data);
	})
)
~~~

## axios实例

#### 1、创建axios实例

~~~
let instance = this.$axios.create({
				baseURL: 'http://localhost:9090',
				timeout: 2000
			})
			
instance.get('/goods.json').then(res=>{
	console.log(res.data);
})
~~~

**可以同时创建多个axios实例**

axios实例常用配置：

> - baseURL 请求的域名，基本地址，类型：String
> - timeout 请求超时时长，单位ms，类型：Number
> - url 请求路径，类型：String
> - method 请求方法，类型：String
> - headers 设置请求头，类型：Object
> - params 请求参数，将参数拼接在URL上，类型：Object
> - data 请求参数，将参数放到请求体中，类型：Object

#### 2、axios全局配置

~~~
//配置全局的超时时长
this.$axios.defaults.timeout = 2000;
//配置全局的基本URL
this.$axios.defaults.baseURL = 'http://localhost:8080';
~~~

#### 3、axios实例配置

~~~
let instance = this.$axios.create();
instance.defaults.timeout = 3000;
~~~

#### 4、axios请求配置

~~~
this.$axios.get('/goods.json',{
				timeout: 3000
			}).then()
~~~

以上配置的优先级为：请求配置->实例配置->全局配置

## 拦截器

**拦截器：在请求或响应被处理前拦截它们**

#### 1、请求拦截器

~~~
this.$axios.interceptors.request.use(config=>{
				// 发生请求前的处理

				return config
			},err=>{
				// 请求错误处理

				return Promise.reject(err);
			})

//或者用axios实例创建拦截器
let instance = $axios.create();
instance.interceptors.request.use(config=>{
    return config
})
~~~

#### 2、响应拦截器

~~~
this.$axios.interceptors.response.use(res=>{
				//请求成功对响应数据做处理

				return res //该返回对象会传到请求方法的响应对象中
			},err=>{
				// 响应错误处理

				return Promise.reject(err);
			})
~~~

#### 3、取消拦截

~~~
let instance = this.$axios.interceptors.request.use(config=>{
				config.headers = {
					token: ''
				}
				return config
			})
			
//取消拦截
this.$axios.interceptors.request.eject(instance);
~~~

## 错误处理

~~~
this.$axios.get('/url').then(res={

			}).catch(err=>{
				//请求拦截器和响应拦截器抛出错误时，返回的err对象会传给当前函数的err对象
				console.log(err);
			})
~~~

## 取消请求

~~~
let source = this.$axios.CancelToken.source();

this.$axios.get('/goods.json',{
				cancelToken: source
			}).then(res=>{
				console.log(res)
			}).catch(err=>{
				//取消请求后会执行该方法
				console.log(err)
			})

//取消请求，参数可选，该参数信息会发送到请求的catch中
source.cancel('取消后的信息');
~~~

# XHR

XHR是XML HttpRequest的简写。

> XMLHttpRequest 对象提供了对 HTTP 协议的完全的访问，包括做出 POST 和 HEAD 请求以及普通的 GET 请求的能力。XMLHttpRequest 可以<font color='red'>同步或异步</font>地返回 Web 服务器的响应，并且能够以文本或者一个 DOM 文档的形式返回内容。<font color='red'>XHR接口强制要求每个请求都具备严格的HTTP语义–应用提供数据和URL，浏览器格式化请求并管理每个连接的完整生命周期</font>，所以XHR仅仅允许应用自定义一些HTTP首部，但更多的首部是不能自己设定的，如：Accept-Charset, Accept-Encoding, Access-Control-*Host, Upgrade, Connection, Referer, Origin Cookie, Sec-, Proxy-, 及其他首部浏览器会拒绝绝对不安全的首部重写，以保证应用不能假扮用户代理、用户或请求来源，如Origin由浏览器自动设置，Access-Control-Allow-Origin由服务器设置，如果接受该请求，不包含该字段即可，浏览器发出的请求将作废。
> CORS请求会省略cookie和HTTP认证等用户凭据；
> 客户端被限制只能发送“简单的跨域请求”，包括只能使用GET POSD HEAD三种方式，只能访问通过XHR发送并读取的HTTP首部。

#### 创建XHR对象

~~~
function createXmlHttp(){
var xmlhttp;  
if (window.XMLHttpRequest)  
  {// code for IE7+, Firefox, Chrome, Opera, Safari  
      xmlhttp=new XMLHttpRequest();  
  }  
else  
  {// code for IE6, IE5  
      xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");  
  }  
    return xmlhttp;
}
~~~

向服务器发送请求：

**需要将请求发送到服务器，使用XHR对象的open()和send()方法 **

~~~
function getList(p){ 
        // 1.创建异步交互对象
        var xhr = createXmlHttp();
        // 2.打开连接
        xhr.open("GET","${pageContext.request.contextPath}/hotpage?time="+new Date().getTime()+"&page="+p,true);
        // 3.发送
        xhr.send(null);
        // 4.设置监听
        xhr.onreadystatechange = function(){
            if(xhr.readyState == 4){
                if(xhr.status == 200){
                    //SpringMVC返回的是一个对象，通过@Response转换成json字符串，
                    var pb =eval('('+xhr.responseText+')');
                    alert(pb.totalCount);
                }else{
                        alert("error");
                     }
            }
        }
     
    }
~~~

#### get请求

~~~
var xhr =  new XMLHttpRequest()
xhr.open('get','/getTest?name=fan&age=18',true);
xhr.send();
~~~

#### post请求

需要自己设置请求头

~~~
var xhr = new XMLHttpRequest()
xhr.open('POST','/postTest',true)
xhr.setRequestHeader("Content-type","application/x-www-form-urlencoded")
xhr.send('num=1&des=我爱你')
~~~

示例代码：

~~~
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>xhr</title>
</head>

<body>
    <button onclick="get()">get方法</button>
    <button onclick="post()">post 方法</button>
    <script>
        function get() {

            var xhr = new XMLHttpRequest()
            // open后面有三个参数：
            // 规定请求的类型、URL 以及是否异步处理请求。
            // method：请求的类型；GET 或 POST
            // url：文件在服务器上的位置
            // async：true（异步）或 false（同步） 默认为true
            xhr.open('get', '/getTest?name=fan&age=18')

            // 发送请求到后端（服务器）
            xhr.send()


            // 当请求被发送到服务器时，我们需要执行一些基于响应的任务。
            // 每当 readyState 改变时，就会触发 onreadystatechange 事件。
            // readyState 属性存有 XMLHttpRequest 的状态信息。
            // 在xhr的准备状态发生改变的时候，调用该方法
            xhr.onreadystatechange = function () {
                if (xhr.readyState == 4 && xhr.status == 200) {
                    console.log(xhr.responseText)
                }
            }
        }

        function post() {
            var xhr = new XMLHttpRequest()
            // post 请求方式，接口后面不能追加参数
            xhr.open('post', '/postTest')

            // 如果使用post 请求方式， 而且是以key=value 这种形式提交的
            // 那么需要设置请求头的类型
            xhr.setRequestHeader('content-type', 'application/x-www-form-urlencoded')
            xhr.send('num=1&des=我爱你')

            xhr.onreadystatechange = function () {
                if (xhr.readyState == 4 && xhr.status == 200) {
                    console.log(xhr.responseText)
                }
            }

        }
    </script>
</body>
</html>
~~~

> onreadystatechange 事件
> 当请求被发送到服务器时，我们需要执行一些基于响应的任务。每当 readyState 改变时，就会触发 onreadystatechange 事件。readyState 属性存有 XMLHttpRequest 的状态信息。 

 ![这里写图片描述](https://img-blog.csdn.net/20180830200529358?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5NjEwODg4/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70) 



# Vue知识点总结

## 1、vue框架介绍

> 框架，framework，是能够让程序开发人员更好的专注于业务逻辑的开发，而无需关心底层功能的实现。
>
> vue是一个渐进式 JavaScript 框架，Vue (读音 /vjuː/，类似于 **view**) 是一套用于构建用户界面的**渐进式框架**。与其它大型框架不同的是，Vue 被设计为可以自底向上逐层应用。
> 国人自己的开发的框架，作者是：尤雨溪
>
> vue有两大核心：数据驱动页面、组件化

## 2、vue框架学习内容

> vue、vue-cli脚手架、vue-router路由、ui库、样式预处理器stylus、网络请求axios、状态管理vuex、服务器端渲染

## 3、vue优点、缺点

> 优点：易学、速度快、采用虚拟DOM、数据双向绑定、指令系统、生态圈活跃
>
> 缺点：兼容性，不支持ie8及以下的浏览器、语法报错提示不是特别的准确

## 4、vue常用配置选项

### 4.1速查表

~~~
new Vue({
	el:'#app',		//设置挂载点 类似于querySelector
	data:{},		//初始数据
	menthods:{},	//自定义函数
	watch:{},		//监听
	computed:{},	//计算属性
	filters:{},		//过滤器
	components:{},	//自定义组件
	beforeCreate(){},	//创建之前
	created(){},		//创建完成
	beforeMount(){},	//挂载之前
	mounted(){},		//挂载完成
	beforeUpdate(){},	//更新之前
	updated(){},		//更新完成
	beforeDestroy(){},//销毁之前
	destroyed(){},	//销毁完成
})
~~~

#### el配置选项

指定vue的作用范围，相当于js中querySelector，只会配到满足条件的第一个标签，所以我们一般使用id选择器（不适用class或者标签选择器）。

#### data配置选项

初始化页面数据，初始化的数据会直接挂在vue实例上

#### methods自定义函数

methods，用来存放用户自定义函数

### 4.2常用指令

插值表达式：mustache

~~~
mustache 语法（文本插值） {{ 变量名或者单行JS语法 }}
~~~

#### v-text

> 可以解析data中设置的初始值，v-text把初始值设置到指定的标签内。
>
> 和mustache的区别
>
> 1. 如果要展示的内容是固定的，可以使用v-text
> 2. 如果要展示的内容中的一部分是固定的，可以是使用mustache
>
> 注意：所有v-xxx指令都要写标签的开始标签上

#### v-html

~~~
可以解析带有html标签的内容

<!DOCTYPE html>
<html lang="en">
 
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <!-- 1 引入vue.js 核心文件 -->
    <script src="../node_modules/vue/dist/vue.js"></script>
</head>
 
<body>
    <!-- 2 设置挂载点 -->
    <div id="box">
        <!-- mustache语法 -->
        <!-- 文本插值 -->
        <h3>{{ `小豪：${txt}` }}</h3>
        <p>{{ nu + 10 }}</p>
        <!-- 布尔值 -->
        <p>{{ isshow ? 'true' : 'false' }}</p>
        <!-- 对象类型 -->
        <p>{{ `姓名：${user.name}` }}</p>
        <!-- 数组对象 -->
        <p>{{ `姓名：${users[1].name}` }}</p>
        <hr>
        <!-- v-text 替换源标签内所有内容-->
        <p v-text="user.name">我被v-text内容覆盖了</p>
        <hr>
        <!-- v-html -->
        <p v-text="ele">我不能识别html标签</p>
        <p v-html="ele"></p>
        <hr>
        <!-- 数据双向绑定 -->
        <input type="text" v-model="txt">
        <p>{{ txt }}</p>
    </div>
    <script>
        // 3 示例化vue
        new Vue({
            el: '#box',
            data: {
                txt: 'vue基础学习',
                nu: 20,
                isshow: false,
                ele:'<b>你好，我要加粗显示</b>',
                user: {
                    name: '小代',
                    age: 20
                },
                users: [
                    {
                        name: '小代',
                        age: 20
                    },
                    {
                        name: '小代2',
                        age: 22
                    }
                ]
            }
        })
    </script>
</body>
 
</html>
~~~

#### 条件判断 v-if、v-else-if、v-else

> 根据条件表达式或者布尔值的结果来展示或者不展示指定标签
>
> 当表达式的结果为true时，在页面结构中才会存在指定的标

#### v-show

> 不论条件表达式或者布尔值的结果是什么，v-show指定的标签都会在页面结构中存在
>         当表达式的结果为true时，在页面结构中会显示指定的标签
>         当表达式的结果为false时，在指定的标签上会添加一个display:none属性
> 使用场景：
>     当页面中，要根据指定的内容来频繁的切换某些内容时，要使用v-show

#### 列表渲染

##### v-for语法格式：

~~~
<标签 v-for="(每次遍历的变量名[,每次遍历的元素在数组的下标]) of/in 要遍历的数据源"></标签>

可以根据数组元素数量来生成指定数量的标签
~~~

##### v-for key属性

~~~
遍历的数据源类型是数组时：

第一个参数是数组中每一项元素，第二个参数是数组中每项元素的下标

<ul>
    <li v-for="(user,index) of users">
        <!-- 字符串拼接方式 -->
        <!-- <p>{{ '姓名:'+user.name+'，年龄：'+${user.age} }}</p> -->
        <!-- 模板语法方式 -->
        <p>{{ index }}----{{ `姓名:${user.name}，年龄：${user.age}` }}</p>
    </li>
</ul>

遍历的数据源类型是对象时：

第一个参数是对象中每一项元素的value属性，第二参数是每一项元素的key属性，第三个参数是每一项元素的下标

 <p v-for="(fruite,index,val) of fruites">{{ val }}---{{ index }}---{{ fruite }}</p>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="../node_modules/vue/dist/vue.js"></script>
</head>
<body>
    <div id="app">
        <div v-if="islogin">已登录</div>
        <div v-else>未登录</div>
        <div v-show="islogin">显示</div>
        <div v-show="!islogin">隐藏</div>
        <!-- 
            注意：v-if有更高的切换开销
            v-show有更高的初始渲染开销。
            因此，如果要非常频繁的切换，则使用v-show较好；如果在运行时条件不太可能改变，则v-if较好
         -->
        <hr>
        <ul>
            <li v-for='(item,idx) of arr'>
                {{ idx }}--->{{ item }}
            </li>
        </ul>
        <ul>
            <!-- 数组 -->
            <li v-for="(item,idx) of arrObj">
                <p>{{ idx }}--{{ item }}</p>
                <!-- 对象 -->
                <p v-for="(item,key,idx) of item">{{ `${idx}-${key}-姓名：${item}` }}</p>
            </li>
        </ul>
    </div>
    <script>
        new Vue({
            el:'#app',
            data:{
                islogin:true,
                arr:[11,22,33,44,55,66],
                obj:{
                    name:'小豪',
                    age:22
                },
                arrObj:[
                    {
                        name:'dyh',
                        age:19
                    },
                    {
                        name:'dyh1',
                        age:14
                    },
                    {
                        name:'dyh2',
                        age:12
                    }
                ]
            }
        })
    </script>
</body>
</html>
~~~

#### 事件绑定 v-on

~~~
语法格式：<标签 v-on:事件名=“自定义函数名”></标签>
简写：<标签 @事件名="自定义函数"></标签>

//=========事件绑定
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .box{
            width: 300px;
            height: 300px;
            background-color: orange;
        }
    </style>
    <script src="../node_modules/vue/dist/vue.js"></script>
</head>
<body>
    <div id="app">
        <!-- <button v-on:click="toggle">{{ !isshow ? '显示' : '隐藏' }}</button> -->
        <!-- 简化版 -->
        <button @click="toggle">{{ !isshow ? '显示' : '隐藏' }}</button>
        <div class="box" v-show="isshow">使用行内样式控制显示隐藏</div>
    </div>
    <script>
        new Vue({
            el:"#app",
            data:{
                isshow:true
            },
            methods:{
                toggle(){
                    //Vue中的this 指向Vue实例
                    this.isshow = !this.isshow;
                }
            }
        })
    </script>
</body>
</html>
//=========选项卡练习
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>选项卡-vue</title>
    <script src="../node_modules/vue/dist/vue.js"></script>
</head>
<body>
    <div id="page">
        //根据按钮数组遍历出指定数量的按钮
        //给按钮绑定点击事件，并把当前遍历的元素下标赋值给指定的变量
        <button v-for="(btn,btnidx) of btns" @click="showidx = btnidx">{{ btn }}</button>
        //根据按钮数组遍历出指定数量的内容标签
        //遍历时，拿当前数组下标与指定遍历进行比较，如果相等则显示，否则不显示
        <div class="content" v-for="(btn,index) of btns" v-show="index == showidx">
            //根据数组下标来遍历对象内容
            <p v-for="con of news[index]">{{ con }}</p>
        </div>
    </div>
    <script>
        new Vue({
            el:"#page",
            data:{
                showidx:0,//默认显示哪个新闻内容
                btns:[
                    '北京新闻1','中国新闻2','国际新闻3'
                ],
                news:[
                    {
                        '新闻1':'北京新闻内容1',
                        '新闻2':'北京新闻内容2',
                        '新闻3':'北京新闻内容3'
                    },
                    {
                        '新闻1':'中国新闻内容1',
                        '新闻2':'中国新闻内容2',
                        '新闻3':'中国新闻内容3'
                    },
                    {
                        '新闻1':'国际新闻内容1',
                        '新闻2':'国际新闻内容2',
                        '新闻3':'国际新闻内容3'
                    }
                ]
            }
        })
    </script>
</body>
</html>
~~~

#### 属性绑定 v-bind

~~~
语法格式：<标签 v-bind:属性名=“属性值”></标签>
可以简写：<标签 :属性名=“属性值”></标签>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>样式绑定</title>
    <style>
        #box div{
            width: 100px;
            height: 100px;
        }
        .red{
            color:red;
        }
        .blue{
            color:blue;
        }
    </style>
    <script src="../node_modules/vue/dist/vue.js"></script>
</head>
<body>
    <div id="box">
        <p v-bind:style="styleA">v-bind绑定样式</p>
        <button @click="green">绿色</button>
        <img v-bind:src="imgUrl">
        <!-- v-bing简写方式 : -->
        <p :class="className">简写</p>
        <button @click="toggle">切换</button>
    </div>
    <script>
        new Vue({
            el:"#box",
            data:{
                styleA:{
                    'background-color':'#f00'
                },
                className:'red',
                imgUrl:'https://cn.vuejs.org/images/logo.png'
            },
            methods:{
                green(){
                    this.styleA = {
                    'background-color':'green'
                    }
                },
                toggle(){
                    this.className = 'blue'
                }
            }
        })
    </script>
</body>
</html>
~~~

#### vue常见错误解析

> vue.js:634 [Vue warn]: Do not mount Vue to <html> or <body> - mount to normal elements instead.
>
> vue实例只能挂在到普通的元素标签上，不能是html、body标签，而且推荐使用id选择器来获取标签
>
> [Vue warn]: Property or method "XXX" is not defined on the instance but referenced during render.
>
> vue框架是一个声明式的框架，所以在挂载点内要使用变量时，要定义才能使用。

#### 属性绑定 

##### style

~~~
第一种用法：直接使用变量
<标签 v-bind:sytle="styleA"></标签>
<script>
	new Vue({
		...
		data:{
			styleA:{
				'background-color':'#f00'
			}
		}
	
	})
</script>
 
第二种用法：使用对象
<标签 v-bind:style="{ 属性名:属性值,... }"
注意：如果属性名中包含"-“，把横杠去掉，并横杠后的字母变成驼峰法命名，或者把属性名用引号引起来
如果属性值是一个单词，也要用引号引起来
比如：font-size、background-color... 
​	fontSize、backgroundColor...
第三种用法：使用数组
<标签 v-bind:style="[变量1,变量2]"
~~~

##### class

> 第一种用法：直接使用变量
> <标签 :class="变量名"></标签>
>
> 第二种用法：使用对象
> <标签 :class="{ 类名:表达式或者布尔值 }"></标签>
> 当表达式或者布尔值的结果为true时，表示使用该类名，否则就不使用该类名
>
> 第三种用法：使用数组
> <标签 :class="[‘类名1’,‘类名N’，...]"
> class使用数组时，每一个类名都要加上引号才会被解析成class属性。

#### 表单元素双向绑定 v-model

设计模式：

> MVC：
>     Model 数据模型层
>     View 视图层
>     Controller 控制器层
> 强制的把程序的输入、输出和处理分开
>
> MVVM：
>     Model 数据模型层
>     View 视图层
>     ViewModel 视图模型层

##### 内容展示-输入框

~~~
<div id="box">
    <!-- view -->
    <input type="text" v-model="msg">
    <p>{{ msg }}</p>
</div>
<script>
    new Vue({
    el:"#box",
    data:{ //可以理解为是model
        msg:""
    }
})
</script>
~~~

##### 文本域

~~~
<!-- 文本域 -->
<textarea v-model="article"></textarea>
<p>{{ article }}</p>
<script>
    new Vue({
        el:"#box",
        data:{ //可以理解为是model
            msg:"",
            article:"这是一篇技术文章"
        }
    })
</script>
~~~

##### checkbox

~~~
数组
语法格式：<input type="checkbox" v-model="变量名" value="属性值" />内容

//数组
<input type="checkbox" v-model="hobbies" value="看电影">看电影
<input type="checkbox" v-model="hobbies" value="打游戏">打游戏
<input type="checkbox" v-model="hobbies" value="运动">运动
<p>{{ hobbies }}</p>
<script>
    new Vue({
        el:"#box",
        data:{ //可以理解为是model
            msg:"",
            article:"这是一篇技术文章",
            hobbies:["打游戏"]
        }
	})
</script>
 
//布尔值
<input type="checkbox" v-model="isagree">是否同意协议
<!-- 不使用v-model实现单选 -->
<input type="checkbox" :checked="isagree" @click="isagree = !isagree">是否同意协议
<p>{{ isagree }}</p>
~~~

##### radio

~~~
radio和checkbox使用v-model一定要加上value属性
<div>
    <span>性别：</span>
    <input type="radio" v-model="sex" value="男">男
    <input type="radio" v-model="sex" value="女">女
    </div>
<p>{{ sex }}</p>
<script>
new Vue({
    el:"#box",
    data:{ //可以理解为是model
        ...
        sex:'男'
    }
})
</script>
~~~

##### select

~~~
select双向绑定不需要添加到option标签中，只需要在select的开始标签里写v-model即可。
<select v-model="course">
    <option value="">请选择</option>
    <option value="0">web前端</option>
    <option value="1">java</option>
    <option value="2">ui</option>
</select>
<p>{{ course }}</p>
<script>
    new Vue({
        el:"#box",
        data:{ 
            ...,
            course:0
        }
    })
</script>
~~~

##### 自定义指令

~~~
vue支持我们自定义一些指令来完成一定的操作

Vue.directive('指令名称',{
	inserted:function(el){
		el.focus();//让元素获得焦点
		//其他操作...
	}
})
new Vue({...})
 
注意，自定义指令，需要写在vue被实例化之前
 
//========示例
// 自定义命令需要在vue实例化前定义
Vue.directive('test',{
    //inserted 当指定插入到标签中时
    inserted:function(e){
        //e 是形参，名字可以自定义，此时e就代表添加了自定义指定v-test那个元素
        e.focus();
        e.value = '测试自定义指令'
        console.log(e)
    }
})
new Vue({
    el:'#app'
})
~~~

##### 用户信息收集功能

~~~
<!DOCTYPE html>
<html lang="en">
 
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <!-- <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script> -->
    <link rel="stylesheet" href="../node_modules/bootstrap/dist/css/bootstrap.css">
    <script src="../node_modules/vue/dist/vue.js"></script>
</head>
 
<body>
    <div id="box" class="container">
        <form class="form-horizontal" autocomplete="off">
            <h3 class="text-center">用户信息收集</h3>
            <div class="form-group">
                <label for="name" class="col-sm-2 control-label">姓名：</label>
                <div class="col-sm-6">
                    <input type="text" id="name" class="form-control" v-model.trim="info.name">
                </div>
            </div>
            <div class="form-group">
                <label for="age" class="col-sm-2 control-label">年龄：</label>
                <div class="col-sm-6">
                    <input type="text" id="age" class="form-control" v-model.trim="info.age">
                </div>
            </div>
            <div class="form-group">
                <label for="age" class="col-sm-2 control-label"></label>
                <div class="col-sm-6">
                    <input type="button" value="提交" class="btn btn-primary" @click="add()">
                    <input type="button" value="重置" class="btn" @click="clear()">
                    <input type="button" value="删除所有用户" class="btn btn-warning" @click="delAll">
                </div>
            </div>
        </form>
        <!-- 表格 -->
        <table class="table table-bordered table-hover">
            <thead>
                <tr>
                    <th>姓名</th>
                    <th>年龄</th>
                    <th>操作</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(obj,idx) of users" :idx="idx">
                    <td>{{ obj.name }}</td>
                    <td>{{ obj.age }}</td>
                    <td class="col-sm-3  text-center">
                        <button class="btn btn-primary" @click="edit(idx)">编辑</button>
                        <button class="btn btn-danger" @click="del(idx)">删除</button>
                    </td>
                </tr>
                <tr v-show="users.length==0" class="text-center">
                    <td colspan="3">尚无用户信息显示！！</td>
                </tr>
            </tbody>
        </table>
 
    </div>
    <script>
        new Vue({
            el: '#box',
            data: {
                isidx:-1,//记录数组项
                info: {
                    name: '',
                    age: ''
                },
                users: JSON.parse(sessionStorage.getItem('users')) || [],
                // users: JSON.parse(localStorage.getItem('users')) || [],
            },
            methods: {
                add() {//添加 push 是把指定的内容追加到数组的末尾
                    //为空判断
                    if(this.info.name == '' || this.info.age == ''){
                        alert("请输入完整内容再提交表单！！！");
                        return false;
                    }
                    //判断是 提交 修改
                    if(this.isidx == -1){
                        //添加
                        this.users.push(JSON.parse(JSON.stringify(this.info)));
                    }else{
                        // 修改替换
                        this.users.splice(this.isidx,1,(JSON.parse(JSON.stringify(this.info))));
                        // this.users[this.isidx] = this.info;
                    }
                    //对象的浅拷贝问题
                    this.session();
                    this.clear();
                },
                session(){//本地临时存储
                    sessionStorage.setItem("users",JSON.stringify(this.users));
                },
                clear() {//重置
                    this.isidx = -1; //恢复提交状态
                    this.reset();
                },
                reset() {//清空
                    this.info = {
                        name: '',
                        age: ''
                    }
                },
                edit(id){//编辑信息
                    console.log(this.users[id])
                    // 深浅拷贝
                    this.info = JSON.parse(JSON.stringify(this.users[id]));
                    this.isidx = id; //赋值数组下标
 
                },
                del(id){//删除
                    this.users.splice(id,1);
                    this.session();
                },
                delAll(){
                    // 把数组赋值空
                    this.users = [];
                    // 1删除本地存储中指定key的内容
                    sessionStorage.removeItem('users');
                    // localStorage.removeItem('users');
                    // 2还可以清空本地存储所有数据
                    // sessionStorage.clear();
                    // localStorage.clear();
                }
            }
        })
    </script>
</body>
 
</html>
~~~

##### 修饰符

###### 事件修饰符

> 阻止默认事件
> <标签 @事件名.prevent></标签>
>
> 阻止事件冒泡
> <标签 @事件名.stop></标签>
>
> 捕获事件冒泡
> <标签 @事件名.capture></标签>
> 注意：.capture修饰符不会阻止或者改变事件冒泡，但是会改变冒泡函数执行的顺序。
>
> self修饰符
> <标签 @事件名.self></标签>
> 注意：.self强调的是当前操作的元素只有是它自己本身时，才会触发指定的函数。
>
> 只执行一次
> <标签 @事件名.once></标签>

~~~
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>修饰符</title>
    <script src="../node_modules/vue/dist/vue.js"></script>
    <style>
        .box,.big{
            width: 300px;
            height: 300px;
            background-color: #f00;
        }
        .small{
            width: 100px;
            height: 100px;
            background-color: blue;
        }
    </style>
</head>
<body>
    <div id="app">
        <!-- 阻止默认事件 -->
        <div class="box" @contextmenu.prevent="menu"></div>
        <hr>
        <!-- 阻止事件冒泡 -->
        <div class="big" @click="bigClick">
            <div class="small" @click.stop="smallClick"></div>
        </div>
        <hr>
        <!-- 捕获事件冒泡 -->
        <div class="big" @click.capture="bigClick">
            <div class="small" @click="smallClick"></div>
        </div>
        <hr>
        <!-- self修饰符 -->
        <div class="big" @click.self="bigClick">
            <div class="small" @click="smallClick"></div>
        </div>
        <hr>
        <!-- once修饰符 -->
        <div class="big" @click.self.once="bigClick">
            <div class="small" @click="smallClick"></div>
        </div>
    </div>
    <script>
        new Vue({
            el:"#app",
            methods:{
                menu(){
                    // if(e){
                    //     e.preventDefault();
                    // }else{
 
                    // }
                    // return false;
                    console.log("鼠标右键执行了")
                },
                bigClick(){
                    console.log("大盒子被点击了")
                },
                smallClick(e){
                    // e.stopPropagation();
                    console.log("小盒子被点击了")
                }
            }
        })
    </script>
</body>
</html>
~~~

###### 表单元素修饰符

~~~
.lazy
不再对数据进行实时双向绑定，而是在执行change事件时才进行双向绑定

.number
number修饰符不强制页面用户输入的内容，而是转变数据类型为number
如果写的内容是数字开头，字符串结尾，那么number修饰符会把字符串过滤掉
如果写的内容是字符串开通，数字结尾，那么number修饰符不做任何操作。

.trim
过滤输入内容左右两边的空格，不包含中间的空格。

<body>
    <div id="app">
        <!-- lazy修饰符 -->
        <input type="text" v-model.lazy="msg">
        <p>{{ msg }}</p>
        <hr>
        <!-- number修饰符 -->
        <input type="text" v-model.number="num">
        <button @click="getType">获取数据类型</button>
        <hr>
        <!-- trim修饰符 -->
        <input type="text" v-model.trim="str">
        <p>{{ str }}</p>
    </div>
    <script>
        new Vue({
            el:"#app",
            data:{
                msg:'',
                num:0,
                str:''
            },
            methods:{
                getType(){
                    console.log(typeof this.num)
                }
            }
        })
    </script>
</body>
~~~

###### 其他修饰符

~~~
@事件.enter      回车键
@事件.down      下键
@事件.up           上键
@事件.left 
@事件.right
@事件.esc
@事件.tab
~~~

#### 数据本地存储

> localStorage
> sessionStorage
> 方法：
>
>     数据添加：setItem('key',value)      		     sessionStorage.setItem("users",JSON.stringify(this.users))
>     数据读取：getItem('key')
>             sessionStorage.getItem('users')
>    
>     删除数据：removeItem('key')
>         根据指定的key来进行删除
>             sessionStorage.removeItem('users');
>             localStorage.removeItem('users');
>    
>     删除本地存储中所以数据：clear()
>             sessionStorage.clear();
>             localStorage.clear();

#### 模拟跨域请求

~~~
基本步骤
第一步：创建一个script标签
var s = document.createElement("script");

第二步：设置script标签的src属性
s.src = "http://suggestion.baidu.com/su?cb=getwd&wd="+this.ipt;

第三步：把生成好的script标签追加到页面中
document.body.append(s)

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .select{
            background-color: coral;
            color: #fff;
        }
    </style>
    <!-- <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script> -->
    <script src="../node_modules/vue/dist/vue.js"></script>
</head>
<body>
    <div id="root">
        <!-- @input="search" -->
        <input type="text" v-model="ipt"  @keydown.down="down" @keydown.up.prevent="up" @keydown.enter="enter">
        <button @click="search">搜索</button>
        <ul>
            <li v-for="(item,idx) of arr" :class="{select:idx==isid}">{{ item }}</li>
        </ul>
    </div>
    <script>
        const vm = new Vue({
            el:'#root',
            data:{
                arr:[],
                ipt:'',
                isid:-1
            },
            methods:{
                search(){
                    if(this.ipt == '')return;
                    // cb 回调函数名称
                    // wd 要搜索的关键词
                    var s = document.createElement("script");
                    s.src="http://suggestion.baidu.com/su?cb=callback&wd="+this.ipt;
                    // s.src="https://sp0.baidu.com/5a1Fazu8AA54nxGko9WTAnF6hhy/su?cb=callback&wd="+this.ipt;
                    document.body.append(s);
                },
                down(){
                    this.isid++;
                    if(this.isid>3){
                        this.isid=-1;
                    }
                },
                up(){
                    this.isid--;
                    if(this.isid<0){
                        this.isid=4;
                    }
                },
                enter(){
                    console.log(this.arr[this.isid],this.isid)
                    if(this.isid == -1 || this.isid == 4){
                        window.open("https://www.baidu.com/s?wd="+this.ipt);
                    }else{
                        window.open("https://www.baidu.com/s?wd="+this.arr[this.isid]);
                    }
                }
            },
            watch:{//监听
                // ipt:function() 简写
                ipt(newVal,oldVlal){
                    if(newVal == ''){
                        return false;
                    }
                    console.log(newVal);
                    console.log(oldVlal);
                    var s = document.createElement("script");
                    s.src="http://suggestion.baidu.com/su?cb=callback&wd="+newVal;
                    document.body.append(s);
                }
            }
        });
        function callback(res){
            //现在收索显示条数
            res.s.length=4;
            vm.arr = res.s;
        }
    </script>
</body>
</html>
~~~

#### 侦听/监听器 watch

可以对页面中已经定义好的变量进行监听，一旦变量值发生了改变，那么就可以执行一定操作。

##### 普通监听

~~~
语法格式一：
new Vue({
	el
	data
	methods
	watch:{
		变量名(newVal[,oldVal]){
			业务逻辑代码...
		}
	}
})
 
语法格式二：
new Vue({
	el
	data
	watch:{
		要监听的变量名:{
			handler([newVal,oldVal]){
				业务逻辑...
			}
		}
	}
})
~~~

##### 深度监听

~~~
如果要监听的变量类型为对象或者数组时，普通监听无法实现监听变化的效果，需要使用深度监听

new Vue({
	el
	data
	watch:{
		要监听的变量名:{
			handler([newVal,oldVal]){
				业务逻辑...
			},
			deep:true//显示的进行深度监听
		}
	}
})

<body>
    <div id="app">
        <p>普通监听</p>
        <input type="text" v-model="msg">
        <p v-show="newVal!=''">最新数据：{{ newVal }} -- 旧数据：{{ oldVla }}</p>
        <p>深度监听</p>
        <input type="text" v-model="userinfo.name">
        <p>{{ userinfo.name }}</p>
        <div v-for="user of users">
            姓名：<input type="text" v-model="user.name"><br>
            年龄：<input type="text" v-model="user.age"><br>
        </div>
    </div>
    <script>
        new Vue({
            el:'#app',
            data:{//数据
                msg:'',
                newVal:'',
                oldVla:'',
                userinfo:{
                    name:''
                },
                users:[
                    {
                        name:'小明',
                        age:18
                    },
                    {
                        name:'小芳',
                        age:19
                    }
                ]
            },
            methods:{//自定义方法
 
            },
            watch:{//侦听
                // 普通监听
                msg(newVal,oldVla){
                    this.newVal = newVal;
                    this.oldVla = oldVla;
                    console.log("数据发送了变化:"+newVal);
                },
                //深监听
                userinfo:{
                    handler(newVal){
                        console.log('用户信息发送改变:'+newVal.name);
                    },
                    deep:true //是否深度监听 默认false
                },
                users:{
                    handler(newVla){
                        console.log('用户信息发送改变');
                    },
                    deep:false
                }
            }
        })
    </script>
</body>
~~~

#### 计算属性 computed

~~~
作用：
如果页面上有需要频繁进行数学运算之后得到结果内容时，可以使用计算属性来实现。
​可以不用在data中定义计算结果的初始变量，只要在挂载点内使用了计算属性的结果后，计算属性对应的函数会自定触发。
​    计算属性依赖的数据，一旦发生改变，那么计算属性的逻辑函数会重新的执行

//语法格式
new Vue({
	el
	data
	methods
	watch
	computed:{
		要计算的结果(){
			业务逻辑...
			return 结果;
		}
	}
})
 
//=======示例
    <div id="app">
        <input type="text" v-model.number="num1"> + <input type="text" v-model.number="num2"> = {{ result }}
    </div>
    <script>
        new Vue({
            el:'#app',
            data:{
                num1:'',
                num2:''
            },
            computed:{
                result(){
                    return this.num1 + this.num2;
                }
            }
        })
    </script>
~~~

##### 计算属性的get和set

~~~
在计算属性中内置了两个方法，一个是get，用来读取数据，一个是set用来设置数据。
在vue中默认使用的是get方法，只要在页面中使用了计算属性的变量或者计算属性变量依赖的数据发生了改变时，get方法会重新执行。

 <div id="app">
 {{ sum }}
 </div>
 <script>
     let vm = new Vue({
         el:"#app",
         data:{
             num1:10,
             num2:20
         },
         computed:{
             sum:{
                 get(){
                     console.log('get')
                     return this.num1 + this.num2
                 },
                 set(){
                 	console.log('set')
                 }
             }
         }
     })
</script>

只有给计算属性的变量直接赋值时，set函数才会执行

可以在谷歌浏览器的控制台中进行测试
vm.sum = 100 //此时自动执行set函数
vm.num1 = 20 //此时自动执行get，因为计算属性依赖于num1
~~~

##### 计算属性和监听的区别

> 相同之处：
> 都可以根据依赖的数据变化，自动的触发相应的逻辑函数代码
>
> 不同之处：
> 计算属性的逻辑函数在页面使用了计算属性的变量后，就会自动的触发对应的逻辑函数
> 监听是只有依赖的数据发生了变化的时候，才会触发对应的逻辑函数
>
> 注意事项：
> 如果计算属性和监听，都对相同的数据进行操作，那么就会产生冲突互相影响。

##### 计算属性computed和methods的区别

> methods中定义的函数，只要在页面上调用，就会无条件的执行
>
> 计算属性computed中定义的函数，依赖的数据不发生变化时，只是读取，不会重新计算
>
> 计算属性特点：
>
> 1. 依赖于数据，如果数据发生变化，那么计算属性会自动更新
> 2. 计算属性的结果无需在data中定义，在页面中可以直接使用
> 3. 会在vue实例上产生一个缓存，如果依赖的数据不发生变化，则会读取缓存，提高性能。

#### 过滤器filters

对页面中要展示的数据进行处理，满足页面数据展示的需求

##### 局部定义 filters

~~~
new Vue({
	el
	data
	filters:{
		'过滤器名称':function(形参1[,形参N...]){
			业务逻辑
			return 结果
		}
	}
})

使用：
需要通过管道符来使用定义好的过滤器，要进行过滤的源数据 | 过滤器名称

传递额外参数：
管道符左边的是过滤器中的第一个参数，在管道符右边过滤器名称处，可以通过小括号来传递额外的参数。

<div id="app">
    <!-- 使用过滤器 -->
	总价格：{{ totalPrice | formatPrice(2) }}
</div>
<script>
    new Vue({
        el:"#app",
        data:{
            totalPrice:2999.9
        },
        filters:{
            //定义一个格式化价格的过滤器
            formatPrice(val,n=1){
            	return '￥'+val.toFixed(n)+'元';
            }
        }
    })
</script>
~~~

##### 全局定义 filter

> //实例化vue之前
> Vue.filter('过滤器名称',function(形参1[,形参N]){
> 	...
> });
> new Vue({})
>
> 全局定义的过滤器，可以在当前页面中的所有vue实例中来使用过滤器

#### 过滤动画

> <transition></transition>标签
> 当元素通过v-if、v-show或者动态组件的方式，进行展示或者不展示标签的情况下，才可以设置过渡动画

#### 内置类名

~~~
匿名类名：
    进入状态
    ​    v-enter            设置进入开始状态的样式
    ​    v-enter-active 设置进入进行中状态的样式
    ​    v-enter-to    设置进入结束状态的样式
    离开状态
    ​    v-leave            设置离开开始状态的样式
    ​    v-leave-active 设置离开进行中状态的样式
    ​    v-leave-to    设置离开结束状态的样式
注意：一定要给需要过渡动画的标签用<transition>标签进行包裹，这样内容的类名才会起作用

具名类名：
如果页面上有多个元素需要设置不用的过渡动画效果，可以给transition标签设置一个name属性来进行区分，一旦设置了name属性，内置的类名就不能以.v-开头(.v-是所有匿名过渡动画的统一前缀)了，应该以.name属性的值-开头

<style>
    .content {
        width: 200px;
        height: 200px;
        background-color: coral;
    }
    .page {
        position: absolute;
        left: 300px;
        background-color: orange;
    }
 
    /* 离开动画 */
    .v-leave {
        /* 设置离开开始状态样式 */
        opacity: 1;
    }
    .v-leave-active {
        /* 设置离开进行中状态样式 */
        transition: opacity 2s;
    }
    .v-leave-to {
        /* 设置离开结束状态的样式 */
        opacity: 0;
    }
    /* 进入动画 */
    .v-enter {
        opacity: 0;
    }
    .v-enter-active {
        transition: opacity 4s;
    }
    .v-enter-to {
        opacity: 1;
    }
 
    /* 具名类名 */
    .page-leave{
        left: 300px;
    }
    .page-leave-active{
        transition: left 3s;
    }
    .page-leave-to{
        left: 0px;
    }
 
    .page-enter {
        left: 0px;
    }
    .page-enter-active {
        transition: left 2s;
    }
    .page-enter-to {
        left: 300px;
    }
</style>
</head>
<body>
<div id="app">
    <button @click="isshow = !isshow">toggle</button>
    <!-- 匿名方式 -->
    <transition>
        <div class="content" v-if="isshow"></div>
    </transition>
    <!-- 具名方式 -->
    <transition name="page">
        <div class="content page" v-show="isshow"></div>
    </transition>
</div>
<script>
    new Vue({
        el: '#app',
        data: {
            isshow: true
        }
    })
</script>
~~~

#### animate.css动画库插件

~~~
第一步：引入animate.css，可以用npm按照或者直接引入在线链接
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.0.0/animate.min.css" />
 
第二步：给需要设置过渡动画的标签添加transition标签
<transition>
      <div id="box" v-show="isshow"></div>
</transition>
 
第三步：给transition标签设置进入和离开的动画属性
<div id="app">
    <transition 
        leave-active-class="animate__animated animate__backOutDown" 
        enter-active-class="animate__animated animate__backInDown"
    >
    	<div id="box" v-show="isshow"></div>
    </transition>
    <button @click="isshow = !isshow">切换</button>
</div>
 
注意：设置动画属性的内容时，都要以animate__开头（是双下划线），具体用法见官网
~~~

## 5、vue生命周期

<font color='red'>vue实例从创建、挂载、更新、销毁的一个完整的过程叫生命周期</font>

#### 钩子函数

> <font color='green'> 页面渲染期： </font>
> 页面加载时自动触发的钩子函数：
> beforeCreate    创建之前
> created              创建完成
> beforeMount    挂载之前
> mounted            挂载完成    ***** 发起网络请求
>
> <font color='green'> 页面更新期： </font>
> 页面上的数据有变化时，会自动触发的钩子函数：
> beforeUpdate     更新之前
> updated                更新完成
>
> <font color='green'> 页面销毁期：</font>
> vue实例被销毁时会自动触发的钩子函数：
> beforeDestroy    销毁之前
> destroyed            销毁完成

~~~
<div id="app">
    <input type="text" v-model="msg">
    <p>{{ msg }}</p>
</div>
<button class="destroy">销毁</button>
<button class="mount">挂载</button>
<script>
    let vm = new Vue({
        el:'#app',
        data:{
            msg:"vue生命周期"
        },
        // 1执行顺序和声明顺序无关
        //页面渲染期
        beforeCreate(){
            console.log('--------beforeCreate 创建之前--------');
            console.log(this.$el);//undefined
            console.log(this.$data);//undefined
        },
        created(){
            console.log('--------created 创建完成--------');
            console.log(this.$el);//undefined
            console.log(this.$data);//Object
        },
        beforeMount(){
            console.log('--------beforeMount 挂载之前--------');
            console.log(this.$el);//<div id="app">.值还没有解析.</div>
            console.log(this.$data);//Object
        },
        mounted(){
            console.log('--------mounted 挂载完成--------');
            console.log(this.$el);//<div id="app">.已经解析成data中对应值.</div>
            console.log(this.$data);//Object
        },
        // 2页面更新期
        beforeUpdate(){
            console.log('--------beforeUpdate 更新之前--------');
            console.log(this.$el);//<div id="app">.已经更新成data中对应值.</div>
            console.log(this.$data);//Object
        },
        updated(){
            console.log('--------updated 更新完成--------');
            console.log(this.$el);//<div id="app">.已经更新成data中对应值.</div>
            console.log(this.$data);//Object
        },
        // 3页面销毁
        beforeDestroy(){
            console.log('--------beforeDestroy 销毁之前--------');
            console.log(this.$el);//<div id="app">.data中对应值.</div>
            console.log(this.$data);//Object
        },
        destroyed(){
            console.log('--------destroyed 销毁完成--------');
            console.log(this.$el);//<div id="app">.data中对应值.</div>
            console.log(this.$data);//Object
        }
    });
    console.log(vm);
    const desBtn = document.querySelector(".destroy");
    const mouBtn = document.querySelector(".mount");
    desBtn.onclick = function(){
        vm.$destroy();//销毁vue实例
    }
    mouBtn.onclick = function(){
        vm.$mount();//挂载vue实例 但 更新周期 不会执行了
    }
</script>
~~~

## 6、组件components

> 组件是vuejs中最强大的功能之一，组件可以扩展html元素，封装可复用的代码，在大型项目中，为了合理分工、代码复用。每一个组件都是一个vue的实例，所以vue实例中的配置选项，在组件都可以使用。

#### 组件的注册

~~~
局部注册
new Vue({
	el
	data
	...
	components:{
		组件名称:{
			template:"组件内容"
		}
	}
})
注意：template是组件的模板内容，必须要设置
 
全局注册
全局注册的组件，可以在所有的vue实例中使用
Vue.component('组件名称',{
	template:'组件内容'
})
new Vue({...})
使用：
在挂载点内，把组件名称当成一个普通的html标签去使用即可
//==========示例
<div id="root">
    <!-- 使用自定义组件 -->
    <mydiv></mydiv>
    <my-div></my-div>
</div>
<script>
    // 局部注册组件
    new Vue({
        el:"#root",
        components:{
            mydiv:{
                template:"<h1>这是第一个自定义组件1</h1>"
            },
            myDiv:{
                template:"<h1>这是第二个自定义组件</h1>"
            }
        }
    })
</script>
~~~

#### 组件模板内容

> vue2组件的模板内容中，只能有一个根标签，vue3组件的模板内容中，可以出现多个根标签

##### template模板/标签的使用

~~~
template标签不会被浏览器解析，并且还可以在其中编写html代码
组件中的template属性和template标签是两个不同的东西，不要混为一谈
鉴于组件的template属性中直接编写页面内容不是很方便，所以我们可以结合template标签来设置组件的内容。
但是需要把template属性和template标签关联起来

<div id="app">
    <first></first>
</div>
<!-- 需要给template标签设置一个唯一的属性，用来区分不用的template标签 -->
<template id="first">
    <div>
        <h1>first组件</h1>
        <p>测试</p>
    </div>
</template>
<script>
    new Vue({
        el:"#app",
        components:{
            first:{
                // 关联指定的template标签
                template:"#first"
            }
        }
    })
</script>
~~~

template代码优化

~~~
由于组件的基本构成是一个对象，当页面中组件数量比较多时，注册组件时的代码量比较多，看上去非常混乱，所以我们可以把组件的构成提前定义好。

<script>
    var first = {
    	template:"#first"
    }
    var mysecond = {
    	template:"#second"
    }
    new Vue({
        el:"#app",
        components:{
        	first,mysecond
        }
    })
</script>
~~~

#### 组件的嵌套

##### extend方法

~~~
<div id="app">
        <parent class="p"></parent>
    </div>
    <script>
        var child = Vue.extend({
            template:"<div>这是一个子组件</div>"
        })
        var parent = Vue.extend({
            template:"<div>这是一个父组件<child></child></div>",
            components:{
                child:child
            }
        })
        new Vue({
            el:"#app",
            components:{
                parent
            }
        });
    </script>
~~~

##### 直接注册使用

~~~
使用template设置好组件的模板内容，然后用components来注册

<template id="main">
    <div>
        <my-left class="left"></my-left>
        <my-right class="right"></my-right>
    </div>
</template>
<script>
    var myLeft = { template:"#left" };
    var myRight = { template:"#right" }
    var myMain = { 
        template:"#main",
        components:{
        	myLeft,myRight
        }
    };
    new Vue({
        el:"#root",
        components:{
            myMain
        }
    })
</script>
~~~

**组件中的data是一个函数，通过return返回数据**

## 7、脚手架

#### 安装

> 版本的问题：稳定版 2.9.6  最新版 4.X
> 基本环境 ：node
> (1)webpack  全局安装
> npm i webpack -g
>
> (2)vue-cli  全局安装
> npm i vue-cli -g

#### 初始化项目

> 用命令行进入到一个非系统盘的目录中  初始化项目
> vue init webpack projectname
>
> 注意：项目名称不能包含中文和空格
>
> **初始化项目步骤：**
>
> 1. 先执行初始化命令，回车
> 2. Project name (myapp) ?
>    确认项目名称，不需要改，则回车
> 3. Project Description (A vue.js project)
>    项目描述，不需要改，则回车
> 4. Author 
>    项目作者，不需要改，则回车
> 5. Vue build (Use arrow keys)
>    项目运行模式
>    Runtime + Compiler 运行时编译 回车
> 6. Install vue-router? (Y/n)
>    是否安装路由，暂时不安装，输入 n 回车
> 7. Use ESLint to lint your code? (Y/n)
>    是否使用eslint验证代码格式，暂时不需要，输入n，回车
> 8. Set up unit tests (Y/n) 
>    是否创建单元测试，暂时不需要，输入n，回车
> 9. Setup e2e tests with Nightwatch? (Y/n)
>    是否用端对端测试，暂时不需要，输入n，回车
> 10. Should we run `npm install` for you after the project has been created?
>     项目初始化方式，选择npm

#### 运行项目

> 在命令行中进入到项目根目录下，然后执行
> npm run dev

#### 项目目录结构

~~~
project 项目根目录
​    build        项目打包依赖目录
​    config        项目配置文件目录
​    node_modules 项目依赖目录
​    src                项目源码目录（项目的主战场）
​        assets    项目静态资源目录
​        components    项目自定义组件
​        App.vue        项目根组件
​        main.js        项目启动文件
​    static        存放通过域名直接访问的静态资源
​    .babelrc        es6语法解析配置
​    .editorconfig    编辑器配置文件
​    .gitignore    git忽略文件配置
​    .postcssrc.js    postcss配置文件
​    index.html    项目首页
​    package.json    项目依赖配置文件
~~~

#### 项目执行顺序

> index.html
> /src/main.js
> /src/App.vue
> /src/components/HelloWorld.vue

#### vue组件构成

> - 模板 template 【必须】
> - js script
> - css style

##### devtools

devtools是vue全家桶中的一个浏览器插件，作用是让我们开发人员能够非常清楚的了解项目的组件结构和数据及状态 

安装：访问谷歌商店，搜索vue关键词==>Vue.js devtools插件 添加扩展即可

使用：打开vue项目页面后，然后打开浏览器的调试工具，就会看到一个vue的选项点击vue选项后，看到当前vue项目的组件结构及每一个组件上的数据

##### scoped

> 为了防止样式污染，可以给组件的style标签设置一个scpoed属性，来限制样式仅在当前组件起作用
> 使用：<style scoped></style>

## 8、组件通信

#### 父子组件-porps验证

> 通过自定义属性和props来实现
>
> 只是在控制台中给出警告，但不影响程序的运行
>
> (1)在父组件中使用子组件时，通过自定义属性来传递数据 
> <v-child imgurl="./1.jpg" title="学习群" desc="组团学习高校"></v-child>
>
> (2)在子组件中用过props来接收父组件传递的数据
> <script>
> export default {
>     props:['imgurl','title','desc']
> }
> </script>

##### 1、验证数据类型

> 在子组件中，接收数据时，props写成一个对象
> //写法一：（如果只验证数据类型）
> props:{
> 	要接收的参数名:类型名称
> }
> //写法二：（不仅仅验证数据类型，还可以做其他的验证）
> props:{
> 	要接收的参数名:{
> 		type:类型名称
> 	}
> }
>
> 支持的数据类型：
>     Boolean、String、Number、Function、Object、Array、Symbol

##### 2、验证必填

不可与默认值同时使用

> props:{
> 	要接收的参数名:{
> 		type:类型名称,
> 		required:true//设置此属性为必填项
> 	}
> }

##### 3、默认值

不可与必填项同时使用

> 如果父组件在使用子组件时，没有传递子组件需要的数据时，会使用默认值来代替
> //写法1
> props:{
> 	要接收的参数名:{
> 		type:'',
> 		default:'默认值'
> 	}
> }
> //写法2
> props:{
> 	要接收的参数名:{
> 		type:'',
> 		default:function(){
> 			return '默认值'
> 		}
> 	}
> }

##### 4、自定义验证规则

> props:{
> 	要接收的参数名:{
> 		type:'',
> 		validator:function(形参){
> 			验证规则逻辑
> 			return 布尔值
> 		}
> 	}
> }
>
> 只要父组件给子组件传递了要验证的参数时，validator中的验证规则函数会自动触发
> 如果规则函数返回true，表示验证成功
> 如果规则函数返回false，表示验证失败（就会在控制台中给出验证失败的警告）

#### 子父组件

1. 数据是由父组件传递给子组件，如果子组件想要改变数据，则要通过父组件传递一个自定义事件，然后在子组件中触发这个事件来实现数据的改变。
2. <font color='red'> 通过自定义事件和$emit实现 </font>

##### 1、父组件在使用子组件时，传递一个自定义事件

~~~
<v-news 
    v-for="(item,index) of newsarr" 
    :key="index" 
    :title="item.title" 
    :count="item.count"
    :index="index"
    @addcount="add"
></v-news>
 
//addcount就是一个自定义事件，对应一个父组件级别的函数
~~~

##### 2、子组件

通过自身的methods自定义函数，通过this.$emit来触发父组件传递的这个自定义事件。

~~~
<template>
	<div>
		<button @click="viewnews(index)">访问</button>
	</div>
</template>
<script>
export default {
    props:['title','count','index'],
    methods:{
        viewnews(i){
            //$emit 触发父组件传递过来的自定义事件
            // 第一个参数是要触发的事件名称
            // 第二个参数是要传递的参数
            this.$emit("addcount",i)
        }
    }
}
</script>
~~~

##### 非父子组件

通过eventbus和$on实现

##### 1、创建一个公用的容器，用来进行数据的发送和接收

> 在src/main.js 中，vue实例化之前，给vue的原型上增加一个公用的容器
> Vue.prototype.容器名称 = new Vue();
> new Vue({...})
>
> 容器名称：可以为 $but 等自己定义

##### 2、$emit

> 在数据发送的组件中，通过公用容器中的$emit方法来触发一个函数，并发送数据
> methods:{//自定义函数
> 	sendData(形参){
> 	this.容器名称.$emit("事件名称","要传递的数据")
> 	}
> }

##### 3、$on

> 在其他任意组件，通过公用容器中的$on方法来监听事件名称，用来接收发送端传递的数据
> mounted(){//钩子函数 挂载完成
> 	this.容器名称.$on('事件名称',(形参)=>{
> 		...
> 	})
> }

## 8、组件进阶

### is属性

###### 1、改变html标签的默认结构约束

~~~
<table>
    <tr is="h3">这是一个标题</tr>
    <tr is="my-child"></tr>
</table>
~~~

###### 2、动态组件

需要结合非父子组件通信和is属性，来实现页面上，展示不同的组件内容

**（1）在左侧菜单组件中，进行数据的展示和点击事件的编写**

~~~
<template>
  <div class="menu">
    <ul>
      <li 
        v-for="(menu, index) of menus" :key="index"
        @click="sendtag(menu.tagname)"
    >{{ menu.title }}</li>
    </ul>
  </div>
</template>
<script>
export default {
  data() {
    return {
      menus: [
        {
          title: "系统设置",
          tagname: "setting"  //需要和import 设置的值对应
        },
        {
          title: "用户管理",
          tagname: "user"
        },
        {
          title: "个人中心",
          tagname: "profile"
        }
      ]
    };
  },
  methods:{
      sendtag(t){
        this.$bus.$emit('changeTag',t)
      }
  }
};
</script>
<style lang="css">
.menu ul {
  text-align: center;
}
.menu ul li {
  padding: 10px;
}
</style>
~~~

**（2）在content组件中，引入所有需要展示的页面组件，并注册，然后通过事件监听来接收数据**

~~~
<template>
    <div class="content">
        <!-- <setting></setting>
        <user></user>
        <profile></profile> -->
        <!-- 动态组件 -->
        <table :is="tagname"></table>
    </div>
</template>
<script>
import setting from './Setting'
import user from './User'
import profile from './Profile'
export default {
    data(){
        return{
            tagname:'setting'
        }
    },
    components:{
        setting,user,profile
    },
    mounted(){//挂载完成
        this.$bus.$on('changeTag',(tag)=>{
            this.tagname = tag;
        })
    }
}
</script>
~~~

### ref属性

vue中一般不直接操作DOM结构，如果必须要进行DOM结构操作，可以给标签或者组件添加ref属性

### 普通字符串

~~~
<h3 ref="myh3">XXX管理系统</h3>
<script>
	mounted(){//钩子函数 挂载完成 操作DOM
    	this.$refs.myh3.innerHTML = '小小后台管理系统'
    }
</script>
~~~

### 数组

~~~
如果在v-for的标签上，设置了ref属性，那么通过$refs获取到的DOM节点的数组
<li v-for ref="myli"></li>
<script>
	mounted(){
    	console.log(this.$refs.myli)
    }
</script>
~~~

### 自定义组件

~~~
ref更多的应用在自定义组件上，可以实现父子组件通信的效果

注意：
ref只能在组件挂载完成后使用
~~~

#### jQuery组件

~~~
安装：
1、直接引入jquery.js文件-->在项目根目录的index.html文件中
<script src="https://cdn.staticfile.org/jquery/1.10.2/jquery.min.js"></script>
2、npm安装
npm i jquery --save
在vue组件中使用jquery时进行引入
import $ from 'jquery'
使用：$(".box").slideUp(1000)
把jquery挂载到原型上(/src/main.js上)
    import jq from 'jquery'
    Vue.prototype.$ = jq
    new Vue({...})
    
把jquery挂到原型上之后，在任意的组件里都可以通过this.$来使用jquery
~~~

#### bootstrap组件

~~~
安装：
1、直接引入bootstrap.css文件-->在项目根目录的index.html文件中
<link href="https://cdn.bootcdn.net/ajax/libs/twitter-bootstrap/4.5.0/css/bootstrap-grid.css" rel="stylesheet">
2、npm安装
npm i bootstrap --save
在vue组件中使用bootstrap时进行引入 (/src/main.js上)
import 'bootstrap/dist/css/bootstrap.css'
使用：<button class="btn btn-danger">测试按钮</button>

引入成功后，就可以正常使用
~~~

### 插槽

如果需要在父组件使用子组件时，来分发一些不同的内容展示在子组件中，可以使用插槽来实现

#### slot匿名插槽

~~~
是在子组件中，写入一个<slot>标签，设置一个插槽的位置。
这样，在父组件使用子组件时，就可以在子组件内写入内容，并展示在子组件的插槽处。

父组件：
<v-index>
    <p>父组件的标题</p>
    <p>父组件的内容</p>
</v-index>
 
子组件：
<div class="index">
    <h1>index组件</h1>
    <!-- 插槽（匿名） -->
    <slot></slot>
</div>
~~~

#### 具名插槽

~~~
如果子组件中有多个插槽，来展示不同的内容，用匿名插槽就会出现内容重复的现象。
为了区分不同的插槽，可以给slot来设置一个name属性来区分它们。

子组件：
<div class="index">
    <!-- 插槽（具名） -->
    <slot name="top"></slot>
    <h1>index组件</h1>
    <slot name="bottom"></slot>
</div>
 
父组件：
<v-index>
    <p slot="top">父组件的标题</p>
    <p slot="bottom">父组件的内容</p>
</v-index>
~~~

#### 作用域插槽

~~~
在使用插槽的时候，希望父组件可以控制插槽的结构和内容，子组件只做遍历循环
子组件的一部分DOM结构由外部传

子组件：
<template>
    <div>
        <p>child组件</p>
        <ul>
            <slot name="default" v-for="item of arr" :childitem="item"></slot>
        </ul>
    </div>
</template>
<script>
export default {
    data(){
        return{
            arr:[
                'web大前端',
                'java开发',
                'ui设计',
                '软件测试'
            ]
        }
    }
}
</script>
 
父组件：
<template>
  <div class="app">
      <v-child>
            <template v-slot:default="props">
                <li>{{ props.childitem }}</li>
            </template>
      </v-child>
  </div>
</template>
<script>
import vChild from './components/Child'
export default {
    components:{
        vChild
    }
};
</script>
<style>
</style>
~~~

## 9、路由

> 让用户能够根据不同的浏览器地址来展示不同的页面组件
>
> **<font color='orange'>SPA：single page application 单页面应用</font>**    
>
> 概念：就是只有一个Web页面的应用，是加载单个HTML页面，并在用户与应用程序交互时动态更新该页面的Web应用程序。
>
> 与传统多页面程序的区别：
>     传统多页面程序：每次请求服务器返回的都是一个完整的页面
>     单页应用程序：只有第一次会加载页面, 以后的每次请求, 仅仅是获取必要的数据.然后, 由页面中js解析获取的数据, 展示在页面中
> 优势：
>     1 减少了请求体积，加快页面响应速度，降低了对服务器的压力
>     2 更好的用户体验，让用户在web app感受native app的流畅
> 概念：
> Vue Router 是 Vue.js 官方的路由管理器。它和 Vue.js 的核心深度集成，让构建单页面应用变得易如反掌。包含的功能有：
>     嵌套的路由/视图表
>     模块化的、基于组件的路由配置
>     路由参数、查询、通配符
>     基于 Vue.js 过渡系统的视图过渡效果
>     细粒度的导航控制
>     带有自动激活的 CSS class 的链接
>     HTML5 历史模式或 hash 模式，在 IE9 中自动降级
>     自定义的滚动条行为

#### 安装路由

~~~
1安装vue-router插件
    npm i vue-router --save

2在vue项目中引入vue-router，并实例化后挂载到vue的配置选项上 /src/main.js
    import Router from 'vue-router'
    Vue.use(Router)
    //实例化vue-router 路由管理器
    let router = new Router({
        routes:[]//路由配置映射表
    })
    new Vue({
        el: '#app',
        components: { App },
        router,
        template: '<App/>'
    })

3创建几个页面组件
    .....

4配置路由映射表规则
    let router = new Router({
        //路由配置映射表
        routes:[
            {
                path:'/index',//path是浏览器地址中的关键词
                component:Index//与关键词匹配的页面组件
            },
            {
                path:'/login',
                component:Login
            }
        ], 

         mode:"history"//去除 #/
    })

5在App.vue中添加路由出口组件
    内置组件  router-view

作用：
​    根据浏览器地址中的关键词和路由映射表中的关键词匹配时
​    会把匹配到的组件模板内容展示到此处
~~~

#### 重定向 redirect

~~~
当某个路由规则没有匹配到时，我们可以设置一个默认的页面（首页/404页面） 

/src/router/index.js文件中
export default new Router({
    routes: [
        {
            path:'/index',component:Index
        },
        {
            path:'/login',component:Login
        },
        {
            path:'*',
            redirect:'/index'
            // component:Login//这个不是重定向，只是在没有匹配到路由规则时，默认展示的组件内容
        }
    ]
})
 
注意：如果需要让浏览器地址进行变化，那么必须使用redirect属性，不能使用component
~~~

#### 路由导航

能够让访问网站的用户，快速的访问到指定的页面

#### 内置标签 router-link

~~~
必要属性：to，具体的某一个路由规则path属性的值
​    选填项：
​    active-class，模糊匹配，可以设置激活状态router-link的样式
​    exact-active-class，精确匹配，可以设置激活状态router-link的样式

<router-link to="/index">首页</router-link>
<router-link to="/login">登录</router-link>
<!-- 路由出口/可变区 -->
<router-view />
~~~

#### 编程式导航

> 在vue-router路由中，内置了一些方法也可以实现页面跳转的效果，可以自定义业务逻辑后再进行页面的跳转。
>
> 1、push
> push方法，会在执行页面跳转之前，把当前访问的页面链接地址进行记录，然后再跳转。
> this.$router.push('path属性的值')
>
> 2、replace
> replace方法，会在执行页面跳转之前，把要跳转的链接地址覆盖当前访问的链接地址。
> this.$router.replace('path属性的值')
>
> 3、go
> 用于返回已访问过的页面地址，一般写-1，表示回退到上一个页面
> this.$router.go(-1)

路由嵌套

~~~
如果某个页面中还有不同的子级页面要展示，可以使用路由嵌套来实现。

(1)创建页面组件
    此处省略...
(2)定义路由规则
    在一级路由规则中，通过children属性，来设置它的子级路由规则

export default new Router({
    routes: [
        {
            path:'/index',
            component:Index,
            children:[
                {
                    path:'movie',
                    component:Movie
                },
                {
                    path:'music',
                    component:Music
                }
            ]
        }
        ...
    ]
});
 
注意：子级路由规则的path属性不需要加斜杠
(3)在一级路由规则对应的页面中放入路由出口，用来展示匹配条件的子级路由页面
<template>
    <div>
        <h1>首页</h1>
        <!-- <button @click="$router.replace('/user')">跳转到用户</button>
        <button @click="$router.go(-1)">返回</button> -->
        <router-link to="/index/movie">电影</router-link>
        <router-link to="/index/music">音乐</router-link>
        <router-view class="box"/>
    </div>
</template>
<style lang="css">
    .box{
        border:1px solid blue;
    }
</style>
 
注意：在子级路由的导航组件中，path属性必须包含一级路由规则/二级路由规则
~~~

##### 路由传参

###### 动态路由

~~~
不同的路由规则，匹配到同一个页面上，这种路由规则叫做动态路由。

设置路由规则
{ path:'user/:变量名',component:组件}
参数名前一定要有冒号，冒号后面的是一个可以变化的字符串、数字的组合。

跳转到动态路由地址
this.$router.push('/index/user/'+uid)
                    /index/user/123
                    
获取动态路由中的参数
$route.params.变量名
~~~

###### 查询参数

> 在要传递的参数数量不确定时，使用动态路由的方式传递参数就不合适
> 我们可以使用查询参数方式进行数据的传递

###### 定义路由规则

> { path:'article/info',component:ArticleInfo }
>
> 注意：不需要添加冒号来告知路由规则后续要跟动态参数

###### 传递参数

~~~
在表格页面通过点击编辑按钮，实现路由跳转并传递参数
toInfo(obj){
    this.$router.push({
        path:'/index/article/info',
        query:{id:obj.id,title:obj.title}
    })
}
 
路由跳转后，链接地址会以下面的方式进行自动拼接：
query的数据数据类型是一个对象，对象的元素与元素之间
?key=value&key1=value...
~~~

###### 获取路由参数

~~~
this.$route.query.id
this.$route.query.title
~~~

## 路由进阶

### 路由命名

~~~
(1)设置路由规则时，添加一个name属性，给这个路由规则设置一个名称（不能重复）
{ 
    path:'user/:uid',
    component:UserInfo,
    name:'user'
}
 
(2)在页面组件中跳转路由规则时，不用按照以前的手动补全一级路由、二级路由和参数的方式
toInfo(uid){
    // this.$router.push('/index/user/'+uid)
    this.$router.push({
        name:'user',
        params:{uid}
    })
}
~~~

### 路由别名

~~~
可以给已有的路由规则，设置一个其他的名称，此时，原有的路由规则和别名都可以正常的访问到指定的页面组件。
{ 
    path:'/login',
    component:Login,
    alias:'/denglu' 
}
此时访问/login和/denglu，看到的是同一个页面组件。
~~~

### 路由模式

~~~
vue-router中有两种路由模式：
一种是hash（默认）【浏览器地址中有#号】
​    hash虽然会出现在url地址，但是不会包含在http请求中，不会重新加载页面
另一种是history模式【浏览器地址中没有#号】
​    利用html5 histroy接口中的方法实现页面跳转，history部署到服务器上后，会出现404，需要后端配合进行配置。

在/src/router/index.js进行设置路由模式
export default new Router({
    // mode:'hash',
    mode:'history',
    routes:[...]
})
~~~

### 路由守卫

> 路由守卫的作用是让指定的路由规则满足一定的条件时，才能够被访问，可以实现请求拦截的功能。
> 根据路由守卫的作用范围不同，分成以下三种：
> - 全局守卫
> - 组件守卫
> - 路由独享守卫

#### 全局守卫

/router/index.js中编写

~~~
1、全局前置守卫钩子函数
是当前项目中所有的路由规则被访问之前，可以进行一定的验证和拦截操作
router.beforeEach((to,from,next)=>{
	//to	目标路由地址  对象
	//from  来源路由地址  对象
	//next 	函数，用来执行或者改变默认的路由规则  函数
})
 
2、全局后置守卫钩子函数
是当前项目中所有的路由规则被访问之后，没有验证和拦截的功能，一般就做记录
router.afterEach((to,from)=>{
    console.log(to,'to')
    console.log(from,'from')
})
~~~

#### 组件守卫

~~~
(1)beforeRouteEnter  写在具体组件中
在此钩子函数中不可以获取到this
//当前组件的路由规则访问之前
beforeRouteEnter(to,from,next){
 let userinfo = localStorage.getItem('user')
 if(userinfo){
	next();//用户已登录，则执行默认的路由规则
 }else{
	next('/login')//用户未登录，则指向到登录的路由规则
 }
}
 
(2)beforeRouteLeave  写在具体组件中
在此钩子函数中可以获取到this
beforeRouteLeave(to, from, next) {
 console.log(this)
 console.log(to, 1111);
 console.log(from, 2222);
 console.log(next, 3333);
 next();
}
 
(3)beforeRouteUpdate  写在具体组件中
在此钩子函数中可以获取到this
// 动态路由的参数值发生变化时，会自动执行
beforeRouteUpdate(to, from, next) {
console.log(to, 1111);
console.log(from, 2222);
console.log(next, 3333);
}
~~~

#### 路由独享守卫

~~~
写在路由映射表配置规则中
{ 
    path:'user/:uid',
    component:UserInfo,
    name:'yonghu',
    beforeEnter:function(to,from,next){
        console.log(to,1111)
        console.log(from,2222)
        console.log(next,3333)
        next()
    }
}
~~~

总结：

> 路由模式
> 当路由模式是history时，组件守卫的beforeRouteUpdate不会执行，这个钩子函数只有在hash才会在满足条件的情况下自动执行。
>
> **router-link和编程式导航的区别：**
> router-link会生成a标签，而编程式导航是我们自行编写的程序代码
> 所以，编程式导航中的代码会无条件的执行，当要跳转的路由地址就是当前访问的地址时，会出现一个错误产生。
> Uncaught (in promise) Error: Avoided redundant navigation to current location: "/index/user".

## 状态管理  -  vuex

### state

<font color='red'>**state是vuex仓库中所有的状态，类似vue组件中的data**</font>

~~~
import Vuex from 'vuex'//引入
Vue.use(Vuex)
let store = new Vuex.Store({ //实例化
    state: {
        num: 100
    }
})
new Vue({
	...
	store:store//挂载到vue上
})
~~~

#### 读取state数据

~~~
<p>当前仓库中的数据量是：{{ $store.state.num }}</p>
~~~

### mutations

<font color='red'> **更改 Vuex 的 store 中的状态的唯一方法是提交 mutation，类似vue组件中的methods** </font>

~~~
let store = new Vuex.Store({
    state: {
        num: 100
    },
    mutations:{
        addNumByOne(state){
            state.num++
        },
        addNumByNum(state,num){
            state.num+=num
        }
    }
})
~~~

#### 在页面组件中使用mutations

~~~
<button @click="$store.commit('addNumByOne')">添加1</button>
<button @click="$store.commit('addNumByNum',5)">添加N</button>
~~~

**注意：mutation必须是一个同步函数，不能执行异步操作 **

### actions

> Action 类似于 mutation，不同在于：
>     Action 提交的是 mutation，而不是直接变更状态。
>     Action 可以包含任意异步操作。
> 乍一眼看上去感觉多此一举，我们直接分发 mutation 岂不更方便？实际上并非如此，还记得 mutation 必须同步执行这个限制么？Action 就不受约束！我们可以在 action 内部执行异步操作

~~~
let store = new Vuex.Store({
    ...
    actions:{
        addNumByOneSync(context){
            setTimeout(()=>{
                context.commit('addNumByOne')
            },1000)
        },
        addNumByNumSync(context,n){
            context.commit('addNumByNum',n)
        }
    }
})
~~~

#### 在页面组件中使用：

~~~
<button @click="$store.dispatch('addNumByOneSync')">添加1--action</button>
<button @click="$store.dispatch('addNumByNumSync',5)">添加N--action</button>
~~~

## getters

>  Vuex 允许我们在 store 中定义“getter”（可以认为是 store 的计算属性）。就像计算属性一样，getter 的返回值会根据它的依赖被缓存起来，且只有当它的依赖值发生了改变才会被重新计算。 

~~~
let store = new Vuex.Store({
	...
	getters:{
		showNum(state){
            //业务逻辑
            return `最新的数量是：${state.num}`;
        }
	}
});
~~~

#### 在组件中使用计算属性

~~~
<p>{{ $store.getters.showNum }}</p>
~~~

## module

> 由于使用单一状态树，应用的所有状态会集中到一个比较大的对象。当应用变得非常复杂时，store 对象就有可能变得相当臃肿。 为了解决以上问题，Vuex 允许我们将 store 分割成模块（module） 

~~~
1、设置模块中的state和mutation
export default new Vuex.Store({
    ...
    modules:{
        shop:{
            namespaced:true,//启用命名空间
            state:{
                num:1
            },
            mutations:{
                addNumByOne(state){
                    state.num++
                }
            }
        }
    }
});
shop是模块名称，可以自行设置。
	namespaced:true 启用命名空间
 
2、在页面中使用shop模块下的state和mutation
<template>
	<div>
		<h1>shop模块</h1>
        <p>shop模块中的num值为:{{ $store.state.shop.num }}</p>
        <button @click="handlerAdd">改变num</button>
    </div>
</template>
<script>
import {mapState} from 'vuex'
export default {
	computed:{
		...mapState('shop',['num']),//默认是更模块 可以增加模块名
	},
	data(){...},
    methods:{
        handlerAdd(){
            // this.$store.commit('addNumByOne')//调用根模块下的mutation
            this.$store.commit('shop/addNumByOne')//调用shop模块下的mutation
        }
    }
}
~~~

## 助手函数

### mapState

~~~
当一个组件需要获取多个状态的时候，将这些状态都声明为计算属性会有些重复和冗余

在页面组件中：
import { mapState } from 'vuex' 
export default {
    computed:{
        ...mapState(['num'])
    }
}
~~~

### mapGetters

~~~
mapGetters 辅助函数仅仅是将 store 中的 getter 映射到局部计算属性

在页面组件中：
import { mapState,mapGetters } from 'vuex' 
export default {
    computed:{
        ...mapState(['num']),
        ...mapGetters(['showNum'])
    }
}
~~~

### mapActions

~~~
使用 mapActions 辅助函数将组件的 methods 映射为 store.dispatch 调用（需要先在根节点注入 store）

在页面组件中：
<template>
    <div>
        <h2>数量减少操作</h2>
        <p>当前仓库中的数据量是：{{ num }}</p>
        <p>{{ showNum }}</p>
        <button @click="addNumByNumSync(5)">action+N</button>
    </div>
</template>
<script>
import { mapState,mapGetters,mapActions } from 'vuex' 
export default {
    ...,
    methods:{
        ...mapActions(['addNumByNumSync']),
    }
}
~~~

### mapMutations

~~~
你可以在组件中使用 this.$store.commit('xxx') 提交 mutation，或者使用 mapMutations 辅助函数将组件中的 methods 映射为 store.commit 调用（需要在根节点注入 store）

在页面组件中：
<script>
import { mapState,mapGetters,mapActions,mapMutations } from 'vuex' 
export default {
    ...
    methods:{
        ...,
        ...mapMutations(['addNumByOne'])
    }
}
</script>
~~~

#### 目录结构优化

~~~
把代码都写在main.js中是非常不明智且不合理的，因为一旦仓库中的状态非常多时，对应的代码量也会变的非常多。
 
(1)我们在src目录下创建一个store文件夹（名称可以自定义），在store目录下再创建一个index.js
 
(2)然后就可以把之前写在main.js中关于vuex的代码都可以放到/src/store/index.js中
 
但是，所有的代码都放在index.js中，也是不合适的，因为状态和改变状态的方法会有很多
 
所以在此基础上继续进行目录结构的细分，把state、mutations、actions、getters对应的代码分别拆分到对应的js文件中，然后在/src/store/index.js中引入这些文件即可。
优化之后的代码：
 
/src/main.js
import store from './store'
new Vue({
    el: '#app',
    router,
    store:store,//一定要把仓库挂到vue实例上
    components: { App },
    template: '<App/>'
})
 
/src/store/index.js
import Vue from 'vue'
import Vuex from 'vuex'
Vue.use(Vuex)
//引入状态
import state from './state'
//引入修改状态的方法
import mutations from './mutation'
//引入异步操作mutation的方法
import actions from './action'
//引入计算属性
import getters from './getter'
//实例化vuex仓库
export default new Vuex.Store({
    state:state,//key和val相同时，state:state可以简写成state
    mutations,
    actions,
    getters
});
 
/src/store/state.js
export default{
    num: 100
}
 
/src/store/mutation.js
export default{
    addNumByOne(state){
        state.num++
    },
    addNumByNum(state,num){
        state.num+=num
    }
}
 
/src/store/action.js
export default{
    addNumByOneSync(context){
        setTimeout(()=>{
            context.commit('addNumByOne')
        },1000)
    },
    addNumByNumSync(context,n){
        context.commit('addNumByNum',n)
    }
}
 
/src/store/getter.js
export default {
    showNum(state){
        //业务逻辑
        return `最新的数量是：${state.num}`;
    }
}
~~~

