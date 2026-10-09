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

## 5. Test Case Repository

Detailed test cases are organized by functional area to improve navigation, review, and maintenance.

| Functional Area | File | Test Cases |
|---|---|---|
| Authentication | [authentication.md](test-cases/authentication.md) | 10 |
| Authorization | [authorization.md](test-cases/authorization.md) | 2 |
| Conversations | [conversations.md](test-cases/conversations.md) | 5 |
| Messaging | [messaging.md](test-cases/messaging.md) | 6 |
| User Experience | [user-experience.md](test-cases/user-experience.md) | 8 |

**Total: 31 test cases**

Each file contains the detailed test cases for its respective functional area. Test case IDs and traceability mappings are maintained across the repository.

Test execution results are documented separately from test case design.