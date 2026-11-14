# Ulties project review

The legacy Sir review example uses Git and CodeRabbit to prepare review reports for a project under the Ulties organization.

- **Prerequisites** — Sir with the listed workspace, Git, test, file, and CodeRabbit tasks, Git access to the project, and a configured CodeRabbit CLI.
- **Inputs** — Required `projectName` and `target`. Optional `base` defaults to `main`.
- **Outputs** — `TEST_RESULT.md` and `REVIEW.md` in a temporary review workspace.
- **Run** — Install `review.yml` using the [registry instructions](../../README.md), then run `sir run review --non-interactive --input=projectName=PROJECT --input=target=BRANCH`.
