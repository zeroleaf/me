---
layout: post
title:  "无状态 API 请求"
date:   2016-07-04 08:48:33
categories: 
---

最近在使用 Laravel 项目开发, 里面集成了 [dingo](https://github.com/dingo/api). 

在 api 请求里, 用 **session** 存储了用户的 id, 但是后来发现页面的请求 cookie 跟 ajax
请求的 cookie 值是不一致的, 从而导致无法从 session 里面读取到相应的数据. 
Google 了一番说是该问题并没有什么比较好的解决方法, 另一方面也有可能是应用程序设计的不合理.
照着这个思路, 细想之下可能确实如此, **api 请求的话最好是无状态的, 需要的参数由客户端传递,**
这样也利于做规模处理.

## 参考

- <https://en.wikipedia.org/wiki/Representational_state_transfer#Stateless>
- <http://stackoverflow.com/questions/3105296/if-rest-applications-are-supposed-to-be-stateless-how-do-you-manage-sessions>
