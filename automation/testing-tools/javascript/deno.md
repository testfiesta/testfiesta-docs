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

# Deno

<figure><img src="../../../.gitbook/assets/Deno_Logo_2024.svg.png" alt="" width="256"><figcaption></figcaption></figure>

Deno provides a built-in test runner for writing and running tests in both JavaScript and TypeScript. Deno can generate standard format JUnit-style XML files which can be submited to Testfiesta or Testrail using taco truck cli. You just need to install the popular [`Deno`](https://docs.deno.com/runtime/) and install tacotruck cli or use [Github action](https://github.com/testfiesta/tacotruck-action). Check simple deno [example](https://github.com/testfiesta/tacotruck-examples/tree/main/demo-deno-tf)

**Configuration**

To generate xml report file  resport  output type and  file name ptah  should be configured in  test command scripts section  of done.json

```javascript
//deno.json

{
  "tasks": {
    "test:report": "deno test --junit-path=./test-results.xml"
  }
}
```

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

**Github action**

{% tabs %}
{% tab title="Testfiesta Example" %}
```json
name: deno
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
      - uses: actions/checkout@v4
      - uses: denoland/setup-deno@v2
        with:
          deno-version: v2.x
      - name: 🧪 Test
        run: deno task test:report
      - name: Report Results
        uses: testfiesta/tacotruck-action@v1
        with:
         provider: testfiesta
         handle: <handle>
         project: <project>
         run-name: <run name>
         base-url: https://api.testfiesta.com
         credentials: ${{ secrets.TESTFIESTA_API_KEY }}
         results-path: ./test-results.xml
```
{% endtab %}

{% tab title="Testrail Example" %}

{% endtab %}
{% endtabs %}
