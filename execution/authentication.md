# Authentication — Test Execution

## Overview

This document records formal test execution results for the Authentication functional area of the Relay application.

Execution records reference the corresponding test cases and document observed behavior, verdicts, and supporting evidence.

Only test cases that have actually been executed are recorded as formal execution results.

## Execution Summary

| Metric | Count |
|---|---:|
| Test Cases Executed | 1 |
| Passed | 1 |
| Failed | 0 |
| Blocked | 0 |
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