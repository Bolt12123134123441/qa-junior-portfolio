# Test Cases: Restful-Booker API

| ID | Endpoint | Scenario | Expected result | Priority |
|----|----------|----------|-----------------|----------|
| TC-PING-001 | GET /ping | Health check | API is up, success status returned | High |
| TC-AUTH-001 | POST /auth | Valid credentials | 200, token returned | High |
| TC-AUTH-002 | POST /auth | Invalid password | No token returned | High |
| TC-BKG-001 | GET /booking | Get all booking IDs | 200, array of objects with bookingid | High |
| TC-BKG-002 | GET /booking/:id | Existing booking | 200, all fields present with correct types | High |
| TC-BKG-003 | POST /booking | Create with valid data | 200, bookingid returned, data matches request | High |
| TC-BKG-004 | POST /booking | Missing required field | Booking is not created, error returned | High |
| TC-BKG-005 | POST /booking | Checkout date before checkin date | Booking is rejected | Medium |
| TC-BKG-006 | POST /booking | totalprice sent as string | Booking is rejected or value handled correctly | Medium |
| TC-BKG-007 | GET /booking/:id | Non-existent ID | 404 | High |
| TC-BKG-008 | PUT /booking/:id | Update with valid token | 200, all fields updated | High |
| TC-BKG-009 | PUT /booking/:id | Update without token | 403 | High |
| TC-BKG-010 | PATCH /booking/:id | Partial update with valid token | 200, only sent fields changed | High |
| TC-BKG-011 | DELETE /booking/:id | Delete with valid token | Booking deleted, GET returns 404 | High |
| TC-BKG-012 | DELETE /booking/:id | Delete without token | 403, booking still exists | High |
