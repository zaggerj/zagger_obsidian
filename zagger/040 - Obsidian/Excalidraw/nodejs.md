# nodejs

## 自带模块

### http

### path

- 获取路径/文件名/扩展名

	- 获取路径：path.dirname(filepath)
	- 获取文件名：path.basename(filepath)
	- 获取扩展名：path.extname(filepath)

- 获取所在路径

  var path = require('path');
  var filepath = '/tmp/demo/js/test.js';
  
  // 输出：/tmp/demo/js
  console.log( path.dirname(filepath) );
  
  
- 获取文件名

  严格意义上来说，path.basename(filepath) 只是输出路径的最后一部分，并不会判断是否文件名。
  
  
  但大部分时候，我们可以用它来作为简易的“获取文件名“的方法。
  
  
  var path = require('path');
  
  // 输出：test.js
  console.log( path.basename('/tmp/demo/js/test.js') );
  
  // 输出：test
  console.log( path.basename('/tmp/demo/js/test/') );
  
  // 输出：test
  console.log( path.basename('/tmp/demo/js/test') );
  如果只想获取文件名，单不包括文件扩展呢？可以用上第二个参数。
  
  // 输出：test
  console.log( path.basename('/tmp/demo/js/test.js', '.js') );
  
- 获取文件扩展名

  var path = require('path');
  var filepath = '/tmp/demo/js/test.js';
  
  // 输出：.js
  console.log( path.extname(filepath) );
  
  
### url

### fs

- mkdirp

	- mkdirp这是一款在node.js中像mkdir -p一样递归创建目录及其子目录
	- [地址](https://www.cnblogs.com/jiaoshou/p/12187136.html)

	-  mkdirp.sync(path.dirname(targetFile))

- rimraf

	- rimraf.sync(resPath)
	- The UNIX command rm -rf for node
	- [地址](https://github.com/isaacs/rimraf)

- fs.mkdirSync(path[, options])

	- 
	- [地址](http://nodejs.cn/api/fs.html#fs_fs_mkdirsync_path_options)

	- fs.mkdirSync(dirname, { recursive: true }); 要求nodejs在10版本以上才支持recursive配置

### child_process

- 事件
- 四个方法

	- exec

		- exec：调用 shell 来执行命令的。这部分跟「exec」这个词的 UNIX/C 语义刚好相反。
		- 子进程执行的是非node程序，传入一串shell命令，执行后结果以回调的形式返回，与execFile不同的是exec可以直接执行一串shell命令
		- 安全性分析

			- 像exec那样，可以直接执行一段shell是极为不安全的，比如有这么一段shell：
echo hello world;rm -rf

				- 通过exec是可以直接执行的，rm -rf会删除当前目录下的文件。exec正如命令行一样，执行的等级很高，执行后会出现安全性的问题，而execFile不同
				- execFile('echo',['hello','world',';rm -rf'])
在传入参数的同时，会检测传入实参执行的安全性，如果存在安全性问题，会抛出异常。除了execFile外，spawn和fork也都不能直接执行shell，因此安全性较高。

		- 通过exec来实现

			- let cp=require('child_process');
cp.exec('echo hello world',function(err,stdout){
  console.log(stdout);
});
			- 执行这个main.js，结果会输出hello world。我们发现exec的第一个参数，跟shell命令完全相似。

	- execFile

		- execFile：不调用 shell，直接执行命令。这命名不明所以
		- 子进程中执行的是非node程序，提供一组参数后，执行的结果以回调的形式返回。
		- 通过execFile来实现

			- let cp=require('child_process');
cp.execFile('echo',['hello','world'],function(err,stdout){
   console.log(stdout);
});
			- execFile类似于执行了名为echo的应用，然后传入参数。execFlie会在process.env.PATH的路径中依次寻找是否有名为'echo'的应用，找到后就会执行。默认的process.env.PATH路径中包含了'usr/local/bin',而这个'usr/local/bin'目录中就存在了这个名为'echo'的程序，传入hello和world两个参数，执行后返回。

	- fork

		- fork：执行一个新的 nodejs 进程，并且建立一个专用的 IPC 通道。子进程除了 IPC 通道外与父进程无任何瓜葛！命名真是一如既往地误人子弟。默认使用与父进程相同的可执行文件（nodejs 版本），也可以另外指定。
		- 子进程执行的是node程序，提供一组参数后，执行的结果以流的形式返回，与spawn不同，fork生成的子进程只能执行node应用。
		- 在javascript中，在处理大量计算的任务方面，HTML里面通过web work来实现，使得任务脱离了主线程。
在node中使用了一种内置于父进程和子进程之间的通信来处理该问题，降低了大数据运行的压力。node中提供了fork方法，通过fork方法在单独的进程中执行node程序，并且通过父子间的通信，子进程接受父进程的信息，并将执行后的结果返回给父进程。
使用fork方法，可以在父进程和子进程之间开放一个IPC通道，使得不同的node进程间可以进行消息通信。

	- spawn

		- spawn：相当于 Python 的 subprocess，可以指定是否使用 shell。默认不使用 shell。也支持 cwd 啊 env 啊 argv0 啊之类的参数。
		- 子进程中执行的是非node程序，提供一组参数后，执行的结果以流的形式返回。
		- spawn同样是用于执行非node应用，且不能直接执行shell，与execFile相比，spawn执行应用后的结果并不是执行完成后，一次性的输出的，而是以流的形式输出。对于大批量的数据输出，通过流的形式可以介绍内存的使用。

			- 我们用一个文件的排序和去重来举例

				- 上述图片示意图中，首先读取的input.txt文件中有acba未经排序的文字，通过sort程序后可以实现排序功能，输出为aabc，最后通过uniq程序可以去重，得到abc。我们可以用spawn流形式的输入输出来实现上述功能
				- let cp=require('child_process');
let cat=cp.spawn('cat',['input.txt']);
let sort=cp.spawn('sort');
let uniq=cp.spawn('uniq');

cat.stdout.pipe(sort.stdin);
sort.stdout.pipe(uniq.stdin);
uniq.stdout.pipe(process.stdout);
console.log(process.stdout);
				- 执行后，最后的结果将输入到process.stdout中。如果input.txt这个文件较大，那么以流的形式输入输出可以明显减小内存的占用，通过设置缓冲区的形式，减小内存占用的同时也可以提高输入输出的效率。

	- 四个方法的区别

- 文章

	- nodejs中的子进程，深入解析child_process模块和cluster模块

		- [地址](https://segmentfault.com/a/1190000016169207)

### cluster

### stream

- 可写事件
- 可读流事件

## 其他模块

### backbone

### express

### fs-extra

- [地址](https://www.jianshu.com/p/d6990a03d610?utm_campaign=maleskine&utm_content=note&utm_medium=seo_notes&utm_source=recommendation)

- 文件操作相关工具库
fs-extra模块是系统fs模块的扩展，提供了更多便利的 API，并继承了fs模块的 API
- 项目地址：

	- [github(fs-extra)](https://github.com/jprichardson/node-fs-extra)

- 安装：
npm install --save-dev fs-extra
- 使用：
var fse = require('fs-extra')

	- 1. copy 复制文件
copy(src, dest, [option],callback)
	- 2. emptyDir 清空目录
异步:
emptydir()
同步:
emptyDirSync(), emptydirSync()
	- 3. ensureFile 创建文件
确保文件存在。如果被请求的文件的目录不存在,创建这些目录。如果文件已经存在,它不修改。
异步:
createFile()
同步:
createFileSync(),ensureFileSync()
	- 4. ensureDir 创建目录
确保目录的存在。如果目录结构不存在,就创建一个。
**同步: **
ensureDirSync()

### got

- npm install got
- const got = require('got');
(async () => {
    try {
        const response = await got('sindresorhus.com');
        console.log(response.body);
        //=> '<!doctype html> ...'
    } catch (error) {
        console.log(error.response.body);
        //=> 'Internal server error ...'
    }
})();

### env-cmd

- [npm地址](https://www.npmjs.com/package/env-cmd)

- 例子图示：env-cmd自动读取.env.js中的export.modules中的导出的环境变量

## [Koa2](https://blog.poetries.top/node-learning-notes/notes/koa2/-1.0%20koa2%E6%A6%82%E8%A7%88%E7%AF%87.html#%E4%B8%80%E3%80%81%E5%9F%BA%E6%9C%AC%E7%94%A8%E6%B3%95)

一种说法：Koa是从第一个中间件开始执行,遇到 await next() 就进入下一个中间件，一直到执行到最后一个中间件。然后再逆序执行上一个中间件 await next() 后面的代码，一直到第一个中间件 await next() 后面的代码执行完毕才发出响应。



另一种说法：app.use 第一个use的 就是最外层的 最外层的用来try catch 错误比较靠谱


还有一种说法：
多个中间件会形成一个栈结构（middle stack），以"先进后出"（first-in-last-out）的顺序执行
最外层的中间件首先执行。
调用next函数，把执行权交给下一个中间件。
...
最内层的中间件最后执行。
执行结束后，把执行权交回上一层的中间件。
...
最外层的中间件收回执行权之后，执行next函数后面的代码


## npm/npx

npm的m是Management，npx的x可以理解为eXecute。

当执行npx xxx的时候，npx先看xxxz在$PATH里有没有，如果没有，找当前目录的node_modules里有没有，如果还是没有，就安装这个xxx 来执行。

npx也可以理解为少些package.json里一个script而诞生的。

## log工具

### [morgan](https://www.npmjs.com/package/morgan)

## [redis](https://blog.csdn.net/hzlarm/article/details/99432240)

### [service redis-server restart](https://zhuanlan.zhihu.com/p/28101275)

### redis-cli

## nginx配置同域联调

### 安装：apt-get install nginx

### nginx -t 测试配置文件格式是否正确

### 启动nginx

### 重启nginx -s reload

### 停止nginx -s stop

### 代理

## 撸demo

### sina

- 框架：koa2-ejs-jest
存储：mysql-sequelize-连表&多模型
用户认证：session-redis-jwt
线上环境：pm2-nginx-日志

  ￼
  
  ￼
  
  ￼
  
  ￼
  
  ￼
  
  ￼
  
  
  
	- sina项目搭建
	-     npm i koa-generator
	-     koa2 -e sina
	-     npm i
	-     npm i cross-env -D

- nodejs

	- 安装依赖

		- [安装mysql
启动service
查看是否启动了](https://dev.mysql.com/doc/)

			- linux上安装mysql
apt-get install sql-server
service mysql start
			-  ps -ef | grep mysql

		- [npm i -S npm i -D](https://www.cnblogs.com/cina33blogs/p/9210931.html)

		  
		    i 是install 的简写
		  
		  
		  -S就是--save的简写
		  -D就是--save-dev 这样安装的包的名称及版本号就会存在package.json的devDependencies这个里面，而--save会将包的名称及版本号放在dependencies里面。
		  
		  
		  我们在使用npm install 安装模块或插件的时候，有两种命令把他们写入到 package.json 文件里面去，比如：
		  
		  
		  --save-dev
		  
		  
		  --save
		  
		  
		  在 package.json 文件里面提现出来的区别就是，使用 --save-dev 安装的 插件，被写入到 devDependencies 对象里面去，而使用 --save 安装的插件，责被写入到 dependencies 对象里面去。
		  
		  
		  那 package.json 文件里面的 devDependencies  和 dependencies 对象有什么区别呢？
		  
		  
		  devDependencies  里面的插件只用于开发环境，不用于生产环境，而 dependencies  是需要发布到生产环境的。
		  
		  
		- npm install express -S
		- npm install nodemon -D
		- npm install nvm -D
		- npm install nrm -D
		- npm install --save mysql2

			- 安装对应数据库驱动

		- [npm install --save sequelize](http://sequelize是node操作mysql的一款npm包，包含很多特性：数据库模型映射、事务处理、模型属性校验、关联映射等，花了两天时间学习了下基本的一些操作，特别是关联映射部分的操作，包含1:1、1:N、N:N部分，利用express框架实现简单的rest服务。)

			- 基于Promise的ORM(Object Relation Mapping)，支持多种数据库、事务、关联等

	- [mysql](https://www.runoob.com/mysql/mysql-administration.html)

		- 一个报错浪费了本人一天半的时间：
auth_socket 导致 Access denied for user 'root'@'localhost'

			- [update user set plugin="mysql_native_password" where user='root';
](https://blog.csdn.net/weixin_43424368/article/details/109600313)

	- postman

		- [遇到一个问题：
使用body传参时，raw格式时，需要设置格式为json](https://www.cnblogs.com/zzcyeah/p/10341856.html)

### ejs 服务端模板引擎

￼
￼

￼

￼


-         await ctx.reader('index', {title: 'Hollo Koa 2!', msg: '你好'})
        <p><%= msg %></p>
        

### 项目目录整理

## nodejs 断点调试代码

### 1. node --inspect-brk="127.0.0.1:9222" bin/Incremental-patch.js

### 2. edge://inspect/#devices

### 3. 

### 4. 

## multer

## tmp

## po

### PO 是 Portable Object (可移植对象)的缩写形式。

PO文件是面向翻译人员的、提取于源代码的一种资源文件。当软件升级的时候，通过使用gettext软件包处理 PO文件，可以在一定程度上使翻译成果得以继承，减轻翻译人员的负担。

## md5

### linux:md5sum

## NODE_ENV不是内部或外部命令,也不是可运行的程序

### [地址：](https://blog.csdn.net/koufulong/article/details/75270337)

## other

### 自带模块

- http
- path

	- 获取路径/文件名/扩展名

		- 获取路径：path.dirname(filepath)
		- 获取文件名：path.basename(filepath)
		- 获取扩展名：path.extname(filepath)

	- 获取所在路径

	  var path = require('path');
	  var filepath = '/tmp/demo/js/test.js';
	  
	  // 输出：/tmp/demo/js
	  console.log( path.dirname(filepath) );
	  
	  
	- 获取文件名

	  严格意义上来说，path.basename(filepath) 只是输出路径的最后一部分，并不会判断是否文件名。
	  
	  
	  但大部分时候，我们可以用它来作为简易的“获取文件名“的方法。
	  
	  
	  var path = require('path');
	  
	  // 输出：test.js
	  console.log( path.basename('/tmp/demo/js/test.js') );
	  
	  // 输出：test
	  console.log( path.basename('/tmp/demo/js/test/') );
	  
	  // 输出：test
	  console.log( path.basename('/tmp/demo/js/test') );
	  如果只想获取文件名，单不包括文件扩展呢？可以用上第二个参数。
	  
	  // 输出：test
	  console.log( path.basename('/tmp/demo/js/test.js', '.js') );
	  
	- 获取文件扩展名

	  var path = require('path');
	  var filepath = '/tmp/demo/js/test.js';
	  
	  // 输出：.js
	  console.log( path.extname(filepath) );
	  
	  
- url
- fs

	- mkdirp

		- mkdirp这是一款在node.js中像mkdir -p一样递归创建目录及其子目录
		- [地址](https://www.cnblogs.com/jiaoshou/p/12187136.html)

		-  mkdirp.sync(path.dirname(targetFile))

	- rimraf

		- rimraf.sync(resPath)
		- The UNIX command rm -rf for node
		- [地址](https://github.com/isaacs/rimraf)

	- fs.mkdirSync(path[, options])

		- 
		- [地址](http://nodejs.cn/api/fs.html#fs_fs_mkdirsync_path_options)

		- fs.mkdirSync(dirname, { recursive: true }); 要求nodejs在10版本以上才支持recursive配置

- child_process

	- 事件
	- 四个方法

		- exec

			- exec：调用 shell 来执行命令的。这部分跟「exec」这个词的 UNIX/C 语义刚好相反。
			- 子进程执行的是非node程序，传入一串shell命令，执行后结果以回调的形式返回，与execFile不同的是exec可以直接执行一串shell命令
			- 安全性分析

				- 像exec那样，可以直接执行一段shell是极为不安全的，比如有这么一段shell：
echo hello world;rm -rf

					- 通过exec是可以直接执行的，rm -rf会删除当前目录下的文件。exec正如命令行一样，执行的等级很高，执行后会出现安全性的问题，而execFile不同
					- execFile('echo',['hello','world',';rm -rf'])
在传入参数的同时，会检测传入实参执行的安全性，如果存在安全性问题，会抛出异常。除了execFile外，spawn和fork也都不能直接执行shell，因此安全性较高。

			- 通过exec来实现

				- let cp=require('child_process');
cp.exec('echo hello world',function(err,stdout){
  console.log(stdout);
});
				- 执行这个main.js，结果会输出hello world。我们发现exec的第一个参数，跟shell命令完全相似。

		- execFile

			- execFile：不调用 shell，直接执行命令。这命名不明所以
			- 子进程中执行的是非node程序，提供一组参数后，执行的结果以回调的形式返回。
			- 通过execFile来实现

				- let cp=require('child_process');
cp.execFile('echo',['hello','world'],function(err,stdout){
   console.log(stdout);
});
				- execFile类似于执行了名为echo的应用，然后传入参数。execFlie会在process.env.PATH的路径中依次寻找是否有名为'echo'的应用，找到后就会执行。默认的process.env.PATH路径中包含了'usr/local/bin',而这个'usr/local/bin'目录中就存在了这个名为'echo'的程序，传入hello和world两个参数，执行后返回。

		- fork

			- fork：执行一个新的 nodejs 进程，并且建立一个专用的 IPC 通道。子进程除了 IPC 通道外与父进程无任何瓜葛！命名真是一如既往地误人子弟。默认使用与父进程相同的可执行文件（nodejs 版本），也可以另外指定。
			- 子进程执行的是node程序，提供一组参数后，执行的结果以流的形式返回，与spawn不同，fork生成的子进程只能执行node应用。
			- 在javascript中，在处理大量计算的任务方面，HTML里面通过web work来实现，使得任务脱离了主线程。
在node中使用了一种内置于父进程和子进程之间的通信来处理该问题，降低了大数据运行的压力。node中提供了fork方法，通过fork方法在单独的进程中执行node程序，并且通过父子间的通信，子进程接受父进程的信息，并将执行后的结果返回给父进程。
使用fork方法，可以在父进程和子进程之间开放一个IPC通道，使得不同的node进程间可以进行消息通信。

		- spawn

			- spawn：相当于 Python 的 subprocess，可以指定是否使用 shell。默认不使用 shell。也支持 cwd 啊 env 啊 argv0 啊之类的参数。
			- 子进程中执行的是非node程序，提供一组参数后，执行的结果以流的形式返回。
			- spawn同样是用于执行非node应用，且不能直接执行shell，与execFile相比，spawn执行应用后的结果并不是执行完成后，一次性的输出的，而是以流的形式输出。对于大批量的数据输出，通过流的形式可以介绍内存的使用。

				- 我们用一个文件的排序和去重来举例

					- 上述图片示意图中，首先读取的input.txt文件中有acba未经排序的文字，通过sort程序后可以实现排序功能，输出为aabc，最后通过uniq程序可以去重，得到abc。我们可以用spawn流形式的输入输出来实现上述功能
					- let cp=require('child_process');
let cat=cp.spawn('cat',['input.txt']);
let sort=cp.spawn('sort');
let uniq=cp.spawn('uniq');

cat.stdout.pipe(sort.stdin);
sort.stdout.pipe(uniq.stdin);
uniq.stdout.pipe(process.stdout);
console.log(process.stdout);
					- 执行后，最后的结果将输入到process.stdout中。如果input.txt这个文件较大，那么以流的形式输入输出可以明显减小内存的占用，通过设置缓冲区的形式，减小内存占用的同时也可以提高输入输出的效率。

		- 四个方法的区别

	- 文章

		- nodejs中的子进程，深入解析child_process模块和cluster模块

			- [地址](https://segmentfault.com/a/1190000016169207)

- cluster
- stream

	- 可写事件
	- 可读流事件

### 其他模块

- backbone
- express
- fs-extra

	- [地址](https://www.jianshu.com/p/d6990a03d610?utm_campaign=maleskine&utm_content=note&utm_medium=seo_notes&utm_source=recommendation)

	- 文件操作相关工具库
fs-extra模块是系统fs模块的扩展，提供了更多便利的 API，并继承了fs模块的 API
	- 项目地址：

		- [github(fs-extra)](https://github.com/jprichardson/node-fs-extra)

	- 安装：
npm install --save-dev fs-extra
	- 使用：
var fse = require('fs-extra')

		- 1. copy 复制文件
copy(src, dest, [option],callback)
		- 2. emptyDir 清空目录
异步:
emptydir()
同步:
emptyDirSync(), emptydirSync()
		- 3. ensureFile 创建文件
确保文件存在。如果被请求的文件的目录不存在,创建这些目录。如果文件已经存在,它不修改。
异步:
createFile()
同步:
createFileSync(),ensureFileSync()
		- 4. ensureDir 创建目录
确保目录的存在。如果目录结构不存在,就创建一个。
**同步: **
ensureDirSync()

- got

	- npm install got
	- const got = require('got');
(async () => {
    try {
        const response = await got('sindresorhus.com');
        console.log(response.body);
        //=> '<!doctype html> ...'
    } catch (error) {
        console.log(error.response.body);
        //=> 'Internal server error ...'
    }
})();

### [Koa2](https://blog.poetries.top/node-learning-notes/notes/koa2/-1.0%20koa2%E6%A6%82%E8%A7%88%E7%AF%87.html#%E4%B8%80%E3%80%81%E5%9F%BA%E6%9C%AC%E7%94%A8%E6%B3%95)

一种说法：Koa是从第一个中间件开始执行,遇到 await next() 就进入下一个中间件，一直到执行到最后一个中间件。然后再逆序执行上一个中间件 await next() 后面的代码，一直到第一个中间件 await next() 后面的代码执行完毕才发出响应。



另一种说法：app.use 第一个use的 就是最外层的 最外层的用来try catch 错误比较靠谱


还有一种说法：
多个中间件会形成一个栈结构（middle stack），以"先进后出"（first-in-last-out）的顺序执行
最外层的中间件首先执行。
调用next函数，把执行权交给下一个中间件。
...
最内层的中间件最后执行。
执行结束后，把执行权交回上一层的中间件。
...
最外层的中间件收回执行权之后，执行next函数后面的代码


### npm/npx

npm的m是Management，npx的x可以理解为eXecute。

当执行npx xxx的时候，npx先看xxxz在$PATH里有没有，如果没有，找当前目录的node_modules里有没有，如果还是没有，就安装这个xxx 来执行。

npx也可以理解为少些package.json里一个script而诞生的。

### log工具

- [morgan](https://www.npmjs.com/package/morgan)

### [redis](https://blog.csdn.net/hzlarm/article/details/99432240)

- [service redis-server restart](https://zhuanlan.zhihu.com/p/28101275)

- redis-cli

### nginx配置同域联调

- 安装：apt-get install nginx
- nginx -t 测试配置文件格式是否正确
- 启动nginx
- 重启nginx -s reload
- 停止nginx -s stop
- 代理

### 撸demo

- sina

	- 框架：koa2-ejs-jest
存储：mysql-sequelize-连表&多模型
用户认证：session-redis-jwt
线上环境：pm2-nginx-日志

	  ￼
	  
	  ￼
	  
	  ￼
	  
	  ￼
	  
	  ￼
	  
	  ￼
	  
	  
	  
		- sina项目搭建
		-     npm i koa-generator
		-     koa2 -e sina
		-     npm i
		-     npm i cross-env -D

	- nodejs

		- 安装依赖

			- [安装mysql
启动service
查看是否启动了](https://dev.mysql.com/doc/)

				- linux上安装mysql
apt-get install sql-server
service mysql start
				-  ps -ef | grep mysql

			- [npm i -S npm i -D](https://www.cnblogs.com/cina33blogs/p/9210931.html)

			  
			    i 是install 的简写
			  
			  
			  -S就是--save的简写
			  -D就是--save-dev 这样安装的包的名称及版本号就会存在package.json的devDependencies这个里面，而--save会将包的名称及版本号放在dependencies里面。
			  
			  
			  我们在使用npm install 安装模块或插件的时候，有两种命令把他们写入到 package.json 文件里面去，比如：
			  
			  
			  --save-dev
			  
			  
			  --save
			  
			  
			  在 package.json 文件里面提现出来的区别就是，使用 --save-dev 安装的 插件，被写入到 devDependencies 对象里面去，而使用 --save 安装的插件，责被写入到 dependencies 对象里面去。
			  
			  
			  那 package.json 文件里面的 devDependencies  和 dependencies 对象有什么区别呢？
			  
			  
			  devDependencies  里面的插件只用于开发环境，不用于生产环境，而 dependencies  是需要发布到生产环境的。
			  
			  
			- npm install express -S
			- npm install nodemon -D
			- npm install nvm -D
			- npm install nrm -D
			- npm install --save mysql2

				- 安装对应数据库驱动

			- [npm install --save sequelize](http://sequelize是node操作mysql的一款npm包，包含很多特性：数据库模型映射、事务处理、模型属性校验、关联映射等，花了两天时间学习了下基本的一些操作，特别是关联映射部分的操作，包含1:1、1:N、N:N部分，利用express框架实现简单的rest服务。)

				- 基于Promise的ORM(Object Relation Mapping)，支持多种数据库、事务、关联等

		- [mysql](https://www.runoob.com/mysql/mysql-administration.html)

			- 一个报错浪费了本人一天半的时间：
auth_socket 导致 Access denied for user 'root'@'localhost'

				- [update user set plugin="mysql_native_password" where user='root';
](https://blog.csdn.net/weixin_43424368/article/details/109600313)

		- postman

			- [遇到一个问题：
使用body传参时，raw格式时，需要设置格式为json](https://www.cnblogs.com/zzcyeah/p/10341856.html)

- ejs 服务端模板引擎

  ￼
  ￼
  
  ￼
  
  ￼
  
  
	-         await ctx.reader('index', {title: 'Hollo Koa 2!', msg: '你好'})
        <p><%= msg %></p>
        

- 项目目录整理

### nodejs 断点调试代码

- 1. node --inspect-brk="127.0.0.1:9222" bin/Incremental-patch.js
- 2. edge://inspect/#devices
- 3. 
- 4. 

## C语言简介

## libuv

## v8

