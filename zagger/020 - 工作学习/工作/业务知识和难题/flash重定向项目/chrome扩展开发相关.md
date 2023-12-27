---
alias:
tags: 长青笔记
cdate: 2023-12-27 11:23
uid: 20231227112448
searchterm: "#长青笔记"
banner: "040 - Obsidian/附件/banners/book-banner.gif"
cssclass: noyaml
banner_icon: 💌
banner_x: 0.5
banner_y: 0.38
---

# 1. chrome扩展开发相关

## 1.1. Metadata

Status:: #笔记状态/🌱 发芽
Source Type:: #📥/💭 想法 
Note Type:: #笔记
Topic:: [[00.学习-前端]]
Author:: zagger
Source URL::
Modify:: 2023-12-27 星期三 11:23:32

## 1.2. 长青笔记

_一句话概括这篇笔记的内容_
Summary::

## 1.3. 自我重述

_用自己的话去重述提取的重点内容_

1. 问题：【插件】跟【客户端flash服务】如何交互？
```
第一步：插件  <----终端ip---      guesttool
第二部：终端  <---http://ip:9999/*--->   插件
插件拿到终端IP后，就直接和终端对接了
```
2. 问：有没有可能用其他chrome内核的浏览器 替换nw？答：重定向环境要的是 webview，不是附加了其它界面元素的浏览器
3. 问：我这边应该是不依赖nw的，如果要替换也是他们终端服务这边要修改东西的？答：是

## 1.4. 重点摘抄

_摘抄部分原文后，进行筛选加粗然后对加粗的继续进行筛选荧光笔选出。_

  
1. Manifest：[清单文件格式  |  Manifest  |  Chrome for Developers](https://developer.chrome.com/docs/extensions/reference/manifest?hl=zh-cn#keys)
	1. `"options_page"`：指定 options.html 文件的路径，以将扩展程序用作选项页面。如需了解详情，请参阅[为用户提供选项](https://developer.chrome.com/docs/extensions/develop/ui/options-page?hl=zh-cn)。
	2. 为用户提供选项：[为用户提供选项  |  Extensions  |  Chrome for Developers](https://developer.chrome.com/docs/extensions/develop/ui/options-page?hl=zh-cn)
2. 内容脚本：[内容脚本  |  Extensions  |  Chrome for Developers](https://developer.chrome.com/docs/extensions/develop/concepts/content-scripts?hl=zh-cn)
	1. chrome.runtime，使用 `chrome.runtime` API 可检索 Service Worker，返回有关清单的详情，并监听和响应应用或扩展程序生命周期中的事件。您还可以使用此 API 将网址的相对路径转换为完全限定网址。Runtime API 提供了为扩展程序可以使用的功能的多个领域提供支持的方法： [chrome.runtime  |  API  |  Chrome for Developers](https://developer.chrome.com/docs/extensions/reference/api/runtime?hl=zh-cn#method-connect)
		1. onMessage事件，在扩展程序进程（通过 [`runtime.sendMessage`](https://developer.chrome.com/docs/extensions/reference/api/runtime?hl=zh-cn#method-sendMessage)）或内容脚本（通过 [`tabs.sendMessage`](https://developer.chrome.com/docs/extensions/reference/tabs/?hl=zh-cn#method-sendMessage)）发送消息时触发。：[chrome.runtime  |  API  |  Chrome for Developers](https://developer.chrome.com/docs/extensions/reference/api/runtime?hl=zh-cn#event-onMessage)
	2. chrome.tabs，使用 `chrome.tabs` API 与浏览器的标签页系统进行交互。您可以使用此 API 在浏览器中创建、修改和重新排列标签页。Tabs API 不仅提供操控和管理标签页的功能，还能检测标签页的[语言](https://developer.chrome.com/docs/extensions/reference/api/tabs?hl=zh-cn#method-detectLanguage)、截取[屏幕截图](https://developer.chrome.com/docs/extensions/reference/api/tabs?hl=zh-cn#method-captureVisibleTab)，以及与标签页的内容脚本[通信](https://developer.chrome.com/docs/extensions/reference/api/tabs?hl=zh-cn#method-sendMessage)。
		1. 事件：[chrome.tabs  |  API  |  Chrome for Developers](https://developer.chrome.com/docs/extensions/reference/api/tabs?hl=zh-cn#event)
			1. onActivated：在窗口中的活动标签页发生变化时触发。请注意，在触发此事件时可能未设置标签页的网址，但您可以监听 onUpdated 事件，以便在设置网址时收到通知。
			2. onUpdated：在标签页更新时触发。
			3. onRemoved：在标签页关闭时触发。
	3. webRequest：使用 `chrome.webRequest` API 可以观察和分析流量，以及拦截、屏蔽或修改传输中的请求。
		1. onBeforeSendHeaders：在请求标头可用时，在发送 HTTP 请求之前触发。这可能会发生在 TCP 连接到服务器之后、发送任何 HTTP 数据之前。[chrome.webRequest  |  API  |  Chrome for Developers](https://developer.chrome.com/docs/extensions/reference/api/webRequest?hl=zh-cn#event-onBeforeSendHeaders)
# 2. 相关文章

_摘抄来源，引用出处，参考链接，文档查询_
Page Link::
1. Manifest V3：
[chrome.tabs  |  API  |  Chrome for Developers](https://developer.chrome.com/docs/extensions/reference/api/tabs?hl=zh-cn#method-executeScript)
[扩展程序 / 使用入门  |  Get started  |  Chrome for Developers](https://developer.chrome.com/docs/extensions/get-started?hl=zh-cn)
[Hello World 扩展程序  |  Extensions  |  Chrome for Developers](https://developer.chrome.com/docs/extensions/get-started/tutorial/hello-world?hl=zh-cn)
[扩展程序 Service Worker 简介  |  Extensions  |  Chrome for Developers](https://developer.chrome.com/docs/extensions/develop/concepts/service-workers?hl=zh-cn)



2. Manifest V2：
[extensions/mv2/reference?hl=zh-cn](https://developer.chrome.com/docs/extensions/mv2/reference?hl=zh-cn)

3. [插件说明 | OS-Easy 前端文档](http://192.168.0.161/fedoc/flashredirect/plugin.html)