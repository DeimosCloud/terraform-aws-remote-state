# Remote State Locking S3
A terraform module to automate creation and configuration of backend using S3 bucket


## Usage example

```hcl
module "remote_state_locking" {
  source   = "git::https://gitlab.com/deimosdev/tooling/terraform-modules/terraform-remote-state"
  region   = var.aws_region
  use_lock = false
}
```

This creates a `backend.tf` file in the specified `backend_output_path` (default: project directory). Apply the configured backend by running `terraform init` again


## Doc generation

Code formatting and documentation for variables and outputs is generated using [pre-commit-terraform hooks](https://github.com/antonbabenko/pre-commit-terraform) which uses [terraform-docs](https://github.com/segmentio/terraform-docs).

Follow [these instructions](https://github.com/antonbabenko/pre-commit-terraform#how-to-install) to install pre-commit locally.

And install `terraform-docs` with
```bash
go get github.com/segmentio/terraform-docs
```
or
```bash
brew install terraform-docs.
```

## Contributing

Report issues/questions/feature requests on in the issues section.

Full contributing guidelines are covered [here](CONTRIBUTING.md).

## Requirements

| Name | Version |
|------|---------|
| terraform | >= 0.12 |
| aws | >= 2.52.0 |
| local | >= 1.2 |
| null | >= 2.1 |
| random | >= 2.1 |
| template | >= 2.1 |

## Providers

| Name | Version |
|------|---------|
| aws | >= 2.52.0 |
| null | >= 2.1 |
| random | >= 2.1 |
| template | >= 2.1 |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| backend\_output\_path | The default file to output backend configuration to | `string` | `"./backend.tf"` | no |
| bucket\_key | The Key to store bucket in | `string` | `"global/terrform.tfstate"` | no |
| bucket\_name | Name of bucket to be created | `string` | `""` | no |
| dynamo\_lock\_name | Name of Dynamo lock to be created for lock | `string` | `""` | no |
| enable\_versioning | enables versioning for objects in the S3 bucket | `bool` | `true` | no |
| force\_destroy | Whether to allow a forceful destruction of this bucket | `bool` | `false` | no |
| name\_prefix | Prefix for all created resources | `string` | `"tfstate-"` | no |
| region | Region to create S3 bucket in | `any` | n/a | yes |
| use\_lock | Whether to enable locking using dynamo\_db | `bool` | `true` | no |

## Outputs

| Name | Description |
|------|-------------|
| bucket\_name | bucket name |
| dynamodb\_table | Dynamodb name |
