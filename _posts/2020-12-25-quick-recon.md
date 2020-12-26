---
title: Quick recon commands
author: Zeroc00I
categories: recon
tags: ["bash","recon"]
math: true
---

# Manual Filtering alive hosts :
	
	By Ip resolution
	xargs -P 500 -a hostswordlist -I@ sh -c 'dig @ | \
	grep -q NOERROR 1>/dev/null && echo | echo @;'
	
	By open 80 port
	xargs -P 500 -a hostswordlist -I@ sh -c 'nc -w1 -z -v @ 80 2>/dev/null && echo @'

# Extract Only Http using gospider (required anew instalation):

	xargs -P 500 -a hosts -I@ sh -c 'nc -w1 -z -v @ 443 2>/dev/null && echo @' | \

	xargs -I@ -P10 sh -c 'gospider -a -s "https://@" -d 2 | grep -Eo "(http|https)://[^/\"]+" | anew httponly'

# Extract only JS using gospider (required anew instalation):

	xargs -P 500 -a hostswordlist -I@ sh -c 'nc -w1 -z -v @ 443 2>/dev/null && echo @' | \
	xargs -I@ -P10 sh -c 'gospider -a -s "https://@" -d 2 | grep -Eo "(http|https)://[^/\"].*.js+" | sed "s#\] \- #\n#g" | anew jsonly'

# Mass portscanner:
	docker run ilyaglow/masscan -Pn --ports 0-65535 --rate 10000 CIDRHERE
