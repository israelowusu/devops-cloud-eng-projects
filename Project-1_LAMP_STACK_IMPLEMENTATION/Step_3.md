# README.md

## Step 3: Installing MySQL and Securing the Database

In this step, we'll install MySQL on your EC2 instance to manage and store data for your web applications. We will also secure the MySQL installation to ensure it's protected against unauthorized access.

### Overview of MySQL

MySQL is a popular relational database management system used widely in web environments, particularly with PHP applications. It helps in storing, managing, and querying relational data efficiently.

### Instructions

#### 1. Connect to Your EC2 Instance

Ensure you are connected to your EC2 instance via SSH. Use the instructions from Step 1 to connect based on your operating system.

#### 2. Install MySQL

1. **Install MySQL Server**:
   - Update your package list and install MySQL Server using the following command:

     ```bash
     sudo apt install mysql-server
     ```

   - When prompted, confirm the installation by typing `Y` and pressing `ENTER`.

2. **Access the MySQL Console**:
   - Once the installation is complete, log in to the MySQL console as the root user:

     ```bash
     sudo mysql
     ```

   - You should see the MySQL monitor welcome message.

#### 3. Secure MySQL Installation

1. **Set a Password for the Root User**:
   - In the MySQL console, run the following command to set a password for the MySQL root user. We will use `PassWord.1` as an example password:

     ```sql
     ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';
     ```

   - Exit the MySQL console:

     ```sql
     mysql> exit
     ```

2. **Run the MySQL Secure Installation Script**:
   - Start the interactive security script:

     ```bash
     sudo mysql_secure_installation
     ```

   - You will be prompted to configure the `VALIDATE PASSWORD PLUGIN`. This plugin checks the strength of passwords and can enforce password policies. You can choose to enable or disable it based on your preference:

     - **To enable validation**, press `Y` and select a validation level:
       - `0` for LOW (Length >= 8)
       - `1` for MEDIUM (Length >= 8, numeric, mixed case, and special characters)
       - `2` for STRONG (Length >= 8, numeric, mixed case, special characters, and dictionary file)

     - **To disable validation**, press `N`.

   - Set and confirm a password for the MySQL root user when prompted. If you enabled password validation, ensure the password meets the chosen criteria.

   - Continue with the rest of the prompts by pressing `Y` to:
     - Change the root password
     - Remove anonymous users
     - Remove the test database
     - Disallow remote root logins
     - Reload privilege tables to apply changes immediately

3. **Verify MySQL Login**:
   - Test if you can log in to the MySQL console with the new root password:

     ```bash
     sudo mysql -p
     ```

   - Enter the root password when prompted, and then exit the MySQL console:

     ```sql
     mysql> exit
     ```

#### 4. Best Practices

- **Create Dedicated User Accounts**:
  - For increased security, create specific user accounts with limited privileges for your databases. Avoid using the root account for application access.

- **Adjust Authentication Method**:
  - If you're using PHP applications, ensure that MySQL users are configured with `mysql_native_password` instead of `caching_sha2_password` due to compatibility issues.

### Conclusion

You have successfully installed and secured MySQL on your EC2 instance. With MySQL now running, your web server is ready to manage and store data. In the next step, we will install PHP to complete the LAMP stack.