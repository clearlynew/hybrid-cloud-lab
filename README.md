
# Hybrid Cloud Lab – Hosting a Web Server on AWS EC2

This is a hands-on project where I launched a cloud server on AWS, set up a secure web server, and made it publicly accessible. The goal was to better understand how networking works in the cloud using real AWS services like EC2, VPC, and security groups.

---

## What This Project Demonstrates

- Launching and connecting to a cloud-based virtual machine (EC2)
- Configuring VPC networking (subnets, internet gateways, route tables)
- Hosting a web page using Apache on a Linux server
- Managing firewall rules and SSH access securely

---

## Tools and Services Used

- AWS EC2 – to host the virtual machine
- Ubuntu 22.04 – as the OS on the server
- Apache2 – simple web server to host a test page
- Windows PowerShell – for SSH access from a local machine
- AWS VPC Console – to manage networking (subnets, IGW, route tables)

---

## Architecture Overview
[ Local Laptop ] <-- Internet --> [ AWS EC2 Server ]


- The EC2 server is in a public subnet with internet access
- Security groups are configured to allow SSH and HTTP traffic

---

## Setup Guide

### 1. Launch the EC2 Instance
- Use the Ubuntu 22.04 AMI (Free Tier eligible)
- Choose t2.micro instance type
- Enable auto-assigned public IP
- Create and download a key pair (.pem file)

### 2. Configure VPC Networking
- Ensure the EC2 instance is in a public subnet
- Attach an Internet Gateway (IGW) to the VPC
- Update the route table to allow outbound traffic:

### 3. Set Security Group Rules
- Allow:
- SSH (port 22) from your IP
- HTTP (port 80) from anywhere (0.0.0.0/0)

### 4. SSH into the EC2 Instance
Open PowerShell and run
ssh -i "C:\Path\To\your-key.pem" ubuntu@<EC2 Public IP>

### 5. Install and Configure Apache
sudo apt update
sudo apt install apache2 -y
echo "Hello from AWS Cloud!" | sudo tee /var/www/html/index.html


### 6. Test in Your Browser
Visit http://<EC2 Public IP> and you should see your message displayed.


