# AI-Powered SOC Investigation Engine

> **Splunk Detection → Context Enrichment → AI Investigation → ServiceNow Incident**

[![Status](https://img.shields.io/badge/Status-Completed-brightgreen)]() [![Type](https://img.shields.io/badge/Type-Cybersecurity%20Case%20Study-blue)]()

## Video Demonstration

🎥 **Watch the project walkthrough:** [Add video link here](VIDEO_LINK_HERE)

---

## Why I Built This

Modern SOC teams receive more alerts than analysts can investigate manually. I built this project to automate repetitive first-stage triage while keeping final decisions with the analyst.

## The Problem

Analysts often open several tools to answer basic questions about an alert: who is the user, who owns the asset, is the IP suspicious, and what technique is involved. Manual enrichment slows triage and creates inconsistent case notes.

## Architecture

```text
Ubuntu / Windows / Active Directory → Splunk → REST API → AI Investigation Engine → AD/CMDB/GeoIP/VT/AbuseIPDB → GPT Risk Assessment → ServiceNow
```

## How the Project Works

I developed detections before running the attacks. Scenarios included Ubuntu SSH brute force, Active Directory privilege escalation, and suspicious PowerShell execution. Splunk triggered detections, the engine retrieved alerts through the REST API, gathered context, and generated an executive summary, technical analysis, MITRE mapping, CIS Controls, risk score, and remediation. Medium- and high-risk alerts became ServiceNow incidents.

## Key Capabilities

- Splunk detection engineering
- REST API alert retrieval
- AD and CMDB enrichment
- GeoIP, VirusTotal, and AbuseIPDB
- AI investigation reports
- Risk scoring
- Automated ServiceNow incidents

## Results

The workflow automated detection through incident creation and produced consistent investigations with relevant context already attached. This reduced repetitive triage work and showed how AI can support analysts without replacing their investigation and response decisions.

## Skills Demonstrated

Splunk Enterprise, Splunk REST API, Python, FastAPI, OpenAI, Active Directory, Windows Events, Ubuntu, ServiceNow, VirusTotal, AbuseIPDB, GeoIP, CMDB, MITRE ATT&CK, CIS Controls.

## Project Gallery

_Screenshots coming soon._

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
