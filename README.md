# Steps for Apigility configuration in Mac OS X

```
cd /etc/apache2/
cp httpd.conf httpd.conf.bak

# /etc/apache2/httpd.conf
# Enable lines
LoadModule rewrite_module libexec/apache2/mod_rewrite.so
LoadModule php5_module libexec/apache2/libphp5.so

# Virtual hosts
Include /private/etc/apache2/extra/httpd-vhosts.conf
```