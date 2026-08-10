# Restful Booker API Automation

API automation testing project using **Postman, Newman, and Jenkins**.

This project tests the core functionality of the Restful Booker API and demonstrates how API tests can be integrated into a CI workflow.

## Project Overview

The project uses Postman to create and maintain API tests, Newman to execute the collection from the command line, and Jenkins to automate test execution.

### Test Workflow

```text
GitHub
   ↓
GitHub Webhook
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
* Partial booking update
* Delete booking

The collection currently contains **22 assertions** validating response status codes, response structure, authentication, and booking data.

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

Booking IDs are dynamically captured from API responses rather than relying on hardcoded IDs. This allows the tests to remain reliable when booking data changes between executions.

## Tools & Technologies

* **Postman** — API development and test creation
* **Newman** — Command-line execution of Postman collections
* **Newman HTML Extra Reporter** — HTML test reporting
* **Jenkins** — Continuous integration
* **Git / GitHub** — Source control
* **GitHub Webhooks** — Automated Jenkins triggering
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

A GitHub webhook triggers the Jenkins job when changes are pushed to the repository.

This allows the API tests to execute automatically whenever the project is updated.

## Jenkins Build

The following screenshot shows the Jenkins build executing the Newman API automation successfully.

![Jenkins Build](screenshots/Jenkins%20Build.png)

## Jenkins Successful Run

This screenshot shows a successful Jenkins execution of the API automation suite.

![Jenkins Successful Run](screenshots/Jenkins%20Success%20Run.png)

## Newman HTML Test Report

Jenkins publishes the Newman HTML Extra report after the API tests complete.

![Restful Booker Test Report](screenshots/Restful%20Booker%20Test%20Report.png)

## Example Test Results

A successful execution runs all seven API requests and validates the test assertions.

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
├── restful-booker.postman_environment.json
│
└── screenshots/
    ├── Jenkins Build.png
    └── Restful Booker Test Report.png
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
* CI troubleshooting and debugging

















