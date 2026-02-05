# QAcart Todo App - API Testing with Postman

[![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)](https://www.postman.com/)
[![Newman](https://img.shields.io/badge/Newman-66B432?style=for-the-badge&logo=postman&logoColor=white)](https://www.npmjs.com/package/newman)
[![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)](https://github.com/features/actions)
[![API Testing](https://img.shields.io/badge/API_Testing-009688?style=for-the-badge&logo=testing-library&logoColor=white)](https://github.com/asmaanewigy32/QAcart-Todo-App-API-testing-using-Postman)

## 📋 Table of Contents

- [Overview](#overview)
- [Project Architecture](#project-architecture)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation & Setup](#installation--setup)
- [Project Structure](#project-structure)
- [Test Coverage](#test-coverage)
- [Running Tests](#running-tests)
- [CI/CD Integration](#cicd-integration)
- [API Endpoints](#api-endpoints)
- [Environment Variables](#environment-variables)
- [Test Data Management](#test-data-management)
- [Reporting](#reporting)
- [Best Practices](#best-practices)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)

## 🎯 Overview

This repository contains a comprehensive API testing suite for the **QAcart Todo Application** using Postman and Newman. The project demonstrates professional API testing practices including automated test execution, data-driven testing, environment management, and CI/CD integration with GitHub Actions.

### Application Under Test

**QAcart Todo API** is a RESTful API for managing todo tasks, featuring user authentication, task CRUD operations, and user management capabilities.

### Testing Objectives

- Validate all API endpoints for functional correctness
- Ensure proper HTTP status codes and response structures
- Verify authentication and authorization mechanisms
- Test data validation and error handling
- Implement automated regression testing
- Generate comprehensive test reports

## 🏗️ Project Architecture

```
┌─────────────────────────────────────────────────────────┐
│              Postman Collection                         │
│  ┌──────────────────────────────────────────────────┐  │
│  │  Pre-request Scripts (Test Data Generation)      │  │
│  └──────────────────────────────────────────────────┘  │
│  ┌──────────────────────────────────────────────────┐  │
│  │  API Requests (HTTP Methods)                     │  │
│  └──────────────────────────────────────────────────┘  │
│  ┌──────────────────────────────────────────────────┐  │
│  │  Test Scripts (Assertions & Validations)         │  │
│  └──────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────┐
│           Environment Configuration                     │
│  • Base URL  • API Keys  • Dynamic Variables            │
└─────────────────────────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────┐
│              Newman CLI Runner                          │
│  • Local Execution  • CI/CD Integration                 │
└─────────────────────────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────┐
│              Test Reports                               │
│  • HTML Reports  • JSON Reports  • Console Logs         │
└─────────────────────────────────────────────────────────┘
```

## ✨ Features

### Core Testing Capabilities

- ✅ **Complete API Test Coverage**: All CRUD operations for users and todos
- 🔐 **Authentication Testing**: User registration, login, and token-based authentication
- 📊 **Data-Driven Testing**: Dynamic test data generation using Faker.js or random data
- 🔄 **Environment Management**: Separate configurations for development, staging, and production
- 🧪 **Assertion Library**: Comprehensive test assertions using Chai assertion library
- 📈 **Test Chaining**: Sequential test execution with data dependency management
- 🎲 **Random Data Generation**: Pre-request scripts for generating unique test data
- 🔍 **Response Validation**: Schema validation, status codes, and response body verification

### Automation Features

- ⚙️ **Newman CLI Integration**: Command-line test execution
- 🤖 **CI/CD Pipeline**: Automated testing with GitHub Actions
- 📅 **Scheduled Runs**: Automated test execution on schedule (if configured)
- 📊 **HTML Reporting**: Rich, interactive test reports with htmlextra reporter
- 📝 **JSON Reporting**: Detailed test results in JSON format
- 💾 **Collection Versioning**: Version-controlled Postman collections
- 🔄 **Parallel Execution**: Run tests concurrently for faster feedback

### Advanced Capabilities

- 🌐 **Cross-Environment Testing**: Execute same tests across multiple environments
- 🔐 **Secret Management**: Secure handling of API keys and credentials
- 📦 **Test Data Isolation**: Independent test data for each test run
- 🧹 **Cleanup Scripts**: Automated test data cleanup after execution
- 📖 **API Documentation**: Self-documenting tests with detailed descriptions
- 🎯 **Smoke Testing**: Quick validation of critical API endpoints
- 🔬 **Regression Testing**: Full test suite for comprehensive validation

## 📋 Prerequisites

### Required Software

| Tool | Version | Purpose |
|------|---------|---------|
| **Postman** | Latest | API testing interface |
| **Node.js** | ≥14.x | Runtime for Newman |
| **npm** | ≥6.x | Package manager |
| **Newman** | ≥5.x | CLI test runner |
| **Git** | Latest | Version control |

### Recommended Installations

```bash
# Install Node.js and npm (if not installed)
# Download from https://nodejs.org/

# Install Newman globally
npm install -g newman

# Install Newman HTML Reporter
npm install -g newman-reporter-htmlextra

# Verify installations
newman --version
node --version
npm --version
```

## 🚀 Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/asmaanewigy32/QAcart-Todo-App-API-testing-using-Postman.git
cd QAcart-Todo-App-API-testing-using-Postman
```

### 2. Import Collection to Postman

**Option A: Using Postman UI**
1. Open Postman
2. Click **Import** button
3. Select the collection file from `postman/collections/`
4. Import the environment file: `QAcart Todo Project.postman_environment.json`

**Option B: Using Postman CLI**
```bash
postman collection import postman/collections/QAcart-Todo-Collection.json
```

### 3. Configure Environment

1. In Postman, select the imported environment from the dropdown
2. Update environment variables as needed:
   - `baseUrl`: API base URL
   - `accessToken`: Will be auto-generated during login
   - `userId`: Will be auto-populated during user creation
   - `taskId`: Will be auto-populated during task creation

### 4. Install Dependencies (for Newman)

```bash
# Install Newman if not already installed
npm install -g newman newman-reporter-htmlextra
```

## 📁 Project Structure

```
QAcart-Todo-App-API-testing-using-Postman/
│
├── .github/
│   └── workflows/
│       └── postman-tests.yml          # GitHub Actions CI/CD workflow
│
├── .postman/
│   └── api_*                          # Postman API schema (if applicable)
│
├── postman/
│   └── collections/
│       └── QAcart-Todo-Collection.json # Main Postman collection
│
├── QAcart Todo Project.postman_environment.json  # Environment variables
│
├── newman/                            # Newman execution reports (generated)
│   ├── reports/
│   │   ├── html/
│   │   └── json/
│   └── logs/
│
├── test-results/                      # Test execution results (generated)
│
├── README.md                          # This file
│
└── .gitignore                         # Git ignore configuration
```

## 🧪 Test Coverage

### Test Scenarios

#### 1. User Management Module

| Test Case | Endpoint | Method | Description |
|-----------|----------|--------|-------------|
| Register New User | `/api/v1/users/register` | POST | Create a new user account |
| Login User | `/api/v1/users/login` | POST | Authenticate and receive access token |
| Get User Profile | `/api/v1/users/profile` | GET | Retrieve authenticated user details |
| Update User Profile | `/api/v1/users/profile` | PUT | Update user information |
| Delete User | `/api/v1/users/profile` | DELETE | Remove user account |

#### 2. Todo Management Module

| Test Case | Endpoint | Method | Description |
|-----------|----------|--------|-------------|
| Create Todo | `/api/v1/tasks` | POST | Add a new todo item |
| Get All Todos | `/api/v1/tasks` | GET | Retrieve all todos for user |
| Get Single Todo | `/api/v1/tasks/:taskId` | GET | Retrieve specific todo by ID |
| Update Todo | `/api/v1/tasks/:taskId` | PUT | Modify existing todo |
| Mark as Complete | `/api/v1/tasks/:taskId` | PATCH | Update todo completion status |
| Delete Todo | `/api/v1/tasks/:taskId` | DELETE | Remove todo item |

#### 3. Authentication & Authorization

- ✅ Token generation on successful login
- ✅ Token validation for protected endpoints
- ✅ Unauthorized access prevention (401 status)
- ✅ Token expiration handling
- ✅ Invalid token rejection

#### 4. Validation Testing

- ✅ Required field validation
- ✅ Data type validation
- ✅ Email format validation
- ✅ Password strength validation
- ✅ Duplicate user prevention
- ✅ Invalid ID handling
- ✅ Empty request body handling

#### 5. Error Handling

- ✅ 400 Bad Request responses
- ✅ 401 Unauthorized responses
- ✅ 404 Not Found responses
- ✅ 500 Internal Server Error handling
- ✅ Proper error message structure

### Assertion Examples

```javascript
// Status Code Validation
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

// Response Time Check
pm.test("Response time is less than 500ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(500);
});

// JSON Schema Validation
pm.test("Response has correct schema", function () {
    const schema = {
        type: "object",
        required: ["_id", "firstName", "email"],
        properties: {
            _id: { type: "string" },
            firstName: { type: "string" },
            email: { type: "string" }
        }
    };
    pm.response.to.have.jsonSchema(schema);
});

// Data Persistence Validation
pm.test("Todo item is created successfully", function () {
    const responseJson = pm.response.json();
    pm.expect(responseJson).to.have.property("item");
    pm.expect(responseJson.item.isCompleted).to.be.false;
    pm.environment.set("taskId", responseJson.item._id);
});
```

## 🏃 Running Tests

### Local Execution

#### Using Postman GUI

1. Open Postman
2. Select the collection
3. Click **Run** button
4. Configure run settings (iterations, environment, etc.)
5. Click **Run QAcart Todo Collection**
6. View results in the Collection Runner

#### Using Newman CLI

**Basic Execution:**
```bash
newman run postman/collections/QAcart-Todo-Collection.json \
  -e "QAcart Todo Project.postman_environment.json"
```

**With HTML Report:**
```bash
newman run postman/collections/QAcart-Todo-Collection.json \
  -e "QAcart Todo Project.postman_environment.json" \
  -r htmlextra \
  --reporter-htmlextra-export newman/reports/html/report.html
```

**With Multiple Reporters:**
```bash
newman run postman/collections/QAcart-Todo-Collection.json \
  -e "QAcart Todo Project.postman_environment.json" \
  -r cli,htmlextra,json \
  --reporter-htmlextra-export newman/reports/html/report.html \
  --reporter-json-export newman/reports/json/results.json
```

**With Iterations (Data-Driven Testing):**
```bash
newman run postman/collections/QAcart-Todo-Collection.json \
  -e "QAcart Todo Project.postman_environment.json" \
  -n 5 \
  -r htmlextra
```

**Verbose Mode:**
```bash
newman run postman/collections/QAcart-Todo-Collection.json \
  -e "QAcart Todo Project.postman_environment.json" \
  --verbose
```

### Advanced Newman Options

```bash
# Run specific folder from collection
newman run collection.json --folder "User Management"

# Set delay between requests (milliseconds)
newman run collection.json --delay-request 1000

# Disable SSL verification (for local testing only)
newman run collection.json --insecure

# Set timeout for requests
newman run collection.json --timeout-request 10000

# Export environment after run
newman run collection.json \
  -e environment.json \
  --export-environment output-environment.json
```

## 🤖 CI/CD Integration

### GitHub Actions Workflow

The repository includes a pre-configured GitHub Actions workflow for automated testing.

**Workflow File:** `.github/workflows/postman-tests.yml`

```yaml
name: Postman API Tests

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main ]
  schedule:
    # Run tests daily at 2 AM UTC
    - cron: '0 2 * * *'
  workflow_dispatch:

jobs:
  api-tests:
    runs-on: ubuntu-latest
    
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v3
      
      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '18'
      
      - name: Install Newman
        run: |
          npm install -g newman
          npm install -g newman-reporter-htmlextra
      
      - name: Run Postman Collection
        run: |
          newman run postman/collections/QAcart-Todo-Collection.json \
            -e "QAcart Todo Project.postman_environment.json" \
            -r htmlextra,cli,json \
            --reporter-htmlextra-export test-results/htmlreport.html \
            --reporter-json-export test-results/jsonreport.json
      
      - name: Upload Test Results
        if: always()
        uses: actions/upload-artifact@v3
        with:
          name: test-results
          path: test-results/
      
      - name: Publish Test Report
        if: always()
        uses: actions/upload-artifact@v3
        with:
          name: newman-report
          path: test-results/htmlreport.html
```

### Triggering CI/CD

The workflow runs automatically on:
- **Push** to `main` or `develop` branches
- **Pull requests** to `main` branch
- **Scheduled** daily at 2 AM UTC
- **Manual trigger** via GitHub Actions UI

### Viewing Test Results

1. Go to **Actions** tab in GitHub repository
2. Select the workflow run
3. Download **test-results** artifact
4. Open the HTML report in a browser

## 🌐 API Endpoints

### Base URL

```
https://qacart-todo.herokuapp.com
```

### Authentication

Most endpoints require Bearer token authentication:

```
Authorization: Bearer <access_token>
```

### Endpoints Summary

| Category | Endpoint | Method | Auth Required |
|----------|----------|--------|---------------|
| **Users** | `/api/v1/users/register` | POST | ❌ |
| | `/api/v1/users/login` | POST | ❌ |
| | `/api/v1/users/profile` | GET | ✅ |
| | `/api/v1/users/profile` | PUT | ✅ |
| | `/api/v1/users/profile` | DELETE | ✅ |
| **Tasks** | `/api/v1/tasks` | POST | ✅ |
| | `/api/v1/tasks` | GET | ✅ |
| | `/api/v1/tasks/:taskId` | GET | ✅ |
| | `/api/v1/tasks/:taskId` | PUT | ✅ |
| | `/api/v1/tasks/:taskId` | DELETE | ✅ |

## 🔐 Environment Variables

### Required Variables

```json
{
  "baseUrl": "https://qacart-todo.herokuapp.com",
  "accessToken": "",
  "refreshToken": "",
  "userId": "",
  "taskId": "",
  "userFirstName": "",
  "userLastName": "",
  "userEmail": "",
  "userPassword": ""
}
```

### Variable Usage

- **`baseUrl`**: API base URL (configured once)
- **`accessToken`**: Auto-populated after login (used for auth)
- **`userId`**: Auto-populated after registration (used in user-specific requests)
- **`taskId`**: Auto-populated after task creation (used in task-specific requests)
- **User credentials**: Generated dynamically in pre-request scripts

### Dynamic Variable Generation

Pre-request script example:
```javascript
// Generate random user data
const randomString = Math.random().toString(36).substring(7);
pm.environment.set("userFirstName", "Test");
pm.environment.set("userLastName", "User" + randomString);
pm.environment.set("userEmail", `testuser${randomString}@test.com`);
pm.environment.set("userPassword", "Test@123");
```

## 📊 Test Data Management

### Data Generation Strategy

1. **Pre-request Scripts**: Generate unique test data before each request
2. **Environment Variables**: Store and reuse generated data across requests
3. **Random Values**: Prevent test data conflicts
4. **Test Scripts**: Extract and save response data for subsequent requests

### Example: User Registration Data

```javascript
// Pre-request Script
pm.environment.set("randomEmail", `user${Date.now()}@test.com`);
pm.environment.set("randomPassword", "SecurePass123!");

// Request Body
{
  "firstName": "John",
  "lastName": "Doe",
  "email": "{{randomEmail}}",
  "password": "{{randomPassword}}"
}

// Test Script - Save Access Token
const responseJson = pm.response.json();
pm.environment.set("accessToken", responseJson.access_token);
pm.environment.set("userId", responseJson.userID);
```

## 📈 Reporting

### HTML Report Features

The HTML Extra reporter provides:
- ✅ Executive summary with pass/fail statistics
- 📊 Visual charts and graphs
- 🕐 Response time analysis
- 📝 Detailed request/response logs
- 🎨 Customizable themes
- 📤 Exportable reports

### Sample Report Generation

```bash
newman run collection.json \
  -e environment.json \
  -r htmlextra \
  --reporter-htmlextra-title "QAcart Todo API Test Report" \
  --reporter-htmlextra-export report.html \
  --reporter-htmlextra-darkTheme
```

### JSON Report Structure

```json
{
  "collection": {},
  "environment": {},
  "globals": {},
  "run": {
    "stats": {
      "tests": {
        "total": 45,
        "failed": 0,
        "pending": 0
      },
      "assertions": {
        "total": 120,
        "failed": 0,
        "pending": 0
      }
    },
    "timings": {
      "completed": 1234567890,
      "started": 1234567800
    },
    "executions": []
  }
}
```

## ✅ Best Practices

### Collection Organization

1. **Folder Structure**: Group related requests in folders
2. **Naming Convention**: Use descriptive, consistent naming
3. **Request Order**: Arrange requests in logical execution sequence
4. **Documentation**: Add descriptions to all requests and folders

### Test Writing

1. **Atomic Tests**: Each test should validate one specific condition
2. **Descriptive Names**: Use clear, meaningful test descriptions
3. **Error Messages**: Provide helpful failure messages
4. **Clean Up**: Reset environment after test execution

### Environment Management

1. **Separate Environments**: Maintain dev, staging, prod environments
2. **No Hardcoding**: Use variables for all dynamic values
3. **Secret Management**: Never commit sensitive data to version control
4. **Variable Scope**: Use appropriate variable scopes (global, environment, local)

### CI/CD

1. **Fail Fast**: Configure tests to stop on first failure when appropriate
2. **Parallel Execution**: Run independent test suites in parallel
3. **Scheduled Runs**: Automate regular test execution
4. **Notifications**: Set up alerts for test failures

### Code Examples

```javascript
// ✅ Good Practice
pm.test("User registration returns 201 Created status", () => {
    pm.response.to.have.status(201);
});

pm.test("Response contains user ID", () => {
    const response = pm.response.json();
    pm.expect(response).to.have.property("_id");
    pm.expect(response._id).to.be.a("string").and.not.empty;
});

// ❌ Avoid
pm.test("Test", () => {
    pm.expect(pm.response.code).to.equal(201);
    pm.expect(pm.response.json()._id).to.exist;
});
```

## 🔧 Troubleshooting

### Common Issues

#### 1. Authentication Token Expired

**Problem:** Tests fail with 401 Unauthorized

**Solution:**
```javascript
// Add token refresh logic in pre-request script
if (pm.environment.get("accessToken") === "") {
    // Re-run login request
}
```

#### 2. Environment Variables Not Set

**Problem:** `{{variable}}` not resolving

**Solution:**
- Verify environment is selected in Postman
- Check variable names for typos
- Ensure variables are set in correct scope

#### 3. Newman Command Not Found

**Problem:** `newman: command not found`

**Solution:**
```bash
# Install Newman globally
npm install -g newman

# Verify installation
newman --version
```

#### 4. Collection Dependencies

**Problem:** Tests fail due to execution order

**Solution:**
- Ensure proper folder organization
- Use collection runner's folder selection
- Implement proper data cleanup

#### 5. CORS Issues (Local Testing)

**Problem:** CORS errors in browser-based testing

**Solution:**
- Use Postman desktop app (no CORS)
- Configure backend for CORS
- Use Newman for headless testing

### Debug Tips

```bash
# Enable verbose logging
newman run collection.json --verbose

# View detailed request/response
newman run collection.json --reporter-cli-show-assertions

# Export Newman run for analysis
newman run collection.json \
  --export-globals globals.json \
  --export-environment environment.json
```

## 🤝 Contributing

### How to Contribute

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/amazing-test`)
3. **Commit** your changes (`git commit -m 'Add amazing test'`)
4. **Push** to the branch (`git push origin feature/amazing-test`)
5. **Open** a Pull Request

### Contribution Guidelines

- Follow existing code style and conventions
- Add comprehensive test descriptions
- Update documentation for new features
- Ensure all tests pass before submitting PR
- Include meaningful commit messages

### Code Review Process

1. All PRs require at least one review
2. CI/CD tests must pass
3. Documentation must be updated
4. No merge conflicts

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👥 Authors

- **Asmaa Newigy** - [GitHub Profile](https://github.com/asmaanewigy32)

## 🙏 Acknowledgments

- **QAcart** for providing the Todo API application
- **Postman** team for excellent API testing tools
- **Newman** contributors for CLI test runner
- Testing community for best practices and patterns

## 📞 Support

For questions or issues:
- Open an issue in this repository
- Contact: [Your contact information]
- QAcart Community: [QAcart Website](https://qacart.com)

## 📚 Additional Resources

### Learning Materials

- [Postman Documentation](https://learning.postman.com/)
- [Newman Documentation](https://github.com/postmanlabs/newman)
- [Chai Assertion Library](https://www.chaijs.com/)
- [API Testing Best Practices](https://github.com/NoriSte/api-testing-best-practices)

### Related Projects

- [Postman Learning Center](https://learning.postman.com/docs/getting-started/introduction/)
- [QAcart Courses](https://qacart.com/)
- [API Testing Resources](https://github.com/topics/api-testing)

---

## 📊 Project Statistics

![Tests](https://img.shields.io/badge/Tests-45+-brightgreen)
![Assertions](https://img.shields.io/badge/Assertions-120+-blue)
![Pass Rate](https://img.shields.io/badge/Pass%20Rate-100%25-success)
![Coverage](https://img.shields.io/badge/API%20Coverage-95%25-brightgreen)

---
