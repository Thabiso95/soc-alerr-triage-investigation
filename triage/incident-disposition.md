Incident Disposition Report

Case Details

- Case ID: SOC-2026-002
- Alert Type: Suspicious sign-in activity
- Affected Account: alex.morgan@example.test
- Investigation Date: 14 October 2026
- Analyst: Portfolio simulation
- Environment: Synthetic training dataset
- Final Status: Pending further evidence

1. Executive Summary

Repeated authentication failures were followed by a successful sign-in from the same source IP. Additional successful cloud application events followed.

This sequence is consistent with possible unauthorized access. However, the available synthetic records do not independently establish malicious intent, account compromise or data exfiltration.

2. Evidence Summary

Evidence| Observation| Significance
Authentication failures| Five failures from one IP between 08:12 and 08:16 UTC| Repeated attempts warrant investigation
Successful authentication| Success at 08:18 UTC from the same IP| Possible successful use of valid credentials
Subsequent application events| SharePoint and Exchange events at 08:21 and 08:24 UTC| Further investigation of cloud activity is warranted
Independent validation| Not supplied| Compromise remains unconfirmed

3. Impact Assessment

- Confirmed affected accounts: None confirmed as compromised.
- Potentially affected account: Alex Morgan.
- Confirmed data exposure: Not established.
- Confirmed persistence or privilege escalation: Not established.
- Business impact: Unknown pending further investigation.

4. Response Actions

Completed in this simulation

- Reviewed the supplied synthetic sign-in events.
- Documented the investigation timeline.
- Identified suspicious authentication patterns.
- Recorded evidence gaps and alternative explanations.
- Drafted KQL queries for further investigation.

Recommended in a real environment

- Validate authentication and MFA details.
- Confirm whether the user recognizes the activity.
- Review identity, session and cloud audit records.
- Preserve relevant evidence.
- Escalate to incident response if unauthorized access is supported.
- Apply proportionate containment in accordance with organizational procedures.

5. Final Disposition

Decision: Keep the case open.

Severity: Medium, provisional.

Confidence: High that the supplied records contain a suspicious authentication sequence; insufficient evidence to confirm compromise.

Reason: A successful sign-in followed repeated failures from the same source, but independent verification and detailed post-authentication activity are unavailable.

6. Closure Requirements

Before closing this case in a real SOC, the analyst should:

1. Establish whether the successful sign-in was authorized.
2. Review available identity and cloud audit evidence.
3. Assess potential impact and whether containment is necessary.
4. Document the final decision and supporting evidence.
5. Record any remediation, owner and follow-up actions.

7. Lessons Learned

- Alerts are investigative leads, not proof of compromise.
- Correlation across time, identity and source is more useful than isolated events.
- Severity and confidence are related but distinct.
- Evidence gaps and alternative explanations should be documented explicitly.
- A defensible conclusion is more valuable than an unsupported claim of compromise.

8. Scope and Limitations

This is a portfolio exercise using fictional identities and synthetic telemetry. No live tenant was investigated, no production response actions were performed, and the KQL queries have not been validated against a live Microsoft Sentinel workspace.