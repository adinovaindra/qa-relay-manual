# Test Execution

## Overview

This directory contains formal test execution records for the Relay application, organized by functional area.

Each execution record documents the test case, execution result, expected and actual behavior, evidence references, and related defect information when applicable.

Formal execution results are recorded only for test cases that have actually been executed. Test results and defects are not assumed or fabricated.

## Execution Records

| Functional Area | Execution Record | Status |
|---|---|---|
| Authentication | [authentication.md](./authentication.md) | In Progress |
| Authorization | [authorization.md](./authorization.md) | Not Started |
| Conversations | [conversations.md](./conversations.md) | Not Started |
| Messaging | [messaging.md](./messaging.md) | Not Started |
| User Experience | [user-experience.md](./user-experience.md) | Not Started |

**Status note:** These statuses describe the progress of formal execution documentation, not the pass/fail status of every test case in each functional area.

## Exploratory Testing

Exploratory testing notes are maintained separately in [exploratory-session-notes.md](./exploratory-session-notes.md).

Exploratory findings are not automatically treated as formal test execution results or confirmed defects. Each finding must be evaluated against the available requirements and expected behavior.

## Execution Principles

- Record actual results based on observed application behavior.
- Preserve the distinction between expected results and actual results.
- Attach or reference evidence where available.
- Record deviations from the planned test procedure when applicable.
- Report a defect only when the available requirement or contract supports the violation.
- Mark behavior that lacks sufficient specification as requiring clarification.
- Record retest and regression results only when those activities have actually been performed.

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