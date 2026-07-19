# AI-Powered SOC Investigation Engine

> **Professional Banner**  
> **Detect → Enrich → Investigate → Score → Create Incident**

---

## Project Summary

The AI-Powered SOC Investigation Engine automates the repetitive first stage of SOC triage. It retrieves triggered detections from Splunk, enriches them with identity, asset, geolocation, reputation, and threat-intelligence context, generates an AI-assisted investigation report, calculates risk, and creates a ServiceNow incident for analyst review.

The project was validated with multiple attack scenarios, including SSH brute force and Active Directory privilege escalation.

---

## Why I Built This

SOC analysts often begin an investigation by opening several tools to answer the same questions: Who is the user? What asset is affected? Is the source IP suspicious? What technique does the event represent? How urgent is it?

That repetitive work delays response and can produce inconsistent case notes.

I built this engine to assemble the available context automatically while keeping the analyst responsible for validating the evidence and deciding how to respond.

---

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

---

## Architecture

```text
Ubuntu / Windows / Active Directory
             │
             │ Security Logs
             ▼
      Splunk Enterprise
             │
             │ REST API
             ▼
AI SOC Investigation Engine
   ├── Active Directory Enrichment
   ├── CMDB Asset Context
   ├── GeoIP
   ├── VirusTotal
   └── AbuseIPDB
             │
             ▼
AI Investigation + Risk Scoring
             │
             ▼
ServiceNow Incident
             │
             ▼
SOC Analyst Review and Response
```

The same investigation pipeline handled both Linux authentication events and Windows identity-security events.

---

## Engineering Journey

### Step 1 — Design

I designed the platform as a staged investigation workflow. Splunk remained responsible for detection, enrichment services supplied context, the AI layer explained the evidence, and ServiceNow provided structured incident tracking.

The analyst remained the final decision-maker.

### Step 2 — Build

I configured Splunk Universal Forwarders on Ubuntu and Windows systems, created detection searches, and built a Python service that retrieved triggered alerts through the Splunk REST API.

The engine normalized different alert types into a common structure and passed the results through enrichment, investigation, scoring, and ticket-creation stages.

### Step 3 — Secure

API keys and service credentials were stored outside the public repository. Access to Splunk and ServiceNow was limited to the required accounts and endpoints.

The platform treated unavailable enrichment data honestly instead of assuming that missing reputation results meant an indicator was safe.

### Step 4 — Test

I tested the workflow with:

- SSH brute-force activity from Kali Linux against Ubuntu
- Active Directory privileged-group membership changes
- Suspicious PowerShell activity
- Linux authentication failures
- Windows security events

I first confirmed the raw events, then verified the Splunk detections and downstream investigation pipeline.

### Step 5 — Validate

I confirmed that the engine retrieved the correct alert, enriched the event, generated a grounded investigation report, mapped relevant MITRE ATT&CK techniques and CIS Controls, calculated a risk score, and created a ServiceNow incident.

The project was documented through three videos: architecture, SSH attack, and Active Directory privilege escalation.

---

## Challenges & Troubleshooting

### Reliable Splunk Searches

The detection searches needed to identify malicious patterns without depending on one exact event. I tested the searches against generated telemetry and adjusted fields, thresholds, and time windows.

### Normalizing Different Alert Types

Linux SSH events and Windows Active Directory events contain different fields. I created a normalized alert structure so the downstream workflow could process both.

### Threat-Intelligence Limitations

Private lab IP addresses often have no public reputation data. The platform represented this as “no public intelligence available” rather than treating it as proof that the address was safe.

### Grounding the AI Report

The AI output had to remain connected to the actual event. I structured the input so the model received the detection, enrichment results, and known limitations before generating conclusions.

---

## Results

- Splunk detections triggered for multiple attack scenarios.
- Alerts were retrieved automatically through the REST API.
- Identity, asset, GeoIP, and threat-intelligence context was assembled.
- AI-generated reports included technical and business explanations.
- MITRE ATT&CK and CIS Controls were mapped to the event.
- Risk scores were calculated consistently.
- ServiceNow incidents were created for analyst review.
- Repetitive first-stage triage was reduced.

---

## Lessons Learned

AI can improve SOC speed and consistency, but it does not replace evidence collection or analyst judgment.

The quality of the final investigation depended on the quality of the detection, field normalization, and enrichment stages. The analyst remained responsible for validating the conclusion and deciding how to respond.

---

## Project Gallery

Use the strongest images from the project asset folder in this order:

1. Architecture diagram
2. Splunk detection
3. Raw attack telemetry
4. Enrichment output
5. AI investigation report
6. Risk score
7. ServiceNow incident
8. Final workflow evidence


---

## Video Demonstration

Add the project YouTube video or playlist link here.

---

## Author

**Stewart Nyamutswa**  
Cybersecurity | SOC Operations | Cloud Security | Incident Response
