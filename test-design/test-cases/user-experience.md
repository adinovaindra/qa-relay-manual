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
| User              | User D - Dave (dave@example.com)        |
| Conversation Data | No conversations associated with User D |

#### Steps

1. Open the Relay application.
2. Sign in as User D using valid credentials.
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
- User D and User E are registered users.
- An existing 1-on-1 conversation between User D and User E is available.
- The conversation contains no messages.
- User D is authorized to access the conversation.
- User D's valid credentials are available.

#### Test Data

| Data                         | Value                            |
| ---------------------------- | -------------------------------- |
| User                         | User D - Dave (dave@example.com) |
| Conversation Participant     | User E - Elon (elon@example.com) |
| Conversation Message History | No messages                      |

#### Steps

1. Open the Relay application.
2. Sign in as User D using valid credentials.
3. Verify that the chat page is displayed.
4. Open the existing conversation with User E.
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

| Data             | Value                            |
| ---------------- | -------------------------------- |
| Email            | User D - Dave (dave@example.com) |
| Invalid Password | password124                      |
| Valid Password   | password123                      |

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

| Data              | Value                                                                 |
| ----------------- | --------------------------------------------------------------------- |
| User              | User D - Dave (dave@example.com)                                      |
| Theme 1           | Light mode                                                            |
| Theme 2           | Dark mode                                                             |
| Application Areas | Register, Login, Conversation list, conversation panel, message input |

#### Steps

1. Open the Relay application.
2. Navigate to the Register page.
3. Select Light Mode using the theme toggle.
4. Verify that the Register page displays Light Mode consistently.
5. Select Dark Mode using the theme toggle.
6. Verify that the Register page displays Dark Mode consistently.
7. Navigate to the Login page.
8. Select Light Mode using the theme toggle.
9. Verify that the Login page displays Light Mode consistently.
10. Select Dark Mode using the theme toggle.
11. Verify that the Login page displays Dark Mode consistently.
12. Log in using Dave's valid credentials.
13. Navigate to the Conversation List.
14. Select Light Mode and verify that the Conversation List displays Light Mode consistently.
15. Select Dark Mode and verify that the Conversation List displays Dark Mode consistently.
16. Open an existing conversation.
17. Select Light Mode and verify that the Conversation Panel and Message Input display Light Mode consistently.
18. Select Dark Mode and verify that the Conversation Panel and Message Input display Dark Mode consistently.
19. Observe the overall appearance of all five application areas in both themes.
20. Verify that switching themes updates the appearance consistently without making content or interactive controls unusable.

#### Expected Result

- Light mode is available and can be selected.
- Dark mode is available and can be selected.
- The selected theme is applied to the observed core application areas.
- Switching from light mode to dark mode changes the displayed theme accordingly.
- Switching from dark mode to light mode restores the light theme.
- The selected theme remains visually consistent across the observed main application screens.

### TC-UX-004-01 — Verify Theme Persistence After Refresh

| Field               | Value                                  |
| ------------------- | -------------------------------------- |
| Test Case ID        | TC-UX-004-01                           |
| Title               | Verify theme persistence after refresh |
| Related Scenario    | SCN-UX-004                             |
| Related Requirement | REQ-UX-003                             |
| Risk Level          | Low                                    |
| Test Design Method  | Requirement-Based                      |
| Test Type           | Functional / Positive                  |
| Priority            | Low                                    |

#### Preconditions

- Relay is accessible.
- A registered user account is available.
- The user's valid credentials are available.
- An existing conversation with User E (Elon) is available.
- The user can access the Register, Login, and main application screens.

#### Test Data

| Data              | Value                                                                 |
| ----------------- | --------------------------------------------------------------------- |
| User              | User D - Dave (dave@example.com)                                      |
| Themes            | Light Mode, Dark Mode                                                 |
| Desktop Viewport  | 1366 × 768                                                            |
| Application Areas | Register, Login, Conversation List, Conversation Panel, Message Input |

#### Steps

1. Set the browser viewport to 1366 × 768.
2. Open the Relay application.
3. Navigate to the Register page.
4. Select Light Mode using the theme toggle.
5. Verify that the Register page displays Light Mode consistently.
6. Refresh the page.
7. Verify that the Register page remains in Light Mode after the page reloads.
8. Select Dark Mode using the theme toggle.
9. Verify that the Register page displays Dark Mode consistently.
10. Refresh the page.
11. Verify that the Register page remains in Dark Mode after the page reloads.
12. Navigate to the Login page.
13. Select Light Mode using the theme toggle.
14. Verify that the Login page displays Light Mode consistently.
15. Refresh the page.
16. Verify that the Login page remains in Light Mode after the page reloads.
17. Select Dark Mode using the theme toggle.
18. Verify that the Login page displays Dark Mode consistently.
19. Refresh the page.
20. Verify that the Login page remains in Dark Mode after the page reloads.
21. Log in using Dave's valid credentials.
22. Verify that the Conversation List is displayed.
23. Open the existing conversation with Elon
24. Select Light Mode and verify that the Conversation List, Conversation Panel, and Message Input display Light Mode consistently.
25. Refresh the page.
26. Verify that the Conversation List, Conversation Panel, and Message Input remain in Light Mode after the page reloads.
27. Select Dark Mode and verify that the Conversation List, Conversation Panel, and Message Input display Dark Mode consistently.
28. Refresh the page.
29. Verify that the Conversation List, Conversation Panel, and Message Input remain in Dark Mode after the page reloads.
30. Verify that the selected theme and displayed theme remain consistent across all tested application areas after refresh.

#### Expected Result

- Light Mode remains selected and displayed after refresh on the Register page.
- Dark Mode remains selected and displayed after refresh on the Register page.
- Light Mode remains selected and displayed after refresh on the Login page.
- Dark Mode remains selected and displayed after refresh on the Login page.
- Light Mode remains selected and displayed after refresh on the main application interface.
- Dark Mode remains selected and displayed after refresh on the main application interface.
- The selected theme and displayed theme remain consistent across all tested application areas after refresh.

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

| Data           | Value                            |
| -------------- | -------------------------------- |
| User           | User D - Dave (dave@example.com) |
| Selected Theme | Dark mode                        |

#### Steps

1. Open the Relay application.
2. Sign in as User D using valid credentials.
3. Verify that the main application interface is displayed.
4. Select dark mode.
5. Verify that dark mode is applied.
6. Log out from Relay.
7. Sign in again as User D using valid credentials.
8. Observe the theme applied to the main application interface.
9. Verify whether the displayed theme matches the previously selected theme.

#### Expected Result

- Dark mode is applied before logout.
- The user can log out and sign in again successfully.
- After re-login, the displayed theme remains consistent with the previously selected dark mode.
- The theme preference persists across the logout and re-login flow.

### TC-UX-004-03 — Verify Theme Persistence During Navigation

| Field               | Value                                      |
| ------------------- | ------------------------------------------ |
| Test Case ID        | TC-UX-004-03                               |
| Title               | Verify theme persistence during navigation |
| Related Scenario    | SCN-UX-004                                 |
| Related Requirement | REQ-UX-003                                 |
| Risk Level          | Low                                        |
| Test Design Method  | Requirement-Based                          |
| Test Type           | Functional / Positive                      |
| Priority            | Low                                        |

#### Preconditions

- Relay is accessible.
- Dave (`dave@example.com`) has a registered account and valid credentials.
- An existing conversation between User D (Dave) and User E (Elon) is available.
- The user can navigate between the Conversation List and Conversation Panel on a mobile viewport.

#### Test Data

| Data              | Value                                                |
| ----------------- | ---------------------------------------------------- |
| User              | User D - Dave (`dave@example.com`)                   |
| Themes            | Light Mode, Dark Mode                                |
| Mobile Viewport   | 390 × 844                                            |
| Application Areas | Conversation List, Conversation Panel, Message Input |

#### Steps

1. Set the browser viewport to 390 × 844.
2. Open the Relay application.
3. Log in using Dave's valid credentials.
4. Verify that the Conversation List is displayed.
5. Select Light Mode using the theme toggle.
6. Verify that the Conversation List displays Light Mode consistently.
7. Open the existing conversation with Elon without refreshing the page.
8. Verify that the Conversation Panel and Message Input display Light Mode consistently after navigation.
9. Navigate back to the Conversation List using the available navigation control without refreshing the page.
10. Verify that the Conversation List still displays Light Mode consistently.
11. Open the existing conversation with Elon again without refreshing the page.
12. Verify that the Conversation Panel and Message Input still display Light Mode consistently.
13. Navigate back to the Conversation List without refreshing the page.
14. Select Dark Mode using the theme toggle.
15. Verify that the Conversation List displays Dark Mode consistently.
16. Open the existing conversation with Elon without refreshing the page.
17. Verify that the Conversation Panel and Message Input display Dark Mode consistently after navigation.
18. Navigate back to the Conversation List using the available navigation control without refreshing the page.
19. Verify that the Conversation List still displays Dark Mode consistently.
20. Open the existing conversation with Elon again without refreshing the page.
21. Verify that the Conversation Panel and Message Input still display Dark Mode consistently.
22. Verify that the selected theme and displayed theme remain consistent when navigating between the Conversation List and Conversation Panel in both themes.

#### Expected Result

- Light Mode remains selected and displayed when navigating from the Conversation List to the Conversation Panel.
- Light Mode remains selected and displayed when returning to the Conversation List.
- Light Mode remains selected and displayed when reopening the conversation.
- Dark Mode remains selected and displayed when navigating from the Conversation List to the Conversation Panel.
- Dark Mode remains selected and displayed when returning to the Conversation List.
- Dark Mode remains selected and displayed when reopening the conversation.
- The selected theme and displayed theme remain consistent across the tested application areas without refreshing the page.

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

| Data              | Value                                                                 |
| ----------------- | --------------------------------------------------------------------- |
| User              | User D - Dave (dave@example.com)                                      |
| Viewport          | Representative desktop viewport: 1366 × 768 pixels                    |
| Application Areas | Register, Login, Conversation list, conversation panel, message input |

#### Steps

1. Open the Relay application in a desktop browser.
2. Set the browser viewport to 1366 × 768 pixels.
3. Sign in as User D using valid credentials.
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
| User              | User D - Dave (dave@example.com)                     |
| Viewport          | Representative mobile viewport: 390 × 844 pixels     |
| Application Areas | Conversation list, conversation panel, message input |

#### Steps

1. Open Relay in a mobile browser or configure the browser viewport to 390 × 844 pixels.
2. Sign in as User D using valid credentials.
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
