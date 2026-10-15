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

| Data                        | Value                                   |
| --------------------------- | --------------------------------------- |
| Authenticated User          | User D - Dave (dave@example.com)        |
| Authenticated User Password | password123                             |
| Conversation Data           | No conversations associated with User D |

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
| Authenticated User           | User D - Dave (dave@example.com) |
| Authenticated User Password  | password123                      |
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

| Data               | Value                            |
| ------------------ | -------------------------------- |
| Authenticated User | User D - Dave (dave@example.com) |
| Invalid Password   | password124                      |
| Valid Password     | password123                      |

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

| Data                        | Value                                                                 |
| --------------------------- | --------------------------------------------------------------------- |
| Authenticated User          | User D - Dave (dave@example.com)                                      |
| Authenticated User Password | password123                                                           |
| Theme 1                     | Light mode                                                            |
| Theme 2                     | Dark mode                                                             |
| Application Areas           | Register, Login, Conversation list, conversation panel, message input |

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

| Data                        | Value                                                                 |
| --------------------------- | --------------------------------------------------------------------- |
| Authenticated User          | User D - Dave (dave@example.com)                                      |
| Authenticated User Password | password123                                                           |
| Themes                      | Light Mode, Dark Mode                                                 |
| Viewport                    | Desktop                                                               |
| Application Areas           | Register, Login, Conversation List, Conversation Panel, Message Input |

#### Steps

1. Open the Relay application.
2. Navigate to the Register page.
3. Select Light Mode using the theme toggle.
4. Verify that the Register page displays Light Mode consistently.
5. Refresh the page.
6. Verify that the Register page remains in Light Mode after the page reloads.
7. Select Dark Mode using the theme toggle.
8. Verify that the Register page displays Dark Mode consistently.
9. Refresh the page.
10. Verify that the Register page remains in Dark Mode after the page reloads.
11. Navigate to the Login page.
12. Select Light Mode using the theme toggle.
13. Verify that the Login page displays Light Mode consistently.
14. Refresh the page.
15. Verify that the Login page remains in Light Mode after the page reloads.
16. Select Dark Mode using the theme toggle.
17. Verify that the Login page displays Dark Mode consistently.
18. Refresh the page.
19. Verify that the Login page remains in Dark Mode after the page reloads.
20. Log in using Dave's valid credentials.
21. Verify that the Conversation List is displayed.
22. Open the existing conversation with Elon
23. Select Light Mode and verify that the Conversation List, Conversation Panel, and Message Input display Light Mode consistently.
24. Refresh the page.
25. Verify that the Conversation List, Conversation Panel, and Message Input remain in Light Mode after the page reloads.
26. Select Dark Mode and verify that the Conversation List, Conversation Panel, and Message Input display Dark Mode consistently.
27. Refresh the page.
28. Verify that the Conversation List, Conversation Panel, and Message Input remain in Dark Mode after the page reloads.
29. Verify that the selected theme and displayed theme remain consistent across all tested application areas after refresh.

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

| Data                        | Value                            |
| --------------------------- | -------------------------------- |
| Authenticated User          | User D - Dave (dave@example.com) |
| Authenticated User Password | password123                      |
| Selected Theme              | Dark mode                        |

#### Steps

1. Open the Relay application.
2. Make sure the current theme is light.
3. Sign in as User D using valid credentials.
4. Verify that the main application interface is displayed.
5. Select dark mode.
6. Verify that dark mode is applied.
7. Log out from Relay.
8. Sign in again as User D using valid credentials.
9. Observe the theme applied to the main application interface.
10. Verify whether the displayed theme matches the previously selected theme.

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

| Data                        | Value                                                |
| --------------------------- | ---------------------------------------------------- |
| Authenticated User          | User D - Dave (dave@example.com)                     |
| Authenticated User Password | password123                                          |
| Themes                      | Light Mode, Dark Mode                                |
| Mobile Viewport             | 440 × 956                                            |
| Application Areas           | Conversation List, Conversation Panel, Message Input |

#### Steps

1. Set the browser viewport to 440 × 956.
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
- User has an active account.
- User has a valid password.
- An existing conversation between User A and User C contains several messages.
- A desktop browser is available.

#### Test Data

| Data                        | Value                                                                 |
| --------------------------- | --------------------------------------------------------------------- |
| Authenticated User          | User A - Alice (alice@example.com)                                    |
| Authenticated User Password | password123                                                           |
| User C                      | Charlie (charlie@example.com)                                         |
| Conversation                | Existing User A - User C conversation containing several messages     |
| Viewport                    | Desktop                                                               |
| Message Input Text          | "I'm good. I'm very good. How about you, Charlie?"                    |
| Application Areas           | Register, Login, Conversation List, Conversation Panel, Message Input |

#### Steps

1. Open the Relay application in a desktop browser.
2. Navigate to the Register page and inspect the displayed layout without creating a new account.
3. Navigate to the Login page and inspect the displayed layout.
4. Sign in as User A using valid credentials.
5. Verify that the main application interface is displayed.
6. Observe the Conversation List and locate the existing conversation with User C - Charlie.
7. Select the Alice – Charlie conversation.
8. Observe the Conversation Panel and verify that several existing messages can be viewed.
9. Observe the Message Input and enter the test text `I'm good. I'm very good. How about you, Charlie?` without sending the message.
10. Inspect the tested application areas for overlapping or clipped elements that prevent access to UI elements or completion of the interactions described in this test case.

#### Expected Result

- The Register page is displayed, and no layout overlap or clipping prevents access to its displayed UI elements.
- The Login page is displayed, and no layout overlap or clipping prevents access to its displayed UI elements.
- Alice successfully accesses the main application interface.
- The Conversation List is accessible, and the existing Alice – Charlie conversation can be located and selected.
- The Conversation Panel displays the selected conversation, and several existing messages can be viewed without layout issues preventing their content from being read.
- The Message Input is accessible, accepts the test text, and displays the entered text without sending the message.
- No layout overlap or clipping prevents access to the relevant UI elements or completion of the interactions described in this test case.
- The test evaluates the desktop browser viewport used during execution and does not establish coverage of every desktop resolution or responsive breakpoint.

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

| Data                        | Value                                                                 |
| --------------------------- | --------------------------------------------------------------------- |
| Authenticated User          | User A - Alice (alice@example.com)                                    |
| Authenticated User Password | password123                                                           |
| User C                      | Charlie (charlie@example.com)                                         |
| Conversation                | Existing Alice - Charlie conversation containing several messages     |
| Viewport                    | Representative mobile viewport: 440 × 956 pixels                      |
| Message Input Text          | `I'm good. I'm very good. How about you, Charlie?`                    |
| Application Areas           | Register, Login, Conversation List, Conversation Panel, Message Input |

#### Steps

1. Open Relay in a mobile browser or configure the browser viewport to 440 × 956 pixels.
2. Navigate to the Register page and inspect its layout without creating a new account.
3. Navigate to the Login page and inspect its layout.
4. Sign in as User A using the valid credentials.
5. Verify that the main application interface is displayed.
6. Observe how the Conversation List is presented on the mobile viewport.
7. Verify that the Conversation List can be accessed and the existing Alice - Charlie conversation can be located and selected.
8. Open the Alice - Charlie conversation.
9. Observe the message area and verify that several existing messages can be viewed.
10. Observe the Message Input and enter the test text `I'm good. I'm very good. How about you, Charlie?` without sending the message.
11. Inspect the tested application areas for overlapping elements, clipping, or horizontal overflow that prevents access to UI elements or completion of the interactions described in this test case.

#### Expected Result

- Relay's main application interface remains usable at the selected mobile viewport.
- The Register page is displayed, and no layout overlap or clipping prevents access to its displayed UI elements.
- The Login page is displayed, and no layout overlap or clipping prevents access to its displayed UI elements.
- Alice successfully accesses the main application interface.
- The Conversation List is accessible, and the existing Alice - Charlie conversation can be located and selected.
- The Conversation Panel displays the selected conversation, and several existing messages can be viewed without layout issues preventing their content from being read.
- The Message Input is accessible, accepts the test text, and displays the entered text without sending the message.
- No overlapping elements, clipping, or horizontal overflow prevents interaction with the tested application areas.
- The test evaluates the mobile viewport used during execution and does not establish coverage of every mobile resolution or responsive breakpoint.
