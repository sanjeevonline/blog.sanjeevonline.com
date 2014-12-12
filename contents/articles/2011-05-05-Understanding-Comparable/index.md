---
template: article.jade
title: Implementing Comparable and understanding compareTo
date: 2011-03-20 15:00
author: sanjeev
aliases: ['/post/2007/01/08/code-and-stuff/', '/post/2007/01/08/first/', '/post/2008/01/08/first']
categories: [technology]
tags: [java, best-practices, technology]
excerpt: Implementing Comparable and understanding compareTo 
---

<h3>Implementing Comparable</h3>

Implementing Comparable allows:

1. Calling Collections.sort and Collections.binarySearch.
2. Calling Arrays.sort and Arrays.binarySearch.
3. Using objects as keys in a TreeMap.
4. Using objects as elements in a TreeSet.

<span class="more"></span>

<h3>Understanding compareTo</h3>

The compareTo() method is the sole member of Comparable interface. It provides a means of fully ordering objects. For a concrete comparable implementation class to work well, the compareTo() implementation needs to satisfy the certain conditions.

1. Anti Commutation :  x.compareTo(y) is the opposite sign of y.compareTo(x)
2. Exception Symmetry : x.compareTo(y) throws exactly the same exceptions as y.compareTo(x)
3. Transitivity :  
	1. if x.compareTo(y) > 0 and y.compareTo(z) > 0, then x.compareTo(z) > 0  (and same for less than)
	2. if x.compareTo(y)==0, then x.compareTo(z) has the same sign as y.compareTo(z)
4. consistency with equals : It is highly recommended, but not required : x.compareTo(y) == 0, if and only if x.equals(y) ; consistency with equals is required for ensuring sorted collections (such as TreeSet) are well-behaved.

<h3>Things to remember while implementing compareTo()</h3>

Compare the various types of fields as follows :

1. Numeric primitive : use < and >. There is an exception to this rule: float and double primitives should be compared using Float.compare(float, float) and Double.compare(double, double). This avoids problems associated with special border values.
2. Boolean primitive :  use tests of the form (x && !y)
3. Object : use compareTo. (Note that possibly-null fields present a problem : while x.equals(null) returns false, x.compareTo(null) will always throw a NullPointerException)
4. Type-safe enumeration : use compareTo, like any Object
5. collection or array : Comparable does not seem to be intended for these kinds of fields. For example, List, Map and Set do not implement Comparable. As well, some collections have no definite order of iteration, so doing an element-by-element comparison cannot be meaningful in those cases.

<h3>Comparable implementations in JDK</h3>

All primitive wrapper classes like Integer, Long, Float, Double, Boolean and many more implement Comparable.  

<h3>Hot tips</h3>

1. One can greatly increase the performance of compareTo by comparing first on items which are most likely to differ.
2. Avoid instanceof in methods that override or implement Object.equals(), Comparable.compareTo()
3. If the task is to perform a sort of items which are stored in a relational database, then it is usually much preferred to let the database perform the sort using the ORDER BY clause, rather than in code.
4. An alternative to implementing Comparable is passing Comparator objects as parameters. Be aware that if a Comparator compares only one of several significant fields, then the Comparator is very likely not synchronized with equals.
5. When a class extends a concrete Comparable class and adds a significant field, a correct implementation of compareTo cannot be constructed. The only alternative is to use composition instead of inheritance. (A similar situation holds true for equals. See Effective Java for more information.)
