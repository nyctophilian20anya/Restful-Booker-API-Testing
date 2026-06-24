# Restful Booker API Testing - Postman Collection
## Overview
Comprehensive API test suite for Restful Booker API covering Auth, Booking CRUD operations, and Negative test scenarios.
## Tech Stack
- Postman
- Newman CLI
- newman-reporter-html
- Restful Booker API (https://restful-booker.herokuapp.com)
## Collection Structure
- Auth - Token Generation
- Booking - Create, Get, Update, Partial Update, Delete
- Negative Tests - Invalid token, Missing fields, Non-existent booking, Invalid ID format
## Key Concepts Covered
- Token-based authentication with chaining
- CRUD operations (GET, POST, PUT, PATCH, DELETE)
- Negative testing and error handling
- Environment variables
- Newman CLI execution
## How to Run
Install Newman:
npm install -g newman
Install HTML Reporter:
npm install -g newman-reporter-html
Run Collection:
newman run "Restful-Booker-Collection.json" -e "RestfulBooker-Env.json" --insecure
Run with HTML Report:
newman run "Restful-Booker-Collection.json" -e "RestfulBooker-Env.json" --insecure -r html --reporter-html-export RestfulBooker-Report.html
## Test Results
- Total Requests: 11
- Total Assertions: 27
- Pass Rate: 89%
## Test Report
Open RestfulBooker-Report.html in browser to view detailed test results.
## Known Issues & Resolutions
SSL Certificate Error (Corporate Network)
Error: unable to get local issuer certificate
Cause: Corporate network blocks SSL verification
Resolution: Use --insecure flag with Newman
Update Booking - 403 Forbidden (Newman)
Cause: Token is session-based and expires between requests
Resolution: Manually run Generate Token before collection run
CI/CD Fix: Use pre-request script to auto-refresh token in pipeline