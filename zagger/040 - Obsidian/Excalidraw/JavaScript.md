---
created: 2023-11-15T20:45
updated: 2023-11-15T20:45
---
# JavaScript

## 基础知识

### es6方法

- [find方法 ](https://www.runoob.com/jsref/jsref-find.html)

	-  const hit1 = find(cache,c=>c.original===obj)

- es6对象扩展

### DOM API

- 增、删、改、查、移动
- 属性操作
- 样式操作

### BOM API

- window
- navigator
- screen
- history
- location

### event

- event object
- [bubbling/capturing](https://blog.csdn.net/qq_38128179/article/details/86293394)

  事件冒泡
  前面提到事件委托的原理是DOM元素的事件冒泡，那么事件冒泡是什么呢？
  
  一个事件触发后，会在子元素和父元素之间传播（propagation）。这种传播分成三个阶段
  
  如上图所示，事件传播分成三个阶段：
  ￼
  捕获阶段：从window对象传导到目标节点（上层传到底层）称为“捕获阶段”（capture phase），捕获阶段不会响应任何事件；
  目标阶段：在目标节点上触发，称为“目标阶段”
  冒泡阶段：从目标节点传导回window对象（从底层传回上层），称为“冒泡阶段”（bubbling phase）。事件代理即是利用事件冒泡的机制把里层所需要响应的事件绑定到外层；
  ps:https://blog.csdn.net/qq_38128179/article/details/86293394
  
- delegation

  JavaScript事件代理（事件委托）
  基本概念
  事件代理（Event Delegation），又称之为事件委托。是JavaScript中常用绑定事件的常用技巧。顾名思义，“事件代理”即是把原本需要绑定在子元素的响应事件（click、keydown......）委托给父元素，让父元素担当事件监听的职务。事件代理的原理是DOM元素的事件冒泡。
  
  举个通俗的例子
  
  比如一个宿舍的同学同时快递到了，一种方法就是他们一个个去领取，还有一种方法就是把这件事情委托给宿舍长，让一个人出去拿好所有快递，然后再根据收件人一 一分发给每个宿舍同学；
  
  在这里，取快递就是一个事件，每个同学指的是需要响应事件的 DOM 元素，而出去统一领取快递的宿舍长就是代理的元素，所以真正绑定事件的是这个元素，按照收件人分发快递的过程就是在事件执行中，需要判断当前响应的事件应该匹配到被代理（真实需要事件响应的）元素中的哪一个或者哪几个。
  ps:https://blog.csdn.net/qq_38128179/article/details/86293394
  
  事件委托的优点
  【1】可以大量节省内存占用，减少事件注册，比如在ul上代理所有li的click事件就非常棒
  
  <ul id="list">
    <li>item 1</li>
    <li>item 2</li>
    <li>item 3</li>
    ......
    <li>item n</li>
  </ul>
  // ...... 代表中间还有未知数个 li
  如上面代码所示，如果给每个li列表项都绑定一个函数，那对内存的消耗是非常大的，因此较好的解决办法就是将li元素的点击事件绑定到它的父元素ul身上，执行事件的时候再去匹配判断目标元素。
  
  【2】可以实现当新增子对象时无需再次对其绑定（动态绑定事件）
  
  假设上述的例子中列表项li就几个，我们给每个列表项都绑定了事件；
  
  在很多时候，我们需要通过 AJAX 或者用户操作动态的增加或者删除列表项li元素，那么在每一次改变的时候都需要重新给新增的元素绑定事件，给即将删去的元素解绑事件；
  
  如果用了事件委托就没有这种麻烦了，因为事件是绑定在父层的，和目标元素的增减是没有关系的，执行到目标元素是在真正响应执行事件函数的过程中去匹配的；所以使用事件在动态绑定事件的情况下是可以减少很多重复工作的。
  
  基本实现
  【1】JavaScript原生实现事件委托
  
  比如我们有这样的一个 HTML 片段：
  
  <ul id="myLinks">
    <li id="goSomewhere">Go somewhere</li>
    <li id="doSomething">Do something</li>
    <li id="sayHi">Say hi</li>
  </ul>
  按照传统的做法，需要像下面这样为它们添加 3 个事 件处理程序
  
      var item1 = document.getElementById("goSomewhere");
      var item2 = document.getElementById("doSomething");
      var item3 = document.getElementById("sayHi");
   
      item1.onclick = function() {
        location.href = "http://www.baidu.com";
      };
      item2.onclick = function() {
        document.title = "事件委托";
      };
      item3.onclick = function() {
        alert("hi");
      };
  如果在一个复杂的 Web 应用程序中，对所有可单击的元素都采用这种方式，那么结果就会有数不 清的代码用于添加事件处理程序。此时，可以利用事件委托技术解决这个问题。使用事件委托，只需在 DOM 树中尽量最高的层次上添加一个事件处理程序，如下面的例子所示
  
      var item1 = document.getElementById("goSomewhere");
      var item2 = document.getElementById("doSomething");
      var item3 = document.getElementById("sayHi");
   
      document.addEventListener("click", function (event) {
        var target = event.target;
        switch (target.id) {
          case "doSomething":
            document.title = "事件委托";
            break;
          case "goSomewhere":
            location.href = "http://www.baidu.com";
            break;
          case "sayHi": alert("hi");
            break;
        }
      })
  【2】jQuery事件delegate()实现事件委托
  
  delegate() 方法为指定的元素（属于被选元素的子元素）添加一个或多个事件处理程序，并规定当这些事件发生时运行的函数。
  
  格式：$(selector).delegate(childSelector, event, data, function)
  
  参数	描述
  childSelector	必需，规定要附加事件处理程序的一个或多个子元素。
  event	
  必需，规定附加到元素的一个或多个事件。由空格分隔多个事件值。必须是有效的事件。
  
  data	可选，规定传递到函数的额外数据。
  function	必需，规定当事件发生时运行的函数。
  <!DOCTYPE html>
  <html>
   
  <head>
    <meta charset="utf-8">
    <script src="http://lib.sinaapp.com/js/jquery/2.0.2/jquery-2.0.2.min.js"></script>
  </head>
   
  <body>
    <ul id="myLinks">
      <li id="goSomewhere">Go somewhere</li>
      <li id="doSomething">Do something</li>
      <li id="sayHi">Say hi</li>
    </ul>
   
    <script>
      $(document).ready(function () {
        $("#myLinks").delegate("#goSomewhere", "click", function () {
          location.href = "http://www.baidu.com";
        });
      });
    </script>
   
  </body>
   
  </html>
  使用事件委托注意事项
  使用“事件委托”时，并不是说把事件委托给的元素越靠近顶层就越好。事件冒泡的过程也需要耗时，越靠近顶层，事件的”事件传播链”越长，也就越耗时。如果DOM嵌套结构很深，事件冒泡通过大量祖先元素会导致性能损失。
  ps:https://blog.csdn.net/qq_38128179/article/details/86293394
  
- 同步任务
- 异步任务

	- 任务队列

		- 宏任务

			- 1. script (可以理解为外层同步代码，作为入口 )   2. setTimeout/setInterval

		- 微任务

			- 1.Promise 2. nextTick

		- 执行顺序 是 微任务 先输出 在输出 宏任务

- 执行栈

### ajax

- 基础

	- ajax

		- xhr四部曲

			- [地址](https://juejin.cn/post/6998321572972855309)

			- 原生js

				- get请求

					- 代码

						- ```javascript
function getAjax(url) {
    let xhr = new XMLHttpRequest()
    xhr.open("get", url, true)
    xhr.onload = function () {
        console.log(xhr)
        console.log(xhr.responseText)
    }
    xhr.onreadystatechange = function () {
        if (xhr.readyState == 4) {
            console.log(xhr.responseText)
        }
    }
    xhr.send(null);
}
getAjax("https://172.16.200.222/8081/thor/uaa/ad-server");
```

					- 带参数

						- 发送一个带有参数的 get 请求
						- var xhr = new XMLHttpRequest
						- 直接在请求地址后面拼接参数，? 开始，key=value 的形式，多个参数之间以 & 分割 
						- xhr.open('get', '/ajax?name=Jack&age=18')
						- xhr.onload = function () { console.log( xhr.responseText ) }
						- xhr.send()

				- post请求

					- 带参数的思路

						- 发送一个带有参数的 post 请求
						- var xhr = new XMLHttpRequest
						- 不需要在请求地址后面拼接任何内容
						- xhr.open('post', '/ajax')
						- xhr.onload = function () { console.log( xhr.responseText ) }
						- post 方式携带参数是直接写在 xhr.send() 后面的 () 里面
						- 自己收集数据 key=value
						- 自己设置请求头
						- xhr.setRequestHeadr('content-type', 'application/x-www-form-urlencoded')
						- FormData 收集数据 
						- 什么都不需要，只要使用 FormData 收集数据就可以了
						- var fd = new FormData(DOM)
						- 在发送请求的时候只要把 fd 带过去就行了

					- 代码1-自己收集参数

					  ```
					  var xhr = new XMLHttpRequest()
					  xhr.open('post', '/ajax')
					  xhr.onload = function () {
					    console.log(xhr.responseText)
					  }
					  xhr.setRequestHeadr('content-type', 'application/x-www-form-urlencoded')
					  xhr.send('key=value&key=value')
					  ```
					  
					- 代码2-formdata收集参数

					  ```
					  var fd = new FormData(document.querySelector('form'))
					  var xhr = new XMLHttpRequest()
					  xhr.open('post', '/ajax')
					  xhr.onload = function () {
					    console.log(xhr.responseText)
					  }
					  xhr.send(fd)
					  ```
					  
			- jq

				- $.get

					- 思路

						- $.get 几个参数，怎么使用
						- 地址
						- 参数 key=value 或者 { name: 'Jack' }
						- 成功的回调函数
						- 预期后台返回的数据类型
						- text ： 什么都不做，直接给你结果
						- json ： 必定会执行一步 JSON.parse()

				- $.post

					- 思路

						- $.post 几个参数，怎么使用
						- 地址
						- 参数 key=value 或者 { name: 'Jack' }， 不能发送 FormData
						- 成功的回调函数
						- 预期后台返回的数据类型

				- $.ajax

					- 思路

						- $.ajax 几个参数，怎么使用
						- 就是配置项 options 
						- url： 请求地址
						- method/type: 请求方式
						- data： 携带参数
						- dataType： 后台返回的数据类型天
						- success： 成功的回掉
						- error： 失败的回调
						- contentType: 发送 FormData 的时候使用的
						- processData： 发送 FormData 的时候使用的

				- JSONP

					- 思路

						- $.ajax 怎么发送 jsonp 请求
						- dataType 必须是 jsonp
						- 方式必须是 get
						- jsonp： 根据后台来决定

		- XHR兼容性
		- GET POST
		- 异步
		- 状态监控
		- 跨域

	- XHR兼容性
	- GET POST
	- 异步
	- 状态监控
	- 跨域

- fetch

	- [MDN地址](https://developer.mozilla.org/zh-CN/docs/Web/API/Fetch_API/Using_Fetch)

		- 好像并没有具体说明fetch使用的技术到底是什么？
还有原理到底是什么？

- axios
- ajax/fetch/axios之间关系

	- 图示

		- Ajax 是一种代表异步 JavaScript + XML 的模型（技术合集），所以 Fetch 也是 Ajax 的一个子集
		- 在之前，我们常说的 Ajax 默认是指以 XHR 为核心的技术合集，而在有了 Fetch 之后，Ajax 不再单单指 XHR 了，我们将以 XHR 为核心的 Ajax 技术称作传统 Ajax。
		- Axios 属于传统 Ajax（XHR）的子集，因为它是基于 XHR 进行的封装。

## js高级理论知识

### 基础总结深入

- 数据类型

  1. 分类(2大类)
    * 基本(值)类型
      * Number: 任意数值
      * String: 任意文本
      * Boolean: true/false
      * undefined: undefined
      * null: null
    * 对象(引用)类型
      * Object: 一般对象类型
      * Array: 特别的对象类型(下标/内部数据有序)
      * Function: 特别的对象类型(可执行)
  2. 判断
    * typeof:
      * 可以区别: 数值, 字符串, 布尔值, undefined, function
      * 不能区别: null与对象, 一般对象与数组
    * instanceof
      * 专门用来判断对象数据的类型: Object, Array与Function
    * ===
      * 可以判断: undefined和null
	- 1. 分类
	- 2. 判断
	- 相关问题

	  1. undefined与null的区别?
	    * undefined代表变量没有赋值
	    * null: 代表变量赋值了, 只是值为null
	  2. 什么时候将变量赋值为null?
	    * 初始化赋值: 将要作为引用变量使用, 但对象还没有确定
	    * 结束时: 将变量指向的对象成为垃圾对象
	  3. 理解变量类型与数据类型?
	    * js的变量本身是没有类型的, 变量的类型实际上是变量内存中数据的类型
	    * 变量类型:
	      * 基本类型: 保存基本类型数据的变量
	      * 引用类型: 保存对象地址值的变量
	    * 数据对象
	      * 基本类型
	      * 对象类型
		- 1. undefined与null的区别?
		- 2. 什么时候将变量赋值为null?
		- 3. 严格区别变量类型与数据类型?

- 数据, 变量与内存

  1. 什么是数据?
    * 存储于内存中代表特定信息的'东东', 本质就是0101二进制
    * 具有可读和可传递的基本特性
    * 万物(一切)皆数据, 函数也是数据
    * 程序中所有操作的目标: 数据
      * 算术运算
      * 逻辑运算
      * 赋值
      * 调用函数传参
      ...
  2. 什么是内存?
    * 内存条通电后产生的存储空间(临时的)
    * 产生和死亡: 内存条(集成电路板)==>通电==>产生一定容量的存储空间==>存储各种数据==>断电==>内存全部消失
    * 内存的空间是临时的, 而硬盘的空间是持久的
    * 分配内存: 声明变量和函数或创建对象时, JS引擎会自动为此分配一定大小的内存来存放对应的数据
    * 释放内存: 清空内存中的数据, 标识内存可以再分配使用(内存不释放就不能复用)
      * 自动释放: 栈空间的局部变量
      * 垃圾回调器回调: 堆空间的垃圾对象
    * 一块内存包含2个数据
      * 内部存储的数据(一般数据/地址数据)
      * 内存地址值数据
    * 内存分类
      * 栈: 全局变量, 局部变量 (空间较小)
      * 堆: 对象 (空间较大)
  3. 什么是变量?
    * 值可以变化的量, 由变量名与变量值组成
    * 一个变量对应一块小内存, 变量名用来查找到内存, 变量值就是内存中保存的内容
  4. 内存,数据, 变量三者之间的关系
    * 内存是一个容器, 用来存储程序运行需要操作的数据
    * 变量是内存的标识, 我们通过变量找到对应的内存, 进而操作(读/写)内存中的数据
	- 1. 什么是数据?
	- 2. 什么是内存?

		- 

	- 3. 什么是变量?
	- 4. 内存,数据, 变量三者之间的关系
	- 相关问题

	  1. 问题1: var a = xxx, a内存中到底保存的是什么?
	    * xxx是一个基本数据
	    * xxx是一个对象
	    * xxx是一个变量
	  
	  2. 关于引用变量赋值问题
	    * 2个引用变量指向同一个对象, 通过一个引用变量修改对象内部数据, 另一个引用变量也看得见
	    * 2个引用变量指向同一个对象,让一个引用变量指向另一个对象, 另一个引用变量还是指向原来的对象
	  
	  3. 问题: 在js调用函数时传递变量参数时, 是值传递还是引用传递?
	    * 只有值传递, 没有引用传递, 传递的都是变量的值, 只是这个值可能是基本数据, 也可能是地址(引用)数据
	    *  如果后一种看成是引用传递, 那就值传递和引用传递都可以有
	  
	  4. 问题: JS引擎如何管理内存?
	    1. 内存生命周期
	      1). 分配需要的内存
	      2). 使用分配到的内存
	      3). 不需要时将其释放/归还
	    2. 释放内存
	      * 为执行函数分配的栈空间内存: 函数执行完自动释放
	      * 存储对象的堆空间内存: 当内存没有引用指向时, 对象成为垃圾对象, 垃圾回收器后面就会回收释放此内存
		- 关于赋值与内存的问题?
		- 关于引用变量赋值问题?
		- 关于数据传递问题?
		- JS引擎如何管理内存?

- 对象

  1. 什么是对象?
    * 代表现实中的某个事物, 是该事物在编程中的抽象
    * 多个数据的集合体(封装体)
    * 用于保存多个数据的容器
  2. 为什么要用对象?
    * 便于对多个数据进行统一管理
  3. 对象的组成
    * 属性
      * 代表现实事物的状态数据
      * 由属性名和属性值组成
      * 属性名都是字符串类型, 属性值是任意类型
    * 方法
      * 代表现实事物的行为数据
      * 是特别的属性==>属性值是函数
  4. 如何访问对象内部数据?
    * .属性名: 编码简单, 但有时不能用
    * ['属性名']: 编码麻烦, 但通用
  
	- 1. 什么是对象?
	- 2. 为什么要用对象?
	- 3. 对象的组成
	- 4. 如何访问对象内部数据?
	- 相关问题

	  什么时候必须使用['属性名']的方式访问对象内部数据?
	    * 属性名不是合法的标识名
	    * 属性名不确定
		- 什么时候必须使用['属性名']的方式?

- 函数

  1. 什么是函数?
    * 具有特定功能的n条语句的封装体
    * 只有函数是可执行的, 其它类型的数据是不可执行的
    * 函数也是对象
  2. 为什么要用函数?
    * 提高代码复用
    * 便于阅读和交流
  3. 如何定义函数?
    * 函数声明
    * 表达式
  4. 调用(执行)函数
    * test()
    * new test()
    * obj.test()
    * test.call/apply(obj)
	- 1. 什么是函数?
	- 2. 为什么要用函数?
	- 3. 如何定义函数?
	- 4. 如何调用(执行)函数?
	- 5. 回调函数

	  1. 什么函数才是回调函数?
	    * 你定义的
	    * 你没有直接调用
	    * 但最终它执行了(在特定条件或时刻)
	  2. 常见的回调函数?
	    * DOM事件函数
	    * 定时器函数
	  
	    * ajax回调函数(后面学)
	    * 生命周期回调函数(后面学)
		- 1. 什么函数才是回调函数?
		- 2. 常见的回调函数?

	- 6. IIEF

	  1. 理解
	    * 全称: Immediately-Invoked Function Expression 立即调用函数表达式
	    * 别名: 匿名函数自调用
	  2. 作用
	    * 隐藏内部实现
	    * 不污染外部命名空间
		- 1. 理解
		- 2. 作用

	- 7. 函数中的this

	  function Person(color) {
	    // console.log(this)
	    this.color = color;
	    this.getColor = function () {
	      // console.log(this)
	      return this.color;
	    };
	    this.setColor = function (color) {
	     // console.log(this)
	      this.color = color;
	    };
	  }
	  
	  Person("red"); //this是谁?
	  
	  var p = new Person("yello"); //this是谁?
	  
	  p.getColor(); //this是谁?
	  
	  var obj = {};
	  p.setColor.call(obj, "black"); //this是谁?
	  
	  var test = p.setColor;
	  test(); //this是谁?
	  
	  function fun1() {
	    function fun2() {
	      console.log(this);
	    }
	  
	    fun2(); //this是谁?
	  }
	  fun1();
### 函数高级

- 原型与原型链

	- 原型(prototype)

	  1. 函数的prototype属性(图)
	    * 每个函数都有一个prototype属性, 它默认指向一个Object空对象(即称为: 原型对象)
	    * 原型对象中有一个属性constructor, 它指向函数对象
	  2. 给原型对象添加属性(一般都是方法)
	    * 作用: 函数的所有实例对象自动拥有原型中的属性(方法)
		- 1. 函数的protype属性

			- 

		- 2. 给原型对象添加属性(一般都是方法)

	- 显式原型与隐式原型

	  1. 每个函数function都有一个prototype，即显式原型
	  2. 每个实例对象都有一个__proto__，可称为隐式原型
	  3. 对象的隐式原型的值为其对应构造函数的显式原型的值
	  4. 内存结构(图)
	  5. 总结:
	    * 函数的prototype属性: 在定义函数时自动添加的, 默认值是一个空Object对象
	    * 对象的__proto__属性: 创建对象时自动添加的, 默认值为构造函数的prototype属性值
	    * 程序员能直接操作显式原型, 但不能直接操作隐式原型(ES6之前)
		- 

	- 原型链

		- 1. 原型链

		  1. 原型链(图解)
		    * 访问一个对象的属性时，
		      * 先在自身属性中查找，找到返回
		      * 如果没有, 再沿着__proto__这条链向上查找, 找到返回
		      * 如果最终没找到, 返回undefined
		    * 别名: 隐式原型链
		    * 作用: 查找对象的属性(方法)
		  2. 构造函数/原型/实体对象的关系(图解)
		  3. 构造函数/原型/实体对象的关系2(图解)
			- 

		- 2. 构造函数/原型/实例对象的关系(图解)

			- var o1 = new Object();
var o2 = {};
			- 
			- 

		- 3. 构造函数/原型/实例对象的关系2(图解)

			- function Foo(){  }
			- 
			- 

		- 4. 原型继承

			- 构造函数的实例对象自动拥有构造函数原型对象的属性(方法)
			- 利用的就是原型链

		- 5. 原型属性问题

		  1. 读取对象的属性值时: 会自动到原型链中查找
		  2. 设置对象的属性值时: 不会查找原型链, 如果当前对象中没有此属性, 直接添加此属性并设置其值
		  3. 方法一般定义在原型中, 属性一般通过构造函数定义在对象本身上
	- 探索instanceof

	  1. instanceof是如何判断的?
	    * 表达式: A instanceof B
	    * 如果B函数的显式原型对象在A对象的原型链上, 返回true, 否则返回false
	  2. Function是通过new自己产生的实例
		- 案例1

			- function Foo() {  }
var f1 = new Foo();
console.log(f1 instanceof Foo);
console.log(f1 instanceof Object);
			- 
			- 

		- 案例2

			- console.log(Object instanceof Function);
console.log(Object instanceof Object);
console.log(Function instanceof Function);
console.log(Function instanceof Object);

function Foo() {}
console.log(Object instanceof  Foo);
			- 
			- 

	- 面试题

	  /*
	    测试题1
	     */
	    var A = function() {
	  
	    }
	    A.prototype.n = 1
	  
	    var b = new A()
	  
	    A.prototype = {
	      n: 2,
	      m: 3
	    }
	  
	    var c = new A()
	    console.log(b.n, b.m, c.n, c.m)
	  
	  
	    /*
	     测试题2
	     */
	    var F = function(){};
	    Object.prototype.a = function(){
	      console.log('a()')
	    };
	    Function.prototype.b = function(){
	      console.log('b()')
	    };
	    var f = new F();
	    f.a()
	    f.b()
	    F.a()
	    F.b()
- 执行上下文与执行上下文栈

	- 变量提升与函数提升

	  1. 变量声明提升
	    * 通过var定义(声明)的变量, 在定义语句之前就可以访问到
	    * 值: undefined
	  2. 函数声明提升
	    * 通过function声明的函数, 在之前就可以直接调用
	    * 值: 函数定义(对象)
	  3. 问题: 变量提升和函数提升是如何产生的?
	- 执行上下文

	  1. 代码分类(位置)
	    * 全局代码
	    * 函数代码
	  2. 全局执行上下文
	    * 在执行全局代码前将window确定为全局执行上下文
	    * 对全局数据进行预处理
	      * var定义的全局变量==>undefined, 添加为window的属性
	      * function声明的全局函数==>赋值(fun), 添加为window的方法
	      * this==>赋值(window)
	    * 开始执行全局代码
	  3. 函数执行上下文
	    * 在调用函数, 准备执行函数体之前, 创建对应的函数执行上下文对象
	    * 对局部数据进行预处理
	      * 形参变量==>赋值(实参)==>添加为执行上下文的属性
	      * arguments==>赋值(实参列表), 添加为执行上下文的属性
	      * var定义的局部变量==>undefined, 添加为执行上下文的属性
	      * function声明的函数 ==>赋值(fun), 添加为执行上下文的方法
	      * this==>赋值(调用函数的对象)
	    * 开始执行函数体代码
		- 1. 代码分类(位置)
		- 2. 全局执行上下文
		- 3. 函数执行上下文

	- 执行上下文栈

		- 理解

		  1. 在全局代码执行前, JS引擎就会创建一个栈来存储管理所有的执行上下文对象
		  2. 在全局执行上下文(window)确定后, 将其添加到栈中(压栈)
		  3. 在函数执行上下文创建后, 将其添加到栈中(压栈)
		  4. 在当前函数执行完后,将栈顶的对象移除(出栈)
		  5. 当所有的代码执行完后, 栈中只剩下window
		- 流程分析

		   var a = 10
		    var bar = function (x) {
		      var b = 5
		      foo(x + b)              
		    }
		    var foo = function (y) {
		      var c = 5
		      console.log(a + c + y)
		    }
		    bar(10)                   
			- 
			- 
			- 
			- 
			- 

	- 面试题

	   /*
	    测试题1: 
	    */
	    function a() {}
	    var a;
	    console.log(typeof a)
	  
	  
	    /*
	    测试题2: 
	     */
	    if (!(b in window)) {
	      var b = 1;
	    }
	    console.log(b)
	  
	    /*
	    测试题3: 
	     */
	    var c = 1
	    function c(c) {
	      console.log(c)
	      var c = 3
	    }
	    c(2)
- 作用域与作用域链

	- 作用域

	  1. 理解
	    * 就是一块"地盘", 一个代码段所在的区域
	    * 它是静态的(相对于上下文对象), 在编写代码时就确定了
	  2. 分类
	    * 全局作用域
	    * 函数作用域
	    * 没有块作用域(ES6有了)
	  3. 作用
	    * 隔离变量，不同作用域下同名变量不会有冲突
		- 

	- 作用域与执行上下文

	  1. 区别1
	    * 全局作用域之外，每个函数都会创建自己的作用域，作用域在函数定义时就已经确定了。而不是在函数调用时
	    * 全局执行上下文环境是在全局作用域确定之后, js代码马上执行之前创建
	    * 函数执行上下文环境是在调用函数时, 函数体代码执行之前创建
	  2. 区别2
	    * 作用域是静态的, 只要函数定义好了就一直存在, 且不会再变化
	    * 上下文环境是动态的, 调用函数时创建, 函数调用结束时上下文环境就会被释放
	  3. 联系
	    * 上下文环境(对象)是从属于所在的作用域
	    * 全局上下文环境==>全局作用域
	    * 函数上下文环境==>对应的函数使用域
		- 

	- 作用域链

	  1. 理解
	    * 多个上下级关系的作用域形成的链, 它的方向是从下向上的(从内到外)
	    * 查找变量时就是沿着作用域链来查找的
	  2. 查找一个变量的查找规则
	    * 在当前作用域下的执行上下文中查找对应的属性, 如果有直接返回, 否则进入2
	    * 在上一级作用域的执行上下文中查找对应的属性, 如果有直接返回, 否则进入3
	    * 再次执行2的相同操作, 直到全局作用域, 如果还找不到就抛出找不到的异常
		- 

		  	var a = 2;
		      function fn1() {
		          var b = 3;
		          function fn2() {
		              var c = 4;
		              console.log(c);
		              console.log(b);
		              console.log(a);
		              console.log(d);
		          }
		          fn2();
		      }
		      fn1();
	- 面试题

		- 面试题1

		    var x = 10;
		    function fn() {
		      console.log(x);
		    }
		    function show(f) {
		      var x = 20;
		      f();
		    }
		    show(fn);
		- 面试题2

		    var fn = function () {
		      console.log(fn)
		    }
		    fn()
		  
		    var obj = {
		      fn2: function () {
		        console.log(fn2)
		      }
		    }
		    obj.fn2()
- 闭包

	- 引子实例

	  <!DOCTYPE html>
	  <html lang="en">
	  <head>
	      <meta charset="UTF-8">
	      <title>Title</title>
	      <script type="text/javascript">
	            /*
	  需求: 点击某个按钮, 提示"点击的是第n个按钮"
	           */
	      </script>
	  </head>
	  <body>
	      <button>测试1</button>
	      <button>测试2</button>
	      <button>测试3</button>
	  </body>
	  
	  </html>
	- 理解闭包

	  1. 如何产生闭包?
	    * 当一个嵌套的内部(子)函数引用了嵌套的外部(父)函数的变量(函数)时, 就产生了闭包
	  2. 闭包到底是什么?
	    * 使用chrome调试查看
	    * 理解一: 闭包是嵌套的内部函数(绝大部分人)
	    * 理解二: 包含被引用变量(函数)的对象(极少数人)
	    * 注意: 闭包存在于嵌套的内部函数中
	  3. 产生闭包的条件?
	    * 函数嵌套
	    * 内部函数引用了外部函数的数据(变量/函数)
	- 常见的闭包

	  1. 将函数作为另一个函数的返回值
	  2. 将函数作为实参传递给另一个函数调用
	- 闭包的作用

	  1. 使用函数内部的变量在函数执行完后, 仍然存活在内存中(延长了局部变量的生命周期)
	  2. 让函数外部可以操作(读写)到函数内部的数据(变量/函数)
	  
	  问题:
	    1. 函数执行完后, 函数内部声明的局部变量是否还存在?
	    2. 在函数外部能直接访问函数内部的局部变量吗?
	- 闭包的生命周期

	  1. 产生: 在嵌套内部函数定义执行完时就产生了(不是在调用)
	  2. 死亡: 在嵌套的内部函数成为垃圾对象时
	  
	  
	  <script type="text/javascript">
	    function fun1() {
	      //问题2: 此时闭包产生了吗? 
	      var a = 3;
	  
	      function fun2() {
	        a++;
	        console.log(a);
	      }
	  
	      return fun2;
	    }
	    //问题1: 此时闭包产生了吗?   
	    var f = fun1();
	    //问题3: 此时闭包释放了吗?  
	    f();
	    f();
	    //问题4: 此时闭包释放回收了吗?   
	    //问题5: 如何让闭包释放回收呢?
	  </script>
	- 闭包的应用: 自定义JS模块

	  闭包的应用 : 定义JS模块
	    * 具有特定功能的js文件
	    * 将所有的数据和功能都封装在一个函数内部(私有的)
	    * 只向外暴露一个包信n个方法的对象或函数
	    * 模块的使用者, 只需要通过模块暴露的对象调用方法来实现对应的功能
	- 闭包的缺点及解决

	  1. 缺点
	    * 函数执行完后, 函数内的局部变量没有释放, 占用内存时间会变长
	    * 容易造成内存泄露
	  2. 解决
	    * 能不用闭包就不用
	    * 及时释放
	- 面试题

		- 面试题一

		  //代码片段一
		  var name = "The Window";
		  var object = {
		      name : "My Object",
		      getNameFunc : function(){
		          return function(){
		              return this.name;
		          };
		      }
		  };
		  alert(object.getNameFunc()());  //?
		  
		  
		  //代码片段二
		  var name2 = "The Window";
		  var object2 = {
		      name2 : "My Object",
		      getNameFunc : function(){
		          var that = this;
		          return function(){
		              return that.name2;
		          };
		      }
		  };
		  alert(object2.getNameFunc()()); //?
		  
		  
		  
		- 面试题二

		    function fun(n,o) {
		          console.log(o)
		          return {
		              fun:function(m){
		                  return fun(m,n);
		              }
		          };
		      }
		      var a = fun(0);  a.fun(1);  a.fun(2);  a.fun(3);//undefined,?,?,?
		      var b = fun(0).fun(1).fun(2).fun(3);//undefined,?,?,?
		      var c = fun(0).fun(1);  c.fun(2);  c.fun(3);//undefined,?,?,?
### 面向对象高级

- 对象创建模式

	- Object构造函数模式

	  方式1: Object构造函数模式
	    * 套路: 先创建空Object对象, 再动态添加属性/方法
	    * 适用场景: 起始时不确定对象内部数据
	    * 问题: 语句太多
	- 对象字面量模式

	  方式2: 对象字面量模式
	    * 套路: 使用{}创建对象, 同时指定属性/方法
	    * 适用场景: 起始时对象内部数据是确定的
	    * 问题: 如果创建多个对象, 有重复代码
	- 工厂模式

	  方式3: 工厂模式
	    * 套路: 通过工厂函数动态创建对象并返回
	    * 适用场景: 需要创建多个对象
	    * 问题: 对象没有一个具体的类型, 都是Object类型
	- 自定义构造函数模式

	  方式4: 自定义构造函数模式
	    * 套路: 自定义构造函数, 通过new创建对象
	    * 适用场景: 需要创建多个类型确定的对象
	    * 问题: 每个对象都有相同的数据, 浪费内存
	- 构造函数+原型的组合模式

	  方式5: 构造函数+原型的组合模式
	    * 套路: 自定义构造函数, 属性在函数中初始化, 方法添加到原型上
	    * 适用场景: 需要创建多个类型确定的对象
- 继承模式

	- 原型链继承

	  方式1: 原型链继承
	    1. 套路
	      1. 定义父类型构造函数
	      2. 给父类型的原型添加方法
	      3. 定义子类型的构造函数
	      4. 创建父类型的对象赋值给子类型的原型
	      5. 将子类型原型的构造属性设置为子类型
	      6. 给子类型原型添加方法
	      7. 创建子类型的对象: 可以调用父类型的方法
	    2. 关键
	      1. 子类型的原型为父类型的一个实例对象
		- 

	- 借用构造函数继承

	  方式2: 借用构造函数继承(假的)
	  1. 套路:
	    1. 定义父类型构造函数
	    2. 定义子类型构造函数
	    3. 在子类型构造函数中调用父类型构造
	  2. 关键:
	    1. 在子类型构造函数中通用super()调用父类型构造函数
	- 组合继承

	  方式3: 原型链+借用构造函数的组合继承
	  1. 利用原型链实现对父类型对象的方法继承
	  2. 利用super()借用父类型构建函数初始化相同属性
### 线程机制与事件机制

- 进程与线程

	- 进程(process)

		- 程序的一次执行, 它占有一片独有的内存空间
		- 可以通过windows任务管理器查看进程

	- 线程(thread)

		- 是进程内的一个独立执行单元
		- 是程序执行的一个完整流程
		-  是CPU的最小的调度单元

	- 图解

		- 

	- 相关知识

		- 应用程序必须运行在某个进程的某个线程上
		- 一个进程中至少有一个运行的线程: 主线程,  进程启动后自动创建
		- 一个进程中也可以同时运行多个线程, 我们会说程序是多线程运行的
		- 一个进程内的数据可以供其中的多个线程直接共享
		- 多个进程之间的数据是不能直接共享的
		- 线程池(thread pool): 保存多个线程对象的容器, 实现线程对象的反复利用

	- 相关问题

		- 何为多进程与多线程?

			- 多进程运行: 一应用程序可以同时启动多个实例运行
			- 多线程: 在一个进程内, 同时有多个线程运行

		- 比较单线程与多线程?

			- 多线程

				- 优点

					- 能有效提升CPU的利用率

				- 缺点

					- 创建多线程开销
					- 线程间切换开销
					- 死锁与状态同步问题

			- 单线程

				- 优点

					- 顺序编程简单易懂

				- 缺点

					- 效率低

		- JS是单线程还是多线程?

			- js是单线程运行的
			- 但使用H5中的 Web Workers可以多线程运行

		- 浏览器运行是单线程还是多线程?

			- 都是多线程运行的

		- 浏览器运行是单进程还是多进程?

			- 有的是单进程

				- firefox
				- 老版IE

			- 有的是多进程

				- chrome
				- 新版IE

			- 如何查看浏览器是否是多进程运行的呢?

				- 任务管理器-->进程

- 浏览器内核

	- 支撑浏览器运行的最核心的程序
	- 不同的浏览器可能不一样

		- Chrome, Safari : webkit
		- firefox : Gecko
		- IE	: Trident
		- 360,搜狗等国内浏览器: Trident + webkit

	- 内核由很多模块组成

		- js引擎模块 : 负责js程序的编译与运行
		- html,css文档解析模块 : 负责页面文本的解析
		- DOM/CSS模块 : 负责dom/css在内存中的相关处理 
		- 布局和渲染模块 : 负责页面的布局和效果的绘制(内存中的对象)
		- ......
		- 定时器模块 : 负责定时器的管理
		- DOM事件响应模块 : 负责事件的管理
		- 网络请求模块 : 负责ajax请求

- 定时器引发的思考

  1. 定时器真是定时执行的吗?
    * 定时器并不能保证真正定时执行
    * 一般会延迟一丁点(可以接受), 也有可能延迟很长时间(不能接受)
  2. 定时器回调函数是在分线程执行的吗?
    * 在主线程执行的, js是单线程的
  3. 定时器是如何实现的?
    * 事件循环模型(后面讲)
	- 1. 定时器真是定时执行的吗?
	- 2. 定时器回调函数是在哪个线程执行的?
	- 3. 定时器是如何实现的?

- JS是单线程执行的

  1. 如何证明js执行是单线程的?
    * setTimeout()的回调函数是在主线程执行的
    * 定时器回调函数只有在运行栈中的代码全部执行完后才有可能执行
  2. 为什么js要用单线程模式, 而不用多线程模式?
    * JavaScript的单线程，与它的用途有关。
    * 作为浏览器脚本语言，JavaScript的主要用途是与用户互动，以及操作DOM。
    * 这决定了它只能是单线程，否则会带来很复杂的同步问题
  
  3. 代码的分类:
    * 初始化代码
    * 回调代码
  4. js引擎执行代码的基本流程
    * 先执行初始化代码: 包含一些特别的代码
      * 设置定时器
      * 绑定监听
      * 发送ajax请求
    * 后面在某个时刻才会执行回调代码
	- 1. 如何证明js执行是单线程的?
	- 2. 为什么js要用单线程模式, 而不用多线程模式?
	- 3. 代码的分类
	- 4. js引擎执行代码的基本流程

- 浏览器的事件循环(轮询)模型

  1. 所有代码分类
    * 初始化执行代码: 包含绑定dom事件监听, 设置定时器, 发送ajax请求的代码
    * 回调执行代码: 处理回调逻辑
  2. js引擎执行代码的基本流程:
    * 初始化代码===>回调代码
  3. 模型的2个重要组成部分:
    * 事件管理模块
    * 回调队列
  4. 模型的运转流程
    * 执行初始化代码, 将事件回调函数交给对应模块管理
    * 当事件发生时, 管理模块会将回调函数及其数据添加到回调列队中
    * 只有当初始化代码执行完后(可能要一定时间), 才会遍历读取回调队列中的回调函数执行
	- 模型原理图

		- 

	- 相关重要概念

	  1. 执行栈
	       execution stack
	       所有的代码都是在此空间中执行的
	   2. 浏览器内核
	       browser core
	       js引擎模块(在主线程处理)
	       其它模块(在主/分线程处理)
	   3. 任务队列(callback queue)
	       task queue
	   4. 消息队列(callback queue)
	       message queue
	   5. 事件队列(callback queue)
	       event queue
	   6. 事件轮询
	       event loop
	       从任务队列中循环取出回调函数放入执行栈中处理(一个接一个)
	   7. 事件驱动模型
	       event-driven interaction model
	   8. 请求响应模型
	       request-response model
		- 1. 执行栈

			- execution stack
			- 所有的代码都是在此空间中执行的

		- 2. 浏览器内核

			- browser core
			- js引擎模块(在主线程处理)
			- 其它模块(在主/分线程处理)

		- 3. 任务队列

			- task queue

		- 4. 消息队列

			- message queue

		- 5. 事件队列

			- event queue

		- 6. 事件轮询

			- event loop
			- 从任务队列中循环取出回调函数放入执行栈中处理(一个接一个)

		- 7. 事件驱动模型

			- event-driven interaction model

		- 8. 请求响应模型

			- request-response model

	- 执行流程

- H5 Web Workers(多线程)

	- 介绍

		- Web Workers 是 HTML5 提供的一个javascript多线程解决方案
		- 我们可以将一些大计算量的代码交由web Worker运行而不冻结用户界面
		- 但是子线程完全受主线程控制，且不得操作DOM。
所以，这个新标准并没有改变JavaScript单线程的本质

	- 使用

		- 创建在分线程执行的js文件

		  var onmessage =function (event){ //不能用函数声明
		      console.log('onMessage()22');
		      var upper = event.data.toUpperCase();//通过event.data获得发送来的数据
		      postMessage( upper );//将获取到的数据发送会主线程
		  }
		- 在主线程中的js中发消息并设置回调

		  //创建一个Worker对象并向它传递将在新线程中执行的脚本的URL
		  var worker = new Worker("worker.js");  
		  //接收worker传过来的数据函数
		  worker.onmessage = function (event) {     
		      console.log(event.data);             
		  };
		  //向worker发送数据
		  worker.postMessage("hello world");    
	- 图解

		- 

	- 应用练习

	  编程实现斐波那契数列（Fibonacci sequence）的计算
	  F（0）=0，F（1）=1，..... F（n）=F(n-1)+F(n-2)
		- 直接在主线程

		  var fibonacci =function(n) {
		      return n <2 ? n : fibonacci(n -1) + fibonacci(n -2);
		  };
		  console.log(fibonacci(48));
		- 使用Worker在分线程

			- 主线程

			  var worker = new Worker('worker2.js');
			  worker.addEventListener('message', function (event) {
			      var timer2 = new Date().getTime();
			      console.log('结果：' + event.data, '时间:' + timer2, '用时：' + ( timer2 - timer ));
			  }, false);
			  
			  var timer = new Date().getTime();
			  console.log('开始计算: ', '时间:' + timer);
			  setTimeout(function () {
			      console.log('定时器函数在计算数列时执行了', '时间:' + new Date().getTime());
			  }, 1000);
			  
			  worker.postMessage(40);
			  console.log('我在计算数列的时候执行了', '时间:' + new Date().getTime());
			- 分线程

			  var fibonacci =function(n) {
			      return n <2 ? n : fibonacci(n -1) + fibonacci(n -2);
			  };
			  
			  var onmessage = function(event) {
			      var n = parseInt(event.data, 10);
			      postMessage(fibonacci(n));
			  };
	- 不足

	  1. 慢
	  1. 不能跨域加载JS
	  2. worker内代码不能访问DOM(更新UI)
	  3. 不是每个浏览器都支持这个新特性
## ES6+

### es6方法

- [find方法 ](https://www.runoob.com/jsref/jsref-find.html)

	-  const hit1 = find(cache,c=>c.original===obj)

- es6对象扩展

### class语法糖

### var let const 变量提升和初始化提升，值是否可变，是否有块级作用域

- 变量提升、初始化提升

	- 找声明：var a
       function foo(){
         //函数里代码找声明时不看，调用时再看
         var a
         alert(a）
         a=2
       }
看代码：a=1
       foo.call()//调用了，看函数代码

		- 1.var 声明提升到函数或者作用域的顶端，
2.并初始化为undefined
3.赋值为1

- 值是否可变
- var 声明的"创建、初始化和赋值"过程

	- var有变量提升，有初始化提升，值可变
	- let有变量提升，没有初始化提升，值可变
	- const有变量提升，没有初始化提升，值不可变，但如果是定义对象，则属性可变

- 暂时性死区问题说明：其实let和const是有变量提升的，但是没有初始化提升

	- var name = '林三心'

function fn () {
  console.log(name)
  let name = 'sunshin_lin'
}
fn() // Cannot access 'name' before initialization


- 块级作用域解决问题：

	- for(var i = 0; i < 5; i++) {
  setTimeout(() => {
    console.log(i)
  })
} // 5 5 5 5 5


for(let i = 0; i < 5; i++) {
  setTimeout(() => {
    console.log(i)
  })
} // 0 1 2 3 4


		- let 声明和赋值在块级作用域
声明了n次i

			- for中let属于块级作用域的

- [地址](https://www.cnblogs.com/echolun/p/10584703.html)

### Object.getOwnPropertyNames()

- returns an array containing all the names of the own properties of the object passed as argument, including non-enumerable properties. It does not consider inherited properties.
- Object.getOwnPropertyNames()返回一个数组，其中包含作为参数传递的对象自身属性的所有名称，包括不可枚举的属性。 它不考虑继承的属性。

## 其他概念

### js数据类型&包装对象&内置对象

- 字符串方法
- 数组方法
- 对象方法

### 运算符操作

### 原型

- [知乎文章：说说原型（prototype）、原型链和原型继承](https://zhuanlan.zhihu.com/p/35790971)

- [廖雪峰的官方网站：原型继承](https://www.liaoxuefeng.com/wiki/1022910821149312/1023021997355072)

### 继承

### 作用域

- es6之前

	- 两个作用域

		- 全局作用域
		- 函数内部作用域

			- 函数可以限制变量的作用域

	- 特点

		- for循环内部，对象，{}等内部是没有作用域
		- 全局范围范围内，使用var定义的变量都是全局变量

- es6之后

	- {}内部作用域也就称为块级作用域
	- 特点

		- 使用let定义的变量只能在大括号{}内部有效

			- 比如循环内部，if内部，包括单独的{}内，是块级元素
			- [for循环内联声明，只在循环中可见，也算是块级作用域中的声明](https://blog.csdn.net/leo_franklin/article/details/112391939)

				- 外部声明方式：我们在外部用let声明key，也不用IIFE来创建作用域，那么结果就是key并没有自己独立的作用域

					- 效果：

				- 内联声明：在for循环中要想let产生自己的块级作用域，需要使用内联声明。

					- 子主题 1

		- {}内部作用域也就称为块级作用域，但是对象的{}内部仍然是没有作用域的.

### 作用域链

### 执行上下文

### call / apply / bind

### 闭包

### this

- 箭头函数this问题

	- 【理论1】

		- 箭头函数的this指向定义时外部作用域内的this指向，
普通函数的this指向调用时根据上下文取确认.

			- 所以也可以说箭头函数是没有this的

	- 【理论2】

		- 箭头函数需要记着这句话：“箭头函数中没有 this 绑定，必须通过查找作用域链来决定其值，如果箭头函数被非箭头函数包含，则 this 绑定的是最近一层非箭头函数的 this，否则，this 为 undefined”。

- [地址](https://www.jianshu.com/p/b62ca176417a)

- es5的this

	- this 永远指向最后调用它的那个对象。

- 函数的所有者和调用者

	- 【理论1】

		- 1、arguments.callee 返回当前运行的函数
2、arguments.callee.length 形参
3、arguments.length 实参

4、*.caller 返回当前函数的上下文也就是函数调用者
		- 函数的所有者，也就是this代表的对象
1,一般情况 o.function( this 这里的this就是指o)
2,function.call(o)
apply(o) 让o去调用function 所有o也就是所有者
		- 【例子】

			- function test(){
   alert(arguments.callee.length)// 0
   alert(arguments.length) //1
   alert(arguments.callee);// 就是这个函数
   alert(test.caller); // a
}
function a(){
   test("sss");
}
a();

	- 【理论2】

		- 函数的调用者指的是【函数被调用的域（可以理解函数本身）】，Function 对象的caller属性是对当前函数的函数的引用。如果该函数是从JavaScript程序的顶层调用的，caller的值为null。
函数的所有者指的是【调用这个函数的对象】。 
		- [【例子】](https://blog.csdn.net/zsc2014030403015/article/details/53862529)

- 函数调用的方法一共有 4 种

	- 作为一个函数调用

		- 这样一个最简单的函数，不属于任何一个对象，就是一个函数，这样的情况在 JavaScript 的在浏览器中的非严格模式默认是属于全局对象 window 的，在严格模式，就是 undefined。 
但这是一个全局的函数，很容易产生命名冲突，所以不建议这样使用。

	- 函数作为方法调用

		- 更多的情况是将函数作为对象的方法使用，我们一直记住的那句话“this 永远指向最后调用它的那个对象”，所以在 fn 中的 this 就是指向 a 的。

	- 使用构造函数调用函数

		- 如果函数调用前使用了 new 关键字, 则是调用了构造函数。
这看起来就像创建了新的函数，但实际上 JavaScript 函数是重新创建的对象
		- new的过程

			- 1.创建一个空对象 obj;
2.将新创建的空对象的隐式原型指向其构造函数的显示原型。
3.使用 call 改变 this 的指向
4.如果无返回值或者返回一个非对象值，则将 obj 返回作为新对象；如果返回值是一个新对象的话那么直接直接返回该对象。

	- 作为函数方法调用函数（call、apply）

		- 在 JavaScript 中, 函数是对象。
		- JavaScript 函数有它的属性和方法。call() 和 apply() 是预定义的函数方法。 两个方法可用于调用函数，两个方法的第一个参数必须是对象本身
		- 在 JavaScript 严格模式(strict mode)下, 在调用函数时第一个参数会成为 this 的值， 即使该参数不是一个对象。在 JavaScript 非严格模式(non-strict mode)下, 如果第一个参数的值是 null 或 undefined, 它将使用全局对象替代。

	- 总结

		- 1.这个简单一点的理解可以理解为“匿名函数的 this 永远指向 window”，
		- 2.你可以这样想，还是那句话this 永远指向最后调用它的那个对象，那么我们就来找最后调用匿名函数的对象，这就很尴尬了，因为匿名函数名字啊，笑哭，所以我们是没有办法被其他对象调用匿名函数的。
		- 3.所以说 匿名函数的 this 永远指向 window。
		- 4.如果这个时候你要问，那匿名函数都是怎么定义的，首先，我们通常写的匿名函数都是自执行的，就是在匿名函数后面加 () 让其自执行。
		- 5.其次就是虽然匿名函数不能被其他对象调用，但是可以被其他函数调用啊，比如例 7 中的 setTimeout。

### 立即执行函数表达式

### new

### 深浅拷贝

### 浏览器的多线程和js引擎的单线程

### 正则

- [一个讲得挺好的正则-掘金文章](https://juejin.cn/post/6999768570570178596?utm_source=gold_browser_extension)

- [正则讲得很好的官网地址](http://www.regexlab.com/zh/regref.htm)

- [另外一个正则讲得可以的地方](https://www.jb51.net/article/110516.htm)

### 文件同步异步加载

### 前端界面优化，大量数据，列表展示时，采用无尽滚动。

- [地址1](https://www.cnblogs.com/wwhhq/p/8169029.html)

	- 无限滚动就是一般常见的触底加载，滚动到页面底部加载更多数据，但是当数据量上来之后，达到千万数量级别，浏览器没法承载这么多的节点渲染，肯定会卡顿甚至崩溃，这个时候就可以使用虚拟列表，通过计算滚动视窗，每次只渲染可见屏幕部分节点，超出屏幕的不可见范围用内填充 padding 代替，对于浏览器来说无论你滚动到什么位置，渲染的都是屏幕范围内的节点，这样就不会有性能负担了。

- [实现方式地址2](https://www.jianshu.com/p/20faf7007860)

- [不要使用无限滚动](https://zhuanlan.zhihu.com/p/82817958)

### 无尽滚动

- [原理解释文档地址](https://juejin.cn/post/6844903463629881351)

- [github-demo地址](https://github.com/GoogleChromeLabs/ui-element-samples/tree/gh-pages/infinite-scroller)

- [貌似无尽滚动官方地址](https://developers.google.com/web/updates/2016/07/infinite-scroller)

- 图示：可以展示出无尽滚动的原理到底是啥样子的

### 下载实现方式

前端接受后端文件流并下载的几种方法: https://www.jianshu.com/p/8ef2c7b8b46c 前端js下载后端文件的两种方式总结: https://blog.csdn.net/u013944583/article/details/106856175/ 

https://www.cnblogs.com/lalalagq/p/10250640.html

- window.open(url)/window.location.href=url（后台提供静态目录和文件路径，get请求）
- 创建a标签 href=url download=filename a.click()（返回文件流response-type: application/octet-stream;charset=UTF-8 ）
- 上述对比第一种方式，通过 onprogress 捕获下载进度（界面通过显示进度条来提升体验）；通过 readystatechange 监听下载完后并可以做其它的事情；

### 防抖和节流

- 防抖：用户触发事件过于频繁，只要最后一次事件的操作

	- 错误姿势

		- // 貌似只做到了500ms之后做事情，操作事件次数并没有减少
let last;
    $scope.doFilter = function(e){
        last = e.timeStamp;
        setTimeout(function () {
            if(last - e.timeStamp == 0){
                refresh();
            }
        }, 500)
    };

	- 正确姿势

		- let lastTimer = null;
    $scope.doFilter = function () {
        if (lastTimer !== null) {
            clearTimeout(lastTimer);
        }
        lastTimer = setTimeout(function () {
            refresh();
        }, 500);
    };
		- // 自定义防抖函数
// 算法思路：500ms后执行一次事件回调，500ms以内重复调用，都是覆盖了上一次的调用（重置了）。停止覆盖，之后500ms后，才有机会执行一次回调
    function myDebounce(fn, delay) {
        let t = null;
        return function () {
            if (t !== null) {
                clearTimeout(t);
            }
            t = setTimeout(() => {
                fn.call(this);
            }, delay);
        };
    }
    $scope.doFilter = myDebounce(function () {
        refresh();
    }, 500);
		- 【正确理解】：

			- 个人理解 函数防抖就是法师发技能的时候要读条，技能读条没完再按技能就会重新读条。
			- 规定时间内，会打断上一次的计时执行，重新计时，然后执行一次

- 节流：控制执行次数，针对比较耗性能的操作
防抖：只执行最后一次

	- // 自定义节流
// 算法思路：500ms执行一次事件回调，500ms之内的调用，直接过滤了，或者说都进不来。控制频率
    function myThrottle(fn, delay) {
        let flag = true;
        return function () {
            if (flag) {
                setTimeout(() => {
                    fn.call(this);
                    flag = true;
                }, 500);
            }
            flag = false;
        };
    }
    window.onscroll = myThrottle(function () {
        console.log('事件触发了！');
    }, 500);
	- 【正确理解】

		- 个人理解 函数节流就是fps游戏的射速，就算一直按着鼠标射击，也只会在规定射速内射出子弹。
		- 规定时间内，无法进入计时，规定时间之外，才能重新进入计时

- 另外一种实现方式

	- [地址](https://juejin.cn/post/6844903669389885453#heading-3)

### 通配符转正则字符串

### mockjs和http-mock-middleware

动态后端代理 在前端开发阶段，有 mock 数据支持就够了，在前后端联调过程中，后端服务器的数据更真实，mock 数据反而不那么重要了。因此在必要的时候将数据代理到后端服务器就显得很有必要了。 http-mock-middleware 主要通过 X-Mock-Proxy 头来判断是否需要代理，下面使用 axios 库演示如何使用 localStorage 控制动态代理： const axios = require("axios"); axios.interceptors.request.use(function(config){ if(process.env.NODE_ENV === "development") { let mockHeader = localStorage.proxyUrl; if(mockHeader) { config.headers = config.headers || {}; config.headers["X-Mock-Proxy"] = mockHeader; } } // other code return config; }); 使用上面的代码，开发时不设置 localStorage.proxyUrl 使用假数据，联调时设置 localStorage.proxyUrl 指向后端服务器使用真数据。 注意：X-Mock-Proxy 的值是一个 url, 因为 http-mock-middleware 无法确定你的服务器是不是 https。通常你需要只设置为 http://host:port/ 就可以了 ￼ 这里的代码没有生效...并没有更新 .data里面的json文件啊, 这里的代码有在本地跑假数据的时候用到了. ￼ 是因为如下的代码: 因为http和https的问题, 这里不管加不加代理,不管是不是远程办公还是公司办公,都走的下面的代码,远程办公的话,会加上下面的agent配置 ￼ 这里的代码,target拼了一个https上去 secure:false取消掉了证书提醒的问题 ￼ 解读这里的代码:如下方 ￼ 翻译中的继承关系 ￼ 

### 游离 HEAD所对应的单独处理


    ￼


    ￼

此时游离HEAD的时候,分支名获取的是一个commitid

    ￼


### 手写mock数据代码

mock //billStatistics mock am.api.billStatistics.exec = function(data,cb){ setTimeout(function(){ cb({ "code": -1, "message": "success", "ts": 1473156708276, "content": { "customerSummary":{//客数汇总 "maleCount": 0, "femaleCount": 0, "specifiedCount": 0, "unspecifiedCount": 0, "specifiedMaleCount": 0, "unspecifiedMaleCount": 0, "specifiedFemaleCount": 0, "unspecifiedFemaleCount": 0, }, "perfSummary":{//业绩汇总 "servicePerf": 0.0, "productPerf": 0.0, "newCardPerf": 0.0, "rechargePerf": 0.0, "comboCardPerf": 0.0, "annualCardPerf": 0.0 }, "categorySummary":[//分项业绩汇总 { "serviceMajorCategoryName": "洗剪吹", "serviceMajorCategoryPerf": 0.0 }, { "serviceMajorCategoryName": "烫染焗", "serviceMajorCategoryPerf": 0.0 } ], "incomeSummary":{//收入汇总 "cash": 0.0,//现金 "pos": 0.0,//银联 "memCardPay": 0.0,//储值卡——会员卡 "memCardPresentPay":0.0,//储值卡赠送金支付 "comboCardPay": 0.0,//疗程卡 "comboCardPresentPay":0.0,//疗程卡赠送支付 "otherBillingPay": 0.0//其他支付 } } }) }) } 

### await async axios

- async 标记当前函数是异步函数，内部支持 await 等待异步执行。返回值是 Promise 实例。
- 所以你这样封装之后，外面使用封装后的函数时仍然需要 async/await。这样做有没有意义要看你怎么封装。一般来说，封装要发挥作用，至少要处理常见错误、提取真实数据，等。类似问题中这样不封装也罢。

### [二进制文件上传](https://cloud.tencent.com/developer/article/1684142?from=information.detail.js%E4%BA%8C%E8%BF%9B%E5%88%B6%E6%96%87%E4%BB%B6%E4%B8%8A%E4%BC%A0)

￼

- 图片处理相关

  /**
   * 媒体流转base64数据
   * @param {stream} videoStream 媒体流
   * @returns base64编码
   */
  export const canvasToDataURL = (videoStream) => {
    if (typeof videoStream !== "object") return "";
    // 创建画布
    let canvas = document.createElement("canvas");
    canvas.width = videoStream.videoWidth;
    canvas.height = videoStream.videoHeight;
    // 画布绘制
    var ctx = canvas.getContext("2d");
    ctx.drawImage(videoStream, 0, 0, canvas.width, canvas.height);
    // 绘制信息
    var linearGradient = ctx.createLinearGradient(0, 0, 300, 0);
    linearGradient.addColorStop("0", "#40E0D0");
    linearGradient.addColorStop("0.5", "#FF8C00");
    linearGradient.addColorStop("1.0", "#f7797d");
    ctx.font = "35px FZShuTi";
    ctx.fillStyle = linearGradient;
    ctx.fillText("Face-Api 简单使用", 20, 50);
    return canvas.toDataURL();
  };
  
  /**
   * base64字符串转二进制文件
   * @param {String} base64Date base64字符串
   * @returns Blob文件对象
   */
  export const base64ToBlob = (base64Date) => {
    let byteString = atob(base64Date.split(",")[1]);
    let mimeString = base64Date.split(",")[0].split(":")[1].split(";")[0];
    let ab = new ArrayBuffer(byteString.length);
    let ia = new Uint8Array(ab);
    for (let i = 0; i < byteString.length; i++) {
      ia[i] = byteString.charCodeAt(i);
    }
    return new Blob([ab], {
      type: mimeString,
    });
  };
  
  /**
   * 图片文件转base64
   * @param {Object} img 图片
   * @param {function} callback 回调函数
   */
  export const fileToBase64 = (img, callback) => {
    const reader = new FileReader();
    reader.addEventListener("load", () => callback(reader.result));
    reader.readAsDataURL(img);
  };
  
  /**
   * 保存base64字符串到文件下载 通过构建a链接方式
   * @param {String} data Base64字符串
   * @param {String} fileName 保存文件名
   */
  export const saveBase64ToFileObjectURL = (data, fileName) => {
    // 创建隐藏的可下载链接
    let eleLink = document.createElement("a");
    eleLink.download = fileName;
    eleLink.style.display = "none";
    eleLink.href = URL.createObjectURL(base64ToBlob(data));
    // 触发点击
    document.body.appendChild(eleLink);
    eleLink.click();
    // 然后移除
    document.body.removeChild(eleLink);
  };
  
	- 方法和案例

		- [区分 window.URL.createObjectURL() 和 FileReader.readAsDataURL()](https://blog.csdn.net/huoren_no1/article/details/108335827)

		- [Blob、File、FileReader 和 Data URL](https://blog.csdn.net/huangpb123/article/details/104178336?utm_medium=distribute.pc_relevant.none-task-blog-title-5&spm=1001.2101.3001.4242)

		- [上传图片 将图片转成二进制传递给后台](https://blog.csdn.net/qq_33771698/article/details/104041017)

		- [vue图片转换为二进制模拟表单传给后台](https://blog.csdn.net/lyc2786161648/article/details/84285146?utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-2.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-2.control)

		- data:text/html;charset=utf-8;charset=gbk,您好

			- 你好

		- data:text/html;charset=utf-8;base64,5L2g5aW9

			- 你好

		- 图片上传和显示

			- 只知道url地址，如何读取图片，然后，canvas转为base64，然后转为file对象

				- [
function getImgToBase64(url,callback){//将图片转换为Base64
  var canvas = document.createElement('canvas'),
    ctx = canvas.getContext('2d'),
    img = new Image;
  img.crossOrigin = 'Anonymous';
  img.onload = function(){
    canvas.height = img.height;
    canvas.width = img.width;
    ctx.drawImage(img,0,0);
    var dataURL = canvas.toDataURL('image/png');
    callback(dataURL);
    canvas = null;
  };
  img.src = url;
](https://blog.csdn.net/namechenfl/article/details/94737383)

			- url地址转base64图片

				- 知道url地址
用img读取img数据，然后用canvas.toDataURL转为dataURL

					-     function dataURLtoFile(dataurl, filename) {//将base64转换为文件
        var arr = dataurl.split(','), mime = arr[0].match(/:(.*?);/)[1],
            bstr = atob(arr[1]), n = bstr.length, u8arr = new Uint8Array(n);
        while(n--){
            u8arr[n] = bstr.charCodeAt(n);
        }
        return new File([u8arr], filename, {type:mime});
    }
					- getImgToBase64('img/test.png',function(data){
　　　var myFile = dataURLtoFile(data,'testimgtestimgtestimg');
　　　console.log(myFile);
});

		- 发送二进制文件到后端

			- FormData 对象的使用：
1.用一些键值对来模拟一系列表单控件：即把form中所有表单元素的name与value组装成
一个queryString
2. 异步上传二进制文件。
			-   var formData = new FormData();
    // 将文件转二进制
    *****注意2******
    formData.append('upload', file.files[0]);

	- 编码

- 文件上传方式
- 概念和方法

	- [几种常见编码总结](https://blog.csdn.net/liluo_2951121599/article/details/81661630?utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-1.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-1.control)

	- 概念

		- ArrayBuffer
		- [chartAt/charCodeAt/fromCharCode](https://www.runoob.com/jsref/jsref-charcodeat.html)

		- window.createObjectURL
		- canvas.drawImage
		- new File()
		- new Blob()
		- new FileReader

			- [fileReader.readAsDataURL](https://blog.csdn.net/qq_33771698/article/details/104041017)

		- new Image()
		- Uint8Array
		- atob,btoa
		- canvas.toDataURL
		- [dataurl](https://www.cnblogs.com/tianma3798/p/13582175.html)

		  https://www.cnblogs.com/tianma3798/p/13582105.html 
		  
		  
		  Data URL格式
		  
		  Data URI 的格式
		  
		  data:[<mime type>][;charset=<charset>][;base64],<encoded data>
		  
		  第一部分是 data: 协议头，它标识这个内容为一个 data URI 资源。
		  
		  
		  第二部分是 MIME 类型，表示这串内容的展现方式，比如：text/plain，则以文本类型展示，image/jpeg，以 jpeg 图片形式展示，同样，客户端也会以这个 MIME 类型来解析数据。
		  
		  
		  第三部分是编码设置，默认编码是 charset=US-ASCII, 即数据部分的每个字符都会自动编码为 %xx，关于编码的测试，可以在浏览器地址框输入分别输入下面两串内容，查看效果：
		  
		  ￼
		  // output: ä½ å¥½ -> 使用默认的编码展示，故乱码
		  data:text/html,你好  
		  // output: 你好 -> 使用 UTF-8 展示
		  data:text/html;charset=UTF-8,你好 
		  // output: 浣犲ソ -> 使用 gbk 展示（浏览器默认编码 UTF-8，故乱码）
		  data:text/html;charset=gbk,你好 
		  // output: 你好 -> UTF-8 编码，内容先使用 base64 解码，然后展示
		  data:text/html;charset=UTF-8;base64,5L2g5aW9 
		  ￼
		  
		  第四部分是 base64 编码设定，这是一个可选项，base64 编码中仅包含 0-9,a-z,A-Z,+,/,=，其中 = 是用来编码补白的。
		  
		  
		  最后一部分为这个 Data URI 承载的内容，它可以是纯文本编写的内容，也可以是经过 base64编码 的内容。
		  
		  
		  很多时候我们使用 data URI 来呈现一些较长的内容，如一串二进制数据编码、图片等，采用 base64 编码可以让内容变得更加简短。而对图片来说，在 gzip 压缩之后，base64 图片实际上比原图 gzip 压缩要大，体积增加大约为三分之一，所以使用的时候需要权衡。
		  
		  
		  参考: http://www.cnblogs.com/hustskyking/p/data-uri.html
		  
		  
		     /**
		       * base64  to blob二进制
		       */
		      function dataURItoBlob(dataURI) {
		          var mimeString = dataURI.split(',')[0].split(':')[1].split(';')[0]; // mime类型
		          var byteString = atob(dataURI.split(',')[1]); //base64 解码
		          var arrayBuffer = new ArrayBuffer(byteString.length); //创建缓冲数组
		          var intArray = new Uint8Array(arrayBuffer); //创建视图
		  
		          for (var i = 0; i < byteString.length; i++) {
		              intArray[i] = byteString.charCodeAt(i);
		          }
		          return new Blob([intArray], {type: mimeString});
		      }
		  
		      /**
		       * 
		       * blob二进制 to base64
		       **/
		      function blobToDataURI(blob, callback) {
		          var reader = new FileReader();
		          reader.onload = function (e) {
		              callback(e.target.result);
		          }
		          reader.readAsDataURL(blob);
		      }
		  
		  
		  
			- [JS 实现blob与base64互转](https://www.cnblogs.com/dcb3688/p/4608062.html)

### js 二进制数组

- [推荐阅读地址](https://blog.csdn.net/qq_38128179/article/details/106012003)

- 概念理解

	- ArrayBuffer
TypedArray
	- 这种数据类型占据的字节数

- ArrayBuffer和blob

	- 

### 密码相关的代码

- crypto.subtle

	- [地址](https://developer.mozilla.org/en-US/docs/Web/API/SubtleCrypto/importKey)

	- 代码

	  /**
	   * 字符串加密
	   * 此处鸣谢张垚、王川
	   */
	  function encryptStr (str) {
	      str = encodeURI(str);
	      const strBuf = new Uint8Array(str.split("").map(x => x.charCodeAt(0)));
	      const ivBuf = new Uint8Array(16);
	      crypto.getRandomValues(ivBuf);
	      const algorithm = { name: 'AES-CBC', iv: ivBuf };
	      const key = new Uint8Array([168, 134, 114, 247, 83, 133, 77, 235, 174, 252, 207, 35, 241, 57, 67, 74, 148, 231, 218, 186, 6, 174, 120, 211, 227, 93, 38, 253, 81, 157, 158, 197]);
	      return crypto.subtle.importKey('raw', key, algorithm, false, ['encrypt']).then(function (cryptoKey) {
	          return crypto.subtle.encrypt(algorithm, cryptoKey, strBuf);
	      }).then(function (encrypted) {
	          return { iv: u82hex(ivBuf), str: u82hex(new Uint8Array(encrypted)) };
	      });
	  }
	  function u82hex (u8) {
	      return Array.from(u8).map(a => (a < 16 ? '0' : '') + a.toString(16)).join("");
	  }
	  function encryptData (data) {
	      /*
	      let src = JSON.parse(JSON.stringify(data));
	      let keys = Object.keys(src);
	      let promises = [];
	      keys.forEach(key => {
	          promises.push(encryptStr(src[key]));
	      });
	      return Promise.all(promises).then((arr) => {
	          arr.forEach((val, i) => {
	              src[keys[i]] = val;
	          })
	          return src;
	      });
	      */
	  
	      return encryptStr(JSON.stringify(data));
	  }
	  
	  module.exports = {
	      encryptStr,
	      encryptData
	  };
	  
	  
- AES五种加密模式（CBC、ECB、CTR、OCF、CFB）

	- [地址](https://www.cnblogs.com/starwolf/p/3365834.html)

### window.location.hostname与 window.location.host 区别

- /**
 * window.location.hostname  不带端口号
 * window.location.host 带
 */

### 简单拖拽

- vue dom部分

  <div class="drag-list">
        <div
          class="drag-item"
          v-for="(item, index) in list"
          :key="index"
          :class="{
            'drag-start-item': dragId === item.id,
            'drag-enter-item': dragEnterId === item.id,
          }"
          draggable="true"
          @drag="onDrag"
          @dragstart="onDragstart($event, item)"
          @dragend="onDragend"
          @dragover="onDragover"
          @dragenter="onDragenter($event, item)"
          @dragleave="onDragleave"
          @drop="onDrop"
        >
          <div class="drag-item-content">
            <div class="item-icon"><img :src='item.img'></div>
             <div class="item-name">{{ item.title }}</div>
          </div>
        </div>
      </div>
  
  
  
- vue js逻辑部分

  onDrag (event) {},
      onDragstart (event, item) {
        this.dragId = item.id
        this.dragEnterId = null
      },
      onDragend (event) {
        this.dragId = null
        this.dragEnterId = null
      },
      onDragover (event) {
        event.preventDefault()
      },
      onDragenter (event, item) {
        this.dragEnterId = item.id
      },
      onDragleave (event) {},
      onDrop (event) {
        event.preventDefault()
  
        let drag = null
        let dragIndex = null
        let targetIndex = null
  
        this.list.forEach((item, index) => {
          if (item.id === this.dragId) {
            drag = item
            dragIndex = index
          }
          if (item.id === this.dragEnterId) {
            targetIndex = index
          }
        })
        if (dragIndex === targetIndex) {
          console.warn('起始与结束相同.')
          return
        }
  
        // 放下的位置大于等于目标宽带一半, 放到目标后面
        // 否则放到目标前面
        if (event.offsetX >= event.target.getBoundingClientRect().width / 2) {
          targetIndex++
        }
  
        // 先从原数组移除拖拽项
        this.list.splice(dragIndex, 1)
  
        // 如果拖拽项原本处于目标项左侧, 移除拖拽项会出目标位置造成影响
        if (dragIndex < targetIndex) {
          targetIndex--
        }
  
        // 把拖拽项插入到新位置
        this.list.splice(targetIndex, 0, drag)
      },
  
  
  
- 理解

	- 原生拖拽实现：拖着目标元素在页面任意位置

		- 

	- HTML5元素拖拽drag与拖放drop

		- 
		- 
		- 
		- 
		- 
		- 
		- 

	- javascript中的offsetWidth、clientWidth、innerWidth及相关属性方法

		- 

- [地址](https://blog.csdn.net/weixin_41910848/article/details/82218243)

### angularjs和vue对比

- 

### js位运算

- [地址](https://segmentfault.com/a/1190000013607145)

- [地址二](https://www.cnblogs.com/yf2196717/p/14738360.html)

### 如何判断是否为日期

- function isDate(str) {
    var reg = /^(\d{4})-(\d{1,2})-(\d{1,2})$/;
    if (!reg.test(str)) return false
    var r = str.match(reg);
    var d = new Date(r[1], r[2]-1, r[3])
    return d.getFullYear() == r[1] && d.getMonth() == r[2] -1 && d.getDate() == r[3]
}
console.log(isDate("2022-10-01"))

### V8 JS 代码的运行流程

## promise

### Promise.resolve等价于下面的写法

### 有时需要将现有对象转为 Promise 对象，Promise.resolve方法就起到这个作用。

### Promise.resolve('foo')

### // 等价于

### new Promise(resolve => resolve('foo'))

### [文章：JavaScript 中如何实现并发控制？](https://mp.weixin.qq.com/s?__biz=MzI2MjcxNTQ0Nw==&mid=2247490704&idx=1&sn=18976b9c9fe2456172c394f1d9cae88b&scene=21#wechat_redirect)

### promise的多次调用

- then 方法可以被同一个 promise 调用多次
- 当 promise 成功执行时，所有 onFulfilled 需按照其注册顺序依次回调
- 当 promise 被拒绝执行时，所有的 onRejected 需按照其注册顺序依次回调

### promise的返回

- then 方法必须返回一个 promise 对象 注3
- promise2 = promise1.then(onFulfilled, onRejected);
- 如果 onFulfilled 或者 onRejected 返回一个值 x ，则运行下面的 Promise 解决过程：[[Resolve]](promise2, x)
- 如果 onFulfilled 或者 onRejected 抛出一个异常 e ，则 promise2 必须拒绝执行，并返回拒因 e
- 如果 onFulfilled 不是函数且 promise1 成功执行， promise2 必须成功执行并返回相同的值
- 如果 onRejected 不是函数且 promise1 拒绝执行， promise2 必须拒绝执行并返回相同的据因
- 译者注： 理解上面的“返回”部分非常重要，即：不论 promise1 被 reject 还是被 resolve 时 promise2 都会被 resolve，只有出现异常时才会被 rejected。

### promise的解决过程

- Promise 解决过程 是一个抽象的操作，其需输入一个 promise 和一个值，我们表示为 [[Resolve]](promise, x)，如果 x 有 then 方法且看上去像一个 Promise ，解决程序即尝试使 promise 接受 x 的状态；否则其用 x 的值来执行 promise 。
- 这种 thenable 的特性使得 Promise 的实现更具有通用性：只要其暴露出一个遵循 Promise/A+ 协议的 then 方法即可；这同时也使遵循 Promise/A+ 规范的实现可以与那些不太规范但可用的实现能良好共存。
- 运行 [[Resolve]](promise, x) 需遵循以下步骤：

	- 2.3.1 x 与 promise 相等

		- 如果 promise 和 x 指向同一对象，以 TypeError 为据因拒绝执行 promise

	- 2.3.2 x 为 Promise

		- 如果 x 为 Promise ，则使 promise 接受 x 的状态:注4
		- 如果 x 处于等待态， promise 需保持为等待态直至 x 被执行或拒绝
		- 如果 x 处于执行态，用相同的值执行 promise
		- 如果 x 处于拒绝态，用相同的据因拒绝 promise

	- 2.3.3 x 为对象或函数

		- 如果 x 为对象或者函数：
		- 把 x.then 赋值给 then注5
		- 如果取 x.then 的值时抛出错误 e ，则以 e 为据因拒绝 promise
		- 如果then是函数，将x作为函数的作用域this调用之。传递两个回调函数作为参数，第一个参数叫做resolvePromise，第二个参数叫做rejectPromise:
		- 如果 resolvePromise 以值 y 为参数被调用，则运行 [[Resolve]](promise, y)
		- 如果 rejectPromise 以据因 r 为参数被调用，则以据因 r 拒绝 promise
		- 如果 resolvePromise 和 rejectPromise 均被调用，或者被同一参数调用了多次，则优先采用首次调用并忽略剩下的调用
		- 如果调用then方法抛出了异常e：
		- 如果 resolvePromise 或 rejectPromise 已经被调用，则忽略之
		- 否则以 e 为据因拒绝 promise
		- 如果 then 不是函数，以 x 为参数执行 promise

	- 2.3.4 x 不为对象或函数

		- 如果 x 不为对象或者函数，以 x 为参数执行 promise

			- If x is not an object or function, fulfill promise with x.
			- 执行promise 意思： fulfill promise

		- 如果一个 promise 被一个循环的 thenable 链中的对象解决，而 [[Resolve]](promise, thenable) 的递归性质又使得其被再次调用，根据上述的算法将会陷入无限递归之中。算法虽不强制要求，但也鼓励施者检测这样的递归是否存在，若检测到存在则以一个可识别的 TypeError 为据因来拒绝 promise。注6

### 【示例】

- onRejected 不是函数并且p1是rejected，p2就是rejected

