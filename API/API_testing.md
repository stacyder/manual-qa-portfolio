# API Testing

Postman
REST API
JSON

[GoRest API Tests.postman_collection.json](API%20Testing/GoRest_API_Tests.postman_collection.json)

| TC ID | Test Name | Steps | Expected Result | Actual Result | Status |
| --- | --- | --- | --- | --- | --- |
| TC-API-01 | POST create user | Send POST /users with JSON body | 201 Created, JSON object with entered data + id | 201 Created, JSON object returned with id=12345 | Pass |
| TC-API-02 | GET user by ID | Send GET /users/{id} | 200 OK, JSON object with user’s data | 200 OK, JSON object returned with id=12345 | Pass |
| TC-API-03 | PATCH update user | Send PATCH /users/{id} with JSON body | 200 OK, JSON object with updated data | 200 OK, name updated to “Updated Name” | Pass |
| TC-API-04 | DELETE user | Send DELETE /users/{id} | 204 No Content, empty body | 204 No Content, body empty | Pass |
| TC-API-05 | GET deleted user | Send GET /users/{id} after deletion | 404 Not Found, JSON error | 404 Not Found, user not found | Pass |

| TC ID | Test Name | Steps | Body | URL | Method | Headers | Expected Result | Actual Result | Status |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| N1 | POST duplicate email | 1. Create a new POST request with the same email as the existing user. 2. Click Send. | `json { "name": "Test User", "gender": "male", "email": "testuser+{{timestamp}}@example.com", "status": "active" }` | [https://gorest.co.in/public/v2/users](https://gorest.co.in/public/v2/users) | POST | Authorization: Bearer `<token>` Content-Type: application/json Accept: application/json | 422 Unprocessable Entity | 422 | Pass |
| N2 | PATCH invalid data | 1. Create a new PATCH request for the existing user `{{userId}}`. 2. Insert invalid gender value. 3. Click Send. | `json { "gender": "unknown" }` | [https://gorest.co.in/public/v2/users/{{userId}}](https://gorest.co.in/public/v2/users/%7B%7BuserId%7D%7D) | PATCH | Authorization: Bearer `<token>` Content-Type: application/json Accept: application/json | 422 Unprocessable Entity | 422 | Pass |
| N3 | GET invalid ID | 1. Create a new GET request with a non-existent ID `9999999`. 2. Click Send. | — | [https://gorest.co.in/public/v2/users/9999999](https://gorest.co.in/public/v2/users/9999999) | GET | Authorization: Bearer `<token>` Accept: application/json | 404 Not Found | 404 | Pass |
| N4 | DELETE invalid ID | 1. Create a new DELETE request with a non-existent ID `9999999`. 2. Click Send. | — | [https://gorest.co.in/public/v2/users/9999999](https://gorest.co.in/public/v2/users/9999999) | DELETE | Authorization: Bearer `<token>` Accept: application/json | 404 Not Found | 404 | Pass |