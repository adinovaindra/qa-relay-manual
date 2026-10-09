## Messaging Test Cases

### TC-MSG-001-01 — Send a Valid Text Message

| Field               | Value                          |
| ------------------- | ------------------------------ |
| Test Case ID        | TC-MSG-001-01                  |
| Title               | Send a valid text message      |
| Related Scenario    | SCN-MSG-001                    |
| Related Requirement | REQ-MSG-001                    |
| Risk Level          | High                           |
| Test Design Method  | Requirement-Based + Risk-Based |
| Test Type           | Functional / Positive          |
| Priority            | High                           |

#### Preconditions

- Relay is accessible.
- User A and User B are registered users.
- An existing 1-on-1 conversation between User A and User B is available.
- User A is authorized to access the conversation.
- User A's valid credentials are available.

#### Test Data

| Data                     | Value              |
| ------------------------ | ------------------ |
| Sender                   | User A             |
| Conversation Participant | User B             |
| Message                  | Valid text message |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Verify that the chat page is displayed.
4. Open the existing conversation with User B.
5. Enter a valid text message in the message input.
6. Send the message.
7. Observe the conversation after the message is sent.

#### Expected Result

- The message is successfully sent within the authorized conversation.
- The sent message appears in the conversation.
- The displayed sender identity of the message corresponds to User A.

### TC-MSG-002-01 — Display Existing Conversation Message History

| Field               | Value                                         |
| ------------------- | --------------------------------------------- |
| Test Case ID        | TC-MSG-002-01                                 |
| Title               | Display existing conversation message history |
| Related Scenario    | SCN-MSG-002                                   |
| Related Requirement | REQ-MSG-002                                   |
| Risk Level          | High                                          |
| Test Design Method  | Requirement-Based + Risk-Based                |
| Test Type           | Functional / Positive                         |
| Priority            | High                                          |

#### Preconditions

- Relay is accessible.
- User A and User B are registered users.
- An existing 1-on-1 conversation between User A and User B is available.
- The conversation contains existing messages.
- User A is authorized to access the conversation.
- User A's valid credentials are available.

#### Test Data

| Data                     | Value                                                         |
| ------------------------ | ------------------------------------------------------------- |
| User                     | User A                                                        |
| Conversation Participant | User B                                                        |
| Existing Messages        | Known messages already available in the selected conversation |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Verify that the chat page is displayed.
4. Open the existing conversation with User B.
5. Observe the message history displayed in the conversation.
6. Identify the existing messages in the conversation.
7. Verify that the displayed messages correspond to the selected conversation.
8. Verify the content of the displayed messages.

#### Expected Result

- Existing messages are displayed within the selected conversation.
- The displayed messages belong to the selected conversation.
- The displayed message content corresponds to the existing messages in the selected conversation.

### TC-MSG-003-01 — Verify Message Persistence After Refresh and Re-Login

| Field               | Value                                                 |
| ------------------- | ----------------------------------------------------- |
| Test Case ID        | TC-MSG-003-01                                         |
| Title               | Verify message persistence after refresh and re-login |
| Related Scenario    | SCN-MSG-003                                           |
| Related Requirement | REQ-MSG-003                                           |
| Risk Level          | High                                                  |
| Test Design Method  | Requirement-Based + Risk-Based                        |
| Test Type           | Functional / Positive                                 |
| Priority            | High                                                  |

#### Preconditions

- Relay is accessible.
- User A and User B are registered users.
- An existing 1-on-1 conversation between User A and User B is available.
- User A is authorized to access the conversation.
- User A's valid credentials are available.

#### Test Data

| Data                     | Value                                                |
| ------------------------ | ---------------------------------------------------- |
| User                     | User A                                               |
| Conversation Participant | User B                                               |
| Test Message             | Unique valid text message used to verify persistence |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Verify that the chat page is displayed.
4. Open the existing conversation with User B.
5. Enter a unique valid test message.
6. Send the test message.
7. Verify that the test message appears in the conversation.
8. Refresh the page.
9. Verify that the test message remains available in the conversation.
10. Log out from Relay.
11. Sign in again as User A using valid credentials.
12. Open the conversation with User B.
13. Locate the previously sent test message.
14. Verify that the test message content remains unchanged.
15. Verify that the test message remains associated with the conversation with User B.

#### Expected Result

- The test message remains available after page refresh.
- The test message remains available after logout and re-login.
- The persisted message content remains unchanged.
- The persisted message remains associated with the correct conversation.

### TC-MSG-004-01 — Verify Chronological Message Ordering

| Field               | Value                                 |
| ------------------- | ------------------------------------- |
| Test Case ID        | TC-MSG-004-01                         |
| Title               | Verify chronological message ordering |
| Related Scenario    | SCN-MSG-004                           |
| Related Requirement | REQ-MSG-002                           |
| Risk Level          | Medium                                |
| Test Design Method  | Requirement-Based + Risk-Based        |
| Test Type           | Functional / Positive                 |
| Priority            | Medium                                |

#### Preconditions

- Relay is accessible.
- User A and User B are registered users.
- An existing 1-on-1 conversation between User A and User B is available.
- User A is authorized to access the conversation.
- User A's valid credentials are available.

#### Test Data

| Data                     | Value                     |
| ------------------------ | ------------------------- |
| User                     | User A                    |
| Conversation Participant | User B                    |
| Message 1                | Unique valid text message |
| Message 2                | Unique valid text message |
| Message 3                | Unique valid text message |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Verify that the chat page is displayed.
4. Open the existing conversation with User B.
5. Enter and send Message 1.
6. Enter and send Message 2.
7. Enter and send Message 3.
8. Observe the displayed message history.
9. Verify the relative order of Message 1, Message 2, and Message 3.
10. Refresh the page.
11. Open the conversation with User B if necessary.
12. Verify the relative order of Message 1, Message 2, and Message 3.
13. Log out from Relay.
14. Sign in again as User A using valid credentials.
15. Open the conversation with User B.
16. Verify the relative order of Message 1, Message 2, and Message 3.

#### Expected Result

- The messages are displayed in chronological order based on their sending sequence.
- Message 1 appears before Message 2.
- Message 2 appears before Message 3.
- The chronological order remains consistent after page refresh.
- The chronological order remains consistent after logout and re-login.

### TC-MSG-005-01 — Verify Automatic Scrolling to the Latest Message

| Field               | Value                                            |
| ------------------- | ------------------------------------------------ |
| Test Case ID        | TC-MSG-005-01                                    |
| Title               | Verify automatic scrolling to the latest message |
| Related Scenario    | SCN-MSG-005                                      |
| Related Requirement | REQ-MSG-004                                      |
| Risk Level          | Medium                                           |
| Test Design Method  | Requirement-Based + Risk-Based                   |
| Test Type           | Functional / Positive                            |
| Priority            | Medium                                           |

#### Preconditions

- Relay is accessible.
- User A and User B are registered users.
- An existing 1-on-1 conversation between User A and User B is available.
- The conversation contains enough existing messages to require scrolling within the message view.
- User A is authorized to access the conversation.
- User A's valid credentials are available.

#### Test Data

| Data                     | Value                                              |
| ------------------------ | -------------------------------------------------- |
| User                     | User A                                             |
| Conversation Participant | User B                                             |
| New Message              | Unique valid text message                          |
| Message History          | Existing conversation containing multiple messages |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Verify that the chat page is displayed.
4. Open the existing conversation with User B.
5. Observe the message view immediately after the conversation is opened.
6. Identify the latest message currently available in the conversation.
7. Verify the visible position of the message view relative to the latest message.
8. Send a unique valid text message.
9. Observe the message view immediately after the message is sent.
10. Identify the newly sent message as the latest message in the conversation.
11. Verify the visible position of the message view relative to the newly sent message.

#### Expected Result

- When the conversation is opened, the message view automatically scrolls to the latest available message.
- The latest message is visible without requiring the user to manually scroll to the bottom of the conversation.
- After a new message is sent, the message view automatically scrolls to the newly sent message.
- The newly sent message is visible without requiring the user to manually scroll to the bottom of the conversation.

### TC-MSG-006-01 — Verify Calendar Date Separators

| Field               | Value                           |
| ------------------- | ------------------------------- |
| Test Case ID        | TC-MSG-006-01                   |
| Title               | Verify calendar date separators |
| Related Scenario    | SCN-MSG-006                     |
| Related Requirement | REQ-MSG-005                     |
| Risk Level          | Medium                          |
| Test Design Method  | Requirement-Based + Risk-Based  |
| Test Type           | Functional / Positive           |
| Priority            | Medium                          |

#### Preconditions

- Relay is accessible.
- User A and User B are registered users.
- An existing 1-on-1 conversation between User A and User B is available.
- User A is authorized to access the conversation.
- User A's valid credentials are available.
- The conversation contains messages from the current date, the previous calendar date, and at least one date before the previous calendar date.

#### Test Data

| Data                     | Value                                                            |
| ------------------------ | ---------------------------------------------------------------- |
| User                     | User A                                                           |
| Conversation Participant | User B                                                           |
| Current Date Message     | Unique valid text message sent on the current date               |
| Previous Date Message    | Unique valid text message sent on the previous calendar date     |
| Older Date Message       | Unique valid text message sent before the previous calendar date |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Verify that the chat page is displayed.
4. Open the existing conversation with User B.
5. Observe the message history.
6. Locate the messages sent on the current date.
7. Verify the date separator associated with the current date.
8. Locate the messages sent on the previous calendar date.
9. Verify the date separator associated with the previous calendar date.
10. Locate the messages sent before the previous calendar date.
11. Verify the date separator associated with the older messages.
12. Verify that messages belonging to the same calendar date are grouped under the same date separator.
13. Refresh the page.
14. Open the conversation with User B if necessary.
15. Verify that the date separators and message grouping remain consistent after refresh.

#### Expected Result

- Messages sent on the current date are grouped under the `Today` date separator.
- Messages sent on the previous calendar date are grouped under the `Yesterday` date separator.
- Messages sent before the previous calendar date are grouped under a two-digit day and month date separator.
- Messages belonging to the same calendar date are grouped under the same date separator.
- Date separators are displayed in the appropriate position relative to the messages they represent.
- Date separators and message grouping remain consistent after page refresh.
