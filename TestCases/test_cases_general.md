# Test Cases

---

## 

> 1 Goal: v**erify login with correct username & password (UI)**
> 

| Test ID | TC-OH-001 |
| --- | --- |
| Module | Home Page |
| Priority | High |
| Preconditions | 1. User is on [https://opensource-demo.orangehrmlive.com/web/index.php/auth/login](https://opensource-demo.orangehrmlive.com/web/index.php/auth/login)
2. Home page is opened 
3. User is not logged in |

| Test Data | Login button |
| --- | --- |
| Steps |   1. Navigate to the login page.
  2. Enter valid credentials.
  3. Click “Login”. |
| Expected result | User redirected to dashboard page |
| Title | Success |

> 2 Goal: v**erify login with empty field (UI)**
> 

| Test ID | TC-OH-002 |
| --- | --- |
| Module | Home Page |
| Priority | High |
| Preconditions | 1. User is on [https://opensource-demo.orangehrmlive.com/web/index.php/auth/login](https://opensource-demo.orangehrmlive.com/web/index.php/auth/login)
2. Home page is opened 
3. User is not logged in |

| Test Data | Login button |
| --- | --- |
| Steps |   1. Navigate to the login page.
  2. Enter valid password. (username is empty field)
  3. Click “Login”
  4. Enter valid username. (password is empty field)
  5. Click “Login”
  6. Username and password are empty fields
  7. Click “Login” |
| Expected result |   1. User is not redirected to the dashboard page.
  2. A validation error message is shown for the required empty field. |
| Title | Success |

> 3 Goal: v**erify login with incorrect username & password (UI)**
> 

| Test ID | TC-OH-003 |
| --- | --- |
| Module | Home Page |
| Priority | High |
| Preconditions | 1. User is on [https://opensource-demo.orangehrmlive.com/web/index.php/auth/login](https://opensource-demo.orangehrmlive.com/web/index.php/auth/login)
2. Home page is opened 
3. User is not logged in |

| Test Data | Login button |
| --- | --- |
| Steps |  1. Navigate to the login page.
  2. Enter non valid credentials.
  3. Click “Login”. |
| Expected result |  1. User is not found and not redirected to the dashboard page.
  2. A validation error message is shown for the required empty field. |
| Title | Success |

> 4 Goal: **Boundary Testing**
> 

| Test ID | TC-OH-004 |
| --- | --- |
| Module | Home Page |
| Priority | Medium |
| Preconditions | 1. User is on [https://opensource-demo.orangehrmlive.com/web/index.php/auth/login](https://opensource-demo.orangehrmlive.com/web/index.php/auth/login)
2. Home page is opened 
3. User is not logged in |

| Test Data | Username field |
| --- | --- |
| Steps |   1.  Enter 100 symbols username in field
  2. Enter valid password
  3. Click “Login”. |
| Expected result |   1. Input is truncated to the maximum allowed length.
  2. No error occurs unless the limit is exceeded (if validation is shown). |
| Title | 1. Failed
2. Failed
 |

> 5 Goal: **Boundary Testing**
> 

| Test ID | TC-OH-005 |
| --- | --- |
| Module | Home Page |
| Priority | Medium |
| Preconditions | 1. User is on [https://opensource-demo.orangehrmlive.com/web/index.php/auth/login](https://opensource-demo.orangehrmlive.com/web/index.php/auth/login)
2. Home page is opened 
3. User is not logged in |

| Test Data | Password field |
| --- | --- |
| Steps |  1.  Enter 500 symbols password in field
 2. Enter valid username
 3. Click “Login”. |
| Expected result |  1. Input is truncated to the maximum allowed length.
 2. No error occurs unless the limit is exceeded (if validation is shown). |
| Title | 1. Failed
2. Failed |

> 6 Goal: v**erify login with correct username & password (network)**
> 

| Test ID | TC-OH-006 |
| --- | --- |
| Module | Home Page |
| Priority | High |
| Preconditions | 1. User is on [https://opensource-demo.orangehrmlive.com/web/index.php/auth/login](https://opensource-demo.orangehrmlive.com/web/index.php/auth/login)
2. Home page is opened 
3. User is not logged in |

| Test Data | Login verification |
| --- | --- |
| Steps | 1. Open DevTools
2. Navigate to the login page
3. Enter valid credentials.
4. Click “Login”. |
| Expected result |   1. 200 OK is returned. 
  2. Valid authentication token/session is issued. 
  3. User is successfully authorized and redirected to the inventory page. |
| Title | Success |

> 7 Goal: v**erify login with incorrect username & password (network)**
> 

| Test ID | TC-OH-007 |
| --- | --- |
| Module | Home Page |
| Priority | High |
| Preconditions | 1. User is on [https://opensource-demo.orangehrmlive.com/web/index.php/auth/login](https://opensource-demo.orangehrmlive.com/web/index.php/auth/login)
2. Home page is opened 
3. User is not logged in |

| Test Data | Login button |
| --- | --- |
| Steps |  1. Open DevTools
 2. Navigate to the login page.
 3. Enter non valid credentials.
 4. Click “Login”. |
| Expected result |   1. Login request is sent 
  2. Response **401 Unauthorized**
  3. Error message returned
  4. No auth token/session created. |
| Title |   1. Success
  2. Failed
  3. Success
  4.  Failed |

> 8 Goal: Verify login protection against SQL injection **(UI)**
> 

| Test ID | TC-OH-008 |
| --- | --- |
| Module | Home Page |
| Priority | High |
| Preconditions | 1. User is on [https://opensource-demo.orangehrmlive.com/web/index.php/auth/login](https://opensource-demo.orangehrmlive.com/web/index.php/auth/login)
2. Home page is opened 
3. User is not logged in |

| Test Data | Value |
| --- | --- |
| Steps |   1. Open the Login page.
  2. Enter `' OR '1'='1` in the Username field.
  3. Enter `test123` in the Password field.
  4. Click the Login button. |
| Expected result | 1. User is not logged in.
2. Error message is displayed 
3. No system or database errors are shown. |
| Title |   1. Success
  2. Success
  3. Success |

> 9 Goal: Verify login protection against SQL injection **(Network)**
> 

| Test ID | TC-OH-009 |
| --- | --- |
| Module | Home Page |
| Priority | High |
| Preconditions | 1. User is on [https://opensource-demo.orangehrmlive.com/web/index.php/auth/login](https://opensource-demo.orangehrmlive.com/web/index.php/auth/login)
2. Home page is opened 
3. User is not logged in |

| Test Data | Value |
| --- | --- |
| Steps |   1. Open the Login page.
  2. Open Browser DevTools.
  3. Go to the Network tab.
  4. Enter `' OR '1'='1` in the Username field.
  5. Enter `test123` in the Password field.
  6. Click the Login button.
  7. In the Network tab, find the login/auth request.
  8. Check the request payload and response. |
| Expected result |   1. Login request returns 401/403
  2. Authentication fails 
  3. No auth token returned
  4. Response does not contain SQL/database errors. |
| Title |   1.  Failed
  2. Success
  3.  Failed
  4. Success |

> 10 Goal: Validate special symbols in password field **(UI)**
> 

| Test ID | TC-OH-0010 |
| --- | --- |
| Module | Home Page |
| Priority | Medium |
| Preconditions | 1. User is on [https://opensource-demo.orangehrmlive.com/web/index.php/auth/login](https://opensource-demo.orangehrmlive.com/web/index.php/auth/login)
2. Home page is opened 
3. User is not logged in |

| Test Data | `P@$$w0rd!#` |
| --- | --- |
| Steps |   1. Open the login page.
  2. Locate the **Username** input field.
  3. Enter `P@$$w0rd!#` into the password field.
  4. Enter valid username
  5. Click the Login button. |
| Expected result | 1. The system should validate the input on the UI level.
2. A validation message should appear 
3. The form should not be submitted.
4. User is not logged in and redirected |
| Title | Success |

> 11 Goal: Validate special symbols in password field **(Network)**
> 

| Test ID | TC-OH-0011 |
| --- | --- |
| Module | Home Page |
| Priority | Medium |
| Preconditions | 1. User is on [https://opensource-demo.orangehrmlive.com/web/index.php/auth/login](https://opensource-demo.orangehrmlive.com/web/index.php/auth/login)
2. Home page is opened 
3. User is not logged in |

| Test Data | `P@$$w0rd!#` |
| --- | --- |
| Steps |   1. Open login page.
  2. Enter valid username.
  3. Enter password `P@$$w0rd!#`.
  4. Click Login button.
  5. Capture outgoing network request.
  6. Check request payload, server response. |
| Expected result | 1. Password with special characters is sent correctly in the request payload.
2. Server  returns 401
3. User is not logged in and redirected.
4. No auth token/session created. |
| Title
 | 1. Success
2.  Failed
3. Success
4. Failed |

> 12 Goal: Validate UI handling of leading/trailing spaces in username or password **(UI)**
> 

| Test ID | TC-OH-0012 |
| --- | --- |
| Module | Home Page |
| Priority | Medium |
| Preconditions | 1. User is on [https://opensource-demo.orangehrmlive.com/web/index.php/auth/login](https://opensource-demo.orangehrmlive.com/web/index.php/auth/login)
2. Home page is opened 
3. User is not logged in |

| Test Data | Username field |
| --- | --- |
| Steps |   1.  Open login page.
  2. Enter username with leading/trailing spaces.
  3. Enter valid password.
  4. Click **Login**. |
| Expected result |   1. UI trims leading/trailing spaces or displays error message.
  2. No layout issues or crashes.
  3. Correct error message displayed if login fails. |
| Title | Success |

> 13 Goal: Verify network request payload for username/password with leading/trailing spaces **(Network)**
> 

| Test ID | TC-OH-0013 |
| --- | --- |
| Module | Home Page |
| Priority | Medium |
| Preconditions | 1. User is on [https://opensource-demo.orangehrmlive.com/web/index.php/auth/login](https://opensource-demo.orangehrmlive.com/web/index.php/auth/login)
2. Home page is opened 
3. User is not logged in |

| Test Data | Username field |
| --- | --- |
| Steps |   1. Open DevTools.
  2. Enter username with leading/trailing spaces.
  3. Click **Login**.
  4. Capture network request. |
| Expected result | 1. Payload sent correctly 
2. .Server returns **401 
3.** Correct error message displayed in UI.
4. No server errors 500.
5. User is not logged in and redirected.
6. No auth token/session created. |
| Title |   1. Success
  2.  Failed
  3. Success
  4. Success
  5. Success
  6.  Failed |

> 14 Goal: Verify case sensitivity in login fields (UI)
> 

| Test ID | TC-OH-0014 |
| --- | --- |
| Module | Home Page |
| Priority | Medium |
| Preconditions | 1. User is on [https://opensource-demo.orangehrmlive.com/web/index.php/auth/login](https://opensource-demo.orangehrmlive.com/web/index.php/auth/login)
2. User account exists in the system.
3. Home page is opened 
4. User is not logged in |

| Test Data | Value |
| --- | --- |
| Steps |   1. Navigate to the login page.
  2. Enter valid credentials using uppercase/lowercase variations
  3. Click “Login”. |
| Expected result |   1. Login succeeds (email should be case-insensitive).
  2. Login fails (password must be case-sensitive).
  3. Error message is displayed  |
| Title |   1. Success
  2. Success
  3. Success |

> 15 Goal: Verify case sensitivity in login fields (Network)
> 

| Test ID | TC-OH-0015 |
| --- | --- |
| Module | Home Page |
| Priority | Medium |
| Preconditions | 1. User is on [https://opensource-demo.orangehrmlive.com/web/index.php/auth/login](https://opensource-demo.orangehrmlive.com/web/index.php/auth/login)
2. User account exists in the system.
3. Home page is opened 
4. User is not logged in |

| Test Data | Value |
| --- | --- |
| Steps |   1. Navigate to the login page.
  2. Open DevTools
  3. Enter valid credentials using uppercase/lowercase variations
  4. Click “Login”. |
| Expected result |   1. 302 Found**,** successful login, server redirects user to dashboard (email should be case-insensitive).
  2. 401 Unauthorized**, l**ogin failed, server does not allow access (password must be case-sensitive). |
| Title |   1. Success
  2. Success |

[Test Cases 01](Test%20Cases/Test%20Cases%2001%203255386ac93e805a854ade0c58c55770.md)

[Test Cases 02](Test%20Cases/Test%20Cases%2002%203255386ac93e80e3b307fe014ec1d320.md)

[DevTools_Analysis.md](Test%20Cases/DevTools_Analysis%20md%203195386ac93e80928064f469d01e6453.md)

[Observation](Test%20Cases/Observation%203255386ac93e8032babfea4c0d6b0a26.md)

[BUG Reports](Test%20Cases/BUG%20Reports%203255386ac93e80b293c2c1e4a29aee8a.md)

[API Testing ](Test%20Cases/API%20Testing%203255386ac93e80e89f68dfdf30c61e4a.md)

[SQL test_cases](Test%20Cases/SQL%20test_cases%203255386ac93e808f9494e4ba920ac769.md)