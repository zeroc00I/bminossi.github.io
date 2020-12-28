---
title: Bite Size Bash and things to keep in mind
author: Zeroc00I
categories: bash
tags: ["bash","sh","shellscript"]
math: true
---

 For those that have not already download Bite Size Bash book from Julia, i would like to suggest you do it in order to improve your knowledge in Unix Shells =)

 ![Bite Size Bash Book](/assets/bitesizebash.jpg)

 Go to her website: https://wizardzines.com/
 Or directly from book sale on: https://gumroad.com/l/bite-size-linux

#  Command Substitution vs Pipeline
 If you dont undestand the concepts between both, check out the examples bellow

## Pipeline seems like

	ls | head

## Otherwise Command Substitution

	head <(ls)

 The benefits of using command substituition intead pipeline is that you have more control of the output, just like named pipelines using MKFIFO.

	wget -O - http://example.com/dvd.iso | tee >(sha1sum > dvd.sha1) >(md5sum > dvd.md5) > dvd.iso

