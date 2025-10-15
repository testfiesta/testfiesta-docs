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

# Vitest

<figure><img src="../../../.gitbook/assets/vitest-8x (1).png" alt=""><figcaption></figcaption></figure>

Vitest is a fast and lightweight testing framework built on Vite. It offers API for unit, integration, and component testing, and works seamlessly with modern JavaScript and TypeScript projects like [React](https://reactjs.org/), [Vue](https://vuejs.org/) , and others. Vitest can generate standard format JUnit-style XML files which can be submited to Testfiesta or Testrail using Tacotruck CLI. You just need to install the popular [`vitest`](https://vitest.dev/guide/) package and install tacotruck cli or use [Github action](https://github.com/testfiesta/tacotruck-action). Check simple vitest [example](https://github.com/testfiesta/tacotruck-examples/tree/main/demo-vitest-tf)

### Configuration

To generate xml report file  report  output type,  file name path should be configured in config file

```typescript
//vitest.config.ts
import { defineConfig } from "vitest/config";

export default defineConfig({
  test: {
    watch: false,
    exclude: [],
    reporters: ["default", ["junit"]],
    outputFile: {
      junit: "./test-results.xml"
    }
  },
});
```

### Install Tacotruck CLI

{% code overflow="wrap" fullWidth="false" %}
```sh
$ npm install -g @testfiesta/tacotruck
```
{% endcode %}

### Submit test results

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
name: vitest
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
        working-directory: ./demo-vitest-tf
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
         run-name: Vitest CI run ${{ github.run_number }}
         results-path: ./demo-vitest-tf/test-results.xml
```
{% endtab %}
{% endtabs %}

### Support and Resources

* [TacoTruck Examples](https://github.com/testfiesta/tacotruck-examples)
* [Vitest Docs](https://vitest.dev/guide)
* [Tacotruck Issues](https://github.com/testfiesta/tacotruck/issues)
* [**CLI Reference**](../../tacotruck-cli/)
* [Tacotruck Github Action](https://github.com/testfiesta/tacotruck-action)
