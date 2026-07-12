# Automated Hybrid SOC Incident Detection and Response Platform

> **Wazuh Alert → Shuffle Webhook → TheHive Alert → Promote to Case → Cortex Analysis → Investigation and Response**

[![Status](https://img.shields.io/badge/status-portfolio--ready-success)]()
[![Security](https://img.shields.io/badge/focus-cybersecurity-blue)]()
[![Author](https://img.shields.io/badge/author-Stewart%20Nyamutswa-lightgrey)]()

## Video Demonstration

🎥 **Project Video:** [Add video link here](VIDEO_LINK_HERE)

## Project Overview


This project implements a hybrid Security Operations Center environment that connects AWS-hosted security platforms with a VirtualBox attack lab. Windows and Ubuntu endpoints generate security telemetry, Kali Linux simulates controlled attacks, Wazuh detects suspicious activity, Shuffle automates alert forwarding, TheHive manages alerts and cases, and Cortex enriches observables with threat intelligence.


## Business Problem


Security teams frequently face high alert volumes, manual case creation, inconsistent investigations, and delayed response. This project reduces repetitive analyst work by automating the transition from detection to structured incident handling.


## Architecture


```text
VirtualBox Lab                          AWS / Cloud Security Stack

Kali Linux ──attacks──► Windows ─┐
                                 ├──► Wazuh Agent ─► Wazuh SIEM
Kali Linux ──attacks──► Ubuntu ──┘                       │
                                                        ▼
                                                 Shuffle Webhook
                                                        │
                                                        ▼
                                                  TheHive Alert
                                                        │
                                               Promote Alert to Case
                                                        │
                                                        ▼
                                                Cortex Analyzer
                                                        │
                                                        ▼
                                           Investigation + Response
```


> Add the final architecture diagram to `architecture/architecture-diagram.png`.

## Workflow


1. Kali Linux generates a controlled attack against Windows or Ubuntu.
2. The endpoint Wazuh agent forwards telemetry to the AWS-hosted Wazuh manager.
3. Wazuh generates an alert based on detection rules.
4. Shuffle receives the alert through a webhook.
5. Shuffle creates a structured alert in TheHive.
6. The analyst promotes a confirmed alert into an investigation case.
7. Cortex analyzes available observables such as IP addresses, domains, URLs, or hashes.
8. The analyst documents findings and performs containment, remediation, and recovery.


## Key Features


- Centralized Windows and Linux endpoint monitoring
- Automated alert forwarding with Shuffle
- TheHive alert and case management
- Cortex observable enrichment
- Controlled attack simulation
- MITRE ATT&CK mapping
- Incident timelines and response documentation
- MTTD and MTTR measurement


## Attack or Test Scenarios


- SSH brute-force attack
- Unauthorized authentication attempts
- Suspicious PowerShell activity
- Windows account manipulation
- Privilege escalation
- Credential compromise
- Lateral movement


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


SIEM, SOAR, incident response, alert triage, threat intelligence, Wazuh, Shuffle, TheHive, Cortex, AWS, Windows logging, Linux logging, VirtualBox, MITRE ATT&CK.


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
