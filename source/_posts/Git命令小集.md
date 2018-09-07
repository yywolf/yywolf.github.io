---
title: Git命令小集
date: 2018-09-06 20:53:27
tags: 
categories: 工具
---
创建一个空目录

```
mkdir learninggit(目录名称)
```

进入目录

```
cd learninggit
```

显示当前目录

```
pwd
例如：/User/michael/leadringgit
```

将创建的目录变成Git可以管理的仓库

```
git init
```

比如：编写一个readme.text文件
将该文件添加到仓库暂存区（可以add多个文件）

```
git add readme.text
```

把暂存区的文件提交到仓库即当前分支

```
git commit -m “提交说明”
```

查看当前仓库的状态

```
git status
```

查看更改的对比

```
git diff readme.text
```

查看提交的日志

```
git log
```

查看简化版的提交日志

```
git log --pretty=oneline
```

回退到上一版本:

```
用HEAD表示当前版本，上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。
git reset --hard HEAD^
```

回退到特定的版本

```
git reset —hard 版本号
```

查看提交的命令

```
git reflog
```

撤销工作区的修改：两种情况

```
比如：撤销readme.text工作区的修改
git checkout -- readme.text 
1.工作区的修改未被提交到暂存区，撤销修改后和版本库的一模一样
2.以前的修改已经被提交过暂存区，撤销当前的修改后，就回到和暂存区的一模一样
总之，就是让文件回到最近一次的git commit或者git add的状态
```

撤销暂存区的修改，重新放回工作区

```
git reset HEAD readme.text
```

删除版本库的文件，然后commit

```
git rm test.text
```

关联远程仓库

```
git remote add origin 远程仓库地址链接
```

推送本地库的所有内容到远程仓库上

```
git push -u origin master  （限于第一次提交到远程空仓库）-u可以将本地分支与远程分支关联起来
```

推送到指定的分支：比如推送master到origin远程分支

```
git push origin master
```

从远程仓库克隆到本地

```
git clone 远程仓库地址
```

新建分支

```
git checkout -b dev   等同于(git branch dev   git checkout dev)
```

在制定远程仓库新建分支

```
git checkout -b dev origin/dev
```

查看当前分支

```
git branch
```

切换到master分支

```
git checkout master
```

合并分支

```
1.合并dev分支的内容到master分支(合并指定分支到当前分支)，会创建新的commit，记录真实的commit情况和详情，但是commit较频繁时，分支很杂乱
git merge dev
2.使用变基，找公共祖先，不会产生新的commit，会合并之前的commit历史
git rebase dev
```

分支合并默认Fast forward
```
禁用Fast farward
git merge --no-ff -m “说明” dev
```

删除分支

```
git branch -d dev
```

查看分支合并情况

```
git log --graph --pretty=oneline --abbrev-commit
```

遇见紧急bug修复，然当前工作未完成，使用该命令储存工作现场，然后切换分支做其他事，等以后恢复现场后继续工作

```
git stash
```

继续当前未完成的工作,查询工作现场存储位置

```
git stash list
```

恢复工作现场(两种方式)

```
1.回复后stash内容不删除
git stash apply
然后可以主动删除stash内容
git stash drop
2.恢复现场的同时删除stash内容
git stash pop
```

强行删除分支

```
git branch -D dev
```

查看远程仓库的信息

```
git remote
or
查看更详细的信息
git remote -v
```

拉取远程仓库的更新到本地

```
git pull
```

制定本地分支与远程分支建立关联

```
git branch --set-upstream dev origin/dev
```

给分支打标签

```
1.切换到需要打标签的分支上
2.git tag v1.0
```

查看当前分支的所有标签

```
git tag
```

给历史提交打标签

```
1.找到历史提交的commit id
git log --pretty=oneline --abbrev-commit
2.git tag v0.9 标签id
```

查看标签信息

```
git show v0.9
```

创建带有说明的标签，-a制定标签名，-m指定说明文字

```
git tag -a v0.1 -m “说明” 标签id
```

删除本地标签

```
git tag -d v0.1
```

推送标签到远程仓库

```
1.推送指定标签
git push origin v1.0
2.一次性推送全部本地标签
git push origin --tags
```

删除远程仓库标签

```
1.先从本地删除
2.再从远程删除
git push origin :refs/tags/v0.9
```

======== git配置========

让git显示颜色

```
git config --global color.ui true
```

给git命令设置别名:比如将status设置别名st

```
git config --global alias.st status
```