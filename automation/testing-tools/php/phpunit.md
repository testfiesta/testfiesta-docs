# PHPUnit

<figure><img src="../../../.gitbook/assets/PHPUnit_Logo.svg" alt=""><figcaption></figcaption></figure>

PHPUnit is a programmer-oriented testing framework for PHP. It is an instance of the xUnit architecture for unit testing frameworks. PHP unit  can  generate standard format JUnit-style XML files  which can be submited  to Testfiesta or Testrail using Tacotruck CLI. Check out simple PHPUnit [example](https://github.com/testfiesta/tacotruck-examples/tree/main/demo-phpunit-tf).

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
name: phpunit

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
          php-version: 8.3
          tools: composer:v2
          coverage: xdebug

      - name: Install Dependencies
        run: composer install --no-interaction --prefer-dist --optimize-autoloader

      - name: Tests
        run: ./vendor/bin/phpunit --log-junit=test-reports/test-results.xml

      - name: Report Results
        uses: testfiesta/tacotruck-action@v1
        with:
         provider: testfiesta
         handle: handle
         project: project
         base-url: https://api.testfiesta.com
         credentials: ${{ secrets.TESTFIESTA_API_KEY }}
         run-name: PHPUnit CI run ${{ github.run_number }}

```
{% endtab %}
{% endtabs %}

### Support and Resources

* [TacoTruck Examples](https://github.com/testfiesta/tacotruck-examples)
* [PHPUnit Docs](https://phpunit.de/documentation.html)
* [Tacotruck Issues](https://github.com/testfiesta/tacotruck/issues)
* [**CLI Reference**](../../tacotruck-cli/)
* [Tacotruck Github Action](https://github.com/testfiesta/tacotruck-action)
