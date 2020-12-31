---
title: Keeping your nmap updated
author: Zeroc00I
categories: nmap
tags: ["nse","nmap"]
math: true
---

#  This script creates nse files, directly from their svn repo :)
 You can increase parallel download files if you want (currently -P20)
	
	curl -sf 'https://svn.nmap.org/nmap/scripts/' | \
	tr '<>"' '\n' | awk '/.nse/{print "https://svn.nmap.org/nmap/scripts/"$1}' | \
	sort -u | \
	xargs -P20 -I@ wget -o /usr/share/nmap/scripts/ @
