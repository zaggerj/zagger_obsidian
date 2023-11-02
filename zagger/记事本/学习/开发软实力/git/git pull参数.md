## Git pull 参数

既然你已经掌握关于 `git fetch` 和 `git push` 参数的方方面面了，关于 git pull 几乎没有什么可以讲的了 :)

因为 git pull 到头来就是 fetch 后跟 merge 的缩写。你可以理解为用同样的参数执行 git fetch，然后再 merge 你所抓取到的提交记录。

还可以和其它更复杂的参数一起使用, 来看一些例子:


以下命令在 Git 中是等效的:

`git pull origin foo` 相当于：

`git fetch origin foo; git merge o/foo`

还有...

`git pull origin bar~1:bugFix` 相当于：

`git fetch origin bar~1:bugFix; git merge bugFix`

看到了? git pull 实际上就是 fetch + merge 的缩写, git pull 唯一关注的是提交最终合并到哪里（也就是为 git fetch 所提供的 destination 参数）

一起来看个例子吧：