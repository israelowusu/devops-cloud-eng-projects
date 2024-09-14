# README.md

## Step 4: Installing PHP

With Apache and MySQL successfully installed, we now need to install PHP to enable dynamic content processing. PHP will work with Apache and MySQL to deliver dynamic web applications and interact with your MySQL database.

### Overview of PHP

PHP (Hypertext Preprocessor) is a server-side scripting language designed for web development. It allows you to create dynamic web pages and interact with databases like MySQL. PHP scripts are executed on the server, and the results are sent to the client’s web browser.

### Instructions

#### 1. Connect to Your EC2 Instance

Ensure you are connected to your EC2 instance via SSH. Use the instructions from Step 1 if needed.

#### 2. Install PHP and Required Modules

1. **Install PHP and Necessary Packages**:
   - Run the following command to install PHP, the PHP-MySQL module, and the Apache PHP module:

     ```bash
     sudo apt install php libapache2-mod-php php-mysql
     ```

   - This command will install PHP along with `libapache2-mod-php` to enable Apache to handle PHP files and `php-mysql` to allow PHP to communicate with MySQL databases.

2. **Verify PHP Installation**:
   - Once the installation is complete, check the installed PHP version by running:

     ```bash
     php -v
     ```

   - You should see output similar to:

     ```text
     PHP 8.3.6 (cli) (built: Apr 15 2024 19:21:47) (NTS)
     Copyright (c) The PHP Group
     Zend Engine v4.3.6, Copyright (c) Zend Technologies
     with Zend OPcache v8.3.6, Copyright (c), by Zend Technologies
     ```

   - This confirms that PHP is installed and properly configured on your system.

#### 3. Test PHP Setup

1. **Create a PHP Info Page**:
   - To verify that PHP is working with Apache, create a PHP info page. This page will display information about your PHP configuration and environment.

   - Create a new file named `info.php` in the Apache web root directory:

     ```bash
     sudo nano /var/www/html/info.php
     ```

   - Add the following content to the `info.php` file:

     ```php
     <?php
     phpinfo();
     ?>
     ```

   - Save and exit the file by pressing `CTRL + X`, then `Y`, and `ENTER`.

2. **Access the PHP Info Page**:
   - Open a web browser and navigate to the following URL:

     ```text
     http://<Public-IP-Address>/info.php
     ```

   - Replace `<Public-IP-Address>` with the actual public IP address of your EC2 instance.

   - You should see a page displaying detailed information about your PHP configuration. This confirms that PHP is correctly set up and working with Apache.

#### 4. Next Steps

Your LAMP stack is now fully operational with:

- **Linux (Ubuntu)**
- **Apache HTTP Server**
- **MySQL**
- **PHP**

To manage your web server and host multiple websites, you might want to set up Apache Virtual Hosts. Virtual Hosts allow you to serve different websites from the same server, each with its own configuration and document root.

### Conclusion

You have successfully installed and configured PHP on your EC2 instance. Your LAMP stack is now complete and ready for developing and hosting dynamic web applications.
