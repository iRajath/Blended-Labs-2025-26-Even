# Lab 5 – Build a Database Server (AWS)

## Author

* **Name**: S Rajath
* **Register Number**: 212224240127
* **Date of Submission**: 13-03-2026

---

## Objective

The objective of this experiment is to understand how to deploy and configure a database server in AWS. This lab focuses on launching an EC2 instance, installing a database management system (DBMS), configuring basic database settings, creating a sample database, and validating connectivity to the database server.

---

## Prerequisites

* Basic understanding of cloud computing concepts
* AWS account or AWS Academy Lab access
* An existing VPC and EC2 knowledge (from previous labs)
* Basic knowledge of Linux commands and SQL

---

## Tools Used

* AWS Management Console
* Amazon EC2
* Security Groups
* SSH Client (Terminal / PuTTY)
* MySQL / MariaDB / PostgreSQL (any one)

---

## Tasks Performed

### Task 1: Launch EC2 Instance for Database Server

Launch a new EC2 instance using Amazon Linux 2 AMI. Select an appropriate instance type and configure key pair and security group.

---

### Task 2: Configure Security Group for Database Access

Modify the security group to allow:

* SSH (Port 22) for remote access
* Database port (e.g., MySQL – 3306 or PostgreSQL – 5432)

---

### Task 3: Connect to EC2 Instance

Connect to the EC2 instance using SSH from your local machine.

---

### Task 4: Install Database Server

Install a database server software such as MySQL, MariaDB, or PostgreSQL on the EC2 instance using package manager commands.

---

### Task 5: Start and Configure Database Service

Start the database service and configure basic settings such as root password and user privileges.

---

### Task 6: Create a Sample Database

Create a sample database and a table inside it. Insert a few records into the table.

---

### Task 7: Test Database Connectivity

Test the database server by connecting to it locally or remotely and performing basic SQL queries.

---

## Workflow (Student Explanation)

(Write the steps you followed in your own words)

1. Create RDS Security Group

   Go to VPC → Security Groups → Create Security Group

   Name: DB Security Group

   VPC: Lab VPC

   Add inbound rule:

   Type: MySQL/Aurora (3306)

   Source: Web Security Group

2. Create DB Subnet Group

   Open RDS → Subnet Groups → Create DB Subnet Group

   Name: DB-Subnet-Group

   VPC: Lab VPC

   Select Availability Zones:

   us-east-1a

   us-east-1b

   Select subnets:

   10.0.1.0/24

   10.0.3.0/24

3. Launch RDS MySQL Database

   Go to RDS → Databases → Create Database

   Engine: MySQL

   Template: Dev/Test

   Availability: Multi-AZ DB Instance

4. Configure Database Settings

   DB Identifier: lab-db

   Username: main

   Password: lab-password

   Instance class: db.t3.micro

   Storage: 20 GB (General Purpose SSD)

   VPC: Lab VPC

   Security Group: DB Security Group

   Initial DB Name: lab

5. Retrieve Database Endpoint

   Wait until database status becomes Available

   Go to Connectivity & Security

   Copy the RDS Endpoint

   Save it for application configuration

6. Connect Web Application to Database

   Open the provided WebServer IP

   Navigate to RDS configuration page

   Enter:

   Endpoint: <RDS Endpoint>

   Database: lab

   Username: main

   Password: lab-password

   Submit and test the Address Book application by adding/editing contacts

## Output Screenshots (Attach 3)

### Screenshot 1: EC2 Instance for Database Server

![orate OtCIM INVOL8 Jesk Sang em rudd saudy](https://github.com/user-attachments/assets/1c6baf66-a1f1-4cba-b3e8-9952203d19ad)

---

### Screenshot 2: Database Service Running

![Lab-5](https://github.com/user-attachments/assets/b447237f-d27f-49f3-bbe4-fd4a54421589)

---

### Screenshot 3: Sample Database and Table

![EE E](https://github.com/user-attachments/assets/4f44db0f-82f4-46d5-9658-e71e6bf0544f)

---

## Result

This experiment demonstrated how to build a database server in AWS using an EC2 instance. By installing and configuring a DBMS, creating a sample database, and testing connectivity, the fundamentals of hosting and managing a cloud-based database server were underst
