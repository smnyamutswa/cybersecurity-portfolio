# Hybrid Identity Risk Analyzer

> **Active Directory + AWS IAM + Agentic AI Risk Analysis**

[![Status](https://img.shields.io/badge/status-portfolio--ready-success)]()
[![Security](https://img.shields.io/badge/focus-cybersecurity-blue)]()
[![Author](https://img.shields.io/badge/author-Stewart%20Nyamutswa-lightgrey)]()

## Video Demonstration

🎥 **Project Video:** [Add video link here](VIDEO_LINK_HERE)

## Project Overview


This project evaluates identity risk across on-premises Active Directory and AWS IAM. Python-based agents collect human and non-human identity data, correlate permissions and privilege relationships, calculate risk scores, and produce AI-generated investigation and remediation reports through a Streamlit dashboard.


## Business Problem


Organizations often lack a unified view of identity risk across Active Directory and cloud IAM. Excessive permissions, stale accounts, password-policy weaknesses, and long-lived access keys can create privilege-escalation paths that remain unnoticed.


## Architecture


```text
Active Directory ─► Human Identity Agent ─┐
                                         ├─► Correlation Agent
AWS IAM ─────────► Non-Human Agent ───────┘
                                                  │
                                                  ▼
                                            Risk Scoring Agent
                                                  │
                                                  ▼
                                         AI Investigation Engine
                                                  │
                                                  ▼
                                      Streamlit Dashboard + Reports
```


> Add the final architecture diagram to `architecture/architecture-diagram.png`.

## Workflow


1. Collect Active Directory users, groups, status, and password attributes.
2. Enumerate AWS IAM users, roles, policies, and access keys.
3. Normalize and correlate identities.
4. Calculate risk based on privilege, account age, policy exposure, and credential hygiene.
5. Generate investigation context and remediation recommendations.
6. Present findings through a centralized dashboard.


## Key Features


- Hybrid identity inventory
- Privilege and excessive-permission detection
- Stale and risky account detection
- Human and non-human identity correlation
- Risk scoring and severity classification
- AI-generated investigation summaries
- AI-generated remediation guidance
- Streamlit visualization


## Attack or Test Scenarios


- Privileged AD accounts with passwords that never expire
- Excessive AWS AdministratorAccess
- Long-lived IAM users and access keys
- Disabled or stale accounts
- Service-account risk
- Cross-environment identity exposure


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


Active Directory, AWS IAM, identity security, Python, LDAP, boto3, Streamlit, OpenAI API, risk scoring, security automation, least privilege.


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
