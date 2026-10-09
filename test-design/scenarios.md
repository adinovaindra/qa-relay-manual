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

Verify that message history groups messages by calendar date and displays the appropriate date separator according to the documented date display rules.

**Related Requirement:** REQ-MSG-005  
**Risk Area:** User Experience  
**Risk Level:** Medium

Coverage considerations:

- Messages sent on the current date
- Messages sent on the previous calendar date
- Messages sent before the previous calendar date
- Messages from the same calendar date
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

Verify that appropriate error states and validation feedback are displayed when relevant application operations fail or required input is missing.

**Related Requirement:** REQ-UX-006, REQ-AUTH-006  
**Risk Area:** Error Handling  
**Risk Level:** Medium

Coverage considerations:

- Validation feedback when a required authentication form field is left empty
- Error feedback when login fails due to invalid credentials
- Error feedback when registration fails
- Error message visibility
- Error message clarity
- Recovery after an error
- Error state does not expose inappropriate information

The required-field validation tooltip `Please fill out this field.` is confirmed by developer clarification for empty required authentication form fields. Exact expected behavior for other error conditions requires clarification where not defined by available requirements or developer clarification.

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

**SCN-EXP-001 — Invalid Registration Input**

**Exploration Objective**

Explore how Relay handles registration email inputs with different formats, observe client-side and application-level validation responses, and identify behaviors requiring clarification.

**Charter**

Investigate email-format validation during registration by trying variations of email input and observing the resulting behavior. Record the validation response, whether registration proceeds, and whether the account is successfully created. Identify differences between browser-level feedback and errors displayed by the application.

**Known Observations**

- An email ending in a trailing dot is rejected with a browser validation tooltip.
- Another email format produces `invalid request data` on the Relay page after Register is clicked.
- An email using the `@yaho.com` domain is accepted, and registration completes successfully.

**Requirement Gap**

The expected email-format validation rules and the intended handling of invalid email input have not been confirmed.

**Exit Criteria**

- Relevant input variations and actual responses are documented.
- Observable differences between validation responses are recorded.
- Behaviors without a confirmed expected result are marked for clarification rather than classified as defects.

---

**SCN-EXP-002 — Invalid or Expired Session**

**Exploration Objective**

Explore how Relay handles access to protected resources when the user's authentication state is no longer valid, and identify behaviors requiring clarification.

**Charter**

Investigate Relay's authentication behavior by observing the browser state after login and logout, then attempting to access a protected resource after logout. Record observable changes to the authentication cookie, navigation behavior, and user-facing feedback. Identify session-expiration behavior that requires further exploration.

**Known Observations**

- The `auth_token` cookie is present in the browser after login.
- The `auth_token` cookie is no longer present in the browser after logout.
- Navigating to `/chat` after logout results in an automatic redirect to `/login`.
- Reuse of a previously issued authentication token after logout has not been tested.

**Requirement Gap**

The expected behavior for expired sessions and invalid authentication states has not been fully confirmed. The extent to which logout invalidates a previously issued authentication token has not been verified.

**Exit Criteria**

- Observable authentication behavior during login, logout, and protected resource access is documented.
- Session-expiration behavior requiring further exploration is identified.
- Behaviors without a confirmed expected result are marked for clarification rather than classified as defects.

---

**SCN-EXP-003 — Invalid Conversation Reference**

**Exploration Objective**

Explore how Relay handles attempts to access conversations using invalid references or valid conversation references that are not accessible to the current user, and identify behaviors requiring clarification.

**Charter**

Investigate Relay's behavior when accessing a conversation through the `conversationId` query parameter. Try an invalid conversation ID, access a valid conversation URL using an account that is not involved in the conversation, and access the same URL using the correct account. Record the resulting page behavior, user-facing feedback, and differences between the observed outcomes. Identify behaviors that require further clarification.

**Known Observations**

- Accessing `/chat` with an invalid `conversationId` (`invalid-conversation-id`) results in an error page displaying `A server error occurred. Reload to try again.`
- Accessing a valid conversation URL while logged in with an account that is not involved in the conversation results in the same error page.
- Accessing the same valid conversation URL while logged in with the correct account allows the conversation to open successfully.
- The underlying cause of the observed error behavior has not been independently verified.

**Requirement Gap**

The expected behavior for invalid conversation references and attempts to access conversations that the current user is not authorized to access has not been fully confirmed. The intended user-facing error handling for these conditions also requires clarification.

**Exit Criteria**

- Observable behavior for invalid conversation references is documented.
- Behavior when accessing a valid conversation URL from different account contexts is documented.
- User-facing error messages and successful access behavior are recorded.
- Behaviors without a confirmed expected result are marked for clarification rather than classified as defects.

---

**SCN-EXP-004 — Empty or Whitespace Message**

**Exploration Objective**

Explore how Relay handles attempts to send empty or whitespace-only messages and identify behaviors requiring clarification.

**Charter**

Investigate message input validation by attempting to send a message with an empty input field and an input containing only whitespace. Observe the state of the Send button, whether the action can be triggered, and any validation feedback provided by the application. Record differences between the observed behaviors and identify any remaining requirement gaps.

**Known Observations**

- When the message input is empty, the Send button appears disabled and cannot be clicked.
- When the message input contains whitespace only, the Send button remains disabled and cannot be clicked.
- The cursor changes to a prohibited symbol when hovering over the disabled Send button, according to direct observation.
- No message submission or validation feedback was observed during these attempts.

**Requirement Gap**

The expected validation rules for empty and whitespace-only messages have not been formally confirmed. The observed UI behavior is documented, but server-side handling has not been independently verified.

**Exit Criteria**

- Observable behavior for empty and whitespace-only message inputs is documented.
- The Send button state and available user interaction are recorded for both conditions.
- Behaviors without a confirmed expected result are marked for clarification rather than classified as defects.

---

**SCN-EXP-005 — Message Length Boundary**

**Exploration Objective**

Explore whether Relay imposes a message length boundary, observe how the application handles long message inputs, and identify behaviors requiring clarification.

**Charter**

Investigate message length handling by entering messages of different lengths and observing the input field, Send button state, and submission behavior. Examine whether the UI exposes a character limit and whether a long message can be submitted and displayed successfully. Record the observed behavior and identify any remaining uncertainty regarding the maximum permitted message length.

**Known Observations**

- A short message (`Test Message 123`) can be entered, and the Send button is active.
- A message of approximately 100 characters can be entered, and the Send button is active.
- The textarea can accommodate approximately 10,000 words without visibly truncating the entered text.
- The Send button remains active when the textarea contains a very large amount of text.
- The inspected `textarea#message-input` element does not contain a `maxlength` attribute.
- A message containing exactly 1,000 characters, verified using Notepad++, was successfully submitted and displayed in the conversation.
- No explicit message length indicator or maximum-length guidance was observed in the UI.

**Requirement Gap**

The maximum permitted message length and the expected behavior when that limit is reached or exceeded have not been confirmed. The observations do not establish whether a limit is enforced during submission or by server-side validation.

**Exit Criteria**

- Observable input behavior for messages of different lengths is documented.
- The Send button state and submission result for a 1,000-character message are recorded.
- Any visible length indicators or input restrictions are documented.
- Behaviors without a confirmed expected result are marked for clarification rather than classified as defects.

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
| Exploratory / Requirement Gaps |              5 |
| **Total**                      |         **29** |

The scenario count is not intended to represent final test case count. Individual scenarios may produce multiple test cases covering positive, negative, boundary, and edge conditions.
