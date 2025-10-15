# GitLab CI

## TacoTruck GitLab CI Integration

A GitLab CI integration for uploading test results to TestFiesta and TestRail.&#x20;

### Usage <a href="#user-content-usage" id="user-content-usage"></a>

#### Use as a CI/CD Component <a href="#user-content-option-1-use-as-a-cicd-component-recommended" id="user-content-option-1-use-as-a-cicd-component-recommended"></a>

The component approach provides the most flexibility and is the recommended way to use TacoTruck.

**Testfiesta**&#x20;

### Testfiesta

```yaml
include:
  - component: gitlab.com/testfiesta/tacotruck-gitlab/tacotruck@v<latest version>
    inputs:
      stage: report
      provider: "testfiesta" # Options: "testfiesta", "testrail", "all"
      results_path: "./test-results.xml"
      base_url: "https://api.testfiesta.com"
      project: "your-project-key"
      handle: "your-org-handle"
      api_key: "$TESTFIESTA_API_KEY"
      run_name: "CI Pipeline Run ${CI_PIPELINE_ID}"

stages:
  - test
  - report

run-tests:
  stage: test
  script:
    - npm test
   artifacts:
    paths:
      - test-results.xml
    reports:
      junit: test-results.xml

# The component automatically provides the submit-run job
# No need to extend or define additional job
```

**Setup**

1. **Get your API token:**
   * Go to Testfiesta dashboard → Settings → API Tokens
   * Generate a new token
2.  **Add to Gitlab CI/CD variables:**

    ```
    TESTFIESTA_API_KEY = "your-api-key" 
    ```

### Testrail

```yaml
include:
  - component: gitlab.com/testfiesta/tacotruck-gitlab/tacotruck@v<latest version>
    inputs:
      stage: report
      provider: "testrail" # Options: "testfiesta", "testrail", "all"
      results_path: "./test-results.xml"
      base_url: "https://<your-username>.testrail.io"
      project: "your-project-id"
      email: "$USERNAME"
      password: "$PASSWORD"
      run_name: "CI Pipeline Run ${CI_PIPELINE_ID}"

stages:
  - test
  - report

run-tests:
  stage: test
  script:
    - npm test
   artifacts:
    paths:
      - test-results.xml
    reports:
      junit: test-results.xml

# The component automatically provides the submit-run job
# No need to extend or define additional jobs
```

**Setup**

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

### Support and Resources

* [TacoTruck Examples](https://github.com/testfiesta/tacotruck-examples)
* [TacoTruck Gitlab CI/CD Component](https://gitlab.com/explore/catalog/testfiesta/tacotruck-cicd)
* [Tacotruck Issues](https://github.com/testfiesta/tacotruck/issues)
* [**CLI Reference**](../tacotruck-cli/)
* [Tacotruck Github Action](https://github.com/testfiesta/tacotruck-action)
