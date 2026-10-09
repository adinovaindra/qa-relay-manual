# Relay — Requirements

## 1. Purpose

This document defines the functional and behavioral requirements used as the basis for manual QA activities for Relay.

The requirements are derived primarily from the available Relay project documentation and are written in a form that can be traced to test scenarios, test cases, execution results, and defects.

Where the available documentation does not define sufficient behavioral detail, the requirement is explicitly identified as requiring clarification rather than being inferred.

---

## 2. Requirement Classification

Requirements are grouped into the following functional areas:

- Authentication
- Authorization
- Conversations
- Messaging
- User Experience

Requirement IDs use the following format:

```text
REQ-[AREA]-[NUMBER]
```

Example:

```text
REQ-AUTH-001
```

---

## 3. Authentication Requirements

| ID           | Requirement                                                                             | Source       | Status     |
| ------------ | --------------------------------------------------------------------------------------- | ------------ | ---------- |
| REQ-AUTH-001 | The application shall allow a user to register an account.                              | Relay README | Documented |
| REQ-AUTH-002 | The application shall allow a registered user to authenticate using valid credentials.  | Relay README | Documented |
| REQ-AUTH-003 | The application shall allow an authenticated user to log out.                           | Relay README | Documented |
| REQ-AUTH-004 | Protected chat functionality shall require an authenticated user.                       | Relay README | Documented |
| REQ-AUTH-005 | Authentication state shall be derived server-side from the user's authentication token. | Relay README | Documented |
| REQ-AUTH-006 | The application shall display the validation tooltip "Please fill out this field." when a required authentication form field is left empty. | Developer clarification | Developer-confirmed |

---

## 4. Authorization Requirements

| ID            | Requirement                                                                                                                             | Source       | Status     |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------ | ---------- |
| REQ-AUTHZ-001 | Conversation access shall be based on the authenticated user's relationship with the conversation.                                      | Relay README | Documented |
| REQ-AUTHZ-002 | A user shall only be allowed to access conversations for which the user is an authorized participant.                                   | Relay README | Documented |
| REQ-AUTHZ-003 | Client-provided user identity shall not be treated as the authoritative identity for authorization decisions.                           | Relay README | Documented |
| REQ-AUTHZ-004 | Message sender identity shall be derived from the authenticated user rather than accepted as authoritative input from the request body. | Relay README | Documented |
| REQ-AUTHZ-005 | Protected operations shall perform authentication and authorization on the server.                                                      | Relay README | Documented |

---

## 5. Conversation Requirements

| ID           | Requirement                                                                                                             | Source       | Status     |
| ------------ | ----------------------------------------------------------------------------------------------------------------------- | ------------ | ---------- |
| REQ-CONV-001 | The application shall support 1-on-1 conversations.                                                                     | Relay README | Documented |
| REQ-CONV-002 | The application shall allow users to retrieve or create conversations through the supported conversation functionality. | Relay README | Documented |
| REQ-CONV-003 | The conversation list shall display the conversation counterpart's name.                                                | Relay README | Documented |
| REQ-CONV-004 | The conversation list shall display a preview of the latest message.                                                    | Relay README | Documented |
| REQ-CONV-005 | The conversation list shall display timestamp information.                                                              | Relay README | Documented |
| REQ-CONV-006 | Conversations shall be ordered based on the latest message activity.                                                    | Relay README | Documented |

---

## 6. Messaging Requirements

| ID          | Requirement                                                                                            | Source                                 | Status     |
| ----------- | ------------------------------------------------------------------------------------------------------ | -------------------------------------- | ---------- |
| REQ-MSG-001 | The application shall allow users to send text messages within an authorized conversation.             | Relay README                           | Documented |
| REQ-MSG-002 | Messages shall be displayed within the conversation history.                                           | Relay README                           | Documented |
| REQ-MSG-003 | Messages shall persist across application refresh and re-login.                                        | Relay README                           | Documented |
| REQ-MSG-004 | Message history shall support automatic scrolling behavior.                                            | Relay README                           | Documented |
| REQ-MSG-005 | Message history shall display calendar date separators according to the documented date display rules. | Relay README / Developer clarification | Documented |

---

## 7. User Experience Requirements

| ID         | Requirement                                                                            | Source       | Status     |
| ---------- | -------------------------------------------------------------------------------------- | ------------ | ---------- |
| REQ-UX-001 | The application shall provide a light mode.                                            | Relay README | Documented |
| REQ-UX-002 | The application shall provide a dark mode.                                             | Relay README | Documented |
| REQ-UX-003 | The user's theme preference shall persist.                                             | Relay README | Documented |
| REQ-UX-004 | The application shall provide a responsive layout for desktop and mobile screen sizes. | Relay README | Documented |
| REQ-UX-005 | The application shall provide clear empty states where applicable.                     | Relay README | Documented |
| REQ-UX-006 | The application shall provide clear error states where applicable.                     | Relay README | Documented |

---

## 8. Requirements Requiring Clarification

The following behaviors are not sufficiently specified by the available documentation and therefore do not receive definitive expected behavior at this stage.

### Registration

- Field validation rules beyond required-field validation
- Password requirements
- Duplicate account behavior
- Invalid input handling

### Authentication

- Exact invalid credential behavior
- Session expiration behavior
- Behavior after session expiration
- Logout behavior when authentication state is already invalid

### Conversations

- Detailed conversation creation rules
- Duplicate conversation behavior
- Self-conversation behavior
- Behavior when accessing an invalid or non-existent conversation

### Messaging

- Empty or whitespace-only message behavior
- Maximum message length
- Message validation rules
- Detailed message timestamp behavior
- Message ordering behavior in edge cases

### User Experience

- Exact responsive breakpoints
- Exact empty-state content
- Exact error-state content
- Theme behavior across navigation and session transitions

These areas will be addressed through clarification, observable product behavior, or explicitly scoped QA interpretation where appropriate.

---

## 9. Requirement Traceability

Requirements will be traced through the QA lifecycle using the following relationship:

```text
Requirement
     ↓
Test Scenario
     ↓
Test Case
     ↓
Test Execution
     ↓
Evidence
     ↓
Defect
     ↓
Retest
     ↓
Regression
```

A requirement is considered QA-verified only when supported by actual test execution evidence.

A documented requirement does not automatically indicate that the implementation has passed QA verification.
