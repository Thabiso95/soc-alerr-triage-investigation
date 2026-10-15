Investigation Logic — Validation Plan

Purpose

This document defines repeatable checks for the synthetic sign-in investigation in case SOC-2026-002.

The tests evaluate the expected behaviour of the investigation logic. Results must be recorded only after the corresponding test has actually been performed.

Test Environment

- Dataset: "evidence/signin-events.csv"
- Dataset type: Synthetic training data
- Expected source: Documentation-only IP addresses
- Live Microsoft Sentinel execution: Not performed
- Automated test execution: Pending

Test Cases

Test ID| Scenario| Expected Result
T01| Five failed sign-ins followed by success from the same IP and account within 10 minutes| Correlation should identify the suspicious sequence
T02| Fewer than three failed sign-ins followed by success| Should not meet the intended three-failure investigation threshold
T03| Five failed sign-ins without a subsequent success| The failed-sign-in correlation query should not return a failure-to-success sequence
T04| Failed sign-ins from one IP followed by success from a different IP| The same-IP correlation should not match the events
T05| Successful sign-in with no preceding failures| Should not match the failure-to-success correlation
T06| Repeated or duplicate event records| Results should be checked for inflated counts or duplicate findings

Validation Procedure

1. Review the synthetic dataset and confirm the timestamps, account names, source IP addresses and authentication outcomes.
2. Check each test case against the intended correlation rules.
3. Record the observed result and whether it matches the expected result.
4. Investigate mismatches before changing the query or test expectation.
5. Separately validate the KQL syntax and table schema in a suitable Microsoft Sentinel workspace before operational use.

Results Register

Test ID| Observed Result| Status| Notes
T01| Pending| Not run| Same-account, same-IP failure-to-success sequence
T02| Pending| Not run| Below-threshold scenario
T03| Pending| Not run| No subsequent success
T04| Pending| Not run| Different source IP
T05| Pending| Not run| No preceding failures
T06| Pending| Not run| Duplicate-event handling

Acceptance Criteria

The investigation logic should identify the intended sequence without incorrectly correlating different users or source IP addresses. Duplicate records and join behaviour must be evaluated to understand their effect on counts.

A passing synthetic test does not establish that a KQL query executes successfully or performs accurately in a live Sentinel environment.

Current Status

Status: Validation plan documented; test execution pending.

No test is marked as passed until it has been performed and its result recorded.