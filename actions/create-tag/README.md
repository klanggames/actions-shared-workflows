# `create-tag` - **Github Action**

This action tags a commit with  the current semantic version using GitVersion.

## Input

* `use-latest`: (optional) whether to create the `latest` tag, default: true

## Example Workflow File

```yaml
name: Create Tag

on:
  push:
    branches:
      - main

jobs:
  create-tag:
    runs-on: ubuntu-latest
      steps:
        - name: Create Tag
          uses: klanggames/actions-shared-workflows/actions/create-tag@v2
```
