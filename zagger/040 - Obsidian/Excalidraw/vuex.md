---
created: 2023-11-15T20:49
updated: 2023-11-15T20:49
---
# vuex

## [一个简单的 store 模式 ](https://cn.vuejs.org/v2/guide/state-management.html#%E7%AE%80%E5%8D%95%E7%8A%B6%E6%80%81%E7%AE%A1%E7%90%86%E8%B5%B7%E6%AD%A5%E4%BD%BF%E7%94%A8)

### 代码

采用一个简单的 store 模式：
``` js
var store = {
  debug: true,
  state: {
    message: 'Hello!'
  },
  setMessageAction (newValue) {
    if (this.debug) console.log('setMessageAction triggered with', newValue)
    this.state.message = newValue
  },
  clearMessageAction () {
    if (this.debug) console.log('clearMessageAction triggered')
    this.state.message = ''
  }
}
```
每个实例/组件仍然可以拥有和管理自己的私有状态：
```js
var vmA = new Vue({
  data: {
    privateState: {},
    sharedState: store.state
  }
})

var vmB = new Vue({
  data: {
    privateState: {},
    sharedState: store.state
  }
})
```

## store：“store”基本上就是一个容器，它包含着你的应用中大部分的状态 (state)。

## 全局模式使用

### mutation:变更state的方法

- 提交mutation:store.commit('increment')
- 读取state：store.state.count

##  Vue 组件中访问 this.$store property

### 你需要为 Vue 实例提供创建好的 store

- new Vue({
  el: '#app',
  store: store,
})

### 从组件的方法提交一个变更：
methods: {
  increment() {
    this.$store.commit('increment')
    console.log(this.$store.state.count)
  }
}

## 由于 store 中的状态是响应式的

### 在组件中

- 调用 store 中的状态简单到仅需要在计算属性中返回即可
- 触发变化也仅仅是在组件的 methods 中提交 mutation。

## State

### 单一状态树

- 状态对象必须是纯粹 (plain) 的
- 单状态树和模块化并不冲突

### 在 Vue 组件中获得 Vuex 状态

- 从 store 实例中读取状态最简单的方法就是在计算属性 (opens new window)中返回某个状态

	- // 创建一个 Counter 组件
const Counter = {
  template: `<div>{{ count }}</div>`,
  computed: {
    count () {
      return store.state.count
    }
  }
}

- Vuex 通过 store 选项，提供了一种机制将状态从根组件“注入”到每一个子组件中（需调用 Vue.use(Vuex)）：

	- const app = new Vue({
  el: '#app',
  // 把 store 对象提供给 “store” 选项，这可以把 store 的实例注入所有的子组件
  store,
  components: { Counter },
  template: `
    <div class="app">
      <counter></counter>
    </div>
  `
})
	- 通过在根实例中注册 store 选项，该 store 实例会注入到根组件下的所有子组件中，且子组件能通过 this.$store 访问到。让我们更新下 Counter 的实现
	- const Counter = {
  template: `<div>{{ count }}</div>`,
  computed: {
    count () {
      return this.$store.state.count
    }
  }
}

### mapState 辅助函数

- // 在单独构建的版本中辅助函数为 Vuex.mapState
import { mapState } from 'vuex'

	- export default {
  computed: mapState({
    // 箭头函数可使代码更简练
    count: state => state.count,
    // 传字符串参数 'count' 等同于 `state => state.count`
    countAlias: 'count',
    // 为了能够使用 `this` 获取局部状态，必须使用常规函数
    countPlusLocalState (state) {
      return state.count + this.localCount
    }
  })
}

- 当映射的计算属性的名称与 state 的子节点名称相同时，我们也可以给 mapState 传一个字符串数组

	- computed: mapState([
  // 映射 this.count 为 store.state.count
  'count'
])

- 对象展开运算符

	- mapState 函数返回的是一个对象

		- computed: {
  localComputed () { /* ... */ },
  // 使用对象展开运算符将此对象混入到外部对象中
  ...mapState({
    // ...
  })
}

- 组件仍然保有局部状态

## Getter

### Vuex 允许我们在 store 中定义“getter”（可以认为是 store 的计算属性）

### 通过属性访问
Getter 会暴露为 store.getters 对象，你可以以属性的形式访问这些值：

store.getters.doneTodos // -> [{ id: 1, text: '...', done: true }]

### 通过让 getter 返回一个函数，来实现给 getter 传参

- getters: {
  // ...
  getTodoById: (state) => (id) => {
    return state.todos.find(todo => todo.id === id)
  }
}
- store.getters.getTodoById(2) // -> { id: 2, text: '...', done: false }
- 注意，getter 在通过方法访问时，每次都会去进行调用，而不会缓存结果。

### mapGetters

## Mutation

### 更改 Vuex 的 store 中的状态的唯一方法是提交 mutation

### Vuex 中的 mutation 非常类似于事件：每个 mutation 都有一个字符串的 事件类型 (type) 和 一个 回调函数 (handler)

- const store = new Vuex.Store({
  state: {
    count: 1
  },
  mutations: {
    increment (state) {
      // 变更状态
      state.count++
    }
  }
})
- store.commit('increment')
- // ...
mutations: {
  increment (state, n) {
    state.count += n
  }
}
- store.commit('increment', 10)
- // ...
mutations: {
  increment (state, payload) {
    state.count += payload.amount
  }
}
- store.commit('increment', {
  amount: 10
})
- //对象风格提交
store.commit({
  type: 'increment',
  amount: 10
})

### mapMutations

## Action

### Action 类似于 mutation，不同在于：
Action 提交的是 mutation，而不是直接变更状态。
Action 可以包含任意异步操作

- const store = new Vuex.Store({
  state: {
    count: 0
  },
  mutations: {
    increment (state) {
      state.count++
    }
  },
  actions: {
    increment (context) {
      context.commit('increment')
    }
  }
})

### Action 函数接受一个与 store 实例具有相同方法和属性的 context 对象

- 你可以调用 context.commit 提交一个 mutation，或者通过 context.state 和 context.getters 来获取 state 和 getters。

	- actions: {
  increment ({ commit }) {
    commit('increment')
  }
}

### 分发 Action

- store.dispatch('increment')
-  action 内部执行异步操作

	- actions: {
  incrementAsync ({ commit }) {
    setTimeout(() => {
      commit('increment')
    }, 1000)
  }
}

- 支持同样的载荷方式和对象方式进行分发

	- // 以载荷形式分发
store.dispatch('incrementAsync', {
  amount: 10
})
	- / 以对象形式分发
store.dispatch({
  type: 'incrementAsync',
  amount: 10
})

- 购物车示例，涉及到调用异步 API 和分发多重 mutation

	- actions: {
  checkout ({ commit, state }, products) {
    // 把当前购物车的物品备份起来
    const savedCartItems = [...state.cart.added]
    // 发出结账请求，然后乐观地清空购物车
    commit(types.CHECKOUT_REQUEST)
    // 购物 API 接受一个成功回调和一个失败回调
    shop.buyProducts(
      products,
      // 成功操作
      () => commit(types.CHECKOUT_SUCCESS),
      // 失败操作
      () => commit(types.CHECKOUT_FAILURE, savedCartItems)
    )
  }
}

- 在组件中分发 Action

	- import { mapActions } from 'vuex'
export default {
  // ...
  methods: {
    ...mapActions([
      'increment', // 将 `this.increment()` 映射为 `this.$store.dispatch('increment')`

      // `mapActions` 也支持载荷：
      'incrementBy' // 将 `this.incrementBy(amount)` 映射为 `this.$store.dispatch('incrementBy', amount)`
    ]),
    ...mapActions({
      add: 'increment' // 将 `this.add()` 映射为 `this.$store.dispatch('increment')`
    })
  }
}

## Module

### 由于使用单一状态树，应用的所有状态会集中到一个比较大的对象。当应用变得非常复杂时，store 对象就有可能变得相当臃肿。

### const moduleA = {
  state: () => ({ ... }),
  mutations: { ... },
  actions: { ... },
  getters: { ... }
}

const moduleB = {
  state: () => ({ ... }),
  mutations: { ... },
  actions: { ... }
}

const store = new Vuex.Store({
  modules: {
    a: moduleA,
    b: moduleB
  }
})

store.state.a // -> moduleA 的状态
store.state.b // -> moduleB 的状态

### 模块内的state是局部的？

### 模块内部的 action、mutation 和 getter 是注册在全局命名空间的？

## [vuex地址](https://vuex.vuejs.org/zh/)

