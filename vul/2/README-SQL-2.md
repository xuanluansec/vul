# php task management system free download - SQL injection vulnerability

### You do not need to log in to the website to remotely trigger SQL injection vulnerabilities!

Supplier:https://www.sourcecodester.com/php/17217/employee-management-system-php-and-mysql-free-download.html

http://localhost/update-admin.php?admin_id=1   -----> 'admin_id' can control some admin_id parameters

Payload:update-admin.php?admin_id=1'+AND+(SELECT+8088+FROM+(SELECT(SLEEP(10)))a)+AND+'1'%3d'1

When you execute this payload, you will notice a delay of around 10 seconds. This indicates that the sleep statement has been successfully executed in the database, causing a SQL injection vulnerability.

![1](https://github.com/xuanluansec/vul/blob/main/vul/img/5.png)

The parameter received on line 15 of the update-admin.php file in the website's root directory triggers a SQL injection vulnerability, as it is passed to the manage_all_info function on lines 452 to 454 of the admin_class.php file in the /classes directory.

update-admin.php
![2](https://github.com/xuanluansec/vul/blob/main/vul/img/6.png)

admin_class.php
![3](https://github.com/xuanluansec/vul/blob/main/vul/img/7.png)
