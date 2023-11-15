---
created: 2023-11-15T20:47
updated: 2023-11-15T20:47
---
# angularjs

## 模块

angularjs 诞生于 2009 年，那时候前端还没有模块化的标准，angularjs 在API层面探索了模块的概念。一个模块由任意个服务组成

### 服务

- 生命周期

  angularjs 文档里面并无生命周期的概念，这里为了方便理解，对不同服务按照可访问性的时间顺序划分为不同的声明周期
  
	- app生命周期

		- 配置阶段

			- 在app启动之时，在创建service之前，它会配置和实例化所有的provider，我们把这个叫做app生命周期的配置阶段，在这个阶段，service还不可使用，因为他们还未创建。
			- 一旦配置阶段完成，那么所有的provider变为不可用，创建service的进程开始启动，这个阶段被叫做app生命周期的运行阶段。
			- Constant“配方”在配置阶段是可用的

		- 运行阶段

	- 初始化前
	- 初始化后

		- 实例化前
		- 实例化后

- 类型

  在 angularjs 模块里面一切都是服务，只是表象不同而已，表象不同是因为它们的使用时机不同，然后不同的服务对封装的需求不同。
  
	- provider
	- service
	- factory

		- AngularJS中的服务其实就是提供一种方式抽取共用类库

			- 服务是controller 之间的胶水， 因为service 在angular中是单例的。每个服务都只有一个实例，它相当于就是一个中介，我们可以在两个控制器中都注入这个服务，然后通过这个服务来传递一些数据。

	- constant
	- value
	- decorator

		- 装饰器
		- ngModelDirective

			- 例子：这里delegate为什么是数组？ctrls为什么是数组，就要看ngModelDirective了

				- 原理1：ngModelDirective
				- 原理2：Form

					- [地址](https://www.cnblogs.com/whitewolf/p/3560418.html)

					- formControl

### 指令、控制器

指令和控制器本身不是服务，但它们被处理的方式和服务是一样的，除此之外，angularjs 为它们提供了额外的支持，比如：指令会被编译，控制器会被初始化并和 Scope 一起工作。

- ngModel

	- ngModelCtrl

		- $setViewValue方法

			- 例子1
			- 参数

				- value:string

					- value参数是我们想要赋值给ngModel实例的实际值

			- 方法描述

				- 这个方法会更新控制器上本地的$viewValue，然后将值传递给每一个$parser函数（包括验证器）
				- 当值被解析，且$parser流水线中所有的函数都调用完成后，值会被赋给$modelValue属性，并且传递给指令中ng-model

### 钩子

- config

	- config方法

		- 在模块加载阶段，对模块进行自定义配置
		- 在模块上添加的服务，指定等，实际上都是在config阶段配置的。
		- config 运行时，只能访问 provider, constant
		- 作用：对provider进行配置

	- 例子合集

		- 例子1
		- 例子2
		- 例子3
		- 例子4
		- 例子5
		- 例子6
		- 例子7
		- 例子8

- run

	- run方法

		- 是应用中最先执行的方法，类似于main方法，run方法只会在angular启动的时候运行一次，定义全局的数据或逻辑，对全局作用域起作用，$rootScope上内容在多个控制器之间可以共享。例如，注册一个全局的事件监听器。每次路由发生变化时候，都执行一个函数来验证用户的权限。
		- run 运行时，各个服务已经实例化完毕，可以任意使用，除了 provider,
		- 作用：
		- run方法用于初始化全局的数据，仅对全局作用域起作用。
		- 所有服务可以使用了。
		- 做一些初始化的事情

	- 例子合集

		- 例子1
		- 例子2
		- 例子3
		- 例子4
		- 例子5
		- 例子6

- 执行顺序

	- 执行顺序不同:config先执行，run后执行。另外，ng启动阶段是 config-->run-->compile/link

## 依赖注入

依赖注入，也可以理解为：注入依赖。
这里的依赖指服务。
谁需要注入依赖？每个服务可以任意注入其它依赖，所有依赖的服务实例化后，才会实例化当前服务

### 服务初始化前 provider only

### 服务初始化后 provider except

## 模板

### 表达式

- 任意可以求值的js表达式
- 过滤器

### 字符串插值

{{ value }}

### HTML

## 控制器

控制器的角色定位有点尴尬，它能做 Scope 做不到的事情，也能做 Scope 能做的事情。
控制器，如同其名字一样，它做的事情是控制，也就是行为。作为一个函数，除了行为，它还能借机做一些其它的事情，这就看具体使用场景了。

### 数据载体

### 行为函数载体

### 默认行为载体

### 默认数据载体

### 服务消费者

## Scope

Scope 是 angularjs 的核心，从 API 层面看，Scope 负责的主要是数据，但它也可以附带行为，这和控制器是有一定的功能重叠的。
一个方法是挂在控制器上好一些，还是挂在 Scope 上好一些？没有标准答案，我想这也是控制器、Scope二者功能重叠的一方面原因吧。
Scope 持有父 Scope 的引用，也持有所有子 Scope 的引用，所以从 Scope 的视角来看，页面上所有的 Scope 构成了一棵 Scope 树，每个 Scope 被一个控制器包围起来，它们有自己的数据和行为

### 数据载体

### 行为函数载体

### 监测数据

### 响应数据变化

### 树形

### 隔离

## 指令

指令系统的完善为 angularjs 提供了各种开箱即用的功能，如：双向绑定，表单校验，事件绑定，循环等等。

### 操作DOM

### 绑定事件

### 数据交互

### 封装

## 过滤器

### 数据转换

### 数据筛选

## 函数

### 对象拷贝：angular.copy(), angular.extend()

### 类型检测：angular.is*()

### 包装为类 jQuery 对象：angular.element()

### 异步启动：angular.bootstrap()

## 内置服务

### $http

### $q

### $timeout/$interval

### $window/$document/$location

### $compile/$interpolate/$parse

## 内置指令

### 数据绑定：ng-model/ng-bind/ng-value

### 渲染，可见性：ng-if/ng-show/ng-hide

### 表单元素状态：ng-checked/ng-readonly/ng-selected

### 样式：ng-class/ng-style

### 表单默认：input/select/form/textarea

### 事件：ng-click/ng-mouse*/ng-key*

### ng-switch/ng-repeat/ng-options

### ng-app

## ngResources

## ngRoute

## 5种方法创建服务

## angular.bootstrap()

### 手动初始化
Angular中也提供了手动绑定的api——bootstrap，它的使用方式如下：

angular.bootstrap(element, [modules], [config]);

## angular.module("ng");

### 一个参数

- 调用这个方法时如果只传递一个参数，就可以用它来引用模块。例如，可以通过以下代码来引用myApp模块
- 这个方法相当于AngularJS模块的getter方法，用来获取对模块的引用。
接下来，就可以在angular.module('myApp')返回的对象上创建我们的应用了。
- 用来获取对模块的引用

### 两个参数

- 第二个参数是一个空数组，这个空数组是为了指定在此module中需要用到哪些其他的modules。
- 现在，我们定义另一个module
- angular.module('myApp.services', [])

## 问题

### ng-if同ng-show和ng-hide指令最本质的区别

- 怪异的ng-if内部的ng-mode问题

	- 现象

		- 1. 直接使用字符串

			-  将创造一个新的data ，即使在父作用域中存在具有相同名称的模型。
			- 直接使用 字符串 作为ng-model的变量，父作用域获取不到。

				- 参考链接

					- [地址](https://www.jb51.cc/angularjs/149094.html)

				- 解决方法：

					- 在父作用域中定义对象，使用对象作为ng-model的变量。
					- "config.validateCode"> </div>

		- 2. 使用点符号的表达式

			- 让 JS 查找范围的原型链
			- 因此，如果它在当前作用域中找不到该值，它将尝试在父作用域中寻找该值，以此类推。

		- 总结：上面1，2是字符串和表达式的区别？

	- 当一个元素被ng-if从DOM中移除，同它关联的作用域也会被销毁。而且当它重新加入DOM中时，会通过原型继承从它的父作用域生成一个新的作用域。
这样会导致，在 ng-if 中用基本变量绑定 ng-model ，并在外层 div 中把此 model 绑定给另一个显示区域，内层改变时，外层不会同步改变，因为此时已经是两个变量了。

		- <p>{{name}}</p>
<div ng-if="true">
<input type="text" ng-model="name" />
</div>


	- 所以遇到ng-model外部有ng-if时，需要进行使用let models = $scope.m = {},避免问题出现
	- 参考链接

		- stackoverflow

			- [地址](https://stackoverflow.com/questions/19177732/what-is-the-difference-between-ng-if-and-ng-show-ng-hide)

				- If ngModel is used within ngIf to bind to a JavaScript primitive defined in the parent scope, any modifications made to the variable within the child scope will not affect the value in the parent scope, e.g.

					- 如果在 ngIf 中使用 ngModel 绑定到父作用域中定义的 JavaScript 原语，那么对子作用域中的变量所做的任何修改都不会影响父作用域中的值
					- 

	- 【解决方案】：

		- hack1：使用ng-show代替ng-if(该方法简单有效)
		- hack2:   在绑定值时添加$parent标识
		- 比如：原来是$scope.canClcik=true；   ng-if="canClick"
		- $scope创建一个子对象obj,如$scope.obj.canClcik=true;   ng-if="obj.canClick"即可生效。

- 它不是通过CSS显示或隐藏DOM节点，而是真正生成或移除节点。

	- 例子1 ：正确使用ng-if和ng-show - april吖～ - 博客园 (cnblogs.com)

		- [文章地址](https://www.cnblogs.com/iceseal/p/4077417.html)

		- 理解：按钮组，也就是btn-group，如果仔细观察的话，会发现一个按钮组的第一个和最后一个按钮分别是有圆角的，仅仅隐藏，其中最后一个，第二个按钮是没有圆角的，因为样式还是作用在隐藏中的第三个元素中了。

	- 文章二：What is the difference between ng-if and ng-show/ng-hide

		- [地址](https://stackoverflow.com/questions/19177732/what-is-the-difference-between-ng-if-and-ng-show-ng-hide angularjs - What is the difference between ng-if and ng-show/ng-hide - Stack Overflow)

## angularjs中的$parse,$eval,$compile

### [地址](https://blog.csdn.net/qq_27870421/article/details/102627557)

### [地址2](https://www.jb51.net/article/95328.htm)

### context上下文

- 控制器就相当于一个上下文的容器，真正的上下文其实是$scope,
- 如果没有声明控制器，他的上下文容器就是ng-app了，那么他真正的上下文就是$rootScope，这个时候他就会寻找$rootScope有没有test。
- 基本上和this非常相似

### $parse

- 代码片段

	- var getter = $parse('user.name');
var setter = getter.assign;
var context = {user:{name:'angular'}};
var locals = {user:{name:'local'}};
 
expect(getter(context)).toEqual('angular');
setter(context, 'newValue');
expect(context.user.name).toEqual('newValue');
expect(getter(context, locals)).toEqual('local');

		- getter和setter就是大家所熟知的get方法和set方法了
		- context和locals仅仅是json对象而已，目的就是模拟上下文关系
		- getter(context)).toEqual('angular') //实际上就是 $parse('user.name')(context)

			- 1.获取当前的表达式user.name
2.获取当前的上下文对象{user:{name:'angular'}}
3.在上下文对象中寻找表达式的值，最终获得“angular“这个字符串

		- setter(context, 'newValue');//实际上就是 $parse('user.name').assign(context, 'newValue')
expect(context.user.name).toEqual('newValue');//测试数据上下文的值是否被改变

			- 这里的setter方法其实是改变值的方法
			- 1. 获取当前的表达式user.name
2.获取当前的上下文对象{user:{name:'angular'}}
3.改变表达式中的值，将上下文对象变成{user:{name:'newValue'}}

		- 于是上下文对象发生了改变，重新用getter方法去获取表达式的时候，上下文已经从{user:{name:'angular'}} --> {user:{name:'newValue'}},最后获取的表达式的值自然就是“newValue”了，
		- expect(getter(context, locals)).toEqual('local');//实际上就是$parse('user.name')(context, locals)

### $eval

- $eval: function(expr, locals) {
    return $parse(expr)(this, locals);
   },
- 只能算是$parse的另一种写法而已

### $compile

- 其实和$parse很像。但是他是解析一段html代码的，他的功能就是将死模板变成活模板，也是指令的核心服务。
- $compile('死模板')(上下文对象)，这样就将死模板编程了活模板，你就可以对这段活的html代码做操作了，例如增加到当前节点
- 但是在指令中的compile属性，它会返回两个函数pre-link和post-link

第一个执行的是pre-link，它对于同一个指令的遍历顺序是从父节点到子节点的遍历，在这个阶段，dom节点还没有稳定下来，无法做一些绑定事件的操作，但是我们可以在这里进行一些初始化数据的处理。

第二个执行的是post-link，也就是我们常说的link函数，他是从子节点到父节点遍历的，在这个阶段，DOM节点已经稳定下来了，我们一般会在这里进行很多的操作。

### 【示例】

- 
- $watch监听函数listener，第一个参数为listener function，第二个参数change handler

## 文章：angularjs中ui插件ui-bootstrap中的modal模态弹出源码分析

### [地址](https://www.jianshu.com/p/51d5c372e018)

### scope.$eval('$dismiss()')

- 关闭当前弹窗

### [文章：浅谈angular-ui-bootstrap-modal这个骚东西](https://my.oschina.net/u/3492622/blog/1509975)

- 【查看源码】

	- modalScope作用域上的$close，$dismiss
	- $modalStack服务dismiss方法

- 【示例】

	- 

- 【示例2】

	- 

## angularjs $compile服务及$scope.$eval实现html动态模板解析

### $eval

- $scope.$eval:angularjs $scope内置方法和$parse()服务一样，用解析字符串变量
例子：$scope.html='nihao';$scope.html2='html'  $scope.$eval('html2') //返回'nihao'*   

### $compile

- $compile:angularjs内置的服务，接受一个需要编译字符串参数，变生成一个function，function要求传入一个scope,
 - 并通过此scope编译当前字符串模板
 - 例子：
 - $scope.html="<div ng-click='doSomeThing()'></div>"
 - var func=$compile(html);
 - var innerHtml=func($scope)//通过当前$scope编译字符串
 - 简写就是:var innerHtml=$compile(html)($scope);
- 例子

	- js
	- html

## 如何衡量一个人的 AngularJS 水平？

### 基础

- 1. ng-if跟ng-show/hide的区别有哪些？

	- 第一点区别是，ng-if 在后面表达式为 true 的时候才创建这个 dom 节点，ng-show 是初始时就创建了，用 display:block 和 display:none 来控制显示和不显示。
	- 第二点区别是，ng-if 会（隐式地）产生新作用域，ng-switch 、 ng-include 等会动态创建一块界面的也是如此。

- 2. ng-repeat迭代数组的时候，如果数组中有相同值，会有什么问题，如何解决？

	- 会提示 Duplicates in a repeater are not allowed. 加 track by $index 可解决。当然，也可以 trace by 任何一个普通的值，只要能唯一性标识数组中的每一项即可（建立 dom 和数据之间的关联）。
	- 目前遇到一个特殊情况，id是不可靠的，id可以忽而uuid，忽而数字id

		- 采用track by (item.id + $index)

- 3. ng-click中写的表达式，能使用JS原生对象上的方法，比如Math.max之类的吗？为什么？

	- 不可以。只要是在页面中，就不能直接调用原生的 JS 方法，因为这些并不存在于与页面对应的 Controller 的 $scope 中。除非在 $scope 中添加了这个函数：
	- $scope.parseInt = function(x){
    return parseInt(x);
}
	- 执行时如$scope.Math.max

- 4. {{now | 'yyyy-MM-dd'}}这种表达式里面，竖线和后面的参数通过什么方式可以自定义？

	- 定义方式：
	- app.filter('过滤器名称',function(){
    return function(需要过滤的对象, 过滤器参数1, 过滤器参数2, ...){
        //...做一些事情   
        return 处理后的对象;
    }
});
	- 使用方式有两种，一种是直接在页面里：
	- <p>{{now | date : 'yyyy-MM-dd'}}</p>
	- 一种是在 js 里面用：
	- // $filter('过滤器名称')(需要过滤的对象, 参数1, 参数2,...)
$filter('date')(now, 'yyyy-MM-dd hh:mm:ss');

- 5. factory和service，provider是什么关系？

	- factory 把 service 的方法和数据放在一个对象里，并返回这个对象；service 通过构造函数方式创建 service，返回一个实例化对象；provider 创建一个可通过 config 配置的 service。
	- 从底层实现上来看，service 调用了 factory，返回其实例；factory 调用了 provider，将其定义的内容放在 $get 中返回。factory 和 service 功能类似，只不过 factory 是普通 function，可以返回任何东西（return 的都可以被访问，所以那些私有变量怎么写你懂的）；service 是构造器，可以不返回（绑定到 this 的都可以被访问）；provider 是加强版 factory，返回一个可配置的 factory。

### 深度

- 1. angular的数据绑定采用什么机制？详述原理

	- 脏检查机制。
	- Angular 在 scope 模型上设置了一个监听队列，用来监听数据变化并更新 view 。每次绑定一个东西到 view 上时 AngularJS 就会往 $watch 队列里插入一条 $watch，用来检测它监视的 model 里是否有变化的东西。当浏览器接收到可以被 angular context 处理的事件时，$digest 循环就会触发，遍历所有的 $watch，最后更新 dom。

		- 举个栗子：
<button ng-click="val=val+1">increase 1</button>
		- click 时会产生一次更新的操作（至少触发两次 $digest 循环）:
		- 按下按钮
		- 浏览器接收到一个事件，进入到 angular context
		- $digest 循环开始执行，查询每个 $watch 是否变化
		- 由于监视 $scope.val 的 $watch 报告了变化，因此强制再执行一次 $digest 循环
		- 新的 $digest 循环未检测到变化
		- 浏览器拿回控制器，更新 $scope.val 新值对应的 dom

	- $digest 循环的上限是 10 次（超过 10次后抛出一个异常，防止无限循环）。

- 2. 两个平级界面块a和b，如果a中触发一个事件，有哪些方式能让b知道，详述原理

	- 这个问题换一种说法就是，如何在平级界面模块间进行通信。有两种方法，一种是共用服务，一种是基于事件。

		- a. 共用服务

			- 在 Angular 中，通过 factory 可以生成一个单例对象，在需要通信的模块 a 和 b 中注入这个对象即可。

		- b. 基于事件

			- 这个又分两种方式

				- 第一种是借助父 controller。

					- 在子 controller 中向父 controller 触发（$emit）一个事件，然后在父 controller 中监听（$on）事件，再广播（$broadcast）给子 controller ，这样通过事件携带的参数，实现了数据经过父 controller，在同级 controller 之间传播。

				- 第二种是借助 $rootScope。

					- 每个 Angular 应用默认有一个根作用域 $rootScope， 根作用域位于最顶层，从它往下挂着各级作用域。所以，如果子控制器直接使用 $rootScope 广播和接收事件，那么就可实现同级之间的通信。

- 3. 一个angular应用应当如何良好地分层？

	- 分两个方面讲

		- a. 目录结构的划分

			- 对于小型项目，可以按照文件类型组织，比如

				- css
js
  controllers
  models
  services
  filters
templates 

			- 但是对于规模较大的项目，最好按业务模块划分，比如

				- css
modules
  account
    controllers
    models
    services
    filters
    templates
  disk
    controllers
    models
    services
    filters
    templates
				- modules 下最好再有一个 common 目录来存放公共的东西。

		- b. 逻辑代码的划分

			- 作为一个 MVVM 框架，Angular 应用本身就应该按照 模型，视图模型（控制器），视图来划分。
			- 这里逻辑代码的拆分，主要是指尽量让 controller 这一层很薄。提取共用的逻辑到 service 中 （比如后台数据的请求，数据的共享和缓存，基于事件的模块间通信等），提取共用的界面操作到 directive 中（比如将日期选择、分页等封装成组件等），提取共用的格式化操作到 filter 中等等。
			- 在复杂的应用中，也可以为实体建立对应的构造函数，比如硬盘（Disk）模块，可能有列表、新建、详情这样几个视图，并分别对应的有 controller，那么可以建一个 Disk 构造函数，里面完成数据的增删改查和验证操作，有跟 Disk 相关的 controller，就注入 Disk 构造器并生成一个实例，这个实例就具备了增删改查和验证方法。这样既层次分明，又实现了复用（让 controller 层更薄了）。

- 4. angular应用常用哪些路由库，各自的区别是什么？

	- Angular1.x 中常用 ngRoute 和 ui.router，还有一种为 Angular2 设计的 new router（面向组件）。后面那个没在实际项目中用过，就不讲了。
	- 无论是 ngRoute 还是 ui.router，作为框架额外的附加功能，都必须以 模块依赖 的形式被引入。
	- 两者区别是：

		- ngRoute 模块是 Angular 自带的路由模块，而 ui.router 模块是基于 ngRoute模块开发的第三方模块。
		- ui.router 是基于 state （状态）的， ngRoute 是基于 url 的，ui.router模块具有更强大的功能，主要体现在视图的嵌套方面。
		- 使用 ui.router 能够定义有明确父子关系的路由，并通过 ui-view 指令将子路由模版插入到父路由模板的 <div ui-view></div>  中去，从而实现视图嵌套。而在 ngRoute 中不能这样定义，如果同时在父子视图中 使用了 <div ng-view></div> 会陷入死循环。

- 5. 如果通过angular的directive规划一套全组件化体系，可能遇到哪些挑战？

	- 能想到的一点是，组件如何与外界进行数据的交互，以及如何通过简单的配置就能使用吧。

- 6. 分属不同团队进行开发的angular应用，如果要做整合，可能会遇到哪些问题，如何解决？

	- 可能会遇到不同模块之间的冲突。比如一个团队所有的开发在 moduleA 下进行，另一团队开发的代码在 moduleB 下：
	- angular.module('myApp.moduleA', [])
    .factory('serviceA', function(){
        ...
    })

angular.module('myApp.moduleB', [])
    .factory('serviceA', function(){
        ...
    })    

angular.module('myApp', ['myApp.moduleA', 'myApp.moduleB'])

		- 会导致两个 module 下面的 serviceA 发生了覆盖。

貌似在 Angular1.x 中并没有很好的解决办法，所以最好在前期进行统一规划，做好约定，严格按照约定开发，每个开发人员只写特定区块代码。

- 7. angular的缺点有哪些？

	- a. 强约束

		- 导致学习成本较高，对前端不友好。
		- 但遵守 AngularJS 的约定时，生产力会很高，对 Java 程序员友好。

	- b. 不利于 SEO

		- 因为所有内容都是动态获取并渲染生成的，搜索引擎没法爬取。
		- 一种解决办法是，对于正常用户的访问，服务器响应 AngularJS 应用的内容；对于搜索引擎的访问，则响应专门针对 SEO 的HTML页面。

	- c. 性能问题

		- 作为 MVVM 框架，因为实现了数据的双向绑定，对于大数组、复杂对象会存在性能问题。
		- 可以用来 优化 Angular 应用的性能 的办法：

			- 减少监控项（比如对不会变化的数据采用单向绑定）
			- 主动设置索引（指定 track by，简单类型默认用自身当索引，对象默认使用 $$hashKey，比如改为track by item.id）
			- 降低渲染数据量（比如分页，或者每次取一小部分数据，根据需要再取）
			- 数据扁平化（比如对于树状结构，使用扁平化结构，构建一个 map 和树状数据，对树操作时，由于跟扁平数据同一引用，树状数据变更会同步到原始的扁平数据）

	- d. 移动端

- 8. 如何看待angular 1.2中引入的controller as 语法？

	- 在 angular 1.2 以前，在 view 上的任何绑定都是直接绑定在 $scope 上的。使用 controllerAs，不需要再注入 $scope，controller 变成了一个很简单的 javascript 对象（POJO），一个更纯粹的 ViewModel。

		- 从源码实现上来看，controllerAs 语法只是把 controller 这个对象的实例用 as 别名在 $scope 上创建了一个属性。

			- if (directive.controllerAs) {
    locals.$scope[directive.controllerAs] = controllerInstance;
}

		- 但是这样做，除了上面提到的使 controller 更加 POJO 外，还可以避免遇到 AngularJS 作用域相关的一个坑（就是上文中 ng-if 产生一级作用域的坑，其实也是 javascript 原型链继承中值类型继承的坑。因为使用 controllerAs 的话 view 上所有字段都绑定在一个引用的属性上，比如 vm.xx，所以坑不再存在）。
		- 不过不引入 $scope 会出现的一个问题是，导致 $emit、 $broadcast、 $on、$watch 等 $scope 下的方法无法使用。这些跟事件相关的操作可以封装起来统一处理，或者在单个 controller 中引入 $scope，特殊对待。

- 9. 详述angular的“依赖注入”

	- AngularJS 是通过构造函数的参数名字来推断依赖服务名称的，通过 toString() 来找到这个定义的 function 对应的字符串，然后用正则解析出其中的参数（依赖项），再去依赖映射中取到对应的依赖，实例化之后传入。
	- 因为 AngularJS 的 injector 是假设函数的参数名就是依赖的名字，然后去查找依赖项，那如果像下面这样简单注入依赖，代码压缩后（参数被重命名了），就无法查找到依赖项了。

		- function myCtrl = ($scope, $http){
    ...
}

	- 所以，通常会使用下面两种方式注入依赖（对依赖添加的顺序有要求）。

		- 数组注释法：

			- myApp.controller('myCtrl', ['$scope', '$http', function($scope, $http){
    ...
}])

		- 显式 $inject ：

			- myApp.controller('myCtrl', myCtrl);
function myCtrl = ($scope, $http){
    ...
}
myCtrl.$inject = ['$scope', '$http'];

	- 对于一个 DI 容器，必须具备三个要素：依赖项的注册，依赖关系的声明和对象的获取。在 AngularJS 中，module 和 $provide 都可以提供依赖项的注册；内置的 injector 可以获取对象（自动完成依赖注入）；依赖关系的声明，就是上面的那两种方式。

- 10.  如何看待angular 2……

## AngularJS 的自定义指令

### 1. 通用的功能，和业务无关的组件，比如某些只读的 input 输入框点击后选中所有内容，一般做法是绑定一个 ng-click="doFun()",然后在doFunc 中选中 input，封装一个directive后，就可以在input上使用属性 xxx-click-select，代码可读性增高，同时又耦合了；

### 2. 需要操作 DOM 的地方，建议封装一个directive去做；

### 3. 使用了一个第三方的组件（例如jQuery插件），又没有ng的封装版本，有时候需要自己封装directive去调用第三方组件；

### 4. 业务中一些模块需要多个地方使用，最后封装成一个directive，把调用输入参数定义好，这样在使用的地方就可以如1一样很简单的调用；

### 5. 其实如果想用可以随时使用自定义 directive，就比如 ng-include="'tasks.item.html'"， 就可以封装成一个 Element的 Directive，这样调用的时候就可以很优雅的使用 <tasks-item></tasks-item> ，这样使代码更可读更简洁，当然寻找代码变得费劲了，需要先找到 tasks-item Directive，才能找到对应的模板，只要代码结构组织好，封装directive的人经验丰富，对于调用者来说其实不需要关心细节。

## angularjs 优化点：

### 1.之前写过的不好用的指令，进行优化

### 2.有些不好维护的代码，about界面，显示问题，激活界面显示问题，跟翻译相关的

### 3.表格方面，既有表格方式，又有瓦片方式，如何封装。

## angularjs 其中一个项目例子

### [地址](https://github.com/yyhsong/iAngularJS)

- [博客地址](https://blog.csdn.net/hwhsong/article/details/54345868)

### [例子2地址](https://github.com/taobataoma/meanTorrent/tree/master/modules/medals/client/controllers)

### [angularjs-imageupload-directive例子](https://github.com/Mischi/angularjs-imageupload-directive/blob/master/public/javascripts/imageupload.js)

## 目前来看，angularjs最大提升的办法就是看angularjs源码了

### [angularjs源码博客地址](https://blog.csdn.net/WuLex/article/details/79696425)

### [angularjs源码文件ng地址](https://github.com/angular/angular.js/tree/master/src/ng)

### [angularjs源码directive地址](https://github.com/angular/angular.js/tree/master/src/ng/directive)

## angularjs中 factory，service，provoder区别

### [地址1](https://segmentfault.com/a/1190000004602085)

## angularjs中的一个异常行为，弹窗关闭时，可能概率性报错

### Dismiss angular modal on URL change - errors in console

### 报错内容为：

- 

### ui-bootstrap-custom-tpls-0.11.0.js文件中$modalStack.close = function (modalInstance, result) {
        var modalWindow = openedWindows.get(modalInstance).value;
        if (modalWindow) {
          modalWindow.deferred.resolve(result);
          removeModalWindow(modalInstance);
        }
      };

- openedWindows.get(modalInstance)可能找不到，因为之前可能已经关闭过弹窗了

### 状态

- 暂时没有很好的解决办法

### stackoverflow解决了这个问题，但是很麻烦

- [文章地址](https://stackoverflow.com/questions/21768778/angular-ui-bootstrap-scope-modalinstance-close-causes-cannot-read-property-v/22334609)

- [文章地址2](https://stackoverflow.com/questions/22286457/dismiss-angular-modal-on-url-change-errors-in-console)

- [代码地址](http://plnkr.co/edit/daf8dP?p=info&preview)

