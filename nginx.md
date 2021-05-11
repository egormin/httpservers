### Snippets in nginx
```
/etc/nginx/sites-available/default

server {
        listen 81 default_server;
        listen [::]:81 default_server;

        root /var/www/;

        # Add index.php to the list if you are using PHP
        index index.php index.html index.htm index.nginx-debian.html;

        server_name _;
        include snippets/application.conf;
        include snippets/fastcgi-php.conf;
        location / {
                # First attempt to serve request as file, then
                # as directory, then fall back to displaying a 404.
                try_files $uri $uri/ =404;
                #try_files $uri index.php;
        }
}

snippets/application.conf;

location /application {
    root /var/www/;
    index index.php index.html index.htm;
    location ~ ^/application/(.+\.php)$ {
        try_files $uri =404;
        root /var/www/;
        fastcgi_pass unix:/run/php/php7.2-fpm.sock;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include /etc/nginx/fastcgi_params;
    }

    location ~* ^/application/(.+\.(jpg|jpeg|gif|css|png|js|ico|html|xml|txt))$ {
        root /var/www/;
    }
}


snippets//phpmyadmin.conf;

location /phpmyadmin {
    root /var/www/;
    index index.php index.html index.htm;
    location ~ ^/phpmyadmin/(.+\.php)$ {
        try_files $uri =404;
        root /var/www/;
        fastcgi_pass unix:/run/php/php7.2-fpm.sock;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include /etc/nginx/fastcgi_params;
    }

    location ~* ^/phpmyadmin/(.+\.(jpg|jpeg|gif|css|png|js|ico|html|xml|txt))$ {
        root /var/www/;
    }
}
```
