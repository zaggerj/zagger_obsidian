---
alias:
tags: 长青笔记
cdate: 2023-12-19 19:26
uid: 20231219192658
searchterm: "#长青笔记"
banner: "040 - Obsidian/附件/banners/book-banner.gif"
cssclass: noyaml
banner_icon: 💌
banner_x: 0.5
banner_y: 0.38
---

# 1. # Window 大小和滚动

## 1.1. Metadata

Status:: #笔记状态/🌱 发芽
Source Type:: #📥/💭 想法 
Note Type:: #笔记
Topic:: [[00.学习-前端]]
Author:: zagger
Source URL::
Modify:: 2023-12-19 星期二 19:26:56

## 1.2. 长青笔记

_一句话概括这篇笔记的内容_
Summary::

## 1.3. 自我重述

_用自己的话去重述提取的重点内容_

## 1.4. 重点摘抄

_摘抄部分原文后，进行筛选加粗然后对加粗的继续进行筛选荧光笔选出。_


`window.innerWidth/innerHeight`：包括了滚动条
`document.documentElement.clientWidth`： 可用于内容的文档的可见部分的 width/height。

![image.png](https://raw.githubusercontent.com/zaggerj/obsidian_picgo/main/obsidian/20231219193036.png)

```js
let scrollHeight = Math.max(
  document.body.scrollHeight, document.documentElement.scrollHeight,
  document.body.offsetHeight, document.documentElement.offsetHeight,
  document.body.clientHeight, document.documentElement.clientHeight
);
```
# 2. 相关文章

_摘抄来源，引用出处，参考链接，文档查询_
Page Link::
