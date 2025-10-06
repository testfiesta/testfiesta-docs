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

# Bun

<figure><img src="../../../.gitbook/assets/bun (1).svg" alt=""><figcaption></figcaption></figure>

Bun ships with a fast, built-in, Jest-compatible test runner that runs directly on the Bun runtime and supports TypeScript, JSX, lifecycle hooks, snapshot testing, UI & DOM testing Vitest can generate standard format JUnit-style XML files which can be submited to Testfiesta or Testrail using taco truck cli. You just need to install the popular [`Bun`](https://bun.sh/docs) and install tacotruck cli or use [Github action](https://github.com/testfiesta/tacotruck-action). Check simple bun [example](https://github.com/testfiesta/tacotruck-examples/tree/main/demo-bun-tf)

**Configuration**

To generate xml report file  resport  output type and  file name ptah  should be configured in  test command scripts section  of package.json

```javascript
//package.json

{
  "scripts": {
    "test:report": "bun test --reporter=junit --reporter-outfile=./test-results.xml"
  },
}
```

**Install tacotruck cli**

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
  --project projectKey \
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
name: bun
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
    steps:
      - uses: actions/checkout@v4
      - uses: oven-sh/setup-bun@v2
        with:
          bun-version: 1.2.16
      - name: 📦 Install dependencies
        run: bun install
      - name: 🧪 Test
        run: bun test:report
      - name: Report Results
        uses: testfiesta/tacotruck-action@v1
        with:
         provider: testfiesta
         handle: <handle>
         project: <project>
         run-name: <run name>
         base-url: https://api.testfiesta.com
         credentials: ${{ secrets.TESTFIESTA_API_KEY }}
         results-path: ./reports/test-results.xml
```
{% endtab %}
{% endtabs %}
