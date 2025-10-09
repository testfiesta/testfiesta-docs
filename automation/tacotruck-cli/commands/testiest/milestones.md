# Milestones

### 1. Create Milestone

**Command Syntax**

```
tacotruck testfiesta milestone:create [options]
```

**Required Options**

* -p, --project \<project>: Project key
* -n, --name \<name>: Milestone name
* -t, --token \<token>: TestFiesta API token
* -u, --url \<url>: TestFiesta API URL
* -o, --organization \<organization>: Organization handle

**Optional Options**

* -d, --description \<description>: Milestone description
* \--due-date \<date>: Due date in YYYY-MM-DD format
* -v, --verbose: Enable detailed logging

**Example**

```sh
tacotruck testfiesta milestone:create \
  -p PROJECT_KEY \
  -n "Release 1.0" \
  -t your_api_token \
  -u https://api.testfiesta.com \
  -o your_organization \
  -d "First major release" \
  --due-date 2023-12-31
```

### 2. List Milestones

**Command Syntax**

```sh
tacotruck testfiesta milestone:list [options]
```

**Required Options**

* -p, --project \<project>: Project key
* -t, --token \<token>: TestFiesta API token
* -l, --limit \<limit>: Number of items to retrieve (default: 10)
* \--offset \<offset>: Offset for pagination (default: 0)
* -v, --verbose: Enable detailed logging

**Optional Options**

* -p, --project \<project>: Project key
* -t, --token \<token>: TestFiesta API token
* -u, --url \<url>: TestFiesta API URL
* -o, --organization \<organization>: Organization handle

**Example**

```sh
tacotruck testfiesta milestone:list \
  -p PROJECT_KEY \
  -t your_api_token \
  -u https://api.testfiesta.com \
  -o your_organization
```

### 3. Get Milestone

**Command Syntax**

```sh
tacotruck testfiesta milestone:get [options]
```

**Required Options**

* -p, --project \<project>: Project key
* -i, --id \<id>: Milestone ID
* -t, --token \<token>: TestFiesta API token
* -u, --url \<url>: TestFiesta API URL
* -o, --organization \<organization>: Organization handle

**Optional Options**

* -v, --verbose: Enable detailed logging

**Example**

```sh
tacotruck testfiesta milestone:get \
  -p PROJECT_KEY \
  -i MILESTONE_ID \
  -t your_api_token \
  -u https://api.testfiesta.com \
  -o your_organization
```

### 4. Update Milestone

**Command Syntax**

```shell
tacotruck testfiesta milestone:update [options]
```

**Required Options**

* -p, --project \<project>: Project key
* -i, --id \<id>: Milestone ID
* -t, --token \<token>: TestFiesta API token
* -u, --url \<url>: TestFiesta API URL
* -o, --organization \<organization>: Organization handle

**Optional Options**

* -n, --name \<name>: New milestone name
* -d, --description \<description>: New milestone description
* \--due-date \<date>: New due date in YYYY-MM-DD format
* \--status \<status>: New status (active, completed)
* -v, --verbose: Enable detailed logging

**Example**

```sh
tacotruck testfiesta milestone:update \
  -p PROJECT_KEY \
  -i MILESTONE_ID \
  -t your_api_token \
  -u https://api.testfiesta.com \
  -o your_organization \
  -n "Release 1.1" \
  -d "Updated release scope" \
  --due-date 2024-01-15
```

### 5. Delete Milestone

**Command Syntax**

```sh
tacotruck testfiesta milestone:delete [options]
```

**Required Options**

* -p, --project \<project>: Project key
* -i, --id \<id>: Milestone ID
* -t, --token \<token>: TestFiesta API token
* -u, --url \<url>: TestFiesta API URL
* -o, --organization \<organization>: Organization handle

**Optional Options**

* -v, --verbose: Enable detailed logging
* \--non-interactive: Skip confirmation prompts

**Example**

```sh
tacotruck testfiesta milestone:delete \
  -p PROJECT_KEY \
  -i MILESTONE_ID \
  -t your_api_token \
  -u https://api.testfiesta.com \
  -o your_organization
```
