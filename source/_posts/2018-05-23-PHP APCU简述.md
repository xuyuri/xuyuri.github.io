title: PHP APCu简述
toc: false
date: 2018-05-22 20:09:20
categories: PHP
tags: [PHP] 
description: PHP APCu简述
---
![](http://7xrc03.com1.z0.glb.clouddn.com/201805/apcu/APCu.png)
本文对PHP的APCu扩展进行简述，并详细介绍其安装流程以及使用方法。

<!--more-->

## 概述
PHP是一种脚本语言，每次在程序运行前都需要将源程序预编译成中间语言，然后再由解释器执行，因此这种解释性语言的程序运行效率通常比编译型语言（例如：C、C++）要低，而如果程序代码没有变更，每次执行前的编译过程就会浪费一定的时间和资源，因此APC应运而生。
### APC
APC（Alternative PHP Cache）是一种对PHP有效的高速缓冲储存器工具，可用于缓存和优化Web服务器上的PHP代码，改善服务器性能。
APC缓存包括：系统缓存和用户数据缓存；

**系统缓存：** APC把PHP文件源码的编译结果进行缓存，每次调用时先对比时间标记，若缓存未过期，则直接使用缓存的中间代码运行（默认缓存1小时），但是这样仍会浪费大量的CPU时间，因此可以在php.ini配置文件中设置系统缓存用不过期（apc.ttl = 0），但是这样设置会导致每次修改代码后都需要重启WEB服务；

**用户数据缓存：** 指用户在程序中主动使用apc_store写入和apc_fetch读取的缓存数据，建议在缓存数据量少时使用，在数据量大的情况下建议使用Redis或MemCache代替。
由于PHP5.3.\*之后的版本自带php_opcache，因此不再需要apc的系统缓存功能，而且apc的3.1.14版本在PHP5.5版本上有严重的内存问题，被官方废弃。目前最新可用的apc版本为3.1.13，仅支持php 5.3.\*

### APCu
APCu是APC的前身，它起到了缓存用户数据的作用。

---

## 安装
下载地址：[APCu](https://pecl.php.net/package/APCu)
由于我的PHP版本为5.6因此，我下载的是4.0.11

### Windows
下载4.0.11版本的dll，根据实际情况选择TS版还是NTS版本，将压缩包中的php_apcu.dll文件放置到PHP扩展目录ext下，并在php.ini文件尾部添加：
```
[APCu]
extension=php_apcu.dll
apc.enabled=1
apc.shm_size=32M
apc.ttl=7200
apc.enable_cli=1
apc.serializer=php
```
重启Web服务，输出phpinfo信息，检测是否包含apcu的配置信息。

### Ubuntu
下载4.0.11版本的tgz压缩包，解压缩后在代码目录中依次执行：
```
/usr/bin/phpize5.6
./configure --with-php-config=/usr/bin/php-config5.6
make
make install
```
注意：phpize和php-config根据实际情况设置
安装完成后在php.ini文件尾部添加：
```
[apc]
extension = apcu.so
apc.enabled= on
apc.shm_size= 64M
apc.enable_cli = on
```
重启Web服务，输出phpinfo信息，检测是否包含apcu的配置信息。

---

## 应用
### 控制台
下载[apc.php](https://github.com/xuyuri/apcu/blob/master/apc.php)文件，修改用户名和密码：
```
defaults('ADMIN_USERNAME','myname');             
defaults('ADMIN_PASSWORD','mypassword'); 
```
将apc.php文件置于WEB根目录下即可查看缓存详情：

![](http://7xrc03.com1.z0.glb.clouddn.com/201805/apcu/APCu-detail.png)
### 使用APCu
**函数列表：**

- apcu_add — Cache a new variable in the data store
- apcu_cache_info — Retrieves cached information from APCu's data store
- apcu_cas — Updates an old value with a new value
- apcu_clear_cache — Clears the APCu cache
- apcu_dec — Decrease a stored number
- apcu_delete — Removes a stored variable from the cache
- apcu_entry — Atomically fetch or generate a cache entry
- apcu_exists — Checks if entry exists
- apcu_fetch — Fetch a stored variable from the cache
- apcu_inc — Increase a stored number
- apcu_sma_info — Retrieves APCu Shared Memory Allocation information
- apcu_store — Cache a variable in the data store

**示例：**
```php
//获取缓存内容
$result = apc_fetch($key);
if (empty($result)) {
    $result = Test::model()->getList();
    if (!empty($result) ) {
        //添加缓存内容
        apc_add($key, $result, 120);
    }
}
```

转载请注明出处：[http://yurixu.com/blog/2018/05/22/PHP-APCU简述/](http://yurixu.com/blog/2018/05/22/PHP-APCU%E7%AE%80%E8%BF%B0/)