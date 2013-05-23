---
template: article.jade
title: Prefer using parameterized types over raw types
date: 2010-12-29 15:00
author: sanjeev
aliases: ['/post/2007/01/08/code-and-stuff/', '/post/2007/01/08/first/', '/post/2008/01/08/first']
categories: [technology]
tags: [java, best-practices]
excerpt: When generics were introduced in JDK 1.5, raw types were retained only to maintain backwards compatibility with older versions of Java. Although using raw types is still possible, they should be avoided for following reasons..
---

When generics were introduced in JDK 1.5, raw types were retained only to maintain backwards compatibility with older versions of Java. Although using raw types is still possible, they should be avoided for following reasons :

* they usually require casts
* they aren't type safe, and some important kinds of errors will only appear at runtime
* they are less expressive, and don't self-document in the same way as parameterized types

<span class="more"></span>

Unless you are using a JDK version prior to 1.5 I don't see a reason why you should not use parameterized types in your code.

Happy coding !!
