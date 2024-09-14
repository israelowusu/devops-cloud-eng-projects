## Step 1: Setting Up Your AWS EC2 Instance with Ubuntu Server

In this step, you'll create and connect to your first EC2 instance on AWS using the free tier. Follow the instructions below to set up an Ubuntu Server and connect to it securely.

### Prerequisites

1. **AWS Account**: Ensure you have an AWS account. If not, [register for a new AWS account](https://aws.amazon.com/).
2. **Virtual Server with Ubuntu**: We will use AWS EC2 to provision a virtual server running Ubuntu Server OS.

### Instructions

#### 1. Register a New AWS Account

- Follow the [AWS account setup instructions](https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/) to create your AWS account.

#### 2. Launch a New EC2 Instance

1. **Sign in to AWS Management Console**:
   - Go to the [AWS Management Console](https://aws.amazon.com/console/).
   
2. **Select EC2 Service**:
   - In the AWS Management Console, find and select "EC2" from the list of services.

3. **Launch a New Instance**:
   - Click on "Launch Instance" to start the process of creating a new EC2 instance.

4. **Choose an Amazon Machine Image (AMI)**:
   - Select "Ubuntu Server 24.04 LTS (HVM)" from the list of available AMIs.

5. **Choose an Instance Type**:
   - Select the "t2.micro" instance type, which is eligible for the free tier.

6. **Configure Instance Details**:
   - Leave the default settings as they are. Ensure the "Auto-assign Public IP" option is enabled for easy access.

7. **Add Storage**:
   - The default storage configuration is typically sufficient for basic use. You can adjust if needed.

8. **Add Tags** (Optional):
   - You may add tags to organize and manage your instances, such as "Name: MyFirstInstance".

9. **Configure Security Group**:
   - Create a new security group or select an existing one. Ensure that port 22 (SSH) is open to your IP address for secure access.

10. **Review and Launch**:
    - Review your settings and click "Launch". You will be prompted to create or select an existing key pair.

11. **Create Key Pair**:
    - Create a new key pair, download the `.pem` file, and save it securely. This key is essential for accessing your instance.

#### 3. Connect to Your EC2 Instance

The connection process varies slightly depending on your operating system. Follow the appropriate instructions below based on your OS.

##### Windows

1. **Install PuTTY**:
   - If you don't have PuTTY installed, download and install it from the [official website](https://www.putty.org/).

2. **Convert PEM to PPK (if necessary)**:
   - Use PuTTYgen to convert the `.pem` file to `.ppk` format if you're using PuTTY. Open PuTTYgen, load your `.pem` file, and save the new `.ppk` file.

3. **Open PuTTY and Configure Connection**:
   - Open PuTTY and enter the public IP address of your EC2 instance in the "Host Name (or IP address)" field.
   - In the "Connection > SSH > Auth" section, browse and select the `.ppk` file you created earlier.

4. **Connect**:
   - Click "Open" to initiate the connection. When prompted, log in using the username `ubuntu`.

##### Mac

1. **Open Terminal**:
   - Terminal is pre-installed on macOS. Open it from the Applications > Utilities folder.

2. **Change Directory to PEM File Location**:
   - Navigate to the directory where your `.pem` file is located, typically the Downloads folder:
     ```bash
     cd ~/Downloads
     ```

3. **Change File Permissions**:
   - Run the following command to ensure proper permissions for the `.pem` file:
     ```bash
     chmod 0400 <private-key-name>.pem
     ```

4. **Connect to the Instance**:
   - Use the SSH command to connect to your EC2 instance:
     ```bash
     ssh -i <private-key-name>.pem ubuntu@<Public-IP-address>
     ```
   - Replace `<private-key-name>.pem` with the name of your downloaded key file and `<Public-IP-address>` with the public IP of your EC2 instance.

### Important Notes

- **Save Your Private Key**: Store your `.pem` file securely. Losing it means you won't be able to access your instance.
- **Monitoring**: Regularly monitor your instance's resource usage and security.
- **Security**: Keep your instance's security up to date and secure.

Congratulations! You have successfully set up and connected to your first Linux server in the cloud. In the next steps, we will configure this EC2 instance to serve a web server.
