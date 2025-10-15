# MSTest

MSTest is Microsoft's official testing framework for .NET applications. It's a fully supported, open-source, cross-platform framework that works with all .NET targets (.NET Framework, .NET Core, .NET, UWP, WinUI). MSTest integrates seamlessly with Visual Studio, VS Code Test Explorer, .NET CLI, and CI pipelines.

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

### Submit Test Results

```bash
tacotruck testfiesta \
  run:submit \
  --token testfiesta_... \
  --handle orgHandle \
  --project projectKey \
  --name runName \
  --data results-path/*.xml
```

### Support and Resources

* [TacoTruck Examples](https://github.com/testfiesta/tacotruck-examples)
* [MSTest Docs](https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-mstest-intro)
* [Tacotruck Issues](https://github.com/testfiesta/tacotruck/issues)
* [**CLI Reference**](../../tacotruck-cli/)
* [Tacotruck Github Action](https://github.com/testfiesta/tacotruck-action)
