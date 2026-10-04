# Relay — Risk Assessment

## 1. Purpose

This document identifies and prioritizes product risks that may affect the reliability, security, data integrity, and usability of Relay.

The risk assessment is used to guide test coverage and testing depth throughout the QA lifecycle.

Higher-risk areas will receive greater testing attention, including deeper negative testing, authorization checks, edge cases, and regression coverage where appropriate.

---

## 2. Risk Assessment Approach

Risk is assessed using two primary dimensions:

- **Impact** — the potential consequence if the behavior fails.
- **Likelihood** — the estimated possibility that the behavior may fail or produce an unintended result.

The overall risk level is determined using the following matrix:

| Impact \ Likelihood | Low    | Medium | High   |
| ------------------- | ------ | ------ | ------ |
| **Low**             | Low    | Low    | Medium |
| **Medium**          | Low    | Medium | High   |
| **High**            | Medium | High   | High   |

### Impact

| Level      | Definition                                                                                                                 |
| ---------- | -------------------------------------------------------------------------------------------------------------------------- |
| **Low**    | Failure has limited effect on usability or a non-critical user experience.                                                 |
| **Medium** | Failure significantly affects a feature or user workflow but does not compromise critical application behavior.            |
| **High**   | Failure can prevent core functionality, cause significant data or session issues, or affect important security boundaries. |

### Likelihood

| Level      | Definition                                                                           |
| ---------- | ------------------------------------------------------------------------------------ |
| **Low**    | Failure is considered less likely under normal usage.                                |
| **Medium** | Failure is reasonably possible, particularly under negative or edge-case conditions. |
| **High**   | Failure is considered plausible under normal or easily reproducible conditions.      |

---

## 3. Risk Register

| ID      | Risk Area           | Failure Scenario                                                                                                                     | Impact | Likelihood | Risk Level |
| ------- | ------------------- | ------------------------------------------------------------------------------------------------------------------------------------ | ------ | ---------- | ---------- |
| RSK-001 | Authorization       | A user can access or interact with a conversation for which they are not an authorized participant.                                  | High   | Medium     | High       |
| RSK-002 | Sender Identity     | A message is attributed to a user other than the authenticated sender.                                                               | High   | Medium     | High       |
| RSK-003 | Authentication      | Users are incorrectly authenticated, denied valid access, or allowed to access protected functionality without valid authentication. | High   | Medium     | High       |
| RSK-004 | Message Persistence | Messages are lost or unavailable after refresh or re-login.                                                                          | High   | Medium     | High       |
| RSK-005 | Conversation Access | A user cannot access an authorized conversation or is provided access to an incorrect conversation.                                  | High   | Medium     | High       |
| RSK-006 | Session / Logout    | Logout fails to correctly terminate the user's authenticated application state.                                                      | High   | Medium     | High       |
| RSK-007 | Input Validation    | Invalid or unexpected input is accepted, rejected incorrectly, or causes unintended application behavior.                            | Medium | Medium     | Medium     |
| RSK-008 | Message Ordering    | Messages or conversations appear in an incorrect order, causing misleading conversation history or previews.                         | Medium | Medium     | Medium     |
| RSK-009 | Error Handling      | Users do not receive appropriate feedback when an operation fails.                                                                   | Medium | Medium     | Medium     |
| RSK-010 | Responsive Behavior | Core functionality becomes difficult to use on smaller screens.                                                                      | Medium | Medium     | Medium     |
| RSK-011 | Empty States        | Users receive unclear or misleading information when no relevant data is available.                                                  | Low    | Medium     | Low        |
| RSK-012 | Theme Persistence   | The selected theme does not persist as documented.                                                                                   | Low    | Medium     | Low        |

---

## 4. Risk-Based Testing Strategy

The risk register will influence the depth and priority of testing.

### High-Risk Areas

High-risk areas receive the highest testing attention.

Testing may include:

- Positive scenarios
- Negative scenarios
- Boundary and edge cases where applicable
- Authorization checks
- Multi-user scenarios
- Session-state checks
- Persistence verification
- Regression coverage after defects are fixed

High-risk areas include:

- Authentication
- Authorization
- Sender identity
- Conversation access
- Message persistence
- Logout/session behavior

### Medium-Risk Areas

Medium-risk areas receive functional coverage and relevant negative or edge-case testing.

These include:

- Input validation
- Message ordering
- Error handling
- Responsive behavior

### Low-Risk Areas

Low-risk areas receive standard functional coverage appropriate to their potential impact.

These include:

- Empty states
- Theme persistence

---

# Relay — Risk Assessment

## 1. Purpose

This document identifies and prioritizes product risks that may affect the reliability, security, data integrity, and usability of Relay.

The risk assessment is used to guide test coverage and testing depth throughout the QA lifecycle.

Higher-risk areas will receive greater testing attention, including deeper negative testing, authorization checks, edge cases, and regression coverage where appropriate.

---

## 2. Risk Assessment Approach

Risk is assessed using two primary dimensions:

- **Impact** — the potential consequence if the behavior fails.
- **Likelihood** — the estimated possibility that the behavior may fail or produce an unintended result.

The overall risk level is determined using the following 3x3 risk matrix:

| Impact \ Likelihood | Low    | Medium | High   |
| ------------------- | ------ | ------ | ------ |
| **High**            | Medium | High   | High   |
| **Medium**          | Low    | Medium | High   |
| **Low**             | Low    | Low    | Medium |

### Impact

| Level      | Definition                                                                                                                 |
| ---------- | -------------------------------------------------------------------------------------------------------------------------- |
| **Low**    | Failure has limited effect on usability or a non-critical user experience.                                                 |
| **Medium** | Failure significantly affects a feature or user workflow but does not compromise critical application behavior.            |
| **High**   | Failure can prevent core functionality, cause significant data or session issues, or affect important security boundaries. |

### Likelihood

| Level      | Definition                                                                           |
| ---------- | ------------------------------------------------------------------------------------ |
| **Low**    | Failure is considered less likely under normal usage.                                |
| **Medium** | Failure is reasonably possible, particularly under negative or edge-case conditions. |
| **High**   | Failure is considered plausible under normal or easily reproducible conditions.      |

---

## 3. Risk Register

| ID      | Risk Area           | Failure Scenario                                                                                                                     | Impact | Likelihood | Risk Level |
| ------- | ------------------- | ------------------------------------------------------------------------------------------------------------------------------------ | ------ | ---------- | ---------- |
| RSK-001 | Authorization       | A user can access or interact with a conversation for which they are not an authorized participant.                                  | High   | Medium     | High       |
| RSK-002 | Sender Identity     | A message is attributed to a user other than the authenticated sender.                                                               | High   | Medium     | High       |
| RSK-003 | Authentication      | Users are incorrectly authenticated, denied valid access, or allowed to access protected functionality without valid authentication. | High   | Medium     | High       |
| RSK-004 | Message Persistence | Messages are lost or unavailable after refresh or re-login.                                                                          | High   | Medium     | High       |
| RSK-005 | Conversation Access | A user cannot access an authorized conversation or is provided access to an incorrect conversation.                                  | High   | Medium     | High       |
| RSK-006 | Session / Logout    | Logout fails to correctly terminate the user's authenticated application state.                                                      | High   | Medium     | High       |
| RSK-007 | Input Validation    | Invalid or unexpected input is accepted, rejected incorrectly, or causes unintended application behavior.                            | Medium | Medium     | Medium     |
| RSK-008 | Message Ordering    | Messages or conversations appear in an incorrect order, causing misleading conversation history or previews.                         | Medium | Medium     | Medium     |
| RSK-009 | Error Handling      | Users do not receive appropriate feedback when an operation fails.                                                                   | Medium | Medium     | Medium     |
| RSK-010 | Responsive Behavior | Core functionality becomes difficult to use on smaller screens.                                                                      | Medium | Medium     | Medium     |
| RSK-011 | Empty States        | Users receive unclear or misleading information when no relevant data is available.                                                  | Low    | Medium     | Low        |
| RSK-012 | Theme Persistence   | The selected theme does not persist as documented.                                                                                   | Low    | Medium     | Low        |

---

## 4. Risk-Based Testing Strategy

The risk register will influence the depth and priority of testing.

### High-Risk Areas

High-risk areas receive the highest testing attention.

Testing may include:

- Positive scenarios
- Negative scenarios
- Boundary and edge cases where applicable
- Authorization checks
- Multi-user scenarios
- Session-state checks
- Persistence verification
- Regression coverage after defects are fixed

High-risk areas include:

- Authentication
- Authorization
- Sender identity
- Conversation access
- Message persistence
- Logout/session behavior

### Medium-Risk Areas

Medium-risk areas receive functional coverage and relevant negative or edge-case testing.

These include:

- Input validation
- Message ordering
- Error handling
- Responsive behavior

### Low-Risk Areas

Low-risk areas receive standard functional coverage appropriate to their potential impact.

These include:

- Empty states
- Theme persistence

---

## 5. Risk-Based Test Coverage

The risk assessment will be used to determine test coverage depth rather than simply distributing an equal number of test cases across all features.

For example:

```text
Authorization
     ↓
High Risk
     ↓
Positive + Negative + Multi-user + Boundary/Edge
     ↓
High Regression Attention
```

Whereas a lower-risk feature may receive:

```text
Theme Persistence
     ↓
Low risk
     ↓
Core functional verification
     ↓
Limited regression depth
```

This approach prioritizes testing effort according to the potential consequences of failure.

---

## 6. Risk Assessment Limitations

The risk ratings in this document are initial QA assessments based on:

- Documented Relay functionality
- Identified requirement gaps
- Potential impact of failure
- The current application scope

Likelihood ratings are not based on production defect statistics or historical incident data.

Risk levels may be revised when additional information becomes available through:

- Requirement clarification
- Exploratory testing
- Manual test execution
- Defect discovery
- Technical investigation

The risk assessment therefore represents the current testing priority rather than a permanent classification of the product.
