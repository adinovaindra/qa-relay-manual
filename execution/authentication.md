# Authentication — Test Execution

## Overview

This document records formal test execution results for the Authentication functional area of the Relay application.

Execution records reference the corresponding test cases and document observed behavior, verdicts, and supporting evidence.

Only test cases that have actually been executed are recorded as formal execution results.

## Execution Summary

| Metric | Count |
|---|---:|
| Test Cases Executed | 4 |
| Passed | 2 |
| Failed | 0 |
| Blocked | 0 |
| Clarification Required | 2 |
| Not Run | Not tracked in this execution record |

*Summary reflects the execution records documented in this file and must be updated as additional test cases are executed.*

## Execution Records

### TC-AUTH-001-01 — Register with Valid Data

**Test Case Reference:** [TC-AUTH-001-01](../test-design/test-cases/authentication.md)

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

**Test Case Reference:** [TC-AUTH-001-02](../test-design/test-cases/authentication.md)

**Scenario Reference:** SCN-AUTH-001, SCN-UX-002

**Requirement Reference:** REQ-AUTH-001, REQ-AUTH-006

**Preconditions**

- Relay application is accessible.
- The tester is not authenticated.

**Expected Result**

- Registration is not completed when a required registration field is left empty.
- The application displays the validation tooltip "Please fill out this field." for an empty required authentication form field.
- When all registration fields are empty, validation feedback must identify a field that requires input.
- The exact validation order when multiple required fields are empty is not specified by the requirement.

**Actual Result**

- **All fields empty:** The browser displayed the native validation message, `Please fill out this field.`, associated with the Name field first. Registration did not proceed.
- **Email empty:** The browser displayed the native validation message, `Please fill out this field.`, associated with the Email field. Registration did not proceed.
- **Password empty:** The browser displayed the native validation message, `Please fill out this field.`, associated with the Password field. Registration did not proceed.
- **Confirm Password empty:** The browser displayed the native validation message, `Please fill out this field.`, associated with the Confirm Password field. Registration did not proceed.

**Execution Result:** PASS — Required-field validation

**Evidence**

- **Screenshot Collage:** [TC-AUTH-001-02 — Required Field Validation](../evidence/authentication/TC-AUTH-001-02-required-field-validation.png)

**Defect Reference:** None identified during this execution.

**Execution Notes**

The displayed validation feedback appeared to be native browser form validation. The execution records observed UI behavior and does not independently verify server-side validation.

The test confirms that registration was prevented when required fields were empty. The exact validation message and field-validation order are recorded as observations rather than independently verified product requirements.

### TC-AUTH-001-03 — Registration with an Existing Email Address

**Test Case Reference:** [TC-AUTH-001-03](../test-design/test-cases/authentication.md)

**Scenario Reference:** SCN-AUTH-001, SCN-UX-002

**Requirement Reference:** REQ-AUTH-001

#### Preconditions

- Relay is accessible.
- An existing user account is available.
- The tester is not authenticated.
- The existing account's email address is known.

#### Expected Result

- Observe whether registration is accepted or rejected when an existing email address is submitted.
- Record the actual application response and any error feedback displayed.
- Determine whether a second account is created using the existing email address.
- The definitive expected behavior requires clarification because duplicate account behavior is not specified by the available requirements.

**Actual Result**

- After the registration form was submitted using an existing email address, the application displayed the error message: `An account with this email already exists`.
- The application indicated that the email address was already associated with an account.

**Execution Result:** Observation Recorded — Clarification Required

**Evidence**

- **Screenshot:** [TC-AUTH-001-03 — Duplicate Email Error](../evidence/authentication/TC-AUTH-001-03-duplicate-email-error.png)

**Defect Reference:** None confirmed during this execution.

**Execution Notes**

The application displayed explicit feedback indicating that the email address already exists. This observation alone does not establish whether the behavior fully satisfies the product requirements. Independent verification of account creation was not documented during this execution.

### TC-AUTH-001-04 — Registration Password Confirmation Validation

**Test Case Reference:** [TC-AUTH-001-04](../test-design/test-cases/authentication.md)

**Scenario Reference:** SCN-AUTH-001, SCN-UX-002

**Requirement Reference:** REQ-AUTH-001

**Preconditions**

- Relay application is accessible.
- The tester is not authenticated.
- The test email address has not been registered previously.

#### Expected Result

- Observe the registration behavior when the password and confirm password values do not match.
- Record whether registration is accepted or rejected.
- Record the actual error feedback, if any.
- The definitive expected behavior requires clarification because password confirmation behavior is not specified by the available requirements.

**Actual Result**

- The Password field was populated with `password123`.
- The Confirm Password field was populated with `password124`.
- After the registration form was submitted, the application displayed the error message: `Passwords do not match.`
- The application provided explicit feedback indicating that the password values did not match.

**Execution Result:** Observation Recorded — Clarification Required

**Evidence**

- **Password Field:** [TC-AUTH-001-04 — Password123](../evidence/authentication/TC-AUTH-001-04-password123.png)
- **Confirm Password Field:** [TC-AUTH-001-04 — Password124](../evidence/authentication/TC-AUTH-001-04-password124.png)
- **Password Mismatch Error:** [TC-AUTH-001-04 — Password Mismatch](../evidence/authentication/TC-AUTH-001-04-password-mismatch.png)

**Defect Reference:** None confirmed during this execution.

**Execution Notes**

The application displayed an explicit error message when the Password and Confirm Password values differed. The observed behavior is consistent with password confirmation validation, but the available requirements do not explicitly establish the definitive expected behavior. No defect was confirmed during this execution.