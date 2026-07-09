# Jira ticket template

## Summary

`[Priority] Alert description - Hostname`

Example:

`[High] Executable file dropped in folder commonly used by malware - WIN-ENDPOINT-01`

## Description

```text
Alert summary:
- Hostname: WIN-ENDPOINT-01
- Severity: 15
- Rule ID: 92213
- Rule description: Executable file dropped in folder commonly used by malware
- Event ID: 11
- User: LAB\analyst
- Process: C:\Windows\System32\sdiagnhost.exe
- File path: C:\Users\Public\sample_payload.ps1
- SHA256: aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa

Threat intelligence:
- Source: VirusTotal
- Malicious detections: 1
- Suspicious detections: 0

Recommended analyst action:
1. Validate the process and file path.
2. Check whether the file exists on the endpoint.
3. Review parent process and command-line activity.
4. Confirm whether the hash appears on other endpoints.
5. Escalate if the file is confirmed malicious or execution occurred.
```

## Labels

- `siem`
- `soar`
- `wazuh`
- `automated-enrichment`
- `triage-required`
