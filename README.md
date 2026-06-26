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

