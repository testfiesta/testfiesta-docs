# Projects

### `testfiesta project:create`

Create a new project in TestFiesta

#### Synopsis

```
tacotruck testfiesta project:create -n <name> -t <token> -u <url> -h <organization> [options]
```

#### Description

This command creates a new project in TestFiesta with the specified name. The project will be associated with the organization identified by the organization handle.

#### Arguments and options

* `-n, --name <name>`: Project name
* `-t, --token <token>`: TestFiesta API token
* `-u, --url <url>`: TestFiesta API URL
* `-h, --organization <organization>`: Organization handle
* `-v, --verbose`: Enable verbose logging

### `testfiesta project:list`

List projects in TestFiesta

#### Synopsis

```
tacotruck testfiesta project:list -t <token> -u <url> -o <organization> [options]
```

#### Description

This command retrieves and displays a list of all projects in the specified TestFiesta organization. Results can be paginated using the limit and offset options.

#### Arguments and options

* `-t, --token <token>`: TestFiesta API token
* `-u, --url <url>`: TestFiesta API URL
* `-o, --organization <organization>`: Organization handle
* `-l, --limit <limit>`: Number of items to retrieve (default: 10)
* `--offset <offset>`: Offset for pagination (default: 0)
* `-v, --verbose`: Enable verbose logging

### `testfiesta project:delete`

Delete a project in TestFiesta

#### Synopsis

```
tacotruck testfiesta project:delete -p <project> -t <token> -u <url> -h <organization> [options]
```

#### Description

This command deletes a project from TestFiesta. By default, it will prompt for confirmation before deletion unless the --non-interactive flag is used.

#### Arguments and options

* `-p, --project <project>`: Project key
* `-t, --token <token>`: TestFiesta API token
* `-u, --url <url>`: TestFiesta API URL
* `-h, --organization <organization>`: Organization handle
* `-v, --verbose`: Enable detailed logging
* `--non-interactive`: Skip confirmation prompts (use with caution)
