# README.md

## Project-1_LAMP_STACK_IMPLEMENTATION Summary

This project sets up a LAMP stack (Linux, Apache, MySQL, PHP) on an AWS EC2 instance running Ubuntu Server. 

1. **Setup Apache**: Begin by installing Apache, which will serve as the web server. Ensure Apache is running and verify its status.

2. **Configure Security**: Adjust the AWS security group settings to allow incoming traffic on port 80, which is necessary for HTTP communication.

3. **Install MySQL**: Install MySQL to manage and store your data. Run the included security script to set up a root password and secure the installation.

4. **Install PHP**: Install PHP along with the necessary modules to enable PHP support in Apache. Confirm that PHP is working by checking its version.

5. **Configure Apache Virtual Host**: Create a new directory for your site and set up a virtual host configuration file to manage your domain or project directory. Enable this new site configuration and disable the default Apache site.

6. **Test Web Server**: Create a basic HTML file to verify that the virtual host is correctly serving content. Access your site via the public IP address to check its functionality.

7. **Enable PHP Processing**: Modify Apache’s configuration to prioritize PHP files over HTML files. Create a PHP info page to confirm that PHP is properly processing requests.

8. **Secure PHP Info**: Remove the PHP info page once you’ve confirmed that PHP is operational, as it can expose sensitive server information.

This setup ensures that you have a fully functional LAMP stack ready for developing and hosting web applications.