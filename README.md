# terraform-aws

A minimal Terraform project that launches a single Ubuntu EC2 instance on AWS. It is a learning spike for the basic Terraform workflow: `init`, `validate`, `apply`, inspect, `destroy`.

## What it creates

| Resource                   | Details                                                       |
| -------------------------- | ------------------------------------------------------------- |
| `aws_instance.app_server`  | `t2.micro` EC2 instance, tagged `Name = learn-terraform`      |
| AMI (looked up, not created) | Latest Canonical **Ubuntu 24.04 LTS (Noble)** amd64 image, gp3 SSD |

- **Region:** `eu-central-1` (Frankfurt)
- **Provider:** `hashicorp/aws` `~> 5.92`
- **Terraform:** `>= 1.2`

## Project layout

| File                                 | Purpose                                                   |
| ------------------------------------ | --------------------------------------------------------- |
| [main.tf](main.tf)                   | AWS provider, Ubuntu AMI lookup, and the EC2 instance     |
| [terraform.tf](terraform.tf)         | Required Terraform and provider versions                  |
| [install.md](install.md)             | Installing Terraform on Windows and configuring AWS access |
| [instructions.md](instructions.md)   | Notes on Terraform concepts and commands                  |

## Prerequisites

1. Terraform 1.2 or later — see [install.md](install.md).
2. An AWS account and credentials configured locally (for example with `aws configure`).

## Usage

```powershell
terraform init       # download the AWS provider
terraform fmt        # format the .tf files
terraform validate   # check the configuration
terraform apply      # review the plan, then type "yes" to create the instance
```

Inspect what was created:

```powershell
terraform state list
terraform show
```

Tear everything down when you are finished, to avoid AWS charges:

```powershell
terraform destroy
```

## Notes

- `t2.micro` is eligible for the AWS Free Tier on eligible accounts; outside the Free Tier it is billed hourly.
- State is stored locally in `terraform.tfstate`. Don't commit it — it can contain sensitive values. See [instructions.md](instructions.md#remote-state-with-hcp-terraform) for remote state.
