---
template: article.jade
title: New Date and Time API in Java8
date: 2013-05-28 01:00
author: sanjeev
aliases: ['/post/2007/01/08/code-and-stuff/', '/post/2007/01/08/first/', '/post/2008/01/08/first']
categories: [technology]
tags: [java]
excerpt: The existing Java date and time classes are poor, mutable, and have unpredictable performance. There has been a long-standing desire for a better date and time API based on the Joda-Time project. The good news is that the ...
---
At some point during your day-to-day coding experience with Java you might have realised that the existing Java date and time classes are poor, mutable, and have unpredictable performance. There has been a long-standing desire for a better date and time API based on the [Joda-Time](http://joda-time.sourceforge.net/) project. The good news is that the new API that got delivered with [JDK8 milestone M6](http://openjdk.java.net/projects/jdk8/milestones#M6) has a more intuitive design allowing code to better express its intent. The classes are immutable which aligns with the multi-core direction of the industry.

<span class="more"></span>

The code for this new API originated on Sourceforge and then migrated to [GitHub](https://github.com/ThreeTen/threeten) and further got integrated into OpenJDK. Eventually, [JSR-310](http://jcp.org/en/jsr/detail?id=310) has now simply become a part of the greater JDK8 JSR.

Find more about it and JDK8 at 

* [Project Joda-Time](http://joda-time.sourceforge.net/)
* [Project ThreeTen](http://sourceforge.net/apps/mediawiki/threeten/index.php?title=ThreeTen)
* [InfoQ Post on the same](http://www.infoq.com/news/2012/09/jsr310-java8)
* [JDK8 feature list](http://openjdk.java.net/projects/jdk8/features)
