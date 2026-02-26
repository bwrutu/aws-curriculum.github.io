# AWS Certified Solutions Architect - Professional (SAP-C02) Domain 2
## Design for New Solutions

**Official Exam Guide:** <a href="https://docs.aws.amazon.com/aws-certification/latest/examguides/solutions-architect-professional-02-domain2.html" target="_blank">Domain 2: Design for New Solutions</a>

**Skill Builder:** <a href="https://skillbuilder.aws/category/exam-prep/solutions-architect-professional-SAP-C02" target="_blank">AWS Certified Solutions Architect - Professional Exam Prep</a>

---

## Domain Overview

Domain 2 (29% - largest domain) focuses on deployment strategies, business continuity, security controls, reliability, performance objectives, and cost optimization for new solutions.

---

## Task 2.1: Design a deployment strategy to meet business requirements

**Knowledge Areas:**
- Infrastructure as code (CloudFormation)
- CI/CD pipelines
- Change management processes
- Configuration management (Systems Manager)

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/" target="_blank">AWS CloudFormation User Guide</a>
- <a href="https://docs.aws.amazon.com/codepipeline/latest/userguide/" target="_blank">AWS CodePipeline</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/" target="_blank">AWS Systems Manager</a>

---

## Task 2.2: Design a solution to ensure business continuity

**Knowledge Areas:**
- AWS Global Infrastructure
- AWS networking (Route 53, routing methods)
- RTOs and RPOs
- Disaster recovery scenarios
- DR solutions on AWS

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/" target="_blank">Amazon Route 53 Developer Guide</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/" target="_blank">Reliability Pillar - Well-Architected</a>
- <a href="https://docs.aws.amazon.com/drs/latest/userguide/" target="_blank">AWS Elastic Disaster Recovery</a>

---

## Task 2.3: Determine security controls based on requirements

**Knowledge Areas:**
- IAM
- Route tables, security groups, network ACLs
- Encryption for data at rest and in transit
- AWS service endpoints
- Credential management
- AWS managed security services (Shield, WAF, GuardDuty, Security Hub)

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/IAM/latest/UserGuide/" target="_blank">AWS IAM User Guide</a>
- <a href="https://docs.aws.amazon.com/waf/latest/developerguide/" target="_blank">AWS WAF Developer Guide</a>
- <a href="https://docs.aws.amazon.com/guardduty/latest/ug/" target="_blank">Amazon GuardDuty User Guide</a>
- <a href="https://docs.aws.amazon.com/secretsmanager/latest/userguide/" target="_blank">AWS Secrets Manager</a>

---

## Task 2.4: Design a strategy to meet reliability requirements

**Knowledge Areas:**
- AWS Global Infrastructure
- AWS storage services and replication
- Multi-AZ and multi-Region architectures
- Auto scaling policies
- Application integration (SNS, SQS, Step Functions)
- Service quotas and limits

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/autoscaling/ec2/userguide/" target="_blank">Amazon EC2 Auto Scaling</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.MultiAZ.html" target="_blank">Amazon RDS Multi-AZ</a>
- <a href="https://docs.aws.amazon.com/step-functions/latest/dg/" target="_blank">AWS Step Functions</a>

---

## Task 2.5: Design a solution to meet performance objectives

**Knowledge Areas:**
- Performance monitoring technologies
- Storage options on AWS
- Instance families and use cases
- Purpose-built databases

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/" target="_blank">Amazon CloudWatch</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-types.html" target="_blank">Amazon EC2 Instance Types</a>
- <a href="https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/" target="_blank">Amazon DynamoDB</a>
- <a href="https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/" target="_blank">Amazon ElastiCache</a>

---

## Task 2.6: Determine a cost optimization strategy

**Knowledge Areas:**
- AWS cost monitoring tools (Cost Explorer, Trusted Advisor, Pricing Calculator)
- Pricing models (Reserved Instances, Savings Plans)
- Storage tiering
- Data transfer costs
- AWS managed service offerings

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/cost-management/latest/userguide/" target="_blank">AWS Cost Management</a>
- <a href="https://aws.amazon.com/savingsplans/" target="_blank">AWS Savings Plans</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/storage-class-intro.html" target="_blank">Amazon S3 Storage Classes</a>

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/cloudformation/faqs/" target="_blank">AWS CloudFormation FAQs</a>
- <a href="https://aws.amazon.com/route53/faqs/" target="_blank">Amazon Route 53 FAQs</a>
- <a href="https://aws.amazon.com/autoscaling/faqs/" target="_blank">AWS Auto Scaling FAQs</a>
- <a href="https://aws.amazon.com/rds/faqs/" target="_blank">Amazon RDS FAQs</a>

---

## Study Tips

1. **Master CloudFormation** - Understand stacks, nested stacks, StackSets for multi-account/region, change sets, drift detection.

2. **Learn DR strategies** - Match RTO/RPO requirements to appropriate DR strategy (backup/restore cheapest but slowest recovery, multi-site fastest but most expensive).

3. **Understand security layers** - Defense in depth: VPC isolation, security groups, NACLs, WAF, GuardDuty, encryption, IAM policies.

4. **Practice performance optimization** - Caching (CloudFront, ElastiCache), right instance types, purpose-built databases, auto-scaling.

5. **Study cost optimization** - Storage tiering, Reserved Instances vs Savings Plans, data transfer costs, rightsizing.

---

**Note:** This is Domain 2 of 4, representing 29% (largest domain) of exam content.
