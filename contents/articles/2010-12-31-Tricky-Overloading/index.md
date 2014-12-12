---
template: article.jade
title: Overloading can be tricky
date: 2010-12-31 15:00
author: sanjeev
aliases: ['/post/2007/01/08/code-and-stuff/', '/post/2007/01/08/first/', '/post/2008/01/08/first']
categories: [technology]
tags: [java, best-practices, technology]
excerpt: Extra care must be taken while writing Overloading methods. The compiler decides which version of an overloaded method will be called based on declared compile-time type, not run-time type.
---

Extra care must be taken while writing Overloading methods. The compiler decides which version of an overloaded method will be called based on declared compile-time type, not run-time type. For the case in which overloaded methods have the same number of arguments, the rules regarding this decision can sometimes be a bit tricky.

If there may be confusion, you may simplify the design:

* use different method names, and avoid overloading altogether
* retain overloading, but ensure each method has a distinct number of arguments
* In addition, it is recommended that varargs not be used when a method is overloaded, since this makes it more difficult to determine which overload is being called.

<span class="more"></span>

Reminder : Overloading requires methods with distinct signatures. The signature of a method includes its name and the ordered list of its argument types. All other items appearing in a method header, such as exceptions, return type, final, and synchronized, do not contribute to a method's signature. 
