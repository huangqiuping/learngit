# Git简单使用

标签（空格分隔）： 工具 git

---
[TOC]

1、获取 Git仓库
在现有目录中初始化仓库
```
git init
```
使用git add命令来实现对指定文件的跟踪
```
git add *.c
git add LICENSE
git commit -m 'initial project version'
```
克隆现有的仓库
```
git clone https://github.com/libgit2/libgit2
```
使用自定义的名字
```
git clone https://github.com/libgit2/libgit2 mylibgit
```
记录每次更新到仓库

检查当前文件状态
```
git status
On branch master
nothing to commit, working directory clean
```

跟踪新文件
```
git add README
```

##1、初始化 git 仓库
```
git init
```
##2、添加文件至 git 仓库
```
git add
git commit
```
##3、检查当时文件状态
```
git status
git status -s
```
##4、查看差异
```
$ git diff     // 未 add 到暂存区
git diff HEAD — readme.txt     // 查看已 add 的 readme.txt 文件和 HEAD 的区别
```
##5、查看记录
```
git log
git log —pretty=oneline
```
##6、回退版本
```
 git reset —hard HEAD^     // 回退到上一版本
 git reset —hard HEAD~100 // 回退至前100个版本
 git reset —hard 2ee34     // 回退至指定版本，可以使用 `git log` 查看历史，`git reflog` 可以查看命令历史，可以确定要回到未来的哪个版本。
```
##7、撤消修改
###1）只修改了（还在工作区），还没有 add 到暂存区
```
git checkout — readme.txt     // — 不能少
```
###2）如果已经 add 到暂存区了
```
git reset HEAD readme.txt     // 将暂存区的修改回退到工作区
```
等同于 git reset —mixed HEAD readme.txt ，—mixed 是默认选项
```
git checkout — readme.txt     // 丢弃工作区的修改
```
###3）如果已经提交
git 
##8、删除文件
###1）不小心误删除了文件（rm掉了)
```
git checkout — test.txt     // 可以恢复已删除的文件，其实 checkout 是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除。
```
###2）真的想要删除文件
```
git rm test.txt
git commit -m “remove the test file"
```
##9、远程仓库

- 首先创建 ssh key
```
ssh-keygen -t rss -C “hqp770@126.com”
```
如果不出异常，会在用户主目录找到.ssh目录，里面有 id_rsa 和 id_rsa.pub两个文件，这两个就是 SSH Key 的秘钥对，id_rsa 是私钥，不能泄露出去，id_rsa.pub 是公钥，可以告诉任何人。

- 将id_rsa.pub 公钥的内容添加到 github 个人 key 下
- 在https://github.com创建远程仓库
根据提示，可以将自己本地的仓库 push 至远程仓库里
```
git remote add origin https://github.com/huangqiuping/learngit.git
git push -u origin master     // -u 参数不但会把本地的 master 分支内容推送至远程新的 master分支，还会把本地的 master分支和远程的master 分支关联起来，在以后的推送或者拉取时就可以简化命令。
git push origin master     // 后面只要再做了修改，就可以同步至远程
```
##10、克隆仓库
```
git clone git@github.com:huangqiuping/gitskills.git
```
或者
```
git clone https://github.com/huangqiuping/gitskills.git
```
Git 支持多种协议，包括 https，但通过 ssh 支持的原生 git 协议速度最快。

##11、分支管理
###1）创建分支
```
git branch dev
git checkout dev
```
创建并切换分支
```
git checkout -b dev
```
-b 参数表示创建并切换，相当于下面两条命令
###2）查看分支
```
git branch // 查看当前分支
```
###3）切换分支
```
git checkout name
```
###4）合并某分支到当前分支
```
git merge name     // 无法自动合并的时候，就需要手动解决冲突了
```
###5）删除分支
```
git branch -d name
```
###6）查看分支合并情况
```
git log --graph --pretty=oneline --abbrev-commit
```
###7）丢弃一个没有合并过的分支
```
git branch -D name
```

##12、隐藏当时修改
如果正在某一分支上修改一些东西，但需要临时解决其他问题，又不想提交当前的修改，可以暂时保存（隐藏）当前修改
```
git stash
```
修改完后，可以使用
```
git stash pop // 恢复暂存修改
git stats list // 查看当时暂存的 list
```
## 13、pull&push
### 1）查看远程库信息
```
git remote -v
```
### 2）从本地推送分支
```
git push origin branch-name，如果推送失败，先使用
git pull，抓取远程的新提交
```
### 3）在本地创建和远程分支对应的分支
```
git checkout -b branch-name origin/branch-name，本地分支名称最好和远程一致
```
### 4）建立本地分支与远程分支的关联
```
git branch —set-upstream branch-name origin/branch-name
```
### 5）从远程抓取分支
```
git pull，如果有冲突，要先处理冲突
git mergetool  // 打开 merge 工具
```
## 14、查找问题是哪个版本引入的
```
git bisect start 
git bisect good commit-id1
git bisect bad commit-id2
```
这时，git会按照二分法找出good版本和bad版本中间的那个提交版本，并自动将工作状态切换到那个版本，这时我们可以验证这个版本是不是有问题，如果有问题，通过
```
git bisect bad
```
告诉git，这时git会继续找出一个中间版本让我们来验证，直到我们找出，并通过
```
git bisect good
```
告诉git为止。使用
```
git bisect reset结束查找
```

## 15、生成ssh key
可以参考[GitHub指导](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/)
```
ssh-keygen
```

## 16、使用`alias`
可能对命令取别名，就像`svn`命令一样，比如`svn commit`命令可以简写为`svn ci`，使用`alias`可以将git的命令也简化，如：
`git commit` --> `git ci`
```
git config --global alias.ci commit
git config --global alias.co checkout 
git config --global alias.st status
git config --global alias.br branch
```

优化后的查看log命令：

```
git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative
```

可以使用`alias`简化：
```
git config --global alias.lg "log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative"
```

## 17、其他配置
可以在git配置文件`.gitconfig`里找到
```
[user]
    email = hqp770@126.com
    name = Terry
[color]
    ui = auto
[core]
    editor = vim 
[merge]
    tool = vimdiff
```



















