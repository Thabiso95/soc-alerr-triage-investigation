Investigation Logic — Validation Results

Purpose

This document records repeatable tests of the synthetic sign-in investigation logic for case SOC-2026-002.

The tests evaluate the Python prototype's ability to correlate failed and successful sign-in events and handle duplicate records. They do not constitute validation of the KQL queries in a live Microsoft Sentinel workspace.

Test Environment

- Dataset: "evidence/signin-events.csv"
- Test dataset: "test-results/test-signin-events.csv"
- Dataset type: Synthetic training data
- Source IP addresses: Documentation-only IP addresses
- Python prototype: Executed in Google Colab
- Live Microsoft Sentinel execution: Not performed
- KQL syntax and schema validation: Pending

Test Cases and Results

Test ID| Scenario| Expected Result| Observed Python Result| Status
T01| Five failed sign-ins followed by success from the same account and IP within 10 minutes| Detect the suspicious sequence| Alert generated before and after deduplication| PASS
T02| Fewer than three failed sign-ins followed by success| No alert at the three-failure threshold| No alert generated| PASS
T03| Five failed sign-ins without a subsequent success| No failure-to-success correlation alert| No alert generated| PASS
T04| Failed sign-ins from one IP followed by success from a different IP| No same-IP correlation alert| No alert generated| PASS
T05| Successful sign-in without preceding failures| No correlation alert| No alert generated| PASS
T06| Three identical failure records followed by success| Detect the raw duplicate-driven count, then suppress the false threshold result after deduplication| Alert generated before deduplication; no alert after deduplication| PASS

Validation Method

The Python prototype was executed against six synthetic test scenarios. The results were evaluated against the expected behaviour of the investigation logic.

The prototype compares failed and successful events for the same account and source IP within the configured correlation window. It applies a minimum threshold of three failed events and supports a deduplication mode for evaluating repeated records.

Findings

1. Failure-to-success correlation: T01 demonstrated the intended suspicious sequence and generated an alert.
2. Threshold handling: T02 did not generate an alert because it contained fewer than three failed events.
3. Sequence requirements: T03 and T05 did not generate alerts because the required failure-to-success sequence was absent.
4. Source IP matching: T04 did not generate an alert because the successful sign-in used a different source IP.
5. Duplicate-event handling: T06 demonstrated that duplicate records can inflate raw event counts. Deduplication prevented the repeated records from satisfying the threshold on their own.

Limitations

- The events are synthetic and do not represent a real organisation or tenant.
- The tests validate the Python prototype only.
- The KQL queries have not been executed or validated in a live Microsoft Sentinel workspace.
- Sentinel table schemas, field availability, query syntax, time-window behaviour and production performance remain unverified.
- These results do not establish that the Python prototype and KQL queries produce identical results in all circumstances.

Acceptance Criteria

The six Python scenarios produced the expected results according to the test logic, including the duplicate-event scenario.

This outcome is evidence of successful synthetic testing of the Python prototype. It is not evidence of live Sentinel validation, and it does not establish that the KQL queries are operationally ready.

Current Status

Python prototype: 6 of 6 synthetic test scenarios passed.

KQL validation in Microsoft Sentinel: Pending.

Overall project status: Synthetic Python validation completed; live KQL validation remains outstanding.