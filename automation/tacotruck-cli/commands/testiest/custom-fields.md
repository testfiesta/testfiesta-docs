# Custom Fields

### `testfiesta field:create`

Create a new custom field in TestFiesta

#### Synopsis

```
tacotruck testfiesta field:create -p <project> -n <name> --type <type> -t <token> -u <url> -o <organization> [options]
```

#### Description

This command creates a new custom field in the specified TestFiesta project. Custom fields allow you to track additional information about your test cases and can be of various types such as text, number, boolean, select, multiselect, or date.

#### Arguments and options

* `-p, --project <project>`: Project key
* `-n, --name <name>`: Field name
* `--type <type>`: Field type (text, number, boolean, select, multiselect, date)
* `-t, --token <token>`: TestFiesta API token
* `-u, --url <url>`: TestFiesta API URL
* `-o, --organization <organization>`: Organization handle
* `-d, --description <description>`: Field description
* `-r, --required`: Mark field as required
* `--default-value <value>`: Default value for the field
* `--options <options>`: JSON array of options for select/multiselect fields
* `-v, --verbose`: Enable verbose logging

### `testfiesta field:list`

List custom fields in TestFiesta

#### Synopsis

```
tacotruck testfiesta field:list -p <project> -t <token> -u <url> -o <organization> [options]
```

#### Description

This command retrieves and displays a list of all custom fields in the specified TestFiesta project. Results can be paginated using the limit and offset options.

#### Arguments and options

* `-p, --project <project>`: Project key
* `-t, --token <token>`: TestFiesta API token
* `-u, --url <url>`: TestFiesta API URL
* `-o, --organization <organization>`: Organization handle
* `-l, --limit <limit>`: Number of items to retrieve (default: 10)
* `--offset <offset>`: Offset for pagination (default: 0)
* `-v, --verbose`: Enable verbose logging

### `testfiesta field:get`

Get a specific custom field from TestFiesta

#### Synopsis

```
tacotruck testfiesta field:get -p <project> -i <id> -t <token> -u <url> -o <organization> [options]
```

#### Description

This command retrieves detailed information about a specific custom field in the TestFiesta project, including its type, description, required status, default value, and available options if applicable.

#### Arguments and options

* `-p, --project <project>`: Project key
* `-i, --id <id>`: Field ID
* `-t, --token <token>`: TestFiesta API token
* `-u, --url <url>`: TestFiesta API URL
* `-o, --organization <organization>`: Organization handle
* `-v, --verbose`: Enable verbose logging

### `testfiesta field:update`

Update a custom field in TestFiesta

#### Synopsis

```
tacotruck testfiesta field:update -p <project> -i <id> -t <token> -u <url> -o <organization> [options]
```

#### Description

This command updates an existing custom field in the specified TestFiesta project. You can modify the name, description, required status, default value, or options for select/multiselect fields.

#### Arguments and options

* `-p, --project <project>`: Project key
* `-i, --id <id>`: Field ID
* `-t, --token <token>`: TestFiesta API token
* `-u, --url <url>`: TestFiesta API URL
* `-o, --organization <organization>`: Organization handle
* `-n, --name <name>`: New field name
* `-d, --description <description>`: New field description
* `-r, --required`: Mark field as required
* `--default-value <value>`: New default value
* `--options <options>`: New JSON array of options
* `-v, --verbose`: Enable verbose logging

### `testfiesta field:delete`

Delete a custom field from TestFiesta

#### Synopsis

```
tacotruck testfiesta field:delete -p <project> -i <id> -t <token> -u <url> -o <organization> [options]
```

#### Description

This command deletes a custom field from the specified TestFiesta project. By default, it will prompt for confirmation before deletion unless the --non-interactive flag is used.

#### Arguments and options

* `-p, --project <project>`: Project key
* `-i, --id <id>`: Field ID
* `-t, --token <token>`: TestFiesta API token
* `-u, --url <url>`: TestFiesta API URL
* `-o, --organization <organization>`: Organization handle
* `-v, --verbose`: Enable verbose logging
* `--non-interactive`: Skip confirmation prompts
