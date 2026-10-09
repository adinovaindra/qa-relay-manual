# Relay — End-to-End Manual QA

## Project Overview

This repository contains a self-directed QA portfolio project for **Relay**, a full-stack 1-on-1 messaging application.

The project demonstrates a structured manual QA workflow, from requirement analysis and risk assessment through test design, exploratory testing, test execution, defect reporting, retesting, regression testing, and test summary.

The project focuses on evidence-based testing, requirement traceability, risk-based prioritization, and clear separation between observed behavior, assumptions, and confirmed defects.

## System Under Test

- **Application:** Relay
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
- Theme behavior
- Responsive behavior
- Message history behavior

Testing activities prioritize functionality and risks that may affect authentication, authorization, conversation access, message integrity, and session behavior.

The scope is limited to observable application behavior. Server-side implementation details and API-level verification are not claimed as verified unless supported by separate technical evidence.

Detailed requirements, risk assessments, scenarios, test cases, exploratory session notes, and supporting evidence are maintained in the project artifacts.

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
│   ├── 01-product-scope.md
│   ├── 02-requirements.md
│   └── 03-risk-assestment.md
├── evidence/
│    └── exploratory testing screenshots
├── execution/
│   └── exploratory-session-notes.md
├── test-design/
|   ├── test-cases/
|   |   ├── authentication.md
|   |   ├── authorization.md
|   |   ├── conversations.md
|   |   ├── messaging.md
|   |   └── user-experience.md    
│   ├── scenarios.md
│   └── test-cases.md
└── README.md
```

## Project Status

**Status: In Progress**

Requirements, risk assessment, test scenarios, test cases, and exploratory testing notes are documented in the repository.

Formal test execution, defect reporting, retesting, regression testing, and test summary activities will be documented as they are performed and supported by evidence.

No test result or defect is considered confirmed without appropriate supporting evidence.

## Evidence and Traceability

The project uses requirement IDs, scenario IDs, and test case IDs to support traceability across QA artifacts.

Exploratory observations are documented separately from formal test execution results. Unspecified expected behavior is treated as a clarification requirement rather than automatically classified as a defect.

Screenshots are maintained as supporting evidence for the observations documented in exploratory session notes.

## Limitations

This is a self-directed portfolio project, not professional QA work performed for an employer.

The project demonstrates QA methods and reasoning applied to the Relay application within the documented scope. It does not claim production defect statistics, complete coverage of every possible behavior, or verification of internal server-side implementation details.

## Author

**Adinova Indra Permana**

Self-directed QA portfolio project focused on manual testing and progression toward Technical QA.
