# AWS Certified Security - Specialty (SCS-C03) Domain 1
## Detection

**Official Exam Guide:** <a href="https://docs.aws.amazon.com/aws-certification/latest/examguides/security-specialty-03-domain1.html" target="_blank">Domain 1: Detection</a>

**Skill Builder:** <a href="https://skillbuilder.aws/category/exam-prep/security-specialty-SCS-C03" target="_blank">AWS Certified Security - Specialty Exam Prep</a>

---

## Domain Overview

Domain 1 (16%) focuses on designing and implementing monitoring/alerting solutions, logging solutions, and troubleshooting security monitoring.

---

## Task 1.1: Design and implement monitoring and alerting solutions

**Key Skills:**
- Analyze workloads to determine monitoring requirements
- Design workload monitoring strategies (resource health checks)
- Aggregate security and monitoring events
- Create metrics, alerts, dashboards for anomaly detection
- Automate regular assessments and investigations

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/guardduty/latest/ug/" target="_blank">Amazon GuardDuty User Guide</a>
- <a href="https://docs.aws.amazon.com/security-lake/latest/userguide/" target="_blank">Amazon Security Lake User Guide</a>
- <a href="https://docs.aws.amazon.com/securityhub/latest/userguide/" target="_blank">AWS Security Hub User Guide</a>
- <a href="https://docs.aws.amazon.com/macie/latest/user/" target="_blank">Amazon Macie User Guide</a>
- <a href="https://docs.aws.amazon.com/config/latest/developerguide/" target="_blank">AWS Config Developer Guide</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-state.html" target="_blank">Systems Manager State Manager</a>

---

## Task 1.2: Design and implement logging solutions

**Key Skills:**
- Identify log ingestion and storage sources
- Configure logging for AWS services and applications
- Implement log storage and data lakes (Security Lake)
- Analyze logs using AWS services
- Normalize, parse, and correlate logs
- Configure appropriate log sources based on threats

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/awscloudtrail/latest/userguide/" target="_blank">AWS CloudTrail User Guide</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/" target="_blank">Amazon CloudWatch Logs User Guide</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/AnalyzingLogData.html" target="_blank">CloudWatch Logs Insights</a>
- <a href="https://docs.aws.amazon.com/athena/latest/ug/" target="_blank">Amazon Athena User Guide</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html" target="_blank">VPC Flow Logs</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/tgw/tgw-flow-logs.html" target="_blank">Transit Gateway Flow Logs</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver-query-logs.html" target="_blank">Route 53 Resolver Query Logs</a>

---

## Task 1.3: Troubleshoot security monitoring, logging, and alerting

**Key Skills:**
- Analyze functionality, permissions, and configuration of resources
- Remediate misconfiguration (CloudWatch Agent, missing logs)

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/lambda/latest/dg/monitoring-cloudwatchlogs.html" target="_blank">Lambda Function Logging</a>
- <a href="https://docs.aws.amazon.com/apigateway/latest/developerguide/set-up-logging.html" target="_blank">API Gateway Logging</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/logging.html" target="_blank">CloudFront Logging</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/Install-CloudWatch-Agent.html" target="_blank">CloudWatch Agent Installation</a>

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/guardduty/faqs/" target="_blank">Amazon GuardDuty FAQs</a>
- <a href="https://aws.amazon.com/security-hub/faqs/" target="_blank">AWS Security Hub FAQs</a>
- <a href="https://aws.amazon.com/macie/faq/" target="_blank">Amazon Macie FAQs</a>
- <a href="https://aws.amazon.com/cloudtrail/faqs/" target="_blank">AWS CloudTrail FAQs</a>

---

## Study Tips

1. **Master threat detection services** - GuardDuty for threats, Macie for sensitive data, Security Hub for centralized findings, Inspector for vulnerabilities.

2. **Learn log aggregation** - Security Lake for OCSF format, CloudWatch Logs for centralization, Athena for querying S3 logs, OpenSearch for analysis.

3. **Understand CloudTrail thoroughly** - Organization trails, event selectors, data events, management events, S3 data events, Lambda data events.

4. **Practice monitoring design** - Which logs to enable (VPC Flow Logs, CloudTrail, ALB logs, CloudFront logs), retention policies, cost optimization.

5. **Study Config rules** - Conformance packs, auto-remediation, aggregators for multi-account, custom rules with Lambda.

---

**Note:** This is Domain 1 of 6, representing 16% of exam content.
