# ExUnit

<figure><img src="../../../.gitbook/assets/Elixir_programming_language_logo.svg" alt=""><figcaption></figcaption></figure>

ExUnit. Elixir's built-in test framework is ExUnit and it includes everything we need to thoroughly test our code. Before moving on it is important to note that tests are implemented as Elixir scripts so we need to use the . exs file extension. ExUnit  can  generate standard format JUnit-style XML files  which can be  submitted  to Testfiesta or Testrail using taco truck cli. You just need to check how to test using [`Exunit`](https://elixirschool.com/en/lessons/testing/basics) , and install tacotruck  cli or use [Github action](https://github.com/testfiesta/tacotruck-action).  Check out simple ExUnit [example](https://github.com/testfiesta/tacotruck-examples/tree/main/demo_elixir_tf).

**Install Tacotruck CLI**

{% code overflow="wrap" fullWidth="false" %}
```sh
$ npm install -g @testfiesta/tacotruck
```
{% endcode %}

**Submit test results**

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
