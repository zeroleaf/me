---
layout: post
title:  "HTML Input 标签"
date:   2016-07-13 14:31:39 +0800
categories: html
---

## datetime-local

该类型的 input 可以显示一个自带的日期选择, 同时可以输入小时跟分钟.

如果想要给该输入框设置默认的时间, 则时间需要满足一定的格式;

~~~ js
datetimelocalObject.value=YYYY-MM-DDThh:mm:ss.ms
~~~

其中, 如果提供了时间部分的内容, 则 **T** 是必须的.

NOTE: PHP 中, T 是一个预定义的时间格式, 表示本机所在的时区, 因此需要使用 `\\` 来转义.
如:

~~~ php
date('Y-m-d\TH:i', time());
~~~

### 参考

- [date](http://php.net/manual/zh/function.date.php)
- [Input DatetimeLocal value Property](http://www.w3schools.com/jsref/prop_datetime-local_value.asp)


