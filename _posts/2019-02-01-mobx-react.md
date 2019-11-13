---
layout: post
title: 'Mobx-react'
date: 2019-02-01 20:00:21 +0800
author: ma_meng
color: rgb(255,127,80)
cover: 'https://img-blog.csdnimg.cn/20191113200814563.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2d1b2thaWdkZw==,size_16,color_FFFFFF,t_70'
subtitle: '关于mobx的使用'
tags: Mobx Mobx-react 装饰器
---
![](https://img-blog.csdnimg.cn/20191113200814563.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2d1b2thaWdkZw==,size_16,color_FFFFFF,t_70)
> 官方文档 [点击查看](https://cn.mobx.js.org)

> 个人Demo [点击查看]()
<!-- https://github.com/geekxia/react-mobx-todos-demo -->

### 基本用法:
1. store中定义全局变量+ 方法
2. 项目中使用设置
3. 组件引用store

### 1.store/index.js中定义全局变量+ 方法
- observable : 定义变量
- action : 定义方法
- computed : 监听到变量(任意一个)发生变化时候, 自动重新只执行
- new一个AppStore一个实例, 然后抛出去

```js
import{ observable, action, computed} from 'mobx';
import monment from 'moment';

class AppStore{
    @observable time = '2019';
    @observable todos = [];
    @computed get desc(){
        return `${this.time}还有${this.todos.length}条任务等待完成`
    }
    @action addTodo(todo){
        this.todos.push(todo);
    }
    @action deleteTodo(todo){
        this.todos.pop(todo);
    }
    @action reasetTodo(){
        this.todos = [];
    }
    @action getNow(){
        this.time = monment().format('YYYY/MM/DD HH:mm:ss');
    }
}
const store = new AppStore();
setInterval (()=>{
    store.getNow()
},1000)

export default store;
```

### 2.项目中使用设置
- 使用 mobx-react 讲mobx状态跟业务逻辑连接起来
- Provider讲 mobx状态注入(全局状态注入)

```js
import React from 'react'
import { Provider } from 'mobx-react';  //API
import  Home from './pages/Home';
import  store  from './store/index';

function App() {
  return (
    <div> 
      <Provider store = {store}>
        <Home />
      </Provider>
    </div>
  );
}

export default App;
```

### 3.组件引用store
- import { inject, observer } from "mobx-react";
- @inject('store') @observer inject引入store, observer监听store变化, 实时更新状态

```js
import React, { Component } from 'react';
import { inject, observer } from "mobx-react";
import './index.css';

@inject('store') @observer
class Home extends Component {
    constructor(props) {
        super(props);
        this.state = {  }
    }
    handleTodos(res){
        let {store} = this.props;
        switch(res){
            case 'addOne': 
                store.addTodo("新加项目")
                break;
            case 'deleteOne': 
                store.deleteTodo()
                break;
            case 'deleteAll':  
                store.reasetTodo()
                break;
            default:
        }
    }

    render() { 
        let { store } = this.props
        return (  
            <div className='home'>
                <h1>在Reac中使用Mobx</h1>
                <div>{store.desc}</div>
                <button 
                    className='button'
                    onClick = {this.handleTodos.bind(this,'addOne')}
                >
                    添加一条
                </button>
                <button
                    className='button'
                    onClick = {this.handleTodos.bind(this,'deleteOne')}
                >
                    删除一条
                </button>
                <button 
                    className='button'
                    onClick = {this.handleTodos.bind(this,'deleteAll')}
                >
                    删除所有
                </button>
                <div>
                    <ul>
                    {store.todos.map((item,index,arr)=>{
                        return <p key={item+index}>{item}</p>
                    })}
                    </ul>
                </div>
            </div>
        );
    }
}
 
export default Home;
```

