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

# Jest

<div align="center" data-full-width="false"><figure><img src="../../../.gitbook/assets/jest-js-icon.svg" alt="" width="299"><figcaption></figcaption></figure></div>

Jest is a delightful JavaScript Testing Framework with a focus on simplicity.It works with projects using: [Babel](https://babeljs.io/), [TypeScript](https://www.typescriptlang.org/), [Node](https://nodejs.org/), [React](https://reactjs.org/), [Angular](https://angular.io/), [Vue](https://vuejs.org/) and more!  Jest can generate standard format JUnit-style XML files which can be  submited  to Testfiesta or Testrail using taco truck cli. You just need to install the popular [`jest-junit`](https://www.npmjs.com/package/jest-junit) package and install tacotruck  cli or use [Github action](https://github.com/testfiesta/tacotruck-action).  Check simple jest  [example](https://github.com/testfiesta/tacotruck-examples/tree/main/demo-jest-tf) &#x20;

**Configuration**

To generate xml report file  resport  output type,  folder and file name should be configured in config file

```javascript
//jest.config.js

/** @type {import('jest').Config} */
const config = {
  reporters: [
    'default',
    ['jest-junit', {outputDirectory: 'reports', outputName: 'test-results.xml'}],
  ],
};

module.exports = config;
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

**Github action**

{% tabs %}
{% tab title="Testfiesta Example" %}
```json
name: jest
on:
  pull_request:
    branches:
      - main
  push:
    branches:
      - main

jobs:
  test:
    runs-on: ubuntu-latest
    defaults:
      run:
        working-directory: ./demo-jest-tf
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
      - name: 📦 Install dependencies
        run: npm install
      - name: 🧪 Test
        run: npm run test
      - name: Report Results
        if: false
        uses: testfiesta/tacotruck-action@v1
        with:
         provider: testfiesta
         handle: handle
         project: project
         base-url: https://staging.api.testfiesta.com
         credentials: ${{ secrets.TESTFIESTA_API_KEY }}
         run-name: Jest CI run ${{ github.run_number }}
         results-path: ./demo-jest-tf/reports/test-results.xml
```
{% endtab %}
{% endtabs %}
