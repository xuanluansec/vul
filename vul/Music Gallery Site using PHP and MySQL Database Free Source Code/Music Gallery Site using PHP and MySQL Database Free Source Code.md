# Music Gallery Site using PHP and MySQL Database Free Source Code - Arbitrary file vulnerability uploading leads to command execution
+ Author: liwenjie
# Vendor Homepage
+ https://www.sourcecodester.com/php/16073/music-gallery-site-using-php-and-mysql-database-free-source-code.html
# Software Link
+ https://www.sourcecodester.com/sites/default/files/download/oretnom23/php-music.zip
# Overview
+ liwenjie has discovered a vulnerability classified as critical in Music Gallery Site using PHP and MySQL Database Free Source Code V1.0. The function upload is affected. This operation will result in unrestricted uploads. Remote attacks can cause RCE.And this process does not require any authentication.
# Vulnerability Details
+ Music Gallery Site using PHP and MySQL Database Free Source Code V1.0
+ Vulnerable File: classes/Master.php?f=save_music
+ Parameter Names: audio_file
+ Attack Type: Remote
# Description
+ liwenjie has discovered a vulnerability classified as critical in Music Gallery Site using PHP and MySQL Database Free Source Code V1.0. The function upload is affected. This operation will result in unrestricted uploads. Remote attacks can cause RCE.And this process does not require any authentication.
# Note
+ No authentication is required to exploit this vulnerability.
# Proof of Concept (PoC) : 

![1](https://github.com/xuanluansec/vul/blob/main/vul/img/24.png)
```
POST request package:https://github.com/xuanluansec/vul/blob/main/vul/Music%20Gallery%20Site%20using%20PHP%20and%20MySQL%20Database%20Free%20Source%20Code/post.txt
```
# Note: Markdown syntax may not be displayed completely.

open http://www.php-music.com:8096/uploads/audio/aaa.php
![2](https://github.com/xuanluansec/vul/blob/main/vul/img/25.png)
