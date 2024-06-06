# Installing Jenkins on AWS EC2

In this tutorial, you will perform the following steps:

## Prerequisites

You should have access to an AWS account. 


## Create a key pair using Amazon EC2. 

- If you already have one, you can skip to step 3.

- Follow the prompt to create your keypair. 

- For File format, select the format in which to save the private key: 

    - For OpenSSH compatibility, select pem.

    - For PuTTY compatibility, select ppk.


## Create a security group for your Amazon EC2 instance. 

- If you already have one, you can skip to step 4.

- Create a security group and add the following rules:

    - Allow inbound HTTP access from anywhere.

    - Allow inbound SSH traffic from your computer’s public IP address so you can connect to your instance.

- On the Inbound tab, add the rules as follows:

    - Select Add Rule, and then select SSH from the Type list.

    - Under Source, select Custom, and in the text box, enter the IP address, followed by /32 indicating a single IP Address. 

    - Select Add Rule, and then select HTTP from the Type list.

    - Select Add Rule, and then select Custom TCP Rule from the Type list.

    - Under Port Range, enter 8080.


## Launch an Amazon EC2 instance

- You have your key pair and your security group, launch your EC2 instance. 


## Connecting to EC2 instances

After creating EC2, it s time to connect to it. 


## Install and configure Jenkins

- Downloading and installing Jenkins

- Ensure that your software packages are up to date on your instance by using the following command to perform a quick software update:

[ec2-user ~]$ sudo yum update –y

- Add the Jenkins repo using the following command:

[ec2-user ~]$ sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo

- Import a key file from Jenkins-CI to enable installation from the package:

[ec2-user ~]$ sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
[ec2-user ~]$ sudo yum upgrade

- Install Java (Amazon Linux 2023):

[ec2-user ~]$ sudo dnf install java-17-amazon-corretto -y

- Install Jenkins:

[ec2-user ~]$ sudo yum install jenkins -y

- Enable the Jenkins service to start at boot:

[ec2-user ~]$ sudo systemctl enable jenkins

- Start Jenkins as a service:

[ec2-user ~]$ sudo systemctl start jenkins

- You can check the status of the Jenkins service using the command:

[ec2-user ~]$ sudo systemctl status jenkins


## Configuring Jenkins

Jenkins is now installed and running on your EC2 instance. To configure Jenkins:

- Connect to http://<your_server_public_DNS>:8080 from your browser. You will be able to access Jenkins through its management interface.

- As prompted, enter the password found in /var/lib/jenkins/secrets/initialAdminPassword.

- Use the following command to display this password:

[ec2-user ~]$ sudo cat /var/lib/jenkins/secrets/initialAdminPassword

- The Jenkins installation script directs you to the Customize Jenkins page. Click Install suggested plugins.

- Once the installation is complete, the Create First Admin User will open. Enter your information, and then select Save and Continue.

- Create your first admin user.

- On the left-hand side, select Manage Jenkins, and then select Manage Plugins.

- Select the Available tab, and then enter Amazon EC2 plugin at the top right.

- Select the checkbox next to Amazon EC2 plugin, and then select Install without restart.

- Jenkins Plugin Manager showing available plugins. Once the installation is done, select Back to Dashboard.

- Select Configure a cloud if there are no existing nodes or clouds.

- Jenkins Dashboard showing configure a cloud. If you already have other nodes or clouds set up, select Manage Jenkins.

- After navigating to Manage Jenkins, select Configure Nodes and Clouds from the left hand side of the page.

-   Select Add a new cloud, and select Amazon EC2. A collection of new fields appears.

- Click Add under Amazon EC2 Credentials

- From the Jenkins Credentials Provider, select AWS Credentials as the Kind.

- Scroll down and enter in the IAM User programmatic access keys with permissions to launch EC2 instances and select Add.

- Scroll down to select your region using the drop-down, and select Add for the EC2 Key Pair’s Private Key.

- From the Jenkins Credentials Provider, select SSH Username with private key as the Kind and set the Username to ec2-user.

- Scroll down and select Enter Directly under Private Key, then select Add.

- Set Private Key to Enter Directly. Open the private key pair you created in the creating a key pair step and paste in the contents from "-----BEGIN RSA PRIVATE KEY-----" to "-----END RSA PRIVATE KEY-----". Select Add when completed.

- Enter Private Key.

- Scroll down to "Test Connection" and ensure it states "Success". Select Save when done

- Test Connection. You are now ready to use EC2 instances as Jenkins agents.














## Create EC2

Click on the following link to see how to create an EC2 instance. 

In this tutorial, you will perform the following steps: 
Prerequisites. 

Create a key pair using Amazon EC2. If you already have one, you can skip to step 

3. Create a security group for your Amazon EC2 instance. If you already have one, you can skip to step 

4. Launch an Amazon EC2 instance. 

Install and configure Jenkins. 

Clean up tutorial resources.

## 