# Lessons learned

## 1. Automation should reduce noise, not hide evidence

The workflow filters low-value events, but it should not permanently discard evidence in a production environment. A better production design would store suppressed events for later hunting or correlation.

## 2. JSON normalization is critical

Raw SIEM alerts contain nested fields and tool-specific naming. A normalization layer makes downstream logic easier to maintain and reduces the chance of broken branches when alert structures change.

## 3. API limits affect architecture

Threat-intelligence enrichment is useful, but external API limits can become a bottleneck. A mature design should include caching, rate-limit handling, retry queues, and fallback logic.

## 4. Severity alone is not enough

A high SIEM severity is useful, but severity should eventually be combined with other signals such as asset criticality, user context, reputation, prevalence, and historical activity.

## 5. Tool selection changes under real constraints

The workflow moved away from an earlier prototype once request-volume and scalability limitations became clear. This reinforced a practical engineering lesson: architecture decisions should adapt when real constraints appear.

## 6. Ticket quality matters

Creating tickets is easy. Creating useful tickets is harder.

A good security ticket should include:

- Short alert summary
- Hostname
- User context
- Rule name and ID
- Severity
- File path or process name
- Hash value when available
- Threat-intelligence result
- Recommended analyst action

## 7. Lab projects should document trade-offs

A recruiter or technical interviewer is more likely to be impressed by documented trade-offs than by a perfect-looking project with no limitations.

This project intentionally documents limitations such as false positives, API dependency, scalability, and privacy controls because those are the issues that matter in real security operations.
