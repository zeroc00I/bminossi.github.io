---
title:  "Arbitrary Upload Any File Extetions"
youtubeId: V7JG_I3TlcQ
author: Khaled Mohamed
categories: [PoC]
tags: ["Stored XSS","Unrestricted File Upload","RCE"]
math: true
---

Hello Everybody today i write about Arbitrary File Upload

Cause occurrence ?

It is because The Developer did not check the file extinsion or type ! Or there is a check but from javascript no php which to

Find the file the responsible for uploads Or if you have the Full source code php maybe you found function 

or any code Harmful that was found ……

And Create an external file html to upload files to the responsible file ? you understand 

![Source Vulnerable](/assets/img/PoC/source-code-Arbitrary.png)

You can Show the html upload code..

    <!DOCTYPE html>
    <html>
    <head>
    <title>Upload xElkomy</title>
    </head>
    <body>
    <form name="upload" method="POST" enctype="multipart/form-data" 
    action="https://xxxxxxxxxxx.com/asp/app/Upload/upload.asp?method=UPLOAD">
    <label>Uploading File Arbitrary</label>
    <input type="file" required name="myfile"><br><br>
    <input type="submit" name="upload" value="Upload - xELKOMY" >
    </form>
    </body>
    </html>
    
Now you understand.
You can read this Also https://medium.com/bugbountywriteup/arbitrary-file-upload-from-a-different-angle-1193ffb80b09

    Less common? Why?
    Because any platform with sane developers will validate the content type and the file extension of any file they interact with.
    But today I want to introduce you with a new validation attitude that I now advise
    everyone to use – validate the content itself.
    If you are expecting an image to be uploaded – expect the content to be suited as a content of an image. 
    If you are expecting an html
    file – sanitize it and make sure no script tags exist. There are plenty of libraries and tools to do that.
    

POC Me :-

{% include youtubePlayer.html id=page.youtubeId %}

I hope you will like it
#xELkomy
