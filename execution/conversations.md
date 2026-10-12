# Conversations — Test Execution

## Overview

This document records formal test execution results for the Conversations functional area of the Relay application.

Execution records reference the corresponding test cases and document observed behavior, verdicts, and supporting evidence.

Only test cases that have actually been executed are recorded as formal execution results.

## Execution Summary

| Metric                 |                                Count |
| ---------------------- | -----------------------------------: |
| Test Cases Executed    |                                    4 |
| Passed                 |                                    4 |
| Failed                 |                                    0 |
| Blocked                |                                    0 |
| Clarification Required |                                    0 |
| Not Run                | Not tracked in this execution record |

_Summary reflects the execution records documented in this file and must be updated as additional test cases are executed._

## Execution Records

### TC-CONV-001-01 — Access and Retrieve an Existing One-on-One Conversation

**Test Case Reference:** [TC-CONV-001-01](../test-design/test-cases/conversations.md#tc-conv-001-01--access-and-retrieve-an-existing-one-on-one-conversation)

**Scenario Reference:** SCN-CONV-001, SCN-CONV-002

**Requirement Reference:** REQ-CONV-001, REQ-CONV-002

**Preconditions**

- Relay is accessible.
- User A and User B are registered users.
- An existing one-on-one conversation between User A and User B is available.
- User A's valid credentials are available.

**Expected Result**

- The chat page is displayed after User A signs in successfully.
- The existing conversation with User B is available in the conversation list.
- Selecting the conversation retrieves and displays the existing one-on-one conversation.
- The displayed conversation corresponds to the conversation between User A and User B.

**Actual Result**

- The observed behavior matched the documented expected results.
- User A successfully accessed the existing conversation with User B.
- The conversation between User A and User B was displayed in the main conversation panel.

**Execution Result:** PASS

**Evidence**

- **Screenshot:** [TC-CONV-001-01 — Existing Conversation Retrieved](../evidence/conversations/TC-CONV-001-01-existing-conversation-retrieved.png)

**Defect Reference:** None identified during this execution.

**Execution Notes**

The observed UI behavior was consistent with the documented expected results. User A could access the existing one-on-one conversation with User B, and the conversation was displayed in the main conversation panel.

This execution records observable UI behavior. It does not independently verify database state or server-side conversation retrieval and authorization enforcement.

### TC-CONV-002-01 — Create a New Conversation

**Test Case Reference:** [TC-CONV-002-01](../test-design/test-cases/conversations.md#tc-conv-002-01--create-a-new-conversation)

**Scenario Reference:** SCN-CONV-002

**Requirement Reference:** REQ-CONV-002

**Preconditions**

- Relay is accessible.
- User A and User C are registered users.
- No existing conversation between User A and User C is available.
- User A's valid credentials are available.

**Expected Result**

- A new conversation between User A and User C is created.
- The newly created conversation is displayed in the main conversation panel.
- The newly created conversation is available in the conversation list.

**Actual Result**

- A new conversation between User A (Alice) and User C (Charlie) was successfully created.
- The newly created conversation was displayed in the main conversation panel.
- The newly created conversation was also displayed in the conversation list.

**Execution Result:** PASS

**Evidence**

- **Screenshot:** [TC-CONV-002-01 — New Conversation Created](../evidence/conversations/TC-CONV-002-01-new-conversation-created.png)

**Defect Reference:** None identified during this execution.

**Execution Notes**

The observed behavior matched all documented expected results. The new conversation between Alice and Charlie was created and appeared in both the main conversation panel and the conversation list.

### TC-CONV-003-01 — Display Documented Conversation List Information

**Test Case Reference:** [TC-CONV-003-01](../test-design/test-cases/conversations.md#tc-conv-003-01--display-documented-conversation-list-information)

**Scenario Reference:** SCN-CONV-003

**Requirement Reference:** REQ-CONV-003, REQ-CONV-004, REQ-CONV-005

**Preconditions**

- Relay is accessible.
- User A and User B are registered users.
- An existing one-on-one conversation between User A and User B is available.
- The conversation contains at least one message.
- User A's valid credentials are available.

**Expected Result**

- The conversation list entry displays User B's name as the conversation counterpart.
- The conversation list entry displays the latest message preview.
- The conversation list entry displays a timestamp associated with the conversation.

**Actual Result**

- User B (Bob) appeared in the conversation list.
- The conversation list entry for the conversation with User B displayed the latest message preview: "Hello Bob! How are you?"
- The timestamp for the conversation with User B was displayed as 21:54.

**Execution Result:** PASS

**Evidence**

- **Screenshot:** [TC-CONV-003-01 — Conversation List Information](../evidence/conversations/TC-CONV-003-01-conversation-list-information.png)

**Defect Reference:** None identified during this execution.

**Execution Notes**

The observed conversation list entry displayed the counterpart's name, latest message preview, and timestamp as documented in the expected results. All three expected results were satisfied.

### TC-CONV-004-01 — Conversation List Reflects Latest Message Activity

**Test Case Reference:** [TC-CONV-004-01](../test-design/test-cases/conversations.md#tc-conv-004-01--conversation-list-reflects-latest-message-activity)

**Scenario Reference:** SCN-CONV-004

**Requirement Reference:** REQ-CONV-006

**Preconditions**

- Relay is accessible.
- User A, User B, and User C are registered users.
- User A has existing one-on-one conversations with User B and User C.
- Both conversations are accessible to User A.
- Both conversations contain existing message activity.
- User A's valid credentials are available.

**Expected Result**

- The conversation list is ordered based on the latest message activity.
- After User A successfully sends a new message in Conversation A, Conversation A appears above Conversation B in the conversation list, provided no newer message activity occurs in Conversation B during the test.
- The conversation list order reflects the latest message activity associated with the conversations.

**Actual Result**

- Before sending a new message, Conversation B (Alice and Charlie) appeared above Conversation A (Alice and Bob) in the conversation list.
- Conversation B displayed a timestamp of 23:15, while Conversation A displayed a timestamp of 21:54.
- User A successfully sent the message "I hope you are good, Bob." in Conversation A at 23:29.
- After the message was sent, Conversation A appeared above Conversation B in the conversation list.
- Conversation A displayed the latest message preview "I hope you are good, Bob." with a timestamp of 23:29.

**Execution Result:** PASS

**Evidence**

- **Before new message:** [TC-CONV-004-01 — Before New Message](../evidence/conversations/TC-CONV-004-01-before-new-message.png)
- **After new message:** [TC-CONV-004-01 — After New Message](../evidence/conversations/TC-CONV-004-01-after-new-message.png)

**Defect Reference:** None identified during this execution.

**Execution Notes**

The observed conversation list order changed after User A sent a new message in Conversation A. Before the message was sent, Conversation B appeared above Conversation A. After the message was sent successfully, Conversation A moved above Conversation B.

The observed UI behavior was consistent with REQ-CONV-006, which states that conversations shall be ordered based on the latest message activity. This execution verifies the visible conversation list behavior and does not independently verify the underlying server-side implementation.
