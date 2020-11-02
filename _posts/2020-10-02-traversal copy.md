---
layout: post
title: "二叉树遍历"
date: 2020-10-01 11:22:21 +0800
author: ma_meng
color: rgb(30,144,255)
cover: "https://img-blog.csdnimg.cn/20201007123627609.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2d1b2thaWdkZw==,size_16,color_FFFFFF,t_70#pic_center"
subtitle: "Welcome to 组件设计"
tags: 二叉树遍历 前中后遍历 层序遍历
---

![](https://img-blog.csdnimg.cn/2020100712260080.png#pic_center)

```js
const root = {
  val: 1,
  left: {
    val: 2,
    left: { val: 4, left: null, right: null },
  },
  right: {
    val: 3,
    left: { val: 5, left: null, right: null },
    right: { val: 6, left: null, right: null },
  },
};
let res = [];
let res2 = [];
let res3 = [];

//前序遍历
const startTraversal = (root) => {
  root.val && res.push(root.val);
  root.left && startTraversal(root.left);
  root.right && startTraversal(root.right);
  return res;
};

//中序遍历
const midTraversal = (root) => {
  root.left && midTraversal(root.left);
  root.val && res2.push(root.val);
  root.right && midTraversal(root.right);
  return res2;
};

//后序遍历
const endTraversal = (root) => {
  root.left && endTraversal(root.left);
  root.right && endTraversal(root.right);
  root.val && res3.push(root.val);
  return res3;
};

//层序遍历
const levelTraversal = (root) => {
  let res = [];
  if (!root) {
    return res;
  }
  let tree = [];

  tree.push(root);

  while (tree.length) {
    let node = tree.shift();
    if (node.val) {
      res.push(node.val);
    }
    if (node.left) {
      tree.push(node.left);
    }
    if (node.right) {
      tree.push(node.right);
    }
  }
  return res;
};

console.log("前序遍历:", startTraversal(root));
console.log("中序遍历:", midTraversal(root));
console.log("后序遍历:", endTraversal(root));
console.log("层序遍历:", levelTraversal(root));
```
