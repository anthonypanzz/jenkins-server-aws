# Jenkins Deployment on AWS - DevOps Project

This repository contains the resources, scripts, and configurations used to deploy Jenkins on an EC2 instance in AWS. The deployment utilizes a VPC setup with public and private subnets, and ensures that Jenkins is accessible securely only from specific IP addresses.

## Project Overview

This project demonstrates how to deploy Jenkins in a highly available, fault-tolerant environment using AWS services like EC2, VPC, Route 53, and IAM. The goal is to set up Jenkins on an EC2 instance within a customized VPC with enhanced security measures, while also ensuring that Jenkins is accessible from only a specific IP address for better security.

### Architecture

- **VPC Setup**: The environment is deployed within a custom VPC with 2 private and 2 public subnets across 2 Availability Zones (AZs). This setup improves reliability and fault tolerance.
- **Security**: Only specific IP addresses are allowed to access the Jenkins server. Security groups and key pairs are used to enhance security.
- **Elastic IP**: An Elastic IP address is allocated and associated with the Jenkins EC2 instance for persistent access.
- **DNS Configuration**: The domain name is registered using Route 53 and DNS records are configured to point to the Jenkins instance.

---

## Project Setup Steps

1. **Create a VPC**  
   Create a VPC with 2 public and 2 private subnets in two Availability Zones to increase reliability and fault tolerance. This VPC will host the EC2 instance for Jenkins and all associated resources.

2. **Deploy an Internet Gateway**  
   Set up an Internet Gateway to allow the EC2 instance in the public subnet to communicate with the wider Internet.

3. **Create Public and Private Route Tables**  
   Configure routing for the public and private subnets. Public subnets will have routes to the Internet Gateway, while private subnets will route traffic through a NAT gateway.

4. **Create a NAT Gateway**  
   A NAT gateway is deployed to allow EC2 instances in the private subnet to access the internet for updates and communication with external services.

5. **Create Security Groups for Jenkins Server**  
   Configure security groups to allow only the necessary inbound and outbound traffic, and restrict access to Jenkins by specific IP addresses.

6. **Create a Key Pair**  
   Generate a key pair for SSH access to the EC2 instance where Jenkins will be deployed.

7. **Deploy an EC2 Instance**  
   Launch an EC2 instance in the public subnet using the appropriate AMI (Amazon Linux or Ubuntu). Assign the created Elastic IP address to this instance for stable, persistent access.

8. **Install Jenkins**  
   SSH into the EC2 instance and install Jenkins by following the official installation instructions for your chosen operating system (e.g., Amazon Linux 2, Ubuntu). Start the Jenkins service and verify that it is running.

9. **Register Domain Name and Configure DNS with Route 53**  
   Register a domain name with Route 53 and create a DNS record that points to the Elastic IP address of the Jenkins EC2 instance. This will allow you to access Jenkins via a user-friendly domain name.

10. **Restrict Jenkins Access to Specific IPs**  
   Using security groups and firewall settings, configure Jenkins to be accessible only from your own IP address. This enhances security by preventing unauthorized access.

11. **Secure Jenkins with Username and Password**  
   Set up authentication on Jenkins by configuring the appropriate username and password for access. This ensures that only authorized users can interact with the Jenkins application.




---

## Conclusion

This project showcases how to deploy Jenkins in a secure and highly available AWS environment using EC2, VPC, Route 53, and other AWS resources. With proper setup and security configurations, Jenkins is securely accessible for CI/CD tasks, allowing teams to automate their development processes effectively.



