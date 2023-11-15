---
created: 2023-11-15T20:54
updated: 2023-11-15T20:54
---
# webpack

## devServer.proxy

### [文章：http-proxy-middleware 源码解读](https://zhuanlan.zhihu.com/p/49259795?from_voters_page=true)

### [Github官方地址](https://github.com/chimurai/http-proxy-middleware#options)

## webpack中使用mockjs的例子

### 手写方式

- 步骤一：

	- 引用mockjs库

- 步骤二：

	- 在devServer的after钩子中配置bindDevServerAfter方法

- 步骤三：

	- bindDevServerAfter做了什么？


		- 1.拦截所有请求
		- 2.请求路径中如结尾带有/自动去掉。

			- substring不含尾

		- 3.realpathname是当前目录拼上./.data文件夹再拼上路径
		- 4.
path.dirname(path)方法返回 path 的目录名
path.basename(path[, ext])方法返回 path 的最后一部分

			- dirname方法
			- basename方法

		- 5.猜测三种路径，判断是否存在，存在的话就调用smartResponse方法

- 步骤四：

	- smartResponse

		- /^\s*\/\//
没明白这个正则到底是干嘛用的，也没有注释说明。

### 使用中间件hm-middleware

- [介绍文章](https://blog.csdn.net/ancaixie6996/article/details/102007410)

- 步骤一：

	- 引用http-mock-middleware

- 步骤二：

	- devServer

		- 其他例子

### ngconsole中的使用方式
http-proxy-middleware中间件进行转发

- mockjs，进行假数据

## webpack中使用http-proxy-middleware，实现通过代理跑devServer的例子

## 入门了解 & 核心概念

## 配置

### devServer.proxy

- 如果你有单独的后端开发服务器 API，并且希望在同域名下发送 API 请求 ，那么代理某些 URL 会很有用。
- object [object, function]
- proxy直接设为一个地址
- 代理的官方文档,devServer.proxy默认使用了http-proxy-middleware

	- [http-proxy-middleware](https://github.com/chimurai/http-proxy-middleware)

## 实战方面

## 优化

## 原理

## [vue-cli脚手架默认配置文件位置](https://blog.csdn.net/zhengjihao/article/details/107074437)

## [webpack4.0-webpack与浏览器缓存问题-10](https://blog.csdn.net/memedadexixaofeifei/article/details/103892548)

## [webpack学习历程 优化使用缓存(一)](https://blog.csdn.net/weixin_44021417/article/details/106765483?utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-2.no_search_link&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-2.no_search_link)

