# Laravel Project Setup on Ubuntu Server

Step 1 :
````javascript
apt-get update -y
````

Step 2 : Install Apache
````javascript
apt upgrade -y 3 . apt install apache2 -y
````

Step 3 : Install PHP with Its Required Extension
````javascript
apt install php8.2 libapache2-mod-php8.2 php8.2-curl php-pear php8.2-gd php8.2-dev php8.2-zip php8.2-mbstring php8.2-mysql php8.2-xml curl -y
````
> Note : Install PHP Latest Version

Step 4 : Configure php.ini File if Needed
````javascript
vim /etc/php/7.4/apache2/php.ini
````

Step 5 : Start Apache
````javascript
systemctl start apache2
````

Step 6 : Enable Apache
````javascript
systemctl enable apache2
````

Step 7 : Install Composer
````javascript
curl -sS https://getcomposer.org/installer | php mv composer.phar /usr/local/bin/composer chmod +x /usr/local/bin/composer
````

Step 8 : To Check Composer Version
````javascript
composer --version
````

Step 9 : Change Directory
````javascript
cd /var/www/html
````

Step 10 : Create Laravel Project
````javascript
composer create-project laravel/laravel projectname --prefer-dist
````

Step 11 : Change Directory to Laravel Project
````javascript
cd projectname
````

Step 12 : To Check Laravel Framework Version
````javascript
php artisan --v
````

Step 13 :
````javascript
chown -R www-data:www-data /var/www/html/your_project_directory_name
````

Step 14 :
````javascript
chmod -R 775 /var/www/html/your_project_directory_name/storage
````

Step 15 :
````javascript
nano /etc/apache2/sites-available/laravel.conf
````

````javascript
<VirtualHost *:80>
ServerName 43.204.73.0
ServerAdmin admin@example.com
DocumentRoot /var/www/html/your_project_directory_name/public
<Directory /var/www/html/your_project_directory_name>
AllowOverride All
</Directory>
ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
````

Now Press Ctrl+X & then Press Y.

Step 16 :
````javascript
a2ensite laravel.conf
````

Step 17 : Reload Apache
````javascript
systemctl reload apache2
````

Step 18 : Reload Apache
````javascript
a2enmod rewrite
````

Step 19 : Restart Apache
````javascript
systemctl restart apache2
````

> Now we can access the Laravel app by ip address of the server.
