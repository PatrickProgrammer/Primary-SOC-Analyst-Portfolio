# Risk, privacy and limitations

## Privacy considerations

Security monitoring systems can collect sensitive endpoint data. A production implementation must define exactly what is collected, how long it is retained, who can access it, and how it is protected.

Recommended controls:

- Collect only security-relevant fields.
- Avoid sending unnecessary personal data to external services.
- Restrict access to SIEM dashboards and ticket queues.
- Store API keys in environment variables or a secrets manager.
- Redact sensitive fields before sharing screenshots or logs.
- Define retention policies for alerts and tickets.

## Third-party dependency risks

This workflow relies on external services such as VirusTotal and Jira. That creates operational risks:

- API outages
- Rate limits
- Authentication failures
- Changes in API response format
- External service compromise

Mitigations:

- Add retry and dead-letter queues.
- Cache enrichment results.
- Monitor API failures.
- Fail closed for high-priority alerts.
- Keep raw SIEM alerts available even if enrichment fails.

## Detection limitations

The workflow uses predefined severity and enrichment logic. This creates potential weaknesses:

- False positives if thresholds are too aggressive.
- False negatives if alerts are suppressed too early.
- Missed context if a hash is unavailable.
- Overreliance on a single enrichment source.

## Scalability limitations

The lab environment is suitable for demonstration and learning. A production environment would require stronger architecture:

- Message queue between Wazuh and automation engine.
- Horizontal scaling for event processing.
- Centralized secrets management.
- Monitoring for workflow failures.
- High availability for core services.
- Role-based access control.

## Security limitation

This repository does not include secrets, API keys, production logs, or real client data. All examples are sanitized.
