# PHP网络技术

## 网页抓取
```php
<?php
//获取网页源码-file_get_contents
$html = file_get_contents('http://www.baidu.com'); 
$html = iconv("UTF-8","GB2312//IGNORE",$html);          //解决file_get_contents返回内容乱码，将utf-8转换为gb2312，并忽略掉不能转换的字符
#print_r($html);                                        //返回网页源码
#print_r($http_response_header);                        //打印http响应头部
//获取网页源码-fopen
$fp = fopen('http://www.baidu.com', 'r');
$html = stream_get_contents($fp);
$html = iconv("UTF-8","GB2312//IGNORE",$html);
print_r($html);                                         //返回网页源码
#print_r(stream_get_meta_data($fp));                    //打印http响应头部
fclose($fp);
?>
```

[1](http://www.webkaka.com/tutorial/php/2013/052534/)
[2](http://www.ido321.com/1158.html)
[3](http://developer.51cto.com/art/200904/121739.htm)	