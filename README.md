# Remote State Locking
A terraform module to automate creation and configuration of backend using S3 bucket


## Usage example

```hcl
module "remote_state_locking" {
  source   = "git::https://gitlab.com/deimosdev/tooling/terraform-remote-state"
  region   = var.aws_region
  use_lock = false
}
```

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
| bucket\_name | Name of bucket. It is generated using random resource is not specified with prefix `terraform-state`| `string` | `""` | no |
| dynamo\_lock\_name | Name of bucket. It is generated using random resource is not specified with prefix `terraform-state-lock` | `string` | `""` | no |
| enable\_versioning | enables versioning for objects in the S3 bucket | `bool` | `true` | no |
| force\_destroy | Whether to allow a forceful destruction of this bucket | `bool` | `false` | no |
| region | Region of for remote state bucket | `any` | n/a | yes |
| use\_lock | Whether to enable locking using dynamo\_db | `bool` | `true` | no |

## Outputs

| Name | Description |
|------|-------------|
| bucket\_name | bucket name |
| dynamodb\_table | Dynamodb name |

