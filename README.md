# AWS Production Infrastructure with Terraform

Production-style AWS infrastructure built with Terraform using Infrastructure as Code (IaC).

## Architecture

The project provisions a highly available application foundation across multiple Availability Zones:

- VPC with CIDR `10.0.0.0/16`
- Public and private subnets across multiple Availability Zones
- Internet Gateway for public connectivity
- NAT Gateway for controlled private-subnet egress
- Application Load Balancer
- Auto Scaling Group for EC2 application instances
- IAM roles with least-privilege intent
- CloudWatch monitoring
- S3 backend-ready Terraform state design

## Goals

This project demonstrates how a cloud engineer can design, provision, secure, and operate AWS infrastructure through repeatable Terraform code rather than manual console configuration.

## Repository Structure

```text
.
├── architecture/
├── terraform/
│   ├── main.tf
│   ├── variables.tf
│   ├── outputs.tf
│   ├── versions.tf
│   ├── terraform.tfvars.example
│   └── modules/
├── .github/workflows/
├── docs/
└── README.md
```

## Security Practices

- Private application subnets
- Security groups with restricted traffic paths
- IAM roles instead of long-lived AWS access keys on EC2
- Encryption-ready storage configuration
- Terraform variables for environment-specific values
- Secrets excluded from version control

## Deployment

Prerequisites:

- Terraform >= 1.6
- AWS CLI
- An AWS account with appropriate permissions
- Configured AWS credentials

Typical workflow:

```bash
terraform init
terraform fmt -check -recursive
terraform validate
terraform plan
terraform apply
```

Never commit AWS access keys, private keys, `.tfstate` files, or real secret values.

## Production Considerations

This is a portfolio project modeled after production practices. Before real production use, add:

- Remote encrypted Terraform state with locking
- AWS Organizations/account separation
- CI/CD approval gates
- Centralized logging
- AWS WAF
- Backup and disaster-recovery policies
- Cost budgets and alerts
- Stronger IAM boundaries and policy review

## Technologies

AWS · Terraform · Linux · GitHub Actions · Infrastructure as Code · CloudWatch · IAM · VPC · EC2 · ALB · Auto Scaling

## Author

Samiullah B — Cloud Engineering / Cloud Security portfolio project.
