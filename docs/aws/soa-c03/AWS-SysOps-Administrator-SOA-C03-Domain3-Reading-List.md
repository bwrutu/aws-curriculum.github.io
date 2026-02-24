# AWS Certified SysOps Administrator - Associate (SOA-C03) Domain 3
## Deployment, Provisioning, and Automation

**Official Exam Guide:** <a href="https://docs.aws.amazon.com/aws-certification/latest/examguides/sysops-administrator-associate-03-domain3.html" target="_blank">Domain 3: Deployment, Provisioning, and Automation</a>  
**Skill Builder:** <a href="https://skillbuilder.aws/category/exam-prep/cloudops-engineer-associate-SOA-C03" target="_blank">AWS Certified SysOps Administrator - Associate (SOA-C03) Exam Prep</a>

Note: Some Skill Builder labs require a subscription.

---

## How to Study This Domain Effectively

### Study Tips

1. **Master Infrastructure as Code (IaC) fundamentals** - Understand the declarative nature of CloudFormation and how it differs from imperative scripting. The exam tests your ability to read CloudFormation templates (both JSON and YAML), identify template components (Parameters, Resources, Outputs, Mappings), and troubleshoot common deployment errors (circular dependencies, missing permissions, resource limits). Practice creating templates for common architectures (VPC with subnets, Auto Scaling groups, RDS with replicas) to understand how resources reference each other and how CloudFormation manages dependencies.

2. **Practice troubleshooting deployment failures** - Most exam questions focus on identifying why deployments fail rather than writing perfect templates. Common issues include Insufficient Address Capacity (CIDR too small), permission errors (missing Identity and Access Management (IAM) roles), resource dependencies (wrong DependsOn), and stack rollback scenarios. Create intentionally broken templates and practice diagnosing the errors from CloudFormation events and error messages. Understanding rollback behavior and how to prevent data loss during updates is critical.

3. **Understand cross-account and cross-region architectures** - Learn Resource Access Manager (RAM) for sharing resources (subnets, Transit Gateway attachments, License Manager), CloudFormation StackSets for deploying to multiple accounts/regions simultaneously, and how to design Organizations-based architectures. The exam tests scenarios requiring centralized resource management, spoke account deployments, and compliance enforcement across an organization. Practice setting up StackSets with automatic deployments to new accounts as they join the organization.

4. **Learn multiple deployment strategies** - Understand blue/green deployments (separate environments, instant switchover), canary deployments (gradual traffic shift), rolling deployments (update instances in batches), and immutable deployments (new instances replace old). Know which services support which strategies (Elastic Beanstalk supports all, ECS/EKS support multiple, EC2 requires custom implementation). The exam tests your ability to select the right strategy based on requirements (zero downtime, rollback speed, validation requirements).

5. **Hands-on with Systems Manager for automation** - Practice creating and running Systems Manager documents (Command, Automation, Session), configuring Maintenance Windows for scheduled tasks, implementing patch baselines and patch groups, and using State Manager for configuration compliance. Understand how to use Run Command for ad-hoc tasks versus Automation for multi-step workflows. The exam extensively tests Systems Manager capabilities for operational automation, so practical experience is essential for understanding execution flow and troubleshooting failures.

### Recommended Approach

1. **Start with CloudFormation fundamentals** - Read the CloudFormation User Guide thoroughly, focusing on template anatomy, intrinsic functions (Ref, GetAtt, Sub, Join), pseudo parameters (AWS::Region, AWS::StackName), and resource dependencies. Create simple templates and gradually increase complexity. Learn how to use CloudFormation Designer for visualization and validation. Understanding template structure is essential before moving to advanced topics like nested stacks, change sets, and drift detection.

2. **Deep dive into EC2 Image Builder and Amazon Machine Image (AMI) management** - Study the complete AMI lifecycle: creating custom AMIs (manually or with Image Builder), managing AMI versions, sharing AMIs across accounts, copying AMIs across regions, and deregistering unused AMIs. Practice using Image Builder to create automated pipelines with components, recipes, and distribution settings. Understand the difference between AMI copying (creates independent copy) and AMI sharing (grants permission to use original). This knowledge is critical for standardized deployments and security compliance.

3. **Master Systems Manager comprehensively** - Study all Systems Manager capabilities systematically: Run Command for remote execution, Automation for runbooks, Session Manager for secure access, Patch Manager for patching, State Manager for configuration management, and Parameter Store for secrets. Understand how these capabilities work together (Automation can call Run Command, State Manager uses documents). Practice creating custom automation runbooks with error handling, approvals, and conditional logic. Systems Manager is central to operational automation and appears throughout the exam.

4. **Learn event-driven automation with Lambda and EventBridge** - Understand how to trigger Lambda functions from various event sources (S3 notifications, DynamoDB Streams, CloudWatch Events/EventBridge, Application Load Balancer (ALB)). Practice writing Lambda functions that automate operational tasks (snapshot creation, instance tagging, security group updates). Study EventBridge event patterns for filtering events and routing to multiple targets. The exam tests your ability to design automated responses to operational events without manual intervention.

5. **Practice with third-party Infrastructure as Code (IaC) tools** - While CloudFormation is AWS-native, understand Terraform basics (providers, resources, state management), Git workflows for IaC (branching, pull requests, code review), and integration patterns (Terraform with AWS, Git with CodePipeline). The exam tests your knowledge of when to use third-party tools (multi-cloud, existing ecosystem) versus AWS-native tools (deeper AWS integration, no state management). Understand the tradeoffs and integration options for hybrid IaC environments.

---

## Task 3.1: Provision and maintain cloud resources

### Skills & Corresponding Documentation

#### Skill 3.1.1: Create and manage AMIs and container images (for example, Amazon EC2 Image Builder)

**Why:** AMI management is fundamental to standardized deployments and is tested through scenarios involving image creation, distribution, and lifecycle management. You must understand how to create custom AMIs from existing instances, use EC2 Image Builder for automated image pipelines with testing and validation, manage AMI versions and deprecation, share AMIs across accounts and regions, and implement security hardening in golden images. The exam tests your knowledge of when to use Image Builder automation versus manual AMI creation, how to distribute images across multiple regions for disaster recovery, and how to maintain AMI inventories efficiently. Understanding AMI management is critical for enforcing security baselines, ensuring consistent deployments, and reducing deployment time through pre-configured images.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html" target="_blank">Amazon Machine Images (AMI)</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/creating-an-ami-ebs.html" target="_blank">Creating an Amazon EBS-Backed Linux AMI</a>
- <a href="https://docs.aws.amazon.com/imagebuilder/latest/userguide/" target="_blank">EC2 Image Builder User Guide</a>
- <a href="https://docs.aws.amazon.com/imagebuilder/latest/userguide/what-is-image-builder.html" target="_blank">What Is EC2 Image Builder?</a>
- <a href="https://docs.aws.amazon.com/imagebuilder/latest/userguide/how-image-builder-works.html" target="_blank">How EC2 Image Builder Works</a>
- <a href="https://docs.aws.amazon.com/imagebuilder/latest/userguide/pipelines.html" target="_blank">Creating Image Pipelines</a>
- <a href="https://docs.aws.amazon.com/imagebuilder/latest/userguide/manage-components.html" target="_blank">Managing Components</a>
- <a href="https://docs.aws.amazon.com/imagebuilder/latest/userguide/manage-recipes.html" target="_blank">Image Recipes</a>
- <a href="https://docs.aws.amazon.com/imagebuilder/latest/userguide/distribute-settings.html" target="_blank">Distributing Images</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/CopyingAMIs.html" target="_blank">Copying an AMI</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/sharingamis-explicit.html" target="_blank">Sharing an AMI with Specific AWS Accounts</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/sharingamis-intro.html" target="_blank">Making an AMI Public</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/deregister-ami.html" target="_blank">Deregistering Your Linux AMI</a>
- <a href="https://docs.aws.amazon.com/AmazonECR/latest/userguide/" target="_blank">Amazon Elastic Container Registry User Guide</a>
- <a href="https://docs.aws.amazon.com/AmazonECR/latest/userguide/docker-push-ecr-image.html" target="_blank">Pushing a Docker Image to Amazon ECR</a>
- <a href="https://docs.aws.amazon.com/AmazonECR/latest/userguide/LifecyclePolicies.html" target="_blank">Lifecycle Policies for ECR</a>

#### Skill 3.1.2: Create and manage stacks of resources by using AWS CloudFormation and the AWS Cloud Development Kit (AWS CDK)

**Why:** CloudFormation is AWS's primary Infrastructure as Code service and is extensively tested throughout the SysOps exam. You must understand template structure (Resources, Parameters, Outputs, Mappings, Conditions), intrinsic functions (Ref, GetAtt, Sub, Join, Select), how to create and update stacks, use change sets to preview changes before execution, implement nested stacks for modularity, and understand stack policies to prevent accidental updates. The exam tests troubleshooting scenarios (dependency errors, rollback failures, drift detection), cross-stack references, and how to use CloudFormation StackSets for multi-account deployments. Understanding CloudFormation is critical for repeatable infrastructure deployments, disaster recovery, and compliance as code. AWS CDK knowledge (higher-level constructs, synthesis to CloudFormation) is also tested for modern IaC approaches.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/" target="_blank">AWS CloudFormation User Guide</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html" target="_blank">What Is AWS CloudFormation?</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cloudformation-overview.html" target="_blank">How Does AWS CloudFormation Work?</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/template-anatomy.html" target="_blank">Template Anatomy</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference.html" target="_blank">Intrinsic Function Reference</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/pseudo-parameter-reference.html" target="_blank">Pseudo Parameters Reference</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacks.html" target="_blank">Working with Stacks</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-changesets.html" target="_blank">Updating Stacks Using Change Sets</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-nested-stacks.html" target="_blank">Working with Nested Stacks</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/protect-stack-resources.html" target="_blank">Prevent Updates to Stack Resources</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-continueupdaterollback.html" target="_blank">Continue Rolling Back an Update</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-stack-drift.html" target="_blank">Detecting Unmanaged Configuration Changes to Stacks and Resources</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/what-is-cfnstacksets.html" target="_blank">Working with AWS CloudFormation StackSets</a>
- <a href="https://docs.aws.amazon.com/cdk/v2/guide/home.html" target="_blank">AWS Cloud Development Kit (CDK) Developer Guide</a>
- <a href="https://docs.aws.amazon.com/cdk/v2/guide/getting_started.html" target="_blank">Getting Started with AWS CDK</a>
- <a href="https://docs.aws.amazon.com/cdk/v2/guide/core_concepts.html" target="_blank">AWS CDK Concepts</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/troubleshooting.html" target="_blank">Troubleshooting Common AWS CloudFormation Issues</a>

#### Skill 3.1.3: Identify and remediate deployment issues (for example, subnet sizing issues, CloudFormation errors, permissions issues)

**Why:** Deployment troubleshooting is heavily tested because real-world deployments frequently fail, and SysOps administrators must diagnose and resolve issues quickly. Common issues include subnet sizing errors (InsufficientFreeAddressesInSubnet when CIDR block is too small), IAM permission errors (missing iam:PassRole, insufficient service permissions), resource dependency problems (circular dependencies, missing DependsOn), resource limit exceeded (VPC limit, Elastic IP limit), and invalid parameter combinations. The exam presents scenarios with error messages and stack events, requiring you to identify the root cause and recommend fixes. Understanding how to read CloudFormation stack events, rollback behavior, and how to use CloudFormation console logs for troubleshooting is essential for maintaining infrastructure deployments.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/troubleshooting.html" target="_blank">Troubleshooting AWS CloudFormation</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/troubleshooting-errors.html" target="_blank">Troubleshooting Errors</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/troubleshooting-launch.html#troubleshooting-launch-capacity" target="_blank">InsufficientAddressCapacity Errors</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-iam-template.html" target="_blank">IAM Permissions for CloudFormation</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-iam-servicerole.html" target="_blank">AWS CloudFormation Service Role</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-console-view-stack-data-resources.html" target="_blank">Viewing AWS CloudFormation Stack Data and Resources</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/troubleshooting.html#troubleshooting-stack-creation" target="_blank">Troubleshooting Stack Creation Failures</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/troubleshooting.html#troubleshooting-stack-update" target="_blank">Troubleshooting Stack Update Failures</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/configure-your-vpc.html" target="_blank">VPC and Subnet Sizing</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/amazon-vpc-limits.html" target="_blank">VPC Quotas</a>
- <a href="https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html" target="_blank">Service Quotas</a>
- <a href="https://docs.aws.amazon.com/servicequotas/latest/userguide/request-quota-increase.html" target="_blank">Requesting a Quota Increase</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cloudformation-limits.html" target="_blank">CloudFormation Quotas</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-attribute-dependson.html" target="_blank">DependsOn Attribute</a>

#### Skill 3.1.4: Provision and share resources across multiple AWS Regions and accounts (for example, AWS Resource Access Manager [AWS RAM], CloudFormation StackSets)

**Why:** Multi-account and multi-region architectures are increasingly common and are tested through scenarios requiring centralized resource management and consistent deployments across an organization. AWS RAM enables sharing resources (VPC subnets, Transit Gateway, Route 53 Resolver rules, License Manager) between accounts without duplicating resources, while StackSets enable deploying identical CloudFormation stacks across multiple accounts and regions simultaneously. The exam tests your understanding of when to use RAM sharing versus replication, how to configure StackSets with organizational units for automatic deployment to new accounts, and how to manage updates across distributed stacks. Understanding cross-account and cross-region patterns is essential for enterprise AWS architectures that require governance, cost optimization, and consistent security controls.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/ram/latest/userguide/" target="_blank">AWS Resource Access Manager User Guide</a>
- <a href="https://docs.aws.amazon.com/ram/latest/userguide/what-is.html" target="_blank">What Is AWS Resource Access Manager?</a>
- <a href="https://docs.aws.amazon.com/ram/latest/userguide/shareable.html" target="_blank">Shareable AWS Resources</a>
- <a href="https://docs.aws.amazon.com/ram/latest/userguide/working-with-sharing.html" target="_blank">Sharing Your AWS Resources</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/vpc-sharing.html" target="_blank">Sharing VPC Subnets</a>
- <a href="https://docs.aws.amazon.com/ram/latest/userguide/working-with-shared.html" target="_blank">Working with Shared AWS Resources</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/what-is-cfnstacksets.html" target="_blank">AWS CloudFormation StackSets User Guide</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacksets-concepts.html" target="_blank">StackSets Concepts</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacksets-getting-started-create.html" target="_blank">Creating a Stack Set</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stackinstances-create.html" target="_blank">Managing Stack Instances</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacksets-orgs-enable-trusted-access.html" target="_blank">Enabling Trusted Access with AWS Organizations</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacksets-orgs-manage-auto-deployment.html" target="_blank">Automatic Deployments with StackSets</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacksets-concepts.html#stacksets-concepts-ops" target="_blank">Cross-Region and Cross-Account Deployments</a>
- <a href="https://docs.aws.amazon.com/organizations/latest/userguide/" target="_blank">AWS Organizations User Guide</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/organizing-your-aws-environment/organizing-your-aws-environment.html" target="_blank">Multi-Account Strategy</a>

#### Skill 3.1.5: Implement deployment strategies and services

**Why:** Deployment strategies determine how application updates are rolled out and are tested through scenarios requiring zero-downtime deployments, rollback capabilities, and risk mitigation. You must understand blue/green deployments (two complete environments with traffic switch), canary deployments (gradual traffic increase to new version), rolling deployments (batch updates), and immutable deployments (new instances replace old). Know which services support which strategies: Elastic Beanstalk supports all strategies, ECS/EKS support multiple, CodeDeploy enables blue/green and canary for EC2/Lambda/ECS. The exam tests your ability to select the appropriate strategy based on requirements (downtime tolerance, validation time, rollback speed, cost) and understand the tradeoffs. Real-world deployments require balancing risk with deployment speed and cost.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/" target="_blank">AWS Elastic Beanstalk Developer Guide</a>
- <a href="https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features.deploy-existing-version.html" target="_blank">Deployment Policies and Settings</a>
- <a href="https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features.CNAMESwap.html" target="_blank">Blue/Green Deployments with Elastic Beanstalk</a>
- <a href="https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features.rolling-version-deploy.html" target="_blank">Rolling Updates</a>
- <a href="https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/environmentmgmt-updates-immutable.html" target="_blank">Immutable Updates</a>
- <a href="https://docs.aws.amazon.com/codedeploy/latest/userguide/" target="_blank">AWS CodeDeploy User Guide</a>
- <a href="https://docs.aws.amazon.com/codedeploy/latest/userguide/welcome.html" target="_blank">What Is AWS CodeDeploy?</a>
- <a href="https://docs.aws.amazon.com/codedeploy/latest/userguide/deployment-steps.html" target="_blank">CodeDeploy Deployment Types</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/blue-green-deployments/welcome.html" target="_blank">Blue/Green Deployments on AWS</a>
- <a href="https://docs.aws.amazon.com/codedeploy/latest/userguide/deployment-configurations.html#deployment-configuration-canary" target="_blank">Canary Deployments</a>
- <a href="https://docs.aws.amazon.com/AmazonECS/latest/developerguide/deployment-types.html" target="_blank">Amazon ECS Deployment Types</a>
- <a href="https://docs.aws.amazon.com/AmazonECS/latest/developerguide/deployment-type-bluegreen.html" target="_blank">Amazon ECS Blue/Green Deployment</a>
- <a href="https://docs.aws.amazon.com/apprunner/latest/dg/manage-deploy.html" target="_blank">AWS App Runner Deployment</a>
- <a href="https://docs.aws.amazon.com/lambda/latest/dg/lambda-deploy-functions.html" target="_blank">Lambda Deployment Options</a>
- <a href="https://aws.amazon.com/blogs/compute/implementing-safe-aws-lambda-deployments-with-aws-codedeploy/" target="_blank">Implementing Safe AWS Lambda Deployments with Canary</a>

#### Skill 3.1.6: Use and manage third-party tools to automate resource deployment (for example, Terraform, Git)

**Why:** While CloudFormation is AWS-native, many organizations use third-party IaC tools like Terraform for multi-cloud deployments or existing toolchain integration. The exam tests your understanding of Terraform basics (providers, resources, state files, modules), when to use Terraform versus CloudFormation (multi-cloud, provider ecosystem, state management), and integration patterns. For Git, understand version control workflows for infrastructure code (branching strategies, pull requests, code review), integration with AWS CodeCommit and CodePipeline for continuous deployment, and how to structure IaC repositories. Understanding third-party tools is important for hybrid environments and demonstrates broader IaC knowledge beyond AWS-native services.

**AWS Documentation:**
- <a href="https://aws.amazon.com/getting-started/hands-on/deploy-terraform/" target="_blank">Terraform on AWS</a>
- <a href="https://registry.terraform.io/providers/hashicorp/aws/latest/docs" target="_blank">AWS Provider for Terraform Documentation</a>
- <a href="https://docs.aws.amazon.com/codecommit/latest/userguide/" target="_blank">AWS CodeCommit User Guide</a>
- <a href="https://docs.aws.amazon.com/codecommit/latest/userguide/welcome.html" target="_blank">What Is AWS CodeCommit?</a>
- <a href="https://docs.aws.amazon.com/codecommit/latest/userguide/getting-started.html" target="_blank">Getting Started with AWS CodeCommit</a>
- <a href="https://docs.aws.amazon.com/codecommit/latest/userguide/repositories.html" target="_blank">Working with Repositories</a>
- <a href="https://docs.aws.amazon.com/codecommit/latest/userguide/how-to-basic-git.html" target="_blank">Using AWS CodeCommit with Git</a>
- <a href="https://docs.aws.amazon.com/codepipeline/latest/userguide/" target="_blank">AWS CodePipeline User Guide</a>
- <a href="https://docs.aws.amazon.com/codepipeline/latest/userguide/reference-pipeline-structure.html" target="_blank">Pipeline Structure Reference</a>
- <a href="https://docs.aws.amazon.com/codepipeline/latest/userguide/pipelines-create.html" target="_blank">Create a Pipeline with AWS CodePipeline</a>
- <a href="https://docs.aws.amazon.com/codepipeline/latest/userguide/integrations.html" target="_blank">Integrating AWS CodePipeline with Third-Party Services</a>
- <a href="https://docs.aws.amazon.com/codebuild/latest/userguide/" target="_blank">AWS CodeBuild User Guide</a>
- <a href="https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html" target="_blank">Build Specification Reference for CodeBuild</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/operational-excellence-pillar/ops_dev_integ_version_control.html" target="_blank">Version Control Best Practices</a>

---

## Task 3.2: Automate the management of existing resources

### Skills & Corresponding Documentation

#### Skill 3.2.1: Use AWS services to automate operational processes (for example, AWS Systems Manager)

**Why:** Systems Manager is the primary service for operational automation in AWS and is one of the most heavily tested topics in the SysOps exam. You must understand all major Systems Manager capabilities: Run Command for remote command execution, Automation for multi-step workflows, Session Manager for secure instance access without SSH, Patch Manager for operating system and application patching, State Manager for configuration compliance, Parameter Store for configuration data and secrets storage, and Maintenance Windows for scheduled operations. The exam tests scenarios requiring you to select the appropriate Systems Manager capability for specific operational tasks, troubleshoot execution failures, and implement automated responses to common operational issues. Understanding Systems Manager comprehensively is essential for modern cloud operations and reduces manual operational overhead significantly.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/" target="_blank">AWS Systems Manager User Guide</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/what-is-systems-manager.html" target="_blank">What Is AWS Systems Manager?</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/features.html" target="_blank">AWS Systems Manager Capabilities</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/execute-remote-commands.html" target="_blank">AWS Systems Manager Run Command</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/run-command.html" target="_blank">Running Commands Using Systems Manager Run Command</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-automation.html" target="_blank">AWS Systems Manager Automation</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/automation-documents.html" target="_blank">Working with Automation Runbooks</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/automation-actions.html" target="_blank">Systems Manager Automation Actions Reference</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager.html" target="_blank">AWS Systems Manager Session Manager</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager-getting-started.html" target="_blank">Setting Up Session Manager</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/patch-manager.html" target="_blank">AWS Systems Manager Patch Manager</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/patch-manager-patch-baselines.html" target="_blank">Working with Patch Baselines</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/patch-manager-patching-operations.html" target="_blank">Patching Operations</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-state.html" target="_blank">AWS Systems Manager State Manager</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-parameter-store.html" target="_blank">AWS Systems Manager Parameter Store</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-maintenance.html" target="_blank">AWS Systems Manager Maintenance Windows</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/sysman-maintenance-working.html" target="_blank">Configuring Maintenance Windows</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/troubleshooting-systems-manager.html" target="_blank">Troubleshooting Systems Manager</a>

#### Skill 3.2.2: Implement event-driven automation by using AWS services and features (for example, AWS Lambda, Amazon S3 Event Notifications)

**Why:** Event-driven automation is a modern operational pattern that eliminates manual intervention and is increasingly tested in the SysOps exam. You must understand how to trigger automation from various event sources: S3 event notifications (object created, deleted), EventBridge rules (AWS API calls, scheduled events, custom events), CloudWatch alarms (metric thresholds), DynamoDB Streams (table changes), and Amazon Simple Notification Service (SNS) topics. For Lambda, understand execution models, environment variables, permissions (execution role), timeout and memory configuration, and error handling. The exam tests scenarios requiring automated responses to operational events (auto-remediation of non-compliant resources, automated backup creation, security incident response). Understanding event-driven patterns enables building self-healing infrastructure that responds automatically to changing conditions.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/lambda/latest/dg/" target="_blank">AWS Lambda Developer Guide</a>
- <a href="https://docs.aws.amazon.com/lambda/latest/dg/welcome.html" target="_blank">What Is AWS Lambda?</a>
- <a href="https://docs.aws.amazon.com/lambda/latest/dg/invocation-eventsourcemapping.html" target="_blank">Lambda Event Source Mappings</a>
- <a href="https://docs.aws.amazon.com/lambda/latest/dg/with-s3.html" target="_blank">Using AWS Lambda with Amazon S3</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/NotificationHowTo.html" target="_blank">Amazon S3 Event Notifications</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/enable-event-notifications.html" target="_blank">Configuring Amazon S3 Event Notifications</a>
- <a href="https://docs.aws.amazon.com/lambda/latest/dg/services-cloudwatchevents.html" target="_blank">Using AWS Lambda with Amazon EventBridge</a>
- <a href="https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-rules.html" target="_blank">Amazon EventBridge Rules</a>
- <a href="https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-create-rule.html" target="_blank">Creating Amazon EventBridge Rules That React to Events</a>
- <a href="https://docs.aws.amazon.com/lambda/latest/dg/with-ddb.html" target="_blank">Using AWS Lambda with Amazon DynamoDB</a>
- <a href="https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Streams.Lambda.html" target="_blank">DynamoDB Streams and AWS Lambda</a>
- <a href="https://docs.aws.amazon.com/lambda/latest/dg/with-sns.html" target="_blank">Using AWS Lambda with Amazon SNS</a>
- <a href="https://docs.aws.amazon.com/lambda/latest/dg/with-sqs.html" target="_blank">Using AWS Lambda with Amazon SQS</a>
- <a href="https://docs.aws.amazon.com/lambda/latest/dg/configuration-function-common.html" target="_blank">Lambda Function Configuration</a>
- <a href="https://docs.aws.amazon.com/lambda/latest/dg/lambda-intro-execution-role.html" target="_blank">Lambda Execution Role</a>
- <a href="https://docs.aws.amazon.com/lambda/latest/dg/invocation-retries.html" target="_blank">Lambda Error Handling and Automatic Retries</a>
- <a href="https://docs.aws.amazon.com/lambda/latest/dg/best-practices.html" target="_blank">Best Practices for Working with AWS Lambda Functions</a>
- <a href="https://docs.aws.amazon.com/lambda/latest/dg/lambda-services.html" target="_blank">Event-Driven Architecture</a>

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/ec2/faqs/" target="_blank">Amazon EC2 FAQs</a>
- <a href="https://aws.amazon.com/ec2/faqs/#Amazon_Machine_Images" target="_blank">Amazon Machine Images (AMI) FAQs</a>
- <a href="https://aws.amazon.com/image-builder/faqs/" target="_blank">EC2 Image Builder FAQs</a>
- <a href="https://aws.amazon.com/ecr/faqs/" target="_blank">Amazon ECR FAQs</a>
- <a href="https://aws.amazon.com/cloudformation/faqs/" target="_blank">AWS CloudFormation FAQs</a>
- <a href="https://aws.amazon.com/cdk/faqs/" target="_blank">AWS Cloud Development Kit (CDK) FAQs</a>
- <a href="https://aws.amazon.com/ram/faqs/" target="_blank">AWS Resource Access Manager FAQs</a>
- <a href="https://aws.amazon.com/elasticbeanstalk/faqs/" target="_blank">AWS Elastic Beanstalk FAQs</a>
- <a href="https://aws.amazon.com/codedeploy/faqs/" target="_blank">AWS CodeDeploy FAQs</a>
- <a href="https://aws.amazon.com/codecommit/faqs/" target="_blank">AWS CodeCommit FAQs</a>
- <a href="https://aws.amazon.com/codepipeline/faqs/" target="_blank">AWS CodePipeline FAQs</a>
- <a href="https://aws.amazon.com/codebuild/faqs/" target="_blank">AWS CodeBuild FAQs</a>
- <a href="https://aws.amazon.com/systems-manager/faq/" target="_blank">AWS Systems Manager FAQs</a>
- <a href="https://aws.amazon.com/lambda/faqs/" target="_blank">AWS Lambda FAQs</a>
- <a href="https://aws.amazon.com/eventbridge/faqs/" target="_blank">Amazon EventBridge FAQs</a>
- <a href="https://aws.amazon.com/s3/faqs/" target="_blank">Amazon S3 FAQs</a>

---

## AWS Whitepapers

- <a href="https://docs.aws.amazon.com/wellarchitected/latest/operational-excellence-pillar/welcome.html" target="_blank">Operational Excellence Pillar - AWS Well-Architected Framework</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/introduction-devops-aws/infrastructure-as-code.html" target="_blank">Infrastructure as Code</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/blue-green-deployments/welcome.html" target="_blank">Blue/Green Deployments on AWS</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/overview-deployment-options/welcome.html" target="_blank">AWS Deployment Strategies</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/organizing-your-aws-environment/organizing-your-aws-environment.html" target="_blank">Organizing Your AWS Environment Using Multiple Accounts</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/operational-excellence-pillar/ops_dev_integ_deploy_mgmt_sys.html" target="_blank">Automating Safe, Hands-Off Deployments</a>
- <a href="https://docs.aws.amazon.com/lambda/latest/dg/lambda-services.html" target="_blank">Event-Driven Architecture</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/introduction-devops-aws/welcome.html" target="_blank">DevOps Best Practices on AWS</a>

---

## Final Thoughts

Domain 3 focuses on Infrastructure as Code, automation, and modern deployment practices that are essential for operational excellence. CloudFormation proficiency is critical - invest significant time understanding templates, troubleshooting deployments, and managing stack updates. Systems Manager is equally important with its comprehensive automation capabilities appearing throughout the exam. Practice creating AMIs with Image Builder, deploying StackSets across multiple accounts, and building event-driven automation with Lambda. The combination of IaC skills, deployment strategy knowledge, and automation expertise tested in this domain directly translates to real-world DevOps and cloud operations roles. Success requires both deep service knowledge and practical troubleshooting experience with failed deployments, so complement documentation study with extensive hands-on practice in breaking and fixing infrastructure deployments.
