# `checkout-and-yarn` - **Github Action**

This action checks out the commit, and runs build and test on it

## Input

* `project-path`: (optional) path to the project or solution

## Example Workflow File

```yaml
name: Build and Test

on:
    pull_request

jobs:
    build-and-test:
        runs-on: ubuntu-latest
        steps:
            - name: Build and Test
              uses: klanggames/actions-shared-workflows/actions/build-and-test@main
              with:
                  project-path: ./src
```
