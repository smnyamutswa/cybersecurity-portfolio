# Secure AWS E-Commerce Platform — Project Summary

## Problem


Internet-facing applications require availability, scalability, data protection, secure network design, centralized monitoring, and defenses against common web attacks. A single-server deployment does not provide sufficient resilience or layered security.


## Solution


This project deploys a production-style e-commerce application on AWS using a multi-tier architecture. The platform uses CloudFront, AWS WAF, an Application Load Balancer, Auto Scaling EC2 instances, Amazon RDS PostgreSQL, Amazon S3, Route 53, and multiple AWS security and monitoring services.


## Workflow


1. Route user traffic through Route 53 and CloudFront.
2. Filter malicious requests using AWS WAF.
3. Distribute requests through the Application Load Balancer.
4. Serve the application from private EC2 instances.
5. Store relational data in private Amazon RDS PostgreSQL.
6. Deliver product images from Amazon S3.
7. Monitor infrastructure and security events using AWS-native services.
8. Deploy application updates through GitHub Actions.


## Results

Add the final measured outcomes and lessons learned after implementation.
