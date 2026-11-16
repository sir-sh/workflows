# Sir workflow registry

Reusable workflows for [Sir](https://www.sir.sh/docs/QUICKSTART). Use Sir in a Linux or macOS shell and run them from the target project's root.

| Workflow | Purpose |
| --- | --- |
| [project-setup](workflows/project-setup) | Install locked PHP and npm dependencies |
| [pre-release-checks](workflows/pre-release-checks) | Run a project's existing release checks |
| [release-notes](workflows/release-notes) | Preview a commit list since a selected ref |
| [hello](workflows/hello) | Write a local greeting |
| [count-file-lines](workflows/count-file-lines) | Count newline characters in a named file |
| [directory-size](workflows/directory-size) | Report the disk space used by the current directory |
| [disk-free](workflows/disk-free) | Show available space on the filesystem containing the current directory |
| [docker-disk-usage](workflows/docker-disk-usage) | Show space used by Docker images, containers, volumes, and build cache |
| [docker-image-list](workflows/docker-image-list) | List images stored on the current Docker daemon |
| [docker-running](workflows/docker-running) | List running containers with their names, images, and status |
| [file-sha256](workflows/file-sha256) | Print the SHA-256 digest of a named file |
| [git-check-whitespace](workflows/git-check-whitespace) | Report whitespace errors in staged and unstaged changes |
| [git-diff-summary](workflows/git-diff-summary) | Summarize unstaged changes to tracked files |
| [git-local-branches](workflows/git-local-branches) | List local branches in most recently updated order |
| [git-merged-branches](workflows/git-merged-branches) | List local branches already merged into the current commit |
| [git-recent-commits](workflows/git-recent-commits) | Show the last ten commits on the current branch |
| [git-recent-tags](workflows/git-recent-tags) | List up to ten tags in newest-first order |
| [git-staged-summary](workflows/git-staged-summary) | Summarize changes staged for the next commit |
| [git-status](workflows/git-status) | Show the current branch and uncommitted changes |
| [machine-uptime](workflows/machine-uptime) | Show how long the machine has been up and its load averages |
| [python-check-json](workflows/python-check-json) | Check that a named file contains parseable JSON |
| [show-utc-time](workflows/show-utc-time) | Print the current UTC time in an ISO 8601 format |
| [system-info](workflows/system-info) | Print the kernel name, release, and machine architecture |
| [tool-versions](workflows/tool-versions) | Report installed versions of Git, Node.js, npm, PHP, Python, and Docker |
| [check-final-newline](workflows/check-final-newline) | Check that a nonempty text file ends with a newline. Empty files pass |
| [docker-compose-check](workflows/docker-compose-check) | Validate the Compose configuration without starting services or printing the rendered configuration |
| [docker-compose-services](workflows/docker-compose-services) | Show the status of all services in the current Compose project, including stopped services |
| [docker-context](workflows/docker-context) | Print the active Docker context before running commands against a daemon |
| [file-compare](workflows/file-compare) | Show a unified diff between two local text files. Differences are a successful result |
| [file-size-bytes](workflows/file-size-bytes) | Print the exact byte count of a named file |
| [git-conflicted-files](workflows/git-conflicted-files) | List unresolved paths during a merge, rebase, or cherry-pick |
| [git-contributors](workflows/git-contributors) | Count commits per author on the current branch using the repository mailmap |
| [git-last-file-change](workflows/git-last-file-change) | Show the latest commit that changed a repository-relative path |
| [git-release-files](workflows/git-release-files) | List added, modified, and deleted paths between a chosen Git ref and HEAD |
| [git-repository-root](workflows/git-repository-root) | Print the root of the current Git worktree for scripts and editor tasks |
| [git-submodule-status](workflows/git-submodule-status) | Inspect checked-out revisions and initialization status of Git submodules |
| [git-untracked-files](workflows/git-untracked-files) | List untracked files while respecting Git ignore rules |
| [json-pretty-print](workflows/json-pretty-print) | Format a local JSON file for inspection and write the result to standard output |
| [list-zip-contents](workflows/list-zip-contents) | List archive entries without extracting any files |
| [node-check-syntax](workflows/node-check-syntax) | Check JavaScript syntax with Node.js without evaluating the file |
| [php-check-syntax](workflows/php-check-syntax) | Check a PHP file for syntax errors without executing it |
| [python-check-csv-columns](workflows/python-check-csv-columns) | Check that each CSV record has the same number of fields as the header |
| [python-check-syntax](workflows/python-check-syntax) | Parse a Python source file without importing it or writing bytecode |
| [python-check-toml](workflows/python-check-toml) | Check that a file contains valid TOML without modifying it |
| [python-check-xml](workflows/python-check-xml) | Check that a local XML document is well-formed without modifying it |
| [shell-check-syntax](workflows/shell-check-syntax) | Parse a POSIX shell script without executing its commands |

## Install a pinned workflow

Copy the full commit SHA of the registry revision you reviewed and replace
`REGISTRY_COMMIT` in the second command. Review YAML before installing it.
Workflows run shell commands with the permissions of the account running Sir.

```sh
git clone https://github.com/sir-sh/workflows.git sir-workflows
git -C sir-workflows checkout --detach REGISTRY_COMMIT
mkdir -p "$HOME/.sir/workflows"
workflow=release-notes
cp "sir-workflows/workflows/$workflow/$workflow.yml" "$HOME/.sir/workflows/"
```

Set the `workflow` variable to the registry entry you want to install.

From the target repository, substitute your actual previous release tag for
`v0.1.0` and preview the notes.

```sh
sir run release-notes --dry-run --non-interactive --input=base=v0.1.0
sir run release-notes --non-interactive --input=base=v0.1.0
```

See [validation results](VALIDATION.md) for real-project runs.
