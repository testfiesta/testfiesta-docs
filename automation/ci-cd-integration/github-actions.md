# GitHub Actions

Submit test results from any language/framework to test management services like Testfiesta, TestRail, and more.

**TestRail**

TestRail uses Basic Authentication with username and password.**Setup**

1. **Create TestRail API credentials:**
   * Go to your TestRail instance → Administration → Site Settings → API
   * Enable the API
   * Note your username and password (or create an API-specific user)
2. **Add to GitHub Secrets:**&#x54;ESTRAIL\_CREDENTIALS = "your-username:your-password"**Important:** Use the format `username:password` - the action will handle the Base64 encoding.

**Usage**- name: Submit to TestRailuses: testfiesta/tacotruck-action@v1with:provider: testrailhandle: \<your-username>project: \<your-project-id>results-path: ./junit-results.xmlcredentials: $\{{ secrets.TESTRAIL\_CREDENTIALS \}}base-url: 'https://\<your-username>.testrail.io'run-name: 'CI Run #$\{{ github.run\_number \}}'config: |{"suite\_id": 2,"run\_name": "Automated Tests - $\{{ github.workflow \}} #$\{{ github.run\_number \}}","milestone\_id": 5,"assigned\_to": 123}**TestRail Configuration Options**

|                |   |                                                            |
| -------------- | - | ---------------------------------------------------------- |
| `suite_id`     | ❌ | Test suite ID (if using suites)                            |
| `run_name`     | ❌ | Name for the test run (defaults to "CI Run {run\_number}") |
| `milestone_id` | ❌ | Milestone to associate the run with                        |
| `assigned_to`  | ❌ | User ID to assign the test run to                          |

**Testfiesta**

Testfiesta uses Bearer token authentication.**Setup**

1. **Get your API token:**
   * Go to Testfiesta dashboard → Settings → API Tokens
   * Generate a new token
2. **Add to GitHub Secrets:**&#x54;ESTFIESTA\_API\_KEY = "your-api-key"

**Usage**- name: Submit to Testfiestauses: testfiesta/tacotruck-action@v1with:provider: testfiestahandle: \<your-org-handle>project: \<your-project-key>results-path: ./test-resultscredentials: $\{{ secrets.TESTFIESTA\_API\_KEY \}}base-url: 'https://api.testfiesta.com'run-name: 'CI Run #$\{{ github.run\_number \}}'config: |{"environment": "staging","tags": \["ci", "regression", "api-tests"],"branch": "$\{{ github.ref\_name \}}"}**Testfiesta Configuration Options**

|               |   |                                          |
| ------------- | - | ---------------------------------------- |
| `environment` | ❌ | Test environment (defaults to "default") |
| `tags`        | ❌ | Array of tags or comma-separated string  |
| `branch`      | ❌ | Git branch (defaults to current branch)  |

#### Input Reference <a href="#input-reference" id="input-reference"></a>

|                 |   |                                                                                |
| --------------- | - | ------------------------------------------------------------------------------ |
| `provider`      | ✅ | Provider name (`testrail`, `testfiesta`)                                       |
| `handle`        | ✅ | Handle of the provider (e.g. username for testrail, org handle for testfiesta) |
| `project`       | ✅ | Project id or key of the provider                                              |
| `results-path`  | ✅ | Path to test results file or directory                                         |
| `credentials`   | ✅ | Authentication credentials (format varies by provider)                         |
| `base-url`      | ✅ | Base URL for the provider's API                                                |
| `run-name`      | ❌ | Name of the test run                                                           |
| `config`        | ❌ | Provider-specific configuration (JSON format)                                  |
| `config-file`   | ❌ | Path to configuration file                                                     |
| `fail-on-error` | ❌ | Fail workflow if submission fails (default: `true`)                            |
