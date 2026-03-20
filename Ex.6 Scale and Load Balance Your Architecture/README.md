# Lab 6 – Scale and Load Balance Your Architecture

## Title

Scale and Load Balance Your Architecture <BR>
Author : `S Rajath`   Reg no : `212224240127`   Date : `13.03.2026`

---

## Objective

The objective of this lab is to understand how to design a scalable and highly available architecture on AWS using Auto Scaling and Elastic Load Balancing. This experiment focuses on distributing incoming traffic across multiple EC2 instances, automatically scaling resources based on demand, and validating fault tolerance.

---

## Prerequisites

* Basic knowledge of Amazon EC2 and VPC
* Completion of previous labs (IAM, EC2, EBS, Database Server)
* AWS Academy Lab access
* Stable internet connection

---

## Tools Used

* AWS Management Console
* Amazon EC2
* Elastic Load Balancer (ELB / ALB)
* Auto Scaling Groups (ASG)
* Amazon CloudWatch

---

## Tasks Performed

### Task 1: Review Existing Architecture

Students review the existing EC2-based application architecture created in previous experiments.

### Task 2: Create a Launch Template

Students create a launch template that defines the EC2 instance configuration including AMI, instance type, security group, and user data.

### Task 3: Create an Auto Scaling Group

Students create an Auto Scaling Group using the launch template and configure minimum, maximum, and desired instance capacity.

### Task 4: Configure an Application Load Balancer

Students create an Application Load Balancer and configure target groups for routing traffic to EC2 instances.

### Task 5: Register Auto Scaling Group with Load Balancer

Students attach the Auto Scaling Group to the target group of the load balancer.

### Task 6: Configure Scaling Policies

Students configure scaling policies based on CPU utilization using Amazon CloudWatch alarms.

### Task 7: Test Load Balancing and Scaling

Students test the setup by generating traffic and observing automatic scaling and load distribution.

---

## Workflow (To be filled by Student)

1. **Create an AMI from Existing EC2 Instance**

   * Navigate to **EC2 → Instances**
   * Select **Web Server 1**
   * Click **Actions → Image and templates → Create Image**
   * Image Name: `WebServerAMI`
   * Description: `Lab AMI for Web Server`
   * Click **Create Image**

2. **Create Target Group**

   * Go to **EC2 → Target Groups**
   * Click **Create Target Group**
   * Target Type: `Instances`
   * Name: `LabGroup`
   * VPC: `Lab VPC`
   * Skip registering targets
   * Click **Create Target Group**

3. **Create Application Load Balancer**

   * Navigate to **EC2 → Load Balancers**
   * Click **Create Load Balancer → Application Load Balancer**
   * Name: `LabELB`
   * VPC: `Lab VPC`
   * Subnets:

     * `Public Subnet 1`
     * `Public Subnet 2`
   * Security Group: `Web Security Group`
   * Listener: `HTTP : 80`
   * Default Action: `Forward to LabGroup`
   * Click **Create Load Balancer**

4. **Create Launch Template**

   * Go to **EC2 → Launch Templates**
   * Click **Create Launch Template**
   * Template Name: `LabConfig`
   * AMI: `WebServerAMI`
   * Instance Type: `t2.micro`
   * Key Pair: `vockey`
   * Security Group: `Web Security Group`
   * Enable **Detailed CloudWatch Monitoring**
   * Click **Create Launch Template**

5. **Create Auto Scaling Group**

   * From the launch template, select **Create Auto Scaling Group**
   * Name: `Lab Auto Scaling Group`
   * VPC: `Lab VPC`
   * Subnets:

     * `Private Subnet 1`
     * `Private Subnet 2`
   * Attach to existing load balancer → `LabGroup`
   * Desired Capacity: `2`
   * Minimum Capacity: `2`
   * Maximum Capacity: `6`
   * Scaling Policy:

     * Name: `LabScalingPolicy`
     * Metric: `Average CPU Utilization`
     * Target Value: `60%`
   * Add Tag:

     * Key: `Name`
     * Value: `Lab Instance`
   * Click **Create Auto Scaling Group**

6. **Test Load Balancing and Auto Scaling**

   * Access the **Load Balancer DNS name** in a browser
   * Verify application loads successfully
   * Use **Load Test** in the web app to increase CPU usage
   * Monitor **CloudWatch alarms** for scaling events
   * Confirm new instances launch automatically
   * Finally terminate **Web Server 1** from EC2


---

## Output Screenshots 

Task 1: Create an AMI for Auto Scaling

![• Elane black Sourd](https://github.com/user-attachments/assets/7dbcdbd1-304e-49db-9074-a67f43382d84)


Task 2: Create a Load Balancer
![Lab - 6](https://github.com/user-attachments/assets/ef5d3c44-536a-43fc-9f78-9785e8f7f798)


Task 3: Create a Launch Template and an Auto Scaling Group

![Lab - 6](https://github.com/user-attachments/assets/9a65ae5c-3d3f-46f8-82f0-b9a6bf9eabc1)


Task 4: Verify that Load Balancing is Working

![• Elese Rock Strd](https://github.com/user-attachments/assets/4ef0ebfd-4b3b-499e-a963-5f2ae96de5cd)


---


## Result

This experiment demonstrated how to build a scalable and fault-tolerant cloud architecture using Auto Scaling Groups and Elastic Load Balancing. The system automatically adjusted resources based on workload and ensured continuous service availability by distributing traffic across multiple instances.
