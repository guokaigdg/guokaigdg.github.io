---
layout: post
title: '图解absolute relative'
date: 2019-12-10 20:00:21 +0800
author: ma_meng
color: rgb(255,210,32)
cover: 'https://img-blog.csdnimg.cn/20191220223756965.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2d1b2thaWdkZw==,size_16,color_FFFFFF,t_70'
subtitle: ''
tags: absolute relative
---
1. Absolute：绝对定位，是相对于最近的且不是static定位的父元素来定位
    
    2. Fixed：绝对定位，是相对于浏览器窗口来定位的，是固定的，不会跟屏幕一起滚动。
    
    3. Relative：相对定位，是相对于其原本的位置来定位的。
    
    4. Static：默认值，没有定位。
    
    5. Inherit：继承父元素的position值。

# 初始设置四个div

    <body>
    	<div class="sun1">sun1</div>
    	<div class="sun2">sun22222</div>
    	<div class="sun3">sun3</div>
    	<div class="sun4">sun4</div>
    </body>


![在这里插入图片描述](https://img-blog.csdnimg.cn/20191220223426701.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2d1b2thaWdkZw==,size_16,color_FFFFFF,t_70)
# 1. 子元素absolute

    .sun2{
        position: absolute;
        height: 100px;
        left: 50px;
        top: 50px;
        background-color:cadetblue
    }

- 第二个元素设置absolute, 脱离文档流，`宽度由文字sun2222撑开`，top跟left根元素即html元素来定位

![2](https://img-blog.csdnimg.cn/2019122022370518.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2d1b2thaWdkZw==,size_16,color_FFFFFF,t_70)

# 2.子元素relative

    .sun2{
        position: relative;
        height: 100px;
        left: 50px;
        top: 50px;
        background-color:cadetblue
    }

- 设置relative的div不会影响其他div的位置，且top和left是相对于它原本自身的位置来定位, 宽度还是`原来父级的宽度`

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191220224057962.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2d1b2thaWdkZw==,size_16,color_FFFFFF,t_70)

# 3.子元素设置一个父级absolute, 子元素absolute

    .sun{
          position:absolute;
          height: 200px;
          background-color: coral;
        }
        .sun2{
          position: absolute;
          height: 100px;
          left: 50px;
          top: 50px;
          background-color:cadetblue
        }

    <div class="sun1">sun1</div>
          <div class="sun">
            这里是sun22222的父元素
            <div class="sun2">sun22222</div>
          </div>
          <div class="sun3">sun3</div>
          <div class="sun4">sun4</div>

- sun2就会相对于父sun的div来定位。子元素sun 宽度由文字sun22222内容撑开决定

![3-1](https://img-blog.csdnimg.cn/20191220223731219.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2d1b2thaWdkZw==,size_16,color_FFFFFF,t_70)

- 子元素sun2222 设置一个500px，宽度不会把父元素撑开

![3-2](https://img-blog.csdnimg.cn/20191220223735825.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2d1b2thaWdkZw==,size_16,color_FFFFFF,t_70)

# 4.子元素设置一个父级absolute, 子元素relative

    .sun{
          position:absolute;
          height: 200px;
          background-color: coral;
        }
        .sun2{
          position: absolute;
          height: 100px;
          left: 50px;
          top: 50px;
          background-color:cadetblue
        }

    .sun{
          position:absolute;
          height: 200px;
          background-color: coral;
        }
        .sun2{
          position: relative;
          height: 100px;
          left: 50px;
          top: 50px;
          background-color:cadetblue
        }

- sun2就会相对于父sun的div来定位。子元素sun2222 宽度与父元素相同

![4-1](https://img-blog.csdnimg.cn/20191220223750576.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2d1b2thaWdkZw==,size_16,color_FFFFFF,t_70)

- 父级absolute, 子元素relative，子元素sun2222 设置一个500px，`**子元素宽度会把父元素撑开**`

![4-2](https://img-blog.csdnimg.cn/20191220223756965.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2d1b2thaWdkZw==,size_16,color_FFFFFF,t_70)

# 5.子元素设置一个父级relative, 子元素absolute（常用）

    .sun{
          position: relative;
          height: 200px;
          background-color: coral;
        }
        .sun2{
          position: absolute;
          height: 100px;
          width: 500px;
          left: 50px;
          top: 50px;
          background-color:cadetblue
        }

- 子元素定位相对于父元素

![5-1](https://img-blog.csdnimg.cn/20191220223759511.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2d1b2thaWdkZw==,size_16,color_FFFFFF,t_70)

- 子元素定位相对于父元素，子元素设置宽度不会影响父元素

![5-2](https://img-blog.csdnimg.cn/20191220223808736.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2d1b2thaWdkZw==,size_16,color_FFFFFF,t_70)

## 总结：

- **absolute: 会脱离文档流 ，定位是相对于离它最近的且不是static定位的父元素而言，若该元素没有设置宽度，则`宽度由元素里面的内容决定`，且宽度不会影响父元素，定位为absolution后，原来的位置相当于是空的，下面的的元素会来占据。**
- **relative: 不会脱离文档流，定位是相对于原本自身的位置，若没有宽度，那么宽度为父元素宽度，该元素的宽度会影响父元素的的大小**