# Linux/macOS

#### Prerequisites

* curl (pre-installed on most systems)
* bash shell

#### Installation Steps

1. Open Terminal
2. Run the installation script: &#x20;

```sh
curl -fsSL https://testfiesta.com/install-tacotruck-cli.sh | bash
```

#### Custom Version Installation

To install a specific version:

```sh
curl -fsSL https://raw.githubusercontent.com/testfiesta/tacotruck/main/scripts/install.sh | bash -s -- 1.0.0-beta.27

```

#### Verify Installation

After installation, either:

* Restart your terminal, or
* Source your shell configuration file: &#x20;

```sh
  # For bash
  source ~/.bashrc
  # For zsh
  source ~/.zshrc
```

Then verify the installation:

```sh
tacotruck --version
```

#### Upgrading CLI

You can simply run the following command to upgrade the CLI:

```sh
tacotruck upgrade
```
