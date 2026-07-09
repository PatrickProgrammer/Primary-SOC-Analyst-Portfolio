# Future improvements

## Engineering improvements

- Add message queue support for more reliable event handling.
- Add duplicate-ticket prevention using event fingerprinting.
- Add enrichment caching to reduce API calls.
- Add retry logic and failed-workflow monitoring.
- Add structured logging for all automation decisions.
- Add automated tests for workflow branches.
- Add infrastructure-as-code for repeatable deployment.

## Detection improvements

- Add Sigma-style detection rule mapping.
- Add user and asset context to improve prioritization.
- Add file prevalence and first-seen logic.
- Add correlation across multiple events from the same host.
- Add suppression rules for known benign activity.
- Add alert confidence scoring.

## SOC workflow improvements

- Add analyst approval steps for high-risk automation.
- Add SLA labels in Jira based on severity.
- Add notification routing for critical alerts.
- Add dashboard metrics for ticket volume and false-positive trends.
- Add post-incident review templates.

## Microsoft security version

A future version could rebuild the same project using the Microsoft security ecosystem:

- Microsoft Defender for Endpoint for endpoint telemetry.
- Microsoft Sentinel for SIEM and analytics rules.
- Logic Apps for SOAR automation.
- Microsoft Graph API for identity and security context.
- Defender XDR incidents for cross-domain correlation.

This would make the project even more aligned with SOC roles that use Microsoft Sentinel and Defender XDR.
