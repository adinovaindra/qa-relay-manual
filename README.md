# Relay — End-to-End Manual QA

## Project Overview

This repository contains a self-directed QA portfolio project for **Relay**, a full-stack 1-on-1 messaging web application.

The project demonstrates a structured manual QA workflow, from requirement analysis and risk assessment through test design, exploratory testing, formal test execution, defect reporting, retesting, regression testing, and test summary.

The project focuses on evidence-based testing, requirement traceability, risk-based prioritization, and a clear separation between observed behavior, assumptions, unspecified behavior, and confirmed defects.

## System Under Test

- **Application:** Relay
- **Application Type:** Full-stack 1-on-1 messaging web application
- **Testing Type:** Manual QA
- **Project Type:** Self-directed QA portfolio project
- **Testing Approach:** Black-box testing based on observable application behavior

## QA Scope

The testing scope covers core Relay functionality, including:

- Authentication
- Authorization
- 1-on-1 conversations
- Messaging
- Message persistence
- Conversation list behavior
- UI states
- Theme behavior and persistence
- Responsive desktop and mobile behavior
- Message history behavior

Testing activities prioritize functionality and risks that may affect authentication, authorization, conversation access, message integrity, and session behavior.

The scope is limited to observable application behavior. Server-side implementation details, database integrity, and API-level behavior are not claimed as verified unless supported by separate technical evidence.

Detailed product scope, requirements, risk assessments, scenarios, test cases, exploratory session notes, formal execution records, and supporting evidence are maintained in the project artifacts.

See [Product & QA Scope](docs/01-product-scope.md) for the detailed scope and limitations.

## QA Workflow

The intended end-to-end QA workflow is:

```text
Requirement Analysis
        ↓
Risk Assessment
        ↓
Test Scenario Design
        ↓
Test Case Design
        ↓
Test Execution
        ↓
Evidence Collection
        ↓
Defect Reporting
        ↓
Retesting
        ↓
Regression Testing
        ↓
Test Summary
```

The workflow represents the project's QA process. Individual activities and completion status are documented separately; the workflow diagram does not imply that every activity has been completed.

## Tools

- Visual Studio Code
- Git
- GitHub
- Markdown
- Web Browser
- Chrome DevTools
- Jira

Tools are used where appropriate to support documentation, manual testing, evidence collection, and defect-management workflow.

## Repository Structure

```text
qa-relay-manual/
├── docs/
│   ├── README.md
│   ├── 01-product-scope.md
│   ├── 02-requirements.md
│   └── 03-risk-assestment.md
├── test-design/
│   ├── README.md
│   ├── scenarios.md
│   ├── test-cases.md
│   └── test-cases/
│       ├── authentication.md
│       ├── authorization.md
│       ├── conversations.md
│       ├── messaging.md
│       └── user-experience.md
├── execution/
│   ├── README.md
│   ├── exploratory-session-notes.md
│   ├── authentication.md
│   ├── authorization.md
│   ├── conversations.md
│   ├── messaging.md
│   └── user-experience.md
├── evidence/
└── README.md
```

### Directory Guide

- `docs/` — Product scope, requirements, and risk assessment.
- `test-design/` — Test scenarios and detailed test cases organized by functional area.
- `execution/` — Formal test execution records organized by functional area, alongside exploratory testing notes.
- `evidence/` — Supporting screenshots and other evidence collected during testing.

Each documentation directory uses its own README as an entry point where appropriate. The root README provides the overall project overview and links to the key artifacts.

## Project Status

**Status: In Progress**

Product scope, requirements, risk assessment, test scenarios, detailed test cases, and exploratory testing notes are documented in the repository.

Formal test execution, defect reporting, retesting, regression testing, and test summary activities are documented as they are performed and supported by evidence.

Test results and defects are not assumed or fabricated. A test result is recorded based on actual execution, while a defect is reported only when the available requirement or contract supports the identified violation.

## Evidence and Traceability

The project uses requirement IDs, scenario IDs, and test case IDs to support traceability across QA artifacts.

Exploratory observations are documented separately from formal test execution results. When expected behavior is not sufficiently specified, the behavior is recorded for clarification or investigation rather than automatically classified as a defect.

Evidence files support the observations and execution results to which they are explicitly linked. A screenshot or recording provides context for observed behavior but does not independently establish a requirement violation without the relevant requirement or contract.

## Limitations

This is a self-directed portfolio project, not professional QA work performed for an employer.

The project demonstrates QA methods and reasoning applied to Relay within the documented scope. It does not claim production defect statistics, exhaustive coverage of every possible behavior, or verification of internal server-side implementation details unless supported by separate technical evidence.

## Related Documentation

### Product Documentation

- [Product & QA Scope](docs/01-product-scope.md)
- [Requirements](docs/02-requirements.md)
- [Risk Assessment](docs/03-risk-assestment.md)
- [Product Documentation Index](docs/README.md)

### Test Design

- [Test Scenario Design](test-design/scenarios.md)
- [Test Case Design Index](test-design/test-cases.md)
- [Test Design Index](test-design/README.md)

### Test Execution

- [Execution Index](execution/README.md)
- [Exploratory Session Notes](execution/exploratory-session-notes.md)

## Author

**Adinova Indra Permana**

Self-directed QA portfolio project focused on manual testing and progression toward Technical QA.