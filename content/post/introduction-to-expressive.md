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

*Zend Expressive* is a PSR-7, middleware-powered _micro_-framework that is built aroud freedom of choice.
It does not lock you in it's ecosystem, istead it gives you way of building application on your own with
libraries that make you most comfortable to work with.
In it's skeleton installer it asks you what Router/DI/Template engine you'd like to use.

### Freedom of choice

You are bound to use one of supported _routers_ and _templating engines_, but implementation of _DI_ is open
due to a fact that _Expressive_ uses [PSR-11](https://github.com/php-fig/container) Containers.
Use of middlewares and standarized request/response also gives us unique opportunity to mix it with different
libraries easer than ever, just simply create a middleware for it, add it to _DI_ (if needed) and it's ready!

{{< gist robopuff caedc94d203aeb7a1283bfabfd18be89>}}

{{< gist robopuff 921f3ff88f3de84354d98976fbf2252e>}}

### How about pipes

Zend Expressive 2.x is all about piping, as a part of documentation currently stands for programmatic approach
which is due to a fact that this way gives you more flexibility and possibilities.

{{< gist robopuff 3db45dec553d104d9105333933339ec2 >}}

That's beeing said, you don't have to use programmatic approach and still use configuration to do it just simply
set a flag `programmatic_pipeline` to `true`

{{< gist robopuff 6cf333710445a846db8fd11acd92ea1c >}}

From now on you'll be able to write routes in configuration again, but remember to set all required middlewares
in correct order or application might not work properly.

{{< gist robopuff 389fedef286cc73bf40502755b58fa84 >}}

### Use Cases in which ZE works best, but is not limited to

It is designed to make life easier, and it delivers. If you want to start a project, a simple one - _Expressive_
can be a best shot, as it's out-of-the-box skeleton installer will make it pretty easy and yet keeps allows you
to choose your preferred _DI_, _Router_ and _Template engine_.

With Middleware approach comes an ease when creating API applications as it gives an opportunity to make it as
a chain of responsability - one step at a time, want an oAuth2 token check? Add middleware - simple as that!

{{< gist robopuff 1309f64fc9eb016c2a5f33f41e4bb30c >}}

To summarize, Zend Expressive will work best for:
  * smaller projects, or learning purposes
  * projects that require modularity and/or freedom of choice in libraries
  * builidng API

To get started with _Zend Expressive_ you just need to start a new project with composer:

`composer create-project zendframework/zend-expressive-skeleton <project-path>`


You can check _Zend Expressive_ official documentation [here](https://docs.zendframework.com/zend-expressive/),
and get _Zend Expressive Skeleton_ [here](https://github.com/zendframework/zend-expressive-skeleton)
