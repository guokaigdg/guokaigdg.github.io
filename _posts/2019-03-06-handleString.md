---
layout: post
title:  "字符串匹配算法"
date: 2019-03-06 5:00:21 +0800
tags: 字符串匹配
color: rgb(255,215,0)
cover: 'https://img-blog.csdnimg.cn/201911240033008.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2d1b2thaWdkZw==,size_16,color_FFFFFF,t_70'
subtitle: ''
---
## 字符串匹配算法

> 实现一个字符串匹配算法，从字符串 S 中，查找是否存在字符串 T，若存在返回所在位置，不存在返回-1！（如果不能基于indexOf/includes等内置的方法，你会如何处理呢？）
### 方法一, arr.substr()遍历匹配

```js
let S = 'adfasfsdgergvdfbewdfbbdbs';
let T = 'bbdbs';
~function(){
    function myIndexOf(T){
        let len = this.length;
        let len2 = T.length;
        let res = -1;
        if(len2 > len){
            return -1;
        }
        for(let i = 0 ; i <= len - len2; i++){
            if(this.substr(i,len2) === T){
                res = i;
                break;
            }
        }
        return res;
    }
    String.prototype.myIndexOf = myIndexOf;
}();

console.log(S.myIndexOf(T));
```
### 方法二: 正则匹配

```js
let S = 'adfasfsdgergvdfbewdfbbdbs';
let T = 'bbdbs';
~function(){
    function myIndexOf(T){
        let reg = new RegExp(T);
        let res = reg.exec(this);
        return res === null? -1: res.index;
    }
    String.prototype.myIndexOf = myIndexOf;
}();

console.log(S.myIndexOf(T));
```