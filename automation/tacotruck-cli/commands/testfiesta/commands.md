# Runs

#### 1. Submit Test run

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
