# Hybrid Identity Risk Analyzer with Agentic AI

> **Active Directory + AWS IAM + AI Investigation and Remediation**

[![Status](https://img.shields.io/badge/Status-Completed-brightgreen)]() [![Type](https://img.shields.io/badge/Type-Cybersecurity%20Case%20Study-blue)]()

## Video Demonstration

🎥 **Watch the project walkthrough:** [Add video link here](VIDEO_LINK_HERE)

---

## Why I Built This

Identity is one of the most important attack surfaces in a modern organization. I built this platform to bring Active Directory and AWS IAM into one identity-risk workflow. The system discovers human and non-human identities, evaluates risky configurations, assigns severity, and generates AI-assisted investigation and remediation reports.

## The Problem

Active Directory and AWS IAM are often reviewed separately, creating blind spots around privileged accounts, non-expiring passwords, long-lived access keys, excessive permissions, and unmanaged service identities.

## Architecture

```text
Active Directory → Human Identity Agent → Human Risk Agent
AWS IAM → Non-Human Identity Agent → NHI Risk Agent
Both → GPT Investigation Agent → GPT Remediation Agent → Streamlit Dashboard
```

## How the Project Works

The Human Identity Agent uses LDAP to collect users, service accounts, privileged group membership, account status, and password attributes. The Non-Human Identity Agent uses boto3 to enumerate IAM users, roles, policies, and access keys. Risk engines score findings, and AI agents generate investigation context and remediation guidance displayed in Streamlit.

## Key Capabilities

- Active Directory identity discovery
- AWS IAM analysis
- Human and non-human risk scoring
- Privileged-account detection
- AI investigation reports
- AI remediation guidance
- Streamlit dashboard

## Results

The platform identified high-risk identities such as privileged AD accounts with non-expiring passwords and AWS IAM users with AdministratorAccess. It explained why each condition mattered, possible attack paths, business impact, and recommended remediation.

## Skills Demonstrated

Active Directory, AWS IAM, Python, ldap3, boto3, Streamlit, OpenAI, identity security, least privilege, risk scoring, agentic AI.

## Project Gallery

<img src="./assets/image-01.png" alt="Project screenshot" width="850">

## What I Learned

This project strengthened my ability to connect technical controls to a real security workflow. It also reinforced the importance of testing integrations end to end, documenting limitations honestly, and designing automation that supports analysts rather than hiding important decisions.

## Future Improvements

- Add more automated test coverage
- Improve dashboards and reporting
- Expand detection or risk logic
- Strengthen secrets management
- Add scheduled execution and notifications

---

## Author

**Stewart Nyamutswa**

Cybersecurity | SOC Operations | Cloud Security | Incident Response
