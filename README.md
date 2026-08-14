# RentSolo Analytics API Testing

A QA/API testing project for the **RentSolo Analytics Page APIs**, created using Postman.

## Project Overview

This repository demonstrates API testing work performed against the RentSolo Analytics APIs, including collection execution and analysis of automated test results.

### Tools & Technologies

- **Postman** — API request creation and functional testing
- **Newman** — CLI/automated collection execution
- **JavaScript** — Postman test scripts
- **Git/GitHub** — Version control and project documentation

## Test Execution

The uploaded Postman test-run artifact reports:

| Metric | Result |
|---|---:|
| Total Passed | 35 |
| Total Failed | 1 |
| Total Requests | 9 |
| Execution Status | Finished |

> The repository includes the original test-run result JSON in `reports/test-run-results.json`.

## Repository Structure

```text
rentsolo-api-testing-postman/
├── README.md
├── .gitignore
├── postman/
│   └── RentSolo-Analytics-APIs.postman_collection.json
├── reports/
│   └── test-run-results.json
└── screenshots/
    └── README.md
```

## Testing Areas

- API functional testing
- Positive and negative test scenarios
- HTTP response validation
- Response data validation
- API regression testing
- Automated collection execution
- Test-result analysis

## How to Use

### 1. Import into Postman

Open Postman and import:

```text
postman/RentSolo-Analytics-APIs.postman_collection.json
```

### 2. Configure the environment

Create/configure the required environment variables and credentials for the target RentSolo environment.

**Do not commit passwords, access tokens, API keys, cookies, or other secrets.**

### 3. Execute the collection

Run the collection from the Postman Collection Runner.

For Newman:

```bash
npm install -g newman
newman run postman/RentSolo-Analytics-APIs.postman_collection.json
```

## QA Skills Demonstrated

This project demonstrates practical experience with:

- API testing
- Postman collections
- Test assertions
- API response validation
- Regression testing
- Automated test execution
- Test-result reporting
- Git/GitHub project organization

## Important Note

The uploaded source file is a **Postman test-run export** rather than the original Postman collection. Therefore, the repository preserves the complete test-run artifact under `reports/` and provides a collection placeholder under `postman/`.

For a fully executable GitHub repository, export the original Postman collection from Postman using:

**Collection → ... → Export → Collection v2.1**

Then replace the placeholder collection file in `postman/`.

## Author

QA / Software Testing Portfolio Project
