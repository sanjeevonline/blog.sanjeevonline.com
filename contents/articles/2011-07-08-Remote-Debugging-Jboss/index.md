---
template: article.jade
title: Remote debugging in Eclipse
date: 2011-07-08 15:00
author: sanjeev
aliases: ['/post/2007/01/08/code-and-stuff/', '/post/2007/01/08/first/', '/post/2008/01/08/first']
categories: [technology]
tags: [eclipse]
excerpt: To debug your application on JBOSS server you would need to enable the debugging on your JBOSS application server
---
To debug your application on JBOSS server you would need to enable the debugging on your JBOSS application server. By default it is turned off. In order to set jboss app server to be running in debugging mode, you should uncomment following line in "jboss-5.1.0.GA/jboss/bin/run.conf"

like this:

	#Sample JPDA settings for remote socket debugging
	JAVA_OPTS=”$JAVA_OPTS -Xrunjdwp:transport=dt_socket,address=8787,serve 

Once done you can configure your eclipse remote application debugger on port 8787 and start debugging your application.

Happy debugging !!
