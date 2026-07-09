# Implementation notes

## Environment

The lab was built in a local virtualized environment using Windows and Linux components.

The main implementation components were:

- Windows endpoint for telemetry generation.
- Wazuh for SIEM-style monitoring and rule-based alerting.
- n8n for automation workflow orchestration.
- VirusTotal API for hash enrichment.
- Jira for incident ticket creation.
- Atomic Red Team for controlled validation.

## Implementation flow

### 1. SIEM setup

Wazuh was configured to collect endpoint telemetry and generate alerts based on rule matches. This gave the lab a central alerting layer.

### 2. Webhook integration

n8n was configured with a webhook endpoint to receive alert payloads from Wazuh.

### 3. JSON normalization

A normalization step was added to extract the most important fields from the incoming alert. This reduced the alert into a consistent triage object used by later workflow steps.

### 4. Severity routing

A severity gate was used to determine whether an alert should immediately create a Jira ticket or continue through enrichment logic.

### 5. Hash extraction and enrichment

When a file hash was available, the workflow queried VirusTotal and used the malicious count as enrichment context.

### 6. Ticket generation

Alerts that met escalation criteria were converted into Jira tickets with relevant context for analysts.

## Earlier workflow engine limitation

During the project, an earlier workflow prototype encountered request-volume limitations. The design was migrated to n8n to provide more flexibility for local hosting, webhook handling, branching logic, and API integrations.

## Operational value

The main value of the implementation is not only that alerts become tickets. The stronger value is that analysts receive alerts with context already attached:

- What host generated the alert?
- What rule fired?
- What severity was assigned?
- Was a file hash present?
- Did threat intelligence produce a malicious result?
- Why was the ticket created?

That context makes triage faster and more repeatable.
