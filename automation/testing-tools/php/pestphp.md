# PestPHP

<figure><img src="../../../.gitbook/assets/pestphp logo.jpeg" alt=""><figcaption></figcaption></figure>

Pest is a testing framework with a focus on simplicity, meticulously designed to bring back the joy of testing in PHP. Pest  can  generate standard format JUnit-style XML files  which can be  submitted  to Testfiesta or Testrail using taco truck cli. You just need to install the popular [`Pest`](https://pestphp.com/docs/installation) and install Tacotruck  CLI or use [Github action](https://github.com/testfiesta/tacotruck-action).  Check out simple pest [example](https://github.com/testfiesta/tacotruck-examples/tree/main/demo-pestphp-tf).

### Configuration

To generate xml file  report  of the test logger and log file path should be included in command&#x20;

```sh
./vendor/bin/phpunit --log-junit=test-reports/test-results.xml
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

```
{% endtab %}
{% endtabs %}

### Support and Resources

* [TacoTruck Examples](https://github.com/testfiesta/tacotruck-examples)
* [PestPHP Docs](https://pestphp.com/docs/pest-v4-is-here-now-with-browser-testing)
* [Tacotruck Issues](https://github.com/testfiesta/tacotruck/issues)
* [**CLI Reference**](../../tacotruck-cli/)
* [Tacotruck Github Action](https://github.com/testfiesta/tacotruck-action)
