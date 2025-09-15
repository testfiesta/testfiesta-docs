# CircleCI

## TacoTruck orb for CircleCI

acoTruck submits test results to various testing platforms and services from within your CircleCI CI/CD pipeline. TacoTruck streamlines test reporting with a unified interface for multiple test result destinations.

### Quick Start

Add the TacoTruck orb to your CircleCI configuration:

```
version: 2.1
orbs:
  tacotruck: testfiesta/tacotruck@<version>

jobs:
  test-and-report:
    executor: tacotruck/default
    steps:
      - checkout
      - tacotruck/install:
          version: "latest"
      - run: npm test
      - tacotruck/submit:
          provider: "testfiesta"
          results_path: "./test-results/junit.xml"
          project_key: "my-project"
          api_key: "TESTFIESTA_API_KEY"
          handle: "my-org"
          run_name: "CI Test Run"

workflows:
  test:
    jobs:
      - test-and-report
```

### Commands

#### **install**

Installs the TacoTruck CLI globally and verifies the installation.

**Parameters:**

* `version` (string, default: "latest") - Version of @testfiesta/tacotruck to install
* `check_version` (boolean, default: true) - Whether to verify installation by printing version

**Examples:**

```
# Install latest version
- tacotruck/install:
    version: "latest"

# Install specific version
- tacotruck/install:
    version: "1.0.0-beta.13"
    check_version: true
```

#### **submit**

Submits test results to supported testing platforms (TestFiesta, TestRail).

**Parameters:**

* `provider` (enum: "testfiesta" | "testrail") - Testing platform provider
* `results_path` (string, default: "./test-results") - Path to test results file or directory
* `project_key` (string, default: "") - Project key for submission (optional)
* `api_key` (env\_var\_name) - Environment variable name containing the API key
* `handle` (string) - Organization handle (TestFiesta) or username (TestRail)
* `run_name` (string, default: "TacoTruck Test Run") - Name for the test run
* `base_url` (string) - API base URL (optional)

**Examples:**

```
# Submit to TestFiesta
- tacotruck/submit:
    provider: "testfiesta"
    results_path: "./test-results/junit.xml"
    project_key: "my-project"
    api_key: "TESTFIESTA_API_KEY"
    handle: "my-org"
    run_name: "CI Test Run"

# Submit to TestRail
- tacotruck/submit:
    provider: "testrail"
    results_path: "./test-results"
    api_key: "TESTRAIL_API_KEY"
    handle: "username"
    run_name: "Automated Test Run"
```

\
\
