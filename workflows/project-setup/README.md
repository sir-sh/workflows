# Project setup

Installs locked dependencies in the current project. Use a disposable checkout
when trying this workflow. Run it from the root of a trusted project.

- **Prerequisites** — Sir, a project with `composer.lock` or `package-lock.json`, and the corresponding Composer/PHP or npm/Node runtime.
- **Inputs** — None.
- **Outputs** — Creates or updates `vendor/` and/or `node_modules/`. Composer can run project scripts. npm lifecycle scripts are disabled.
- **Failure** — Exits with an error if neither lockfile exists or if an install fails.

Install `project-setup.yml` using the [registry instructions](../../README.md),
then run `sir run project-setup --non-interactive`.
