# AWS Certified Security - Specialty (SCS-C03) Domain 5
## Data Protection

**Official Exam Guide:** <a href="https://docs.aws.amazon.com/aws-certification/latest/examguides/security-specialty-03-domain5.html" target="_blank">Domain 5: Data Protection</a>

**Skill Builder:** <a href="https://skillbuilder.aws/category/exam-prep/security-specialty-SCS-C03" target="_blank">AWS Certified Security - Specialty Exam Prep</a>

---

## Domain Overview

Domain 5 (18%) focuses on data in transit protection, data at rest protection, and protecting confidential data/secrets/keys.

---

## Task 5.1: Design and implement controls for data in transit

**Key Skills:**
- Require encryption when connecting to resources
- Design secure and private access mechanisms
- Configure inter-resource encryption in transit

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/elasticloadbalancing/latest/application/create-https-listener.html" target="_blank">HTTPS Listeners for Application Load Balancers</a>
- <a href="https://docs.aws.amazon.com/elasticloadbalancing/latest/application/listener-update-certificates.html" target="_blank">SSL/TLS Certificates for Load Balancers</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/privatelink/" target="_blank">AWS PrivateLink</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/vpce-interface.html" target="_blank">VPC Interface Endpoints</a>
- <a href="https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/" target="_blank">AWS Client VPN</a>
- <a href="https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-data-encryption-options.html" target="_blank">EMR Encryption Options</a>

---

## Task 5.2: Design and implement controls for data at rest

**Key Skills:**
- Design data encryption at rest based on requirements
- Configure mechanisms to protect data integrity
- Design lifecycle management and retention solutions
- Configure secure data replication and backup

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/kms/latest/developerguide/" target="_blank">AWS KMS Developer Guide</a>
- <a href="https://docs.aws.amazon.com/cloudhsm/latest/userguide/" target="_blank">AWS CloudHSM User Guide</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingEncryption.html" target="_blank">Protecting Data Using Encryption</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lock.html" target="_blank">S3 Object Lock</a>
- <a href="https://docs.aws.amazon.com/amazonglacier/latest/dev/vault-lock.html" target="_blank">S3 Glacier Vault Lock</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/Versioning.html" target="_blank">S3 Versioning</a>
- <a href="https://docs.aws.amazon.com/aws-backup/latest/devguide/" target="_blank">AWS Backup Developer Guide</a>
- <a href="https://docs.aws.amazon.com/datasync/latest/userguide/" target="_blank">AWS DataSync User Guide</a>

---

## Task 5.3: Design and implement controls for confidential data, credentials, secrets, and keys

**Key Skills:**
- Design credential and secret rotation
- Manage imported key material
- Understand differences between imported and AWS-generated keys
- Mask sensitive data
- Manage encryption keys and certificates

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/secretsmanager/latest/userguide/" target="_blank">AWS Secrets Manager User Guide</a>
- <a href="https://docs.aws.amazon.com/kms/latest/developerguide/importing-keys.html" target="_blank">Importing Key Material in KMS</a>
- <a href="https://docs.aws.amazon.com/kms/latest/developerguide/keystore-external.html" target="_blank">External Key Stores</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/mask-sensitive-log-data.html" target="_blank">CloudWatch Logs Data Protection</a>
- <a href="https://docs.aws.amazon.com/acm/latest/userguide/" target="_blank">AWS Certificate Manager User Guide</a>
- <a href="https://docs.aws.amazon.com/privateca/latest/userguide/" target="_blank">AWS Private Certificate Authority</a>

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/kms/faqs/" target="_blank">AWS KMS FAQs</a>
- <a href="https://aws.amazon.com/cloudhsm/faqs/" target="_blank">AWS CloudHSM FAQs</a>
- <a href="https://aws.amazon.com/secrets-manager/faqs/" target="_blank">AWS Secrets Manager FAQs</a>
- <a href="https://aws.amazon.com/certificate-manager/faqs/" target="_blank">AWS Certificate Manager FAQs</a>

---

## Study Tips

1. **Master KMS thoroughly** - Customer managed keys, AWS managed keys, key policies, grants, encryption context, key rotation, multi-Region keys.

2. **Learn encryption patterns** - Server-side encryption (SSE-S3, SSE-KMS, SSE-C), client-side encryption, envelope encryption, key hierarchy.

3. **Understand S3 encryption** - Default encryption, bucket policies to enforce encryption, S3 Object Lock (WORM), Glacier Vault Lock.

4. **Practice secrets management** - Secrets Manager automatic rotation, RDS/Redshift integration, Parameter Store (standard vs advanced), rotation Lambda.

5. **Study certificate management** - ACM for public certificates, Private CA for internal PKI, certificate renewal, certificate validation methods (DNS, email).

---

**Note:** This is Domain 5 of 6, representing 18% of exam content.
