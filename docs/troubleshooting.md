# Troubleshooting

Common issues and resolutions for the **Zero-Trust Network Architecture**.

## Access Issues

### 1. User Cannot Authenticate

**Symptom:** User gets authentication error.

**Resolution:**
- Verify user exists in identity provider
- Check MFA is properly configured
- Verify group membership
- Review IAM Identity Center logs

### 2. Access Denied After Authentication

**Symptom:** User authenticates but cannot access resource.

**Resolution:**
- Check Verified Access policy conditions
- Verify user's device posture meets requirements
- Review conditional access policies
- Check resource-level permissions

### 3. Intermittent Access Failures

**Symptom:** Access works sometimes but not always.

**Resolution:**
- Check session token expiration
- Verify network connectivity
- Review rate limiting policies
- Check for policy conflicts

## Network Issues

### 4. Traffic Blocked by Firewall

**Symptom:** Legitimate traffic being dropped.

**Resolution:**
- Review Network Firewall logs
- Check rule group priorities
- Verify stateful rule configuration
- Add exception rules if needed

### 5. PrivateLink Connection Failures

**Symptom:** Cannot connect to private endpoints.

**Resolution:**
- Verify endpoint exists and is available
- Check security group allows traffic
- Verify DNS resolution
- Check VPC endpoint policies

### 6. Micro-Segmentation Too Restrictive

**Symptom:** Workloads cannot communicate.

**Resolution:**
- Review security group rules
- Check for missing egress rules
- Verify CIDR ranges are correct
- Use VPC Flow Logs to diagnose

## Policy Issues

### 7. Policy Not Taking Effect

**Symptom:** New policy doesn't seem to apply.

**Resolution:**
- Check policy attachment
- Verify policy syntax
- Review policy evaluation order
- Clear cached credentials

### 8. Too Many Policy Denials

**Symptom:** High volume of access denials.

**Resolution:**
- Review denial reasons in logs
- Check for overly restrictive policies
- Verify user group assignments
- Consider policy exceptions

## Monitoring Issues

### 9. Missing Audit Logs

**Symptom:** Expected events not appearing in logs.

**Resolution:**
- Verify CloudTrail is enabled
- Check log delivery to S3
- Review CloudWatch log groups
- Verify IAM permissions for logging

## Cost Issues

### 10. Unexpected High Costs

**Symptom:** Monthly bill higher than estimates.

**Resolution:**
- Review Verified Access usage
- Check Network Firewall data processed
- Optimize PrivateLink endpoints
- Review CloudWatch log retention

> For architecture details, see the project README.
