---
layout:     post
title:      Debugging Ajax
date:       2006-02-28
categories: Debugging
---
I stumbled upon a useful little tip for examining the current html of a web  page. This is very useful when the current state of a dynamic page needs to be  looked at.

[http://blogs.telerik.com/blogs/rumen_stankov/archive/2006/02/20/124.aspx](http://blogs.telerik.com/blogs/rumen_stankov/archive/2006/02/20/124.aspx)

Basically, to look at the current html of a web page type the following  into the address bar :-

```javascript:\'&lt;xmp&gt;\' + window.document.body.outerHTML +  \'&lt;/xmp&gt;\'```

This can be done with firefox via the **View Generated Source** extension, so this is just an IE hack really.