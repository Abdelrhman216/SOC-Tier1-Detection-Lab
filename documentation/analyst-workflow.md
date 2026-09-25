# SOC Tier 1 Analyst Workflow

**Author:** Abdelrhman Ali Saleh

## 1. Alert Validation

Determine whether the alert represents expected activity, a false positive, or suspicious behavior.

## 2. Evidence Collection

Collect:

- Timestamp
- Source IP
- Destination IP
- Username
- Hostname
- Event ID
- Process / command line
- Related SIEM alerts

## 3. Investigation

Correlate available endpoint, authentication, process, and network telemetry.

## 4. Severity Assessment

Consider:

- Asset involved
- Attack type
- Evidence of successful compromise
- Privilege level
- Potential business impact

## 5. Response

Recommended Tier 1 actions include:

- Validate the event
- Identify affected assets
- Preserve evidence
- Escalate when required
- Apply approved containment procedures

## 6. Documentation

Record findings, evidence, impact, response, and lessons learned in an incident report.
