Mod rewrite allows you to filter what access is allowed before displaying the page, which can overwrite website setups.

It is pretty simple to setup:

1.) sudo apt-get install apache2 //install apache2
2.) sudo a2enmod rewrite //enable modrewrite module
3.) sudo nano /var/www/your_page/.htaccess //create an htaccess file for your page
    RewriteEngine on //make sure its on
    RewriteCond %{HTTP_USER_AGENT} "iphone|ipod|opera mobile" [NC] //if the user is mobile
    RewriteRule ^index.html$ http://your_page/index2.html //push to this page instead
4.) sudo nano /etc/apache2/sites-available/default //add the following to allow htaccess to be used to rewrite
     <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
     </Directory>
5.) sudo service apache2 restart //restart apache2
6.) Visit the page from 2 different locations to verify - mobile or desktop, to see if it bounces correctly!
