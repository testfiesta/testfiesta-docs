# Testing

<figure><img src="../../../.gitbook/assets/Go-Logo_Blue.png" alt="" width="375"><figcaption></figcaption></figure>

In Golang, package **testing** is responsible for different types of testing maybe it is performance testing, parallel testing, functional testing, or any possible combination of these all. [Gotestsum](https://pkg.go.dev/github.com/IstrateM/gotestsum/pkg/gotestsum) package  can  generate standard format JUnit-style XML files  which can be  submited  to Testfiesta or Testrail using taco truck cli. You just need to install the popular [`Go testing`](https://pkg.go.dev/testing) ,  [Gotestsum](https://pkg.go.dev/github.com/IstrateM/gotestsum/pkg/gotestsum)  and install tacotruck cli or use [Github action](https://github.com/testfiesta/tacotruck-action).  Check  out simple testing  [example](https://github.com/testfiesta/tacotruck-examples/tree/main/demo-golang-tf).

### Configuration

To generate the XML test result, see the following steps:

\
1\. Install gotestsum (only needed once)

```sh
go install gotest.tools/gotestsum@latest
```

2. Make sure `~/go/bin` is in your PATH

```sh
export PATH=$PATH:~/go/bin
```

3. Generate JUnit XML report

```sh
gotestsum --junitfile test-results.xml -- ./test/...
```

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
  --project projectKey \
  --name runName \
  --data results-path/*.xml
```
{% endtab %}
{% endtabs %}

### Github Action

{% tabs %}
{% tab title="Testfiesta" %}
```yaml
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

```
{% endtab %}
{% endtabs %}

### Support and Resources

* [TacoTruck Examples](https://github.com/testfiesta/tacotruck-examples)
* [Testing Docs](https://pkg.go.dev/testing)
* [Tacotruck Issues](https://github.com/testfiesta/tacotruck/issues)
* [**CLI Reference**](../../tacotruck-cli/)
* [Tacotruck Github Action](https://github.com/testfiesta/tacotruck-action)
