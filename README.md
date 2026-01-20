# Project Overview

This repository contains a collection of personal shell configurations, aliases, and utility scripts designed to enhance a Linux terminal environment. It customizes standard commands like `man`, `git`, and `sudo`, and provides convenient aliases for navigating and managing specific workspaces and applications.

## Key Files

*   **`alias`**: Defines custom shell aliases for common commands and directory navigation. It introduces wrappers for `nano`, `man`, `sudo`, and `git`.
*   **`config`**: The main shell configuration script. It manages SSH agent setup, sets environment variables (e.g., `TZ`, `COURSERA`), customizes the `PS1` prompt, and ensures a `tmux` session is active.
*   **`func`**: Contains shell functions, notably `tmux_activate`, which is called by `config` to handle `tmux` session management.
*   **`bin/`**: This directory holds custom executable scripts that extend or modify the behavior of standard system commands.
    *   **`bin/man_nano`**: A wrapper for the `man` command that opens man pages in `nano` for easier viewing and searching.
    *   **`bin/mygit`**: A `git` wrapper that automatically performs a `git pull origin main --rebase` before any `git push` operation, ensuring the local branch is up-to-date.
    *   **`bin/mysudo`**: A `sudo` wrapper that, for `apt` commands other than `apt update`, first runs `sudo apt update` to ensure package lists are current before executing the requested `apt` command.

## Usage and Installation

To utilize these configurations, you would typically source the `config` file (which in turn uses `alias` and `func`) from your shell's startup file (e.g., `.bashrc`, `.zshrc`).

For example, add the following to your `~/.bashrc` or `~/.zshrc`:

```bash
source /path/to/local/config
```

Ensure the `bin` directory is in your `PATH` environment variable for the custom scripts to be discoverable:

```bash
export PATH="/path/to/local/bin:$PATH"
```

## Development Conventions

The scripts are primarily written in `bash` or `sh` and follow standard shell scripting practices. They focus on practical command-line enhancements and automation for personal use.
