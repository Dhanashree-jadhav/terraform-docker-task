# Terraform Docker Container Setup

This repository contains a Terraform configuration to provision an NGINX Docker container.

## Steps
1. `terraform init` - Initialize the Terraform working directory.
2. `terraform plan` - Preview the execution plan.
3. `terraform apply` - Create the NGINX container (verify at `http://localhost:8080`).
4. `terraform state list` - Check managed resources.
5. `terraform destroy` - Clean up resources.

## Deliverables
- `main.tf`: Terraform configuration.
- `execution_logs.txt`: Logs of Terraform and Docker commands.

## Requirements
- Terraform installed.
- Docker Desktop running.