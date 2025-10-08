# Projects

### 1. Create Project

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

### 2. Delete Project

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
