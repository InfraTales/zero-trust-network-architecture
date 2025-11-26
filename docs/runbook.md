# Runbook

Operational guide for deploying, operating, and maintaining the **Zero-Trust Network Architecture**.

## 1. Deployment

### Prerequisites

- AWS CLI configured with appropriate credentials
- Terraform 1.5+ installed
- Identity provider configured (Okta, Azure AD, etc.)

### Deploy Steps

```bash
# Initialize Terraform
terraform init

# Plan deployment
terraform plan -var="environment=prod" -out=tfplan

# Apply deployment
terraform apply tfplan
```

## 2. Identity Configuration

### Add New User

1. Create user in identity provider
2. Assign to appropriate groups
3. Groups map to AWS IAM roles
4. User can access via Verified Access

### Configure Conditional Access

```hcl
# Example: Require MFA for sensitive resources
resource "aws_verifiedaccess_trust_provider" "mfa_required" {
  policy_reference_name = "mfa-required"
  trust_provider_type   = "user"
  user_trust_provider_type = "iam-identity-center"
}
```

## 3. Network Policies

### Add Micro-Segment

1. Create new security group
2. Define ingress/egress rules
3. Associate with workloads
4. Update firewall policies

### Update Firewall Rules

```bash
# Deploy firewall rule changes
terraform apply -target=aws_networkfirewall_rule_group.main
```

## 4. Monitoring

### Key Metrics to Watch

- **Authentication failures**: Potential brute force
- **Policy denials**: Misconfiguration or attack
- **Anomalous access patterns**: Compromised credentials
- **Network traffic**: Lateral movement attempts

### Dashboards

Pre-configured dashboards for:

- Access request overview
- Policy enforcement status
- Network traffic analysis
- Security findings

## 5. Incident Response

### Suspected Compromise

1. Isolate affected workload (update security group)
2. Revoke user sessions
3. Review CloudTrail logs
4. Engage incident response team

### Emergency Access Revocation

```bash
# Revoke all sessions for user
aws identitystore delete-user --identity-store-id <id> --user-id <user-id>
```

## 6. Maintenance

### Regular Tasks

- Review access policies quarterly
- Rotate service credentials monthly
- Update firewall rules as needed
- Audit user access annually

### Teardown

```bash
terraform destroy -var="environment=dev"
```

> For troubleshooting common issues, see `docs/troubleshooting.md`.
