# AWS Certified Security - Specialty (SCS-C03) Domain 6
## Security Foundations and Governance

**Official Exam Guide:** <a href="https://docs.aws.amazon.com/aws-certification/latest/examguides/security-specialty-03-domain6.html" target="_blank">Domain 6: Security Foundations and Governance</a>

**Skill Builder:** <a href="https://skillbuilder.aws/category/exam-prep/security-specialty-SCS-C03" target="_blank">AWS Certified Security - Specialty Exam Prep</a>

---

## Domain Overview

Domain 6 (14%) focuses on centralized account management, secure deployment strategies, and compliance evaluation.

---

## Task 6.1: Develop strategy for centralized account deployment and management

**Key Skills:**
- Deploy and configure AWS Organizations
- Implement and manage AWS Control Tower
- Implement organization policies (SCPs, RCPs, AI opt-out)
- Centrally manage security services
- Manage root user credentials

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/organizations/latest/userguide/" target="_blank">AWS Organizations User Guide</a>
- <a href="https://docs.aws.amazon.com/controltower/latest/userguide/" target="_blank">AWS Control Tower User Guide</a>
- <a href="https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps.html" target="_blank">Service Control Policies (SCPs)</a>
- <a href="https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_rcps.html" target="_blank">Resource Control Policies (RCPs)</a>

---

## Task 6.2: Implement secure and consistent deployment strategy

**Key Skills:**
- Use IaC to deploy resources securely
- Use tags to organize AWS resources
- Deploy and enforce policies from central source
- Securely share resources across accounts

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/" target="_blank">AWS CloudFormation User Guide</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacksets-concepts.html" target="_blank">CloudFormation StackSets</a>
- <a href="https://docs.aws.amazon.com/cfn-guard/latest/ug/" target="_blank">CloudFormation Guard</a>
- <a href="https://docs.aws.amazon.com/waf/latest/developerguide/fms-chapter.html" target="_blank">AWS Firewall Manager</a>
- <a href="https://docs.aws.amazon.com/servicecatalog/latest/adminguide/" target="_blank">AWS Service Catalog</a>
- <a href="https://docs.aws.amazon.com/ram/latest/userguide/" target="_blank">AWS Resource Access Manager</a>

---

## Task 6.3: Evaluate compliance of AWS resources

**Key Skills:**
- Create rules to detect and remediate non-compliant resources
- Use audit services to collect evidence
- Evaluate architecture for compliance

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/config/latest/developerguide/" target="_blank">AWS Config Developer Guide</a>
- <a href="https://docs.aws.amazon.com/config/latest/developerguide/conformance-packs.html" target="_blank">AWS Config Conformance Packs</a>
- <a href="https://docs.aws.amazon.com/securityhub/latest/userguide/" target="_blank">AWS Security Hub User Guide</a>
- <a href="https://docs.aws.amazon.com/audit-manager/latest/userguide/" target="_blank">AWS Audit Manager User Guide</a>
- <a href="https://docs.aws.amazon.com/artifact/latest/ug/" target="_blank">AWS Artifact User Guide</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/userguide/" target="_blank">AWS Well-Architected Tool</a>

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/organizations/faqs/" target="_blank">AWS Organizations FAQs</a>
- <a href="https://aws.amazon.com/controltower/faqs/" target="_blank">AWS Control Tower FAQs</a>
- <a href="https://aws.amazon.com/config/faq/" target="_blank">AWS Config FAQs</a>
- <a href="https://aws.amazon.com/artifact/faq/" target="_blank">AWS Artifact FAQs</a>

---

## Study Tips

1. **Master multi-account strategy** - Organizations OUs, SCPs for guardrails, delegated administrators, consolidated billing, RCPs for resources.

2. **Learn Control Tower** - Landing zones, Account Factory, guardrails (preventive/detective), baseline controls, customizations.

3. **Understand compliance automation** - Config rules and conformance packs, Security Hub standards (CIS, PCI-DSS, NIST), Audit Manager frameworks.

4. **Practice IaC security** - CloudFormation Guard for policy-as-code, StackSets for multi-account deployment, cfn-lint for validation.

5. **Study centralized security** - Security Hub as aggregator, GuardDuty delegated administrator, Firewall Manager for WAF/Shield policies.

---

## Complete Exam Summary

**Exam Format:**
- 65 questions (50 scored + 15 unscored)
- Multiple choice, Multiple response, Ordering, Matching
- Passing score: 750/1000
- 170 minutes

**Domain Weightings:**
- Domain 1: Detection (16%)
- Domain 2: Incident Response (14%)
- Domain 3: Infrastructure Security (18%)
- Domain 4: Identity and Access Management (20%)
- Domain 5: Data Protection (18%)
- Domain 6: Security Foundations and Governance (14%)

**Target Candidate:**
- 3-5 years experience securing cloud solutions
- Knowledge of AWS shared responsibility model
- Multi-account governance experience
- Incident response and forensics knowledge

**Key AWS Security Services:**
- **Detection:** GuardDuty, Security Hub, Macie, Inspector, Detective
- **IAM:** IAM, IAM Identity Center, Cognito, STS, Directory Service
- **Network:** WAF, Shield, Network Firewall, VPC, PrivateLink
- **Encryption:** KMS, CloudHSM, ACM, Secrets Manager
- **Logging:** CloudTrail, CloudWatch, VPC Flow Logs, Security Lake
- **Compliance:** Config, Control Tower, Organizations, Audit Manager
- **Compute Security:** Systems Manager, EC2 Image Builder
- **Governance:** Organizations, SCPs, RCPs, Firewall Manager

**Key Security Concepts:**
- Defense in depth (multiple security layers)
- Least privilege access (IAM policies, SCPs, permissions boundaries)
- Encryption (at rest and in transit)
- Threat detection and response
- Compliance and governance
- Network segmentation
- Identity federation
- Secrets management
- Patch management
- Incident response lifecycle

**Study Resources:**
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/" target="_blank">Security Pillar - Well-Architected Framework</a>
- <a href="https://aws.amazon.com/architecture/security-identity-compliance/" target="_blank">AWS Security & Compliance Architecture</a>
- <a href="https://aws.amazon.com/whitepapers/" target="_blank">AWS Security Whitepapers</a>

Good luck with your AWS Certified Security - Specialty certification!

---

**Note:** This is Domain 6 of 6, representing 14% of exam content.
