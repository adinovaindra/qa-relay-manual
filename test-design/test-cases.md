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

### TC-AUTH-001-02 — Required Field Validation During Registration

| Field               | Value                                                |
| ------------------- | ---------------------------------------------------- |
| Test Case ID        | TC-AUTH-001-02                                       |
| Title               | Verify required field validation during registration |
| Related Scenario    | SCN-AUTH-001, SCN-UX-002                             |
| Related Requirement | REQ-AUTH-001, REQ-AUTH-006                           |
| Risk Level          | High                                                 |
| Test Design Method  | Requirement-Based + Exploratory                      |
| Test Type           | Functional / Negative                                |
| Priority            | High                                                 |

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
6. Observe the validation behavior and any error message displayed.
7. Repeat the test with each registration field left empty individually.
8. Leave all registration fields empty and click the "Create account" button.
9. Observe which field receives validation feedback first.

#### Expected Result

- Registration is not completed when a required registration field is left empty.
- The application displays the validation tooltip "Please fill out this field." for an empty required authentication form field.
- Validation feedback is associated with the field requiring input.
- The exact validation order when multiple required fields are empty is not specified by the requirement.

### TC-AUTH-001-03 — Registration with an Existing Email Address

| Field               | Value                                                |
| ------------------- | ---------------------------------------------------- |
| Test Case ID        | TC-AUTH-001-03                                       |
| Title               | Verify registration behavior for an existing account |
| Related Scenario    | SCN-AUTH-001, SCN-UX-002                             |
| Related Requirement | REQ-AUTH-001                                         |
| Risk Level          | High                                                 |
| Test Design Method  | Clarification-Driven + Exploratory                   |
| Test Type           | Functional / Negative                                |
| Priority            | High                                                 |

#### Preconditions

- Relay is accessible.
- An existing user account is available.
- The tester is not authenticated.
- The existing account's email address is known.

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
8. Observe the registration result and any error message displayed.

#### Expected Result

- Observe whether registration is accepted or rejected when an existing email address is submitted.
- Record the actual application response and any error feedback displayed.
- Determine whether a second account is created using the existing email address.
- The definitive expected behavior requires clarification because duplicate account behavior is not specified by the available requirements.

### TC-AUTH-001-04 — Registration Password Confirmation Validation

| Field               | Value                                                       |
| ------------------- | ----------------------------------------------------------- |
| Test Case ID        | TC-AUTH-001-04                                              |
| Title               | Verify password confirmation validation during registration |
| Related Scenario    | SCN-AUTH-001, SCN-UX-002                                    |
| Related Requirement | REQ-AUTH-001                                                |
| Risk Level          | High                                                        |
| Test Design Method  | Clarification-Driven + Exploratory                          |
| Test Type           | Functional / Negative                                       |
| Priority            | High                                                        |

#### Preconditions

- Relay is accessible.
- The tester is not authenticated.
- The test email address has not been registered previously.

#### Test Data

| Data             | Value                                        |
| ---------------- | -------------------------------------------- |
| Name             | Valid test user name                         |
| Email            | Unique test email address                    |
| Password         | Valid test password                          |
| Confirm Password | A password different from the password field |

#### Steps

1. Open the Relay application.
2. Navigate to the registration page.
3. Enter a valid name.
4. Enter a unique email address.
5. Enter a valid password in the "Password" field.
6. Enter a different password in the "Confirm password" field.
7. Click the "Create account" button.
8. Observe the registration result and any error message displayed.

#### Expected Result

- Observe the registration behavior when the password and confirm password values do not match.
- Record whether registration is accepted or rejected.
- Record the actual error feedback, if any.
- The definitive expected behavior requires clarification because password confirmation behavior is not specified by the available requirements.

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

### TC-AUTH-002-02 — Required Field Validation During Login

| Field               | Value                                         |
| ------------------- | --------------------------------------------- |
| Test Case ID        | TC-AUTH-002-02                                |
| Title               | Verify required field validation during login |
| Related Scenario    | SCN-UX-002                                    |
| Related Requirement | REQ-AUTH-002, REQ-AUTH-006                    |
| Risk Level          | High                                          |
| Test Design Method  | Requirement-Based + Exploratory               |
| Test Type           | Functional / Negative                         |
| Priority            | High                                          |

#### Preconditions

- Relay is accessible.
- The tester is not authenticated.

#### Test Data

| Data        | Value                                           |
| ----------- | ----------------------------------------------- |
| Email       | Registered test user's email, or empty          |
| Password    | Registered test user's valid password, or empty |
| Empty Field | Email and/or password intentionally left empty  |

#### Steps

1. Open the Relay application.
2. Verify that the login page is displayed.
3. Leave both the email and password fields empty.
4. Click the "Sign in" button.
5. Observe which field receives validation feedback and the message displayed.
6. Enter a valid email address while leaving the password field empty.
7. Click the "Sign in" button.
8. Observe the validation feedback displayed.
9. Enter a valid password while leaving the email field empty.
10. Click the "Sign in" button.
11. Observe the validation feedback displayed.

#### Expected Result

- Login is not completed when a required authentication field is left empty.
- The application displays the validation tooltip "Please fill out this field." for an empty required authentication form field.
- When both fields are empty, validation feedback is observed on the email field first.
- When only the password field is empty, validation feedback is associated with the password field.
- When only the email field is empty, validation feedback is associated with the email field.

### TC-AUTH-003-01 — Login with an Invalid Password

| Field               | Value                           |
| ------------------- | ------------------------------- |
| Test Case ID        | TC-AUTH-003-01                  |
| Title               | Login with an invalid password  |
| Related Scenario    | SCN-AUTH-003, SCN-UX-002        |
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
5. Click the "Sign in" button.
6. Observe the result of the login attempt and any error message displayed.

#### Expected Result

- Authentication does not succeed with the provided invalid credentials.
- The user does not enter an authenticated state.
- The application provides error feedback for the failed login attempt.
- The exact error message is not specified by the available requirements and must be recorded during execution.

### TC-AUTH-003-02 — Login with an Unknown Account

| Field               | Value                           |
| ------------------- | ------------------------------- |
| Test Case ID        | TC-AUTH-003-02                  |
| Title               | Login with an unknown account   |
| Related Scenario    | SCN-AUTH-003, SCN-UX-002        |
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
5. Click the "Sign in" button.
6. Observe the result of the login attempt and any error message displayed.

#### Expected Result

- Authentication does not succeed with the provided invalid credentials.
- The user does not enter an authenticated state.
- The application provides error feedback for the failed login attempt.
- The exact error message is not specified by the available requirements and must be recorded during execution.

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

### TC-AUTH-005-01 — Access Protected Chat Without Authentication

| Field               | Value                                        |
| ------------------- | -------------------------------------------- |
| Test Case ID        | TC-AUTH-005-01                               |
| Title               | Access Protected Chat Without Authentication |
| Related Scenario    | SCN-AUTH-005                                 |
| Related Requirement | REQ-AUTH-004, REQ-AUTH-005                   |
| Risk Level          | High                                         |
| Test Design Method  | Requirement-Based + Risk-Based               |
| Test Type           | Functional / Negative                        |
| Priority            | High                                         |

#### Preconditions

- The user is logged out of Relay.
- No valid authenticated session is available in the browser.
- The Relay application is accessible.

#### Test Data

| Data                 | Value           |
| -------------------- | --------------- |
| Protected Route      | `/chat`         |
| Authentication State | Unauthenticated |

#### Steps

1. Open Relay in a browser where no authenticated session is available.
2. Navigate directly to `/chat`.
3. Observe the resulting page and URL.
4. Verify whether protected chat content is accessible.

#### Expected Result

- The unauthenticated user cannot access protected chat functionality.
- The application redirects the user to `/login`, consistent with the observed application behavior.
- Protected conversation content is not displayed to the unauthenticated user.

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

### TC-UX-001-01 — Verify Empty Conversation List

| Field               | Value                          |
| ------------------- | ------------------------------ |
| Test Case ID        | TC-UX-001-01                   |
| Title               | Verify empty conversation list |
| Related Scenario    | SCN-UX-001                     |
| Related Requirement | REQ-UX-005                     |
| Risk Level          | Low                            |
| Test Design Method  | Requirement-Based + Risk-Based |
| Test Type           | Functional / Positive          |
| Priority            | Low                            |

#### Preconditions

- Relay is accessible.
- A registered user account is available.
- The user has no conversations associated with their account.
- The user's valid credentials are available.

#### Test Data

| Data              | Value                                   |
| ----------------- | --------------------------------------- |
| User              | User A                                  |
| Conversation Data | No conversations associated with User A |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Verify that the chat page is displayed.
4. Observe the conversation list.
5. Verify how the application represents the absence of conversations.

#### Expected Result

- The conversation list is displayed.
- The application provides an appropriate representation of the empty conversation list.
- The exact content and wording of the empty state are subject to clarification if not defined by the available documentation.

### TC-UX-001-02 — Verify Empty Conversation Message History

| Field               | Value                                     |
| ------------------- | ----------------------------------------- |
| Test Case ID        | TC-UX-001-02                              |
| Title               | Verify empty conversation message history |
| Related Scenario    | SCN-UX-001                                |
| Related Requirement | REQ-UX-005                                |
| Risk Level          | Low                                       |
| Test Design Method  | Requirement-Based + Risk-Based            |
| Test Type           | Functional / Positive                     |
| Priority            | Low                                       |

#### Preconditions

- Relay is accessible.
- User A and User B are registered users.
- An existing 1-on-1 conversation between User A and User B is available.
- The conversation contains no messages.
- User A is authorized to access the conversation.
- User A's valid credentials are available.

#### Test Data

| Data                         | Value       |
| ---------------------------- | ----------- |
| User                         | User A      |
| Conversation Participant     | User B      |
| Conversation Message History | No messages |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Verify that the chat page is displayed.
4. Open the existing conversation with User B.
5. Observe the message history area.
6. Verify how the application represents the absence of messages.

#### Expected Result

- The selected conversation is displayed.
- No message entries are displayed in the conversation history.
- The application provides an appropriate representation of the empty message history.
- The exact content and wording of the empty state are subject to clarification if not defined by the available documentation.

### TC-UX-002-01 — Recover from a Failed Login Attempt

| Field               | Value                                  |
| ------------------- | -------------------------------------- |
| Test Case ID        | TC-UX-002-01                           |
| Title               | Recover from a failed login attempt    |
| Related Scenario    | SCN-UX-002, SCN-AUTH-002, SCN-AUTH-003 |
| Related Requirement | REQ-UX-006, REQ-AUTH-002               |
| Risk Level          | Medium                                 |
| Test Design Method  | Requirement-Based + Risk-Based         |
| Test Type           | Functional / Negative → Positive       |
| Priority            | Medium                                 |

#### Preconditions

- Relay is accessible.
- A registered user account is available.
- The tester is not authenticated.
- The registered user's valid credentials are known.

#### Test Data

| Data             | Value                                   |
| ---------------- | --------------------------------------- |
| Email            | Registered test user's email            |
| Invalid Password | Incorrect password                      |
| Valid Password   | Registered test user's correct password |

#### Steps

1. Open the Relay application.
2. Verify that the login page is displayed.
3. Enter the registered user's email address.
4. Enter an incorrect password.
5. Click the "Sign in" button.
6. Observe the login result and any error feedback displayed.
7. Replace the incorrect password with the registered user's valid password.
8. Click the "Sign in" button.
9. Observe the login result.
10. Verify the authentication state after the second login attempt.
11. Verify whether the protected chat functionality is accessible.

#### Expected Result

- The first login attempt does not authenticate the user.
- Error feedback is provided for the failed login attempt.
- The user can correct the password and submit the login form again.
- The second login attempt authenticates the user successfully.
- The protected chat functionality is accessible after successful authentication.
- The exact error message for the failed login attempt is not prescribed by the available requirements.

### TC-UX-003-01 — Verify Light and Dark Mode

| Field               | Value                      |
| ------------------- | -------------------------- |
| Test Case ID        | TC-UX-003-01               |
| Title               | Verify light and dark mode |
| Related Scenario    | SCN-UX-003                 |
| Related Requirement | REQ-UX-001, REQ-UX-002     |
| Risk Level          | Low                        |
| Test Design Method  | Requirement-Based          |
| Test Type           | Functional / Positive      |
| Priority            | Low                        |

#### Preconditions

- Relay is accessible.
- A registered user account is available.
- The user's valid credentials are available.
- The user can access the main application screens.

#### Test Data

| Data              | Value                                                |
| ----------------- | ---------------------------------------------------- |
| User              | User A                                               |
| Theme 1           | Light mode                                           |
| Theme 2           | Dark mode                                            |
| Application Areas | Conversation list, conversation panel, message input |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Verify that the main application interface is displayed.
4. Identify the currently selected theme.
5. Switch to light mode if it is not already active.
6. Observe the appearance of the conversation list, conversation panel, and message input.
7. Verify that light mode is applied to the observed application areas.
8. Switch to dark mode.
9. Observe the appearance of the same application areas.
10. Verify that dark mode is applied to the observed application areas.
11. Switch back to light mode.
12. Verify that the application returns to light mode.
13. Navigate between the conversation list and an available conversation.
14. Observe the theme applied across the main application screens.

#### Expected Result

- Light mode is available and can be selected.
- Dark mode is available and can be selected.
- The selected theme is applied to the observed core application areas.
- Switching from light mode to dark mode changes the displayed theme accordingly.
- Switching from dark mode to light mode restores the light theme.
- The selected theme remains visually consistent across the observed main application screens.

### TC-UX-004-01 — Verify Theme Persistence After Refresh and Navigation

| Field               | Value                                                 |
| ------------------- | ----------------------------------------------------- |
| Test Case ID        | TC-UX-004-01                                          |
| Title               | Verify theme persistence after refresh and navigation |
| Related Scenario    | SCN-UX-004                                            |
| Related Requirement | REQ-UX-003                                            |
| Risk Level          | Low                                                   |
| Test Design Method  | Requirement-Based                                     |
| Test Type           | Functional / Positive                                 |
| Priority            | Low                                                   |

#### Preconditions

- Relay is accessible.
- A registered user account is available.
- The user's valid credentials are available.
- The user can access the main application screens.

#### Test Data

| Data              | Value                                    |
| ----------------- | ---------------------------------------- |
| User              | User A                                   |
| Selected Theme    | Dark mode                                |
| Application Areas | Conversation list and conversation panel |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Verify that the main application interface is displayed.
4. Select dark mode.
5. Verify that dark mode is applied to the main application interface.
6. Refresh the page.
7. Observe the theme applied after the page reloads.
8. Navigate between the conversation list and an available conversation.
9. Observe the theme applied after navigation.
10. Verify that the displayed theme remains consistent with the selected theme.

#### Expected Result

- Dark mode is applied after it is selected.
- Dark mode remains selected and displayed after page refresh.
- Dark mode remains selected and displayed after navigation between the observed application areas.
- The selected theme and the displayed theme remain consistent.

### TC-UX-004-02 — Verify Theme Persistence After Logout and Re-Login

| Field               | Value                                              |
| ------------------- | -------------------------------------------------- |
| Test Case ID        | TC-UX-004-02                                       |
| Title               | Verify theme persistence after logout and re-login |
| Related Scenario    | SCN-UX-004                                         |
| Related Requirement | REQ-UX-003                                         |
| Risk Level          | Low                                                |
| Test Design Method  | Requirement-Based + Risk-Based                     |
| Test Type           | Functional / Positive                              |
| Priority            | Low                                                |

#### Preconditions

- Relay is accessible.
- A registered user account is available.
- The user's valid credentials are available.
- The user can access the main application screens.

#### Test Data

| Data           | Value     |
| -------------- | --------- |
| User           | User A    |
| Selected Theme | Dark mode |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Verify that the main application interface is displayed.
4. Select dark mode.
5. Verify that dark mode is applied.
6. Log out from Relay.
7. Sign in again as User A using valid credentials.
8. Observe the theme applied to the main application interface.
9. Verify whether the displayed theme matches the previously selected theme.

#### Expected Result

- Dark mode is applied before logout.
- The user can log out and sign in again successfully.
- After re-login, the displayed theme remains consistent with the previously selected dark mode.
- The theme preference persists across the logout and re-login flow.

### TC-UX-005-01 — Verify Responsive Layout on Desktop

| Field               | Value                               |
| ------------------- | ----------------------------------- |
| Test Case ID        | TC-UX-005-01                        |
| Title               | Verify responsive layout on desktop |
| Related Scenario    | SCN-UX-005                          |
| Related Requirement | REQ-UX-004                          |
| Risk Level          | Medium                              |
| Test Design Method  | Requirement-Based + Risk-Based      |
| Test Type           | Functional / Positive               |
| Priority            | Medium                              |

#### Preconditions

- Relay is accessible.
- A registered user account is available.
- The user's valid credentials are available.
- At least one existing conversation is available to the user.

#### Test Data

| Data              | Value                                                |
| ----------------- | ---------------------------------------------------- |
| User              | User A                                               |
| Viewport          | Representative desktop viewport: 1366 × 768 pixels   |
| Application Areas | Conversation list, conversation panel, message input |

#### Steps

1. Open the Relay application in a desktop browser.
2. Set the browser viewport to 1366 × 768 pixels.
3. Sign in as User A using valid credentials.
4. Verify that the main application interface is displayed.
5. Observe the conversation list.
6. Verify that the conversation list can be accessed and its entries can be selected.
7. Open an existing conversation.
8. Observe the message area and verify that existing messages can be viewed.
9. Observe the message input and verify that it can be accessed and used to enter text.
10. Inspect the main application layout for overlapping or clipped elements that prevent interaction.

#### Expected Result

- Relay's main application interface remains usable at the selected desktop viewport.
- The conversation list can be accessed and a conversation can be selected.
- The message area allows the user to view the selected conversation's messages.
- The message input can be accessed and used to enter text.
- No layout issue prevents interaction with the tested application areas.
- This test uses a representative desktop viewport; it does not establish the product's official responsive breakpoints.

### TC-UX-005-02 — Verify Responsive Layout on Mobile

| Field               | Value                              |
| ------------------- | ---------------------------------- |
| Test Case ID        | TC-UX-005-02                       |
| Title               | Verify responsive layout on mobile |
| Related Scenario    | SCN-UX-005                         |
| Related Requirement | REQ-UX-004                         |
| Risk Level          | Medium                             |
| Test Design Method  | Requirement-Based + Risk-Based     |
| Test Type           | Functional / Positive              |
| Priority            | Medium                             |

#### Preconditions

- Relay is accessible.
- A registered user account is available.
- The user's valid credentials are available.
- At least one existing conversation is available to the user.
- A mobile browser or browser viewport configured to represent a mobile screen is available.

#### Test Data

| Data              | Value                                                |
| ----------------- | ---------------------------------------------------- |
| User              | User A                                               |
| Viewport          | Representative mobile viewport: 390 × 844 pixels     |
| Application Areas | Conversation list, conversation panel, message input |

#### Steps

1. Open Relay in a mobile browser or configure the browser viewport to 390 × 844 pixels.
2. Sign in as User A using valid credentials.
3. Verify that the main application interface is displayed.
4. Observe how the conversation list is presented on the mobile viewport.
5. Verify that the conversation list can be accessed and a conversation can be selected.
6. Open an existing conversation.
7. Observe the message area and verify that existing messages can be viewed.
8. Observe the message input and verify that it can be accessed and used to enter text.
9. Inspect the layout for overlapping, clipping, or horizontal overflow that prevents interaction with the tested application areas.
10. Verify that the tested core functionality remains accessible on the mobile viewport.

#### Expected Result

- Relay's main application interface remains usable at the selected mobile viewport.
- The conversation list can be accessed and a conversation can be selected.
- The message area allows the user to view the selected conversation's messages.
- The message input can be accessed and used to enter text.
- No layout issue prevents interaction with the tested application areas.
- This test uses a representative mobile viewport; it does not establish the product's official responsive breakpoints.
