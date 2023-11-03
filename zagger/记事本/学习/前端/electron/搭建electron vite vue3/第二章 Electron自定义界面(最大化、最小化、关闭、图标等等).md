## 一、介绍 😆 😁 😉

[Electron](https://so.csdn.net/so/search?q=Electron&spm=1001.2101.3001.7020)是一个使用 JavaScript、HTML 和 CSS 构建桌面应用程序的框架。 嵌入 Chromium 和 Node.js 到 二进制的 Electron 允许您保持一个 JavaScript 代码代码库并创建 在Windows上运行的跨平台应用 macOS和Linux——不需要本地开发经验(这段话是来自官网)。

这里我已经搭建好了项目 👉👉👉 [快速搭建Electron+Vite3+Vue3+TypeScript5脚手架](https://blog.csdn.net/qq_19991931/article/details/130429607?spm=1001.2014.3001.5502 "快速搭建Electron+Vite3+Vue3+TypeScript5脚手架")

在没有任何配置的情况下，项目启动以后会自己带着logo、title、最大化最小化关闭以及工具栏。这些都是可以通过配置去自定义的。原项目启动的UI如下

![](https://img-blog.csdnimg.cn/e232ff644bfe4f97bf65bc5fb95b2253.png)

## 二、去掉Electron自带的导航 😝 😝 😝

修改Electron下的main.ts文件，修改完成以后重新启动自带的导航就不会在显示了。

![](https://img-blog.csdnimg.cn/c085e8a9df234964964557aa46c48a55.jpeg)