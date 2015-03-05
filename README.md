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