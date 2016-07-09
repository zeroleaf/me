---
layout: post
title:  "Nginx 常见问题"
date:   2016-07-09 10:55:18 +0800
categories: nginx
---

## 413 Request Entity Too Large

这个经常会在上传文件时出现, 打开 nginx 主配置文件 `nginx.conf`, 找到 `http` 段添加如下配置:

~~~ conf
client_max_body_size 16m;
~~~

对于 PHP, 还要在 `php.ini` 文件中添加如下配置, 否则可能会出现提交数据大小不一致的问题:

~~~ ini
post_max_size = 16M
upload_max_filesize = 16M
~~~

然后重启 nginx 即可.

