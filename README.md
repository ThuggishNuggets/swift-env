# About this project
A Swift Language and Toolchain Installer and Environment switcher/selector for Ubuntu 18.04 LTS. You can think of it a bit like `rbenv`.
- Quickly install any existing public release version of the Swift Language and Toolchain using just the version number (e.g. `swift install 5.2.4`)
- Quickly switch between any installed Swift versions with a single command (e.g. `swift env 4.2.1`)
- Supports multi-user server environments, installations of Swift are shared for all users, but environments selections are per-user, no need to worry about another user screwing up your environment settings!
- Can be easily modified to support Ubuntu 20.04 LTS by editing the download URLs in `swift-install` to match.

# Installation
- Clone repo and copy files `swift-env`, `swift-install` and, optionally, `swift-reset` to `/usr/local/bin` (for shared server setups, you can change this to whatever you want, but you'll be responsible for updating the respective scripts to point to the correct location)
- Add execute privileges to files `swift-env`, `swift-install` and, optionally, `swift-reset` using `sudo chmod +x /usr/local/bin/<filename>`

# Command: `swift-install`
Downloads and installs the version of the Swift language and toolchain matching the version argument supplied to the command. After installation, this command automatically changes the current environment to the newly installed version using `swift env <version>`.

This command installs Swift versions for all users, while changing the currently selected Swift environment is a per-user setting utilizing symlinks in the user's `home` directory so multiple simultaneous users of the same server will not interfere with one another's environment settings.

```
Usage: swift install <version>

Examples:
swift install 4.2.1
swift install 5.2.4
```

# Command: `swift-env`
Changes the current sym-linked Swift environments to the supplied version. Prompts to use `swift install <version>` if and installation matching the version argument cannot be found. Changing the currently selected Swift environment is a per-user setting utilizing symlinks in the user's `home` directory so multiple simultaneous users of the same server will not interfere with one another's environment settings.

```
Usage: swift env <version>

Examples:
swift env 4.2.1
swift env 5.2.4
```

# Command: `swift-reset`
DEV COMMAND. Don't use this unless you've read the script and understand what it does first. This command was created to aid in the development and testing of the `swift-env` and `swift-install` commands. It accepts a Swift version and attempts to remove it and any symlinks to it, after which it opens `.bashrc` in the default editor application so that you can edit the `PATH` and environment variables manually.

```
Usage: swift reset <version>

Example:
swift reset 4.2.1
```
