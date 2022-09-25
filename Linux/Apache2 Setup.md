## Apache, MySQL and PHP Installation
From: [Digital Ocean](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-20-04)

__Install Apache2:__
```shell
sudo apt update
sudo apt install apache2
```
__Install MySQL:__
```shell
sudo apt install mysql-server
sudo mysql_secure_installation
sudo mysql
```
__Install PHP:__
```shell
sudo apt install php libapache2-mod-php php-mysql
php -v
sudo nano /etc/apache2/mods-enabled/dir.conf
#add index.php in the file
sudo systemctl restart apache2
```
## Virtual Host Examples
__Setting up Apache Virtual Hosts:__
```shell
sudo mkdir /var/www/your_domain
sudo chown -R www-data:www-data /var/www/your_domain
sudo chmod -R 755 /var/www/your_domain
sudo nano /etc/apache2/sites-available/your_domain.conf
```
- __For sites hosted on this webserver:__
```text
<VirtualHost *:80>
 ServerAdmin webmaster@localhost
 ServerName your_domain
 ServerAlias your_domain
 DocumentRoot /var/www/your_domain
 ErrorLog ${APACHE_LOG_DIR}/error.log
 CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
- __For sites hosted elsewhere (redirection):__
```text
<VirtualHost *:80>
 ServerName www.domain1.com
 Redirect / http://www.domain2.com
</VirtualHost>
```
__Then validate the config and enable it:__
```shell
sudo a2ensite your_domain.conf
sudo a2dissite 000-default.conf
sudo apache2ctl configtest
sudo systemctl restart apache2
```
## Certbot Installation and Configuration
__Install certbot and its Apache support:__
```shell
sudo apt install certbot
sudo apt install python-certbot-apache
```
__Use Certbot to request a certificate:__
```shell
sudo certbot --apache -d your_domain -d www.your_domain
```
## Server Hardening
- __Set the ServerTokens directive to Prod:__
```shell
sudo nano /etc/apache2/conf-available/security.conf
#Search for the ServerTokens directive, and change it to Prod as follow:
ServerTokens Prod
```
- __Set the ServerSignature directive to Off:__
```shell
sudo nano /etc/apache2/conf-available/security.conf
#Search for the ServerSignature directive, and change it to Off as follow:
ServerSignature Off
```
__After all changes, restart Apache2:__
```shell
sudo systemctl restart apache2
```
Also consider checking the headers with [securityheaders.com](https://securityheaders.com).
