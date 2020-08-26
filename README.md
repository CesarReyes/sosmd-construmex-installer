# Constructex web site installer

This installs a clean Wordpress version.

* Homepage: <http://localhost:8000>  
* WP admin side go to: <http://localhost:8000/wp-admin>  
* User/Pwd: admin/secret  

## Requirements

* MacOs or Linux
* Docker 2.x+

## To install

Just run the `install.sh` file  

```bash
./install.sh
```

## After install  

To suppport upload large files update the file `wordpress/.htaccess` replace with the below content and reload the Docker container `sosmd-constructex_wordpress_1` using the Docker dashboard:

```bash
# BEGIN WordPress
php_value upload_max_filesize 400M
php_value post_max_size 400M
php_value memory_limit 256M
php_value max_execution_time 300
php_value max_input_time 300

<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
</IfModule>
# END WordPress
```
