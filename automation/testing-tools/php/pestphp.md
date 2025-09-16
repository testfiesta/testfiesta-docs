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

# PestPHP



<figure><img src="../../../.gitbook/assets/pestphp logo.jpeg" alt=""><figcaption></figcaption></figure>

Pest is a testing framework with a focus on simplicity,meticulously designed to bring back the joy of testing in PHP. Pest  can  generate standard format JUnit-style XML files  which can be  submited  to Testfiesta or Testrail using taco truck cli. You just need to install the popular [`Pest`](https://pestphp.com/docs/installation) and install tacotruck  cli or use [Github action](https://github.com/testfiesta/tacotruck-action).  Check simple pest  [example](https://github.com/testfiesta/tacotruck-examples/tree/main/demo-pestphp-tf) &#x20;

**Generate xml report file**&#x20;

To genereate xml file  report  of the test logger and log file path should be included in command&#x20;

```javascript
// test report command
./vendor/bin/phpunit --log-junit=test-reports/test-results.xml
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
name: pestphp

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
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup PHP
        uses: shivammathur/setup-php@v2
        with:
          php-version: 8.2
          tools: composer:v2
          coverage: xdebug

      - name: Install Dependencies
        run: composer install --no-interaction --prefer-dist --optimize-autoloader

      - name: Tests
        run: ./vendor/bin/pest --ci --log-junit=test-reports/test-results.xml

      - name: Report Results
        uses: testfiesta/tacotruck-action@v1
        with:
         provider: testfiesta
         handle: handle
         project: project
         base-url: https://staging.api.testfiesta.com
         credentials: ${{ secrets.TESTFIESTA_API_KEY }}
         run-name: PestPHP CI run ${{ github.run_number }}
         results-path: ./test-reports/test-results.xml
```
{% endtab %}

{% tab title="Testrail Example" %}

{% endtab %}
{% endtabs %}
