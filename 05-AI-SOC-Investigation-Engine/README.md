# AI-Powered SOC Investigation Engine

> **Professional Banner**  
> **Turn a Splunk alert into an analyst-ready incident**

## Project Summary

This project automates the repetitive first stage of a SOC investigation.

The engine retrieves detections from Splunk, gathers identity and asset context, checks available geolocation and threat-intelligence sources, generates an AI-assisted investigation report, calculates a risk score, and creates a ServiceNow incident for analyst review.

I validated the workflow with several scenarios, including SSH brute-force activity and Active Directory privilege escalation.

## Why I Built This

A SOC analyst often opens several tools before they can answer basic questions about an alert:

- Who is the user?
- What system is affected?
- Is the source address known to be malicious?
- What attack technique does the event resemble?
- How urgent is the case?

That work is necessary, but much of it is repetitive. I built this engine to assemble the available evidence automatically so the analyst can spend more time evaluating the event and deciding how to respond.

## Technologies Used

- Splunk Enterprise
- Splunk Universal Forwarder
- Splunk REST API
- Python
- FastAPI
- OpenAI API
- Active Directory
- GeoIP
- VirusTotal
- AbuseIPDB
- CMDB data
- ServiceNow
- Windows Security Events
- Ubuntu
- Kali Linux
- MITRE ATT&CK
- CIS Controls

## Architecture

```text
Ubuntu, Windows, and Active Directory
                 │
                 │ Security logs
                 ▼
          Splunk Enterprise
                 │
                 │ REST API
                 ▼
     AI SOC Investigation Engine
       ├── Active Directory context
       ├── CMDB asset context
       ├── GeoIP
       ├── VirusTotal
       └── AbuseIPDB
                 │
                 ▼
       Investigation and risk score
                 │
                 ▼
          ServiceNow incident
                 │
                 ▼
        SOC analyst review and response
```

## Engineering Journey

### Step 1 — Design

I designed the platform so each tool had one clear responsibility.

Splunk handled detection. The enrichment stage collected context. The AI stage explained the evidence. ServiceNow tracked the incident. The analyst remained responsible for the final decision.

### Step 2 — Build

I configured Splunk Universal Forwarders on Ubuntu and Windows systems and created searches for the attack scenarios.

I then built a Python service that called the Splunk REST API, normalized different event types, enriched the alert, generated the report, calculated risk, and created a ServiceNow incident.

### Step 3 — Secure

API keys and service credentials were kept outside the public repository. The Splunk and ServiceNow accounts were limited to the actions required by the workflow.

The engine also treated missing intelligence honestly. No result from a reputation service was recorded as unavailable information, not proof that an indicator was safe.

### Step 4 — Test

I tested the workflow with:

- SSH brute-force attempts from Kali Linux
- Active Directory privileged-group changes
- Suspicious PowerShell activity
- Linux authentication failures
- Windows security events

For each test, I first confirmed the raw event, then the Splunk detection, and finally the complete investigation workflow.

### Step 5 — Validate

I confirmed that the engine retrieved the correct alert, gathered the available context, generated a report grounded in the evidence, mapped relevant MITRE ATT&CK techniques and CIS Controls, assigned a risk score, and opened a ServiceNow incident.

## Challenges & Troubleshooting

### Building useful Splunk detections

A search that matches one test event is easy to create. A useful detection needs the right fields, threshold, and time window. I adjusted the searches after reviewing the raw telemetry.

### Normalizing Linux and Windows events

SSH alerts and Active Directory events do not share the same fields. I created one normalized event format so that the downstream investigation stages could handle both.

### Limited threat-intelligence results

Private lab addresses usually have no public reputation history. The engine had to explain that limitation instead of overstating the available evidence.

### Keeping AI grounded

The AI report was only useful when it received the actual event, enrichment results, and known gaps. Structured input reduced generic or unsupported conclusions.

## Results

- Triggered Splunk detections for multiple attack scenarios
- Retrieved alerts automatically through the REST API
- Collected identity, asset, GeoIP, and threat-intelligence context
- Generated technical and business-focused investigation summaries
- Mapped relevant MITRE ATT&CK techniques and CIS Controls
- Assigned consistent risk scores
- Created ServiceNow incidents for analyst review
- Reduced repetitive first-stage triage work

## Lessons Learned

AI can make investigations faster, but it cannot replace reliable telemetry or analyst judgment.

The final report was only as good as the detection, event fields, and enrichment data that came before it. The analyst still needed to validate the conclusion and choose the response.

## Project Gallery

Screenshots and architecture diagrams will be added to the [`assets`](./assets/) folder.

<p align="center"><em>Images will be displayed here as medium-size, clickable previews.</em></p>
## Video Demonstration

Add the project demonstration link here.
