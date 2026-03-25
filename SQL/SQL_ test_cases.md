# SQL test_cases

Positive Tests

| TC ID | Test Name | Steps | SQL Query | Expected Result | Status |
| --- | --- | --- | --- | --- | --- |
| P1 | INSERT new user | Insert a new user into the `users` table | `sql INSERT INTO users (name, gender, email, status) VALUES ('Test User', 'male', 'testuser1@example.com', 'active'); SELECT * FROM users;` | New row created with correct data | Pass |
| P2 | SELECT user by ID | Select the user by ID 1 | `sql SELECT * FROM users WHERE id = 1;` | Returns the user row with correct values | Pass |
| P3 | UPDATE user status | Update user status to 'inactive' | `sql UPDATE users SET status = 'inactive' WHERE id = 1; SELECT * FROM users WHERE id = 1;` | Status updated to 'inactive' | Pass |
| P4 | DELETE user | Delete user by ID 1 | `sql DELETE FROM users WHERE id = 1; SELECT * FROM users;` | User removed from table | Pass |
| P5 | SELECT deleted user | Try to select deleted user | `sql SELECT * FROM users WHERE id = 1;` | No rows returned | Pass |

Negative Tests

| TC ID | Test Name | Steps | SQL Query | Expected Result | Status |
| --- | --- | --- | --- | --- | --- |
| N1 | INSERT duplicate email | Try to insert a user with an existing email | `sql INSERT INTO users (name, gender, email, status) VALUES ('Another User', 'male', 'testuser1@example.com', 'active');` | Error: UNIQUE constraint violation | Pass |
| N2 | UPDATE invalid gender | Try to update user's gender to invalid value | `sql UPDATE users SET gender = 'unknown' WHERE id = 2;` | Error: ENUM/constraint violation | Pass |
| N3 | SELECT non-existent user | Select user with ID that does not exist | `sql SELECT * FROM users WHERE id = 9999;` | No rows returned | Pass |
| N4 | DELETE non-existent user | Delete user with ID that does not exist | `sql DELETE FROM users WHERE id = 9999; SELECT * FROM users;` | 0 rows affected, table unchanged | Pass |