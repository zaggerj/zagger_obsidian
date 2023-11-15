---
created: 2023-11-15T20:48
updated: 2023-11-15T20:48
---
# linux环境

## linux 基础概念

### [linux入门概念](https://mp.weixin.qq.com/s/-cYSuXpxZ_mmhQQayOIiiQ)

- unix

	- 开源的“操作系统”，作为一个底部框架，有很多孩子，比方说：GNU，BSD

		- 苹果把BSD更改加强编程macos
		- 安卓

- linux

	- 发行版 ：从linux加改装之后发布到网上
manjaro linux

- linux中一切都是文件
- 文件系统都是大体相同的

	- bin：binary，存放最常用命令；

		- 可执行文件，程序存在的地方

	- boot：启动Linux的核心文件；

		- 系统阅读并决定怎么启动系统

	- dev：device，用于存放设备文件

		- 硬件：鼠标，事件，终端，input，各种硬件配置

	- etc：etcetera，and so on，存放各种配置文件

		- 放系统配置文件,是全局的，需要管理员权限才可以更改。pacman.conf软件管理器的配置文件
		- etc

	- home：用户主目录

		- 家目录，david用户，下的所有文件，全是用户所有的文件，照片，视频，个人的配置文件，不同用户互相隔离。.vim,.bashrc

	- lib

		- 系统最基本的动态链接共享库；

	- lib64
	- mnt：mount，一般是空的，用来临时挂载别的文件系统

		- 加载后，会在mnt里多出相应设备的目录。是系统临时用的挂载点。uPan或者新的硬盘挂载，可以手动装在
		- 可直接理解为“挂载” 挂接光驱、USB设备的目录

	- proc：process，虚拟目录，是内存的映射；

		- 所有的进程，htop，查看所有进程文件，比方4428，不是所有文件都写在硬盘上了，只是表现为一个文件，这样的话，大家都可以更改和配置。
		- 例子：

			- cat /proc/version

				- 查看Linux版本信息

			- cat /proc/cpuinfo

				- 查看cpu信息

			- cat /proc/interrupts

				- 查看中断

			- cat /proc/loadavg

				- 查看系统负载

	- /sbin

		- 系统管理员命令存放目录；

	- misc：misc device

		- 杂项设备，是用来存放系统没有归类过的文件设备。
		- misc：miscellaneous，abbr，混杂的，各色各样混在一起，多才多艺的

	- root：根目录下，所以高home一级
	- run
	- srv：service，所有的服务文件，跑服务器的话，就会有很多服务的文件，是有可能不存在硬盘。
	- sys：系统文件夹，有很多关于系统可以更改的东西，屏幕亮度的文件。。。
	- tmp：tempory，存放临时文件
	- usr：system resources 还是 software resources，最庞大的目录，要用到的应用程序和文件几乎都在这个目录。

		- 是系统核心所在，包含了所有的共享文件。它是 unix 系统中最重要的目录之一，涵盖了二进制文件，各种文档，各种头文件，x，还有各种库文件；还有诸多程序，例如 ftp，telnet 等等。
		- 所有linux系统不要usr上用来运行，
		- /usr/include：系统头文件；
		- /usr/lib：存放常用动态链接共享库、静态档案库；
		- /usr/bin、/usr/sbin：这是对/bin、/sbin的一个补充；
		- /usr/X11R6 存放X window的目录
		- /usr/bin 众多的应用程序
		- /usr/sbin 超级用户的一些管理程序
		- /usr/doc linux文档
		- /usr/include linux下开发和编译应用程序所需要的头文件
		- /usr/lib 常用的动态链接库和软件包的配置文件
		- /usr/man 帮助文档
		- /usr/src 源代码，linux内核的源代码就放在/usr/src/linux里
		- /usr/local/bin 本地增加的命令
		- /usr/local/lib 本地增加的库

	- var：某些大文件的溢出区，比方说各种服务的日志文件

		- variable，可变的，缓存cache，可能会越来越大。。。

- 操作系统使用

	- 终端：命令行，ms中的dos

		- pwd
		- ls -la
		- man ls   manual：查看一个命令的使用方法，参数,q退出

			- [man find](https://blog.csdn.net/qq_42347124/article/details/112055628)

				- SYNOPSIS 概要[sɪˈnɒpsɪs]

				- hierarchy 有层次的 [ˈhaɪərɑːki]

				- -H,-L,-P
对比可以看出若不在[路径组]中指明./instance/reports这个软连接-H则无法搜索到./instance下的结果，-L可以搜索到路径下包括软连接在内的结果，-P则无法搜索到任何软连接下的结果。

				  # 一
				  mkdir -p /home/kali/Documents/test0/{instance,reports}
				  touch test.txt
				  # 二
				  ln -s /home/kali/Documents/test0/reports /home/kali/Documents/test0/instance/reports
				  # 三
				  
				  ┌──(kali㉿kali)-[~/Documents/test0]
				  └─$ find -H ./instance/reports -name test.txt
				  ./instance/reports/test.txt
				  
				  ┌──(kali㉿kali)-[~/Documents/test0]
				  └─$ find -L ./instance/reports -name test.txt                                                                                                                  
				  ./instance/reports/test.txt
				  
				  ┌──(kali㉿kali)-[~/Documents/test0]
				  └─$ find -P ./instance/reports -name test.txt
				                                                                                                                                                                      
				  ┌──(kali㉿kali)-[~/Documents/test0]
				  └─$ find -H ./ -name test.txt
				  ./reports/test.txt
				  
				  ┌──(kali㉿kali)-[~/Documents/test0]
				  └─$ find -L ./ -name test.txt
				  ./instance/reports/test.txt
				  ./reports/test.txt
				                                                                                                                                                                       
				  ┌──(kali㉿kali)-[~/Documents/test0]
				  └─$ find -P ./ -name test.txt
				  ./reports/test.txt
				  
				  ————————————————
				  版权声明：本文为CSDN博主「搁浅的人、落水的鲸」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
				  原文链接：https://blog.csdn.net/qq_42347124/article/details/112055628
				  
				- 路径组

					- 路径组为被搜寻的路径，要搜寻多个路径时用空格隔开，如find -L ./reports ./instance -name test.txt即为在目录./reports和./instance中搜寻名为test.txt的文件。

				- 操作符

					- 当存在需要表达式实现有逻辑关系的搜寻或执行时就可能会用到操作符。常用的操作符有-a（和）和-o（或），例如sudo find / -iname '*.jpeg' -o -iname '*.jpg'即为搜索电脑中全部的jpeg(jpg)格式的文件。

		- cd:change directory

			- ~,用户目录

		- mkdir:make directory
		- touch:摸一下？
		- nano,open,vim,nvim 编辑
		- cat,less 显示文件
		- mv：move，移动文件,重命名
mv -i是否覆盖
		- cp:copy，复制文件，重命名
		- rm:remove，删除文件
rm -r 删除文件夹 --recursive递归重复性的删除
		- pwd：print working directory

### linux遇到问题处理

- go代理配置 - fzf build

  Goproxy 中国
  https://goproxy.cn/
  
  make install
  GOARCH=amd64 go build -a -ldflags "-s -w -X main.version=0.27.0 -X main.revision=19759ed3" -tags "" -o target/fzf-linux_amd64
  go: github.com/gdamore/tcell@v1.4.0: Get "https://proxy.golang.org/github.com/gdamore/tcell/@v/v1.4.0.mod": dial tcp 216.58.200.49:443: connect: connection refused
  Makefile:126: recipe for target 'target/fzf-linux_amd64' failed
  make: *** [target/fzf-linux_amd64] Error 1
  
  
  解决办法：go env -w GOPROXY=https://goproxy.cn
  
  make install 成功 
  
- gzip -d filename.gz
- .zshrc文件一直报错

	- 一直报错.fzf/shell  command not found: bind

		- # [ -f ~/.fzf.bash ] && source ~/.fzf.bash 这句话应该运行在bash上面估计是因为不zsh语法不兼容，所以不应该出现在这里20210425

	- 一直报不是一个git仓库 其实是因为命令行启动时 执行了git命令

		- # alias show-last-tag=git describe --tags `git rev-list --tags --max-count=1` #这个代码一直报错  因为读取到这里时，代码会首先执行rev-list --tags --max-count=1

- 查看日志命令集合

	- tail -f servece.log 
查看服务器日志
	- 查看文件集合

		- cat 查看文本内容
		- more分页看
		- less分页看，搜索，回翻
		- tail -10 查看文件尾部10行
		- head -20 查看文件头部20行

	- cat service.log | grep 13888888888
service.log中所有含有13888888888的记录给搜出来，搜索的速度还是贼快的
	- cat -n service.log | grep 13888888888 行号
	- sed -n "29496,29516p" service.log
从29496行开始检索，到29516行结束
	- cat -n service.log | tail -n +29496 | head -n 20
从29496行开始检索，往前推20条
	- cat service.log | grep 13 |more ：
将查询后的结果交由more输出
	- cat service.log | grep 13 &gt; /home/sanwai/aa.txt  将查询后的结果写到/home/sanwai/aa.txt文件上
	- 有的时候，我们想统计这个日志输出了多少行，我们可以使用这条命令：
cat service.log | wc -l

- vim -c 'set encoding=utf-8' /var/log/vdi/api.log
- wget -c https://github.com/ryanoasis/nerd-fonts/raw/master/patched-fonts/DroidSansMono/complete/Droid%20Sans%20Mono%20Nerd%20Font%20Complete.otf

- linux电脑无法使用root帐号进行代码联调时

  解决办法1：
  target host
   wget http://172.16.55.99:8081
  
  des host
   http-server => hs
  Starting up http-server, serving ./
  Available on:
    http://172.16.55.99:8080
    http://127.0.0.1:8080
  
### [linux比较好的网站，](https://zhuanlan.zhihu.com/p/36801617)

## linux上开发环境配置

### windows10 wsl

### ubuntu 20.04

### zsh,.oh-my-zsh

- git

	- 默认开启，git命令缩写
	- cat ~/.oh-my-zsh/plugins/git/git.plugin.zsh
	- alias | grep config

- Z

	- 内置组件
	- z -x 无效路径

- autojump

	- linux安装autojump

		- git clone git://github.com/joelthelion/autojump.git
./install.py
		- 最后把以下代码加入 .zshrc：
[[ -s ~/.autojump/etc/profile.d/autojump.sh ]] && . ~/.autojump/etc/profile.d/autojump.sh

	- autojump 的缩写 j
	- j --purge 无效路径 删除无效路径
	- jo music 打开 muisc 文件夹
	- j w in 多个参数一起使用 打开 /home/user/work/inbox

- zsh-syntax-highlighting

	- git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
	- 在 ~/.zshrc 中配置
plugins=(其他的插件 zsh-syntax-highlighting)
	- source ~/.zshrc

- zsh-autosuggestions

	- git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
	- 在 ~/.zshrc 中配置
plugins=(其他的插件 zsh-autosuggestions)
	- bindkey ',' autosuggest-accept

- git-open

	- git clone https://github.com/paulirish/git-open.git $ZSH_CUSTOM/plugins/git-open
	- plugins=(其他的插件 git-open)
	- alias go="git-open"

- history 

	- HIST_STAMPS="yyyy-mm-dd"

- trash 官网

	- npm install --global trash-cli
alias cp="cp -i
	- 防止 copy 的时候覆盖已存在的文件, 带上 i 选项，文件已存在的时候，会提示，需要确认才能 copy

- bat 代替 cat

	- cat 某个文件，可以在终端直接输出文件内容，bat 相比 cat 增加了行号和颜色高亮 👍

### node

- npm配置

	- It's not recommended to use sudo with npm install, follow the steps from npmjs official docs instead
	- mkdir ~/.npm-global
	- npm config set prefix '~/.npm-global'
	- export PATH=~/.npm-global/bin:$PATH
	- source ~/.profile
	- [npm install -g xxxx
https://docs.npmjs.com/getting-started/fixing-npm-permissions](https://stackoverflow.com/questions/46058546/error-eacces-permission-denied-access-usr-lib-node-modules)

	- sudo chown -R 1000:1000 "/home/zagger/.npm"
	- sudo chown -R 1000:1000 "/home/zagger/.npm_global"
	- 

### [pip，pip3](https://ywnz.com/linuxjc/6998.html)

- pip3

	- sudo apt update
sudo apt install python3-pip
pip3 --version

- pip2

	- https://bootstrap.pypa.io/pip/2.7/get-pip.py --output get-pip.py
sudo python2 get-pip.py

### nvim

### fzf

- [安装最新的](https://github.com/junegunn/fzf/releases)

	- 鼠标右键下载的那个包，点击复制链接，下载tar的链接如下：wget https://github.com/junegunn/fzf/releases/download/0.27.0/fzf-0.27.0-linux_amd64.tar.gz

		- tar xvf fzf-0.27.0-linux_amd64.tar.gz

			- apt-get install fzf
where fzf
cp fzf /usr/bin
fzf --version

### lazygit

- https://github.com/jesseduffield/lazygit#ubuntu

	- sudo add-apt-repository ppa:lazygit-team/release
sudo apt-get update
sudo apt-get install lazygit

### [zim](https://github.com/zimfw/zimfw)

### [dotfiles  ](https://luolei.org/dotfiles-tutorial/)

## [常用命令](https://blog.csdn.net/weixin_30340745/article/details/96306905)

进入文件 cd /home 进入 '/ home' 目录' cd .. 返回上一级目录 cd ../.. 返回上两级目录 查看文件夹中的文件 ls 查看目录中的文件 ll 查看目录中的文件 ls -l 显示文件和目录的详细资料 ls -a 显示隐藏文件 创建文件夹 mkdir dir1 创建一个叫做 'dir1' 的目录' mkdir dir1 dir2 同时创建两个目录 删除文件 rm -f file1 删除一个叫做 'file1' 的文件' rmdir dir1 删除一个叫做 'dir1' 的目录' rm -rf dir1 删除一个叫做 'dir1' 的目录并同时删除其内容 rm -rf dir1 dir2 同时删除两个目录及它们的内容 mv dir1 new_dir 重命名/移动 一个目录 cp file1 file2 复制一个文件 cp -a dir1 dir2 复制一个目录 cp -r dir1 dir2 复制一个目录及子目录 编辑一个文件 vim a.js 当编辑完退出时候 esc :w + enter 保存 :q + enter 退出vim模式 vim 编辑手册 vimtutor 

### rsync

rsync -avz js built resources views personal_login css fonts includes scope_manage root@172.16.201.91:/var/www/html

- [rsync -avz js built resources views personal_login css fonts includes scope_manage root@172.16.201.91:/var/www/html](https://www.runoob.com/linux/linux-comm-chown.html)

### [chown：change owner](https://www.runoob.com/linux/linux-comm-chown.html)

Linux chown 命令
￼ Linux 命令大全
Linux chown（英文全拼：change owner）命令用于设置文件所有者和文件关联组的命令。
Linux/Unix 是多人多工操作系统，所有的文件皆有拥有者。利用 chown 将指定文件的拥有者改为指定的用户或组，用户可以是用户名或者用户 ID，组可以是组名或者组 ID，文件是以空格分开的要改变权限的文件列表，支持通配符。 。
chown 需要超级用户 root 的权限才能执行此命令。
只有超级用户和属于组的文件所有者才能变更文件关联组。非超级用户如需要设置关联组可能需要使用 chgrp 命令。
使用权限 : root

语法

chown [-cfhvR] [--help] [--version] user[:group] file...
参数 :
user : 新的文件拥有者的使用者 ID
group : 新的文件拥有者的使用者组(group)
-c : 显示更改的部分的信息
-f : 忽略错误信息
-h :修复符号链接
-v : 显示详细的处理信息
-R : 处理指定目录以及其子目录下的所有文件
--help : 显示辅助说明
--version : 显示版本

实例

把 /var/run/httpd.pid 的所有者设置 root：
chown root /var/run/httpd.pid
将文件 file1.txt 的拥有者设为 runoob，群体的使用者 runoobgroup :
chown runoob:runoobgroup file1.txt
将当前前目录下的所有文件与子目录的拥有者皆设为 runoob，群体的使用者 runoobgroup:
chown -R runoob:runoobgroup *
把 /home/runoob 的关联组设置为 512 （关联组ID），不改变所有者：
chown :512 /home/runoob
￼ Linux 命令大全


### [chmod：change mode](https://www.runoob.com/linux/linux-comm-chmod.html)

Linux chmod命令
￼ Linux 命令大全
Linux chmod（英文全拼：change mode）命令是控制用户对文件的权限的命令
Linux/Unix 的文件调用权限分为三级 : 文件所有者（Owner）、用户组（Group）、其它用户（Other Users）。
￼
只有文件所有者和超级用户可以修改文件或目录的权限。可以使用绝对模式（八进制数字模式），符号模式指定文件的权限。
￼
使用权限 : 所有使用者

语法

chmod [-cfvR] [--help] [--version] mode file...

参数说明

mode : 权限设定字串，格式如下 :
[ugoa...][[+-=][rwxX]...][,...]
其中：
u 表示该文件的拥有者，g 表示与该文件的拥有者属于同一个群体(group)者，o 表示其他以外的人，a 表示这三者皆是。
+ 表示增加权限、- 表示取消权限、= 表示唯一设定权限。
r 表示可读取，w 表示可写入，x 表示可执行，X 表示只有当该文件是个子目录或者该文件已经被设定过为可执行。
其他参数说明：
-c : 若该文件权限确实已经更改，才显示其更改动作
-f : 若该文件权限无法被更改也不要显示错误讯息
-v : 显示权限变更的详细资料
-R : 对目前目录下的所有文件与子目录进行相同的权限变更(即以递归的方式逐个变更)
--help : 显示辅助说明
--version : 显示版本

符号模式

使用符号模式可以设置多个项目：who（用户类型），operator（操作符）和 permission（权限），每个项目的设置可以用逗号隔开。 命令 chmod 将修改 who 指定的用户类型对文件的访问权限，用户类型由一个或者多个字母在 who 的位置来说明，如 who 的符号模式表所示:
who用户类型说明
u | user | 文件所有者
g | group | 文件所有者所在组
o | others | 所有其他用户
a | all | 所用用户, 相当于 ugo
operator 的符号模式表:
Operator说明
+ | 为指定的用户类型增加权限
- | 去除指定用户类型的权限
= | 设置指定用户权限的设置，即将用户类型的所有权限重新设置
permission 的符号模式表:
模式名字说明
r | 读 | 设置为可读权限
w | 写 | 设置为可写权限
x | 执行权限 | 设置为可执行权限
X | 特殊执行权限 | 只有当文件为目录文件，或者其他类型的用户有可执行权限时，才将文件权限设置可执行
s | setuid/gid | 当文件被执行时，根据who参数指定的用户类型设置文件的setuid或者setgid权限
t | 粘贴位 | 设置粘贴位，只有超级用户可以设置该位，只有文件所有者u可以使用该位

八进制语法

chmod命令可以使用八进制数来指定权限。文件或目录的权限位是由9个权限位来控制，每三位为一组，它们分别是文件所有者（User）的读、写、执行，用户组（Group）的读、写、执行以及其它用户（Other）的读、写、执行。历史上，文件权限被放在一个比特掩码中，掩码中指定的比特位设为1，用来说明一个类具有相应的优先级。
#权限rwx二进制
7 | 读 + 写 + 执行 | rwx | 111
6 | 读 + 写 | rw- | 110
5 | 读 + 执行 | r-x | 101
4 | 只读 | r-- | 100
3 | 写 + 执行 | -wx | 011
2 | 只写 | -w- | 010
1 | 只执行 | --x | 001
0 | 无 | --- | 000
例如， 765 将这样解释：
所有者的权限用数字表达：属主的那三个权限位的数字加起来的总和。如 rwx ，也就是 4+2+1 ，应该是 7。
用户组的权限用数字表达：属组的那个权限位数字的相加的总和。如 rw- ，也就是 4+2+0 ，应该是 6。
其它用户的权限数字表达：其它用户权限位的数字相加的总和。如 r-x ，也就是 4+0+1 ，应该是 5。

实例

将文件 file1.txt 设为所有人皆可读取 :
chmod ugo+r file1.txt
将文件 file1.txt 设为所有人皆可读取 :
chmod a+r file1.txt
将文件 file1.txt 与 file2.txt 设为该文件拥有者，与其所属同一个群体者可写入，但其他以外的人则不可写入 :
chmod ug+w,o-w file1.txt file2.txt
为 ex1.py 文件拥有者增加可执行权限:
chmod u+x ex1.py
将目前目录下的所有文件与子目录皆设为任何人可读取 :
chmod -R a+r *
此外chmod也可以用数字来表示权限如 :
chmod 777 file
语法为：
chmod abc file
其中a,b,c各为一个数字，分别表示User、Group、及Other的权限。
r=4，w=2，x=1
若要 rwx 属性则 4+2+1=7；
若要 rw- 属性则 4+2=6；
若要 r-x 属性则 4+1=5。
chmod a=rwx file
和
chmod 777 file
效果相同
chmod ug=rwx,o=x file
和
chmod 771 file
效果相同
若用 chmod 4755 filename 可使此程序具有 root 的权限。

更多说明

命令说明
chmod a+r file | 给file的所有用户增加读权限
chmod a-x file | 删除file的所有用户的执行权限
chmod a+rw file | 给file的所有用户增加读写权限
chmod +rwx file | 给file的所有用户增加读写执行权限
chmod u=rw,go= file | 对file的所有者设置读写权限，清空该用户组和其他用户对file的所有权限（空格代表无权限）
chmod -R u+r,go-r docs | 对目录docs和其子目录层次结构中的所有文件给用户增加读权限，而对用户组和其他用户删除读权限
chmod 664 file | 对file的所有者和用户组设置读写权限, 为其其他用户设置读权限
chmod 0755 file | 相当于u=rwx (4+2+1),go=rx (4+1 & 4+1)。0 没有特殊模式。
chmod 4755 file | 4设置了设置用户ID位，剩下的相当于 u=rwx (4+2+1),go=rx (4+1 & 4+1)。
find path/ -type d -exec chmod a-x {} \; | 删除可执行权限对path/以及其所有的目录（不包括文件）的所有用户，使用'-type f'匹配文件
find path/ -type d -exec chmod a+x {} \; | 允许所有用户浏览或通过目录path/



### curl -O 

Mac 终端 命令行 下载文件
curl -O 文件链接
curl -O https://apk.izuiyou.com/download/zuiyou_data_20190625.txt

- curl -O https://apk.izuiyou.com/download/zuiyou_data_20190625.txt

### ssh

ssh -NL 8099:172.16.203.10:80 zhangyao@50.175.233.194

- ssh -NL 8099:172.16.203.10:80 zhangyao@50.175.233.194

### du

sudo du -sh *

- sudo du -sh *

### export

export http_proxy=http://127.0.0.1:1087;export https_proxy=http://127.0.0.1:1087;

- export http_proxy=http://127.0.0.1:1087;export https_proxy=http://127.0.0.1:1087;

### grep

grep -rn "treeControl" ./ --exclude-dir={.git,node_modules,resources,built}

- grep -rn "treeControl" ./ --exclude-dir={.git,node_modules,resources,built}

### cut

- cut out selected portions of each line of a file
- 剪切文件每行的选定部分
- synopsis概要
- delim定界
- -d

	- -d delim
	-              Use delim as the field delimiter character instead of the tab character.

- -c

	- -c list
	- The list specifies character positions

- -f

	- -f list
	- The list specifies fields, separated in the input by the field delimiter character (see the -d option.)  Output fields are separated by a single occurrence of the field delimiter character.
	- 

- -n

	- -n      
	- Do not split multi-byte characters.  Characters will only be output if at least one byte is selected, and, after a prefix of zero or more unselected bytes, the rest of the bytes that form the character are selected.

- -s

	-      -s      
	- Suppress lines with no field delimiter characters.  Unless specified, lines with no delimiters are passed through unmodified.

- -b list

	- The list specifies byte positions Extract users' login names and shells from the system passwd(5) file as ``name:shell'' pairs:
           cut -d : -f 1,7 /etc/passwd

- Show the names and login times of the currently logged in users:
           who | cut -c 1-16,26-38

	- zagger   console15:05
zagger   ttys00015:07
zagger   ttys00115:07
zagger   ttys00215:07
zagger   ttys00315:07
zagger   ttys00415:07
zagger   ttys00516:57
zagger   ttys00618:36

- git branch|grep '*'|cut -d' ' -f2

### [awk](https://www.runoob.com/linux/linux-comm-awk.html)

### [tee = T 这是管线工人的术语，代表 T 型的管线分叉器](https://blog.csdn.net/jjlovefj/article/details/83176871)

vim 用 :w !sudo tee % 进行保存的终极奥义 - ayanmw - 博客园 (cnblogs.com)

### [proxychains](https://www.chenxublog.com/2020/06/12/proxychains-proxy.html)

- apt-get install proxychains
- /etc/proxychains.conf中加入
socks5 127.0.0.1 10808
- proxychains git clone xxxxxxxxx

### lsd

### [bat](https://zhuanlan.zhihu.com/p/43653265)

sharkdp/bat: A cat(1) clone with wings. (github.com)

### onefetch

### [neofetch](https://www.linuxprobe.com/neofetch-ubuntu.html)

### du -h -d1

### [ncdu ](https://github.com/rofl0r/ncdu)

(4 封私信 / 47 条消息) 哪些命令行工具让你相见恨晚？ - 知乎 (zhihu.com)

### netstat 命令

- 简介

	- 用于显示网络状态。
利用 netstat 指令可让你得知整个 Linux 系统的网络情况。

- 参数解释：

	- netstat -tulpn 
t:tcp
u:utp
l:listen
p:process
n:Show network addresses as numbers
n是不进行dns反向解析

- 例子

	- netstat -n | grep 8080
windows10-bash上能找到wsl中开启的8080dev-server服务，wsl命令行中找不到。
	- watch netstat -tulpn
	- # netstat -a //显示详细的网络状况
	- 显示当前户籍UDP连接状况
# netstat -nu
	- 显示UDP端口号的使用情况
# netstat -apu
	- 显示网卡列表 interfaces 
# netstat -i
	- 显示组播组的关系
# netstat -g
	- 显示网络统计信息
# netstat -s
	- 显示监听的套接口
# netstat -l

### netstat

netstat -a      # 列出所有端口
netstat -at     # 列出所有TCP端口
netstat -au    # 列出所有UDP端口
netstat -ax    # 列出所有unix端口

netstat -atnlp | grep "1045.spicy"  #直接使用ip地址列出所有处理监听状态的TCP端口，且加上程序名

- netstat -atnlp | grep "1045.spicy"

### ss命令

- ss -tulpn
- watch ss -tulpn

### xargs命令

- 概念理解

	- 通过管道接受字符串，并将接收到的字符串通过空格分割成许多参数(默认情况下是通过空格分割) 然后将参数传递给其后面的命令，作为后面命令的命令行参数
	- echo '--help' | cat 跟
echo '--help' | xargs cat 区别 

		- echo '--help' | cat 

			-  echo '--help' | cat   该命令输出的是echo的内容，也就是说将echo的内容当作cat处理的文件内容了
			- 实际上就是echo命令的输出通过管道定向到cat的输入了。然后cat从其标准输入中读取待处理的文本内容
			- 这等价于在test.txt文件中有一行字符 '--help' 然后运行  cat test.txt 的效果。

		- echo '--help' | xargs cat

			- 等价于 cat --help
			- xargs将其接受的字符串 --help 做成cat的一个命令参数来运行cat命令
			- echo 'test.c test.cpp' | xargs cat 等价于 cat test.c test.cpp 此时会将test.c和test.cpp的内容都显示出来。

- 选项

	- -d 选项

		- 默认情况下xargs将其标准输入中的内容以空白(包括空格、Tab、回车换行等)分割成多个之后当作命令行参数传递给其后面的命令，并运行之，我们可以使用 -d 命令指定分隔符
		- echo '11@22@33' | xargs echo
输出：
11@22@33

			- 默认情况下以空白分割，那么11@22@33这个字符串中没有空白，所以实际上等价于 echo 11@22@33 其中字符串 '11@22@33' 被当作echo命令的一个命令行参数

		- echo '11@22@33' | xargs -d '@' echo
输出：
11 22 33

			- 指定以@符号分割参数，所以等价于 echo 11 22 33 相当于给echo传递了3个参数，分别是11、22、33

	- -p 选项

		- 使用该选项之后xargs并不会马上执行其后面的命令，而是输出即将要执行的完整的命令(包括命令以及传递给命令的命令行参数)，询问是否执行，输入 y 才继续执行，否则不执行。这种方式可以清楚的看到执行的命令是什么样子，也就是xargs传递给命令的参数是什么
		- echo '11@22@33' | xargs -p -d '@'  echo
输出：
echo 11 22 33

			-  ?...y      ==>这里询问是否执行命令 echo 11 22 33 输入y并回车，则显示执行结果，否则不执行
 11 22 33   ==>执行结果

	-  -n 选项

		- 该选项表示将xargs生成的命令行参数，每次传递几个参数给其后面的命令执行，例如如果xargs从标准输入中读入内容，然后以分隔符分割之后生成的命令行参数有10个，使用 -n 3 之后表示一次传递给xargs后面的命令是3个参数，因为一共有10个参数，所以要执行4次，才能将参数用完
		- echo '11@22@33@44@55@66@77@88@99@00' | xargs -d '@' -n 3 echo

			- 输出结果：
11 22 33
44 55 66
77 88 99
00

				- 等价于：
echo 11 22 33
echo 44 55 66
echo 77 88 99
echo 00

			- 实际上运行了4次，每次传递3个参数，最后还剩一个，就直接传递一个参数。

	- -E 选项，有的系统的xargs版本可能是-e  eof-str

		- 该选项指定一个字符串，当xargs解析出多个命令行参数的时候，如果搜索到-e指定的命令行参数，则只会将-e指定的命令行参数之前的参数(不包括-e指定的这个参数)传递给xargs后面的命令
		- echo '11 22 33' | xargs -E '33' echo
输出：
11 22

			- 可以看到正常情况下有3个命令行参数 11、22、33 由于使用了-E '33' 表示在将命令行参数 33 之前的参数传递给执行的命令，33本身不传递。等价于 echo 11 22 这里-E实际上有搜索的作用，表示只取xargs读到的命令行参数前面的某些部分给命令执行。

		- 注意：-E只有在xargs不指定-d的时候有效，如果指定了-d则不起作用，而不管-d指定的是什么字符，空格也不行。

			- echo '11 22 33' | xargs -d ' ' -E '33' echo  => 输出 11 22 33
echo '11@22@33@44@55@66@77@88@99@00 aa 33 bb' | xargs -E '33' -d '@' -p  echo  => 输出 11 22 33 44 55 66 77 88 99 00 aa 33 bb

	- ## -0 选项表示以 '\0' 为分隔符，一般与find结合使用

		- find . -name "*.txt"
输出：
./2.txt
./3.txt
./1.txt     => 默认情况下find的输出结果是每条记录后面加上换行，也就是每条记录是一个新行
		- find . -name "*.txt" -print0
输出：
./2.txt./3.txt./1.txt     => 加上 -print0 参数表示find输出的每条结果后面加上 '\0' 而不是换行

			- find . -name "*.txt" -print0 | xargs -0 echo
输出：
./2.txt ./3.txt ./1.txt
			- find . -name "*.txt" -print0 | xargs -d '\0' echo
输出：
./2.txt ./3.txt ./1.txt
			- xargs的 -0 和 -d '\0' 表示其从标准输入中读取的内容使用 '\0' 来分割，由于 find 的结果是使用 '\0' 分隔的，所以xargs使用 '\0' 将 find的结果分隔之后得到3个参数： ./2.txt ./3.txt ./1.txt  注意中间是有空格的。上面的结果就等价于 echo ./2.txt ./3.txt ./1.txt
			- 实际上使用xargs默认的空白分隔符也是可以的  find . -name "*.txt"  | xargs  echo   因为换行符也是xargs的默认空白符的一种。find命令如果不加-print0其搜索结果的每一条字符串后面实际上是加了换行

- [讲得很好的一个地址](https://www.cnblogs.com/wangqiguo/p/6464234.html)

### ps命令:Processes Status 

- process status,用于显示当前进程的状态，类似于 windows 的任务管理器
- UNIX风格:ps -ef | grep node

	- wsl:ps -ef | grep dev-server 
	- # ps -ef | grep php //查找指定进程格式：
	- # ps -A //显示进程信息：
	- # ps -u root //显示root进程用户信息
	- # ps -ef //显示所有命令，连带命令行
	- 图示：

- BSD风格:ps aux | grep -v grep | grep mongod

	- 图示

### top命令

### cat aaa.txt | grep bbb | cut -d' ' -f3 | sort | uniq |wc -l

### systemctl restart vdi-*;thor-*

### lsof -i tcp:8081：查看系统进程

- lists openfiles

	- 在Unix中一切（包括网络套接口）都是文件

- [地址](https://www.jianshu.com/p/a3aa6b01b2e1)

- ps -A|grep nginx

	- ps -ef|grep nw

- netstat -n|grep 80

### kill pid：杀掉系统进程

### git diff 97ecd986a7bb38cfecc745e93544f6c31ebbf48a.. --name-only | xargs zip ../patch/update.zip

### zip

- 选项

	- -q:--quiet

		- 表示不显示压缩进度状态

	- -r:--recurse-paths

		- 表示子目录子文件全部压缩为zip；这部分比较重要，不然的话只有something这个文件夹被压缩，里面的没有被压缩进去

	- -e:--encrypt

		- 表示你的压缩文件需要加密，终端会提示你输入密码的；还有种加密方法，这种是直接在命令行里做的，比如zip -r -P Password01! modudu.zip SomeDir, 就直接用Password01!来加密modudu.zip了

	- -m：--move

		- 表示压缩完删除原文件

	- o:--latest-time

		- 表示设置所有被压缩文件的最后修改时间为当前压缩时间

- 跨目录操作

	- zip -q -r -e -m -o '\user\someone\someDir\someFile.zip' '\users\someDir'

- zip  [-aABcdDeEfFghjklLmoqrRSTuvVwXyz!@$]  [--longoption ...]  [-b path] [-n suffixes] [-t date] [-tt date]
       [zipfile [file ...]]  [-xi list]

### unzip

- 选项

	- -x

		- 文件列表 解压缩文件，但不包括指定的file文件。

			- [-x xfile(s)]
An  optional list of archive members to be excluded from processing.  Since wildcard characters nor-
mally match (`/') directory separators (for exceptions see the option -W), this option may  be  used
to  exclude  any  files  that are in subdirectories.  For example, ``unzip foo *.[ch] -x */*'' wouldextract all C source files in the main directory, but none in any subdirectories.   Without  the  -x
option, all C source files in all directories within the zipfile would be extracted.

	- -n

		- 不覆盖已经存在的文件

	- -v 

		- 查看压缩文件目录，但不解压。 

	- -t

		- 测试文件有无损坏，但不解压。 

	- -d 

		- 目录 把压缩文件解到指定目录下。

	- -o

		- 覆盖已存在的文件且不要求用户确认

	- -j 

		- 不重建文档的目录结构，把所有文件解压到同一目录下

	- -z

		-  只显示压缩文件的注解。 

- unzip [-Z] [-cflptTuvz[abjnoqsCDKLMUVWX$/:^]] file[.zip] [file(s) ...]  [-x xfile(s) ...] [-d exdir]

	- unzip test.zip 				->将test.zip解压到当前文件下
unzip -n test.zip -d /tmp 	->将test.zip解压到/tmp目录下，并且不要覆盖已有文件
unzip -v test.zip			->查看test.zip内容，但不解压
unzip -o test.zip -d tmp/	->将test.zip解压到/tmp目录下，并且覆盖已有文件


### 分类

- 目录切换命令

	- cd usr： 切换到该目录下usr目录
	- cd ..（或cd../）： 切换到上一层目录
	- cd /： 切换到系统根目录
	- cd ~： 切换到用户主目录
	- cd -： 切换到上一个所在目录

- 目录的操作命令（增删改查）

	- 1. mkdir 目录名称： 增加目录
	- 2. ls或者ll（ll是ls -l的缩写，ll命令以看到该目录下的所有目录和文件的详细信息）：查看目录信息
	- 3. find 目录 参数： 寻找目录（查）

		- 示例：

			- 列出当前目录及子目录下所有文件和文件夹: find .
			- 在/home目录下查找以.txt结尾的文件名:find /home -name "*.txt"
			- 同上，但忽略大小写: find /home -iname "*.txt"
			- 当前目录及子目录下查找所有以.txt和.pdf结尾的文件:find . \( -name "*.txt" -o -name "*.pdf" \)或find . -name "*.txt" -o -name "*.pdf"

		- find

			- 例子

				- find . -name "*.txt" -ok rm {} \;
				- find . -name .DS_Store -print0 | xargs -0 git rm -f --ignore-unmatch
				- 先通过find . -name '*.txt' -size +1M -type f 查看是否有大于1M的txt文件，没有的话就不用继续了
再通过find . -name '*.txt' -size +1M -type f -print0|xargs -0 
du -m|sort -nr|head -10​
				- sudo find ./ -name ".DS_Store" -depth -exec rm {} \; 

					- 删除当前目录下的所有文件是是这个的文件

			- 选项

				- 格式：
find   path   -option   [   -print ]   [ -exec   -ok   command ]   {} \;
				- -name
按照文件名查找文件。
				- -perm
按照文件权限来查找文件。
				- -user
按照文件属主来查找文件。
				- -group
按照文件所属的组来查找文件。
				- pathname: find命令所查找的目录路径。例如用.来表示当前目录，用/来表示系统根目录。
				- -prune                       #忽略某个目录
				- -print： find命令将匹配的文件输出到标准输出。
				- -exec： find命令对匹配的文件执行该参数所给出的shell命令。相应命令的形式为'command' { } \;，注意{ }和\；之间的空格。
				- -ok： 和-exec的作用相同，只不过以一种更为安全的模式来执行该参数所给出的shell命令，在执行每一个命令之前，都会给出提示，让用户来确定是否执行。
				- -axxx,xxx代表时间单位，time，min等等
a代表access，访问的文件
				- -mmin   # 查找在系统中最后N分钟里修改过的文件
m代表modify
				- -ctime    -n +n               #按文件创建时间来查找文件，-n指n天以内，+n指n天以前 
				- -size      n[c]               #查长度为n块[或n字节]的文件
				- -type    b/d/c/p/l/f         #查是块设备、目录、字符设备、管道、符号链接、普通文件

	- 4. mv 目录名称 新目录名称： 修改目录的名称（改）

		- 注意：mv的语法不仅可以对目录进行重命名而且也可以对各种文件，压缩包等进行	重命名的操作。mv命令用来对文件或目录重新命名，或者将文件从一个目录移到另一个目录中。后面会介绍到mv命令的另一个用法。

	- 5. mv 目录名称 目录的新位置：  移动目录的位置---剪切（改）

		- 注意：mv语法不仅可以对目录进行剪切操作，对文件和压缩包等都可执行剪切操作。另外mv与cp的结果不同，mv好像文件“搬家”，文件个数并未增加。而cp对文件进行复制，文件个数增加了。

	- 6. cp -r 目录名称 目录拷贝的目标位置： 拷贝目录（改），-r代表递归拷贝

		- 注意：cp命令不仅可以拷贝目录还可以拷贝文件，压缩包等，拷贝文件和压缩包时不	用写-r递归

	- 7. rm [-rf] 目录: 删除目录（删）

		- 注意：rm不仅可以删除目录，也可以删除其他文件或压缩包，为了增强大家的记忆，	无论删除任何目录或文件，都直接使用rm -rf 目录/文件/压缩包

- 文件的操作命令（增删改查）

	- 1. touch 文件名称:  文件的创建（增）
	- 2. cat/more/less/tail 文件名称 文件的查看（查）

		- cat： 只能显示最后一屏内容
		- more： 可以显示百分比，回车可以向下一行，	空格可以向下一页，q可以退出查看
		- less： 可以使用键盘上的PgUp和PgDn向上	和向下翻页，q结束查看
		- tail-10 ： 查看文件的后10行，Ctrl+C结束
		- 注意：命令 tail -f 文件 可以对某个文件进行动态监控，例如tomcat的日志文件，	会随着程序的运行，日志会变化，可以使用tail -f catalina-2016-11-11.log 监控	文	件的变化

	- 3. vim 文件：  修改文件的内容（改）

		- vim编辑器是Linux中的强大组件，是vi编辑器的加强版，vim编辑器的命令和快捷方式有很多，但此处不一一阐述，大家也无需研究的很透彻，使用vim编辑修改文件的方式基本会使用就可以了。
		- 在实际开发中，使用vim编辑器主要作用就是修改配置文件，下面是一般步骤：
		- vim 文件------>进入文件----->命令模式------>按i进入编辑模式----->编辑文件	------->按Esc进入底行模式----->输入:wq/q! （输入wq代表写入内容并退出，即保存；输入q!代表强制退出不保存。）

	- 4. rm -rf 文件： 删除文件（删）

		- 同目录删除：熟记 rm -rf 文件 即可

- 压缩文件的操作命令

	- 1）打包并压缩文件：

		- Linux中的打包文件一般是以.tar结尾的，压缩的命令一般是以.gz结尾的。
		- 而一般情况下打包和压缩是一起进行的，打包并压缩后的文件的后缀名一般.tar.gz。
		- 命令：tar -zcvf 打包压缩后的文件名 要打包压缩的文件
		- 其中：

			- z：调用gzip压缩命令进行压缩
			- c：打包文件
			- v：显示运行过程
			- f：指定文件名

		- 比如：加入test目录下有三个文件分别是 :aaa.txt bbb.txt ccc.txt,如果我们要打包test目录并指定压缩后的压缩包名称为test.tar.gz可以使用命令：tar -zcvf test.tar.gz aaa.txt bbb.txt ccc.txt或：tar -zcvf test.tar.gz /test/

	- 2）解压压缩包：

		- 命令：tar [-xvf] 压缩文件

			- 其中：x：代表解压

		- 示例：

			- 1 将/test下的test.tar.gz解压到当前目录下可以使用命令：tar -xvf test.tar.gz
			- 2 将/test下的test.tar.gz解压到根目录/usr下:tar -xvf xxx.tar.gz -C /usr（- C代表指定解压的位置）

- Linux的权限命令

	- 权限概念：

		- 操作系统中每个文件都拥有特定的权限、所属用户和所属组。
		- 权限是操作系统用来限制资源访问的机制，在Linux中权限一般分为读(readable)、写(writable)和执行(excutable)，分为三组。分别对应文件的属主(owner)，属组(group)和其他用户(other)，通过这样的机制来限制哪些用户、哪些组可以对特定的文件进行什么样的操作。

	- 查看权限

		- 通过 ls -l 命令我们可以查看某个目录下的文件或目录的权限

			- 示例：在随意某个目录下ls -l

				- 第一列的内容的信息解释如下：

	- 下面将详细讲解文件的类型、Linux中权限以及文件有所有者、所在组、其它组具体是什么？

		- 文件的类型：

			- d： 代表目录
			- -： 代表文件
			- l： 代表链接（可以认为是window中的快捷方式）

		- Linux中权限分为以下几种：

			- r：代表权限是可读，r也可以用数字4表示
			- w：代表权限是可写，w也可以用数字2表示
			- x：代表权限是可执行，x也可以用数字1表示

		- 文件和目录权限的区别：

			- 对文件和目录而言，读写执行表示不同的意义。

				- 文件
				- 目录

		- 在linux中的每个用户必须属于一个组，不能独立于组外。在linux中每个文件有所有者、所在组、其它组的概念。

			- 所有者

				- 一般为文件的创建者，谁创建了该文件，就天然的成为该文件的所有者，用ls ‐ahl命令可以看到文件的所有者 也可以使用chown 用户名 文件名来修改文件的所有者 。

			- 文件所在组

				- 当某个用户创建了一个文件后，这个文件的所在组就是该用户所在的组 用ls ‐ahl命令可以看到文件的所有组 也可以使用chgrp 组名 文件名来修改文件所在的组。

			- 其它组

				- 除开文件的所有者和所在组的用户外，系统的其它用户都是文件的其它组

	- 我们再来看看如何修改文件/目录的权限。

		- 修改文件/目录的权限的命令：chmod

			- 示例：修改/test下的aaa.txt的权限为属主有全部权限，属主所在的组有读写权限， 其他用户只有读的权限
			- chmod u=rwx,g=rw,o=r aaa.txt

				- 图示
				- chmod 764 aaa.txt

		- 补充一个比较常用的东西:

			- 假如我们装了一个zookeeper，我们每次开机到要求其自动启动该怎么办？
			- 新建一个脚本zookeeper
			- 为新建的脚本zookeeper添加可执行权限，命令是:chmod +x zookeeper
			- 把zookeeper这个脚本添加到开机启动项里面，命令是：chkconfig --add zookeeper
			- 如果想看看是否添加成功，命令是：chkconfig --list

- Linux 用户管理

	- 概念：

		- Linux系统是一个多用户多任务的分时操作系统，任何一个要使用系统资源的用户，都必须首先向系统管理员申请一个账号，然后以这个账号的身份进入系统。
		- 用户的账号一方面可以帮助系统管理员对使用系统的用户进行跟踪，并控制他们对系统资源的访问；另一方面也可以帮助用户组织文件，并为用户提供安全性保护。

	- Linux用户管理相关命令:

		- useradd 选项 用户名:添加用户账号
		- userdel 选项 用户名:删除用户帐号
		- usermod 选项 用户名:修改帐号
		- passwd 用户名:更改或创建用户的密码
		- passwd -S 用户名 :显示用户账号密码信息
		- passwd -d 用户名:  清除用户密码

	- 总结

		- useradd命令用于Linux中创建的新的系统用户。useradd可用来建立用户帐号。帐号建好之后，再用passwd设定帐号的密码．而可用userdel删除帐号。使用useradd指令所建立的帐号，实际上是保存在/etc/passwd文本文件中。
		- passwd命令用于设置用户的认证信息，包括用户密码、密码过期时间等。系统管理者则能用它管理系统用户的密码。只有管理者可以指定用户名称，一般用户只能变更自己的密码。

-  Linux系统用户组的管理

	- 概念

		- 每个用户都有一个用户组，系统可以对一个用户组中的所有用户进行集中管理。不同Linux 系统对用户组的规定有所不同，如Linux下的用户属于与它同名的用户组，这个用户组在创建用户时同时创建。
		- 用户组的管理涉及用户组的添加、删除和修改。组的增加、删除和修改实际上就是对/etc/group文件的更新。

	- Linux系统用户组的管理相关命令:

		- groupadd 选项 用户组 :增加一个新的用户组
		- groupdel 用户组:要删除一个已有的用户组
		- groupmod 选项 用户组 : 修改用户组的属性

- 其他常用命令

	- pwd： 显示当前所在位置
	- grep 要搜索的字符串 要搜索的文件 --color： 

		- 搜索命令，--color代表高亮显示

	- ps -ef/ps aux： 这两个命令都是查看当前系统正在运行进程，两者的区别是展示格式不同。

		- 如果想要查看特定的进程可以使用这样的格式：ps aux|grep redis （查看包括redis字符串的进程）
		- 注意：如果直接用ps（（Process Status））命令，会显示所有进程的状态，通常结合grep命令查看某进程的状态。

	- kill -9 进程的pid： 杀死进程（-9 表示强制终止。）

		- 先用ps查找进程，然后用kill杀掉

	- 网络通信命令：

		- 查看当前系统的网卡信息：ifconfig
		- 查看与某台机器的连接情况：ping
		- 查看当前系统的端口使用：netstat -an

	- shutdown：  shutdown -h now： 指定现在立即关机；

		- shutdown +5 "System will shutdown after 5 minutes":指定5分钟后关机，同时送出警告信息给登入用户。

	- reboot：  reboot：  重开机。

		- reboot -w： 做个重开机的模拟（只有纪录并不会真的重开机）。

- [文章来源地址](https://juejin.cn/post/6844903634036064269)

- 查询linux命令的网站

	- [地址](https://man.linuxde.net/)

## [chrome plugin: vimium](https://www.zhihu.com/question/23483616?sort=created)

作者：小佐
链接：https://www.zhihu.com/question/23483616/answer/246787555
来源：知乎
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

最常用的快捷键
向下/上/左/右移动  j/k/h/l
向下/上跳动  d/u
回到顶/尾部  gg/G
窗口打开模式 本窗口/新窗口 f/F
查找历史记录+书签   o/O
关闭/恢复标签 x/X
查找书签  b/B（当前/新窗口打开）
选择左/右标签 J/K
搜索剪贴板关键字 在当前/新窗口  p/P
跳转到当前url上一级/最高级 gu/gU
创建/查看标签页  t/T
将焦点聚集在第一个输入框  gi  (2gi就是第二个输入框)
刷新 r
新标签中打开多个链接   <a-f> 即：alt+f
开/关静音  <a-m>即：alt+m
固定标签栏 <a-p>即 alt+p
上一个标签  ^


其他不常用快捷键

查找（不支持中文）  /
    向下/上查找结果  n/N  (回车后直接打开链接，不用再使用f/F定位)
复制当前链接 yy
新模式 i
查看源码 gs
查看所以快捷键 ?
编辑当前地址栏 g+e/E   并在当前/新窗口中打开
复制当前标签页  yt
移动当前标签到左/右侧边  <</>>
滚动到页面最左/右边（在有滚动条下才有效果） zH/zL
插入模式  i（可以屏蔽掉vimium快捷键，使其不和网页默认快捷键冲突）
将标签页移动到新窗口  W
创建新标记（可创建多个   m 使用方法
      设置当前/全局滚动条位置   m+小/大写字母
      跳转到设置的滚动位置   ~+字母
切换到复制模式 v


其他技巧

焦点切换
    从地址栏切换回页面  tag
翻页
    下/上一页  ]]  [[  部分网站不支持  可以使用 Shortcut Manager 插件代替
    下一页代码：
        function next(){
            var a=$(".cur").next().find("a").attr("href");
             window.location.assign(a);
        }
        next();
    上一页代码：
        function after(){
            var a=$(".cur").prev().find("a").attr("href");
             window.location.assign(a);
        }
        after();
自定义搜索引擎
    设置：
        请查看选项：Custom search engines
    使用：
        按b/B打开搜索框，输入搜索引擎关键字+空格
    扩展：
        计算功能
            g (1+2)*3-4=     进入google搜索模式直接输入公式后面加"="号
打开chrome系统页面
    chrome设置页面
        about:setting
    扩展程序
        about:extensions
    历史(history)，下载(downloads)，书签(bookmarks),建议使用chrome默认快捷键代替
        ctrl+h,ctrl+j,ctrl+shift+o
关于<a-p>,<c-e>
    是emacs中的表示方法，分别指alt+p,ctrl+e
快速定位+复制文本：alt+f,v,hjkl,y四步曲
    alt+f 搜索指定关键字，并定位到起始点
    再按v切换到复制模式
    再使用hjkl控制方向选择范围
    最后y复制
删除/修改命令
    删除指定命令
        unmap j   删除命令j
        unmapAll  删除所有命令
    修改命令（后面的命令参数可以在选择里面打开 show available commands找到）
        map a LinkHints.activateMode  把a定义原来f的功能
        map f scrollPageDown   把f定义成原来d的功能
本地文件中使用vimium
    打开chrome插件设置页面，勾选"允许访问文件网址"

## 虚拟机

### 

### 

## 文件权限

### [地址](https://www.cnblogs.com/songgj/p/8890710.html)

### 文件基本权限

- 首先看下linux下的文件权限，可以使用ll命令或者是带-l（长列表选项）的ls命令。

### 文件列表信息

- ：文件类型、权限、链接数、所属用户、所属用户组、文件大小、最后修改时间、文件名。

## linux命令可以从两个地方读取要处理的内容

### 一个是通过命令行参数

### 一个是标准输入

### cat、grep

- 命令行参数、标准输入，两个都支持

	- echo 'main' | cat test.cpp

		- cat会输出test.cpp的内容，而不是'main'字符串
		- echo 'main' | 会通过管道将 echo 的标准输出(也就是字符串'main')导入到 cat 的标准输入，也就是说此时cat的标准输入中是有内容的，其内容就是字符串'main'但是上面的内容中cat不会从它的标准输入中读入要处理的内容
		- 标准输入是有一个缓冲区的
		- 很多的命令的设计是先从命令行参数中获取参数，然后从标准输入中读取

	- echo 'main' | cat

		- 命令中cat会从其标准输入中读取内容并处理，也就是会输出 'main' 字符串
		- echo命令将其标准输出的内容 'main' 通过管道定向到 cat 的标准输入中。

	- cat

		- 仅仅输入cat并回车，则该程序会等待输入，我们需要从键盘输入要处理的内容给cat
		- 此时cat也是从标准输入中得到要处理的内容的，因为我们的cat命令行中也没有指定要处理的文件名

	- echo 'main' | cat -

		- 大多数命令有一个参数  -  如果直接在命令的最后指定 -  则表示从标准输入中读取
		- 会显示 'main' 字符串

	- echo 'main' | cat test.cpp -

		- 同时指定test.cpp 和 - 参数，此时cat程序会先输出test.cpp的内容，然后输出标准输入'main'字符串

	- echo 'main' | cat - test.cpp

		- 会先输出标准输入'main'字符串，然后输出test.cpp文件的内容

	- echo 'main' | grep 'main' test.cpp -

		- 

### 另外很多程序是不处理标准输入的，例如 kill , rm 这些程序如果命令行参数中没有指定要处理的内容则不会默认从标准输入中读取

- 不执行

	- echo '516' | kill
	- echo 'test' | rm -f

- kill 是结束进程，rm是删除文件
- 方法

	- 1. 通过 kill `ps -ef | grep 'ddd'`    
#这种形式，这个时候实际上等同于拼接字符串得到的命令，其效果类似于  kill $pid
	- 2. for procid in $(ps -aux | grep "some search" | awk '{print $2}'); do kill -9 $procid; done   
#其实与第一种原理一样，只不过需要多次kill的时候是循环处理的，每次处理一个
	- 3. ps -ef | grep 'ddd' | xargs kill  
#OK，使用了xargs命令，铺垫了这么久终于铺到了主题上。xargs命令可以通过管道接受字符串，并将接收到的字符串通过空格分割成许多参数(默认情况下是通过空格分割) 然后将参数传递给其后面的命令，作为后面命令的命令行参数

## [Linux和UNIX的关系及区别（详解版）](http://c.biancheng.net/view/707.html)

## 命令行翻墙：用proxychains-ng为程序设置代理

### [地址](https://www.jianshu.com/p/f7902bba9499)

### macos配置文件目录：nvim /usr/local/etc/proxychains.conf

- 图示

### proxychains后面接ping命令是不可以的，因为proxychains是在tcp层，ping命令是基于icmp在ip层

### proxychains后面可以接很多命令，curl、wget、git等等，当要下载国外资源的时候这个能提速很多，特别是链接github。

### macos上失效时，尝试这么解决

- 图示
- m1电脑尝试长按电源键进入恢复模式而不是cmd+r

