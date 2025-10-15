# Milestones

### `testfiesta milestone:create`

Create a new milestone in TestFiesta

#### Synopsis

```
tacotruck testfiesta milestone:create -p <project> -n <name> -t <token> -u <url> -o <organization> [options]
```

#### Description

This command creates a new milestone in the specified TestFiesta project. Milestones can be used to track progress across multiple test runs and organize testing efforts around specific release cycles or project phases.

#### Arguments and options

* `-p, --project <project>`: Project key
* `-n, --name <name>`: Milestone name
* `-t, --token <token>`: TestFiesta API token
* `-u, --url <url>`: TestFiesta API URL
* `-o, --organization <organization>`: Organization handle
* `-d, --description <description>`: Milestone description
* `--due-date <date>`: Due date in YYYY-MM-DD format
* `-v, --verbose`: Enable verbose logging

### `testfiesta milestone:list`

List milestones in TestFiesta

#### Synopsis

```
tacotruck testfiesta milestone:list -p <project> -t <token> -u <url> -o <organization> [options]
```

#### Description

This command retrieves and displays a list of all milestones in the specified TestFiesta project. Results can be paginated using the limit and offset options.

#### Arguments and options

* `-p, --project <project>`: Project key
* `-t, --token <token>`: TestFiesta API token
* `-u, --url <url>`: TestFiesta API URL
* `-o, --organization <organization>`: Organization handle
* `-l, --limit <limit>`: Number of items to retrieve (default: 10)
* `--offset <offset>`: Offset for pagination (default: 0)
* `-v, --verbose`: Enable verbose logging

### `testfiesta milestone:get`

Get a specific milestone from TestFiesta

#### Synopsis

```
tacotruck testfiesta milestone:get -p <project> -i <id> -t <token> -u <url> -o <organization> [options]
```

#### Description

This command retrieves detailed information about a specific milestone in the TestFiesta project, including its name, description, due date, status, and associated test runs.

#### Arguments and options

* `-p, --project <project>`: Project key
* `-i, --id <id>`: Milestone ID
* `-t, --token <token>`: TestFiesta API token
* `-u, --url <url>`: TestFiesta API URL
* `-o, --organization <organization>`: Organization handle
* `-v, --verbose`: Enable verbose logging

### `testfiesta milestone:update`

Update a milestone in TestFiesta

#### Synopsis

```
tacotruck testfiesta milestone:update -p <project> -i <id> -t <token> -u <url> -o <organization> [options]
```

#### Description

This command updates an existing milestone in the specified TestFiesta project. You can modify the name, description, due date, and status of the milestone.

#### Arguments and options

* `-p, --project <project>`: Project key
* `-i, --id <id>`: Milestone ID
* `-t, --token <token>`: TestFiesta API token
* `-u, --url <url>`: TestFiesta API URL
* `-o, --organization <organization>`: Organization handle
* `-n, --name <name>`: New milestone name
* `-d, --description <description>`: New milestone description
* `--due-date <date>`: New due date in YYYY-MM-DD format
* `--status <status>`: New status (active, completed)
* `-v, --verbose`: Enable verbose logging

### `testfiesta milestone:delete`

Delete a milestone from TestFiesta

#### Synopsis

```
tacotruck testfiesta milestone:delete -p <project> -i <id> -t <token> -u <url> -o <organization> [options]
```

#### Description

This command deletes a milestone from the specified TestFiesta project. By default, it will prompt for confirmation before deletion unless the --non-interactive flag is used.

#### Arguments and options

* `-p, --project <project>`: Project key
* `-i, --id <id>`: Milestone ID
* `-t, --token <token>`: TestFiesta API token
* `-u, --url <url>`: TestFiesta API URL
* `-o, --organization <organization>`: Organization handle
* `-v, --verbose`: Enable verbose logging
* `--non-interactive`: Skip confirmation prompts
