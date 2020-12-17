

## 1. 搭建项目
    1). 使用create-react-app脚手架创建模板项目(工程化)
    2). 引入antd-mobile, 并实现按需打包和自定义主题
    3). 引入react-router-dom(v4): 
        HashRouter/Route/Switch
        history: push()/replace()
    4). 引入redux
        redux/react-redux/redux-thunk
        redux: createStore()/combineReducers()/applyMiddleware()
        react-redux: <Provider store={store}> / connect()(Xxx)
        4个重要模块: reducers/store/actions/action-types

## 2. 登陆/注册界面
    1). 创建3个1级路由: main/login/register
    2). 完成登陆/注册的静态组件
        antd组件: NavBar/WingBlank/WhiteSpace/List/InputItem/Radio/Button
        路由跳转: this.props.history.replace('/login')
        收集表单输入数据: state/onChange/变量属性名
    
## 3. 注册/登陆前台处理
    1). ajax
        ajax请求函数(通用): 使用axios库, 返回的是promise对象
        后台接口请求函数: 针对具体接口定义的ajax请求函数, 返回的是promise对象
        代理: 跨域问题/配置代理解决
        await/async: 同步编码方式实现异步ajax请求 
    2). redux
        store.js
          生成并暴露一个store管理对象
        reducers.js
          包含n个reducer函数
          根据老state和指定action来产生返回一个新的state
        actions.js
          包含n个action creator函数
          同步action: 返回一个action对象({type: 'XXX', data: xxx})
          异步action: 返回一个函数: disptach => {执行异步代理, 结束时dispatch一个同步action}
        action-types.js
          action的type名称常量
    3). component
        UI组件: 
            组件内部没有使用任何redux相关的API
            通过props接收容器组件传入的从redux获取数据
            数据类型: 一般和函数
        容器组件
            connect(
              state => ({user: state.user}),
              {action1, action2}
            )(UI组件)