## Create project

```
curl -s https://getcomposer.org/installer | php --
php composer.phar create-project -sdev zfcampus/zf-apigility-skeleton path/to/install
```

## Steps for Apache configuration in Mac OS X

```
cd /etc/apache2/
cp httpd.conf httpd.conf.bak

Enable lines

```apache
# /etc/apache2/httpd.conf
ServerName localhost
LoadModule rewrite_module libexec/apache2/mod_rewrite.so
LoadModule php5_module libexec/apache2/libphp5.so
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

# XDebug config

```
git clone https://github.com/derickr/xdebug.git
cd xdebug
phpize
./configure --enable-xdebug
make
cp -r modules/  /usr/local/xdebug

# Check http://localhost/phpinfo.php to find php.ini, then update
zend_extension= /usr/local/xdebug/xdebug.so

sudo apachectl restart
```

# Notes

```
composer.phar self-update
```