# ReqRes API Testing — Postman + Newman

## Project Overview
ReqRes is a free hosted mock API built for testers to 
practice API testing without needing a real backend. 
I used it to build my first complete API testing project 
— exploring endpoints, writing test cases, automating 
assertions in Postman, and generating a Newman report.

## What I Tested

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

## Tools Used

- **Postman v12.9.6** — used to organize all requests into a single collection,
  send requests, and write automated JavaScript assertions for status codes,
  response body fields, and response time
- **Newman v6.2.2** — used to run the entire Postman collection from the
  command line and generate a shareable HTML report

## How to Run the Tests

Make sure Newman is installed:

```bash
npm install -g newman
npm install -g newman-reporter-htmlextra
```

Place `reqres-collection.json` and `reqres-env.json` in the same folder,
open your terminal in that folder and run:

```bash
newman run reqres-collection.json -e reqres-env.json -r htmlextra --reporter-htmlextra-export reports/api-report.html
```

The HTML report will be generated inside a `/reports` folder.

## Test Results

| Total Tests | Passed | Failed | Pass Rate |
|-------------|--------|--------|-----------|
| 16 | 16 | 0 | 100% |

## Key Learnings

- Learned all the important HTTP status codes and what they mean in real testing
  scenarios — 200, 201, 204, 400, 404 and when to expect each one
- Learned how to use Postman professionally — environments, collection variables,
  pre-request scripts, and automated assertions using JavaScript
- Discovered the difference between mock API behavior and real API behavior —
  a mock API accepts almost anything, while a real API must validate data types,
  reject duplicates, and enforce proper authentication

## Project Deliverables

- **Postman Collection:** All 8 requests with automated assertions ([collection/](./collection/))
- **Test Cases:** 20 documented test cases covering all endpoints ([View Spreadsheet](https://docs.google.com/spreadsheets/d/1DOS1U8fGukQIAvANRHiUabf2O-nUd6b89yGk9-k_ha4/edit?usp=sharing))
- **Newman Report:** Full automated test run report ([View Live Report](https://mohammadmurtuza2001.github.io/reqres-api-testing/report/api-report.html))
- **Test Summary:** Written summary of results and observations ([test-summary/](./test-summary/api-test-summary.md))

## Author

**Mohammad Murtuza Moin** | Aspiring QA Engineer
