# terraform_aws_security_group

Module `terraform_aws_security_group` is a Terraform module to create AWS
security groups. However, it also helps manage ICMP rules in the sense
that will create, if desired, a policy that denies all ICMP *except* for
ICMP type 3, which helps manage path MTU discovery. It also will tag your
security group for you, if desired.

Usage Example:

    module "security_group" {
      source       = "github.com/paybyphone/terraform_aws_security_group?ref=VERSION"
      vpc_id       = "${var.vpc_id}"
      project_path = "your/project"
    }



## Inputs

| Name | Description | Default | Required |
|------|-------------|:-----:|:-----:|
| project_path | The path of the project in VCS. | - | yes |
| vpc_id | The ID of the VPC. | - | yes |
| allow_icmp | Controls whether or not to allow ALL ICMP. If this is set to "false", ICMP type 3 (host unreachable) is still allowed to facilitate path MTU discovery and other host path issues. | `true` | no |
| icmp_action | Private variable for boolean type conversion. | `<map>` | no |

## Outputs

| Name | Description |
|------|-------------|
| security_group_id | The ID of the created security group. |

