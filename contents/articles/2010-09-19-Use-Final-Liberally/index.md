---
template: article.jade
title: Use final liberally. Please do.
date: 2010-09-19 15:00
author: sanjeev
aliases: ['/post/2007/01/08/code-and-stuff/', '/post/2007/01/08/first/', '/post/2008/01/08/first']
categories: [technology]
tags: [java, best-practices]
excerpt: Use the final keyword liberally to communicate your intent
---
Use the final keyword liberally to communicate your intent. The final keyword has more than one meaning :

* a final class cannot be extended
* a final method cannot be overridden
* final fields, parameters, and local variables cannot change their value once set

In the last case, "value" for primitives is understood in the usual sense, while "value" for objects means the object's identity, not its state. Once the identity of a final object reference is set, it can still change its state, but not its identity. Declaring primitive fields as final automatically ensures thread-safety for that field.

Some habitually declare parameters as final, since this almost always is the desired behaviour. Others find this verbose, and of little real benefit.

Consistently using final with local variables (when appropriate) can be useful as well. It brings attention to the non-final local variables, which usually have more logic associated with them (for example, result variables, accumulators, loop variables). Many find this verbose. A reasonable approach is to use final for local variables only if there is at least one non-final local variable in the method ; this serves to quickly distinguish the non-final local variables from the others.

Using final :

* clearly communicates your intent
* allows the compiler and virtual machine to perform minor optimizations
* clearly flags items which are simpler in behavior - final says,  "If you are looking for complexity, you won't find it here."
