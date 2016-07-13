---
layout: post
title:  "IOS 浏览器跳转到 AppStore 上指定的 App"
date:   2016-07-12 10:20:14 +0800
categories: ios
---

要想在 Safari 中跳转到 AppStore 中指定的 App, 只要跳转到指定的链接即可,
链接格式如下:

`itms-apps://itunes.apple.com/app/idYOUR_APP_ID`

其中, idYOUR_APP_ID 部分的内容可以在 Web 版的 itunes 上找到(在地址栏上).

同时, 可以通过如下的 js 代码判断是否是 ios 系统:

~~~ js
var u = navigator.userAgent;
var isIOS = !!u.match(/\(i[^;]+;( U;)? CPU.+Mac OS X/); //ios终端
~~~

## 参考

- [JS判断客户端是否是iOS或者Android](http://caibaojian.com/browser-ios-or-android.html)
- [iOS浏览器跳转到自己的应用](https://segmentfault.com/q/1010000002503244)


