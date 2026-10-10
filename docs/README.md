# Product Documentation

## Purpose

This directory contains the product and QA documentation used to define the scope, expected behavior, and risk priorities for testing Relay.

These documents provide the basis for test scenario design and help distinguish documented requirements from behavior that still requires clarification.

## Documents

| Document | Purpose |
|---|---|
| [Product & QA Scope](./01-product-scope.md) | Defines Relay's documented capabilities, QA objectives, in-scope and out-of-scope areas, assumptions, and limitations. |
| [Requirements](./02-requirements.md) | Organizes requirements for authentication, authorization, conversations, messaging, and user experience, and identifies areas requiring clarification. |
| [Risk Assessment](./03-risk-assestment.md) | Describes the risk assessment approach, risk register, risk-based testing strategy, and coverage considerations. |

## How These Documents Are Used

1. Review the product and QA scope to understand what is included in the current testing effort.
2. Use the requirements to identify expected behavior and maintain requirement traceability.
3. Use the risk assessment to prioritize test design and testing effort.
4. Derive test scenarios and test cases from the documented requirements and identified risks.

Requirements or behavior that are not sufficiently specified must not be treated as confirmed product expectations. Such gaps should be recorded for clarification or investigated without assuming a defect.

## Related Documentation

- [Project Overview](../README.md)

### Test Design

- [Test Scenario Design](../test-design/scenarios.md)
- [Test Case Design Index](../test-design/test-cases.md)
- [Test Design Index](../test-design/README.md)

### Test Execution

- [Execution Index](../execution/README.md)
- [Exploratory Session Notes](../execution/exploratory-session-notes.md)