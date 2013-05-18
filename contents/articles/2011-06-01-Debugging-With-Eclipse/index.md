---
template: article.jade
title: Skip over certain classes when using Step Into(F5) in Eclipse’s debugger
date: 2011-06-01 15:00
author: sanjeev
aliases: ['/post/2007/01/08/code-and-stuff/', '/post/2007/01/08/first/', '/post/2008/01/08/first']
categories: [technology]
tags: [eclipse, productivity]
excerpt: Whenever I use the Step Into feature (F5) in Eclipse’s debugger, I’m mainly interested in stepping through code in my own classes, not the ones from external libraries or even Java classes.
---
Whenever I use the Step Into feature (F5) in Eclipse’s debugger, I’m mainly interested in stepping through code in my own classes, not the ones from external libraries or even Java classes.

For example, there’s almost no reason to ever want to step into Spring’s code or proxy classes (other than to learn more about them or maybe debug a potential bug in Spring). And normally I’m not interested in Java util classes (eg. ArrayList). This also goes for Hibernate, Apache Commons, Google and many other external libraries.

Fortunately, Eclipse makes it easy to specify which classes to skip by allowing step filters. This makes it easier to focus on your own code and also keeps your editor area clean since Eclipse won’t be opening classes in separate editors all the time.

<h3>Enable Step Filters</h3>

To use step filters, the first step is to enable it. Eclipse comes with some default filters so let’s start by enabling them all. This will filter all Java classes (ie. java.) and all Sun classes (ie. sun.).

1. Go to Window > Preferences > Java > Debug > Step Filtering.
2. Select the option Use Step Filters.
3. Click Select All to enable all the filters.
4. Leave the other options below the filter list as-is.

Here’s an example of what it should look like:

![Debug setting in eclipse](http://i.imgur.com/jO19t.jpg)

NB: Even with step filters enabled, you can still set breakpoints within any of these classes (if you have the source) and Eclipse will still stop at the breakpoint. Step filtering only affects the way that Step Into works.

Also note that Eclipse will still step into your classes if they’re called from the ignored classes. For example, when you call Collections.sort(List, Comparator) and pass your own Comparator implementation, Eclipse will not step into the sort code, but it will step into your Comparator when it’s called by the sort code.

If you want to change this behaviour (ie. prevent Eclipse from stopping in your method), then deselect Step through filters. However, I’d recommend only doing this if you’ve tried out the default, because most times you’ll probably want to step through your own code.

<h3>The next step is to create some step filters of your own.</h3>

Once you’ve enabled step filters, all you have to do is add the classes you want to filter. Let’s assume that we want to ignore all classes from Spring, especially proxy classes.

 1. If you’re not there already, go to Window > Preferences > Java > Debug > Step Filtering
 2. Click Add Filter… A dialog should appear prompting you to enter a pattern
 3. Enter a regular expression for the classes you want to filter in the Pattern to filter field then click Ok. In our example, enter org.springframework.* (see image below). It’s easier to specify the top level package name with an asterix at the end
 4. Add another filter with the pattern $Proxy* to skip over Spring proxy classes (eg. when using Spring Transactions)
 5. Click Ok on the Preferences dialog when you’re done

Here’s what the step filter pattern dialog should look like:

![Filter pattern dialog](http://i.imgur.com/2RWRS.jpg)

Now when you use the debugger, you won’t be taken into Spring classes when you use Step Into (F5).

<h3>Some ideas for custom filters</h3>

In addition to the Spring classes, you might also want to consider adding the following common libraries to your step filters to make debugging easier:

* org.apache.*
* org.hibernate.*
* com.google.*
* org.eclipse.*
* org.osgi.*

The last two are especially useful if you’re doing Eclipse RCP and/or OSGi development.
