---
created: 2023-11-15T20:50
updated: 2023-11-15T20:50
---
# react

## jsx

### 在 JSX 语法中，你可以在大括号内放置任何有效的 JavaScript 表达式


在下面的例子中，我们声明了一个名为 name 的变量，然后在 JSX 中使用它，并将它包裹在大括号中：

const name = 'Josh Perez';
const element = <h1>Hello, {name}</h1>;
ReactDOM.render(
  element,
  document.getElementById('root')
);

### 在编译之后，JSX 表达式会被转为普通 JavaScript 函数调用，并且对其取值后得到 JavaScript 对象。


也就是说，你可以在 if 语句和 for 循环的代码块中使用 JSX，将 JSX 赋值给变量，把 JSX 当作参数传入，以及从函数中返回 JSX：
function getGreeting(user) {
  if (user) {

    return <h1>Hello, {formatName(user)}!</h1>;  }

  return <h1>Hello, Stranger.</h1>;}

### JSX 特定属性

- 你可以通过使用引号，来将属性值指定为字符串字面量：

	- const element = <div tabIndex="0"></div>;

- 也可以使用大括号，来在属性值中插入一个 JavaScript 表达式：

	- const element = <img src={user.avatarUrl}></img>;

### 元素渲染

- react对象，描述，元素内容
- 浏览器DOM
- React元素
- 将一个元素渲染为 DOM

  
  假设你的 HTML 文件某处有一个 <div>：
  <div id="root"></div>
  
  我们将其称为“根” DOM 节点，因为该节点内的所有内容都将由 React DOM 管理。
  
  仅使用 React 构建的应用通常只有单一的根 DOM 节点。如果你在将 React 集成进一个已有应用，那么你可以在应用中包含任意多的独立根 DOM 节点。
  
  想要将一个 React 元素渲染到根 DOM 节点中，只需把它们一起传入 ReactDOM.render()：
  const element = <h1>Hello, world</h1>;
  ReactDOM.render(element, document.getElementById('root'));
  
- 更新已渲染的元素

  
  React 元素是不可变对象。一旦被创建，你就无法更改它的子元素或者属性。一个元素就像电影的单帧：它代表了某个特定时刻的 UI。
  
  根据我们已有的知识，更新 UI 唯一的方式是创建一个全新的元素，并将其传入 ReactDOM.render()。
  
- React 只更新它需要更新的部分

  React DOM 会将元素和它的子元素与它们之前的状态进行比较，并只会进行必要的更新来使 DOM 达到预期的状态。
  
### State&生命周期

- 将函数组件转换成 class 组件

  ```函数
  function Clock(props) {
    return (
  
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {props.date.toLocaleTimeString()}.</h2>
      </div>  );
  }
  
  function tick() {
    ReactDOM.render(
  
      <Clock date={new Date()} />,    document.getElementById('root')
    );
  }
  
  setInterval(tick, 1000);
  
  ```
  ## 第一步；
  ``` class
  class Clock extends React.Component {
    render() {
      return (
        <div>
          <h1>Hello, world!</h1>
          <h2>It is {this.props.date.toLocaleTimeString()}.</h2>
        </div>
      );
    }
  }
  ```
  
  ## 第二步
  
  让我们来快速概括一下发生了什么和这些方法的调用顺序：
  当 <Clock /> 被传给 ReactDOM.render()的时候，React 会调用 Clock 组件的构造函数。因为 Clock 需要显示当前的时间，所以它会用一个包含当前时间的对象来初始化 this.state。我们会在之后更新 state。
  之后 React 会调用组件的 render() 方法。这就是 React 确定该在页面上展示什么的方式。然后 React 更新 DOM 来匹配 Clock 渲染的输出。
  当 Clock 的输出被插入到 DOM 中后，React 就会调用 ComponentDidMount() 生命周期方法。在这个方法中，Clock 组件向浏览器请求设置一个计时器来每秒调用一次组件的 tick() 方法。
  浏览器每秒都会调用一次 tick() 方法。 在这方法之中，Clock 组件会通过调用 setState() 来计划进行一次 UI 更新。得益于 setState() 的调用，React 能够知道 state 已经改变了，然后会重新调用 render() 方法来确定页面上该显示什么。这一次，render() 方法中的 this.state.date 就不一样了，如此以来就会渲染输出更新过的时间。React 也会相应的更新 DOM。
  一旦 Clock 组件从 DOM 中被移除，React 就会调用 componentWillUnmount() 生命周期方法，这样计时器就停止了。
  
  
  
	- 通过以下五步将 Clock 的函数组件转成 class 组件：
	- 创建一个同名的 ES6 class，并且继承于 React.Component。
	- 添加一个空的 render() 方法。
	- 将函数体移动到 render() 方法之中。
	- 在 render() 方法中使用 this.props 替换 props。
	- 删除剩余的空函数声明。

- 向 class 组件中添加局部的 state
- 正确地使用 State

	- 不要直接修改 State
	- State 的更新可能是异步的
	- State 的更新会被合并

- [事件处理](https://www.webhek.com/post/javascript-bind.html)

	- 不同点是你不能通过返回 false 的方式阻止默认行为
	- e 是一个合成事件。React 根据 W3C 规范来定义这些合成事件，所以你不需要担心跨浏览器的兼容性问题。
	- 你必须谨慎对待 JSX 回调函数中的 this，在 JavaScript 中，class 的方法默认不会绑定 this

		- [复习一下bind，bind方法，可以提前绑定this，和参数，返回一个新的方法](https://www.webhek.com/post/javascript-bind.html)

	- 向事件处理程序传递参数

	  
	  在循环中，通常我们会为事件处理函数传递额外的参数。例如，若 id 是你要删除那一行的 ID，以下两种方式都可以向事件处理函数传递参数：
	  <button onClick={(e) => this.deleteRow(id, e)}>Delete Row</button>
	  <button onClick={this.deleteRow.bind(this, id)}>Delete Row</button>
	  
	  上述两种方式是等价的，分别通过箭头函数和 Function.prototype.bind 来实现。
	  
	  在这两种情况下，React 的事件对象 e 会被作为第二个参数传递。如果通过箭头函数的方式，事件对象必须显式的进行传递，而通过 bind 的方式，事件对象以及更多的参数将会被隐式的进行传递。
	  
- 条件渲染

	- 元素变量

		- 你可以使用变量来储存元素。 它可以帮助你有条件地渲染组件的一部分，而其他的渲染部分并不会因此而改变。
		- 声明一个变量并使用 if 语句进行条件渲染是不错的方式，但有时你可能会想使用更为简洁的语法

	- 与运算符 &&

		- 通过花括号包裹代码，你可以在 JSX 中嵌入任何表达式。这也包括 JavaScript 中的逻辑与 (&&) 运算符。它可以很方便地进行元素的条件渲染。

	- 三目运算符

		- 另一种内联条件渲染的方法是使用 JavaScript 中的三目运算符 condition ? true : false。

	- 阻止组件渲染

		- 在极少数情况下，你可能希望能隐藏组件，即使它已经被其他组件渲染。若要完成此操作，你可以让 render 方法直接返回 null，而不进行任何渲染。

- 列表&key

	- 渲染多个组件

		- 我们使用 Javascript 中的 map() 方法来遍历 numbers 数组。将数组中的每个元素变成 <li> 标签，最后我们将得到的数组赋值给 listItems

	- 基础列表组件

		- 警告 a key should be provided for list items

	- key

		- key 帮助 React 识别哪些元素改变了，比如被添加或删除。因此你应当给数组中的每一个元素赋予一个确定的标识。
		- 当元素没有确定 id 的时候，万不得已你可以使用元素索引 index 作为 key
		- 如果列表项目的顺序可能会变化，我们不建议使用索引来用作 key 值，因为这样做会导致性能变差，还可能引起组件状态的问题

	- 用 key 提取组件

		- 如果你提取出一个 ListItem 组件，你应该把 key 保留在数组中的这个 <ListItem /> 元素上，而不是放在 ListItem 组件中的 <li> 元素上。
		- 上面这句话的意思是：
应该在循环的组件上使用这个key，而不是在这个li元素上使用。

	- key 只是在兄弟节点之间必须唯一

		- key 会传递信息给 React ，但不会传递给你的组件。如果你的组件中需要使用 key 属性的值，请用其他属性名显式传递这个值

	- 在 JSX 中嵌入 map()

		- JSX 允许在大括号中嵌入任何表达式，所以我们可以内联 map() 返回的结果：
		- function NumberList(props) {
		-   const numbers = props.numbers;
		-   return (
		-     <ul>
		-       {numbers.map((number) =>
		-         <ListItem key={number.toString()}
		-                   value={number} />
		-       )}
		-     </ul>
		-   );
		- }
		- 如果一个 map() 嵌套了太多层级，那可能就是你提取组件的一个好时机。

- 表单

	- 受控组件

		- 对于受控组件来说，输入的值始终由 React 的 state 驱动
		- 由于在表单元素上设置了 value 属性，因此显示的值将始终为 this.state.value，这使得 React 的 state 成为唯一数据源。由于 handlechange 在每次按键时都会执行并更新 React 的 state，因此显示的值将随着用户输入而更新。
		- <input type="text" value={this.state.value} onChange={this.handleChange} />

	- textarea 标签
	- select 标签

		- 由于 selected 属性的缘故，椰子选项默认被选中。React 并不会使用 selected 属性，而是在根 select 标签上使用 value 属性。这在受控组件中更便捷，因为您只需要在根标签中更新它。
		-  <select value={this.state.value} onChange={this.handleChange}>
		-             <option value="grapefruit">葡萄柚</option>
		-             <option value="lime">酸橙</option>
		-             <option value="coconut">椰子</option>
		-             <option value="mango">芒果</option>
		-           </select>
		- 你可以将数组传递到 value 属性中，以支持在 select 标签中选择多个选项：
		- <select multiple={true} value={['B', 'C']}>

	- 文件 input 标签

		- 因为它的 value 只读，所以它是 React 中的一个非受控组件

	- 处理多个输入

		- 当需要处理多个 input 元素时，我们可以给每个元素添加 name 属性，并让处理函数根据 event.target.name 的值选择要执行的操作。
		- 这里使用了 ES6 计算属性名称的语法更新给定输入名称对应的 state 值：
		- 例如：
		- this.setState({
  [name]: value
});
		- var partialState = {};
partialState[name] = value;
this.setState(partialState);

	- 受控输入空值

		- 在受控组件上指定 value 的 prop 会阻止用户更改输入。如果你指定了 value，但输入仍可编辑，则可能是你意外地将value 设置为 undefined 或 null。
		- 下面的代码演示了这一点。（输入最初被锁定，但在短时间延迟后变为可编辑。）
		- ReactDOM.render(<input value="hi" />, mountNode);

setTimeout(function() {
  ReactDOM.render(<input value={null} />, mountNode);
}, 1000);

	- 受控组件的替代品

		- 使用非受控组件, 这是实现输入表单的另一种方式

	- 成熟的解决方案

		- Formik 是不错的选择。然而，它也是建立在受控组件和管理 state 的基础之上 —— 所以不要忽视学习它们

	- 状态提升

