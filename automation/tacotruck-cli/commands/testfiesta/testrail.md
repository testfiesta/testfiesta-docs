# TestRail

## TestRail Command Reference

### 1. Test Run Management

#### `testrail run:submit` - Submit Test Results

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

### 2. Project Management

#### `testrail project:create` - Create Project

**Command Syntax**

```
tacotruck testrail project:create [options]
```

**Required Options**

* -n, --name \<name>: Project name
* -t, --token \<token>: TestRail API token in username:password format
* -u, --url \<url>: TestRail instance URL (e.g., https://example.testrail.io)

**Optional Options**

* -s, --suite-mode \<suiteMode>: TestRail project structure:
* 1: Single repository for all cases (default)
* 2: Single repository with baselines
* 3: Multiple test suites
* -v, --verbose: Enable detailed logging

**Example**

**Required Options**

* -n, --name \<name>: Project name
* -t, --token \<token>: TestRail API token in username:password format
* -u, --url \<url>: TestRail instance URL (e.g., https://example.testrail.io)

**Optional Options**

* -s, --suite-mode \<suiteMode>: TestRail project structure:
* 1: Single repository for all cases (default)
* 2: Single repository with baselines
* 3: Multiple test suites
* -v, --verbose: Enable detailed logging

**Example**

```
tacotruck testrail project:create \
  -n "API Testing Project" \
  -t "username:password" \
  -u https://example.testrail.io \
  -s 1
```

#### `testrail project:delete` - Delete Project

**Command Syntax**

```
tacotruck testrail project:delete [options]
```

**Required Options**

* -i, --project-id \<id>: TestRail project ID to delete
* -t, --token \<token>: TestRail API token in username:password format
* -u, --url \<url>: TestRail instance URL (e.g., https://example.testrail.io)

**Optional Options**

* -f, --force: Skip confirmation prompt
* -v, --verbose: Enable detailed logging

**Example**

```
tacotruck testrail project:delete \
  -i 15 \
  -t "username:password" \
  -u https://example.testrail.io
```

