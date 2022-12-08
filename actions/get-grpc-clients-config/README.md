# `get-grpc-clients-config` - **Github Action**

get the gRPC client config from an `.env` file

## Input

* `github-token`: (optional) the github token
* `path`: (optional) path to .env file, default `.env`

## Outputs

* grpc-services: json array for grpc service names, used as matrix for publihsing jobs
* environment-port:
* sharedsvc-port:
* world-port:
* service-name:
* sector-port:
* grpc-channel-provider-version: default 10.0.0

## Example Workflow File

```yaml
name: Publish gRPC clients
on:
  pull_request:

concurrency:
  group: ${{ github.workflow }}-${{ github.ref }}
  cancel-in-progress: ${{ startsWith(github.ref, 'refs/pull/') }}

permissions:
  contents: read

jobs:
  config:
    runs-on: ubuntu-latest
    outputs:
      grpc-services: ${{ steps.config.outputs.grpc-services }}
      environment-port: ${{ steps.config.outputs.environment-port }}
      sharedsvc-port: ${{ steps.config.outputs.sharedsvc-port }}
      world-port: ${{ steps.config.outputs.world-port }} 
      service-name: ${{ steps.config.outputs.service-name }}
      sector-port:  ${{ steps.config.outputs.sector-port }}
      grpc-channel-provider-version: ${{ steps.config.outputs.grpc-channel-provider-version }}
      
    steps:
      - uses: klanggames/actions-shared-workflows/actions/get-grpc-clients-config@v2
        id: config
```