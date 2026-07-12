# Hybrid Identity Risk Analyzer — Project Summary

## Problem


Organizations often lack a unified view of identity risk across Active Directory and cloud IAM. Excessive permissions, stale accounts, password-policy weaknesses, and long-lived access keys can create privilege-escalation paths that remain unnoticed.


## Solution


This project evaluates identity risk across on-premises Active Directory and AWS IAM. Python-based agents collect human and non-human identity data, correlate permissions and privilege relationships, calculate risk scores, and produce AI-generated investigation and remediation reports through a Streamlit dashboard.


## Workflow


1. Collect Active Directory users, groups, status, and password attributes.
2. Enumerate AWS IAM users, roles, policies, and access keys.
3. Normalize and correlate identities.
4. Calculate risk based on privilege, account age, policy exposure, and credential hygiene.
5. Generate investigation context and remediation recommendations.
6. Present findings through a centralized dashboard.


## Results

Add the final measured outcomes and lessons learned after implementation.
