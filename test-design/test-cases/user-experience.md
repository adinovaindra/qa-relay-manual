## User Experience Test Cases

### TC-UX-001-01 — Verify Empty Conversation List

| Field               | Value                          |
| ------------------- | ------------------------------ |
| Test Case ID        | TC-UX-001-01                   |
| Title               | Verify empty conversation list |
| Related Scenario    | SCN-UX-001                     |
| Related Requirement | REQ-UX-005                     |
| Risk Level          | Low                            |
| Test Design Method  | Requirement-Based + Risk-Based |
| Test Type           | Functional / Positive          |
| Priority            | Low                            |

#### Preconditions

- Relay is accessible.
- A registered user account is available.
- The user has no conversations associated with their account.
- The user's valid credentials are available.

#### Test Data

| Data              | Value                                   |
| ----------------- | --------------------------------------- |
| User              | User A                                  |
| Conversation Data | No conversations associated with User A |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Verify that the chat page is displayed.
4. Observe the conversation list.
5. Verify how the application represents the absence of conversations.

#### Expected Result

- The conversation list is displayed.
- The application provides an appropriate representation of the empty conversation list.
- The exact content and wording of the empty state are subject to clarification if not defined by the available documentation.

### TC-UX-001-02 — Verify Empty Conversation Message History

| Field               | Value                                     |
| ------------------- | ----------------------------------------- |
| Test Case ID        | TC-UX-001-02                              |
| Title               | Verify empty conversation message history |
| Related Scenario    | SCN-UX-001                                |
| Related Requirement | REQ-UX-005                                |
| Risk Level          | Low                                       |
| Test Design Method  | Requirement-Based + Risk-Based            |
| Test Type           | Functional / Positive                     |
| Priority            | Low                                       |

#### Preconditions

- Relay is accessible.
- User A and User B are registered users.
- An existing 1-on-1 conversation between User A and User B is available.
- The conversation contains no messages.
- User A is authorized to access the conversation.
- User A's valid credentials are available.

#### Test Data

| Data                         | Value       |
| ---------------------------- | ----------- |
| User                         | User A      |
| Conversation Participant     | User B      |
| Conversation Message History | No messages |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Verify that the chat page is displayed.
4. Open the existing conversation with User B.
5. Observe the message history area.
6. Verify how the application represents the absence of messages.

#### Expected Result

- The selected conversation is displayed.
- No message entries are displayed in the conversation history.
- The application provides an appropriate representation of the empty message history.
- The exact content and wording of the empty state are subject to clarification if not defined by the available documentation.

### TC-UX-002-01 — Recover from a Failed Login Attempt

| Field               | Value                                  |
| ------------------- | -------------------------------------- |
| Test Case ID        | TC-UX-002-01                           |
| Title               | Recover from a failed login attempt    |
| Related Scenario    | SCN-UX-002, SCN-AUTH-002, SCN-AUTH-003 |
| Related Requirement | REQ-UX-006, REQ-AUTH-002               |
| Risk Level          | Medium                                 |
| Test Design Method  | Requirement-Based + Risk-Based         |
| Test Type           | Functional / Negative → Positive       |
| Priority            | Medium                                 |

#### Preconditions

- Relay is accessible.
- A registered user account is available.
- The tester is not authenticated.
- The registered user's valid credentials are known.

#### Test Data

| Data             | Value                                   |
| ---------------- | --------------------------------------- |
| Email            | Registered test user's email            |
| Invalid Password | Incorrect password                      |
| Valid Password   | Registered test user's correct password |

#### Steps

1. Open the Relay application.
2. Verify that the login page is displayed.
3. Enter the registered user's email address.
4. Enter an incorrect password.
5. Click the "Sign in" button.
6. Observe the login result and any error feedback displayed.
7. Replace the incorrect password with the registered user's valid password.
8. Click the "Sign in" button.
9. Observe the login result.
10. Verify the authentication state after the second login attempt.
11. Verify whether the protected chat functionality is accessible.

#### Expected Result

- The first login attempt does not authenticate the user.
- Error feedback is provided for the failed login attempt.
- The user can correct the password and submit the login form again.
- The second login attempt authenticates the user successfully.
- The protected chat functionality is accessible after successful authentication.
- The exact error message for the failed login attempt is not prescribed by the available requirements.

### TC-UX-003-01 — Verify Light and Dark Mode

| Field               | Value                      |
| ------------------- | -------------------------- |
| Test Case ID        | TC-UX-003-01               |
| Title               | Verify light and dark mode |
| Related Scenario    | SCN-UX-003                 |
| Related Requirement | REQ-UX-001, REQ-UX-002     |
| Risk Level          | Low                        |
| Test Design Method  | Requirement-Based          |
| Test Type           | Functional / Positive      |
| Priority            | Low                        |

#### Preconditions

- Relay is accessible.
- A registered user account is available.
- The user's valid credentials are available.
- The user can access the main application screens.

#### Test Data

| Data              | Value                                                |
| ----------------- | ---------------------------------------------------- |
| User              | User A                                               |
| Theme 1           | Light mode                                           |
| Theme 2           | Dark mode                                            |
| Application Areas | Conversation list, conversation panel, message input |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Verify that the main application interface is displayed.
4. Identify the currently selected theme.
5. Switch to light mode if it is not already active.
6. Observe the appearance of the conversation list, conversation panel, and message input.
7. Verify that light mode is applied to the observed application areas.
8. Switch to dark mode.
9. Observe the appearance of the same application areas.
10. Verify that dark mode is applied to the observed application areas.
11. Switch back to light mode.
12. Verify that the application returns to light mode.
13. Navigate between the conversation list and an available conversation.
14. Observe the theme applied across the main application screens.

#### Expected Result

- Light mode is available and can be selected.
- Dark mode is available and can be selected.
- The selected theme is applied to the observed core application areas.
- Switching from light mode to dark mode changes the displayed theme accordingly.
- Switching from dark mode to light mode restores the light theme.
- The selected theme remains visually consistent across the observed main application screens.

### TC-UX-004-01 — Verify Theme Persistence After Refresh and Navigation

| Field               | Value                                                 |
| ------------------- | ----------------------------------------------------- |
| Test Case ID        | TC-UX-004-01                                          |
| Title               | Verify theme persistence after refresh and navigation |
| Related Scenario    | SCN-UX-004                                            |
| Related Requirement | REQ-UX-003                                            |
| Risk Level          | Low                                                   |
| Test Design Method  | Requirement-Based                                     |
| Test Type           | Functional / Positive                                 |
| Priority            | Low                                                   |

#### Preconditions

- Relay is accessible.
- A registered user account is available.
- The user's valid credentials are available.
- The user can access the main application screens.

#### Test Data

| Data              | Value                                    |
| ----------------- | ---------------------------------------- |
| User              | User A                                   |
| Selected Theme    | Dark mode                                |
| Application Areas | Conversation list and conversation panel |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Verify that the main application interface is displayed.
4. Select dark mode.
5. Verify that dark mode is applied to the main application interface.
6. Refresh the page.
7. Observe the theme applied after the page reloads.
8. Navigate between the conversation list and an available conversation.
9. Observe the theme applied after navigation.
10. Verify that the displayed theme remains consistent with the selected theme.

#### Expected Result

- Dark mode is applied after it is selected.
- Dark mode remains selected and displayed after page refresh.
- Dark mode remains selected and displayed after navigation between the observed application areas.
- The selected theme and the displayed theme remain consistent.

### TC-UX-004-02 — Verify Theme Persistence After Logout and Re-Login

| Field               | Value                                              |
| ------------------- | -------------------------------------------------- |
| Test Case ID        | TC-UX-004-02                                       |
| Title               | Verify theme persistence after logout and re-login |
| Related Scenario    | SCN-UX-004                                         |
| Related Requirement | REQ-UX-003                                         |
| Risk Level          | Low                                                |
| Test Design Method  | Requirement-Based + Risk-Based                     |
| Test Type           | Functional / Positive                              |
| Priority            | Low                                                |

#### Preconditions

- Relay is accessible.
- A registered user account is available.
- The user's valid credentials are available.
- The user can access the main application screens.

#### Test Data

| Data           | Value     |
| -------------- | --------- |
| User           | User A    |
| Selected Theme | Dark mode |

#### Steps

1. Open the Relay application.
2. Sign in as User A using valid credentials.
3. Verify that the main application interface is displayed.
4. Select dark mode.
5. Verify that dark mode is applied.
6. Log out from Relay.
7. Sign in again as User A using valid credentials.
8. Observe the theme applied to the main application interface.
9. Verify whether the displayed theme matches the previously selected theme.

#### Expected Result

- Dark mode is applied before logout.
- The user can log out and sign in again successfully.
- After re-login, the displayed theme remains consistent with the previously selected dark mode.
- The theme preference persists across the logout and re-login flow.

### TC-UX-005-01 — Verify Responsive Layout on Desktop

| Field               | Value                               |
| ------------------- | ----------------------------------- |
| Test Case ID        | TC-UX-005-01                        |
| Title               | Verify responsive layout on desktop |
| Related Scenario    | SCN-UX-005                          |
| Related Requirement | REQ-UX-004                          |
| Risk Level          | Medium                              |
| Test Design Method  | Requirement-Based + Risk-Based      |
| Test Type           | Functional / Positive               |
| Priority            | Medium                              |

#### Preconditions

- Relay is accessible.
- A registered user account is available.
- The user's valid credentials are available.
- At least one existing conversation is available to the user.

#### Test Data

| Data              | Value                                                |
| ----------------- | ---------------------------------------------------- |
| User              | User A                                               |
| Viewport          | Representative desktop viewport: 1366 × 768 pixels   |
| Application Areas | Conversation list, conversation panel, message input |

#### Steps

1. Open the Relay application in a desktop browser.
2. Set the browser viewport to 1366 × 768 pixels.
3. Sign in as User A using valid credentials.
4. Verify that the main application interface is displayed.
5. Observe the conversation list.
6. Verify that the conversation list can be accessed and its entries can be selected.
7. Open an existing conversation.
8. Observe the message area and verify that existing messages can be viewed.
9. Observe the message input and verify that it can be accessed and used to enter text.
10. Inspect the main application layout for overlapping or clipped elements that prevent interaction.

#### Expected Result

- Relay's main application interface remains usable at the selected desktop viewport.
- The conversation list can be accessed and a conversation can be selected.
- The message area allows the user to view the selected conversation's messages.
- The message input can be accessed and used to enter text.
- No layout issue prevents interaction with the tested application areas.
- This test uses a representative desktop viewport; it does not establish the product's official responsive breakpoints.

### TC-UX-005-02 — Verify Responsive Layout on Mobile

| Field               | Value                              |
| ------------------- | ---------------------------------- |
| Test Case ID        | TC-UX-005-02                       |
| Title               | Verify responsive layout on mobile |
| Related Scenario    | SCN-UX-005                         |
| Related Requirement | REQ-UX-004                         |
| Risk Level          | Medium                             |
| Test Design Method  | Requirement-Based + Risk-Based     |
| Test Type           | Functional / Positive              |
| Priority            | Medium                             |

#### Preconditions

- Relay is accessible.
- A registered user account is available.
- The user's valid credentials are available.
- At least one existing conversation is available to the user.
- A mobile browser or browser viewport configured to represent a mobile screen is available.

#### Test Data

| Data              | Value                                                |
| ----------------- | ---------------------------------------------------- |
| User              | User A                                               |
| Viewport          | Representative mobile viewport: 390 × 844 pixels     |
| Application Areas | Conversation list, conversation panel, message input |

#### Steps

1. Open Relay in a mobile browser or configure the browser viewport to 390 × 844 pixels.
2. Sign in as User A using valid credentials.
3. Verify that the main application interface is displayed.
4. Observe how the conversation list is presented on the mobile viewport.
5. Verify that the conversation list can be accessed and a conversation can be selected.
6. Open an existing conversation.
7. Observe the message area and verify that existing messages can be viewed.
8. Observe the message input and verify that it can be accessed and used to enter text.
9. Inspect the layout for overlapping, clipping, or horizontal overflow that prevents interaction with the tested application areas.
10. Verify that the tested core functionality remains accessible on the mobile viewport.

#### Expected Result

- Relay's main application interface remains usable at the selected mobile viewport.
- The conversation list can be accessed and a conversation can be selected.
- The message area allows the user to view the selected conversation's messages.
- The message input can be accessed and used to enter text.
- No layout issue prevents interaction with the tested application areas.
- This test uses a representative mobile viewport; it does not establish the product's official responsive breakpoints.