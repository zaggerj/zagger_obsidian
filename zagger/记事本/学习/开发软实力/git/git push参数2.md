## `<place>` 参数详解

还记得之前课程说的吧，当为 git push 指定 place 参数为 `master` 时，我们同时指定了提交记录的来源和去向。

要同时为源和目的地指定 `<place>` 的话，只需要用冒号 `:` 将二者连起来就可以了：

`git push origin <source>:<destination>`

这个参数实际的值是个 refspec，“refspec” 是一个自造的词，意思是 Git 能识别的位置（比如分支 `foo` 或者 `HEAD~1`）

一旦你指定了独立的来源和目的地，就可以组织出言简意赅的远程操作命令了，让我们看看演示！