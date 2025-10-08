# Runs

### 1. Submit  Run

**Command Syntax**

```
tacotruck testrail run:submit [options]
```

**Required Options**

* -d, --data \<path>: Path to test run data JSON/XML file
* -t, --token \<token>: TestRail API token in username:password format
* -u, --url \<url>: TestRail instance URL (e.g., https://example.testrail.io)
* -p, --project \<projectId>: TestRail project ID
* -n, --name \<name>: Name for the test run

**Optional Options**

* -D, --x \<text>: Description for the test run
* -s, --suite-id \<id>: TestRail suite ID (required for projects with multiple test suites)
* -a, --include-all: Include all test cases in the run
* -c, --case-ids \<ids>: Comma-separated list of case IDs to include (only if --include-all is not set)
* -v, --verbose: Enable detailed logging

**Example**

```
tacotruck testrail run:submit \
  -d ./results.xml \
  -t "username:password" \
  -u https://example.testrail.io \
  -p 15 \
  -n "Automated Test Run" \
  -D "Run from CI pipeline" \
  -s 25 \
  -a
```

