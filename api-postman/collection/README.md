
## How to run
1. Import `collection/restful-booker.postman_collection.json` into Postman
2. Run `TC-AUTH-001` first to get a token (it is saved to the `token` collection variable)
3. Create a fresh booking with `TC-BKG-003` before running requests that need a booking ID

Note: booking IDs in the manual requests are examples from the test session.
The public API resets its data every 10 minutes.
