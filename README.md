# Sir workflow registry

Reusable workflows for [Sir](https://www.sir.sh/docs/QUICKSTART). Use Sir in a Linux or macOS shell and run them from the target project's root.

| Workflow | Purpose |
| --- | --- |
| [project-setup](workflows/project-setup) | Install locked PHP and npm dependencies |
| [pre-release-checks](workflows/pre-release-checks) | Run a project's existing release checks |
| [release-notes](workflows/release-notes) | Preview a commit list since a selected ref |

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
