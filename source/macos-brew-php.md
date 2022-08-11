# How to install php on MacOs with Homebrew

```
brew install php
```
This command install the lasted `php` version, in this case it is `php@8.1`.

If you need old version just type `brew install php@7.4` for example.

After install check `php` version and remember the paths.

```
$ brew info php
-----------------------------------------------------------------
php: stable 8.1.9 (bottled), HEAD
...
/usr/local/Cellar/php/8.1.9 (513 files, 80.2MB)
...
```
You can install several `php` versions and switch between them via `brew`.

```
$ brew unlink php@8.1 && brew link php@7.4 --force
$ php -v
-----------------------------------------------------------------
PHP 7.4.30 (cli) (built: Jun  9 2022 09:31:00) ( NTS )
...
```