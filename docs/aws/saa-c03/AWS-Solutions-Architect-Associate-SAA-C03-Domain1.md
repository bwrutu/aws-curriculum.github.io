# AWS Certified Solutions Architect Associate (SAA-C03) Domain 1
## Design Secure Architectures

**Official Exam Guide:** <a href="https://aws.amazon.com/certification/certified-solutions-architect-associate/" target="_blank">SAA-C03 Exam Guide</a>  
**Skill Builder:** <a href="https://skillbuilder.aws/learning-plans/architect" target="_blank">Solutions Architect Learning Plan</a>

---

## Domain Overview

**Domain Weight:** 30% of the exam (largest domain)

This domain tests your ability to design secure access to AWS resources, secure application architectures, and implement appropriate security controls.

---

## Task 1.1: Design secure access to AWS resources

### Identity and Access Management (IAM)

#### IAM Users, Groups, and Roles

**Key Concepts:**
- **IAM Users** - Individual identities with long-term credentials
- **IAM Groups** - Collections of users with shared permissions
- **IAM Roles** - Temporary credentials for services or federated access
- **IAM Policies** - JSON documents defining permissions

**Best Practices:**
- Use roles instead of users for applications
- Implement least privilege principle
- Enable MFA for privileged users
- Rotate credentials regularly
- Use policy conditions for additional security

**Common Scenarios:**
- EC2 accessing S3 → Use IAM role attached to instance
- Cross-account access → Use IAM role with trust policy
- Temporary access → Use STS to assume roles
- Service-to-service → Use IAM roles, not access keys

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html" target="_blank">IAM Best Practices</a>
- <a href="https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html" target="_blank">IAM Roles</a>
- <a href="https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html" target="_blank">IAM Policies</a>

#### Federated Access

**Key Concepts:**
- **SAML 2.0** - Enterprise federation (Active Directory, ADFS)
- **Web Identity Federation** - Social identity providers (Google, Facebook)
- **AWS IAM Identity Center (SSO)** - Centralized access management
- **Cognito** - User authentication for mobile/web apps

**Use Cases:**
- Enterprise SSO → IAM Identity Center
- Mobile/web apps → Amazon Cognito
- Custom federation → SAML or OIDC with IAM
- Temporary credentials → STS AssumeRoleWithWebIdentity

**AWS Documentation:**
- <a href="https://aws.amazon.com/iam/identity-center/" target="_blank">AWS IAM Identity Center</a>
- <a href="https://aws.amazon.com/cognito/" target="_blank">Amazon Cognito</a>
- <a href="https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_saml.html" target="_blank">SAML Federation</a>

#### Multi-Factor Authentication (MFA)

**Key Concepts:**
- Virtual MFA devices (authenticator apps)
- Hardware MFA devices (YubiKey, etc.)
- MFA for root account (mandatory best practice)
- MFA for privileged operations

**Implementation:**
- Require MFA for sensitive operations
- MFA in IAM policies using conditions
- MFA delete for S3 objects

---

## Task 1.2: Design secure application tiers

### Network Security

#### VPC Security

**Key Components:**
- **Security Groups** - Stateful firewall at instance level
- **Network ACLs** - Stateless firewall at subnet level
- **VPC Flow Logs** - Network traffic monitoring
- **VPC Endpoints** - Private connectivity to AWS services

**Security Groups vs NACLs:**

| Feature | Security Groups | Network ACLs |
|---------|----------------|--------------|
| Level | Instance | Subnet |
| State | Stateful | Stateless |
| Rules | Allow only | Allow and Deny |
| Evaluation | All rules | Rules in order |
| Default | Deny all | Allow all |

**Best Practices:**
- Default deny, explicit allow
- Separate security groups by tier (web, app, db)
- Use security group references (not IP addresses)
- Implement defense in depth with both SGs and NACLs

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/security-groups.html" target="_blank">Security Groups</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html" target="_blank">Network ACLs</a>

#### VPC Endpoints

**Types:**
- **Interface Endpoints** - ENI with private IP (PrivateLink)
- **Gateway Endpoints** - Route table target (S3, DynamoDB)

**Use Cases:**
- Access S3/DynamoDB without internet gateway
- Private access to AWS services
- Compliance requirements (data doesn't leave AWS network)
- Reduced data transfer costs

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/vpc/latest/privatelink/vpc-endpoints.html" target="_blank">VPC Endpoints</a>

### Application Security

#### AWS WAF (Web Application Firewall)

**Key Features:**
- Protect against common web exploits (OWASP Top 10)
- SQL injection and XSS protection
- Rate limiting
- Geo-blocking
- Custom rules

**Integration:**
- CloudFront
- Application Load Balancer
- API Gateway
- AppSync

**AWS Documentation:**
- <a href="https://aws.amazon.com/waf/" target="_blank">AWS WAF</a>

#### AWS Shield

**Protection Levels:**
- **Shield Standard** - Free DDoS protection
- **Shield Advanced** - Enhanced DDoS protection + support

**AWS Documentation:**
- <a href="https://aws.amazon.com/shield/" target="_blank">AWS Shield</a>

---

## Task 1.3: Select appropriate data security options

### Encryption

#### Encryption at Rest

**S3 Encryption:**
- **SSE-S3** - S3-managed keys (AES-256)
- **SSE-KMS** - KMS-managed keys (audit trail, rotation)
- **SSE-C** - Customer-provided keys
- **Client-side encryption** - Encrypt before upload

**EBS Encryption:**
- Encrypts volumes, snapshots, and AMIs
- Uses KMS keys
- Transparent to applications
- Minimal performance impact

**RDS Encryption:**
- Encrypts data, backups, read replicas
- Must enable at creation (can't add later)
- Uses KMS

**Best Practices:**
- Enable encryption by default
- Use KMS for audit trail and key rotation
- Encrypt snapshots and backups

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingEncryption.html" target="_blank">S3 Encryption</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSEncryption.html" target="_blank">EBS Encryption</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.Encryption.html" target="_blank">RDS Encryption</a>

#### Encryption in Transit

**Key Technologies:**
- **TLS/SSL** - HTTPS connections
- **AWS Certificate Manager (ACM)** - Free SSL/TLS certificates
- **VPN** - Encrypted site-to-site connections

**Implementation:**
- Use HTTPS for all API calls
- Enable encryption in transit for services (RDS, ElastiCache)
- Use VPN or Direct Connect with encryption

**AWS Documentation:**
- <a href="https://aws.amazon.com/certificate-manager/" target="_blank">ACM</a>

#### AWS Key Management Service (KMS)

**Key Concepts:**
- **Customer Managed Keys (CMK)** - You control
- **AWS Managed Keys** - AWS manages for services
- **Key Policies** - Resource-based policies for keys
- **Automatic Rotation** - Annual key rotation

**Use Cases:**
- S3, EBS, RDS encryption
- Encrypt application data
- Envelope encryption for large data
- Cross-account access to encrypted data

**AWS Documentation:**
- <a href="https://aws.amazon.com/kms/" target="_blank">AWS KMS</a>
- <a href="https://docs.aws.amazon.com/kms/latest/developerguide/best-practices.html" target="_blank">KMS Best Practices</a>

#### AWS Secrets Manager

**Key Features:**
- Store database credentials, API keys, secrets
- Automatic rotation
- Integration with RDS, Redshift, DocumentDB
- Fine-grained access control

**vs Systems Manager Parameter Store:**
- Secrets Manager: Automatic rotation, higher cost
- Parameter Store: Manual rotation, free tier

**AWS Documentation:**
- <a href="https://aws.amazon.com/secrets-manager/" target="_blank">Secrets Manager</a>

### Data Protection

#### S3 Security

**Access Control:**
- **Bucket Policies** - Resource-based policies
- **IAM Policies** - User/role-based access
- **ACLs** - Legacy access control (avoid if possible)
- **S3 Block Public Access** - Account-level protection

**Additional Security:**
- **Versioning** - Protect against accidental deletion
- **MFA Delete** - Require MFA to delete objects
- **Object Lock** - WORM (Write Once Read Many)
- **S3 Access Points** - Simplified access management

**Best Practices:**
- Enable Block Public Access
- Use bucket policies over ACLs
- Enable versioning for critical data
- Use S3 Access Analyzer to find public buckets

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/security-best-practices.html" target="_blank">S3 Security Best Practices</a>

#### Database Security

**RDS Security:**
- Encryption at rest and in transit
- IAM database authentication
- Network isolation (private subnets)
- Security groups
- Automated backups with encryption

**DynamoDB Security:**
- Encryption at rest (default)
- IAM for access control
- VPC endpoints for private access
- DynamoDB Streams encryption
- Fine-grained access control

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.html" target="_blank">RDS Security</a>
- <a href="https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/security.html" target="_blank">DynamoDB Security</a>

---

## Monitoring and Compliance

### AWS CloudTrail

**Key Features:**
- Log all API calls
- Compliance auditing
- Security analysis
- Troubleshooting

**Best Practices:**
- Enable in all regions
- Enable log file validation
- Integrate with CloudWatch Logs
- Store logs in S3 with encryption

**AWS Documentation:**
- <a href="https://aws.amazon.com/cloudtrail/" target="_blank">CloudTrail</a>

### Amazon GuardDuty

**Key Features:**
- Threat detection
- Analyzes VPC Flow Logs, CloudTrail, DNS logs
- Machine learning for anomaly detection
- Automated remediation with EventBridge

**AWS Documentation:**
- <a href="https://aws.amazon.com/guardduty/" target="_blank">GuardDuty</a>

### AWS Config

**Key Features:**
- Track resource configurations
- Compliance monitoring
- Configuration history
- Automated remediation

**AWS Documentation:**
- <a href="https://aws.amazon.com/config/" target="_blank">AWS Config</a>

---

## Common Security Architectures

### Three-Tier Web Application

**Architecture:**
```
Internet → ALB (public subnet)
         ↓
      Web Tier (private subnet with NAT)
         ↓
      App Tier (private subnet)
         ↓
       DB Tier (private subnet, Multi-AZ RDS)
```

**Security Measures:**
- Public subnets: Only load balancers
- Private subnets: Application and database tiers
- Security groups: Tiered access (web → app → db)
- NACLs: Additional subnet-level protection
- WAF on ALB
- Encryption at rest and in transit

### Secure S3 Data Lake

**Architecture:**
- S3 buckets with default encryption
- Block Public Access enabled
- Bucket policies with least privilege
- VPC endpoints for private access
- CloudTrail for audit logs
- S3 Access Analyzer for public access detection
- S3 Object Lock for compliance
- Lifecycle policies for data retention

---

## Exam Tips

**Common Question Patterns:**

1. **"Most secure way to..."** → Usually involves encryption, least privilege, and isolation
2. **"EC2 needs to access S3..."** → Use IAM role, not access keys
3. **"Prevent accidental deletion..."** → S3 versioning + MFA delete
4. **"Encrypt data at rest..."** → Enable encryption for storage services
5. **"Monitor API calls..."** → CloudTrail
6. **"Detect threats..."** → GuardDuty
7. **"Protect web application..."** → WAF + Shield

**Security Best Practices to Remember:**
- Least privilege always
- Defense in depth (multiple layers)
- Encryption everywhere (at rest and in transit)
- IAM roles over access keys
- Monitor and audit everything
- Automate security responses

---

## Final Thoughts

Domain 1 (Design Secure Architectures) is **30% of the exam** - the largest domain. Security is fundamental to every architecture on AWS.

**Master these topics:**
1. IAM (users, groups, roles, policies)
2. Security Groups vs NACLs
3. S3 security (encryption, policies, Block Public Access)
4. Encryption (KMS, at rest, in transit)
5. Network security (VPC, endpoints, private subnets)
6. Monitoring (CloudTrail, GuardDuty, Config)

Security is never an afterthought - it's designed in from the start!
