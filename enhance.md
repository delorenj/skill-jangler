I need you to enhance the SKILL.md file for the mise-task-managing skill.

CURRENT SKILL.MD:
------------------------------------------------------------
---
name: mise-task-managing
description: Use this skill when creating tasks to encapsulate complex devops workflows (packaging releases, managing dev environments, performing database operations), provide a central hub for all dev commands and invocables (wrap scripts, cli commands, db queries, one-liners, etc), and any other devops related services.
---

# Mise-Task-Managing Skill

Comprehensive assistance with mise-task-managing development, generated from official documentation.

## When to Use This Skill

This skill should be triggered when:
- Working with mise-task-managing
- Asking about mise-task-managing features or APIs
- Implementing mise-task-managing solutions
- Debugging mise-task-managing code
- Learning mise-task-managing best practices

## Quick Reference

### Common Patterns

**Pattern 1:** On this pagemise unset ​Usage: mise unset [-f --file <FILE>] [-g --global] [ENV_KEY]…Source code: src/cli/unset.rsRemove environment variable(s) from the config file.By default, this command modifies mise.toml in the current directory.Arguments ​[ENV_KEY]… ​Environment variable(s) to remove e.g.: NODE_ENVFlags ​-f --file <FILE> ​Specify a file to use instead of mise.toml-g --global ​Use the global config fileExamples:# Remove NODE_ENV from the current directory's config $ mise unset NODE_ENV # Remove NODE_ENV from the global config $ mise unset NODE_ENV -g Edit this pageLast updated: PagerPrevious pagemise uninstallNext pagemise unuse

```
mise unset
```

**Pattern 2:** On this pagemise plugins ​Usage: mise plugins [FLAGS] <SUBCOMMAND>Aliases: pSource code: src/cli/plugins/mod.rsManage pluginsFlags ​-c --core ​The built-in plugins only Normally these are not shown--user ​List installed pluginsThis is the default behavior but can be used with --core to show core and user plugins-u --urls ​Show the git url for each plugin e.g.: https://github.com/asdf-vm/asdf-nodejs.gitSubcommands ​mise plugins install [FLAGS] [NEW_PLUGIN] [GIT_URL]mise plugins link [-f --force] <NAME> [DIR]mise plugins ls [-u --urls]mise plugins ls-remote [-u --urls] [--only-names]mise plugins uninstall [-p --purge] [-a --all] [PLUGIN]…mise plugins update [-j --jobs <JOBS>] [PLUGIN]… Edit this pageLast updated: PagerPrevious pagemise outdatedNext pagemise plugins install

```
mise plugins
```

**Pattern 3:** On this pagemise run ​Usage: mise run [FLAGS]Aliases: rSource code: src/cli/run.rsRun task(s)This command will run a tasks, or multiple tasks in parallel. Tasks may have dependencies on other tasks or on source files. If source is configured on a tasks, it will only run if the source files have changed.Tasks can be defined in mise.toml or as standalone scripts. In mise.toml, tasks take this form:[tasks.build] run = "npm run build" sources = ["src/**/*.ts"] outputs = ["dist/**/*.js"]Alternatively, tasks can be defined as standalone scripts. These must be located in mise-tasks, .mise-tasks, .mise/tasks, mise/tasks or .config/mise/tasks. The name of the script will be the name of the tasks.$ cat .mise/tasks/build&lt;&lt;EOF #!/usr/bin/env bash npm run build EOF $ mise run buildFlags ​--no-cache ​Do not use cache on remote tasks-C --cd <CD> ​Change to this directory before executing the command-c --continue-on-error ​Continue running tasks even if one fails-n --dry-run ​Don't actually run the tasks(s), just print them in order of execution-f --force ​Force the tasks to run even if outputs are up to date-s --shell <SHELL> ​Shell to use to run toml tasksDefaults to sh -c -o errexit -o pipefail on unix, and cmd /c on Windows Can also be set with the setting MISE_UNIX_DEFAULT_INLINE_SHELL_ARGS or MISE_WINDOWS_DEFAULT_INLINE_SHELL_ARGS Or it can be overridden with the shell property on a task.-t --tool… <TOOL@VERSION> ​Tool(s) to run in addition to what is in mise.toml files e.g.: node@20 python@3.10-j --jobs <JOBS> ​Number of tasks to run in parallel [default: 4] Configure with jobs config or MISE_JOBS env var-r --raw ​Read/write directly to stdin/stdout/stderr instead of by line Redactions are not applied with this option Configure with raw config or MISE_RAW env var-S --silent ​Don't show any output except for errors--timeout <TIMEOUT> ​Timeout for the task to complete e.g.: 30s, 5m--no-timings ​Hides elapsed time after each task completesDefault to always hide with MISE_TASK_TIMINGS=0-q --quiet ​Don't show extra output-o --output <OUTPUT> ​Change how tasks information is output when running tasksprefix - Print stdout/stderr by line, prefixed with the task's labelinterleave - Print directly to stdout/stderr instead of by linereplacing - Stdout is replaced each time, stderr is printed as istimed - Only show stdout lines if they are displayed for more than 1 secondkeep-order - Print stdout/stderr by line, prefixed with the task's label, but keep the order of the outputquiet - Don't show extra outputsilent - Don't show any output including stdout and stderr from the task except for errorsExamples:# Runs the "lint" tasks. This needs to either be defined in mise.toml # or as a standalone script. See the project README for more information. $ mise run lint # Forces the "build" tasks to run even if its sources are up-to-date. $ mise run build --force # Run "test" with stdin/stdout/stderr all connected to the current terminal. # This forces `--jobs=1` to prevent interleaving of output. $ mise run test --raw # Runs the "lint", "test", and "check" tasks in parallel. $ mise run lint ::: test ::: check # Execute multiple tasks each with their own arguments. $ mise tasks cmd1 arg1 arg2 ::: cmd2 arg1 arg2 Edit this pageLast updated: PagerPrevious pagemise reshimNext pagemise search

```
mise run
```

**Pattern 4:** On this pagemise settings ​Usage: mise settings [FLAGS] [SETTING] [VALUE] <SUBCOMMAND>Source code: src/cli/settings/mod.rsShow current settingsThis is the contents of ~/.config/mise/config.tomlNote that aliases are also stored in this file but managed separately with mise aliasesArguments ​[SETTING] ​Name of setting[VALUE] ​Setting value to setGlobal Flags ​-l --local ​Use the local config file instead of the global oneFlags ​-a --all ​List all settings-J --json ​Output in JSON format--json-extended ​Output in JSON format with sources-T --toml ​Output in TOML formatSubcommands ​mise settings add [-l --local] <SETTING> <VALUE>mise settings get [-l --local] <SETTING>mise settings ls [FLAGS] [SETTING]mise settings set [-l --local] <SETTING> <VALUE>mise settings unset [-l --local] <KEY>Examples:# list all settings $ mise settings # get the value of the setting "always_keep_download" $ mise settings always_keep_download # set the value of the setting "always_keep_download" to "true" $ mise settings always_keep_download=true # set the value of the setting "node.mirror_url" to "https://npm.taobao.org/mirrors/node" $ mise settings node.mirror_url https://npm.taobao.org/mirrors/node Edit this pageLast updated: PagerPrevious pagemise setNext pagemise settings add

```
mise settings
```

**Pattern 5:** On this pagemise ​Usage: mise [FLAGS] [TASK] <SUBCOMMAND>Usage: mise [FLAGS] [TASK] <SUBCOMMAND>Arguments ​[TASK] ​Task to run.Shorthand for mise task run <TASK>.Global Flags ​-C --cd <DIR> ​Change directory before running command-E --env… <ENV> ​Set the environment for loading mise.<ENV>.toml-j --jobs <JOBS> ​How many jobs to run in parallel [default: 8]--raw ​Read/write directly to stdin/stdout/stderr instead of by line-y --yes ​Answer yes to all confirmation prompts-q --quiet ​Suppress non-error messages--silent ​Suppress all task output and mise non-error messages-v --verbose… ​Show extra output (use -vv for even more)Flags ​--output <OUTPUT> ​--no-config ​Do not load any config filesCan also use MISE_NO_CONFIG=1Subcommands ​mise activate [FLAGS] [SHELL_TYPE]mise alias [-p --plugin <PLUGIN>] [--no-header] <SUBCOMMAND>mise alias get <PLUGIN> <ALIAS>mise alias ls [--no-header] [TOOL]mise alias set <ARGS>…mise alias unset <PLUGIN> [ALIAS]mise backends <SUBCOMMAND>mise backends lsmise bin-paths [TOOL@VERSION]…mise cache <SUBCOMMAND>mise cache clear [PLUGIN]…mise cache pathmise cache prune [--dry-run] [-v --verbose…] [PLUGIN]…mise completion [--include-bash-completion-lib] [SHELL]mise config [FLAGS] <SUBCOMMAND>mise config generate [-t --tool-versions <TOOL_VERSIONS>] [-o --output <OUTPUT>]mise config get [-f --file <FILE>] [KEY]mise config ls [FLAGS]mise config set [-f --file <FILE>] [-t --type <TYPE>] <KEY> <VALUE>mise deactivatemise doctor [-J --json] <SUBCOMMAND>mise doctor path [-f --full]mise en [-s --shell <SHELL>] [DIR]mise env [FLAGS] [TOOL@VERSION]…mise exec [FLAGS] [TOOL@VERSION]… [-- COMMAND]…mise fmt [FLAGS]mise generate <SUBCOMMAND>mise generate bootstrap [FLAGS]mise generate config [-t --tool-versions <TOOL_VERSIONS>] [-o --output <OUTPUT>]mise generate devcontainer [FLAGS]mise generate git-pre-commit [FLAGS]mise generate github-action [FLAGS]mise generate task-docs [FLAGS]mise generate task-stubs [-m --mise-bin <MISE_BIN>] [-d --dir <DIR>]mise generate tool-stub [FLAGS] <OUTPUT>mise implode [--config] [-n --dry-run]mise install [FLAGS] [TOOL@VERSION]…mise install-into <TOOL@VERSION> <PATH>mise latest [-i --installed] <TOOL@VERSION>mise link [-f --force] <TOOL@VERSION> <PATH>mise lock [FLAGS] [TOOL]…mise ls [FLAGS] [INSTALLED_TOOL]…mise ls-remote [--all] [TOOL@VERSION] [PREFIX]mise mcpmise outdated [FLAGS] [TOOL@VERSION]…mise plugins [FLAGS] <SUBCOMMAND>mise plugins install [FLAGS] [NEW_PLUGIN] [GIT_URL]mise plugins link [-f --force] <NAME> [DIR]mise plugins ls [-u --urls]mise plugins ls-remote [-u --urls] [--only-names]mise plugins uninstall [-p --purge] [-a --all] [PLUGIN]…mise plugins update [-j --jobs <JOBS>] [PLUGIN]…mise prune [FLAGS] [INSTALLED_TOOL]…mise registry [-b --backend <BACKEND>] [--hide-aliased] [NAME]mise reshim [-f --force]mise run [FLAGS]mise search [FLAGS] [NAME]mise self-update [FLAGS] [VERSION]mise set [FLAGS] [ENV_VAR]…mise settings [FLAGS] [SETTING] [VALUE] <SUBCOMMAND>mise settings add [-l --local] <SETTING> <VALUE>mise settings get [-l --local] <SETTING>mise settings ls [FLAGS] [SETTING]mise settings set [-l --local] <SETTING> <VALUE>mise settings unset [-l --local] <KEY>mise shell [FLAGS] <TOOL@VERSION>…mise sync <SUBCOMMAND>mise sync node [FLAGS]mise sync python [--pyenv] [--uv]mise sync ruby [--brew]mise tasks [FLAGS] [TASK] <SUBCOMMAND>mise tasks add [FLAGS] <TASK> [-- RUN]…mise tasks deps [--hidden] [--dot] [TASKS]…mise tasks edit [-p --path] <TASK>mise tasks info [-J --json] <TASK>mise tasks ls [FLAGS]mise tasks run [FLAGS] [TASK] [ARGS]…mise test-tool [FLAGS] [TOOLS]…mise tool [FLAGS] <TOOL>mise tool-stub <FILE> [ARGS]…mise trust [FLAGS] [CONFIG_FILE]mise uninstall [-a --all] [-n --dry-run] [INSTALLED_TOOL@VERSION]…mise unset [-f --file <FILE>] [-g --global] [ENV_KEY]…mise unuse [FLAGS] <INSTALLED_TOOL@VERSION>…mise upgrade [FLAGS] [TOOL@VERSION]…mise use [FLAGS] [TOOL@VERSION]…mise version [-J --json]mise watch [FLAGS] [TASK] [ARGS]…mise where <TOOL@VERSION>mise which [FLAGS] [BIN_NAME] Edit this pageLast updated: PagerPrevious pageCache BehaviorNext pagemise activate

```
mise
```

**Pattern 6:** On this pagemise tasks add ​Usage: mise tasks add [FLAGS] <TASK> [-- RUN]…Source code: src/cli/tasks/add.rsCreate a new taskArguments ​<TASK> ​Tasks name to add[-- RUN]… ​Flags ​--description <DESCRIPTION> ​Description of the task-a --alias… <ALIAS> ​Other names for the task--depends-post… <DEPENDS_POST> ​Dependencies to run after the task runs-w --wait-for… <WAIT_FOR> ​Wait for these tasks to complete if they are to run-D --dir <DIR> ​Run the task in a specific directory-H --hide ​Hide the task from mise task and completions-r --raw ​Directly connect stdin/stdout/stderr-s --sources… <SOURCES> ​Glob patterns of files this task uses as input--outputs… <OUTPUTS> ​Glob patterns of files this task creates, to skip if they are not modified--shell <SHELL> ​Run the task in a specific shell-q --quiet ​Do not print the command before running--silent ​Do not print the command or its output-d --depends… <DEPENDS> ​Add dependencies to the task--run-windows <RUN_WINDOWS> ​Command to run on windows-f --file ​Create a file task instead of a toml taskExamples:mise task add pre-commit --depends "test" --depends "render" -- echo pre-commit Edit this pageLast updated: PagerPrevious pagemise tasksNext pagemise tasks deps

```
mise tasks add
```

**Pattern 7:** On this pagemise fmt ​Usage: mise fmt [FLAGS]Source code: src/cli/fmt.rsFormats mise.tomlSorts keys and cleans up whitespace in mise.tomlFlags ​-a --all ​Format all files from the current directory-c --check ​Check if the configs are formatted, no formatting is done-s --stdin ​Read config from stdin and write its formatted version into stdoutExamples:mise fmt Edit this pageLast updated: PagerPrevious pagemise execNext pagemise generate

```
mise fmt
```

**Pattern 8:** On this pagemise ls ​Usage: mise ls [FLAGS] [INSTALLED_TOOL]…Aliases: listSource code: src/cli/ls.rsList installed and active tool versionsThis command lists tools that mise "knows about". These may be tools that are currently installed, or those that are in a config file (active) but may or may not be installed.It's a useful command to get the current state of your tools.Arguments ​[INSTALLED_TOOL]… ​Only show tool versions from [TOOL]Flags ​-c --current ​Only show tool versions currently specified in a mise.toml-g --global ​Only show tool versions currently specified in the global mise.toml-l --local ​Only show tool versions currently specified in the local mise.toml-i --installed ​Only show tool versions that are installed (Hides tools defined in mise.toml but not installed)--outdated ​Display whether a version is outdated-J --json ​Output in JSON format-m --missing ​Display missing tool versions--prefix <PREFIX> ​Display versions matching this prefix--prunable ​List only tools that can be pruned with mise prune--no-header ​Don't display headersExamples:$ mise ls node 20.0.0 ~/src/myapp/.tool-versions latest python 3.11.0 ~/.tool-versions 3.10 python 3.10.0 $ mise ls --current node 20.0.0 ~/src/myapp/.tool-versions 20 python 3.11.0 ~/.tool-versions 3.11.0 $ mise ls --json { "node": [ { "version": "20.0.0", "install_path": "/Users/jdx/.mise/installs/node/20.0.0", "source": { "type": "mise.toml", "path": "/Users/jdx/mise.toml" } } ], "python": [...] } Edit this pageLast updated: PagerPrevious pagemise lockNext pagemise ls-remote

```
mise ls
```

## Reference Files

This skill includes comprehensive documentation in `references/`:

- **cli_reference.md** - Cli Reference documentation
- **configuration.md** - Configuration documentation
- **dev_tools.md** - Dev Tools documentation
- **environments.md** - Environments documentation
- **getting_started.md** - Getting Started documentation
- **tasks.md** - Tasks documentation

Use `view` to read specific reference files when detailed information is needed.

## Working with This Skill

### For Beginners
Start with the getting_started or tutorials reference files for foundational concepts.

### For Specific Features
Use the appropriate category reference file (api, guides, etc.) for detailed information.

### For Code Examples
The quick reference section above contains common patterns extracted from the official docs.

## Resources

### references/
Organized documentation extracted from official sources. These files contain:
- Detailed explanations
- Code examples with language annotations
- Links to original documentation
- Table of contents for quick navigation

### scripts/
Add helper scripts here for common automation tasks.

### assets/
Add templates, boilerplate, or example projects here.

## Notes

- This skill was automatically generated from official documentation
- Reference files preserve the structure and examples from source docs
- Code examples include language detection for better syntax highlighting
- Quick reference patterns are extracted from common usage examples in the docs

## Updating

To refresh this skill with updated documentation:
1. Re-run the scraper with the same configuration
2. The skill will be rebuilt with the latest information

------------------------------------------------------------

REFERENCE DOCUMENTATION:
------------------------------------------------------------

## cli_reference.md
# Mise-Task-Managing - Cli Reference

**Pages:** 45

---

## mise plugins ​

**URL:** https://mise.jdx.dev/cli/plugins.html

**Contents:**
- mise plugins ​
- Flags ​
  - -c --core ​
  - --user ​
  - -u --urls ​
- Subcommands ​

The built-in plugins only Normally these are not shown

List installed plugins

This is the default behavior but can be used with --core to show core and user plugins

Show the git url for each plugin e.g.: https://github.com/asdf-vm/asdf-nodejs.git

---

## mise ​

**URL:** https://mise.jdx.dev/cli/

**Contents:**
- mise ​
- Arguments ​
  - [TASK] ​
- Global Flags ​
  - -C --cd <DIR> ​
  - -E --env… <ENV> ​
  - -j --jobs <JOBS> ​
  - --raw ​
  - -y --yes ​
  - -q --quiet ​

Usage: mise [FLAGS] [TASK] <SUBCOMMAND>

Shorthand for mise task run <TASK>.

Change directory before running command

Set the environment for loading mise.<ENV>.toml

How many jobs to run in parallel [default: 8]

Read/write directly to stdin/stdout/stderr instead of by line

Answer yes to all confirmation prompts

Suppress non-error messages

Suppress all task output and mise non-error messages

Show extra output (use -vv for even more)

Do not load any config files

Can also use MISE_NO_CONFIG=1

---

## mise plugins link ​

**URL:** https://mise.jdx.dev/cli/plugins/link.html

**Contents:**
- mise plugins link ​
- Arguments ​
  - <NAME> ​
  - [DIR] ​
- Flags ​
  - -f --force ​

Symlinks a plugin into mise

This is used for developing a plugin.

The name of the plugin e.g.: node, ruby

The local path to the plugin e.g.: ./mise-node

Overwrite existing plugin

**Examples:**

Example 1 (unknown):
```unknown
# essentially just `ln -s ./mise-node ~/.local/share/mise/plugins/node`
$ mise plugins link node ./mise-node

# infer plugin name as "node"
$ mise plugins link ./mise-node
```

---

## mise uninstall ​

**URL:** https://mise.jdx.dev/cli/uninstall.html

**Contents:**
- mise uninstall ​
- Arguments ​
  - [INSTALLED_TOOL@VERSION]… ​
- Flags ​
  - -a --all ​
  - -n --dry-run ​

Removes installed tool versions

This only removes the installed version, it does not modify mise.toml.

Delete all installed versions

Do not actually delete anything

**Examples:**

Example 1 (unknown):
```unknown
# will uninstall specific version
$ mise uninstall node@18.0.0

# will uninstall the current node version (if only one version is installed)
$ mise uninstall node

# will uninstall all installed versions of node
$ mise uninstall --all node@18.0.0 # will uninstall all node versions
```

---

## mise generate tool-stub ​

**URL:** https://mise.jdx.dev/cli/generate/tool-stub.html

**Contents:**
- mise generate tool-stub ​
- Arguments ​
  - <OUTPUT> ​
- Flags ​
  - --version <VERSION> ​
  - -u --url <URL> ​
  - --platform-url… <PLATFORM_URL> ​
  - --platform-bin… <PLATFORM_BIN> ​
  - -b --bin <BIN> ​
  - --skip-download ​

Generate a tool stub for HTTP-based tools

This command generates tool stubs that can automatically download and execute tools from HTTP URLs. It can detect checksums, file sizes, and binary paths automatically by downloading and analyzing the tool.

When generating stubs with platform-specific URLs, the command will append new platforms to existing stub files rather than overwriting them. This allows you to incrementally build cross-platform tool stubs.

Output file path for the tool stub

URL for downloading the tool

Example: https://github.com/owner/repo/releases/download/v2.0.0/tool-linux-x64.tar.gz

Platform-specific URLs in the format platform:url or just url (auto-detect platform)

When the output file already exists, new platforms will be appended to the existing platforms table. Existing platform URLs will be updated if specified again.

If only a URL is provided (without platform:), the platform will be automatically detected from the URL filename.

Examples: --platform-url linux-x64:https://... --platform-url https://nodejs.org/dist/v22.17.1/node-v22.17.1-darwin-arm64.tar.gz

Platform-specific binary paths in the format platform:path

Examples: --platform-bin windows-x64:tool.exe --platform-bin linux-x64:bin/tool

Binary path within the extracted archive

If not specified and the archive is downloaded, will auto-detect the most likely binary

Skip downloading for checksum and binary path detection (faster but less informative)

Fetch checksums and sizes for an existing tool stub file

This reads an existing stub file and fills in any missing checksum/size fields by downloading the files. URLs must already be present in the stub.

HTTP backend type to use

**Examples:**

Example 1 (unknown):
```unknown
Generate a tool stub for a single URL:
$ mise generate tool-stub ./bin/gh --url "https://github.com/cli/cli/releases/download/v2.336.0/gh_2.336.0_linux_amd64.tar.gz"

Generate a tool stub with platform-specific URLs:
$ mise generate tool-stub ./bin/rg \
    --platform-url linux-x64:https://github.com/BurntSushi/ripgrep/releases/download/14.0.3/ripgrep-14.0.3-x86_64-unknown-linux-musl.tar.gz \
    --platform-url darwin-arm64:https://github.com/BurntSushi/ripgrep/releases/download/14.0.3/ripgrep-14.0.3-aarch64-apple-darwin.tar.gz

Append additional platforms to an existing stub:
$ mise generate tool-stub ./bin/rg \
    --platform-url linux-x64:https://example.com/rg-linux.tar.gz
$ mise generate tool-stub ./bin/rg \
    --platform-url darwin-arm64:https://example.com/rg-darwin.tar.gz
# The stub now contains both platforms

Use auto-detection for platform from URL:
$ mise generate tool-stub ./bin/node \
    --platform-url https://nodejs.org/dist/v22.17.1/node-v22.17.1-darwin-arm64.tar.gz
# Platform 'macos-arm64' will be auto-detected from the URL

Generate with platform-specific binary paths:
$ mise generate tool-stub ./bin/tool \
    --platform-url linux-x64:https://example.com/tool-linux.tar.gz \
    --platform-url windows-x64:https://example.com/tool-windows.zip \
    --platform-bin windows-x64:tool.exe

Generate without downloading (faster):
$ mise generate tool-stub ./bin/tool --url "https://example.com/tool.tar.gz" --skip-download

Fetch checksums for an existing stub:
$ mise generate tool-stub ./bin/jq --fetch
# This will read the existing stub and download files to fill in any missing checksums/sizes
```

---

## mise sync ruby ​

**URL:** https://mise.jdx.dev/cli/sync/ruby.html

**Contents:**
- mise sync ruby ​
- Flags ​
  - --brew ​

Symlinks all ruby tool versions from an external tool into mise

Get tool versions from Homebrew

**Examples:**

Example 1 (unknown):
```unknown
brew install ruby
mise sync ruby --brew
mise use -g ruby - Use the latest version of Ruby installed by Homebrew
```

---

## mise plugins ls ​

**URL:** https://mise.jdx.dev/cli/plugins/ls.html

**Contents:**
- mise plugins ls ​
- Flags ​
  - -u --urls ​

List installed plugins

Can also show remotely available plugins to install.

Show the git url for each plugin e.g.: https://github.com/asdf-vm/asdf-nodejs.git

**Examples:**

Example 1 (unknown):
```unknown
$ mise plugins ls
node
ruby

$ mise plugins ls --urls
node    https://github.com/asdf-vm/asdf-nodejs.git
ruby    https://github.com/asdf-vm/asdf-ruby.git
```

---

## mise doctor path ​

**URL:** https://mise.jdx.dev/cli/doctor/path.html

**Contents:**
- mise doctor path ​
- Flags ​
  - -f --full ​

Print the current PATH entries mise is providing

Print all entries including those not provided by mise

**Examples:**

Example 1 (unknown):
```unknown
Get the current PATH entries mise is providing
$ mise path
/home/user/.local/share/mise/installs/node/24.0.0/bin
/home/user/.local/share/mise/installs/rust/1.90.0/bin
/home/user/.local/share/mise/installs/python/3.10.0/bin
```

---

## mise sync node ​

**URL:** https://mise.jdx.dev/cli/sync/node.html

**Contents:**
- mise sync node ​
- Flags ​
  - --brew ​
  - --nvm ​
  - --nodenv ​

Symlinks all tool versions from an external tool into mise

For example, use this to import all Homebrew node installs into mise

This won't overwrite any existing installs but will overwrite any existing symlinks

Get tool versions from Homebrew

Get tool versions from nvm

Get tool versions from nodenv

**Examples:**

Example 1 (unknown):
```unknown
brew install node@18 node@20
mise sync node --brew
mise use -g node@18 - uses Homebrew-provided node
```

---

## mise implode ​

**URL:** https://mise.jdx.dev/cli/implode.html

**Contents:**
- mise implode ​
- Flags ​
  - --config ​
  - -n --dry-run ​

Removes mise CLI and all related data

Skips config directory by default.

Also remove config directory

List directories that would be removed without actually removing them

---

## mise plugins install ​

**URL:** https://mise.jdx.dev/cli/plugins/install.html

**Contents:**
- mise plugins install ​
- Arguments ​
  - [NEW_PLUGIN] ​
  - [GIT_URL] ​
- Flags ​
  - -f --force ​
  - -a --all ​
  - -v --verbose… ​
  - -j --jobs <JOBS> ​

note that mise automatically can install plugins when you install a tool e.g.: mise install node@20 will autoinstall the node plugin

This behavior can be modified in ~/.config/mise/config.toml

The name of the plugin to install e.g.: node, ruby Can specify multiple plugins: mise plugins install node ruby python

The git url of the plugin

Reinstall even if plugin exists

Install all missing plugins This will only install plugins that have matching shorthands. i.e.: they don't need the full git repo url

Show installation output

Number of jobs to run in parallel

**Examples:**

Example 1 (unknown):
```unknown
# install the poetry via shorthand
$ mise plugins install poetry

# install the poetry plugin using a specific git url
$ mise plugins install poetry https://github.com/mise-plugins/mise-poetry.git

# install the poetry plugin using the git url only
# (poetry is inferred from the url)
$ mise plugins install https://github.com/mise-plugins/mise-poetry.git

# install the poetry plugin using a specific ref
$ mise plugins install poetry https://github.com/mise-plugins/mise-poetry.git#11d0c1e
```

---

## mise backends ls ​

**URL:** https://mise.jdx.dev/cli/backends/ls.html

**Contents:**
- mise backends ls ​

List built-in backends

**Examples:**

Example 1 (unknown):
```unknown
$ mise backends ls
aqua
asdf
cargo
core
dotnet
gem
go
npm
pipx
spm
ubi
vfox
```

---

## mise alias set ​

**URL:** https://mise.jdx.dev/cli/alias/set.html

**Contents:**
- mise alias set ​
- Arguments ​
  - <PLUGIN> ​
  - <ALIAS> ​
  - [VALUE] ​

Add/update an alias for a backend/plugin

This modifies the contents of ~/.config/mise/config.toml

The backend/plugin to set the alias for

The value to set the alias to

**Examples:**

Example 1 (unknown):
```unknown
mise alias set maven asdf:mise-plugins/mise-maven
mise alias set node lts-jod 22.0.0
```

---

## mise install-into ​

**URL:** https://mise.jdx.dev/cli/install-into.html

**Contents:**
- mise install-into ​
- Arguments ​
  - <TOOL@VERSION> ​
  - <PATH> ​

Install a tool version to a specific path

Used for building a tool to a directory for use outside of mise

Tool to install e.g.: node@20

Path to install the tool into

**Examples:**

Example 1 (unknown):
```unknown
# install node@20.0.0 into ./mynode
$ mise install-into node@20.0.0 ./mynode && ./mynode/bin/node -v
20.0.0
```

---

## mise tool ​

**URL:** https://mise.jdx.dev/cli/tool.html

**Contents:**
- mise tool ​
- Arguments ​
  - <TOOL> ​
- Flags ​
  - -J --json ​
  - --backend ​
  - --description ​
  - --installed ​
  - --active ​
  - --requested ​

Gets information about a tool

Tool name to get information about

Output in JSON format

Only show backend field

Only show description field

Only show installed versions

Only show active versions

Only show requested versions

Only show config source

Only show tool options

**Examples:**

Example 1 (unknown):
```unknown
$ mise tool node
Backend:            core
Installed Versions: 20.0.0 22.0.0
Active Version:     20.0.0
Requested Version:  20
Config Source:      ~/.config/mise/mise.toml
Tool Options:       [none]
```

---

## mise completion ​

**URL:** https://mise.jdx.dev/cli/completion.html

**Contents:**
- mise completion ​
- Arguments ​
  - [SHELL] ​
- Flags ​
  - --include-bash-completion-lib ​

Generate shell completions

Shell type to generate completions for

Include the bash completion library in the bash completion script

This is required for completions to work in bash, but it is not included by default you may source it separately or enable this flag to include it in the script.

**Examples:**

Example 1 (unknown):
```unknown
mise completion bash --include-bash-completion-lib > ~/.local/share/bash-completion/completions/mise
mise completion zsh  > /usr/local/share/zsh/site-functions/_mise
mise completion fish > ~/.config/fish/completions/mise.fish
```

---

## mise cache clear ​

**URL:** https://mise.jdx.dev/cli/cache/clear.html

**Contents:**
- mise cache clear ​
- Arguments ​
  - [PLUGIN]… ​

Deletes all cache files in mise

Plugin(s) to clear cache for e.g.: node, python

---

## mise mcp ​

**URL:** https://mise.jdx.dev/cli/mcp.html

**Contents:**
- mise mcp ​

[experimental] Run Model Context Protocol (MCP) server

This command starts an MCP server that exposes mise functionality to AI assistants over stdin/stdout using JSON-RPC protocol.

The MCP server provides access to:

Note: This is primarily intended for integration with AI assistants like Claude, Cursor, or other tools that support the Model Context Protocol.

**Examples:**

Example 1 (unknown):
```unknown
# Start the MCP server (typically used by AI assistant tools)
$ mise mcp

# Example integration with Claude Desktop (add to claude_desktop_config.json):
{
  "mcpServers": {
    "mise": {
      "command": "mise",
      "args": ["mcp"]
    }
  }
}

# Interactive testing with JSON-RPC commands:
$ echo '{"jsonrpc":"2.0","id":1,"method":"initialize","params":{"protocolVersion":"2024-11-05","capabilities":{},"clientInfo":{"name":"test","version":"1.0"}}}' | mise mcp

# Resources you can query:
- mise://tools - List active tools
- mise://tools?include_inactive=true - List all installed tools
- mise://tasks - List all tasks
- mise://env - List environment variables
- mise://config - Show configuration info
```

---

## mise deactivate ​

**URL:** https://mise.jdx.dev/cli/deactivate.html

**Contents:**
- mise deactivate ​

Disable mise for current shell session

This can be used to temporarily disable mise in a shell session.

**Examples:**

Example 1 (unknown):
```unknown
mise deactivate
```

---

## mise latest ​

**URL:** https://mise.jdx.dev/cli/latest.html

**Contents:**
- mise latest ​
- Arguments ​
  - <TOOL@VERSION> ​
- Flags ​
  - -i --installed ​

Gets the latest available version for a plugin

Supports prefixes such as node@20 to get the latest version of node 20.

Tool to get the latest version of

Show latest installed instead of available version

**Examples:**

Example 1 (unknown):
```unknown
$ mise latest node@20  # get the latest version of node 20
20.0.0

$ mise latest node     # get the lat

## configuration.md
# Mise-Task-Managing - Configuration

**Pages:** 15

---

## mise unset ​

**URL:** https://mise.jdx.dev/cli/unset.html

**Contents:**
- mise unset ​
- Arguments ​
  - [ENV_KEY]… ​
- Flags ​
  - -f --file <FILE> ​
  - -g --global ​

Remove environment variable(s) from the config file.

By default, this command modifies mise.toml in the current directory.

Environment variable(s) to remove e.g.: NODE_ENV

Specify a file to use instead of mise.toml

Use the global config file

**Examples:**

Example 1 (unknown):
```unknown
# Remove NODE_ENV from the current directory's config
$ mise unset NODE_ENV

# Remove NODE_ENV from the global config
$ mise unset NODE_ENV -g
```

---

## mise settings ​

**URL:** https://mise.jdx.dev/cli/settings.html

**Contents:**
- mise settings ​
- Arguments ​
  - [SETTING] ​
  - [VALUE] ​
- Global Flags ​
  - -l --local ​
- Flags ​
  - -a --all ​
  - -J --json ​
  - --json-extended ​

Show current settings

This is the contents of ~/.config/mise/config.toml

Note that aliases are also stored in this file but managed separately with mise aliases

Use the local config file instead of the global one

Output in JSON format

Output in JSON format with sources

Output in TOML format

**Examples:**

Example 1 (unknown):
```unknown
# list all settings
$ mise settings

# get the value of the setting "always_keep_download"
$ mise settings always_keep_download

# set the value of the setting "always_keep_download" to "true"
$ mise settings always_keep_download=true

# set the value of the setting "node.mirror_url" to "https://npm.taobao.org/mirrors/node"
$ mise settings node.mirror_url https://npm.taobao.org/mirrors/node
```

---

## mise fmt ​

**URL:** https://mise.jdx.dev/cli/fmt.html

**Contents:**
- mise fmt ​
- Flags ​
  - -a --all ​
  - -c --check ​
  - -s --stdin ​

Sorts keys and cleans up whitespace in mise.toml

Format all files from the current directory

Check if the configs are formatted, no formatting is done

Read config from stdin and write its formatted version into stdout

---

## mise settings get ​

**URL:** https://mise.jdx.dev/cli/settings/get.html

**Contents:**
- mise settings get ​
- Arguments ​
  - <SETTING> ​
- Flags ​
  - -l --local ​

Show a current setting

This is the contents of a single entry in ~/.config/mise/config.toml

Note that aliases are also stored in this file but managed separately with mise aliases get

Use the local config file instead of the global one

**Examples:**

Example 1 (unknown):
```unknown
$ mise settings get idiomatic_version_file
true
```

---

## mise settings unset ​

**URL:** https://mise.jdx.dev/cli/settings/unset.html

**Contents:**
- mise settings unset ​
- Arguments ​
  - <KEY> ​
- Flags ​
  - -l --local ​

This modifies the contents of ~/.config/mise/config.toml

The setting to remove

Use the local config file instead of the global one

**Examples:**

Example 1 (unknown):
```unknown
mise settings unset idiomatic_version_file
```

---

## mise lock ​

**URL:** https://mise.jdx.dev/cli/lock.html

**Contents:**
- mise lock ​
- Arguments ​
  - [TOOL]… ​
- Flags ​
  - -p --platform… <PLATFORM> ​
  - -f --force ​
  - -n --dry-run ​
  - -j --jobs <JOBS> ​

Update lockfile checksums and URLs for all specified platforms

Updates checksums and download URLs for all platforms already specified in the lockfile. If no lockfile exists, shows what would be created based on the current configuration. This allows you to refresh lockfile data for platforms other than the one you're currently on. Operates on the lockfile in the current config root. Use TOOL arguments to target specific tools.

Tool(s) to update in lockfile e.g.: node python If not specified, all tools in lockfile will be updated

Comma-separated list of platforms to target e.g.: linux-x64,macos-arm64,windows-x64 If not specified, all platforms already in lockfile will be updated

Update all tools even if lockfile data already exists

Show what would be updated without making changes

Number of jobs to run in parallel [default: 4]

$ mise lock Update lockfile in current directory for all platforms $ mise lock node python Update only node and python $ mise lock --platform linux-x64 Update only linux-x64 platform $ mise lock --dry-run Show what would be updated or created $ mise lock --force Re-download and update even if data exists

---

## mise config get ​

**URL:** https://mise.jdx.dev/cli/config/get.html

**Contents:**
- mise config get ​
- Arguments ​
  - [KEY] ​
- Flags ​
  - -f --file <FILE> ​

Display the value of a setting in a mise.toml file

The path of the config to display

The path to the mise.toml file to edit

If not provided, the nearest mise.toml file will be used

**Examples:**

Example 1 (unknown):
```unknown
$ mise toml get tools.python
3.12
```

---

## mise use ​

**URL:** https://mise.jdx.dev/cli/use.html

**Contents:**
- mise use ​
- Arguments ​
  - [TOOL@VERSION]… ​
- Flags ​
  - -f --force ​
  - --fuzzy ​
  - -g --global ​
  - -n --dry-run ​
  - -e --env <ENV> ​
  - -j --jobs <JOBS> ​

Installs a tool and adds the version to mise.toml.

This will install the tool version if it is not already installed. By default, this will use a mise.toml file in the current directory.

In the following order:

Use the --global flag to use the global config file instead.

Tool(s) to add to config file

e.g.: node@20, cargo:ripgrep@latest npm:prettier@3 If no version is specified, it will default to @latest

Tool options can be set with this syntax:

Force reinstall even if already installed

Save fuzzy version to config file

e.g.: mise use --fuzzy node@20 will save 20 as the version this is the default behavior unless MISE_PIN=1

Use the global config file (~/.config/mise/config.toml) instead of the local one

Perform a dry run, showing what would be installed and modified without making changes

Create/modify an environment-specific config file like .mise.<env>.toml

Number of jobs to run in parallel [default: 4]

Directly pipe stdin/stdout/stderr from plugin to user Sets --jobs=1

Remove the plugin(s) from config file

Specify a path to a config file or directory

If a directory is specified, it will look for a config file in that directory following the rules above.

Save exact version to config file e.g.: mise use --pin node@20 will save 20.0.0 as the version Set MISE_PIN=1 to make this the default behavior

Consider using mise.lock as a better alternative to pinning in mise.toml: https://mise.jdx.dev/configuration/settings.html#lockfile

**Examples:**

Example 1 (unknown):
```unknown
mise use ubi:BurntSushi/ripgrep[exe=rg]
```

Example 2 (unknown):
```unknown
# run with no arguments to use the interactive selector
$ mise use

# set the current version of node to 20.x in mise.toml of current directory
# will write the fuzzy version (e.g.: 20)
$ mise use node@20

# set the current version of node to 20.x in ~/.config/mise/config.toml
# will write the precise version (e.g.: 20.0.0)
$ mise use -g --pin node@20

# sets .mise.local.toml (which is intended not to be committed to a project)
$ mise use --env local node@20

# sets .mise.staging.toml (which is used if MISE_ENV=staging)
$ mise use --env staging node@20
```

---

## mise settings ls ​

**URL:** https://mise.jdx.dev/cli/settings/ls.html

**Contents:**
- mise settings ls ​
- Arguments ​
  - [SETTING] ​
- Flags ​
  - -a --all ​
  - -l --local ​
  - -J --json ​
  - --json-extended ​
  - -T --toml ​

Show current settings

This is the contents of ~/.config/mise/config.toml

Note that aliases are also stored in this file but managed separately with mise aliases

Use the local config file instead of the global one

Output in JSON format

Output in JSON format with sources

Output in TOML format

**Examples:**

Example 1 (unknown):
```unknown
$ mise settings ls
idiomatic_version_file = false
...

$ mise settings ls python
default_packages_file = "~/.default-python-packages"
...
```

---

## mise config ls ​

**URL:** https://mise.jdx.dev/cli/config/ls.html

**Contents:**
- mise config ls ​
- Flags ​
  - --no-header ​
  - --tracked-configs ​
  - -J --json ​

List config files currently in use

Do not print table header

List all tracked config files

Output in JSON format

**Examples:**

Example 1 (unknown):
```unknown
$ mise config ls
Path                        Tools
~/.config/mise/config.toml  pitchfork
~/src/mise/mise.toml        actionlint, bun, cargo-binstall, cargo:cargo-edit, cargo:cargo-insta
```

---

## mise settings add ​

**URL:** https://mise.jdx.dev/cli/settings/add.html

**Contents:**
- mise settings add ​
- Arguments ​
  - <SETTING> ​
  - <VALUE> ​
- Flags ​
  - -l --local ​

Adds a setting to the configuration file

Used with an array setting, this will append the value to the array. This modifies the contents of ~/.config/mise/config.toml

Use the local config file instead of the global one

**Examples:**

Example 1 (unknown):
```unknown
mise settings add disable_hints python_multi
```

---

## mise settings set ​

**URL:** https://mise.jdx.dev/cli/settings/set.html

**Contents:**
- mise settings set ​
- Arguments ​
  - <SETTING> ​
  - <VALUE> ​
- Flags ​
  - -l --local ​

This modifies the contents of ~/.config/mise/config.toml

Use the local config file instead of the global one

**Examples:**

Example 1 (unknown):
```unknown
mise settings idiomatic_version_file=true
```

---

## mise config set ​

**URL:** https://mise.jdx.dev/cli/config/set.html

**Contents:**
- mise config set ​
- Arguments ​
  - <KEY> ​
  - <VALUE> ​
- Flags ​
  - -f --file <FILE> ​
  - -t --type <TYPE> ​

Set the value of a setting in a mise.toml file

The path of the config to display

The value to set the key to

The path to the mise.toml file to edit

If not provided, the nearest mise.toml file will be used

**Examples:**

Example 1 (unknown):
```unknown
$ mise config set tools.python 3.12
$ mise config set settings.always_keep_download true
$ mise config set env.TEST_ENV_VAR ABC
$ mise config set settings.disable_tools --type list node,rust

# Type for `settings` is inferred
$ mise config set settings.jobs 4
```

---

## mise unuse ​

**URL:** https://mise.jdx.dev/cli/unuse.html

**Contents:**
- mise unuse ​
- Arguments ​
  - <INSTALLED_TOOL@VERSION>… ​
- Flags ​
  - -g --global ​
  - -e --env <ENV> ​
  - -p --path <PATH> ​
  - --no-prune ​

Removes installed tool versions from mise.toml

By default, this will use the mise.toml file that has the tool defined.

In the following order:

Will also prune the installed version if no other configurations are using it.

Use the global config file (~/.config/mise/config.toml) instead of the local one

Create/modify an environment-specific config file like .mise.<env>.toml

Specify a path to a config file or directory

If a directory is specified, it will look for a config file in that directory following the rules above.

Do not also prune the installed version

**Examples:**

Example 1 (unknown):
```unknown
# will uninstall specific version
$ mise unuse node@18.0.0

# will uninstall specific version from global config
$ mise unuse -g node@18.0.0

# will uninstall specific version from .mise.local.toml
$ mise unuse --env local node@20

# will uninstall specific version from .mise.staging.toml
$ mise unuse --env staging node@20
```

---

## mise config ​

**URL:** https://mise.jdx.dev/cli/config.html

**Contents:**
- mise config ​
- Flags ​
  - --no-header ​
  - --tracked-configs ​
  - -J --json ​
- Subcommands ​

Do not print table header

List all tracked config files

Output in JSON format

**Examples:**

Example 1 (unknown):
```unknown
$ mise config ls
Path                        Tools
~/.config/mise/config.toml  pitchfork
~/src/mise/mise.toml        actionlint, bun, cargo-binstall, cargo:cargo-edit, cargo:cargo-insta
```

---


## dev_tools.md
# Mise-Task-Managing - Dev Tools

**Pages:** 30

---

## Comparison to asdf ​

**URL:** https://mise.jdx.dev/dev-tools/comparison-to-asdf.html

**Contents:**
- Comparison to asdf ​
- Migrate from asdf to mise ​
- asdf in go (0.16+) ​
- Supply chain security ​
- UX ​
- Performance ​
- Windows support ​
- Security ​
- Command Compatibility ​
- Extra backends ​

mise can be used as a drop-in replacement for asdf. It supports the same .tool-versions files that you may have used with asdf and can use asdf plugins through the asdf backend.

It will not, however, reuse existing asdf directories (so you'll need to either reinstall them or move them), and 100% compatibility is not a design goal. That said, if you're coming from asdf-bash (0.15 and below), mise actually has fewer breaking changes than asdf-go (0.16 and above) despite 100% compatibility not being a design goal of mise.

Casual users coming from asdf have generally found mise to just be a faster, easier to use asdf.

Make sure you have a look at environments and tasks which are major portions of mise that have no asdf equivalent.

If you're moving from asdf to mise, please review #how-do-i-migrate-from-asdf for guidance.

asdf has gone through a rewrite in go. Because this is quite new as of this writing (2025-01-01), I'm going to keep information about 0.16+ asdf versions (which I call "asdf-go" vs "asdf-bash") in this section and the rest of this doc will apply to asdf-bash (0.15 and below).

In terms of performance, mise is still faster than the go asdf, however the difference is much closer. asdf is likely fast enough that the difference in overhead between asdf-go and mise may not even be enough to notice for you—after all there are plenty of people still using asdf-bash that claim they don't even notice how slow it is (don't ask me how):

I don't think performance is a good enough reason to switch though now that asdf-go is a thing. It's a reason, but it's a minor one. The improved security in mise, better DX, and lack of reliance on shims are all more important than performance.

Given they went through the trouble of rewriting asdf—that's also an indication they want to keep working on it (which is awesome that they're doing that btw). This does mean that some of what's written here may go out of date if they address some of the problems with asdf.

asdf plugins are not secure. This is explained in SECURITY.md, but the quick explanation is that asdf plugins involve shell code which can essentially do anything on your machine. It's dangerous code. What's worse is asdf plugins are rarely written by the tool vendor (who you need to trust anyway to use the tool), which means for every asdf plugin you use you'll be trusting a random developer to not go rogue and to not get hacked themselves and publish changes to a plugin with an exploit.

mise still uses asdf plugins for some tools, but we're actively reducing that count as well as moving things into the mise-plugins org. It looks like asdf has a similar model with their asdf-community org, but it isn't. asdf gives plugin authors commit access to their plugin in asdf-community when they move it in, which I feel like defeats the purpose of having a dedicated org in the first place. By the end of 2025 I would like for there to no longer be any asdf plugins in the registry that aren't owned by me.

I've also been adopting extra security verification steps when vendors offer that ability such as gpg verification on node installs, and native Cosign/SLSA/Minisign/GitHub attestation verification for aqua tools.

Some commands are the same in asdf but others have been changed. Everything that's possible in asdf should be possible in mise but may use slightly different syntax. mise has more forgiving commands, such as using fuzzy-matching, e.g.: mise install node@20. While in asdf you can run asdf install node latest:20, you can't use latest:20 in a .tool-versions file or many other places. In mise you can use fuzzy-matching everywhere.

asdf requires several steps to install a new runtime if the plugin isn't installed, e.g.:

In mise this can all be done in a single step which installs the plugin, installs the runtime, and sets the version:

If you have an existing .tool-versions file, or .mise.toml, you can install all plugins and runtimes with a single command:

I've found asdf to be particularly rigid and difficult to learn. It also made strange decisions like having asdf list all but asdf latest --all (why is one a flag and one a positional argument?). mise makes heavy use of aliases so you don't need to remember if it's mise plugin add node or mise plugin install node. If I can guess what you meant, then I'll try to get mise to respond in the right way.

That said, there are a lot of great things about asdf. It's the best multi-runtime manager out there and I've really been impressed with the plugin system. Most of the design decisions the authors made were very good. I really just have 2 complaints: the shims and the fact it's written in Bash.

asdf made (what I consider) a poor design decision to use shims that go between a call to a runtime and the runtime itself. e.g.: when you call node it will call an asdf shim file ~/.asdf/shims/node, which then calls asdf exec, which then calls the correct version of node.

These shims have terrible performance, adding ~120ms to every runtime call. mise activate does not use shims and instead updates PATH so that it doesn't have any overhead when simply calling binaries. These shims are the main reason that I wrote this. Note that in the demo GIF at the top of this README that mise isn't actually used when calling node -v for this reason. The performance is identical to running node without using mise.

I don't think it's possible for asdf to fix these issues. The author of asdf did a great writeup of performance problems. asdf is written in bash which certainly makes it challenging to be performant, however I think the real problem is the shim design. I don't think it's possible to fix that without a complete rewrite.

mise does call an internal command mise hook-env every time the directory has changed, but because it's written in Rust, this is very quick—taking ~10ms on my machine. 4ms if there are no changes, 14ms if it's a full reload.

tl;dr: asdf adds overhead (~120ms) when calling a runtime, mise adds a small amount of overhead (~ 5ms) when the prompt loads.

asdf does not run on Windows at all. With mise, tools using non-asdf backends can support Windows. Of course, this means the tool vendor must provide Windows binaries but if they do, and the backend isn't asdf, the tool should work on Windows.

asdf plugins are insecure. They typically are written by individuals with no ties to the vendors that provide the underlying tool. Where possible, mise does not use asdf plugins and instead uses backends like aqua and ubi which do not require separate plugins.

Aqua tools include native Cosign/SLSA/Minisign/GitHub attestation verification built into mise. See SECURITY for more information.

In nearly all places you can use the exact syntax that works in asdf, however this likely won't show up in the help or CLI reference. If you're coming from asdf and comfortable with that way of working you can almost always use the same syntax with mise, e.g.:

UPDATE (2025-01-01): asdf-go (0.16+) actually got rid of asdf global|local entirely in favor of asdf set which we can't support since we already have a command named mise set. mise command compatibility will likely not be as good with asdf-go 0.16+.

It's not recommended though. You almost always want to modify config files and install things so mise use node@20 saves an extra command. Also, the "@" in the command is preferred since it allows you to install multiple tools at once: mise use|install node@20 node@18. Also, there are edge cases where it's not possible—or at least very challenging—for us to definitively know which syntax is being used and so we default to mise-style. While there aren't many of these, asdf-compatibility is done as a "best-effort" in order to make transitioning from asdf feel familiar for those users who can rely on their muscle memory. Ensuring asdf-syntax works with everything is not a design goal.

mise has support for backends other than asdf plugins. For example you can install CLIs directly from cargo and npm:

**Examples:**

Example 1 (unknown):
```unknown
asdf plugin add node
asdf install node latest:20
asdf local node latest:20
```

Example 2 (unknown):
```unknown
mise use node@20
```

Example 3 (unknown):
```unknown
mise install
```

Example 4 (unknown):
```unknown
mise install node 20.0.0
mise local node 20.0.0
```

---

## mise ls ​

**URL:** https://mise.jdx.dev/cli/ls.html

**Contents:**
- mise ls ​
- Arguments ​
  - [INSTALLED_TOOL]… ​
- Flags ​
  - -c --current ​
  - -g --global ​
  - -l --local ​
  - -i --installed ​
  - --outdated ​
  - -J --json ​

List installed and active tool versions

This command lists tools that mise "knows about". These may be tools that are currently installed, or those that are in a config file (active) but may or may not be installed.

It's a useful command to get the current state of your tools.

Only show tool versions from [TOOL]

Only show tool versions currently specified in a mise.toml

Only show tool versions currently specified in the global mise.toml

Only show tool versions currently specified in the local mise.toml

Only show tool versions that are installed (Hides tools defined in mise.toml but not installed)

Display whether a version is outdated

Output in JSON format

Display missing tool versions

Display versions matching this prefix

List only tools that can be pruned with mise prune

Don't display headers

**Examples:**

Example 1 (unknown):
```unknown
$ mise ls
node    20.0.0 ~/src/myapp/.tool-versions latest
python  3.11.0 ~/.tool-versions           3.10
python  3.10.0

$ mise ls --current
node    20.0.0 ~/src/myapp/.tool-versions 20
python  3.11.0 ~/.tool-versions           3.11.0

$ mise ls --json
{
  "node": [
    {
      "version": "20.0.0",
      "install_path": "/Users/jdx/.mise/installs/node/20.0.0",
      "source": {
        "type": "mise.toml",
        "path": "/Users/jdx/mise.toml"
      }
    }
  ],
  "python": [...]
}
```

---

## mise outdated ​

**URL:** https://mise.jdx.dev/cli/outdated.html

**Contents:**
- mise outdated ​
- Arguments ​
  - [TOOL@VERSION]… ​
- Flags ​
  - -l --bump ​
  - -J --json ​
  - --no-header ​

Shows outdated tool versions

See mise upgrade to upgrade these versions.

Tool(s) to show outdated versions for e.g.: node@20 python@3.10 If not specified, all tools in global and local configs will be shown

Compares against the latest versions available, not what matches the current config

For example, if you have node = "20" in your config by default mise outdated will only show other 20.x versions, not 21.x or 22.x versions.

Using this flag, if there are 21.x or newer versions it will display those instead of 20.x.

Output in JSON format

Don't show table header

**Examples:**

Example 1 (unknown):
```unknown
$ mise outdated
Plugin  Requested  Current  Latest
python  3.11       3.11.0   3.11.1
node    20         20.0.0   20.1.0

$ mise outdated node
Plugin  Requested  Current  Latest
node    20         20.0.0   20.1.0

$ mise outdated --json
{"python": {"requested": "3.11", "current": "3.11.0", "latest": "3.11.1"}, ...}
```

---

## gem Backend ​

**URL:** https://mise.jdx.dev/dev-tools/backends/gem.html

**Contents:**
- gem Backend ​
- Dependencies ​
- Usage ​
- Ruby upgrades ​
- Settings ​

mise can be used to install CLIs from RubyGems. The code for this is inside of the mise repository at ./src/backend/gem.rs.

This relies on having gem (provided with ruby) installed. You can install it with or without mise. Here is how to install ruby with mise:

The following installs the latest version of rubocop and sets it as the active version on PATH:

The version will be set in ~/.config/mise/config.toml with the following format:

If the ruby version used by a gem package changes, (by mise or system ruby), you may need to reinstall the gem. This can be done with:

Or you can reinstall all gems with:

Set these with mise settings set [VARIABLE] [VALUE] or by setting the environment variable listed.

No settings available.

**Examples:**

Example 1 (unknown):
```unknown
mise use -g ruby
```

Example 2 (unknown):
```unknown
mise use -g gem:rubocop
rubocop --version
```

Example 3 (unknown):
```unknown
[tools]
"gem:rubocop" = "latest"
```

Example 4 (unknown):
```unknown
mise install -f gem:rubocop
```

---

## Vfox Backend ​

**URL:** https://mise.jdx.dev/dev-tools/backends/vfox.html

**Contents:**
- Vfox Backend ​
- Dependencies ​
- Usage ​
- Default plugin backend ​
- Plugins ​
  - Example: Plugin Usage ​

Vfox plugins may be used in mise to install tools.

The code for this is inside the mise repository at ./src/backend/vfox.rs.

No dependencies are required for vfox. Vfox lua code is read via a lua interpreter built into mise.

The following installs the latest version of cmake and sets it as the active version on PATH:

The version will be set in ~/.config/mise/config.toml with the following format:

On Windows, mise uses vfox plugins by default. If you'd like to use plugins by default even on Linux/macOS, set the following settings:

Now you can list available plugins with mise registry:

And they will be installed when running commands such as mise use -g cmake without needing to specify vfox:cmake.

In addition to the standard vfox plugins, mise supports modern plugins that can manage multiple tools using the plugin:tool format. These plugins are perfect for:

For more information, see:

**Examples:**

Example 1 (unknown):
```unknown
$ mise use -g vfox:version-fox/vfox-cmake
$ cmake --version
cmake version 3.21.3
```

Example 2 (unknown):
```unknown
[tools]
"vfox:version-fox/vfox-cmake" = "latest"
```

Example 3 (unknown):
```unknown
mise settings add disable_backends asdf
```

Example 4 (unknown):
```unknown
$ mise registry | grep vfox:
clang                         vfox:mise-plugins/vfox-clang
cmake                         vfox:mise-plugins/vfox-cmake
crystal                       vfox:mise-plugins/vfox-crystal
dart                          vfox:mise-plugins/vfox-dart
dotnet                        vfox:mise-plugins/vfox-dotnet
etcd                          aqua:etcd-io/etcd vfox:mise-plugins/vfox-etcd
flutter                       vfox:mise-plugins/vfox-flutter
gradle                        aqua:gradle/gradle vfox:mise-plugins/vfox-gradle
groovy                        vfox:mise-plugins/vfox-groovy
kotlin                        vfox:mise-plugins/vfox-kotlin
maven                         aqua:apache/maven vfox:mise-plugins/vfox-maven
php                           vfox:mise-plugins/vfox-php
scala                         vfox:mise-plugins/vfox-scala
terraform                     aqua:hashic

------------------------------------------------------------

YOUR TASK:
Create an EXCELLENT SKILL.md file that will help Claude use this documentation effectively.

Requirements:
1. **Clear "When to Use This Skill" section**
   - Be SPECIFIC about trigger conditions
   - List concrete use cases

2. **Excellent Quick Reference section**
   - Extract 5-10 of the BEST, most practical code examples from the reference docs
   - Choose SHORT, clear examples (5-20 lines max)
   - Include both simple and intermediate examples
   - Use proper language tags (cpp, python, javascript, json, etc.)
   - Add clear descriptions for each example

3. **Detailed Reference Files description**
   - Explain what's in each reference file
   - Help users navigate the documentation

4. **Practical "Working with This Skill" section**
   - Clear guidance for beginners, intermediate, and advanced users
   - Navigation tips

5. **Key Concepts section** (if applicable)
   - Explain core concepts
   - Define important terminology

IMPORTANT:
- Extract REAL examples from the reference docs above
- Prioritize SHORT, clear examples
- Make it actionable and practical
- Keep the frontmatter (---\nname: ...\n---) intact
- Use proper markdown formatting

SAVE THE RESULT:
Save the complete enhanced SKILL.md to: /home/delorenj/code/Skill_Seekers/output/mise-task-managing/SKILL.md

First, backup the original to: /home/delorenj/code/Skill_Seekers/output/mise-task-managing/SKILL.md.backup
