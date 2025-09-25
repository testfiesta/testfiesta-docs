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

# Jest

<div align="center" data-full-width="false"><figure><img src="../../../.gitbook/assets/jest-js-icon.svg" alt="" width="299"><figcaption></figcaption></figure></div>

Jest is a delightful JavaScript Testing Framework with a focus on simplicity.It works with projects using: [Babel](https://babeljs.io/), [TypeScript](https://www.typescriptlang.org/), [Node](https://nodejs.org/), [React](https://reactjs.org/), [Angular](https://angular.io/), [Vue](https://vuejs.org/) and more! Jest can generate standard format JUnit-style XML files which can be submited to Testfiesta or Testrail using taco truck cli. You just need to install the popular [`jest-junit`](https://www.npmjs.com/package/jest-junit) package and install tacotruck cli or use [Github action](https://github.com/testfiesta/tacotruck-action). Check simple jest [example](https://github.com/testfiesta/tacotruck-examples/tree/main/demo-jest-tf)

**Install tacotruck cli**

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
