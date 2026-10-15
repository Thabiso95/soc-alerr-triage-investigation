SOC Alert Triage and Investigation Report

1. Case Information

- Case ID: SOC-2026-002
- Incident Type: Suspicious sign-in and potential account compromise
- Environment: Simulated Microsoft Entra ID / Microsoft Sentinel investigation
- Investigation Status: Open — awaiting further evidence
- Initial Severity: Medium — provisional
- Data Classification: Synthetic training data

2. Alert Summary

A simulated security alert identifies unusual sign-in activity involving a fictional employee account. The activity includes an unfamiliar source IP address and a subsequent attempt to access a cloud resource.

The available information is insufficient to confirm that the account has been compromised. The analyst must correlate sign-in events, review authentication outcomes, establish the sequence of activity and determine whether escalation is justified.

3. Investigation Objectives

1. Validate the alert using the available event records.
2. Establish a timeline of suspicious activity.
3. Determine whether authentication succeeded.
4. Assess whether the activity is consistent with account compromise or a legitimate user action.
5. Identify evidence gaps and potential false-positive explanations.
6. Recommend proportionate containment and follow-up actions.

4. Evidence to Review

- Sign-in timestamps and authentication outcomes
- Source IP addresses and available location context
- User and application identifiers
- Authentication failure patterns
- Subsequent successful sign-ins
- Access to cloud resources after authentication
- Relevant identity risk signals, where available

5. Initial Assessment

The alert is a lead for investigation, not proof of compromise. An unfamiliar IP address alone does not establish malicious activity.

Severity must be reassessed as evidence becomes available. A confirmed unauthorized successful sign-in, suspicious resource access or other corroborating evidence may justify escalation.

6. Recommended Analyst Actions

1. Validate the alert details and confirm the affected account.
2. Correlate authentication events by account, source IP and time.
3. Review the sign-in context and available identity risk indicators.
4. Check for suspicious activity following any successful authentication.
5. Preserve relevant event records and document the investigation timeline.
6. Escalate to the appropriate incident-response team if evidence supports compromise.
7. Consider account containment and credential reset only in accordance with the organization's response procedures and the assessed risk.

7. Current Conclusion

No confirmed compromise can be stated at this stage. The case remains open pending review of the synthetic evidence dataset.

8. Limitations

This is a portfolio simulation using fictional identities and synthetic security telemetry. No real tenant, employee account or production security incident is involved. The investigation findings must not be represented as results from a live Microsoft Sentinel environment.