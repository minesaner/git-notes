#Git 笔记
###`git init`
>把当前目录变成 git 可以管理的仓库

###`git add <.|<file1> <file2>...>`
>把文件添加到仓库

###`git commit -m <message>`
>把文件提交到仓库

###`git log`
>查看提交记录

####常用参数
>`--oneline` - 单行输出  
`--pretty=format:"%H %h %T %t %P %p %an %ae %ad %ar %cn %ce %cd %cr %s"` 自定义格式输出  
`-N` - 最近 N 次的提交记录  
`--abbrev-commit` - 仅显示 SHA-1 的前几个字符  
`--mergs` - 查看所有合并过的提交历史记录  
`--no-merges` - 查看所有未被合并过的提交信息  
`--grep=<message>` - 过滤只包含 `<message>` 提交说明的记录  
`--since=""|--after=""` - 显示指定时间之后的提交(不包含当前日期)  
`--until=""|--before=""` - 显示指定时间之前的提交(包含当前日期)  
`--author=<author>` - 查询指定作者的提交记录

###示例
```
git log --since="2016-1-1"
git log --since="yesterday"
git log --pretty=format:"%cn committed %h on %cd"
git log -3
```  


####常用操作
>`git log <file1>[ <file2>...]` - 查看文件或文件夹的提交记录  
`git log <branch> --` - 分支的提交记录  
`git log -- <file>` - 文件的提交记录  
`git log <branch> -- <file>`  
`git log <commit>` -- ` - <commit>` 之前的记录，包含此条  
`git log <commit1> <commit2>` - `<commit1>` 与 `<commit2>` 之间的记录  
`git log <commit1>..<commit2>` - `<commit1>` 与 `<commit2>` 之间的记录，不包括 `<commit1>`

###`git push <远程主机名> <本地分支名>:<远程分支名>`
>将本地分支的更新，推送到远程主机。  
如果省略远程分支名，则表示将本地分支推送与之存在”追踪关系”的远程分支(通常两者同名)，如果该远程分支不存在，则会被新建；
如果省略本地分支名，则表示删除指定的远程分支（等同于 `git push origin --delete master`）。

###`git pull <远程主机名> <远程分支名>:<本地分支名>`
>取回远程主机某个分支的更新，再与本地的指定分支合并。  
如果远程分支是与当前分支合并，则`:<本地分支名>`部分可以省略；
如果当前分支与远程分支存在追踪关系，可以省略`<远程分支名>:<本地分支名>`部分。

###`git branch --set-upstream <本地分支名> <远程主机名>/<远程分支名>`
>本地分支与远程分支建立追踪关系

###`git reset HEAD`
>暂存区的目录树会被重写，被 HEAD 指向的分支目录树所替换，但是工作区不受影响。

###`git rm --cached <file>`
>从暂存区删除文件，工作区则不做出改变。

###`git checkout .` 或者 `git checkout -- <file>`
>用暂存区全部或指定的文件替换工作区的文件。

###`git checkout HEAD .` 或者 `git checkout HEAD <file>`
会用 HEAD 指向的分支中的全部或者部分文件替换暂存区和以及工作区中的文件。

###`git diff [<HEAD|--cached>]`
>`git diff` 比较工作区与提交任务的差异；  
`git diff HEAD` 工作区和当前工作分支相比的差异；  
`git diff --cached`提交暂存区和版本库中文件的差异。
