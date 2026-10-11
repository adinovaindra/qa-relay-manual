# Authentication — Test Execution

## Overview

This document records formal test execution results for the Authentication functional area of the Relay application.

Execution records reference the corresponding test cases and document observed behavior, verdicts, and supporting evidence.

Only test cases that have actually been executed are recorded as formal execution results.

## Execution Summary

| Metric                 |                                Count |
| ---------------------- | -----------------------------------: |
| Test Cases Executed    |                                    8 |
| Passed                 |                                    7 |
| Failed                 |                                    1 |
| Blocked                |                                    0 |
| Clarification Required |                                    0 |
| Not Run                | Not tracked in this execution record |

_Summary reflects the execution records documented in this file and must be updated as additional test cases are executed._

## Execution Records

### TC-AUTH-001-01 — Register with Valid Data

**Test Case Reference:** [TC-AUTH-001-01](../test-design/test-cases/authentication.md#tc-auth-001-01--register-with-valid-data)

**Scenario Reference:** SCN-AUTH-001

**Requirement Reference:** REQ-AUTH-001

**Preconditions**

- Relay application is accessible.
- The test email has not been registered previously, based on the tester's knowledge before execution.
- The tester is not authenticated.

**Expected Result**

- The registration request creates a new account.
- The newly registered account can authenticate successfully.

**Actual Result**

- Before registration, a sign-in attempt using the test email failed.
- After the registration form was submitted, the application redirected to the login page without displaying a success or error message.
- A subsequent sign-in using the newly registered credentials succeeded, and the authenticated application page was displayed.

**Execution Result:** PASS

**Evidence**

- **Screen Recording:** [TC-AUTH-001-01 — Registration and Login](https://github.com/user-attachments/assets/c25b0b54-9729-4314-8733-237f74e5dec6)
- **Screenshot:** [TC-AUTH-001-01 — Successful Login](../evidence/authentication/TC-AUTH-001-01-successful-login.png)

**Defect Reference:** None identified during this execution.

**Execution Notes**

The initial sign-in attempt was an additional pre-execution validation and was not part of the formal test case steps.

The observed UI behavior supports the reported registration and authentication outcome. The test did not independently verify database state.

### TC-AUTH-001-02 — Required Field Validation During Registration

**Test Case Reference:** [TC-AUTH-001-02](../test-design/test-cases/authentication.md#tc-auth-001-02--required-field-validation-during-registration)

**Scenario Reference:** SCN-AUTH-001, SCN-UX-002

**Requirement Reference:** REQ-AUTH-001, REQ-AUTH-006

**Preconditions**

- Relay application is accessible.
- The tester is not authenticated.

**Expected Result**

- Registration is not completed when one or more required registration fields are left empty.
- The application displays the validation tooltip "Please fill out this field." on the first empty field in visual order.
- Only one validation tooltip is displayed at a time.
- When all registration fields are empty, the tooltip appears on the Name field.
- When multiple fields are empty, the tooltip appears on the empty field that comes first in visual order.

**Actual Result**

- **All fields empty:** The browser displayed the native validation message, `Please fill out this field.`, associated with the Name field first. Registration did not proceed.
- **Email empty:** The browser displayed the native validation message, `Please fill out this field.`, associated with the Email field. Registration did not proceed.
- **Password empty:** The browser displayed the native validation message, `Please fill out this field.`, associated with the Password field. Registration did not proceed.
- **Confirm Password empty:** The browser displayed the native validation message, `Please fill out this field.`, associated with the Confirm Password field. Registration did not proceed.

**Execution Result:** PASS

**Evidence**

- **Screenshot Collage:** [TC-AUTH-001-02 — Required Field Validation](../evidence/authentication/TC-AUTH-001-02-required-field-validation.png)

**Defect Reference:** None identified during this execution.

**Execution Notes**

The displayed validation feedback appeared to be native browser form validation. The execution records observed UI behavior and does not independently verify server-side validation.

The test confirms that registration was prevented when required fields were empty.

### TC-AUTH-001-03 — Registration with an Existing Email Address

**Test Case Reference:** [TC-AUTH-001-03](../test-design/test-cases/authentication.md#tc-auth-001-03--registration-with-an-existing-email-address)

**Scenario Reference:** SCN-AUTH-001, SCN-UX-002

**Requirement Reference:** REQ-AUTH-001

#### Preconditions

- Relay is accessible.
- An existing user account is available.
- The tester is not authenticated.
- The existing account's email address is known.

#### Expected Result

- Registration is rejected when the email address is already registered.
- The application displays the exact error message `An account with this email already exists.`
- The error message includes a period at the end.
- Registration does not proceed successfully.

**Actual Result:**

- The application displayed the error message `An account with this email already exists` without a trailing period.
- The registration form remained visible after the error message appeared, and the previously entered form data remained displayed.
- Backend account creation was not independently verified.

**Execution Result:** FAIL

**Evidence**

- **Screenshot:** [TC-AUTH-001-03 — Duplicate Email Error](../evidence/authentication/TC-AUTH-001-03-duplicate-email-error.png)

**Defect Reference:** [BUG-001 — Duplicate Email Error Message Missing Trailing Period](../defect-reports/authentication.md#bug-001--duplicate-email-error-message-missing-trailing-period) · [Jira RQA-6](https://adinovapramono69.atlassian.net/browse/RQA-6)

**Execution Notes:**

The observed error message does not exactly match REQ-AUTH-001, which specifies `An account with this email already exists.` including the trailing period. The screenshot supports the observed UI behavior but does not independently verify whether a new account was created in the backend.

### TC-AUTH-001-04 — Registration Password Confirmation Validation

**Test Case Reference:** [TC-AUTH-001-04](../test-design/test-cases/authentication.md#tc-auth-001-04--registration-password-confirmation-validation)

**Scenario Reference:** SCN-AUTH-001, SCN-UX-002

**Requirement Reference:** REQ-AUTH-001

**Preconditions**

- Relay application is accessible.
- The tester is not authenticated.
- The test email address has not been registered previously.

#### Expected Result

- Registration is rejected when the password and confirm password values do not match.
- The application displays the exact error message `Passwords do not match.`

**Actual Result:**

- The application displayed the error message `Passwords do not match.` when the password and confirm password values differed.
- The registration form remained visible after the validation message appeared.
- Backend account creation was not independently verified.

**Execution Result:** PASS

**Evidence**

- **Password Field:** [TC-AUTH-001-04 — Password123](../evidence/authentication/TC-AUTH-001-04-password123.png)
- **Confirm Password Field:** [TC-AUTH-001-04 — Password124](../evidence/authentication/TC-AUTH-001-04-password124.png)
- **Password Mismatch Error:** [TC-AUTH-001-04 — Password Mismatch](../evidence/authentication/TC-AUTH-001-04-password-mismatch.png)

**Defect Reference:** None identified during this execution.

**Execution Notes:**

The observed error message matches the exact message specified in REQ-AUTH-001. The registration form remained visible after the validation message appeared, supporting the expected validation behavior. Backend account creation was not independently verified.

### TC-AUTH-002-01 — Login with Valid Credentials

**Test Case Reference:** [TC-AUTH-002-01](../test-design/test-cases/authentication.md#tc-auth-002-01--login-with-valid-credentials)

**Scenario Reference:** SCN-AUTH-002

**Requirement Reference:** REQ-AUTH-002

**Preconditions**

- Relay is accessible.
- A registered user account is available.
- The tester is not authenticated.
- The account credentials are known and valid.

**Expected Result**

- The user is authenticated successfully using valid credentials.
- The user enters an authenticated state.
- The protected chat functionality is accessible to the authenticated user.

**Actual Result**

- The login attempt was submitted using an existing user account and its valid password.
- After the login button was clicked, the application redirected the user to the `/chat` page.
- The application displayed the authenticated chat page.
- The displayed user context matched the account used for the login attempt.

**Execution Result:** PASS

**Evidence**

- **Login Attempt:** [TC-AUTH-002-01 — Login Attempt](../evidence/authentication/TC-AUTH-002-01-login-attempt.png)
- **Successful Login:** [TC-AUTH-002-01 — Successful Login](../evidence/authentication/TC-AUTH-002-01-successful-login.png)

**Defect Reference:** None identified during this execution.

**Execution Notes**

The observed redirect to `/chat` and the displayed user context support the expected successful authentication outcome. The test records the observed application behavior and does not independently verify server-side session or token implementation.

### TC-AUTH-002-02 — Required Field Validation During Login

**Test Case Reference:** [TC-AUTH-002-02](../test-design/test-cases/authentication.md#tc-auth-002-02--required-field-validation-during-login)

**Scenario Reference:** SCN-UX-002

**Requirement Reference:** REQ-AUTH-002, REQ-AUTH-006

**Preconditions**

- Relay application is accessible.
- The tester is not authenticated.
- A registered user's email and password are available for test data.

**Expected Result**

- Login is not completed when one or more required login fields are left empty.
- The browser displays the validation tooltip "Please fill out this field." on the first empty required field in visual order.
- Only one validation tooltip is displayed at a time.
- When both Email and Password are empty, the tooltip appears on the Email field first.
- When only the Password field is empty, the tooltip appears on the Password field.
- When only the Email field is empty, the tooltip appears on the Email field.

**Actual Result**

- **Test Data:** Email: `bob@example.com`; Password: `password123`.
- **Variation 1 — Both fields empty:** After the Sign in button was clicked with both fields empty, the browser displayed the tooltip `Please fill out this field.` on the email field.
- **Variation 2 — Email field empty:** With the email field empty and the password field populated, the browser displayed the tooltip `Please fill out this field.` on the email field.
- **Variation 3 — Password field empty:** With the email field populated and the password field empty, the browser displayed the tooltip `Please fill out this field.` on the password field.
- No successful login was observed in these three variations.

**Execution Result:** PASS

**Evidence**

- **Both Fields Empty:** [TC-AUTH-002-02 — All Fields Empty](../evidence/authentication/TC-AUTH-002-02-all-fields-empty.png)
- **Email Field Empty:** [TC-AUTH-002-02 — Email Field Empty](../evidence/authentication/TC-AUTH-002-02-email-field-empty.png)
- **Password Field Empty:** [TC-AUTH-002-02 — Password Field Empty](../evidence/authentication/TC-AUTH-002-02-password-field-empty.png)

**Defect Reference:** None identified during this execution.

**Execution Notes**

All three executed variations behaved as expected. The browser's native required-field validation displayed the tooltip `Please fill out this field.` on the expected field for each tested variation.

The observed results support the expected validation behavior for the tested combinations. Not every possible combination of multiple empty fields was independently tested. This execution does not independently verify server-side validation or authentication handling.

### TC-AUTH-003-01 — Login with an Invalid Password

**Test Case Reference:** [TC-AUTH-003-01](../test-design/test-cases/authentication.md#tc-auth-003-01--login-with-an-invalid-password)

**Scenario Reference:** SCN-AUTH-003, SCN-UX-002

**Requirement Reference:** REQ-AUTH-002, REQ-AUTH-007

**Preconditions**

- Relay is accessible.
- A registered user account is available.
- The tester is not authenticated.
- The registered user's email address is known.

**Expected Result**

- Authentication does not succeed with the provided invalid password.
- The user does not enter an authenticated state.
- The application displays the generic error message "Invalid email or password".
- The error feedback is visible to the user.
- The error message does not reveal whether the email address is registered.

**Actual Result**

- **Test Data:** Email: `bob@example.com`; Incorrect password: `password124`.
- The login form was submitted using the registered email address and an incorrect password.
- The application displayed the error message `Invalid email or password`.
- The user remained on the `/login` page after the error message appeared.
- The application did not redirect the user to the `/chat` page.

**Execution Result:** PASS

**Evidence**

- **Wrong Password Input:** [TC-AUTH-003-01 — Wrong Password Input](../evidence/authentication/TC-AUTH-003-01-wrong-password-input.png)
- **Wrong Password Response:** [TC-AUTH-003-01 — Wrong Password Response](../evidence/authentication/TC-AUTH-003-01-wrong-password-response.png)

**Defect Reference:** None identified during this execution.

**Execution Notes**

The observed error message matches the generic error message specified in REQ-AUTH-007. The continued presence on the `/login` page and absence of redirection to `/chat` support the expected failed-authentication outcome. This execution does not independently verify server-side authentication handling or session state.

### TC-AUTH-003-02 — Login with an Unknown Account

**Test Case Reference:** [TC-AUTH-003-02](../test-design/test-cases/authentication.md#tc-auth-003-02--login-with-an-unknown-account)

**Scenario Reference:** SCN-AUTH-003, SCN-UX-002

**Requirement Reference:** REQ-AUTH-002, REQ-AUTH-007

**Preconditions**

- Relay is accessible.
- The tester is not authenticated.
- The test email address is not associated with a registered Relay account.

**Expected Result**

- Authentication does not succeed for the unknown account.
- The user does not enter an authenticated state.
- The application displays the generic error message "Invalid email or password".
- The error feedback is visible to the user.
- The error message does not reveal whether the email address is registered.

**Actual Result**

- **Test Data:** Email: `invalid@example.com`; Password: `password123`.
- The login form was submitted using the unregistered email address and the provided password.
- The application displayed the error message `Invalid email or password`.
- The user remained on the `/login` page after the error message appeared.
- The application did not redirect the user to the `/chat` page.

**Execution Result:** PASS

**Evidence**

- **Invalid Email Input:** [TC-AUTH-003-02 — Invalid Email Input](../evidence/authentication/TC-AUTH-003-02-invalid-email-input.png)
- **Invalid Email Response:** [TC-AUTH-003-02 — Invalid Email Response](../evidence/authentication/TC-AUTH-003-02-invalid-email-response.png)

**Defect Reference:** None identified during this execution.

**Execution Notes**

The observed error message matches the generic error message specified in REQ-AUTH-007 and is consistent with the message observed for an invalid password in TC-AUTH-003-01. The continued presence on the `/login` page and absence of redirection to `/chat` support the expected failed-authentication outcome. This execution does not independently verify server-side account lookup, authentication handling, or session state.
