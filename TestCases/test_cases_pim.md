# Test Cases 01

> 1 Goal: Verify that a user can successfully create a new employee with valid data.
 **(UI)**
> 

| Test ID | TC-PIM-01 |
| --- | --- |
| Module | PIM |
| Priority | High |
| Preconditions | 1. User is on [https://opensource-demo.orangehrmlive.com/web/index.php/pim/viewEmployeeList](https://opensource-demo.orangehrmlive.com/web/index.php/pim/viewEmployeeList)
2. PIM module is opened 
3. User is logged in |

| Test Data | Value |
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

> 2 Goal: Verify that the correct API request is sent and the server returns a successful response when creating a new employee. **(Network)**
> 

| Test ID | TC-PIM-02 |
| --- | --- |
| Module | PIM |
| Priority | High |
| Preconditions | 1. User is on [https://opensource-demo.orangehrmlive.com/web/index.php/pim/viewEmployeeList](https://opensource-demo.orangehrmlive.com/web/index.php/pim/viewEmployeeList)
2. PIM module is opened 
3. User is logged in
4. DevTools is open. |

| Test Data | Value |
| --- | --- |
| Steps | 1. Click Add Employee.﻿
2. Fill in the fields (First Name, Middle Name, Last Name)﻿
3. Click Save
4. Open the Response section of the request |
| Expected result |  1. A POST request for employee creation is sent to the server.
  2. Request payload contains the entered employee data.
  3. The server returns Status Code 200 or 201.
  4. Response body contains data of the created employee
  5. The employee is successfully created and displayed in the system UI |
| Title | Success |

> 3 Goal: Verify that a user can search for an existing employee using the Employee Name field.
 **(UI)**
> 

| Test ID | TC-PIM-03 |
| --- | --- |
| Module | PIM |
| Priority | High |
| Preconditions |   1. User is logged into the system.
  2. User has access to the **PIM module**.
  3. Employee Alisia Adamson exists in the system. |

| Test Data | Value: Alisia Adamson |
| --- | --- |
| Steps |   1. Navigate to **PIM** module.
  2. Open **Employee List**.
  3. Enter Alisia Adamson in the **Employee Name** field.
  4. Click **Search**. |
| Expected result |   1. The system displays search results.
  2. Employee Alisia Adamson appears in the list.
  3. Employee information matches the existing record. |
| Title | Success |

> 4 Goal: Verify that a network request is sent when searching for an employee and the response returns correct employee data.
 **(Network)**
> 

| Test ID | TC-PIM-04 |
| --- | --- |
| Module | PIM |
| Priority | Medium |
| Preconditions |   1. User is logged into the system.
  2. User has access to the **PIM module**.
  3. Employee Alisia Adamson exists in the system.
  4. DevTools is open |

| Test Data | Value: Alisia Adamson |
| --- | --- |
| Steps |   1. Navigate to **PIM** module.
  2. Open **Employee List**.
  3. Enter Alisia Adamson in the **Employee Name** field.
  4. Click **Search**.
  5. Open the request related to employee search. |
| Expected result |   1. A network request is triggered after clicking **Search**.
  2. Request **Method = GET**.
  3. The request URL contains the **employee search parameter**.
  4. The server returns **Status Code 200**.
  5. The **response contains employee data** matching the searched employee.
  6. No errors are observed in the network request. |
| Title | Success |

> 5 Goal: Verify that a user can delete an existing employee from the employee list.
 **(UI)**
> 

| Test ID | TC-PIM-05 |
| --- | --- |
| Module | PIM |
| Priority | High |
| Preconditions |   1. User is logged into the system.
  2. User has access to the **PIM module**.
  3. Employee Alisia Adamson exists in the system. |

| Test Data | Value: Alisia Adamson |
| --- | --- |
| Steps |   1. Navigate to **PIM** module.
  2. Open **Employee List**.
  3. Locate employee Alisia Adamson in the list.
  4. Select the checkbox next to the employee.
  5. Click **Delete**.
  6. Confirm deletion in the confirmation dialog. |
| Expected result |   1. The employee record is successfully deleted.
  2. The employee no longer appears in the employee list.
  3. A success notification message is displayed. |
| Title | Success |

> 6 Goal: Verify that a network request is sent when deleting an employee and the server returns a successful response.
 **(Network)**
> 

| Test ID | TC-PIM-06 |
| --- | --- |
| Module | PIM |
| Priority | Medium |
| Preconditions |   1. User is logged into the system.
  2. User has access to the **PIM module**.
  3. Employee Alisia Adamson exists in the system.
  4. DevTools is open |

| Test Data | Value: Alisia Adamson |
| --- | --- |
| Steps |   1. Locate employee Alisia Adamson.
  2. Select the checkbox next to the employee.
  3. Click **Delete**.
  4. Confirm the deletion.
  5. Observe the network request triggered after confirming deletion. |
| Expected result |   1. A network request is triggered after confirming deletion.
  2. Request **Method = DELETE** 
  3. Request contains the **employee ID** of the deleted employee.
  4. The server returns **Status Code 200**.
  5. The response confirms successful deletion.
  6. No network errors occur. |
| Title |   1. Success
  2. Success
  3. Success
  4. Success
  5. Success
  6. Failed |

> 7 Verify that the system displays validation errors when required fields are empty during employee creation.
 **(UI)**
> 

| Test ID | TC-PIM-07 |
| --- | --- |
| Module | PIM |
| Priority | Medium |
| Preconditions |   1. User is logged into the system.
  2. User has access to the **PIM module**. |

| Test Data | Empty fields |
| --- | --- |
| Steps |   1. Navigate to **PIM** module.
  2. Click **Add Employee**.
  3. Leave **First Name** field empty.
  4. Leave **Last Name** field empty.
  5. Click **Save**. |
| Expected result |   1. The employee record is not created.
  2. Validation messages **"Required"** appear under **First Name** and **Last Name** fields.
  3. The form is not submitted. |
| Title | Success |

> 8 Verify that the system prevents sending a request to the server when required fields are empty.
 **(Network)**
> 

| Test ID | TC-PIM-08 |
| --- | --- |
| Module | PIM |
| Priority | Medium |
| Preconditions |   1. User is logged into the system.
  2. User has access to the **PIM module**.
  3. DevTools is open |

| Test Data | Empty fields |
| --- | --- |
| Steps |   1. Navigate to **PIM** module.
  2. Click **Add Employee**.
  3. Leave **First Name** field empty.
  4. Leave **Last Name** field empty.
  5. Click **Save**.
  6. Observe the Network tab for any request. |
| Expected result |   1. No network request is sent to the server.
  2. Validation is handled on the **UI side (client-side validation)**.
  3. Error messages appear without any API request. |
| Title | Success |