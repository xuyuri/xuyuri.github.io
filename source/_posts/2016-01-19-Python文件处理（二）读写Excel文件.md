title: Python文件处理（二）读写Excel文件
toc: false
date: 2016-01-19 09:31:47
categories: Python
tags: [Python, Excel] 
description: 本文首先介绍Python读写Excel的基本函数，最后通过实例讲解基本用法。
---

![](http://7xj5r6.com1.z0.glb.clouddn.com/Python-Logo.png)

本文首先介绍如何利用Python进行文件读写操作，最后通过实例讲解基本用法。
<!-- more -->

## 基础知识
### 背景介绍
一日，见女票在处理实验仪器输出的Excel文档，反复从一个Excel中拷贝数据粘贴到另一个Excel中，作为程序猿的我实在无法忍受这种低效率的行为（程序猿行动指南：一切能交给机器做的事情，就不用人类去操心！），于是用Python写了个读写Excel的工具供女票使用，下文首先讲解Python读写Excel的基本知识，最后附工具代码。
读Excel，本文使用xlrd模块；
写Excel，本文介绍两种模块：pyExcelerator和xlwt。

- 安装

xlrd：[https://pypi.python.org/pypi/xlrd](https://pypi.python.org/pypi/xlrd)
xlwt：[https://pypi.python.org/pypi/xlwt/#downloads](https://pypi.python.org/pypi/xlwt/#downloads)
pyExcelerator：[https://pypi.python.org/pypi/pyExcelerator/](https://pypi.python.org/pypi/pyExcelerator/)

下载源码后，解压，安装：
```python
python setup.py install
```

### 函数汇总

### 读Excel

### 写Excel

## 实战

写在最后：
[1] [python操作Excel读写--使用xlrd](http://www.cnblogs.com/lhj588/archive/2012/01/06/2314181.html)
[2] [Python 使用 xlrd 读取 Excel格式文件](http://www.pythonclub.org/python-files/excel)
[3] [【python第三方库学习】xlrd读取Excel文件](http://blog.csdn.net/xiaoputao0903/article/details/25633513)
[4] [Python xlrd、xlwt、xlutils读取、修改Excel文件](http://my.oschina.net/dddttttt/blog/466103)
[5] [Python读取和写入Excel文件](http://blog.sina.com.cn/s/blog_6babbcb8010182c3.html)
[6] [The xlrd Module](http://www.lexicon.net/sjmachin/xlrd.html)
[7] [Microsoft Excel File Format](http://www.openoffice.org/sc/excelfileformat.pdf)
[8] [Working with Excel files in Python ](http://www.simplistix.co.uk/presentations/python-excel.pdf)
[9] [Python and Excel](http://www.simplistix.co.uk/presentations/python_excel_09/excel-lightning.pdf)
[10] [Working with Excel Files in Python](http://www.python-excel.org/)
[11] [xlwt documentation](http://xlwt.readthedocs.org/en/latest/)
---- 未完待续 ----