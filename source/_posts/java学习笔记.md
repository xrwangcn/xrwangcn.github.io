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

## Tips
- Java里不允许将一个数字作为布尔值使用
- switch语句如果执行块没有break语句，会继续执行下一个case语句块，如果下一段语句块有break，则执行完结束，如果仍然没有，则继续执行直到遇到一个break或者default语句。
- 数组和对象类似，声明时都是做了一个引用。
- foreach循环里变量名相当于一个新声明的变量，每次循环都把数组的每一个变量赋值给当下的变量。


