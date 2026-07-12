# Secure AWS E-Commerce Platform

> **Highly Available Cloud Architecture with Layered Security and Monitoring**

[![Status](https://img.shields.io/badge/status-portfolio--ready-success)]()
[![Security](https://img.shields.io/badge/focus-cybersecurity-blue)]()
[![Author](https://img.shields.io/badge/author-Stewart%20Nyamutswa-lightgrey)]()

## Video Demonstration

🎥 **Project Video:** [Add video link here](VIDEO_LINK_HERE)

## Project Overview


This project deploys a production-style e-commerce application on AWS using a multi-tier architecture. The platform uses CloudFront, AWS WAF, an Application Load Balancer, Auto Scaling EC2 instances, Amazon RDS PostgreSQL, Amazon S3, Route 53, and multiple AWS security and monitoring services.


## Business Problem


Internet-facing applications require availability, scalability, data protection, secure network design, centralized monitoring, and defenses against common web attacks. A single-server deployment does not provide sufficient resilience or layered security.


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
  ├── EC2 Web Server 1
  └── EC2 Web Server 2
          │
          ▼
Amazon RDS PostgreSQL

Amazon S3 ─► Product Images

Monitoring and Security:
CloudWatch | CloudTrail | GuardDuty | Security Hub | AWS Config
```


> Add the final architecture diagram to `architecture/architecture-diagram.png`.

## Workflow


1. Route user traffic through Route 53 and CloudFront.
2. Filter malicious requests using AWS WAF.
3. Distribute requests through the Application Load Balancer.
4. Serve the application from private EC2 instances.
5. Store relational data in private Amazon RDS PostgreSQL.
6. Deliver product images from Amazon S3.
7. Monitor infrastructure and security events using AWS-native services.
8. Deploy application updates through GitHub Actions.


## Key Features


- Multi-tier VPC architecture
- Public and private subnet separation
- CloudFront content delivery
- AWS WAF managed protections
- Load balancing and Auto Scaling
- Private EC2 application tier
- Private RDS PostgreSQL database
- S3 asset storage
- GuardDuty and Security Hub monitoring
- CloudTrail, CloudWatch, and AWS Config
- GitHub Actions CI/CD


## Attack or Test Scenarios


- SQL injection testing
- WAF rule validation
- Rate-limit testing
- Monitoring suspicious activity
- Load-balancer health-check validation
- Cloud security finding review


## Technologies

See [`TECHNOLOGIES.md`](./TECHNOLOGIES.md).

## Screenshots

Store screenshots in [`screenshots/`](./screenshots/).

Recommended evidence:

1. Architecture diagram
2. Environment or service overview
3. Attack or test execution
4. Detection or finding
5. Automation workflow
6. Investigation or analysis
7. Response or remediation
8. Final result

## Results

Document measurable results here:

- Alerts generated:
- Cases created:
- Findings investigated:
- Mean Time to Detect:
- Mean Time to Respond:
- False positives:
- Successful remediations:
- Verification results:

## Skills Demonstrated


AWS architecture, cloud security, VPC networking, WAF, CloudFront, EC2, RDS, S3, ALB, Auto Scaling, GuardDuty, Security Hub, CloudTrail, CloudWatch, AWS Config, CI/CD.


## Security and Privacy

- No production credentials are included.
- API keys and passwords must be stored in environment variables or secret managers.
- Public screenshots must be reviewed for sensitive information.
- Private IP addresses may be anonymized where necessary.
- Attack simulations must only be performed in authorized lab environments.

## Future Improvements

- Add more attack or test scenarios.
- Improve detection and correlation logic.
- Add automated notifications.
- Add additional threat-intelligence sources.
- Add metrics and trend dashboards.
- Expand documentation with incident reports and lessons learned.

## Author

**Stewart Nyamutswa**

Cybersecurity | SOC Operations | Cloud Security | Incident Response
