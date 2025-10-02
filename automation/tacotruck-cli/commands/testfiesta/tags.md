# Tags

### 1. Create Tag

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

### 2. List Tag

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

### 3. Get Tag

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

### 4. Update Tag

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

### 5. Delete Tag

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
