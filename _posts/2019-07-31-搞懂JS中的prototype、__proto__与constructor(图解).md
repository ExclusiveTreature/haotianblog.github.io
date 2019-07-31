---
layout:     post
title:      弄懂JS中的prototype、__proto__与constructor
subtitle:   H.T. Blog prototype、__proto__与constructor
date:       2019-07-31
author:     haotian
header-img: img/post-bg-universe.jpg
catalog: true
tags:
    - prototype、__proto__与constructor
---

## 文章目录
1. 前言
2. _ _ proto _ _ 属性
3. prototype属性
4. constructor属性
5. 总结

## 前言
作为一名前端工程师，必须搞懂JS中的prototype、__proto__与constructor属性，相信很多初学者对这些属性存在许多困惑，容易把它们混淆，本文旨在帮助大家理清它们之间的关系并彻底搞懂它们。这里说明一点，__proto__属性的两边是各由两个下划线构成（这里为了方便大家看清，在两下划线之间加入了一个空格：_ _proto_ _），本文基于谷歌浏览器（版本 72.0.3626.121）的实验结果所得。

<br/>
function Foo() {....} <br/>
var f1 = new Foo() <br/>

以上代码表示创建一个构造函数Foo()，并用new关键字实例化该构造函数得到一个实例化对象f1。这里稍微补充一下new操作符将函数作为构造器进行调用时的过程：函数被调用，然后新创建一个对象，并且成了函数的上下文（也就是此时函数内部的this是指向该新创建的对象，这意味着我们可以在构造器函数内部通过this参数初始化值），最后返回该新对象的引用。虽然是简简单单的两行代码，然而它们背后的关系却是错综复杂的，如下图所示：
![](https://img-blog.csdnimg.cn/20190311194017886.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2NjMTg4Njg4NzY4Mzc=,size_16,color_FFFFFF,t_70)