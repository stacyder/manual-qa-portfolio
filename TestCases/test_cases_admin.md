# Test Cases 02

> 1 Goal: Verify that an admin user can successfully create a new system user.
> 

| Test ID | TC-AD-01 |
| --- | --- |
| Module | ADMIN |
| Priority | High |
| Preconditions |   1. User is logged into the system as **Admin**.
  2. Admin has access to the **Admin module**.
  3. An employee already exists in the system  |

| Test Data | Employee |
| --- | --- |
| Steps | 1. Navigate to the PIM module.
2. Click Add Employee.
3. Enter First Name  Alisia
4. Enter Middle Name  A
5. Enter Last Name  Adamson
6. Click Save |
| Expected result |   1. Employee is successfully created.
  2. The Personal Details page is displayed.
  3. The new employee record appears in the system. |
| Title | Success |

> 2 Goal: Verify that the system sends a request to the server when creating a new user and the server returns a successful response. (Network)
> 

| Test ID | TC-AD-02 |
| --- | --- |
| Module | ADMIN |
| Priority | High |
| Preconditions |   1. User is logged into the system as **Admin**.
  2. Admin has access to the **Admin module**.
  3. An employee already exists in the system 
  4. DevTools is open |

| Test Data | Employee  |
| --- | --- |
| Steps |   1. Navigate to **Admin 
  2. Add User**.
  3. Fill in all required fields.
  4. Click **Save**.
  5. Observe the network request triggered by the save action |
| Expected result |   1.  A network request is triggered after clicking **Save**.
  2. Request method is **POST**.
  3. Request payload contains the entered user data (username, role, status).
  4. The server returns **Status Code 200 or 201**.
  5. The response confirms successful user creation. |
| Title | Success |

> 3 Goal: Verify that an admin can search for an existing user using the Username field.
(UI)
> 

| Test ID | TC-AD-03 |
| --- | --- |
| Module | ADMIN |
| Priority | High |
| Preconditions |   1. User is logged into the system as **Admin**.
  2. User has access to the **Admin module**.
  3. A user **alisiaa** exists in the system. |

| Test Data | Field Value
Username alisiaa |
| --- | --- |
| Steps |   1. Navigate to **Admin** module.
  2. In the **Username** field enter **alisiaa**.
  3. Click **Search**. |
| Expected result |   1. The system displays the search results.
  2. User **alisiaa** appears in the **System Users list**.
  3. The displayed user information matches the existing record. |
| Title | Success |

> 4 Goal: Verify that a network request is sent when searching for a user and the response returns correct user data. (Network)
> 

| Test ID | TC-AD-04 |
| --- | --- |
| Module | ADMIN |
| Priority | Medium |
| Preconditions |   1. User is logged into the system as **Admin**.
  2. **DevTools** is open.
  3. User **alisiaa** exists in the system. |

| Test Data | Field Value
Username alisiaa |
| --- | --- |
| Steps |   1. Go to **Admin 
  2. Go to User Management**.
  3. Enter **alisiaa** in the **Username** field.
  4. Click **Search**.
  5. Observe the network request triggered by the search action. |
| Expected result |   1. A network request is triggered after clicking **Search**.
  2. Request **Method GET** 
  3.  Request contains the **username search parameter**.
  4. The server returns **Status Code 200**.
  5. The response contains user data matching the search criteria. |
| Title | Success |

> 5 Goal: Verify that the system correctly filters users by selected **User Role**.
(UI)
> 

| Test ID | TC-AD-05 |
| --- | --- |
| Module | ADMIN |
| Priority | Medium |
| Preconditions |   1. User is logged into the system as **Admin**.
  2. User has access to the **Admin module**.
  3. The system contains users with different roles (e.g., **Admin** and **ESS**). |

| Test Data | Field Value
User Role ESS |
| --- | --- |
| Steps |   1. Navigate to **Admin** module.
  2. Locate the **User Role** filter.
  3. Select **ESS** from the dropdown.
  4. Click **Search**. |
| Expected result |   1. The system displays search results.
  2. Only users with the role **ESS** appear in the results.
  3. Users with other roles (e.g., Admin) are not displayed. |
| Title | Success |

> 6 Goal: Verify that the selected **user role** is sent to the server in the network request and the response contains users with the selected role only.
(Network)
> 

| Test ID | TC-AD-06 |
| --- | --- |
| Module | ADMIN |
| Priority | Medium |
| Preconditions |   1. User is logged into the system as **Admin**.
  2. DevTools is open |

| Test Data | Field Value
Username alisiaa |
| --- | --- |
| Steps |   1. Go to **Admin
  2. Go to User Management**.
  3. Select **User Role = ESS**.
  4. Click **Search**.
  5. Observe the network request triggered by the search action. |
| Expected result |   1. A network request is triggered after clicking **Search**.
  2. The request contains the selected **role parameter**.
  3. The server returns **Status Code 200**.
  4. The response contains only users with the role **ESS**. |
| Title | Success |