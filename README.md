SOC Alert Triage and Investigation

Portfolio Project | Security Operations | Microsoft Sentinel | KQL

Project Overview

This project demonstrates a structured SOC alert triage and investigation workflow using synthetic Microsoft Entra ID sign-in events.

The simulated case investigates repeated authentication failures followed by a successful sign-in and subsequent cloud application activity. The objective is to assess the available evidence, identify investigation gaps, assign provisional severity and recommend appropriate response actions.

Environment: Simulated investigation using synthetic training data
Case ID: SOC-2026-002
Current disposition: Suspicious activity requiring further investigation

Investigation Scenario

A fictional employee account experiences five failed sign-in attempts from one source IP, followed by a successful sign-in from the same source. Subsequent SharePoint Online and Exchange Online events warrant further review.

The sequence raises concern about possible unauthorized access. However, the supplied events alone do not prove account compromise or data exfiltration.

Investigation Workflow

1. Review the alert scenario and available evidence.
2. Reconstruct the authentication timeline.
3. Correlate failed and successful sign-in activity.
4. Investigate available identity audit events.
5. Assess severity, confidence and potential false positives.
6. Document the disposition and recommended next steps.

Repository Contents

File| Purpose
"incident-report.md"| Case overview, objectives and initial assessment
"evidence/signin-events.csv"| Synthetic sign-in event dataset
"evidence/investigation-timeline.md"| Chronological event analysis
"queries/suspicious-signin-correlation.kql"| KQL investigation query for failed sign-ins followed by success
"queries/post-signin-audit-investigation.kql"| KQL query for identity audit activity
"triage/triage-decision-matrix.md"| Severity, confidence and escalation rationale
"triage/incident-disposition.md"| Incident disposition report and closure requirements

Skills Demonstrated

- SOC alert triage and evidence-based prioritization
- Authentication event analysis
- KQL query development
- Investigation timeline reconstruction
- False-positive and alternative-explanation assessment
- Incident severity and confidence assessment
- Evidence-gap identification
- Incident documentation and escalation recommendations

Investigation Findings

The synthetic records contain five failed sign-ins for the same account and source IP, followed by a successful sign-in two minutes after the final failure. Subsequent cloud application events occur within the following six minutes.

This is a suspicious pattern that merits investigation. The available dataset does not establish whether the sign-in was unauthorized, whether sensitive data was accessed or whether the account was compromised.

Validation Evidence

The Python prototype validation tests (T01–T06) passed using synthetic sign-in event data.

Validation screenshot: "View Python validation results" (evidence/python-validation-results.jpg)

Validation Scope

- Dataset: Synthetic training data ("evidence/signin-events.csv").
- IP addresses: Documentation-only addresses.
- Python prototype tests: Passed.
- Live Microsoft Sentinel execution: Not yet performed.
- Live KQL query validation: Not yet performed.

The results demonstrate the expected behaviour of the Python prototype within the test environment. They do not constitute validation against a live Microsoft Sentinel workspace.

Limitations and Disclaimer

This is a training and portfolio simulation. All identities and event records are fictional. The source IP addresses use documentation-only ranges. No production tenant, live security alert or real incident was investigated.

This project does not claim to demonstrate a live Microsoft Sentinel deployment.

Project Status

Status: Documentation and query authoring completed; live-workspace validation remains outstanding.

Author

Cybersecurity portfolio project focused on developing practical SOC investigation, KQL and incident triage skills.
