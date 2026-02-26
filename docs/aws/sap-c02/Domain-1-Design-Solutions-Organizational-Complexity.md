# AWS Certified Solutions Architect - Professional (SAP-C02) Domain 1
## Design Solutions for Organizational Complexity

**Official Exam Guide:** <a href="https://docs.aws.amazon.com/aws-certification/latest/examguides/solutions-architect-professional-02-domain1.html" target="_blank">Domain 1: Design Solutions for Organizational Complexity</a>

**Skill Builder:** <a href="https://skillbuilder.aws/category/exam-prep/solutions-architect-professional-SAP-C02" target="_blank">AWS Certified Solutions Architect - Professional Exam Prep</a>

---

## Domain Overview

Domain 1 (26% of exam) focuses on architecting complex network connectivity, prescribing security controls, designing reliable architectures, multi-account environments, and cost optimization strategies.

---

## Task 1.1: Architect network connectivity strategies

**Knowledge Areas:**
- AWS Global Infrastructure
- AWS networking (VPC, Direct Connect, VPN, transitive routing, container networking)
- Hybrid DNS (Route 53 Resolver, on-premises DNS integration)
- Network segmentation (subnetting, IP addressing, VPC connectivity)
- Network traffic monitoring

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/" target="_blank">Amazon VPC User Guide</a>
- <a href="https://docs.aws.amazon.com/directconnect/latest/UserGuide/" target="_blank">AWS Direct Connect User Guide</a>
- <a href="https://docs.aws.amazon.com/vpn/latest/s2svpn/" target="_blank">AWS Site-to-Site VPN</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/tgw/" target="_blank">AWS Transit Gateway</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver.html" target="_blank">Amazon Route 53 Resolver</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/peering/" target="_blank">VPC Peering</a>

---

## Task 1.2: Prescribe security controls

**Knowledge Areas:**
- IAM and IAM Identity Center
- Route tables, security groups, network ACLs
- Encryption keys and certificate management (KMS, ACM)
- AWS security tools (CloudTrail, IAM Access Analyzer, Security Hub, Inspector)

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/IAM/latest/UserGuide/" target="_blank">AWS IAM User Guide</a>
- <a href="https://docs.aws.amazon.com/singlesignon/latest/userguide/" target="_blank">AWS IAM Identity Center</a>
- <a href="https://docs.aws.amazon.com/kms/latest/developerguide/" target="_blank">AWS Key Management Service</a>
- <a href="https://docs.aws.amazon.com/acm/latest/userguide/" target="_blank">AWS Certificate Manager</a>
- <a href="https://docs.aws.amazon.com/awscloudtrail/latest/userguide/" target="_blank">AWS CloudTrail</a>
- <a href="https://docs.aws.amazon.com/securityhub/latest/userguide/" target="_blank">AWS Security Hub</a>

---

## Task 1.3: Design reliable and resilient architectures

**Knowledge Areas:**
- Recovery time objectives (RTOs) and recovery point objectives (RPOs)
- Disaster recovery strategies (Elastic Disaster Recovery, pilot light, warm standby, multi-site)
- Data backup and restoration

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/drs/latest/userguide/" target="_blank">AWS Elastic Disaster Recovery</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/" target="_blank">AWS Well-Architected Reliability Pillar</a>
- <a href="https://docs.aws.amazon.com/aws-backup/latest/devguide/" target="_blank">AWS Backup</a>

---

## Task 1.4: Design a multi-account AWS environment

**Knowledge Areas:**
- AWS Organizations and AWS Control Tower
- Multi-account event notifications
- AWS resource sharing across environments

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/organizations/latest/userguide/" target="_blank">AWS Organizations User Guide</a>
- <a href="https://docs.aws.amazon.com/controltower/latest/userguide/" target="_blank">AWS Control Tower User Guide</a>
- <a href="https://docs.aws.amazon.com/ram/latest/userguide/" target="_blank">AWS Resource Access Manager</a>

---

## Task 1.5: Determine cost optimization and visibility strategies

**Knowledge Areas:**
- AWS cost monitoring tools (Trusted Advisor, Pricing Calculator, Cost Explorer, Budgets)
- AWS purchasing options (Reserved Instances, Savings Plans, Spot Instances)
- AWS rightsizing tools (Compute Optimizer, S3 Storage Lens)

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html" target="_blank">AWS Cost Explorer</a>
- <a href="https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-managing-costs.html" target="_blank">AWS Budgets</a>
- <a href="https://docs.aws.amazon.com/awssupport/latest/user/trusted-advisor.html" target="_blank">AWS Trusted Advisor</a>
- <a href="https://docs.aws.amazon.com/compute-optimizer/latest/ug/" target="_blank">AWS Compute Optimizer</a>

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/vpc/faqs/" target="_blank">Amazon VPC FAQs</a>
- <a href="https://aws.amazon.com/directconnect/faqs/" target="_blank">AWS Direct Connect FAQs</a>
- <a href="https://aws.amazon.com/organizations/faqs/" target="_blank">AWS Organizations FAQs</a>
- <a href="https://aws.amazon.com/iam/faqs/" target="_blank">AWS IAM FAQs</a>

---

## Study Tips

1. **Master hybrid connectivity** - Understand Transit Gateway for hub-and-spoke architectures, Direct Connect with VPN backup, and Route 53 Resolver for hybrid DNS.

2. **Learn multi-account strategies** - AWS Organizations with SCPs, Control Tower landing zones, and Resource Access Manager for cross-account sharing.

3. **Understand disaster recovery** - Know RTO/RPO requirements for each DR strategy (backup/restore, pilot light, warm standby, multi-site).

4. **Practice security designs** - IAM policies with least privilege, encryption at rest/in transit, security layers (security groups, NACLs, WAF).

5. **Study cost optimization** - Reserved Instances vs Savings Plans, Spot Instances, rightsizing with Compute Optimizer, cost allocation tags.

---

**Note:** This is Domain 1 of 4, representing 26% of exam content.
