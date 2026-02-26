# AWS Certified Solutions Architect - Professional (SAP-C02) Domain 4
## Accelerate Workload Migration and Modernization

**Official Exam Guide:** <a href="https://docs.aws.amazon.com/aws-certification/latest/examguides/solutions-architect-professional-02-domain4.html" target="_blank">Domain 4: Accelerate Workload Migration and Modernization</a>

**Skill Builder:** <a href="https://skillbuilder.aws/category/exam-prep/solutions-architect-professional-SAP-C02" target="_blank">AWS Certified Solutions Architect - Professional Exam Prep</a>

---

## Domain Overview

Domain 4 (20% of exam) focuses on selecting workloads for migration, determining optimal migration approaches, designing new architectures, and identifying modernization opportunities.

---

## Task 4.1: Select existing workloads and processes for potential migration

**Knowledge Areas:**
- Migration assessment and tracking tools (Migration Hub)
- Portfolio assessment
- Asset planning
- Prioritization and migration (wave planning)

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/migrationhub/latest/ug/" target="_blank">AWS Migration Hub User Guide</a>
- <a href="https://docs.aws.amazon.com/prescriptive-guidance/latest/migration-methodology/" target="_blank">AWS Migration Methodology</a>
- <a href="https://docs.aws.amazon.com/prescriptive-guidance/latest/strategy-migration/" target="_blank">Migration Strategy</a>

**7Rs Migration Strategies:**
- Retire - Eliminate unnecessary applications
- Retain - Keep on-premises for now
- Rehost (Lift-and-shift) - Move as-is to AWS
- Relocate - Move to AWS managed infrastructure (VMware Cloud on AWS)
- Repurchase - Move to SaaS
- Replatform - Optimize during migration
- Refactor/Re-architect - Redesign for cloud-native

---

## Task 4.2: Determine the optimal migration approach for existing workloads

**Knowledge Areas:**
- Data migration tools (DataSync, Transfer Family, Snow Family, S3 Transfer Acceleration)
- Application migration tools (Application Discovery Service, Application Migration Service)
- AWS networking services and DNS (Direct Connect, Site-to-Site VPN, Route 53)
- Identity services (IAM Identity Center, Directory Service)
- Database migration tools (DMS, SCT)
- Governance tools (Control Tower, Organizations)

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/datasync/latest/userguide/" target="_blank">AWS DataSync</a>
- <a href="https://docs.aws.amazon.com/mgn/latest/ug/" target="_blank">AWS Application Migration Service</a>
- <a href="https://docs.aws.amazon.com/dms/latest/userguide/" target="_blank">AWS Database Migration Service</a>
- <a href="https://docs.aws.amazon.com/SchemaConversionTool/latest/userguide/" target="_blank">AWS Schema Conversion Tool</a>
- <a href="https://docs.aws.amazon.com/snowball/latest/developer-guide/" target="_blank">AWS Snow Family</a>

---

## Task 4.3: Determine a new architecture for existing workloads

**Knowledge Areas:**
- Compute services (EC2, Elastic Beanstalk)
- Containers (ECS, EKS, Fargate, ECR)
- AWS storage services (EBS, EFS, FSx, S3, Storage Gateway)
- Databases (DynamoDB, OpenSearch, RDS, self-managed on EC2)

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/" target="_blank">Amazon EC2 User Guide</a>
- <a href="https://docs.aws.amazon.com/AmazonECS/latest/developerguide/" target="_blank">Amazon ECS Developer Guide</a>
- <a href="https://docs.aws.amazon.com/eks/latest/userguide/" target="_blank">Amazon EKS User Guide</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/" target="_blank">Amazon RDS User Guide</a>
- <a href="https://docs.aws.amazon.com/fsx/latest/WindowsGuide/" target="_blank">Amazon FSx for Windows File Server</a>

---

## Task 4.4: Determine opportunities for modernization and enhancements

**Knowledge Areas:**
- Serverless compute (Lambda)
- Containers (ECS, EKS, Fargate)
- AWS storage services (S3, EFS)
- Purpose-built databases (DynamoDB, Aurora Serverless, ElastiCache)
- Integration services (SQS, SNS, EventBridge, Step Functions)

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/lambda/latest/dg/" target="_blank">AWS Lambda Developer Guide</a>
- <a href="https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/" target="_blank">Amazon DynamoDB Developer Guide</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/aurora-serverless.html" target="_blank">Aurora Serverless</a>
- <a href="https://docs.aws.amazon.com/step-functions/latest/dg/" target="_blank">AWS Step Functions</a>
- <a href="https://docs.aws.amazon.com/eventbridge/latest/userguide/" target="_blank">Amazon EventBridge</a>

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/application-migration-service/faqs/" target="_blank">AWS Application Migration Service FAQs</a>
- <a href="https://aws.amazon.com/dms/faqs/" target="_blank">AWS Database Migration Service FAQs</a>
- <a href="https://aws.amazon.com/datasync/faqs/" target="_blank">AWS DataSync FAQs</a>
- <a href="https://aws.amazon.com/lambda/faqs/" target="_blank">AWS Lambda FAQs</a>

---

## Study Tips

1. **Master the 7Rs** - Understand when to use each migration strategy based on application characteristics, business requirements, and timeline.

2. **Learn migration tools** - AWS Application Migration Service for servers, DMS for databases, DataSync for file systems, Snow Family for large data.

3. **Understand database migration** - DMS for homogeneous and heterogeneous migrations, SCT for schema conversion, read replicas for minimal downtime.

4. **Practice modernization patterns** - Monolith to microservices, VMs to containers, traditional databases to purpose-built, synchronous to event-driven.

5. **Study TCO analysis** - Compare on-premises costs (hardware, software, facilities, staff) vs AWS costs with appropriate purchasing options.

---

## Complete Exam Summary

**Exam Format:**
- 75 questions (65 scored + 10 unscored)
- Multiple choice and multiple response
- Passing score: 750/1000
- 180 minutes

**Domain Weightings:**
- Domain 1: Design Solutions for Organizational Complexity (26%)
- Domain 2: Design for New Solutions (29%)
- Domain 3: Continuous Improvement for Existing Solutions (25%)
- Domain 4: Accelerate Workload Migration and Modernization (20%)

**Target Candidate:**
- 2+ years designing and implementing cloud solutions on AWS
- Advanced understanding of Well-Architected Framework
- Experience with complex, multi-application architectures

**Key Areas to Master:**
- **Networking:** VPC, Transit Gateway, Direct Connect, Route 53
- **Security:** IAM, encryption, security services, least privilege
- **Reliability:** Multi-AZ/Region, DR strategies, auto scaling
- **Performance:** CloudFront, caching, purpose-built databases
- **Cost:** Reserved Instances, Savings Plans, rightsizing, tagging
- **Migration:** 7Rs, migration tools, modernization patterns
- **Multi-Account:** Organizations, Control Tower, Resource Access Manager

**Well-Architected Framework Pillars:**
1. Operational Excellence
2. Security
3. Reliability
4. Performance Efficiency
5. Cost Optimization
6. Sustainability

**Study Resources:**
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html" target="_blank">AWS Well-Architected Framework</a>
- <a href="https://aws.amazon.com/architecture/" target="_blank">AWS Architecture Center</a>
- <a href="https://aws.amazon.com/whitepapers/" target="_blank">AWS Whitepapers</a>

Good luck with your AWS Certified Solutions Architect - Professional certification!

---

**Note:** This is Domain 4 of 4, representing 20% of exam content.
