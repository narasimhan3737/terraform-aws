# Installation

## Install Terraform on Windows

Install Terraform with [Chocolatey](https://chocolatey.org/) from an elevated (Administrator) shell:

```powershell
choco install terraform
```

Check that it installed:

```powershell
terraform -version
```

This project requires Terraform **1.2 or later** (see [terraform.tf](terraform.tf)).

## Configure AWS credentials

Terraform's AWS provider reads the same credentials as the AWS CLI. The simplest setup is:

```powershell
aws configure
```

You can also set environment variables instead:

```powershell
$env:AWS_ACCESS_KEY_ID     = "<your-access-key-id>"
$env:AWS_SECRET_ACCESS_KEY = "<your-secret-access-key>"
```

## Format `.tf` files

Rewrite all Terraform files in the current directory to the standard style:

```powershell
terraform fmt
```
