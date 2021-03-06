#React知识点
--------------------------
##jsx语法 js中写xml
		w3c标签 自定义的组件标签（首字母大写）

		<div></div>

##组件
-	React.js 将帮助我们将界面分成了各个独立的小块，每一个块就是组件，这些组件之间可以组合、嵌套，就成了我们的页面。

-	组件有输入、自己的状态和输出。 
		- 输入在React中叫做prop 
		- 自己的状态在React中叫做state 
		- 输入在React中是render函数返回值。

-	class Test extends React.Component {
		constructor(props){
			super(props);
			this.state = {
				n:1
			}
		}

		// 输出
		render(){
			this.props  // 外界定制的数据
			return (
				<div></div>
			)
		}
	}

-	props 是父组件定制的数据，组件自身不能更改
-	state 是组件自身的状态，只能在组件内部更改
-	render 函数的返回值是需要在页面中显示的内容


-	组件定义
		函数组件 展示型的组件，没有生命周期函数
		类组件 

-	组件之间通信
		父组件向子组件 传递props
		子组件向父组件  执行回调函数

-	兄弟组件之间通信
		状态提升，提升到这两个组件公用的父组件中

-	订阅发布模式

-	redux


##生命周期钩子函数
---------------------------------------------

- redux 和react没有关系，结合原生的 jq

- 安装：
	npm install --save redux

- redux
	Redux 是 JavaScript 状态（数据）容器，提供可预测化的状态管理

- 三大原则
	单一数据源
	状态是只读的
	使用纯函数来执行修改


- 使用：
	先创建容器
	定义reducer 初始化数据
	修改数据 提交action对象

-	在redux中修改数据必须提交action，不能直接修改

- 遇到问题：
    'react-scripts' 不是内部或外部命令，也不是可运行的程序
    或批处理文件。

- 使用npm i 把所有的模块从新安装

- 安装模块的时候，可以把下载源切换到国内的淘宝镜像
	npm i redux -S --registry=https://registry.npm.taobao.org
	npm i redux --save --registry=https://registry.npm.taobao.org

-----------------------------------------
##redux + react 结合起来

- npm i redux react-redux -S --registry=https://registry.npm.taobao.org

- 定义redux 完成

- 组件在redux中取值，组件中交互时候，派发action

- 使用 react-redux 链接redux和react组件

### react-redux
-	Provider组件
		把应用根组件包在Provider这个组件内部，让所有的组件都知道redux的存     在，方便之后通过connect取值

-	connect函数

		a. 从redux拿值作为props传递给组件
		b. 组件中有交互，需要派发action，所以需要向组件内部传入函数，在函数中派发action

###使用流程
-	1. 在index.js中，引入redux
		import {createStore} from 'redux'
-	2. 创建容器
		let store = createStore(reducer,data)

-	3. 定义reducer，在src目录下创建目录reducer，在文件中暴露函数

-	4. 引入react-redux，链接redux和react,在index.js中引入
		import { Provider } from 'react-redux'
		
-	5. 根组件包装在Provider组件中,同时传入store
		<Provider store={store}>
            <App />
        </Provider>, 
		  
-	6. 在List个组件中取redux中的值，先在需要的组件中引入connect
		import {connect} from 'react-redux'
		connect(取值函数，dispatch函数)(被包装组件)

-	7. 需要包装一下List组件，同时做一些函数的映射取值，写法
		connect(mapStateToProps)(List)

		connect返回的是一个新的组件
		mapStateToProps 接收一个redux中的state作为参数，执行之后的返回值是       一个对象，将来通过props传给List

-	8. 在List组件中通过props取值
