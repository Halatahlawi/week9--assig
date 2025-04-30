Clarusway SDA Bootcamp Deployment Project
Week-9 Assignment | SDA2016 | Hala Tahlawi
AWS Web Application Deployment with ALB + ASG + S3

Project Overview
This project demonstrates the deployment of a highly available Clarusway Bootcamp website on Amazon Web Services (AWS), utilizing core services such as Amazon S3, Auto Scaling Group (ASG), and Application Load Balancer (ALB). The goal is to ensure scalability, availability, and reliability of a static website hosted using NGINX.

Technologies Used
Amazon S3 – Hosts static assets like HTML and image files.

Auto Scaling Group (ASG) – Provides scalability and high availability for EC2 instances running NGINX.

Application Load Balancer (ALB) – Distributes incoming HTTP traffic evenly across healthy instances.

Part 1: S3 Configuration
S3 Bucket Details
Bucket Name: halahahlawi-clarusway-assets

Uploaded Files
index.html

logo.png

sda.png

Static Website Hosting
Status: Enabled

Bucket Policy: Configured for public read access

Static Website URL
URL: https://halahahlawi-clarusway-assets.s3.us-east-1.amazonaws.com/index.html 
Verification Command: curl.exe -I "https://halahahlawi-clarusway-assets.s3.us-east-1.amazonaws.com/index.html"



Part 2: Auto Scaling Group (ASG) Setup
Launch Template Configuration
Includes the following EC2 User Data script for instance initialization:

#!/bin/bash
yum update -y
yum install nginx -y
systemctl start nginx
systemctl enable nginx
aws s3 cp s3://HalaTahlawi-clarusway-assets/index.html /usr/share/nginx/html/


ASG Parameters
Minimum Capacity: 1 instance

Maximum Capacity: 3 instances

Desired Capacity: 2 instances

Health Checks: Enabled (EC2 & ELB)

Part 3: Application Load Balancer (ALB) Setup
ALB Configuration
Type: Internet-facing

Listener: Port 80 (HTTP)

Target Group
Targets: Instances launched by the ASG

Health Check Path: /

Ensures traffic is routed only to healthy instances

ALB DNS URL
URL: halatahlawi4-989862332.us-east-1.elb.amazonaws.com

Verification
Load balancing behavior successfully confirmed across healthy EC2 instances.


