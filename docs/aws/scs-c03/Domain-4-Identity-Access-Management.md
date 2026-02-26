# AWS Certified Security - Specialty (SCS-C03) Domain 4
## Identity and Access Management

**Official Exam Guide:** <a href="https://docs.aws.amazon.com/aws-certification/latest/examguides/security-specialty-03-domain4.html" target="_blank">Domain 4: Identity and Access Management</a>

**Skill Builder:** <a href="https://skillbuilder.aws/category/exam-prep/security-specialty-SCS-C03" target="_blank">AWS Certified Security - Specialty Exam Prep</a>

---

## Domain Overview

Domain 4 (20% - largest domain) focuses on authentication strategies and authorization strategies.

---

## Task 4.1: Design and implement authentication strategies

**Key Skills:**
- Design identity solutions for human, application, system authentication
- Configure temporary credential mechanisms
- Troubleshoot authentication issues

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/singlesignon/latest/userguide/" target="_blank">AWS IAM Identity Center User Guide</a>
- <a href="https://docs.aws.amazon.com/cognito/latest/developerguide/" target="_blank">Amazon Cognito Developer Guide</a>
- <a href="https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa.html" target="_blank">Using Multi-Factor Authentication (MFA)</a>
- <a href="https://docs.aws.amazon.com/STS/latest/APIReference/" target="_blank">AWS STS API Reference</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/PresignedUrlUploadObject.html" target="_blank">S3 Presigned URLs</a>
- <a href="https://docs.aws.amazon.com/directoryservice/latest/admin-guide/" target="_blank">AWS Directory Service Administration Guide</a>

---

## Task 4.2: Design and implement authorization strategies

**Key Skills:**
- Design authorization controls for human, application, system access
- Design ABAC and RBAC strategies
- Implement IAM policies with least privilege
- Analyze authorization failures
- Investigate unintended permissions

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/IAM/latest/UserGuide/" target="_blank">AWS IAM User Guide</a>
- <a href="https://docs.aws.amazon.com/verifiedpermissions/latest/userguide/" target="_blank">Amazon Verified Permissions</a>
- <a href="https://docs.aws.amazon.com/rolesanywhere/latest/userguide/" target="_blank">IAM Roles Anywhere</a>
- <a href="https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_boundaries.html" target="_blank">Permissions Boundaries</a>
- <a href="https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_policy-simulator.html" target="_blank">IAM Policy Simulator</a>
- <a href="https://docs.aws.amazon.com/IAM/latest/UserGuide/what-is-access-analyzer.html" target="_blank">IAM Access Analyzer</a>
- <a href="https://docs.aws.amazon.com/IAM/latest/UserGuide/access-analyzer-policy-generation.html" target="_blank">Access Analyzer Policy Generation</a>

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/iam/faqs/" target="_blank">AWS IAM FAQs</a>
- <a href="https://aws.amazon.com/cognito/faqs/" target="_blank">Amazon Cognito FAQs</a>
- <a href="https://aws.amazon.com/single-sign-on/faqs/" target="_blank">IAM Identity Center FAQs</a>

---

## Study Tips

1. **Master IAM policy structure** - Principal, Action, Resource, Effect, Condition elements. Identity-based vs resource-based policies.

2. **Learn ABAC implementation** - Tag-based access control, principal tags, resource tags, request condition tags, session tags.

3. **Understand permission boundaries** - Maximum permissions for IAM entities, prevent privilege escalation, delegate administration safely.

4. **Practice with Access Analyzer** - Identify resources shared with external entities, validate policies, generate policies from CloudTrail logs.

5. **Study federation patterns** - SAML 2.0 federation, OIDC providers, IAM Identity Center (SSO), Cognito user pools and identity pools.

---

**Note:** This is Domain 4 of 6, representing 20% (largest domain) of exam content.
