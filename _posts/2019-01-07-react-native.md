---
layout: post
title: 'React-native 练手项目'
date: 2019-01-07 20:00:21 +0800
author: ma_meng
color: rgb(255,192,203)
cover: 'https://img-blog.csdnimg.cn/20191111132643280.png'
subtitle: 'RN RN RN 来玩啊'
tags: react react-native
---


[Github地址](https://github.com/guokaigdg/React-native-app-guokai)

### React-native 练手APP
业余时间学习下React-native, 感兴趣的可以来一起交流下
> email: guokaigdg@gmail.com <br>
> wechat:guokaigdg <br>

#### 开发环境
> react-native-cli: 2.0.1 <br>
> node: v8.9.4 <br>
> macOS Mojave 版本10.14.1 <br>
> 测试环境: react-native run-ios --simulator "iPhone 6"


#### 进度
> (2019-1-7 - 2019-？佛系时间)
#### 2019/1/7
- 创建第一个页面,并且创建一个轮播图
- <img src = "https://img-blog.csdnimg.cn/20190108013736540.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2d1b2thaWdkZw==,size_16,color_FFFFFF,t_70" width = '25%'>

#### 2019/1/8
 - 给搜索按钮/轮播图片添加点击事件   <br>
   搜索:直接到<Buttoon> ps:<Button onPress={()=>Alert.alert('点击了按钮','点击OK关闭',null)}><br>
   轮播图/ListView : <TouchableHighlight>
 - 状态栏目添加了网络请求状态/状态栏颜色  <br>
  注意区分Android/ios不同表现,使用:StatusBar组件

#### 2019/1/9
- 更换app图标 
- 给商品区域创立一个单个栏目,如图
- 优化将轮播图格式独立出来<br>
  多个格式放一个数组: style={[styles.advertismentContenr,{backgroundColor:'blue'}]}
- <img src = "https://img-blog.csdnimg.cn/2019010922561528.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2d1b2thaWdkZw==,size_16,color_FFFFFF,t_70" width = '25%'>

#### 2019/1/10
- 使用JavaScript数组的map()方法进一步优化TouchableHighlight组件(优化轮播图)
- onChangeText() 输入框变化时候调用此回调函数
- Chorm Console调试搜索结果
- 优化搜索框样式borderRedius
- 轮播图使用网络图片
- <img src = "https://img-blog.csdnimg.cn/20190111014039891.gif" width = '25%'>


#### 2019/1/11
- 给轮播图添加指示器
- 加载网路图片/本地图片
- 重新定义商品模型(布局)加优化 <br>
  (给商品加图片加文字重新布局)
- <img src = "https://img-blog.csdnimg.cn/20190112030407101.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2d1b2thaWdkZw==,size_16,color_FFFFFF,t_70" width = '25%'>

#### 遗留问题

- [ ] iPhone不同机型有刘海的跟没有刘海marginTop大小自动适应

#### 2019/1/12
-  实现了拖拽下拉刷新 refreshContol
-  在根目录下创建一个images保存图片以供取读
### 2019/1/13
- 讲style 从App.js分离出来单独设置为style.js
#### 2019/1/14
-  添加页面跳转Navigator还没成功


#### 2019/1/28
- 安装react navigation 

```
npm install -save react-navigation
npm install -save react-native-vector-icons
```
#### 2019/3/8
- 使用React avigation导航
- 官方中文网址https://reactnavigation.org/docs/zh-Hans/hello-react-navigation.html

#### 2019/3/9
- 使用Tab Navigation导航
- 使用Drawer Navigation导航
#### 2019/3/10
- 页面跳转的数据传递 
> 1. 参数传递: navigate接受可选的第二个参数，以便将参数传递给要导航到的路由。例如：this.props.navigation.navigate('RouteName', {paramName:  'value'})。<br>
>2. 读取参数：我们可以使用this.props.navigation.getParam读取参数<br>
>3. 也可以使用 this.props.navigation.state.params作为getParam的替代方案， 如果未指定参数，它的值是 null。

#### 2019/3/11
- 设置标题栏显示的标题自定义标题样式
- 独立设计组件引用组件
#### 2019/3/12
- 整合Login/Home/StackNavigator/DrawerNavigato/BottomTabNavigator做成简单Demo 
#### 2019/3/13
- 页面组件的navigationOptions静态属性内自定义标题

#### 2019/3/14
- 标题栏和其所属的页面之间的交互 数据传递
- Math.floor(Math.random()) 生成随机数
- <img src = "https://img-blog.csdnimg.cn/20190315153042444.gif" width = '25%'>

#### 2019/3/18
- 使用图标 import Icon from 'react-native-vector-icons/Ionicons' 
- <img src = "https://img-blog.csdnimg.cn/20190319015048530.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2d1b2thaWdkZw==,size_16,color_FFFFFF,t_70" width = '25%'>
#### 2019/3/19
- state数据传输
#### 2019/3/25
- 使用组件:加载指示器ActivityIndicator
#### 2019/3/26
- 点击变化容器:TouchableOpacity
#### 2019/3/27
- 点击开关: <Switch />

#### 2019/4/08
- - <img src = "https://img-blog.csdnimg.cn/20190411095504998.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2d1b2thaWdkZw==,size_16,color_FFFFFF,t_70" width = '25%'> 


#### 2019/4/14
- react-native-splash-screen 启动页
- 使用第三方组件:
1. 先分析项目中需要哪些第三方组件
2. 挨个测试第三方组件的兼容性(主要是测试react native能兼容的最大版本) <br>
    a)下载第三方组件开发者提供的演示 <br>
    b)本地调试演示项目 <br>
    c)如果演示项目调试成功, 并且满足功能需求, 就尝试将组件整合到你期望的rn版本中
3. 确定要使用的reactnative版本

#### 2019/4/15
- react-native-splash-screen 启动页
#### 2019/4/17
- react-native-image-crop-picker 裁剪上传图片
