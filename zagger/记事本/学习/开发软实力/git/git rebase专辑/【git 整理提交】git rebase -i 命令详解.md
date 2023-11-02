## git rebase -i 详解

[官方文档](https://help.github.com/en/github/using-git/about-git-rebase#commands-available-while-rebasing)

### 变基时可用的命令

变基时有六个命令可用：

- `pick`
    
    `pick`只是意味着包括提交。重新进行命令时，重新安排`pick`命令的顺序会更改提交的顺序。如果选择不包括提交，则应删除整行。
    
- `reword`
    
    该`reword`命令与相似`pick`，但是使用后，重新设置过程将暂停并为您提供更改提交消息的机会。提交所做的任何更改均不受影响。
    
- `edit`
    
    如果您选择`edit`提交，则将有机会修改提交，这意味着您可以完全添加或更改提交。您还可以进行更多提交，然后再继续进行变基。这使您可以将大型提交拆分为较小的提交，或者删除在提交中所做的错误更改。
    
- `squash`
    
    该命令使您可以将两个或多个提交合并为一个提交。提交被压缩到其上方的提交中。Git使您有机会编写描述这两个更改的新提交消息。
    
- `fixup`
    
    这类似于`squash`，但是要合并的提交已丢弃其消息。提交仅合并到其上方的提交中，并且较早提交的消息用于描述这两个更改。
    
- `exec`
    
    这使您可以对提交运行任意的Shell命令。
    

### 准备



现在我们已经有了一些，提交了，接下来开始练习

### pick 更改提交顺序、删除提交

pick`只是意味着包括提交。重新进行命令时，重新安排`pick`命令的顺序会更改提交的顺序。如果选择不包括提交，则应删除整行。

#### 假定，我们现在要改变提交 5.txt 和 4.txt 的顺序，该怎么操作

更改涉及到了两次提交，最早提交次数为2（4.txt是倒数第二次提交）

1. 告诉git 我要改变倒数第2次后的提交

`git rebase -i HEAD~2`

- 1
- 2

**接着，git给你一个文本，告诉你我知道了，你说的这些可以有以下操作**

下面是执行命令后的样子

`pick 8b485bb add 4 pick a75ed74 add 5  # Rebase 63ce9fb..a75ed74 onto 63ce9fb (2 command(s)) # # Commands: # p, pick = use commit # r, reword = use commit, but edit the commit message # e, edit = use commit, but stop for amending # s, squash = use commit, but meld into previous commit # f, fixup = like "squash", but discard this commit's log message # x, exec = run command (the rest of the line) using shell # d, drop = remove commit # # These lines can be re-ordered; they are executed from top to bottom. # # If you remove a line here THAT COMMIT WILL BE LOST. # # However, if you remove everything, the rebase will be aborted. # # Note that empty commits are commented out ~ ~ ~`

- 1
- 2
- 3
- 4
- 5
- 6
- 7
- 8
- 9
- 10
- 11
- 12
- 13
- 14
- 15
- 16
- 17
- 18
- 19
- 20
- 21
- 22
- 23
- 24

解释：我们刚刚执行的命令中 `HEAD~2`代表选择离HEAD最近的两条提交

下面注释的是提示，我们不需要管，只要专注前两行就ok

2. 把 第一行 和 第二行 交换顺序

**小技巧：这个是vi编辑器，首先`Esc` ，进入命令模式，移动到第一行 按`dd`,本行就被剪切，`pick a75ed74 add 5`就变成了第一行，接着按 `p`刚刚剪切的就成了第二行，快速交换顺序**

不会用vi建议百度篇教程学习一哈

变成下面的样子

`pick a75ed74 add 5 pick 8b485bb add 4`

- 1
- 2

接着 `Esc`,`:wq` 保存退出

![1583289087091](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9naXRlZS5jb20vcmVuc2hlbl8wNTIvbXlOb3RlLWltZy9yYXcvbWFzdGVyL2ltYWdlLzIwMjAwMzA0MTAzMTI3LTUzMjE1NS5wbmc?x-oss-process=image/format,png)

成功！

`git log`查看，4 和 5 的顺序改变了

![1583289148057](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9naXRlZS5jb20vcmVuc2hlbl8wNTIvbXlOb3RlLWltZy9yYXcvbWFzdGVyL2ltYWdlLzIwMjAwMzA4MTkzNTQxLTQzOTMucG5n?x-oss-process=image/format,png)

#### 假定，我们现在要删除 某一个提交，该怎么操作

我们来删除 add 4 的那条提交

`git rebase -i HEAD~2`

- 1

出现如下

`pick a75ed74 add 5 pick 8b485bb add 4  # Rebase 575fd8b..bb2a77d onto 575fd8b (1 command(s)) # .....略`

- 1
- 2
- 3
- 4
- 5

我们删除 第二行

接着 `Esc`,`:wq` 保存退出

![1583289690314](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9naXRlZS5jb20vcmVuc2hlbl8wNTIvbXlOb3RlLWltZy9yYXcvbWFzdGVyL2ltYWdlLzIwMjAwMzA0MTA0MTMwLTY1NjExOS5wbmc?x-oss-process=image/format,png)

`git log`查看，4 和 5 的顺序改变了

![1583289787442](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9naXRlZS5jb20vcmVuc2hlbl8wNTIvbXlOb3RlLWltZy9yYXcvbWFzdGVyL2ltYWdlLzIwMjAwMzA0MTA0MzE2LTc3MzYwMC5wbmc?x-oss-process=image/format,png)

### record 修改提交消息(提交内容不变)

该`reword`命令与相似`pick`，但是使用后，重新设置过程将暂停并为您提供更改提交消息的机会。提交所做的任何更改均不受影响。

#### 假定，我们现在要 修改某个提交的消息，该怎么操作

修改一下 add 2 的提交消息

`git log` 查看 add 2 距离 HEAD 有多少的距离，得：3

`git rebase -i HEAD~3`

- 1

出现如下

`pick 9cd34c4 add 2 pick 63ce9fb add 3 pick 575fd8b add 5  # Rebase 77bd0eb..575fd8b onto 77bd0eb (3 command(s)) # .... 略`

- 1
- 2
- 3
- 4
- 5
- 6
- 7

我们只需要修改 第一行 add 2 ，其余保持不变

`r 9cd34c4 add 2 pick 63ce9fb add 3 pick 575fd8b add 5  # Rebase 77bd0eb..575fd8b onto 77bd0eb (3 command(s)) # .... 略`

- 1
- 2
- 3
- 4
- 5
- 6

r 是 record简写

接着 `Esc`,`:wq` 保存退出

git会说 开始执行，接着弹出一个编辑窗口

`add 2  # Please enter the commit message for your changes. Lines starting # with '#' will be ignored, and an empty message aborts the commit. # # Date:      Wed Mar 4 09:58:45 2020 +0800 # # interactive rebase in progress; onto 77bd0eb # Last command done (1 command done): #    r 9cd34c4 add 2 # Next commands to do (2 remaining commands): #    pick 63ce9fb add 3 #    pick 575fd8b add 5 # You are currently editing a commit while rebasing branch 'master' on '77bd0eb'. # # Changes to be committed: #       new file:   2.txt #`

- 1
- 2
- 3
- 4
- 5
- 6
- 7
- 8
- 9
- 10
- 11
- 12
- 13
- 14
- 15
- 16
- 17
- 18
- 19

我们就可以修改 add 2 了

下面的注释是对当前状态的一些说明

大致是说，上一次执行的命令 是 `r 9cd34c4 add 2`

下面还有两条命令

当前命令改变的committed的文件 是 2.txt 等等

**修改 add 2**

`add 2 ~ new comment`

- 1

接着 `Esc`,`:wq` 保存退出

成功

![1583290748248](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9naXRlZS5jb20vcmVuc2hlbl8wNTIvbXlOb3RlLWltZy9yYXcvbWFzdGVyL2ltYWdlLzIwMjAwMzA0MTA1OTEzLTE2Mzk3Ny5wbmc?x-oss-process=image/format,png)

`git log`查看, 消息 “add 2” 变为了 “add 2 ~ new comment”

![1583290791964](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9naXRlZS5jb20vcmVuc2hlbl8wNTIvbXlOb3RlLWltZy9yYXcvbWFzdGVyL2ltYWdlLzIwMjAwMzA4MTkzODEzLTE4OTI4My5wbmc?x-oss-process=image/format,png)

==只要不动pick的 顺序，就代表什么都不做==

### edit修改提交

如果您选择`edit`提交，则将有机会修改提交，这意味着您可以完全添加或更改提交。您还可以进行更多提交，然后再继续进行变基。这使您可以将大型提交拆分为较小的提交，或者删除在提交中所做的错误更改。

#### 假定 我想要在两个提交之间 再加提交，怎么办

假定，我们要在 add 3 和 add 5 之间 添加一条提交

`git rebase -i HEAD~2`

- 1

`pick 6934312 add 3 pick 5ce6dde add 5  # Rebase 7f9d45d..5ce6dde onto 7f9d45d (2 command(s)) # ....`

- 1
- 2
- 3
- 4
- 5
- 6

修改为

`e 6934312 add 3 pick 5ce6dde add 5`

- 1
- 2

接着 `Esc`,`:wq` 保存退出

有如下

`$ git rebase -i HEAD~2 Stopped at 6934312135c150bf74bead26e371df1443273ca4... add 3 You can amend the commit now, with          git commit --amend  Once you are satisfied with your changes, run          git rebase --continue   xxxxxx MINGW32 ~/Desktop/git-demo (master|REBASE-i 1/2)`

- 1
- 2
- 3
- 4
- 5
- 6
- 7
- 8
- 9
- 10
- 11
- 12
- 13

可以看到，我们的master分支多了`REBASE-i 1/2`

我们尝试做一些修改，给3.txt 增加一些内容，然后提交

`git add 3.txt  git commit -m "edit 3.txt" [detached HEAD 7262a57] edit 3.txt  1 file changed, 1 insertion(+)`

- 1
- 2
- 3
- 4
- 5
- 6
- 7

接着，我们继续 rebase

`git rebase --continue Successfully rebased and updated refs/heads/master.`

- 1
- 2
- 3

`git log` 查看，在 add 5 和 add 3 中间 增加了我们刚刚的修改

![1583292653954](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9naXRlZS5jb20vcmVuc2hlbl8wNTIvbXlOb3RlLWltZy9yYXcvbWFzdGVyL2ltYWdlLzIwMjAwMzA0MTEzMDU2LTczMjkzMS5wbmc?x-oss-process=image/format,png)

#### 假定 我想要单纯的修改这次提交内容和消息，怎么办

参照上面的做到这一步，我们选择提交的方式 加一个参数 `git commit --amend`修改

`git add 3.txt  git commit --amend  # 这样 就不会在多出一次提交 # 本次对 3.txt的修改会记录 到  add 3  这次提交记录中`

- 1
- 2
- 3
- 4
- 5
- 6

接着结束这次 rebase

`git rebase --continue Successfully rebased and updated refs/heads/master.`

- 1
- 2
- 3

### squash合并提交

`squash`

该命令使您可以将两个或多个提交合并为一个提交。提交被压缩到其上方的提交中。Git使您有机会编写描述这两个更改的新提交消息。

#### 假定，我想合并某几个提交，怎么办

如下

![1583296701676](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9naXRlZS5jb20vcmVuc2hlbl8wNTIvbXlOb3RlLWltZy9yYXcvbWFzdGVyL2ltYWdlLzIwMjAwMzA0MTIzODIyLTY3NTQyMy5wbmc?x-oss-process=image/format,png)

我们合并 add 5 和 add 3

`git rebase - i HEAD~2`

- 1

`pick 6934312 add 3 pick 6fa47e4 add 5  # Rebase 7f9d45d..6fa47e4 onto 7f9d45d (2 command(s))`

- 1
- 2
- 3
- 4
- 5

修改为

`pick 6934312 add 3 s 6fa47e4 add 5`

- 1
- 2

接着 `Esc`,`:wq` 保存退出

开始执行变更

然后 在弹出来的编辑框里 写提交信息

`# This is a combination of 2 commits. # The first commit's message is:  add 3  # This is the 2nd commit message:  add 5  # Please enter the commit message for your changes. Lines starting # with '#' will be ignored, and an empty message aborts the commit. # # Date:      Wed Mar 4 09:59:04 2020 +0800 # # interactive rebase in progress; onto 7f9d45d # Last commands done (2 commands done): #    pick 6934312 add 3 #    s 6fa47e4 add 5 # No commands remaining. # You are currently editing a commit while rebasing branch 'master' on '7f9d45d'. # # Changes to be committed: #       new file:   3.txt #       new file:   5.txt`

- 1
- 2
- 3
- 4
- 5
- 6
- 7
- 8
- 9
- 10
- 11
- 12
- 13
- 14
- 15
- 16
- 17
- 18
- 19
- 20
- 21
- 22
- 23
- 24
- 25

我们可以修改提交消息，默认是把两个消息都合并

接着 `Esc`,`:wq` 保存退出

`git log`查看，合并成功

![1583297200752](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9naXRlZS5jb20vcmVuc2hlbl8wNTIvbXlOb3RlLWltZy9yYXcvbWFzdGVyL2ltYWdlLzIwMjAwMzA0MTI0NjU3LTUwMDk0MC5wbmc?x-oss-process=image/format,png)

### fixup合并提交，只保留较早的提交信息

这类似于`squash`，但是要合并的提交已丢弃其消息。提交仅合并到其上方的提交中，并且较早提交的消息用于描述这两个更改。

最后两次提交

`git rebase -i HEAD~2`

- 1

`pick 7f9d45d add 2 ~ new comment pick 311adc9 add 3  # Rebase 77bd0eb..311adc9 onto 77bd0eb (2 command(s)) #  ---------------------- # 变更为 # -----------------------  pick 7f9d45d add 2 ~ new comment f 311adc9 add 3  # 保存`

- 1
- 2
- 3
- 4
- 5
- 6
- 7
- 8
- 9
- 10
- 11
- 12

### exec 执行任意shell命令

`git rebase -i HEAD~3  # 弹出编辑框 #---------------------------- pick 81fe4d0 添加test2.txt和test3.txt pick 77bd0eb add 1 pick e7c68b8 add 2 ~ new comment  # Rebase 258a059..e7c68b8 onto 258a059 (3 command(s)) #....  # ---------------- # 加一行 命令 # --------------- x echo "Hello is echo do ......." pick 81fe4d0 添加test2.txt和test3.txt pick 77bd0eb add 1 pick e7c68b8 add 2 ~ new comment  ## 执行了我们刚刚键入的命令 Executing: echo "Hello is echo do ......." Hello is echo do ....... Successfully rebased and updated refs/heads/master.`

- 1
- 2
- 3
- 4
- 5
- 6
- 7
- 8
- 9
- 10
- 11
- 12
- 13
- 14
- 15
- 16
- 17
- 18
- 19
- 20
- 21
- 22
- 23
- 24
- 25
- 26

### 其他

`# Commands: # p, pick = use commit # r, reword = use commit, but edit the commit message # e, edit = use commit, but stop for amending # s, squash = use commit, but meld into previous commit # f, fixup = like "squash", but discard this commit's log message # x, exec = run command (the rest of the line) using shell # d, drop = remove commit`

- 1
- 2
- 3
- 4
- 5
- 6
- 7
- 8
- 9

#### drop

删除提交

用法与 p,r,e,s,f,x 一致

#### 命令写错了怎么办

看提示

`You can fix this with 'git rebase --edit-todo'. # 用 git rebase --edit--todo  来重新编辑命令`

- 1
- 2