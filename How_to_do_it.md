# MySQL on Raspberry Pi
This is a simple guide to establish your own database with MySQL (I would recommend using MariaDB instead).

MariaDB intended to maintain high compatibility with MySQL, ensuring a drop-in replacement capability with library binary parity and exact matching with MySQL APIs and commands.
However, new features diverge more. It includes new storage engines like Aria, ColumnStore, and MyRocks.

## Installation:
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
