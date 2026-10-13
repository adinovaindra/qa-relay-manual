# Messaging — Test Execution

## Overview

This document records formal test execution results for the Messaging functional area of the Relay application.

Execution records reference the corresponding test cases and document observed behavior, verdicts, and supporting evidence.

Only test cases that have actually been executed are recorded as formal execution results.

## Execution Summary

| Metric                 |                                Count |
| ---------------------- | -----------------------------------: |
| Test Cases Executed    |                                    7 |
| Passed                 |                                    7 |
| Failed                 |                                    0 |
| Blocked                |                                    0 |
| Clarification Required |                                    0 |
| Not Run                | Not tracked in this execution record |

_Summary reflects the execution records documented in this file and must be updated as additional test cases are executed._

## Execution Records

### TC-MSG-001-01 — Send a Valid Text Message

**Test Case Reference:** [TC-MSG-001-01](../test-design/test-cases/messaging.md#tc-msg-001-01--send-a-valid-text-message)

**Scenario Reference:** SCN-MSG-001

**Requirement Reference:** REQ-MSG-001

**Preconditions**

- Relay is accessible.
- User A and User B are registered users.
- An existing 1-on-1 conversation between User A and User B is available.
- User A is authorized to access the conversation.
- User A's valid credentials are available.

**Expected Result**

- The message is successfully sent within the authorized conversation.
- The sent message appears in the conversation.
- The displayed sender identity of the message corresponds to Alice.

**Actual Result**

- User A - Alice (`alice@example.com`) successfully signed in to the Relay application.
- The chat page was displayed after successful sign-in.
- Alice selected the existing conversation with User B - Bob (bob@example.com) from the conversation list.
- The conversation displayed an existing message from Bob at 12.04: `Yeah, i am good, Alice. Long time no see. Where do you live now?`
- Alice sent the message `I live in Yogyakarta, Bob. How about you? What do you do for now?` at 12.06.
- The newly sent message appeared in the conversation.
- The application displayed Alice's name and email address (`alice@example.com`) beside the theme toggle button.

**Execution Result:** PASS

**Evidence**

- **Screenshot:** [TC-MSG-001-01 — Valid Text Message](../evidence/messaging/TC-MSG-001-01-valid-text-message.png)

**Defect Reference:** None identified during this execution.

**Execution Notes**

The observed UI behavior was consistent with the expected result. Alice successfully sent a valid text message in the existing conversation with Bob, and the sent message appeared in the conversation. The application header displayed Alice's name and email address during the authenticated session.

This execution verifies the observable UI behavior for sending a text message and displaying the authenticated user's identity. It does not independently verify message persistence in the database, server-side message creation, or server-side sender identity enforcement.

### TC-MSG-002-01 — Display Existing Conversation Message History

**Test Case Reference:** [TC-MSG-002-01](../test-design/test-cases/messaging.md#tc-msg-002-01--display-existing-conversation-message-history)

**Scenario Reference:** SCN-MSG-002

**Requirement Reference:** REQ-MSG-002

**Preconditions**

- Relay is accessible.
- User A - Alice (alice@example.com) and User B - Bob (bob@example.com) are registered users.
- An existing 1-on-1 conversation between User A and User B is available.
- The conversation contains existing messages.
- User A is authorized to access the conversation.
- User A's valid credentials are available.

**Expected Result**

- Existing messages are displayed within the selected conversation.
- The displayed messages belong to the selected conversation.
- The displayed message content corresponds to the existing messages in the selected conversation.

**Actual Result**

- Alice (`alice@example.com`) successfully signed in to the Relay application.
- The chat page was displayed after successful sign-in.
- Alice selected the existing conversation with Bob (`bob@example.com`) from the conversation list.
- Multiple existing messages were displayed in the conversation history.
- Examples of the displayed messages included:
  - **Sender: Bob** — `Yeah, i am good, Alice. Long time no see. Where do you live now?` — displayed at 12.04.
  - **Sender: Alice** — `I live in Yogyakarta, Bob. How about you? What do you do for now?` — displayed at 12.06.
- The screenshot evidence was captured at approximately 12:35, as shown by the system clock.

**Execution Result:** PASS

**Evidence**

- **Screenshot:** [TC-MSG-002-01 — Existing Message History](../evidence/messaging/TC-MSG-002-01-existing-message-history.png)

**Defect Reference:** None identified during this execution.

**Execution Notes**

The observed UI behavior was consistent with the expected result. Multiple existing messages from both conversation participants were visible after Alice opened the conversation with Bob.

This execution verifies the observable display of existing conversation message history. It does not independently verify database persistence, message ordering beyond the observations recorded here, or server-side message retrieval.

### TC-MSG-003-01 — Verify Message Persistence After Refresh and Re-Login

**Test Case Reference:** [TC-MSG-003-01](../test-design/test-cases/messaging.md#tc-msg-003-01--verify-message-persistence-after-refresh-and-re-login)

**Scenario Reference:** SCN-MSG-003

**Requirement Reference:** REQ-MSG-003

**Preconditions**

- Relay is accessible.
- User A - Alice (alice@example.com) and User B - Bob (bob@example.com) are registered users.
- An existing 1-on-1 conversation between User A and User B is available.
- User A is authorized to access the conversation.
- User A's valid credentials are available.

**Expected Result**

- The test message remains available after page refresh.
- The test message remains available after logout and re-login.
- The persisted message content remains unchanged.
- The persisted message remains associated with the correct conversation.

**Actual Result**

- Alice (`alice@example.com`) successfully signed in to Relay.
- The chat page was displayed after successful sign-in.
- Alice opened the existing conversation with Bob (`bob@example.com`).
- Alice sent the message `Seriously? Wow, what an amazing coincidence! How long have you been working in SQA?` at 12.58.
- The screenshot captured after sending showed the message and the system clock at 12:58.
- After application refresh, the message remained visible at 12.59, as shown in the corresponding screenshot and system clock.
- Alice logged out, signed in again with the same account, and reopened the conversation with Bob.
- The screen recording showed that the message remained available after refresh and re-login.

**Execution Result:** PASS

**Evidence**

- **Screen Recording:** [TC-MSG-003-01 — Persistence Full Flow](https://github.com/user-attachments/assets/e983d4d5-e39a-4ea3-9e31-ec5962f9737f)
- **Screenshot:** [TC-MSG-003-01 — Message Sent at 12:58](../evidence/messaging/TC-MSG-003-01-message-sent-1258.png)
- **Screenshot:** [TC-MSG-003-01 — Message Persists After Refresh at 12:59](../evidence/messaging/TC-MSG-003-01-message-persists-after-refresh-1259.png)

**Defect Reference:** None identified during this execution.

**Execution Notes**

The observed UI behavior was consistent with the expected result. The message remained visible after application refresh and after Alice logged out, signed in again, and reopened the conversation with Bob.

The screenshots support the initial send and post-refresh observations. The screen recording provides evidence of the overall execution flow, including re-login. Database records and backend storage mechanisms were not independently verified.

### TC-MSG-004-01 — Verify Chronological Message Ordering

**Test Case Reference:** [TC-MSG-004-01](../test-design/test-cases/messaging.md#tc-msg-004-01--verify-chronological-message-ordering)

**Scenario Reference:** SCN-MSG-004

**Requirement Reference:** REQ-MSG-002

**Preconditions**

- Relay is accessible.
- User A - Alice (alice@example.com) and User C - Charlie (charlie@example.com) are registered users.
- An existing 1-on-1 conversation between User A and User C is available.
- User A is authorized to access the conversation.
- User A's valid credentials are available.

**Expected Result**

- The messages are displayed in chronological order based on their sending sequence.
- Message 1 appears before Message 2.
- Message 2 appears before Message 3.
- The chronological order remains consistent after page refresh.
- The chronological order remains consistent after logout and re-login.

**Actual Result**

- Alice (`alice@example.com`) successfully signed in to Relay.
- The chat page was displayed after successful sign-in.
- Alice opened the existing conversation with Charlie (`charlie@example.com`).
- Alice sent Message 1: `Happy birthday, Charlie!` at 14.51.
- Alice sent Message 2: `I wish you a lifetime of happiness.` at 14.51.
- Alice sent Message 3: `I hope we can meet again really soon!` at 14.52.
- After sending the third message, all three messages were displayed in the same order as their sending sequence.
- Alice refreshed the application page. The conversation persisted, and the message order remained unchanged.
- The screenshot captured after refresh showed the message history and the system clock at 14:53.
- Alice logged out, signed in again using the same account, and reopened the conversation with Charlie.
- The message order remained unchanged after re-login, as observed in the screen recording.

**Execution Result:** PASS

**Evidence**

- **Screen Recording:** [TC-MSG-004-01 — Chronological Ordering Full Flow](https://github.com/user-attachments/assets/925dd4c1-6a3e-4120-99ca-28b937c70822)
- **Screenshot:** [TC-MSG-004-01 — Message History After Third Message](../evidence/messaging/TC-MSG-004-01-after-third-message.png)
- **Screenshot:** [TC-MSG-004-01 — Message History After Refresh at 14:53](../evidence/messaging/TC-MSG-004-01-after-refresh.png)

**Defect Reference:** None identified during this execution.

**Execution Notes**

The observed UI behavior was consistent with the expected result. The three messages remained in their original sending order after application refresh and after Alice logged out, signed in again, and reopened the conversation with Charlie.

The screen recording provides evidence of the execution flow from sign-in through re-login. The screenshot captured after sending the third message supports the initial message-order observation, while the screenshot captured at 14:53 supports the post-refresh observation.

Message 1 and Message 2 were both sent at 14:51 according to the displayed system clock. Their relative order was verified through the observed message history. Exact timestamps and backend message ordering were not independently verified.

### TC-MSG-005-01 — Verify Automatic Scrolling to the Latest Message

**Test Case Reference:** [TC-MSG-005-01](../test-design/test-cases/messaging.md#tc-msg-005-01--verify-automatic-scrolling-to-the-latest-message)

**Scenario Reference:** SCN-MSG-005

**Requirement Reference:** REQ-MSG-004

**Preconditions**

- Relay is accessible.
- User A - Alice (alice@example.com) and User B - Bob (bob@example.com) are registered users.
- An existing 1-on-1 conversation between User A and User B is available.
- The conversation contains enough existing messages to require scrolling within the message view.
- User A is authorized to access the conversation.
- User A's valid credentials are available.

**Expected Result**

- When the conversation is opened, the message view automatically scrolls to the latest available message.
- The latest message is visible without requiring the user to manually scroll to the bottom of the conversation.
- After a new message is sent, the message view automatically scrolls to the newly sent message.
- The newly sent message is visible without requiring the user to manually scroll to the bottom of the conversation.

**Actual Result**

- Alice (`alice@example.com`) successfully signed in to Relay.
- The chat page was displayed after successful sign-in.
- Alice opened the existing conversation with Bob (`bob@example.com`).
- Upon opening the conversation, the application displayed the latest existing message: `Less than a year. I'm currently testing a team messaging app called Relay. Have you ever heard of it?`
- The message view was positioned at the bottom of the conversation, as indicated by the scrollbar reaching its lowest position.
- Alice sent the new text message `I've never heard of it before. What tech stack does it use?`
- After the message was sent, the application automatically scrolled down to the newly sent message.
- The newly sent message was visible without requiring Alice to manually scroll to the bottom of the conversation.

**Execution Result:** PASS

**Evidence**

- **Screen Recording:** [TC-MSG-005-01 — Automatic Scroll Full Flow](https://github.com/user-attachments/assets/e4d7d7cd-8a9e-41e1-ad0e-14ef2c9128ed)
- **Screenshot:** [TC-MSG-005-01 — Automatic Scroll on Conversation Open](../evidence/messaging/TC-MSG-005-01-auto-scroll-on-open.png)
- **Screenshot:** [TC-MSG-005-01 — Automatic Scroll After Sending Message](../evidence/messaging/TC-MSG-005-01-auto-scroll-after-send.png)

**Defect Reference:** None identified during this execution.

**Execution Notes**

The observed UI behavior was consistent with the expected result. The message view was positioned at the latest existing message when the conversation was opened, and it automatically scrolled to the newly sent message after Alice sent it.

The screen recording provides evidence of the execution flow from sign-in through verification after sending the message. The screenshots support the observed message-view positions before and after sending the new message. No manual scrolling was required during the observed steps.

### TC-MSG-006-01 — Verify Calendar Date Separators

**Test Case Reference:** [TC-MSG-006-01](../test-design/test-cases/messaging.md#tc-msg-006-01--verify-calendar-date-separators)

**Scenario Reference:** SCN-MSG-006

**Requirement Reference:** REQ-MSG-005

**Preconditions**

- Relay is accessible.
- User A (`alice@example.com`) and User B (`bob@example.com`) are registered users.
- An existing 1-on-1 conversation between User A and User B is available.
- User A is authorized to access the conversation.
- User A's valid credentials are available.
- The conversation contains messages from the current date, the previous calendar date, and at least one date before the previous calendar date.

**Expected Result**

- Messages sent on the current date are grouped under the `Today` date separator.
- Messages sent on the previous calendar date are grouped under the `Yesterday` date separator.
- Messages sent before the previous calendar date are grouped under a date separator in the documented DD Mon format (e.g., 01 Jan).
- Messages belonging to the same calendar date are grouped under the same date separator.
- Date separators are displayed in the appropriate position relative to the messages they represent.

**Actual Result**

- Alice (`alice@example.com`) successfully signed in to Relay.
- The chat page was displayed after successful sign-in.
- Alice opened the existing conversation with Bob (`bob@example.com`).
- The current-date message, `I've never heard of it before. What tech stack does it use?`, was displayed under the `Today` date separator.
- Alice scrolled upward to the previous-date message, `I live in Yogyakarta, Bob. How about you? What do you do for now?`.
- The previous-date message was displayed under the `Yesterday` date separator.
- Alice scrolled further upward to the older message, `Hello Bob! How are you?`.
- The older message was displayed under the `11 Oct` date separator.
- The observed date separators appeared in the appropriate positions relative to their corresponding messages.

**Execution Result:** PASS

**Evidence**

- **Screenshot:** [TC-MSG-006-01 — Current Date Message and Today Separator](../evidence/messaging/TC-MSG-006-01-today-separator.png)
- **Screenshot:** [TC-MSG-006-01 — Previous Date Message and Yesterday Separator](../evidence/messaging/TC-MSG-006-01-yesterday-separator.png)
- **Screenshot:** [TC-MSG-006-01 — Older Date Message and Date Separator](../evidence/messaging/TC-MSG-006-01-older-date-separator.png)

**Defect Reference:** None identified during this execution.

**Execution Notes**

The observed UI behavior was consistent with the expected date-separator rules for the three date categories examined: current date (`Today`), previous calendar date (`Yesterday`), and an older date (`11 Oct`).

The three screenshots provide evidence of the displayed date separators and their corresponding messages. The execution did not include a refresh or re-login verification, as these behaviors are outside the current scope of this test case.

### TC-MSG-007-01 — Prevent Sending Empty or Whitespace-Only Messages

**Test Case Reference:** [TC-MSG-007-01](../test-design/test-cases/messaging.md#tc-msg-007-01--prevent-sending-empty-or-whitespace-only-messages)

**Scenario Reference:** SCN-MSG-007

**Requirement Reference:** REQ-MSG-006

**Preconditions**

- Relay is accessible.
- User A (`alice@example.com`) and User B (`bob@example.com`) are registered users.
- An existing 1-on-1 conversation between User A and User B is available.
- User A is authorized to access the conversation.
- User A's valid credentials are available.

**Expected Result**

- The Send button is disabled when the message input is empty.
- The Send button is disabled when the message input contains only whitespace characters.
- Empty or whitespace-only messages cannot be submitted through the UI.

**Actual Result**

- Alice (`alice@example.com`) successfully signed in to Relay.
- The chat page was displayed after successful sign-in.
- Alice opened the existing conversation with Bob (`bob@example.com`).
- With the message input left empty, the Send button was disabled.
- After Alice entered whitespace-only content into the message input, the Send button remained disabled.

**Execution Result:** PASS

**Evidence**

- **Screenshot:** [TC-MSG-007-01 — Empty Message Input](../evidence/messaging/TC-MSG-007-01-empty-input.png)
- **Screenshot:** [TC-MSG-007-01 — Whitespace-Only Message Input](../evidence/messaging/TC-MSG-007-01-whitespace-only-input.png)

**Defect Reference:** None identified during this execution.

**Execution Notes**

The observed UI behavior was consistent with the expected result. The Send button was disabled for both an empty message input and a whitespace-only message input.

The two screenshots provide evidence of the button state under each input condition. This execution verified the UI behavior only; it did not independently verify backend rejection of empty or whitespace-only message payloads.