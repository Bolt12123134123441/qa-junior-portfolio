# Restful-Booker API Testing

Manual API testing of the Restful-Booker booking flow in Postman: test cases, execution results and documented findings.

## Objective
Verify the core booking flow of the Restful-Booker API
(https://restful-booker.herokuapp.com) before a hypothetical release:
authentication, creating, reading, updating and deleting bookings.

## Scope
- In scope: /ping, /auth, /booking (GET, POST, PUT, PATCH, DELETE)
- Out of scope: performance and security testing

## Environment
- Base URL: https://restful-booker.herokuapp.com
- Tools: Postman
- Documentation: https://restful-booker.herokuapp.com/apidoc/index.html

## Contents
- [Test cases and results](test-case.md)
- [Findings](Findings.md)
- [Postman collection](collection/)

## Approach
- Studied the official API documentation and derived test cases from it
- Executed each test case manually in Postman and recorded expected vs. actual results
- Covered positive scenarios, negative scenarios (invalid data, missing token, non-existent IDs), authorization checks and response structure
- Classified every deviation: defect, observation (documentation is silent) or documented behavior

## Findings
- [OBS-001](Findings.md): POST /booking accepts a checkout date earlier than the checkin date
