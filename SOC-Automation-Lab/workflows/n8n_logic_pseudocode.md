# n8n workflow pseudocode

This file documents the workflow logic without exposing credentials, internal URLs or a raw n8n export.

```python
alert = receive_webhook_payload()

normalized = {
    "timestamp": alert.get("timestamp"),
    "severity": alert.get("rule", {}).get("level"),
    "rule_id": alert.get("rule", {}).get("id"),
    "description": alert.get("rule", {}).get("description"),
    "hostname": alert.get("agent", {}).get("name"),
    "event_type": alert.get("rule", {}).get("groups"),
    "username": extract_username(alert),
    "process": extract_process_image(alert),
    "file_path": extract_target_file(alert),
    "sha256": extract_sha256(alert),
}

if normalized["severity"] >= 10:
    create_jira_ticket(
        priority="High",
        summary=f"Critical alert: {normalized['description']}",
        body=build_ticket_body(normalized)
    )

elif normalized["sha256"]:
    vt_result = query_virustotal(normalized["sha256"])
    normalized["threat_intel_verdict"] = vt_result

    if vt_result["malicious"] > 0:
        create_jira_ticket(
            priority="Medium",
            summary=f"Malicious indicator detected: {normalized['description']}",
            body=build_ticket_body(normalized)
        )
    else:
        suppress_or_log(normalized)

else:
    suppress_or_log(normalized)
```

## Notes

- API keys should be stored in environment variables or a secrets manager.
- Workflow errors should be logged and reviewed.
- VirusTotal results should be cached in larger environments to reduce API usage.
- Ticket creation should include duplicate prevention in production.
```
