# How

```
brew install mysql
```

After install check mysql version

```
$ brew info mysql
-----------------------------------------------------------------
mysql: stable 8.0.30 (bottled)
...
/usr/local/Cellar/mysql/8.0.30 (312 files, 297MB) *
...
```
To start server
```
$ cd /usr/local/Cellar/mysql/8.0.30/bin
$ sudo mysql.server start
or
$ brew services start mysql
-----------------------------------------------------------------
Starting MySQL
 SUCCESS! 
```
Create new alias for `mysql`
```
$ nano ~/.bash_profile
```
Add new row
```
alias mysql=/usr/local/Cellar/mysql/8.0.30/bin/mysql
```
To save and exit from nano press `Ctrl+X` `Y` `Enter`

```
$ source ~/.bash_profile
```
Now we can type 

```
$ mysql -v
-----------------------------------------------------------------
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
```
I get error message. For resolve make next
```
$ brew services stop mysql
$ sudo pkill mysqld
$ brew postinstall mysql
$ brew services start mysql
$ mysql -uroot
-----------------------------------------------------------------
mysql>
```
Now set new password
```
mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY 'secret';
-----------------------------------------------------------------
Query OK, 0 rows affected (0.12 sec)
```
To exit mysql type
```
mysql> exit;
-----------------------------------------------------------------
Bye
```