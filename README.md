# DummyJSON API Testing Portfolio

API testing portfolio using **Postman**, **Newman** and **GitHub Actions** to validate a public e-commerce API.

This project demonstrates how to design, execute and automate API tests using Postman collections, JavaScript assertions, environment variables, Newman CLI execution, HTML reports and CI execution with GitHub Actions.

## API Under Test

This project uses the public DummyJSON API:

```text
https://dummyjson.com

The tested flows are based on an e-commerce-like API, including authentication, product catalog, product search, pagination, carts and negative validations.

Tools Used
Postman
Newman
Newman HTML Extra Reporter
GitHub Actions
JavaScript test scripts
Node.js / npm
Test Coverage
Health Check

Validates that the API is available and returns a valid products response.

Covered request:

GET /products?limit=1
Authentication

Validates authentication behavior and protected endpoint access.

Covered requests:

POST /auth/login
GET /auth/me
GET /auth/me without token
POST /auth/login with invalid credentials

Main validations:

Successful login with valid credentials.
Access token and refresh token are returned.
Authenticated user data matches the login user.
Protected endpoint rejects requests without token.
Invalid credentials do not return authentication tokens.
Products Catalog

Validates product catalog responses, pagination, search and category filtering.

Covered requests:

GET /products
GET /products?limit=5&skip=10
GET /products/search?q=phone
GET /products/{product_id}
GET /products/category-list
GET /products/category/{category_slug}

Main validations:

Products response structure.
Pagination fields: products, total, skip, limit.
Correct data types.
Pagination values match requested parameters.
Search returns products related to the search term.
Product detail contains required catalog fields.
Product category matches requested category.
Carts

Validates user cart retrieval and cart detail data.

Covered requests:

GET /carts/user/{user_id}
GET /carts/{cart_id}

Main validations:

User carts are returned.
Cart belongs to the expected user.
Cart contains products.
Cart totals and quantities are present.
Cart detail matches the stored cart_id.
Negative Validations

Validates controlled error responses for invalid scenarios.

Covered requests:

GET /products/{non_existing_product_id}
GET /carts/{non_existing_cart_id}
GET /auth/me without token
POST /auth/login with invalid credentials

Main validations:

Non-existing product returns 404.
Non-existing cart returns 404.
Protected endpoint without token returns 401.
Invalid login does not return tokens.
Error responses include a clear message.
Project Structure
dummyjson-api-testing-portfolio/
  .github/
    workflows/
      newman-tests.yml

  collections/
    dummyjson-ecommerce-api.postman_collection.json

  environments/
    dummyjson-production.postman_environment.json

  testResults/
    .gitkeep

  .gitignore
  package.json
  package-lock.json
  README.md
Environment Variables

The Postman environment includes static and dynamic variables.

Static variables

These variables are required before running the collection:

base_url
username
password
search_term
category_slug
non_existing_product_id
non_existing_cart_id
Dynamic variables

These variables are generated during execution:

access_token
refresh_token
user_id
product_id
cart_id
How to Run Locally

Install dependencies:

npm install

Run the Postman collection with Newman:

npm test

Generate an HTML report:

npm run report

The HTML report will be generated in:

testResults/htmlreport.html
GitHub Actions

This project includes a GitHub Actions workflow that runs the Newman API tests automatically on:

push
pull_request

Workflow file:

.github/workflows/newman-tests.yml

The workflow:

Checks out the repository.
Installs Node.js.
Installs project dependencies.
Runs the Newman API tests.
Generates an HTML report.
Uploads the report as a GitHub Actions artifact.
Reports

The HTML report is generated using:

newman-reporter-htmlextra

Local reports are generated in:

testResults/htmlreport.html

In GitHub Actions, the report is uploaded as an artifact named:

newman-html-report
Notes

This project uses a public demo API and public demo credentials.

Dynamic values such as tokens, user IDs, product IDs and cart IDs are generated during the test execution and are not meant to be manually maintained.

The goal of this portfolio is to demonstrate practical API testing skills, including:

API test design.
Postman test scripts.
Environment variable management.
Request chaining.
Positive and negative validations.
Newman CLI execution.
HTML report generation.
CI execution with GitHub Actions.

## Topics recomendados para GitHub

Agrega estos topics al repo:

```text
postman
newman
api-testing
qa
quality-assurance
github-actions
test-automation
javascript
postman-collection
api-automation
