### AE5 Command Line Tool

[![Travis Status](https://travis-ci.com/Anaconda-Platform/ae5-tools.svg?branch=master)](https://travis-ci.com/Anaconda-Platform/ae5-tools) &nbsp; [![Anaconda-Server Badge](https://anaconda.org/ae5-admin/ae5-tools/badges/latest_release_date.svg)](https://anaconda.org/ae5-admin/ae5-tools) &nbsp; [![Anaconda-Server Badge](https://anaconda.org/ae5-admin/ae5-tools/badges/version.svg)](https://anaconda.org/ae5-admin/ae5-tools)

This tool uses AE5's internal APIs to do cool things, including:

- obtaining information about projects, sessions, deployments, jobs, and runs
- starting and stopping sessions and deployments
- uploading and downloading projects

More to come. The intent is also to make it possible to allow packages to plug into the tool and provide additional commands.

There is already a fair amount of inline help, so type `ae5 --help` to get started.

#### General capabilities

- Adoption of a standard project identifier format `<owner>/<name>/<id>:<revision>`, with convenient defaults:
    - `<id>` can usually be omitted, leaving `<owner>/<name>:<revision>`
    - `<revision>` can be omitted in most contexts, with the latest revision considered by default; the latest revision can also be specified with `:latest`, Docker-style
    - `<owner>` can be also be omitted, allowing projects to be specified solely by `<name>` or `<id>`. The ambiguity of these choices is resolved by assuming no project will have a name matching the `<id>` format `a[0-3]-[0-9a-f]{32}`. 
- Output formats include terminal-formatted text tables, CSV files, and JSON.
- All tabular output can be filtered by simple field matching, and sorted by columns.
- Hostname, username, and password can be specified as command-line options or as environment variables, to facilitate programmatic use.
- Login sessions are persisted to `~/.ae5`, so that multiple commands can be issued without having to re-enter passwords.
- Keycloak impersonation allows administrators to run commands on behalf of them.
- A REPL mode provided by [click-repl](https://github.com/click-contrib/click-repl) be entered by typing `ae5` with no positional arguments, enabling multiple commands to be entered in a single session, with autocompletion, inline help, and persistent history.

#### Command Tree

- Composite commands:
    - `account`: `list`
    - `deployment`: `collaborators`, `endpoints`, `info`, `list`, `open`, `patch`, `start`, `stop`
    - `job`: `info`, `list`, `stop`
    - `project`: `activity`, `collaborators`, `delete`, `deploy`, `deployments`, `download`, `info`, `jobs`, `list`, `patch`, `runs`, `sample-info`, `samples`, `status`, `upload`
    - `revision`: `download`, `info`, `list`
    - `run`: `info`, `list`, `stop`
    - `session`: `info`, `list`, `open`, `start`, `stop`
    - `user`: `info`, `list`
- Simple commands: `call`, `login`, `logout`
- Login options: `--hostname`, `--username`, `--admin-username`, `--admin-hostname`, `--impersonate`
- Output format options: `--format`, `--filter`, `--columns`, `--sort`, `--width`, `--wide`, `--no-header`
- Help options: `--help-format`, `--help-filter`, `--help-login`, `--help`

