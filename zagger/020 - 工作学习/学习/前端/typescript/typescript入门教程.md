---
alias: 
tags: 长青笔记
cdate: 2023-11-14 16:39
uid: 20231114163923
update: NaN
searchterm: "#长青笔记"
banner: 040 - Obsidian/附件/banners/book-banner.gif
cssclass: noyaml
banner_icon: 💌
banner_x: 0.5
banner_y: 0.38
created: 2023-11-14 16:39:15
updated: 2023-11-14 16:49:40
---

# 1. typescript入门教程

## 1.1. Metadata

Status:: #笔记状态/🌱 发芽
Source Type:: #📥/💭 想法 
Note Type:: #笔记
Topic:: [[typescript]]
Author:: {原资讯的作者或者对话的人或者引起某种想法的原因}
Source URL::
Modify:: `=dateformat(this.file.mtime, "yyyy-MM-dd HH:MM:ss")`

## 1.2. 长青笔记

_一句话概括这篇笔记的内容_
Summary::学习typescript，为学习vue3做好准备，并且在后续多编写typescript相关的代码。

## 1.3. 自我重述

_用自己的话去重述提取的重点内容_
打好基础
## 1.4. 重点摘抄

_摘抄部分原文后，进行筛选加粗然后对加粗的继续进行筛选荧光笔选出。_


---

# 2. 原始数据类型

JavaScript 的类型分为两种：原始数据类型（[Primitive data types](https://developer.mozilla.org/en-US/docs/Glossary/Primitive)）和对象类型（Object types）。

原始数据类型包括：布尔值、数值、字符串、`null`、`undefined` 以及 ES6 中的新类型 [`Symbol`](http://es6.ruanyifeng.com/#docs/symbol) 和 ES10 中的新类型 [`BigInt`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/BigInt)。
## 2.1. 布尔值[§](https://ts.xcatliu.com/basics/primitive-data-types.html#%E5%B8%83%E5%B0%94%E5%80%BC)

布尔值是最基础的数据类型，在 TypeScript 中，使用 `boolean` 定义布尔值类型。
注意，使用构造函数 `Boolean` 创造的对象**不是**布尔值，而是一个 `Boolean` 对象。
直接调用 `Boolean` 也可以返回一个 `boolean` 类型。
在 TypeScript 中，`boolean` 是 JavaScript 中的基本类型，而 `Boolean` 是 JavaScript 中的构造函数。其他基本类型（除了 `null` 和 `undefined`）一样，不再赘述。
## 2.2. 数值[§](https://ts.xcatliu.com/basics/primitive-data-types.html#%E6%95%B0%E5%80%BC)

使用 `number` 定义数值类型
## 2.3. 字符串[§](https://ts.xcatliu.com/basics/primitive-data-types.html#%E5%AD%97%E7%AC%A6%E4%B8%B2)

使用 `string` 定义字符串类型
## 2.4. 空值[§](https://ts.xcatliu.com/basics/primitive-data-types.html#%E7%A9%BA%E5%80%BC)

JavaScript 没有空值（Void）的概念，在 TypeScript 中，可以用 `void` 表示没有任何返回值的函数
声明一个 `void` 类型的变量没有什么用，因为你只能将它赋值为 `undefined` 和 `null`（只在 --strictNullChecks 未指定时）

## 2.5. Null 和 Undefined[§](https://ts.xcatliu.com/basics/primitive-data-types.html#null-%E5%92%8C-undefined)

在 TypeScript 中，可以使用 `null` 和 `undefined` 来定义这两个原始数据类型
与 `void` 的区别是，`undefined` 和 `null` 是所有类型的子类型。也就是说 `undefined` 类型的变量，可以赋值给 `number` 类型的变量.
而 `void` 类型的变量不能赋值给 `number` 类型的变量

# 3. 任意值

任意值（Any）用来表示允许赋值为任意类型。

## 3.1. 什么是任意值类型[§](https://ts.xcatliu.com/basics/any.html#%E4%BB%80%E4%B9%88%E6%98%AF%E4%BB%BB%E6%84%8F%E5%80%BC%E7%B1%BB%E5%9E%8B)

如果是一个普通类型，在赋值过程中改变类型是不被允许的.
但如果是 `any` 类型，则允许被赋值为任意类型。
## 3.2. 任意值的属性和方法[§](https://ts.xcatliu.com/basics/any.html#%E4%BB%BB%E6%84%8F%E5%80%BC%E7%9A%84%E5%B1%9E%E6%80%A7%E5%92%8C%E6%96%B9%E6%B3%95)

在任意值上访问任何属性都是允许的，也允许调用任何方法。
可以认为，**声明一个变量为任意值之后，对它的任何操作，返回的内容的类型都是任意值**。

## 3.3. 未声明类型的变量[§](https://ts.xcatliu.com/basics/any.html#%E6%9C%AA%E5%A3%B0%E6%98%8E%E7%B1%BB%E5%9E%8B%E7%9A%84%E5%8F%98%E9%87%8F)

**变量如果在声明的时候，未指定其类型，那么它会被识别为任意值类型**



---

## 3.4. 相关文章

_摘抄来源，引用出处，参考链接，文档查询_
Page Link::https://ts.xcatliu.com/basics/primitive-data-types.html


