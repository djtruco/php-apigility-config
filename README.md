# Steps for Apigility configuration in Mac OS X

```
cd /etc/apache2/
cp httpd.conf httpd.conf.bak

# /etc/apache2/httpd.conf
# Enable lines
LoadModule rewrite_module libexec/apache2/mod_rewrite.so
LoadModule php5_module libexec/apache2/libphp5.so
Include /private/etc/apache2/extra/httpd-vhosts.conf

# Copy httpd-vhosts.conf to /etc/apache2/extra/

# Check configuration
sudo apachectl -t

# Add apache group to apigility project (Check config from httpd.conf)
# User _www
# Group _www

sudo apachectl restart
```


# Create project

```
curl -s https://getcomposer.org/installer | php --
php composer.phar create-project -sdev zfcampus/zf-apigility-skeleton path/to/install
```