# aws-secure-landing-zone-demo
Description: Secure multi-account AWS foundation: Organizations, OUs, IAM Identity Center, SCPs, GuardDuty/Security Hub enablement

# 01 - Secure Multi-Account Foundation (Landing Zone Lite)

# Overview / Business Context
Organizations need isolated accounts for security and compliance without credential sprawl. This lite landing zone sets up governance basics using AWS Organizations, centralized identity, and guardrails—mirroring on-prem separation of duties.

# Key AWS Services Used
- AWS Organizations + OUs
- IAM Identity Center (SSO)
- Service Control Policies (SCPs)
- GuardDuty, Security Hub, AWS Config, CloudTrail

# Architecture Diagram
![High-Level Architecture](diagrams/architecture.png)  
*(Embed your draw.io PNG/SVG here – drag image into GitHub or use relative path)*

# Design Decisions & Justifications
- OU structure rationale (Workloads vs Security – blast radius reduction).
- SCP choices (deny dangerous actions – lessons from compliance experience).
- SSO over local IAM (reduces sprawl, audit-friendly).
- Trade-offs: Manual setup vs full Control Tower (lite for demo, scalable later).

# Deployment Steps
1. Enable AWS Organizations all features.
2. Create OUs (Security, Workloads).
3. Move member account to Workloads OU.
4. Set up IAM Identity Center + permission sets (Can alternatively use AD/Entra ID/Okta based on your experience)
5. Create/attach SCPs.
6. Enable org-wide CloudTrail, GuardDuty, etc.
(Include numbered list + console screenshots or CLI snippets)

# Validation / Testing
- SSO portal login success (screenshot: portal showing accounts).
- Console access in sandbox-dev account (screenshot).
- Test SCP deny (e.g., try creating IAM user → fails).

# IaC Code
- SCP JSON policies (in `/policies/` folder).
- (Future: Add Terraform/CloudFormation modules here)

# Cost & Security Notes
- Cost: ~$0 (Free Tier – GuardDuty/Config minimal if no findings).
- Security: SCPs enforce least-privilege, centralized logging/monitoring.

# Lessons Learned / On-Prem Tie-In
- Similar to AD GPOs + centralized SIEM/logging.
- Highlights shift from per-system admins to federated access.
## Future Enhancements
- Delegate GuardDuty/Security Hub to Security OU account.
- Automate with AWS Control Tower or Terraform.
