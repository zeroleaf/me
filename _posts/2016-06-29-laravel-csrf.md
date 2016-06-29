---
layout: post
title:  "Laravel Csrf"
date:   2016-06-29 18:08:05
categories: laravel csrf
---

默认的 Laravel 中的所有路由都是启用 **CSRF** 插件的(5.2版本), 如果需要将某些路由排除在外,
可以在 `app/Http/Middleware/VerifyCsrfToken` 中指定, 示例如下:

~~~ php
protected $except = [
    'webhook/*'
];
~~~

这样, **webhook/** 下的所有请求都不会有跨域的验证了.

## 附

之所以所有的请求都会添加 `Csrf` 中间件, 是因为默认的, 所有的请求都是包含有 `web` 中间件组的,
具体代码在 `App/Provider/RouteServiceProvider` 中:

~~~ php
/**
 * Define the "web" routes for the application.
 *
 * These routes all receive session state, CSRF protection, etc.
 *
 * @param  \Illuminate\Routing\Router  $router
 * @return void
 */
protected function mapWebRoutes(Router $router)
{
    $router->group([
        'namespace' => $this->namespace, 'middleware' => 'web',
    ], function ($router) {
        require app_path('Http/routes.php');
    });
}
~~~

而 `web` 中间件组又包含有 `Csrf` 中间价, 具体见 `App/Http/Kernel` 中:

~~~ php
/**
 * The application's route middleware groups.
 *
 * @var array
 */
protected $middlewareGroups = [
    'web' => [
        \App\Http\Middleware\EncryptCookies::class,
        \Illuminate\Cookie\Middleware\AddQueuedCookiesToResponse::class,
        \Illuminate\Session\Middleware\StartSession::class,
        \Illuminate\View\Middleware\ShareErrorsFromSession::class,
        \App\Http\Middleware\VerifyCsrfToken::class,
    ],

    // ...
];
~~~

因此, 如果想完全禁用 `Csrf` 中间件, `web` 中间件组中移除即可. 

