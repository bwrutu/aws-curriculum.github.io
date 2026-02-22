# AWS Certified AI Practitioner (AIF-C01) Domain 5
## Security, Compliance, and Governance for AI Solutions

**Official Exam Guide:** <a href="https://aws.amazon.com/certification/certified-ai-practitioner/" target="_blank">AWS Certified AI Practitioner Exam Guide</a>

---

## Domain Overview

**Domain Weight:** 14% of the exam

This domain tests your understanding of security, compliance, and governance practices specific to AI/ML workloads on AWS.

---

## Key Concepts

### 1. Data Security for AI/ML

**Why:** AI/ML workloads process large amounts of data, often sensitive. Protecting this data is critical.

**Security Measures:**
- **Encryption at rest**: Amazon S3, EBS encryption
- **Encryption in transit**: TLS/SSL
- **Access controls**: IAM policies and roles
- **Data classification**: Identify sensitive data
- **Secure data pipelines**: Encrypted data flow

**AWS Services:**
- AWS KMS (Key Management Service)
- AWS Secrets Manager
- Amazon Macie (data discovery and classification)
- IAM (access management)

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/security.html" target="_blank">Security in SageMaker</a>
- <a href="https://docs.aws.amazon.com/bedrock/latest/userguide/security.html" target="_blank">Amazon Bedrock Security</a>

### 2. Model Security

**Why:** ML models themselves can be targets for attacks or contain sensitive information.

**Threats:**
- Model theft
- Model inversion attacks
- Adversarial examples
- Data poisoning

**Protection Measures:**
- Access controls for models
- Model encryption
- Endpoint security
- Input validation
- Output filtering

### 3. Compliance and Regulations

**Why:** AI/ML systems must comply with industry regulations and data protection laws.

**Key Regulations:**
- GDPR (data protection in EU)
- HIPAA (healthcare data in US)
- PCI DSS (payment card data)
- SOC 2 (service organization controls)
- Industry-specific regulations

**AWS Compliance:**
- AWS Artifact (compliance reports)
- HIPAA eligible services (SageMaker, Bedrock)
- PCI DSS compliant infrastructure
- SOC reports available

**AWS Documentation:**
- <a href="https://aws.amazon.com/compliance/programs/" target="_blank">AWS Compliance Programs</a>
- <a href="https://aws.amazon.com/sagemaker/compliance/" target="_blank">SageMaker Compliance</a>

### 4. Governance and Monitoring

**Why:** Proper governance ensures AI systems are used appropriately and monitored for issues.

**Governance Practices:**
- AI use case approval processes
- Model validation and testing
- Change management
- Access controls and audit trails
- Regular reviews

**Monitoring:**
- Model performance monitoring
- Data quality monitoring
- Security monitoring
- Usage tracking
- Cost monitoring

**AWS Services:**
- Amazon SageMaker Model Monitor
- AWS CloudTrail (audit logging)
- Amazon CloudWatch (monitoring and alerting)
- AWS Config (configuration management)

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-monitor.html" target="_blank">SageMaker Model Monitor</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/logging-using-cloudtrail.html" target="_blank">CloudTrail for ML</a>

### 5. IAM for AI/ML Services

**Why:** Proper access controls prevent unauthorized use of AI services and data.

**Best Practices:**
- Least privilege principle
- Role-based access control
- Service-specific permissions
- Temporary credentials
- MFA for sensitive operations

**Common Patterns:**
- IAM roles for SageMaker notebooks
- IAM roles for Bedrock API access
- IAM policies for S3 data access
- Cross-account access for ML pipelines

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/security-iam.html" target="_blank">IAM for SageMaker</a>
- <a href="https://docs.aws.amazon.com/bedrock/latest/userguide/security-iam.html" target="_blank">IAM for Bedrock</a>

### 6. Network Security for AI/ML

**Why:** Isolating AI/ML workloads in secure networks prevents unauthorized access.

**Security Measures:**
- VPC deployment
- Private subnets
- VPC endpoints
- Security groups
- Network ACLs

**AWS Services:**
- Amazon VPC
- VPC Endpoints for AWS services
- AWS PrivateLink

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/interface-vpc-endpoint.html" target="_blank">SageMaker in VPC</a>

---

## AWS Services for AI/ML Security

### Core Security Services

1. **AWS Identity and Access Management (IAM)**
   - User and role management
   - Fine-grained permissions
   - <a href="https://aws.amazon.com/iam/" target="_blank">IAM Documentation</a>

2. **AWS Key Management Service (KMS)**
   - Encryption key management
   - Data encryption
   - <a href="https://aws.amazon.com/kms/" target="_blank">KMS Documentation</a>

3. **AWS CloudTrail**
   - API call logging
   - Audit trails
   - <a href="https://aws.amazon.com/cloudtrail/" target="_blank">CloudTrail Documentation</a>

4. **Amazon CloudWatch**
   - Monitoring and alerting
   - Log aggregation
   - <a href="https://aws.amazon.com/cloudwatch/" target="_blank">CloudWatch Documentation</a>

5. **AWS Config**
   - Resource configuration tracking
   - Compliance monitoring
   - <a href="https://aws.amazon.com/config/" target="_blank">Config Documentation</a>

6. **Amazon Macie**
   - Sensitive data discovery
   - Data classification
   - <a href="https://aws.amazon.com/macie/" target="_blank">Macie Documentation</a>

---

## Shared Responsibility Model for AI/ML

**AWS Responsibilities:**
- Physical security of infrastructure
- Hardware and network security
- Service availability
- Foundation model security (for Bedrock)

**Customer Responsibilities:**
- Data security and encryption
- Access management (IAM)
- Network configuration (VPC)
- Model security
- Application-level security
- Compliance with regulations

---

## Best Practices Summary

1. **Encrypt data** at rest and in transit
2. **Use IAM roles** instead of access keys
3. **Enable CloudTrail** for audit logging
4. **Implement least privilege** access
5. **Monitor models** in production
6. **Classify data** and protect sensitive information
7. **Use VPC** for network isolation
8. **Regular security reviews** and audits
9. **Compliance validation** for regulated industries
10. **Incident response plan** for security events

---

## AWS Documentation

- <a href="https://aws.amazon.com/architecture/security-identity-compliance/" target="_blank">AWS Security Best Practices</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/security.html" target="_blank">Machine Learning Security</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/security.html" target="_blank">SageMaker Security</a>
- <a href="https://docs.aws.amazon.com/bedrock/latest/userguide/security.html" target="_blank">Bedrock Security</a>

---

## Final Thoughts on Domain 5

Security, compliance, and governance are critical for production AI/ML systems. Understand both AWS security services and AI-specific security considerations!
