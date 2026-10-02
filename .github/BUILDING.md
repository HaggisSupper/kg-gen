# GitHub builds

Build and validate this Python package on GitHub-hosted Ubuntu runners. Open
**Actions → Hosted Python build → Run workflow** to start a manual build. The
same package build runs on pushes and pull requests.

CI installs the declared package and development dependencies on the hosted
runner, checks dependency vulnerabilities and Python syntax/name errors, then
runs the existing credential-free chunking unit tests. It builds a fresh wheel
and source distribution into `ci-dist/`, verifies package metadata with Twine,
and publishes both as the `python-distributions` artifact. The committed older
`dist/` files are not substituted for newly built artifacts.

The full test collection also exercises paid external model APIs. To run that
gate, configure the repository's `OPENAI_API_KEY` Actions secret, manually
dispatch the workflow, and enable **Run API-dependent integration tests**.
That job fails clearly when the secret is missing. It is not enabled on pushes
or untrusted pull requests. A successful package build verifies the unit tests
and packaging only; inspect a successful integration job before claiming that
the external-model integration tests passed.

Builds currently target Python 3.12. This does not certify every Python version
listed in package metadata. Download fresh distributions from a successful
completed run and inspect the logs and artifact before reporting success.
Older README installation commands are for the hosted workflow's execution
environment. Do not build on this computer or use self-hosted runners when
Actions is blocked.
