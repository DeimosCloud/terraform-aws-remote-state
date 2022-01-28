# Terraform AWS Remote State Module
A terraform module to automate creation and configuration of backend using S3 bucket

## Usage

```hcl
provider "aws" {
  region  = "us-east-2" # Bucket is created in the same region
}

module "remote_state_locking" {
  source   = "git::https://gitlab.com/deimosdev/tooling/terraform-modules/terraform-aws-remote-state"
  use_lock = false
}
```

This creates a `backend.tf` file in the specified `backend_output_path` (default: project directory). Apply the configured backend by running `terraform init` again

## Contributing

Report issues/questions/feature requests on in the issues section.

Full contributing guidelines are covered [here](CONTRIBUTING.md).

<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 0.12 |
| <a name="requirement_aws"></a> [aws](#requirement\_aws) | >= 3.0.0, < 4.0.0 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | 3.74.0 |
| <a name="provider_local"></a> [local](#provider\_local) | 2.1.0 |
| <a name="provider_random"></a> [random](#provider\_random) | 3.1.0 |
| <a name="provider_template"></a> [template](#provider\_template) | 2.2.0 |

## Modules

No modules.

## Resources

| Name | Type |
|------|------|
| [aws_dynamodb_table.terraform_locks](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/dynamodb_table) | resource |
| [aws_s3_bucket.remote_state](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/s3_bucket) | resource |
| [local_file.remote_state_locks](https://registry.terraform.io/providers/hashicorp/local/latest/docs/resources/file) | resource |
| [random_id.this](https://registry.terraform.io/providers/hashicorp/random/latest/docs/resources/id) | resource |
| [aws_region.current](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/region) | data source |
| [template_file.remote_state](https://registry.terraform.io/providers/hashicorp/template/latest/docs/data-sources/file) | data source |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_backend_output_path"></a> [backend\_output\_path](#input\_backend\_output\_path) | The default file to output backend configuration to | `string` | `"./backend.tf"` | no |
| <a name="input_bucket_key"></a> [bucket\_key](#input\_bucket\_key) | The Key to store bucket in | `string` | `"global/terrform.tfstate"` | no |
| <a name="input_bucket_name"></a> [bucket\_name](#input\_bucket\_name) | Name of bucket to be created. If not provided name is generated from name\_prefix appended with a random string | `string` | `""` | no |
| <a name="input_dynamo_lock_name"></a> [dynamo\_lock\_name](#input\_dynamo\_lock\_name) | Name of Dynamo lock to be created for lock. If not provided name is generated from name\_prefix appended with a random string | `string` | `""` | no |
| <a name="input_enable_versioning"></a> [enable\_versioning](#input\_enable\_versioning) | enables versioning for objects in the S3 bucket | `bool` | `true` | no |
| <a name="input_force_destroy"></a> [force\_destroy](#input\_force\_destroy) | Whether to allow a forceful destruction of this bucket | `bool` | `false` | no |
| <a name="input_name_prefix"></a> [name\_prefix](#input\_name\_prefix) | Prefix for all created resources | `string` | `"tfstate-"` | no |
| <a name="input_use_lock"></a> [use\_lock](#input\_use\_lock) | Whether to enable locking using dynamo\_db | `bool` | `true` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_bucket_name"></a> [bucket\_name](#output\_bucket\_name) | bucket name |
| <a name="output_dynamodb_table"></a> [dynamodb\_table](#output\_dynamodb\_table) | Dynamodb name |
<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->