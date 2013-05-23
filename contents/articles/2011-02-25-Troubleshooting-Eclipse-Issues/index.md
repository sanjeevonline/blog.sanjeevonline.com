---
template: article.jade
title: Troubleshooting eclipse issues
date: 2011-02-25 15:00
author: sanjeev
aliases: ['/post/2007/01/08/code-and-stuff/', '/post/2007/01/08/first/', '/post/2008/01/08/first']
categories: [technology]
tags: [eclipse, productivity]
excerpt: Following are some tips that shall help you in avoiding potential issues and for being a little more productive while working with eclipse.
---
Following are some tips that shall help you in avoiding potential issues and for being a little more productive while working with eclipse.

* <b>Avoid installation problems</b>

	Never install a new version of Eclipse on top of an older version. Rename the old one first to move it out of the way, and let the new version be unpacked in a clean directory.

* <b>Recovering your messed up workspace</b>

	Corrupted workspace is a common occurrence and troublemaker for many developers. So If your Eclipse installation has startup errors or a corrupted configuration, it might be time to get a fresh start. Start Eclipse with the –clean option, and all cached framework and runtime data will be cleared out. This often helps fix plug-in issues and improve general stability.

<span class="more"></span>

* <b>Increase the memory allocation</b>

	With new plugins getting added to the core eclipse functionality and the need to use additional third party plugins, the memory requirements for your eclipse workspace increases. The default memory allocation configured in eclipse is not enough for most J2ee development projects and that causes a sluggish response from you eclipse. If you get Out of Memory errors or sluggish response, you may have to increase the defaults that are set in eclipse.ini file in the Eclipse installation directory. In particular, if you get an error about “PermGen” memory (permanent generation), add this line at the end and restart Eclipse: -

		XX:MaxPermSize=256m 

	Use the lowest memory settings that work and perform well for your mix of projects.

* <b>Side by side editing</b>

	By dragging editors, you can show two files side by side. You can also edit two portions of the same file by using the Window > New Editor command.

* <b>Automatic code improvements</b>

	Set up Eclipse to automatically format source code and organize imports on every save. Select Window > Preferences > Java Editor > Save Actions to enable these actions. This dialog also lets you configure actions like removing unnecessary casts or adding missing annotations. Configuring your eclipse with optimized Compiler, Formatter and CheckStyle settings is described in detail in the post Using Eclipse Effectively

* <b>Keyboard shortcuts</b>
	It is productive and convenient to use keyboard shortcuts for performing certain tasks in eclipse rather than looking for options to do the same in various navigation menus. For example looking up references of a variable, method or a class can be quickly achieved via shortcut Ctrl+Shift+g. For your reference I have included a list of the most important keyboard shortcuts in my post Eclipse Keyboard Shortcuts
