---
title: RXSS in The URL Path
author: Khaled Mohamed [xElkomy]
categories: [PoC]
tags: ["Reflected XSS","Cross Site Scripting"]
math: true
---

### السلام عليكم ورحمة الله وبركاتة

Hello everyone today i write about bug i found in some programs :)

this bug called Refelcted XSS in url path 

and this bug is very easy to understand from everyone.

##################################

Weakness: Cross-site Scripting (XSS) - Generic

Impact: Same impact for any Reflected XSS :)

How we Discover this :-

In any target you test you can add some charcters in path after first Slash

Such this :-

  `http://example.com/'"\>`

  `http://example.com/'\>`

  `http://example.com/"\>`

  `http://example.com/'>`

  ......etc
But I love this (%0A("')) Or this (A("'))

after this we can see like this Image :-

![Source Vulnerable](/assets/img/PoC/Capture.PNG)

Now we have Bug here :-

and in this case we need in this moment exploit this Bug for be RXSS >

## Exploit:-

After add this in url and found this is reflective in target we need exploited this bug 

http://example.com/(A("'))

In my mind i add event handler how we found that double qute in this target in close href

ok now we remove ' and add event handler 

To be the final form Like this

http://example.com/(A("onerror='alert(1)'))

But Unfortunately this site block The Brackets after alert 

Now we can add something differnt in javascript change alert(1) to `` alert`1` ``

After this we have Reflected XSS is good bug for good bounty :)

## Reason this bug:-

Because the developer Include some attachments from paths

Not built-in in source for this page but it's dynamic because this allow user change something but he includes this path from URL from the clients

The End...


I'm sorry for my English language




