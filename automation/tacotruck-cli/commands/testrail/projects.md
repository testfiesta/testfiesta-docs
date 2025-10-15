# Projects

### `testrail project:create`

Create a new project in TestRail

#### Synopsis

```
tacotruck testrail project:create -n <name> -t <token> -u <url> [options]
```

#### Description

This command creates a new project in TestRail with the specified name. You can choose the project structure (suite mode) during creation.

#### Arguments and options

* `-n, --name <name>`: Project name
* `-t, --token <token>`: TestRail API token in username:password format
* `-u, --url <url>`: TestRail instance URL (e.g., https://example.testrail.io)
* `-s, --suite-mode <suiteMode>`: TestRail project structure:
  * `1`: Single repository for all cases (default)
  * `2`: Single repository with baselines
  * `3`: Multiple test suites
* `-v, --verbose`: Enable verbose logging

### `testrail project:delete`

Delete a project in TestRail

#### Synopsis

```
tacotruck testrail project:delete -i <projectId> -t <token> -u <url> [options]
```

#### Description

This command deletes a project from TestRail. By default, it will prompt for confirmation before deletion unless the --force flag is used.

#### Arguments and options

* `-i, --project-id <id>`: TestRail project ID to delete
* `-t, --token <token>`: TestRail API token in username:password format
* `-u, --url <url>`: TestRail instance URL (e.g., https://example.testrail.io)
* `-f, --force`: Skip confirmation prompt
* `-v, --verbose`: Enable verbose logging
