---
layout: post
title: '面试问题大集合 巴拉巴拉'
date: 2019-02-07 20:00:21 +0800
author: ma_meng
color: rgb(135,206,250)
cover: 'https://img-blog.csdnimg.cn/2019112202101646.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2d1b2thaWdkZw==,size_16,color_FFFFFF,t_70'
subtitle: ''
tags: 面试小仓库
---

#### 实现 (5).add(3).minus(2) ，使其输出结果为：6 
```js
 ~ function () {
	//=>每一个方法执行完，都要返回NUMBER这个类的实例，这样才可以继续调取NUMBER类原型中的方法（链式写法）
	function check(n) {
		n = Number(n);
		return isNaN(n) ? 0 : n;
	}

	function add(n) {
		n = check(n);
		return this + n;
	}

	function minus(n) {
		n = check(n);
		return this - n;
	}

	Number.prototype.add = add;
	Number.prototype.minus = minus;
	//["add", "minus"].forEach(item => {
	//	Number.prototype[item] = eval(item);
	// }); 
}();
console.log((5).add(3).minus(2));
```
一、HTML5 / CSS3部分

介绍一下BFC及其应用，IFC、GFC 和 FFC你都了解吗？

怎么让一个 div 水平垂直居中

分析比较 opacity: 0、visibility: hidden、display: none 优劣和适用场景

已知如下代码，如何修改才能让图片宽度为 300px ？注意下面代码不可修改。


1
<img src="1.jpg" style="width:480px!important;”>
用CSS实现三栏布局 ，左定右定中间自适应？ 
使用CSS，让一个div消失在视野中，发挥想象力 ？
如何用css绘制一个三角(不允许使用图片)？ 
css有哪些盒子模型？它们对应的样式是什么？如何让IE以标准模型渲染？
CSS优先级算法如何计算？
请解释一下CSS3的flexbox（弹性盒布局模型）,以及适用场景？ 
二、JAVASCRIPT部分

call 和 apply 的区别是什么，哪个性能更好一些

实现 (5).add(3).minus(2) ，使其输出结果为：6

箭头函数与普通函数（function）的区别是什么？构造函数（function）可以使用 new 生成实例，那么箭头函数可以吗？为什么？

如何把一个字符串的大小写取反（大写变小写小写变大写），例如 ’AbC' 变成 'aBc' 

实现一个字符串匹配算法，从字符串 S 中，查找是否存在字符串 T，若存在返回所在位置，不存在返回-1！（如果不能基于indexOf/includes等内置的方法，你会如何处理呢？）

输出下面代码运行结果


1
//example 1
2
var a={}, b='123', c=123;  
3
a[b]='b';
4
a[c]='c';  
5
console.log(a[b]);
6
​
7
---------------------
8
//example 2
9
var a={}, b=Symbol('123'), c=Symbol('123');  
10
a[b]='b';
11
a[c]='c';  
12
console.log(a[b]);
13
​
14
---------------------
15
//example 3
16
var a={}, b={key:'123'}, c={key:'456'};  
17
a[b]='b';
18
a[c]='c';  
19
console.log(a[b]);
在输入框中如何判断输入的是一个正确的网址，例如：用户输入一个字符串，验证是否符合URL网址的格式

下面代码输出的结果


1
function Foo() {
2
    Foo.a = function() {
3
        console.log(1)
4
    }
5
    this.a = function() {
6
        console.log(2)
7
    }
8
}
9
Foo.prototype.a = function() {
10
    console.log(3)
11
}
12
Foo.a = function() {
13
    console.log(4)
14
}
15
Foo.a();
16
let obj = new Foo();
17
obj.a();
18
Foo.a();
编写代码实现图片的懒加载

编写一条正则，用来验证此规则：一个6~16位的字符串，必须同时包含有大小写字母和数字

完成如下需求


1
/* 实现一个$attr(name,value)遍历
2
 * 属性为name
3
 * 值为value的元素集合
4
 * 
5
 * 例如下面示例:
6
 */
7
let ary = $attr('class','box'); //=>获取页面中所有class为box的元素
英文字母汉字组成的字符串，用正则给英文单词前后加空格
三、烧脑的算法题（注意不要揪头发）(*^▽^*)

算法题（携程）


1
/*编写一个程序，将数组扁平化，并去除其中重复部分数据，最终得到一个升序且不重复的数组*/
2
let arr = [[1, 2, 2], [3, 4, 5, 5], [6, 7, 8, 9,[11, 12, [12, 13, [14]]]], 10];
情人节福利题：重构内置new方法


1
function Dog(name) {
2
    this.name = name;
3
}
4
Dog.prototype.bark = function () {
5
    console.log('wangwang');
6
}
7
Dog.prototype.sayName = function () {
8
    console.log('my name is ' + this.name);
9
}
10
/*
11
let sanmao = new Dog('三毛');
12
sanmao.sayName();
13
sanmao.bark();
14
*/
15
//=>基于内置的new关键词，我们可以创建Dog的一个实例sanmao，实例可以调取原型上的属性和方法，现在的需求是：自己实现一个_new方法，也能模拟出内置new后的结果
16
function _new() {
17
    //=>完成你的代码
18
    
19
}
20
let sanmao = _new(Dog, '三毛');
21
sanmao.bark(); //=>"wangwang"
22
sanmao.sayName(); //=>"my name is 三毛"
23
console.log(sanmao instanceof Dog); //=>true
两个数组和并为一个数组


1
let ary1 = ['A1', 'A2', 'B1', 'B2', 'C1', 'C2', 'D1', 'D2'];
2
let ary2 = ['A', 'B', 'C', 'D']; 
3
//=>合并后的数组为：['A1', 'A2', 'A', 'B1', 'B2', 'B', 'C1', 'C2', 'C', 'D1', 'D2', 'D']
改造下面代码，使之输出0-9


1
for (var i = 0; i < 10; i++) {
2
    setTimeout(() => {
3
        console.log(i);
4
    }, 1000);
5
}
下面代码输出的结果是多少，为什么？如何改造一下，就能让其输出 20 10？


1
var b = 10;
2
(function b() {
3
    b = 20;
4
    console.log(b);
5
})();
6
console.log(b);
下面代码a在什么值情况下会输出1


1
var a = ?;
2
if (a == 1 && a == 2 && a == 3) {
3
    console.log(1);
4
}
下面代码的输出结果？为什么？


1
let obj = {
2
    2: 3,
3
    3: 4,
4
    length: 2,
5
    push: Array.prototype.push
6
}
7
obj.push(1);
8
obj.push(2);
9
console.log(obj);
冒泡排序如何实现，时间复杂度是多少， 还可以如何改进？

完成如下需求


1
/* 
2
某公司1到12月份的销售额存在一个对象里面
3
如下： {
4
    1: 222,
5
    2: 123,
6
    5: 888
7
}，
8
请把数据处理为如下结构：[222, 123, null, null, 888, null, null, null, null, null, null, null] 
9
*/
给定两个数组， 写一个方法来计算它们的交集


1
let nums1 = [1, 2, 2, 1];
2
let nums2 = [2, 2];
3
//=> 输出结果 [2,2]

### 算法题「旋转数组」


1
/* 
2
给定一个数组，将数组中的元素向右移动 k 个位置，其中 k 是非负数
3
输入: [1, 2, 3, 4, 5, 6, 7] 和 k = 3
4
输出: [5, 6, 7, 1, 2, 3, 4]
5
解释:
6
向右旋转 1 步: [7, 1, 2, 3, 4, 5, 6]
7
向右旋转 2 步: [6, 7, 1, 2, 3, 4, 5]
8
向右旋转 3 步: [5, 6, 7, 1, 2, 3, 4]
9
​
10
输入: [-1, -100, 3, 99] 和 k = 2
11
输出: [3, 99, -1, -100]
12
解释: 
13
向右旋转 1 步: [99, -1, -100, 3]
14
向右旋转 2 步: [3, 99, -1, -100] 
15
*/
请实现一个 add 函数，满足以下功能

```
1
add(1);       //1
2
add(1)(2);    //3
3
add(1)(2)(3); //6
4
add(1)(2,3);  //6
5
add(1,2)(3);  //6
6
add(1,2,3);   //6
```