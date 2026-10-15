SOC Alert Triage Decision Matrix

Case Reference

- Case ID: SOC-2026-002
- Alert Type: Repeated failed sign-ins followed by successful authentication
- Affected Account: alex.morgan@example.test
- Evidence Source: Synthetic sign-in events
- Current Disposition: Suspicious — investigation required

1. Triage Assessment

Assessment Area| Evidence| Analyst Decision
Repeated authentication failures| Five failures from one source IP within four minutes| Suspicious pattern; investigate possible password guessing
Subsequent authentication success| Successful sign-in from the same IP two minutes after the last failure| Raises concern that valid credentials may have been obtained
Subsequent cloud activity| SharePoint and Exchange events follow the successful sign-in| Review cloud audit logs to establish what actions occurred
Source reputation| No reputation intelligence supplied| Unknown; do not label the IP malicious without evidence
User legitimacy| No user confirmation or device baseline supplied| Unverified
Confirmed compromise| No independent confirmation of unauthorized access| Not established

2. Provisional Severity

Current severity: Medium

Rationale

The combination of repeated failures, a subsequent success from the same source and subsequent cloud activity warrants investigation. However, the dataset does not prove malicious intent, unauthorized access or data loss.

Severity should be increased if additional evidence demonstrates account takeover, sensitive data access, persistence or continued malicious activity. It may be reduced if the activity is verified as legitimate and no other indicators remain.

3. Confidence Assessment

- Confidence in suspicious authentication pattern: High, within the supplied synthetic records.
- Confidence that the account was compromised: Low to moderate; independent corroboration is absent.
- Confidence in source attribution or geographic origin: Low; no enrichment data is available.

Confidence in a suspicious pattern must not be confused with confidence that an incident is confirmed.

4. False-Positive and Alternative Explanations

Potential explanations to investigate include:

1. A user repeatedly entering an incorrect password before succeeding.
2. A legitimate user connecting through a VPN or shared network.
3. An authorized administrator or support process generating authentication attempts.
4. Related cloud application events representing activity within an existing session rather than separate authentication attempts.

These explanations are possibilities, not established facts. Validate them against identity, device, session and audit evidence.

5. Escalation Criteria

Escalate promptly according to organizational procedures if evidence indicates:

- The account owner denies the successful sign-in.
- Authentication details show unauthorized access or suspicious session behaviour.
- Cloud audit logs reveal unauthorized data access, downloads or mailbox-rule changes.
- Additional compromised accounts or ongoing malicious activity are identified.

If there is credible evidence of active compromise, follow the incident-response process for containment. Do not delay urgent containment solely to complete this document.

6. Evidence Required Before Closure

- Validated authentication and MFA results
- User and device context
- Correlated sign-in and audit events
- Relevant identity risk indicators
- Account-owner or administrator validation where appropriate
- Documented rationale for the final severity and disposition

7. Current Decision

Disposition: Keep the case open and investigate further.

Severity: Medium, provisional.

Compromise confirmed: No.

Next action: Validate the successful authentication and examine subsequent cloud audit activity.

8. Training Disclaimer

This decision matrix uses fictional identities and synthetic events. It demonstrates a triage methodology and does not represent a real Microsoft Sentinel alert or production incident.