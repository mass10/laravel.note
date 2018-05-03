# Apache をインストール

##### Ubuntu

```
$ sudo apt-get install apache2
$ sudo a2enmod rewrite
$ sudo service apache2 restart
```


# Composer を設置

composer を任意のディレクトリにダウンロードして

```
$ wget https://getcomposer.org/installer
```

実行

```
$ php installer
$ mv composer.phar composer
$ mv composer /usr/local/bin/
```

# Laravel をインストールする

※Do not run Composer as root/super user! See https://getcomposer.org/root for details

```
$ composer global require "laravel/installer"
```

composer global require "laravel/installer=~1.1"


# スケルトンを作成

```
$ PATH=$PATH:~/.config/composer/vendor/bin/
$ laravel new myapp1
$ laravel new myapp1 5.0
```


# アプリケーションを配置する

##### HTTPS を有効にする

(Ubuntu)

```
$ sudo a2enmod ssl
$ sudo a2ensite default-ssl
$ sudo service apache2 restart
```

##### パーミッションについて

```
# chown -R www-data:www-data storage
# chown -R www-data:www-data bootstrap/cache
```


# running internal server

```
php artisan serve --port=8080
```



# Problem - laravel/installer v2.0.1 requires ext-zip * -> the requested PHP extension zip is missing from your system.

composer global require "laravel/installer" が失敗した場合。

```
sudo apt install php7.0-zip
```

# Problem - PHP Warning:  require(......./autoload.php): failed to open stream: No such file or directory

```
USERNAME@ubuntu:~/workspace/laravel.note/code/example1$ php artisan serve --port=8080
PHP Warning:  require(/home/USERNAME/workspace/laravel.note/code/example1/vendor/autoload.php): failed to open stream: No such file or directory in /home/USERNAME/workspace/laravel.note/code/example1/artisan on line 18
PHP Fatal error:  require(): Failed opening required '/home/USERNAME/workspace/laravel.note/code/example1/vendor/autoload.php' (include_path='.:/usr/share/php') in /home/USERNAME/workspace/laravel.note/code/example1/artisan on line 18
```
