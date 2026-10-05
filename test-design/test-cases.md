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

| Field | Value |
|---|---|
| Test Case ID | TC-AUTH-004-01 |
| Title | Logout from an authenticated session |
| Related Scenario | SCN-AUTH-004 |
| Related Requirement | REQ-AUTH-003 |
| Risk Level | High |
| Test Design Method | Requirement-Based |
| Test Type | Functional / Positive |
| Priority | High |

#### Preconditions

- Relay is accessible.
- A registered user account is available.
- The tester is authenticated successfully.

#### Test Data

| Data | Value |
|---|---|
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

