title: "Updating SSL Certificate on Apache Server "
date: 2024-02-22T04:06:22Z
author:
authorLink:
description:
tags:
- Go-daddy
- SSL
- Apache
- Ubuntu
categories:
- 
draft: false
hiddenFromHomePage: true
---
# Introduction 

* Ensuring the security of your website is crucial, and one aspect of this is maintaining up-to-date SSL certificates. 

* In this guide, we'll walk through the process of updating SSL certificates on an Apache server hosted on Ubuntu.

### Prerequisites 📝

**Before we begin, make sure you have the following:**

* Access to the Ubuntu server with Apache installed.

* The new SSL certificate files ready for deployment.

* The necessary permissions to restart the Apache service.

### Steps to Update SSL Certificates ⚒️ 🔩

**1- Copy Cert Files to Server** 🐾

* Use the scp command to securely copy the SSL certificate files to your Ubuntu server. 

* Replace testing.pem with the path to your private key, /home/abc/ssl/file.zip with the path to your certificate files, and 11.11.11.11 with your server's IP address.

      scp -i testing.pem /home/abc//ssl/file.zip ubuntu@11.11.11.11:/tmp/

**2- Backup Existing Certificates** 📼 💼

* Before making any changes, it's essential to create backups of your existing SSL certificates. 

*Rename the old certificates with the following commands:*

    mv /etc/apache2/ssl/_.abc.crt /etc/apache2/ssl/_.abc.crt-bk

    mv /etc/apache2/ssl/gd_abc.crt /etc/apache2/ssl/gd_abc.crt-bk

    mv /etc/apache2/ssl/_.abc.key /etc/apache2/ssl/_.abc.key-bk

**3- Unzip Certificate Files**  📜

* Navigate to the directory where you uploaded the ZIP file and unzip its contents.

      unzip /tmp/file.zip -d /tmp/

**4- Copy and Rename New Certificates** 📝

* Copy the new certificate files to the /etc/apache2/ssl.crt/ folder and rename them according to the previous naming convention.

      cp /tmp/sdfjkdj3jslsl.crt /etc/apache2/ssl.crt/_.abc.crt

      cp /tmp/gd_bundle-dejfjsl.crt /etc/apache2/ssl.crt/gd_abc.crt

**5- Update Private Key** 🏹

* Copy the new private key to the appropriate location and rename it.

      cp /tmp/skdfjsdfksss.key /etc/apache2/ssl/_.abc.key


**6- Reload Apache** 🔃

* Reload the Apache service to apply the changes.

      /etc/init.d/apache2 reload

### Conclusion 📔

* By following these steps, you've successfully updated the SSL certificates on your Apache server. 

* Regularly updating SSL certificates helps maintain the security and trustworthiness of your website. 

* Ensure to perform these updates as needed, especially when certificates are close to expiration. 

* If you encounter any issues during this process, refer to your server and certificate provider's documentation for additional support.      
