---
alias:
tags: 长青笔记
cdate: 2023-12-19 14:26
uid: 20231219142634
searchterm: "#长青笔记"
banner: "040 - Obsidian/附件/banners/book-banner.gif"
cssclass: noyaml
banner_icon: 💌
banner_x: 0.5
banner_y: 0.38
---

# 1. 节点属性：type，tag 和 content

## 1.1. Metadata

Status:: #笔记状态/🌱 发芽
Source Type:: #📥/💭 想法 
Note Type:: #笔记
Topic:: [[00.学习-前端]]
Author:: zagger
Source URL::
Modify:: 2023-12-19 星期二 14:26:33

## 1.2. 长青笔记

_一句话概括这篇笔记的内容_
Summary::

## 1.3. 自我重述

_用自己的话去重述提取的重点内容_

## 1.4. 重点摘抄

_摘抄部分原文后，进行筛选加粗然后对加粗的继续进行筛选荧光笔选出。_

### 1.4.1. 节点属性：type，tag 和 content

让我们更深入地了解一下 DOM 节点。

在本章中，我们将更深入地了解它们是什么，并学习它们最常用的属性。

### 1.4.2. [DOM 节点类](https://zh.javascript.info/basic-dom-node-properties#dom-jie-dian-lei)

不同的 DOM 节点可能有不同的属性。
例如，标签 `<a>` 相对应的元素节点具有链接相关的（link-related）属性，
标签 `<input>` 相对应的元素节点具有与输入相关的属性，等。文本节点与元素节点不同。
但是所有这些标签对应的 DOM 节点之间也存在共有的属性和方法，
因为所有类型的 DOM 节点都形成了一个单一层次的结构（single hierarchy）。![image.png](https://raw.githubusercontent.com/zaggerj/obsidian_picgo/main/obsidian/20231219142936.png)


每个 DOM 节点都属于相应的内建类。

层次结构（hierarchy）的根节点是 [EventTarget](https://dom.spec.whatwg.org/#eventtarget)，
[Node](https://dom.spec.whatwg.org/#interface-node) 继承自它，
其他 DOM 节点继承自 Node。

下图做了进一步说明：

![image.png](https://raw.githubusercontent.com/zaggerj/obsidian_picgo/main/obsidian/20231219142739.png)

类如下所示：

- [EventTarget](https://dom.spec.whatwg.org/#eventtarget) —— 是一切的根“抽象（abstract）”类。
    
    该类的对象从未被创建。它作为一个基础，以便让所有 DOM 节点都支持所谓的“事件（event）”，我们会在之后学习它。
    
- [Node](http://dom.spec.whatwg.org/#interface-node) —— 也是一个“抽象”类，充当 DOM 节点的基础。
    
    它提供了树的核心功能：`parentNode`，`nextSibling`，`childNodes` 等（它们都是 getter）。`Node` 类的对象从未被创建。但是还有一些继承自它的其他类（因此继承了 `Node` 的功能）。
    
- [Document](https://dom.spec.whatwg.org/#interface-document) 由于历史原因通常被 `HTMLDocument` 继承（尽管最新的规范没有规定）—— 是一个整体的文档。

	 *`HTMLDocument` 继承自 Document类，全局变量 `document`属于 `HTMLDocument`。*
    
    全局变量 `document` 就是属于这个类。它作为 DOM 的入口。
- [CharacterData](https://dom.spec.whatwg.org/#interface-characterdata) —— 一个“抽象”类，被下述类继承：
    
    - [Text](https://dom.spec.whatwg.org/#interface-text) —— 对应于元素内部文本的类，例如 `<p>Hello</p>` 中的 `Hello`。
    - [Comment](https://dom.spec.whatwg.org/#interface-comment) —— 注释类。它们不会被展示出来，但每个注释都会成为 DOM 中的一员。
- [Element](http://dom.spec.whatwg.org/#interface-element) —— 是 DOM 元素的基础类。
    
    它提供了元素级导航（navigation），如 `nextElementSibling`，`children`，以及搜索方法，如 `getElementsByTagName` 和 `querySelector`。
    
    浏览器不仅支持 HTML，还支持 XML 和 SVG。因此，`Element` 类充当的是更具体的类的基础：`SVGElement`，`XMLElement`（我们在这里不需要它）和 `HTMLElement`。
    
- 最后，[HTMLElement](https://html.spec.whatwg.org/multipage/dom.html#htmlelement) —— 是所有 HTML 元素的基础类。我们大部分时候都会用到它。
    
    它会被更具体的 HTML 元素继承：
    
    - [HTMLInputElement](https://html.spec.whatwg.org/multipage/forms.html#htmlinputelement) —— `<input>` 元素的类，
    - [HTMLBodyElement](https://html.spec.whatwg.org/multipage/semantics.html#htmlbodyelement) —— `<body>` 元素的类，
    - [HTMLAnchorElement](https://html.spec.whatwg.org/multipage/semantics.html#htmlanchorelement) —— `<a>` 元素的类，
    - ……等。

还有很多其他标签具有自己的类，可能还具有特定的属性和方法，而一些元素，如 `<span>`、`<section>`、`<article>` 等，没有任何特定的属性，所以它们是 `HTMLElement` 类的实例。

因此，给定节点的全部属性和方法都是继承链的结果。

例如，我们考虑一下 `<input>` 元素的 DOM 对象。它属于 [HTMLInputElement](https://html.spec.whatwg.org/multipage/forms.html#htmlinputelement) 类。

它获取属性和方法，并将其作为下列类（按继承顺序列出）的叠加：

- `HTMLInputElement` —— 该类提供特定于输入的属性，
- `HTMLElement` —— 它提供了通用（common）的 HTML 元素方法（以及 getter 和 setter）
- `Element` —— 提供通用（generic）元素方法，
- `Node` —— 提供通用 DOM 节点属性，
- `EventTarget` —— 为事件（包括事件本身）提供支持，
- ……最后，它继承自 `Object`，因为像 `hasOwnProperty` 这样的“普通对象”方法也是可用的。

我们可以通过回调来查看 DOM 节点类名，因为对象通常都具有 `constructor` 属性。它引用类的 constructor，`constructor.name` 就是它的名称：



# 2. 相关文章

_摘抄来源，引用出处，参考链接，文档查询_
Page Link::
