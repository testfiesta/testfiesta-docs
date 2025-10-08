# Cargo Test

<figure><img src="../../../.gitbook/assets/cargo test.png" alt=""><figcaption></figcaption></figure>

Cargo test is the built-in test command in Rust’s Cargo tool. It compiles your project and runs unit tests, integration tests, and documentation tests automatically.

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
