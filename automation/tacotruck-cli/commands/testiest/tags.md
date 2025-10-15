# Tags

### `testfiesta tag:create`

Create a new tag in TestFiesta

#### Synopsis

```
tacotruck testfiesta tag:create -n <name> -t <token> -u <url> -o <organization> [options]
```

#### Description

This command creates a new tag in TestFiesta. Tags can be used to categorize and filter test cases, test runs, and other entities in the system.

#### Arguments and options

* `-n, --name <name>`: Tag name
* `-t, --token <token>`: TestFiesta API token
* `-u, --url <url>`: TestFiesta API URL
* `-o, --organization <organization>`: Organization handle
* `-d, --description <description>`: Tag description
* `-c, --color <color>`: Tag color (hex code, e.g., #FF5733)
* `-v, --verbose`: Enable verbose logging

### `testfiesta tag:list`

List tags in TestFiesta

#### Synopsis

```
tacotruck testfiesta tag:list -t <token> -u <url> -o <organization> [options]
```

#### Description

This command retrieves and displays a list of all tags in the TestFiesta organization. Results can be paginated using the limit and offset options.

#### Arguments and options

* `-t, --token <token>`: TestFiesta API token
* `-u, --url <url>`: TestFiesta API URL
* `-o, --organization <organization>`: Organization handle
* `-l, --limit <limit>`: Number of items to retrieve (default: 10)
* `--offset <offset>`: Offset for pagination (default: 0)
* `-v, --verbose`: Enable verbose logging

### `testfiesta tag:get`

Get a specific tag from TestFiesta

#### Synopsis

```
tacotruck testfiesta tag:get -i <id> -t <token> -u <url> -o <organization> [options]
```

#### Description

This command retrieves detailed information about a specific tag in TestFiesta, including its name, description, color, and usage statistics.

#### Arguments and options

* `-i, --id <id>`: Tag ID
* `-t, --token <token>`: TestFiesta API token
* `-u, --url <url>`: TestFiesta API URL
* `-o, --organization <organization>`: Organization handle
* `-v, --verbose`: Enable verbose logging

### `testfiesta tag:update`

Update a tag in TestFiesta

#### Synopsis

```
tacotruck testfiesta tag:update -i <id> -t <token> -u <url> -o <organization> [options]
```

#### Description

This command updates an existing tag in TestFiesta. You can modify the name, description, and color of the tag.

#### Arguments and options

* `-i, --id <id>`: Tag ID
* `-t, --token <token>`: TestFiesta API token
* `-u, --url <url>`: TestFiesta API URL
* `-o, --organization <organization>`: Organization handle
* `-n, --name <name>`: New tag name
* `-d, --description <description>`: New tag description
* `-c, --color <color>`: New tag color (hex code, e.g., #FF5733)
* `-v, --verbose`: Enable verbose logging

### `testfiesta tag:delete`

Delete a tag from TestFiesta

#### Synopsis

```
tacotruck testfiesta tag:delete -i <id> -t <token> -u <url> -o <organization> [options]
```

#### Description

This command deletes a tag from TestFiesta. By default, it will prompt for confirmation before deletion unless the --non-interactive flag is used.

#### Arguments and options

* `-i, --id <id>`: Tag ID
* `-t, --token <token>`: TestFiesta API token
* `-u, --url <url>`: TestFiesta API URL
* `-o, --organization <organization>`: Organization handle
* `-v, --verbose`: Enable verbose logging
* `--non-interactive`: Skip confirmation prompts
