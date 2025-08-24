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

# Vitest

<figure><img src="../../../.gitbook/assets/vitest-8x.png" alt=""><figcaption></figcaption></figure>

Vitest is a fast and lightweight testing framework built on Vite. It offers  API for unit, integration, and component testing, and works seamlessly with modern JavaScript and TypeScript projects like [React](https://reactjs.org/), [Vue](https://vuejs.org/) , and others. Vitest can generate standard format JUnit-style XML files which can be  submited  to Testfiesta or Testrail using taco truck cli. You just need to install the popular [`vitest`](https://vitest.dev/guide/) package and install tacotruck  cli or use [Github action](https://github.com/testfiesta/tacotruck-action).  Check simple jest  [example](https://github.com/testfiesta/tacotruck-examples/tree/main/demo-jest-tf) &#x20;

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

