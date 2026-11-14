# Release notes

Prints one bullet per commit reachable from HEAD since a selected base. It
does not create a tag, write a release, or push to a remote.

- **Prerequisites** — Sir, Git, and a checkout with enough history to resolve the base and its relationship to HEAD.
- **Inputs** — Required `base`, an ancestor commit, branch, or previous release tag.
- **Outputs** — Commit subjects and short hashes on standard output. Sir also prints run progress.
- **Failure** — An unknown base or a base outside HEAD's history fails the workflow.

Install `release-notes.yml` using the [registry instructions](../../README.md).
From the project root, run
`sir run release-notes --non-interactive --input=base=v0.1.0`,
substituting your actual base ref.
