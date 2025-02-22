---
editable: false
sourcePath: en/_cli-ref/cli-ref/managed-services/backup/vm/index.md
---

# yc backup vm

Manage resources

#### Command Usage

Syntax: 

`yc backup vm <command>`

Aliases: 

- `vms`
- `resource`
- `resources`

#### Command Tree

- [yc backup vm list](list.md) — Lists available resources
- [yc backup vm list-tasks](list-tasks.md) — Show information about tasks
- [yc backup vm list-policies](list-policies.md) — Shows policies applied to the instance
- [yc backup vm list-applicable-policies](list-applicable-policies.md) — Shows policies that could be applied to the instance
- [yc backup vm get](get.md) — Show information about selected vm(-s)
- [yc backup vm delete](delete.md) — Delete the resource

#### Global Flags

| Flag | Description |
|----|----|
|`--profile`|<b>`string`</b><br/>Set the custom configuration file.|
|`--debug`|Debug logging.|
|`--debug-grpc`|Debug gRPC logging. Very verbose, used for debugging connection problems.|
|`--no-user-output`|Disable printing user intended output to stderr.|
|`--retry`|<b>`int`</b><br/>Enable gRPC retries. By default, retries are enabled with maximum 5 attempts.<br/>Pass 0 to disable retries. Pass any negative value for infinite retries.<br/>Even infinite retries are capped with 2 minutes timeout.|
|`--cloud-id`|<b>`string`</b><br/>Set the ID of the cloud to use.|
|`--folder-id`|<b>`string`</b><br/>Set the ID of the folder to use.|
|`--folder-name`|<b>`string`</b><br/>Set the name of the folder to use (will be resolved to id).|
|`--endpoint`|<b>`string`</b><br/>Set the Cloud API endpoint (host:port).|
|`--token`|<b>`string`</b><br/>Set the OAuth token to use.|
|`--impersonate-service-account-id`|<b>`string`</b><br/>Set the ID of the service account to impersonate.|
|`--format`|<b>`string`</b><br/>Set the output format: text (default), yaml, json, json-rest.|
|`-h`,`--help`|Display help for the command.|
