# `setup-gitversion` - **Github Action**

This action installs GitVersion, creates the default GitVersion.yml configuration file, and generates the full semantic version as output.

## Example Workflow File

### Outputs

* `fullSemVer` full semantic version; `major.minor.patch[-suffix+commit]` eg. if last tag `1.1.2` on main `1.1.3`, or on `somefeature` branch `1.1.3-somefeature0001+1`

```yaml
name: Some Action

on:
  push:
    branches:
      - main

jobs:
  create-tag:
    runs-on: ubuntu-latest
      steps:
        - name: Setup GitVersion
          uses: klanggames/actions-shared-workflows/actions/setup-gitversion@v2
```
