---
title: Keeping your nmap updated
author: Zeroc00I
categories: nmap
tags: ["nse","nmap"]
math: true
---

#  This script create nse files, directly from their svn repo :)
 You can increse parallel download (currently -P20)
	
	curl -sf 'https://svn.nmap.org/nmap/scripts/' | tr '<>"' '\n' | awk '/.nse/{print "https://svn.nmap.org/nmap/scripts/"$1}' | sort -u | xargs -P20 -I@ wget @
