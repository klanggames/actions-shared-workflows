# `publish-service` - **Github Action**

This action publishes a service docker image to GCR. By default it build `linux/amd64` and `linux/arm64` images. Tags are generated automatically using the input version and ref sha. `latest` tag is added for pushes to `main`.

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
            project_path: ./src/Klang.Seed.SomeServiceProject
            workload_identity_provider: <workload_identity>
            service_account: <service_account>
            images: |
              gcr.io/seed-209211/some-service
            service_version: 1.0.0
            platforms: "linux/amd64,linux/arm64"
```

Don't forget the specify `id-token: 'write'` job permission.
