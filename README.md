Clarusway SDA Bootcamp Deployment Project
Week-9 Assignment SDA2016Hala Tahlawi
AWS Web Application Deployment with ALB + ASG + S3
------------------------------------------------------
This project showcases the deployment of a highly available Clarusway Bootcamp website on Amazon Web Services (AWS) using the following key services:
Technologies Used
	•	Amazon S3 – for hosting static assets like HTML and image files.
	•	Auto Scaling Group (ASG) – to ensure high availability and scalability of NGINX web servers.
	•	Application Load Balancer (ALB) – to distribute incoming traffic evenly across multiple EC2 instances.
⸻
Part 1: S3 Configuration
S3 Bucket Created:
yourname-clarusway-assets
Files Uploaded:
	•	index.html
	•	logo.png
	•	sda.png
Static Website Hosting:
	•	Enabled for the bucket.
Bucket Policy:
	•	Configured to allow public read access to the static content.
Static Website URL:
	•	(Insert your actual S3 static website URL here)
  URL : https://halahahlawi-clarusway-assets.s3.us-east-1.amazonaws.com/index.html
  Verification: curl.exe -I "https://halahahlawi-clarusway-assets.s3.us-east-1.amazonaws.com/index.html"

  Part 2: Auto Scaling Group (ASG) Setup
Launch Template Created
Includes the following User Data script for EC2 instance initialization:
#!/bin/bash
yum update -y
yum install nginx -y
systemctl start nginx
systemctl enable nginx
aws s3 cp s3://HalaTahlawi-clarusway-assets/index.html /usr/share/nginx/html/
Auto Scaling Group Configuration
	•	Minimum Capacity: 1 instance
	•	Maximum Capacity: 3 instances
	•	Desired Capacity: 2 instances
	•	Health Checks: Enabled for both EC2 and ELB
⸻
Part 3: Application Load Balancer (ALB) Setup
ALB Configuration
	•	Type: Internet-facing
	•	Listener: Port 80 (HTTP)
Target Group
	•	Registered instances from the Auto Scaling Group
Health Check Settings
	•	Path: /
	•	Ensures that only healthy instances receive traffic  
   ALB DNS URL : halatahlawi4-989862332.us-east-1.elb.amazonaws.com

 Load balancing confirmed with:
Clean-up • S3 bucket deleted. • ASG terminated. • ALB removed.




