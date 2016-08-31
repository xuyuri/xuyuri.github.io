title: Sublime Text 3 编译运行PHP
toc: false
date: 2016-08-30 21:30:23
categories: 工具 
tags: Sublime PHP
description:
---

![](/img/article/sublime-text.png)
本文介绍如何在Sublime Text 3中运行PHP代码。
<!--more-->
◆ Windows环境下确保PHP已经添加到环境变量
◆ 添加PHP编译系统
选择：工具——>编译系统——>新编译系统
![](/img/article/Sublime.png)
新建的编译系统默认内容为：
```php
{
	"shell_cmd": "make"
}
```
修改内容如下：
```php
{
	"cmd": ["php", "$file"], 
    "file_regex": "php$", 
    "selector": "source.php",
    "encoding":"cp936"
}
```
<font color=red>注意：</font>最后的encoding设置为cp936，否则在执行PHP代码时可能会因为编码问题导致错误提示：
`Decode error - output not utf-8`
如果出现：
`Decode error - output not cp936`
可以尝试将encourage设置为utf-8

转载请注明出处：[http://yurixu.com/blog/2016/08/30/Sublime Text 3 编译运行PHP](http://yurixu.com/blog/2016/08/30/Sublime Text 3 编译运行PHP/)