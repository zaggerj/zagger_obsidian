---
alias:
tags: 长青笔记
cdate: 2023-11-13 08:33
uid: 20231211084830
searchterm: "#长青笔记"
banner: "040 - Obsidian/附件/banners/book-banner.gif"
cssclass: noyaml
banner_icon: 💌
banner_x: 0.5
banner_y: 0.38
tags: 资源/软件安装
created: 2023-11-03T22:29
updated: 2023-11-14T09:21
---

# 1. vim使用技巧

## 1.1. Metadata

Status:: #笔记状态/🌱 发芽
Source Type:: #📥/💭 想法 
Note Type:: #笔记
Topic:: [[00.学习-前端]]
Author:: zagger
Source URL::
Modify:: 2023-12-11 星期一 08:48:25

## 1.2. 长青笔记

_一句话概括这篇笔记的内容_
Summary::

## 1.3. 自我重述

_用自己的话去重述提取的重点内容_

## 1.4. 重点摘抄

_摘抄部分原文后，进行筛选加粗然后对加粗的继续进行筛选荧光笔选出。_

### 1.4.1. 翻整页
```
Ctrl+f forward
Ctrl+b backward
```

### 1.4.2. 翻半页

```
Ctrl+d down
Ctrl+u up
```

### 1.4.3. 查看文档
`:h:%` 
%代表文件本身

### 1.4.4. find f
<mark style="background: #FF5582A6;">f只能搜索同一行</mark>

### 1.4.5. zz 提升行
![image.png](https://raw.githubusercontent.com/zaggerj/obsidian_picgo/main/obsidian/20231211093101.png)
zz之后
![image.png](https://raw.githubusercontent.com/zaggerj/obsidian_picgo/main/obsidian/20231211093112.png)

### 1.4.6. 寄存器|暂存器
#### 1.4.6.1. vim寄存器

#### 1.4.6.2. 无名寄存器（”“）

Vim 的删除、复制与粘贴命令都会用到众多寄存器中的某一个。我们可以通过给命令加 “{register} 前缀的方式指定要用的寄存器。若不指明， Vim 将缺省使用**无名寄存器(“”)**  
倘若我们没有指定要使用的寄存器， Vim 将缺省使用无名寄存器，它可以用双引号表示为了显式地引用该寄存器，我们得使用两个双引号。例如， “”p，它完全等同于 p 命令。

#### 1.4.6.3. 复制专用寄存器（”0）

当我们使用 y{motion} 命令时，要复制的文本不仅会被拷贝到无名寄存器中，而且也被拷贝到了复制专用寄存器中，后者可用数字 0加以引用。  
复制专用寄存器， 顾名思义， 仅当使用 y{motion} 命令时才会被赋值。 换句话讲，使用 x、 s、c{motion} 以及 d{motion} 命令均不会覆盖该寄存器。如果我们复制了一些文本，可以确信该文本会一直保存于寄存器 0 中，直到我们复制其他文本时才会被覆盖。复制专用寄存器是稳定的，而无名寄存器是易变的。

#### 1.4.6.4. 有名寄存器（”a – “z）

Vim 提供了一组以 26 个英文字母命名的有名寄存器。这意  
味着我们可以剪切（”ad{motion}）、复制（”ay{motion}）或者粘贴（”ap）多达 26 段文本。

#### 1.4.6.5. 只读寄存器

```
"%  当前文件的名称（包含路径）
"#  Name of the alternate file（包含路径）
".  最后一次插入的文本
":  上次执行的 Ex 命令
"/  上次查找的模式
```
#### 1.4.6.6. 系统剪切板

之前我们在vim中复制粘贴的内容，只能在vim中使用。同样的系统中复制粘贴的内容只能在系统其它程序中使用，无法直接粘贴到vim中。我们可以在vim中使用系统剪切板。vim可以使用`+`来访问系统剪切板。例如使用 `"+yy`将内容复制到系统剪切板中，供其他程序使用。

但是在有好的shell工具的加持下，我更喜欢用`<Ctrl+v>`这样的方式直接粘贴一大段文字到vim中。或者配合vim的可视模式，直接使用shell中的快捷键从vim中粘贴选中的内容到系统剪切板
#### 1.4.6.7. gt 切换tab
#### 1.4.6.8. 快速退出vim
1. 按住shift zz保存退出， zq不保存退出，q表示放弃，之所以按住shift，其实是切换大小写
2. 在命令编辑模式下：
	:q 不保存退出
	:q! 不保存强制退出
	:wq 保存退出，w表示写入，不论是否修改，都会更改时间戳
	:x     保存退出，如果内容未改，不会更改时间戳
#### 1.4.6.9. tab window buffer 区别
![image.png](https://raw.githubusercontent.com/zaggerj/obsidian_picgo/main/obsidian/20231211110733.png)

#### 1.4.6.10. 命令模式ctrl+r+‘+‘ 引用系统剪切板
# 2. 相关文章

_摘抄来源，引用出处，参考链接，文档查询_
Page Link::
[vim 从嫌弃到依赖(15)——寄存器 - 知乎](https://zhuanlan.zhihu.com/p/523486683)
[vim寄存器](https://codeleading.com/article/89514035966/)
[vim退出快捷键「建议收藏」 - 全栈程序员必看](https://javaforall.cn/172543.html)
[VIM学习笔记 命令行模式 (Command-line Mode) - 知乎](https://zhuanlan.zhihu.com/p/76531156)