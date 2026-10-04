# Relay — Product & QA Scope

## 1. Purpose

This document defines the product scope and QA scope for the Relay End-to-End Manual QA portfolio project.

The purpose of this scope is to establish what will be tested, what will remain outside the current testing scope, the available requirement sources, and the initial areas of product risk.

This document serves as the foundation for subsequent test design, execution, defect reporting, retesting, regression testing, and test summary activities.

---

## 2. System Under Test

**Application:** Relay  
**Application Type:** Full-stack 1-on-1 messaging web application  
**Testing Approach:** Manual QA  
**Project Type:** Self-directed QA portfolio project

Relay is a messaging application designed for simple team communication through 1-on-1 conversations.

The application provides authentication, protected chat access, conversation management, text messaging, message persistence, server-side authorization, and supporting user experience features.

---

## 3. Product Overview

The current Relay implementation includes the following documented capabilities:

### Authentication

- User registration
- User login
- User logout
- Authentication state management
- Protected access to chat functionality

### Conversations

- 1-on-1 conversations
- Conversation participant relationships
- Conversation list
- Conversation ordering based on latest message activity
- Counterpart information
- Latest message preview
- Timestamp information

### Messaging

- Send and receive text messages
- Persistent messages across refresh and re-login
- Automatic message scrolling
- Calendar date separators for message history

### Authorization

- Server-side authentication for protected operations
- Server-side conversation authorization
- Authorization based on the authenticated user's relationship with a conversation
- Authenticated user identity derived server-side
- Message sender derived from the authenticated user

### User Experience

- Light and dark mode
- Persistent theme preference
- Responsive desktop and mobile layout
- Clear empty states
- Clear error states

---

## 4. QA Objective

The primary objective of this portfolio is to demonstrate an end-to-end manual QA workflow against a realistic full-stack web application.

The QA workflow will cover:

```text
Requirement Analysis
        ↓
Risk Assessment
        ↓
Test Scenario Design
        ↓
Test Case Design
        ↓
Manual Test Execution
        ↓
Evidence Collection
        ↓
Defect Reporting
        ↓
Retest
        ↓
Regression Testing
        ↓
Test Summary
```

The testing activities will focus on functional behavior, authorization boundaries, data persistence, integration behavior, and important user experience flows.

---

## 5. In Scope

The following areas are included in the current testing scope:

### 5.1 Authentication

- User registration
- Login with valid credentials
- Login with invalid credentials
- Logout
- Protected access
- Authentication state behavior

### 5.2 Authorization

- Access to authorized conversations
- Rejection of unauthorized conversation access
- Server-side authorization behavior
- Authenticated user identity handling
- Message sender identity handling

### 5.3 Conversations

- 1-on-1 conversation access
- Conversation participant relationships
- Conversation creation and retrieval behavior
- Conversation list behavior
- Conversation ordering based on latest activity

### 5.4 Messaging

- Sending text messages
- Receiving/displaying messages
- Message persistence
- Message ordering
- Message history
- Message scrolling
- Date separators

### 5.5 User Experience

- Empty states
- Error states
- Light and dark mode
- Theme persistence
- Responsive desktop/mobile behavior

### 5.6 End-to-End Integration

Testing of critical user flows across application layers, including:

```text
UI
 ↓
Server-side API logic
 ↓
Authentication / Authorization
 ↓
Database operation
 ↓
Response
 ↓
UI state
```

The portfolio will primarily evaluate the observable behavior of the application rather than perform source-code review as the main testing activity.

---

## 6. Out of Scope

The following areas are outside the current scope:

- Performance testing
- Load and stress testing
- Formal penetration testing
- Comprehensive security assessment
- Automated testing
- CI/CD testing
- Production monitoring
- Infrastructure testing
- Full database integrity audit
- Detailed API contract testing as a primary test activity
- Native mobile application testing
- Broad cross-browser compatibility testing
- Source-code/unit-test review as the primary QA activity
- Realtime messaging

Realtime messaging is intentionally excluded from the current Relay implementation and is documented as outside the application's current scope.

---

## 7. Assumptions

The following assumptions will be treated as assumptions until they are supported by explicit requirements or verified through testing:

| ID | Assumption | Initial Status |
|---|---|---|
| ASM-001 | A user can register a new account. | Documented |
| ASM-002 | A registered user can authenticate using valid credentials. | Documented |
| ASM-003 | Relay supports 1-on-1 conversations. | Documented |
| ASM-004 | Messages persist across refresh and re-login. | Documented |
| ASM-005 | Conversation access is authorized server-side. | Documented |
| ASM-006 | Message sender identity is derived from the authenticated user. | Documented |

Documented behavior is not treated as QA-verified behavior until it has been tested.

---

## 8. Requirement Sources

The primary sources available for this portfolio are:

1. **Relay README / project documentation**
2. **The actual Relay application**
3. **Observable application behavior during manual execution**
4. **QA-generated requirement interpretations**, when explicitly identified as interpretation rather than original product requirements

The Relay README is treated as the primary source of documented product behavior for initial scope definition.

---

## 9. Requirement Gaps / Clarifications

The current documentation does not define all detailed behavioral rules required for exhaustive test design.

The following areas require clarification or explicit observation before assigning definitive expected results:

### Registration

- Required registration fields
- Field validation rules
- Password requirements
- Duplicate account behavior
- Invalid input handling

### Authentication

- Exact invalid credential behavior
- Session expiration behavior
- Behavior after session expiration
- Logout behavior when authentication state is already invalid

### Conversations

- Rules for creating a conversation
- Duplicate conversation handling
- Self-conversation behavior
- Exact behavior when accessing an invalid or non-existent conversation

### Messaging

- Empty or whitespace-only messages
- Maximum message length
- Message validation rules
- Message timestamp behavior
- Message ordering rules in edge cases

### User Experience

- Exact responsive breakpoints
- Exact empty-state messaging
- Exact error-state messaging
- Theme behavior under different navigation/session conditions

Where expected behavior is not defined by available documentation or observable product requirements, the QA verdict will not be assumed. Such cases will be marked for clarification or further investigation.

---

## 10. Initial Risk Areas

The following areas are identified as initial QA risk areas based on the documented product behavior and the impact of potential failures:

| Risk Area | Potential Impact | Initial Risk |
|---|---|---|
| Authentication | Users may be unable to securely access the application. | High |
| Authorization | Users may access conversations they are not authorized to access. | Critical |
| Sender Identity | Messages may be attributed to the wrong user. | Critical |
| Message Persistence | User messages may be lost or inconsistent across sessions. | High |
| Conversation Access | Users may access or interact with incorrect conversations. | High |
| Session / Logout | Authentication state may remain incorrectly active. | High |
| Message Ordering | Conversation history may become confusing or misleading. | Medium |
| Error Handling | Users may not receive appropriate feedback when operations fail. | Medium |
| Input Validation | Invalid or unexpected input may be accepted, rejected incorrectly, or cause unintended application behavior. | Medium |
| Empty States | Users may receive unclear or misleading UI states. | Low |
| Responsive Behavior | Core functionality may become difficult to use on smaller screens. | Medium |

These are initial risk assessments and will be refined as requirements, test scenarios, and execution evidence become available.