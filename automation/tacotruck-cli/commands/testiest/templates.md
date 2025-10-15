# Templates

### `testfiesta template:create`

Create a new template in TestFiesta

#### Synopsis

```
tacotruck testfiesta template:create -p <project> -n <name> -t <token> -u <url> -o <organization> --content <content> [options]
```

#### Description

This command creates a new template in the specified TestFiesta project. Templates can be used to standardize test case or test run creation.

#### Arguments and options

* `-p, --project <project>`: Project key
* `-n, --name <name>`: Template name
* `-t, --token <token>`: TestFiesta API token
* `-u, --url <url>`: TestFiesta API URL
* `-o, --organization <organization>`: Organization handle
* `--content <content>`: Template content or path to template file
* `-d, --description <description>`: Template description
* `--type <type>`: Template type (test-case, test-run)
* `-v, --verbose`: Enable verbose logging

### `testfiesta template:list`

List templates in TestFiesta

#### Synopsis

```
tacotruck testfiesta template:list -p <project> -t <token> -u <url> -o <organization> [options]
```

#### Description

This command retrieves and displays a list of all templates in the specified TestFiesta project. Results can be filtered by template type and paginated using the limit and offset options.

#### Arguments and options

* `-p, --project <project>`: Project key
* `-t, --token <token>`: TestFiesta API token
* `-u, --url <url>`: TestFiesta API URL
* `-o, --organization <organization>`: Organization handle
* `--type <type>`: Filter by template type (test-case, test-run)
* `-l, --limit <limit>`: Number of items to retrieve (default: 10)
* `--offset <offset>`: Offset for pagination (default: 0)
* `-v, --verbose`: Enable verbose logging

### `testfiesta template:get`

Get a specific template from TestFiesta

#### Synopsis

```
tacotruck testfiesta template:get -p <project> -i <id> -t <token> -u <url> -o <organization> [options]
```

#### Description

This command retrieves detailed information about a specific template in the TestFiesta project. The template content can optionally be saved to a file.

#### Arguments and options

* `-p, --project <project>`: Project key
* `-i, --id <id>`: Template ID
* `-t, --token <token>`: TestFiesta API token
* `-u, --url <url>`: TestFiesta API URL
* `-o, --organization <organization>`: Organization handle
* `--output <path>`: Save template content to file
* `-v, --verbose`: Enable verbose logging

### `testfiesta template:delete`

Delete a template from TestFiesta

#### Synopsis

```
tacotruck testfiesta template:delete -p <project> -i <id> -t <token> -u <url> -o <organization> [options]
```

#### Description

This command deletes a template from the specified TestFiesta project. By default, it will prompt for confirmation before deletion unless the --non-interactive flag is used.

#### Arguments and options

* `-p, --project <project>`: Project key
* `-i, --id <id>`: Template ID
* `-t, --token <token>`: TestFiesta API token
* `-u, --url <url>`: TestFiesta API URL
* `-o, --organization <organization>`: Organization handle
* `-v, --verbose`: Enable verbose logging
* `--non-interactive`: Skip confirmation prompts

You're currently in ask mode, so I can't directly modify any files. If you'd like to implement this updated documentation format, you would need to switch to agent mode or manually apply these changes to your documentation files.
