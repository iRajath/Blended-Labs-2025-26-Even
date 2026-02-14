# Build Your VPC and Launch a Web Server (AWS) 

## Author


* **Name**: S RAJATH
* **Register Number**: 212224240127
* **Date of Submission**: 14.02.2026


## Objective

The objective of this experiment is to understand how to design and configure a basic network infrastructure in AWS using a Virtual Private Cloud (VPC). This lab focuses on creating a VPC with a public subnet, configuring an Internet Gateway and route table, launching an EC2 instance, and hosting a simple web server that can be accessed over the internet.

---

## Prerequisites

* Basic understanding of cloud computing concepts
* AWS account or AWS Academy Lab access
* Web browser with internet connectivity

---

## Tools Used

* AWS Management Console
* Amazon VPC
* Amazon EC2
* Internet Gateway
* Route Table
* Security Groups

---

## Tasks Performed

### Task 1: Create a VPC

Create a new Virtual Private Cloud (VPC) with a private IP address range. The VPC acts as a logically isolated network in AWS where all other resources will be deployed.

Students should create a VPC with an appropriate CIDR block (for example, 10.0.0.0/16) and assign a meaningful name.


### Task 2: Create a Public Subnet

Create a subnet inside the VPC to host public resources. Enable auto-assign public IPv4 so that instances launched in this subnet receive a public IP address.

The subnet should use a smaller CIDR range (for example, 10.0.1.0/24).


### Task 3: Create and Attach Internet Gateway

Create an Internet Gateway (IGW) and attach it to the VPC. This allows communication between resources in the VPC and the internet.


### Task 4: Configure Route Table

Create a route table and add a default route (0.0.0.0/0) pointing to the Internet Gateway. Associate this route table with the public subnet.

This step ensures that traffic from the subnet can reach the internet.


### Task 5: Create Security Group

Create a security group to act as a virtual firewall for the EC2 instance. Configure inbound rules to allow:

SSH on port 22

HTTP on port 80


### Task 6: Launch EC2 Instance

Launch an EC2 instance inside the public subnet using Amazon Linux 2 AMI and a suitable instance type (t2.micro).

Attach the previously created security group and key pair.


### Task 7: Configure Web Server

Install and start a web server (Apache HTTPD) on the EC2 instance using user data or manual commands.

Create a simple HTML page and verify that it can be accessed from a web browser using the public IP address of the instance.---

## Workflow (Student Explanation)

(Write the steps you followed in your own words)

#### Task 1: Creating a VPC

* I logged in to Amazon Web Services Management Console.

* I searched for VPC in the Services search bar and opened the VPC Dashboard.

* I verified that the region was set to N. Virginia (us-east-1).

* I clicked on Create VPC and selected VPC and more option.

* I kept the IPv4 CIDR block as 10.0.0.0/16.

* I selected:

1 Availability Zone

1 Public Subnet

1 Private Subnet

* I customized subnet CIDR blocks:

Public subnet: 10.0.0.0/24

Private subnet: 10.0.1.0/24

* I selected 1 NAT Gateway in 1 AZ.

* I kept DNS Hostnames and DNS Resolution enabled.

* I clicked Create VPC and waited until all resources were created successfully.

This created:

VPC

Internet Gateway

NAT Gateway

Public and Private Subnets

Route Tables

#### Task 2: Creating Additional Subnets

* In the VPC console, I selected Subnets.

* I created a second public subnet:

Name: lab-subnet-public2

AZ: us-east-1b

CIDR: 10.0.2.0/24

* I created a second private subnet:

Name: lab-subnet-private2

AZ: us-east-1b

CIDR: 10.0.3.0/24

* I went to Route Tables.

* I selected the private route table and associated it with the second private subnet.

* I selected the public route table and associated it with the second public subnet.

Now the VPC had public and private subnets in two Availability Zones.

#### Task 3: Creating a Security Group

In the VPC console, I selected Security Groups.

* I clicked Create Security Group.

* I entered:

Name: Web Security Group

Description: Enable HTTP access

VPC: lab-vpc

* I added an inbound rule:

Type: HTTP

Source: Anywhere (0.0.0.0/0)

* I created the security group.

This security group allows web traffic to the instance.

#### Task 4: Launching an EC2 Web Server

* I searched for and opened Amazon Elastic Compute Cloud (EC2).

* I clicked Launch Instance.

* I entered the instance name as Web Server 1.

* I selected:

Amazon Linux 2023 AMI

Instance type: t2.micro

* I selected the key pair: vockey.

Under Network settings:

VPC: lab-vpc

Subnet: lab-subnet-public2

Auto-assign Public IP: Enabled

* I selected the existing security group: Web Security Group.

* In Advanced details, I added the user data script to install Apache and deploy the web application.

* I launched the instance.

After the instance status showed 2/2 checks passed, I copied the Public IPv4 DNS and opened it in a browser.

* The web page displaying AWS logo and instance details was successfully loaded.

## Output Screenshots (Attach 3)

### Screenshot 1: VPC and Subnet Details
![Cloud Computing Lab - 2](https://github.com/user-attachments/assets/be97fbc7-5579-41d8-ae43-b51ad2023732)

![Cloud Computing Lab - 2](https://github.com/user-attachments/assets/0924d195-6c7f-4a36-9693-b9dca69300b4)

![Cloud Computing Lab - 2](https://github.com/user-attachments/assets/6cc12a0d-3f66-41be-b389-ec5bbf3feb09)


### Screenshot 2: EC2 Instance Running

![Cloud Computing Lab - 2](https://github.com/user-attachments/assets/59e343f4-af93-4590-9cb6-4dccb88dc51f)





### Screenshot 3: Web Server Output in Browser


![Cloud Computing Lab - 2](https://github.com/user-attachments/assets/a43be521-34ce-47c5-9ab9-9eed27e0378f)


## Result 

This experiment successfully demonstrated the creation of a custom VPC and deployment of a public-facing web server in AWS. By configuring networking components such as subnets, route tables, and security groups, and by launching an EC2 instance with a web server, the basic architecture of a cloud-hosted application was understood.
