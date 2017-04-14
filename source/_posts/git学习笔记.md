## Git配置

安装完成后，在git bash输入以下命令：

`$ git config --global user.name "Your Name"`
`$ git config --global user.email "email@example.com"`

## 使用

# Init

创建版本库：`$ git init`，默认.git文件夹是隐藏文件夹，空文件夹和存在的项目文件夹都可以进行初始化。

# 常用命令

添加命令：  
`git add xxx.txt`，添加git仓库任意文件夹内的xxx文件。  
`git add .`是添加git库里所有有改动的文件，我在工作中经常使用的命令。  
提交命令：  
`git commit  -m "要改动的文件解释"`，提交改动并附带修改的注释。  
查看命令：  
`git status`命令可以掌握仓库当前的状态,可以看到那些文件已经修改了，以及哪些没有提交，**随时掌握工作区的状态**。  
`git diff`命令查看具体修改了那些内容。  
`git log`查看版本日志  
`git log --pretty=oneline`查看日志的精简log，版本号和提交信息
