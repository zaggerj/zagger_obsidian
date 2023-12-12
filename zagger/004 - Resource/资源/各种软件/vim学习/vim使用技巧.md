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
以下是一些常用的 Vim 暂存器及其用途：

1. `"a` 到 `"z`：这些是命名暂存器，用于存储文本。可以使用 `"ay` 将选中的文本复制到暂存器 `a` 中，然后使用 `"ap` 将暂存器 `a` 中的内容粘贴到光标位置。
    
2. `"0`：这是复制暂存器，用于存储最近复制的文本。当你使用 `y` 命令或者 `"ay` 将文本复制到暂存器时，它将存储在 `"0` 中。可以使用 `"0p` 将最近复制的文本粘贴到光标位置。
    
3. `"+`：这是系统剪贴板暂存器。可以使用 `"+y` 将选中的文本复制到系统剪贴板中，然后使用 `"+p` 将剪贴板中的内容粘贴到光标位置。
    
4. `"*`：这是与系统剪贴板关联的暂存器。在大多数情况下，它与 `"+` 暂存器相同。可以使用 `"*y` 将选中的文本复制到与系统剪贴板关联的暂存器中，然后使用 `"*p` 将其粘贴到光标位置。
    
5. `"_`：这是黑洞暂存器。当你不想保留复制的内容时，可以将其存储到黑洞暂存器中。例如，使用 `"_dd` 删除一行而不将其存储到任何暂存器中。
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

##### 1.4.6.9.1. tab相关
tab之于window 如果window之于buffer, tab和window都只是布局而已,真正影响到文件保存的只有buffer, 至少会有一个window,但到tab可有可无
1. **跳转到指定的选项卡tab**
- `tab1`跳转到第1个tab
- `tab2`跳转到第2个tab
- `tab3`跳转到第3个tab
- `tab5`跳转到第5个tab

2. **移动选项卡位置**
- `:-tabmove` 当前选项卡左移动
- `:+tabmove` 当前选项卡右移动
- `:0tabmove` 当前选项卡移动到最左边
- `:tabmove 0` 当前选项卡移动到最左边
- 这样的选项卡很方便打开一个帮助
    - `:tab help gt`

3. **按照选项卡打开文件**
- `vim -p file1.js file2.js file3.js`
- 对比原来按照`window`打开文件
    - `vim -o file1.js file2.js file3.js`
    - `vim -O file1.js file2.js file3.js`

![图片描述](https://www.learnfk.com/storage/vim/6490f5e11cdda4d30eb3f630155ff2d8.jpg)

- `:tabn`和`:tabp`可以切换标签页
- 更快速的方法是`gt`、`gT`、`1gt`

#### 1.4.6.10. 容器汇总

- vim命令打开的参数对应一个列表 - `arguments`参数列表
    - 列表 - `:args`
    - 添加 - `:arga`
    - 删除 - `:argd`
    - 执行命令 - `:argdo`
- 打开的文件缓存对应一个列表 - `buffers`缓存列表
    - 列表 - `:ls`
    - 添加 - `:e .`
    - 切换 - `:b1`
    - 关闭 - `:bd`
    - 执行命令 - `:bufdo`
- tab选项卡对应一个列表 - `tabs`选项卡列表
    - 列表 - `:tabs`
    - 打开 - `:tabnew`
    - 切换 - gt、gT
    - 关闭 - `:tabc`
    - 执行命令 - `:tabdo`
- tab选项卡中的窗口对应一个列表 - `windows`窗口列表
    - 列表 - `:sp`、`:vsp`
    - 打开 - ctrl+w后加hjkl
    - 关闭 - `:q`
    - 执行命令 - `:windo`
```vim
:tabnew filename #打开一个tab 
:tabedit #当前window 创建tab
:tabe 新建一个tab用来打开一个文件
:tabs用来查看tab列表
:gt 切换下一个tab
:gT切换上一个tab
:ngt切换到对应的tab，n是编号
```
#### 1.4.6.11. 使用全键盘方式跳入跳出超链接

- 是 ctrl+] 就可以**跳入链接**
- ctrl+o 可以**跳出链接**，回到原位置 `older position`
- `:h ctrl-c` 就是帮助我们查找一下 `ctrl-c` 快捷键究竟做些什么
- `:h ctrl-g`
#### 1.4.6.12. 命令模式c+r+‘+‘ 引用系统剪切板
#### 1.4.6.13. vim键盘图
![5a19c121fda7a831559898ae84a9f8e8.gif](https://raw.githubusercontent.com/zaggerj/obsidian_picgo/main/obsidian/5a19c121fda7a831559898ae84a9f8e8.gif)

#### 1.4.6.14. set noacd 取消 设置当前目录自动跟随当前文件
#### 1.4.6.15. <C+w>, <S+t> 提升窗口到单独的tab
#### 1.4.6.16. e # 快速用buffer打开上一个文件
#### 1.4.6.17. vs # 快速用分屏打开上一个文件
# 2. 相关文章

_摘抄来源，引用出处，参考链接，文档查询_
Page Link::
1. vim寄存器相关：
	1. [vim 从嫌弃到依赖(15)——寄存器 - 知乎](https://zhuanlan.zhihu.com/p/523486683)
	2. vim寄存器：[vim寄存器](https://codeleading.com/article/89514035966/)
2. vim快捷键：[vim退出快捷键「建议收藏」 - 全栈程序员必看](https://javaforall.cn/172543.html)
3. Command-line Mode [VIM学习笔记 命令行模式 (Command-line Mode) - 知乎](https://zhuanlan.zhihu.com/p/76531156)
4. vim buffer、tab、window
	1. [29.vim高效使用方法之buffer、window和tab\_vim buffer-CSDN博客](https://blog.csdn.net/a464057216/article/details/51523860)
	2. [vim之buffer/window/tab - 马肯尼煤牙巴骨 - 博客园](https://www.cnblogs.com/nocanstillbb/p/16375043.html)
	3. [[Vim] Tab，Window，Buffer 概念和操作-CSDN博客](https://blog.csdn.net/weixin_43162745/article/details/88732197)
5. 命令集合：
	1. [vim命令大全，非常详细，强烈建议收藏！ - 知乎](https://zhuanlan.zhihu.com/p/628940845)
	2. [Vim 全局命令global详解 - 无涯教程网](https://www.learnfk.com/vim/vim-tutorial-global-command-global.html)
6. vim杂项：
	1. [Vim 概述 - 知乎](https://zhuanlan.zhihu.com/p/648077001)
	2. [vim内置终端使用分享 - 知乎](https://zhuanlan.zhihu.com/p/596644062)
	3. [拥抱 Vim：这些快捷键让你爱上 Vim 编辑器](https://baijiahao.baidu.com/s?id=1760966208530497278&wfr=spider&for=pc)
	4. [vim操作教程，看这一篇绝对足够啦\~\_vim 显示标记-CSDN博客](https://blog.csdn.net/weixin_42639919/article/details/133626489)
	5. [精通 vim 你应该理解的几个名词 - 知乎](https://zhuanlan.zhihu.com/p/96801314/)
	6. [maps.vim](https://github.com/LinHQ1999/nvim-config/blob/office/mysettings/maps.vim)
	7. [Vim 使用帮助详解 - 无涯教程网](https://www.learnfk.com/vim/vim-tutorial-use-help.html)
	8. ![](https://raw.githubusercontent.com/zaggerj/obsidian_picgo/main/obsidian/5a19c121fda7a831559898ae84a9f8e8.gif)
	9. [Vim 标签页 tab详解 - 无涯教程网](https://www.learnfk.com/vim/vim-tutorial-tab-tab.html)
	10. [Vim实践与学习-08配置相关 - 知乎](https://zhuanlan.zhihu.com/p/103461924)
	11. [Vim 配置入门 - 阮一峰的网络日志](https://www.ruanyifeng.com/blog/2018/09/vimrc.html)
	12. [vim超实用指南，收藏这一篇就够了！ - 知乎](https://zhuanlan.zhihu.com/p/467661880)