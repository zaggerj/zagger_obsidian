---
created: 2023-11-15T20:48
updated: 2023-11-15T20:48
---
# oseasy

## vdi

### 服务器查看log

tailf /etc/thor/log/thorconsole.log 看log


ystemctl restart openstack-nova-compute 重启服务


- tailf /etc/thor/log/thorconsole.log
tail -f -n 10 /etc/thor/log/thorconsole.log
- systemctl restart thor-supervisor
- du -sh *

### // 开发时 admin/views 重定向到 views目录的结果，保证开发时，本地代码可以跑起来。
        app.get(/^\/admin\/views\//, function (req, resp) {
            resp.redirect(req.url.replace("/admin/", "/"));
        });

### ngconsole

# 常用命令

## 打增量包

用途：需要打补丁包时，一般仅仅打增量包就够了，打全量包有百害而无一利。

原理：打增量包就是把变动的文件集合起来，因此核心在于如何获取变更的文件列表。在 git 里面，获取文件变更列表可以通过两种方式完成，这取决于你的实际情况。

### build 后提交前获取变更列表

此时，变更的文件列表可以使用 `git status` 命令查看到，因此获取文件列表很简单：

```bash
git status -s
```

### build 后提交后获取变更列表

这种方式更常见，通用性也更强，因为可能打了不止一次包，如何找到从开始到现在的所有的变更文件呢？使用 `git diff` 命令

```bash
# 假设首次提交的 COMMIT ID 为 3a7bb6d0a7580eaf3f0c3ddc483dc717c66d01cc
# 则从 3a7bb6d0a7580eaf3f0c3ddc483dc717c66d01cc 到分支当前状态，所有的文件变更列表为：
git diff 3a7bb6d0a7580eaf3f0c3ddc483dc717c66d01cc.. --name-status
```

这条命令获取指定的 git 提交范围（revision range），并计算差异，最终打印变更类型和文件名（--name-status）

变更的文件列表一般长这样：

```plain
M built/forget.map
M built/index.js
M built/index.map
M built/init.map
M built/spice.js
M built/spice.map
M built/split.map
M built/ssh.map
M built/weblogin.map
M resources/arm/lang.json
M resources/en/lang.json
M resources/vpc/lang.json
M resources/zh-cn/lang.json
M resources/zh-tw/lang.json
```

可以看到，变更列表由两列组成，第一列就是变更类型，第二列是文件路径，文件列表就是第二列的全部内容。在 git bash 里面可以使用 awk 命令获取这个列表：

```bash
git diff 3a7bb6d0a7580eaf3f0c3ddc483dc717c66d01cc.. --name-status | awk -e '{print $2}'
```

输出：

```plain
built/forget.map
built/index.js
built/index.map
built/init.map
built/spice.js
built/spice.map
built/split.map
built/ssh.map
built/weblogin.map
resources/arm/lang.json
resources/en/lang.json
resources/vpc/lang.json
resources/zh-cn/lang.json
resources/zh-tw/lang.json
```

之后将文件列表传递给 `git archive` 命令即可完成打包压缩：

```bash
git diff 3a7bb6d0a7580eaf3f0c3ddc483dc717c66d01cc.. --name-status | awk -e '{print $2}' | xargs git archive -o update.zip HEAD
```

某些情况，`git archive` 可能仅仅打了一部分文件，这时可以使用 bash 数组来存储文件列表，然后打包：

```bash
FILES=($(git diff 3a7bb6d0a7580eaf3f0c3ddc483dc717c66d01cc.. --name-status | awk -e '{print $2}'))
# 此处为 bash 数组特定用法，不可修改半个字符
git archive -o update.zip HEAD "${FILES[@]}"
```

## 打包翻译资源给产品经理

用途：需要做繁体、英文版时，产品经理会要求前端提供目前的翻译资源，然后交由国际部进行翻译，翻译完成后，由前端整合进代码里面

命令（需要提前 build）

```bash
cd ngconsole
mkdir -p out/{en,zh-cn,zh-tw,vpc}
for dir in en zh-cn zh-tw vpc; do
 for file in code.json lang.json; do
 # 也可以使用 node 格式化
 # node -e 'process.stdout.write(JSON.stringify(fs.readFileSync(process.argv[1], "utf-8"), null, 4))' resources/$dir/$file > out/$dir/$file
 jq -r '.' resources/$dir/$file > out/$dir/$file
 done
done
cd out
zip -r ../语言包.zip .
cd ..
rm -rf out
```

提交资源给产品经理时，将如下说明一并发送，确保收到的资源被正确的修改。

翻译说明：

1. .json 是一种键值一一对应的纯文本文件，每行的格式为："键": "值"
2. 翻译时，仅仅翻译值的部分就可以了，如下面绿色部分：

 ```json
 {
 "101": "资源池未找到",
 "102": "资源池创建失败",
 "103": "资源池更新失败",
 "104": "资源池销毁失败",
 "105": "创建云PC HA策略名称相同",
 "106": "创建云PC HA策略必须有云PC",
 "分布式存储": "分布式存储",
 "新增分布式存储": "新增分布式存储",
 "修改分布式存储": "修改分布式存储",
 "删除分布式存储": "删除分布式存储",
 "分布式存储名": "分布式存储名",
 }
 ```

3. 以下情况无需翻译：
 * &lt;li&gt; 即 小于号和大于号包裹的区域
 * <https://www.baidu.com> 即 网址无需翻译
 * {{0} } 双大括号直接忽略
 * `&xxxx;` 形如这种格式的都忽略，常见的有 `&nbsp`;
4. 推荐使用 notepad++ 等支持高亮特性编辑器打开.json文件进行编辑


- 跑arm版本的服务器时，需要本地起https服务

	- https://127.0.0.1:8081
	- webpack.devServer.https:true
	- nvm use v8
	- node_modules/spdy-transport/lib/spdy-transport/priority.js 中报错的一行注释掉

- [input type=number禁止输入小数如何实现](https://www.php.cn/js-tutorial-379946.html)

	- 正则手动替换小数点
$('#number').on('keyup', function () {
    if (!/^\d+$/.test(this.value)) {
         this.value='';
    }
})

- [awk](https://www.cnblogs.com/ggjucheng/archive/2013/01/13/2858470.html)

	- 统计文件夹下文件占用的字节数（不包括子目录）

		- ls -l |awk 'BEGIN {size=0;} {size=size+$5;} END{print "[end]size is ", size/1024/1024,"M"}' 

	- git diff a8a0456a2f3a2d24e69cd6aa8a5a0ce46845a93d.. --name-status | gawk -e '{print $2}'

		- 从某个提交到现在有多少个文件变更，并输出第二列

	- [git archive](https://www.jianshu.com/p/98fa58073554)

		- git archive --format tar.gz --output "./output.tar.gz" master mydir mydir2  

			- 打包master下的mydir mydir2目录

- 找到nw进程的路径-从而找到nw资源的名称

	- linux：
ps -eo cmd|grep [n]w|tail -1|awk '{print $2}'
	- macos：
ps -eo command | grep '[n]w' | awk '{print $2}'

- [jq](https://blog.csdn.net/qq_26502245/article/details/100191694)

	- ibrew install jq
	- cat json.txt | jq '.'

		- 最简单的jq程序是表达式"."，它不改变输入，但可以将其优美地输出，便于阅读和理解。

	- cat json.txt | jq '.[0]'

		- 输出列表中的第一个元素，可以使用[index]

	- cat json.txt | jq '.[0] | {name:.name,city:.address.city}'

		- {
  "name": "站长工具",
  "city": "厦门"
}

	- cat json.txt | jq '.[0] | {name:.name,city:.address.city}'
	- node -e 'process.stdout.write(JSON.stringify(fs.readFileSync(process.argv[1], "utf-8"), null, 4))' resources/$dir/$file > out/$dir/$file

### (id: (\d+),)
id: $2, \n order: $2,

### note 记事 一个便签一条

- fzf
- vim

	- c-f 查找 多个关键词 先文件名 后文件内容

- ranger

	- c-f查找当前文件夹下的文件

### 客户端业务流程图

- VDI客户端

	- 操作系统

		- 底层：接口服务

			- http请求

		- 客户端程序：c写的

			- nw/webview

				- 资源：new-vdi-client项目，客户端界面
				- spice远程连接界面

				  界面里面就是虚拟机内的操作系统界面
				  
				- flash视频播放界面

				  此界面与虚拟机内的比方界面无缝重合
				  
- VDI服务器

	- 主动推送服务器虚拟机准备好了

- flash重定向

	- [flash前端代码](http://172.16.203.254/huangzijie/flash/tree/master)

		- 排查下log，目录：nw_flash/logs/access.log 查看当天的日志

	- [flash插件](http://172.16.203.254/zhangyao/newflashrediredt/tree/master)

		- cs.js

		  前景页面
		  此页面即 src/js/cs.js。
		  
		  当它出于活动状态时，它做了这么几件事情：
		  
		  每隔 1 秒监听一次浏览器窗口位置是否发生了变化，如果变化则发送给背景页面
		  监听浏览器窗口缩放事件，缩放时发送消息给背景页面
		  监听浏览器页面可见性事件，变化时发送消息给背景页面，临时停止此 tab 页的播放
		  
		  
		- core.js

		  背景页面
		  背景页面的概念参考百度文档。
		  
		  背景页面是常驻内存的，它需要为白名单网址提供重定向并保存当前重定向信息。
		  
		  所有的重定向逻辑都在 src/js/core.js 里面，它做了这样几件事：
		  
		  监听来自页面的 viewport-change 事件，并发送给客户端 flash 服务
		  阻止白名单网站的 .swf 文件请求，这样是为了禁用 flash 播放器
		  监听浏览器激活 tab 页变化事件
		  监听浏览器 tab 页更新事件
		  监听浏览器 tab 页关闭事件
		  重定向的核心逻辑就在 tab 页的 3 个事件里面，总的来说就这么几条：
		  
		  打开的时候开始播放
		  关闭的时候停止播放
		  切换 tab 页的时候，前一个 tab 页临时停止播放，当前 tab 页开始播放
		  当一个 tab 页在白名单里面时，就会开始播放，播放时插件会将 src/js/cs.js 注入到当前 tab 页，注入的目的是为了捕获浏览器窗口移动或者缩放。
		  
		  
		  
	- nw
	- linux命令

		- 联调客户端常用的命令

		  1. top查看终端资源
		  2.netstat -a查看网络连接
		  3.ctrl+alt+f6切换终端命令行
		  4.alt+f1切换图形界面
		  5.Ctrl+alt+u在终端程序中打开terminal
		  6.ps -ef|grep nw查看nw进程
		  7.ssh -L 127.0.0.1:9222:127.0.0.1:9222 root@ip
		  
		- 遇到的问题

		  macos上面nw不显示地址栏的话，
		  需要在命令行运行nw，右键nw，显示内容，显示内容，然后里面有个content：路径+--url=传递地址参数，地址为：nwjs：/Users/huangzijie/Downloads/nwjs-sdk-v0.44.0-osx-x64/nwjs.app/Contents/MacOS/nwjs --url=https://www.iqiyi.com/v_260uudpmizo.html
		  
- linux端快捷方式

	- ctrl+alt+f6
alt+f2

- 客户端可以设置端类型

	- localStorage.client_type=3 设置为安卓端 这样的话就可以使用http请求，从而使用假数据

- 客户端翻译需要在vue的this上放_:i18n

	- 这样在dom上面才可以进行_("str_key")进行翻译

- 打增量包

  常用命令
  
  打增量包
  
  
  用途：需要打补丁包时，一般仅仅打增量包就够了，打全量包有百害而无一利。
  
  
  原理：打增量包就是把变动的文件集合起来，因此核心在于如何获取变更的文件列表。在 git 里面，获取文件变更列表可以通过两种方式完成，这取决于你的实际情况。
  
  
  build 后提交前获取变更列表
  
  
  此时，变更的文件列表可以使用 git status 命令查看到，因此获取文件列表很简单：
  
  git status -s
  
  build 后提交后获取变更列表
  
  
  这种方式更常见，通用性也更强，因为可能打了不止一次包，如何找到从开始到现在的所有的变更文件呢？使用 git diff 命令
  
  # 假设首次提交的 COMMIT ID 为 3a7bb6d0a7580eaf3f0c3ddc483dc717c66d01cc
  # 则从 3a7bb6d0a7580eaf3f0c3ddc483dc717c66d01cc 到分支当前状态，所有的文件变更列表为：
  git diff 3a7bb6d0a7580eaf3f0c3ddc483dc717c66d01cc.. --name-status
  
  这条命令获取指定的 git 提交范围（revision range），并计算差异，最终打印变更类型和文件名（--name-status）
  
  
  变更的文件列表一般长这样：
  
  M       built/forget.map
  M       built/index.js
  M       built/index.map
  M       built/init.map
  M       built/spice.js
  M       built/spice.map
  M       built/split.map
  M       built/ssh.map
  M       built/weblogin.map
  M       resources/arm/lang.json
  M       resources/en/lang.json
  M       resources/vpc/lang.json
  M       resources/zh-cn/lang.json
  M       resources/zh-tw/lang.json
  
  可以看到，变更列表由两列组成，第一列就是变更类型，第二列是文件路径，文件列表就是第二列的全部内容。在 git bash 里面可以使用 awk 命令获取这个列表：
  
  git diff 3a7bb6d0a7580eaf3f0c3ddc483dc717c66d01cc.. --name-status | awk -e '{print $2}'
  
  输出：
  
  built/forget.map
  built/index.js
  built/index.map
  built/init.map
  built/spice.js
  built/spice.map
  built/split.map
  built/ssh.map
  built/weblogin.map
  resources/arm/lang.json
  resources/en/lang.json
  resources/vpc/lang.json
  resources/zh-cn/lang.json
  resources/zh-tw/lang.json
  
  之后将文件列表传递给 git archive 命令即可完成打包压缩：
  
  git diff 3a7bb6d0a7580eaf3f0c3ddc483dc717c66d01cc.. --name-status | awk -e '{print $2}' | xargs git archive -o update.zip HEAD
  
  某些情况，git archive 可能仅仅打了一部分文件，这时可以使用 bash 数组来存储文件列表，然后打包：
  
  FILES=($(git diff 3a7bb6d0a7580eaf3f0c3ddc483dc717c66d01cc.. --name-status | awk -e '{print $2}'))
  # 此处为 bash 数组特定用法，不可修改半个字符
  git archive -o update.zip HEAD "${FILES[@]}"
  
  
### Ubuntu下图形界面与控制台终端之间切换的快捷键

- 图形界面——>控制台终端：Ctrl+Alt+F1/F2/F3/F4/F5/F6;

控制台终端——>图形界面：Alt+F7 或者Ctrl+Alt+T



在Linux中控制台、终端及Shell命令窗口都是一回事

### [接口文档showdoc](http://192.168.0.161:4999/web/#/9?page_id=109)

### [公司论坛利用js快捷提交](http://college.os-easy.com/newbbs/#/postdetail?id=9205b8d4-b3ba-41c5-9bfc-eb2dab15541c)

(function(s){let el=document.querySelector("textarea");while(!el.__vue__){el=el.parentElement;}let x=el.__vue__;x.commentTxt=s;x.publishComment()})("拍这张照片的时候脑子都被震懵了！");

let el=document.querySelector("textarea");while(!el.__vue__){el=el.parentElement;}

el.__vue__

el.__vue__.commentTxt="123"

el.__vue__.publishComment()

### 模板遮罩逻辑梳理

- enable字段决定了是否开启了定时任务
- 开启了的，显示遮罩
- 取出时间参数，解析时间
- 进行读秒

### [Git操作中crlf和lf冲突问题](https://blog.csdn.net/aojianzhong5810/article/details/101851263?utm_medium=distribute.pc_relevant.none-task-blog-baidujs_title-0&spm=1001.2101.3001.4242)

- 1、编辑器统一

a. 修改git全局配置，禁止git自动将lf转换成crlf, 命令：

git config --global core.autocrlf false
b. 修改编辑器的用户配置，例如vscode

"files.eol": "\n", // 文件换行使用lf方式
- 2、git方式统一

git提交的时候，文件中的换行符必须是LF，如果不是不能提交。

# 提交时转换为LF，检出时不转换
git config --global core.autocrlf input

# 拒绝提交包含混合换行符的文件
git config --global core.safecrlf true
- 3、EditorConfig

主流编辑器都支持EditorConfig，配置end_of_line后，你编辑的代码会自动转化为对应的换行符。当然你需要将autocrlf关闭，防止再次被转换成其他格式，

# 取值包括 crlf,lf,cr
end_of_line = lf

# 提交检出均不转换
git config --global core.autocrlf false

- 4、prettier

prettier是目前非常流行的代码格式化工具，提供了endOfLine来支持格式化换行符。

{
  // ...
  "endOfLine" : "lf"
  // ...
}
# 提交检出均不转换
git config --global core.autocrlf false
- 因为我们现有的项目都已经支持prettier，自然就使用了【husky+lint-staged+prettier】的方式，来支持所有代码格式化成 lf 换行符。

转载于:https://www.cnblogs.com/dahe1989/p/10784581.html

相关资源：...+git合并分支解决冲突及详解步骤_idea合并git分支,idea操作git...

### 5.3.0-vpc-arm/x86翻译问题

### eslint

### 后端直接给svg字符串，带数据的那种

- 标签直接转为dom元素，然后append到父元素中去

	-  function parseDom(arg) {
　　 var objE = document.createElement("div");
　　 objE.innerHTML = arg;
　　 return objE.childNodes;
};
	- et str='<h1>Interesting</h1>';
let parser = new DOMParser();
let doc = parser.parseFromString(str, "text/xml");
let node = doc.getElementsByTagName('h1')[0];
$('#test')[0].append(node);

- 如何将普通字符串转化为dom节点插入页面
- [地址](https://www.iteye.com/blog/zha-zi-1931474)

- DOMParser

	- [地址](https://www.w3school.com.cn/xmldom/dom_domparser.asp)

	- [地址2](https://blog.csdn.net/lu92649264/article/details/113877817)

### webpack熟悉下

### vue快速熟悉下

### 二进制熟悉下

### 原生js熟悉下

### 上传下载

## voi

### voi桌面

- 问题

	- 1.voi个人桌面新增-设置关联账号弹窗-取消时报错，取消按钮时，也同样传递的是all

## 打印机页面结构

### 状态显示：保存中，正在恢复，驱动盘状态载入中

### 恢复按钮

- onClickRecover

### 保存按钮

- onClickManage

### 导入按钮

- onClickUploadPrinter

### 删除按钮

- onClickDel

### 配合导入按钮的进度条展示区域

### 自动更新复选框

### 然后就是表格主体了

- 编辑打印机驱动
- 创建副本
- 编辑配置文件
- 查看详情

## 驱动中心

### 状态显示：正常，合并中，错误，正在恢复

### 恢复按钮

- onClickRecover

### 保存按钮

- onClickManage

### 导入按钮

- onClickUploadPrinter

### 删除按钮

- onClickDel

### 配合导入按钮的进度条展示区域

### 自动更新复选框

### 然后就是表格主体了

- 编辑操作

