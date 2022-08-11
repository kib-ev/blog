# How to install myphpadmin (httpd) on MacOs with Homebrew

To install myphpadmin at first you need to install `php` and `httpd` with homebrew

How to install php on MasOs with Homebrew
How to install httpd on MasOs with Homebrew

```
brew install httpd
```

After install check mysql version and remember the paths

```
$ brew info httpd
-----------------------------------------------------------------
httpd: stable 2.4.54 (bottled)
...
/usr/local/Cellar/httpd/2.4.54 (1,662 files, 31.8MB) *
...
DocumentRoot is /usr/local/var/www.
...
The default ports have been set in /usr/local/etc/httpd/httpd.conf to 8080
...
```

Сonfig file is located `/usr/local/etc/httpd/httpd.conf`

To start server

```
$ brew services start httpd
-----------------------------------------------------------------
==> Successfully started `httpd` (label: homebrew.mxcl.httpd)
```

Now we can type 

```
$ mysql -v
-----------------------------------------------------------------
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
```

I get error message. To solve do the following

```
$ brew services stop mysql
$ sudo pkill mysqld
$ brew postinstall mysql
$ brew services start mysql
$ mysql -uroot
-----------------------------------------------------------------
mysql>
```

Set new password for root

```
mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY 'secret';
-----------------------------------------------------------------
Query OK, 0 rows affected (0.12 sec)
```

After setting the password to open mysql cli, need to type

```
$ mysql -u root -p
-----------------------------------------------------------------
Enter password: 
Welcome to the MySQL monitor. ...
```

To exit mysql cli type

```
mysql> exit;
-----------------------------------------------------------------
Bye
```
[1]<>