
# Restful Booker API Automation

Automated REST API testing project using **Postman, Newman, and Jenkins**.

The project validates the core functionality of the Restful Booker API and demonstrates how API tests can be integrated into a CI workflow. Tests are executed through Newman and automatically triggered by GitHub commits using a Jenkins webhook.

## Project Overview

This project was created to demonstrate API automation and CI/CD practices commonly used in software QA and SDET environments.

### Test Workflow

```text
GitHub
   ↓
Webhook
   ↓
Jenkins
   ↓
Newman
   ↓
Postman Collection
   ↓
Restful Booker API
   ↓
HTML Test Report
```

## Test Coverage

The Postman collection covers the following API workflows:

* Authentication
* Retrieve booking IDs
* Retrieve booking information
* Create a booking
* Update a booking
* Partially update a booking
* Delete a booking

The tests include **22 assertions** validating response status codes, response structure, booking data, authentication, and CRUD operations.

## API Test Design

The collection uses Postman JavaScript scripts for:

* Response validation
* Status code assertions
* JSON response validation
* Dynamic booking ID handling
* Authentication token management
* Environment variables
* Pre-request validation
* Collection variables

Booking IDs are dynamically captured from API responses rather than relying on hardcoded IDs. This helps prevent tests from failing when booking data changes between executions.

## Tools & Technologies

* **Postman** — API development and test creation
* **Newman** — Command-line execution of Postman collections
* **Newman HTML Extra Reporter** — HTML test reporting
* **Jenkins** — Continuous integration
* **Git / GitHub** — Source control and CI trigger
* **JavaScript** — Postman test and pre-request scripts
* **REST API / HTTP** — API testing

## Running Tests Locally

Install Newman:

```bash
npm install -g newman
```

Run the collection:

```bash
newman run restful-booker.postman_collection.json \
-e restful-booker.postman_environment.json
```

### Generate an HTML Report

```bash
newman run restful-booker.postman_collection.json \
-e restful-booker.postman_environment.json \
-r cli,htmlextra \
--reporter-htmlextra-export newman-report.html
```

The HTML report is generated after the test execution and can be opened in a browser.

## Jenkins CI

The project is integrated with Jenkins for continuous integration.

The Jenkins job:

1. Pulls the latest code from the GitHub `main` branch.
2. Configures the Node.js/Newman environment.
3. Executes the Postman collection using Newman.
4. Generates an HTML test report.
5. Publishes the report in Jenkins.
6. Marks the build as successful or failed based on the test results.

### Automated Trigger

A GitHub webhook triggers the Jenkins job whenever changes are pushed to the repository.

This allows API tests to execute automatically whenever the project is updated.

## Example Jenkins Result

A successful execution runs all seven API requests and validates the test assertions.

Example:

```text
Requests:       7
Failed:         0
Assertions:    22
Failed:         0
Build:       SUCCESS
```

## Project Structure

```text
restful-booker-api-tests/
│
├── .gitignore
├── README.md
├── restful-booker.postman_collection.json
└── restful-booker.postman_environment.json
```

## Skills Demonstrated

This project demonstrates practical experience with:

* REST API testing
* API test automation
* Postman
* Newman
* JavaScript test scripting
* Dynamic test data
* Environment and collection variables
* Authentication handling
* CRUD API testing
* Git and GitHub
* Jenkins CI
* GitHub webhooks
* Automated test execution
* HTML test reporting
* Debugging CI environment issues


