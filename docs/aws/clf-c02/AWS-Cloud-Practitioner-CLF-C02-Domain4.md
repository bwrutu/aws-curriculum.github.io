# AWS Certified Cloud Practitioner (CLF-C02) Domain 4
## Billing, Pricing, and Support

**Official Exam Guide:** [Domain 4: Billing, Pricing, and Support](https://docs.aws.amazon.com/aws-certification/latest/examguides/cloud-practitioner-02-domain4.html)  
**Skill Builder:** [AWS Cloud Practitioner Foundational (CLF-C02) Exam Prep](https://skillbuilder.aws/category/exam-prep/cloud-practitioner-foundational-CLF-C02)

Note: Some Skill Builder labs require a subscription.

---

## How to Study This Domain Effectively

### Study Tips

1. **Practice with real pricing scenarios** - Use the AWS Pricing Calculator to model different compute purchasing options (On-Demand vs Reserved vs Spot) for the same workload. Understanding the cost implications hands-on will help you quickly identify the right option during the exam when presented with scenario-based questions about cost optimization.

2. **Create a comparison matrix** - Build a side-by-side comparison table of all compute purchasing options, storage tiers, and Support plans with their key features, use cases, and pricing models. This visual reference helps you quickly recall differences when exam questions ask you to "compare" or "identify the most cost-effective option."

3. **Familiarize yourself with the AWS billing console** - Even with a free tier account, explore AWS Cost Explorer, AWS Budgets, and the billing dashboard. Knowing where to find billing information and how these tools work is crucial for questions about cost management and monitoring.

4. **Understand the relationship between services** - Many exam questions test your knowledge of how billing features work together (e.g., how cost allocation tags relate to Cost and Usage Reports, or how AWS Organizations enables consolidated billing). Study these connections, not just individual services in isolation.

5. **Memorize Support plan features** - Create flashcards for the different AWS Support plans (Developer, Business, Enterprise On-Ramp, Enterprise) with their key features, response times, and use cases. Exam questions frequently test your ability to recommend the appropriate Support plan based on specific business requirements.

### Recommended Approach

1. **Start with AWS pricing fundamentals** - Begin by reading the AWS Pricing Overview and understanding the core pricing models (pay-as-you-go, save when you reserve, pay less by using more). This foundation helps you understand why different purchasing options exist and when to use them.

2. **Deep dive into compute purchasing options** - Study each compute purchasing option (On-Demand, Reserved Instances, Savings Plans, Spot, Dedicated) in detail, focusing on their flexibility, commitment requirements, and ideal use cases. Use the EC2 pricing documentation and FAQs to understand the nuances of each option.

3. **Master cost management tools** - Study AWS Budgets, Cost Explorer, and AWS Pricing Calculator in sequence. Understand what each tool does, when to use it, and how they complement each other. Pay special attention to AWS Organizations and consolidated billing, as these are frequently tested.

4. **Learn Support resources comprehensively** - Study AWS Support plans first, then expand to understanding technical resources like AWS Prescriptive Guidance, Knowledge Center, AWS re:Post, and the role of AWS Partners. Understanding the entire support ecosystem helps you answer questions about where to find help for different scenarios.

5. **Review whitepapers and finish with practice** - Read the Cost Optimization pillar of the Well-Architected Framework and the AWS Pricing Overview whitepaper. Then take practice exams focusing on Domain 4 to identify gaps in your knowledge and revisit specific documentation as needed.

---

## Task 4.1: Compare AWS pricing models

### Knowledge Areas & AWS Documentation Reading List

#### 1. Compute purchasing options (for example, On-Demand Instances, Reserved Instances, Spot Instances, AWS Savings Plans, Dedicated Hosts, Dedicated Instances, Capacity Reservations)

**Why:** This is one of the most heavily tested knowledge areas in Domain 4. Exam questions frequently present scenarios where you must identify the most cost-effective compute purchasing option based on workload characteristics (predictable vs variable usage, flexibility requirements, commitment tolerance). Understanding the differences between Reserved Instances, Savings Plans, and Spot Instances is critical for answering cost optimization questions, which appear across multiple domains. Real-world AWS architects must regularly make these purchasing decisions to balance cost and performance requirements.

**AWS Documentation:**
- [Amazon EC2 Pricing](https://aws.amazon.com/ec2/pricing/)
- [Amazon EC2 On-Demand Pricing](https://aws.amazon.com/ec2/pricing/on-demand/)
- [Amazon EC2 Reserved Instances](https://aws.amazon.com/ec2/pricing/reserved-instances/)
- [Amazon EC2 Reserved Instances Pricing](https://aws.amazon.com/ec2/pricing/reserved-instances/pricing/)
- [Amazon EC2 Spot Instances](https://aws.amazon.com/ec2/spot/)
- [Amazon EC2 Spot Instances Pricing](https://aws.amazon.com/ec2/spot/pricing/)
- [AWS Savings Plans](https://aws.amazon.com/savingsplans/)
- [AWS Savings Plans Pricing](https://aws.amazon.com/savingsplans/pricing/)
- [Compute Savings Plans](https://aws.amazon.com/savingsplans/compute-pricing/)
- [EC2 Instance Savings Plans](https://aws.amazon.com/savingsplans/ec2-instance-pricing/)
- [Amazon EC2 Dedicated Hosts](https://aws.amazon.com/ec2/dedicated-hosts/)
- [Amazon EC2 Dedicated Hosts Pricing](https://aws.amazon.com/ec2/dedicated-hosts/pricing/)
- [Amazon EC2 Dedicated Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/dedicated-instance.html)
- [Amazon EC2 Capacity Reservations](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-capacity-reservations.html)
- [On-Demand Capacity Reservations Pricing](https://aws.amazon.com/ec2/pricing/on-demand/)

#### 2. Storage options and tiers

**Why:** Storage pricing is tested through scenarios that require you to match storage tiers with use cases based on access patterns, retrieval requirements, and cost constraints. Exam questions often present data lifecycle scenarios where you must identify the most cost-effective storage class (e.g., S3 Standard vs S3 Intelligent-Tiering vs S3 Glacier). Understanding storage tier pricing helps you answer questions about cost optimization for data that's accessed frequently versus infrequently. This knowledge is essential because storage costs can significantly impact overall AWS bills, especially for data-heavy workloads.

**AWS Documentation:**
- [Amazon S3 Pricing](https://aws.amazon.com/s3/pricing/)
- [Amazon S3 Storage Classes](https://aws.amazon.com/s3/storage-classes/)
- [Amazon S3 Intelligent-Tiering](https://aws.amazon.com/s3/storage-classes/intelligent-tiering/)
- [Amazon S3 Glacier Storage Classes](https://aws.amazon.com/s3/storage-classes/glacier/)
- [Amazon EBS Pricing](https://aws.amazon.com/ebs/pricing/)
- [Amazon EBS Volume Types](https://docs.aws.amazon.com/ebs/latest/userguide/ebs-volume-types.html)
- [Amazon EFS Pricing](https://aws.amazon.com/efs/pricing/)
- [Amazon EFS Storage Classes](https://aws.amazon.com/efs/storage-classes/)
- [AWS Storage Services Overview](https://aws.amazon.com/products/storage/)

### Skills & Corresponding Documentation

#### Identifying when to use various compute purchasing options

**Why:** This skill is tested through scenario-based questions where you're given specific workload characteristics and must select the appropriate purchasing option. Exam questions will describe usage patterns (steady-state vs variable, mission-critical vs fault-tolerant, short-term vs long-term) and expect you to recommend On-Demand, Reserved Instances, Spot, or Savings Plans accordingly. Understanding the decision criteria for each option is crucial for cost optimization questions throughout the exam.

**AWS Documentation:**
- [Optimizing your cost with Amazon EC2 Auto Scaling](https://docs.aws.amazon.com/autoscaling/ec2/userguide/cost-optimization.html)
- [Amazon EC2 Instance Purchasing Options](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-purchasing-options.html)
- [How to Choose Between Savings Plans and Reserved Instances](https://aws.amazon.com/blogs/aws-cloud-financial-management/understanding-your-savings-plan-recommendations/)
- [Spot Instance Best Practices](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/spot-best-practices.html)
- [When to Use Spot Instances](https://docs.aws.amazon.com/whitepapers/latest/cost-optimization-leveraging-ec2-spot-instances/when-to-use-spot-instances.html)

#### Describing Reserved Instance flexibility

**Why:** Exam questions test your understanding of how Reserved Instances can be modified and applied across different instance types, sizes, and Availability Zones. You need to know the difference between Standard and Convertible Reserved Instances, regional versus zonal Reserved Instances, and instance size flexibility within an instance family. This knowledge helps answer questions about optimizing Reserved Instance usage and maximizing cost savings across changing workload requirements.

**AWS Documentation:**
- [Reserved Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-reserved-instances.html)
- [How Reserved Instances are Applied](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/apply_ri.html)
- [Instance Size Flexibility for EC2 Reserved Instances](https://aws.amazon.com/blogs/aws/new-instance-size-flexibility-for-ec2-reserved-instances/)
- [Regional and Zonal Reserved Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/reserved-instances-scope.html)
- [Modifying Reserved Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ri-modifying.html)
- [Convertible Reserved Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ri-convertible-exchange.html)

#### Describing Reserved Instance behavior in AWS Organizations

**Why:** Understanding how Reserved Instances work within AWS Organizations is critical for questions about consolidated billing and cost optimization across multiple accounts. Exam scenarios often involve organizations with multiple AWS accounts that need to share Reserved Instance benefits. You must know how Reserved Instance discounts are automatically applied across linked accounts and how this affects billing and cost allocation.

**AWS Documentation:**
- [Reserved Instances and Savings Plans Sharing in AWS Organizations](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/ri-turn-off.html)
- [Consolidated Billing for AWS Organizations](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/consolidated-billing.html)
- [AWS Organizations - Reserved Instance and Savings Plans Discount Sharing](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps_examples_billing.html)
- [Managing Reserved Instance Sharing](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/manage-ri-sharing.html)

#### Understanding incoming data transfer costs and outgoing data transfer costs (for example, from one AWS Region to another Region, within the same Region)

**Why:** Data transfer pricing is a common exam topic that tests your understanding of when data transfer is free versus when it incurs costs. Questions present scenarios involving data movement between AWS services, Availability Zones, Regions, and to the internet, expecting you to identify which transfers incur charges. Understanding data transfer costs is essential for architecting cost-effective solutions and avoiding unexpected billing surprises in production environments.

**AWS Documentation:**
- [AWS Data Transfer Pricing](https://aws.amazon.com/ec2/pricing/on-demand/#Data_Transfer)
- [Amazon EC2 Data Transfer](https://aws.amazon.com/ec2/pricing/on-demand/#Data_Transfer)
- [Understanding Data Transfer Costs](https://aws.amazon.com/blogs/architecture/overview-of-data-transfer-costs-for-common-architectures/)
- [Data Transfer within the Same AWS Region](https://aws.amazon.com/ec2/pricing/on-demand/)
- [Amazon CloudFront Pricing - Data Transfer](https://aws.amazon.com/cloudfront/pricing/)
- [VPC Data Transfer Costs](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html#nat-gateway-pricing)

#### Understanding pricing options for various storage options and tiers

**Why:** This skill is tested through questions that require matching storage classes with specific use cases based on access frequency, retrieval time requirements, and cost constraints. You must understand the pricing differences between S3 storage classes (Standard, Intelligent-Tiering, Glacier, etc.), EBS volume types (gp3, io2, st1), and EFS storage classes. Exam scenarios often describe data access patterns and ask you to select the most cost-effective storage option.

**AWS Documentation:**
- [Comparing Amazon S3 Storage Classes](https://aws.amazon.com/s3/storage-classes/#Performance_across_the_S3_Storage_Classes)
- [Amazon S3 Storage Classes - Use Cases](https://docs.aws.amazon.com/AmazonS3/latest/userguide/storage-class-intro.html)
- [Amazon S3 Lifecycle Configuration](https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lifecycle-mgmt.html)
- [EBS Volume Types and Performance](https://docs.aws.amazon.com/ebs/latest/userguide/ebs-volume-types.html)
- [Amazon EFS Performance](https://docs.aws.amazon.com/efs/latest/ug/performance.html)
- [Cost Optimization with Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/optimizing-cost.html)

**AWS Service FAQs:**

- [Amazon EC2 FAQ](https://aws.amazon.com/ec2/faqs/)
- [Amazon EC2 Reserved Instances FAQ](https://aws.amazon.com/ec2/faqs/#reserved-instances)
- [Amazon EC2 Spot Instances FAQ](https://aws.amazon.com/ec2/faqs/#spot-instances)
- [AWS Savings Plans FAQ](https://aws.amazon.com/savingsplans/faq/)
- [Amazon S3 FAQ](https://aws.amazon.com/s3/faqs/)
- [Amazon EBS FAQ](https://aws.amazon.com/ebs/faqs/)
- [Amazon EFS FAQ](https://aws.amazon.com/efs/faq/)
- [Amazon S3 Glacier FAQ](https://aws.amazon.com/s3/faqs/#Amazon_S3_Glacier)

**AWS Whitepapers:**

- [Cost Optimization Pillar - AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/cost-optimization-pillar/welcome.html)
- [AWS Pricing Overview](https://docs.aws.amazon.com/whitepapers/latest/how-aws-pricing-works/welcome.html)
- [Cost Optimization: EC2 Right Sizing](https://aws.amazon.com/aws-cost-management/aws-cost-optimization/right-sizing/)
- [Overview of Amazon Web Services](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/introduction.html)

---

## Task 4.2: Understand resources for billing, budget, and cost management

### Knowledge Areas & AWS Documentation Reading List

#### 1. Billing support and information

**Why:** Exam questions test your knowledge of where to find billing information and how to access billing support within AWS. You need to understand the AWS Billing Console structure, where to view invoices, how to access detailed cost reports, and when to contact AWS billing support. This knowledge area appears in questions about troubleshooting billing issues, understanding charges, and accessing historical billing data. Understanding billing support options is essential for managing AWS costs effectively in real-world scenarios.

**AWS Documentation:**
- [AWS Billing and Cost Management](https://docs.aws.amazon.com/cost-management/)
- [AWS Billing Console](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-what-is.html)
- [Understanding Your AWS Billing and Usage Reports](https://docs.aws.amazon.com/cur/latest/userguide/what-is-cur.html)
- [Managing Your AWS Payments](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/manage-payments.html)
- [Viewing Your Monthly Charges](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/getting-viewing-bill.html)
- [AWS Free Tier](https://aws.amazon.com/free/)
- [AWS Billing and Cost Management User Guide](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-what-is.html)

#### 2. Pricing information for AWS services

**Why:** This knowledge area tests your ability to locate and understand AWS service pricing information. Exam questions may ask where to find pricing details for specific services or how pricing varies based on service configurations and usage patterns. You must know how to use AWS pricing pages, understand the factors that affect pricing (region, usage volume, data transfer), and identify resources for comparing costs. This is fundamental for cost estimation and optimization in real-world AWS deployments.

**AWS Documentation:**
- [AWS Pricing](https://aws.amazon.com/pricing/)
- [AWS Service Pricing Pages](https://aws.amazon.com/pricing/)
- [AWS Pricing Calculator](https://calculator.aws/)
- [AWS Price List API](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/price-changes.html)
- [AWS Price List Service](https://aws.amazon.com/blogs/aws/aws-price-list-api-update-new-bulk-consumption-model/)
- [Understanding AWS Pricing](https://aws.amazon.com/pricing/)

#### 3. AWS Organizations

**Why:** AWS Organizations is heavily tested in billing and cost management questions because it enables consolidated billing and centralized cost allocation across multiple AWS accounts. Exam scenarios often involve organizations managing multiple accounts that need to share Reserved Instance benefits, apply service control policies, or allocate costs across departments. Understanding how Organizations impacts billing, enables volume discounts, and facilitates cost tracking is critical for multi-account cost management questions.

**AWS Documentation:**
- [AWS Organizations](https://aws.amazon.com/organizations/)
- [AWS Organizations User Guide](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_introduction.html)
- [Consolidated Billing for AWS Organizations](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/consolidated-billing.html)
- [Best Practices for AWS Organizations](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_best-practices.html)
- [AWS Organizations - Managing Costs](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_tag-policies.html)
- [Service Control Policies and Billing](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps.html)

#### 4. AWS cost allocation tags

**Why:** Cost allocation tags are essential for tracking and organizing AWS costs, and exam questions frequently test your understanding of how tags work with billing reports. You need to know the difference between AWS-generated tags and user-defined tags, how to activate tags for cost tracking, and how tags appear in cost reports. This knowledge is critical for questions about cost allocation, chargeback/showback scenarios, and organizing costs by project, department, or environment in real-world AWS environments.

**AWS Documentation:**
- [Using Cost Allocation Tags](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/cost-alloc-tags.html)
- [AWS-Generated Cost Allocation Tags](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/aws-tags.html)
- [User-Defined Cost Allocation Tags](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/custom-tags.html)
- [Activating User-Defined Cost Allocation Tags](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/activating-tags.html)
- [Tag Policies in AWS Organizations](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_tag-policies.html)
- [Tagging Best Practices](https://docs.aws.amazon.com/whitepapers/latest/tagging-best-practices/tagging-best-practices.html)

### Skills & Corresponding Documentation

#### Understanding the appropriate uses and capabilities of AWS Budgets and AWS Cost Explorer

**Why:** This is a frequently tested skill that requires you to differentiate between AWS Budgets and Cost Explorer and know when to use each tool. Exam questions present scenarios where you need to recommend the right tool for specific cost management tasks: setting cost alerts (Budgets), analyzing historical spending patterns (Cost Explorer), forecasting future costs (both), or tracking costs by service or tag. Understanding these tools is essential for proactive cost management and preventing budget overruns.

**AWS Documentation:**
- [AWS Budgets](https://aws.amazon.com/aws-cost-management/aws-budgets/)
- [Managing Your Costs with AWS Budgets](https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-managing-costs.html)
- [Creating a Budget](https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-create.html)
- [AWS Cost Explorer](https://aws.amazon.com/aws-cost-management/aws-cost-explorer/)
- [Analyzing Your Costs with AWS Cost Explorer](https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html)
- [Using AWS Cost Explorer to Understand Your Costs](https://docs.aws.amazon.com/cost-management/latest/userguide/ce-exploring-data.html)
- [Cost Explorer Forecasting](https://docs.aws.amazon.com/cost-management/latest/userguide/ce-forecast.html)
- [Best Practices for AWS Cost Management](https://aws.amazon.com/aws-cost-management/cost-optimization/)

#### Understanding the appropriate uses and capabilities of AWS Pricing Calculator

**Why:** Exam questions test your knowledge of when and how to use AWS Pricing Calculator for estimating costs before deploying resources. You must understand that Pricing Calculator is used for pre-deployment cost estimation and architecture planning, not for analyzing actual spending. Questions may ask you to identify scenarios where Pricing Calculator is the appropriate tool versus AWS Budgets or Cost Explorer for cost planning and comparison.

**AWS Documentation:**
- [AWS Pricing Calculator](https://calculator.aws/)
- [AWS Pricing Calculator User Guide](https://docs.aws.amazon.com/pricing-calculator/latest/userguide/what-is-pricing-calculator.html)
- [Getting Started with AWS Pricing Calculator](https://docs.aws.amazon.com/pricing-calculator/latest/userguide/getting-started.html)
- [Creating an Estimate in AWS Pricing Calculator](https://docs.aws.amazon.com/pricing-calculator/latest/userguide/creating-an-estimate.html)
- [AWS TCO Calculator Migration](https://aws.amazon.com/pricing/tco-calculator/)

#### Understanding AWS Organizations consolidated billing and allocation of costs

**Why:** This skill is critical for multi-account billing scenarios that commonly appear on the exam. You need to understand how consolidated billing combines usage across linked accounts for volume discounts, how the management account receives a single bill, and how Reserved Instance and Savings Plans benefits are shared across accounts. Exam questions often present scenarios involving multiple departments or teams with separate AWS accounts that need cost tracking and allocation.

**AWS Documentation:**
- [Consolidated Billing for AWS Organizations](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/consolidated-billing.html)
- [Consolidated Billing Process](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/useconsolidatedbilling-procedure.html)
- [Understanding Consolidated Bills](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/con-bill-blended-rates.html)
- [Volume Discounts and Consolidated Billing](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/useconsolidatedbilling-discounts.html)
- [AWS Organizations - Cost Allocation](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/allocate-costs.html)
- [Best Practices for Consolidated Billing](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/useconsolidatedbilling-best-practices.html)

#### Understanding various types of cost allocation tags and their relation to billing reports (for example, AWS Cost and Usage Report)

**Why:** Exam questions test your understanding of how different types of cost allocation tags (AWS-generated vs user-defined) work with billing reports, particularly the AWS Cost and Usage Report. You must know that tags need to be activated before they appear in cost reports, understand the difference between resource-level tags and account-level tags, and know how tags enable cost tracking and allocation. This knowledge is essential for implementing chargeback systems and detailed cost analysis.

**AWS Documentation:**
- [AWS Cost and Usage Report](https://docs.aws.amazon.com/cur/latest/userguide/what-is-cur.html)
- [Setting Up the AWS Cost and Usage Report](https://docs.aws.amazon.com/cur/latest/userguide/cur-create.html)
- [Cost Allocation Tags in Cost and Usage Reports](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/cost-alloc-tags.html)
- [Understanding Your Cost and Usage Report](https://docs.aws.amazon.com/cur/latest/userguide/understanding-cur.html)
- [Using Cost Allocation Tags with AWS Cost and Usage Report](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/configurecostallocreport.html)
- [Cost Categories](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/manage-cost-categories.html)

**AWS Service FAQs:**

- [AWS Billing and Cost Management FAQ](https://aws.amazon.com/aws-cost-management/faqs/)
- [AWS Budgets FAQ](https://aws.amazon.com/aws-cost-management/aws-budgets/faqs/)
- [AWS Cost Explorer FAQ](https://aws.amazon.com/aws-cost-management/aws-cost-explorer/faqs/)
- [AWS Organizations FAQ](https://aws.amazon.com/organizations/faqs/)
- [AWS Cost and Usage Report FAQ](https://aws.amazon.com/aws-cost-management/aws-cost-and-usage-reporting/faqs/)

**AWS Whitepapers:**

- [Cost Optimization Pillar - AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/cost-optimization-pillar/welcome.html)
- [Tagging Best Practices](https://docs.aws.amazon.com/whitepapers/latest/tagging-best-practices/tagging-best-practices.html)
- [AWS Pricing Overview](https://docs.aws.amazon.com/whitepapers/latest/how-aws-pricing-works/welcome.html)
- [AWS Cost Management](https://aws.amazon.com/aws-cost-management/)

---

## Task 4.3: Identify AWS technical resources and AWS Support options

### Knowledge Areas & AWS Documentation Reading List

#### 1. Resources and documentation available on official AWS websites

**Why:** This knowledge area tests your ability to identify where to find official AWS information and documentation. Exam questions expect you to know the difference between various AWS resource types (user guides, API references, whitepapers, blogs) and when to use each. Understanding where to find reliable AWS information is fundamental for both exam preparation and real-world AWS work, as you need to reference official documentation to implement services correctly and follow best practices.

**AWS Documentation:**
- [AWS Documentation](https://docs.aws.amazon.com/)
- [AWS Whitepapers and Guides](https://aws.amazon.com/whitepapers/)
- [AWS Architecture Center](https://aws.amazon.com/architecture/)
- [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/)
- [AWS Blogs](https://aws.amazon.com/blogs/)
- [AWS News](https://aws.amazon.com/new/)
- [AWS Case Studies](https://aws.amazon.com/solutions/case-studies/)
- [AWS Reference Architectures](https://aws.amazon.com/architecture/reference-architecture-diagrams/)

#### 2. AWS Support plans

**Why:** AWS Support plans are heavily tested because you must be able to recommend the appropriate plan based on business requirements and SLA needs. Exam questions present scenarios describing company size, criticality of workloads, required response times, and need for technical guidance, expecting you to select the right Support plan (Basic, Developer, Business, Enterprise On-Ramp, or Enterprise). Understanding the features, pricing, and use cases for each plan is essential for making support recommendations in real-world AWS environments.

**AWS Documentation:**
- [AWS Support](https://aws.amazon.com/premiumsupport/)
- [AWS Support Plans](https://aws.amazon.com/premiumsupport/plans/)
- [Compare AWS Support Plans](https://aws.amazon.com/premiumsupport/plans/)
- [AWS Basic Support](https://aws.amazon.com/premiumsupport/plans/basic/)
- [AWS Developer Support](https://aws.amazon.com/premiumsupport/plans/developers/)
- [AWS Business Support](https://aws.amazon.com/premiumsupport/plans/business/)
- [AWS Enterprise On-Ramp Support](https://aws.amazon.com/premiumsupport/plans/enterprise-onramp/)
- [AWS Enterprise Support](https://aws.amazon.com/premiumsupport/plans/enterprise/)
- [AWS Support Features](https://aws.amazon.com/premiumsupport/features/)

#### 3. Role of the AWS Partner Network, including independent software vendors and system integrators

**Why:** Exam questions test your understanding of how AWS Partners extend AWS capabilities and provide specialized services. You need to know the different types of partners (consulting partners, technology partners, managed service providers), what services they offer, and when to engage partners versus using AWS resources directly. This knowledge helps answer questions about implementing complex solutions, accessing specialized expertise, and understanding the AWS ecosystem beyond AWS-provided services.

**AWS Documentation:**
- [AWS Partner Network (APN)](https://aws.amazon.com/partners/)
- [Types of AWS Partners](https://aws.amazon.com/partners/programs/)
- [AWS Consulting Partners](https://aws.amazon.com/partners/consulting/)
- [AWS Technology Partners](https://aws.amazon.com/partners/technology/)
- [AWS Managed Service Providers (MSP)](https://aws.amazon.com/partners/programs/msp/)
- [Find AWS Partners](https://aws.amazon.com/partners/find/)
- [AWS Partner Success Stories](https://aws.amazon.com/partners/success/)

#### 4. AWS Support Center

**Why:** Understanding the AWS Support Center is tested through questions about where to create and manage support cases, access AWS Trusted Advisor checks, and view support case history. You must know the capabilities of the Support Center, what actions can be performed there, and which Support plans are required for different features. This knowledge is practical for managing AWS accounts and resolving technical or billing issues in real-world scenarios.

**AWS Documentation:**
- [AWS Support Center](https://console.aws.amazon.com/support/home)
- [Getting Started with AWS Support](https://docs.aws.amazon.com/awssupport/latest/user/getting-started.html)
- [Creating Support Cases](https://docs.aws.amazon.com/awssupport/latest/user/case-management.html)
- [AWS Support Center Console](https://docs.aws.amazon.com/awssupport/latest/user/accessing-support.html)
- [AWS Support API](https://docs.aws.amazon.com/awssupport/latest/user/about-support-api.html)

### Skills & Corresponding Documentation

#### Locating AWS whitepapers, blogs, and documentation on official AWS websites

**Why:** This skill is tested through questions that ask where to find specific types of AWS information. You need to know that whitepapers provide in-depth technical guidance, blogs offer implementation examples and new feature announcements, and documentation contains service-specific technical details. Exam questions may describe an information need (learning best practices, finding implementation guides, staying current with announcements) and ask you to identify the appropriate AWS resource.

**AWS Documentation:**
- [AWS Whitepapers](https://aws.amazon.com/whitepapers/)
- [AWS Architecture Center](https://aws.amazon.com/architecture/)
- [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/)
- [AWS Blogs - All Categories](https://aws.amazon.com/blogs/)
- [AWS News Blog](https://aws.amazon.com/blogs/aws/)
- [AWS Architecture Blog](https://aws.amazon.com/blogs/architecture/)
- [AWS Documentation Home](https://docs.aws.amazon.com/)
- [AWS Getting Started Resources](https://aws.amazon.com/getting-started/)

#### Identifying and locating AWS technical resources (for example AWS Prescriptive Guidance, AWS Knowledge Center, AWS re:Post)

**Why:** Exam questions test your knowledge of specialized AWS technical resources beyond standard documentation. You must understand that AWS Prescriptive Guidance provides step-by-step implementation strategies, Knowledge Center answers common questions, and re:Post is a community-driven Q&A platform. Questions often present troubleshooting scenarios or implementation challenges and ask you to identify the most appropriate resource for finding solutions, making this knowledge essential for real-world AWS problem-solving.

**AWS Documentation:**
- [AWS Prescriptive Guidance](https://aws.amazon.com/prescriptive-guidance/)
- [AWS Prescriptive Guidance Patterns](https://docs.aws.amazon.com/prescriptive-guidance/latest/patterns/welcome.html)
- [AWS Knowledge Center](https://aws.amazon.com/premiumsupport/knowledge-center/)
- [AWS re:Post](https://repost.aws/)
- [AWS re:Post - Getting Started](https://repost.aws/knowledge-center)
- [AWS Training and Certification](https://aws.amazon.com/training/)
- [AWS Skill Builder](https://skillbuilder.aws/)

#### Identifying AWS Support options for AWS customers (for example, customer service and communities, AWS Developer Support, AWS Business Support, AWS Enterprise On-Ramp Support, AWS Enterprise Support)

**Why:** This skill requires you to match specific customer scenarios with the appropriate AWS Support plan. Exam questions describe company characteristics (startup vs enterprise, development vs production workloads, internal vs external expertise) and ask you to recommend the right support level. You must know response time SLAs, which plans include Technical Account Managers, architectural guidance availability, and pricing models to answer these scenario-based questions correctly.

**AWS Documentation:**
- [AWS Support Plan Comparison](https://aws.amazon.com/premiumsupport/plans/)
- [AWS Developer Support Plan](https://aws.amazon.com/premiumsupport/plans/developers/)
- [AWS Business Support Plan](https://aws.amazon.com/premiumsupport/plans/business/)
- [AWS Enterprise On-Ramp Support Plan](https://aws.amazon.com/premiumsupport/plans/enterprise-onramp/)
- [AWS Enterprise Support Plan](https://aws.amazon.com/premiumsupport/plans/enterprise/)
- [AWS Support Response Times](https://aws.amazon.com/premiumsupport/plans/)
- [AWS Technical Account Manager (TAM)](https://aws.amazon.com/premiumsupport/technology-and-programs/tam/)
- [AWS Infrastructure Event Management](https://aws.amazon.com/premiumsupport/programs/iem/)

#### Identifying the role of AWS Trusted Advisor, AWS Health Dashboard, and the AWS Health API to help manage and monitor environments for cost optimization

**Why:** These three services are frequently tested together because they provide different types of monitoring and recommendations. You need to understand that Trusted Advisor provides best practice checks across five categories (cost optimization, security, performance, fault tolerance, service limits), Health Dashboard shows service health events affecting your resources, and Health API enables programmatic access to health information. Exam questions present monitoring scenarios and expect you to identify which tool provides the needed visibility.

**AWS Documentation:**
- [AWS Trusted Advisor](https://aws.amazon.com/premiumsupport/technology/trusted-advisor/)
- [Getting Started with AWS Trusted Advisor](https://docs.aws.amazon.com/awssupport/latest/user/trusted-advisor.html)
- [AWS Trusted Advisor Check Categories](https://docs.aws.amazon.com/awssupport/latest/user/trusted-advisor-check-reference.html)
- [AWS Trusted Advisor Best Practices](https://aws.amazon.com/premiumsupport/technology/trusted-advisor/best-practices/)
- [AWS Health Dashboard](https://aws.amazon.com/premiumsupport/technology/aws-health-dashboard/)
- [AWS Personal Health Dashboard](https://docs.aws.amazon.com/health/latest/ug/what-is-aws-health.html)
- [AWS Health API](https://docs.aws.amazon.com/health/latest/ug/health-api.html)
- [Getting Started with AWS Health](https://docs.aws.amazon.com/health/latest/ug/getting-started-health-dashboard.html)

#### Identifying the role of the AWS Trust and Safety team to report abuse of AWS resources

**Why:** Exam questions test your knowledge of when and how to report AWS resource abuse. You must know that the Trust and Safety team handles reports of spam, malware, port scanning, DDoS attacks, and other abusive behavior originating from AWS resources. This knowledge is important for security-related scenarios where you need to identify the proper escalation path for security incidents or abuse reports, both for protecting your own resources and reporting malicious activity.

**AWS Documentation:**
- [Report Amazon AWS Abuse](https://aws.amazon.com/premiumsupport/knowledge-center/report-aws-abuse/)
- [AWS Acceptable Use Policy](https://aws.amazon.com/aup/)
- [How to Report Abuse of AWS Resources](https://support.aws.amazon.com/#/contacts/report-abuse)
- [AWS Security](https://aws.amazon.com/security/)

#### Understanding the role of AWS Partners (for example AWS Marketplace, independent software vendors, system integrators)

**Why:** This skill tests your understanding of how different types of AWS Partners contribute to the AWS ecosystem. You need to know that AWS Marketplace provides third-party software, ISVs develop AWS-integrated applications, and system integrators help design and implement AWS solutions. Exam questions often present scenarios where customers need specialized software, implementation help, or managed services, and you must identify when to leverage partners versus AWS-provided services.

**AWS Documentation:**
- [AWS Marketplace](https://aws.amazon.com/marketplace)
- [AWS Marketplace - Buyer Guide](https://docs.aws.amazon.com/marketplace/latest/buyerguide/what-is-marketplace.html)
- [AWS Partner Network Types](https://aws.amazon.com/partners/programs/)
- [AWS Consulting Partners](https://aws.amazon.com/partners/consulting/)
- [AWS Technology Partners](https://aws.amazon.com/partners/technology/)
- [AWS ISV Partners](https://aws.amazon.com/partners/programs/isv/)
- [AWS System Integrators](https://aws.amazon.com/partners/programs/global-system-integrators/)

#### Identifying the benefits of being an AWS Partner (for example, partner training and certification, partner events, partner volume discounts)

**Why:** Exam questions may test your knowledge of AWS Partner benefits to understand the partner ecosystem and how it supports customers. You should know that partners receive specialized training, access to partner-exclusive events, technical support from AWS, and potential volume discounts. This knowledge helps answer questions about why customers might choose certified AWS Partners and what value partners bring beyond standard AWS services.

**AWS Documentation:**
- [AWS Partner Network Benefits](https://aws.amazon.com/partners/benefits/)
- [AWS Partner Training and Certification](https://aws.amazon.com/partners/training/)
- [AWS Partner Events](https://aws.amazon.com/partners/events/)
- [AWS Partner Funding Programs](https://aws.amazon.com/partners/funding/)
- [AWS Competency Program](https://aws.amazon.com/partners/competencies/)
- [AWS Service Delivery Program](https://aws.amazon.com/partners/service-delivery/)

#### Identifying the key services that AWS Marketplace offers (for example, cost management, governance and entitlement)

**Why:** This skill tests your understanding of AWS Marketplace capabilities beyond just software procurement. You need to know that Marketplace provides cost management tools for tracking software spending, governance features for managing licenses and subscriptions, and entitlement management for controlling software access. Exam questions present scenarios involving third-party software procurement and management, expecting you to identify how Marketplace features address these needs.

**AWS Documentation:**
- [AWS Marketplace - What is AWS Marketplace](https://docs.aws.amazon.com/marketplace/latest/buyerguide/what-is-marketplace.html)
- [AWS Marketplace Cost Management](https://docs.aws.amazon.com/marketplace/latest/buyerguide/buyer-paying-for-products.html)
- [AWS Marketplace Governance](https://docs.aws.amazon.com/marketplace/latest/buyerguide/buyer-private-marketplace.html)
- [AWS Marketplace Private Marketplace](https://aws.amazon.com/marketplace/features/private-marketplace)
- [AWS Marketplace Entitlement Service](https://docs.aws.amazon.com/marketplace/latest/userguide/entitlement-service.html)
- [Managing Subscriptions in AWS Marketplace](https://docs.aws.amazon.com/marketplace/latest/buyerguide/buyer-subscribing-to-products.html)

#### Identifying technical assistance options available at AWS (for example, AWS Professional Services, AWS Solutions Architects)

**Why:** Exam questions test your knowledge of AWS technical assistance resources available to help customers design and implement solutions. You must understand that AWS Professional Services provides hands-on consulting for complex implementations, AWS Solutions Architects offer architectural guidance through Support plans, and AWS Training and Certification helps build internal expertise. Questions present implementation challenges and expect you to identify the appropriate technical assistance option.

**AWS Documentation:**
- [AWS Professional Services](https://aws.amazon.com/professional-services/)
- [AWS Professional Services - Cloud Advisory](https://aws.amazon.com/professional-services/programs/)
- [AWS Solutions Architects](https://aws.amazon.com/architecture/well-architected/)
- [AWS IQ - Find AWS Certified Experts](https://aws.amazon.com/iq/)
- [AWS Managed Services (AMS)](https://aws.amazon.com/managed-services/)
- [AWS Support - Architectural Guidance](https://aws.amazon.com/premiumsupport/features/)
- [AWS Training and Certification](https://aws.amazon.com/training/)

**AWS Service FAQs:**

- [AWS Support FAQ](https://aws.amazon.com/premiumsupport/faqs/)
- [AWS Trusted Advisor FAQ](https://aws.amazon.com/premiumsupport/technology/trusted-advisor/faqs/)
- [AWS Marketplace FAQ](https://aws.amazon.com/marketplace/help/)
- [AWS Partner Network FAQ](https://aws.amazon.com/partners/faqs/)
- [AWS Professional Services FAQ](https://aws.amazon.com/professional-services/faqs/)
- [AWS Health FAQ](https://aws.amazon.com/premiumsupport/technology/aws-health-dashboard/faqs/)

**AWS Whitepapers:**

- [AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html)
- [AWS Support - A Detailed Overview](https://docs.aws.amazon.com/whitepapers/latest/aws-support-overview/aws-support-overview.html)
- [Overview of Amazon Web Services](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/introduction.html)
- [Operational Excellence Pillar - AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/operational-excellence-pillar/welcome.html)

---

## Final Thoughts

Domain 4: Billing, Pricing, and Support represents 12% of your exam and is highly practical—these are concepts you'll use immediately when working with AWS. Focus on understanding the "why" behind different pricing models and support options rather than just memorizing features. Use the AWS Pricing Calculator and explore the AWS Billing Console even with a free tier account to gain hands-on familiarity. The knowledge you build here will not only help you pass the exam but also enable you to make cost-effective decisions and access the right support resources throughout your AWS career.
