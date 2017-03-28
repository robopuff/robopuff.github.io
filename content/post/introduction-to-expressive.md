+++
title = "Freedom of choice, an introduction to Zend Expressive"
tags = [ "php", "zend", "expressive" ]
date = "2017-03-28"
categories = [
    "Development",
    "Zend"
]
+++

## What is Zend Expressive

*Zend Expressive* is a [PSR-7](https://github.com/php-fig/http-message), middleware-powered _micro_-framework that is
built around freedom of choice. It does not lock you in it's ecosystem, instead it gives you way of building application
on your own with libraries that make you most comfortable to work with.
In it's skeleton installer it asks you what Router/DI/Template engine you'd like to use.

### Freedom of choice

You are bound to use one of supported _routers_ and _templating engines_, but implementation of _DI_ is open
due to a fact that _Expressive_ uses [PSR-11](https://github.com/php-fig/container) Containers.
Use of middleware and standardised request/response also gives us unique opportunity to mix it with different
libraries easier than ever, just simply create a middleware for it, add it to _DI_ (if needed) and it's ready!

{{< gist robopuff caedc94d203aeb7a1283bfabfd18be89>}}

{{< gist robopuff 921f3ff88f3de84354d98976fbf2252e>}}

### How about pipes

Zend Expressive 2.x is all about piping, as a part of documentation currently stands for programmatic approach
which is due to a fact that this way gives you more flexibility and possibilities.

{{< gist robopuff 3db45dec553d104d9105333933339ec2 >}}

That's beeing said, you don't have to use programmatic approach and still use configuration to do it just simply
set a flag `programmatic_pipeline` to `true`

{{< gist robopuff 6cf333710445a846db8fd11acd92ea1c >}}

From now on you'll be able to write routes in configuration again, but remember to set all required middleware
in correct order or application might not work properly.

{{< gist robopuff 389fedef286cc73bf40502755b58fa84 >}}

### In a middle of a Middlewares

In _Zend Expressive 2.x_ you can use _single-pass_ ( a [PSR-15](https://github.com/php-fig/fig-standards/tree/master/proposed/http-middleware)
proposal with [http-interop](https://github.com/http-interop/http-middleware) implementation) or a _double-pass_ middleware.

_Single-pass_ refferes to implementation of `Psr\Http\ServerMiddleware\MiddlewareInterface` (or interop implementation 
`Interop\Http\ServerMiddleware\MiddlewareInterface`) which means that there is a method `process` which takes two parameters
`ServerRequestInterface $request` and `DelegateInterface $delegate` but invoking it from a chain will require passing only _request_
(interface is optional, same can be achieved with `__invoke(ServerRequestInterface $request, DelegateInterface $delegate)`
instead of `process` method).
{{< gist robopuff 629d4526773d9fc79308476dda6a7c21 >}}

_Double-pass_ is little bit different as it passes more arguments to `$next`, a _request_, _response_ and a callable
{{< gist robopuff a230db2e8c8a201ea945690fb55aa854 >}}

### Use Cases in which ZE works best, but is not limited to

It is designed to make life easier, and it delivers. If you want to start a project, a simple one - _Expressive_
can be a best shot, as it's out-of-the-box skeleton installer will make it pretty easy and yet keeps allows you
to choose your preferred _DI_, _Router_ and _Template engine_.

With Middleware approach comes an ease when creating API applications as it gives an opportunity to make it as
a chain of responsibility - one step at a time, want an oAuth2 token check? Add middleware - simple as that!

{{< gist robopuff 1309f64fc9eb016c2a5f33f41e4bb30c >}}

To summarize, Zend Expressive will work best for:

* smaller projects, or learning purposes
* projects that require modularity and/or freedom of choice in libraries
* building API

To get started with _Zend Expressive_ you just need to start a new project with composer:

`composer create-project zendframework/zend-expressive-skeleton <project-path>`


You can check _Zend Expressive_ official documentation [here](https://docs.zendframework.com/zend-expressive/),
and get _Zend Expressive Skeleton_ [here](https://github.com/zendframework/zend-expressive-skeleton)
