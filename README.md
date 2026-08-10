# Restful Booker API Automation

API automation tests created with Postman and Newman.

## Test Coverage

- Authentication
- Get booking IDs
- Get booking information
- Create booking
- Update booking
- Partial booking update
- Delete booking

## Tools

- Postman
- Newman
- REST API
- JavaScript test scripts

## Running Tests

```bash
newman run restful-booker.postman_collection.json \
-e restful-booker.postman_environment.json
