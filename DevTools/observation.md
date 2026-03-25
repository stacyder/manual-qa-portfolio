# Observation

**Observation ID:** OBS-TS-PIM-06

**Title:** Additional GET request returns status code 422 after employee deletion

---

### Description

During testing of the **Delete Employee** functionality, a successful **DELETE request (Status Code 200)** was observed in the Network tab indicating that the employee was deleted successfully.

After the deletion request, an additional **GET request** was triggered automatically by the system to retrieve the employee data.

This request returned **Status Code 422**, likely because the employee record no longer exists in the system.

---

### Steps to Observe

1. Open **Developer Tools** in the browser.
2. Navigate to the **Network** tab.
3. Go to **PIM → Employee List**.
4. Select an existing employee.
5. Click **Delete** and confirm the action.
6. Observe the network requests triggered after deletion.

---

### Actual Result

- **DELETE request** returns **Status Code 200**.
- An additional **GET request** is triggered afterwards.
- The **GET request returns Status Code 422**.

---

### Expected Result

- Employee should be deleted successfully.
- No visible errors should appear in the UI.

---

### Impact

No visible impact on the user interface.

Employee is removed successfully from the system.

---

**Observation ID:** OBS-TС-OH-07

**Title:** Additional GET request returns status code 422 after employee deletion

---

During network analysis of the login functionality in OrangeHRM, it was observed that the server returns status code **302** after submitting incorrect login credentials. The response contains a redirect to the login page (`/auth/login`).

---

**Steps Observed:**

1. Open Developer Tools → Network tab.
2. Enter incorrect username or password on the Login page.
3. Click **Login**.
4. Observe the request `POST /auth/validate`.

---

**Observed Result:**

The server returns **Status Code 302** and redirects the user to `/auth/login`.

**Conclusion:**

This behavior is expected. The system prevents authentication with invalid credentials and redirects the user back to the login page.