---
title: HEXO+GitHub配置博客及遇见的一些坑的解决办法
date: 2017-04-09 13:10:51
categories:
- 学习笔记
tags:
- Python
---
## 笔记
- dict是一种空间换时间的一种方法。
- dict的key必须是不可变对象。
- 哈希算法计算key值的value存放地址。
- set不能添加任何list即使tuple里的list也不行，但是仅仅添加tuple可以。

### 函数
- 写在py文件上的%要有print才能输出
- 函数可以同时返回多个值，但其实就是一个tuple。
- 默认参数会降低函数调用的难度。
- 默认参数必须指向不变对象。
- 关键字参数使用**传递的dict是一份原来dict的copy。