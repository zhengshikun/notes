#<center>git的使用

2018/7/1 14:10:45 

##什么是git

Git是一个开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目。

Git 是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件。

Git 与常用的版本控制工具 CVS, Subversion 等不同，它采用了分布式版本库的方式，不必服务器端软件支持。

##工作流程

- 克隆 Git 资源作为工作目录。
- 在克隆的资源上添加或修改文件。
- 如果其他人修改了，你可以更新资源。
- 在提交前查看修改。
- 提交修改。
- 在修改完成后，如果发现错误，可以撤回提交并再次修改并提交。

##创建仓库

###git init

git init 命令来初始化一个 Git 仓库，Git 的很多命令都需要在 Git 的仓库中运行，所以 git init 是使用 Git 的第一个命令。

###git clone

git clone 从现有 Git 仓库中拷贝项目

    git clone <repo> <directory>

- repo:Git 仓库
- directory:本地目录。

##基本操作

###git add

将想要快照的内容写入缓存区

使用 git add . 命令来添加当前项目的所有文件。

###git status

以查看在你上次提交之后是否有修改。

加 -s 参数，以获得简短的结果输出。

###git diff

查看执行 git status 的结果的详细信息。

- 尚未缓存的改动：git diff
- 查看已缓存的改动： git diff --cached
- 查看已缓存的与未缓存的所有改动：git diff HEAD
- 显示摘要而非整个 diff：git diff --stat

###git commit

将缓存区内容添加到仓库中。

如果你觉得 git add 提交缓存的流程太过繁琐，Git 也允许你用 -a 选项跳过这一步。

     git commit -a

###git reset HEAD

用于取消已缓存的内容。

###git rm

从 Git 中移除某个文件，就必须要从已跟踪文件清单中移除，然后提交。

    git rm <file>

如果删除之前修改过并且已经放到暂存区域的话，则必须要用强制删除选项 -f

    git rm -f <file>

如果把文件从暂存区域移除，但仍然希望保留在当前工作目录中，换句话说，仅是从跟踪清单中删除，

    git rm --cached <file>

###git mv

git mv 命令用于移动或重命名一个文件、目录、软连接。

##git分支管理

几乎每一种版本控制系统都以某种形式支持分支。使用分支意味着你可以从开发主线上分离开来，然后在不影响主线的同时继续工作。

创建分支命令：

    git branch (branchname)

切换分支命令:

    git checkout (branchname)

当你切换分支的时候，Git 会用该分支的最后提交的快照替换你的工作目录的内容， 所以多个分支不需要多个目录。

合并分支命令:

    git merge 

列出分支基本命令：

    git branch

删除分支命令：

    git branch -d (branchname)

##Git 查看提交历史

使用 git log 命令查看

用 --oneline 选项来查看历史记录的简洁的版本。

    git log --oneline

用 --graph 选项，查看历史中什么时候出现了分支、合并。

    git log --oneline --graph

用 '--reverse'参数来逆向显示所有日志。

    git log --reverse --oneline

如果只想查找指定用户的提交日志可以使用命令：git log --author

    git log --author=Linus --oneline -5

###Git 标签

如果你达到一个重要的阶段，并希望永远记住那个特别的提交快照，你可以使用 git tag 给它打上标签。

    git tag -a v1.0

##Git 远程仓库(Github)

###添加远程库

     git remote add [shortname] [url]

###查看当前的远程库

    git remote
    git remote -v

###提取远程仓库

从远程仓库下载新分支与数据：

    git fetch

从远端仓库提取数据并尝试合并到当前分支：

    git merge

###推送到远程仓库

    git push [alias] [branch]

###删除远程仓库

    git remote rm [别名]