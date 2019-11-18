---
layout: post
title: '上周一个面试题目-将数字转成汉字(js实现)'
date: 2019-11-16 20:00:21 +0800
author: ma_meng
color: rgb(255,210,32)
cover: 'https://img-blog.csdnimg.cn/20191117162503448.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2d1b2thaWdkZw==,size_16,color_FFFFFF,t_70'
subtitle: '上周一个面试题目'
tags: 面试题
---

### 题目是把数字转成汉字表示, 比如 10245转成 一碗零二百四十五 (js实现)

> 思路: 
- 数字 => 字符串
- 字符串对应数字 => 汉字 (特别要注意此处插入顺序跟正常正好相反, 要倒序处理)
- 汉字中插入数值单位(万/千/百 ...) 
- 对连续了零进行处理

```js
    handleNumberToChinese = (num) =>{
      let arr1 = ['零', '一', '二', '三', '四', '五', '六', '七', '八', '九'];
      let arr2 = ['', '十', '百', '千', '万', '十', '百', '千', '亿', '十', '百', '千','万'];
      var arr = num;
      let newArr = arr.toString().split('');
      console.log(newArr);
      let result = '';
      for(let i = 0 ; i < newArr.length ; i++ ){
        result = arr2[i] + result;
        let reverse = newArr.length - i -1; //倒序处理
        let arr1_index = newArr[reverse];
        result = arr1[arr1_index] + result;
      }
        result = result.replace(/零(千|百|十)/g, '零').replace(/十零/g, '十');
        result = result.replace(/零+/g, '零');
        result = result.replace(/零亿/g, '亿').replace(/零万/g, '万');
        result = result.replace(/亿万/g, '亿');
        result = result.replace(/零+$/, '');
        result = result.replace(/^一十/g, '十');
        return result;
      }
```