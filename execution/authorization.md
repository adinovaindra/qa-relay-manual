# Authorization — Test Execution

## Overview

This document records formal test execution results for the Authorization functional area of the Relay application.

Execution records reference the corresponding test cases and document observed behavior, verdicts, and supporting evidence.

Only test cases that have actually been executed are recorded as formal execution results.

## Execution Summary

| Metric                 |                                Count |
| ---------------------- | -----------------------------------: |
| Test Cases Executed    |                                    2 |
| Passed                 |                                    2 |
| Failed                 |                                    0 |
| Blocked                |                                    0 |
| Clarification Required |                                    0 |
| Not Run                | Not tracked in this execution record |

_Summary reflects the execution records documented in this file and must be updated as additional test cases are executed._

## Execution Records

### TC-AUTHZ-001-01 — Authorized User Accesses Existing Conversation

**Test Case Reference:** [TC-AUTHZ-001-01](../test-design/test-cases/authorization.md#tc-authz-001-01--authorized-user-accesses-existing-conversation)

**Scenario Reference:** SCN-AUTHZ-001

**Requirement Reference:** REQ-AUTHZ-001, REQ-AUTHZ-002

**Preconditions**

- Relay is accessible.
- User A is a registered user.
- User B is a registered user.
- A conversation exists between User A and User B.
- User A's valid credentials are available.

**Expected Result**

- User A can access the existing conversation.
- The conversation content is displayed to User A.
- The displayed conversation corresponds to the conversation between User A and User B.

**Actual Result**

- **Authorized User:** Bob (`bob@example.com`).
- **Other Participant:** Alice (`alice@example.com`).
- Bob signed in using valid credentials and opened the conversation with Alice.
- The conversation initially displayed the empty state `No messages yet`.
- Bob sent the message `Hello Alice, I am Bob!` in the conversation.
- The message appeared in Bob's conversation view at 21.17.
- Alice subsequently signed in using valid credentials and opened the corresponding conversation.
- The same message, `Hello Alice, I am Bob!`, was visible in Alice's conversation view at 21.17.
- The conversation URL in both user sessions contained the same conversation ID: `deeaf79d-e410-4a9a-8011-71aa2c782f28`.

**Execution Result:** PASS

**Evidence**

- **Bob's Conversation View:** [TC-AUTHZ-001-01 — Bob Sent Message](../evidence/authorization/TC-AUTHZ-001-01-bob-sent-message.png)
- **Alice's Conversation View:** [TC-AUTHZ-001-01 — Alice Received Message](../evidence/authorization/TC-AUTHZ-001-01-alice-received-message.png)

**Defect Reference:** None identified during this execution.

**Execution Notes**

The screenshots support that Bob could open the existing conversation with Alice, send a message, and view the sent message in his conversation. Alice could subsequently open the conversation with the same conversation ID and view the same message.

The initial empty state did not prevent the conversation from being accessed. A message was sent during execution to verify that conversation content could be displayed.

This execution verifies the observable UI behavior for an authorized participant. It does not independently verify server-side authorization enforcement, database state, or whether an unauthorized user is prevented from accessing the conversation.

### TC-AUTHZ-004-01 — Message Is Attributed to the Authenticated User

**Test Case Reference:** [TC-AUTHZ-004-01](../test-design/test-cases/authorization.md#tc-authz-004-01--message-is-attributed-to-the-authenticated-user)

**Scenario Reference:** SCN-AUTHZ-004

**Requirement Reference:** REQ-AUTHZ-004

**Preconditions**

- Relay is accessible.
- User A and User B are registered users.
- A conversation exists between User A and User B.
- User A's valid credentials are available.

**Expected Result**

- The message is created successfully.
- The newly created message is attributed to User A.
- The sender identity displayed for the message corresponds to the authenticated user who sent it.

**Actual Result**

- Alice (`alice@example.com`) was authenticated in the Relay application.
- Alice sent the message `Hello Bob! How are you?` in the conversation with Bob.
- The newly created message appeared in the conversation as an outgoing message.
- The application header displayed Alice's name and email address while the message was shown in the authenticated session.

**Execution Result:** PASS

**Evidence**

- **Screenshot:** [TC-AUTHZ-004-01 — Message Sender Identity](../evidence/authorization/TC-AUTHZ-004-01-message-sender-identity.png)

**Defect Reference:** None identified during this execution.

**Execution Notes**

The observed UI behavior is consistent with the expected result. The authenticated user was Alice, and the newly created message appeared as an outgoing message in the conversation with Bob.

This execution verifies the observable UI behavior for message attribution. It does not independently verify sender identity in the database or server-side enforcement.