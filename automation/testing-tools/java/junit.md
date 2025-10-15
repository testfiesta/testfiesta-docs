# JUnit

<figure><img src="../../../.gitbook/assets/junit.png" alt=""><figcaption></figcaption></figure>

JUnit is a widely-used unit testing framework for Java applications. It provides annotations to identify test methods, assertions for testing expected results, and test runners for running tests. JUnit supports test-driven development and is integrated into most Java IDEs and build tools like Maven and Gradle. It offers powerful features for organizing, running, and reporting test results. Checkout simple junit [example](https://github.com/testfiesta/tacotruck-examples/tree/main/demo-java-junit-tf).

### Generate XML Report

To generate XML file reports, you can configure JUnit to output test results in XML format using Maven Surefire or Gradle plugins.

#### Maven Configuration

Configure Maven Surefire plugin in your `pom.xml`:

```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-surefire-plugin</artifactId>
    <version>3.0.0</version>
    <configuration>
        <reportFormat>xml</reportFormat>
        <reportsDirectory>${project.build.directory}/surefire-reports</reportsDirectory>
    </configuration>
</plugin>
```

#### Gradle Configuration

Configure test reporting in your `build.gradle`:

```gradle
test {
    useJUnitPlatform()
    reports {
        junitXml.enabled = true
        junitXml.destination = file("$buildDir/test-results/test")
    }
    testLogging {
        events "passed", "skipped", "failed"
    }
}
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
name: junit-tests
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
          
      - name: 🧪 Run JUnit Tests
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
          run-name: JUnit CI run ${{ github.run_number }}
          results-path: ./target/surefire-reports/*.xml
```

### Gradle GitHub Action

For Gradle projects, use this configuration instead:

```yaml
name: junit-gradle-tests
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
        
      - name: 🧪 Run JUnit Tests
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
          run-name: JUnit Gradle CI run ${{ github.run_number }}
          results-path: ./build/test-results/test/*.xml
```

### Support and Resources

* [TacoTruck Examples](https://github.com/testfiesta/tacotruck-examples)
* [JUnit Docs](https://docs.junit.org/current/user-guide)
* [Tacotruck Issues](https://github.com/testfiesta/tacotruck/issues)
* [**CLI Reference**](../../tacotruck-cli/)
* [Tacotruck Github Action](https://github.com/testfiesta/tacotruck-action)
