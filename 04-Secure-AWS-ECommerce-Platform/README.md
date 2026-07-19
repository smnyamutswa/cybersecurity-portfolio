# Secure Cloud-Native E-Commerce Platform on AWS

> **Professional Banner**  
> **Highly Available Architecture · Layered Security · Infrastructure as Code**

---

## Project Summary

Stewart Secure Shop is a production-style e-commerce application deployed on AWS. It uses a multi-tier VPC, two EC2 application servers, an Application Load Balancer, Amazon RDS PostgreSQL, Amazon S3, CloudFront, AWS WAF, and AWS-native monitoring services.

The infrastructure was deployed with CloudFormation so the environment could be created consistently and managed as code.

---

## Why I Built This

Many beginner AWS projects stop after deploying a website to a single public EC2 instance. That approach does not demonstrate high availability, private data storage, layered security, monitoring, or repeatable deployment.

I built this project to understand how multiple AWS services work together to deliver and protect a complete application.

---

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

---

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
  ├── EC2 Application Server 1
  └── EC2 Application Server 2
              │
              ▼
     Amazon RDS PostgreSQL

Amazon S3 ───► Product Images

Monitoring and Security:
CloudWatch | CloudTrail | GuardDuty | Security Hub | AWS Config
```

Public traffic reaches the application through Route 53, CloudFront, WAF, and the load balancer. The application and database remain in private subnets.

---

## Engineering Journey

### Step 1 — Design

I designed a multi-tier VPC with public subnets, private application subnets, and private database subnets.

The design separated internet-facing components from the application and data layers while supporting high availability across multiple Availability Zones.

### Step 2 — Build

I deployed the infrastructure through multiple CloudFormation stacks. The application used Flask behind Gunicorn and Nginx on two Ubuntu EC2 instances.

Amazon RDS PostgreSQL stored customer and product data, while Amazon S3 stored product images and static assets.

### Step 3 — Secure

I placed the application servers and database in private subnets, restricted security-group access, enabled SSL for the database connection, and placed AWS WAF in front of the application.

GuardDuty, Security Hub, CloudTrail, CloudWatch, and AWS Config provided security and operational visibility.

### Step 4 — Test

I tested load-balancer health checks, availability across two EC2 instances, database connectivity, S3 image delivery, CloudFront behavior, WAF managed rules, rate limiting, and controlled security testing against infrastructure I owned.

### Step 5 — Validate

I confirmed that both targets were healthy, the application was available through the custom domain, product data loaded from RDS, images loaded from S3, and security events appeared in AWS monitoring services.

---

## Challenges & Troubleshooting

### Unhealthy Load Balancer Targets

The load balancer initially marked both EC2 instances as unhealthy. I traced the request path and corrected the Gunicorn listening configuration and health-check behavior.

### S3 AccessDenied Errors

Product images failed to load because the bucket and distribution permissions did not allow the intended access path. I updated the policy and validated the CloudFront configuration.

### Database Connectivity

The Flask application initially could not reach PostgreSQL. I checked the RDS endpoint, security groups, credentials, and SSL requirements until the connection succeeded.

### CloudFront and Routing Problems

CloudFront origin behavior and routing caused timeout and content-delivery issues. Troubleshooting each layer separately helped isolate the failure.

### WAF Rule Tuning

Some controlled test requests were initially allowed. I reviewed the managed-rule configuration, priorities, and rate-limit settings until the intended behavior was achieved.

---

## Results

- A custom-domain e-commerce application was deployed successfully.
- Traffic was distributed across two healthy EC2 instances.
- Application servers and RDS remained in private subnets.
- Product data was stored in PostgreSQL.
- Product images were delivered from S3.
- CloudFront acted as the public content-delivery layer.
- AWS WAF inspected incoming traffic.
- AWS monitoring services provided centralized visibility.
- CloudFormation made the environment repeatable.

---

## Lessons Learned

Cloud security is not delivered by one service. It depends on the way networking, compute, identity, storage, application security, and monitoring work together.

Building the platform taught me AWS services. Troubleshooting it taught me cloud engineering.

---

## Project Gallery

Use the strongest images from the project asset folder in this order:

1. Architecture diagram
2. CloudFormation stacks
3. VPC and subnet layout
4. Healthy load-balancer targets
5. Running application
6. RDS and S3 integration
7. WAF testing
8. GuardDuty, Security Hub, or CloudWatch evidence


---

## Video Demonstration

Add the project YouTube video or playlist link here.

---

## Author

**Stewart Nyamutswa**  
Cybersecurity | SOC Operations | Cloud Security | Incident Response
