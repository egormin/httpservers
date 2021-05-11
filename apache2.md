### Task 1
Go to the link http://linappma, showld open phpmyadmin from /var/www/phpmyadmin

```
/etc/apache2/sites-available/linappma

<VirtualHost *:80>
        ServerAdmin webmaster@linappma
        ServerName linappma
        ServerAlias linappma
        DocumentRoot /var/www/phpmyadmin
        
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

### Task 2
Go to the link http://linaproot, showld open phpmyadmin from /var/www/

```
/etc/apache2/sites-available/linaproot

<VirtualHost *:80>
        ServerAdmin webmaster@linaproot
        ServerName linaproot
        ServerAlias linaproot
        DocumentRoot /var/www/

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

### Task 3
Make apache to use .htaccess files
```
<Directory /var/www/>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
</Directory>
```
