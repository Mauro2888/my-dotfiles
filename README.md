# Installation Guide

This guide explains how to install multiple applications using `brew` and `xargs` on macOS.

## Installing Homebrew

Before starting, you'll need to install Homebrew. Homebrew is a package manager for macOS that simplifies the installation of software.

1. Open Terminal on your Mac (you can find it in Applications > Utilities > Terminal)

2. Install Homebrew by running this command:
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

3. Follow the prompts in the Terminal. You may be asked to enter your Mac password.

4. After installation, add Homebrew to your PATH:

For macOS Intel chips:
```bash
echo 'eval "$(/usr/local/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/usr/local/bin/brew shellenv)"
```

For macOS Apple Silicon (M1/M2):
```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

5. Verify the installation:
```bash
brew --version
```

## Prerequisites

- macOS operating system
- [Homebrew](https://brew.sh/) package manager installed
- A text file (`apps-dev.txt`) containing the list of applications to install

## Setup Instructions

1. Run file named `apps-dev.txt` for dev tools and `apps.txt` for common in your desired directory:

2. Run the batch installation command:

```bash
xargs brew install < apps-dev.txt
```

```bash
xargs brew install < apps.txt
```

## How It Works

The command works as follows:
- `xargs` reads items from standard input and executes a command with those items as arguments
- `<` redirects the contents of `apps-dev.txt` as input
- `brew install` is executed for each line in the file

## Tips

- To check if applications are already installed:
  ```bash
  brew list
  ```

- To update all installed applications:
  ```bash
  brew upgrade
  ```

- To verify if Homebrew is working correctly:
  ```bash
  brew doctor
  ```

## Troubleshooting

If you encounter any issues:

1. Ensure Homebrew is up to date:
```bash
brew update
```

2. Check for any Homebrew issues:
```bash
brew doctor
```

3. Verify file permissions:
```bash
ls -l apps-dev.txt
```