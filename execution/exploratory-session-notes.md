# Exploratory Session Notes

## Session Information

| Field | Value |
|---|---|
| Session ID | EXP-SESSION-001 |
| Related Scenario | SCN-EXP-001 — Invalid Registration Input |
| System Under Test | Relay |
| Session Type | Exploratory Testing |
| Session Status | Initial observations documented |

## 1. Session Objective

Explore how Relay handles registration email inputs with different formats and document the observable validation responses and registration outcomes.

## 2. Exploration Notes

### Observation 1 — Email with a Trailing Dot

**Input**

`adinovapramono@yahoo.co.`

**Action**

Enter the email address in the registration form.

**Actual Result**

The browser displays the following validation tooltip:

`'.' is used at wrong position in 'yahoo.co.'.`

**Outcome**

The input is rejected by browser validation. Whether a registration request is sent has not been verified.

### Observation 2 — Email Producing an Application Error

**Input**

`adinovapramono@yahoo.co.m`

**Action**

Enter the email address and click Register.

**Actual Result**

The Relay page displays:

`invalid request data`

**Outcome**

The registration attempt produces an application-level error message. The underlying cause and the component responsible for the rejection have not been determined.

### Observation 3 — Registration with `@yaho.com`

**Input**

`adinovapramono@yaho.com`

**Action**

Enter the email address and complete registration.

**Actual Result**

Registration succeeds, and the user can enter the application.

**Outcome**

The application accepts this input and completes registration. The existence or deliverability of the email address has not been verified.

## 3. Findings

- Different email inputs produce different observable responses.
- One input is rejected by browser validation.
- Another input produces an error message on the Relay page.
- The third input is accepted and registration succeeds.

## 4. Learning

The observations show that registration validation behavior can differ depending on the input. The available evidence does not establish the exact validation rules or identify the cause of the application error.

## 5. Open Questions

- What email-format rules does Relay intend to enforce?
- What condition causes the `invalid request data` response?
- Should invalid email input produce a more specific validation message?

These questions require further investigation or requirement clarification.

## 6. Evidence

Evidence files: Not recorded in this session note.

## 7. Follow-up

- Clarify the expected email-format validation rules if the requirement or product documentation is available.
- Investigate the `invalid request data` response if useful evidence can be collected.
- Do not classify the observations as defects until an applicable requirement or other sufficient evidence establishes the expected behavior.

## Session EXP-SESSION-002 — Invalid or Expired Session

### Session Information

| Field | Value |
|---|---|
| Session ID | EXP-SESSION-002 |
| Related Scenario | SCN-EXP-002 — Invalid or Expired Session |
| System Under Test | Relay |
| Session Type | Exploratory Testing — Black-box UI |
| Session Status | Initial Exploration Completed |

### 1. Session Objective

Explore Relay's observable behavior when a user logs out and subsequently attempts to access a protected page through the normal browser flow.

### 2. Exploration Notes

#### Observation 1 — Cookie After Login

**Action:** Log in to Relay.

**Actual Result:** The `auth_token` cookie is present in the browser after login.

#### Observation 2 — Cookie After Logout

**Action:** Log out from Relay.

**Actual Result:** The `auth_token` cookie is no longer present in the browser.

#### Observation 3 — Access Chat After Logout

**Action:** Navigate to `/chat` after logging out.

**Actual Result:** The browser automatically redirects to `/login`.

### 3. Findings

- The `auth_token` cookie is present after login.
- The cookie is removed from the browser after logout.
- Accessing `/chat` through the normal browser flow after logout results in a redirect to `/login`.

### 4. Limitations

This session covers observable browser behavior only.

The session does not establish whether a previously issued JWT remains valid after logout because reuse of the old token was not tested.

The underlying enforcement mechanism responsible for the redirect has not been independently verified.

### 5. Evidence

Evidence references: Not recorded in this session note.

### 6. Follow-up / Scope Decision

The observed browser behavior is documented for Portfolio 1 — End-to-End Manual QA.

Testing the reuse of a previously issued JWT through direct API requests is outside the scope of this session and is not claimed as completed.

No defect is confirmed by the observations collected in this session.

## Session EXP-SESSION-003 — Invalid Conversation Reference

### Session Information

| Field | Value |
|---|---|
| Session ID | EXP-SESSION-003 |
| Related Scenario | SCN-EXP-003 — Invalid Conversation Reference |
| System Under Test | Relay |
| Session Type | Exploratory Testing — Black-box UI |
| Session Status | Initial Exploration Completed |

### 1. Session Objective

Explore Relay's observable behavior when accessing conversations through the `conversationId` query parameter, including invalid conversation references and valid conversation references accessed from different account contexts.

### 2. Exploration Notes

#### Observation 1 — Invalid Conversation ID

**Action:** Open the chat page using an invalid conversation ID: `invalid-conversation-id`.

**Actual Result:** The page displays an error screen with the message `This page couldn't load` and the text `A server error occurred. Reload to try again.`

**Evidence:** Screenshot reference: [Screenshot](../evidence/EXP-003-invalid-conversation-id.png)

#### Observation 2 — Valid Conversation ID, Different Account

**Action:** Log in using an account that is not involved in the target conversation, then open the URL containing the valid conversation ID.

**Actual Result:** The page displays the same error screen with the message `This page couldn't load` and the text `A server error occurred. Reload to try again.`

**Evidence:** Screenshot reference: [Screenshot](../evidence/EXP-003-valid-id-other-account.png)

#### Observation 3 — Valid Conversation ID, Correct Account

**Action:** Log in using the account that is involved in the target conversation, then open the same conversation URL.

**Actual Result:** The conversation opens successfully.

**Evidence:** Screenshot reference: [Screenshot](../evidence/EXP-003-valid-id-authorized-account.png)

### 3. Findings

- An invalid conversation ID results in an application error screen.
- A valid conversation URL accessed from an account that is not involved in the conversation results in the same error screen.
- The same valid conversation URL opens successfully when accessed using the correct account.
- The observed results differ according to the conversation reference and account context.

### 4. Limitations

- The underlying cause of the error screen has not been independently verified.
- The expected behavior for invalid conversation references has not been confirmed.
- The intended user-facing behavior when a user attempts to access a conversation they are not authorized to access has not been confirmed.
- The observations do not establish whether the error is caused by authorization enforcement, application error handling, or another underlying issue.

### 5. Evidence

Screenshots supporting the observations are referenced in Section 2 — Exploration Notes.

### 6. Follow-up / Scope Decision

The observed behaviors are documented for Portfolio 1 — End-to-End Manual QA.

Further investigation may be needed to clarify the expected behavior for invalid conversation references and unauthorized conversation access.

No defect is confirmed by the observations collected in this session.

## Session EXP-SESSION-004 — Empty or Whitespace Message

### Session Information

| Field | Value |
|---|---|
| Session ID | EXP-SESSION-004 |
| Related Scenario | SCN-EXP-004 — Empty or Whitespace Message |
| System Under Test | Relay |
| Session Type | Exploratory Testing — Black-box UI |
| Session Status | Initial Exploration Completed |

### 1. Session Objective

Explore Relay's observable behavior when attempting to send an empty message or a whitespace-only message, focusing on the Send button state, available user interactions, and validation feedback.

### 2. Exploration Notes

#### Observation 1 — Empty Message

**Action:** Open a valid conversation and leave the message input field empty.

**Actual Result:**

- The Send button appears disabled.
- The Send button cannot be clicked.
- No message is submitted.
- No validation message or error feedback is displayed during the attempt.

**Evidence:** [Screenshot](../evidence/EXP-004-empty-message.png)

#### Observation 2 — Whitespace-only Message

**Action:** Enter whitespace characters into the message input field without entering any visible text.

**Actual Result:**

- The message input contains whitespace but no visible text.
- The Send button remains disabled.
- The Send button cannot be clicked.
- No message is submitted.
- No validation message or error feedback is displayed during the attempt.
- The cursor changes to a prohibited symbol when hovering over the disabled Send button, according to direct observation.

**Evidence:** [Screenshot](../evidence/EXP-004-whitespace-only-message.png)

### 3. Findings

- The Send button is disabled when the message input is empty.
- The Send button remains disabled when the message input contains whitespace only.
- Both conditions prevent message submission through the observed UI interaction.
- No validation message or error feedback was observed during either attempt.

### 4. Limitations

- The expected validation rules for empty and whitespace-only messages have not been formally confirmed.
- The observations cover the browser UI only.
- Server-side handling of empty or whitespace-only message content has not been independently verified.
- No conclusion is drawn about behavior when client-side validation is bypassed.

### 5. Evidence

Screenshots supporting the observations are referenced in Section 2 — Exploration Notes.

### 6. Follow-up / Scope Decision

The observed behaviors are documented for Portfolio 1 — End-to-End Manual QA.

The findings may be used to support clarification of the expected validation rules for empty and whitespace-only messages.

No defect is confirmed by the observations collected in this session.

## Session EXP-SESSION-005 — Message Length Boundary

### Session Information

| Field | Value |
|---|---|
| Session ID | EXP-SESSION-005 |
| Related Scenario | SCN-EXP-005 — Message Length Boundary |
| System Under Test | Relay |
| Session Type | Exploratory Testing — Browser UI |
| Session Status | Initial Exploration Completed |

### 1. Session Objective

Explore Relay's observable behavior when entering and submitting messages of different lengths, with a focus on identifying potential message length restrictions and documenting the result of a verified 1,000-character submission.

### 2. Exploration Notes

#### Observation 1 — Short Message Input

**Action:** Enter `Test Message 123` into the message input field without submitting it.

**Actual Result:**

- The message can be entered into the input field.
- The Send button becomes active.

#### Observation 2 — Approximately 100-Character Message Input

**Action:** Enter a longer text of approximately 100 characters into the message input field without submitting it.

**Actual Result:**

- The text can be entered into the input field.
- The Send button remains active.

#### Observation 3 — Very Long Message Input

**Action:** Enter approximately 10,000 words into the message input field and observe the input behavior.

**Actual Result:**

- The textarea accommodates the entered text without visible truncation.
- The Send button remains active.
- The exact character count of this input was not measured.

#### Observation 4 — Textarea Attribute Inspection

**Action:** Inspect the message input element using browser DevTools.

**Actual Result:**

The inspected element is a textarea with the following relevant attributes:

- `id="message-input"`
- `rows="1"`
- No `maxlength` attribute is present in the inspected HTML element.

The textarea also has CSS classes that constrain its displayed height and enable vertical scrolling.

#### Observation 5 — Submission of a 1,000-Character Message

**Action:** Submit a message containing exactly 1,000 characters. Verify the character count using Notepad++ before submitting it.

**Actual Result:**

- The message is submitted successfully.
- The message appears in the conversation as a message bubble.
- No submission error was observed during this attempt.

**Evidence:** [Screenshot](../evidence/EXP-005-message-1000-characters.png)

### 3. Findings

- The Send button remains active for the tested short, approximately 100-character, and very long inputs.
- The textarea accepts approximately 10,000 words without visible truncation during the observed input attempt.
- The inspected textarea element does not expose a `maxlength` attribute.
- A message containing exactly 1,000 characters was successfully submitted and displayed in the conversation.
- The maximum permitted message length has not been determined.

### 4. Limitations

- The exact character count of the approximately 10,000-word input was not measured.
- The absence of a `maxlength` attribute does not establish that no message length restriction exists elsewhere in the application.
- The submission result has been verified for a 1,000-character message only.
- Persistence after refresh or re-login was not verified as part of this session.
- Behavior at and beyond any actual maximum message length remains unknown.

### 5. Evidence

- A screenshot of the successfully submitted 1,000-character message is referenced in Section 2 — Exploration Notes.
- The 1,000-character count was verified using Notepad++ before submission.

### 6. Follow-up / Scope Decision

The observed behaviors are documented for Portfolio 1 — End-to-End Manual QA.

The 1,000-character submission confirms that Relay can successfully submit and display a message of that length under the conditions tested. It does not establish the maximum permitted message length.

Further testing may be considered if identifying the exact maximum message length becomes necessary and can be done safely within the available test scope.

No defect is confirmed by the observations collected in this session.