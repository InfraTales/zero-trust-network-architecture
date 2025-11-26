# Cost Analysis (₹)

This document provides cost estimates for the **Zero-Trust Network Architecture** in **Indian Rupees (₹)**.

## Production Environment

At production scale (enterprise-wide deployment), the architecture typically costs:

| Service | Monthly Cost (₹) | Notes |
|---------|------------------|-------|
| **AWS Verified Access** | ₹20,000–40,000 | Per-user access verification |
| **Network Firewall** | ₹30,000–50,000 | Inspection and filtering |
| **PrivateLink** | ₹15,000–25,000 | Private service endpoints |
| **IAM Identity Center** | ₹5,000–10,000 | SSO and identity federation |
| **CloudWatch** | ₹8,000–15,000 | Logging and monitoring |
| **WAF** | ₹10,000–20,000 | Application layer protection |
| **Secrets Manager** | ₹3,000–5,000 | Credential management |
| **Total** | **₹90,000–165,000** | ~$1,125–2,060/month |

## Development Environment

For dev/staging environments:

| Environment | Approx Monthly Cost (₹) | Notes |
|------------|--------------------------|-------|
| Dev | ₹20,000–35,000 | Limited users, basic policies |
| Staging | ₹45,000–75,000 | Production-like, fewer endpoints |
| Production | ₹90,000–165,000 | Full enterprise deployment |

## Cost Optimization Strategies

- **Consolidate endpoints** – Reduce PrivateLink endpoints where possible
- **Policy optimization** – Efficient firewall rules reduce processing
- **Right-size WAF** – Match capacity units to actual traffic
- **Identity federation** – Use existing IdP to reduce IAM costs
- **Log retention** – Implement tiered retention policies

## Related Documentation

See `ARCHITECTURE.md` for service details and `DEPLOYMENT.md` for configuration options.
