# Wazuh–Shuffle–TheHive–Cortex Incident Response Lab — Project Summary

## Problem


SOC analysts often copy alert details manually between SIEM, case-management, and threat-intelligence platforms. This introduces delay, inconsistency, and missing context during investigations.


## Solution


This project demonstrates an end-to-end security-alert pipeline in which Wazuh alerts are sent to Shuffle, transformed into TheHive alerts, promoted into investigation cases, and enriched through Cortex analyzers.


## Workflow


1. Wazuh detects endpoint or authentication activity.
2. Shuffle receives the alert payload.
3. Shuffle maps the Wazuh fields into a TheHive-compatible alert.
4. TheHive stores the alert with title, severity, source, tags, and observables.
5. The analyst promotes validated alerts into cases.
6. Cortex analyzes observables.
7. The analyst documents conclusions and response actions.


## Results

Add the final measured outcomes and lessons learned after implementation.
