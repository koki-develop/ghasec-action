# ghasec-action

A GitHub Action to run [ghasec](https://github.com/koki-develop/ghasec), a security linter for GitHub Actions workflows.

## Usage

<!-- x-release-please-start-version -->
```yaml
- uses: koki-develop/ghasec-action@v1.0.1
```
<!-- x-release-please-end -->

### Inputs

| Name | Description | Default |
| --- | --- | --- |
| `version` | Version of ghasec to install (e.g. `X.Y.Z`, `vX.Y.Z`, or `latest`) | `latest` |
| `token` | GitHub token for API requests (to avoid rate limiting) | `${{ github.token }}` |
| `online` | Enable rules that require network access | `false` |
| `args` | Additional arguments to pass to ghasec | |

### Example

<!-- x-release-please-start-version -->
```yaml
name: ghasec

on:
  pull_request:
  push:
    branches: [main]

jobs:
  ghasec:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v6
      - uses: koki-develop/ghasec-action@v1.0.1
```
<!-- x-release-please-end -->

## License

[MIT](./LICENSE)
