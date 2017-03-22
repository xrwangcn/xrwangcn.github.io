---
title: java学习笔记
date: 2016-07-11 20:57:13
categories:
tags:
---
## Java配置

JAVA_HOME值为：`C:\Program Files\Java\jdk1.8.0_05` 
Path环境变量的末尾添加如下值： `;%JAVA_HOME%\bin` **（前面有个分号）** 
CLASSPATH的值： `.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar; `
**(注意最前面的.) **
所有变量均在系统变量中配置。

## MAVEN配置

新建系统变量 MAVEN_HOME 变量值：`D:\Java\apache-maven-3.1.1` 
编辑系统变量 Path 添加变量值： `;%MAVEN_HOME%\bin`
需要注意的是maven解压出来的文件一定要放在jdk安装目录下才能成功配置。

## Java里一下自己遇见的问题
Number类和Character