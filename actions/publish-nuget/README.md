# `publish-nuget` - **Github Action**

This action publishes a nuget package with the semantic version from GitVersion to GitHub NuGet registry.

## Input

* `project-path`:
    description: The path to the project to publish,
    required: true
* `token`:
    description: NuGet source api-key,
    default: ${{ github.token }},
    required: false

## Example Workflow File

```yaml
name: Publish NuGet

on:
  push:
    branches:
      - main

jobs:
  publish-nuget:
    runs-on: ubuntu-latest
      steps:
        - name: Publish NuGet
          uses: klanggames/actions-shared-workflows/actions/publish-nuget@v2
          with:
            project-path: ./src/Klang.Seed.YamlConfigParser
            token: ${{ secrets.GITHUB_TOKEN }}
```
