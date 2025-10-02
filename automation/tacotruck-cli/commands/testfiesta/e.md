# Runs

#### `testfiesta run:submit` - Submit Test Results

**Command Syntax**

```javascript
tacotruck testfiesta run:submit [options]
```

**Required Options**

* -d, --data \<path>: Path to test results file (XML/JSON)
* -t, --token \<token>: TestFiesta API token
* -h, --organization \<organization>: Organization handle
* -p, --project \<project>: Project key
* -n, --name \<name>: Name for the test run
* -u, --url \<url>: TestFiesta API URL

**Optional Options**

* -v, --verbose: Enable detailed logging

**Example**

```javascript
tacotruck testfiesta run:submit \
  -d ./results.xml \
  -t testfiesta_8a71af8ca7d84b9aadd54d919717e6a2.3b9426653583b1ab6bf30ba161e7fb5c \
  -h offici \
  -p DOLOR \
  -n "CLI test run" \
  -u https://api.testfiesta.com
  
```

**Output Example**

```
// Some code
```

### 2. Project Management

#### `testfiesta project:create` - Create Project

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

#### `testfiesta project:list` - List Projects

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

#### `testfiesta project:delete` - Delete Project

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

### 3. Custom Field Management

#### testfiesta field:create - Create Custom Field

**Command Syntax**

```
tacotruck testfiesta field:create [options]
```

**Required Options**

* -p, --project \<project>: Project key
* -n, --name \<name>: Field name
* \--type \<type>: Field type (text, number, boolean, select, multiselect, date)
* -t, --token \<token>: TestFiesta API token
* -u, --url \<url>: TestFiesta API URL
* -o, --organization \<organization>: Organization handle

**Optional Options**

* -d, --description \<description>: Field description
* -r, --required: Mark field as required
* \--default-value \<value>: Default value
* \--options \<options>: JSON array of options for select/multiselect fields
* -v, --verbose: Enable detailed logging

**Example**

```
tacotruck testfiesta field:create
-p PROJECT_KEY
-n "Priority"
--type select
-t your_api_token
-u https://api.testfiesta.com
-o your_organization
-d "Test priority level"
-r
--options '["Low", "Medium", "High", "Critical"]'
```

**Output Example**

```
// Some code
```

#### `testfiesta field:list` - List Custom Fields

**Command Syntax**

```
tacotruck testfiesta field:list [options]
```

**Required Options**

* -p, --project \<project>: Project key
* -t, --token \<token>: TestFiesta API token
* -u, --url \<url>: TestFiesta API URL
* -o, --organization \<organization>: Organization handle

**Optional Options**

* -l, --limit \<limit>: Number of items to retrieve (default: 10)
* \--offset \<offset>: Offset for pagination (default: 0)
* -v, --verbose: Enable detailed logging

**Example**

```javascript
tacotruck testfiesta field:list \
  -p PROJECT_KEY \
  -t your_api_token \
  -u https://api.testfiesta.com \
  -o your_organization
```

**Output Example**

```
// Some code
```

#### `testfiesta field:get` - Get Custom Field

**Command Syntax**

```
tacotruck testfiesta field:get [options]
```

**Required Options**

* -p, --project \<project>: Project key
* -i, --id \<id>: Field ID
* -t, --token \<token>: TestFiesta API token
* -u, --url \<url>: TestFiesta API URL
* -o, --organization \<organization>: Organization handle

**Optional Options**

* -v, --verbose: Enable detailed logging

**Example**

```
tacotruck testfiesta field:get \
  -p PROJECT_KEY \
  -i FIELD_ID \
  -t your_api_token \
  -u https://api.testfiesta.com \
  -o your_organization
```

**Output Example**

```
// Some code
```

#### `testfiesta field:update` - Update Custom Field

**Command Syntax**

```
tacotruck testfiesta field:update [options]
```

**Optional Options**

* -n, --name \<name>: New field name
* -d, --description \<description>: New field description
* -r, --required: Mark field as required
* \--default-value \<value>: New default value
* \--options \<options>: New JSON array of options
* -v, --verbose: Enable detailed logging

**Example**

```
tacotruck testfiesta field:update \
  -p PROJECT_KEY \
  -i FIELD_ID \
  -n "Updated Priority" \
  -t your_api_token \
  -u https://api.testfiesta.com \
  -o your_organization \
  -d "Updated description"
```

**Output Example**

```
// Some code
```

#### `testfiesta field:delete` - Delete Custom Field

**Command Syntax**

```javascript
tacotruck testfiesta field:delete [options]
```

**Required Options**

* -p, --project \<project>: Project key
* -i, --id \<id>: Field ID
* -t, --token \<token>: TestFiesta API token
* -u, --url \<url>: TestFiesta API URL
* -o, --organization \<organization>: Organization handle

**Optional Options**

* -v, --verbose: Enable detailed logging
* \--non-interactive: Skip confirmation prompts

**Example**

```javascript
tacotruck testfiesta field:delete \
  -p PROJECT_KEY \
  -i FIELD_ID \
  -t your_api_token \
  -u https://api.testfiesta.com \
  -o your_organization
```

**Output Example**

```
// Some code
```

### 4. Tag Management

#### `testfiesta tag:create` - Create Tag

**Command Syntax**

```
tacotruck testfiesta tag:create [options]
```

**Required Options**

* -n, --name \<name>: Tag name
* -t, --token \<token>: TestFiesta API token
* -u, --url \<url>: TestFiesta API URL
* -o, --organization \<organization>: Organization handle

**Optional Options**

* -d, --description \<description>: Tag description
* -c, --color \<color>: Tag color (hex code)
* -v, --verbose: Enable detailed logging

**Example**

```javascript
tacotruck testfiesta tag:create
-n "Regression"
-t your_api_token
-u https://api.testfiesta.com
-o your_organization
-d "Regression tests"
-c "#FF5733"
```

**Output Example**

```
// Some code
```

#### `testfiesta tag:list` - List Tags

**Command Syntax**

```
tacotruck testfiesta tag:list [options]
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

```
tacotruck testfiesta tag:list \
  -t your_api_token \
  -u https://api.testfiesta.com \
  -o your_organization
```

**Output Example**

```
// Some code
```

#### `testfiesta tag:get` - Get Tag

**Command Syntax**

```
tacotruck testfiesta tag:get [options]
```

**Required Options**

* -i, --id \<id>: Tag ID
* -t, --token \<token>: TestFiesta API token
* -u, --url \<url>: TestFiesta API URL
* -o, --organization \<organization>: Organization handle

**Optional Options**

* -v, --verbose: Enable detailed logging

**Example**

```
tacotruck testfiesta tag:get \
  -i TAG_ID \
  -t your_api_token \
  -u https://api.testfiesta.com \
  -o your_organization
```

**Output Example**

```
// Some code
```

#### `testfiesta tag:update` - Update Tag

**Command Syntax**

```
tacotruck testfiesta tag:update [options]
```

**Required Options**

* -i, --id \<id>: Tag ID
* -t, --token \<token>: TestFiesta API token
* -u, --url \<url>: TestFiesta API URL
* -o, --organization \<organization>: Organization handle

**Optional Options**

* -n, --name \<name>: New tag name
* -d, --description \<description>: New tag description
* -c, --color \<color>: New tag color (hex code)
* -v, --verbose: Enable detailed logging

**Example**

```
tacotruck testfiesta tag:update \
  -i TAG_ID \
  -n "Updated Tag" \
  -t your_api_token \
  -u https://api.testfiesta.com \
  -o your_organization \
  -d "Updated description" \
  -c "#33FF57"
```

**Output Example**

```
// Some code
```

#### `testfiesta tag:delete` - Delete Tag

**Command Syntax**

```
tacotruck testfiesta tag:delete [options]
```

**Required Options**

* -i, --id \<id>: Tag ID
* -t, --token \<token>: TestFiesta API token
* -u, --url \<url>: TestFiesta API URL
* -o, --organization \<organization>: Organization handle

**Optional Options**

* -v, --verbose: Enable detailed logging
* \--non-interactive: Skip confirmation prompts

**Example**

```
tacotruck testfiesta tag:delete \
  -i TAG_ID \
  -t your_api_token \
  -u https://api.testfiesta.com \
  -o your_organization
```

**Output Example**

```
// Some code
```
