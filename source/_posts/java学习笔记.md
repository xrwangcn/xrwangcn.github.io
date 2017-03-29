---
title: java学习笔记
date: 2016-07-11 20:57:13
categories:
- 学习笔记
tags:
- Java
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
- 调用方法结束释放掉方法所产生的空间。
- 成员变量相当于类的属性，局部变量是方法自己使用的用完就释放，成员变量可以被本类的所有方法所使用，同时可以被与本类有关的其他类所使用，而局部变量只能在当前的方法中使用。成员变量和局部变量同名时，局部变量具有更高的优先级。
- 包的命名规范是全小写字母拼写，import关键字。
- 内部类是一个编译时的概念，一旦编译成功，就会成为完全不同的两类。对于一个名为outer的外部类和其内部定义的名为inner的内部类。编译完成后出现outer.class和outer$inner.class两类。所以内部类的成员变量/方法名可以和外部类的相同。


## Questions
- 关于封装还不是太明白
- 一个包内的文件可以有几个主方法，调用的是哪个主方法？
- 匿名类有点不懂，找资料


## Solutions
- eclipse自动添加getter和setter方法出现the operation is not ... 提示，解决办法：把光标放在需要生成的类里，重新执行一次。