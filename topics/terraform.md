# Terraform

- [Terraform](#terraform)
  - [Can you explain what Infrastructure as Code and why its important](#can-you-explain-what-infrastructure-as-code-and-why-its-important)
  - [Whats the first command you run when start a terraform project](#whats-the-first-command-you-run-when-start-a-terraform-project)
  - [What are the most useful Terraform commands?](#what-are-the-most-useful-terraform-commands)
  - [What is the terraform state file and why is it important](#what-is-the-terraform-state-file-and-why-is-it-important)
  - [How would you store your terraform state](#how-would-you-store-your-terraform-state)
  - [What is a terraform backend](#what-is-a-terraform-backend)
  - [What is State File Locking?](#what-is-state-file-locking)

## Can you explain what Infrastructure as Code and why its important

- Infrastructure as Code or IaC is a process that DevOps teams should follow to have a more organized way of managing the infra. Instead of some throwaway scripts or manually configuring any cloud component, there should be a code repo where all of these will lie and any change in configuration should be done through it. It is wise to put it under source control also. This improves speed, consistency, and accountability.

## Whats the first command you run when start a terraform project

- terraform init to download the state and any providers

## What are the most useful Terraform commands?

- `terraform init` - initializes the current directory
- `terraform refresh` - refreshes the state file
- `terraform output` - views Terraform outputs
- `terraform apply` - applies the Terraform code and builds stuff
- `terraform destroy` - destroys what has been built by Terraform
- `terraform graph` - creates a DOT-formatted graph
- `terraform plan` - a dry run to see what Terraform will do

## What is the terraform state file and why is it important

- Terraform must store state about your managed infrastructure and configuration. This state is used by Terraform to map real world resources to your configuration, keep track of metadata, and to improve performance for large infrastructures. This state is stored by default in a local file named "terraform.tfstate".
- This is how terraform knows what actions to perform

## How would you store your terraform state

- You can store your terraform state in the local repository by default, but you should store it somewhere remotely like a backend or github (not for prod)

## What is a terraform backend

- Each Terraform configuration can specify a backend, which defines two main things:
  - Where operations are performed (terraform cloud/enterprise)
  - Where the state is stored
- Preferred backends are Terraform Cloud/Enterprise or Amazon S3 and DynamoDB

## What is State File Locking?

- State file locking is Terraform mechanism in which operations on a specific state file are blocked to avoid conflicts between multiple users performing the same process. When one user releases the lock, then only the other one can operate on that state. This helps in preventing state file corruption. This is a backend operation.
