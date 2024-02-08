---
title: "Nginx Proxy"
date: 2024-02-08T04:06:22Z
author:
authorLink:
description:
tags:
- Nginx
- Proxy
- 
- 
categories:
- 
draft: false
hiddenFromHomePage: true
---

## for nginx Proxy add below lines in nginx configuration file

original file without proxy

server {
        listen 80;

        root /var/www/html;
        index index.html index.htm index.nginx-debian.html index.php;

        server_name abc.com www.abc.com;

        location / {
                try_files $uri $uri/ =404;
        }

        error_log /var/log/nginx/abc.com.error;
        access_log /var/log/nginx/abc.com.access;

}

proxy add file 

server {
        listen 80;

        root /var/www/html;
        index index.html index.htm index.nginx-debian.html index.php;

        server_name abc.com www.abc.com;

        location / {
                try_files $uri $uri/ =404;
        }
        
        # add proxy

        location / {
                proxy_pass https://www.xyz.com/;
        }

        error_log /var/log/nginx/abc.com.error;
        access_log /var/log/nginx/abc.com.access;

}

* after change the file check nginx 

`nginx -t`

* if test is successfull then reload nginx

`/etc/init.d/nginx reload`
