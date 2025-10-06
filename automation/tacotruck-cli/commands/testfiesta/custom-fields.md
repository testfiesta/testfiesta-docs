# Custom Fields

### 1. Create Custom Field

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

### 2. List Custom Field

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

### 3. Get Custom Field

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

### 4. Update Custom Field

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

### 1. Delete Custom Field

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
