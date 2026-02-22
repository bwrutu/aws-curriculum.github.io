# AWS Certified Cloud Practitioner (CLF-C02) Domain 3
## Cloud Technology and Services

**Official Exam Guide:** [Domain 3: Cloud Technology and Services](https://docs.aws.amazon.com/aws-certification/latest/examguides/cloud-practitioner-02-domain3.html)  
**Skill Builder:** [AWS Cloud Practitioner Foundational (CLF-C02) Exam Prep](https://skillbuilder.aws/category/exam-prep/cloud-practitioner-foundational-CLF-C02)

---

## How to Study This Domain Effectively

### Study Tips

1. **Group services by category** - Organize services by function: Compute, Storage, Database, Networking, Security, Management, Analytics, Machine Learning. This helps you identify the right service type quickly during the exam.

2. **Focus on use cases** - Understand WHEN to use each service, not deep technical details. Learn "Lambda for serverless event-driven functions" rather than Lambda runtime configurations.

3. **Create comparison tables** - Compare similar services: EC2 vs Lambda, RDS vs DynamoDB, S3 vs EBS vs EFS. Exam questions ask you to choose between similar services based on requirements.

4. **Understand service integration** - Learn how services work together: EC2 + ELB + Auto Scaling, Lambda + API Gateway, S3 + CloudFront.

5. **Use AWS Free Tier** - Hands-on practice with EC2, S3, RDS, and Lambda cements understanding.

### Recommended Approach

1. Start with **Compute** (EC2, Lambda)
2. Learn **Storage** (S3, EBS, EFS)
3. Master **Database** (RDS, DynamoDB)
4. Study **Networking** (VPC, CloudFront, Route 53)
5. Learn **Management & Monitoring** (CloudWatch, CloudFormation)
6. Cover **Application Integration** (SNS, SQS)
7. Review **Analytics & Machine Learning** basics

---

## Core AWS Services by Category

### COMPUTE SERVICES

#### Amazon EC2 (Elastic Compute Cloud)
- Virtual servers in the cloud
- Instance types: General purpose, Compute optimized, Memory optimized
- Pricing: On-Demand, Reserved, Spot, Savings Plans
- Auto Scaling for elasticity
- [Amazon EC2](https://aws.amazon.com/ec2/)

#### AWS Lambda
- Serverless compute - run code without servers
- Event-driven, automatic scaling
- Pay only for compute time
- Use for: Event processing, data transformation, APIs
- [AWS Lambda](https://aws.amazon.com/lambda/)

#### AWS Elastic Beanstalk
- Platform as a Service (PaaS)
- Deploy applications without managing infrastructure
- Handles capacity provisioning, load balancing, auto-scaling
- [AWS Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk/)

#### Container Services
- **Amazon ECS** - AWS container orchestration
- **Amazon EKS** - Managed Kubernetes
- **AWS Fargate** - Serverless containers
- [Amazon ECS](https://aws.amazon.com/ecs/) | [Amazon EKS](https://aws.amazon.com/eks/)

---

### STORAGE SERVICES

#### Amazon S3 (Simple Storage Service)
- Object storage for any type of data
- 11 9's durability (99.999999999%)
- Storage classes: Standard, Intelligent-Tiering, Glacier
- Use for: Backups, data lakes, static websites, archives
- [Amazon S3](https://aws.amazon.com/s3/)

#### Amazon EBS (Elastic Block Store)
- Block storage for EC2 instances
- Volume types: gp3 (general), io2 (high performance), st1 (throughput), sc1 (cold)
- Snapshots for backups
- [Amazon EBS](https://aws.amazon.com/ebs/)

#### Amazon EFS (Elastic File System)
- Shared file storage for multiple EC2 instances
- NFS protocol
- Automatic scaling
- [Amazon EFS](https://aws.amazon.com/efs/)

#### Storage Comparison
- **S3** - Object storage, web accessible
- **EBS** - Block storage, single EC2 instance
- **EFS** - File storage, multiple EC2 instances

---

### DATABASE SERVICES

#### Amazon RDS (Relational Database Service)
- Managed relational databases
- Engines: MySQL, PostgreSQL, Oracle, SQL Server, MariaDB
- Multi-AZ for high availability
- Read replicas for scaling reads
- Use for: Structured data, ACID transactions
- [Amazon RDS](https://aws.amazon.com/rds/)

#### Amazon DynamoDB
- Managed NoSQL database
- Key-value and document data model
- Single-digit millisecond performance
- Automatic scaling
- Use for: High-scale applications, gaming, IoT
- [Amazon DynamoDB](https://aws.amazon.com/dynamodb/)

#### Amazon Aurora
- AWS high-performance relational database
- MySQL and PostgreSQL compatible
- 5x faster than MySQL, 3x faster than PostgreSQL
- Global Database for worldwide replication
- [Amazon Aurora](https://aws.amazon.com/rds/aurora/)

#### Amazon Redshift
- Data warehouse for analytics
- Petabyte-scale
- Use for: Business intelligence, analytics
- [Amazon Redshift](https://aws.amazon.com/redshift/)

#### Database Migration
- **AWS DMS** - Database Migration Service
- **AWS DataSync** - Data transfer service
- [AWS DMS](https://aws.amazon.com/dms/)

---

### NETWORKING & CONTENT DELIVERY

#### Amazon VPC (Virtual Private Cloud)
- Isolated network environment
- Subnets (public and private)
- Internet Gateway, NAT Gateway
- Security Groups, Network ACLs
- [Amazon VPC](https://aws.amazon.com/vpc/)

#### Elastic Load Balancing (ELB)
- Distributes traffic across targets
- Types: Application Load Balancer (ALB), Network Load Balancer (NLB)
- Improves availability and fault tolerance
- [Elastic Load Balancing](https://aws.amazon.com/elasticloadbalancing/)

#### Amazon CloudFront
- Content Delivery Network (CDN)
- Caches content at Edge Locations
- Reduces latency for global users
- [Amazon CloudFront](https://aws.amazon.com/cloudfront/)

#### Amazon Route 53
- DNS web service
- Domain registration
- Health checking and failover
- [Amazon Route 53](https://aws.amazon.com/route53/)

#### AWS Direct Connect
- Dedicated network connection to AWS
- More consistent performance than internet
- [AWS Direct Connect](https://aws.amazon.com/directconnect/)

---

### SECURITY, IDENTITY & COMPLIANCE

#### AWS IAM (Identity and Access Management)
- Users, groups, roles, policies
- Principle of least privilege
- Multi-Factor Authentication (MFA)
- [AWS IAM](https://aws.amazon.com/iam/)

#### AWS KMS (Key Management Service)
- Encryption key management
- Encrypt data at rest
- [AWS KMS](https://aws.amazon.com/kms/)

#### AWS Shield
- DDoS protection
- Shield Standard (free)
- Shield Advanced (enhanced protection)
- [AWS Shield](https://aws.amazon.com/shield/)

#### AWS WAF (Web Application Firewall)
- Protects web applications
- Filter malicious traffic
- [AWS WAF](https://aws.amazon.com/waf/)

---

### MANAGEMENT & GOVERNANCE

#### AWS CloudWatch
- Monitoring and observability
- Metrics, logs, alarms
- Monitor AWS resources and applications
- [Amazon CloudWatch](https://aws.amazon.com/cloudwatch/)

#### AWS CloudTrail
- Audit logging
- Tracks API calls and user activity
- Compliance and security analysis
- [AWS CloudTrail](https://aws.amazon.com/cloudtrail/)

#### AWS CloudFormation
- Infrastructure as Code (IaC)
- Define resources in templates
- Automate provisioning
- [AWS CloudFormation](https://aws.amazon.com/cloudformation/)

#### AWS Systems Manager
- Operational insights and automation
- Patch management, configuration management
- [AWS Systems Manager](https://aws.amazon.com/systems-manager/)

#### AWS Config
- Track configuration changes
- Compliance auditing
- [AWS Config](https://aws.amazon.com/config/)

#### AWS Trusted Advisor
- Best practice recommendations
- Cost optimization, security, performance
- [AWS Trusted Advisor](https://aws.amazon.com/premiumsupport/technology/trusted-advisor/)

---

### APPLICATION INTEGRATION

#### Amazon SNS (Simple Notification Service)
- Pub/sub messaging
- Send notifications to subscribers
- [Amazon SNS](https://aws.amazon.com/sns/)

#### Amazon SQS (Simple Queue Service)
- Message queuing
- Decouple application components
- [Amazon SQS](https://aws.amazon.com/sqs/)

#### AWS Step Functions
- Orchestrate workflows
- Coordinate distributed applications
- [AWS Step Functions](https://aws.amazon.com/step-functions/)

---

### ANALYTICS

#### Amazon Athena
- Query S3 data using SQL
- Serverless
- [Amazon Athena](https://aws.amazon.com/athena/)

#### Amazon EMR (Elastic MapReduce)
- Big data processing
- Hadoop, Spark frameworks
- [Amazon EMR](https://aws.amazon.com/emr/)

#### Amazon Kinesis
- Real-time data streaming
- Process streaming data
- [Amazon Kinesis](https://aws.amazon.com/kinesis/)

#### AWS Glue
- ETL service (Extract, Transform, Load)
- Data catalog
- [AWS Glue](https://aws.amazon.com/glue/)

---

### MACHINE LEARNING & AI

#### Amazon SageMaker
- Build, train, deploy ML models
- Fully managed
- [Amazon SageMaker](https://aws.amazon.com/sagemaker/)

#### Amazon Rekognition
- Image and video analysis
- Face detection, object recognition
- [Amazon Rekognition](https://aws.amazon.com/rekognition/)

#### Amazon Comprehend
- Natural language processing (NLP)
- Sentiment analysis, entity recognition
- [Amazon Comprehend](https://aws.amazon.com/comprehend/)

#### Amazon Lex
- Build conversational interfaces
- Chatbots
- [Amazon Lex](https://aws.amazon.com/lex/)

---

### DEVELOPER TOOLS

#### AWS CodeCommit
- Source control (like GitHub)
- Git repositories
- [AWS CodeCommit](https://aws.amazon.com/codecommit/)

#### AWS CodeBuild
- Compile source code, run tests
- Continuous integration
- [AWS CodeBuild](https://aws.amazon.com/codebuild/)

#### AWS CodeDeploy
- Automated deployment
- Deploy to EC2, Lambda, on-premises
- [AWS CodeDeploy](https://aws.amazon.com/codedeploy/)

#### AWS CodePipeline
- Continuous delivery
- Automate release pipelines
- [AWS CodePipeline](https://aws.amazon.com/codepipeline/)

---

## AWS Service FAQs (Essential Reading)

- [EC2 FAQs](https://aws.amazon.com/ec2/faqs/)
- [S3 FAQs](https://aws.amazon.com/s3/faqs/)
- [Lambda FAQs](https://aws.amazon.com/lambda/faqs/)
- [RDS FAQs](https://aws.amazon.com/rds/faqs/)
- [DynamoDB FAQs](https://aws.amazon.com/dynamodb/faqs/)
- [VPC FAQs](https://aws.amazon.com/vpc/faqs/)
- [CloudFront FAQs](https://aws.amazon.com/cloudfront/faqs/)
- [Route 53 FAQs](https://aws.amazon.com/route53/faqs/)
- [CloudWatch FAQs](https://aws.amazon.com/cloudwatch/faqs/)
- [CloudFormation FAQs](https://aws.amazon.com/cloudformation/faqs/)

---

## AWS Whitepapers

1. **[AWS Overview](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/introduction.html)**
2. **[Architecting for the Cloud](https://docs.aws.amazon.com/whitepapers/latest/architecting-for-the-cloud-aws-best-practices/introduction.html)**
3. **[AWS Storage Services Overview](https://docs.aws.amazon.com/whitepapers/latest/aws-storage-services-overview/welcome.html)**
4. **[AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html)**

---

## Final Thoughts on Domain 3

Domain 3 (Cloud Technology and Services) represents **34% of the exam** - the largest domain.

### Key Takeaways:

1. **Know service categories** - Compute, Storage, Database, Network, Security, Management
2. **Understand use cases** - When to use each service, not technical details
3. **Learn service comparisons** - EC2 vs Lambda, RDS vs DynamoDB, S3 vs EBS vs EFS
4. **Remember integration patterns** - How services work together
5. **Focus on top services** - EC2, Lambda, S3, RDS, DynamoDB, VPC, CloudWatch, IAM

### Study Strategy:

- Spend **35-40% of study time** on this domain
- Create service comparison charts
- Practice identifying services from use case descriptions
- Use AWS Free Tier hands-on
- Memorize service categories and primary use cases

### Common Exam Patterns:

- **Serverless compute?** → Lambda
- **Object storage?** → S3
- **Relational database?** → RDS
- **NoSQL database?** → DynamoDB
- **Content delivery?** → CloudFront
- **Load balancing?** → ELB
- **Monitoring?** → CloudWatch
- **API calls logging?** → CloudTrail

Master the top 20-30 services thoroughly - they cover 80% of exam questions!
