# Defect Reports

## Purpose

This directory contains defect reports identified during manual testing of the Relay application.

Defect reports document observed deviations from defined requirements or contracts, supported by execution results and relevant evidence. Each report provides traceability to the related requirement, test case, execution record, and supporting evidence where applicable.

A failed test assertion does not automatically establish an application defect. Defects are reported only when the available requirement or contract supports the expected behavior and sufficient evidence supports the observed deviation.

## Defect Report Index

Confirmed defects are documented by functional area.

| Functional Area | Defect Report                            | Defects Recorded |
| --------------- | ---------------------------------------- | ---------------: |
| Authentication  | [authentication.md](./authentication.md) |                2 |
| Authorization   | None documented                          |                0 |
| Conversations   | None documented                          |                0 |
| Messaging       | None documented                          |                0 |
| User Experience | None documented                          |                0 |
| **Total**       |                                          |            **2** |

The index reflects the defect reports currently documented in this directory. A functional area with no documented defects is not necessarily defect-free; it means that no defect report is currently recorded for that area in this directory. Update the index when defect reports are added, removed, or reorganized.

## Defect Identification

Each defect is assigned a unique identifier using the following format:

`BUG-NNN`

Examples:

- `BUG-001`
- `BUG-002`

Defect IDs are unique across the entire portfolio and must not restart for each functional area.

Each defect report should include, where applicable:

- Defect ID and title
- Related test case and requirement
- Preconditions and reproduction steps
- Expected result
- Actual result
- Supporting evidence
- Severity and priority
- Current status
- Related execution record
- Notes, limitations, and verification gaps

## Defect Reporting Principles

- Base expected behavior on documented requirements, contracts, or explicit developer confirmation.
- Describe actual behavior using observations supported by execution or evidence.
- Do not infer an internal implementation failure from UI observations alone.
- Distinguish defect severity from priority.
- Preserve traceability between requirements, test cases, execution records, evidence, and defect reports.
- Update defect status and related records only when supported by actual actions or new evidence.
- Record verification activities only when they have actually been performed and are within the agreed portfolio scope.
- Retesting after a fix and regression testing after a fix are excluded from this portfolio. Keep open defects documented transparently in the final test summary.

## Defect Severity

Severity describes the impact of a confirmed defect on application functionality, users, data, or security. It is assessed separately from Priority, which describes the urgency of addressing the defect.

This portfolio uses the following severity levels:

| Severity | Definition                                                                                                                                    |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Critical | The defect causes a serious security compromise, unauthorized access to important data, or a critical failure that makes the system unusable. |
| High     | The defect significantly blocks core functionality or an important user workflow, without meeting the Critical criteria.                      |
| Medium   | The defect disrupts a specific feature or workflow, but its impact is limited and core functionality remains usable.                          |
| Low      | The defect has a minor impact on usability, presentation, or non-critical details without disrupting core functionality.                      |

Severity must be assigned based on the demonstrated impact and available evidence. The severity of a defect must not be inferred solely from the risk level of the affected feature.

These levels are the classification scheme adopted for this self-directed QA portfolio and are not claimed to be Relay's official production severity policy.

## How to Use This Directory

1. Identify an unexpected result during test execution.
2. Compare the observed result against the applicable requirement or contract.
3. Determine whether the evidence supports a confirmed defect or whether further clarification or investigation is needed.
4. Create or update the defect report when justified.
5. Link the defect report from the related execution record.
6. Record verification activities only when they have actually been performed and are within the agreed portfolio scope.
7. Update this index to reflect the documented defect reports.

## Related Documentation

- [Project Overview](../README.md)

### Product Documentation

- [Product & QA Scope](../docs/01-product-scope.md)
- [Requirements](../docs/02-requirements.md)
- [Risk Assessment](../docs/03-risk-assestment.md)
- [Product Documentation Index](../docs/README.md)

### Test Design

- [Test Scenarios](../test-design/scenarios.md)
- [Test Case Index](../test-design/test-cases.md)
- [Test Design Index](../test-design/README.md)

### Test Execution

- [Execution Index](../execution/README.md)
- [Authentication Execution Record](../execution/authentication.md)
- [Exploratory Session Notes](../execution/exploratory-session-notes.md)
