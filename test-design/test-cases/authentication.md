## Authentication Test Cases

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