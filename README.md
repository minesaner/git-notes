#Git 笔记
##说明
>`<file>` : 文件  
`<branch>` : 本地分支名称  
`<rembra>` : 远程分支名称  
`<commit>` : 提交记录的 hash 值  
`<remote>` : 远程主机名  

##`git init`
>###把当前目录变成 git 可以管理的仓库

##`git add`
###操作说明
>`git add <.|<file1> <file2>...>` : 把文件添加到仓库

##`git commit`
###操作说明
>`git commit -m <message>` : 把文件提交到仓库

##`git log`
###操作说明
>`git log <file1>[ <file2>...]` : 查看文件或文件夹的提交记录  
`git log <branch> --` : 分支的提交记录  
`git log -- <file>` : 文件的提交记录  
`git log <branch> -- <file>`  
`git log <commit>` -- : `<commit>` 之前的记录，包含此条  
`git log <commit1> <commit2>` : `<commit1>` 与 `<commit2>` 之间的记录  
`git log <commit1>..<commit2>` : `<commit1>` 与 `<commit2>` 之间的记录，不包括 `<commit1>`

####参数说明
>`--oneline` - 单行输出  
`--pretty=format:"%H %h %T %t %P %p %an %ae %ad %ar %cn %ce %cd %cr %s"` : 自定义格式输出  
`-N` : 最近 N 次的提交记录  
`--abbrev-commit` : 仅显示 SHA-1 的前几个字符  
`--mergs` : 查看所有合并过的提交历史记录  
`--no-merges` : 查看所有未被合并过的提交信息  
`--grep=<message>` : 过滤只包含 `<message>` 提交说明的记录  
`--since=""|--after=""` : 显示指定时间之后的提交(不包含当前日期)  
`--until=""|--before=""` : 显示指定时间之前的提交(包含当前日期)  
`--author=<author>` : 查询指定作者的提交记录

####示例
```
git log --since="2016-1-1"
git log --since="yesterday"
git log --pretty=format:"%cn committed %h on %cd"
git log -3
```  

##`git push`
###操作说明
>`git push <remote> <branch>:<rembra>` : 将本地分支的更新，推送到远程主机  
`git push <remote> <branch>` : 将本地分支推送与之存在”追踪关系”的远程分支(通常两者同名)，如果该远程分支不存在，则会被新建  
`git push <remote> :<rembra>` : 删除指定的远程分支  
`git push <remote> --delete <rembra>` : 删除指定的远程分支

##`git pull`
###操作说明
>`git pull <remote> <rembra>:<branch>` : 取回远程主机某个分支的更新，再与本地的指定分支合并。  
`git pull <remote> <rembra>` : 远程分支是与当前分支合并  
`git pull <remote>` : 当前分支与存在追踪关系的远程分支合并

##`git branch`
###操作说明
>`git branch <branch>` : 创建分支  
`git branch -d|-D <branch>` : 删除分支  
`git branch --set-upstream <branch> <remote>/<rembra>` : 本地分支与远程分支建立追踪关系

##`git rm`
###操作说明
>`git rm --cached <file>` : 从暂存区删除文件，工作区则不做出改变

##`git reset [-q] [<commit>] [--] <file>...`
###操作说明
>`git reset [-q] [<commit>] [--] <file>...` : 用指定 `<commit>` 全部或部分文件替换暂存区，不影响工作区  
`git reset [--hard|--soft|--mixed] [<commit>]` : 替换文件且重置引用  

####参数说明
>`--hard` : 重置引用，替换暂存区，替换工作区  
`--soft` : 只更改引用的指向，不改变暂存区和工作区  
`--mixed`（默认） : 更改引用的指向及重置暂存区，但是不改变工作区  
`-q` : Be quiet, only report errors

##`git checkout`
###操作说明
>`git checkout .` : 用暂存区全部文件替换工作区  
`git checkout -- <file>` : 用暂存区指定的文件替换工作区  
`git checkout <branch> .` : 用指定分支的全部文件替换暂存区和工作区  
`git checkout <branch> <file>` : 用指定分支的部分文件替换暂存区和工作区

##`git diff`
###参数说明
>`--cached` : 提交暂存区和版本库中文件的差异

###操作说明
>`git diff` : 比较工作区与提交任务的差异  
`git diff <branch>` : 工作区和当前工作分支相比的差异
