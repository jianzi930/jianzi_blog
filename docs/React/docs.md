## React 脚手架（CLI）

- React 脚手架的介绍
- 使用 React 脚手架创建项目
- 项目目录结构调整

### React 脚手架的介绍

- 脚手架：为了保证各施工过程顺利进行而搭设的工作平台
- 对于前端项目开发来说，脚手架是为了保证前端项目开发过程顺利进行而搭设的开发平台
- 脚手架的意义：
  - 现代的前端开发日趋成熟，需要依赖于各种工具，比如，webpack、babel、eslint、sass/less/postcss等
  - 工具配置繁琐、重复，各项目之间的配置大同小异
  - 开发阶段、项目发布，配置不同
    - 项目开始前，帮你搭好架子，省去繁琐的 webpack 配置
    - 项目开发时，热更新、格式化代码、git 提交时自动校验代码格式等
    - 项目发布时，一键自动打包，包括：代码压缩、优化、按需加载等

### 使用 React 脚手架创建项目
- 命令：`npx create-react-app react-basic`
  - npx create-react-app 是固定命令，`create-react-app` 是 React 脚手架的名称
  - react-basic 表示项目名称，可以修改
- 启动项目：`yarn start` or `npm start` 
- `npx` 是 npm v5.2 版本新添加的命令，用来简化 npm 中工具包的使用
  - 原始：1 全局安装`npm i -g create-react-app` 2 在通过脚手架的命令来创建 React 项目
  - 现在：npx 调用最新的 create-react-app 直接创建 React 项目

### 项目目录结构说明和调整

- 说明：
  - `src` 目录是我们写代码进行项目开发的目录
  - 查看 `package.json` 两个核心库：`react`、`react-dom`（脚手架已经帮我们安装好，我们直接用即可）
- 调整：
  1. 删除 src 目录下的所有文件
  2. 创建 index.js 文件作为项目的入口文件，在这个文件中写 React 代码即可

## React 的基本使用

### 基本步骤

+ 使用步骤

```
- 导入react和react-dom     
- 创建react元素(虚拟DOM)
- 渲染react元素到页面中
```

+ 导入react和react-dom

```js
// 导入react和react-dom
import React from 'react'
import ReactDOM from 'react-dom'
```

+ 创建react元素

```js
// 创建元素
const title = React.createElement('h1', {id: 'title', className: 'title'}, 'hello react')
```

+ 渲染react元素到页面

```js
// 渲染react元素
ReactDOM.render(title, document.getElementById('root'))
```

# JSX

## JSX的基本使用

### createElement的问题

- 繁琐不简洁
- 不直观，无法一眼看出所描述的结构
- 不优雅，开发体验不好

### JSX简介 

`JSX`是`JavaScript XML`的简写，表示了在Javascript代码中写XML(HTML)格式的代码

优势：声明式语法更加直观，与HTML结构相同，降低学习成本，提高开发效率。

 **JSX是react的核心内容**

注意：*JSX 不是标准的 JS 语法，是 JS 的语法扩展。脚手架中内置的 [@babel/plugin-transform-react-jsx](@babel/plugin-transform-react-jsx) 包，用来解析该语法。*

### 使用步骤

```
- 导入react和reactDOM包
- 使用jsx语法创建react元素
- 把react元素渲染到页面中
```

+ 导入react和reactDOM

```js
// 导入react和react-dom
import React from 'react'
import ReactDOM from 'react-dom'
```

+ 创建react元素

```js
// 创建元素
const title = <h1 title="哈哈"></h1>
```

+ 渲染元素

```js
// 渲染元素
ReactDOM.render(title, document.getElementById('root'))
```

### JSX注意点

+ 只有在脚手架中才能使用jsx语法
  + 因为JSX需要经过babel的编译处理，才能在浏览器中使用。脚手架中已经默认有了这个配置。
+ JSX必须要有一个根节点，使用 `<></>`  或 `<React.Fragment></React.Fragment>` 可以不显示根节点
+ 没有子节点的元素可以使用`/>`结束

+ JSX中语法更接近与JavaScript
  + `class` =====> `className`
  + `for`========>  `htmlFor`
+ JSX可以换行，如果JSX有多行，<font color='red'>推荐使用`()`包裹JSX，防止自动插入分号的bug</font>

## 使用prettier插件格式化react代码

+ 安装插件
+ 添加prettier的配置

```js
// 保存到额时候用使用prettier进行格式化
"editor.formatOnSave": true,
// 不要有分号
"prettier.semi": false,
// 使用单引号
"prettier.singleQuote": true,
// 默认使用prittier作为格式化工具
"editor.defaultFormatter": "esbenp.prettier-vscode",
```

## JSX中嵌入JavaScript表达式

> 在jsx中可以在`{}`来使用js表达式

+ 基本使用

```js
const name = 'zs'
const age = 18
const title = (
  <h1>
    姓名：{name}, 年龄：{age}
  </h1>
)
```

+ 可以访问对象的属性

```js
const car = {
    brand: '玛莎拉蒂'
}
const title = (
  <h1>
    汽车：{car.brand}
  </h1>
)
```

+ 可以访问数组的下标

```js
const friends = ['张三', '李四']
const title = (
  <h1>
    汽车：{friends[1]}
  </h1>
)
```

+ 可以使用三元运算符

```js
const gender = 18
const title = (
  <h1>
    性别：{age >= 18? '是':'否'}
  </h1>
)
```

+ 可以调用方法

```js
function sayHi() {
  return '你好'
}
const title = <h1>姓名：{sayHi()}</h1>
```

+ JSX本身

```js
const span = <span>我是一个span</span>
const title = <h1>盒子{span}</h1>
```

+ JSX中的注释

```js
{/* 这是jsx中的注释 */}   推荐快键键 ctrl + /
```

+ 不要出现语句，比如`if` `for`

## 条件渲染

> 在react中，一切都是javascript，所以条件渲染完全是通过js来控制的

+ 通过判断`if/else`控制 

```js
const isLoding = false
const loadData = () => {
  if (isLoding) {
    return <div>数据加载中.....</div>
  } else {
    return <div>数据加载完成，此处显示加载后的数据</div>
  }
}

const title = <div>条件渲染：{loadData()}</div>
```

+ 通过三元运算符控制

```js
const isLoding = false
const loadData = () => {
  return isLoding ? (
    <div>数据加载中.....</div>
  ) : (
    <div>数据加载完成，此处显示加载后的数据</div>
  )
}
```

+ 逻辑运算符

```js
const isLoding = false
const loadData = () => {
  return isLoding && <div>加载中...</div>
}

const title = <div>条件渲染：{loadData()}</div> // jsx，里面的js要加花括号
const title = loadData() // js，不用加花括号
```

## vscode配置自动补全

```js
// 当按tab键的时候，会自动补全
"emmet.triggerExpansionOnTab": true,
// 输入时联想提示
"emmet.showAbbreviationSuggestions": true,
// jsx的提示
"emmet.includeLanguages": {
  "javascript": "javascriptreact"
}
```

## 列表渲染

> 我们经常需要遍历一个数组来重复渲染一段结构
>
> 在react中，通过map方法进行列表的渲染

+ 列表的渲染 

```js
const songs = ['温柔', '倔强', '私奔到月球']

const list = songs.map(song => <li>{song}</li>)

const dv = (
  <div>
    <ul>{list}</ul>
  </div>
)
```

+ 直接在JSX中渲染

```js
const songs = ['温柔', '倔强', '私奔到月球']

const dv = (
  <div>
    <ul>{songs.map(song => <li>{song}</li>)}</ul>
  </div>
)
```

+ key属性的使用

```js
const dv = (
  <div>
    <ul>
      {songs.map(song => (
        <li key={song}>{song}</li>
      ))}
    </ul>
  </div>
)
```

**注意：列表渲染时应该给重复渲染的元素添加key属性，key属性的值要保证唯一**

**注意：key值避免使用index下标，因为下标会发生改变**

## 样式处理

动态的控制样式

### 行内样式-style

```js
const color = 'red'
const dv = (
  <div style={{ color, backgroundColor: 'pink' }}>style样式</div>
)
```

### 类名-className

```js
// 导入样式
import './base.css'
const isRed = true
const dv1 = <div className="title">style样式</div> // 静态
const dv2 = <div className={isRed ? 'title' : ''}>style样式</div> // 动态
const dv2 = <div className={`${isRed ? 'title' : ''} head`}>style样式</div> // 动态
```

base.css样式文件

```css
.title {
  text-align: center;
  color: red;
  background-color: pink;
}
.head {
    color: green;
}
```

### className库

```js
// 原理
import './base.css'
const isRed = true
function className(obj) {
    return Object.keys.filter(item => item[key]).join(' ')
}
const dv2 = <div className={className({head: true, title: isRed})}>style样式</div>
```

安装 `npm i classnames`
使用
```js
import classnames fom 'classnames'
const dv2 = <div className={classnames('head', {title: isRed})}>style样式</div>
```

# React创建组件的两种方式

## 函数组件

> 函数组件：使用JS的函数或者箭头函数创建的组件

+ 为了区分普通标签，函数组件的名称必须`大写字母开头`
+ 函数组件`必须有返回值`，表示该组件的结构
+ 如果返回值为null，表示不渲染任何内容

使用函数创建组件

```js
function Hello (props) {
    const sayhai = () => {
        console.log('hi')
    }
    return (
    	<div onClick={sayhai}>这是我的函数组件{props.name}</div>
    )
}
```

使用箭头函数创建组件

```js
const Hello = props => <div>这是一个函数组件{props.name}</div>
```

使用组件

```js
ReactDOM.render(<Hello />, document.getElementById('root'))
```

## 类与继承

### class 基本语法 

- 在 ES6 之前通过构造函数创建对象
- 在 ES6 中新增了一个关键字 class, 类 和构造函数类似，用于创建对象
- 类创建对象的基本语法
  - 基本语法`class 类名{}`
  - 构造函数`constructor`的用法，创建对象
  - 在类中提供方法，直接提供即可
  - 在类中不需要使用,分隔

```js
// 构造函数创建
function Person(name, age) {
	this.name = name
	this.age = age
}
Person.prototype.sayHi = function() {
    console.log(this.name)
}
var person1 = new Person('tom', 13)
person.sayHi()
```

```js
// 类创建
class Person {
    constructor() {
        this.name = name
		this.age = age
    }
    sayHi() {
        console.log(this.name)
    }
}
var person1 = new Person('tom', 13)
person.sayHi()
```

### extends 实现继承

- extends 基本使用
- 类可以使用它继承的类中所有的成员（属性和方法）
- 类中可以提供自己的属性和方法
- 注意：如果想要给类中新增属性，必须先调用 super 方法，相当于调用父类的构造函数，把属性挂在父类上

```js
class Person {
    constructor() {
        this.name = name
		this.age = age
    }
    sayHi() {
        console.log(this.name)
    }
}
// 只继承
class Chinese extends Person {}
// 相当于
class Chinese extends Person {
    constructor(name, age) {
        super(name, age)
    }
}
// 扩展
class Chinese extends Person {
    constructor(name, age) {
        super(name, age)
        this.skin = 'yellow'
    }
    pingpang() {
        console.log('打乒乓球')
    }
}
class Japanese extends Person {
    constructor(name, age) {
        super(name, age)
        this.language = 'japanese'
    }
}
```

## 类组件

> 类组件：使用ES6的class语法创建组件

约定1：类组件的名称必须是大写字母开头

约定2：类组件应该继承`React.Component`父类，从而可以使用父类中提供的方法或者属性

约定3：类组件必须提供`render`方法

约定4：render方法`必须有返回值`,表示该组件的结构

定义组件

```js
class Hello extends React.Component {
  render() {
    return <div>这是一个类组件</div>
  }
}

```

使用组件

```js
ReactDOM.render(<Hello />, document.getElementById('root'))
```

## 将组件提取到单独的js文件中

实现方式

1. 创建Hello.js
2. 在 Hello.js 中导入React
3. 创建组件（函数 或 类）
4. 在 Hello.js 中导出该组件
5. 在 index.js 中导入 Hello 组件
6. 渲染组件

## 有状态组件和无状态组件

+ 函数组件又叫做**无状态组件**   函数组件是不能自己提供数据的(在hooks出现之前)
+ 类组件又叫做**有状态组件  智能组件** 类组件可以自己提供数据，组件内部的状态（数据如果发生了改变，内容会自动的更新）
+ 状态（state）即组件的私有数据，当组件的状态发生了改变，页面结构也就发生了改变。
+ 函数组件是没有状态的，只负责页面的展示（静态，不会发生变化）性能比较高
+ 类组件有自己的状态，负责**更新UI**，只要类组件的数据发生了改变，UI就会发生更新。
+ 在复杂的项目中，一般都是由函数组件和类组件共同配合来完成的。

比如计数器案例，点击按钮让数值+1， 0和1就是不同时刻的状态，当状态从0变成1之后，UI也要跟着发生变化。React想要实现这种功能，就需要使用有状态组件来完成。

## 类组件的状态

+ 状态`state`即数据，是组件内部的`私有数据`,只有在组件内部可以使用
+ `state的值是一个对象`,表示一个组件中可以有多个数据
+ state的基本使用

```js
class Hello extends React.Component {
  constructor() {
    super()
    // 组件通过state提供数据
    this.state = {
      msg: 'hello react'
    }
  }
  render() {
    return <div>state中的数据--{this.state.msg}</div>
  }
}
```

+ 简洁的语法（class本身支持这种写法，与react无关）

```js
class Hello extends React.Component {
  state = {
    msg: 'hello react'
  }
  render() {
    return <div>state中的数据--{this.state.msg}</div>
  }
}
```

## react插件的安装

安装谷歌插件`react-devtools`

# 事件处理

## 注册事件

React注册事件与DOM的事件语法非常像

语法`on+事件名=｛事件处理程序｝` 比如`onClick={this.handleClick}`

注意：**React事件采用驼峰命名法**，比如`onMouseEnter`, `onClick`

```js
class App extends React.Component {
  render() {
    return (
      <div>
        <button onClick={this.handleClick}>点我</button>
      </div>
    )
  }

  handleClick() {
    console.log('点击事件触发了')
  }
}
```

## 事件对象

+ 可以通过事件处理程序的参数获取到事件对象

+ React 中的事件对象叫做：合成事件（对象）
+ 合成事件：兼容所有浏览器，无需担心跨浏览器兼容性问题

```js
function handleClick(e) {
    e.preventDefault()
    console.log('事件对象', e)
}
<a onClick={this.handleClick}>点我，不会跳转页面</a>
```

## this指向问题

> 事件处理程序中的this指向的是undefined
>
> render方法中的this指向的而是当前react组件。**只有事件处理程序中的this有问题**

render方法是由实例调用的，即

```js
var instance = new App()
instance.render()
```

render方法是在App.prototype上的，所以实例能访问到

```js
class App extends React.Component {
  state = {
    msg: 'hello react'
  }
  handleClick() {
    console.log(this.state.msg)
  }
  render() {
    this.handleClick() // 这里调用不会有问题，因为this为实例
    var fn = this.handleClick
    fn() // 这里有问题，在严格模式下为undefined, 非严格模式为window
    return (
      <div>
        <button onClick={this.handleClick}>点我</button>
      </div>
    )
  }
}
```

## this指向问题解决方案

```js
方案1：箭头函数
方案2：bind修改this指向
方案3：类实例方法
```

+ 在render中使用箭头函数

箭头函数的特点：自身没有this，访问的是外部的this

方式1：

```js
class App extends React.Component {
  state = {
    msg: 'hello react'
  }
  render() {
    return (
      <div>
        <button onClick={() => { console.log(this.state.msg) }>点我</button>
      </div>
    )
  }
}
```

缺点：会把大量的js处理逻辑放到JSX中，将来不容易维护

方式2

```js
class App extends React.Component {
  state = {
    msg: 'hello react'
  }
  handleClick() {
    console.log(this.state.msg)
  }
  render() {
    return (
      <div>
        <button onClick={() => {this.handleClick()}}>点我</button>
      </div>
    )
  }
}
```

缺点：把大量的js逻辑写在了JSX结构中，不好维护

+ 解决方案2：使用bind

```js
class App extends React.Component {
  state = {
    msg: 'hello react'
  }
  handleClick() {
    console.log(this.state.msg)
  }
  render() {
    return (
      <div>
        <button onClick={this.handleClick.bind(this)}>点我</button>
      </div>
    )
  }
}
```

或者

```js
class App extends React.Component {
  constructor() {
  	super()
    this.handleClick = this.handleClick.bind(this)
  }
  state = {
    msg: 'hello react'
  }
  handleClick() {
    console.log(this.state.msg)
  }
  render() {
    return (
      <div>
        <button onClick={this.handleClick}>点我</button>
      </div>
    )
  }
}
```

+ 解决方案3：class实例方法

  相当于实例属性，而不是挂在原型对象上

```js
class App extends React.Component {
  state = {
    msg: 'hello react'
  }

  handleClick = () => {
    console.log(this.state.msg)
  }
  render() {
    return (
      <div>
        <button onClick={this.handleClick}>点我</button>
      </div>
    )
  }
}
```

**注意：这个语法是试验性的语法，但是有babel的转义，所以没有任何问题**

# setState修改状态

## 基础使用

+ 组件中的状态是可变的
+ 语法`this.setState({要修改的数据})`
+ 注意：不要直接修改state中的值，必须通过`this.setState()`方法进行修改
+ `setState`的作用
  + 修改state
  + 更新UI

+ 思想：数据驱动视图

```js
class App extends React.Component {
  state = {
    count: 1,
    obj: {
        name: 'tom',
        age: 12
    }
  }
  handleClick() {
    // 直接调用this.state.count++ 也可以修改count的值，但是不能更新ui
    this.setState({
      count: this.state.count + 1
      obj: {
        ...this.state.obj,
        name: 'mary'
      } // 修改obj中的name
    })
  }
  render() {
    return (
      <div>
        <p>次数: {this.state.count}</p>
        <button onClick={this.handleClick.bind(this)}>点我+1</button>
      </div>
    )
  }
}
```

## 扩展

+ setState() 是异步更新数据的，等同步代码执行后再去队列中执行
+ 注意：使用该语法时，后面的 setState() 不要依赖于前面的 setState()
```js
1. 当你调用 setState 的时候，React.js 并不会马上修改 state （为什么）
2. 而是把这个对象放到一个更新队列里面
3. 稍后才会从队列当中把新的状态提取出来合并到 state 当中，然后再触发组件更新。
```

+ 可以多次调用 setState() ，只会触发一次重新渲染
```js
this.state = { count: 1 }
this.setState({
	count: this.state.count + 1
})
this.setState({
	count: this.state.count + 1
})
this.setState({
	count: this.state.count + 2
})
console.log(this.state.count) // 2，合并异步队列的对象，即后面的会覆盖前面的，所以只执行+2这一个
```
在使用 React.js 的时候，并不需要担心多次进行 `setState` 会带来性能问题。

### 推荐语法

+  推荐：使用 `setState((preState) => {})` 语法

+  参数preState: React.js 会把上一个 `setState` 的结果传入这个函数
```js
this.setState((preState) => {
    return {
    	count: preState.count + 1
    }
})
console.log(this.state.count) // 1
```
**这种语法依旧是异步的，但是state可以获取到最新的状态，适用于需要调用多次setState**

### 第二个参数

+ 场景：在状态更新（页面完成重新渲染）后立即执行某个操作
+ 语法：`setState(updater[, callback])`
```js
this.setState(
	(state) => ({}),
	() => {console.log('这个回调函数会在状态更新后立即执行')}
)
this.setState(
	(state, props) => {},
	() => {
		document.title = '更新state后的标题：' + this.state.count
	}
)
```
# 表单处理

> 我们在开发过程中，经常需要操作表单元素，比如获取表单的值或者是设置表单的值。

react中处理表单元素有两种方式：

+ 受控组件
+ 非受控组件（DOM操作）

## 受控组件基本概念

+ HTML中表单元素是可输入的，即表单用户维护着自己的可变状态（value）。

+ 但是在react中，可变状态通常是保存在state中的，并且要求状态只能通过`setState`进行修改。

+ React中将state中的数据与表单元素的value值绑定到了一起，`由state的值来控制表单元素的值`
+ 受控组件：**value值受到了react控制的表单元素** 


## 受控组件使用步骤

1. 在state中添加一个状态，作为表单元素的value值（控制表单元素的值）
2. 给表单元素添加change事件，设置state的值为表单元素的值（控制值的变化）

```js
class App extends React.Component {
  state = {
    msg: 'hello react'
  }

  handleChange = (e) => {
    this.setState({
      msg: e.target.value
    })
  }

  render() {
    return (
      <div>
        <input type="text" value={this.state.msg} onChange={this.handleChange}/>
      </div>
    )
  }
}
```

## 常见的受控组件

+ 文本框、文本域、下拉框（操作value属性）
+ 复选框（操作checked属性）

```js
class App extends React.Component {
  state = {
    usernmae: '',
    desc: '',
    city: "2",
    isSingle: true
  }
 
  handleName = e => {
    this.setState({
      name: e.target.value
    })
  }
  handleDesc = e => {
    this.setState({
      desc: e.target.value
    })
  }
  handleCity = e => {
    this.setState({
      city: e.target.value
    })
  }
  handleSingle = e => {
    this.setState({
      isSingle: e.target.checked
    })
  }

  render() {
    return (
      <div>
        姓名：<input type="text" value={this.state.username} onChange={this.handleName}/>
        <br/>
        描述：<textarea value={this.state.desc} onChange={this.handleDesc}></textarea>
        <br/>
        城市：<select value={this.state.city} onChange={this.handleCity}>
          <option value="1">北京</option>
          <option value="2">上海</option>
          <option value="3">广州</option>
          <option value="4">深圳</option>
        </select>
        <br/>
        是否单身：<input type="checkbox" checked={this.state.isSingle} onChange={this.handleSingle}/>
      </div>
    )
  }
}
```

## 多表单元素的优化

问题：每个表单元素都需要一个单独的事件处理程序，处理太繁琐

优化：使用一个事件处理程序处理多个表单元素

步骤

 + 给表单元素添加name属性，名称与state属性名相同
 + 根据表单元素类型获取对应的值
 + 在事件处理程序中通过`[name]`修改对应的state

```js
class App extends React.Component {
  state = {
    username: '',
    desc: '',
    city: "2",
    isSingle: true
  }
 
  handleChange = e => {
    let {name, type, value, checked} = e.target
    console.log(name, type, value, checked)
    value = type === 'checkbox' ? checked : value
    console.log(name, value)
    this.setState({
      [name]: value
    })
  }
  render() {
    return (
      <div>
        姓名：<input type="text" name="username" value={this.state.username} onChange={this.handleChange}/>
        <br/>
        描述：<textarea name="desc" value={this.state.desc} onChange={this.handleChange}></textarea>
        <br/>
        城市：<select name="city" value={this.state.city} onChange={this.handleChange}>
          <option value="1">北京</option>
          <option value="2">上海</option>
          <option value="3">广州</option>
          <option value="4">深圳</option>
        </select>
        <br/>
        是否单身：<input type="checkbox" name="isSingle" checked={this.state.isSingle} onChange={this.handleChange}/>
      </div>
    )
  }
}
```

## 非受控组件

> 非受控组件借助于ref，使用原生DOM的方式来获取表单元素的值

使用步骤

+ 调用`React.createRef()`方法创建一个ref

```js
constructor() {
  super()
  this.txtRef = React.createRef()
}
```

+ 将创建好的ref对象添加到文本框中

```js
<input type="text" ref={this.txtRef}/>
```

+ 通过ref对象获取文本框的值

```js
handleClick = () => {
  console.log(this.txtRef.current.value)
}
```

非受控组件用的不多，推荐使用受控组件

# 综合案例

评论列表案例

## 列表展示功能

渲染评论列表（列表渲染）/ 暂无评论

+ 在state中初始化评论列表数据

+ 使用数组的map方法遍历列表数据

+ 给每个li添加key属性

  ```js
  <div>
  {this.renderList()}
  </div>
  
  this.renderList = () => {
  	if(this.state.list.length < 0) {
  		return <div>暂无评论</div>
  	}
      return (
      	<ul>
          	{
                  this.state.list.map(item => {
                      <li key={item.id}>{item.name}</li>
                  })
              }
          </ul>
      )
  }
  ```

## 发表评论功能

获取评论信息，评论人和评论内容（受控组件）

+ 使用受控组件的方式获取评论数据

发表评论，更新评论列表（更新状态）

 + 给comments增加一条数据

边界处理

 + 清空内容
 + 判断非空

## 清空评论功能

+ 给清空评论按钮注册事件
+ 清空评论列表
+ 没有更多评论的处理

```js
<button onClick={this.clear}>清空</button>

this.clear = () => {
    this.setState({list: []})
}
```

## 删除评论

```js
<button onClick={() => this.del(id)}>删除</button>

this.del = (id) => {
    this.setState({list: this.state.list.filter(item => item.id !== id)})
}
```

# 组件通讯

**组件**是独立且封闭的单元，默认情况下，只能使用组件自己的数据。在组件化过程中，我们将一个完整的功能
拆分成多个组件，以更好的完成整个应用的功能。而在这个过程中，多个组件之间不可避免的要共享某些数据
。为了实现这些功能，就需要打破组件的独立封闭性，让其与外界沟通。这个过程就是**组件通讯**。

## props

+ 组件是封闭的，要接收外部数据应该通过props来实现
+ **props的作用：接收传递给组件的数据**
+ 传递数据：给组件标签添加属性
+ 接收数据：函数组件通过参数props接收数据，类组件通过this.props接收数据

### 函数组件通讯

子组件

```js
function Hello(props) {
    console.log(props)
    return (
    	<div>接收到数据：{props.name}</div>
    )
}
```

父组件

```js
<Hello name="jack" age={19} />
```

### 类组件通讯

子组件

```js
class Hello extends React.Component {
    render() {
        return (
        	<div>接收到的数据：{this.props.age}</div>
        )
    }
}
```

父组件

```js
<Hello name="jack" age={19} />
```

### props的特点

+ 可以给组件传递任意类型的数据

  包括字符串，数组，对象，函数，jsx结构

  <img src="C:\Users\13650\AppData\Roaming\Typora\typora-user-images\image-20220227155039298.png" alt="image-20220227155039298" style="zoom:50%;" />

+ props是只读的，不允许修改props的数据

+ 注意：在类组件中需要依赖props使用的时候，**需要把 props传递给super()**，否则构造函数无法获取到props

  ```js
  // constructor里面默认是访问不到props属性的,这是class定义构造函数在继承时特性
  class Hello extends React.Component {
      constructor() {
          console.log(this.props) // undefined
      }
      render() {
      	return <div>接收到的数据：{this.props.age}</div>
      }
  }
  ```

  ```js
  // 所以要调用super来进行访问
  class Hello extends React.Component {
      constructor(props) {
          // 推荐将props传递给父类构造函数
          super(props)
          this.state = {
              age: this.props.age + 10 // 接受并在props基础上修改
          }
      }
      render() {
      	return (
          	<div>接收到的props数据：{this.props.age}</div>
  			<div>自己的state数据：{this.state.age}</div>
          )
      }
  }
  ```

## 组件通讯三种方式

+ 父传子
+ 子传父
+ 非父子

### 父传子

1. 父组件提供要传递的state数据
2. 给子组件标签添加属性，值为 state 中的数据
3. 子组件中通过 props 接收父组件中传递的数据

父组件提供数据并且传递给子组件

```js
class Parent extends React.Component {
    state = { lastName: '王' }
    render() {
        return (
            <div>
                传递数据给子组件：<Child name={this.state.lastName} />
            </div>
        )
    }
}
```

子组件接收数据

```js
function Child(props) {
	return <div>子组件接收到数据：{props.name}</div>
}
```

```
<div {...this.props}></div> // 把父组件传过来的属性都传给子组件
```

### 子传父

思路：利用回调函数，父组件提供回调，子组件调用，将要传递的数据作为回调函数的参数。

1. 父组件提供一个回调函数（用于接收数据）
2. 将该函数作为属性的值，传递给子组件
3. 子组件通过 props 调用回调函数
4. 将子组件的数据作为参数传递给回调函数

父组件提供函数并且传递给字符串

```js
class Parent extends React.Component {
    getChildMsg = (msg) => {
        console.log('接收到子组件数据', msg)
    }
    render() {
        return (
            <div>
            	子组件：<Child getMsg={this.getChildMsg} />
            </div>
        )
    }
}
```

子组件接收函数并且调用

```js
class Child extends React.Component {
    state = { childMsg: 'React' }
    handleClick = () => {
    	this.props.getMsg(this.state.childMsg)
    }
    return (
    	<button onClick={this.handleClick}>点我，给父组件传递数据</button>
    )
}
```

**注意：回调函数中 this 指向问题！**

### todoMVC案例

修改任务状态：不能直接修改原数据

<img src="C:\Users\13650\AppData\Roaming\Typora\typora-user-images\image-20220228154911221.png" alt="image-20220228154911221" style="zoom:50%;" />

双击显示输入框：通过editing类控制显示输入框或文本，currentId控制要修改的任务id

<img src="C:\Users\13650\AppData\Roaming\Typora\typora-user-images\image-20220228160317725.png" alt="image-20220228160317725" style="zoom:50%;" />

修改任务：currentName控制当前输入框的内容，防止在按下enter键之前修改了原来的值

<img src="C:\Users\13650\AppData\Roaming\Typora\typora-user-images\image-20220228160622151.png" alt="image-20220228160622151" style="zoom:50%;" />

<img src="C:\Users\13650\AppData\Roaming\Typora\typora-user-images\image-20220228160812001.png" alt="image-20220228160812001" style="zoom:50%;" />

取消或添加：

<img src="C:\Users\13650\AppData\Roaming\Typora\typora-user-images\image-20220228161441356.png" alt="image-20220228161441356" style="zoom:50%;" />

### 兄弟组件

+ 将共享状态提升到最近的公共父组件中，由公共父组件管理这个状态
+ 思想：**状态提升**
+ 公共父组件职责：
  + 提供共享状态 
  + 提供操作共享状态的方法
+ 要通讯的子组件只需通过 props 接收状态或操作状态的方法

## 组件通讯-context 

### 基本概念

思考：App 组件要传递数据给 Child 组件，该如何处理？

处理方式：使用 props 一层层组件往下传递（繁琐）

更好的姿势：使用 Context

 作用：跨组件传递数据（比如：主题、语言等）

### 实现思路

+ 调用 React. createContext() 创建 Provider（提供数据） 和 Consumer（消费数据） 两个组件。

```js
expoet const context = React.createContext()
```

+ 使用 Provider 组件作为父节点。
+ 设置 value 属性，表示要传递的数据。

```js
state = {
    color: 'pink'
}
changeColor = (color) => {
    this.setState({
        color
    }) 
}
<context.Provider value={color: this.state.color, changeColor}>
    <div className="App">
    	<Child1 />
    </div>
</context.Provider>
```

+ 调用 Consumer 组件接收数据，Consumer里面的内容必须是一个函数，函数的参数为Provider提供的数据

```js
import context from 'xxxx'
<context.Consumer>
	{{color, changeColor} => (
     	<span>颜色是{color}</span>
     	<button onClick={() => changeColor('red')}>修改</button>
     )}
</context.Consumer>
```

总结：

1. 如果两个组件是远方亲戚（比如，嵌套多层）可以使用Context实现组件通讯
2. Context提供了两个组件：Provider 和 Consumer
3. Provider组件：用来提供数据
4. Consumer组件：用来消费数据

# props深入

## children属性

children属性：表示该组件的子节点，只要该组件有子节点，该组件的props就有该属性

children 属性与普通的props一样，值可以是任意值（文本、React元素、组件，甚至是函数）

```js
function Hello(props) {
  return (
    <div>
      该组件的子节点：{props.children}
      这是{props.title('题目')} // 相当于vue中的作用域插槽，父组件可以使用子组件
    </div>
  )
}

<Hello title={(data) => <div>这是{data}</div>}>我是子节点</Hello>

```

## props校验

目的：校验接收的props的数据类型，增加组件的健壮性

对于组件来说，props是外来的，无法保证组件使用者传入什么格式的数据

如果传入的数据格式不对，可能会导致组件内部报错。**组件的使用者不能很明确的知道错误的原因。**

props校验允许在创建组件的时候，就约定props的格式、类型等

### 使用步骤

2. 导入 prop-types 包
3. 使用组件名.propTypes = {} 来给组件的props添加校验规则
4. 校验规则通过 PropTypes 对象来指定

```js
import PropTypes from 'prop-types'
function App(props) {
    return (
    	<h1>Hi, {props.colors}</h1>
    )
}
App.propTypes = {
    // 约定colors属性为array类型
    // 如果类型不对，则报出明确错误，便于分析错误原因
    colors: PropTypes.array
}
```

### 约束规则

1. 常见类型：array、bool、func、number、object、string
2. React元素类型：element
3. 必填项：isRequired
4. 特定结构的对象：shape({})

```js
// 常见类型
optionalFunc: PropTypes.func,
// 必选
requiredFunc: PropTypes.func.isRequired,
// 特定结构的对象
optionalObjectWithShape: PropTypes.shape({
	color: PropTypes.string,
	fontSize: PropTypes.number
})
```

## props默认值

场景：分页组件  每页显示条数
作用：给 props 设置默认值，在未传入 props 时生效

```js
function App(props) {
    return (
        <div>
            此处展示props的默认值：{props.pageSize}
        </div>
    )
}
// 设置默认值
App.defaultProps = {
	pageSize: 10
}
// 不传入pageSize属性
<App />
```

## 类的静态属性static

+ 实例成员: 通过实例调用的属性或者方法，，，叫做实例成员（属性或者方法）

+ 静态成员：通过类或者构造函数本身才能访问的属性或者方法

```js
class Person {
   name = 'zs',
   static age = 18
   sayHi() {
       console.log('哈哈')
   }
   static goodBye() {
       console.log('byebye')
   }
}

const p = new Person()

console.log(p.name)
p.sayHi()

console.log(Person.age)
Person.goodBye()
```

# 组件的生命周期

## 概述

+  意义：组件的生命周期有助于理解组件的运行方式、完成更复杂的组件功能、分析组件错误原因等
+  组件的生命周期：组件从被创建到挂载到页面中运行，再到组件不用时卸载的过程
+  钩子函数的作用：为开发人员在不同阶段操作组件提供了时机。
+  **只有 类组件 才有生命周期。**

## 生命周期的整体说明

+ 每个阶段的执行时机

+ 每个阶段钩子函数的执行顺序

+ 每个阶段钩子函数的作用

  <img src="C:\Users\13650\AppData\Roaming\Typora\typora-user-images\image-20220305143438718.png" alt="image-20220305143438718" style="zoom:50%;" />

## 挂载阶段

执行时机：组件创建时（页面加载时）

执行顺序：

| 钩子 函数         | 触发时机                  | 作用                                     |
| ----------------- | ------------------------- | ---------------------------------------- |
| constructor       | 创建组件时，最先执行      | 1. 初始化state  2. 创建Ref等             |
| render            | 每次组件渲染都会触发      | 渲染UI（**注意： 不能调用setState()** ） |
| componentDidMount | 组件挂载（完成DOM渲染）后 | 1. 发送网络请求   2.DOM操作              |

## 更新阶段

+ 执行时机：1. setState() 2. forceUpdate() 3. 组件接收到新的props
+ 说明：以上三者任意一种变化，组件就会重新渲染
+ `shouldComponentUpdate(nextProps, nextState)`
  + 作用：通过返回值决定该组件是否重新渲染，返回 true 表示重新渲染，false 表示不重新渲染
  + 触发时机：更新阶段的钩子函数，组件重新渲染前执行 （shouldComponentUpdate => render）

```js
shouldComponentUpdate(nextProps) {
    // this.props是props还没改变，nextProps是props将要改变后的值
    if(this.props.count === nextProps) return false
    return true
}
render() {…}
```

 案例：随机数

| 钩子函数              | 触发时机                  | 作用                                                 |
| --------------------- | ------------------------- | ---------------------------------------------------- |
| shouldComponentUpdate | 更新数据重新渲染前        | 根据条件决定是否重新渲染                             |
| render                | 每次组件渲染都会触发      | 渲染UI（与 挂载阶段 是同一个render）                 |
| componentDidUpdate    | 组件更新（完成DOM渲染）后 | DOM操作，可以获取到更新后的DOM内容，不要调用setState |

## 卸载阶段

+ 执行时机：组件从页面中消失

| 钩子函数             | 触发时机                 | 作用                               |
| :------------------- | ------------------------ | ---------------------------------- |
| componentWillUnmount | 组件卸载（从页面中消失） | 执行清理工作（比如：清理定时器等） |

```
constructor() {
	super()
	this.timer = setTimeout(() => console.log(1), 1000)
}
componentWillUnmount() {
	clearTimeout(this.timer)
}
```

# 组件性能优化

## 组件更新机制

+ setState() 的两个作用： 1. 修改 state 2. 更新组件（UI）

+ 过程：父组件重新渲染时，也会重新渲染子组件。但只会渲染当前组件子树（当前组件及其所有子组件）

  <img src="C:\Users\13650\AppData\Roaming\Typora\typora-user-images\image-20220304180924039.png" alt="image-20220304180924039" style="zoom:50%;" />

##  减轻state

+ 减轻 state：只存储跟组件渲染相关的数据（比如：count / 列表数据 / loading 等）
+ 注意：不用做渲染的数据不要放在 state 中，比如定时器 id等 
+ 对于这种需要在多个方法中用到的数据，应该直接放在 this 中 
  + this.xxx = 'bbb'
  + this.xxx

```js
class Hello extends Component {
    componentDidMount() {
        // timerId存储到this中，而不是state中
        this.timerId = setInterval(() => {}, 2000)
    }
    componentWillUnmount() {
    	clearInterval(this.timerId)
    }
    render() { … }
}
```
vue中不要把和渲染无关的数据放到data中

## 避免不必要的重新渲染

+  组件更新机制：父组件更新会引起子组件也被更新，这种思路很清晰
+  问题：子组件没有任何变化时也会重新渲染 （接收到的props没有发生任何的改变）
+  如何避免不必要的重新渲染呢？
+  解决方式：使用钩子函数 `shouldComponentUpdate(nextProps, nextState)`

+  作用：通过返回值决定该组件是否重新渲染，返回 true 表示重新渲染，false 表示不重新渲染
+  触发时机：更新阶段的钩子函数，组件重新渲染前执行 （shouldComponentUpdate => render）
```js
class Hello extends Component {
    shouldComponentUpdate() {
        // this.props是props还没改变，nextProps是props将要改变后的值
        if(this.props.count === nextProps) return false
        return true
    }
    render() {…}
}
```
## 纯组件

+ 纯组件：`React.PureComponent` 与 `React.Component `功能相似
+ 区别：PureComponent 内部自动实现了 shouldComponentUpdate 钩子，不需要手动比较
+ 原理：纯组件内部通过分别 对比 前后两次 props 和 state 的值，来决定是否重新渲染组件
```js
class Hello extends React.PureComponent {
    render() {
        return (
        	<div>纯组件</div>
        )
    }
}
```
**只有在性能优化的时候可能会用到纯组件，不要所有的组件都使用纯组件，因为纯组件需要消耗性能进行对比**

## 纯组件比较-值类型

+ 说明：纯组件内部的对比是 shallow compare（浅层对比）

+ 对于值类型来说：比较两个值是否相同（直接赋值即可，没有坑）

```js
let number = 0
let newNumber = number
newNumber = 2
console.log(number === newNumber) // false
```
```js
state = { number: 0 }
setState({
  number: Math.floor(Math.random() * 3)
})
// PureComponent内部对比：
最新的state.number === 上一次的state.number // false，重新渲染组件
```
## 纯组件比较-引用类型

+ 说明：纯组件内部的对比是 shallow compare（浅层对比）
+ 对于引用类型来说：只比较对象的引用（地址）是否相同

```js
state = { obj: { number: 0 } }
// 直接修改原数据，地址相同，不会重新渲染（不要直接修改数据在react）
state.obj.number = 2
setState({ obj: state.obj })
// PureComponent内部比较：
最新的state.obj === 上一次的state.obj // true，不重新渲染组件（但是如果不用纯组件，还是会重新渲染）
```

纯组件的最佳实践：

 注意：state 或 props 中属性值为引用类型时，应该创建新数据，不要直接修改原数据！

```js
// 创建新数据修改数据，地址不同，可以重新渲染
setState({ obj: {...state.obj, number: 2} })
// 不要用数组的push / unshift 等直接修改当前数组的的方法
// 而应该用 concat 或 slice 等这些返回新数组的方法
this.setState({
	list: [...this.state.list, {新数据}]
})
```