# Automated Hybrid SOC Incident Detection and Response Platform — Project Summary

## Problem


Security teams frequently face high alert volumes, manual case creation, inconsistent investigations, and delayed response. This project reduces repetitive analyst work by automating the transition from detection to structured incident handling.


## Solution


This project implements a hybrid Security Operations Center environment that connects AWS-hosted security platforms with a VirtualBox attack lab. Windows and Ubuntu endpoints generate security telemetry, Kali Linux simulates controlled attacks, Wazuh detects suspicious activity, Shuffle automates alert forwarding, TheHive manages alerts and cases, and Cortex enriches observables with threat intelligence.


## Workflow


1. Kali Linux generates a controlled attack against Windows or Ubuntu.
2. The endpoint Wazuh agent forwards telemetry to the AWS-hosted Wazuh manager.
3. Wazuh generates an alert based on detection rules.
4. Shuffle receives the alert through a webhook.
5. Shuffle creates a structured alert in TheHive.
6. The analyst promotes a confirmed alert into an investigation case.
7. Cortex analyzes available observables such as IP addresses, domains, URLs, or hashes.
8. The analyst documents findings and performs containment, remediation, and recovery.


## Results

Add the final measured outcomes and lessons learned after implementation.
