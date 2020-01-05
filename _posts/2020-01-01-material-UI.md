---
layout: post
title: "Material-UI "
date: 2020-01-01 20:00:21 +0800
author: ma_meng
color: rgb(30,144,255)
cover: "https://img-blog.csdnimg.cn/20200105182046604.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2d1b2thaWdkZw==,size_16,color_FFFFFF,t_70"
subtitle: "2020拥抱 Material-UI"
tags: Material-UI Google-UI
---

![](https://img-blog.csdnimg.cn/20200105182046604.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2d1b2thaWdkZw==,size_16,color_FFFFFF,t_70)

# 说明

Material-UI —— 世界上最受欢迎的 React UI 框架。

# 安装 Material-UI

- 📦 安装

```
// 用 npm 安装
npm install @material-ui/core

// 用 yarn 安装
yarn add @material-ui/core
```

# 安装 material-ui/icons

- 📦 安装

```
npm install @material-ui/icons
```

[@material-ui/icons](https://www.npmjs.com/package/@material-ui/icons)

[Material Icons - Material-UI](https://material-ui.com/zh/components/material-icons/)

# 安装 material-design-icons

```
 <Icon>star</Icon>
```

```
npm install material-design-icons
```

# 字形：

```
$ npm install typeface-roboto --save
// entry.js
import 'typeface-roboto'

```

# 图标库 <Icon>XXXX</Icon>

- 以下网址选图标, 注意一定要从下面选， 因为引入的是这个图标库

[Tools](https://material.io/resources/icons/?style=baseline)

### 官方文档

[material-design-icons-iconfont](https://www.npmjs.com/package/material-design-icons-iconfont)

```
//安装
npm install material-design-icons-iconfont --save
```

**引入**

```
import 'material-design-icons-iconfont/dist/material-design-icons.css'
```

**使用**

- 方法一

```

<i className="material-icons">face</i>

```

- 方法二

```

import Icon from "@material-ui/core/Icon";
<Icon >backup</Icon>

```

- 修改样式

```
<Icon style={}>{item.icon}</Icon>
```

# Material-UI/Styles

## 说明：

使用 Jss 语法，将 css 写进 js 文件中，实现很多新功能，你如 theme nesting（主题嵌套），dynamic styles(动态模式)self-support（自我支持） 等等...

## **优点：**

- 💅 具备 styled-components 的  [优势](https://www.styled-components.com/docs/basics#motivation)。
- 🚀 速度快
- 🧩 可通过[插件](https://github.com/cssinjs/jss/blob/master/docs/plugins.md)API 扩展。
- ⚡️ 它使用  [JSS](https://github.com/cssinjs/jss)  作为其核心 它在运行时和服务器端工作。
- 📦 大小不超[15 KB](https://bundlephobia.com/result?p=@material-ui/styles) ， 跟 Material-UI 一起使用不会增加体积

## 官方文档：

[@material-ui/styles - Material-UI](https://material-ui.com/zh/styles/basics/#%E5%AE%89%E8%A3%85)

## vscode 插件，支持 jss 语法

- 插件名称：Emmet JSS

## 使用方式

**一共有`三种`使用方式， 以下介绍 hook 的使用**

- Hook API (钩子函数)
- Styled components API （样式化的组件 ）
- Higher-order component API （高阶组件）

## Hook API

### 1.**安装**

```

    // 用npm安装
    npm install @material-ui/styles

    // 用yarn安装
    yarn add @material-ui/styles

```

### 2.**使用( HOOK API 方式）**

```

    **第一步**： import { makeStyles } from '@material-ui/core/styles';

    **第二步**： const useStyles = makeStyles({
    					  root: {
    					    color: 'white',
    					    height: 48,
    							...
    					  },
    					});

    **第三步**：const classes = useStyles();

    **第四步**：className={classes.root}


    import React from 'react';
    import { makeStyles } from '@material-ui/core/styles';  //**第一步**
    import Button from '@material-ui/core/Button';

    const useStyles = makeStyles({   //**第二步**
      root: {
        background: 'rgba(255, 105, 135, .3)',
        height: 48,
        padding: '0 30px',
      },
    });

    export default function Hook() {
      const classes = useStyles();       //**第三步**
      return (
    			<Button className={classes.root}>Hook</Button>  //**第四步**
    	);
    }

```

### 3.注意事项

`①`引入 flex 布局以及其中布局样式要带有“”

```

    CSS
    .sidebar-switch-wrap {
      display: flex;
      justify-content: flex-start;
    }

    JSS
    right: {
        display: "flex",
        flexDirection: "column",
    },

```

`②`className = **`"root`** → className=`{**classes.root**}`

`③` **className 写法：`"font-h1-default"` → `[classes.fontH1Default]`**

```

//CSS写法：
  className={CX({
    "font-h1-default": true
    "font-h1-choosen": item.href === newHref
  })}

//JSS写法：
  className={CX({
    [classes.fontH1Default]: true,
    [classes.fontH1Choosen]: item.href === newHref
  })}

```

`④`伪类

```

goback: {
    width: 24,
    "&:hover": {
      backgroundColor: "#F7F6F3",
      cursor: "pointer"
    },
    "&:active": {
      backgroundColor: "#DAD9D7"
    }
  },

```

## 特性

### 1. 支持嵌套选择器

```

const useStyles = makeStyles({
  root: {
    color: 'red',
    '& p': {
      color: 'green',
      '& span': {
        color: 'blue'
      }
    }
  },
});

```

### 2. 支持传入属性

```

    const useStyles = makeStyles({
      foo: props => ({
        backgroundColor: props.backgroundColor,
      }),
      bar: {
        color: props => props.color,
      },
    });

    function MyComponent() {

      const props = { backgroundColor: 'black', color: 'white' };

      const classes = useStyles(props);   //**传入属性**

      return <div className={`${classes.foo} ${classes.bar}`} />
    }

    **//设置容器固定宽高, 实际项目中使用**

    import React from "react";
    import { makeStyles } from "@material-ui/styles";
    const useStyle = makeStyles({
      LyoutContainerTB: newType => ({
        display: "flex",
        alignItems: "center",
        width: "100%",
        paddingTop: newType.paddingTop,
        paddingBottom: newType.paddingBottom
      })
    });

    function LyoutContainerTB(props) {
      const { type, children } = props;
      const newType = { paddingTop: type, paddingBottom: type };
      const classes = useStyle(newType);
      return <div className={`${classes.LyoutContainerTB}`}>{children}</div>;
    }
    export default LyoutContainerTB;

```

## 高级用法

### 字符串模板

- 如果你喜欢用 css 语法而不是 jss, 那么可以使用规则
  [`jss-plugin-template`](https://cssinjs.org/jss-plugin-template/?v=v10.0.3)插入 css 语法

```

const useStyles = makeStyles({
    root: `font-size: 16px; border: 0; color: white; height: 48px; padding: 0 30px; box-shadow: 0 3px 5px 2px rgba(255, 105, 135, 0.3);`,
    '@media print': {
    button: `color: black`
    },
    '@keyframes id': {
    from: `opacity: 0`,
    to: `opacity: 1`
    }
});

```
