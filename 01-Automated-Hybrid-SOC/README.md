# Automated Hybrid SOC Incident Detection and Response Platform

> **Professional Banner**  
> **Detect → Automate → Investigate → Enrich → Respond**

---

## Project Summary

This project demonstrates a complete hybrid SOC workflow built across AWS and a local VirtualBox lab. Wazuh collects security telemetry from Windows and Linux endpoints, Shuffle automates alert delivery, TheHive manages investigations, and Cortex enriches supported observables.

The platform was designed to show what happens after a security event is detected. Instead of stopping at a SIEM alert, the workflow moves the event into a structured case where an analyst can review evidence, document findings, perform response actions, and close the incident.

---

## Why I Built This

Many SOC labs focus only on generating alerts. I wanted to understand the full incident lifecycle: how an alert is detected, transferred between platforms, enriched, investigated, and converted into an actionable case.

The project also gave me practical experience integrating tools that represent different SOC functions rather than treating one product as the entire security operation.

---

## Technologies Used

- Wazuh
- Shuffle SOAR
- TheHive
- Cortex
- AWS EC2
- Ubuntu Linux
- Windows
- Kali Linux
- VirtualBox
- Webhooks and REST APIs
- JSON
- MITRE ATT&CK

---

## Architecture

```text
Kali Linux
    │
    │ Controlled Attack
    ▼
Windows / Ubuntu Endpoints
    │
    │ Security Telemetry
    ▼
Wazuh Manager
    │
    │ Webhook Alert
    ▼
Shuffle SOAR
    │
    │ Structured Alert
    ▼
TheHive
    │
    │ Case + Observables
    ▼
Cortex
    │
    │ Enrichment Results
    ▼
SOC Analyst Investigation and Response
```

The local VirtualBox environment generated attack activity, while AWS-hosted security platforms collected, processed, and organized the resulting evidence.

---

## Engineering Journey

### Step 1 — Design

I designed the lab as a hybrid SOC environment. Kali Linux acted as the attacker, Windows and Ubuntu systems acted as monitored endpoints, and AWS hosted the central security platforms.

The workflow was designed around five functions: endpoint visibility, detection, automation, case management, and enrichment.

### Step 2 — Build

I deployed Wazuh agents to the monitored systems and connected them to the Wazuh manager. I then configured Shuffle to receive Wazuh alerts through a webhook and map the important JSON fields into TheHive.

TheHive was configured for alert and case management, while Cortex was connected for observable analysis.

### Step 3 — Secure

Credentials and API keys were kept outside public documentation. Access between services was restricted to the required ports, and attack simulations were performed only inside the authorized lab.

A human-review step remained in place before promoting alerts into investigation cases.

### Step 4 — Test

I generated controlled security events, including SSH authentication failures, successful SSH access, file-integrity changes, suspicious Windows authentication activity, and privilege-related events.

I verified that Wazuh detected the events, Shuffle received the payloads, and TheHive created structured alerts.

### Step 5 — Validate

I validated the complete flow by promoting confirmed alerts into TheHive cases, reviewing the event timeline, extracting observables, running supported Cortex analyzers, and documenting containment and remediation actions.

---

## Challenges & Troubleshooting

### Invalid JSON Sent to TheHive

TheHive initially rejected some Shuffle requests because required fields were missing or incorrectly formatted. I corrected the JSON mapping and ensured fields such as `sourceRef` were unique.

### Service Dependencies

TheHive and Cortex required supporting database and search services. I troubleshot storage usage, container health, hostnames, and startup order before the environment became stable.

### Private-IP Enrichment

Public reputation services could not provide useful intelligence for private VirtualBox addresses. This taught me to distinguish between a broken analyzer and a successful analyzer with no meaningful public data.

---

## Results

- Windows and Linux security events were centralized in Wazuh.
- Wazuh alerts were forwarded automatically through Shuffle.
- TheHive alerts were created with structured fields and context.
- Confirmed alerts were promoted into investigation cases.
- Supported observables were analyzed through Cortex.
- Incident timelines and analyst actions were documented.
- Repetitive manual alert transfer was reduced.

---

## Lessons Learned

The main lesson was that a SOC is a workflow, not a single tool. Detection, automation, investigation, enrichment, and response each serve a different purpose.

Automation improved speed and consistency, but analyst judgment remained necessary for validation, containment, remediation, and closure.

---

## Project Gallery

Use the strongest images from the project asset folder in this order:

1. Architecture diagram
2. Wazuh alert
3. Shuffle workflow
4. TheHive alert
5. Promoted investigation case
6. Cortex result
7. Final incident timeline


---

## Video Demonstration

Add the project YouTube video or playlist link here.

---

## Author

**Stewart Nyamutswa**  
Cybersecurity | SOC Operations | Cloud Security | Incident Response
