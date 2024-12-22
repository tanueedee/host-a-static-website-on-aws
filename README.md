### Diagram
![Alt text](/Host_a_Static_Website_on_AWS.png)

# Host a Static Website on AWS

This project demonstrates how to host a static HTML web application on AWS using various AWS services to ensure scalability, security, and fault tolerance. The implementation details and resources are outlined below. The repository includes a reference architecture diagram and deployment scripts to replicate this setup.

## Features and Architecture

1. **Virtual Private Cloud (VPC):** Configured a VPC with both public and private subnets across two different Availability Zones for enhanced reliability.
2. **Internet Gateway:** Deployed an Internet Gateway to enable VPC instances to communicate with the wider Internet.
3. **Security Groups:** Configured Security Groups to act as a network firewall mechanism for the infrastructure.
4. **Multi-AZ Deployment:** Leveraged two Availability Zones for improved fault tolerance and system reliability.
5. **Public Subnets:** Used public subnets for NAT Gateway and Application Load Balancer.
6. **EC2 Instance Connect Endpoint:** Implemented secure connections to resources in public and private subnets.
7. **Private Subnets:** Deployed web servers (EC2 instances) within private subnets to enhance security.
8. **NAT Gateway:** Enabled private subnet instances to access the Internet.
9. **Website Hosting:** Hosted the static website on EC2 instances.
10. **Application Load Balancer:** Configured an Application Load Balancer and a target group to distribute web traffic evenly across multiple EC2 instances in an Auto Scaling Group.
11. **Auto Scaling Group:** Ensured availability, scalability, and fault tolerance by managing EC2 instances dynamically.
12. **GitHub Integration:** Stored web files on GitHub for version control and collaboration.
13. **SSL Security:** Secured communication using AWS Certificate Manager.
14. **Monitoring and Alerts:** Configured Amazon Simple Notification Service (SNS) to send alerts for Auto Scaling Group activities.
15. **Domain Registration and DNS:** Registered a domain and set up DNS records using Amazon Route 53.

## Getting Started

### Prerequisites
- AWS account with necessary IAM permissions.
- Domain name registered with Amazon Route 53 or another DNS provider.
- Git installed on your local machine.

### Deployment Steps

1. **Launch VPC and Networking Components:**
   - Create a VPC with public and private subnets across two Availability Zones.
   - Deploy an Internet Gateway and NAT Gateway.
   - Configure route tables for proper connectivity.

2. **Set Up Security Groups:**
   - Create Security Groups for the Application Load Balancer and EC2 instances to control traffic.

3. **Deploy EC2 Instances:**
   - Launch EC2 instances in private subnets.
   - Use the provided deployment script to configure the web server.

4. **Configure Application Load Balancer:**
   - Set up an Application Load Balancer in public subnets.
   - Define a target group for the Auto Scaling Group.

5. **Set Up Auto Scaling Group:**
   - Create an Auto Scaling Group to manage EC2 instances across multiple Availability Zones.

6. **Enable SSL/TLS Security:**
   - Use AWS Certificate Manager to create and attach an SSL certificate to the Application Load Balancer.

7. **Monitor and Alert:**
   - Set up Amazon SNS to receive notifications for Auto Scaling events.

8. **Configure Domain Name:**
   - Use Route 53 to set up DNS records pointing to the Application Load Balancer.

### Deployment Script
Use the following script to configure EC2 instances:

```bash
#!/bin/bash
# Switch to the root user
sudo su
# Update installed packages
yum update -y
# Install Apache HTTP Server
yum install -y httpd
# Change to the Apache web root
dcd /var/www/html
# Install Git
yum install git -y
# Clone the project repository
git clone https://github.com/aosnotes77/host-a-static-website-on-aws.git
# Copy files to the Apache web root
cp -R host-a-static-website-on-aws/. /var/www/html/
# Remove the cloned repository
temove -rf host-a-static-website-on-aws
# Enable Apache to start on boot
systemctl enable httpd
# Start Apache
systemctl start httpd
```
## Repository
The GitHub repository contains:
- Architecture diagram
- Deployment script
- Static website files



