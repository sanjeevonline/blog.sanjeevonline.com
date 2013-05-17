---
template: article.jade
title: Beware of floating point numbers
date: 2010-10-20 15:00
author: sanjeev
aliases: ['/post/2007/01/08/code-and-stuff/', '/post/2007/01/08/first/', '/post/2008/01/08/first']
categories: [technology]
tags: [java, best-practices]
excerpt: iOutside of a scientific or engineering context, the use of float and double (and the corresponding wrapper classes Float and Double ) should likely be avoided.
---
Outside of a scientific or engineering context, the use of float and double (and the corresponding wrapper classes Float and Double ) should likely be avoided. The fundamental problem is that rounding errors will always occur when using these data types - they are unavoidable.

In a typical business application, using float and double to represent money values is dangerous, because of these rounding issues. Instead, BigDecimal should usually be used to represent money. It is also a common practice to have utility classes like "MonetaryAmount.java" that are wrappers over "BigDecimal" class of the JDK and that provides helper methods and functionality as needed by the business application.

From an IBM article on this topic :

<i>
"...binary floating-point arithmetic should not be used for financial, commercial, and user-centric applications or web services because the decimal data used in these applications cannot be represented exactly using binary floating-point."
</i>

From an article by Brian Goetz :

<i>
"...it is a bad idea to use floating point to try to represent exact quantities like monetary amounts. Using floating point for dollars-and-cents calculations is a recipe for disaster. Floating point numbers are best reserved for values such as measurements, whose values are fundamentally inexact to begin with." 
</i>
