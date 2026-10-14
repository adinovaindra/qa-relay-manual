## Conversations Test Cases

### TC-CONV-001-01 — Access and Retrieve an Existing One-on-One Conversation

| Field               | Value                                                   |
| ------------------- | ------------------------------------------------------- |
| Test Case ID        | TC-CONV-001-01                                          |
| Title               | Access and retrieve an existing one-on-one conversation |
| Related Scenario    | SCN-CONV-001, SCN-CONV-002                              |
| Related Requirement | REQ-CONV-001, REQ-CONV-002                              |
| Risk Level          | High                                                    |
| Test Design Method  | Requirement-Based                                       |
| Test Type           | Functional / Positive                                   |
| Priority            | High                                                    |

#### Preconditions

- Relay is accessible.
- User A and User B are registered users.
- An existing one-on-one conversation between User A and User B is available.
- User A's valid credentials are available.

#### Test Data

| Data                     | Value                                       |
| ------------------------ | ------------------------------------------- |
| Authorized User          | User A - Alice (alice@example.com)          |
| Authorized User Password | password123                                 |
| Other Participant        | User B - Bob (bob@example.com)              |
| Conversation             | Existing conversation between Alice and Bob |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Verify that the chat page is displayed.
4. Verify that the existing conversation with User B is present in the conversation list.
5. Select the conversation with User B.
6. Observe the conversation displayed in the main conversation panel.

#### Expected Result

- The chat page is displayed after User A signs in successfully.
- The existing conversation with User B is available in the conversation list.
- Selecting the conversation retrieves and displays the existing one-on-one conversation.
- The displayed conversation corresponds to the conversation between User A and User B.

### TC-CONV-002-01 — Create a New Conversation

| Field               | Value                     |
| ------------------- | ------------------------- |
| Test Case ID        | TC-CONV-002-01            |
| Title               | Create a new conversation |
| Related Scenario    | SCN-CONV-002              |
| Related Requirement | REQ-CONV-002              |
| Risk Level          | High                      |
| Test Design Method  | Requirement-Based         |
| Test Type           | Functional / Positive     |
| Priority            | High                      |

#### Preconditions

- Relay is accessible.
- User A and User C are registered users.
- No existing conversation between User A and User C is available.
- User A's valid credentials are available.

#### Test Data

| Data                     | Value                                  |
| ------------------------ | -------------------------------------- |
| Sender                   | User A - Alice (alice@example.com)     |
| Sender Password          | password123                            |
| Conversation Participant | User C - Charlie (charlie@example.com) |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Verify that the chat page is displayed.
4. Open the **"Select a user"** dropdown under **"New Chat"**.
5. Select **Charlie**.
6. Click the **"Start Chat"** button.
7. Observe the conversation displayed in the main conversation panel.
8. Observe the conversation list.

#### Expected Result

- A new conversation between User A and User C is created.
- The newly created conversation is displayed in the main conversation panel.
- The newly created conversation is available in the conversation list.

### TC-CONV-003-01 — Display Documented Conversation List Information

| Field               | Value                                            |
| ------------------- | ------------------------------------------------ |
| Test Case ID        | TC-CONV-003-01                                   |
| Title               | Display documented conversation list information |
| Related Scenario    | SCN-CONV-003                                     |
| Related Requirement | REQ-CONV-003, REQ-CONV-004, REQ-CONV-005         |
| Risk Level          | Medium                                           |
| Test Design Method  | Requirement-Based                                |
| Test Type           | Functional / Positive                            |
| Priority            | Medium                                           |

#### Preconditions

- Relay is accessible.
- User A and User B are registered users.
- An existing 1-on-1 conversation between User A and User B is available.
- The conversation contains at least one message.
- User A's valid credentials are available.

#### Test Data

| Data                        | Value                                                        |
| --------------------------- | ------------------------------------------------------------ |
| Authenticated User          | User A - Alice (alice@example.com)                           |
| Authenticated User Password | password123                                                  |
| Conversation Participant    | User B - Bob (bob@example.com)                               |
| Conversation                | Existing 1-on-1 conversation containing at least one message |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Verify that the chat page is displayed.
4. Locate the existing conversation with User B in the conversation list.
5. Inspect the conversation list entry.
6. Verify the information displayed for the conversation.

#### Expected Result

- The conversation list entry displays User B's name as the conversation counterpart.
- The conversation list entry displays the latest message preview.
- The conversation list entry displays a timestamp associated with the conversation.

### TC-CONV-004-01 — Conversation List Reflects Latest Message Activity

| Field               | Value                                              |
| ------------------- | -------------------------------------------------- |
| Test Case ID        | TC-CONV-004-01                                     |
| Title               | Conversation list reflects latest message activity |
| Related Scenario    | SCN-CONV-004                                       |
| Related Requirement | REQ-CONV-006                                       |
| Risk Level          | Medium                                             |
| Test Design Method  | Requirement-Based + Risk-Based                     |
| Test Type           | Functional / Positive                              |
| Priority            | Medium                                             |

#### Preconditions

- Relay is accessible.
- User A, User B, and User C are registered users.
- User A has existing 1-on-1 conversations with User B and User C.
- Both conversations are accessible to User A.
- Both conversations contain existing message activity.
- User A's valid credentials are available.

#### Test Data

| Data                        | Value                                                                                  |
| --------------------------- | -------------------------------------------------------------------------------------- |
| Authenticated User          | User A - Alice (alice@example.com)                                                     |
| Authenticated User Password | password123                                                                            |
| Conversation A              | Existing 1-on-1 conversation between User A and User B - Bob (bob@example.com)         |
| Conversation B              | Existing 1-on-1 conversation between User A and User C - Charlie (charlie@example.com) |
| New Message                 | Valid text message sent by User A in Conversation A                                    |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Verify that the chat page is displayed.
4. Locate Conversation A and Conversation B in the conversation list.
5. Record their current relative order.
6. Open Conversation A.
7. Send a valid text message.
8. Return to or observe the conversation list.
9. Identify the current position of Conversation A and Conversation B.
10. Inspect the latest message activity associated with both conversations.
11. Compare the conversation positions with their latest message activity.

#### Expected Result

- The conversation list is ordered based on the latest message activity.
- After User A successfully sends a new message in Conversation A, Conversation A appears above Conversation B in the conversation list, provided no newer message activity occurs in Conversation B during the test.
- The conversation list order reflects the latest message activity associated with the conversations.
