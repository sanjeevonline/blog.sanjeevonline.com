---
template: article.jade
title: Avoiding null pointer exceptions
date: 2010-11-27 15:00
author: sanjeev
aliases: ['/post/2007/01/08/code-and-stuff/', '/post/2007/01/08/first/', '/post/2008/01/08/first']
categories: [technology]
tags: [java, best-practices]
excerpt: Null pointer exceptions(NPE) are the undoubtedly the most common and most annoying errors. In most cases I have observed that it could have been avoided by simply sticking to some best coding practices while writing code. 
---
Null pointer exceptions(NPE) are the undoubtedly the most common and most annoying errors. In most cases I have observed that it could have been avoided by simply sticking to some best coding practices while writing code. Here is an example of a potential NPE.

    // BAD CODE
    private Boolean isExpired(final StatusEnum status) {
        if (status.equals(StatusEnum.EXPIRED)) { // Potential null pointer if status is null.
            return Boolean.TRUE;
        } else {
            return Boolean.FALSE;
        }
    }

Here if the "status" that is passed to the method is null you will get a NPE at the first statement in the method. However if we write the code like as follows it can be avoided.

    //GOOD CODE
    private Boolean isExpired(final StatusEnum status) {
        if (StatusEnum.EXPIRED.equals(status)) { // Move variable part as parameter to equals method.
            return Boolean.TRUE;
        } else {
            return Boolean.FALSE;
        }
    }
Some editors like IntelliJ provide a quick fix for similar use cases. If you have object.equals(”string literal”) it can replace with “string literal”.equals(object)  and you can do the replace all on your entire code base in one go if you wish. 

Happy coding!!
