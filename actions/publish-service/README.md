# `publish-service` - **Github Action**

This action publishes a service docker image to GCR. By default it build `linux/amd64` and `linux/arm64` images.

## Example Workflow File

```yaml
name: Publish Service

on:
  push:
    branches:
      - main

jobs:
  publish-nuget:
    permissions:
      contents: 'read'
      id-token: 'write'
    runs-on: ubuntu-latest
      steps:
        - name: Publish Service Docker Image
          uses: klanggames/actions-shared-workflows/actions/publish-service@v1
          with:
            project-path: ./src/Klang.Seed.SomeServiceProject
            workload_identity_provider: <workload_identity>
            service_account: <service_account>
            tags: |
              gcr.io/seed-209211/some-service:1.0.0
              gcr.io/seed-209211/some-service:latest
            service_version: 1.0.0
            platforms: "linux/amd64,linux/arm64"
```

Don't forget the specify `id-token: 'write'` job permission.
