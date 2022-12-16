# `publish-npm` - **Github Action**

This action publishes an unity compatible npm package with the semantic version from GitVersion.

## Input

* `project-path`:
  * description: The path to the project to publish,
  * required: true
* `version`:
  * description: The package version
  * required: true
* `output-folder`:
  * description: The path to the npm output folder,
  * default: ${{ github.workspace }}/.npm,
    required: false
* `tool-version`:
  * description: Version of unity npm packager tool,
  * default: 0.1.4,
  * required: false
* `registry`:
  * description: Target NPM registry,
  * default: <https://npm.pkg.github.com>,
  * required: false
* `node-auth-token`:
  * description: Node authentication token,
  * default: ${{ github.token }},
  * required: false
* `tool-token`:
  * description: github token used to download the unity npm packager tool,
  * required: true

## Example Workflow File

```yaml
name: Publish NPM

on:
  push:
    branches:
      - main

jobs:
  publish-npm:
    runs-on: ubuntu-latest
      steps:
        - uses: actions/checkout@v3
          with:
            fetch-depth: 0

        - uses: ./actions/setup-gitversion
          id: gitversion

        - name: Publish NPM
          uses: klanggames/actions-shared-workflows/actions/publish-npm@mv2
          with:
            project-path: ./src/Klang.Seed.YamlConfigParser
            version: ${{ steps.gitversion.outputs.fullSemVer }}s
            tool-token: ${{ secrets.GITHUB_TOKEN }}
```
