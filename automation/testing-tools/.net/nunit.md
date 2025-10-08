# NUnit

<figure><img src="../../../.gitbook/assets/Nunit_logo_250.png" alt=""><figcaption></figcaption></figure>

NUnit is a unit-testing framework for all .NET languages. NUnit can be used for a wide range of testing, from unit testing with TDD to full fledged system and integration testing. Nunit can generate standard format JUnit-style XML files which can be  submited  to Testfiesta or Testrail using taco truck cli. You just need to install the popular [`Nunit`](http://nunit.org/nunitv2/docs/2.6.2/quickStart.html)  and install tacotruck cli or use [Github action](https://github.com/testfiesta/tacotruck-action). Check out simple NUnit [example](https://github.com/testfiesta/tacotruck-examples/tree/main/demo-dotnet-nunit-tf).

**Generate xml report file**&#x20;

To generate xml file  report  of the test logger and log file path should be included in command&#x20;

```sh
dotnet test --logger:"junit;LogFilePath=../test-results.xml"
```

**Install Tacotruck CLI**

{% code overflow="wrap" fullWidth="false" %}
```sh
$ npm install -g @testfiesta/tacotruck
```
{% endcode %}

**Submit test results**

{% tabs %}
{% tab title="Testfiesta Example" %}
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
