# Findings

### OBS-001: POST /booking accepts a checkout date earlier than the checkin date

- **Endpoint:** POST /booking
- **Test case:** TC-BKG-005
- **Environment:** https://restful-booker.herokuapp.com (public instance), tested with Postman on 25.10.2026
- **Preconditions:** No authentication required

**Steps to reproduce**
1. Send the following request:

   POST https://restful-booker.herokuapp.com/booking
   Headers: `Content-Type: application/json`, `Accept: application/json`

   ```json
   {
     "firstname": "John",
     "lastname": "Pork",
     "totalprice": 150,
     "depositpaid": true,
     "bookingdates": {
       "checkin": "2026-11-10",
       "checkout": "2026-11-05"
     },
     "additionalneeds": "Breakfast"
   }
   ```

   Equivalent curl command:

   ```bash
   curl -X POST https://restful-booker.herokuapp.com/booking \
     -H "Content-Type: application/json" \
     -H "Accept: application/json" \
     -d '{"firstname":"John","lastname":"Pork","totalprice":150,"depositpaid":true,"bookingdates":{"checkin":"2026-11-10","checkout":"2026-11-05"},"additionalneeds":"Breakfast"}'
   ```

2. Note the `bookingid` in the response.
3. Send `GET https://restful-booker.herokuapp.com/booking/{bookingid}` with `Accept: application/json` (do this within a few minutes, the data resets every 10 minutes).

**Expected result:** The booking is rejected with a 4xx status and an error message, because the checkout date is earlier than the checkin date.

**Actual result:**
- Step 1: `200 OK`, the response contains a `bookingid` and the booking with the same reversed dates.
- Step 3: `200 OK`, the booking is stored with `checkin: 2026-11-10` and `checkout: 2026-11-05`.

**Reproducibility:** 3 out of 3 attempts

**Severity:** Medium
**Type:** Observation (documentation does not describe date validation)
**Evidence:** screenshots/TC-BKG-005-post-response.png, screenshots/TC-BKG-005-get-response.png

**Notes:** A user interface may prevent this input, but the API should validate data independently, because other clients (mobile apps, scripts) can call it directly.
