# Getting started

Tacotruck is a powerful tool for moving quality data between different testing platforms. Whether you need to submit test results to TestRail, TestFiesta, or migrate data between test case management tools, Tacotruck provides a simple interface to accomplish these tasks.

### Installation

#### MacOS & Linux

```sh
curl -fsSL https://testfiesta.com/install-tacotruck-cli.sh | bash
```

#### NPM

Make sure you have installed [nodejs](https://nodejs.org/en) in your system with version `18` or higher.

```sh
npm install -g @testfiesta/tacotruck
```

#### Using NPX

```sh
npx @testfiesta/tacotruck
```

### Verify Installation

You can verify installation process by running the following command:

```bash
tacotruck --version
```

### Upgrading CLI

You can simply run the following command to upgrade the CLI:

```sh
tacotruck upgrade
```

### Commands&#x20;

```sh
Commands:

  #testrail testfiesta 
  testfiesta run:submit [options]        Submit test run to testfiesta
  testfiesta project:create [options]    Create a new project in TestFiesta
  testfiesta project:delete [options]    Delete a project in TestFiesta
  testfiesta project:list [options]      List projects in TestFiesta
  testfiesta field:list [options]        List custom fields in a project
  testfiesta field:get [options]         Get a specific custom field by ID
  testfiesta field:create [options]      Create a new custom field
  testfiesta field:update [options]      Update an existing custom field
  testfiesta field:delete [options]      Delete a custom field
  testfiesta tag:list [options]          List all tags
  testfiesta tag:get [options]           Get a specific tag by ID
  testfiesta tag:create [options]        Create a new tag
  testfiesta tag:update [options]        Update an existing tag
  testfiesta tag:delete [options]        Delete a tag
  testfiesta template:list [options]     List templates in a project
  testfiesta template:get [options]      Get a specific template by ID
  testfiesta template:create [options]   Create a new template
  testfiesta template:update [options]   Update an existing template
  testfiesta template:delete [options]   Delete a template
  testfiesta milestone:list [options]    List milestones in a project
  testfiesta milestone:get [options]     Get a specific milestone by ID
  testfiesta milestone:create [options]  Create a new milestone
  testfiesta milestone:update [options]  Update an existing milestone
  testfiesta milestone:delete [options]  Delete a milestone
  
  #testrail commands 
  testrail run:submit [options]      Submit test run to TestRail
  testrail project:create [options]  Create a new project in TestRail
  testrail project:delete [options]  Delete a project in TestRail
```

### Basic Commands

Tacotruck supports multiple testing platforms. Here are the main commands:

#### TestFiesta Integration

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

### Supported File Formats

Tacotruck supports various test result formats:

* JUnit XML
