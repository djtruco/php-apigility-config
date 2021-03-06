## Create project

```
curl -s https://getcomposer.org/installer | php --
php composer.phar create-project -sdev zfcampus/zf-apigility-skeleton path/to/install
```

## Steps for Apache configuration in Mac OS X

Install php version to run in Apache

```
sudo phpbrew install php-5.5.22 +apxs2
```

```
cd /etc/apache2/
cp httpd.conf httpd.conf.bak
```

Enable lines

```apache
# /etc/apache2/httpd.conf
ServerName localhost
LoadModule rewrite_module libexec/apache2/mod_rewrite.so
# LoadModule php5_module libexec/apache2/libphp5.so
LoadModule php5_module libexec/apache2/libphp5.5.22.so
Include /private/etc/apache2/extra/httpd-vhosts.conf
```

Copy httpd-vhosts.conf to /etc/apache2/extra/


In the Terminal use the id command to see your username and group: `id`.
Change this back in `/etc/apache2/httpd.conf`

```apache
# User _www
# Group _www
User dsaenzt
Group staff
```

Check configuration: `sudo apachectl -t`

Restart: `sudo apachectl restart`

### XDebug config

Copy `phpinfo.php` in `/Library/WebServer/Documents`. Becauseof the 
`httpd-vhosts.conf` which reenables default document root you can check php
config any time through `http://localhost/phpinfo.php`.

```
git clone https://github.com/derickr/xdebug.git
cd xdebug
phpize
./configure --enable-xdebug
make
cp -r modules/  /usr/local/xdebug
```

```
# Check http://localhost/phpinfo.php to find php.ini, then update
zend_extension= /usr/local/xdebug/xdebug.so
```

Restart server: `sudo apachectl restart`

### Gearman config

```
# install job server
brew install gearman

# instal php client
brew install php55-gearman
```

It turns out the homebrew puts everything in `/usr/local/opt/gearman/bin` in
your PATH (`gearman` and `gearman-admin`). But it puts gearmand in
`/usr/local/opt/gearman/sbin`. Homebrew totally misses it.

I solved it by soft-linking to my `/usr/local/bin`.

    ln -s /usr/local/opt/gearman/sbin/gearmand /usr/local/bin

Boom. Now gearmand is in your PATH.

# Timezone

Edit `/etc/php.ini` and enable:

```
date.timezone = "Europe/Madrid"
```

# Notes

Add to your $PATH binaries from packages installed globally with composer and
local folder `vendor/bin` for php projects (check dotfiles).

```
composer.phar self-update
```