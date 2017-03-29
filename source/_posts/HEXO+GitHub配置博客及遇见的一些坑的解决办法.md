---
title: HEXO+GitHub配置博客及遇见的一些坑的解决办法
date: 2017-03-10 13:10:51
categories:
- 技术学习
tags:
- hexo
- git
---
## 前言

因为一直有想搭博客的打算，查阅资料以后发现hexo+GitHub的方式非常好，不用自己的服务器，因为GitHub的yourname.github.io会提供提供资源专门放置个人博客。而选择hexo是因为这个轻博客框架对Windows友好，主题丰富成熟。
言归正传，[网上的配置方法](http://blog.csdn.net/qwe511455842/article/details/54566013#)很多，我说明简要步骤，及我在配置过程中所遇到的坑。我所采用的方法是将我的repo里的主分支放置部署的blog，然后hexo分支放置的是整体文件。但是即使按照网上其他博客的方法配置仍然有各种小问题，我稍后会在下面出现的地方一一列举。
<!-- more -->
## 配置环境及搭建

因为的电脑是系统是Windows，所以这篇博客也是基于Windows所写的，但是同寝室室友用的mac os，配置过程也是大同小异，虽不完全相同，但部分也同样具有借鉴意义。

### git

[git](https://www.git-scm.com/download/win)是必备的，不论是hexo的安装还是提交等，都需要使用git工具，这点应该是容易的。创建账号等过程不一一详述，此处有一个重点是关于建立git的repo和分支。
博主因为考虑到实验室和寝室之间换电脑的问题，想过云盘、另建一个仓库等始终觉得不是很完美的方法，然后再知乎的[一篇回答](https://www.zhihu.com/question/21193762)下找到了思路，并成功把坑修好。

#### 仓库

git上首先我们要创建一个仓库，这个仓库的名字必须是yourname.github.io。其中yourname是你的github用户名，比如我的就是[xrwangcn.github.io](http://xrwangcn.github.io)，记得下面有一个Initialiaze this repository with a README需要勾选，因为我第一次没有勾选然后出现没有成功发布在xxx.github.io的情况。

![](\images\310d.png)
创建好仓库后，进入settings往下拉到这里，如果出现这条信息则说明个人主页发布成功。（此处因为我的[xrwangcn.github.io](http://xrwangcn.github.io)绑定了域名[xavior.me](http://xrwangcn.github.io)所以显示的不太一样，绑定域名下文会讲到）

![](\images\310e.png)
到这里成功以后说明我们的仓库已经创建成功了。

#### 分支

我们需要创建一个hexo的分支然后存储我们以后博客所有的源文件，以方便我们在各个电脑上写博客，点击图片上的这个就可以创建成功了。

![](\images\310f.png)
至此分支创建完毕。

#### SSH

我们需要创建一个ssh公钥这样每次在你的电脑上就可以很方便的不用每次都输入用户名和密码进行部署你的博客，生成ssh需要在**git bash（安装好git后当前文件夹右键能看到）**下执行以下命令（key_name为你的秘钥名，我是输入的邮箱）：
``` bash
$ ssh-keygen -t rsa -C "key_name"  
```
按照给的路径找到文件id_rsa.pub，将里面的秘钥复制到GitHub的里右上角settings里的SSH里。

### node.js

应注意电脑是[32位](https://nodejs.org/dist/v4.2.3/node-v4.2.3-x86.msi)的系统还是[64位](https://nodejs.org/dist/v4.2.3/node-v4.2.3-x64.msi)的系统。下载完成以后可以一直默认下去直到安装完成，node.js安装完成以后则开始进行hexo的配置和初始化。

### hexo

我们可以新建一个专门的blog目录放置我们的整体git仓库，比如在blog目录下把我们上面建立的仓库克隆下来。
``` bash
$ git clone git@github.com:XXX/XXX.github.io.git
```
**XXX还是你的用户名，不要全部复制注意修改。（下文不再赘述）**
切换为hexo分支：
``` bash
$ git checkout hexo
```
然后在本地的XXX.github.io文件夹通过**git bash**一次执行以下命令*（在执行下面的命令以前请将.git文件夹先备份，因为后面hexo init指令会生成新的.git文件夹进而覆盖掉之前的.git文件夹导致后面失败）*：
``` bash
$ npm install hexo 
```
``` bash
$ hexo init 
```
``` bash
$ npm install
```
``` bash
$ install hexo-deployer-git 
```
打开yourname.github.io文件夹下的_config.yml，一直往下拉到最底部，按照下图修改，repo就是你的仓库地址，branch为master。

![](\images\310a.png)

### 部署

这一步我们需要先创建一个.gitignore文件，这个文件的作用是不我们不想上传的文件夹或者文件过滤点，因为hexo init生成的node_modules文件夹即使换电脑初始化以后还会存在**（而且如果不过滤上传是经常会由于文件路径长到没法识别，文件非常多）**，所以没有备份的必要，public文件夹是部署blog需要上传master分支的文件夹，也没有备份的必要。
在yourname.github.io文件夹下git bash命令行输入
``` bash
$ touch .gitignore 
```
生成“.gitignore”文件，在“.gitignore”里输入我们要隐藏的文件夹，代码如下（注意格式）：
``` javascript
.deploy_git/
node_modules/
public/
```

接下来执行将博客源文件发布到hexo分支的代码，在git bash下执行：
``` bash
$ git add . 
```
``` bash
$ git commit -m "..." 
```
``` bash
$ git push origin hexo
```
至此所有源文件已经发布到你的hexo分支上，依然在此hexo分支下执行部署命令：
``` bash
$ hexo clean
```
这条命令不是必须执行，但是我经常会遇到改完了发布了然后没有更新的情况，所以我建议每次都clean清空然后重新部署
``` bash
$ hexo d
```

## 本地资料丢失或者换电脑之后的操作

重装电脑，或者换工作环境以后需要执行下面的操作就可以进行另一台电脑的博客的书写了：
``` bash
$ git clone git@github.com:XXX/XXX.github.io.git
```
**记得将分支切换到hexo**
在本地新拷贝的XXX.github.io文件夹下通过Git bash依次执行下列指令：
``` bash
$ npm install hexo
```
``` bash
$ npm install
```
``` bash
$ npm install hexo-deployer-git 
```
**（注意此处没有hexo init）**
## 绑定域名

首先需要在阿里云的万网注册一个自己喜欢的域名，成功注册好以后，进入解析界面，添加如下的解析：

![](\images\310b.png)
A的记录值是由GitHub所提供的IP地址，解析添加好以后再source文件夹下创建CNAME的文件，文件里写入自己的域名，然后按照上面的步骤重新发布即可用新的域名访问了~

## hexo 填坑指南（持续填坑ing）
执行`hexo new`出现`YAMLException: can not read a block mapping entry; a multiline key may not be an implicit key at line 4, column 1`错误，请到\scaffolds文件夹下找到post.md文件修改一下front-matter即可。

至此博客已经部署完成，欢迎指正。
