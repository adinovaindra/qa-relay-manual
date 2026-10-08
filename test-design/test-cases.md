# Relay — Test Case Design

## 1. Purpose

This document defines the detailed manual test cases derived from the approved test scenarios, documented requirements, identified requirement gaps, and risk assessment for Relay.

Test cases translate high-level test scenarios into specific, repeatable verification steps with defined preconditions, test data, expected results, and traceability.

Test execution results are intentionally excluded from the test case design stage and will be documented separately during execution.

---

## 2. Test Case Design Approach

Test cases are derived from approved test scenarios and designed to provide concrete verification of documented product behavior.

The test case design considers:

- Positive testing
- Negative testing
- Boundary and edge conditions where applicable
- Risk level
- Requirement traceability
- Repeatability of test execution

Where expected behavior is not defined by available product documentation, the behavior will not be assumed. Such cases are handled as exploratory or clarification-driven testing.

---

## 3. Test Case Structure

Each test case contains the following information:

| Field               | Description                                                                               |
| ------------------- | ----------------------------------------------------------------------------------------- |
| Test Case ID        | Unique identifier for the test case                                                       |
| Title               | Short description of the behavior being verified or investigated                          |
| Related Scenario    | Parent test scenario                                                                      |
| Related Requirement | Requirement associated with the test case, if applicable                                  |
| Risk Level          | Risk associated with the behavior                                                         |
| Test Design Method  | Method used to derive the test case                                                       |
| Test Type           | Testing classification                                                                    |
| Priority            | Execution priority                                                                        |
| Preconditions       | Conditions required before execution                                                      |
| Test Data           | Data required for execution                                                               |
| Steps               | Ordered actions performed by the tester                                                   |
| Expected Result     | Expected behavior based on the available requirement, contract, or defined test objective |

Execution-specific information such as Actual Result, Status, Evidence, and Defect ID will be recorded during the execution phase.

---

## 4. Test Design Methods

Test cases may be derived using one or more of the following methods:

| Method                    | Description                                                                                                          |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| Requirement-Based         | Derived primarily from a documented requirement or product contract.                                                 |
| Exploratory               | Derived through exploration of the application's actual behavior or user flow.                                       |
| Requirement + Exploratory | The requirement defines the test objective, while exploration is used to determine the practical application flow.   |
| Risk-Based                | Derived primarily from an identified product or QA risk.                                                             |
| Clarification-Driven      | Created to investigate behavior where the expected result is not sufficiently defined by the available requirements. |
| Regression                | Derived from previously verified behavior, changes, or known defects.                                                |

A test case may use more than one design method when appropriate.

Exploratory discovery of application behavior does not by itself establish the expected result. Expected behavior must remain grounded in an available requirement, contract, or explicitly defined test objective.

---

## 5. Authentication Test Cases

### TC-AUTH-001-01 — Register with Valid Data

| Field               | Value                               |
| ------------------- | ----------------------------------- |
| Test Case ID        | TC-AUTH-001-01                      |
| Title               | Register a new user with valid data |
| Related Scenario    | SCN-AUTH-001                        |
| Related Requirement | REQ-AUTH-001                        |
| Risk Level          | High                                |
| Test Design Method  | Requirement-Based + Exploratory     |
| Test Type           | Functional / Positive               |
| Priority            | High                                |

#### Preconditions

- Relay is accessible.
- The test email address has not been registered previously.
- The tester is not authenticated.

#### Test Data

| Data     | Value                                                                |
| -------- | -------------------------------------------------------------------- |
| Name     | Valid test user name                                                 |
| Email    | Unique test email address                                            |
| Password | Valid password according to the application's supported requirements |

#### Steps

1. Open the Relay application.
2. Verify that the application opens on the login page.
3. Click the "Create one" link.
4. Verify that the registration page is displayed.
5. Enter a valid name.
6. Enter a unique email address.
7. Enter a valid password according to the application's supported requirements.
8. Enter the same password in the "Confirm password" field.
9. Click the "Create account" button.
10. Observe the page displayed after account creation.
11. Enter the newly registered user's email address.
12. Enter the newly registered user's password.
13. Click the "Sign in" button.

#### Expected Result

- The registration request creates a new user account.
- The newly created account can be used to authenticate successfully.

### TC-AUTH-001-02 — Required Field Behavior

| Field               | Value                                                                 |
| ------------------- | --------------------------------------------------------------------- |
| Test Case ID        | TC-AUTH-001-02                                                        |
| Title               | Investigate registration behavior when a required field is left empty |
| Related Scenario    | SCN-AUTH-001                                                          |
| Related Requirement | REQ-AUTH-001                                                          |
| Risk Level          | High                                                                  |
| Test Design Method  | Exploratory + Clarification-Driven                                    |
| Test Type           | Functional / Negative                                                 |
| Priority            | High                                                                  |

#### Preconditions

- Relay is accessible.
- The tester is not authenticated.

#### Test Data

| Data             | Value                                                                |
| ---------------- | -------------------------------------------------------------------- |
| Name             | Valid test user name                                                 |
| Email            | Unique test email address                                            |
| Password         | Valid password according to the application's supported requirements |
| Confirm Password | Same as password                                                     |
| Empty Field      | One registration field intentionally left empty                      |

#### Steps

1. Open the Relay application.
2. Navigate to the registration page.
3. Leave one registration field empty.
4. Enter valid data in the remaining fields.
5. Click the "Create account" button.
6. Observe the result of the registration attempt.

#### Expected Result

- Clarification Required — the available product documentation does not define the expected behavior when a registration field is left empty.

### TC-AUTH-001-03 — Duplicate Account Behavior

| Field               | Value                                                     |
| ------------------- | --------------------------------------------------------- |
| Test Case ID        | TC-AUTH-001-03                                            |
| Title               | Investigate registration behavior for an existing account |
| Related Scenario    | SCN-AUTH-001                                              |
| Related Requirement | REQ-AUTH-001                                              |
| Risk Level          | High                                                      |
| Test Design Method  | Exploratory + Clarification-Driven                        |
| Test Type           | Functional / Negative                                     |
| Priority            | High                                                      |

#### Preconditions

- Relay is accessible.
- An existing user account is available.
- The tester is not authenticated.

#### Test Data

| Data             | Value                                                                |
| ---------------- | -------------------------------------------------------------------- |
| Name             | Valid test user name                                                 |
| Email            | Email address belonging to an existing account                       |
| Password         | Valid password according to the application's supported requirements |
| Confirm Password | Same as password                                                     |

#### Steps

1. Open the Relay application.
2. Navigate to the registration page.
3. Enter a valid name.
4. Enter the email address of an existing account.
5. Enter a valid password according to the application's supported requirements.
6. Enter the same password in the "Confirm password" field.
7. Click the "Create account" button.
8. Observe the result of the registration attempt.

#### Expected Result

- Clarification Required — the available product documentation does not define the expected behavior when an existing account's email address is submitted during registration.

### TC-AUTH-001-04 — Registration Error Handling

| Field               | Value                                               |
| ------------------- | --------------------------------------------------- |
| Test Case ID        | TC-AUTH-001-04                                      |
| Title               | Investigate error handling during user registration |
| Related Scenario    | SCN-AUTH-001                                        |
| Related Requirement | REQ-AUTH-001                                        |
| Risk Level          | High                                                |
| Test Design Method  | Exploratory + Clarification-Driven                  |
| Test Type           | Functional / Negative                               |
| Priority            | High                                                |

#### Preconditions

- Relay is accessible.
- The tester is not authenticated.
- A registration condition capable of producing an error is available.

#### Test Data

| Data               | Value                                                  |
| ------------------ | ------------------------------------------------------ |
| Registration Input | Valid registration data                                |
| Error Condition    | Registration request resulting in an application error |

#### Steps

1. Open the Relay application.
2. Navigate to the registration page.
3. Enter valid registration data.
4. Submit the registration request under the selected error condition.
5. Observe the result of the registration attempt.

#### Expected Result

- Clarification Required — the available product documentation does not define the expected error behavior for registration failures.

### TC-AUTH-002-01 — Login with Valid Credentials

| Field               | Value                        |
| ------------------- | ---------------------------- |
| Test Case ID        | TC-AUTH-002-01               |
| Title               | Login with valid credentials |
| Related Scenario    | SCN-AUTH-002                 |
| Related Requirement | REQ-AUTH-002                 |
| Risk Level          | High                         |
| Test Design Method  | Requirement-Based            |
| Test Type           | Functional / Positive        |
| Priority            | High                         |

#### Preconditions

- Relay is accessible.
- A registered user account is available.
- The tester is not authenticated.
- The account credentials are known and valid.

#### Test Data

| Data     | Value                                 |
| -------- | ------------------------------------- |
| Email    | Registered test user's email          |
| Password | Registered test user's valid password |

#### Steps

1. Open the Relay application.
2. Verify that the login page is displayed.
3. Enter the registered user's email address.
4. Enter the corresponding valid password.
5. Click the **"Sign in"** button.
6. Observe the result of the login attempt.
7. Verify the authentication state after successful login.
8. Attempt to access the protected chat functionality.

#### Expected Result

- The user is authenticated successfully using the valid credentials.
- The user enters an authenticated state.
- The protected chat functionality is accessible to the authenticated user.

### TC-AUTH-003-01 — Login with Invalid Password

| Field               | Value                           |
| ------------------- | ------------------------------- |
| Test Case ID        | TC-AUTH-003-01                  |
| Title               | Login with an invalid password  |
| Related Scenario    | SCN-AUTH-003                    |
| Related Requirement | REQ-AUTH-002                    |
| Risk Level          | High                            |
| Test Design Method  | Requirement-Based + Exploratory |
| Test Type           | Functional / Negative           |
| Priority            | High                            |

#### Preconditions

- Relay is accessible.
- A registered user account is available.
- The tester is not authenticated.
- The registered user's email address is known.

#### Test Data

| Data     | Value                        |
| -------- | ---------------------------- |
| Email    | Registered test user's email |
| Password | Incorrect password           |

#### Steps

1. Open the Relay application.
2. Verify that the login page is displayed.
3. Enter the registered user's email address.
4. Enter an incorrect password.
5. Click the **"Sign in"** button.
6. Observe the result of the login attempt.

#### Expected Result

- Authentication does not succeed with the invalid password.
- The user does not enter an authenticated state.
- Specific error behavior: **Clarification Required** due to lack of information defined by the available product documentation.

### TC-AUTH-003-02 — Login with Unknown Account

| Field               | Value                           |
| ------------------- | ------------------------------- |
| Test Case ID        | TC-AUTH-003-02                  |
| Title               | Login with an unknown account   |
| Related Scenario    | SCN-AUTH-003                    |
| Related Requirement | REQ-AUTH-002                    |
| Risk Level          | High                            |
| Test Design Method  | Requirement-Based + Exploratory |
| Test Type           | Functional / Negative           |
| Priority            | High                            |

#### Preconditions

- Relay is accessible.
- The tester is not authenticated.
- The test email address is not associated with a registered Relay account.

#### Test Data

| Data     | Value                              |
| -------- | ---------------------------------- |
| Email    | Unknown/unregistered email address |
| Password | Test password                      |

#### Steps

1. Open the Relay application.
2. Verify that the login page is displayed.
3. Enter an email address that is not associated with a registered Relay account.
4. Enter a test password.
5. Click the **"Sign in"** button.
6. Observe the result of the login attempt.

#### Expected Result

- Authentication does not succeed for the unknown account.
- The user does not enter an authenticated state.
- Specific error behavior: **Clarification Required** due to lack of information defined by the available product documentation.

### TC-AUTH-004-01 — Logout from Authenticated Session

| Field               | Value                                |
| ------------------- | ------------------------------------ |
| Test Case ID        | TC-AUTH-004-01                       |
| Title               | Logout from an authenticated session |
| Related Scenario    | SCN-AUTH-004                         |
| Related Requirement | REQ-AUTH-003                         |
| Risk Level          | High                                 |
| Test Design Method  | Requirement-Based                    |
| Test Type           | Functional / Positive                |
| Priority            | High                                 |

#### Preconditions

- Relay is accessible.
- A registered user account is available.
- The tester is authenticated successfully.

#### Test Data

| Data | Value                              |
| ---- | ---------------------------------- |
| User | Authenticated registered test user |

#### Steps

1. Open the Relay application.
2. Verify that the user is authenticated.
3. Click the **"Logout"** button.
4. Observe the result of the logout action.
5. Verify the authentication state after logout.
6. Attempt to access the protected chat functionality.

#### Expected Result

- The user is logged out successfully.
- The user is no longer in an authenticated state.
- The protected chat functionality is no longer accessible to the logged-out user.

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

| Field | Value |
|---|---|
| Test Case ID | TC-CONV-003-01 |
| Title | Display documented conversation list information |
| Related Scenario | SCN-CONV-003 |
| Related Requirement | REQ-CONV-003, REQ-CONV-004, REQ-CONV-005 |
| Risk Level | Medium |
| Test Design Method | Requirement-Based |
| Test Type | Functional / Positive |
| Priority | Medium |

#### Preconditions

- Relay is accessible.
- User A and User B are registered users.
- An existing 1-on-1 conversation between User A and User B is available.
- The conversation contains at least one message.
- User A's valid credentials are available.

#### Test Data

| Data | Value |
|---|---|
| User | User A |
| Conversation Participant | User B |
| Conversation | Existing 1-on-1 conversation containing at least one message |

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

| Field | Value |
|---|---|
| Test Case ID | TC-CONV-004-01 |
| Title | Conversation list reflects latest message activity |
| Related Scenario | SCN-CONV-004 |
| Related Requirement | REQ-CONV-006 |
| Risk Level | Medium |
| Test Design Method | Requirement-Based + Risk-Based |
| Test Type | Functional / Positive |
| Priority | Medium |

#### Preconditions

- Relay is accessible.
- User A, User B, and User C are registered users.
- User A has existing 1-on-1 conversations with User B and User C.
- Both conversations are accessible to User A.
- Both conversations contain existing message activity.
- User A's valid credentials are available.

#### Test Data

| Data | Value |
|---|---|
| User | User A |
| Conversation A | Existing 1-on-1 conversation between User A and User B |
| Conversation B | Existing 1-on-1 conversation between User A and User C |
| New Message | Valid text message sent by User A in Conversation B |

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

### TC-MSG-001-01 — Send a Valid Text Message

| Field | Value |
|---|---|
| Test Case ID | TC-MSG-001-01 |
| Title | Send a valid text message |
| Related Scenario | SCN-MSG-001 |
| Related Requirement | REQ-MSG-001 |
| Risk Level | High |
| Test Design Method | Requirement-Based + Risk-Based |
| Test Type | Functional / Positive |
| Priority | High |

#### Preconditions

- Relay is accessible.
- User A and User B are registered users.
- An existing 1-on-1 conversation between User A and User B is available.
- User A is authorized to access the conversation.
- User A's valid credentials are available.

#### Test Data

| Data | Value |
|---|---|
| Sender | User A |
| Conversation Participant | User B |
| Message | Valid text message |

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

| Field | Value |
|---|---|
| Test Case ID | TC-MSG-002-01 |
| Title | Display existing conversation message history |
| Related Scenario | SCN-MSG-002 |
| Related Requirement | REQ-MSG-002 |
| Risk Level | High |
| Test Design Method | Requirement-Based + Risk-Based |
| Test Type | Functional / Positive |
| Priority | High |

#### Preconditions

- Relay is accessible.
- User A and User B are registered users.
- An existing 1-on-1 conversation between User A and User B is available.
- The conversation contains existing messages.
- User A is authorized to access the conversation.
- User A's valid credentials are available.

#### Test Data

| Data | Value |
|---|---|
| User | User A |
| Conversation Participant | User B |
| Existing Messages | Known messages already available in the selected conversation |

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

| Field | Value |
|---|---|
| Test Case ID | TC-MSG-003-01 |
| Title | Verify message persistence after refresh and re-login |
| Related Scenario | SCN-MSG-003 |
| Related Requirement | REQ-MSG-003 |
| Risk Level | High |
| Test Design Method | Requirement-Based + Risk-Based |
| Test Type | Functional / Positive |
| Priority | High |

#### Preconditions

- Relay is accessible.
- User A and User B are registered users.
- An existing 1-on-1 conversation between User A and User B is available.
- User A is authorized to access the conversation.
- User A's valid credentials are available.

#### Test Data

| Data | Value |
|---|---|
| User | User A |
| Conversation Participant | User B |
| Test Message | Unique valid text message used to verify persistence |

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

| Field | Value |
|---|---|
| Test Case ID | TC-MSG-004-01 |
| Title | Verify chronological message ordering |
| Related Scenario | SCN-MSG-004 |
| Related Requirement | REQ-MSG-002 |
| Risk Level | Medium |
| Test Design Method | Requirement-Based + Risk-Based |
| Test Type | Functional / Positive |
| Priority | Medium |

#### Preconditions

- Relay is accessible.
- User A and User B are registered users.
- An existing 1-on-1 conversation between User A and User B is available.
- User A is authorized to access the conversation.
- User A's valid credentials are available.

#### Test Data

| Data | Value |
|---|---|
| User | User A |
| Conversation Participant | User B |
| Message 1 | Unique valid text message |
| Message 2 | Unique valid text message |
| Message 3 | Unique valid text message |

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

| Field | Value |
|---|---|
| Test Case ID | TC-MSG-005-01 |
| Title | Verify automatic scrolling to the latest message |
| Related Scenario | SCN-MSG-005 |
| Related Requirement | REQ-MSG-004 |
| Risk Level | Medium |
| Test Design Method | Requirement-Based + Risk-Based |
| Test Type | Functional / Positive |
| Priority | Medium |

#### Preconditions

- Relay is accessible.
- User A and User B are registered users.
- An existing 1-on-1 conversation between User A and User B is available.
- The conversation contains enough existing messages to require scrolling within the message view.
- User A is authorized to access the conversation.
- User A's valid credentials are available.

#### Test Data

| Data | Value |
|---|---|
| User | User A |
| Conversation Participant | User B |
| New Message | Unique valid text message |
| Message History | Existing conversation containing multiple messages |

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

| Field | Value |
|---|---|
| Test Case ID | TC-MSG-006-01 |
| Title | Verify calendar date separators |
| Related Scenario | SCN-MSG-006 |
| Related Requirement | REQ-MSG-005 |
| Risk Level | Medium |
| Test Design Method | Requirement-Based + Risk-Based |
| Test Type | Functional / Positive |
| Priority | Medium |

#### Preconditions

- Relay is accessible.
- User A and User B are registered users.
- An existing 1-on-1 conversation between User A and User B is available.
- User A is authorized to access the conversation.
- User A's valid credentials are available.
- The conversation contains messages from the current date, the previous calendar date, and at least one date before the previous calendar date.

#### Test Data

| Data | Value |
|---|---|
| User | User A |
| Conversation Participant | User B |
| Current Date Message | Unique valid text message sent on the current date |
| Previous Date Message | Unique valid text message sent on the previous calendar date |
| Older Date Message | Unique valid text message sent before the previous calendar date |

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