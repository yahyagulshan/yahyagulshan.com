---
title: "How to setup virtual host on Ubuntu"
date: 2024-02-15T04:06:22Z
author:
authorLink:
description:
tags:
- Ubuntu
- Virtualhost
- Apache
- Nginx
categories:
- Ubuntu
draft: false
hiddenFromHomePage: true
---

# How to Set Up a Virtual Host on Ubuntu 18.04 and 20.04

**Introduction**

In this comprehensive guide, we'll walk you through the process of establishing a virtual host on Ubuntu 18.04 and 20.04, enabling you to host multiple websites on a single server. We'll cover both Apache and Nginx web servers, ensuring you have the flexibility to choose the one that best suits your needs.

**Prerequisites**

* A running Ubuntu 18.04 or 20.04 server

* Administrative privileges (root or sudo access)

* Basic understanding of web servers and virtual hosts

### Step-by-Step Guide (Apache)

### 1. Choose and Install Your Web Server:

* For Apache: `sudo apt install apache2`

* For Nginx: `sudo apt install nginx`

### 2. Create the Website Directory:

`sudo mkdir /var/www/yourdomain.com`

* Replace yourdomain.com with your actual domain name.

### 3. Create the Index File:

* Create an index.html file within the website directory using a text editor (e.g., nano or vim) and add your website content.

### 4. Configure the Virtual Host File:

**Apache:**

`sudo vi /etc/apache2/sites-available/yourdomain.com.conf`

**Nginx:**

`sudo vi /etc/nginx/sites-available/yourdomain.com.conf`

* Paste the appropriate configuration snippet based on your chosen web server:

**Apache:**

    <VirtualHost *:80>
   
   
    ServerName yourdomain.com
    ServerAlias www.yourdomain.com
    ServerAdmin webmaster@yourdomain.com
    DocumentRoot /var/www/yourdomain.com

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    <Directory /var/www/yourdomain.com>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Require all granted
    </Directory>


    </VirtualHost>

![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/7a1e1ec4-0713-424f-b69b-43653119dcdd)

**Nginx:**

    server {
   
    listen 80;
    server_name yourdomain.com www.yourdomain.com;

    root /var/www/yourdomain.com;
    index index.html index.htm;

    access_log /var/log/nginx/yourdomain.com.access.log;
    error_log /var/log/nginx/yourdomain.com.error.log;

    location / {
        try_files $uri $uri/ /index.html;
    }
    
    }


![image](https://github.com/yahyagulshan/yahyagulshan.com/assets/59036269/54f147eb-44bd-4c40-b4d1-242c26f6fe4c)


### 5. Enable the Virtual Host:

**Apache:**

`sudo a2ensite yourdomain.com.conf`

**Nginx:**

`sudo ln -s /etc/nginx/sites-available/yourdomain.com.conf /etc/nginx/sites-enabled/yourdomain.com.conf`

### 6. Test Your Virtual Host:

* Open your web browser and visit http://yourdomain.com or http://localhost (if accessing from the server itself). You should see your website content displayed.

### 7. Set Up SSL (HTTPS)

**Recommended:**

`sudo add-apt-repository ppa:certbot/certbot`

`sudo apt update`

`sudo apt install python3-certbot-apache`

`sudo certbot --apache -d yourdomain.com -d www.yourdomain.com`

**Alternative (Nginx):**

`sudo apt install certbot python3-certbot-nginx`

`sudo certbot --nginx -d yourdomain.com -d www.yourdomain.com`

### 8. Automate SSL Renewal Apache(Optional):

* For automatic renewal every 3 months:

`sudo crontab -e`

* Add the following line:

`0 6 1 */3 * root certbot renew >> /var/log/certbot-renewal.log`


### 9. Automate SSL Renewal Nginx(Optional):

* For check autorenewal in on

`sudo certbot renew --dry-run`
