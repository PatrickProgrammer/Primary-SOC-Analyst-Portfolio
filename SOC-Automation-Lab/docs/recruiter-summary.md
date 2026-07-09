# Recruiter summary

## Project name

SIEM + SOAR Security Operations Automation Lab

## One-line summary

Built an end-to-end security operations lab that collects endpoint alerts with Wazuh, enriches indicators using VirusTotal, and automatically creates Jira tickets through an n8n automation workflow.

## Skills demonstrated

- SIEM monitoring
- Alert triage
- SOAR automation
- JSON normalization
- API integration
- Threat-intelligence enrichment
- Jira ticketing workflow
- Endpoint telemetry analysis
- Controlled adversary simulation
- Security documentation
- Risk and privacy awareness

## Resume bullet options

- Built a SIEM + SOAR lab integrating Wazuh, n8n, VirusTotal and Jira to automate alert enrichment and incident ticket creation.
- Developed n8n workflow logic to normalize Wazuh JSON alerts, route high-severity detections, enrich file hashes and generate Jira tickets.
- Validated detection and automation behavior using controlled Atomic Red Team simulations against Windows endpoint telemetry.
- Documented architecture, testing, limitations and future improvements for a security operations automation workflow.

## Interview explanation

A strong explanation:

> I built this project to understand how SIEM alerts can be converted into actionable SOC tickets. Wazuh generated alerts from endpoint telemetry, n8n received the alert through a webhook, then I normalized the JSON fields and applied decision logic. High-severity alerts went directly to Jira. Alerts with file hashes were enriched using VirusTotal before being escalated. The project taught me that the hardest part is not connecting tools together, but tuning the workflow so it reduces noise without hiding important evidence.

## What to emphasize in interviews

- You understand the full alert lifecycle.
- You built automation logic instead of only installing tools.
- You dealt with tool limitations and adapted the design.
- You understand false positives and workflow tuning.
- You can explain both the technical and operational value of the project.
