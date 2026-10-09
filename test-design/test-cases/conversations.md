## Conversations Test Cases

### TC-CONV-001-01 — Access an Existing One-on-One Conversation

| Field               | Value                                      |
| ------------------- | ------------------------------------------ |
| Test Case ID        | TC-CONV-001-01                             |
| Title               | Access an existing one-on-one conversation |
| Related Scenario    | SCN-CONV-001                               |
| Related Requirement | REQ-CONV-001                               |
| Risk Level          | High                                       |
| Test Design Method  | Requirement-Based                          |
| Test Type           | Functional / Positive                      |
| Priority            | High                                       |

#### Preconditions

- Relay is accessible.
- User A and User B are registered users.
- An existing one-on-one conversation between User A and User B is available.
- User A's valid credentials are available.

#### Test Data

| Data              | Value                                           |
| ----------------- | ----------------------------------------------- |
| User              | User A                                          |
| Other Participant | User B                                          |
| Conversation      | Existing conversation between User A and User B |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Navigate to the existing conversation between User A and User B.
4. Observe the conversation displayed.

#### Expected Result

- User A can access the existing one-on-one conversation.
- The conversation between User A and User B is displayed.

### TC-CONV-002-01 — Retrieve an Existing Conversation

| Field               | Value                             |
| ------------------- | --------------------------------- |
| Test Case ID        | TC-CONV-002-01                    |
| Title               | Retrieve an existing conversation |
| Related Scenario    | SCN-CONV-002                      |
| Related Requirement | REQ-CONV-002                      |
| Risk Level          | High                              |
| Test Design Method  | Requirement-Based                 |
| Test Type           | Functional / Positive             |
| Priority            | High                              |

#### Preconditions

- Relay is accessible.
- User A and User B are registered users.
- An existing conversation between User A and User B is available.
- User A's valid credentials are available.

#### Test Data

| Data              | Value                                           |
| ----------------- | ----------------------------------------------- |
| User              | User A                                          |
| Other Participant | User B                                          |
| Conversation      | Existing conversation between User A and User B |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Verify that the chat page is displayed.
4. Verify that the existing conversation with User B is present in the conversation list.
5. Select the conversation with User B.
6. Observe the conversation displayed in the main conversation panel.

#### Expected Result

- The existing conversation with User B is available in the conversation list.
- Selecting the conversation retrieves and displays the existing conversation.
- The displayed conversation corresponds to the existing conversation between User A and User B.

### TC-CONV-002-02 — Create a New Conversation

| Field               | Value                     |
| ------------------- | ------------------------- |
| Test Case ID        | TC-CONV-002-02            |
| Title               | Create a new conversation |
| Related Scenario    | SCN-CONV-002              |
| Related Requirement | REQ-CONV-002              |
| Risk Level          | High                      |
| Test Design Method  | Requirement-Based         |
| Test Type           | Functional / Positive     |
| Priority            | High                      |

#### Preconditions

- Relay is accessible.
- User A and Alice are registered users.
- No existing conversation between User A and Alice is available.
- User A's valid credentials are available.

#### Test Data

| Data                     | Value  |
| ------------------------ | ------ |
| User                     | User A |
| Conversation Participant | Alice  |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Verify that the chat page is displayed.
4. Open the **"Select a user"** dropdown under **"New Chat"**.
5. Select **Alice**.
6. Click the **"Start Chat"** button.
7. Observe the conversation displayed in the main conversation panel.
8. Observe the conversation list.

#### Expected Result

- A new conversation between User A and Alice is created.
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

| Data                     | Value                                                        |
| ------------------------ | ------------------------------------------------------------ |
| User                     | User A                                                       |
| Conversation Participant | User B                                                       |
| Conversation             | Existing 1-on-1 conversation containing at least one message |

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

| Data           | Value                                                  |
| -------------- | ------------------------------------------------------ |
| User           | User A                                                 |
| Conversation A | Existing 1-on-1 conversation between User A and User B |
| Conversation B | Existing 1-on-1 conversation between User A and User C |
| New Message    | Valid text message sent by User A in Conversation B    |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Verify that the chat page is displayed.
4. Locate Conversation A and Conversation B in the conversation list.
5. Record their current relative order.
6. Open Conversation B.
7. Send a valid text message.
8. Return to or observe the conversation list.
9. Identify the current position of Conversation A and Conversation B.
10. Inspect the latest message activity associated with both conversations.
11. Compare the conversation positions with their latest message activity.

#### Expected Result

- The conversation list reflects the latest message activity.
- Conversation B's position is consistent with its latest message activity relative to Conversation A.
- The conversation position is consistent with the latest message activity associated with the conversation.