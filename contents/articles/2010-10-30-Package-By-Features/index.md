---
template: article.jade
title: Package by feature not layer
date: 2010-10-20 15:00
author: sanjeev
aliases: ['/post/2007/01/08/code-and-stuff/', '/post/2007/01/08/first/', '/post/2008/01/08/first']
categories: [technology]
tags: [best-practices, java]
excerpt: The first question that we normaly phase whie building an application is "How do I divide it up into packages?". For typical business applications, there seems to be two ways of answering this question.
---
The first question in building an application is "How do I divide it up into packages?". For typical business applications, there seems to be two ways of answering this question.

* Package by feature
* Package by layer

In my experience, the package-by-feature style seems to be the superior of the two. Here are some of the reasoning:

<span class="more"></span>

* <b>Higher Modularity</b>: As mentioned above, only package-by-feature has packages with high cohesion, high modularity, and low coupling between packages.
* <b>Easier Code Navigation</b>: Maintenance programmers need to do a lot less searching for items, since all items needed for a given task are usually in the same directory. Some tools that encourage package-by-layer use package naming conventions to ease the problem of tedious code navigation. However, package-by-feature transcends the need for such conventions in the first place, by greatly reducing the need to navigate between directories.
* <b>Higher Level of Abstraction</b>: Staying at a high level of abstraction is one of programming's guiding principles of lasting value. It makes it easier to think about a problem, and emphasizes fundamental services over implementation details. As a direct benefit of being at a high level of abstraction, the application becomes more self-documenting : the overall size of the application is communicated by the number of packages, and the basic features are communicated by the package names. The fundamental flaw with package-by-layer style, on the other hand, is that it puts implementation details ahead of high level abstractions - which is backwards.
* <b>Separates Both Features and Layers</b>: The package-by-feature style still honors the idea of separating layers, but that separation is implemented using separate classes. The package-by-layer style, on the other hand, implements that separation using both separate classes and separate packages, which does not seem necessary or desirable.
* <b>Minimizes Scope</b>: Minimizing scope is another guiding principle of lasting value. Here, package-by-feature allows some classes to decrease their scope from public to package-private. This is a significant change, and will help to minimize ripple effects. The package-by-layer style, on the other hand, effectively abandons package-private scope, and forces you to implement nearly all items as public. This is a fundamental flaw, since it doesn't allow you to minimize ripple effects by keeping secrets.
* <b>Better Growth Style</b>: In the package-by-feature style, the number of classes within each package remains limited to the items related to a specific feature. If a package becomes too large, it may be refactored in a natural way into two or more packages. The package-by-layer style, on the other hand, is monolithic. As an application grows in size, the number of packages remains roughly the same, while the number of classes in each package will increase without bound.

<h4>Credits & References</h4>

* [Java Gyan](http://www.javagyan.com/articles/packagebyfeaturenotlayer)
