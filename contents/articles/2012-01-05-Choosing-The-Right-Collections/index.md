---
template: article.jade
title: Choosing the right collection
date: 2012-01-05 15:00
author: sanjeev
aliases: ['/post/2007/01/08/code-and-stuff/', '/post/2007/01/08/first/', '/post/2008/01/08/first']
categories: [technology]
tags: [java, best-practices]
excerpt: Here is a quick guide for selecting the proper implementation of a Set, List, or Map in your application.
---
Here is a quick guide for selecting the proper implementation of a Set, List, or Map in your application. 

The best general purpose or 'primary' implementations are likely ArrayList, LinkedHashMap, and LinkedHashSet. Their overall performance is better, and you should use them unless you need a special feature provided by another implementation. That special feature is usually ordering or sorting.

Here, "ordering" refers to the order of items returned by an Iterator, and "sorting" refers to sorting items according to [Comparable](http://docs.oracle.com/javase/6/docs/api/java/lang/Comparable.html) or [Comparator](http://docs.oracle.com/javase/6/docs/api/java/util/Comparator.html). 
 
<iframe width='100%' height='180' frameborder='0' src='https://docs.google.com/spreadsheet/pub?key=0Ap6Wf8mnIbkvdEI0LXZIN0V6c0JzcWxudTNsLWZBenc&output=html&widget=true'></iframe>
 

Principal features of non-primary implementations :

* HashMap has slightly better performance than LinkedHashMap
* HashSet has slightly better performance than LinkedHashSet
* TreeSet is ordered and sorted, but slow
* TreeMap is ordered and sorted, but slow
* LinkedList has fast adding to the start of the list, and fast deletion from the interior via iteration

Iteration order for above implementations :

* HashSet - undefined
* HashMap - undefined
* LinkedHashSet - insertion order
* LinkedHashMap - insertion order of keys (by default), or 'access order'
* ArrayList - insertion order
* LinkedList - insertion order
* TreeSet - ascending order, according to Comparable / Comparator
* TreeMap - ascending order of keys, according to Comparable / Comparator

For LinkedHashSet and LinkedHashMap, the re-insertion of an item does not affect insertion order.

While being used in a Map or Set, these items must not change state (hence, it is recommended that these items be immutable objects):

* keys of a Map
* items in a Set

Sorting requires either that :

* the stored items implement [Comparable](http://docs.oracle.com/javase/6/docs/api/java/lang/Comparable.html)
* a [Comparator](http://docs.oracle.com/javase/6/docs/api/java/util/Comparator.html) for the stored objects be defined

To retain the order of a ResultSet as specified in an ORDER BY clause, insert the records into a List or a LinkedHashMap.
