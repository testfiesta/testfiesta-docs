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

# Mocha

<figure><img src="../../../.gitbook/assets/Mocha_logo.svg" alt="" width="256"><figcaption></figcaption></figure>

Mocha is a feature-rich JavaScript test framework running on [Node.js](https://nodejs.org/) and in the browser, making asynchronous testing _simple_ and _fun_. Mocha can generate standard format JUnit-style XML files which can be  submited  to Testfiesta or Testrail using taco truck cli. You just need to install the popular [`Mocha`](https://mochajs.org/#installation)  and install tacotruck  cli or use [Github action](https://github.com/testfiesta/tacotruck-action).  Check simple jest  [example](https://github.com/testfiesta/tacotruck-examples/tree/main/demo-mocha-tf) &#x20;

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
