# User Experience — Test Execution

## Overview

This document records formal test execution results for the User Experience functional area of the Relay application.

Execution records reference the corresponding test cases and document observed behavior, verdicts, and supporting evidence.

Only test cases that have actually been executed are recorded as formal execution results.

## Execution Summary

| Metric                 |                                Count |
| ---------------------- | -----------------------------------: |
| Test Cases Executed    |                                    5 |
| Passed                 |                                    5 |
| Failed                 |                                    0 |
| Blocked                |                                    0 |
| Clarification Required |                                    0 |
| Not Run                | Not tracked in this execution record |

_Summary reflects the execution records documented in this file and must be updated as additional test cases are executed._

## Execution Records

### TC-UX-001-01 — Verify Empty Conversation List

**Test Case Reference:** [TC-UX-001-01](../test-design/test-cases/user-experience.md#tc-ux-001-01--verify-empty-conversation-list)

**Scenario Reference:** SCN-UX-001

**Requirement Reference:** REQ-UX-005

**Preconditions**

- Relay is accessible.
- A registered user account is available.
- The user has no conversations associated with their account.
- The user's valid credentials are available.

**Expected Result**

- The conversation list is displayed.
- The application provides an appropriate representation of the empty conversation list.
- The exact content and wording of the empty state are subject to clarification if not defined by the available documentation.

**Actual Result**

- Dave (`dave@example.com`) signed in using valid credentials.
- After successful sign-in, the application redirected to `/chat`.
- The conversation list was empty and displayed the text `No conversations yet`.
- The conversation panel displayed the following message:

  `Select a conversation`

  `Choose a conversation from the list or start a new chat to begin messaging.`

**Execution Result:** PASS

**Evidence**

- **Screenshot:** [TC-UX-001-01 - Empty Conversation List.png](../evidence/user-experience/TC-UX-001-01-empty-conversation-list.png)

**Defect Reference:** None identified during this execution.

**Execution Notes**

The observed text `No conversations yet` clearly communicates that the account has no conversations. This behavior is consistent with the general requirement in REQ-UX-005 to provide clear empty states where applicable.

The conversation panel also displayed a prompt asking the user to select a conversation or start a new chat. This was recorded as an additional observation because no conversation was selected.

The exact empty-state wording was not evaluated against a prescribed message because the available documentation does not define the required text. This execution verifies the observable UI representation of the empty conversation list; it does not independently verify the underlying account or conversation data in the backend.

### TC-UX-001-02 — Verify Empty Conversation Message History

**Test Case Reference:** [TC-UX-001-02](../test-design/test-cases/user-experience.md#tc-ux-001-02--verify-empty-conversation-message-history)

**Scenario Reference:** SCN-UX-001

**Requirement Reference:** REQ-UX-005

**Preconditions**

- Relay is accessible.
- User D - Dave (dave@example.com) and User E - Elon (elon@example.com) are registered users.
- An existing 1-on-1 conversation between User D and User E is available.
- The conversation contains no messages.
- User D is authorized to access the conversation.
- User D's valid credentials are available.

**Expected Result**

- The selected conversation panel is displayed.
- The application provides an appropriate representation of an empty message history.
- The empty state communicates that no messages are available and provides suitable guidance for starting the conversation.
- The exact empty-state wording is subject to clarification if not defined by the available documentation.

**Actual Result**

- Dave signed in using valid credentials.
- After successful sign-in, the application redirected to `/chat`.
- Dave selected the existing conversation with User E (Elon) from the conversation list.
- The conversation panel opened without displaying any chat messages.
- The conversation panel displayed the following text:

  `No messages yet`

  `Send a message to start the conversation.`

**Execution Result:** PASS

**Evidence**

- **Screenshot:** [TC-UX-001-02 - Empty Conversation Message History.png](../evidence/user-experience/TC-UX-001-02-empty-conversation-message-history.png)

**Defect Reference:** None identified during this execution.

**Execution Notes**

The observed empty state clearly communicates that the selected conversation contains no messages and provides guidance for starting the conversation. This behavior is consistent with the general empty-state objective described by SCN-UX-001 and REQ-UX-005.

The exact wording was recorded as observed and was not evaluated against a prescribed message because the available documentation does not define the required text. This execution verifies the visible UI representation of the empty message history; it does not independently verify the underlying message data in the backend.

### TC-UX-002-01 — Recover from a Failed Login Attempt

**Test Case Reference:** [TC-UX-002-01](../test-design/test-cases/user-experience.md#tc-ux-002-01--recover-from-a-failed-login-attempt)

**Scenario Reference:** SCN-UX-002, SCN-AUTH-002, SCN-AUTH-003

**Requirement Reference:** REQ-UX-006, REQ-AUTH-002

**Preconditions**

- Relay is accessible.
- A registered user account is available (dave@example.com).
- The tester is not authenticated.
- The registered user's valid credentials are known.

**Expected Result**

- The first login attempt does not authenticate the user.
- Error feedback is provided for the failed login attempt.
- The user can correct the password and submit the login form again.
- The second login attempt authenticates the user successfully.
- The protected chat functionality is accessible after successful authentication.
- The exact error message for the failed login attempt is not prescribed by the available requirements.

**Actual Result**

- The login page was opened.
- The email `dave@example.com` and invalid password `password124` were entered.
- After clicking **Sign in**, the application displayed the error message `Invalid email or password`.
- The user re-entered the credentials using the valid password `password123`.
- After clicking **Sign in**, the application successfully redirected the user to the `/chat` page.

**Execution Result:** PASS

**Evidence**

- **Screenshot:** [TC-UX-002-01 - Invalid Login Credentials.png](../evidence/user-experience/TC-UX-002-01-invalid-login-credentials.png)
- **Screenshot:** [TC-UX-002-01 - Invalid login Error Message.png](../evidence/user-experience/TC-UX-002-01-invalid-login-error-message.png)
- **Screenshot:** [TC-UX-002-01 - Valid Login Credentials.png](../evidence/user-experience/TC-UX-002-01-valid-login-credentials.png)
- **Screenshot:** [TC-UX-002-01 - Successful Login Redirect.png](../evidence/user-experience/TC-UX-002-01-successful-login-redirect.png)

**Defect Reference:** None identified during this execution.

**Execution Notes**

The application displayed a generic login error after the invalid password was submitted. The subsequent login attempt with valid credentials succeeded, demonstrating that the user could recover from the failed login attempt without being prevented from signing in.

The observed error message was recorded as displayed. This execution evaluates the failed-login recovery flow and successful subsequent login; it does not independently verify backend authentication or account-locking behavior.

### TC-UX-003-01 — Verify Light and Dark Mode

**Test Case Reference:** [TC-UX-003-01](../test-design/test-cases/user-experience.md#tc-ux-003-01--verify-light-and-dark-mode)

**Scenario Reference:** SCN-UX-003

**Requirement Reference:** REQ-UX-001, REQ-UX-002

**Preconditions**

- Relay is accessible.
- A registered user account is available (dave@example.com).
- The user's valid credentials are available.
- The user can access the main application screens.

**Expected Result**

- Light mode is available and can be selected.
- Dark mode is available and can be selected.
- The selected theme is applied to the observed core application areas.
- Switching from light mode to dark mode changes the displayed theme accordingly.
- Switching from dark mode to light mode restores the light theme.
- The selected theme remains visually consistent across the observed main application screens.

**Actual Result**

- On opening Relay, the Login page was displayed in Dark Mode.
- The user navigated to the Register page by clicking **Create One**, which redirected to `/register`.
- On the Register page:
  - Clicking **Light** changed the theme to Light Mode.
  - Clicking **Dark** changed the theme back to Dark Mode.
- The user navigated to the Login page by clicking **Sign in**, which redirected to `/login`.
- On the Login page:
  - Clicking **Light** changed the theme to Light Mode.
  - Clicking **Dark** changed the theme back to Dark Mode.
- The user signed in successfully using Dave's valid credentials and was redirected to `/chat`.
- On the Conversation List:
  - Clicking **Light** changed the theme to Light Mode, and the Conversation List appearance changed accordingly.
  - Clicking **Dark** changed the theme back to Dark Mode, and the Conversation List appearance changed accordingly.
- The user opened an existing conversation with Elon.
- On the Conversation Panel and Message Input:
  - Clicking **Light** changed the theme to Light Mode, and both areas changed accordingly.
  - Clicking **Dark** changed the theme back to Dark Mode, and both areas changed accordingly.
- All tested interactive controls functioned as expected.

**Execution Result:** PASS

**Evidence**

- **Screenshot:** [TC-UX-003-01 - Register Light Theme.png](../evidence/user-experience/TC-UX-003-01-register-light-theme.png)
- **Screenshot:** [TC-UX-003-01 - Register Dark Theme.png](../evidence/user-experience/TC-UX-003-01-register-dark-theme.png)
- **Screenshot:** [TC-UX-003-01 - Login Light Theme.png](../evidence/user-experience/TC-UX-003-01-login-light-theme.png)
- **Screenshot:** [TC-UX-003-01 - Login Dark Theme.png](../evidence/user-experience/TC-UX-003-01-login-dark-theme.png)
- **Screenshot:** [TC-UX-003-01 - Chat Focused On Conversation List Light Theme.png](../evidence/user-experience/TC-UX-003-01-chat-focused-on-conversation-list-light-theme.png)
- **Screenshot:** [TC-UX-003-01 - Chat Focused On Conversation List Dark Theme.png](../evidence/user-experience/TC-UX-003-01-chat-focused-on-conversation-list-dark-theme.png)
- **Screenshot:** [TC-UX-003-01 - Chat Focused On Conversation Panel Light Theme.png](../evidence/user-experience/TC-UX-003-01-chat-focused-on-conversation-panel-light-theme.png)
- **Screenshot:** [TC-UX-003-01 - Chat Focused On Conversation Panel Dark Theme.png](../evidence/user-experience/TC-UX-003-01-chat-focused-on-conversation-panel-dark-theme.png)

**Defect Reference:** None identified during this execution.

**Execution Notes**

Both Light Mode and Dark Mode were exercised on all five application areas: Register, Login, Conversation List, Conversation Panel, and Message Input.

The observed theme changes were consistent with the selected mode in each tested area. No interactive-control issues were observed during this execution.

This test verifies theme switching and the visible appearance of the tested application areas. Theme persistence after refresh, navigation, logout, and re-login remains covered separately by TC-UX-004-01 and TC-UX-004-02.

### TC-UX-004-01 — Verify Theme Persistence After Refresh

**Test Case Reference:** [TC-UX-004-01](../test-design/test-cases/user-experience.md#tc-ux-004-01--verify-theme-persistence-after-refresh)

**Scenario Reference:** SCN-UX-004

**Requirement Reference:** REQ-UX-003

**Preconditions**

- Relay is accessible.
- A registered user account is available (dave@example.com).
- The user's valid credentials are available.
- An existing conversation with User E (Elon) is available.
- The user can access the Register, Login, and main application screens.

**Expected Result**

- Light Mode remains selected and displayed after refresh on the Register page.
- Dark Mode remains selected and displayed after refresh on the Register page.
- Light Mode remains selected and displayed after refresh on the Login page.
- Dark Mode remains selected and displayed after refresh on the Login page.
- Light Mode remains selected and displayed after refresh on the main application interface.
- Dark Mode remains selected and displayed after refresh on the main application interface.
- The selected theme and displayed theme remain consistent across all tested application areas after refresh.

**Actual Result**

- The user opened Relay and navigated to the Register page by clicking **Create One**.
- On the Register page:
  - Clicking **Light** changed the theme to Light Mode.
  - Refreshing the page preserved Light Mode.
  - Clicking **Dark** changed the theme to Dark Mode.
  - Refreshing the page preserved Dark Mode.
- The user navigated to the Login page by clicking **Sign in**.
- On the Login page:
  - Clicking **Light** changed the theme to Light Mode.
  - Refreshing the page preserved Light Mode.
  - Clicking **Dark** changed the theme to Dark Mode.
  - Refreshing the page preserved Dark Mode.
- The user signed in successfully using Dave's valid credentials and was redirected to the chat page.
- The user selected the existing conversation with Elon from the Conversation List, displaying the Conversation List, Conversation Panel, and Message Input.
- On the chat page:
  - Clicking **Light** changed the theme to Light Mode across the observed areas.
  - Refreshing the page preserved Light Mode.
  - Clicking **Dark** changed the theme to Dark Mode across the observed areas.
  - Refreshing the page preserved Dark Mode.
- The selected theme remained visually consistent across the three observed chat areas after each refresh.

**Execution Result:** PASS

**Evidence**

- **Screen Recording:** [TC-UX-004-01 — Theme Persistence After Refresh Full Flow](https://github.com/user-attachments/assets/59853e9d-37e0-4c46-a4ff-74c584e14b9d)

**Defect Reference:** None identified during this execution.

**Execution Notes**

Both Light Mode and Dark Mode were tested on the Register page, Login page, and chat page. Each selected theme remained active after refreshing the page.

On the chat page, the theme remained visually consistent across the Conversation List, Conversation Panel, and Message Input after refresh.

The execution supports a PASS verdict for theme persistence after refresh in the tested application areas. Persistence across navigation and logout/re-login remains covered separately by TC-UX-004-02 and TC-UX-004-03.

The screen recording was identified as supporting evidence.
