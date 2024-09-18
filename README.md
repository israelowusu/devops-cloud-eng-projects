# DevOps/Cloud Engineering Projects

## Project-1: LAMP Stack Setup (Linux, Apache, MySQL, PHP)

This project sets up a LAMP stack on an AWS EC2 instance running Ubuntu Server.

1. **Setup Apache**: Install and configure Apache as the web server. Verify Apache is running and accessible.
   
2. **Configure Security**: Adjust AWS security group settings to allow HTTP traffic on port 80.
   
3. **Install MySQL**: Install MySQL to manage data. Secure the installation with a root password and security script.
   
4. **Install PHP**: Install PHP with necessary modules for Apache. Confirm PHP functionality.
   
5. **Configure Apache Virtual Host**: Set up a directory for your site and configure a virtual host for domain management.
   
6. **Test Web Server**: Create an HTML file to verify the virtual host setup. Access the site using the server’s public IP.

7. **Enable PHP Processing**: Modify Apache to prioritize PHP files and create a PHP info page to test functionality.
   
8. **Secure PHP Info**: Remove the PHP info page after confirming PHP functionality to avoid exposing sensitive server details.

---

## Project-2: LEMP Stack Setup (Linux, Nginx, MySQL, PHP)

This project sets up a LEMP stack on an AWS EC2 instance running Ubuntu Server.

1. **Setup Nginx**: Install and configure Nginx as the web server. Ensure Nginx is running and accessible via the public IP.
   
2. **Configure Security**: Modify AWS security groups to allow HTTP traffic on port 80 for Nginx.
   
3. **Install MySQL**: Install MySQL for data management. Secure it with a root password and user account configuration.
   
4. **Install PHP**: Install PHP with `php-fpm` to work with Nginx and necessary modules for MySQL communication.
   
5. **Configure Nginx Server Block**: Set up a directory structure for your website and create a server block to manage the domain.
   
6. **Test Web Server**: Create an HTML file to verify the server block configuration and test site access.
   
7. **Enable PHP Processing**: Configure Nginx to process PHP files using `php-fpm`. Create a PHP info page to confirm PHP processing.
   
8. **Connect PHP to MySQL**: Create a sample database and PHP script to retrieve data from MySQL and display it on the webpage.

This setup ensures a fully functional LEMP stack, ready for deploying PHP-based web applications.
