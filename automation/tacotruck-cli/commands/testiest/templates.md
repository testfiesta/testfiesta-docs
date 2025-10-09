# Templates

### 1. Create Template

**Command Syntax**

```sh
tacotruck testfiesta template:create [options]
```

**Required Options**

* -p, --project \<project>: Project key
* -n, --name \<name>: Template name
* -t, --token \<token>: TestFiesta API token
* -u, --url \<url>: TestFiesta API URL
* -o, --organization \<organization>: Organization handle
* \--content \<content>: Template content or path to template file

**Optional Options**

* -d, --description \<description>: Template description
* \--type \<type>: Template type (test-case, test-run)
* -v, --verbose: Enable detailed logging

**Example**

```sh
tacotruck testfiesta template:create \
  -p PROJECT_KEY \
  -n "API Test Case Template" \
  -t your_api_token \
  -u https://api.testfiesta.com \
  -o your_organization \
  -d "Standard template for API test cases" \
  --type test-case \
  --content ./templates/api-test.json
```

### 2. List Templates

**Command Syntax**

```sh
tacotruck testfiesta template:list [options]
```

**Required Options**

* -p, --project \<project>: Project key
* -t, --token \<token>: TestFiesta API token
* -u, --url \<url>: TestFiesta API URL
* -o, --organization \<organization>: Organization handle

**Optional Options**

* \--type \<type>: Filter by template type (test-case, test-run)
* -l, --limit \<limit>: Number of items to retrieve (default: 10)
* \--offset \<offset>: Offset for pagination (default: 0)
* -v, --verbose: Enable detailed logging

**Example**

```sh
tacotruck testfiesta template:list \
  -p PROJECT_KEY \
  -t your_api_token \
  -u https://api.testfiesta.com \
  -o your_organization \
  --type test-case
```

### 3. Get Template

**Command Syntax**

```sh
tacotruck testfiesta template:get [options]
```

**Required Options**

* -p, --project \<project>: Project key
* -i, --id \<id>: Template ID
* -t, --token \<token>: TestFiesta API token
* -u, --url \<url>: TestFiesta API URL
* -o, --organization \<organization>: Organization handle

**Optional Options**

* -v, --verbose: Enable detailed logging

**Example**

```sh
Required Options
-p, --project <project>: Project key
-i, --id <id>: Template ID
-t, --token <token>: TestFiesta API token
-u, --url <url>: TestFiesta API URL
-o, --organization <organization>: Organization handle
Optional Options
-v, --verbose: Enable detailed logging
```

### 4. Update Template

**Command Syntax**

```sh
tacotruck testfiesta template:update [options]
```

**Required Options**

* -p, --project \<project>: Project key
* -i, --id \<id>: Template ID
* -t, --token \<token>: TestFiesta API token
* -u, --url \<url>: TestFiesta API URL
* -o, --organization \<organization>: Organization handle

**Optional Options**

* -n, --name \<name>: New template name
* -d, --description \<description>: New template description
* \--content \<content>: New template content or path to template file
* -v, --verbose: Enable detailed logging

**Example**

```sh
tacotruck testfiesta template:update \
  -p PROJECT_KEY \
  -i TEMPLATE_ID \
  -t your_api_token \
  -u https://api.testfiesta.com \
  -o your_organization \
  -n "Updated API Template" \
  -d "Updated template for API testing" \
  --content ./templates/updated-api-test.json
```

### 5. Delete Tag

**Command Syntax**

```sh
tacotruck testfiesta template:delete [options]
```

**Required Options**

* -p, --project \<project>: Project key
* -i, --id \<id>: Template ID
* -t, --token \<token>: TestFiesta API token
* -u, --url \<url>: TestFiesta API URL
* -o, --organization \<organization>: Organization handle

**Optional Options**

* -v, --verbose: Enable detailed logging
* \--non-interactive: Skip confirmation prompts

**Example**

```sh
tacotruck testfiesta tag:delete \
  -i TAG_ID \
  -t your_api_token \
  -u https://api.testfiesta.com \
  -o your_organization
```
