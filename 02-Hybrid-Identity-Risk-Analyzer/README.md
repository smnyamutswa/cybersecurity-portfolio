# Hybrid Identity Risk Analyzer with Agentic AI

> **Professional Banner**  
> **Discover Identities → Correlate Risk → Investigate → Recommend Remediation**

---

## Project Summary

This project analyzes identity risk across Microsoft Active Directory and AWS IAM. Python-based agents collect human and cloud identity data, identify risky configurations, assign severity scores, and generate AI-assisted investigation and remediation reports.

The results are presented through a Streamlit dashboard that allows an analyst to run a full scan, review identity metrics, inspect high-risk accounts, and understand why each identity was flagged.

---

## Why I Built This

Organizations frequently manage Active Directory and AWS IAM as separate environments even though both can expose the business to identity-based attacks.

I built this project to create one risk-analysis workflow for privileged users, stale accounts, weak password settings, long-lived cloud identities, and excessive permissions. The goal was not simply to list accounts, but to explain which identities deserved attention and why.

---

## Technologies Used

- Microsoft Active Directory
- AWS IAM
- Python
- ldap3
- boto3
- Streamlit
- OpenAI API
- Tailscale
- JSON
- Risk-scoring logic
- Least-privilege principles

---

## Architecture

```text
Active Directory
      │ LDAP
      ▼
Human Identity Agent
      │
      ├──────────────┐
      │              │
AWS IAM              │
      │ boto3        │
      ▼              │
Non-Human Identity Agent
      │              │
      └──────┬───────┘
             ▼
      Correlation Agent
             ▼
       Risk Scoring Agent
             ▼
    AI Investigation Agent
             ▼
     AI Remediation Agent
             ▼
     Streamlit Dashboard
```

The Active Directory lab ran locally, while the agents and dashboard ran on AWS EC2. Tailscale provided private connectivity between the two environments.

---

## Engineering Journey

### Step 1 — Design

I separated the platform into specialized agents so that identity collection, normalization, risk scoring, investigation, and remediation guidance could be developed and tested independently.

The risk score was deterministic, while AI was used to explain findings rather than invent them.

### Step 2 — Build

I created an Active Directory lab with users, groups, privileged accounts, and risky password settings. A read-only account collected identity data through LDAP.

The AWS agent used boto3 to enumerate IAM users, roles, policies, access keys, and administrative permissions. The results were normalized into a common structure.

### Step 3 — Secure

The Active Directory reader was restricted to read-only access. AWS permissions were limited to the actions required for inventory and assessment.

Secrets were stored outside the public repository, and Tailscale provided a private connection instead of exposing LDAP directly to the internet.

### Step 4 — Test

I created test conditions that included Domain Admin membership, Password Never Expires, disabled accounts, long-lived IAM users, administrative policies, and weak service-account configurations.

I ran each agent independently before testing the full pipeline.

### Step 5 — Validate

I verified that every finding included the identity, score, severity, reasons, and remediation guidance. I also confirmed that the AI reports stayed grounded in the deterministic risk findings.

The final results were displayed in Streamlit with identity metrics, severity distributions, and detailed investigation reports.

---

## Challenges & Troubleshooting

### Hybrid LDAP Connectivity

The AWS-hosted application initially could not reach the local domain controller. I validated Tailscale routing, firewall rules, LDAP ports, and service-account permissions until the connection succeeded.

### Different Identity Models

Active Directory and AWS IAM use different attributes and privilege models. I created a normalized structure without pretending both systems were identical.

### AI Hallucination Risk

Unstructured prompts produced recommendations that were too general. I improved the prompts by supplying the exact identity attributes, risk reasons, score, and known limitations.

---

## Results

- Active Directory users and groups were collected through LDAP.
- AWS IAM users, roles, policies, and access keys were inventoried.
- Privileged and weakly configured identities were identified.
- Every finding received a score, severity, reasons, and recommendation.
- AI-generated investigation and remediation reports were produced.
- Results were presented through a centralized Streamlit dashboard.

---

## Lessons Learned

Identity risk depends on context. A privileged account with a non-expiring password is more dangerous than a disabled user, and a long-lived IAM user with administrative access requires urgent attention.

The project also showed that AI is most useful after reliable data collection and deterministic analysis are already in place.

---

## Project Gallery

Use the strongest images from the project asset folder in this order:

1. Architecture diagram
2. Active Directory lab
3. AWS IAM identities
4. Agent execution
5. Risk findings
6. AI investigation report
7. Streamlit dashboard


---

## Video Demonstration

Add the project YouTube video or playlist link here.

---

## Author

**Stewart Nyamutswa**  
Cybersecurity | SOC Operations | Cloud Security | Incident Response
