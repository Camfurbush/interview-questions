# Terraform Scenarios

This scenario is intended to walk you through the general process of how to use terraform.

## What are the first steps for working with Terraform

1. Download/write the terraform code
1. Run `terraform init` to download the state and providers for the code

## What are the main files for working with Terraform

1. Typically main.tf, variables.tf, outputs.tf, providers.tf are the most commonly used. As well as any .tfvars files that provide the values for variables, and the terraform.tfstate that contains the state

## How would you apply your Terraform code?

1. First you would open a terminal and ensure that it's in the same directory as your code.
1. Run `terraform init` to download providers and terraform state
1. You can perform a `terraform validate` to make sure the code will "compile" or interpolate correctly, but not required
1. Perform a `terraform plan` to show the planned changes for your code
1. Run `terraform apply` and type `yes` to apply the changes
