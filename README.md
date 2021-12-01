# Niginx

touch /etc/nginx/sites-available/your-domain or dir

sudo nano /etc/nginx/sites-available/your-domain

```

   server {
	    listen 80;
	    listen [::]:80;

        root /var/www/blog/public;  # blog folder url

        # Add index.php to the list if you are using PHP
        index index.php index.html;

        server_name blog.test;  # server name



        location / {
            # First attempt to serve request as file, then
            # as directory, then fall back to displaying a 404.
            try_files $uri $uri/ /index.php?$query_string;

            # for directory listing
            autoindex on;

        }

        # pass PHP scripts to FastCGI server
        #
        location ~ \.php$ {
            include snippets/fastcgi-php.conf;
        #
        #	# With php-fpm (or other unix sockets):
            fastcgi_pass unix:/var/run/php/php7.2-fpm.sock;
        #	# With php-cgi (or other tcp sockets):
        #	fastcgi_pass 127.0.0.1:9000;
        }

        # deny access to .htaccess files, if Apache's document root
        # concurs with nginx's one
        #
        #location ~ /\.ht {
        #	deny all;
        #}
    }

```


```
sudo ln -s /etc/nginx/sites-available/your-domain /etc/nginx/sites-enabled/your-domain
```

```
sudo nginx -t
```

```
  1. sudo nano /etc/hosts
  2. paste "127.0.1.1       blog.test"

```



