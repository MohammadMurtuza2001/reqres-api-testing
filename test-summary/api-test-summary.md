# API Test Summary — ReqRes API

| | |
|---|---|
| **Tester** | Mohammad Murtuza Moin |
| **Date** | 7-May-2026 |
| **API Under Test** | https://reqres.in |
| **Tool** | Postman v12.9.6 + Newman v6.2.2 |

---

## Endpoints Tested

| Endpoint | Method | Purpose |
|----------|--------|---------|
| /api/users?page=2 | GET | Retrieve the list of users on page 2 |
| /api/users/2 | GET | Retrieve a single user by ID |
| /api/users/999 | GET | Verify correct 404 response for a non-existent user |
| /api/users | POST | Create a new user with name and job fields |
| /api/users/2 | PUT | Update the complete data of an existing user |
| /api/users/2 | DELETE | Delete a user and verify empty response |
| /api/login | POST | Verify successful login with correct credentials |
| /api/login | POST | Verify failed login with incorrect credentials |

---

## Test Execution Results

| Total Tests | Passed | Failed | Pass Rate |
|-------------|--------|--------|-----------|
| 16 | 16 | 0 | 100% |

---

## Test Results by Endpoint

| Endpoint | Method | Tests | Passed | Failed | Notes |
|----------|--------|-------|--------|--------|-------|
| /api/users?page=2 | GET | 2 | 2 | 0 | Status 200 confirmed, data array present |
| /api/users/2 | GET | 2 | 2 | 0 | Status 200 confirmed, user id equals 2 |
| /api/users/999 | GET | 2 | 2 | 0 | Status 404 confirmed, response within 2000ms |
| /api/users | POST | 2 | 2 | 0 | Status 201 confirmed, name field present in response |
| /api/users/2 | PUT | 2 | 2 | 0 | Status 200 confirmed, job field present in response |
| /api/users/2 | DELETE | 2 | 2 | 0 | Status 204 confirmed, empty response body received |
| /api/login (success) | POST | 2 | 2 | 0 | Status 200 confirmed, token present in response |
| /api/login (fail) | POST | 2 | 2 | 0 | Status 400 confirmed, error field present in response |

---

## Test Cases

Full test case documentation (20 test cases) available here:
[View Test Cases on Google Sheets](https://docs.google.com/spreadsheets/d/1DOS1U8fGukQIAvANRHiUabf2O-nUd6b89yGk9-k_ha4/edit?usp=sharing)

---

## Key Observations

- API core functionality is solid — all requests returned correct status codes
  with response times consistently below 600ms, well within acceptable limits
- Some requests behaved differently than expected initially, which was later
  understood to be mock API behavior rather than a real API bug
- ReqRes does not validate data types or reject duplicate entries — in a real
  production API, sending invalid data types or duplicate records should return
  400 Bad Request or 409 Conflict. This is a known limitation of mock APIs
- The API requires an x-api-key header for all requests. A free account at
  reqres.in provides 100 requests per day, sufficient for testing and learning
- Deleting a user and re-fetching them still returns 200 — this confirms ReqRes
  does not persist data, which is expected mock behavior but would be a critical
  bug in a real system

---

## Conclusion

The ReqRes API behaved correctly across all 8 endpoints tested, returning the
expected status codes and response structures in every case. All 16 automated
assertions passed with a 100% pass rate, and response times were consistently
fast. The API is reliable for testing and learning purposes, though its mock
nature means it does not enforce real-world data validation rules that a
production API would require.
