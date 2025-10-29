# Homebrew

#### Prerequisites

* Homebrew package manager installed on your macOS or Linux system

#### Installation Steps

1. Open Terminal
2. Install TacoTruck using this custom Homebrew tap:

```shell
# Add the tap
brew tap testfiesta/tacotruck

# Install TacoTruck
brew install tacotruck 
```

#### Custom Version Installation

To install a specific version:

```sh
curl -fsSL https://raw.githubusercontent.com/testfiesta/tacotruck/main/scripts/install.sh | bash -s -- 1.0.0-beta.27

```

#### Verify Installation

You can verify installation process by running the following command:

```bash
tacotruck --version
```

#### Upgrading CLI

You can simply run the following command to upgrade the CLI:

```sh
tacotruck upgrade
```
