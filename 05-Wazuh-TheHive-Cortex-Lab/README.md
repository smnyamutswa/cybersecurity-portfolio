# Wazuh–Shuffle–TheHive–Cortex Incident Response Lab

> **Automated Alert Creation, Observable Analysis, and Case Investigation**

[![Status](https://img.shields.io/badge/status-portfolio--ready-success)]()
[![Security](https://img.shields.io/badge/focus-cybersecurity-blue)]()
[![Author](https://img.shields.io/badge/author-Stewart%20Nyamutswa-lightgrey)]()

## Video Demonstration

🎥 **Project Video:** [Add video link here](VIDEO_LINK_HERE)

## Project Overview


This project demonstrates an end-to-end security-alert pipeline in which Wazuh alerts are sent to Shuffle, transformed into TheHive alerts, promoted into investigation cases, and enriched through Cortex analyzers.


## Business Problem


SOC analysts often copy alert details manually between SIEM, case-management, and threat-intelligence platforms. This introduces delay, inconsistency, and missing context during investigations.


## Architecture


```text
Wazuh Alert
    │
    ▼
Shuffle Webhook
    │
    ▼
TheHive Alert
    │
    ▼
Promote to Case
    │
    ▼
Cortex Analyzer
    │
    ▼
Investigation and Response
```


> Add the final architecture diagram to `architecture/architecture-diagram.png`.

## Workflow


1. Wazuh detects endpoint or authentication activity.
2. Shuffle receives the alert payload.
3. Shuffle maps the Wazuh fields into a TheHive-compatible alert.
4. TheHive stores the alert with title, severity, source, tags, and observables.
5. The analyst promotes validated alerts into cases.
6. Cortex analyzes observables.
7. The analyst documents conclusions and response actions.


## Key Features


- Wazuh-to-Shuffle webhook integration
- Automated TheHive alert creation
- Structured alert field mapping
- Alert-to-case promotion
- Cortex observable analysis
- Incident investigation tasks
- Case timeline and response documentation


## Attack or Test Scenarios


- File-integrity monitoring alert
- SSH authentication failure
- Windows authentication activity
- Suspicious IP observable analysis
- Hash analysis


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


Wazuh, Shuffle, TheHive, Cortex, webhook integration, JSON mapping, threat intelligence, case management, incident response, security automation.


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
