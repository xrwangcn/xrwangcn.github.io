---
title: git学习笔记
date: 2017-04-14 20：05:52
categories:
- 学习笔记
tags:
- git
---
## Git配置
通过学习 by [廖雪峰的Git教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)  
安装完成后，在git bash输入以下命令：  
`$ git config --global user.name "Your Name"`
`$ git config --global user.email "email@example.com"`

### Init

创建版本库：`$ git init`，默认.git文件夹是隐藏文件夹，空文件夹和存在的项目文件夹都可以进行初始化。
<!-- more -->
## 常用命令

### 添加命令
`git add xxx.txt`，添加git仓库任意文件夹内的xxx文件。  
`git add .`是添加git库里所有有改动的文件，我在工作中经常使用的命令。  
### 提交命令 
`git commit  -m "要改动的文件解释"`，提交改动并附带修改的注释。  
### 查看命令
`git status`命令可以掌握仓库当前的状态,可以看到那些文件已经修改了，以及哪些没有提交，**随时掌握工作区的状态**。  
`git diff`命令查看具体修改了那些内容。  
`git diff HEAD -- readme.txt`查看readme.txt文件工作区与版本库最新版本里的区别。
`git log`查看版本日志  
`git log --pretty=oneline`查看日志的精简log，版本号和提交信息
### 版本回退
在Git中，用`HEAD`表示当前版本，也就是最新的提交，上一个版本就是`HEAD^`，上上一个版本就是`HEAD^^`，当然往上100个版本写100个^比较容易数不过来，所以写成`HEAD~100`。
`git reset --hard HEAD^`回退到上一个版本的命令 **（未推送到远程时）**。  
`git reset --hard 1234567^`回退到版本ID为1234567....的命令。  
`git reflog`用来记录你的每一次命令，便于查找ID。  
### 撤销与删除
`git checkout -- readme.txt`意思就是，把`readme.txt`文件在工作区的修改全部撤销，目的使让这个文件回到最近一次`git commit`或`git add`时的状态。  
`git reset HEAD file`可以把暂存区的修改撤销掉（unstage），重新放回工作区。  
`git rm file`删除文件。
`ssh-keygen -t rsa -C "youremail@example.com"`到生成目录`C:\Users\Administrator\.ssh`把`id_rsa.pub`添加到github上的ssh设置里。
### 关联本地仓库
`git remote add origin git仓库地址名字`这条命令把本地仓库与远程仓库相关联，远程仓库默认叫做origin。  
`git push -u origin master`把本地的内容推送到远程库，由于远程库是空的，我们第一次推送`master`分支时，加上了`-u`参数，Git不但会把本地的`master`分支内容推送的远程新的`master`分支，还会把本地的`master`分支和远程的`master`分支关联起来，在以后的推送或者拉取时就可以简化命令。  
`git push origin master`之后推送的命令，在分支下可以简化为`git push`
`git clone xxxxxxx`克隆一个远程仓库。
### 分支管理
`git checkout -b dev`，创建`dev`分支，然后切换到`dev`分支，相当于两条命令，先创建后切换：`git branch dev`，`git checkout dev`  
`git branch`命令查看当前分支，当前分支前面会标记*号。
`git checkout master`切换分支。  
`git branch -d dev`删除Dev分支。
`git merge <name>`合并某分支到当前分支。
### 解决冲突
两个分支合发生冲突时，需要在文件里修改冲突的部分，然后重新提交，合并就可以完成。
```bash
$ git checkout -b (new branch)
$ git add xx(.)
$ git commit -m "..."
$ git checkout master
$ git add .
$ git commit -m "..."  
```  
发生冲突  
```bash
$ git add .
$ git commit -m "..."
```  
### 分支策略
首先，master分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；  
那在哪干活呢？干活都在dev分支上，也就是说，dev分支是不稳定的，到某个时候，比如1.0版本发布时，再把dev分支合并到master上，在master分支发布1.0版本；  
你和你的小伙伴们每个人都在dev分支上干活，每个人都有自己的分支，时不时地往dev分支上合并就可以了。
（no-ff和fast forward不是很懂）  
### bug分支
`git stash`保存工作现场  
`git stash list`查看保存区域  
`git stash apply {name}`恢复区域  
`git stash drop {name}`删除工作区域
`git stash pop`恢复全部工作区，同时删除stash内容
### Feature新功能分支
添加一个新功能时，最好新建一个feature分支，在上面开发，完成后，合并，最后，删除该feature分支。  
`git branch -D <name>`强制删除分支  
### 多人协作
`git remote`查看远程库
`git remote -v`查看远程库的推送和抓取地址  
`git push origin master`推送远程主分支
`git push origin <name>`推送到远程名字为name的分支  
### 标签管理
`git tag <tagname>`打一个tagname的标签  
`git tag`查看标签  
`git tag <tagname> commitID`对当前ID打标签
`git show <tagname>`查看标签信息  
`git tag -a <tagname> -m "blablabla..." commitID`创建带有说明的标签  
`git tag -s <tagname> -m "blablabla..."`可以用PGP签名标签
`git push origin <tagname>`可以推送一个本地标签；  
`git push origin --tags`可以推送全部未推送过的本地标签；  
`git tag -d <tagname>`可以删除一个本地标签；  
`git push origin :refs/tags/<tagname>`可以删除一个远程标签。  
### 忽略特殊文件
`.gitignore`文件，忽略一些不必提交的工作文件。
GitHub配置好得配置文件[https://github.com/github/gitignore](https://github.com/github/gitignore)  
`FolderName/`忽略文件夹命令  
使用Windows的童鞋注意了，如果你在资源管理器里新建一个`.gitignore`文件，它会非常弱智地提示你必须输入文件名，但是在文本编辑器里“保存”或者“另存为”就可以把文件保存为`.gitignore`了。  
`git add -f <filename>`强制添加被gitignore忽略的文件  
`git check-ignore -v <filename>`查看文件被那个规则忽略  
### 配置别名
`git config --global alias.别名 命令名`给命令名配置一个别名  
`--global`对所有的git仓库都起作用，如果不加，只对当前仓库有作用  
Git配置文件在`.git/config`文件夹中，当前用户的Git配置文件放在用户主目录下的一个隐藏文件`.gitconfig`中。  
