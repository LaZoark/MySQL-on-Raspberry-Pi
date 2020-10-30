## Installation
```shell
sudo apt-get -y install mariadb-server 
sudo apt-get -y install php-mysql
sudo apt-get -y install python-mysqldb	(optional)
```

## To install phpMyAdmin
```shell
sudo apt -y install phpmyadmin
cd /etc/apache2
sudo chown pi:root apache2.conf
```

Paste “ Include /etc/phpmyadmin/apache.conf ” at the end of the “apache2.conf”
```shell
sudo nano "/etc/apache2/apache2.conf"
```

then restart the service
```shell
sudo service apache2 restart
```

## To access the CLI(with root member)
```shell
sudo mysql -u root -p
```


## After entering the CLI

To create a `user` at `your IP`(let't take "localhost" for example) and set your `password`(ex. "123456")
```shell
CREATE USER ABC'@'localhost' IDENTIFIED by '123456';
```
You can also make the user available at any IP by setting `%` (任意訪問)
```shell
CREATE USER 'ABC'@'%' IDENTIFIED by '123456';
```
Setting permissions of the database.`ALL PRIVILEGES` can be replaced with `SELECT`, `INSERT`, `DELETE` and other commands.
(the `*.*` below means `whatever database`.`everything`)
```shell
GRANT ALL PRIVILEGES ON *.* TO 'ABC'@'%';
```
Update the permissions table, make changes to the permissions take effect immediately.
```shell
FLUSH PRIVILEGES;
```




### Alternative
In case you have somehow encounter difficulties, woundering how to fix the problem but nothing help...

You might try the secure installation. Hope it would help.
```shell
sudo mysql_secure_installation
```


## Some useful command in CLI

● show user 顯示目前登入使用者
```
MariaDB [ABC]> SELECT USER();
```

● show the version 顯示資料庫版本
```
MariaDB [ABC]> SELECT VERSION();
```

● show all databases 顯示已經建立的資料庫
```
MariaDB [ABC]> SHOW databases;
```

● build a database named "ABC" 建立 ABC 資料庫：
```
MariaDB [(noen)]>CREATE DATABASE ABC;
```

● choose a database 選擇資料庫
```
MariaDB [(none)]> USE ABC;
```

● delete a database called "ABC" 刪除資料庫
```
MariaDB [(none)]> DROP DATABASE ABC;
```

● build a table 建立資料表
```
MariaDB [ABC]> create table customer(name varchar(10), join_date date) DEFAULT CHARSET=utf8;
```

● check out a table 查看資料表
```
MariaDB [ABC]> DESC customer;
```
● delete a table 刪除資料表
```
MariaDB [ABC]> DROP table customer;
```
● clear all the data in a table 清空資料表內資料
```
MariaDB [ABC]> DELETE FROM customer;
```
