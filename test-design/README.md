# Test Design

## Purpose

This directory contains the test scenarios and detailed manual test cases designed for the Relay End-to-End Manual QA portfolio project.

Test design translates documented requirements, identified risks, and explicitly noted requirement gaps into structured, traceable test coverage. Execution results are recorded separately from test design.

## Test Design Workflow

```text
Product Scope & Requirements
            ↓
      Risk Assessment
            ↓
     Test Scenarios
            ↓
       Test Cases
            ↓
     Test Execution
```

The workflow describes the intended relationship between artifacts. It does not imply that every test case has been executed.

## Documents

| Document | Purpose |
|---|---|
| [Test Scenario Design](./scenarios.md) | Defines high-level scenarios, links them to requirements and risk areas, and summarizes scenario traceability and coverage. |
| [Test Case Design Index](./test-cases.md) | Explains the test case design approach, test case fields, design methods, and links to the detailed test cases by functional area. |

## Test Case Repository

Detailed test cases are organized by functional area.

| Functional Area | File | Test Cases |
|---|---|---:|
| Authentication | [authentication.md](./test-cases/authentication.md) | 10 |
| Authorization | [authorization.md](./test-cases/authorization.md) | 2 |
| Conversations | [conversations.md](./test-cases/conversations.md) | 5 |
| Messaging | [messaging.md](./test-cases/messaging.md) | 6 |
| User Experience | [user-experience.md](./test-cases/user-experience.md) | 8 |
| **Total** | | **31** |

## Design Principles

- Maintain traceability between requirements, scenarios, and test cases where applicable.
- Use positive, negative, and boundary or edge testing where relevant.
- Consider risk level when prioritizing test coverage.
- Keep expected results grounded in documented requirements, contracts, or explicitly defined test objectives.
- Do not assume unspecified behavior; identify it as requiring clarification or exploratory investigation.
- Keep execution results, evidence references, and defect information separate from test case design.

## Related Documentation

- [Project Overview](../README.md)

### Product Documentation

- [Product & QA Scope](../docs/01-product-scope.md)
- [Requirements](../docs/02-requirements.md)
- [Risk Assessment](../docs/03-risk-assestment.md)
- [Product Documentation Index](../docs/README.md)

### Test Execution

- [Execution Index](../execution/README.md)
- [Exploratory Session Notes](../execution/exploratory-session-notes.md)