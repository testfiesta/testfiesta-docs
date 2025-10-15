# TestNG

<figure><img src="../../../.gitbook/assets/testng.png" alt=""><figcaption></figcaption></figure>

TestNG is a powerful testing framework for Java that provides advanced features beyond JUnit. It supports data-driven testing, parallel execution, flexible test configuration, and comprehensive reporting. TestNG uses annotations to define test methods and offers features like test groups, dependencies, parameters, and listeners. It's particularly well-suited for integration testing, functional testing, and complex test scenarios with its XML-based configuration and advanced test management capabilities. Checkout simple [TestNG](https://github.com/testfiesta/tacotruck-examples/tree/main/demo-java-testng-tf).

### Generate XML Report

TestNG automatically generates XML reports by default. You can configure additional reporting options using Maven Surefire or Gradle plugins.

#### Maven Configuration

Configure Maven Surefire plugin in your `pom.xml`:

```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-surefire-plugin</artifactId>
    <version>3.0.0</version>
    <configuration>
        <suiteXmlFiles>
            <suiteXmlFile>src/test/resources/testng.xml</suiteXmlFile>
        </suiteXmlFiles>
        <reportFormat>xml</reportFormat>
        <reportsDirectory>${project.build.directory}/surefire-reports</reportsDirectory>
    </configuration>
</plugin>
```

#### Gradle Configuration

Configure TestNG in your `build.gradle`:

```gradle
test {
    useTestNG() {
        suites 'src/test/resources/testng.xml'
    }
    reports {
        junitXml.enabled = true
        junitXml.destination = file("$buildDir/test-results/test")
    }
    testLogging {
        events "passed", "skipped", "failed"
    }
}

dependencies {
    testImplementation 'org.testng:testng:7.8.0'
}
```

#### TestNG XML Suite Configuration

Create a `testng.xml` file in `src/test/resources/`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<suite name="TestSuite" verbose="1">
    <test name="TestNGTests">
        <classes>
            <class name="com.example.tests.SampleTest"/>
        </classes>
    </test>
</suite>
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
  --data target/surefire-reports/*.xml
```

### GitHub Action

```yaml
name: testng-tests
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
      
      - name: Set up JDK 17
        uses: actions/setup-java@v4
        with:
          java-version: '17'
          distribution: 'temurin'
          
      - name: Cache Maven dependencies
        uses: actions/cache@v3
        with:
          path: ~/.m2
          key: ${{ runner.os }}-m2-${{ hashFiles('**/pom.xml') }}
          restore-keys: ${{ runner.os }}-m2
          
      - name: 🧪 Run TestNG Tests
        run: mvn clean test
        
      - name: Report Results
        if: always()
        uses: testfiesta/tacotruck-action@v1
        with:
          provider: testfiesta
          handle: handle
          project: project
          base-url: https://api.testfiesta.com
          credentials: ${{ secrets.TESTFIESTA_API_KEY }}
          run-name: TestNG CI run ${{ github.run_number }}
          results-path: ./target/surefire-reports/*.xml
```

### Gradle GitHub Action

For Gradle projects, use this configuration instead:

```yaml
name: testng-gradle-tests
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
      
      - name: Set up JDK 17
        uses: actions/setup-java@v4
        with:
          java-version: '17'
          distribution: 'temurin'
          
      - name: Setup Gradle
        uses: gradle/gradle-build-action@v2
        
      - name: 🧪 Run TestNG Tests
        run: ./gradlew test
        
      - name: Report Results
        if: always()
        uses: testfiesta/tacotruck-action@v1
        with:
          provider: testfiesta
          handle: handle
          project: project
          base-url: https://api.testfiesta.com
          credentials: ${{ secrets.TESTFIESTA_API_KEY }}
          run-name: TestNG Gradle CI run ${{ github.run_number }}
          results-path: ./build/test-results/test/*.xml
```

### TestNG Parallel Execution

TestNG supports parallel test execution. Configure in your `testng.xml`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<suite name="ParallelTestSuite" parallel="methods" thread-count="3">
    <test name="ParallelTests">
        <classes>
            <class name="com.example.tests.ParallelTest"/>
        </classes>
    </test>
</suite>
```

Or configure parallel execution in Maven:

```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-surefire-plugin</artifactId>
    <version>3.0.0</version>
    <configuration>
        <parallel>methods</parallel>
        <threadCount>3</threadCount>
        <suiteXmlFiles>
            <suiteXmlFile>src/test/resources/testng.xml</suiteXmlFile>
        </suiteXmlFiles>
    </configuration>
</plugin>
```

### Support and Resources

* [TacoTruck Examples](https://github.com/testfiesta/tacotruck-examples)
* [TestNG Docs](https://testng.org/)
* [Tacotruck Issues](https://github.com/testfiesta/tacotruck/issues)
* [**CLI Reference**](../../tacotruck-cli/)
* [Tacotruck Github Action](https://github.com/testfiesta/tacotruck-action)
