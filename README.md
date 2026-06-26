# pkg-libdiag

Debian packaging repository for the Qualcomm Diag shared library and tools. It integrates with [qcom-build-utils](https://github.com/qualcomm-linux/qcom-build-utils) for standardized Debian package building.

## Packages

| Package | Description |
|---|---|
| `qcom-libdiag` | Qualcomm Diag shared library |
| `qcom-libdiag-dev` | Development headers, static libraries, and pkg-config files |
| `qcom-diag` | Diagnostic tools and utilities for Qualcomm platforms |

## Branches

- **qli-ci**: Default branch containing workflow logic in `.github/` and boilerplate documentation.
- **qcom/ubuntu/resolute**: Packaging branch for Ubuntu Resolute.
- **qcom/debian/trixie**: Packaging branch for Debian Trixie.
- **qcom/debian/latest**: Packaging branch tracking the latest Debian release.

## Workflows

The `qli-ci` branch includes the following workflows in `.github/workflows/`:

- **qcom-preflight-checks.yml**: Sanity check workflow inherited from the base Qualcomm template.
- **stale-issues.yaml**: Manages stale issues.
- **build-debian-package.yml**: Builds the Debian package by invoking reusable workflows from qcom-build-utils.
- **pkg-pr-hook.yml**: Executes during a PR and once the PR is merged.
- **promote-prebuilt.yml**: Promotes a prebuilt package artifact to a new release.
- **promote-upstream.yml**: Promotes the package's tracked version to a new upstream release.
- **release.yml**: Triggers a package release.
- **workflows_sync.yml**: Keeps workflows in sync with the base template.

## Repository Configuration

### Runners

Workflows run on GitHub arm64 runners. Sections requiring access to S3 or Artifactory run on AWS runners — contact **Steve Manley** to enable the repo for those.

### GHCR Registry Access

Build workflows use the `pkg-builder` container image from the qualcomm-linux GHCR. Contact **Mark Matyas** (mmatyas@qti.qualcomm.com) to grant your repository `packages:read` access:

https://github.com/orgs/qualcomm-linux/packages/container/pkg-builder/settings

### Repository Variables

- **UPSTREAM_REPO_GITHUB_NAME** *(set in this repo)*: GitHub name of the upstream repository.
- **PKG_REPO_GITHUB_NAME** *(set in the upstream repo)*: GitHub name of this package repository (`qualcomm-linux/pkg-libdiag`).

### Branch Protection Rules

Configure branch protection for `debian/**` and `qcom/**`:

- Restrict deletions.
- Require pull requests before merging.
- Block force pushes.
- Add `build / build-debian-package` as a required status check.
- Add `qcom-service-bot` with admin rights and include the Admin role in the ruleset so it can push directly.

### Additional Settings

- Enable **"Automatically delete head branches"** for pull requests.
- Allow only merge commits for pull request merges.
- Enable **release immutability** in the upstream repository.
- Add **qcom-service-bot** as a user with write access. If/when the repo is made public, manage contributors via the Qualcomm mailing list (`maintainers.pkg-libdiag`, `contributors.pkg-libdiag`) at https://lists.qualcomm.com/ListManager, using the bot's Qualcomm username **githubservice**@qti.qualcomm.com.

## Making the Repo Public

When the repo is ready to go public, initiate the Trademark/legal process with [Stephanie Arce](sarce@qti.qualcomm.com) and [complete an OSS Contribution Request](https://jira-dc4.qualcomm.com/jira/secure/CreateIssue.jspa?pid=46536&issuetype=13440). Once approved, submit an enablement ticket via https://ossops.qualcomm.com/github/enable-repo/ with [Mark Matyas](mmatyas@qti.qualcomm.com) as POC.

More information: https://github.qualcomm.com/pages/osdo/handbook/qcom-github/docs/new-project-checklist/

## Getting in Contact

For support or inquiries, contact [Jairaj Solanki](jsolanki@qti.qualcomm.com).

## License

pkg-libdiag is licensed under the [BSD-3-Clause-Clear License](https://spdx.org/licenses/BSD-3-Clause-Clear.html). See [LICENSE.txt](LICENSE.txt) for the full license text.
