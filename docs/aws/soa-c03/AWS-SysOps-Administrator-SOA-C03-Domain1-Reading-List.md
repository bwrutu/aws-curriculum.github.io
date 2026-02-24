# AWS Certified SysOps Administrator - Associate (SOA-C03) Domain 1
## Monitoring, Logging, Analysis, Remediation, and Performance Optimization

**Official Exam Guide:** <a href="https://docs.aws.amazon.com/aws-certification/latest/examguides/sysops-administrator-associate-03-domain1.html" target="_blank">Domain 1: Monitoring, Logging, Analysis, Remediation, and Performance Optimization</a>  
**Skill Builder:** <a href="https://skillbuilder.aws/category/exam-prep/cloudops-engineer-associate-SOA-C03" target="_blank">AWS Certified SysOps Administrator - Associate (SOA-C03) Exam Prep</a>

Note: Some Skill Builder labs require a subscription.

---

## How to Study This Domain Effectively

### Study Tips

1. **Practice hands-on monitoring setup** - Create CloudWatch dashboards, configure alarms, and set up log groups in your own AWS account. The SysOps exam heavily tests practical implementation, not just theoretical knowledge. Set up the CloudWatch agent on EC2 instances to understand how custom metrics and logs flow into CloudWatch, as this is a common exam scenario.

2. **Master CloudWatch Logs Insights query syntax** - The exam frequently presents scenarios requiring log analysis. Practice writing queries to filter, aggregate, and analyze logs. Understanding how to extract specific information from logs using Insights queries is critical for troubleshooting questions.

3. **Understand the difference between monitoring and observability** - Know when to use CloudWatch metrics versus logs versus traces (X-Ray). Exam questions often ask you to identify the right tool for specific troubleshooting scenarios. For example, CloudWatch metrics for performance trends, logs for detailed error investigation, and X-Ray for distributed application tracing.

4. **Learn Systems Manager Automation runbooks** - Familiarize yourself with both AWS-provided and custom automation runbooks. The exam tests your ability to identify which runbook solves a specific operational task (patching, backup, incident response). Understanding document types (Automation, Command, Session) and their use cases is essential.

5. **Focus on cost optimization through monitoring** - The SysOps role involves cost management. Understand how to identify underutilized resources through CloudWatch metrics, implement lifecycle policies (S3, EFS), and use tools like AWS Compute Optimizer. Exam questions frequently combine monitoring with cost optimization recommendations.

### Recommended Approach

1. **Start with CloudWatch fundamentals** - Begin by reading the CloudWatch User Guide, focusing on metrics, namespaces, dimensions, and statistics. Understand the difference between standard and custom metrics, and how metric resolution (standard versus high-resolution) affects monitoring capabilities. This foundation is essential before moving to more complex topics like composite alarms and anomaly detection.

2. **Build hands-on experience with the CloudWatch agent** - Install and configure the CloudWatch agent on EC2 instances. Practice collecting custom metrics (memory, disk) and application logs. Configure the agent using both the wizard and JSON configuration file. This hands-on practice directly prepares you for configuration and troubleshooting questions on the exam.

3. **Master CloudWatch alarms and EventBridge integration** - Study how alarms trigger actions, including Amazon Simple Notification Service (Amazon SNS) notifications, Auto Scaling policies, and EventBridge rules. Understand composite alarms (combining multiple alarms with AND/OR logic) and metric math. Practice creating event patterns in EventBridge to route alarms to different targets. The exam extensively tests alarm configuration and troubleshooting.

4. **Deep dive into Systems Manager** - Study Automation, Run Command, Session Manager, Patch Manager, and State Manager. Understand how these services work together for operational tasks. Focus on automation runbooks (AWS-provided versus custom), document types, and how to troubleshoot failed executions. Systems Manager is central to the SysOps role and heavily tested.

5. **Study performance optimization with real metrics** - Review AWS Performance Best Practices documentation for each service (EC2, Amazon Elastic Block Store (Amazon EBS), S3, Amazon Relational Database Service (Amazon RDS), Amazon Elastic File System (Amazon EFS)). Understand how to interpret performance metrics (Input/Output Operations Per Second (IOPS), throughput, latency) and identify bottlenecks. Study optimization techniques like EBS volume types, S3 Transfer Acceleration, RDS Performance Insights, and EC2 placement groups. Practice analyzing metrics to recommend performance improvements.

---

## Task 1.1: Implement metrics, alarms, and filters by using AWS monitoring and logging services

### Skills & Corresponding Documentation

#### Skill 1.1.1: Configure AWS monitoring and logging by using AWS services (for example, Amazon CloudWatch, AWS CloudTrail, Amazon Managed Service for Prometheus)

**Why:** This skill is fundamental to the SysOps role and heavily tested because monitoring and logging form the foundation of operational excellence in AWS. Exam questions test your ability to choose the right service for specific monitoring needs: CloudWatch for metrics and logs, CloudTrail for API auditing and compliance, and Managed Service for Prometheus for container-based workloads. Understanding when to use each service and how to configure them properly is critical, as real-world SysOps administrators must establish comprehensive observability for troubleshooting, security analysis, and performance optimization.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/" target="_blank">Amazon CloudWatch User Guide</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html" target="_blank">What Is Amazon CloudWatch?</a>
- <a href="https://docs.aws.amazon.com/awscloudtrail/latest/userguide/" target="_blank">AWS CloudTrail User Guide</a>
- <a href="https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html" target="_blank">What Is AWS CloudTrail?</a>
- <a href="https://docs.aws.amazon.com/prometheus/latest/userguide/" target="_blank">Amazon Managed Service for Prometheus User Guide</a>
- <a href="https://docs.aws.amazon.com/prometheus/latest/userguide/what-is-Amazon-Managed-Service-Prometheus.html" target="_blank">What Is Amazon Managed Service for Prometheus?</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/GettingStarted.html" target="_blank">Getting Started with Amazon CloudWatch</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch_concepts.html" target="_blank">CloudWatch Concepts</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/working_with_metrics.html" target="_blank">Using CloudWatch Metrics</a>
- <a href="https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-concepts.html" target="_blank">CloudTrail Concepts</a>
- <a href="https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-and-update-a-trail.html" target="_blank">Creating a Trail</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/" target="_blank">CloudWatch Logs</a>

#### Skill 1.1.2: Configure and manage the CloudWatch agent to collect metrics and logs from Amazon EC2 instances, Amazon Elastic Container Service (Amazon ECS) clusters, or Amazon Elastic Kubernetes Service (Amazon EKS) clusters

**Why:** The CloudWatch agent is essential for collecting system-level and application metrics that AWS doesn't provide by default, such as memory utilization, disk usage, and custom application logs. Exam scenarios frequently test your knowledge of agent installation, configuration file syntax, and troubleshooting agent failures. You must understand how to configure the agent to send metrics and logs to CloudWatch from EC2, ECS, and EKS environments, as this is a daily operational task for SysOps administrators monitoring infrastructure health and application performance.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/Install-CloudWatch-Agent.html" target="_blank">Collect Metrics and Logs from Amazon EC2 Instances with the CloudWatch Agent</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/install-CloudWatch-Agent-on-EC2-Instance.html" target="_blank">Installing the CloudWatch Agent</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch-Agent-Configuration-File-Details.html" target="_blank">Create the CloudWatch Agent Configuration File</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch-Agent-Configuration-File-Details.html" target="_blank">Manually Create or Edit the CloudWatch Agent Configuration File</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/metrics-collected-by-CloudWatch-agent.html" target="_blank">Metrics Collected by the CloudWatch Agent</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch-Agent-Configuration-File-Details.html#CloudWatch-Agent-Configuration-File-Complete-Example" target="_blank">CloudWatch Agent Configuration File: Complete Examples</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/troubleshooting-CloudWatch-Agent.html" target="_blank">Troubleshooting the CloudWatch Agent</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/deploy-container-insights-ECS-instancelevel.html" target="_blank">Installing the CloudWatch Agent on Amazon ECS</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/deploy-container-insights-EKS.html" target="_blank">Setting Up Container Insights on Amazon EKS and Kubernetes</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/troubleshooting-CloudWatch-Agent.html" target="_blank">Verify CloudWatch Agent Installation and Configuration</a>

#### Skill 1.1.3: Configure, identify, and troubleshoot CloudWatch alarms that can invoke AWS services directly or through Amazon EventBridge (for example, by creating composite alarms and identifying their invokable actions)

**Why:** CloudWatch alarms are the primary mechanism for proactive monitoring and automated remediation in AWS, making this a heavily tested skill. Exam questions present scenarios where you must configure alarms for specific thresholds, troubleshoot why alarms aren't triggering correctly, or design composite alarms that combine multiple conditions. Understanding alarm states (OK, ALARM, INSUFFICIENT_DATA), evaluation periods, missing data treatment, and integration with EventBridge for complex workflows is critical for real-world incident response and automation.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html" target="_blank">Using Amazon CloudWatch Alarms</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/ConsoleAlarms.html" target="_blank">Creating a CloudWatch Alarm Based on a Static Threshold</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/Create_Anomaly_Detection_Alarm.html" target="_blank">Creating a CloudWatch Alarm Based on Anomaly Detection</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/Create_Composite_Alarm.html" target="_blank">Creating a Composite Alarm</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html#alarm-states" target="_blank">Alarm States</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html#alarms-and-missing-data" target="_blank">Configuring How CloudWatch Alarms Treat Missing Data</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/using-metric-math.html" target="_blank">Using Metric Math</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/UsingAlarmActions.html" target="_blank">Create Alarms to Stop, Terminate, Reboot, or Recover an Instance</a>
- <a href="https://docs.aws.amazon.com/eventbridge/latest/userguide/" target="_blank">Amazon EventBridge User Guide</a>
- <a href="https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-create-rule.html" target="_blank">Creating Amazon EventBridge Rules That React to Events</a>
- <a href="https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-event-patterns.html" target="_blank">Amazon EventBridge Event Patterns</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch-troubleshooting.html#CloudWatch-alarm-troubleshooting" target="_blank">Troubleshooting Amazon CloudWatch Alarms</a>

#### Skill 1.1.4: Create, implement, and manage customizable and shareable CloudWatch dashboards that display metrics and alarms for AWS resources across multiple accounts and AWS Regions

**Why:** CloudWatch dashboards provide centralized visibility into system health and are tested through scenarios requiring cross-account, cross-region monitoring configurations. The exam tests your understanding of dashboard widgets, automatic dashboards, cross-account observability, and sharing dashboards with stakeholders. As a SysOps administrator, you must design dashboards that provide meaningful insights for different audiences (operations teams, management, developers) and understand how to aggregate metrics from multiple sources for unified monitoring in complex, multi-account AWS Organizations environments.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch_Dashboards.html" target="_blank">Using Amazon CloudWatch Dashboards</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/create_dashboard.html" target="_blank">Creating a CloudWatch Dashboard</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/add_remove_graph_dashboard.html" target="_blank">Add or Remove a Graph from a CloudWatch Dashboard</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/Cross-Account-Cross-Region.html" target="_blank">Cross-Account Cross-Region CloudWatch Console</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch-dashboard-sharing.html" target="_blank">Share Your CloudWatch Dashboards</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch-Automatic-Dashboards.html" target="_blank">CloudWatch Automatic Dashboards</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/using-metric-math.html" target="_blank">Using Metric Math</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/create-and-work-with-widgets.html" target="_blank">CloudWatch Dashboard Widgets</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch-Unified-Cross-Account-Setup.html" target="_blank">Enable Cross-Account Observability in CloudWatch</a>

#### Skill 1.1.5: Configure AWS services to send notifications to Amazon Simple Notification Service (Amazon SNS) and to invoke alarms that send notifications to Amazon SNS

**Why:** SNS integration with CloudWatch alarms is fundamental for alert notification and is tested in nearly every monitoring scenario. You must understand how to configure SNS topics, subscriptions (email, SMS, HTTP/HTTPS, Lambda), and how alarms publish to SNS. Exam questions test troubleshooting scenarios where notifications aren't being received, understanding subscription confirmation requirements, and configuring appropriate notification protocols. Real-world SysOps roles require proper alert routing to ensure the right teams receive timely notifications for system issues.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/US_SetupSNS.html" target="_blank">Set Up Amazon SNS Notifications</a>
- <a href="https://docs.aws.amazon.com/sns/latest/dg/" target="_blank">Amazon Simple Notification Service Developer Guide</a>
- <a href="https://docs.aws.amazon.com/sns/latest/dg/welcome.html" target="_blank">What Is Amazon SNS?</a>
- <a href="https://docs.aws.amazon.com/sns/latest/dg/sns-create-topic.html" target="_blank">Creating an Amazon SNS Topic</a>
- <a href="https://docs.aws.amazon.com/sns/latest/dg/sns-create-subscribe-endpoint-to-topic.html" target="_blank">Subscribing to an Amazon SNS Topic</a>
- <a href="https://docs.aws.amazon.com/sns/latest/dg/sns-message-filtering.html" target="_blank">Amazon SNS Message Filtering</a>
- <a href="https://docs.aws.amazon.com/sns/latest/dg/sns-troubleshooting.html" target="_blank">Troubleshooting Amazon SNS</a>
- <a href="https://docs.aws.amazon.com/sns/latest/dg/sns-mobile-application-as-subscriber.html" target="_blank">Using Amazon SNS for Application-to-Person (A2P) Messaging</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/US_SetupSNS.html" target="_blank">Configuring CloudWatch to Send Notifications</a>

---

## Task 1.2: Identify and remediate issues by using monitoring and availability metrics

### Skills & Corresponding Documentation

#### Skill 1.2.1: Analyze performance metrics and automate remediation strategies by using AWS services and functionality (for example, CloudWatch, AWS User Notifications, AWS Lambda, AWS Systems Manager, CloudTrail, auto scaling)

**Why:** Automated remediation is a core SysOps competency that reduces manual intervention and improves system reliability, making it heavily tested on the exam. You must understand how to analyze metrics to identify performance issues and implement automated responses using Lambda functions, Systems Manager Automation, or Auto Scaling policies. Exam scenarios test your ability to design remediation workflows that respond to specific metric thresholds or events, such as automatically restarting failed services, scaling resources, or running diagnostic scripts when issues are detected.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/working_with_metrics.html" target="_blank">Using Amazon CloudWatch Metrics</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch_Anomaly_Detection.html" target="_blank">CloudWatch Anomaly Detection</a>
- <a href="https://docs.aws.amazon.com/lambda/latest/dg/" target="_blank">AWS Lambda Developer Guide</a>
- <a href="https://docs.aws.amazon.com/lambda/latest/dg/services-cloudwatchevents.html" target="_blank">Using AWS Lambda with Amazon CloudWatch Events</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/" target="_blank">AWS Systems Manager User Guide</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-automation.html" target="_blank">AWS Systems Manager Automation</a>
- <a href="https://docs.aws.amazon.com/autoscaling/ec2/userguide/" target="_blank">Amazon EC2 Auto Scaling User Guide</a>
- <a href="https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-scale-based-on-demand.html" target="_blank">Dynamic Scaling for Amazon EC2 Auto Scaling</a>
- <a href="https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-scaling-target-tracking.html" target="_blank">Target Tracking Scaling Policies</a>
- <a href="https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-scaling-simple-step.html" target="_blank">Step and Simple Scaling Policies</a>
- <a href="https://docs.aws.amazon.com/notifications/latest/userguide/" target="_blank">AWS User Notifications</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/AnalyzingLogData.html" target="_blank">Analyzing Log Data with CloudWatch Logs Insights</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/MonitoringLogData.html" target="_blank">Creating Metric Filters</a>

#### Skill 1.2.2: Use EventBridge to route, enrich, and deliver events, and troubleshoot any issues with event bus rules

**Why:** EventBridge is AWS's event-driven architecture service and is increasingly tested as organizations move toward event-driven operations. The exam tests your understanding of event buses (default, custom, partner), event patterns, rules, and targets. You must know how to create rules that match specific event patterns, route events to appropriate targets (Lambda, Step Functions, Systems Manager, SNS), and troubleshoot when events aren't being delivered. Understanding EventBridge is critical for building scalable, loosely-coupled operational automation that responds to changes in your AWS environment.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/eventbridge/latest/userguide/" target="_blank">Amazon EventBridge User Guide</a>
- <a href="https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-what-is.html" target="_blank">What Is Amazon EventBridge?</a>
- <a href="https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-event-bus.html" target="_blank">Amazon EventBridge Event Buses</a>
- <a href="https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-rules.html" target="_blank">Amazon EventBridge Rules</a>
- <a href="https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-event-patterns.html" target="_blank">Amazon EventBridge Event Patterns</a>
- <a href="https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-targets.html" target="_blank">Amazon EventBridge Targets</a>
- <a href="https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-get-started.html" target="_blank">Tutorial: Create an EventBridge Rule for AWS Service Events</a>
- <a href="https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-transform-target-input.html" target="_blank">EventBridge Event Transformation</a>
- <a href="https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-troubleshooting.html" target="_blank">Troubleshooting Amazon EventBridge</a>
- <a href="https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-event-patterns-content-based-filtering.html" target="_blank">Content Filtering in Amazon EventBridge</a>
- <a href="https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-schema.html" target="_blank">Schema Registry in Amazon EventBridge</a>

#### Skill 1.2.3: Create or run custom and predefined Systems Manager Automation runbooks (for example, by using AWS SDKs or custom scripts) to automate tasks and streamline processes on AWS

**Why:** Systems Manager Automation runbooks are the primary tool for operational task automation in AWS and are extensively tested. The exam requires you to understand predefined AWS runbooks (AWS-RestartEC2Instance, AWS-CreateSnapshot, AWS-PatchInstanceWithRollback), how to create custom runbooks, and when to use different document types (Automation, Command). You must know runbook syntax, including steps, actions, parameters, and error handling. Understanding how to execute runbooks manually, on a schedule, or triggered by events is critical for the operational automation scenarios that dominate the SysOps exam.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-automation.html" target="_blank">AWS Systems Manager Automation</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/automation-documents.html" target="_blank">Working with Automation Documents</a>
- <a href="https://docs.aws.amazon.com/systems-manager-automation-runbooks/latest/userguide/" target="_blank">Systems Manager Automation Runbook Reference</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/automation-documents.html" target="_blank">Creating Your Own Runbooks</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/automation-actions.html" target="_blank">Automation Actions Reference</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/automation-working-executing.html" target="_blank">Running an Automation</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/automation-troubleshooting.html" target="_blank">Troubleshooting Systems Manager Automation</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/automation-aws-apis-calling.html" target="_blank">Using AWS APIs in Runbooks</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/execute-remote-commands.html" target="_blank">AWS Systems Manager Run Command</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/documents.html" target="_blank">Systems Manager Document Types</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/automation-walk.html" target="_blank">Automation Walkthrough Examples</a>

---

## Task 1.3: Implement performance optimization strategies for compute, storage, and database resources

### Skills & Corresponding Documentation

#### Skill 1.3.1: Optimize compute resources and remediate performance problems by using performance metrics, resource tags, and AWS tools

**Why:** Compute optimization is essential for cost management and performance, making it a frequent exam topic. You must understand how to analyze EC2 CloudWatch metrics (CPU, network, disk I/O), use AWS Compute Optimizer for rightsizing recommendations, and implement solutions like changing instance types, enabling enhanced networking, or using placement groups. The exam tests your ability to identify underutilized or overutilized instances through metrics analysis and recommend appropriate actions. Understanding resource tagging for cost allocation and automated remediation is also critical for operational efficiency.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-cloudwatch.html" target="_blank">Monitoring Your Instances Using CloudWatch</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/viewing_metrics_with_cloudwatch.html" target="_blank">List Available CloudWatch Metrics for Your Instances</a>
- <a href="https://docs.aws.amazon.com/compute-optimizer/latest/ug/" target="_blank">AWS Compute Optimizer User Guide</a>
- <a href="https://docs.aws.amazon.com/compute-optimizer/latest/ug/viewing-recommendations.html" target="_blank">Viewing Recommendations in AWS Compute Optimizer</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-resize.html" target="_blank">Changing the Instance Type</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/enhanced-networking.html" target="_blank">Enhanced Networking on Linux</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html" target="_blank">Placement Groups</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Using_Tags.html" target="_blank">Tagging Your Amazon EC2 Resources</a>
- <a href="https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/cost-alloc-tags.html" target="_blank">Using Cost Allocation Tags</a>
- <a href="https://docs.aws.amazon.com/awssupport/latest/user/trusted-advisor-check-reference.html" target="_blank">AWS Trusted Advisor Check Reference</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-optimize-cpu.html" target="_blank">Optimizing CPU Options</a>

#### Skill 1.3.2: Analyze Amazon Elastic Block Store (Amazon EBS) performance metrics, troubleshoot issues, and optimize volume types to improve performance and reduce cost

**Why:** EBS performance optimization is critical for application performance and is heavily tested through scenarios involving IOPS, throughput, and latency issues. You must understand how to interpret EBS CloudWatch metrics (VolumeReadBytes, VolumeWriteBytes, VolumeQueueLength, BurstBalance), identify performance bottlenecks, and select appropriate volume types (gp3, gp2, io2, io1, st1, sc1) based on workload requirements. The exam tests your knowledge of EBS-optimized instances, volume initialization from snapshots, and when to modify volume types to balance performance and cost. Understanding the transition from gp2 to gp3 for cost savings is a common exam scenario.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html" target="_blank">Amazon EBS Volume Types</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSPerformance.html" target="_blank">Amazon EBS Volume Performance on Linux Instances</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/monitoring-volume-status.html" target="_blank">Monitoring the Status of Your Volumes</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using_cloudwatch_ebs.html" target="_blank">Amazon CloudWatch Metrics for Amazon EBS</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-io-characteristics.html" target="_blank">I/O Characteristics and Monitoring</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-initialize.html" target="_blank">Initializing Amazon EBS Volumes</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-optimized.html" target="_blank">Amazon EBS–Optimized Instances</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-modify-volume.html" target="_blank">Modifying an EBS Volume</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSPerformance.html#ebs-performance-tips" target="_blank">EBS Performance Guidelines</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/benchmark_procedures.html" target="_blank">Benchmark EBS Volumes</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-fast-snapshot-restore.html" target="_blank">Amazon EBS Fast Snapshot Restore</a>

#### Skill 1.3.3: Implement and optimize Amazon S3 performance strategies (for example, AWS DataSync, S3 Transfer Acceleration, multipart uploads, S3 Lifecycle policies) to enhance data transfer, storage efficiency, and access patterns

**Why:** S3 performance optimization is tested through scenarios involving large data transfers, high request rates, and cost reduction strategies. You must understand request rate performance (3,500 PUT/POST/DELETE and 5,500 GET/HEAD per prefix per second), when to use multipart uploads (files over 100 MB), Transfer Acceleration for global uploads, and how prefix design affects performance. The exam tests your knowledge of lifecycle policies to transition objects between storage classes automatically, and how to optimize access patterns using CloudFront, S3 Select, or intelligent-tiering. Understanding these strategies is essential for managing large-scale data storage efficiently.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/optimizing-performance.html" target="_blank">Best Practices Design Patterns: Optimizing Amazon S3 Performance</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/optimizing-performance-guidelines.html" target="_blank">Performance Guidelines for Amazon S3</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/transfer-acceleration.html" target="_blank">Using Amazon S3 Transfer Acceleration</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/mpuoverview.html" target="_blank">Uploading and Copying Objects Using Multipart Upload</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lifecycle-mgmt.html" target="_blank">Managing Your Storage Lifecycle</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/lifecycle-transition-general-considerations.html" target="_blank">Transitioning Objects Using Amazon S3 Lifecycle</a>
- <a href="https://docs.aws.amazon.com/datasync/latest/userguide/" target="_blank">AWS DataSync User Guide</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/monitoring-overview.html" target="_blank">Monitoring Amazon S3</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/optimizing-performance.html" target="_blank">Request Rate and Performance Guidelines</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/DownloadDistS3AndCustomOrigins.html" target="_blank">Using Amazon CloudFront with Amazon S3</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/selecting-content-from-objects.html" target="_blank">Filtering and Retrieving Data Using Amazon S3 Select</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/intelligent-tiering.html" target="_blank">Amazon S3 Intelligent-Tiering</a>

#### Skill 1.3.4: Evaluate and select shared storage solutions (for example, Amazon Elastic File System [Amazon EFS], Amazon FSx), and optimize the solutions (for example, EFS lifecycle policies) for specific use cases and requirements

**Why:** Shared storage selection and optimization is tested through scenarios requiring concurrent access from multiple instances. You must understand when to use EFS (Linux NFS, elastic scaling) versus FSx for Windows File Server (Windows SMB) versus FSx for Lustre (HPC workloads). The exam tests your knowledge of EFS performance modes (General Purpose versus Max I/O), throughput modes (Bursting, Provisioned, Elastic), and storage classes (Standard versus Infrequent Access). Understanding lifecycle policies to automatically move files to IA storage and performance optimization techniques is critical for managing shared storage costs and performance effectively.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/efs/latest/ug/" target="_blank">Amazon Elastic File System User Guide</a>
- <a href="https://docs.aws.amazon.com/efs/latest/ug/performance.html" target="_blank">Amazon EFS Performance</a>
- <a href="https://docs.aws.amazon.com/efs/latest/ug/performance.html#performancemodes" target="_blank">EFS Performance Modes</a>
- <a href="https://docs.aws.amazon.com/efs/latest/ug/performance.html#throughput-modes" target="_blank">EFS Throughput Modes</a>
- <a href="https://docs.aws.amazon.com/efs/latest/ug/lifecycle-management-efs.html" target="_blank">EFS Lifecycle Management</a>
- <a href="https://docs.aws.amazon.com/efs/latest/ug/storage-classes.html" target="_blank">EFS Storage Classes</a>
- <a href="https://docs.aws.amazon.com/efs/latest/ug/how-it-works.html" target="_blank">Amazon EFS: How It Works</a>
- <a href="https://docs.aws.amazon.com/efs/latest/ug/monitoring_overview.html" target="_blank">Monitoring Amazon EFS</a>
- <a href="https://docs.aws.amazon.com/fsx/latest/WindowsGuide/" target="_blank">Amazon FSx for Windows File Server User Guide</a>
- <a href="https://docs.aws.amazon.com/fsx/latest/LustreGuide/" target="_blank">Amazon FSx for Lustre User Guide</a>
- <a href="https://docs.aws.amazon.com/fsx/latest/ONTAPGuide/" target="_blank">Amazon FSx for NetApp ONTAP User Guide</a>
- <a href="https://docs.aws.amazon.com/fsx/latest/OpenZFSGuide/" target="_blank">Amazon FSx for OpenZFS User Guide</a>
- <a href="https://aws.amazon.com/efs/when-to-choose-efs/" target="_blank">Choosing Between Amazon EFS and Amazon FSx</a>

#### Skill 1.3.5: Monitor Amazon RDS metrics (for example, Amazon RDS Performance Insights, CloudWatch alarms), and modify configurations to increase performance efficiency (for example, Performance Insights proactive recommendations, RDS Proxy)

**Why:** RDS performance monitoring and optimization is critical for database-driven applications and is heavily tested. You must understand how to interpret RDS CloudWatch metrics (CPUUtilization, DatabaseConnections, ReadLatency, WriteLatency, FreeableMemory), use Performance Insights to identify query bottlenecks, and implement optimization strategies like read replicas, RDS Proxy for connection pooling, and parameter group modifications. The exam tests scenarios where you must diagnose performance issues (high CPU, connection exhaustion, slow queries) and recommend appropriate solutions. Understanding when to scale vertically versus horizontally and how to use Enhanced Monitoring is essential.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Monitoring.html" target="_blank">Monitoring Amazon RDS</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_PerfInsights.html" target="_blank">Using Amazon RDS Performance Insights</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/MonitoringOverview.html" target="_blank">Overview of Monitoring Amazon RDS</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/accessing-monitoring.html" target="_blank">Viewing DB Instance Metrics</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_Monitoring.OS.Viewing.html" target="_blank">Using CloudWatch Alarms with Amazon RDS</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/rds-proxy.html" target="_blank">Using Amazon RDS Proxy</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithParamGroups.html" target="_blank">Working with DB Parameter Groups</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ReadRepl.html" target="_blank">Working with Read Replicas</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_Monitoring.OS.html" target="_blank">Using Enhanced Monitoring</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_BestPractices.html" target="_blank">Best Practices for Amazon RDS</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_PerfInsights.UsingDashboard.AnalyzeDBLoad.html" target="_blank">Analyzing DB Load by Wait Events</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_BestPractices.html#CHAP_BestPractices.Performance" target="_blank">DB Instance RAM Recommendations</a>

#### Skill 1.3.6: Implement, monitor, and optimize EC2 instances and their associated storage and networking capabilities (for example, EC2 placement groups)

**Why:** Comprehensive EC2 optimization is fundamental to the SysOps role and spans multiple exam domains. You must understand how to optimize compute (instance types, sizing), storage (EBS volume types, instance store), and networking (enhanced networking, placement groups, Elastic Network Adapters). The exam tests your ability to diagnose performance issues across all three areas and implement appropriate solutions. Understanding placement group strategies (cluster for low latency, spread for fault tolerance, partition for distributed workloads) and when to enable enhanced networking or use Elastic Fabric Adapter for high-performance computing is critical for optimizing application performance and reducing costs.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-best-practices.html" target="_blank">Best Practices for Amazon EC2</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-cloudwatch.html" target="_blank">Monitoring Your Instances Using CloudWatch</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-types.html" target="_blank">Instance Types</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html" target="_blank">Placement Groups</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/enhanced-networking.html" target="_blank">Enhanced Networking on Linux</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-eni.html" target="_blank">Elastic Network Interfaces</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/nvme-ebs-volumes.html" target="_blank">Amazon EBS and NVMe on Linux Instances</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html" target="_blank">Amazon EC2 Instance Store</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/efa.html" target="_blank">Elastic Fabric Adapter</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-network-bandwidth.html" target="_blank">Network Performance</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-optimize-cpu.html" target="_blank">Optimizing CPU Options</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html" target="_blank">Instance Metadata and User Data</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-troubleshoot.html" target="_blank">Troubleshooting Instances</a>

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/cloudwatch/faqs/" target="_blank">Amazon CloudWatch FAQs</a>
- <a href="https://aws.amazon.com/cloudtrail/faqs/" target="_blank">AWS CloudTrail FAQs</a>
- <a href="https://aws.amazon.com/prometheus/faqs/" target="_blank">Amazon Managed Service for Prometheus FAQs</a>
- <a href="https://aws.amazon.com/sns/faqs/" target="_blank">Amazon SNS FAQs</a>
- <a href="https://aws.amazon.com/eventbridge/faqs/" target="_blank">Amazon EventBridge FAQs</a>
- <a href="https://aws.amazon.com/lambda/faqs/" target="_blank">AWS Lambda FAQs</a>
- <a href="https://aws.amazon.com/systems-manager/faq/" target="_blank">AWS Systems Manager FAQs</a>
- <a href="https://aws.amazon.com/ec2/autoscaling/faqs/" target="_blank">Amazon EC2 Auto Scaling FAQs</a>
- <a href="https://aws.amazon.com/compute-optimizer/faqs/" target="_blank">AWS Compute Optimizer FAQs</a>
- <a href="https://aws.amazon.com/ec2/faqs/" target="_blank">Amazon EC2 FAQs</a>
- <a href="https://aws.amazon.com/ebs/faqs/" target="_blank">Amazon EBS FAQs</a>
- <a href="https://aws.amazon.com/s3/faqs/" target="_blank">Amazon S3 FAQs</a>
- <a href="https://aws.amazon.com/datasync/faqs/" target="_blank">AWS DataSync FAQs</a>
- <a href="https://aws.amazon.com/efs/faq/" target="_blank">Amazon EFS FAQs</a>
- <a href="https://aws.amazon.com/fsx/windows/faqs/" target="_blank">Amazon FSx for Windows File Server FAQs</a>
- <a href="https://aws.amazon.com/fsx/lustre/faqs/" target="_blank">Amazon FSx for Lustre FAQs</a>
- <a href="https://aws.amazon.com/rds/faqs/" target="_blank">Amazon RDS FAQs</a>
- <a href="https://aws.amazon.com/rds/performance-insights/faqs/" target="_blank">Amazon RDS Performance Insights FAQs</a>
- <a href="https://aws.amazon.com/rds/proxy/faqs/" target="_blank">Amazon RDS Proxy FAQs</a>

---

## AWS Whitepapers

- <a href="https://docs.aws.amazon.com/wellarchitected/latest/operational-excellence-pillar/welcome.html" target="_blank">Operational Excellence Pillar - AWS Well-Architected Framework</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/performance-efficiency-pillar/welcome.html" target="_blank">Performance Efficiency Pillar - AWS Well-Architected Framework</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html" target="_blank">AWS Security Best Practices</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/operational-excellence-pillar/monitoring-and-observability.html" target="_blank">Monitoring and Observability</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/cost-optimization-laying-the-foundation/introduction.html" target="_blank">Introduction to AWS Cost Optimization</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-io-characteristics.html" target="_blank">Best Practices for Amazon EBS</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/optimizing-performance.html" target="_blank">Amazon S3 Performance Optimization</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/building-scalable-secure-multi-vpc-network-infrastructure/welcome.html" target="_blank">Building a Scalable and Secure Multi-VPC AWS Network Infrastructure</a>

---

## Final Thoughts

Domain 1 represents the core operational responsibilities of a SysOps administrator and is heavily weighted in the exam. Master CloudWatch comprehensively - it's the foundation of AWS monitoring and appears in nearly every exam scenario. Focus your study time on hands-on practice with the CloudWatch agent, creating alarms and dashboards, and building automated remediation workflows using EventBridge and Systems Manager. The combination of monitoring, logging, and automation skills tested in this domain directly translates to real-world operational excellence in AWS environments. Success in this domain requires both deep service knowledge and practical troubleshooting experience, so ensure you complement documentation study with hands-on lab work in your own AWS account.
