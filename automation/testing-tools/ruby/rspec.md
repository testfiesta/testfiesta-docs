# RSpec

<figure><img src="../../../.gitbook/assets/rspec-plain-wordmark-8x-2.png" alt="" width="375"><figcaption></figcaption></figure>

RSpec is a behavior-driven development (BDD) testing framework for the Ruby programming language, widely used for testing Ruby code and, notably, Ruby on Rails applications. RSpec  can  generate standard format JUnit-style XML files  which can be  submitted  to Testfiesta or Testrail using Tacotruck CLI. You just need to install the popular [`pytest`](https://docs.pytest.org/en/stable/getting-started.html) , and install tacotruck  cli or use [Github action](https://github.com/testfiesta/tacotruck-action).  Check out simple RSpec [example](https://github.com/testfiesta/tacotruck-examples/tree/main/demo-rspec-tf).\


### Configuration

To generate xml file report,  report file path should be included in command.

```sh
bundle exec rspec --format documentation --format RspecJunitFormatter --out spec/reports/test-results.xml
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
  --key projectKey \
  --name runName \
  --data results-path/*.xml
```
{% endtab %}
{% endtabs %}

### Github Action

{% tabs %}
{% tab title="Testfiesta" %}
```yaml
name: ruby rspec

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
    name: Test
    steps:
    - name: Set up Ruby
      uses: ruby/setup-ruby@v1
      with:
        ruby-version: 3.4.5

    - name: Checkout code
      uses: actions/checkout@v4

    - name: Install dependencies
      run: bundle install

    - name: Run tests
      run: bundle exec rspec --format documentation --format RspecJunitFormatter --out spec/test-reports/test-results.xml

    - name: Report Results
      uses: testfiesta/tacotruck-action@v1
      with:
         provider: testfiesta
         handle: handle
         project: project
         base-url: https://api.testfiesta.com

```
{% endtab %}
{% endtabs %}

### Support and Resources

* [TacoTruck Examples](https://github.com/testfiesta/tacotruck-examples)
* [RSpec Docs](https://rspec.info/documentation)
* [Tacotruck Issues](https://github.com/testfiesta/tacotruck/issues)
* [**CLI Reference**](../../tacotruck-cli/)
* [Tacotruck Github Action](https://github.com/testfiesta/tacotruck-action)
