# Terraform Notes

Notes on the core Terraform concepts and commands used in this project.

## Resource address

```hcl
resource "aws_instance" "app_server" {
}
```

| Part                   | Meaning                                    |
| ---------------------- | ------------------------------------------ |
| `aws_instance`         | Resource **type**                          |
| `app_server`           | Resource **name**                          |
| `aws_instance.app_server` | Resource **address** (type + name), used to refer to this resource elsewhere |

## Workflow

### 1. Initialize — `terraform init`

```powershell
terraform init
```

- Downloads and installs the providers the configuration needs.
- Saves the providers in the `.terraform/` subdirectory.
- Creates `.terraform.lock.hcl`, which records the exact provider versions used. Commit this file so everyone uses the same versions.

### 2. Validate — `terraform validate`

```powershell
terraform validate
```

- Checks that the configuration is syntactically valid and internally consistent.
- Points out the problem and suggests a fix when the configuration is invalid.

### 3. Create infrastructure — `terraform apply`

```powershell
terraform apply
```

- First creates an execution plan showing what will change.
- You then approve (`yes`) or reject the plan before anything is created.

### 4. Inspect state

```powershell
terraform state list
```

- Lists the resources tracked in the workspace's state.

```powershell
terraform show
```

- Shows the full current state of the workspace, including resource attributes.

### 5. Destroy infrastructure — `terraform destroy`

```powershell
terraform destroy
```

- Removes every resource managed by this configuration, after showing a plan and asking for approval.

## Remote state with HCP Terraform

By default, state is stored locally in `terraform.tfstate`. [HCP Terraform](https://developer.hashicorp.com/terraform/cloud-docs) can store state remotely instead, so a team can share it safely.
