# `publish-nuget` - **Github Action**

This action publishes a nuget package with the semantic version from GitVersion to GitHub NuGet registry.

## Input

* `project-path`:
  * description: The path to the project to publish,
  * required: true
* `version`:
  * description: The package version
  * required: true
* `token`:
  * description: NuGet source api-key,
  * default: ${{ github.token }},
  * required: false

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
        - uses: actions/checkout@v3
          with:
            fetch-depth: 0

        - uses: ./actions/setup-gitversion
          id: gitversion

        - uses: klanggames/actions-shared-workflows/actions/publish-nuget@v3
          with:
            project-path: ./src/Klang.Seed.YamlConfigParser
            version: ${{ steps.gitversion.outputs.fullSemVer }}
            token: ${{ secrets.GITHUB_TOKEN }}
```
