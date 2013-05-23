---
template: article.jade
title: Change default author name for JavaDocs in Eclipse
date: 2011-08-03 15:00
author: sanjeev
aliases: ['/post/2007/01/08/code-and-stuff/', '/post/2007/01/08/first/', '/post/2008/01/08/first']
categories: [technology]
tags: [eclipse]
excerpt: The auto generated Java docs at the class level picks the user name from the system user.
---
The auto generated Java docs at the class level picks the user name from the system user. This could result in weird author names in your code files as in an organization usernames are usually as per organizational naming conventions. For example my user name that I use to login is something like SK0012345 and you will agree that it wouldn't look good as an author name in a Java file and might not make any sense to most other viewers of the code. 

	/**
 	* Test default author in JavaDocs
 	* @author SK0012345
 	*/
	public class TestClass {
	}

Here is a quick way to change the default author name in your Eclipse projects. Simply edit your eclipse.ini file found in the root directory where you placed Eclipse. I have Eclipse at C:\devtools\development\eclipse, so my path would be C:\devtools\development\eclipse\eclipse.ini. Once editing this file add the following line and save.

<span class="more"></span>

	-Duser.name=Sanjeev Kumar

After saving restart Eclipse and when you do a JavaDoc comment and use the author attribute by typing @author and pressing enter on the autocomplete you will see something like this:

	/**
 	* Test default author in JavaDocs
 	* @author Sanjeev Kumar
 	*/
	public class TestClass {
	}

Simple yet useful. Happy coding!
