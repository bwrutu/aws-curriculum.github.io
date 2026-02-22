# AWS Certified Cloud Practitioner (CLF-C02) Domain 2
## Security and Compliance

**Official Exam Guide:** [Domain 2: Security and Compliance](https://docs.aws.amazon.com/aws-certification/latest/examguides/cloud-practitioner-02-domain2.html)  
**Skill Builder:** [AWS Cloud Practitioner Foundational (CLF-C02) Exam Prep](https://skillbuilder.aws/category/exam-prep/cloud-practitioner-foundational-CLF-C02)

Note: Some Skill Builder labs require a subscription.

---

## How to Study This Domain Effectively

### Study Tips

1. **Understand the Shared Responsibility Model thoroughly** - This is the most important concept in Domain 2. Create a visual diagram showing what AWS manages (security OF the cloud) vs what you manage (security IN the cloud). Exam questions frequently present scenarios and ask you to identify who is responsible for a specific security task.

2. **Learn IAM inside and out** - IAM is tested heavily across all domains. Understand users, groups, roles, and policies. Practice creating IAM policies and understand the principle of least privilege. Many exam questions present scenarios about granting permissions and ask you to identify the correct IAM approach.

3. **Memorize compliance programs** - Know major compliance programs (HIPAA, PCI DSS, SOC, GDPR, FedRAMP) and what they mean for AWS customers. Create flashcards linking compliance programs to industries (healthcare → HIPAA, payment cards → PCI DSS). Exam questions ask you to identify which compliance program applies to specific business scenarios.

4. **Understand encryption concepts** - Know the difference between encryption at rest and encryption in transit. Understand AWS Key Management Service (KMS) and when to use it. Exam questions test your ability to identify appropriate encryption solutions for different data protection scenarios.

5. **Study security services by use case** - Group security services by what they protect: network (Security Groups, NACLs, WAF), data (KMS, CloudHSM), identity (IAM, Cognito), monitoring (CloudTrail, GuardDuty, Inspector). This organization helps you quickly identify the right service for exam scenarios.

### Recommended Approach

1. **Master the Shared Responsibility Model first** - Everything in Domain 2 builds on this foundation. Understand it thoroughly before moving to other topics. This model appears in questions across all domains, not just security.

2. **Deep dive into IAM** - Study IAM users, groups, roles, and policies in detail. Understand best practices like MFA, password policies, and least privilege. Practice in the AWS Console to see how IAM works hands-on.

3. **Learn network security** - Study Security Groups and Network ACLs, understanding their differences (stateful vs stateless, deny rules). Learn AWS WAF and AWS Shield for DDoS protection.

4. **Study data protection** - Understand encryption at rest and in transit. Learn KMS, CloudHSM, AWS Certificate Manager, and Secrets Manager. Know when to use each service.

5. **Master monitoring and compliance** - Study CloudTrail, Config, GuardDuty, and Inspector. Understand AWS Artifact for compliance documentation. Review major compliance programs and what they mean.

---

## Task 2.1: Understand the AWS shared responsibility model

### Knowledge Areas & AWS Documentation Reading List

#### 1. AWS responsibility (security OF the cloud)

**Why:** Understanding what AWS manages is critical for the exam. AWS is responsible for protecting the infrastructure (physical security, hardware, networking, hypervisor). Exam questions test whether you know AWS handles tasks like data center security, hardware patching, and network infrastructure. This prevents you from incorrectly assuming you need to manage these aspects.

**AWS Documentation:**
- [AWS Shared Responsibility Model](https://aws.amazon.com/compliance/shared-responsibility-model/)
- [Security of the AWS Cloud](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/security-and-compliance.html)
- [AWS Global Infrastructure Security](https://aws.amazon.com/compliance/data-center/controls/)
- [Physical and Environmental Security](https://aws.amazon.com/compliance/data-center/)

#### 2. Customer responsibility (security IN the cloud)

**Why:** Customers are responsible for securing their data, applications, IAM, operating systems, and network configuration. Exam questions frequently test whether you understand customer responsibilities like configuring Security Groups, encrypting data, and managing IAM users. Knowing the customer's security responsibilities helps you answer questions about what actions YOU must take to secure workloads.

**AWS Documentation:**
- [Customer Responsibility](https://aws.amazon.com/compliance/shared-responsibility-model/)
- [Security Best Practices](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html)
- [AWS Security Best Practices](https://aws.amazon.com/architecture/security-identity-compliance/)
- [Shared Responsibility Model Examples](https://aws.amazon.com/blogs/security/shared-responsibility-model/)

#### 3. Shared controls (for example, patch management, configuration management, awareness and training)

**Why:** Some security controls are shared between AWS and customers. AWS patches the infrastructure (hypervisor, physical systems), but customers patch operating systems and applications. Understanding shared controls helps you answer questions about who patches what, who manages configuration, and security training responsibilities.

**AWS Documentation:**
- [Shared Controls](https://aws.amazon.com/compliance/shared-responsibility-model/)
- [Patch Management](https://aws.amazon.com/systems-manager/features/#Patch_Manager)
- [AWS Systems Manager](https://aws.amazon.com/systems-manager/)
- [Configuration Management](https://aws.amazon.com/config/)

---

## Task 2.2: Understand AWS Cloud security, governance, and compliance concepts

### Knowledge Areas & AWS Documentation Reading List

#### 1. AWS compliance and governance concepts (for example, AWS Artifact, AWS Compliance Program)

**Why:** Organizations need compliance documentation for audits and certifications. AWS Artifact provides access to compliance reports (SOC, PCI, ISO). Exam questions test whether you know where to find compliance documentation and which compliance programs apply to specific industries. Understanding AWS compliance programs helps you answer questions about meeting regulatory requirements.

**AWS Documentation:**
- [AWS Compliance](https://aws.amazon.com/compliance/)
- [AWS Artifact](https://aws.amazon.com/artifact/)
- [AWS Compliance Programs](https://aws.amazon.com/compliance/programs/)
- [HIPAA Compliance](https://aws.amazon.com/compliance/hipaa-compliance/)
- [PCI DSS Compliance](https://aws.amazon.com/compliance/pci-dss-level-1-faqs/)
- [SOC Compliance](https://aws.amazon.com/compliance/soc-faqs/)
- [GDPR](https://aws.amazon.com/compliance/gdpr-center/)
- [FedRAMP](https://aws.amazon.com/compliance/fedramp/)
- [ISO Certifications](https://aws.amazon.com/compliance/iso-certified/)

#### 2. Identification and access management (for example, AWS Identity and Access Management [IAM], AWS IAM Identity Center [AWS Single Sign-On])

**Why:** IAM is the most critical security service and appears throughout the exam. You must understand IAM users, groups, roles, and policies. Exam questions test your ability to identify correct IAM solutions for granting permissions, implementing least privilege, and managing access. IAM Identity Center (SSO) helps manage access across multiple AWS accounts.

**AWS Documentation:**
- [AWS IAM](https://aws.amazon.com/iam/)
- [IAM User Guide](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html)
- [IAM Best Practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)
- [IAM Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html)
- [IAM Roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html)
- [IAM Users and Groups](https://docs.aws.amazon.com/IAM/latest/UserGuide/id.html)
- [Multi-Factor Authentication (MFA)](https://aws.amazon.com/iam/features/mfa/)
- [AWS IAM Identity Center](https://aws.amazon.com/iam/identity-center/)
- [Principle of Least Privilege](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#grant-least-privilege)

#### 3. Security best practices (for example, least privilege, separation of duties)

**Why:** Security best practices like least privilege and separation of duties are fundamental principles tested throughout Domain 2. Exam questions present scenarios and ask you to identify which best practice applies or recommend secure solutions. Understanding these principles helps you evaluate whether a proposed solution follows AWS security recommendations.

**AWS Documentation:**
- [Security Best Practices in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)
- [Least Privilege](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#grant-least-privilege)
- [Separation of Duties](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)
- [Defense in Depth](https://aws.amazon.com/architecture/security-identity-compliance/)
- [Security Pillar - Design Principles](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/design-principles.html)

#### 4. AWS security services (for example, AWS CloudTrail, Amazon GuardDuty, AWS Security Hub, AWS Inspector, AWS Config)

**Why:** AWS provides multiple security services for different purposes. CloudTrail logs API calls, GuardDuty detects threats, Security Hub provides central security view, Inspector scans for vulnerabilities, and Config tracks configuration changes. Exam questions test your ability to identify which service solves specific security monitoring and compliance needs.

**AWS Documentation:**
- [AWS CloudTrail](https://aws.amazon.com/cloudtrail/)
- [Amazon GuardDuty](https://aws.amazon.com/guardduty/)
- [AWS Security Hub](https://aws.amazon.com/security-hub/)
- [Amazon Inspector](https://aws.amazon.com/inspector/)
- [AWS Config](https://aws.amazon.com/config/)
- [AWS CloudWatch](https://aws.amazon.com/cloudwatch/)
- [Amazon Macie](https://aws.amazon.com/macie/)
- [AWS Audit Manager](https://aws.amazon.com/audit-manager/)

---

## Task 2.3: Identify AWS access management capabilities

### Knowledge Areas & AWS Documentation Reading List

#### 1. IAM users, groups, and roles

**Why:** Understanding the difference between users (individual identities), groups (collections of users), and roles (temporary access for services/users) is fundamental. Exam questions frequently ask you to identify the correct IAM construct for specific scenarios (e.g., use roles for EC2 instances to access S3, not access keys).

**AWS Documentation:**
- [IAM Users](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users.html)
- [IAM Groups](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_groups.html)
- [IAM Roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html)
- [When to Create IAM Users](https://docs.aws.amazon.com/IAM/latest/UserGuide/id.html#id_which-to-choose)
- [Using Roles vs Resource-based Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_compare-resource-policies.html)

#### 2. IAM policies (for example, AWS managed policies, customer managed policies, inline policies)

**Why:** IAM policies define permissions and are tested extensively. You must understand the difference between AWS managed (AWS maintains), customer managed (you create and maintain), and inline policies (embedded in user/role). Exam questions ask you to identify appropriate policy types and evaluate policy permissions.

**AWS Documentation:**
- [IAM Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html)
- [Managed Policies vs Inline Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html)
- [AWS Managed Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies)
- [Customer Managed Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#customer-managed-policies)
- [Policy Evaluation Logic](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_evaluation-logic.html)

#### 3. Multi-factor authentication (MFA)

**Why:** MFA adds an extra layer of security beyond passwords. Exam questions test whether you understand when to require MFA (root account, privileged users, sensitive operations). MFA is a critical security best practice and frequently appears in security-focused scenarios.

**AWS Documentation:**
- [Multi-Factor Authentication](https://aws.amazon.com/iam/features/mfa/)
- [Using MFA in AWS](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa.html)
- [MFA for Root Account](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user.html#id_root-user_manage_mfa)
- [Virtual MFA Devices](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable_virtual.html)
- [Hardware MFA Devices](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable_physical.html)

#### 4. Temporary security credentials (for example, AWS Security Token Service [AWS STS], AWS IAM Identity Center)

**Why:** Temporary credentials are more secure than long-term access keys. AWS STS generates temporary credentials for roles, while IAM Identity Center provides temporary access for federated users. Exam questions test whether you understand when to use temporary credentials instead of permanent access keys.

**AWS Documentation:**
- [AWS Security Token Service (STS)](https://docs.aws.amazon.com/STS/latest/APIReference/welcome.html)
- [Temporary Security Credentials](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp.html)
- [Requesting Temporary Security Credentials](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_request.html)
- [AWS IAM Identity Center](https://aws.amazon.com/iam/identity-center/)
- [Federation](https://aws.amazon.com/identity/federation/)

---

## Task 2.4: Identify components and resources for security

### Knowledge Areas & AWS Documentation Reading List

#### 1. Network security (for example, AWS Network Firewall, security groups, network ACLs, AWS WAF)

**Why:** Network security controls protect your AWS resources from unauthorized access. Security Groups act as virtual firewalls for instances, NACLs provide subnet-level security, WAF protects web applications, and Network Firewall provides VPC-level protection. Exam questions test your ability to identify the correct network security tool for different scenarios.

**AWS Documentation:**
- [Amazon VPC Security](https://docs.aws.amazon.com/vpc/latest/userguide/security.html)
- [Security Groups](https://docs.aws.amazon.com/vpc/latest/userguide/security-groups.html)
- [Network ACLs](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html)
- [AWS WAF](https://aws.amazon.com/waf/)
- [AWS Network Firewall](https://aws.amazon.com/network-firewall/)
- [AWS Shield](https://aws.amazon.com/shield/)
- [Comparison: Security Groups vs NACLs](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-security-groups.html#security-group-nacl-comparison)

#### 2. Encryption (for example, AWS Key Management Service [AWS KMS], AWS Certificate Manager [ACM], AWS Secrets Manager)

**Why:** Encryption protects data at rest and in transit. KMS manages encryption keys, ACM manages SSL/TLS certificates, and Secrets Manager stores sensitive information like database passwords. Exam questions test your knowledge of which service to use for different encryption scenarios and when encryption is required.

**AWS Documentation:**
- [AWS Key Management Service (KMS)](https://aws.amazon.com/kms/)
- [KMS Developer Guide](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html)
- [AWS Certificate Manager](https://aws.amazon.com/certificate-manager/)
- [AWS Secrets Manager](https://aws.amazon.com/secrets-manager/)
- [Encryption at Rest](https://docs.aws.amazon.com/whitepapers/latest/efs-encrypted-file-systems/encryption-of-data-at-rest.html)
- [Encryption in Transit](https://docs.aws.amazon.com/whitepapers/latest/efs-encrypted-file-systems/encryption-of-data-in-transit.html)
- [AWS CloudHSM](https://aws.amazon.com/cloudhsm/)

#### 3. DDoS protection (for example, AWS Shield)

**Why:** DDoS attacks can make applications unavailable. AWS Shield provides DDoS protection (Standard is free, Advanced provides enhanced protection). Exam questions test whether you know Shield protects against DDoS attacks and when to use Shield Advanced for mission-critical applications.

**AWS Documentation:**
- [AWS Shield](https://aws.amazon.com/shield/)
- [Shield Standard](https://docs.aws.amazon.com/waf/latest/developerguide/shield-chapter.html)
- [Shield Advanced](https://docs.aws.amazon.com/waf/latest/developerguide/shield-advanced.html)
- [DDoS Resiliency](https://docs.aws.amazon.com/whitepapers/latest/aws-best-practices-ddos-resiliency/welcome.html)

#### 4. Data classification (for example, Amazon Macie)

**Why:** Amazon Macie automatically discovers and classifies sensitive data like PII (Personally Identifiable Information). Exam questions test whether you know Macie helps with data discovery, classification, and protection for compliance requirements.

**AWS Documentation:**
- [Amazon Macie](https://aws.amazon.com/macie/)
- [Macie User Guide](https://docs.aws.amazon.com/macie/latest/user/what-is-macie.html)
- [Data Classification](https://aws.amazon.com/blogs/security/how-to-classify-your-data-using-amazon-macie/)

---

## AWS Service FAQs (Recommended Reading)

- [IAM FAQs](https://aws.amazon.com/iam/faqs/)
- [KMS FAQs](https://aws.amazon.com/kms/faqs/)
- [CloudTrail FAQs](https://aws.amazon.com/cloudtrail/faqs/)
- [GuardDuty FAQs](https://aws.amazon.com/guardduty/faqs/)
- [Shield FAQs](https://aws.amazon.com/shield/faqs/)
- [WAF FAQs](https://aws.amazon.com/waf/faqs/)
- [Security Hub FAQs](https://aws.amazon.com/security-hub/faqs/)
- [Inspector FAQs](https://aws.amazon.com/inspector/faqs/)
- [Config FAQs](https://aws.amazon.com/config/faq/)
- [Artifact FAQs](https://aws.amazon.com/artifact/faq/)

---

## AWS Whitepapers (Essential Reading)

1. **[AWS Security Pillar](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html)** - Security best practices and design principles
2. **[Introduction to AWS Security](https://docs.aws.amazon.com/whitepapers/latest/introduction-aws-security/welcome.html)** - Comprehensive security overview
3. **[AWS Security Best Practices](https://aws.amazon.com/architecture/security-identity-compliance/)** - Security implementation guidance
4. **[Shared Responsibility Model](https://aws.amazon.com/compliance/shared-responsibility-model/)** - Understanding security responsibilities
5. **[AWS Compliance](https://aws.amazon.com/compliance/)** - Compliance programs and certifications
6. **[DDoS Resiliency Best Practices](https://docs.aws.amazon.com/whitepapers/latest/aws-best-practices-ddos-resiliency/welcome.html)** - DDoS protection strategies

---

## Final Thoughts on Domain 2

Domain 2 (Security and Compliance) represents **30% of the exam** - the largest single domain. Security is AWS's #1 priority and understanding security concepts is critical for passing the exam.

### Key Takeaways:

1. **Master the Shared Responsibility Model** - Know what AWS secures vs what you secure
2. **IAM is everywhere** - Users, groups, roles, and policies appear in every domain
3. **Know your security services** - CloudTrail (logging), GuardDuty (threat detection), Config (compliance)
4. **Understand encryption** - At rest (KMS), in transit (ACM), secrets (Secrets Manager)
5. **Network security matters** - Security Groups (stateful), NACLs (stateless), WAF (application protection)
6. **Compliance is critical** - Know AWS Artifact and major compliance programs (HIPAA, PCI DSS, SOC)

### Study Strategy:

- Spend **30-35% of your study time** on this domain (matches exam weight)
- Create a Shared Responsibility Model diagram and memorize it
- Practice creating IAM policies in the AWS Console
- Understand the difference between Security Groups and NACLs (frequently tested)
- Learn which compliance program applies to which industry
- Know when to use each security service (CloudTrail vs GuardDuty vs Inspector)

### Common Exam Question Patterns:

- Scenario: Who is responsible for patching? → Answer: AWS patches infrastructure, you patch OS/apps
- Scenario: Grant EC2 access to S3 → Answer: Use IAM role, not access keys
- Scenario: Detect suspicious activity → Answer: Amazon GuardDuty
- Scenario: Track API calls → Answer: AWS CloudTrail
- Scenario: Healthcare data compliance → Answer: HIPAA compliance via AWS Artifact
- Scenario: Protect web application → Answer: AWS WAF + Shield

Security is the foundation of everything in AWS. Master Domain 2 thoroughly!
