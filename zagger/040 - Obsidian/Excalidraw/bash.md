---
created: 2023-11-15T20:48
updated: 2023-11-15T20:48
---
# bash

## [Shell脚本中点号+文件名的作用](https://www.cnblogs.com/cjjjj/p/9817950.html)

## shell脚本：需要解释器解释

### 1.系统命令的堆积

### 2.特定的语法+系统的命令=文件

### 3.xx.sh

## shell脚本能做什么

### 基于标准化之上的 => 工具化
作用：简化操作步骤，提高效率，减少认为敢于，减少系统故障

### 1.自动化完成基础配置，（系统初始化操作、系统更新、内核调整、网络、时区、SSH优化）

### 2.自动化安装程序，自动化安装LNMP、LAMP、MySQL、Nginx、Redis

### 3.自动化调整配置文件，（Nginx Conf、MySQL Conf）

### 4.自动化部署业务
部署php、java、秒级回退

### 5.自动定期备份恢复程序，mysql全备+增量+binlog+crond+shell脚本
mysql - e "source /root/db.sql"

### 6.自动化信息的采集,硬件、系统、服务、网络等等，Zabbix+Shell
free -m

### 7. 自动化日志手机（ELK）
收集->存储->展示->分析
日志分析（取值->排序->去重->统计->分析）

### 8.自动化扩容（zabbix+shell）
监控服务器，如果发现cpu持续80%+触发动作（脚本）
脚本：调用api开通云主机->初始化环境->加入集群->对外提供
当前cpu使用率20%->判断有多少web节点->判断是否成超过预设->缩减到对应的预设状态->变更负载的配置

### 9.Shell什么都能做，但要符合实际情况以及实际业务需求

## Shell技能

### shell是什么

- 直接上一个 test 文件，里面写入 echo "123"
./test 执行 输出123
bash test 执行 输出123
sh test 执行 输出123
which sh
ls /usr/bin/sh -l
链接到bash了
- #!/usr/bin/sh
告诉系统，使用什么解释器执行
否则统一要加下
- 执行方式推荐用
bash 脚本 不需要添加执行权限，使用解释器直接执行了

### 特性

- 1.命令补全和文件路径补全，如果写错无法补全
- 2.命令历史记忆功能，history
- 3.别名功能，alias\unalias
- 4.常用快捷键,c-u,k,a,e,l,c,z,d,w,r,y
- 5.前后台作业控制bg,fg,jobs,screen
- 6.输入输出重定向 >,>>,1>,2>>,&>,cat <

	- cat 命令：
cat  <  /etc/hosts > /etc/etst.sql  读入一个文件，然后重定向到文件中
cat /etc/test.sql > test.sql 读取键盘上的输入值，重定向

- 7.管道 | 将前者命令的标准输出交给后者命令的输入，tee，把当前管道的内容记录下来

	- tee

		- tee = T 这是管线工人的术语，代表 T 型的管线分叉器

- 8.命令排序 ; && || 

	- cat /etc/hosts &>/dev/null && mkdir .test2

- 9.shell 通配符

	- * 匹配任意多个字符
	- ? 匹配任意一个字符
	- []匹配括号中任意一个字符
	- ()在子shell中执行（cd /boot;ls) (umask 077;touch file1000)

		- (cd /boot;ls) 
 pwd
发现文件夹没有变
子shell执行，执行完了关闭就行了

	- {}集合 touch file{1..9}
	- \ 转义

		- 转义后面不要有kongge

- 10.echo输出颜色、printf格式化输出文本

	- echo -e "\033[30m 黑色字 \033[0m"
echo -e "\033[31m 红色字 \033[0m"
echo -e "\033[32m 绿色字 \033[0m"
echo -e "\033[33m 黄色字 \033[0m"
echo -e "\033[34m 蓝色字 \033[0m" 
echo -e "\033[35m 紫色字 \033[0m" 
echo -e "\033[36m 天蓝字 \033[0m" 
echo -e "\033[37m 白色字 \033[0m" 

### 变量

- 用一个固定的字符串表示不固定的内容

	- a=1
b=2
c=$a+$b
echo $c | bc
	- ifconfig eth0|grep "inet"
IP=` ifconfig eth0|grep "inet"`
IP=$(ifconfig eth0|grep "inet")

		- address="www.baidu.com"
ping -c1 $address &>/dev/null && echo "$address ok" || echo "$address error"

- 自定义变量

	- 定义变量

		- 变量名=变量值

			- 不允许数字命名，不能使用-命名

	- 引用变量

- 系统环境变量

	- env查看环境变量

		- LANG

			- language
			- linux中记录系统字符集 语言
zh_CN.UTF-8

		- PS1

			- 命令行格式

		- PATH

			- 命令的位置

		- 历史命令

			- HISTSIZE
			- HISTFILESIE
			- HISTFILE

		- TMOUT
		- HISTCONTROL
		- PROMPT_COMMAND

- 预先定义变量
- 位置参数变量
- 内置变量 continue、break、exit

### 条件判断

- if else

### 循环语句

- for、while

### 流程控制

- case

### 函数

- function

### 数组

- array

### 正则表达式

### 案例、项目

## 快捷键

### c-l清屏

### c-c终止进程

### c-u从光标删除到行首

### c-k从光标删除到行尾

## 基本语法

### 命令格式

- $ command [ arg1 ... [ argN ]]

  $ ls -l
  
  上面这个命令中，ls是命令，-l是参数。
  
  有些参数是命令的配置项，这些配置项一般都以一个连词线开头，比如上面的-l。同一个配置项往往有长和短两种形式，比如-l是短形式，--list是长形式，它们的作用完全相同。短形式便于手动输入，长形式一般用在脚本之中，可读性更好，利于解释自身的含义。
  
  # 短形式
  $ ls -r
  
  # 长形式
  $ ls --reverse
  
  上面命令中，-r是短形式，--reverse是长形式，作用完全一样。前者便于输入，后者便于理解。
  
  Bash 单个命令一般都是一行，用户按下回车键，就开始执行。有些命令比较长，写成多行会有利于阅读和编辑，这时可以在每一行的结尾加上反斜杠，Bash 就会将下一行跟当前行放在一起解释。
  
  $ echo foo bar
  
  # 等同于
  $ echo foo \
  bar
  
  
### 空格

Bash 使用空格（或 Tab 键）区分不同的参数。

$ command foo bar

上面命令中，foo和bar之间有一个空格，所以 Bash 认为它们是两个参数。

如果参数之间有多个空格，Bash 会自动忽略多余的空格。

$ echo this is a     test
this is a test

上面命令中，a和test之间有多个空格，Bash 会忽略多余的空格。



### 分号

分号（;）是命令的结束符，使得一行可以放置多个命令，上一个命令执行结束后，再执行第二个命令。

$ clear; ls

上面例子中，Bash 先执行clear命令，执行完成后，再执行ls命令。

注意，使用分号时，第二个命令总是接着第一个命令执行，不管第一个命令执行成功或失败。


### && ||

除了分号，Bash 还提供两个命令组合符&&和||，允许更好地控制多个命令之间的继发关系。

Command1 && Command2

上面命令的意思是，如果Command1命令运行成功，则继续运行Command2命令。

Command1 || Command2

上面命令的意思是，如果Command1命令运行失败，则继续运行Command2命令。

下面是一些例子。

$ cat filelist.txt ; ls -l filelist.txt

上面例子中，只要cat命令执行结束，不管成功或失败，都会继续执行ls命令。

$ cat filelist.txt && ls -l filelist.txt

上面例子中，只有cat命令执行成功，才会继续执行ls命令。如果cat执行失败（比如不存在文件flielist.txt），那么ls命令就不会执行。

$ mkdir foo || mkdir bar

上面例子中，只有mkdir foo命令执行失败（比如foo目录已经存在），才会继续执行mkdir bar命令。如果mkdir foo命令执行成功，就不会创建bar目录了。



### echo

- echo hello world
- echo hello\
world
- echo -n 
结尾没有\n
- echo -e
会eval

### type

- type echo
- type -a echo
所有定义
- type -t bash
命令类型

## [Bash的模式扩展](https://wangdoc.com/bash/expansion.html)

### 简介

Shell 接收到用户输入的命令以后，会根据空格将用户的输入，拆分成一个个词元（token）。然后，Shell 会扩展词元里面的特殊字符，扩展完成后才会调用相应的命令。

这种特殊字符的扩展，称为模式扩展（globbing）。其中有些用到通配符，又称为通配符扩展（wildcard expansion）。Bash 一共提供八种扩展。
本章介绍这八种扩展。

Bash 是先进行扩展，再执行命令。因此，扩展的结果是由 Bash 负责的，与所要执行的命令无关。命令本身并不存在参数扩展，收到什么参数就原样执行。这一点务必需要记住。

模块扩展的英文单词是globbing，这个词来自于早期的 Unix 系统有一个/etc/glob文件，保存扩展的模板。后来 Bash 内置了这个功能，但是这个名字就保留了下来。

模式扩展与正则表达式的关系是，模式扩展早于正则表达式出现，可以看作是原始的正则表达式。它的功能没有正则那么强大灵活，但是优点是简单和方便。

Bash 允许用户关闭扩展。

$ set -o noglob
# 或者
$ set -f
下面的命令可以重新打开扩展。

$ set +o noglob
# 或者
$ set +f

-  波浪线扩展  家目录

  波浪线~会自动扩展成当前用户的主目录。
  
  $ echo ~
  /home/me
  
  ~/dir表示扩展成主目录的某个子目录，dir是主目录里面的一个子目录名。
  
  # 进入 /home/me/foo 目录
  $ cd ~/foo
  
  ~user表示扩展成用户user的主目录。
  
  $ echo ~foo
  /home/foo
  
  $ echo ~root
  /root
  
  上面例子中，Bash 会根据波浪号后面的用户名，返回该用户的主目录。
  
  如果~user的user是不存在的用户名，则波浪号扩展不起作用。
  
  $ echo ~nonExistedUser
  ~nonExistedUser
  
  ~+会扩展成当前所在的目录，等同于pwd命令。
  
  $ cd ~/foo
  $ echo ~+
  /home/me/foo
  
  
  
- ?字符扩展 单个字符

  ?字符代表文件路径里面的任意单个字符，不包括空字符。比如，Data???匹配所有Data后面跟着三个字符的文件名。
  
  # 存在文件 a.txt 和 b.txt
  $ ls ?.txt
  a.txt b.txt
  
  上面命令中，?表示单个字符，所以会同时匹配a.txt和b.txt。
  
  如果匹配多个字符，就需要多个?连用。
  
  # 存在文件 a.txt、b.txt 和 ab.txt
  $ ls ??.txt
  ab.txt
  
  上面命令中，??匹配了两个字符。
  
  ? 字符扩展属于文件名扩展，只有文件确实存在的前提下，才会发生扩展。如果文件不存在，扩展就不会发生。
  
  # 当前目录有 a.txt 文件
  $ echo ?.txt
  a.txt
  
  # 当前目录为空目录
  $ echo ?.txt
  ?.txt
  
  上面例子中，如果?.txt可以扩展成文件名，echo命令会输出扩展后的结果；如果不能扩展成文件名，echo就会原样输出?.txt。
  
  
- * 字符扩展 文件路径任意数量的任意字符包括零个字符

  *字符代表文件路径里面的任意数量的任意字符，包括零个字符。
  
  # 存在文件 a.txt、b.txt 和 ab.txt
  $ ls *.txt
  a.txt b.txt ab.txt
  
  上面例子中，*.txt代表后缀名为.txt的所有文件。
  
  如果想输出当前目录的所有文件，直接用*即可。
  
  $ ls *
  
  *可以匹配空字符，下面是一个例子。
  
  # 存在文件 a.txt、b.txt 和 ab.txt
  $ ls a*.txt
  a.txt ab.txt
  
  $ ls *b*
  b.txt ab.txt
  
  注意，*不会匹配隐藏文件（以.开头的文件），即ls *不会输出隐藏文件。
  
  如果要匹配隐藏文件，需要写成.*。
  
  # 显示所有隐藏文件
  $ echo .*
  
  如果要匹配隐藏文件，同时要排除.和..这两个特殊的隐藏文件，可以与方括号扩展结合使用，写成.[!.]*。
  
  $ echo .[!.]*
  
  注意，*字符扩展属于文件名扩展，只有文件确实存在的前提下才会扩展。如果文件不存在，就会原样输出。
  
  # 当前目录不存在 c 开头的文件
  $ echo c*.txt
  c*.txt
  
  上面例子中，当前目录里面没有c开头的文件，导致c*.txt会原样输出。
  
  *只匹配当前目录，不会匹配子目录。
  
  # 子目录有一个 a.txt
  # 无效的写法
  $ ls *.txt
  
  # 有效的写法
  $ ls */*.txt
  
  上面的例子，文本文件在子目录，*.txt不会产生匹配，必须写成*/*.txt。有几层子目录，就必须写几层星号。
  
  Bash 4.0 引入了一个参数globstar，当该参数打开时，允许**匹配零个或多个子目录。因此，**/*.txt可以匹配顶层的文本文件和任意深度子目录的文本文件。详细介绍请看后面shopt命令的介绍。
  
  
  
	- ls */*.txt 子目录有一个 a.txt
	- **/*.txt 匹配顶层的文本文件和任意深度子目录的文本文件

- 方括号扩展

  方括号扩展的形式是[...]，只有文件确实存在的前提下才会扩展。如果文件不存在，就会原样输出。括号之中的任意一个字符。比如，[aeiou]可以匹配五个元音字母中的任意一个。
  
  # 存在文件 a.txt 和 b.txt
  $ ls [ab].txt
  a.txt b.txt
  
  # 只存在文件 a.txt
  $ ls [ab].txt
  a.txt
  
  上面例子中，[ab]可以匹配a或b，前提是确实存在相应的文件。
  
  方括号扩展属于文件名匹配，即扩展后的结果必须符合现有的文件路径。如果不存在匹配，就会保持原样，不进行扩展。
  
  # 不存在文件 a.txt 和 b.txt
  $ ls [ab].txt
  ls: 无法访问'[ab].txt': 没有那个文件或目录
  
  上面例子中，由于扩展后的文件不存在，[ab].txt就原样输出了，导致ls命名报错。
  
  方括号扩展还有两种变体：[^...]和[!...]。它们表示匹配不在方括号里面的字符，这两种写法是等价的。比如，[^abc]或[!abc]表示匹配除了a、b、c以外的字符。
  
  # 存在 aaa、bbb、aba 三个文件
  $ ls ?[!a]?
  aba bbb
  
  上面命令中，[!a]表示文件名第二个字符不是a的文件名，所以返回了aba和bbb两个文件。
  
  注意，如果需要匹配[字符，可以放在方括号内，比如[[aeiou]。如果需要匹配连字号-，只能放在方括号内部的开头或结尾，比如[-aeiou]或[aeiou-]。
  
  
  [start-end] 扩展
  
  方括号扩展有一个简写形式[start-end]，表示匹配一个连续的范围。比如，[a-c]等同于[abc]，[0-9]匹配[0123456789]。
  
  # 存在文件 a.txt、b.txt 和 c.txt
  $ ls [a-c].txt
  a.txt
  b.txt
  c.txt
  
  # 存在文件 report1.txt、report2.txt 和 report3.txt
  $ ls report[0-9].txt
  report1.txt
  report2.txt
  report3.txt
  ...
  
  下面是一些常用简写的例子。
  
  [a-z]：所有小写字母。
  [a-zA-Z]：所有小写字母与大写字母。
  [a-zA-Z0-9]：所有小写字母、大写字母与数字。
  [abc]*：所有以a、b、c字符之一开头的文件名。
  program.[co]：文件program.c与文件program.o。
  BACKUP.[0-9][0-9][0-9]：所有以BACKUP.开头，后面是三个数字的文件名。
  这种简写形式有一个否定形式[!start-end]，表示匹配不属于这个范围的字符。比如，[!a-zA-Z]表示匹配非英文字母的字符。
  
  $ echo report[!1–3].txt
  report4.txt report5.txt
  
  上面代码中，[!1-3]表示排除1、2和3。
  
  
- 大括号扩展

  
  大括号扩展
  
  大括号扩展{...}表示分别扩展成大括号里面的所有值，各个值之间使用逗号分隔。比如，{1,2,3}扩展成1 2 3。
  
  $ echo {1,2,3}
  1 2 3
  
  $ echo d{a,e,i,u,o}g
  dag deg dig dug dog
  
  $ echo Front-{A,B,C}-Back
  Front-A-Back Front-B-Back Front-C-Back
  
  注意，大括号扩展不是文件名扩展。它会扩展成所有给定的值，而不管是否有对应的文件存在。
  
  $ ls {a,b,c}.txt
  ls: 无法访问'a.txt': 没有那个文件或目录
  ls: 无法访问'b.txt': 没有那个文件或目录
  ls: 无法访问'c.txt': 没有那个文件或目录
  
  上面例子中，即使不存在对应的文件，{a,b,c}依然扩展成三个文件名，导致ls命令报了三个错误。
  
  另一个需要注意的地方是，大括号内部的逗号前后不能有空格。否则，大括号扩展会失效。
  
  $ echo {1 , 2}
  {1 , 2}
  
  上面例子中，逗号前后有空格，Bash 就会认为这不是大括号扩展，而是三个独立的参数。
  
  逗号前面可以没有值，表示扩展的第一项为空。
  
  $ cp a.log{,.bak}
  
  # 等同于
  # cp a.log a.log.bak
  
  大括号可以嵌套。
  
  $ echo {j{p,pe}g,png}
  jpg jpeg png
  
  $ echo a{A{1,2},B{3,4}}b
  aA1b aA2b aB3b aB4b
  
  大括号也可以与其他模式联用，并且总是先于其他模式进行扩展。
  
  $ echo /bin/{cat,b*}
  /bin/cat /bin/b2sum /bin/base32 /bin/base64 ... ...
  
  # 基本等同于
  $ echo /bin/cat;echo /bin/b*
  
  上面例子中，会先进行大括号扩展，然后进行*扩展，等同于执行两条echo命令。
  
  大括号可以用于多字符的模式，方括号不行（只能匹配单字符）。
  
  $ echo {cat,dog}
  cat dog
  
  由于大括号扩展{...}不是文件名扩展，所以它总是会扩展的。这与方括号扩展[...]完全不同，如果匹配的文件不存在，方括号就不会扩展。这一点要注意区分。
  
  # 不存在 a.txt 和 b.txt
  $ echo [ab].txt
  [ab].txt
  
  $ echo {a,b}.txt
  a.txt b.txt
  
  上面例子中，如果不存在a.txt和b.txt，那么[ab].txt就会变成一个普通的文件名，而{a,b}.txt可以照样扩展。
  
  {start..end} 扩展
  
  大括号扩展有一个简写形式{start..end}，表示扩展成一个连续序列。比如，{a..z}可以扩展成26个小写英文字母。
  
  $ echo {a..c}
  a b c
  
  $ echo d{a..d}g
  dag dbg dcg ddg
  
  $ echo {1..4}
  1 2 3 4
  
  $ echo Number_{1..5}
  Number_1 Number_2 Number_3 Number_4 Number_5
  
  这种简写形式支持逆序。
  
  $ echo {c..a}
  c b a
  
  $ echo {5..1}
  5 4 3 2 1
  
  注意，如果遇到无法理解的简写，大括号模式就会原样输出，不会扩展。
  
  $ echo {a1..3c}
  {a1..3c}
  
  这种简写形式可以嵌套使用，形成复杂的扩展。
  
  $ echo .{mp{3..4},m4{a,b,p,v}}
  .mp3 .mp4 .m4a .m4b .m4p .m4v
  
  大括号扩展的常见用途为新建一系列目录。
  
  $ mkdir {2007..2009}-{01..12}
  
  上面命令会新建36个子目录，每个子目录的名字都是”年份-月份“。
  
  这个写法的另一个常见用途，是直接用于for循环。
  
  for i in {1..4}
  do
    echo $i
  done
  
  上面例子会循环4次。
  
  如果整数前面有前导0，扩展输出的每一项都有前导0。
  
  $ echo {01..5}
  01 02 03 04 05
  
  $ echo {001..5}
  001 002 003 004 005
  
  这种简写形式还可以使用第二个双点号（start..end..step），用来指定扩展的步长。
  
  $ echo {0..8..2}
  0 2 4 6 8
  
  上面代码将0扩展到8，每次递增的长度为2，所以一共输出5个数字。
  
  多个简写形式连用，会有循环处理的效果。
  
  $ echo {a..c}{1..3}
  a1 a2 a3 b1 b2 b3 c1 c2 c3
  
	- mkdir {2007..2009}-{01..12}

- 变量扩展

  Bash 将美元符号$开头的词元视为变量，将其扩展成变量值，详见《Bash 变量》一章。
  
  $ echo $SHELL
  /bin/bash
  
  变量名除了放在美元符号后面，也可以放在${}里面。
  
  $ echo ${SHELL}
  /bin/bash
  
  ${!string*}或${!string@}返回所有匹配给定字符串string的变量名。
  
  $ echo ${!S*}
  SECONDS SHELL SHELLOPTS SHLVL SSH_AGENT_PID SSH_AUTH_SOCK
  
  上面例子中，${!S*}扩展成所有以S开头的变量名。
  
  
	- ${!S*}扩展成所有以S开头的变量名。

- 子命令扩展

  
  子命令扩展
  
  $(...)可以扩展成另一个命令的运行结果，该命令的所有输出都会作为返回值。
  
  $ echo $(date)
  Tue Jan 28 00:01:13 CST 2020
  
  上面例子中，$(date)返回date命令的运行结果。
  
  还有另一种较老的语法，子命令放在反引号之中，也可以扩展成命令的运行结果。
  
  $ echo `date`
  Tue Jan 28 00:01:13 CST 2020
  
  $(...)可以嵌套，比如$(ls $(pwd))。
  
  
  
- 算术扩展

  
  算术扩展
  
  $((...))可以扩展成整数运算的结果，详见《Bash 的算术运算》一章。
  
  $ echo $((2 + 2))
  4
  
## # 1. Hello Bash Script 

### # echo "hello bash linuxhint audience" > file.txt

## # 2. Rediret to file

### # wait for user input,until user press c-c to stop the process,go and check the file

### # cat > file.txt

### # append some text to the file

### # cat >> file.txt

## # 3. comment 

###     # one line comment with hash

###     # multi-line comment colon+space+single quote single quote

###     : '

###     this is a cat command

###     this is a cat command'

###     # here doc delimiter

###     : '

###     cat << kceativ

###     this is hello  creative text

###     add another line

###     kceativ'

## # 4. conditional statements

### 1.if判断单分支

- 语法格式：

	- if 条件测试命令
	- then 命令序列
	- fi

- 例子：

	- 如果/boot分区的控件使用超过50%，则输出警告：

		- #!/bin/bash
RATE=`df -hT | grep "/run" | awk '{print $6}' | cut-d "%" -f1`
if [ $RATE -gt 50 ]
then 
      echo "Warning,/boot DISK is full!"
fi

### 2.if判断双分支

- 语法格式

	- if 条件测试命令
	- then 命令序列1
	- else 命令序列2
	- fi

- 例子:

	- 判断服务是否启动，如果没有启动则启动

		- #!/bin/bash
http=`netstat -tlun | awk '{print $4 "\n"}' | grep ":80$"`
(或http=$( ps aux | grep httpd | grep -v grep ))

		- if [ -z "$http" ]
then 
       echo "httpd do not run!"
       /usr/bin/nginx
else 
      echo "httpd running"
fi
		- service mysql start

### 3.if判断多分支

- 语法格式：

	- if 条件测试命令1;
then
       命令序列1
elif 条件测试命令2;
then
       命令序列2
elif ...
else
命令序列n
fi

- 例子：

	- echo "Mandarin Chinese,please press 1"
	- echo "English,please press 2"
	- echo "changshahua, please press 3"
	- read -p "please input a num:" -t 30 num
	- if [ "$num" == "1" ]
	- then 
	-     echo "Mandarin"
	- elif [ "$num" == "2" ]
	- then 
	-     echo "English"
	- elif [ "$num" == "3" ]
	- then 
	-     echo "changshahua"
	- else 
	-     echo "error,please press again!"
	- fi

### # -gt -ne

- : '
- count=10
- if [ $count -eq 10 ]
- then
-     echo "the condition is true"
- else 
-     echo "the condition is false"
- fi'

### # > <

- # (( $count > 9 ))
- : '
- if (( $count < 9 ))
- then 
-     echo "first condition is true"
- elif (( $count > 9 ))
- then
-     echo "second condition is true"
- else 
-     echo "the coudition is false"
- fi'

### # and

- 第一种:&&

	- : '
	- age=30
	- if [ "$age" -gt 18 ] &&  ["$age" -lt 40 ] 
	- then 
	-     echo "Age is correct"
	- else 
	-     echo "Age is not correct"
	- fi'

- 第二种:-a

	- : '
	- age=30
	- if [ "$age" -gt 18  -a  "$age" -lt 40 ] 
	- then 
	-     echo "Age is correct"
	- else 
	-     echo "Age is not correct"
	- fi'

### # or

- 第一种

	- : '
	- age=30
	- if [ "$age" -lt 18  -o  "$age" -lt 40 ] 
	- then 
	-     echo "Age is correct"
	- else 
	-     echo "Age is not correct"
	- fi'

- 第二种

	- : '
	- age=30
	- if [[ "$age" -lt 18 || "$age" -lt 40 ]]
	- then 
	-     echo "Age is correct"
	- else 
	-     echo "Age is not correct"
	- fi'

- 第三种

	- : '
	- age=30
	- if [ "$age" -lt 18 ] || [ "$age" -lt 40 ]
	- then 
	-     echo "Age is correct"
	- else 
	-     echo "Age is not correct"
	- fi'

### # case

## # 5. loops

### 第一种：while

- : '
number=1
while [ $number -lt 10 ]
do
    echo "$number"
    number=$(( number+1 ))
done'
- 例子

	- cat /etc/passwd
cat /etc/passwd | grep "/bin/zsh"
# 批量添加用户
i=1
while [ $i -le 20 ]
do
    useradd xiaoyu$i
    echo "123456" | passwd --stdin xiaoyu$i &>/dev/null
    i=$(($i+1))
done

# 批量删除的话 直接 userdel -r xiaoyu$i

### 第二种： until

- : '
number=1
until [ $number -ge 10 ]
do 
    echo "$number"
    number=$(( number+1 ))
done'

### 第三种：for in

- 语法：

	- 根据变量的不同取值，重复执行一组命令操作：
格式：
for 变量名 in 取值列表
do
命令序列
done

- 例子1：

	- for i in 1 2 3 4 5
do
    echo $i
done

- 例子2：

	- for num in 1 2 3 4 5
do
      echo $num
done

- 例子3：

	- a=`ls /mnt/d/Github`
for file in $a
do
    echo $file
done

- 例子4：

	- # 输入目录名，显示目录下所有内容
read -p "please input a filename:" -t 30 filename
if [ -z $filename ];then
    echo "please input filename"
    exit 1
fi
if [ ! -e $filename ];then
    echo  "$filename not in" 
    exit 2
fi
if [ ! -d $filename ];then
    echo "$filename is not directory"
    exit 3
fi
file=`ls $filename`
for test in $file
do
    echo $test
done

### 第四种：for in：# {start..ending..increment}

- : '
for i in {0..20..2} 
do
    echo $i
done'

### case多重分支语句：

- 根据变量的不同取值，分别执行不同的目录操作
- 例子：

	- echo "Mandarin Chinese,please press 1"
echo "English,please press 2"
echo "changshahua, please press 3"

read -p "please input a num:" -t 30 num

case $num in
    "1")
        echo "Mandarin"
        ;;
    "2")
        echo "English"
        ;;
    "3")
        echo "changshahua"
        ;;
    *)
        echo "error,please input 1 or 2 or 3"
        ;;
esac

### 第五种：for

- 例子1

	- for (( i=0; i<5;i++ ))
do
    echo $i
done'

- 例子2:数值循环

	- s=0
for ((i=1;i<=100;i++))
do 
     s=$(($s+$i))
done
echo $s

### # break

- : '
for (( i=0;i<=10;i++ ))
do 
    if [ $i -gt 5 ]
    then 
        break
    fi
    echo $i
done'

### # continue out of the loop

- : '
for (( i=0;i<=10;i++ ))
do 
    if [ $i -eq 3 ] || [ $i -eq 7 ]
    then 
        continue
    fi
    echo $i
done'

## # 6. script input

### # argument 0,1,2,3  $0 is script itself
# echo $0 $1 $2 $3

-  args=("$@")
- # echo ${args[0]} ${args[1]} ${args[2]}
- # echo $@
- # length of args
- # echo $#

### read 

- : '
- while read line 
- do 
-     echo "$line"
- done < "${1:-/dev/stdin}" '

## # 7.output 

### ls -la 1>file1.txt 2>file2.txt

### ls +la > file1.txt 2>&1

## # 2021-05-04 i can follow again

### # 输出重定向

- 设备文件名 #文件描述符 # 默认设备
-  标准输入 /dev/stdin 0 键盘
-  标准输出 /dev/stdout 1 显示器
-  标准错误输出 /dev/stderr 2 显示器
-  输出重定向概念:
-    把应该输出到屏幕的输出，重定向到文件
-    > 覆盖 >> 追加
-  例如: ls > aa 覆盖到aa ls>>aa 追加到aa
-  ls abcde 2 >> aa 错误信息输出到aa
-  强调：错误输出，不能有空格
-  ls &>aa 错误和正确都输入到aa
-  ls >> aa 2>>bb 正确信息输入aa，错误信息输入bb
-  ls 1>>aa 2>>bb
-  ls >> aa 2>&1 错误和正确都输入到aa，可以追加
-  2会先重定向到1打包的输入而不是1文件，然后在追加到aa中来
-  2>1和2>&1的写法有什么区别：
-  2>1的作用是把标准错误的输出重定向到1，但这个1不是标准输出，而是一个文件!!!,文件名就是1；
-  2>&1的作用是把标准错误的输出重定向到标准输出1，&指示不要把1当作普通文件，而是fd=1即标准输出来处理。

### # 多命令顺序执行

- 1. command1;command2;
- 2. command1 && command2
- 3. command1 || command2
- 4. command1 | command2 命令1执行的结果当做命令2的执行条件

	- netstat -tlun | grep 80 查询监听端口号，并查看80端口是否启动
	- ls -l /etc/ | more 分屏显示ls内容
	- ls -l /etc/ | grep yum

### # 变量

- 1. 分类： 本地变量，环境变量，位置参数变量，预定义变量
- 2. 本地变量：

	-     变量名和值不能是特殊符号
	-     声明: 变量名=变量值
	-     注意：=号两边不能有空格
	-     aa=123
	-     调用: echo $aa

- 3. 查看变量

	-    set 查看所有变量，包含环境变量和本地变量 

- 4. 删除变量

	-     unset 

- 5. 变量设定规则

	-     1》变量以等号连接值，等号不能有空格
	-     2》变量名由数字和字母和下划线组成，不能以数字开头
	-     3》变量值中有空格，用引号括起来

		-     aa="hellow world"
		-     echo "$aa" # hello world
		-     echo '$aa' # $aa
		-     bb="ls" 
		-     echo $bb # bb
		-     bb=ls
		-     echo $bb # bb
		-     bb=`ls`
		-     echo $bb # ls输出
		-     bb=$(ls)
		-     echo $bb # ls输出

	-     4》双引号内，有特殊字符。如$
	-     5》单引号中特殊字符无含义
	-     6》在变量值中，可以输入\转义符
	-     7》变量值可以直接调用系统命令。`命令` $(命令)
	-     8》变量值可以累加 aa=123 aa="$aa"456,ehco $aa --->123456

### # 环境变量

- 作用域

	- set 
	- bash进入子bash
	- pstree查看级别
	- set
	- exit返回上一次
	- pstree

- 1. 环境变量

	-     1》声明

		-         export 变量名=变量名
		-         export aa

	-     2》查看

		-         set 查看所有变量
		-         env 
		-         export 只能查看环境变量
		-             declare 声明变量类型的，如果不特别声明，所有变量为字符串型
		-             -i 声明为int
		-             -x 声明为环境变量

	-     3》删除

		-         unset 变量
		- ./helloScript.sh 能执行
		- helloScript.sh 无法执行
		- 环境变量中加入当前目录，之后就可以直接执行了

- 2. 如何加入环境变量

	- echo $PATH
	- export PATH="$PATH":/root/xiaoyu
	- echo $PATH

- 3. 常用环境变量

	- echo $PATH 系统查找命令的路径
	- PATH="$PATH":/root/xiaoyu 在系统默认路径后，追加/root/xiaoyu 目录作为目录查找路径（临时生效）

- 4. 环境变量配置文件

	-   /etc/profile
	-   /etc/bashrc  所有用户生效
	-   ~/.bashrc
	-   ~/.bash_profile 只对指定用户生效

- 5. 位置参数变量

	-     $0 命令自己
	-     $1 第一个参数
	-     $2 第二个参数
	-     $9 第几个参数
	-     最多九个参数
	-     例如：输出位置参数变量
	-     #!/bin/bash
	-     echo "the command is $0"
	-     echo "canshu1 is $1"
	-     echo "canshu2 is $2"

- 6. 预定义变量

	-     $? 上一个命令的返回值。0 上一个命令正确执行，非0 上一个命令不正确
	-     $# 统计命令之后的参数个数
	-     $* 返回所有参数
	-     $n 位置参数变量
	- 例如： 输出预定义变量
	- #!/bin/bash
	- echo "canshu zongshu $#"
	- echo "canshu liebiao:$*"
	- echo $?

### # read命令

-     read -p ”提示信息“ -t 等待时间 变量名
- 例子：通过read读入变量值
- #!/bin/bash
- read -p "please input num1:" -t 30 test1
- read -p "input num2:" -t 30 test2
- sum=$(( $test1 + $test2 ))
- echo "$test1 + $test2 = $sum"
- 需要计算的表达式形式为：$((  ))

### # 数值运算

- 变量值默认都是字符串类型，要想进行数值运算。以下三种，任选一种：
- 1. declare方法

	-     num1=123
	-     num2=456
	-     declare -i sum=$num1+$sum2
	- 注意+两边不能有空格

- 2. sum=$(( $num1 + $num2 ))

	- 注意：加号两边带不带空格都可以

- 3. sum=$(expr $num1 + $num2 )

	- 注意：+左右必须空格

- 4. 运算符

	- +-\*/%取余

### # shell 中常用命令

- 1. 行提取命令grep

	- 选项：-v 反向选择
	-       -n 提取时，显示行号
	- 举例：
	-     grep "[^a-z]abc" test.txt
	-     abc前不是小写字母的行匹配
	-     grep "\.$" test.txt
	-     匹配以.结尾的行
	-     grep "^[^A-Za-z]" test.txt
	-     匹配不易字母开头的行

- 2. 列提出命令 cut

	- 语法： cut -d "分隔符" -f 提取列 文件名
	- 举例：
	-     more /etc/passwd | grep "/bin/bash" | cut -d ":" -f 1,3 
	-     提取passwd文件中可以登录的用户的用户名和UID
	-     cut -d " " -f 1,3 test.txt

-     3. awk

	-     awk '条件 {动作}'
	-     last | awk '{printf $1 "\t" $3 "\n"}'
	-     条件不给 默认 以空格当做分割
	-     提取last显示结果的第一和第三列
	-     ps -ef | awk '{printf $1 "\t" $3 "\n"}'
	- 举例：
	- last | grep "[0-9]\{1,3\})(\.)\1\2\1\2\1" | awk `{prinf $1 "\t" $3 "\n"}`
	-     在last中提取包含ip的行，在行中提取第一和第三列

- 4. echo命令

	- echo -e "123\t456\n"
	- echo -e "\e[1;31m this is red text \e[0m" 输出红色字体
	- \e[ 格式
	- 1;31m 指定颜色
	- 0m 恢复颜色（重置）
	- 30m=黑色，31=红色，32m=绿色，33m=黄色，34m=蓝色，35m=洋红，36m=青色，37=白色
	- echo -e "\e[1:42 backgroud \e[0m"
	- 背景颜色：40=黑色，41=红色，42=绿色，43=黄色，44=蓝色，45=洋红，46=青色，47=白色
	- jimu.sh 俄罗斯方块游戏
	- shutdown -r now
	- 关机服务器

### 条件测试

- 语法格式： test 测试条件 测试内容
- 或者：[ 测试条件 测试内容 ]
- 测试文件类型：

	- test -e 文件名 ： 测试文件是否存在，存为未真
[ -e 文件名 ]  ：注意：[]中必须有空格
	- test -f 文件名： 判断是否是普通文件
	- test -d 文件名：判断是都为目录
	- test -b 文件名：判断是否为块设备文件
	- test -c 文件名：判断是否为字符设备文件
	- 所有test 都会返回true or false 但是不会输出，需要通过$? 拿到返回结果是否是0，是0 为true。
或者通过test -c file.txt && echo yes || echo no

- 测试文件权限

	- test -r 文件名：判断是否有可读权限
	- test -w 文件名：判断是否有可写权限
	- test -x 文件名：判断是否有可执行权限
	- test -s 文件名 判断是否为为空白，有内容为真

- 判断两个文档

	- [ file1 -nt file2 ] : file1 是否比file2新
	- [ file1 -ot file2 ] : file1是否比file2旧
	- [ file1 -ef file2 ] : file1 与file2是否是链接文件
FILE1 and FILE2 have the same device and inode numbers

### 两个数值之间判断：

- [ n1 -eq n2 ]  n1和n2是否相等
- [ n1 -ne n2 ] n1和n2是否不等
- [ n1 -gt n2 ] n1大于n2
- [ n1 -lt n2 ] n1小于n2
- [ n1 -ge n2 ] n1大与等于n2
- [ n1 -1e n2 ] n1小于等于n2

### 判断字符串

- [ -z 字符串 ] 判断字符串是否为空
- [字符串1 == 字符串2 ] 判断字符串1是否与字符串2相等
- [ $aa == $bb ] && echo yes || echo no
- [ 字符串1 != 字符串2  ] 判断字符串是否不相等

### 多重判断

- -a 逻辑与
[ -z $file -a -e $file ]
- -o 逻辑或
- ! 逻辑非

### 常用的一些shell语句

- # bash script
- read -p  "please input your filename:" -t 30 filename
- test -z $filename && echo "please input your filename!!" && exit 1
- test ! -e $filename && echo "file do not exist!!" && exit 2
- test -f $filename && filetype=common
- test -d $filename && filetype=directory
- test -r $filename && permission=read
- test -w $filename && permission="$permission write"
- test -x $filename && permission="$permission executable"
- echo -e "the filename is: $filename \n"
- echo -e "filetype is: $filetype \n"
- echo -e "permission is: $permission \n"

## [bash网址](https://wangdoc.com/bash/expansion.html)

