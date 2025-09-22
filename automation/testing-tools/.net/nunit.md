# NUnit

<figure><img src="../../../.gitbook/assets/Nunit_logo_250.png" alt=""><figcaption></figcaption></figure>

NUnit is a unit-testing framework for all .NET languages. NUnit can be used for a wide range of testing, from unit testing with TDD to full fledged system and integration testing. Nunit can generate standard format JUnit-style XML files which can be  submited  to Testfiesta or Testrail using taco truck cli. You just need to install the popular [`Nunit`](http://nunit.org/nunitv2/docs/2.6.2/quickStart.html)   and install tacotruck  cli or use [Github action](https://github.com/testfiesta/tacotruck-action).  Check simple NUnit  [example](https://github.com/testfiesta/tacotruck-examples/tree/main/demo-dotnet-nunit-tf) &#x20;

**Generate xml report file**&#x20;

To genereate xml file  report  of the test logger and log file path should be included in command&#x20;

```javascript
// dotnet test command
dotnet test --logger:"junit;LogFilePath=../test-results.xml"
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
{% endtabs %}
