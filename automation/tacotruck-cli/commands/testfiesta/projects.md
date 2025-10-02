# Projects

### 1. Create Project

**Command Syntax**

```
tacotruck testfiesta project:create [options]
```

**Required Options**

* -n, --name \<name>: Project name
* -t, --token \<token>: TestFiesta API token
* -u, --url \<url>: TestFiesta API URL
* -h, --organization \<organization>: Organization handle

**Optional Options**

* -v, --verbose: Enable detailed logging

**Example**

```
tacotruck testfiesta project:create \
  -n "My New Project" \
  -t your_api_token \
  -u https://api.testfiesta.com \
  -h your_organization
```

**Output Example**

```
// Some code
```

### 2. List Project

**Command Syntax**

```
tacotruck testfiesta project:list [options]
```

**Required Options**

* -t, --token \<token>: TestFiesta API token
* -u, --url \<url>: TestFiesta API URL
* -o, --organization \<organization>: Organization handle

**Optional Options**

* -l, --limit \<limit>: Number of items to retrieve (default: 10)
* \--offset \<offset>: Offset for pagination (default: 0)
* -v, --verbose: Enable detailed logging

**Example**

```javascript
tacotruck testfiesta project:list \
  -t your_api_token \
  -u https://api.testfiesta.com \
  -o your_organization \
  -l 20 \
  --offset 0
```

**Output Example**

```
// Some code
```

### 3. Delete Project

**Command Syntax**

```
tacotruck testfiesta project:delete [options]
```

**Required Options**

* -p, --project \<project>: Project key
* -t, --token \<token>: TestFiesta API token
* -u, --url \<url>: TestFiesta API URL
* -h, --organization \<organization>: Organization handle

**Optional Options**

* -v, --verbose: Enable detailed logging
* \--non-interactive: Skip confirmation prompts

**Example**

```
tacotruck testfiesta project:delete \
  -p PROJECT_KEY \
  -t your_api_token \
  -u https://api.testfiesta.com \
  -h your_organization
```

**Output Example**

```
// Some code
```
