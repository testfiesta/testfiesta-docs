# Testing

<figure><img src="../../../.gitbook/assets/Go-Logo_Blue.png" alt=""><figcaption></figcaption></figure>

In Golang, package **testing** is responsible for different types of testing maybe it is performance testing, parallel testing, functional testing, or any possible combination of these all. [Gotestsum](https://pkg.go.dev/github.com/IstrateM/gotestsum/pkg/gotestsum) package  can  generate standard format JUnit-style XML files  which can be  submited  to Testfiesta or Testrail using taco truck cli. You just need to install the popular [`Go testing`](https://pkg.go.dev/testing) ,  [Gotestsum](https://pkg.go.dev/github.com/IstrateM/gotestsum/pkg/gotestsum)  and install tacotruck  cli or use [Github action](https://github.com/testfiesta/tacotruck-action).  Check simple testing  [example](https://github.com/testfiesta/tacotruck-examples/tree/main/demo-golang-tf) &#x20;

**Steps to generate test report xml file** \
1\. Install gotestsum (only needed once)

```
go install gotest.tools/gotestsum@latest
```

2. Make sure \~/go/bin is in your PATH

```
export PATH=$PATH:~/go/bin
```

3. Generate JUnit XML report

```
gotestsum --junitfile test-results.xml -- ./test/...
```

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
```json
name: Go Tests
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

      - name: 📦 Set up Go
        uses: actions/setup-go@v4
        with:
          go-version: "1.24.2"

      - name: 📦 Install dependencies
        run: go mod download

      - name: 📦 Install gotestsum
        run: |
          go install gotest.tools/gotestsum@latest
          export PATH=$PATH:~/go/bin

      - name: 🧪 Run tests
        run: gotestsum --junitfile test-results.xml -- ./test/...

      - name: Report Results
        uses: testfiesta/tacotruck-action@v1
        with:
          provider: testfiesta
          handle: handle
          project: project
          run-name: Go testing CI run
          base-url: https://api.testfiesta.com
          credentials: ${{ secrets.TESTFIESTA_API_KEY }}
          results-path: ./test-results.xml
```
{% endtab %}
{% endtabs %}
