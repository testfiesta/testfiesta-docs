---
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
---

# Playwright

<figure><img src="../../../.gitbook/assets/Playwright_Logo.svg" alt=""><figcaption></figcaption></figure>

Playwright Test is an end-to-end test framework for modern web apps. It bundles test runner, assertions, isolation, parallelization and rich tooling. Playwright can generate standard format JUnit-style XML files which can be  submited  to Testfiesta or Testrail using taco truck cli. You just need to install the popular [`Playweight`](https://mochajs.org/#installation)  and install tacotruck  cli or use [Github action](https://github.com/testfiesta/tacotruck-action).  Check simple playwrite  [example](https://github.com/testfiesta/tacotruck-examples/tree/main/demo-playwright-tf) &#x20;

**Configuration**

To generate xml report file  resport  output type and file name path should be configured in config file

```javascript
//playwright.config.js

import { defineConfig, devices } from '@playwright/test';

export default defineConfig({
  testDir: './tests',
  reporter: [['html'], ['junit', { outputFile: 'test-results.xml' }]],
});
```

**Install tacotruck cli** &#x20;

{% code overflow="wrap" fullWidth="false" %}
```javascript
$ npm install -g @testfiesta/tacotruck
$ tacotruck -h
// output
Usage: tacotruck [options] [command]
[...]
```
{% endcode %}

**Submit test results**

{% tabs %}
{% tab title="Testfiesta Example" %}
```
tacotruck testfiesta \
  run:submit \
  --token testfiesta_... \
  --handle orgHandle \
  --key projectKey \
  --name runName \
  --data results-path/*.xml
```
{% endtab %}

{% tab title="Testrail Example" %}
```
tacotruck testrail \
  run:submit \
  --url https://<your-org-name>.testrail.io \
  --email username@example.com \
  --password password \
  --name "Test run name" \
  --data results-path/*.xml
```
{% endtab %}
{% endtabs %}

