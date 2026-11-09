## Automated Tests
The automated collection runs the full booking flow as one chain:
authentication, create, read, update (PUT), partial update (PATCH), delete and
deletion verification, plus authorization checks (403 without a token) and
a non-existent ID check (404).

- Collection: [autpost.postman_collection.json](autpost.postman_collection.json)
- Result: 13 requests, <N> assertions, <N> failed
- Newman report: [my-report.html](my-report.html)



### How to run
1. Import the collection into Postman and click **Run** (keep the request order)
2. Or with Newman:
   `newman run collection/restful-booker.automated.postman_collection.json`

Note: the public API resets its data every 10 minutes and is rate limited,
so avoid running the collection repeatedly in a short time.
