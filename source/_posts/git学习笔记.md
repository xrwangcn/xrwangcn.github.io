---
title: git学习笔记
date: 2017-04-14 20：05:52
categories:
- 学习笔记
tags:
- git
---
## Git配置

安装完成后，在git bash输入以下命令：

`$ git config --global user.name "Your Name"`
`$ git config --global user.email "email@example.com"`

## 使用

# Init

创建版本库：`$ git init`，默认.git文件夹是隐藏文件夹，空文件夹和存在的项目文件夹都可以进行初始化。
<!-- more -->
# 常用命令

添加命令：  
`git add xxx.txt`，添加git仓库任意文件夹内的xxx文件。  
`git add .`是添加git库里所有有改动的文件，我在工作中经常使用的命令。  
提交命令：  
`git commit  -m "要改动的文件解释"`，提交改动并附带修改的注释。  
查看命令：  
`git status`命令可以掌握仓库当前的状态,可以看到那些文件已经修改了，以及哪些没有提交，**随时掌握工作区的状态**。  
`git diff`命令查看具体修改了那些内容。  
`git diff HEAD -- readme.txt`查看readme.txt文件工作区与版本库最新版本里的区别。
`git log`查看版本日志  
`git log --pretty=oneline`查看日志的精简log，版本号和提交信息
在Git中，用`HEAD`表示当前版本，也就是最新的提交，上一个版本就是`HEAD^`，上上一个版本就是`HEAD^^`，当然往上100个版本写100个^比较容易数不过来，所以写成`HEAD~100`。
`git reset --hard HEAD^`回退到上一个版本的命令 **（未推送到远程时）**。  
`git reset --hard 1234567^`回退到版本ID为1234567....的命令。  
`git reflog`用来记录你的每一次命令，便于查找ID。  
`git checkout -- readme.txt`意思就是，把`readme.txt`文件在工作区的修改全部撤销，目的使让这个文件回到最近一次`git commit`或`git add`时的状态。  
`git reset HEAD file`可以把暂存区的修改撤销掉（unstage），重新放回工作区。  
`git rm file`删除文件。
`ssh-keygen -t rsa -C "youremail@example.com"`到生成目录`C:\Users\Administrator\.ssh`把`id_rsa.pub`添加到github上的ssh设置里。
本地已有仓库相关联：
`git remote add origin git仓库地址名字`这条命令把本地仓库与远程仓库相关联，远程仓库默认叫做origin。  
`git push -u origin master`把本地的内容推送到远程库，由于远程库是空的，我们第一次推送`master`分支时，加上了`-u`参数，Git不但会把本地的`master`分支内容推送的远程新的`master`分支，还会把本地的`master`分支和远程的`master`分支关联起来，在以后的推送或者拉取时就可以简化命令。  
`git push origin master`之后推送的命令，在分支下可以简化为`git push`
`git clone xxxxxxx`克隆一个远程仓库。
分支管理：  
`git checkout -b dev`，创建`dev`分支，然后切换到`dev`分支，相当于两条命令，先创建后切换：`git branch dev`，`git checkout dev`  
`git branch`命令查看当前分支，当前分支前面会标记*号。
`git checkout master`切换分支。  
`git branch -d dev`删除Dev分支。
`git merge <name>`合并某分支到当前分支。