title: Windows开启cUrl模块（Call to undefined function curl_init()）
toc: false
date: 2016-05-10 08:00:49
categories: PHP
tags: [PHP, 网络] 
description: Windows下如何开启cUrl模块
---

![](http://7xrc03.com1.z0.glb.clouddn.com/cUrl.gif)

- 开启php_curl.dll扩展
去掉PHP配置文件php.ini中`;extension=php_curl.dll`前面的分号；
- 检查php_curl.dll
在extension_dir对应的扩展目录中查找是否存在php_curl.dll，没有需要下载
- 拷贝libeay32.dll和ssleay32.dll
将PHP目录中的libeay32.dll和ssleay32.dll文件拷贝至C:\Windows\System32（64位复制到SysWOW64下）
- 重启Apache或IIS

---- 完结 ----