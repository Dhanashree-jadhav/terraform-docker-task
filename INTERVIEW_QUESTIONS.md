# Terraform FAQ

Below are common questions about Terraform and Infrastructure as Code (IaC), answered with examples tied to provisioning an NGINX Docker container.

## 1. What is IaC?
**Answer:** Infrastructure as Code (IaC) is managing infrastructure using code instead of manual processes, enabling automation and consistency.

- **Example:** In this project, `main.tf` defines an NGINX container. Running `terraform apply` automates its creation, avoiding manual Docker commands like `docker run`.

## 2. How does Terraform work?
**Answer:** Terraform uses declarative code to define infrastructure, compares it to the current state, and applies changes via providers.

- **Example:** Here, `terraform init` fetched the Docker provider, `terraform plan` previewed the NGINX container creation, and `terraform apply` executed it.

## 3. What is Terraform State File?
**Answer:** The `terraform.tfstate` file tracks the current state of resources managed by Terraform.

- **Example:** After applying `main.tf`, `terraform state list` showed `docker_image.nginx` and `docker_container.nginx`, reflecting the state file’s contents.

## 4. Difference between `apply` and `plan`?
**Answer:** `terraform plan` previews changes; `terraform apply` executes them.

- **Example:** `terraform plan` showed the NGINX container would be created, while `terraform apply` actually started it on port 8080.

## 5. What are Terraform Providers?
**Answer:** Providers are plugins that let Terraform manage specific platforms (e.g., Docker, AWS).

- **Example:** The `kreuzwerker/docker` provider in `main.tf` enabled Terraform to pull the NGINX image and run a container.

## 6. What is Resource Dependency?
**Answer:** A dependency is when one resource relies on another, managed implicitly or explicitly.

- **Example:** The `docker_container.nginx` resource depends on `docker_image.nginx` because it uses `image = docker_image.nginx.name`.

## 7. How do you handle secret variables?
**Answer:** Use variables, environment variables, or secret management tools to avoid hardcoding secrets.

- **Example:** If NGINX needed an API key, define `variable "api_key" { sensitive = true }` and pass it via `TF_VAR_api_key=secret123`.

## 8. Explain the Benefits of Terraform
**Answer:** Terraform automates, ensures consistency, supports versioning, and works across platforms.

- **Example:** This project automated NGINX deployment, ensuring the same setup on any machine, tracked via Git, and could extend to AWS with a different provider.