# Cargo Test

<figure><img src="../../../.gitbook/assets/cargo test.png" alt=""><figcaption></figcaption></figure>

Cargo test is the built-in test command in Rust’s Cargo tool. It compiles your project and runs unit tests, integration tests, and documentation tests automatically.

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

### Support and Resources

* [TacoTruck Examples](https://github.com/testfiesta/tacotruck-examples)
* [Cargo Test Docs](https://doc.rust-lang.org/rust-by-example/testing.html)
* [Tacotruck Issues](https://github.com/testfiesta/tacotruck/issues)
* [**CLI Reference**](../../tacotruck-cli/)
* [Tacotruck Github Action](https://github.com/testfiesta/tacotruck-action)
