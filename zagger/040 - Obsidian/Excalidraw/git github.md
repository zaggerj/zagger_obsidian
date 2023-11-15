---
created: 2023-11-15T20:48
updated: 2023-11-15T20:48
---
# git github

## 命令集合

### [github打不开解决方式](https://blog.csdn.net/A_pointer2/article/details/113362994)

somebody says：今天有人说不知为何最近网络不太正常。这就是年轻人不知节气，不懂时令。每年惊蛰、芒种前后网络都会不太好，需要提前做准备。惊蛰是万物复苏的时候，海里的蛤蟆虾米咸带鱼也开始活动，所以会影响到海底光缆。而芒种又要收麦子又要种晚稻，一收一种，上行流量和下行流量同时激增，必然影响网络访问。

# GitHub Start 
140.82.113.3      github.com
140.82.114.20     gist.github.com

151.101.184.133    assets-cdn.github.com
151.101.184.133    raw.githubusercontent.com
199.232.28.133     raw.githubusercontent.com 
151.101.184.133    gist.githubusercontent.com
151.101.184.133    cloud.githubusercontent.com
151.101.184.133    camo.githubusercontent.com
199.232.96.133     avatars.githubusercontent.com
151.101.184.133    avatars0.githubusercontent.com
199.232.68.133     avatars0.githubusercontent.com
199.232.28.133     avatars0.githubusercontent.com 
199.232.28.133     avatars1.githubusercontent.com
151.101.184.133    avatars1.githubusercontent.com
151.101.108.133    avatars1.githubusercontent.com
151.101.184.133    avatars2.githubusercontent.com
199.232.28.133     avatars2.githubusercontent.com
151.101.184.133    avatars3.githubusercontent.com
199.232.68.133     avatars3.githubusercontent.com
151.101.184.133    avatars4.githubusercontent.com
199.232.68.133     avatars4.githubusercontent.com
151.101.184.133    avatars5.githubusercontent.com
199.232.68.133     avatars5.githubusercontent.com
151.101.184.133    avatars6.githubusercontent.com
199.232.68.133     avatars6.githubusercontent.com
151.101.184.133    avatars7.githubusercontent.com
199.232.68.133     avatars7.githubusercontent.com
151.101.184.133    avatars8.githubusercontent.com
199.232.68.133     avatars8.githubusercontent.com
199.232.96.133     avatars9.githubusercontent.com
199.232.96.133     avatars.githubusercontent.com

# GitHub End
ps：https://blog.csdn.net/A_pointer2/article/details/113362994

### git命令大全

常用命令大全 我们我们开发时候在工作区，当我们把修改，add之后，修改内容会被提到暂存区，当我们commit 之后修改的内容 会被提到我们本地的仓库（repository）,当我们push之后，会被提到远程仓库（remote） Workspace：工作区 Index / Stage：暂存区 Repository：仓库区（或本地仓库） Remote：远程仓库 一、新建代码库 在当前目录新建一个Git代码库 git init 新建一个目录，将其初始化为Git代码库 git init [project-name] 下载一个项目和它的整个代码历史 git clone [url] 生成ssh git config --global user.name "yk" 添加邮箱 git config --global user.email "youremail@163.com" 生成公钥 生成ssh-keygen -t rsa -C "你的邮箱" 连续回车 ssh-keygen -t rsa 生成公钥 （然后有个C盘的路径，沿着那个路径找到那个文件，把里面的内容粘贴过来，在GitHub上那个ssh，设置秘钥，密码粘进去） 添加到暂存区 添加指定文件到暂存区 git add [file1] [file2] ... 添加指定目录到暂存区，包括子目录 $ git add [dir] 添加当前目录的所有文件到暂存区 $ git add . 添加每个变化前，都会要求确认 对于同一个文件的多处变化，可以实现分次提交 git add -p 删除工作区文件，并且将这次删除放入暂存区 git rm [file1] [file2] ... 改名文件，并且将这个改名放入暂存区 git mv [file-original] [file-renamed] 代码提交 提交暂存区到仓库区 git commit -m [message] 提交暂存区的指定文件到仓库区 git commit [file1] [file2] ... -m [message] 使用一次新的commit，替代上一次提交 如果代码没有任何新变化，则用来改写上一次commit的提交信息 git commit --amend -m [message] 分支 查看所有分支 git branch -a 查看所有远程分支 git branch -r 查看所有本地分支 git branch 新建一个分支，但依然停留在当前分支 git branch [branch-name] 新建一个分支，并切换到该分支 git checkout -b [branch] 切换到指定分支，并更新工作区 git checkout [branch-name] 切换到上一个分支 git checkout - 合并指定分支到当前分支 git merge [branch] 删除本地分支 git branch -d  强制删除本地分支 git branch -D  删除远程分支 git push origin --delete [branch-name] git branch -dr [remote/branch] 新建一个分支，与指定的远程分支建立追踪关系 git branch --track [branch] [remote-branch] git branch -d 删除分支，会在删除前检查merge状态，避免误删没有合并的分支。 git branch -D 是git branch --delete --force的简写，它会强制删除该分支。 如果想要删除远程分支以及追踪分支需使用: git push --origin -delete branch 查看信息 显示有变更的文件 git status 显示当前分支的版本历史 git log 如果嫌输出信息太多，看得眼花缭乱的，可以试试加上--pretty=oneline参数： git log --pretty=oneline 搜索提交历史，根据关键词 $ git log -S [keyword] 显示某个文件的版本历史，包括文件改名 git log --follow [file] git whatchanged [file] 显示过去5次提交 git log -5 --pretty --oneline 显示暂存区和工作区的差异 git diff 显示当前分支的最近几次提交 git reflog 远程同步 上传本地指定分支到远程仓库 git push [remote] [branch] 强行推送当前分支到远程仓库，即使有冲突 git push [remote] --force 推送所有分支到远程仓库 git push [remote] --all 下载远程仓库的所有变动 git fetch [remote] 显示所有远程仓库 git remote -v 增加一个新的远程仓库，并命名 git remote add [shortname] [url] 取回远程仓库的变化，并与本地分支合并 git pull [remote] [branch] 撤销 恢复暂存区的指定文件到工作区 git checkout [file] 恢复暂存区的所有文件到工作区 git checkout . 重置暂存区的指定文件，与上一次commit保持一致，但工作区不变 git reset [file] 重置暂存区与工作区，与上一次commit保持一致 git reset --hard 恢复某个commit的指定文件到暂存区和工作区 git checkout [commit] [file] 重置当前分支的指针为指定commit，同时重置暂存区，但工作区不变 git reset [commit] 重置当前分支的HEAD为指定commit，同时重置暂存区和工作区，与指定commit一致 git reset --hard [commit] git reset --hard 1094a //返回到指定某一版本 Git必须知道当前版本是哪个版本，在Git中，用HEAD表示当前版本，也就是最新的提交1094adb...（注意我的提交ID和你的肯定不一样），上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。 git reset --hard HEAD^ //返回上一个版本 暂时将未提交的变化移除，稍后再移入 $ git stash $ git stash pop 

### git reflog show --date=iso 5.2.0-uos

### git diff ^5.2.0-vpc 5.2.0-uos --stat | grep -v "resources\| built\| .data\| js/all.bundle.js\| zips\| *.json\| yarn*"

### [git config --global --replace-all core.pager "less -F -X"](https://stackoverflow.com/questions/2183900/how-do-i-prevent-git-diff-from-using-a-pager/2183920)

### git add -u <==> git add –update

### [git rm -rf configstore/  删除忽略文件，文件夹中的文件改动](https://www.jianshu.com/p/e5b13480479b)

### git status

- 如果你使用 git status -s 命令或 git status --short 命令，你将得到一种格式更为紧凑的输出

  $ git status -s
   M README
  MM Rakefile
  A  lib/git.rb
  M  lib/simplegit.rb
  ?? LICENSE.txt
  新添加的未跟踪文件前面有 ?? 标记，新添加到暂存区中的文件前面有 A 标记，修改过的文件前面有 M 标记。 输出中有两栏，左栏指明了暂存区的状态，右栏指明了工作区的状态。例如，上面的状态报告显示： README 文件在工作区已修改但尚未暂存，而 lib/simplegit.rb 文件已修改且已暂存。 Rakefile 文件已修，暂存后又作了修改，因此该文件的修改中既有已暂存的部分，又有未暂存的部分。
  
  
  
### git checkout --ours {codefiles} 保留当前分支代码

### git checkout --theirs {codefiles} 保留要合并分支代码

### git checkout 'HEAD' built/*

### git log -p --word-diff built/0.js

### 删除项目中的所有.DS_Store。这会跳过不在项目中的 .DS_Store

- 1.find . -name .DS_Store -print0 | xargs -0 git rm -f --ignore-unmatch
将 .DS_Store 加入到 .gitignore
2.echo .DS_Store >> ~/.gitignore
更新项目
3.git add --all
4.git commit -m '.DS_Store banished!'

### 只需要删除磁盘上的 .DS_Store: 删除当前目录及其子目录下的所有.DS_Store 文件

- find . -name '*.DS_Store' -type f -delete

### 禁用或启用自动生成
禁止.DS_store生成：
defaults write com.apple.desktopservices DSDontWriteNetworkStores -bool TRUE

恢复.DS_store生成：恢复.DS_store生成：
defaults delete com.apple.desktopservices DSDontWriteNetworkStores

## [github 分析网站推荐](https://zhuanlan.zhihu.com/p/107503801)

### https://www.zhihu.com/search?type=content&q=onefetch

## [SSHkey](https://segmentfault.com/a/1190000013759207)

## 多个SSHKey配置生效的代码

Host github.com
HostName github.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/github
User zaggerj

Host e.coding.net
HostName e.coding.net
PreferredAuthentications publickey
IdentityFile ~/.ssh/coding.net
User zaggerj

Host 172.16.203.254
HostName 172.16.203.254
PreferredAuthentications publickey
IdentityFile ~/.ssh/gitlab
User zagger

Host gitee.com
HostName gitee.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/gitee
User zagger

##  proxychains git push gitee master 

###  proxychains

## git 基础

### 工作副本

### 快照

### 仓库

### 工作目录

- 已跟踪文件
- 未跟踪文件

### 暂存区

- stage

### 跟踪新文件 

- git add file

	- 文件处于已暂存状态

		- 只要在 Changes to be committed 这行下面的，就说明是已暂存状态

	- 该文件的版本将被留存在后续的历史记录中
	- git add 命令使用文件或目录的路径作为参数；如果参数是目录的路径，该命令将递归地跟踪该目录下的所有文件。

### 暂存已修改的文件

- 出现在 Changes not staged for commit 这行下面，说明已跟踪文件的内容发生了变化，但还没有放到暂存区
- 要暂存这次更新，需要运行 git add 命令

	- 功能

		- 1. 开始跟踪新文件
		- 2. 把已跟踪的文件放到暂存区
		- 3.  用于合并时把有冲突的文件标记为已解决状态等

	- git add命令的理解：

		- 精确地将内容添加到下一次提交中

- 假设此时，你想要在 CONTRIBUTING.md 里再加条注释

	-  文件同时出现在暂存区和非暂存区
	- 实际上 Git 只不过暂存了你运行 git add 命令时的版本，而不是你运行git commit时，工作目录中的当前版本

		- 运行了 git add 之后又作了修订的文件，需要重新运行 git add 把最新版本重新暂存起来

### 状态简览

- git status 命令的输出十分详细，但其用语有些繁琐。
-  Git 有一个选项可以帮你缩短状态命令的输出，这样可以以简洁的方式查看更改。 如果你使用 git status -s 命令或 git status --short 命令，你将得到一种格式更为紧凑的输出。

	-  输出中有两栏，左栏指明了暂存区的状态，右栏指明了工作区的状态。
	- 新添加的未跟踪文件前面有 ?? 标记
	- 新添加到暂存区中的文件前面有 A 标记
	- 修改过的文件前面有 M 标记，README 文件在工作区已修改但尚未暂存
	-  lib/simplegit.rb 文件已修改且已暂存
	- Rakefile 文件已修，暂存后又作了修改，因此该文件的修改中既有已暂存的部分，又有未暂存的部分。
	- 例子：

		- $ git status -s
 M README
MM Rakefile
A  lib/git.rb
M  lib/simplegit.rb
?? LICENSE.txt

### 忽略文件

- 一般我们总会有些文件无需纳入 Git 的管理，也不希望它们总出现在未跟踪文件列表
- 通常都是些自动生成的文件，比如日志文件，或者编译过程中创建的临时文件等
- .gitignore规范格式

  文件 .gitignore 的格式规范如下：
  所有空行或者以 # 开头的行都会被 Git 忽略。
  
  可以使用标准的 glob 模式匹配，它会递归地应用在整个工作区中。
  匹配模式可以以（/）开头防止递归。
  
  匹配模式可以以（/）结尾指定目录。
  
  要忽略指定模式以外的文件或目录，可以在模式前加上叹号（!）取反。
  所谓的 glob 模式是指 shell 所使用的简化了的正则表达式。 星号（*）匹配零个或多个任意字符；[abc] 匹配任何一个列在方括号中的字符 （这个例子要么匹配一个 a，要么匹配一个 b，要么匹配一个 c）； 问号（?）只匹配一个任意字符；如果在方括号中使用短划线分隔两个字符， 表示所有在这两个字符范围内的都可以匹配（比如 [0-9] 表示匹配所有 0 到 9 的数字）。 使用两个星号（**）表示匹配任意中间目录，比如 a/**/z 可以匹配 a/z 、 a/b/z 或 a/b/c/z 等。
  
  # 忽略所有的 .a 文件
  *.a
  
  # 但跟踪所有的 lib.a，即便你在前面忽略了 .a 文件
  !lib.a
  
  # 只忽略当前目录下的 TODO 文件，而不忽略 subdir/TODO
  /TODO
  
  # 忽略任何目录下名为 build 的文件夹
  build/
  
  # 忽略 doc/notes.txt，但不忽略 doc/server/arch.txt
  doc/*.txt
  
  # 忽略 doc/ 目录及其所有子目录下的 .pdf 文件
  doc/**/*.pdf
  Tip | GitHub 有一个十分详细的针对数十种项目及语言的 .gitignore 文件列表， 你可以在 https://github.com/github/gitignore 找到它。
  Note | 在最简单的情况下，一个仓库可能只根目录下有一个 .gitignore 文件，它递归地应用到整个仓库中。 然而，子目录下也可以有额外的 .gitignore 文件。子目录中的 .gitignore 文件中的规则只作用于它所在的目录中。 （Linux 内核的源码库拥有 206 个 .gitignore 文件。）多个 .gitignore 文件的具体细节超出了本书的范围，更多详情见 man gitignore 。
  
	- # 忽略所有的 .a 文件
*.a

# 但跟踪所有的 lib.a，即便你在前面忽略了 .a 文件
!lib.a

# 只忽略当前目录下的 TODO 文件，而不忽略 subdir/TODO
/TODO

# 忽略任何目录下名为 build 的文件夹
build/

# 忽略 doc/notes.txt，但不忽略 doc/server/arch.txt
doc/*.txt

# 忽略 doc/ 目录及其所有子目录下的 .pdf 文件
doc/**/*.pdf
	- Tip：GitHub 有一个十分详细的针对数十种项目及语言的 .gitignore 文件列表， 你可以在 https://github.com/github/gitignore 找到它。
	- Note：在最简单的情况下，一个仓库可能只根目录下有一个 .gitignore 文件，它递归地应用到整个仓库中。 然而，子目录下也可以有额外的 .gitignore 文件。子目录中的 .gitignore 文件中的规则只作用于它所在的目录中。 （Linux 内核的源码库拥有 206 个 .gitignore 文件。）

多个 .gitignore 文件的具体细节超出了本书的范围，更多详情见 man gitignore 。

- 例子：

	- $ cat .gitignore
*.[oa]
*~

		- 第一行告诉 Git 忽略所有以 .o 或 .a 结尾的文件

			- 一般这类对象文件和存档文件都是编译过程中出现的

		- 第二行告诉 Git 忽略所有名字以波浪符（~）结尾的文件

			- 许多文本编辑软件（比如 Emacs）都用这样的文件名保存副本

### 查看已暂存和未暂存的修改

- git diff 命令

	- git diff通常可能会用它来回答这两个问题：当前做的哪些更新尚未暂存？ 有哪些更新已暂存并准备好下次提交？
	- 虽然 git status 已经通过在相应栏下列出文件名的方式回答了这个问题，但 git diff 能通过文件补丁的格式更加具体地显示哪些行发生了改变。
	- git diff：此命令比较的是工作目录中当前文件和暂存区域快照之间的差异

		-  也就是修改之后还没有暂存起来的变化内容。

	- git diff --staged：这条命令将比对已暂存文件与最后一次提交的文件差异
	- Note：Git Diff 的插件版本
在本书中，我们使用 git diff 来分析文件差异。 但是你也可以使用图形化的工具或外部 diff 工具来比较差异。 可以使用 git difftool 命令来调用 emerge 或 vimdiff 等软件（包括商业软件）输出 diff 的分析结果。 使用 git difftool --tool-help 命令来看你的系统支持哪些 Git Diff 插件。

### 提交更新

- git commit

	- 确认还有什么已修改或新建的文件还没有 git add 过， 否则提交的时候不会记录这些尚未暂存的变化

		- git commit
		- 这样会启动你选择的文本编辑器来输入提交说明。
		- Note：启动的编辑器是通过 Shell 的环境变量 EDITOR 指定的，一般为 vim 或 emacs。 当然也可以按照 起步 介绍的方式， 使用 git config --global core.editor 命令设置你喜欢的编辑器。

- git commit -v

	- 更详细的内容修改提示可以用 -v 选项查看，这会将你所作的更改的 diff 输出呈现在编辑器中，以便让你知道本次提交具体作出哪些修改。

- git commit -m "Story 182: Fix benchmarks for speed"
- 提交时记录的是放在暂存区域的快照

	- 任何还未暂存文件的仍然保持已修改状态，可以在下次提交时纳入版本管理
	- 每一次运行提交操作，都是对你项目作一次快照，以后可以回到这个状态，或者进行比较。

### 跳过使用暂存区域

- 给 git commit 加上 -a 选项

	- 提交之前不再需要 git add 文件“CONTRIBUTING.md”了。 这是因为 -a 选项使本次提交包含了所有修改过的文件。 这很方便

### 移除文件

- 要从 Git 中移除某个文件

	- 必须要从已跟踪文件清单中移除（确切地说，是从暂存区域移除），然后提交。
	- 可以用 git rm 命令完成此项工作

		- 并连带从工作目录中删除指定的文件，这样以后就不会出现在未跟踪文件清单中了

	- 如果只是简单地从工作目录中手工删除文件

		- 运行 git status 时就会在 “Changes not staged for commit” 部分（也就是 未暂存清单）看到

	- git rm PROJECTS.md

		- 下一次提交时，该文件就不再纳入版本管理了

	- git rm --cached README

		- 你想让文件保留在磁盘，但是并不想让 Git 继续跟踪。
		- 当你忘记添加 .gitignore 文件，不小心把一个很大的日志文件或一堆 .a 这样的编译生成文件添加到暂存区时

	- git rm log/\*.log

		- 注意到星号 * 之前的反斜杠 \， 因为 Git 有它自己的文件模式扩展匹配方式，所以我们不用 shell 来帮忙展开。 此命令删除 log/ 目录下扩展名为 .log 的所有文件

	- $ git rm \*~

		- 该命令会删除所有名字以 ~ 结尾的文件。

### 移动文件

-  如果在 Git 中重命名了某个文件，仓库中存储的元数据并不会体现出这是一次改名操作
- git mv file_from file_to

	- 即便此时查看状态信息，也会明白无误地看到关于重命名操作的说明
	- 其实，运行 git mv 就相当于运行了下面三条命令：

		- $ mv README.md README
		- $ git rm README.md
		- $ git add README

	- 如此分开操作，Git 也会意识到这是一次重命名，所以不管何种方式结果都一样。 

		- 两者唯一的区别是，mv 是一条命令而非三条命令，直接用 git mv 方便得多。 
		- 不过有时候用其他工具批处理重命名的话，要记得在提交前删除旧的文件名，再添加新的文件名。

## git操作

### 查看提交历史

- git log 的常用选项

	- 选项	说明
	- -p 按补丁格式显示每个提交引入的差异。
	- --stat 显示每次提交的文件修改统计信息。
	- --shortstat 只显示 --stat 中最后的行数修改添加移除统计。
	- --name-only 仅在提交信息后显示已修改的文件清单。
	- --name-status 显示新增、修改、删除的文件清单。
	- --abbrev-commit 仅显示 SHA-1 校验和所有 40 个字符中的前几个字符。
	- --relative-date 使用较短的相对时间而不是完整格式显示日期（比如“2 weeks ago”）。
	- --graph 在日志旁以 ASCII 图形显示分支与合并历史。
	- --pretty 使用其他格式显示历史提交信息。可用的选项包括 oneline、short、full、fuller 和 format（用来定义自己的格式）。
	- --oneline --pretty=oneline --abbrev-commit 合用的简写。

- git log
- git log -p/--patch

	- 显示每次提交所引入的差异

- git log -p -2

	- 限制显示的日志条目数量

- git log --stat

	- 附带一系列的总结性选项。 比如你想看到每次提交的简略统计信息
	- 每次提交的下面列出所有被修改过的文件、有多少文件被修改了以及被修改过的文件的哪些行被移除或是添加了。 在每次提交的最后还有一个总结。

- --pretty

	- 选项可以使用不同于默认格式的方式展示提交历史。 这个选项有一些内建的子选项供你使用
	- 比如 oneline 会将每个提交放在一行显示，在浏览大量的提交时非常有用。 另外还有 short，full 和 fuller 选项，它们展示信息的格式基本一致，但是详尽程度不一
	- git log --pretty=oneline

		- ca82a6dff817ec66f44342007202690a93763949 changed the version number
085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7 removed unnecessary test
a11bef06a3f659402fe7563abf99ad00de2209e6 first commit

	- git log --pretty=format:"%h - %an, %ar : %s"

		- ca82a6d - Scott Chacon, 6 years ago : changed the version number
085bb3b - Scott Chacon, 6 years ago : removed unnecessary test
a11bef0 - Scott Chacon, 6 years ago : first commit
		- git log --pretty=format 常用的选项 列出了 format 接受的常用格式占位符的写法及其代表的意义。

			- 选项	说明
			- %H 提交的完整哈希值
			- %h 提交的简写哈希值
			- %T 树的完整哈希值
			- %t 树的简写哈希值
			- %P 父提交的完整哈希值
			- %p 父提交的简写哈希值
			- %an 作者名字
			- %ae 作者的电子邮件地址
			- %ad 作者修订日期（可以用 --date=选项 来定制格式）
			- %ar 作者修订日期，按多久以前的方式显示
			- %cn 提交者的名字
			- %ce 提交者的电子邮件地址
			- %cd 提交日期
			- %cr 提交日期（距今多长时间）
			- %s 提交说明

- --graph

	- 	git log --pretty=format:"%h %s" --graph

		- 这个选项添加了一些 ASCII 字符串来形象地展示你的分支、合并历史：

- -S（俗称“pickaxe”选项，取“用鹤嘴锄在土里捡石头”之意）

	- 它接受一个字符串参数，并且只会显示那些添加或删除了该字符串的提交。
	-  假设你想找出添加或删除了对某一个特定函数的引用的提交，可以调用：
	- $ git log -S function_name

- path

	-  如果只关心某些文件或者目录的历史提交，可以在 git log 选项的最后指定它们的路径。 因为是放在最后位置上的选项，所以用两个短划线（--）隔开之前的选项和后面限定的路径名。

- 限制输出长度

	-  -<n> 的选项

		- 其中的 n 可以是任何整数，表示仅显示最近的 n 条提交。 

			- 不过实践中这个选项不是很常用，因为 Git 默认会将所有的输出传送到分页程序中，所以你一次只会看到一页的内容。

	- --since 和 --until 

		- 该命令可用的格式十分丰富——可以是类似 "2008-01-15" 的具体的某一天，也可以是类似 "2 years 1 day 3 minutes ago" 的相对日期。
		- git log --since=2.weeks
		- git log --since="1.day"

	- Note：还可以过滤出匹配指定条件的提交。 用 --author 选项显示指定作者的提交，用 --grep 选项搜索提交说明中的关键字。
	- Note：你可以指定多个 --author 和 --grep 搜索条件，这样会只输出 任意 匹配 --author 模式和 --grep 模式的提交。然而，如果你添加了 --all-match 选项， 则只会输出 所有 匹配 --grep 模式的提交。
	- 限制输出选项

		- -<n> 仅显示最近的 n 条提交。
		- --since, --after 仅显示指定时间之后的提交。
		- --until, --before 仅显示指定时间之前的提交。
		- --author 仅显示作者匹配指定字符串的提交。
		- --committer 仅显示提交者匹配指定字符串的提交。
		- --grep 仅显示提交说明中包含指定字符串的提交。
		- -S 仅显示添加或删除内容匹配指定字符串的提交。

	- 例子：

		- git log --pretty="%h - %s" --author='Junio C Hamano' --since="2008-10-01" \
   --before="2008-11-01" --no-merges -- t/

			- 在 Git 源码库中查看 Junio Hamano 在 2008 年 10 月其间， 除了合并提交之外的哪一个提交修改了测试文件

		- git log --pretty="%h - %s" --author="zagger" --since="2021-04-01" --before="2021-05-01" --no-merges -- js/ 

	- Tip：隐藏合并提交
按照你代码仓库的工作流程，记录中可能有为数不少的合并提交，它们所包含的信息通常并不多。 为了避免显示的合并提交弄乱历史记录，可以为 log 加上 --no-merges 选项。

### 撤销操作

- git commit --amend

	- 这个命令会将暂存区中的文件提交

		- 如果自上次提交以来你还未做任何修改（例如，在上次提交后马上执行了此命令）， 那么快照会保持不变，而你所修改的只是提交信息。

	- 你提交后发现忘记了暂存某些需要的修改

		- $ git commit -m 'initial commit'
$ git add forgotten_file
$ git commit --amend
		- 最终你只会有一个提交——第二次提交将代替第一次提交的结果。
		- Note：当你在修补最后的提交时，并不是通过用改进后的提交 原位替换 掉旧有提交的方式来修复的， 理解这一点非常重要。从效果上来说，就像是旧有的提交从未存在过一样，它并不会出现在仓库的历史中。
修补提交最明显的价值是可以稍微改进你最后的提交，而不会让“啊，忘了添加一个文件”或者 “小修补，修正笔误”这种提交信息弄乱你的仓库历史。

- 取消暂存的文件

## git工具

### [重置揭秘](https://git-scm.com/book/zh/v2/Git-%E5%B7%A5%E5%85%B7-%E9%87%8D%E7%BD%AE%E6%8F%AD%E5%AF%86#_git_reset)

- 三棵树

  理解 reset 和 checkout 的最简方法，就是以 Git 的思维框架（将其作为内容管理器）来管理三棵不同的树。 “树” 在我们这里的实际意思是 “文件的集合”，而不是指特定的数据结构。 （在某些情况下索引看起来并不像一棵树，不过我们现在的目的是用简单的方式思考它。）
  
  Git 作为一个系统，是以它的一般操作来管理并操纵这三棵树的：
  
	- HEAD

		- 上一次提交的快照，下一次提交的父结点
		- HEAD 是当前分支引用的指针，它总是指向该分支上的最后一次提交。 这表示 HEAD 将是下一次提交的父结点。
		- 该分支上的最后一次提交 的快照。

	- Index

		- 预期的下一次提交的快照
		- 索引是你的 预期的下一次提交。
		- 我们也会将这个概念引用为 Git 的“暂存区”，这就是当你运行 git commit 时 Git 看起来的样子。

	- Working Directory

		- 沙盒
		- 工作目录会将它们解包为实际的文件以便编辑。 你可以把工作目录当做 沙盒。在你将修改提交到暂存区并记录到历史之前，可以随意更改。

- 工作流程

	- Git 工作流程是通过操纵这三个区域来以更加连续的状态记录项目快照的

	  ￼
	  
	- 假设我们进入到一个新目录，其中有一个文件。 我们称其为该文件的 v1 版本，将它标记为蓝色。
	-  现在运行 git init，这会创建一个 Git 仓库，其中的 HEAD 引用指向未创建的 master 分支。（？“未创建”是指还没有提交？）

	  ￼
	  
	- 此时，只有工作目录有内容。
	- 现在我们想要提交这个文件，所以用 git add 来获取工作目录中的内容，并将其复制到索引中。

	  ￼
	  
	- 接着运行 git commit，它会

		- 1. 取得索引（Index）中的内容并将它保存为一个永久的快照， 
		- 然后2. 创建一个指向该快照的提交对象，
		- 最后3. 更新 master 来指向本次提交。

		  ￼
		  
	- 此时如果我们运行 git status，会发现没有任何改动，因为现在三棵树完全相同。
	- 现在我们想要对文件进行修改然后提交它。 我们将会经历同样的过程；
	- 首先在工作目录中修改文件。 我们称其为该文件的 v2 版本，并将它标记为红色。

	  ￼
	  
	- 如果现在运行 git status，我们会看到文件显示在 “Changes not staged for commit” 下面并被标记为红色，
	- ！！！因为该条目在索引与工作目录之间存在不同。
	-  接着我们运行 git add 来将它暂存到索引中。

	  ￼
	  
	- 此时，由于索引和 HEAD 不同，
	- 若运行 git status 的话就会看到 “Changes to be committed” 下的该文件变为绿色 ——
	- 也就是说，现在预期的下一次提交与上一次提交不同。 
	- 最后，我们运行 git commit 来完成提交。

	  ￼
	  
	- 现在运行 git status 会没有输出，因为三棵树又变得相同了。
	- 切换分支或克隆的过程也类似。 
	- 当检出一个分支时，

		- ！！！它会修改 HEAD 指向新的分支引用，
		- ！！！将 索引 填充为该次提交的快照， 
		- ！！！然后将 索引 的内容复制到 工作目录 中。

- 重置的作用

	- 在以下情景中观察 reset 命令会更有意义。
	- 为了演示这些例子，假设我们再次修改了 file.txt 文件并第三次提交它。 现在的历史看起来是这样的：

	  ￼
	  
	- 第 1 步：移动 HEAD（--soft）

		- reset 做的第一件事是移动 HEAD 的指向。
		- reset 移动 HEAD 指向的分支
		-  这意味着如果 HEAD 设置为 master 分支（例如，你正在 master 分支上）， 运行 git reset 9e5e6a4 将会使 master 指向 9e5e6a4。

		  ￼
		  
		- 无论你调用了何种形式的带有一个提交的 reset，它首先都会尝试这样做。 使用 reset --soft，它将仅仅停在那儿。
		- 理解一下发生的事情：它本质上是撤销了上一次 git commit 命令。 当你在运行 git commit 时，Git 会创建一个新的提交，并移动 HEAD 所指向的分支来使其指向该提交。
		-  当你将它 reset 回 HEAD~（HEAD 的父结点）时，其实就是把该分支移动回原来的位置，而不会改变索引和工作目录。
		- 现在你可以更新索引并再次运行 git commit 来完成 git commit --amend 所要做的事情了

	- 第 2 步：更新索引（--mixed）

		- 注意，如果你现在运行 git status 的话，就会看到新的 HEAD 和以绿色标出的它和索引之间的区别。
		- 接下来，reset 会用 HEAD 指向的当前快照的内容来更新索引。

		  ￼
		  
		- 如果指定 --mixed 选项，reset 将会在这时停止。 这也是默认行为
		- 所以如果没有指定任何选项（在本例中只是 git reset HEAD~），这就是命令将会停止的地方。
		- 现在再看一眼上图，理解一下发生的事情：它依然会撤销一上次 提交，但还会 取消暂存 所有的东西。 
		- 于是，我们回滚到了所有 git add 和 git commit 的命令执行之前。

	- 第 3 步：更新工作目录（--hard）

		- reset 要做的的第三件事情就是让工作目录看起来像索引。

		  ￼
		  
		- 你撤销了最后的提交、git add 和 git commit 命令 以及 工作目录中的所有工作。
		- 必须注意，--hard 标记是 reset 命令唯一的危险用法，它也是 Git 会真正地销毁数据的仅有的几个操作之一。 
		- 其他任何形式的 reset 调用都可以轻松撤消，但是 --hard 选项不能，因为它强制覆盖了工作目录中的文件。
		- 在这种特殊情况下，我们的 Git 数据库中的一个提交内还留有该文件的 v3 版本， 我们可以通过 reflog 来找回它。但是若该文件还未提交，Git 仍会覆盖它从而导致无法恢复。

	- 回顾

		- reset 命令会以特定的顺序重写这三棵树，在你指定以下选项时停止：
		- 移动 HEAD 分支的指向 （若指定了 --soft，则到此停止）
		- 使索引看起来像 HEAD （若未指定 --hard，则到此停止）
		- 使工作目录看起来像索引

	- 通过路径来重置

		-  若指定了一个路径，reset 将会跳过第 1 步，并且将它的作用范围限定为指定的文件或文件集合。
		- 因为 HEAD 只是一个指针，你无法让它同时指向两个提交中各自的一部分。 不过索引和工作目录 可以部分更新，所以重置会继续进行第 2、3 步。
		- 假如我们运行 git reset file.txt （这其实是 git reset --mixed HEAD file.txt 的简写形式，因为你既没有指定一个提交的 SHA-1 或分支，也没有指定 --soft 或 --hard），它会：

			- 移动 HEAD 分支的指向 （已跳过）
			- 让索引看起来像 HEAD （到此处停止）

		- 所以它本质上只是将 file.txt 从 HEAD 复制到索引中。

		  ￼
		  
		-  取消暂存文件 的实际效果

		  ￼
		  
			-  如果我们查看该命令的示意图，然后再想想 git add 所做的事，就会发现它们正好相反。
			- 这就是为什么 git status 命令的输出会建议运行此命令来取消暂存一个文件。 

		- 我们可以不让 Git 从 HEAD 拉取数据，而是通过具体指定一个提交来拉取该文件的对应版本。 我们只需运行类似于 git reset eb43bf file.txt 的命令即可。

		  ￼
		  
			- （？？？它其实做了同样的事情，也就是把工作目录中的文件恢复到 v1 版本，运行 git add 添加它， 然后再将它恢复到 v3 版本（只是不用真的过一遍这些步骤）。 如果我们现在运行 git commit，它就会记录一条“将该文件恢复到 v1 版本”的更改， 尽管我们并未在工作目录中真正地再次拥有它。？？？这段话很令人费解，极有可能是翻译错误，引起来歧义）

还有一点同 git add 一样，就是 reset 命令也可以接受一个 --patch 选项来一块一块地取消暂存的内容。 这样你就可以根据选择来取消暂存或恢复内容了。

				- this effectively does the same thing as if we had reverted the content of the file to v1 in the working directory, ran git add on it, then reverted it back to v3 again (without actually going through all those steps). If we run git commit now, it will record a change that reverts that file back to v1, even though we never actually had it in our working directory again.

		- 还有一点同 git add 一样，就是 reset 命令也可以接受一个 --patch 选项来一块一块地取消暂存的内容。 这样你就可以根据选择来取消暂存或恢复内容了。

## git忽略本地修改不提交到远程仓库

### 忽略某文件提交到远程仓库
git update-index --assume-unchanged [file-path]

### 取消忽略某文件提交到远程仓库
git update-index --no-assume-unchanged [file-path]

