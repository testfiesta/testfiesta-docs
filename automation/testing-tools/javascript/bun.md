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

Bun ships with a fast, built-in, Jest-compatible test runner that runs directly on the Bun runtime and supports TypeScript, JSX, lifecycle hooks, snapshot testing, UI & DOM testing Vitest can generate standard format JUnit-style XML files which can be submited to Testfiesta or Testrail using Tacotruck CLI. You just need to install the popular [`Bun`](https://bun.sh/docs) and install tacotruck cli or use [Github action](https://github.com/testfiesta/tacotruck-action). Check out simple bun [example](https://github.com/testfiesta/tacotruck-examples/tree/main/demo-bun-tf).

### Configuration

To generate xml report, output path and file name should be configured in  test command scripts section of package.json

```json
{
  "scripts": {
    "test:report": "bun test --reporter=junit --reporter-outfile=./test-results.xml"
  },
}
```

### Install Tacotruck CLI

{% code overflow="wrap" fullWidth="false" %}
```sh
$ npm install -g @testfiesta/tacotruck
```
{% endcode %}

### Submit Test results

{% tabs %}
{% tab title="Testfiesta" %}
```sh
tacotruck testfiesta \
  run:submit \
  --token testfiesta_... \
  --handle orgHandle \
  --project projectKey \
  --name runName \
  --data results-path/*.xml
```
{% endtab %}
{% endtabs %}

### Github Action

{% tabs %}
{% tab title="Testfiesta" %}
```yaml
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

### Support and Resources

* [TacoTruck Examples](https://github.com/testfiesta/tacotruck-examples)
* [Bun Docs](https://bun.com/docs)
* [Tacotruck Issues](https://github.com/testfiesta/tacotruck/issues)
* [**CLI Reference**](../../tacotruck-cli/)
* [Tacotruck Github Action](https://github.com/testfiesta/tacotruck-action)
