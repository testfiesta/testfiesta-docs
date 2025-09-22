# GitLab CI

### TacoTruck GitLab CI Integration <a href="#tacotruck-gitlab-ci-integration" id="tacotruck-gitlab-ci-integration"></a>

A GitLab CI integration for uploading test results to TestFiesta and TestRail.

#### Usage <a href="#user-content-usage" id="user-content-usage"></a>

**Use as a CI/CD Component**

The component approach provides the most flexibility and is the recommended way to use TacoTruck.**Testfiesta**

#### Testfiesta <a href="#testfiesta" id="testfiesta"></a>

include:- component: gitlab.com/testfiesta/tacotruck-gitlab/tacotruck@v\<latest version>inputs:stage: reportprovider: "testfiesta" # Options: "testfiesta", "testrail", "all"results\_path: "./test-results.xml"base\_url: "https://api.testfiesta.com"project: "your-project-key"handle: "your-org-handle"api\_key: "$TESTFIESTA\_API\_KEY"run\_name: "CI Pipeline Run ${CI\_PIPELINE\_ID}"​stages:- test- report​run-tests:stage: testscript:- npm testartifacts:paths:- test-results.xmlreports:junit: test-results.xml​# The component automatically provides the submit-run job# No need to extend or define additional jobs**Setup**

1. **Get your API token:**
   * Go to Testfiesta dashboard → Settings → API Tokens
   * Generate a new token
2. **Add to Gitlab CI/CD variables:**&#x54;ESTFIESTA\_API\_KEY = "your-api-key"

#### Testrail <a href="#testrail" id="testrail"></a>

include:- component: gitlab.com/testfiesta/tacotruck-gitlab/tacotruck@v\<latest version>inputs:stage: reportprovider: "testrail" # Options: "testfiesta", "testrail", "all"results\_path: "./test-results.xml"base\_url: "https://\<your-username>.testrail.io"project: "your-project-id"email: "$USERNAME"password: "$PASSWORD"run\_name: "CI Pipeline Run ${CI\_PIPELINE\_ID}"​stages:- test- report​run-tests:stage: testscript:- npm testartifacts:paths:- test-results.xmlreports:junit: test-results.xml​# The component automatically provides the submit-run job# No need to extend or define additional jobs**Setup**

1. **Add to Gitlab CI/CD variables:**&#x55;SERNAME = "your-username"PASSWORD = "your-password"

**Available Job**When using the template, you have access to this job:

* `submit-run`: Main job for conditional reporting (supports TestFiesta, TestRail, or both)

#### Configuration <a href="#user-content-configuration" id="user-content-configuration"></a>

**Component Inputs**

When using the component , configure these inputs:

|                |                                                   |                     |                  |
| -------------- | ------------------------------------------------- | ------------------- | ---------------- |
| `stage`        | Pipeline stage for the job                        | `"report"`          | No               |
| `provider`     | Provider type: "testfiesta", "testrail", or "all" | `"all"`             | No               |
| `results_path` | Path to test results XML file                     | `"${RESULTS_PATH}"` | Yes              |
| `base_url`     | Base URL for the provider                         | `"${BASE_URL}"`     | Yes              |
| `project`      | Project key (TestFiesta) or ID (TestRail)         | `"${PROJECT}"`      | Yes              |
| `run_name`     | Name for the test run                             | `"${RUN_NAME}"`     | No               |
| `handle`       | Organization handle (TestFiesta only)             | `"${HANDLE}"`       | Yes (TestFiesta) |
| `api_key`      | API key (TestFiesta only)                         | `"${API_KEY}"`      | Yes (TestFiesta) |
| `username`     | Username (TestRail only)                          | `"${USERNAME}"`     | Yes (TestRail)   |
| `password`     | Password (TestRail only)                          | `"${PASSWORD}"`     | Yes (TestRail)   |
