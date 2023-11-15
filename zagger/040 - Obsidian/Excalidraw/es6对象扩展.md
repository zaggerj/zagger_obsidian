---
created: 2023-11-15T20:49
updated: 2023-11-15T20:49
---
# es6对象扩展

## 解构赋值

### 对象的解构

- 对象的属性则是无序的，所以对象的解构赋值简单理解是等号的左边和右边的结构相同

	- let {name,age} = {name:"swr",age:28}

- 对象的解构赋值是根据key值进行匹配

	- // 这里可以看出，左侧的name和右侧的name，是互相匹配的key值
	- // 而左侧的name匹配完成后，再赋值给真正需要赋值的Name
	- let { name:Name,age } = { name:'swr',age:28 }

- 变量已经被声明了呢？

	- let name,age
	- // 需要用圆括号，包裹起来
	- ({name,age} = {name:"swr",age:28})

- 变量能否也设置默认值？

	- let {name="swr",age} = {age:28}
	- // 这里规则和数组的解构赋值一样，当name = undefined时，则会使用默认值
	- console.log(a) // {name:"swr",age:28}
	- let [a] = [{name:"swr",age:28}]
	- let { length } = "hello swr"
console.log(length) // 9
	- function ajax({method,url,type='params'}){
    console.log(method) // 'get'
    console.log(url) // '/'
    console.log(type) // 'params'
}
ajax({method:"get",url:"/"})

### 数组的解构

- let arr = [,1,2]
let [a='我是默认值',b,c] = arr

### 定义

- 对象的解构赋值用于从一个对象取值，相当于将目标对象自身的所有可遍历的（enumerable）、但尚未被读取的属性，分配到指定的对象上面。所有的键和它们的值，都会拷贝到新对象上面。

### 要求

- 由于解构赋值要求等号右边是一个对象，所以如果等号右边是undefined或null，就会报错，因为它们无法转为对象。
- 解构赋值必须是最后一个参数，否则会报错。
- 注意，解构赋值的拷贝是浅拷贝，即如果一个键的值是复合类型的值（数组、对象、函数）、那么解构赋值拷贝的是这个值的引用，而不是这个值的副本
- 扩展运算符的解构赋值，不能复制继承自原型对象的属性。
- 如果使用解构赋值，扩展运算符后面必须是一个变量名，而不能是一个解构赋值表达式，所以上面代码引入了中间变量newObj，如果写成下面这样会报错。

let { x, ...{ y, z } } = o;
- 上面代码中，变量x是单纯的解构赋值，所以可以读取对象o继承的属性；变量y和z是扩展运算符的解构赋值，只能读取对象o自身的属性，所以变量z可以赋值成功，变量y取不到值。

	- const o = Object.create({ x: 1, y: 2 });
o.z = 3;
let { x, ...newObj } = o;
let { y, z } = newObj;
x // 1
y // undefined
z // 3

		- Object.create

			- 语法
Object.create(proto，[propertiesObject])
参数
proto
新创建对象的原型对象。
propertiesObject
可选。需要传入一个对象，该对象的属性类型参照Object.defineProperties()的第二个参数。如果该参数被指定且不为 undefined，该传入对象的自有可枚举属性(即其自身定义的属性，而不是其原型链上的枚举属性)将为新创建的对象添加指定的属性值和对应的属性描述符。
返回值
一个新对象，带着指定的原型对象和属性。

## 扩展运算符

### 数组的拼接

- let a = [0,1,2]
let b = [3,4,5]

	- let c = a.concat(b)

- let d = [...a,...b]

### 取数组中最大的值

- 以前

	- function max(...args){
    return Math.max.apply(null,args)
}
console.log(max(1,2,3,4,5,6)) // 6

- 现在

	- //现在我们用扩展运算符看看
function max(...args){
    return Math.max(...args) // 把args [1,2,3,4,5,6]展开为1,2,3,4,5,6
}
console.log(max(1,2,3,4,5,6)) // 6

### 把argument转为数组

- function max(){
    console.log(arguments) // { '0': 1, '1': 2, '2': 3, '3': 4, '4': 5, '5': 6 }
    let arr = [...arguments]
    console.log(arr) // [1,2,3,4,5,6]
}
max(1,2,3,4,5,6)

### 扩展运算符不能把伪数组转为数组
（除了有迭代器iterator的伪数组，如arguments）

- let likeArr = { "0":1,"1":2,"length":2 }
let arr = [...likeArr] 
// 报错 TypeError: likeArr is not iterable
- 可以用Array.from把伪数组转为数组
- let likeArr = { "0":1,"1":2,"length":2 }
let arr = Array.from(likeArr)
console.log(arr) // [1,2]

### 对象也可以使用扩展运算符

- 以前

	- // 以往我们这样合并对象
let name = { name:"alai" }
let age = { age:21 }
let person = {}
Object.assign(person,name,age)
console.log(person) // { name: 'alai', age: 21 }

- 使用扩展运算符

	- let name = { name:"alai" }
let age = { age:21}
let person = {...name,...age}
console.log(person) // { name: 'alai', age: 21 }

- 对象扩展运算符为浅拷贝
- 深拷贝

	- function deepCopy(obj) {
  if(obj === null) return null
  if(typeof obj !== 'object') return obj
  if(obj instanceof RegExp) return new RegExp(obj)
  if(obj instanceof Date) return new Date(obj)
  let newObj = new obj.constructor
  for(let key in obj){
    newObj[key] = deepCopy(obj[key])
  }
  return newObj
}

### 数组进行克隆一份，互不影响

- let a = [0,1,2,3]
let b = [...a]
b.push(4)
console.log(a) // [0,1,2,3]
console.log(b) // [0,1,2,3,4]

### 给函数传不确定参数数量

- function sum(...args){ // 使用...扩展运算符
    console.log(args) // [ 1, 2, 3, 4, 5, 6 ] args是一个数组
    return eval(args.join('+'))
}
console.log(sum(1,2,3,4,5,6)) // 21
- 正确的写法 扩展运算符只能放在最后一个参数

	- function sum(a,b,...args){
    console.log(a) // 1
    console.log(b) // 2
    console.log(args) // [ 3, 4, 5, 6 ]
}
sum(1,2,3,4,5,6)

### 定义

- 对象的扩展运算符（...）用于取出参数对象的所有可遍历属性，拷贝到当前对象之中。

	- let z = { a: 3, b: 4 };
let n = { ...z };
n // { a: 3, b: 4 

### 要求

- 由于数组是特殊的对象，所以对象的扩展运算符也可以用于数组。

	- let foo = { ...['a', 'b', 'c'] };
foo
// {0: "a", 1: "b", 2: "c"}


- 如果扩展运算符后面是一个空对象，则没有任何效果。

	- {...{}, a: 1}
// { a: 1 }

- 如果扩展运算符后面不是对象，则会自动将其转为对象。

	- // 等同于 {...Object(1)}
{...1} // {}

- 由于该对象没有自身属性，所以返回一个空对象。

	- // 等同于 {...Object(true)}
{...true} // {}

// 等同于 {...Object(undefined)}
{...undefined} // {}

// 等同于 {...Object(null)}
{...null} // {}

- 如果扩展运算符后面是字符串，它会自动转成一个类似数组的对象，因此返回的不是空对象。

	- {...'hello'}
// {0: "h", 1: "e", 2: "l", 3: "l", 4: "o"}

- 对象的扩展运算符等同于使用Object.assign()方法。

	- let aClone = { ...a };
// 等同于
let aClone = Object.assign({}, a);

- 扩展运算符可以用于合并两个对象。

	- let ab = { ...a, ...b };
// 等同于
let ab = Object.assign({}, a, b);

## [地址](https://www.cnblogs.com/code-duck/p/13413880.html)

