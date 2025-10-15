# CircleCI

<figure><img src="../../.gitbook/assets/circle-ci.svg" alt=""><figcaption></figcaption></figure>

CircleCI is a leading continuous integration and continuous deployment (CI/CD) platform that automates your software development process. It enables teams to rapidly build, test, and deploy applications with confidence through automated pipelines.

### TacoTruck: First-Class CircleCI Support

TacoTruck provides **first-class support** for CircleCI through our official orb, making test result submission seamless and efficient. Our orb is designed specifically for CircleCI's architecture and follows CircleCI best practices.

### 🚀 Getting Started

#### Prerequisites

* CircleCI account and project setup
* Test results in supported formats (JUnit XML, etc.)
* API credentials for your target testing platform

### CI/CD Examples

#### Example 1: Node.js Application with TestFiesta

> **Note**: The TacoTruck executor extends the Node.js executor, providing both Node.js environment and TacoTruck CLI pre-installed. For Node.js projects, you can use `tacotruck/default` directly without needing the separate Node orb.

```yaml
version: 2.1

orbs:
  tacotruck: testfiesta/tacotruck@1.0.0

jobs:
  run-tests:
    executor: tacotruck/default
    steps:
      - checkout
      - node/install-packages:
          pkg-manager: npm
      
      # Run tests with coverage
      - run:
          name: Run tests
          command: |
            npm run test:ci
            npm run test:coverage
      
      # Store test results for CircleCI and next job
      - store_test_results:
          path: ./coverage
      - store_artifacts:
          path: ./coverage/lcov-report
      
      # Persist test results for reporting job
      - persist_to_workspace:
          root: .
          paths:
            - coverage/junit.xml

  report-results:
    executor: tacotruck/default
    steps:
      - attach_workspace:
          at: .
      
      # Install TacoTruck
      - tacotruck/install:
          version: "latest"
          check_version: true
      
      # Submit results to TestFiesta
      - tacotruck/submit:
          provider: "testfiesta"
          results_path: "./coverage/junit.xml"
          project_key: "frontend-app"
          api_key: "TESTFIESTA_API_KEY"
          handle: "acme-corp"
          run_name: "Frontend Tests - Build #${CIRCLE_BUILD_NUM}"
          base_url: "https://api.testfiesta.com"

workflows:
  test-and-deploy:
    jobs:
      - run-tests:
          filters:
            branches:
              only: /.*/
      - report-results:
          requires:
            - run-tests
          filters:
            branches:
              only: /.*/
```

#### Example 2: C# Application with NUnit and TestFiesta

```yaml
version: 2.1

orbs:
  tacotruck: testfiesta/tacotruck@1.0.0

jobs:
  run-tests:
    docker:
      - image: mcr.microsoft.com/dotnet/sdk:8.0
    steps:
      - checkout
      
      - run:
          name: Restore NuGet packages
          command: dotnet restore
      
      - run:
          name: Build application
          command: dotnet build --configuration Release --no-restore
      
      - run:
          name: Run tests
          command: |
            dotnet test --configuration Release --no-build \
              --logger "junit;LogFilePath=/tmp/test-results.xml"
      
      - persist_to_workspace:
          root: /tmp
          paths:
            - test-results.xml

  report-results:
    executor: tacotruck/default
    steps:
      - attach_workspace:
          at: /tmp
      
      - tacotruck/install:
          version: "latest"
          check_version: true
      
      - tacotruck/submit:
          provider: "testfiesta"
          results_path: "/tmp/test-results.xml"
          project_key: "dotnet-api"
          api_key: "TESTFIESTA_API_KEY"
          handle: "dev-team"
          run_name: "C# NUnit Tests - Build #${CIRCLE_BUILD_NUM}"
          base_url: "https://api.testfiesta.com"

workflows:
  dotnet-pipeline:
    jobs:
      - run-tests:
          filters:
            branches:
              only: /.*/
      - report-results:
          requires:
            - run-tests
          filters:
            branches:
              only: /.*/

```

### Support and Resources

* &#x20;[TacoTruck Examples Repository](https://github.com/testfiesta/tacotruck-examples)
* &#x20;[NUnit Example](https://github.com/testfiesta/tacotruck-examples/tree/main/demo-circle-ci-nunit-tf)
* [GitHub Issues](https://github.com/testfiesta/tacotruck-orb/issues)
* [TacoTruck CLI Reference](https://github.com/testfiesta/tacotruck)
* &#x20;[TacoTruck Orb Reference](https://circleci.com/developer/orbs/orb/testfiesta/tacotruck)
