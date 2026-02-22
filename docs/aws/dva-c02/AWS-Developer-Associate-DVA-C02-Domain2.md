# AWS Certified Developer Associate (DVA-C02) Domain 2
## Security

**Official Exam Guide:** [Domain 2: Security](https://docs.aws.amazon.com/aws-certification/latest/examguides/developer-associate-02-domain2.html){:target="_blank" rel="noopener noreferrer"}  
**Skill Builder:** [AWS Developer Associate (DVA-C02) Exam Prep](https://skillbuilder.aws/category/exam-prep/developer-associate-DVA-C02){:target="_blank" rel="noopener noreferrer"}

Note: Some Skill Builder labs require a subscription.

---

## How to Study This Domain Effectively

### Study Tips

1. **Practice IAM policy creation hands-on** - Security is best learned by doing. Create IAM users, roles, and policies in your AWS account. Experiment with different policy structures, test least privilege access, practice assuming roles programmatically, and observe what happens when permissions are insufficient. Understanding IAM through trial and error builds intuition that's difficult to gain from reading alone, and policy evaluation is heavily tested on the exam.

2. **Implement authentication flows in sample applications** - Build small applications that use Cognito User Pools for user authentication, implement JWT token validation, configure federated identity providers, and practice programmatic access with temporary credentials. Hands-on experience with authentication flows helps you understand the exam scenarios that describe user login requirements, token management, and federated access patterns.

3. **Work with AWS KMS encryption in code** - Write code that encrypts and decrypts data using KMS, configure encryption at rest for S3 and DynamoDB, practice using envelope encryption, and understand how to grant cross-account KMS access. The exam tests your ability to implement encryption programmatically, not just understand it conceptually, so writing actual encryption code is essential for mastering this domain.

4. **Master AWS Secrets Manager and Parameter Store** - Create secrets in Secrets Manager, store parameters in Systems Manager Parameter Store, practice retrieving secrets in Lambda functions and EC2 applications, implement automatic rotation for RDS credentials, and understand cost differences between the two services. Exam questions frequently test when to use each service and how to securely retrieve secrets in application code.

5. **Create a security decision matrix** - Build a reference table that maps common security scenarios to AWS services: user authentication (Cognito), service-to-service auth (IAM roles), API authorization (API Gateway authorizers), encryption at rest (KMS), encryption in transit (TLS/SSL certificates), secret management (Secrets Manager vs Parameter Store), and temporary credentials (STS). This matrix helps you quickly identify the right security approach during exam questions.

### Recommended Approach

1. **Start with IAM fundamentals** - Begin by deeply understanding IAM users, groups, roles, and policies. Learn policy structure (Effect, Action, Resource, Condition), policy evaluation logic, the difference between identity-based and resource-based policies, and how to implement least privilege. IAM is the foundation for all AWS security, and mastering it is critical for this domain and the entire exam.

2. **Master authentication patterns with Cognito** - Study Cognito User Pools for user directory and authentication, Cognito Identity Pools for temporary AWS credentials, integration with social identity providers, JWT token structure and validation, and how Cognito integrates with API Gateway and Application Load Balancer. Understanding Cognito authentication flows is essential for answering user authentication scenarios.

3. **Deep dive into encryption services** - Study AWS KMS thoroughly: customer managed keys vs AWS managed keys, key policies, grants, envelope encryption, and cross-account access. Then learn encryption at rest for S3, EBS, RDS, and DynamoDB. Finally, understand encryption in transit with TLS/SSL certificates and AWS Certificate Manager. Encryption appears throughout the exam in various contexts.

4. **Learn secret management best practices** - Study AWS Secrets Manager for automatic rotation and database credentials, Systems Manager Parameter Store for configuration data, how to retrieve secrets in Lambda and EC2, encryption of secrets with KMS, and when to use each service. Practice writing code that retrieves secrets securely rather than hardcoding credentials.

5. **Practice security scenarios end-to-end** - Build complete applications that implement authentication (Cognito), authorization (IAM policies), encryption (KMS), and secret management (Secrets Manager). Understanding how these services work together in real applications prepares you for complex exam scenarios. Complete with practice exams focused on Domain 2 to identify security knowledge gaps.

---

## Task 1: Implement authentication and/or authorization for applications and AWS services

### Skills & Corresponding Documentation

#### Skill 2.1.1: Use an identity provider to implement federated access (for example, Amazon Cognito, IAM)

**Why:** Federated access is extensively tested because modern applications often integrate with external identity providers like Google, Facebook, Active Directory, or SAML providers. You must understand how Cognito User Pools authenticate users, how Cognito Identity Pools provide temporary AWS credentials, how IAM identity providers enable SAML and OIDC federation, and when to use each approach. Exam questions present authentication requirements involving external identity sources and expect you to configure the appropriate federation mechanism.

**AWS Documentation:**
- [Amazon Cognito User Pools](https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-identity-pools.html){:target="_blank" rel="noopener noreferrer"}
- [Amazon Cognito Identity Pools (Federated Identities)](https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-identity.html){:target="_blank" rel="noopener noreferrer"}
- [Amazon Cognito Developer Guide](https://docs.aws.amazon.com/cognito/latest/developerguide/what-is-amazon-cognito.html){:target="_blank" rel="noopener noreferrer"}
- [Integrating User Pools with Identity Pools](https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-integrate-apps.html){:target="_blank" rel="noopener noreferrer"}
- [Adding Social Identity Providers to User Pools](https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-pools-social-idp.html){:target="_blank" rel="noopener noreferrer"}
- [IAM Identity Providers and Federation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers.html){:target="_blank" rel="noopener noreferrer"}
- [SAML 2.0 Federation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_saml.html){:target="_blank" rel="noopener noreferrer"}
- [OpenID Connect (OIDC) Federation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_oidc.html){:target="_blank" rel="noopener noreferrer"}
- [Web Identity Federation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_oidc.html){:target="_blank" rel="noopener noreferrer"}
- [Cognito User Pool Authentication Flow](https://docs.aws.amazon.com/cognito/latest/developerguide/amazon-cognito-user-pools-authentication-flow.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 2.1.2: Secure applications by using bearer tokens

**Why:** Bearer token authentication is fundamental for securing APIs and is tested through scenarios involving JWT tokens, OAuth 2.0 flows, and token validation. You must understand how Cognito issues JWT tokens (ID, access, refresh), how to validate tokens in API Gateway or Lambda, token expiration and refresh mechanisms, and how to extract claims from tokens. Exam questions present API security requirements and expect you to implement token-based authentication correctly.

**AWS Documentation:**
- [Using Tokens with User Pools](https://docs.aws.amazon.com/cognito/latest/developerguide/amazon-cognito-user-pools-using-tokens-with-identity-providers.html){:target="_blank" rel="noopener noreferrer"}
- [JSON Web Tokens (JWT)](https://docs.aws.amazon.com/cognito/latest/developerguide/amazon-cognito-user-pools-using-the-id-token.html){:target="_blank" rel="noopener noreferrer"}
- [Verifying a JSON Web Token](https://docs.aws.amazon.com/cognito/latest/developerguide/amazon-cognito-user-pools-using-tokens-verifying-a-jwt.html){:target="_blank" rel="noopener noreferrer"}
- [Using ID Tokens and Access Tokens](https://docs.aws.amazon.com/cognito/latest/developerguide/amazon-cognito-user-pools-using-the-id-token.html){:target="_blank" rel="noopener noreferrer"}
- [Token Refresh](https://docs.aws.amazon.com/cognito/latest/developerguide/amazon-cognito-user-pools-using-tokens-with-identity-providers.html#amazon-cognito-user-pools-using-the-refresh-token){:target="_blank" rel="noopener noreferrer"}
- [API Gateway Lambda Authorizers](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-use-lambda-authorizer.html){:target="_blank" rel="noopener noreferrer"}
- [API Gateway Cognito User Pool Authorizers](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-integrate-with-cognito.html){:target="_blank" rel="noopener noreferrer"}
- [OAuth 2.0 Grants in Cognito](https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-pools-app-integration.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 2.1.3: Configure programmatic access to AWS

**Why:** Programmatic access is tested because applications must authenticate to AWS services via SDKs and CLI. You need to understand AWS access keys vs temporary credentials, IAM roles for EC2 instances and Lambda functions, credential provider chains, credential precedence, and security best practices (never hardcode credentials). Exam questions present scenarios where applications need AWS access and expect you to configure secure programmatic authentication.

**AWS Documentation:**
- [AWS Security Credentials](https://docs.aws.amazon.com/general/latest/gr/aws-security-credentials.html){:target="_blank" rel="noopener noreferrer"}
- [Managing Access Keys for IAM Users](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html){:target="_blank" rel="noopener noreferrer"}
- [IAM Roles for Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html){:target="_blank" rel="noopener noreferrer"}
- [AWS Lambda Execution Role](https://docs.aws.amazon.com/lambda/latest/dg/lambda-intro-execution-role.html){:target="_blank" rel="noopener noreferrer"}
- [Configuring the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html){:target="_blank" rel="noopener noreferrer"}
- [AWS SDK Credential Provider Chain](https://docs.aws.amazon.com/sdk-for-java/latest/developer-guide/credentials-chain.html){:target="_blank" rel="noopener noreferrer"}
- [Best Practices for Managing AWS Access Keys](https://docs.aws.amazon.com/general/latest/gr/aws-access-keys-best-practices.html){:target="_blank" rel="noopener noreferrer"}
- [Temporary Security Credentials](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp.html){:target="_blank" rel="noopener noreferrer"}
- [Using Instance Profiles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-ec2_instance-profiles.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 2.1.4: Make authenticated calls to AWS services

**Why:** This skill is fundamental for developers because all AWS SDK interactions require proper authentication. You must understand how to configure SDK credentials, use SigV4 signing for API requests, implement retry logic for throttling, handle credential expiration, and work with temporary credentials from assumed roles. Exam questions present code scenarios and expect you to identify correct authentication patterns or troubleshoot authentication failures.

**AWS Documentation:**
- [Signing AWS API Requests](https://docs.aws.amazon.com/general/latest/gr/signing_aws_api_requests.html){:target="_blank" rel="noopener noreferrer"}
- [Signature Version 4 Signing Process](https://docs.aws.amazon.com/general/latest/gr/signature-version-4.html){:target="_blank" rel="noopener noreferrer"}
- [Making Requests Using AWS SDKs](https://docs.aws.amazon.com/general/latest/gr/signing-aws-api-requests.html){:target="_blank" rel="noopener noreferrer"}
- [AWS SDK Authentication and Access](https://docs.aws.amazon.com/sdk-for-javascript/v3/developer-guide/setting-credentials.html){:target="_blank" rel="noopener noreferrer"}
- [Boto3 Credentials Configuration](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/credentials.html){:target="_blank" rel="noopener noreferrer"}
- [Error Handling for AWS SDKs](https://docs.aws.amazon.com/sdk-for-javascript/v3/developer-guide/error-handling.html){:target="_blank" rel="noopener noreferrer"}
- [Request Signing for Custom Requests](https://docs.aws.amazon.com/general/latest/gr/sigv4-signed-request-examples.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 2.1.5: Assume an IAM role

**Why:** Role assumption is heavily tested because it's the secure way to grant temporary permissions and enable cross-account access. You must understand AssumeRole, AssumeRoleWithWebIdentity, and AssumeRoleWithSAML API calls, how to configure trust policies, session duration settings, external ID for third-party access, and how to use temporary credentials in code. Exam questions present scenarios requiring role switching or cross-account access and expect you to implement role assumption correctly.

**AWS Documentation:**
- [Using IAM Roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use.html){:target="_blank" rel="noopener noreferrer"}
- [AWS STS AssumeRole](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html){:target="_blank" rel="noopener noreferrer"}
- [Switching to an IAM Role (AWS CLI)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-cli.html){:target="_blank" rel="noopener noreferrer"}
- [AssumeRole in AWS SDKs](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html){:target="_blank" rel="noopener noreferrer"}
- [Trust Policies for IAM Roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-trust-policy){:target="_blank" rel="noopener noreferrer"}
- [Cross-Account Access with IAM Roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/tutorial_cross-account-with-roles.html){:target="_blank" rel="noopener noreferrer"}
- [Using External IDs for Third-Party Access](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-user_externalid.html){:target="_blank" rel="noopener noreferrer"}
- [Temporary Security Credentials](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_use-resources.html){:target="_blank" rel="noopener noreferrer"}
- [Session Tags in AssumeRole](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_session-tags.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 2.1.6: Define permissions for IAM principals

**Why:** IAM policy creation is one of the most critical skills because permissions control all AWS access. You must understand policy structure (Version, Statement, Effect, Action, Resource, Condition), identity-based vs resource-based policies, inline vs managed policies, policy variables, NotAction and NotResource, and least privilege principles. Exam questions frequently present access requirements and expect you to write or identify correct IAM policies that grant appropriate permissions.

**AWS Documentation:**
- [IAM Policies and Permissions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html){:target="_blank" rel="noopener noreferrer"}
- [IAM JSON Policy Reference](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies.html){:target="_blank" rel="noopener noreferrer"}
- [Creating IAM Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create.html){:target="_blank" rel="noopener noreferrer"}
- [IAM Policy Elements Reference](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html){:target="_blank" rel="noopener noreferrer"}
- [Identity-Based vs Resource-Based Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_identity-vs-resource.html){:target="_blank" rel="noopener noreferrer"}
- [IAM Policy Evaluation Logic](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_evaluation-logic.html){:target="_blank" rel="noopener noreferrer"}
- [Managed Policies vs Inline Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html){:target="_blank" rel="noopener noreferrer"}
- [IAM Policy Conditions](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_condition.html){:target="_blank" rel="noopener noreferrer"}
- [Policy Variables](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_variables.html){:target="_blank" rel="noopener noreferrer"}
- [Testing IAM Policies with the IAM Policy Simulator](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_testing-policies.html){:target="_blank" rel="noopener noreferrer"}
- [Granting Least Privilege](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#grant-least-privilege){:target="_blank" rel="noopener noreferrer"}

#### Skill 2.1.7: Implement application-level authorization for fine-grained access control

**Why:** Application-level authorization is tested through scenarios requiring more granular access control than IAM provides. You must understand how to implement custom authorization logic in Lambda authorizers, use Cognito groups for role-based access, implement attribute-based access control (ABAC) with IAM tags and policy variables, and enforce row-level or column-level security in applications. Exam questions present multi-tenant or hierarchical access scenarios and expect you to implement appropriate authorization patterns.

**AWS Documentation:**
- [Fine-Grained Access Control](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html#policies_resource-based){:target="_blank" rel="noopener noreferrer"}
- [API Gateway Lambda Authorizers](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-use-lambda-authorizer.html){:target="_blank" rel="noopener noreferrer"}
- [Cognito User Pool Groups](https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-pools-user-groups.html){:target="_blank" rel="noopener noreferrer"}
- [Attribute-Based Access Control (ABAC)](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction_attribute-based-access-control.html){:target="_blank" rel="noopener noreferrer"}
- [Using Tags to Control Access](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_tags.html){:target="_blank" rel="noopener noreferrer"}
- [DynamoDB Fine-Grained Access Control](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html){:target="_blank" rel="noopener noreferrer"}
- [S3 Bucket Policies for Fine-Grained Access](https://docs.aws.amazon.com/AmazonS3/latest/userguide/bucket-policies.html){:target="_blank" rel="noopener noreferrer"}
- [Controlling Access with VPC Endpoints](https://docs.aws.amazon.com/vpc/latest/privatelink/vpc-endpoints-access.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 2.1.8: Handle cross-service authentication in microservice architectures

**Why:** Microservices authentication is tested because modern distributed applications require secure service-to-service communication. You must understand how to use IAM roles for service authentication, implement service mesh patterns, use VPC endpoints for private connectivity, secure API Gateway integrations, and handle authentication context propagation across services. Exam questions present microservices scenarios and expect you to implement secure inter-service authentication.

**AWS Documentation:**
- [Service-to-Service Authentication](https://docs.aws.amazon.com/whitepapers/latest/microservices-on-aws/service-to-service-authentication.html){:target="_blank" rel="noopener noreferrer"}
- [IAM Roles for Services](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use.html){:target="_blank" rel="noopener noreferrer"}
- [VPC Endpoints for Private Connectivity](https://docs.aws.amazon.com/vpc/latest/privatelink/vpc-endpoints.html){:target="_blank" rel="noopener noreferrer"}
- [API Gateway Resource Policies](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-resource-policies.html){:target="_blank" rel="noopener noreferrer"}
- [Service-to-Service Authentication in Microservices](https://docs.aws.amazon.com/whitepapers/latest/microservices-on-aws/distributed-systems-components.html){:target="_blank" rel="noopener noreferrer"}
- [AWS App Mesh for Service Mesh](https://docs.aws.amazon.com/app-mesh/latest/userguide/what-is-app-mesh.html){:target="_blank" rel="noopener noreferrer"}
- [Cross-Service Confused Deputy Prevention](https://docs.aws.amazon.com/IAM/latest/UserGuide/confused-deputy.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Function URLs with IAM Authentication](https://docs.aws.amazon.com/lambda/latest/dg/urls-auth.html){:target="_blank" rel="noopener noreferrer"}

**AWS Service FAQs:**

- [Amazon Cognito FAQ](https://aws.amazon.com/cognito/faqs/){:target="_blank" rel="noopener noreferrer"}
- [AWS IAM FAQ](https://aws.amazon.com/iam/faqs/){:target="_blank" rel="noopener noreferrer"}
- [AWS STS FAQ](https://aws.amazon.com/iam/faqs/){:target="_blank" rel="noopener noreferrer"}
- [AWS API Gateway FAQ](https://aws.amazon.com/api-gateway/faqs/){:target="_blank" rel="noopener noreferrer"}

**AWS Whitepapers:**

- [Security Pillar - AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [AWS Security Best Practices](https://docs.aws.amazon.com/whitepapers/latest/aws-security-best-practices/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [Identity and Access Management for AWS](https://docs.aws.amazon.com/whitepapers/latest/aws-security-best-practices/identity-and-access-management.html){:target="_blank" rel="noopener noreferrer"}
- [Microservices on AWS - Security](https://docs.aws.amazon.com/whitepapers/latest/microservices-on-aws/security.html){:target="_blank" rel="noopener noreferrer"}

---

## Task 2: Implement encryption by using AWS services

### Skills & Corresponding Documentation

#### Skill 2.2.1: Define encryption at rest and in transit

**Why:** Understanding encryption types is fundamental for securing data throughout its lifecycle. You must know that encryption at rest protects stored data (S3, EBS, RDS, DynamoDB) using KMS or service-managed keys, while encryption in transit protects data during transmission using TLS/SSL. Exam questions test your ability to identify when each type is needed, understand how they work together for defense in depth, and select appropriate encryption services for different scenarios.

**AWS Documentation:**
- [Encryption at Rest](https://docs.aws.amazon.com/whitepapers/latest/logical-separation/encrypting-data-at-rest-and--in-transit.html){:target="_blank" rel="noopener noreferrer"}
- [Encryption in Transit](https://docs.aws.amazon.com/whitepapers/latest/logical-separation/encrypting-data-at-rest-and--in-transit.html){:target="_blank" rel="noopener noreferrer"}
- [Data Protection in AWS](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/data-protection.html){:target="_blank" rel="noopener noreferrer"}
- [S3 Encryption](https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingEncryption.html){:target="_blank" rel="noopener noreferrer"}
- [EBS Encryption](https://docs.aws.amazon.com/ebs/latest/userguide/ebs-encryption.html){:target="_blank" rel="noopener noreferrer"}
- [RDS Encryption](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.Encryption.html){:target="_blank" rel="noopener noreferrer"}
- [DynamoDB Encryption at Rest](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/EncryptionAtRest.html){:target="_blank" rel="noopener noreferrer"}
- [TLS/SSL Certificates](https://docs.aws.amazon.com/acm/latest/userguide/acm-overview.html){:target="_blank" rel="noopener noreferrer"}
- [Encrypting Data in Transit](https://docs.aws.amazon.com/whitepapers/latest/efs-encrypted-file-systems/encryption-of-data-in-transit.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 2.2.2: Describe certificate management (for example, AWS Private CA)

**Why:** Certificate management is tested because TLS/SSL certificates are essential for secure communication. You must understand AWS Certificate Manager for public certificates, AWS Private Certificate Authority for private PKI, certificate validation methods (DNS, email), certificate renewal, how to attach certificates to load balancers and CloudFront distributions, and when to use public vs private certificates. Exam questions present HTTPS requirements and expect you to configure certificate management correctly.

**AWS Documentation:**
- [AWS Certificate Manager (ACM)](https://docs.aws.amazon.com/acm/latest/userguide/acm-overview.html){:target="_blank" rel="noopener noreferrer"}
- [Issuing and Managing Certificates](https://docs.aws.amazon.com/acm/latest/userguide/gs.html){:target="_blank" rel="noopener noreferrer"}
- [AWS Private Certificate Authority](https://docs.aws.amazon.com/privateca/latest/userguide/PcaWelcome.html){:target="_blank" rel="noopener noreferrer"}
- [Certificate Validation](https://docs.aws.amazon.com/acm/latest/userguide/domain-ownership-validation.html){:target="_blank" rel="noopener noreferrer"}
- [Using ACM Certificates with AWS Services](https://docs.aws.amazon.com/acm/latest/userguide/acm-services.html){:target="_blank" rel="noopener noreferrer"}
- [Managed Certificate Renewal](https://docs.aws.amazon.com/acm/latest/userguide/managed-renewal.html){:target="_blank" rel="noopener noreferrer"}
- [Importing Certificates into ACM](https://docs.aws.amazon.com/acm/latest/userguide/import-certificate.html){:target="_blank" rel="noopener noreferrer"}
- [Private Certificates and Internal Resources](https://docs.aws.amazon.com/privateca/latest/userguide/PcaWelcome.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 2.2.3: Describe differences between client-side encryption and server-side encryption

**Why:** Understanding encryption ownership and responsibility is critical for compliance and security design. You must know that server-side encryption (SSE) is managed by AWS services (SSE-S3, SSE-KMS, SSE-C), while client-side encryption requires applications to encrypt data before sending to AWS. Exam questions test your understanding of when each approach is appropriate, compliance implications, performance considerations, and how to implement each encryption type correctly.

**AWS Documentation:**
- [Protecting Data Using Encryption](https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingEncryption.html){:target="_blank" rel="noopener noreferrer"}
- [Server-Side Encryption](https://docs.aws.amazon.com/AmazonS3/latest/userguide/serv-side-encryption.html){:target="_blank" rel="noopener noreferrer"}
- [Client-Side Encryption](https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingClientSideEncryption.html){:target="_blank" rel="noopener noreferrer"}
- [S3 Server-Side Encryption with Amazon S3 Managed Keys (SSE-S3)](https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingServerSideEncryption.html){:target="_blank" rel="noopener noreferrer"}
- [S3 Server-Side Encryption with AWS KMS (SSE-KMS)](https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingKMSEncryption.html){:target="_blank" rel="noopener noreferrer"}
- [S3 Server-Side Encryption with Customer-Provided Keys (SSE-C)](https://docs.aws.amazon.com/AmazonS3/latest/userguide/ServerSideEncryptionCustomerKeys.html){:target="_blank" rel="noopener noreferrer"}
- [AWS Encryption SDK](https://docs.aws.amazon.com/encryption-sdk/latest/developer-guide/introduction.html){:target="_blank" rel="noopener noreferrer"}
- [Client-Side Encryption with AWS SDKs](https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingClientSideEncryption.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 2.2.4: Use encryption keys to encrypt or decrypt data

**Why:** Working with KMS keys programmatically is essential for implementing encryption in applications. You must understand how to call KMS Encrypt and Decrypt APIs, work with customer managed keys (CMKs), use envelope encryption for large data, implement grant-based access, and handle encryption context for additional security. Exam questions present encryption requirements and expect you to write or identify code that correctly encrypts and decrypts data using KMS.

**AWS Documentation:**
- [AWS Key Management Service (KMS)](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html){:target="_blank" rel="noopener noreferrer"}
- [Encrypting and Decrypting Data](https://docs.aws.amazon.com/kms/latest/developerguide/programming-encryption.html){:target="_blank" rel="noopener noreferrer"}
- [KMS Encrypt API](https://docs.aws.amazon.com/kms/latest/APIReference/API_Encrypt.html){:target="_blank" rel="noopener noreferrer"}
- [KMS Decrypt API](https://docs.aws.amazon.com/kms/latest/APIReference/API_Decrypt.html){:target="_blank" rel="noopener noreferrer"}
- [Using Customer Managed Keys](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html#customer-cmk){:target="_blank" rel="noopener noreferrer"}
- [Envelope Encryption](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html#enveloping){:target="_blank" rel="noopener noreferrer"}
- [Encryption Context](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html#encrypt_context){:target="_blank" rel="noopener noreferrer"}
- [KMS GenerateDataKey](https://docs.aws.amazon.com/kms/latest/APIReference/API_GenerateDataKey.html){:target="_blank" rel="noopener noreferrer"}
- [Using KMS Keys in AWS SDKs](https://docs.aws.amazon.com/kms/latest/developerguide/programming-top.html){:target="_blank" rel="noopener noreferrer"}
- [Data Key Caching](https://docs.aws.amazon.com/encryption-sdk/latest/developer-guide/data-key-caching.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 2.2.5: Generate certificates and SSH keys for development purposes

**Why:** Certificate and key generation is tested through scenarios involving development environments, EC2 instance access, and secure communication setup. You must understand how to generate SSH key pairs for EC2 access, create self-signed certificates for development, use OpenSSL for certificate generation, and understand key pair management. Exam questions may ask about securing development environments or configuring secure access to instances.

**AWS Documentation:**
- [Amazon EC2 Key Pairs](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html){:target="_blank" rel="noopener noreferrer"}
- [Creating Key Pairs](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/create-key-pairs.html){:target="_blank" rel="noopener noreferrer"}
- [Connecting to Your Linux Instance Using SSH](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html){:target="_blank" rel="noopener noreferrer"}
- [Self-Signed Certificates for Development](https://docs.aws.amazon.com/acm/latest/userguide/import-certificate-prerequisites.html){:target="_blank" rel="noopener noreferrer"}
- [AWS Systems Manager Session Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager.html){:target="_blank" rel="noopener noreferrer"}
- [EC2 Instance Connect](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-connect-methods.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 2.2.6: Use encryption across account boundaries

**Why:** Cross-account encryption is tested because enterprises often need to share encrypted data between AWS accounts. You must understand how to configure KMS key policies for cross-account access, use grants for temporary permissions, share encrypted S3 objects across accounts, and implement encryption in cross-account scenarios. Exam questions present multi-account requirements and expect you to configure encryption access correctly across account boundaries.

**AWS Documentation:**
- [Allowing Users in Other Accounts to Use a KMS Key](https://docs.aws.amazon.com/kms/latest/developerguide/key-policy-modifying-external-accounts.html){:target="_blank" rel="noopener noreferrer"}
- [Cross-Account Access to KMS Keys](https://docs.aws.amazon.com/kms/latest/developerguide/key-policy-modifying-external-accounts.html){:target="_blank" rel="noopener noreferrer"}
- [Sharing Encrypted S3 Objects Across Accounts](https://docs.aws.amazon.com/AmazonS3/latest/userguide/example-walkthroughs-managing-access-example4.html){:target="_blank" rel="noopener noreferrer"}
- [Using Grants in AWS KMS](https://docs.aws.amazon.com/kms/latest/developerguide/grants.html){:target="_blank" rel="noopener noreferrer"}
- [Cross-Account KMS Key Usage](https://docs.aws.amazon.com/kms/latest/developerguide/key-policy-modifying-external-accounts.html){:target="_blank" rel="noopener noreferrer"}
- [Encrypting Data Keys with Cross-Account Access](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html#cross-account){:target="_blank" rel="noopener noreferrer"}

#### Skill 2.2.7: Enable and disable key rotation

**Why:** Key rotation is a security best practice that's tested through scenarios about maintaining encryption security over time. You must understand automatic key rotation for customer managed keys (yearly rotation), how rotation affects existing data (it doesn't - old versions decrypt existing data), manual rotation requirements for imported keys, and the difference between AWS managed key rotation (every year) and customer managed key rotation. Exam questions test your understanding of rotation mechanics and best practices.

**AWS Documentation:**
- [Rotating AWS KMS Keys](https://docs.aws.amazon.com/kms/latest/developerguide/rotate-keys.html){:target="_blank" rel="noopener noreferrer"}
- [Automatic Key Rotation](https://docs.aws.amazon.com/kms/latest/developerguide/rotate-keys.html#rotate-keys-how-it-works){:target="_blank" rel="noopener noreferrer"}
- [How Automatic Key Rotation Works](https://docs.aws.amazon.com/kms/latest/developerguide/rotate-keys.html#rotate-keys-how-it-works){:target="_blank" rel="noopener noreferrer"}
- [Manual Key Rotation](https://docs.aws.amazon.com/kms/latest/developerguide/rotate-keys.html#rotate-keys-manually){:target="_blank" rel="noopener noreferrer"}
- [Key Rotation Best Practices](https://docs.aws.amazon.com/kms/latest/developerguide/best-practices.html){:target="_blank" rel="noopener noreferrer"}
- [Rotating Customer Managed Keys](https://docs.aws.amazon.com/kms/latest/developerguide/rotate-keys.html){:target="_blank" rel="noopener noreferrer"}

**AWS Service FAQs:**

- [AWS KMS FAQ](https://aws.amazon.com/kms/faqs/){:target="_blank" rel="noopener noreferrer"}
- [AWS Certificate Manager FAQ](https://aws.amazon.com/certificate-manager/faqs/){:target="_blank" rel="noopener noreferrer"}
- [AWS Private Certificate Authority FAQ](https://aws.amazon.com/private-ca/faqs/){:target="_blank" rel="noopener noreferrer"}
- [Amazon S3 FAQ - Encryption](https://aws.amazon.com/s3/faqs/#Encryption){:target="_blank" rel="noopener noreferrer"}

**AWS Whitepapers:**

- [AWS Key Management Service Best Practices](https://docs.aws.amazon.com/whitepapers/latest/kms-best-practices/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [Encrypting Data at Rest](https://docs.aws.amazon.com/whitepapers/latest/logical-separation/encrypting-data-at-rest-and--in-transit.html){:target="_blank" rel="noopener noreferrer"}
- [AWS Security Best Practices - Encryption](https://docs.aws.amazon.com/whitepapers/latest/aws-security-best-practices/encryption.html){:target="_blank" rel="noopener noreferrer"}

---

## Task 3: Manage sensitive data in application code

### Skills & Corresponding Documentation

#### Skill 2.3.1: Describe data classification (for example, personally identifiable information [PII], protected health information [PHI])

**Why:** Data classification is tested because different data types require different protection levels and compliance controls. You must understand what constitutes PII (names, SSNs, email addresses), PHI (health records under HIPAA), financial data (PCI DSS), and other sensitive data types. You should know regulatory requirements, how to identify sensitive data in applications, and AWS services that help classify data. Exam questions present data handling scenarios and expect you to identify appropriate protection measures based on data classification.

**AWS Documentation:**
- [Data Classification](https://docs.aws.amazon.com/whitepapers/latest/data-classification/data-classification.html){:target="_blank" rel="noopener noreferrer"}
- [AWS Data Privacy](https://aws.amazon.com/compliance/data-privacy/){:target="_blank" rel="noopener noreferrer"}
- [Identifying and Protecting Sensitive Data](https://docs.aws.amazon.com/whitepapers/latest/data-classification/identifying-and-protecting-sensitive-data.html){:target="_blank" rel="noopener noreferrer"}
- [Amazon Macie for Data Discovery](https://docs.aws.amazon.com/macie/latest/user/what-is-macie.html){:target="_blank" rel="noopener noreferrer"}
- [HIPAA Compliance](https://aws.amazon.com/compliance/hipaa-compliance/){:target="_blank" rel="noopener noreferrer"}
- [PCI DSS Compliance](https://aws.amazon.com/compliance/pci-dss-level-1-faqs/){:target="_blank" rel="noopener noreferrer"}
- [GDPR Compliance](https://aws.amazon.com/compliance/gdpr-center/){:target="_blank" rel="noopener noreferrer"}
- [Data Protection in AWS](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/data-protection.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 2.3.2: Encrypt environment variables that contain sensitive data

**Why:** Environment variable encryption is tested because configuration often contains sensitive values like API keys, database passwords, and tokens. You must understand how to encrypt Lambda environment variables with KMS, store encrypted values in ECS task definitions, use encryption in Elastic Beanstalk environments, and decrypt variables programmatically in application code. Exam questions present scenarios with sensitive configuration data and expect you to implement secure storage and retrieval patterns.

**AWS Documentation:**
- [Lambda Environment Variables](https://docs.aws.amazon.com/lambda/latest/dg/configuration-envvars.html){:target="_blank" rel="noopener noreferrer"}
- [Securing Lambda Environment Variables](https://docs.aws.amazon.com/lambda/latest/dg/configuration-envvars.html#configuration-envvars-encryption){:target="_blank" rel="noopener noreferrer"}
- [Encrypting Lambda Environment Variables](https://docs.aws.amazon.com/lambda/latest/dg/configuration-envvars.html#configuration-envvars-encryption){:target="_blank" rel="noopener noreferrer"}
- [ECS Task Definition Environment Variables](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/taskdef-envfiles.html){:target="_blank" rel="noopener noreferrer"}
- [ECS Secrets Management](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/specifying-sensitive-data.html){:target="_blank" rel="noopener noreferrer"}
- [Elastic Beanstalk Environment Properties](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/environments-cfg-softwaresettings.html){:target="_blank" rel="noopener noreferrer"}
- [Using KMS to Encrypt Environment Variables](https://aws.amazon.com/blogs/compute/managing-secrets-for-amazon-ecs-applications-using-parameter-store-and-iam-roles-for-tasks/){:target="_blank" rel="noopener noreferrer"}

#### Skill 2.3.3: Use secret management services to secure sensitive data

**Why:** Secret management is heavily tested because hardcoded credentials are a major security vulnerability. You must understand AWS Secrets Manager for automatic rotation and database credentials, Systems Manager Parameter Store for configuration data and secrets, when to use each service (rotation needs, cost, integration), how to retrieve secrets in Lambda and EC2, and how to grant access to secrets via IAM. Exam questions present credential management scenarios and expect you to implement secure secret retrieval patterns.

**AWS Documentation:**
- [AWS Secrets Manager](https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html){:target="_blank" rel="noopener noreferrer"}
- [What is AWS Secrets Manager](https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html){:target="_blank" rel="noopener noreferrer"}
- [Creating and Managing Secrets](https://docs.aws.amazon.com/secretsmanager/latest/userguide/managing-secrets.html){:target="_blank" rel="noopener noreferrer"}
- [Rotating Secrets](https://docs.aws.amazon.com/secretsmanager/latest/userguide/rotating-secrets.html){:target="_blank" rel="noopener noreferrer"}
- [Retrieving Secrets in Code](https://docs.aws.amazon.com/secretsmanager/latest/userguide/retrieving-secrets.html){:target="_blank" rel="noopener noreferrer"}
- [AWS Systems Manager Parameter Store](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-parameter-store.html){:target="_blank" rel="noopener noreferrer"}
- [Parameter Store vs Secrets Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/parameter-store-vs-secrets-manager.html){:target="_blank" rel="noopener noreferrer"}
- [Using Parameter Store with Lambda](https://docs.aws.amazon.com/systems-manager/latest/userguide/ps-integration-lambda-extensions.html){:target="_blank" rel="noopener noreferrer"}
- [SecureString Parameters](https://docs.aws.amazon.com/systems-manager/latest/userguide/sysman-paramstore-securestring.html){:target="_blank" rel="noopener noreferrer"}
- [Secrets Manager Lambda Extension](https://docs.aws.amazon.com/secretsmanager/latest/userguide/retrieving-secrets_lambda.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 2.3.4: Sanitize sensitive data

**Why:** Data sanitization is tested through scenarios involving logging, error messages, debugging output, and data transmission. You must understand how to remove or mask sensitive data from logs, prevent credentials from appearing in error messages, sanitize data before sending to third parties, and implement secure logging practices. Exam questions present situations where sensitive data might leak and expect you to implement appropriate sanitization measures.

**AWS Documentation:**
- [Logging Best Practices](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/sec_detect_investigate_events_logging.html){:target="_blank" rel="noopener noreferrer"}
- [CloudWatch Logs Data Protection](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/protect-sensitive-log-data.html){:target="_blank" rel="noopener noreferrer"}
- [Redacting Sensitive Data](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/mask-sensitive-log-data.html){:target="_blank" rel="noopener noreferrer"}
- [AWS Lambda Logging Best Practices](https://docs.aws.amazon.com/lambda/latest/dg/monitoring-cloudwatchlogs.html){:target="_blank" rel="noopener noreferrer"}
- [Data Masking in Applications](https://docs.aws.amazon.com/whitepapers/latest/data-classification/data-masking.html){:target="_blank" rel="noopener noreferrer"}
- [Preventing Sensitive Data Exposure](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/data-protection.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 2.3.5: Implement application-level data masking and sanitization

**Why:** Application-level masking is tested because applications often need to display partial sensitive data (last 4 digits of SSN) or different data views based on user roles. You must understand how to implement masking logic in application code, use Lambda@Edge for response transformation, implement field-level encryption in CloudFront, and design APIs that return appropriately masked data. Exam questions present requirements for partial data visibility and expect you to implement masking strategies correctly.

**AWS Documentation:**
- [Data Masking Techniques](https://docs.aws.amazon.com/whitepapers/latest/data-classification/data-masking.html){:target="_blank" rel="noopener noreferrer"}
- [Field-Level Encryption in CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/field-level-encryption.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda@Edge for Response Transformation](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/lambda-at-the-edge.html){:target="_blank" rel="noopener noreferrer"}
- [API Gateway Response Transformation](https://docs.aws.amazon.com/apigateway/latest/developerguide/request-response-data-mappings.html){:target="_blank" rel="noopener noreferrer"}
- [DynamoDB Attribute Projection](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Expressions.ProjectionExpressions.html){:target="_blank" rel="noopener noreferrer"}
- [Application-Level Access Control](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 2.3.6: Implement data access patterns for multi-tenant applications

**Why:** Multi-tenant data isolation is tested through scenarios involving SaaS applications that serve multiple customers. You must understand tenant isolation strategies (database per tenant, schema per tenant, shared database with tenant ID), how to implement row-level security with IAM policy variables, use Cognito identity pools with fine-grained access control, and ensure data cannot leak between tenants. Exam questions present multi-tenant requirements and expect you to implement secure isolation patterns.

**AWS Documentation:**
- [SaaS Tenant Isolation Strategies](https://docs.aws.amazon.com/whitepapers/latest/saas-tenant-isolation-strategies/saas-tenant-isolation-strategies.html){:target="_blank" rel="noopener noreferrer"}
- [Multi-Tenant Architecture on AWS](https://aws.amazon.com/partners/programs/saas-factory/){:target="_blank" rel="noopener noreferrer"}
- [DynamoDB Multi-Tenant Data Access](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html){:target="_blank" rel="noopener noreferrer"}
- [Row-Level Security with IAM](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/FGAC_DDB.html){:target="_blank" rel="noopener noreferrer"}
- [Cognito Identity Pools for Multi-Tenant Access](https://docs.aws.amazon.com/cognito/latest/developerguide/identity-pools.html){:target="_blank" rel="noopener noreferrer"}
- [Using Policy Variables for Multi-Tenancy](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_variables.html){:target="_blank" rel="noopener noreferrer"}
- [S3 Multi-Tenant Access Patterns](https://aws.amazon.com/blogs/apn/isolating-saas-tenants-with-dynamically-generated-iam-policies/){:target="_blank" rel="noopener noreferrer"}
- [RDS Multi-Tenant Patterns](https://docs.aws.amazon.com/prescriptive-guidance/latest/saas-multitenant-api-access-authorization/rds-postgresql.html){:target="_blank" rel="noopener noreferrer"}

**AWS Service FAQs:**

- [AWS Secrets Manager FAQ](https://aws.amazon.com/secrets-manager/faqs/){:target="_blank" rel="noopener noreferrer"}
- [AWS Systems Manager FAQ](https://aws.amazon.com/systems-manager/faq/){:target="_blank" rel="noopener noreferrer"}
- [Amazon Macie FAQ](https://aws.amazon.com/macie/faq/){:target="_blank" rel="noopener noreferrer"}
- [AWS Lambda FAQ](https://aws.amazon.com/lambda/faqs/){:target="_blank" rel="noopener noreferrer"}

**AWS Whitepapers:**

- [Data Classification](https://docs.aws.amazon.com/whitepapers/latest/data-classification/data-classification.html){:target="_blank" rel="noopener noreferrer"}
- [SaaS Tenant Isolation Strategies](https://docs.aws.amazon.com/whitepapers/latest/saas-tenant-isolation-strategies/saas-tenant-isolation-strategies.html){:target="_blank" rel="noopener noreferrer"}
- [Security Best Practices - Data Protection](https://docs.aws.amazon.com/whitepapers/latest/aws-security-best-practices/data-protection.html){:target="_blank" rel="noopener noreferrer"}
- [AWS Security Best Practices](https://docs.aws.amazon.com/whitepapers/latest/aws-security-best-practices/welcome.html){:target="_blank" rel="noopener noreferrer"}

---

## Final Thoughts

Domain 2: Security is fundamental to AWS development and requires both theoretical knowledge and practical implementation skills. Focus heavily on IAM (policies, roles, trust relationships, policy evaluation), Cognito (authentication flows, JWT tokens, federated identities), and KMS (encryption at rest, envelope encryption, key policies). Practice writing IAM policies and implementing authentication in real applications—security is best learned through hands-on experimentation. Master secret management with Secrets Manager and Parameter Store, understand when to use each, and practice retrieving secrets in Lambda functions. Security principles from this domain appear throughout the exam and in real-world AWS development, making it essential to deeply understand authentication, authorization, encryption, and secret management patterns. The time invested in mastering these security fundamentals will pay dividends across all other exam domains and in your AWS development career.
