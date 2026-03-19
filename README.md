# AWS-ALB-Advanced-Request-Routing
### Project Overview
This project demonstrates how to implement Advanced Request Routing using AWS Application Load Balancer (ALB) to intelligently direct traffic based on conditions such as path, HTTP methods, headers, IP address, and weighted routing.
It simulates real-world scenarios like A/B testing, blue/green deployments, and bot traffic separation, which are critical in modern cloud architectures.

### Key Concepts

Amazon EC2 → Compute instances hosting applications

Elastic Load Balancing (ELB) → Distributes traffic across resources

Application Load Balancer (ALB) → Layer 7 routing with advanced rules

Advanced Request Routing → Routing based on conditions (path, headers, IP, method, weight)

### Objectives

Launch multiple EC2 instances

Configure ALB with multiple target groups

Implement advanced routing rules

Simulate traffic segmentation (users, bots, testing)  

Validate routing behavior

### Implementation Steps
1️⃣ Launch EC2 Instances

Use this script for setup:

#!/bin/bash
sudo yum update -y
sudo yum install -y httpd
sudo systemctl start httpd
sudo systemctl enable httpd

echo "Response from $(hostname)" > /var/www/html/index.html

2️⃣ Create Target Groups

TG-1 → Human traffic

TG-2 → Bot/Crawler traffic

TG-3 → Canary / Testing environment

3️⃣ Create Application Load Balancer

Type: Internet-facing

Listener: HTTP (Port 80)

4️⃣ Configure Advanced Routing Rules

Examples:

Path-based → /api → TG-1

Header-based → User-Agent: bot → TG-2

Weighted routing →

80% → TG-1

20% → TG-3

5️⃣ Test Configuration

Simulate bot vs user traffic

Validate weighted distribution

Verify routing behavior

### Security Considerations

Use AWS WAF to block malicious patterns

Restrict access using IP-based rules

Enable HTTPS (TLS termination at ALB)

Enable logging (ALB + CloudWatch)

Use private subnets for EC2 instances

Implement least privilege IAM roles

### Why This Matters

Enables fine-grained traffic control

Supports zero-downtime deployments

Improves security posture

Critical for modern cloud-native & microservices architectures

### Real-World Use Cases

A/B testing (feature rollout)

Blue/Green deployments

Bot traffic isolation

Geo/IP-based restrictions

API routing by method (GET/POST)

### Security insights
ALB is not just a load balancer — it's a smart traffic controller

Advanced routing enables secure, scalable deployments

Essential skill for Cloud Security & DevSecOps roles

### Conclusion

This project demonstrates how to design intelligent routing strategies using AWS ALB to support scalable, secure, and resilient cloud architectures.
