# BUG Reports

# BUG-01

**Bug ID:** BUG-OH-001

**Title:** Employee search field accepts leading spaces and returns inconsistent results

**Module:** PIM

**Preconditions**

User is logged in and navigates to **PIM → Employee List**.

**Steps to Reproduce**

1. Enter `" Linda"` (with leading spaces) in **Employee Name** field.
2. Click **Search**.

**Expected Result**

System should trim spaces and return correct employee results.

**Actual Result**

Search results may be inconsistent or empty.

**Severity:** Low

**Priority:** Low

---

# BUG-02

**Bug ID:** BUG-OH-002

**Title:** System allows creating employee with only spaces in required fields

**Module:** PIM

**Preconditions**

User is on **PIM → Add Employee** page.

**Steps**

1. Enter `" "` (space) in **First Name**.
2. Enter `" "` in **Last Name**.
3. Click **Save**.

**Expected Result**

System should display validation error.

**Actual Result**

Form accepts input containing only spaces.

**Severity:** Medium

**Priority:** Medium

---

# BUG-03

**Bug ID:** BUG-OH-003

**Title:** Deleted employee still appears in search results until page refresh

**Module:** PIM

**Preconditions**

Employee exists in system.

**Steps**

1. Delete employee from Employee List.
2. Immediately search for the same employee name.

**Expected Result**

Deleted employee should not appear in results.

**Actual Result**

Employee still appears until page refresh.

**Severity:** Medium

**Priority:** Medium

---

# BUG-04

**Bug ID:** BUG-OH-004

**Title:** Employee search field allows extremely long input

**Module:** PIM

**Steps**

1. Enter 300+ characters in **Employee Name** field.
2. Click **Search**.

**Expected Result**

Input length should be limited.

**Actual Result**

Field accepts extremely long input without validation.

**Severity:** Low

**Priority:** Low

---

# BUG-05

**Bug ID:** BUG-OH-005

**Title:** Multiple network requests triggered when clicking Search button repeatedly

**Module:** PIM

**Steps**

1. Enter employee name.
2. Click **Search** several times quickly.

**Expected Result**

Only one request should be triggered.

**Actual Result**

Multiple requests appear in Network tab.

**Severity:** Low

**Priority:** Low

---

# BUG-06

**Bug ID:** BUG-OH-006

**Title:** User role filter returns incorrect results

**Module:** Admin

**Preconditions**

Multiple users with different roles exist.

**Steps**

1. Navigate to **Admin → User Management**.
2. Select **User Role = ESS**.
3. Click **Search**.

**Expected Result**

Only users with **ESS role** should appear.

**Actual Result**

Users with other roles may appear in results.

**Severity:** High

**Priority:** High

---

# BUG-07

**Bug ID:** BUG-OH-007

**Title:** Username field allows special characters without validation

**Module:** Admin

**Steps**

1. Go to **Admin → Add User**.
2. Enter username `admin!!!@@@`.
3. Click **Save**.

**Expected Result**

System should restrict invalid characters.

**Actual Result**

Username with special characters is accepted.

**Severity:** Medium

**Priority:** Medium

---

# BUG-08

**Bug ID:** BUG-OH-008

**Title:** Password field accepts weak password without warning

**Module:** Admin

**Steps**

1. Go to **Admin → Add User**.
2. Enter password `123`.
3. Click **Save**.

**Expected Result**

System should require strong password.

**Actual Result**

Weak password is accepted.

**Severity:** Medium

**Priority:** Medium

---

# BUG-09

**Bug ID:** BUG-OH-009

**Title:** Employee autocomplete dropdown displays duplicate suggestions

**Module:** Admin

**Steps**

1. Navigate to **Admin → Add User**.
2. Start typing employee name.

**Expected Result**

Employee should appear once in dropdown.

**Actual Result**

Duplicate employee suggestions appear.

**Severity:** Low

**Priority:** Low

---

# BUG-10

**Bug ID:** BUG-OH-010

**Title:** Error message disappears too quickly after validation failure

**Module:** PIM

**Steps**

1. Navigate to **Add Employee**.
2. Leave required fields empty.
3. Click **Save**.

**Expected Result**

Validation error message should remain visible.

**Actual Result**

Error message disappears quickly.

**Severity:** Low

**Priority:** Low