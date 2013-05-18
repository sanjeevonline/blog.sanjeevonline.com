---
template: article.jade
title: Prefer switch over if-else
date: 2010-12-28 15:00
author: sanjeev
aliases: ['/post/2007/01/08/code-and-stuff/', '/post/2007/01/08/first/', '/post/2008/01/08/first']
categories: [technology]
tags: [java, best-practices]
excerpt: In most cases switch will be lighter and performs faster than an if/else ladder.
---
In most cases switch will be lighter and performs faster than an if/else ladder. The compiler is able to optimize switch statements into a lookup table and perform compile-time checking for literals when dealing with enumerations, so I'd suggest that it's usually preferable to use switch over if/else if if you're dealing with numeric or enum types in Java. 
