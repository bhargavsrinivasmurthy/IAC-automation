# Terraform Docker IaC Automation

## 1. Project Overview

This project demonstrates Infrastructure as Code (IaC) automation using Terraform, Docker, and GitHub Actions.

It implements automated infrastructure validation, separate staging and production environments, production approval protection, infrastructure drift detection, and Git-based rollback demonstration.

## 2. Technologies Used

- Terraform – Infrastructure as Code
- Docker – Container management
- Git and GitHub – Version control
- GitHub Actions – CI/CD automation
- YAML – Workflow configuration
- PowerShell – Local development commands

## 3. Project Structure

```text
iac-automation/
├── .github/
│   └── workflows/
│       ├── terraform-ci.yml
│       ├── terraform-cd.yml
│       └── terraform-drift.yml
├── environments/
│   ├── staging/
│   │   └── main.tf
│   └── production/
│       └── main.tf
├── main.tf
├── README.md
└── .gitignore
```

Additional Terraform lock files and configuration files may also be present.

## 4. Infrastructure

The Terraform configuration uses the Docker provider to manage:

- Docker images
- Docker containers
- Container port mappings

Nginx is used as the demonstration web server.

## 5. CI Pipeline

The Terraform CI workflow validates Terraform configurations.

The validation process includes:

- Terraform formatting checks
- Terraform initialization
- Terraform validation
- Staging and production configuration checks

## 6. CD Pipeline

The Terraform CD workflow supports separate staging and production environments.

### Staging

- Deploy demonstration infrastructure.
- Verify the Nginx web server.
- Destroy temporary demonstration resources.

### Production

- Uses GitHub Environment protection.
- Requires manual deployment approval.
- Runs the deployment workflow after approval.
- Verifies the Nginx response.
- Cleans up demonstration resources.

**Note:** The production workflow was tested as a temporary demonstration, not as a live customer production deployment.

## 7. Infrastructure Drift Detection

The Terraform Drift Detection workflow checks whether the deployed infrastructure differs from its expected Terraform configuration.

The demonstration successfully reported:

`Drift detected successfully`

The workflow also completed its cleanup step.

## 8. Rollback and Recovery

Git-based rollback was demonstrated using a separate branch:

`demo/rollback-recovery`

The demonstration included:

1. Creating a temporary test file.
2. Committing a simulated failed change.
3. Reverting the commit using `git revert`.
4. Verifying the working tree was clean.
5. Confirming that Git history was preserved.

**Important:** This demonstrates Git configuration rollback, not an automated Terraform infrastructure rollback.

## 9. Testing Results

| Component | Result |
|---|---|
| Terraform CI validation | Passed |
| Staging deployment | Passed |
| Staging Nginx verification | Passed |
| Staging cleanup | Passed |
| Production approval | Verified |
| Production demonstration | Passed |
| Production Nginx verification | Passed |
| Production cleanup | Passed |
| Drift detection | Passed |
| Git revert demonstration | Passed |

## 10. Prerequisites

Install the following tools:

- Git
- Terraform CLI
- Docker Desktop
- Visual Studio Code

A working Docker daemon is required for the Docker-based infrastructure demonstration.

## 11. Local Setup

Clone the repository:

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
```

Navigate into the project:

```bash
cd iac-automation
```

Check Terraform:

```bash
terraform version
```

Check Docker:

```bash
docker version
```

Initialize Terraform:

```bash
terraform init
```

Format Terraform files:

```bash
terraform fmt -recursive
```

Validate the root configuration:

```bash
terraform validate
```

Run `terraform plan` before applying any infrastructure changes.

## 12. Safety Considerations

- Review Terraform plans before applying changes.
- Protect production environments with approval rules.
- Never commit credentials or secrets.
- Keep Terraform state secure.
- Test infrastructure changes in staging first.
- Review drift before attempting remediation.
- Use Git revert to preserve version history when reversing committed changes.
- Verify the target environment before running Terraform apply or destroy.

## 13. Future Improvements

- Automated infrastructure recovery.
- Terraform remote state management.
- Automated security scanning.
- Infrastructure cost monitoring.
- Notifications for failed deployments.
- Enhanced monitoring and observability.

## 14. Project Outcome

This project demonstrates practical experience with Terraform, Docker, GitHub Actions, CI/CD automation, environment protection, drift detection, and version-controlled recovery.

It provides a foundation for further Cloud Infrastructure and DevOps engineering projects.