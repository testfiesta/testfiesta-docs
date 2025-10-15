# Cypress

<figure><img src="../../../.gitbook/assets/cypress.svg" alt=""><figcaption></figcaption></figure>

Cypress is a modern JavaScript-based end-to-end testing framework designed for modern web applications. It runs directly in the browser, providing real-time testing, debugging, and visual feedback. Cypress eliminates the need for external drivers or dependencies and offers a simple yet powerful API for testing web applications. Checkout simple cypress [example](https://github.com/testfiesta/tacotruck-examples/tree/main/demo-cypress-tf).

### Generate XML Report

To generate xml file report, you can use Cypress's built-in JUnit reporter. Configure Cypress to generate JUnit XML reports in `cypress.config.js`:

```javascript
const { defineConfig } = require('cypress')

module.exports = defineConfig({
  e2e: {
    reporter: 'junit',
    reporterOptions: {
      mochaFile: 'reports/test-results.xml',
      toConsole: true
    }
  }
})
```

### Install Tacotruck CLI

```bash
$ npm install -g @testfiesta/tacotruck
```

### Submit Test Results

{% tabs %}
{% tab title="Testfiesta" %}
```sh
tacotruck testfiesta \
  run:submit \
  --token testfiesta_... \
  --handle orgHandle \
  --project projectKey \
  --name runName \
  --data test-results/*.xml
```
{% endtab %}
{% endtabs %}

### Github Action

{% tabs %}
{% tab title="Testfiesta" %}
```yaml
name: cypress
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
      - uses: actions/setup-node@v4
        with:
          node-version: 20
      - name: 📦 Install dependencies
        run: npm install
      - name: 🧪 Cypress run
        uses: cypress-io/github-action@v6
        with:
          start: npm start
          wait-on: 'http://localhost:3000'
      - name: Report Results
        if: false
        uses: testfiesta/tacotruck-action@v1
        with:
         provider: testfiesta
         handle: handle
         project: project
         base-url: https://api.testfiesta.com
         credentials: ${{ secrets.TESTFIESTA_API_KEY }}
         run-name: Cypress CI run ${{ github.run_number }}
         results-path: ./reports/test-results.xml
```
{% endtab %}
{% endtabs %}

### Support and Resources

* [TacoTruck Examples](https://github.com/testfiesta/tacotruck-examples)
* [Cypress Docs](https://docs.cypress.io/app/get-started/why-cypress)
* [Tacotruck Issues](https://github.com/testfiesta/tacotruck/issues)
* [**CLI Reference**](../../tacotruck-cli/)
* [Tacotruck Github Action](https://github.com/testfiesta/tacotruck-action)
