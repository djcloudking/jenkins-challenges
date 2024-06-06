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

- For this tutorial, you will create a security group and add the following rules:

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

### Download and install Jenkins



## Configuring Jenkins

## Clean up tutorial resources.









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