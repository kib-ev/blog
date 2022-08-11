# How to install myphpadmin on MacOs with Homebrew

To install myphpadmin at first you need to install `php` and `httpd` with homebrew

[How to install php on MasOs with Homebrew][1]

[How to install httpd on MasOs with Homebrew][2]

After installing, you can do next

```
brew install myphpadmin
```

After install check `myphpadmin` version and remember the paths

```
$ brew info myphpadmin
-----------------------------------------------------------------
phpmyadmin: stable 5.2.0 (bottled)
...
/usr/local/Cellar/phpmyadmin/5.2.0 (3,583 files, 44.9MB) *
...
To enable phpMyAdmin in Apache, add the following to httpd.conf and
restart Apache:
    Alias /phpmyadmin /usr/local/share/phpmyadmin
    <Directory /usr/local/share/phpmyadmin/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        <IfModule mod_authz_core.c>
            Require all granted
        </IfModule>
        <IfModule !mod_authz_core.c>
            Order allow,deny
            Allow from all
        </IfModule>
    </Directory>
Then open http://localhost/phpmyadmin
...
```



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
[1]: https://github.com/kib-ev/blog/blob/master/source/macos-brew-php.md
[2]: https://github.com/kib-ev/blog/blob/master/source/macos-brew-httpd.md