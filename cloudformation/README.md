# AWS Network Foundation — CloudFormation

A CloudFormation version of the core AWS networking foundation used in the portfolio. This project demonstrates AWS CloudFormation, VPC design, CIDR planning, public/private subnets, route tables, Internet Gateway, NAT Gateway, Security Groups, and outputs.

## Architecture

```text
Internet
   |
Internet Gateway
   |
Public Subnets (2 AZs)
   |        |
  ALB      NAT Gateway
             |
       Private App Subnets
```

## Covered skills

- AWS CloudFormation
- VPC
- CIDR `10.20.0.0/16`
- Public/private subnet design
- Route tables and routes
- Internet Gateway
- NAT Gateway
- Security Groups
- Multi-AZ networking
- Infrastructure as Code

## Deploy

```bash
aws cloudformation validate-template --template-body file://network-stack.yaml
aws cloudformation deploy --template-file network-stack.yaml --stack-name cloud-engineer-network-lab
```

Delete when finished to avoid unnecessary AWS charges:

```bash
aws cloudformation delete-stack --stack-name cloud-engineer-network-lab
```

Never commit credentials or secrets.
