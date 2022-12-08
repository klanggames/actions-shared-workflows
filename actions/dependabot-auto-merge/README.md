# `dependabot-auto-merge` - **Github Action**

auto-merge dependabot PRs when only minor

## Input

* `github-token`: (optional) the github token
* `update-type`: (optional) default `version-update:semver-minor`

## Example Workflow File

```yaml
name: Dependabot Auto Merge
on:
  pull_request:
  check_suite:
    types:
      - completed

# no other workflow can run at the same time
concurrency:
  group: ${{ github.workflow }}-${{ github.ref }}
  cancel-in-progress: ${{ startsWith(github.ref, 'refs/pull/') }}

permissions:
  pull-requests: write
  contents: write

jobs:
  dependabot-auto-merge:
    runs-on: ubuntu-latest
    if: ${{ github.actor == 'dependabot[bot]' }}
    steps:
      - uses: klanggames/actions-shared-workflows/actions/dependabot-auto-merge@v2
```
