# README.md

## Step 5: Creating a Virtual Host for Your Website using Apache

Now that you have your LAMP stack up and running, you can set up a Virtual Host in Apache to manage your website. This setup will enable you to serve your website from a specific directory and configure Apache to handle multiple sites on the same server.

### Overview

A Virtual Host is a configuration in Apache that allows you to run multiple websites on a single server. Each Virtual Host can be associated with a different domain name or IP address.

In this step, we’ll create a Virtual Host for a domain called `projectlamp`. You can replace this with any domain name of your choice. The following instructions will guide you through the setup process.

### Instructions

#### 1. Create the Directory for Your Website

1. **Create a Directory**:
   - Run the following command to create a new directory for your website:

     ```bash
     sudo mkdir /var/www/projectlamp
     ```

2. **Set Directory Ownership**:
   - Assign ownership of this directory to your current user:

     ```bash
     sudo chown -R $USER:$USER /var/www/projectlamp
     ```

#### 2. Create and Configure the Virtual Host File

1. **Create a New Virtual Host File**:
   - Open a new configuration file for your Virtual Host in Apache’s `sites-available` directory:

     ```bash
     sudo vi /etc/apache2/sites-available/projectlamp.conf
     ```

2. **Add Configuration**:
   - Enter the following configuration into the file. Press `i` to enter insert mode, then paste the configuration:

     ```apache
     <VirtualHost *:80>
         ServerName projectlamp
         ServerAlias www.projectlamp
         ServerAdmin webmaster@localhost
         DocumentRoot /var/www/projectlamp
         ErrorLog ${APACHE_LOG_DIR}/error.log
         CustomLog ${APACHE_LOG_DIR}/access.log combined
     </VirtualHost>
     ```

3. **Save and Exit**:
   - To save the file and exit, follow these steps:
     1. Press `ESC` to leave insert mode.
     2. Type `:wq` and press `ENTER`.

4. **Verify the New Virtual Host File**:
   - Check that the new file is in the `sites-available` directory:

     ```bash
     sudo ls /etc/apache2/sites-available
     ```

   - You should see `projectlamp.conf` listed among other configuration files.

#### 3. Enable the Virtual Host

1. **Enable the New Virtual Host**:
   - Use the `a2ensite` command to enable your new Virtual Host:

     ```bash
     sudo a2ensite projectlamp
     ```

2. **Disable the Default Site** (if necessary):
   - If you’re not using a custom domain name, you should disable the default site configuration to prevent conflicts:

     ```bash
     sudo a2dissite 000-default
     ```

3. **Check for Syntax Errors**:
   - Verify that your configuration file does not contain syntax errors:

     ```bash
     sudo apache2ctl configtest
     ```

   - Ensure that the output shows `Syntax OK`.

4. **Reload Apache**:
   - Apply the new configuration by reloading Apache:

     ```bash
     sudo systemctl reload apache2
     ```

#### 4. Create a Test Page

1. **Create an Index Page**:
   - Add a test `index.html` file to your website’s root directory:

     ```bash
     sudo echo 'Hello LAMP from hostname' $(TOKEN=`curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600"` && curl -H "X-aws-ec2-metadata-token: $TOKEN" -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(TOKEN=`curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600"` && curl -H "X-aws-ec2-metadata-token: $TOKEN" -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html
     ```

2. **Test the Virtual Host**:
   - Open your web browser and visit:

     ```text
     http://<Public-IP-Address>:80
     ```

   - Replace `<Public-IP-Address>` with your EC2 instance’s public IP address.

   - You should see the text you added to the `index.html` file, indicating that the Virtual Host is functioning correctly.

3. **Test Using Public DNS Name** (Optional):
   - You can also access your website using the public DNS name:

     ```text
     http://<Public-DNS-Name>:80
     ```

   - Replace `<Public-DNS-Name>` with your EC2 instance’s public DNS name.

#### 5. Next Steps

- **Temporary Landing Page**:
  - The `index.html` file you created serves as a temporary landing page. When you’re ready to deploy your application, replace or remove this file.

- **PHP Setup**:
  - If you plan to use PHP for dynamic content, remember that `index.php` will take precedence over `index.html`. Place your PHP files in the `/var/www/projectlamp` directory as needed.

### Conclusion

You have successfully created and configured a Virtual Host in Apache for your website. This setup allows you to manage multiple websites on the same server and serves as a foundation for deploying and hosting your web applications. 

If you encounter any issues or have further questions, don't hesitate to seek support or consult Apache documentation. 