# Get start

## Getting Started with Tacotruck

Tacotruck is a powerful tool for moving quality data between different testing platforms. Whether you need to submit test results to TestRail, TestFiesta, or migrate data between test case management tools, tacotruck provides a simple interface to accomplish these tasks.

### Installation

#### Global Installation

```javascript
npm install -g @testfiesta/tacotruck
```

#### Using without Installation

```javascript
npx @testfiesta/tacotruck
```

### Basic Commands

Tacotruck supports multiple testing platforms. Here are the main commands:

#### TestFiesta Integration

Submit test results to TestFiesta:

```javascript
tacotruck testfiesta run:submit \
  --data ./results.xml \
  --token "your_api_token" \
  --organization "your_org_handle" \
  --project "your_project_key" \
  --name "Test Run Name" \
  --url "https://api.testfiesta.com"
```

Required parameters:

* \--data: Path to your test results file (XML/JSON)
* \--token: TestFiesta API token
* \--organization: Your organization handle
* \--project: Project key
* \--name: Name for the test run
* \--url: TestFiesta API URL

Optional parameters:

* \--verbose: Enable detailed logging

#### TestRail Integration

Submit test results to TestRail:

```javascript
tacotruck testrail run:submit \
  --data ./results.xml \
  --token "username:password" \
  --url "https://example.testrail.io" \
  --project "project_id" \
  --name "Test Run Name"
```

Required parameters:

* \--data: Path to your test results file (XML/JSON)
* \--token: TestRail API token (in username:password format)
* \--url: Your TestRail instance URL
* \--project: TestRail project ID
* \--name: Name for the test run

Optional parameters:

* \--x: Description for the test run
* \--suite-id: TestRail suite ID (required for projects with multiple test suites)
* \--include-all: Include all test cases in the run
* \--case-ids: Comma-separated list of case IDs to include
* \--verbose: Enable detailed logging

### Supported File Formats

Tacotruck supports various test result formats:

* JUnit XML

\
\
