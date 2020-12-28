---
title: Bite Size Bash and things to keep in mind
author: Zeroc00I
categories: bash
tags: ["bash","sh","shellscript"]
math: true
---

 For those that have not already purchased Bite Size Bash book from Julia, i would like to suggest you do it in order to improve your knowledge in Unix Shells =)

 ![Bite Size Bash Book](/assets/img/bitesizebash.jpg)

 Go to her website:
 [https://wizardzines.com/] (https://wizardzines.com/)
 
 Or directly from book sale on: 
 [https://gumroad.com/l/bite-size-linux] (https://gumroad.com/l/bite-size-linux)

#  Command Substitution vs Pipeline
 (If you dont undestand the concepts between both, check out the examples bellow)

## Pipeline seems like

	ls | head

## Otherwise Command Substitution

	head <(ls)

 The benefits of using command substituition intead pipeline is that you have more control of the output, just like named pipelines using MKFIFO.

	wget -O - http://example.com/dvd.iso | tee >(sha1sum > dvd.sha1) >(md5sum > dvd.md5) > dvd.iso

# Parameter expansion ${} - There are some very usefull tricks

### Similar to sed functionality, we can do the following replacing patterns to another string

	soOutput=`cat /etc/lsb-release`

	DISTRIB_ID=Ubuntu DISTRIB_RELEASE=19.10 DISTRIB_CODENAME=eoan DISTRIB_DESCRIPTION="Ubuntu 19.10"

	echo ${soOutput//Ubuntu/Kali}
	DISTRIB_ID=Kali DISTRIB_RELEASE=19.10 DISTRIB_CODENAME=eoan DISTRIB_DESCRIPTION="Kali 19.10"


### Similar to wc -c

	echo $soOutput | wc -c
	96

	echo ${#soOutput}
	96

## Check unset/null variable

	idunno="echo hi"

	${thisvariabledoesntexist:-$idunno}

 Output: 

	hi

## Take better control of exceptions

	${nothingwasset:?this variable doesnt exist}

 Output:

	bash: nothingwasset: this variable doesnt exist

# Trap - Calling a command when some intended event ocurr

### Print currently day when Ctrl + C is pressed

	trap '$(date +%d)' EXIT

# Set -euo and erros in bash

## Stops the script on erros

	set -e

## Stops on unset variables

	set -u

### Stops the script when any command fail

	set -o pipefail

### Bonus: Debugging every line with all variables expanded

	set -x or bash -x script.sh
