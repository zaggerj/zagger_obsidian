---
alias:
tags: 长青笔记
cdate: 2023-12-19 11:31
uid: 20231219113151
searchterm: "#长青笔记"
banner: "040 - Obsidian/附件/banners/book-banner.gif"
cssclass: noyaml
banner_icon: 💌
banner_x: 0.5
banner_y: 0.38
---

# 1. 遍历 DOM

## 1.1. Metadata

Status:: #笔记状态/🌱 发芽
Source Type:: #📥/💭 想法 
Note Type:: #笔记
Topic:: [[00.学习-前端]]
Author:: zagger
Source URL::
Modify:: 2023-12-19 星期二 11:31:49

## 1.2. 长青笔记

_一句话概括这篇笔记的内容_
Summary::

## 1.3. 自我重述

_用自己的话去重述提取的重点内容_

## 1.4. 重点摘抄

_摘抄部分原文后，进行筛选加粗然后对加粗的继续进行筛选荧光笔选出。_

### 1.4.1. 遍历 DOM

DOM 让我们可以对元素和它们中的内容做任何事，但是首先我们需要获取到对应的 DOM 对象。

对 DOM 的所有操作都是以 `document` 对象开始。它是 DOM 的主“入口点”。从它我们可以访问任何节点。

这里是一张描述对象间链接的图片，通过这些链接我们可以在 DOM 节点之间移动。
![image.png](https://raw.githubusercontent.com/zaggerj/obsidian_picgo/main/obsidian/20231219113234.png)


让我们更详细地讨论它们吧。
### 1.4.2. [在最顶层：documentElement 和 body](https://zh.javascript.info/dom-navigation#zai-zui-ding-ceng-documentelement-he-body)
<mark style="background: #FF5582A6;">小结</mark>：顶层document节点：`<html>`=`document.documentElement`， `<body>` = `document.body`，`<head>` = `document.head`

最顶层的树节点可以直接作为 `document` 的属性来使用：

`<html>` = `document.documentElement`

**最顶层的 document 节点是 `document.documentElement`。这是对应 `<html>` 标签的 DOM 节点。**

`<body>` = `document.body`

另一个被广泛使用的 DOM 节点是 `<body>` 元素 —— `document.body`。

`<head>` = `document.head`

`<head>` 标签可以通过 `document.head` 访问。

**这里有个问题：`document.body` 的值可能是 `null`**

脚本无法访问在运行时不存在的元素。

尤其是，如果一个脚本是在 `<head>` 中，那么脚本是访问不到 `document.body` 元素的，因为浏览器还没有读到它。

所以，下面例子中的第一个 `alert` 显示 `null`：

```html
<html>

<head>
  <script>
    alert( "From HEAD: " + document.body ); // null，这里目前还没有 <body>
  </script>
</head>

<body>

  <script>
    alert( "From BODY: " + document.body ); // HTMLBodyElement，现在存在了
  </script>

</body>
</html>
```

**在 DOM 的世界中，`null` 就意味着“不存在”**

在 DOM 中，`null` 值就意味着“不存在”或者“没有这个节点”。

### 1.4.3. [子节点：childNodes，firstChild，lastChild](https://zh.javascript.info/dom-navigation#zi-jie-dian-childnodesfirstchildlastchild)

从现在开始，我们将使用下面这两个术语：

- **子节点（或者叫作子）** —— 对应的是直系的子元素。换句话说，它们被完全嵌套在给定的元素中。例如，`<head>` 和 `<body>` 就是 `<html>` 元素的子元素。
- **子孙元素** —— 嵌套在给定元素中的所有元素，包括子元素，以及子元素的子元素等。

例如，这里 `<body>` 有子元素 `<div>` 和 `<ul>`（以及一些空白的文本节点）：

```html
<html>
<body>
  <div>Begin</div>

  <ul>
    <li>
      <b>Information</b>
    </li>
  </ul>
</body>
</html>
```

……`<body>` 元素的子孙元素不仅包含直接的子元素 `<div>` 和 `<ul>`，还包含像 `<li>`（`<ul>` 的子元素）和 `<b>`（`<li>` 的子元素）这样的元素 — 整个子树。

**`childNodes` 集合列出了所有子节点，包括文本节点。**

下面这个例子显示了 `document.body` 的子元素：

```html
<html>
<body>
  <div>Begin</div>

  <ul>
    <li>Information</li>
  </ul>

  <div>End</div>

  <script>
    for (let i = 0; i < document.body.childNodes.length; i++) {
      alert( document.body.childNodes[i] ); // Text, DIV, Text, UL, ..., SCRIPT
    }
  </script>
  ...more stuff...
</body>
</html>
```

请注意这里的一个有趣的细节。如果我们运行上面这个例子，所显示的最后一个元素是 `<script>`。实际上，文档下面还有很多东西，但是在这个脚本运行的时候，浏览器还没有读到下面的内容，所以这个脚本也就看不到它们。

**`firstChild` 和 `lastChild` 属性是访问第一个和最后一个子元素的快捷方式。**

它们只是简写。如果元素存在子节点，那么下面的脚本运行结果将是 true：

```js
elem.childNodes[0] === elem.firstChild
elem.childNodes[elem.childNodes.length - 1] === elem.lastChild
```
这里还有一个特别的函数 `elem.hasChildNodes()` 用于检查节点是否有子节点。

### 1.4.4. [DOM 集合](https://zh.javascript.info/dom-navigation#dom-ji-he)

正如我们看到的那样，`childNodes` 看起来就像一个数组。但实际上它并不是一个数组，而是一个 **集合** —— 一个类数组的可迭代对象。

这个性质会导致两个重要的结果：

1. 我们可以使用 `for..of` 来迭代它：

```js
for (let node of document.body.childNodes) {
  alert(node); // 显示集合中的所有节点
}
```

这是因为集合是可迭代的（提供了所需要的 `Symbol.iterator` 属性）。

2. 无法使用数组的方法，因为它不是一个数组：

`alert(document.body.childNodes.filter); // undefined（这里没有 filter 方法！）`

集合的性质所得到的第一个结果很不错。第二个结果也还可以忍受，因为如果我们想要使用数组的方法的话，我们可以使用 `Array.from` 方法来从集合创建一个“真”数组：

`alert( Array.from(document.body.childNodes).filter ); // function`

**DOM 集合是只读的**

DOM 集合，甚至可以说本章中列出的 **所有** <mark style="background: #FF5582A6;">导航（navigation）属性</mark>都是只读的。

我们不能通过类似 `childNodes[i] = ...` 的操作来替换一个子节点。

修改子节点需要使用其它方法。我们将会在下一章中看到它们。

**DOM 集合是实时的**

除小部分例外，几乎所有的 DOM 集合都是 **实时** 的。换句话说，它们反映了 DOM 的当前状态。

如果我们保留一个对 `elem.childNodes` 的引用，然后向 DOM 中添加/移除节点，那么这些节点的更新会自动出现在集合中。

**不要使用 `for..in` 来遍历集合**

可以使用 `for..of` 对集合进行迭代。但有时候人们会尝试使用 `for..in` 来迭代集合。

请不要这么做。`for..in` 循环遍历的是所有可枚举的（enumerable）属性。集合还有一些“额外的”很少被用到的属性，通常这些属性也是我们不期望得到的：

```html
<body>
<script>
  // 显示 0，1，length，item，values 及其他。
  for (let prop in document.body.childNodes) alert(prop);
</script>
</body>
```
# 2. 相关文章

_摘抄来源，引用出处，参考链接，文档查询_
Page Link::
