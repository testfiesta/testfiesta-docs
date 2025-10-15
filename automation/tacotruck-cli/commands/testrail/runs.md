# Runs

### `testrail run:submit`

Submit test results to TestRail

#### Synopsis

```
tacotruck testrail run:submit -d <path> -t <token> -u <url> -p <projectId> -n <name> [options]
```

#### Description

This command submits test results from a JUnit XML or JSON file to TestRail. It authenticates with TestRail using the provided API token, creates a new test run with the specified name, and uploads all test results to the specified project.

The command shows progress during the upload process and confirms successful submission when complete.

#### Arguments and options

* `-d, --data <path>`: Path to test run data JSON/XML file
* `-t, --token <token>`: TestRail API token in username:password format
* `-u, --url <url>`: TestRail instance URL (e.g., https://example.testrail.io)
* `-p, --project <projectId>`: TestRail project ID
* `-n, --name <name>`: Name for the test run
* `-D, --x <text>`: Description for the test run
* `-s, --suite-id <id>`: TestRail suite ID (required for projects with multiple test suites)
* `-a, --include-all`: Include all test cases in the run
* `-c, --case-ids <ids>`: Comma-separated list of case IDs to include (only if --include-all is not set)
* `-v, --verbose`: Enable verbose logging

