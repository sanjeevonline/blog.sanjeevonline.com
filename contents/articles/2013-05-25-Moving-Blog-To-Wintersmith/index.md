---
template: article.jade
title: Re-platformig this blog to Wintersmith
date: 2013-05-25 01:00
author: sanjeev
aliases: ['/post/2007/01/08/code-and-stuff/', '/post/2007/01/08/first/', '/post/2008/01/08/first']
categories: [technology]
tags: [nodejs]
excerpt: After deferring it for more than a year, finally I decided to re-platform my blog. I had several viable options at hand like -
---
After deferring it for more than a year, finally I decided to re-platform my blog. I had several viable options at hand like -

1. Dynamic blogs
	1. Based on [Enki](http://www.enkiblog.com/)
	2. Custom app that I can host on [Heroku](www.heroku.com)
	3. Java, Pyhton or go based app on [Google App Engine](https://developers.google.com/appengine/)
2. Static blogs
	1. [Google sites](sites.google.com)
	2. Ruby based [Jekyll](http://jekyllrb.com/)
	3. Python based [Hyde](http://hyde.github.io/)
	3. NodeJs based [Wintersmith](http://jnordberg.github.io/wintersmith/)

After careful analysis and googling about it yielded that for a simple site like this blog it would be a little too much of work to take the Dynamic blog route and sticking to a static site generator would be quicker, easier and maintainable. Besides static sites perform better and can be hosted anywhere.

<span class="more"></span>

My earlier version of this blog was hosted on Google Sites for few years, which was good but there were some limitations to the kind of javascript, css, styles and themes that you can use and I wanted complete freedom. Ruby based Jekyll and Python based Hyde also looked promising but NodeJs based Wintersmith was simply impressive. Learning JavaScript and NodeJs being one of my personal goal for this year, it was the option that looked best.

So here it is, my new blog based on Wintersmith.

Some of the benefits of going with Wintersmith are -

1. Small and simple [codebase](https://github.com/jnordberg/wintersmith)
2. [Jade](http://jade-lang.com/) templates
3. Nice [plugin](https://github.com/jnordberg/wintersmith/wiki/Plugins) system
4. [Underscore.js](http://underscorejs.org/) which is great when working with templates
5. Being a Mac user it was fairly easy to setup it up and I was able to get it up and running in few minutes
6. I can continue to use my favourite Markdown in my favourite Mou editor
7. I spend a lot of time on Github anyways so having [my site's code](https://github.com/sanjeevonline/sanjeevonline.com) and generated site on Git itself is comforting
