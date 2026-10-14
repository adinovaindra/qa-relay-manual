# Authentication Defect Reports

## Purpose

This document contains defect reports related to Relay authentication functionality, including registration, login, logout, and authentication-related validation.

Each defect is documented with its reproduction steps, expected and actual results, supporting evidence, severity, priority, status, and traceability to the relevant test artifacts.

---

## BUG-001 — Duplicate Email Error Message Missing Trailing Period

| Field                    | Value                                                                                                                         |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------- |
| Defect ID                | BUG-001                                                                                                                       |
| Jira Issue               | [RQA-6](https://adinovapramono69.atlassian.net/browse/RQA-6)                                                                  |
| Title                    | Duplicate Email Error Message Missing Trailing Period                                                                         |
| Functional Area          | Authentication / Registration                                                                                                 |
| Related Test Case        | [TC-AUTH-001-03](../test-design/test-cases/authentication.md#tc-auth-001-03--registration-with-an-existing-email-address)     |
| Related Requirement      | [REQ-AUTH-001](../docs/02-requirements.md)                                                                                    |
| Related Execution Record | [TC-AUTH-001-03 Execution Record](../execution/authentication.md#tc-auth-001-03--registration-with-an-existing-email-address) |
| Severity                 | Low                                                                                                                           |
| Priority                 | Low                                                                                                                           |
| Status                   | Open                                                                                                                          |

### Description

When a user attempts to register using an email address that is already registered, Relay displays an error message that does not exactly match the message specified in REQ-AUTH-001.

The displayed message is missing the trailing period required by the documented requirement.

### Preconditions

- Relay is accessible.
- A user account associated with the test email address already exists.
- The tester is not authenticated.

### Test Data

| Data             | Value             |
| ---------------- | ----------------- |
| Email            | bob@example.com   |
| Name             | Bob               |
| Password         | password123       |
| Confirm Password | Matching password |

### Steps to Reproduce

1. Open the Relay application.
2. Navigate to the registration page.
3. Enter valid registration data.
4. Submit the registration form.
5. Observe the error message displayed by the application.

### Expected Result

The application rejects the registration attempt and displays the exact error message specified in REQ-AUTH-001:

`An account with this email already exists.`

The message must include a period at the end.

### Actual Result

The application displays the following message:

`An account with this email already exists`

The message does not include the required trailing period.

The registration form remains visible after the error message appears, and the previously entered form data remains displayed.

### Evidence

- Screenshot: [`TC-AUTH-001-03-duplicate-email-error.png`](../evidence/authentication/TC-AUTH-001-03-duplicate-email-error.png)

The screenshot supports the observed error message and the visible registration form after the error appears.

### Impact Assessment

The displayed error message does not exactly match the documented requirement. The observed discrepancy is limited to punctuation in the error message.

No additional functional impact has been established from the available evidence.

### Status and Verification Notes

- **Current Status:** Open
- **Retest:** Not performed — outside this portfolio scope
- **Fix Verification:** Not performed — no fix verification is included in this portfolio deliverables

The defect remains open because no verified fix is available within this portfolio project. Retesting after a fix is not required for this portfolio completion.

Backend account creation was not independently verified. The screenshot does not establish whether the application created a new account despite displaying the duplicate-email error.

### Traceability

`REQ-AUTH-001` → `TC-AUTH-001-03` → Execution Record → `BUG-001`

---

## BUG-002 — Generic Login Error Message Missing Trailing Period

| Field                    | Value                                                                                                                              |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------- |
| Defect ID                | BUG-002                                                                                                                            |
| Jira Issue               | [RQA-7](https://adinovapramono69.atlassian.net/browse/RQA-7)                                                                       |
| Title                    | Generic Login Error Message Missing Trailing Period                                                                               |
| Functional Area          | Authentication / Login                                                                                                             |
| Related Test Cases       | [TC-AUTH-003-01](../test-design/test-cases/authentication.md#tc-auth-003-01--login-with-an-invalid-password), [TC-AUTH-003-02](../test-design/test-cases/authentication.md#tc-auth-003-02--login-with-an-unknown-account) |
| Related Requirement      | [REQ-AUTH-002](../docs/02-requirements.md), [REQ-AUTH-007](../docs/02-requirements.md)                                                                                         |
| Related Execution Record | [TC-AUTH-003-01 Execution Record](../execution/authentication.md#tc-auth-003-01--login-with-an-invalid-password), [TC-AUTH-003-02 Execution Record](../execution/authentication.md#tc-auth-003-02--login-with-an-unknown-account) |
| Severity                 | Low                                                                                                                                |
| Priority                 | Low                                                                                                                                |
| Status                   | Open                                                                                                                               |

### Description

When a login attempt fails because the password is incorrect or the email address is not registered, Relay displays a generic error message that does not exactly match the message specified in REQ-AUTH-007.

The displayed message is missing the trailing period required by the documented requirement.

### Preconditions

- Relay is accessible.
- The tester is not authenticated.
- A registered user account is available for the invalid-password scenario.
- The test email address is not associated with a registered account for the unknown-account scenario.

### Test Data

| Data               | Value                                         |
| ------------------ | --------------------------------------------- |
| Registered Email   | bob@example.com                               |
| Incorrect Password | password124                                   |
| Unknown Email      | invalid@example.com                           |
| Test Password      | password123                                   |

### Steps to Reproduce

**Scenario A — Invalid Password**

1. Open the Relay application.
2. Navigate to the login page.
3. Enter the registered user's email address.
4. Enter an incorrect password.
5. Click the "Sign in" button.
6. Observe the error message displayed by the application.

**Scenario B — Unknown Account**

1. Open the Relay application.
2. Navigate to the login page.
3. Enter an email address that is not associated with a registered account.
4. Enter a test password.
5. Click the "Sign in" button.
6. Observe the error message displayed by the application.

### Expected Result

For both scenarios, the application displays the exact generic error message specified in REQ-AUTH-007:

`Invalid email or password.`

The message must include a period at the end and must not reveal whether the email address is registered.

### Actual Result

For both scenarios, the application displays the following message:

`Invalid email or password`

The message does not include the required trailing period.

### Evidence

- Screenshot: [`TC-AUTH-003-01-wrong-password-response.png`](../evidence/authentication/TC-AUTH-003-01-wrong-password-response.png)
- Screenshot: [`TC-AUTH-003-02-invalid-email-response.png`](../evidence/authentication/TC-AUTH-003-02-invalid-email-response.png)

The screenshots support the observed error messages in both login scenarios.

### Impact Assessment

The displayed error message does not exactly match the documented requirement. The observed discrepancy is limited to punctuation in the generic login error message.

No additional functional impact has been established from the available evidence.

### Status and Verification Notes

- **Current Status:** Open
- **Retest:** Not performed — outside this portfolio scope
- **Fix Verification:** Not performed — no fix verification is included in this portfolio deliverables

The defect remains open because no verified fix is available within this portfolio project. Retesting after a fix is not required for this portfolio completion.

Backend authentication handling and the underlying implementation were not independently verified. The available evidence confirms the displayed messages but does not establish whether both scenarios share the same underlying implementation.

### Traceability

`REQ-AUTH-002` / `REQ-AUTH-007` → `TC-AUTH-003-01` / `TC-AUTH-003-02` → Execution Records → `BUG-002`

---

## Other Authentication Defects

No other authentication defects are documented in this file at this time.
