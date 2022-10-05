# `publish-grpc-clients` - **Github Action**

This action publishes gRPC client packages form a service project.

## Input

* `grpc-service-name`: grpc service nme
* `project-path`: path the the services project
* `tool-download-token`: PAT to download tools from GitHub releases
* `nuget-auth-token`: PAT to read and write NuGet packages from/to GitHub NuGet registry
* `grpc-client-generator-version`: (optional) gRPC client generator tool version
* `channel-provider-version`: (optional) GRPCChannelProvider package version
* `unity-npm-packager-version`: (optional) unity-npm-packager tool version
* `service-name`: service name use in header for routing traffic
* `environment-port`: (optional) environment port
* `world-port`: (optional) world port
* `sector-port`: (optional) sector port
* `output-path`: (optional) output folder
* `output-path`: (optional) output folder

## Example Workflow File

```yaml
steps:
  - name: Checkout repository
    uses: actions/checkout@v3
    with:
      fetch-depth: 0

  - name: Setup GitVersion
    uses: klanggames/actions-shared-workflows/actions/setup-gitversion@v1
    id: gitversion

  - name: Publish gRPC Client/Proto Packages
    uses: klanggames/actions-shared-workflows/actions/publish-grpc-clients@v1
    with:
      project-path: <PATH_TO_PROJECT_FILE>
      tool-download-token: ${{ <GITHUB_PAT_WITH_RELEASE_READ_PERMISSIONS> }}
      nuget-auth-token: ${{ <GITHUB_PAT_WITH_NUGET_READ_WRITE_PERMISSIONS> }}
      service-name: <SERVICE_NAME>
      grpc-service-name: <GRPC_SERVICE_NAME>
      environment-port: <PORT>
      package-version: 1.0.0
```
