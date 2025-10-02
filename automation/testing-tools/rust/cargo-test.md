# Cargo Test

<figure><img src="../../../.gitbook/assets/cargo test.png" alt=""><figcaption></figcaption></figure>

Cargo test is the built-in test command in Rust’s Cargo tool. It compiles your project and runs unit tests, integration tests, and documentation tests automatically.

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
{% endtabs %}
