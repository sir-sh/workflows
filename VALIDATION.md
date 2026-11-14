# Sir v0.2 workflow validation

The initial runs used Sir v0.1.0 (`da3a235a00d8727ea9f2dfd4ac5ce4548fff39a0`) and registry revision `ef3b005ddd174b2cb2593f2c884b0e901132aff0` in a disposable Linux container with PHP 8.4 and Node 22. Each project was a separate checkout.

| Project and revision | Project setup | Pre-release checks | Release notes |
| --- | --- | --- | --- |
| [Sir CLI](https://github.com/sir-sh/cli/tree/da3a235a00d8727ea9f2dfd4ac5ce4548fff39a0) | Composer installed the locked development dependencies | Pint passed. Pest reported 411 passes, two warnings, and two risky tests | Output matched `git log` for `HEAD~2..HEAD` |
| [Sir website](https://github.com/sir-sh/website/tree/eb343d5fe1f1d2a52618d523723905a8b39d19dc) | npm installed the locked dependencies | TypeScript and the Next.js production build passed. The repository has no npm test script | Output matched `git log` for `HEAD~2..HEAD` |

In both projects setup's dry run created neither dependency directory. The check workflow returned failure for a command that exited 7. The release-note workflow returned failure for an unknown ref. All runs used named inputs where required and ran without interactive prompts. For the CLI's checks, use a separate empty `HOME` for Pint and Pest so the test suite does not discover the registry workflows from the caller's Sir profile.

The CLI's development lock requires PHP 8.3 or later. Sir v0.1.0's production installation was also verified on PHP 8.2.
