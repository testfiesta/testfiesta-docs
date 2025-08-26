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

# ExUnit



<figure><img src="../../../.gitbook/assets/Elixir_programming_language_logo.svg" alt=""><figcaption></figcaption></figure>

ExUnit. Elixir's built-in test framework is ExUnit and it includes everything we need to thoroughly test our code. Before moving on it is important to note that tests are implemented as Elixir scripts so we need to use the . exs file extension. ExUnit  can  generate standard format JUnit-style XML files  which can be  submited  to Testfiesta or Testrail using taco truck cli. You just need to check how to test using [`Exunit`](https://elixirschool.com/en/lessons/testing/basics) , and install tacotruck  cli or use [Github action](https://github.com/testfiesta/tacotruck-action).  Check simple ExUnit   [example](https://github.com/testfiesta/tacotruck-examples/tree/main/demo_elixir_tf) &#x20;

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
<pre class="language-json"><code class="lang-json">name: elixir

on:
  pull_request:
    branches:
      - main
  push:
    branches:
      - main

env:
  MIX_ENV: test

permissions:
  contents: read
jobs:
  test:
    runs-on: ubuntu-latest
    name: Test
    steps:
    - name: Set up Elixir
      uses: erlef/setup-beam@v1
      with:
        otp-version: 27
        elixir-version: 1.18.3

    - name: Checkout code
      uses: actions/checkout@v4

    - name: Install dependencies
      run: mix deps.get

    - name: Compiles without warnings
      run: mix compile --warnings-as-errors

    - name: Check Formatting
      run: mix format --check-formatted

    - name: Run tests
      run: mix test

<strong>    - name: Report Results
</strong>      uses: testfiesta/tacotruck-action@v1
      with:
         provider: testfiesta
         handle: handle
         project: project
         base-url: https://api.testfiesta.com
         credentials: ${{ secrets.TESTFIESTA_API_KEY }}
         run-name: Elixir CI run ${{ github.run_number }}
         results-path: ./test-reports/test-results.xml
</code></pre>
{% endtab %}

{% tab title="Testrail Example" %}

{% endtab %}
{% endtabs %}
