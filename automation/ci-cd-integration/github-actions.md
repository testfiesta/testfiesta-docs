# GitHub Actions

Submit test results from any language/framework to test management services like Testfiesta, TestRail, and more.

#### **TestRail**

TestRail uses Basic Authentication with username and password.

**Setup**

1. **Create TestRail API credentials:**
   * Go to your TestRail instance → Administration → Site Settings → API
   * Enable the API
   * Note your username and password (or create an API-specific user)
2.  **Add to GitHub Secrets:**

    ```markup
    TESTRAIL_CREDENTIALS = "your-username:your-password"
    ```

    **Important:** Use the format `username:password` - the action will handle the Base64 encoding.

**Usage**

```
- name: Submit to TestRail
  uses: testfiesta/tacotruck-action@v1
  with:
    provider: testrail
    handle: <your-username>
    project: <your-project-id>
    results-path: ./junit-results.xml
    credentials: ${{ secrets.TESTRAIL_CREDENTIALS }}
    base-url: 'https://<your-username>.testrail.io'
    run-name: 'CI Run #${{ github.run_number }}'
    config: |
      {
        "suite_id": 2,
        "run_name": "Automated Tests - ${{ github.workflow }} #${{ github.run_number }}",
        "milestone_id": 5,
        "assigned_to": 123
      }
```

**TestRail Configuration Options**

| Option         | Required | Description                                                |
| -------------- | -------- | ---------------------------------------------------------- |
| `suite_id`     | ❌        | Test suite ID (if using suites)                            |
| `run_name`     | ❌        | Name for the test run (defaults to "CI Run {run\_number}") |
| `milestone_id` | ❌        | Milestone to associate the run with                        |
| `assigned_to`  | ❌        | User ID to assign the test run to                          |

#### **Testfiesta**

Testfiesta uses Bearer token authentication.

**Setup**

1. **Get your API token:**
   * Go to Testfiesta dashboard → Settings → API Tokens
   * Generate a new token
2.  **Add to GitHub Secrets:**

    ```
    TESTFIESTA_API_KEY = "your-api-key"
    ```

**Usage**

```
- name: Submit to Testfiesta
  uses: testfiesta/tacotruck-action@v1
  with:
    provider: testfiesta
    handle: <your-org-handle>
    project: <your-project-key>
    results-path: ./test-results
    credentials: ${{ secrets.TESTFIESTA_API_KEY }}
    base-url: 'https://api.testfiesta.com'
    run-name: 'CI Run #${{ github.run_number }}'
    config: |
      {
        "environment": "staging",
        "tags": ["ci", "regression", "api-tests"],
        "branch": "${{ github.ref_name }}"
      }
```

**Testfiesta Configuration Options**

| Option        | Required | Description                              |
| ------------- | -------- | ---------------------------------------- |
| `environment` | ❌        | Test environment (defaults to "default") |
| `tags`        | ❌        | Array of tags or comma-separated string  |
| `branch`      | ❌        | Git branch (defaults to current branch)  |

### Input Reference

| Input           | Required | Description                                                                    |
| --------------- | -------- | ------------------------------------------------------------------------------ |
| `provider`      | ✅        | Provider name (`testrail`, `testfiesta`)                                       |
| `handle`        | ✅        | Handle of the provider (e.g. username for testrail, org handle for testfiesta) |
| `project`       | ✅        | Project id or key of the provider                                              |
| `results-path`  | ✅        | Path to test results file or directory                                         |
| `credentials`   | ✅        | Authentication credentials (format varies by provider)                         |
| `base-url`      | ✅        | Base URL for the provider's API                                                |
| `run-name`      | ❌        | Name of the test run                                                           |
| `config`        | ❌        | Provider-specific configuration (JSON format)                                  |
| `config-file`   | ❌        | Path to configuration file                                                     |
| `fail-on-error` | ❌        | Fail workflow if submission fails (default: `true`)                            |
