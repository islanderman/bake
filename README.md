# bake - macOS System Update Tool

`bake` is a command-line tool designed to streamline system updates and package management on macOS. It automates updates for macOS software, Homebrew packages, and Mac App Store apps, optimizes Homebrew git repositories, and provides features to manage backed-up package lists.

## Features

- **System Updates**: Updates macOS software, Homebrew formulas, casks, and MAS apps in a single command.
- **Git Optimization**: Optimizes Homebrew git repositories weekly or on demand.
- **Package Backup**: Maintains a backup of installed packages at `~/.config/bake/packages.json`.
- **Package Management**: Lists backed-up packages and generates installation commands.
- **Logging**: Logs all operations to `~/.bake/log/` with a 10-day retention period.
- **Verbose Mode**: Detailed output with log file location display.
- **Shell Completion**: Optional autocompletion support for bash, zsh, and fish.

## Installation

1. **Clone the Repository**:

   ```bash
   git clone https://github.com/yourusername/bake.git
   cd bake
   ```

2. Install Dependencies:

   ```bash
   pip3 install -r requirements.txt --user
   ```

3. Set Up the Script:

   ```bash
   chmod +x bake.py
    sudo mv bake.py /usr/local/bin/bake
   ```

4. Prerequisites:
  - Install [Homebrew](https://brew.sh/)

  ```bash
  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
  ```

  - Install [Mas CLI](https://github.com/mas-cli/mas)

  ```bash
  brew install mas
  ```

  - *Optional: Enable Shell Completion:*
    1. Install `argcomplete`:

  ```bash
    pip3 install argcomplete --user
  ```
    2. Generate and source completion script (ex. for `bash`):

  ```bash
    bake --completion bash >> ~/.bashrc
    source ~/.bashrc
  ```

## Usage

```bash
    # Show version
    bake

    # Update system
    bake up [-v/--verbose] [-f/--force]

    # Show timestamps
    bake show timestamp package
    bake show timestamp optimization

    # List backed-up packages
    bake show packages

    # Generate installation commands
    bake show install

    # Display license
    bake --license

    # Generate shell completion script
    bake --completion [bash|zsh|fish]
```

### Commands
  - `up`: Performs a full system update.
    - `-v/--verbose`: Show detailed output and log file location.
    - `-f/--force`: Force git repository optimization.
  - `show`:
      - `timestamp package`: Show last package backup timestamp.
      - `timestamp optimization`: Show last git optimization timestamp.
      - `packages`: List all packages from the backup.
      - `install`: Generate installation commands for backed-up packages.
### Options
  - `-v/--version`: Display version number.
  - `--completion`: Generate shell completion script.
  - `--license`: Display MIT license and copyright.

## Examples
  - Update system with verbose output:

  ```bash
    bake up -v
  ```

  - List backed-up packages:

  ```bash
    bake show packages
  ```

  - Generate installation commands:

  ```bash
    bake show install
  ```

## Configuration
  - **Package Backup**: Stored at ~/.config/bake/packages.json.
  - **Git Optimization Tracking**: Stored at ~/.cache/bake/last_optimization.json.
  - **Logs**: Stored at ~/.bake/log/ with a 10-day retention.

## Requirements
  - Python 3.6+
  - macOS
  - Homebrew
  - MAS CLI
  - Dependencies (see requirements.txt):

  ```bash
    pip3 install colorama>=0.4.6 tqdm>=4.66.5 argcomplete>=3.5.0 --user
  ```

## Contributing
  1. Fork the repository.
  2. Create a feature branch (git checkout -b feature/new-feature).
  3. Commit changes (git commit -am 'Add new feature').
  4. Push to the branch (git push origin feature/new-feature).
  5. Create a pull request.

## License
MIT License - see bake --license for details.

### Author
islanderman - Copyright (c) 2025
