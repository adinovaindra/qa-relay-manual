# Relay — Final Test Summary

## 1. Summary

Formal manual execution is complete for all **32 defined test cases** in the current test suite. The recorded results are **29 PASS** and **3 FAIL**. The three failed test cases map to **two documented defects**, both currently Open.

These results describe only the defined test cases executed within the documented scope. They do not establish that every Relay feature, workflow, browser/device combination, or internal system component has been tested, nor that the application is defect-free.

## 2. Scope and Approach

Testing focused on selected observable UI behavior for these functional areas:

- Authentication: registration, login, logout, and protected-page behavior.
- Authorization: selected UI behavior for an authorized participant and visible message attribution.
- Conversations: access, creation, displayed conversation information, and ordering by latest activity.
- Messaging: sending and displaying text messages, message history and persistence, ordering, automatic scrolling, date separators, and prevention of empty/whitespace-only message submission through the UI.
- User Experience: empty states, recovery from an unsuccessful login attempt, theme behavior and persistence, and selected desktop/mobile viewport behavior.

The approach was black-box manual testing based on observable application behavior and documented requirements/contracts. Expected results were assessed against the referenced requirement or explicitly defined test objective. Execution records are maintained by functional area; exploratory observations are documented separately and are not included in the 32 formal execution results.

This was a selected-scope functional exercise, not exhaustive testing. Source-code changes, waiting for a fix/build, retesting after a fix, and regression testing after a fix were outside this activity.

## 3. Execution Results

| Functional area                         | Executed |   PASS |  FAIL | Result note                                                                     |
| --------------------------------------- | -------: | -----: | ----: | ------------------------------------------------------------------------------- |
| [Authentication](./authentication.md)   |       10 |      7 |     3 | Three error-message punctuation mismatches                                      |
| [Authorization](./authorization.md)     |        2 |      2 |     0 | Selected authorized-user UI behavior only                                       |
| [Conversations](./conversations.md)     |        4 |      4 |     0 | Selected conversation access, creation, list information, and ordering behavior |
| [Messaging](./messaging.md)             |        7 |      7 |     0 | Selected message submission and display behavior                                |
| [User Experience](./user-experience.md) |        9 |      9 |     0 | Selected empty/error states, themes, and viewport checks                        |
| **Total**                               |   **32** | **29** | **3** | **All currently defined test cases executed**                                   |

The area totals reconcile to the individual execution records and the test case index. A PASS indicates that the recorded expected result was met for that test under the conditions executed; it is not a general assurance about untested behavior or internal implementation.

## 4. Failed Test Cases and Open Defects

All three failed executions concern a missing trailing period in a displayed error message. The documented requirements specify the punctuation, and the execution records describe the observed mismatch.

| Failed test case                                                                                                            | Observation against requirement                                                   | Defect                                                                                                                                                                                                                                 | Status |
| --------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ |
| [`TC-AUTH-001-03`](../test-design/test-cases/authentication.md#tc-auth-001-03--registration-with-an-existing-email-address) | Duplicate-email message omits the required trailing period in `REQ-AUTH-001`      | [`BUG-001`](../defect-reports/authentication.md#bug-001--duplicate-email-error-message-missing-trailing-period) / [RQA-6](https://adinovapramono69.atlassian.net/browse/RQA-6) — Duplicate Email Error Message Missing Trailing Period | Open   |
| [`TC-AUTH-003-01`](../test-design/test-cases/authentication.md#tc-auth-003-01--login-with-an-invalid-password)              | Wrong-password login message omits the required trailing period in `REQ-AUTH-007` | [`BUG-002`](../defect-reports/authentication.md#bug-002--generic-login-error-message-missing-trailing-period) / [RQA-7](https://adinovapramono69.atlassian.net/browse/RQA-7) — Generic Login Error Message Missing Trailing Period     | Open   |
| [`TC-AUTH-003-02`](../test-design/test-cases/authentication.md#tc-auth-003-02--login-with-an-unknown-account)               | Unknown-email login message omits the required trailing period in `REQ-AUTH-007`  | `BUG-002` / `RQA-7` — Generic Login Error Message Missing Trailing Period                                                                                                                                                              | Open   |

The three failed test cases are linked to two defects, not three separate defects. The [defect report](../defect-reports/authentication.md) retains the detailed reproduction steps, requirement/test-case traceability, and evidence references. The [requirements](../docs/02-requirements.md) and [test case index](../test-design/test-cases.md) provide the wider traceability context. The reported discrepancy is limited to the observed error-message punctuation; no additional functional impact or internal root cause has been established by the available evidence.

Both defects remain Open. No source-code fix or new build was produced for this activity, and no retest or post-fix regression was performed.

## 5. Verification Gaps and Untested Areas

The following are explicit limits of the verification performed:

- `REQ-AUTHZ-003` and `REQ-AUTHZ-005` are documented requirements that **have not been independently verified through formal test execution**. Their verification status remains unverified.
- The authorization executions cover selected authorized-user UI behavior and visible message attribution. They do not independently establish server-side authorization enforcement, rejection of unauthorized conversation access, or enforcement against client-supplied identity manipulation.
- UI observations do not independently verify server-side authentication/session enforcement, API contracts, database state or integrity, or internal data operations. For example, the logout/protected-page and message-attribution checks are limited to their recorded observable behavior.
- The duplicate-email and login error observations do not independently establish backend account creation or authentication handling.
- Responsive checks cover the recorded viewport conditions only. They do not establish coverage of every screen size, responsive breakpoint, browser, operating system, or device.
- The defined test suite and exploratory sessions do not constitute exhaustive coverage of every Relay feature, state, input combination, integration, or failure mode.
- Retest after a fix and regression testing after a fix were not performed and are outside this activity's agreed scope.

## 6. Limitations and Residual Risk

The results are bounded by the selected test cases, their documented preconditions and data, the observable application behavior, and the evidence recorded during execution. The execution records do not consistently identify a specific application build/version, so the results should not be interpreted as a certification of a particular release artifact beyond the context recorded in those records.

The unverified authorization requirements and lack of independent API/server/database verification leave residual uncertainty about enforcement and system state beyond the UI. Selected viewport checks leave compatibility uncertainty outside the tested conditions. The two open authentication defects also remain unresolved within this activity.

A functional area with no recorded failed test case or documented defect report should not be interpreted as defect-free. Likewise, a passing UI observation must not be generalized into a claim that the corresponding backend or security control has been independently verified.

## 7. Conclusion

Within the defined scope, **32 of 32 formal test cases were executed, with 29 PASS and 3 FAIL**. The failures are traceable to two open defects involving missing trailing punctuation in authentication error messages. The other recorded test cases passed under their executed conditions.

The results provide evidence about selected observable Relay UI behavior, but they do not demonstrate exhaustive application coverage or independently verify internal API, server-side authorization, database integrity, or comprehensive security behavior. The two defects remain Open, and the documented verification gaps and residual risks should be considered when interpreting these results.
