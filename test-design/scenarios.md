# Relay — Test Scenario Design

## 1. Purpose

This document defines the manual test scenarios derived from the documented requirements, identified requirement gaps, and risk assessment for Relay.

Test scenarios define the functional and behavioral areas that require verification before detailed test cases and execution activities are created.

The scenarios are intentionally kept at a higher level than individual test cases.

---

## 2. Scenario Design Approach

Test scenarios are derived from three primary inputs:

```text
Documented Requirements
        +
Risk Assessment
        +
Requirement Gaps
        ↓
Test Scenarios
```

The scenario design prioritizes high-risk functionality while maintaining coverage of important user experience and supporting behaviors.

Where a scenario is based on an unspecified behavior, the expected result will not be assumed until the behavior is clarified or observed.

---

## 3. Authentication Scenarios

### SCN-AUTH-001 — User Registration

Verify that a user can register a new account.

**Related Requirement:** REQ-AUTH-001  
**Risk Area:** Authentication  
**Risk Level:** High

Coverage considerations:

- Valid registration
- Required field behavior
- Invalid input behavior
- Duplicate account behavior
- Registration error handling

---

### SCN-AUTH-002 — Valid User Login

Verify that a registered user can authenticate using valid credentials.

**Related Requirement:** REQ-AUTH-002
**Risk Area:** Authentication  
**Risk Level:** High

Coverage considerations:

- Valid credentials
- Authentication state after successful login
- Access to protected functionality after login

---

### SCN-AUTH-003 — Invalid User Login

Verify that authentication does not succeed when invalid credentials are provided.

**Related Requirement:** REQ-AUTH-002  
**Risk Area:** Authentication  
**Risk Level:** High

Coverage considerations:

- Invalid password
- Invalid or unknown account
- Error handling
- Protected access after failed authentication

The exact expected error behavior requires clarification if it is not defined by available product documentation.

---

### SCN-AUTH-004 — User Logout

Verify that an authenticated user can log out of Relay.

**Related Requirement:** REQ-AUTH-003  
**Risk Area:** Session / Logout  
**Risk Level:** High

Coverage considerations:

- Logout from an authenticated session
- Authentication state after logout
- Access to protected functionality after logout

---

### SCN-AUTH-005 — Protected Access Without Authentication

Verify that protected chat functionality cannot be accessed without a valid authenticated session.

**Related Requirement:** REQ-AUTH-004, REQ-AUTH-005
**Risk Area:** Authentication  
**Risk Level:** High

Coverage considerations:

- Access while unauthenticated
- Access after logout
- Access using an invalid authentication state
- Server-side authentication state based on the authenticated user's token
- Client-side authentication state cannot bypass server-side access control

---

## 4. Authorization Scenarios

### SCN-AUTHZ-001 — Authorized Conversation Access

Verify that an authenticated participant can access a conversation they are authorized to access.

**Related Requirement:** REQ-AUTHZ-001, REQ-AUTHZ-002  
**Risk Area:** Authorization / Conversation Access  
**Risk Level:** High

Coverage considerations:

- Access by an authorized participant
- Access to an existing conversation
- Access after authentication
- Conversation content visible to the authorized participant

---

### SCN-AUTHZ-002 — Unauthorized Conversation Access

Verify that a user cannot access a conversation for which they are not an authorized participant.

**Related Requirement:** REQ-AUTHZ-002, REQ-AUTHZ-005
**Risk Area:** Authorization  
**Risk Level:** High

Coverage considerations:

- Direct access to another user's conversation
- Access through manipulated conversation identifiers
- UI-level versus server-side authorization behavior

---

### SCN-AUTHZ-003 — Authenticated Identity Handling

Verify that protected operations use the authenticated user's identity rather than relying on client-provided identity values.

**Related Requirement:** REQ-AUTHZ-003  
**Risk Area:** Sender Identity / Authorization  
**Risk Level:** High

Coverage considerations:

- Client-provided user identity
- Identity mismatch attempts
- Resulting authorization behavior

---

### SCN-AUTHZ-004 — Message Sender Identity

Verify that a message is attributed to the authenticated user who sends it.

**Related Requirement:** REQ-AUTHZ-004  
**Risk Area:** Sender Identity  
**Risk Level:** High

Coverage considerations:

- Normal message creation
- Attempted sender identity manipulation
- Displayed sender identity after message creation

---

## 5. Conversation Scenarios

### SCN-CONV-001 — One-on-One Conversation Access

Verify that Relay supports access to 1-on-1 conversations between participants.

**Related Requirement:** REQ-CONV-001  
**Risk Area:** Conversation Access  
**Risk Level:** High

Coverage considerations:

- Access by each conversation participant
- Conversation contains the expected counterpart
- Conversation content is limited to the intended participants
- Access to an existing 1-on-1 conversation

---

### SCN-CONV-002 — Conversation Creation and Retrieval

Verify the supported conversation creation and retrieval behavior.

**Related Requirement:** REQ-CONV-002  
**Risk Area:** Conversation Access  
**Risk Level:** High

Coverage considerations:

- Creating a conversation where supported
- Retrieving an existing conversation
- Behavior when the requested conversation already exists
- Invalid conversation references

Detailed creation rules require clarification where not specified by the available documentation.

---

### SCN-CONV-003 — Conversation List Information

Verify that the conversation list displays the documented conversation information.

**Related Requirement:** REQ-CONV-003, REQ-CONV-004, REQ-CONV-005  
**Risk Area:** Conversation List  
**Risk Level:** Medium

Coverage considerations:

- Counterpart name
- Latest message preview
- Timestamp

---

### SCN-CONV-004 — Conversation Ordering

Verify that conversations are ordered according to the latest message activity.

**Related Requirement:** REQ-CONV-006  
**Risk Area:** Message Ordering  
**Risk Level:** Medium

Coverage considerations:

- Ordering after sending a new message
- Ordering after activity in multiple conversations
- Conversation with no recent message activity
- Consistency between latest message and conversation position

---

## 6. Messaging Scenarios

### SCN-MSG-001 — Send Text Message

Verify that an authenticated participant can send a text message within an authorized conversation.

**Related Requirement:** REQ-MSG-001  
**Risk Area:** Messaging / Authorization  
**Risk Level:** High

Coverage considerations:

- Sending a valid text message
- Sending within an authorized conversation
- Message appears in the conversation after sending
- Sender identity is correctly associated with the message

---

### SCN-MSG-002 — Display Message History

Verify that messages are displayed within the conversation history.

**Related Requirement:** REQ-MSG-002  
**Risk Area:** Messaging  
**Risk Level:** High

Coverage considerations:

- Existing messages are displayed
- Messages belong to the selected conversation
- Message content is displayed correctly

---

### SCN-MSG-003 — Message Persistence

Verify that messages remain available after application refresh and re-login.

**Related Requirement:** REQ-MSG-003  
**Risk Area:** Message Persistence  
**Risk Level:** High

Coverage considerations:

- Persistence after page refresh
- Persistence after logout and re-login
- Persistence across an existing conversation
- Persisted message content remains unchanged
- Message remains associated with the correct conversation

---

### SCN-MSG-004 — Message Ordering

Verify that messages are displayed in the expected chronological order.

**Related Requirement:** REQ-MSG-002  
**Risk Area:** Message Ordering  
**Risk Level:** Medium

Coverage considerations:

- Chronological ordering of consecutive messages
- Ordering after page refresh
- Ordering after re-login
- Ordering when multiple messages are sent in sequence
- Ordering behavior around date boundaries

The exact ordering behavior for edge cases requires clarification where not defined by available documentation.

---

### SCN-MSG-005 — Automatic Message Scrolling

Verify that message history provides the documented automatic scrolling behavior.

**Related Requirement:** REQ-MSG-004  
**Risk Area:** User Experience  
**Risk Level:** Medium

Coverage considerations:

- Scroll behavior when opening a conversation
- Scroll behavior after sending a message
- Scroll position when viewing recent messages
- Behavior when conversation history contains many messages

---

### SCN-MSG-006 — Calendar Date Separators

Verify that message history displays calendar date separators.

**Related Requirement:** REQ-MSG-005  
**Risk Area:** User Experience  
**Risk Level:** Medium

Coverage considerations:

- Messages from the same calendar date
- Messages across different calendar dates
- Date separator placement
- Date separator consistency after refresh
- Date separator behavior when viewing message history

---

## 7. User Experience Scenarios

### SCN-UX-001 — Empty States

Verify that appropriate empty states are displayed when relevant application data is unavailable.

**Related Requirement:** REQ-UX-005  
**Risk Area:** Empty States  
**Risk Level:** Low

Coverage considerations:

- Empty conversation list
- Conversation with no messages
- Empty state visibility
- Empty state clarity
- Transition from empty state to populated state

The exact expected content of empty states requires clarification where not defined by available documentation.

---

### SCN-UX-002 — Error States

Verify that appropriate error states are displayed when relevant operations fail.

**Related Requirement:** REQ-UX-006  
**Risk Area:** Error Handling  
**Risk Level:** Medium

Coverage considerations:

- Error feedback when an operation fails
- Error message visibility
- Error message clarity
- Recovery after an error
- Error state does not expose inappropriate information

The exact expected error-state content requires clarification where not defined by available documentation.

---

### SCN-UX-003 — Light and Dark Mode

Verify that Relay provides the documented light and dark theme modes.

**Related Requirement:** REQ-UX-001, REQ-UX-002  
**Risk Area:** Theme  
**Risk Level:** Low

Coverage considerations:

- Switching from light mode to dark mode
- Switching from dark mode to light mode
- Visual consistency of core application areas
- Theme behavior across major application screens

---

### SCN-UX-004 — Theme Persistence

Verify that the selected theme preference persists as documented.

**Related Requirement:** REQ-UX-003  
**Risk Area:** Theme Persistence  
**Risk Level:** Low

Coverage considerations:

- Theme persistence after page refresh
- Theme persistence after navigation
- Theme persistence after logout and re-login
- Consistency between selected theme and displayed theme

---

### SCN-UX-005 — Responsive Layout

Verify that Relay remains usable across supported desktop and mobile screen sizes.

**Related Requirement:** REQ-UX-004  
**Risk Area:** Responsive Behavior  
**Risk Level:** Medium

Coverage considerations:

- Core functionality on desktop viewport
- Core functionality on mobile viewport
- Conversation list usability
- Message area usability
- Message input usability
- Layout behavior at supported viewport sizes

The exact supported breakpoints require clarification where not defined by available documentation.

---

## 8. Requirement-Gap Exploratory Scenarios

The following exploratory scenarios target behaviors identified as requirement gaps.

They are not treated as definitive requirement-based PASS/FAIL scenarios until expected behavior is established.

### SCN-EXP-001 — Duplicate Registration

Explore the behavior when attempting to register an account using an already registered account identifier.

**Related Requirement Gap:** Duplicate account behavior

Purpose:

- Observe actual application behavior.
- Determine whether duplicate registration is prevented.
- Identify the user feedback provided.
- Determine whether the behavior requires clarification or defect investigation.

---

### SCN-EXP-002 — Invalid Registration Input

Explore how Relay handles invalid or incomplete registration input.

**Related Requirement Gap:** Registration validation rules

Purpose:

- Identify validation behavior.
- Observe error feedback.
- Determine whether validation rules are consistent.

---

### SCN-EXP-003 — Invalid or Expired Session

Explore application behavior when the authentication state is no longer valid.

**Related Requirement Gap:** Session expiration behavior

Purpose:

- Observe protected resource behavior.
- Observe user-facing feedback.
- Determine how the application handles an invalid session.

---

### SCN-EXP-004 — Invalid Conversation Reference

Explore application behavior when a user attempts to access a conversation that does not exist or is not accessible.

**Related Requirement Gap:** Invalid or non-existent conversation behavior

Purpose:

- Observe authorization behavior.
- Observe error handling.
- Determine whether the application exposes inappropriate information.

---

### SCN-EXP-005 — Empty or Whitespace Message

Explore application behavior when attempting to send an empty or whitespace-only message.

**Related Requirement Gap:** Message validation rules

Purpose:

- Observe whether empty content is accepted or rejected.
- Observe validation feedback.
- Determine whether additional requirement clarification is needed.

---

### SCN-EXP-006 — Message Length Boundary

Explore application behavior to determine whether a message length boundary exists and how the application behaves near and beyond it.

**Related Requirement Gap:** Maximum message length

Purpose:

- Determine whether a message length limit exists.
- Observe behavior at the boundary.
- Observe behavior beyond the boundary.

---

## 9. Scenario Traceability

The scenarios are designed to maintain traceability between requirements, risks, and future test cases.

```text
Requirement
     ↓
Risk
     ↓
Test Scenario
     ↓
Test Case
     ↓
Execution
     ↓
Evidence
     ↓
Defect / Result
```

Exploratory scenarios may originate from requirement gaps or risk observations rather than a fully defined requirement.

Their observed behavior will be documented separately from requirement-based verification.

---

## 10. Scenario Coverage Summary

The current scenario set covers:

| Area                           | Scenario Count |
| ------------------------------ | -------------: |
| Authentication                 |              5 |
| Authorization                  |              4 |
| Conversations                  |              4 |
| Messaging                      |              6 |
| User Experience                |              5 |
| Exploratory / Requirement Gaps |              6 |
| **Total**                      |         **30** |

The scenario count is not intended to represent final test case count. Individual scenarios may produce multiple test cases covering positive, negative, boundary, and edge conditions.
