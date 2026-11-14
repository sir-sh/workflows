# Pre-release checks

Runs a project’s existing verification command from its root. Supply a command
you would run directly in your shell.

- **Prerequisites** — Sir, a POSIX shell, and the project's installed test/build tools.
- **Inputs** — Required `command`, a trusted shell command. Use `&&` to stop a chain at its first failure.
- **Outputs** — The checker's console output and Sir's run result.
- **Failure** — A nonzero command exit fails the workflow.

Install `pre-release-checks.yml` using the [registry instructions](../../README.md),
then run the command appropriate to your project. For example:

```sh
sir run pre-release-checks --non-interactive --input='command=npx --no-install tsc --noEmit && npm run build'
```
