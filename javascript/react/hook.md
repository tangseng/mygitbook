# 生命周期及钩子

**组件的生命周期：**
>
一个组件类由extends Component创建，并且提供一个render方法以及其他可选的生命周期函数、组件的相关事件和方法来定义的

* getInitialState，在constructor里面调用
* getDefaultProps，组件创建时执行一次并缓存结果
* componentWillMount
* componentDidMount
* componentWillReceiveProps
* shouldComponentUpdate
* componentWillUpdate
* componentDidUpdate
* componentWillUnmount