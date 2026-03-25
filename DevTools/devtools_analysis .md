# DevTools_Analysis.md

> **Verify login with correct username & password (network)**
> 

| Test ID | TC-OH-006 |
| --- | --- |
| Method | POST |
| Status Code | 302 |
| Request URL | [https://opensource-demo.orangehrmlive.com/web/index.php/auth/validate](https://opensource-demo.orangehrmlive.com/web/index.php/auth/validate) |
| Request Payload | username: Admin
password: admin123
token: dynamic CSRF token |
| Response | 302 Redirect
Location: /dashboard |

> **Verify login with incorrect username & password (network)**
> 

| Test ID | TC-OH-007 |
| --- | --- |
| Method | POST |
| Status Code | 302 |
| Request URL | https://opensource-demo.orangehrmlive.com/web/index.php/auth/validate |
| Request Payload | username: Admin
password: admin123dn
token: dynamic CSRF token |
| Response | 302 Redirect
Location: /auth/login |

> Verify login protection against SQL injection **(Network)**
> 

| Test ID | TC-OH-009 |
| --- | --- |
| Method | POST |
| Status Code | 302 |
| Request URL | [https://opensource-demo.orangehrmlive.com/web/index.php/auth/validate](https://opensource-demo.orangehrmlive.com/web/index.php/auth/validate) |
| Request Payload | username: ' OR '1'='1
password: admin123
token: dynamic CSRF token |
| Response | 302 Redirect
Location: /auth/login |

> Validate special symbols in password field **(Network)**
> 

| Test ID | TC-OH-0011 |
| --- | --- |
| Method | POST |
| Status Code | 302 |
| Request URL | [https://opensource-demo.orangehrmlive.com/web/index.php/auth/validate](https://opensource-demo.orangehrmlive.com/web/index.php/auth/validate) |
| Request Payload | username: Admin
password: P@$$w0rd!#
token: dynamic CSRF token |
| Response | 302 Redirect
Location: /auth/login |

> Verify network request payload for username/password with leading/trailing spaces **(Network)**
> 

| Test ID | TC-OH-0013 |
| --- | --- |
| Method | POST |
| Status Code | 302 |
| Request URL | [https://opensource-demo.orangehrmlive.com/web/index.php/auth/validate](https://opensource-demo.orangehrmlive.com/web/index.php/auth/validate) |
| Request Payload | username:  Admin
password: admin123
token: dynamic CSRF token |
| Response | 302 Redirect
Location: /auth/login |

> Verify case sensitivity in login username field **(Network)**
> 

| Test ID | TC-OH-0015 |
| --- | --- |
| Method | POST |
| Status Code | 302 |
| Request URL | [https://opensource-demo.orangehrmlive.com/web/index.php/auth/validate](https://opensource-demo.orangehrmlive.com/web/index.php/auth/validate) |
| Request Payload | username:  AdmiN
password: admin123
token: dynamic CSRF token |
| Response | 302 Redirect
Location: /dashboard/index |

> Verify that the correct API request is sent and the server returns a successful response when creating a new employee
> 

| Test ID | TC-PIM-02 |
| --- | --- |
| Method | GET |
| Status Code | 200 |
| Request URL | https://opensource-demo.orangehrmlive.com/web/index.php/api/v2/pim/employees/181/personal-details |
| Request Payload | N/A |
| Response | Returns employee data including First Name, Last Name and Employee ID

{
"empNumber": 181,
"lastName": "Adamson",
"firstName": "Alisia",
"middleName": "A",
"employeeId": "038056",
"terminationId": null
} |

> Verify that a network request is sent when searching for an employee and the response returns correct employee data.
> 

| Test ID | TC-PIM-04 |
| --- | --- |
| Method | GET |
| Status Code | 200 |
| Request URL | [https://opensource-demo.orangehrmlive.com/web/index.php/api/v2/pim/employees?limit=50&offset=0&model=detailed&empNumber=181&includeEmployees=onlyCurrent&sortField=employee.firstName&sortOrder=ASC](https://opensource-demo.orangehrmlive.com/web/index.php/api/v2/pim/employees?limit=50&offset=0&model=detailed&empNumber=181&includeEmployees=onlyCurrent&sortField=employee.firstName&sortOrder=ASC) |
| Request Payload | limit=50&offset=0&model=detailed&empNumber=181&includeEmployees=onlyCurrent&sortField=employee.firstName&sortOrder=ASC |
| Response | Returns employee data including First Name, Last Name and Employee number
{
"data": [
{
"empNumber": 181,
"lastName": "Adamson",
"firstName": "Alisia",
"middleName": "A",
"employeeId": "038056",
"terminationId": null,
"jobTitle": {
"id": null,
"title": null,
"isDeleted": null
},
"subunit": {
"id": null,
"name": null
},
"empStatus": {
"id": null,
"name": null
},
"supervisors": []
}
],
"meta": {
"total": 1
},
"rels": []
} |

> Verify that a network request is sent when deleting an employee and the server returns a successful response.
> 

| Test ID | TC-PIM-06 |
| --- | --- |
| Method | DELETE |
| Status Code | 200 |
| Request URL | [https://opensource-demo.orangehrmlive.com/web/index.php/api/v2/pim/employees](https://opensource-demo.orangehrmlive.com/web/index.php/api/v2/pim/employees) |
| Request Payload | {"ids":[223]}

223-empl. number |
| Response | {"data":["223"],"meta":[],"rels":[]} |

> Verify that a network request is sent when deleting an employee and the server returns a successful response. (No network errors occur)
> 

| Test ID | TC-PIM-06 |
| --- | --- |
| Method | GET |
| Status Code | 422 |
| Request URL | [https://opensource-demo.orangehrmlive.com/web/index.php/api/v2/pim/employees?limit=50&offset=0&model=detailed&empNumber=223&includeEmployees=onlyCurrent&sortField=employee.firstName&sortOrder=ASC](https://opensource-demo.orangehrmlive.com/web/index.php/api/v2/pim/employees?limit=50&offset=0&model=detailed&empNumber=223&includeEmployees=onlyCurrent&sortField=employee.firstName&sortOrder=ASC) |
| Request Payload | limit=50&offset=0&model=detailed&empNumber=223&includeEmployees=onlyCurrent&sortField=employee.firstName&sortOrder=ASC |
| Response | Server returns error because employee record no longer exists

"error": {
"status": "422",
"message": "Invalid Parameter",
"data": {
"invalidParamKeys": [
"empNumber"
]
}
}
} |

> Verify that the system sends a request to the server when creating a new user and the server returns a successful response.
> 

| Test ID | TC-AD-02 |
| --- | --- |
| Method | GET |
| Status Code | 200 |
| Request URL | https://opensource-demo.orangehrmlive.com/web/index.php/api/v2/admin/users?limit=50&offset=0&sortField=u.userName&sortOrder=ASC |
| Request Payload | limit=50&offset=0&sortField=u.userName&sortOrder=ASC |
| Response | Response contains created user data
userName: alisiaa
userRole: ESS
status: true |

> Verify that a network request is sent when searching for a user and the response returns correct user data.
> 

| Test ID | TC-AD-04 |
| --- | --- |
| Method | GET |
| Status Code | 200 |
| Request URL | [https://opensource-demo.orangehrmlive.com/web/index.php/api/v2/admin/users?limit=50&offset=0&username=alisiaa&sortField=u.userName&sortOrder=ASC](https://opensource-demo.orangehrmlive.com/web/index.php/api/v2/admin/users?limit=50&offset=0&username=alisiaa&sortField=u.userName&sortOrder=ASC) |
| Request Payload | limit=50&offset=0&username=**alisiaa**&sortField=u.userName&sortOrder=ASC |
| Response | Response contains user data including userName, userRole and employee information |

> Verify that the selected **user role** is sent to the server in the network request and the response contains users with the selected role only.
> 

| Test ID | TC-AD-06 |
| --- | --- |
| Method | GET |
| Status Code | 200 |
| Request URL | [https://opensource-demo.orangehrmlive.com/web/index.php/api/v2/admin/users?limit=50&offset=0&userRoleId=2&sortField=u.userName&sortOrder=ASC](https://opensource-demo.orangehrmlive.com/web/index.php/api/v2/admin/users?limit=50&offset=0&userRoleId=2&sortField=u.userName&sortOrder=ASC) |
| Request Payload | limit=50&offset=0&**userRoleId=2**&sortField=u.userName&sortOrder=ASC |
| Response | Response returns users with role ESS

 },
"userRole": {
"id": 2,
"name": "ESS",
"displayName": "ESS"
} |