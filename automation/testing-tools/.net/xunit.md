# XUnit

<figure><img src="../../../.gitbook/assets/xunit-logo.svg" alt=""><figcaption></figcaption></figure>

xUnit is a free, open source, community-focused unit testing tool for C#, F#, and Visual Basic. xUnit.net v3 supports .NET 8.0 or later, and .NET Framework 4.7.2 or later. xUnit.net works with ReSharper, CodeRush, TestDriven.NET and Xamarin. You just need to install the popular xUnit.net test runner and install Tacotruck CLI or use Github action. Check out simple xUnit.net [example](https://github.com/testfiesta/tacotruck-examples/tree/main/demo-dotnet-xunit-tf).

### Generate XML Report

To generate xml file report, you can use the [spekt/testlogger](https://github.com/spekt/testlogger) library which provides Junit, NUnit and Xunit logger/reporter extensions for Visual Studio Test Platform (VSTest).

First, install the appropriate test logger package:

```bash
dotnet add package JunitXml.TestLogger
```

Then run tests with the logger and log file path:

```bash
dotnet test --logger:"junit;LogFilePath=../test-results.xml"
```

### Install Tacotruck CLI

```bash
$ npm install -g @testfiesta/tacotruck
```

### Submit test results

{% tabs %}
{% tab title="Testfiesta" %}
```bash
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
* [XUnit Docs](https://xunit.net/?tabs=cs)
* [Tacotruck Issues](https://github.com/testfiesta/tacotruck/issues)
* [**CLI Reference**](../../tacotruck-cli/)
* [Tacotruck Github Action](https://github.com/testfiesta/tacotruck-action)
