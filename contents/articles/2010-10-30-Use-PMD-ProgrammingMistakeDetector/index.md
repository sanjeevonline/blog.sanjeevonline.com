---
template: article.jade
title: Use PMD - Programming Mistake Detector?
date: 2010-10-30 15:00
author: sanjeev
aliases: ['/post/2007/01/08/code-and-stuff/', '/post/2007/01/08/first/', '/post/2008/01/08/first']
categories: [technology]
tags: [java, best-practices]
excerpt: How do you ensure that your code follows standard programming principles? For most Java development projects going on these days the answer would be to use "PMD"...
---

<h3>About PMD</h3>

How do you ensure that your code follows standard programming principles? For most Java development projects going on these days the answer would be to use "PMD". It is aiming towards becoming a de-facto tool for analyzing the source code and is being used by more and more Java applications everyday. 

<b>Note</b>: There are a lot many tools that PMD competes with i.e Checkstyle, FindBugs, Hammurapi, Soot, Squale etc. However exploring capabilities of these tools(other than PMD) are out of scope of this article.

PMD is a static rule set based Java source code analyzer that identifies potential problems in the code like:

1. Possible bugs - empty try/catch/finally/switch statements
2. Dead code - unused local variables, parameters and private methods
3. Suboptimal code - wasteful String/StringBuffer usage
4. Overcomplicated expressions - unnecessary if statements, for loops that could be while loops
5. Duplicate code - copied/pasted code means copied/pasted bugs

You can [download everything from here](http://sourceforge.net/project/showfiles.php?group_id=56262), and you can get an overview of all the rules at the [rulesets index page](http://pmd.sourceforge.net/rules/index.html).

PMD is integrated with JDeveloper, Eclipse, JEdit, JBuilder, BlueJ, CodeGuide, NetBeans/Sun Java Studio Enterprise/Creator, IntelliJ IDEA, TextPad, Maven, Ant, Gel, JCreator, and Emacs.

<h3>Instructions for configuring PMD for Eclipse</h3>


Let me walk you through the steps required to quickly configure it with your Eclipse installation. It works like a breeze.

1. Start Eclipse.
2. Start the installation procedure : select the Help>Software Updates>Find and Install... menu item.
3. Select "Search for new features to install" option and click Next.
4. Click New Remote Site...
5. Give a name (ie PMD Eclipse Site), enter the URL http://pmd.sourceforge.net/eclipse
6. Select this new site in the Sites to include in search list and click Next.
7. Select PMD for Eclipse 3 and Apache Xerces in the "Select the features to install" list and click Next.
8. Accept the terms of the license agreements and click Next.
9. Verify that the install location is your Eclipse installation directory, otherwise select the correct one, click Finish.
10. A warning appear telling the feature is not signed. Ignore and click Install to continue.
11. Accept to restart the workbench to load PMD into the workbench.
Eclipse is restarted and a PMD welcome page is displayed : the plugin is correctly installed. 

<h3>Writing custom rules</h3>

It is interesting and important to note that you can write your custom rules. Writing PMD rules is cool because you don't have to wait for PMD team to get around to implementing feature requests. Following are the two approaches to write custom rules.
1. Write a rule using Java
2. Write an XPath expression
More details about each of these approaches can be found at [sourceforge](http://pmd.sourceforge.net/howtowritearule.html).


Happy coding.. 
