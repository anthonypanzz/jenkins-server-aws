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
![Screenshot 2025-04-01 221547](https://github.com/user-attachments/assets/661e6fcf-7d39-458f-aaa5-acd464d51d3e)


2. **Deploy an Internet Gateway**  
   Set up an Internet Gateway to allow the EC2 instance in the public subnet to communicate with the wider Internet.

3. **Create Public and Private Route Tables**  
   Configure routing for the public and private subnets. Public subnets will have routes to the Internet Gateway, while private subnets will route traffic through a NAT gateway.
![Screenshot 2025-04-01 221856](https://github.com/user-attachments/assets/3cdbfefc-c2c0-40ff-aa72-29260a62c7df)


4. **Create a NAT Gateway**  
   A NAT gateway is deployed to allow EC2 instances in the private subnet to access the internet for updates and communication with external services.
![Screenshot 2025-04-01 221937](https://github.com/user-attachments/assets/a6c24a8d-6426-4681-8ace-aa2e8c0e1d58)


5. **Create Security Groups for Jenkins Server**  
   Configure security groups to allow only the necessary inbound and outbound traffic, and restrict access to Jenkins by specific IP addresses.
![Screenshot 2025-04-01 220653](https://github.com/user-attachments/assets/bc4315d4-3904-432f-a852-c37775770094)



6. **Create a Key Pair**  
   Generate a key pair for SSH access to the EC2 instance where Jenkins will be deployed.
![Screenshot 2025-04-01 220634](https://github.com/user-attachments/assets/d6392828-6c49-4f6c-a649-bf4615440e3d)



7. **Deploy an EC2 Instance**  
   Launch an EC2 instance in the public subnet using the appropriate AMI (Amazon Linux or Ubuntu). Assign the created Elastic IP address to this instance for stable, persistent access.
![Screenshot 2025-04-01 220732](https://github.com/user-attachments/assets/07c83282-95dd-4682-8b1b-51e5d254e093)
![Screenshot 2025-04-01 220617](https://github.com/user-attachments/assets/2ab065d3-30be-434b-895a-b14370020fea)




9. **Install Jenkins**  
   SSH into the EC2 instance and install Jenkins by following the official installation instructions for your chosen operating system (Amazon Linux 2, Ubuntu). Start the Jenkins service and verify that it is running.
![Screenshot 2025-04-01 215310](https://github.com/user-attachments/assets/de01bcad-e014-4ac1-9e53-e5545e8abecb)
 ![Screenshot 2025-04-01 220828](https://github.com/user-attachments/assets/77ad7c21-23c3-4b4c-a9e5-4b7adb7eb645)
![Screenshot 2025-04-01 215705](https://github.com/user-attachments/assets/f39076ff-5d7a-4098-9f3b-cee4bc6e111c)



11. **Register Domain Name and Configure DNS with Route 53**  
   Register a domain name with Route 53 and create a DNS record that points to the Elastic IP address of the Jenkins EC2 instance. This will allow you to access Jenkins via a user-friendly domain name.
![Screenshot 2025-04-01 215937](https://github.com/user-attachments/assets/2ee668c6-2c97-4dfb-9992-25d61a0ef1a0)
![Screenshot 2025-04-01 220035](https://github.com/user-attachments/assets/4c0bdb2c-996b-44ef-904b-bfe8df3d7da8)
![Screenshot 2025-04-01 220109](https://github.com/user-attachments/assets/d2056c2c-2af7-4f75-bae6-e4a8370c679d)






12. **Restrict Jenkins Access to Specific IPs**  
   Using security groups and firewall settings, configure Jenkins to be accessible only from your own IP address. This enhances security by preventing unauthorized access.



13. **Secure Jenkins with Username and Password**  
   Set up authentication on Jenkins by configuring the appropriate username and password for access. This ensures that only authorized users can interact with the Jenkins application.
![Screenshot 2025-04-01 220305](https://github.com/user-attachments/assets/0a407f24-83f7-4095-b9b6-7d00df989a9b)
![Screenshot 2025-04-01 220330](https://github.com/user-attachments/assets/4a939dcc-57a1-4c36-9cc7-fe3425c16110)




---

## Conclusion

This project showcases how to deploy Jenkins in a secure and highly available AWS environment using EC2, VPC, Route 53, and other AWS resources. With proper setup and security configurations, Jenkins is securely accessible for CI/CD tasks, allowing teams to automate their development processes effectively.



