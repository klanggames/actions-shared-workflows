# `build-push-docker` - **Github Action**

This action publishes a docker image to Google Artifact Registry. By default it builds `linux/amd64` and `linux/arm64` images. Tags are generated automatically using the input version and ref sha. `latest` tag is added for pushes to `main`.

## Example Workflow File

```yaml
name: Publish Docker

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
        - name: Publish Docker Image
          uses: klanggames/actions-shared-workflows/actions/build-push-docker-service@v2
          with:
            workload_identity_provider: <workload_identity>
            service_account: <service_account>
            images: europe-west1-docker.pkg.dev/klang-images-shr/prototype-gcloud-artifact-push/prototype-gcloud-artifact-push
            version: 1.0.0
            platforms: "linux/amd64,linux/arm64"
```

Don't forget the specify `id-token: 'write'` job permission.
