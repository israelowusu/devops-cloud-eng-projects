## Step 2: Installing Apache and Updating the Firewall

In this step, we will install the Apache HTTP Server on your EC2 instance and configure the firewall to allow web traffic. Apache is a widely used web server software that will enable you to host web pages on your server.

### Overview of Apache

Apache HTTP Server, commonly referred to as Apache, is a free, open-source web server software developed by the Apache Software Foundation. It is one of the most popular web servers globally, known for its speed, reliability, and security. Apache can be customized with various extensions and modules to meet different needs.

### Instructions

#### 1. Connect to Your EC2 Instance

Before proceeding with the installation, make sure you are connected to your EC2 instance via SSH. Use the instructions from Step 1 to connect to your instance based on your operating system.

#### 2. Update the Package List

Update the list of available packages to ensure you get the latest version of Apache:

```bash
sudo apt update
```

#### 3. Install Apache

Run the following command to install Apache:

```bash
sudo apt install apache2
```

#### 4. Verify Apache is Running

Check the status of the Apache service to ensure it is running:

```bash
sudo systemctl status apache2
```

- **If the status is green and shows `active (running)`,** Apache is successfully installed and running.

#### 5. Configure the Firewall

To allow web traffic through port 80 (the default port for HTTP), you need to update the security group settings in AWS:

1. **Go to the EC2 Management Console**:
   - Navigate to the [EC2 Dashboard](https://console.aws.amazon.com/ec2/).

2. **Select Security Groups**:
   - Find the security group associated with your EC2 instance.

3. **Edit Inbound Rules**:
   - Add a new rule:
     - Type: `HTTP`
     - Protocol: `TCP`
     - Port Range: `80`
     - Source: `0.0.0.0/0` (Allows traffic from any IP address)

4. **Save Rules**:
   - Apply the changes to the security group.

#### 6. Test Apache Locally

To ensure Apache is responding correctly on your EC2 instance, run the following commands in the Ubuntu shell:

```bash
curl http://localhost:80
```

or

```bash
curl http://127.0.0.1:80
```

- **Expected Output**: You should see a test page or some formatted text, indicating that Apache is responding correctly to local requests.

#### 7. Test Apache from the Internet

To verify that your Apache server is accessible from the internet:

1. **Retrieve Your Public IP Address**:
   - You can find your public IP address in the AWS Management Console or use the following command:

     ```bash
     TOKEN=`curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600"` && curl -H "X-aws-ec2-metadata-token: $TOKEN" -s http://169.254.169.254/latest/meta-data/public-ipv4
     ```

2. **Open a Web Browser**:
   - Enter the following URL in your web browser:

     ```text
     http://<Public-IP-Address>:80
     ```

   - You should see the same content that you viewed with the `curl` command, formatted as an HTML page.

### Conclusion

You have successfully installed Apache on your EC2 instance, configured the firewall to allow web traffic, and tested Apache's functionality both locally and from the internet. You are now ready to proceed with the next steps in your project.
