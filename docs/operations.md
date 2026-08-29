# Operations Runbook

## Validate before changes

```bash
terraform fmt -check -recursive
terraform init -backend=false
terraform validate
terraform plan
```

## Change workflow

1. Create a feature branch.
2. Make the smallest infrastructure change possible.
3. Run format and validation locally.
4. Review the Terraform plan.
5. Open a pull request and let CI validate the configuration.
6. Apply only after reviewing the plan and required approvals.

## Failure handling

- Check the failing Terraform resource first.
- Inspect AWS service events and CloudWatch logs where applicable.
- Avoid manual console changes that create configuration drift.
- If drift occurs, import or reconcile the resource before the next apply.

## Cost controls

NAT Gateways, load balancers, and continuously running compute can create charges. Destroy development resources when they are not needed and use budgets/alerts for real AWS accounts.
