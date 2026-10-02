# Repository build policy

Run all builds, dependency installation, packaging, release artifact creation,
security checks, lint, type checks, and tests in GitHub Actions on GitHub-hosted
runners. Do not use this computer or a self-hosted runner for project builds.
Local read-only inspection and static configuration validation are allowed.

Inspect existing workflows before changing them and preserve required checks
and platform requirements. Push authorized changes or use a pull request, then
inspect the workflow result and artifacts. A queued run is not proof of success.
Report authentication, permission, runner, billing, or missing-secret blockers
instead of building locally. A specific later user instruction may override
this policy.

