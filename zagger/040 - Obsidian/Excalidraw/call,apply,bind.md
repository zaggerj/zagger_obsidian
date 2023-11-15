---
created: 2023-11-15T20:53
updated: 2023-11-15T20:53
---
# call,apply,bind

## 【call】

### 概念

- 是函数的方法

### 特点

- 可以函数调用
- 可以改变this的指向

### 例子

- let dog = {
    name: '旺旺',
    sayName: function () {
        console.log('我是', this.name)
    },
    eat: function (food1, food2) {
        console.log('我喜欢吃', food1 + food2)
    }
}
let cat = {
    name: '喵喵'
}

function fun() {
    console.log(this.name)
}
// call可以调用函数，call可以改变函数中this的指向
fun.call(cat)
dog.sayName() // 我是旺旺
dog.sayName.call(cat) // 我是喵喵
dog.eat("骨头")
dog.eat.call(cat, "鱼", "肉") // 传递参数依次传递
dog.eat.apply(cat, ["鱼", "肉"]) // 传递参数，数组的方式
let bindFun = dog.eat.bind(cat, '鱼', '肉') // 传递参数，跟call一样，bind不会调用函数,会返回一个函数，然后来调用
bindFun();

### [一个很纠结的掘金博客文章，可以看一下](https://juejin.cn/post/6999781802923524132?utm_source=gold_browser_extension#comment)

- Function.prototype.call.call(my, this, "Hello")

### [另一个掘金的文档，关于call方法的实现](https://juejin.cn/post/6978744007601946654)

## 【bind】

### 【定义】

- bind()方法创建一个新的函数, 当被调用时，将其this关键字设置为提供的值，在调用新函数时，在任何提供之前提供一个给定的参数序列。

### 【特点】

- bind返回的函数，需要手动调用下

### 【例子】

-     var a ={
        name : "Cherry",
        fn : function (a,b) {
            console.log( a + b)
        }
    }

    var b = a.fn;
    b.bind(a,1,2)()           // 3

## 【文章集合】

### [this、apply、call、bind](https://juejin.cn/post/6844903496253177863)

-     var a = {
        name : "Cherry",

        func1: function () {
            console.log(this.name)
        },

        func2: function () {
            setTimeout(  function () {
                this.func1()
            }.bind(a)(),100);
        }

    };

    a.func2()            // Cherry

	-     var a = {
        name : "Cherry",

        func1: function () {
            console.log(this.name)
        },

        func2: function () {
            setTimeout(  function () {
                this.func1()
            }.bind(a),100);
        }

    };

    a.func2()            // Cherry
	- xx.bind(a)返回函数
xx.bind(a)()调用了函数了

### [JS中的bind()方法](https://blog.csdn.net/qlwangcong518/article/details/86261597)

