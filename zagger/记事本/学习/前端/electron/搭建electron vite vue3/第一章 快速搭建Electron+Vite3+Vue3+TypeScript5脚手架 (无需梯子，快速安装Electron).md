# 搭建Vite+Vue3+TypeScript项目
## 一、Vite 官网
1. [Home | Vite中文网 (vitejs.cn)](https://vitejs.cn/)
2. [Vite | 下一代的前端工具链 (vitejs.dev)](https://cn.vitejs.dev/)
3. ![[Pasted image 20231103092804.png]]
4. `pnpm create vite`
5. 依次填写项目名称、选择 vue，选择 typescript
6. ![[Pasted image 20231103093229.png]]
7. ![[Pasted image 20231103093246.png]]
8. ![[Pasted image 20231103093256.png]]
9. 然后进入目录，安装依赖，尝试启动服务
   ```js
   cd my_desk_app
  pnpm install
  pnpm run dev
```
## 安装 Electron 相关依赖
如果你自己安装过 Electron 的相关依赖，想必你一定经历过失败、失败、失败。

这里需要借助一个[网站检测服务器响应速度](https://ping.chinaz.com/ "网站检测服务器响应速度")，然后拿到最快响应的ip进行本地配置加快我们的域名解析。

通过该工具可以多个地点Ping服务器以检测服务器响应速度。检查github.com。我都选择国内的，看自己想法选择啊。选择之前自己在本地**ping**一下，通了的话就能使用。

![](https://img-blog.csdnimg.cn/9ed9132c4faf47438a7183e4ce389b92.png)

![](https://img-blog.csdnimg.cn/1626f5c9cac440cbaa23ad322de8c75f.png)

修改 C:\Windows\System32\drivers\etc\hosts

![](https://img-blog.csdnimg.cn/1c0cbdf0d02b4e5eadc943c74c189936.png)

```bash
20.27.177.113 github.com
```
如果设置执行 yarn 出现 RequestError: connect ETIMEDOUT ***.***.***.***:443就更改一下 electron 安装源

```bash
yarn config set electron_mirror https://npmmirror.com/mirrors/electron/
```

安装electron依赖 👇 👇 👇 👇

```bash
yarn add -D electron electron-builder
```

根据官网提供的文档,需要创建一个BrowserWindow装载vite项目,你也可以写一个html页面。 这里我们启动vite项目以后就会产生一个连接，正好把它装载到 BrowserWindow中。

![](https://img-blog.csdnimg.cn/c2be86c0125a42b6b4515d6a348b201c.png)

![](https://img-blog.csdnimg.cn/f760efb4daf944b7a10020c17b701ed0.png)

因为src下面存放的是我们的vite项目，所以在根目录下创建一个electron文件夹，避免后续文件多了以后混淆起来，现在创建这个main.ts就是我们electron的入口文件。名字随便起，知道是干啥的就行。

项目根目录下 electron 文件夹下创建 main.ts 文件

```TypeScript
const { app, BrowserWindow } = require('electron')
let win
/**
* @Description: electron程序入口
* @Author: Etc.End
* @Copyright: TigerSong
* @CreationDate 2023-05-20 14:39:26
*/
const createWindow = () => {
	win = new BrowserWindow({
		width: 1200,
		height: 800,
		minWidth: 1200,
		minHeight: 800,
		center: true,
		skipTaskbar: false,
		transparent: false,
		webPreferences: {
		contextIsolation: false,
		webSecurity: false,
	}
	})
	win.loadURL(
	'http://localhost:5173/'
	)
	win.webContents.openDevTools()
}
app.whenReady().then(() => {
	createWindow()
})
/**
* @Description: 限制只能打开一个页面
* @CreationDate 2023-05-20 14:35:52
*/
const gotTheLock = app.requestSingleInstanceLock()
if (!gotTheLock) {
	app.quit()
} else {
	app.on('second-instance', (event, commandLine, workingDirectory) => {
	if (win) {
	if (win.isMinimized()) win.restore()
	win.focus()
	}
	})
}
app.on('window-all-closed', function () {
if(process.platform !== 'darwin') app.quit()
})

```

接着修改package.json文件