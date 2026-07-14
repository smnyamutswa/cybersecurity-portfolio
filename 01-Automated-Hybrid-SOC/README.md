# Automated Hybrid SOC Incident Detection and Response Platform

> **Wazuh → Shuffle → TheHive → Cortex → Investigation and Response**

[![Status](https://img.shields.io/badge/Status-Completed-brightgreen)]() [![Type](https://img.shields.io/badge/Type-Cybersecurity%20Case%20Study-blue)]()

## Video Demonstration

🎥 **Watch the project walkthrough:** [Add video link here](VIDEO_LINK_HERE)

---

## Why I Built This

I built this project to understand what happens after a security tool generates an alert. A real SOC does not stop at detection. Alerts must be forwarded, organized, enriched, investigated, and closed with documented response actions. This project connects those stages into one workflow using Wazuh, Shuffle, TheHive, and Cortex.

## The Problem

Security analysts often spend too much time copying alert details between tools, creating cases manually, and gathering context before an investigation can begin. The goal was to reduce that manual work while keeping the analyst involved in the decisions that matter.

## Architecture

```text
Kali Linux → Windows / Ubuntu → Wazuh → Shuffle Webhook → TheHive Alert → Promote to Case → Cortex → Investigation and Response
```

## How the Project Works

I simulated SSH brute-force activity and privilege escalation from Kali Linux against Ubuntu. Wazuh detected the authentication activity, Shuffle mapped the alert into TheHive, and the analyst promoted the alert into an investigation case. Cortex analyzers were then run against available observables and the final case included the original alert, workflow evidence, timeline, and response actions.

## Key Capabilities

- Windows and Linux monitoring with Wazuh
- Webhook automation with Shuffle
- Automatic TheHive alert creation
- Alert-to-case promotion
- Cortex observable analysis
- Incident timeline reconstruction
- Structured response documentation

## Results

The workflow moved a security event from detection to investigation without requiring the analyst to rebuild the case manually in every tool. I also documented a real limitation: private NAT addresses do not produce useful public reputation results in threat-intelligence services.

## Skills Demonstrated

Wazuh, Shuffle, TheHive, Cortex, AWS EC2, VirtualBox, Linux authentication logs, incident response, SOAR, case management, MITRE ATT&CK.

## Project Gallery

<img src="./assets/image-01.png" alt="Project screenshot" width="850">

<img src="./assets/image-02.png" alt="Project screenshot" width="850">

<img src="./assets/image-03.png" alt="Project screenshot" width="850">

<img src="./assets/image-04.png" alt="Project screenshot" width="850">

<img src="./assets/image-05.png" alt="Project screenshot" width="850">

<img src="./assets/image-06.png" alt="Project screenshot" width="850">

<img src="./assets/image-07.png" alt="Project screenshot" width="850">

<img src="./assets/image-08.png" alt="Project screenshot" width="850">

<img src="./assets/image-09.png" alt="Project screenshot" width="850">

<img src="./assets/image-10.png" alt="Project screenshot" width="850">

<img src="./assets/image-11.png" alt="Project screenshot" width="850">

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
