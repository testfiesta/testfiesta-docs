# Runs

### `testfiesta run:submit`

Submit test results to TestFiesta

#### Synopsis

```
tacotruck testfiesta run:submit -d <path> -t <token> -h <organization> -p <project> -n <name> -u <url> [options]
```

#### Description

This command submits test results from a JUnit XML or JSON file to TestFiesta. It authenticates with TestFiesta using the provided API token, creates a new test run with the specified name, and uploads all test results to the specified project.

The command shows progress during the upload process and confirms successful submission when complete.

#### Arguments and options

* `-d, --data <path>`: Path to test run data JSON/XML file
* `-t, --token <token>`: TestFiesta API token
* `-h, --organization <organization>`: Organization handle
* `-p, --project <project>`: Project key
* `-n, --name <name>`: Name for the test run
* `-u, --url <url>`: TestFiesta instance URL (e.g., https://api.testfiesta.com)
* `-v, --verbose`: Enable verbose logging
