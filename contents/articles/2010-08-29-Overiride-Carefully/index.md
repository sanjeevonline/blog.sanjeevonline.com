---
template: article.jade
title: Overridable methods need special care
date: 2010-08-29 15:00
author: sanjeev
aliases: ['/post/2007/01/08/code-and-stuff/', '/post/2007/01/08/first/', '/post/2008/01/08/first']
categories: [technology]
tags: [java, best-practices]
excerpt: Allowing a method to be overridden should always be done intentionally, not by accident. Any method which is not private, static, or final can be overridden. 
---
<b>Allowing a method to be overridden should always be done intentionally, not by accident</b>.
 
Any method which is not private, static, or final can be overridden. Over-ridable methods, and any methods which call them, represent unusual places in your code, to which special attention must be paid. This is because sub-classing violates encapsulation, in the sense that it is possible for a subclass to break its superclass's contract. If you do not intend a method to be overridden, then you should declare it as private, static, or final.

<span class="more"></span>

When you do override a method, you should use the @Override annotation. This allows the compiler to verify that the method is indeed a valid override of an existing method. For example, your implementations of toString, equals, and hashCode should always use @Override in the method header. 
