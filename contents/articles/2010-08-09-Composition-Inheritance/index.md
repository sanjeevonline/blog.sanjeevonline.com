---
template: article.jade
title: Prefer composition over inheritance
date: 2010-08-07 15:00
author: sanjeev
aliases: ['/post/2007/01/08/code-and-stuff/', '/post/2007/01/08/first/', '/post/2008/01/08/first']
categories: [technology]
tags: [java, best-practices]
excerpt: Trust me on this one, I have learnt it the hard way. To start with lets start with the understanding of the terms composition and inheritance
---
Trust me on this one, I have learnt it the hard way. To start with lets start with the understanding of the terms composition and inheritance.

* Composition
  * Functionality of an object is made up of an aggregate of different classes
  * In practice, this means holding a pointer to another class to which work is deferred
  * Collaboration is implemented simply by forwarding all calls to an object field
  * It has no dependence on implementation details of the object field
  * It is more flexible, since it is defined dynamically at run-time, not statically at compile-time
* Inheritance
  * Functionality of an object is made up of it's own functionality plus functionality from its parent classes

Sub-classing or inheritance has the following issues :

* It violates encapsulation, since the implementations of the superclass and subclass become tightly coupled
* new methods added to the superclass can break the subclass
* superclass and subclass need to evolve in parallel
* designing a class so that it may be safely extended takes extra work - extending a class not explicitly designed for such use is risky
* different packages are often under the control of different programmers - extending a class in a different package is risky

A common exception is the template method design pattern. There, the safest style is to make all items in the abstract base class final, except for the single abstract method which needs to be implemented by the subclass.