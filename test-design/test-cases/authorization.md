## Authorization Test Cases

### TC-AUTHZ-001-01 — Authorized User Accesses Existing Conversation

| Field               | Value                                             |
| ------------------- | ------------------------------------------------- |
| Test Case ID        | TC-AUTHZ-001-01                                   |
| Title               | Authorized user accesses an existing conversation |
| Related Scenario    | SCN-AUTHZ-001                                     |
| Related Requirement | REQ-AUTHZ-001, REQ-AUTHZ-002                      |
| Risk Level          | High                                              |
| Test Design Method  | Requirement-Based                                 |
| Test Type           | Functional / Positive                             |
| Priority            | High                                              |

#### Preconditions

- Relay is accessible.
- User A is a registered user.
- User B is a registered user.
- A conversation exists between User A and User B.
- User A's valid credentials are available.

#### Test Data

| Data              | Value                                           |
| ----------------- | ----------------------------------------------- |
| Authorized User   | User A                                          |
| Other Participant | User B                                          |
| Conversation      | Existing conversation between User A and User B |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Navigate to the conversation between User A and User B.
4. Observe the conversation displayed.

#### Expected Result

- User A can access the existing conversation.
- The conversation content is displayed to User A.
- The displayed conversation corresponds to the conversation between User A and User B.

### TC-AUTHZ-004-01 — Message Is Attributed to the Authenticated User

| Field               | Value                                           |
| ------------------- | ----------------------------------------------- |
| Test Case ID        | TC-AUTHZ-004-01                                 |
| Title               | Message is attributed to the authenticated user |
| Related Scenario    | SCN-AUTHZ-004                                   |
| Related Requirement | REQ-AUTHZ-004                                   |
| Risk Level          | High                                            |
| Test Design Method  | Requirement-Based                               |
| Test Type           | Functional / Positive                           |
| Priority            | High                                            |

#### Preconditions

- Relay is accessible.
- User A and User B are registered users.
- A conversation exists between User A and User B.
- User A's valid credentials are available.

#### Test Data

| Data      | Value              |
| --------- | ------------------ |
| Sender    | User A             |
| Recipient | User B             |
| Message   | Valid test message |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Navigate to the conversation between User A and User B.
4. Enter the test message.
5. Send the message.
6. Observe the newly created message in the conversation.

#### Expected Result

- The message is created successfully.
- The newly created message is attributed to User A.
- The sender identity displayed for the message corresponds to the authenticated user who sent it.