title: 'file_get_contents(): Unable to find the wrapper https'
toc: false
date: 2016-08-17 21:38:35
categories: PHP
tags: issue
description: file_get_contents如何支持Https链接
---
![](http://7xrc03.com1.z0.glb.clouddn.com/HTTPS.jpg)
使用file_get_contents向https类型的链接发送构造的请求头，返回：
`Warning: file_get_contents(): Unable to find the wrapper "https" - did you forget to enable it when you configured PHP? `

<!--more-->

**原因分析**：
PHP没有开启php_openssl扩展；
**检测方法**：
检测主机是否开启php_openssl扩展的方法：
```php
$ssl = stream_get_wrappers();
echo 'openssl: ',  extension_loaded ('openssl') ? 'yes':'no', "\n";
echo 'http wrapper: ', in_array('http', $ssl) ? 'yes':'no', "\n";
echo 'https wrapper: ', in_array('https', $ssl) ? 'yes':'no', "\n";
echo 'wrappers: ', var_export($ssl);
```
如果返回的结果如下：
```php
openssl: yes
http wrapper: yes
https wrapper: yes
wrappers: array(11) {
  [...]
}
```
表明主机已经开启了php_openssl扩展。
**解决方案**：
修改PHP配置文件php.ini，启用php_openssl扩展并开启allow_url_fopen。
```
extension=php_openssl.dll
allow_url_fopen = On
```
转载请注明出处：
