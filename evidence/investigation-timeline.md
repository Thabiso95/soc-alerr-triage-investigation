Investigation Timeline — SOC-2026-002

Case Context

This timeline is based entirely on synthetic sign-in events created for training. All timestamps are UTC.

Time (UTC)| Event| Initial Interpretation
08:00| Alex Morgan signs in successfully from 198.51.100.24| Baseline activity; not enough information to establish the user's normal behaviour
08:12| Failed sign-in from 203.0.113.77| Possible credential error or unauthorized attempt
08:13| Second failed sign-in from the same IP| Repeated authentication failure
08:14| Third failed sign-in from the same IP| Repeated attempts warrant closer review
08:15| Fourth failed sign-in from the same IP| Pattern is consistent with repeated password guessing, but intent is unconfirmed
08:16| Fifth failed sign-in from the same IP| Five consecutive failures increase concern
08:18| Successful sign-in from 203.0.113.77| Significant event: success follows five failures from the same source within six minutes
08:21| Successful SharePoint Online sign-in from the same source| Cloud access follows the successful authentication; confirm whether this represents separate authentication or related session activity
08:24| Successful Exchange Online sign-in from the same source| Further activity warrants review; do not assume separate log entries prove separate compromises
08:30| Jamie Lee signs in successfully from 198.51.100.42| Separate user and source; no direct evidence linking this event to the alert

Key Findings

1. Five failed sign-ins for Alex Morgan originated from the same source IP over a short period.
2. A successful sign-in followed from that same IP two minutes after the last recorded failure.
3. Successful cloud application events followed within six minutes of the successful sign-in.
4. The synthetic dataset does not establish the source's real-world identity, location, reputation or intent.
5. The records do not independently prove that the successful sign-in was unauthorized.

Working Hypothesis

The sequence is consistent with possible password guessing followed by successful authentication. Unauthorized account access is a credible hypothesis requiring investigation, but it is not yet a confirmed compromise.

Evidence Gaps

- Whether multifactor authentication was required and successfully completed
- Whether the sign-in was associated with a known device or session
- Whether the user recognizes the activity
- Whether identity risk detections were generated
- Whether SharePoint or Exchange activity involved unusual operations, downloads or mailbox-rule changes
- Whether the source IP was associated with a VPN, proxy or legitimate corporate network
- Whether additional sign-in or audit records corroborate the sequence

Recommended Next Actions

1. Validate the original sign-in records and authentication details.
2. Correlate activity with identity and cloud audit logs.
3. Contact the account owner through an approved channel to validate the activity.
4. Escalate to incident response if unauthorized access is substantiated.
5. Apply containment measures proportionately if the assessed risk justifies them.
6. Preserve relevant evidence and record all investigation decisions.

Provisional Disposition

Status: Suspicious activity requiring further investigation.

Severity: Medium, provisional. Increase severity if corroborating evidence indicates unauthorized access, sensitive data exposure or continued malicious activity.

Confidence: Moderate that the authentication pattern is suspicious; insufficient evidence to confirm account compromise.

Scope Limitation

This is a simulated investigation. No live Microsoft Entra ID tenant or Microsoft Sentinel workspace was queried.