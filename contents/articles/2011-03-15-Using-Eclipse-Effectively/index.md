---
template: article.jade
title: Using Eclipse effectively
date: 2011-03-15 15:00
author: sanjeev
aliases: ['/post/2007/01/08/code-and-stuff/', '/post/2007/01/08/first/', '/post/2008/01/08/first']
categories: [technology]
tags: [eclipse, best-practices, productivity]
excerpt: To ensure that the code that you write is always clean and complaint to your project specific coding standards and guidelines, it is important that you configure your eclipse to effectively use its compiler settings, Formatter, CheckStyle and related built in features.
---

To ensure that the code that you write is always clean and complaint to your project specific coding standards and guidelines, it is important that you configure your eclipse to effectively use its compiler settings, Formatter, CheckStyle and related built in features. Most developers wouldn't bother to do so but trust me that it is huge time saver in long run and shall always keep your code quality under check.

Following spread sheet has the configuration that we use in our current projects. You can customize these settings according to your development standards and needs. 

<iframe width='100%' height='500' frameborder='0' src='https://docs.google.com/spreadsheet/pub?key=0Ap6Wf8mnIbkvdFZnZTNweGxOd2haZnpyN1NPSXNZNkE&output=html&widget=true'></iframe>

Also ideally your Eclipse should be configured with your "code formatter" and "CheckStyle" XML configurations. 

<span class="more"></span>

To start with you can simply import these xmls that are attached to this page to enable code formatting and checkstyle for your code. You can get more detail on CheckStyle at http://checkstyle.sourceforge.net/. 

Links to configure the CheckStyle, Formatter and compiler setting can be found under your Eclipse-->Preferences menu.

Here the checkstyle and formatter that I  use on my projects 

* [Java code formatter configuration XML](https://docs.google.com/file/d/0B56Wf8mnIbkvVm9saFEwaHE0UWM/edit?usp=sharing)
* [Checkstyle configuration XML](https://docs.google.com/file/d/0B56Wf8mnIbkvX0pualpCWnRpc0E/edit?usp=sharing)

