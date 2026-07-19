# Secure Cloud-Native E-Commerce Platform on AWS

> **Professional Banner**  
> **A highly available web application built with layered AWS security**

## Project Summary

Stewart Secure Shop is a production-style e-commerce application deployed on AWS.

The platform uses Route 53, CloudFront, AWS WAF, an Application Load Balancer, two EC2 application servers, Amazon RDS PostgreSQL, and Amazon S3. CloudWatch, CloudTrail, GuardDuty, Security Hub, and AWS Config provide monitoring and security visibility.

I deployed the infrastructure with CloudFormation so that the environment was repeatable instead of being built manually each time.

## Why I Built This

Many beginner AWS projects place a website on one public EC2 instance and stop there.

I wanted to build something that forced me to think about private networking, high availability, database security, content delivery, web protection, monitoring, and infrastructure as code as one connected system.

## Technologies Used

- AWS CloudFormation
- Amazon Route 53
- Amazon CloudFront
- AWS WAF
- Application Load Balancer
- Amazon EC2
- Auto Scaling
- Amazon RDS PostgreSQL
- Amazon S3
- Amazon CloudWatch
- AWS CloudTrail
- Amazon GuardDuty
- AWS Security Hub
- AWS Config
- Flask
- Gunicorn
- Nginx
- GitHub Actions

## Architecture

```text
Users
  │
  ▼
Route 53
  │
  ▼
CloudFront
  │
  ▼
AWS WAF
  │
  ▼
Application Load Balancer
  │
  ▼
Auto Scaling Group
  ├── EC2 application server 1
  └── EC2 application server 2
              │
              ▼
     Amazon RDS PostgreSQL

Amazon S3 ───► Product images

Monitoring:
CloudWatch | CloudTrail | GuardDuty | Security Hub | AWS Config
```

## Engineering Journey

### Step 1 — Design

I designed a multi-tier VPC with public subnets, private application subnets, and private database subnets across multiple Availability Zones.

Only the load balancer was directly reachable from the public traffic path. The application servers and database remained private.

### Step 2 — Build

I divided the infrastructure into multiple CloudFormation stacks so that networking, compute, database, and supporting services could be deployed and troubleshot separately.

The application ran on Ubuntu using Flask, Gunicorn, and Nginx. PostgreSQL stored application data, while S3 stored product images.

### Step 3 — Secure

I restricted security groups by service and placed AWS WAF in front of the application.

The database used SSL connections and remained inside private subnets. GuardDuty, Security Hub, CloudTrail, CloudWatch, and AWS Config provided several layers of visibility.

### Step 4 — Test

I tested the application through the complete traffic path rather than only connecting directly to an EC2 instance.

Testing included load-balancer health checks, database connectivity, S3 image delivery, CloudFront behavior, WAF managed rules, rate limiting, and controlled security tests against my own infrastructure.

### Step 5 — Validate

I confirmed that both EC2 targets were healthy, the custom domain worked, the database returned product data, images loaded correctly, and AWS security services recorded relevant activity.

## Challenges & Troubleshooting

### The load balancer marked both servers unhealthy

I traced the request from the load balancer to Nginx and Gunicorn. The issue was in the application listening and health-check path rather than the load balancer itself.

### S3 returned AccessDenied

The image path worked only after I corrected the bucket and CloudFront permissions.

### The application could not connect to PostgreSQL

I checked the endpoint, credentials, security groups, network path, and SSL requirement one layer at a time until the connection succeeded.

### CloudFront made troubleshooting less obvious

A failure at the origin could appear to be a CloudFront problem. I learned to test each layer independently before testing the entire path.

### WAF required tuning

Some controlled requests were initially allowed. I reviewed managed-rule configuration, rule priorities, and rate-limit values until the behavior matched the design.

## Results

- Deployed a custom-domain e-commerce application
- Distributed traffic across two healthy EC2 servers
- Kept application servers and RDS in private subnets
- Stored product data in PostgreSQL
- Delivered product images from S3
- Used CloudFront as the public delivery layer
- Protected the application with AWS WAF
- Enabled AWS-native security and operational monitoring
- Made the infrastructure repeatable with CloudFormation

## Lessons Learned

Cloud security comes from the architecture as a whole.

A private subnet is useful only when routing, security groups, load balancing, identity, monitoring, and application configuration all support the same design.

Building the environment taught me AWS services. Troubleshooting the full request path taught me cloud engineering.

## Project Gallery

All screenshots and diagrams are stored in the [`assets`](./assets/) folder.

Suggested viewing order:

1. Architecture diagram
2. CloudFormation stacks
3. VPC and subnet layout
4. Healthy load-balancer targets
5. Running application
6. RDS and S3 integration
7. WAF testing
8. Monitoring and security findings

## Video Demonstration

Add the project demonstration link here.
