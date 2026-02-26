# AWS Certified Security - Specialty (SCS-C03) Domain 3
## Infrastructure Security

**Official Exam Guide:** <a href="https://docs.aws.amazon.com/aws-certification/latest/examguides/security-specialty-03-domain3.html" target="_blank">Domain 3: Infrastructure Security</a>

**Skill Builder:** <a href="https://skillbuilder.aws/category/exam-prep/security-specialty-SCS-C03" target="_blank">AWS Certified Security - Specialty Exam Prep</a>

---

## Domain Overview

Domain 3 (18%) focuses on network edge security, compute workload security, and network security controls.

---

## Task 3.1: Design and implement security controls for network edge services

**Key Skills:**
- Define edge security strategies
- Implement network edge protection (CloudFront, WAF, Shield)
- Design AWS edge controls (geography, rate limiting, fingerprinting)
- Configure integrations with third-party services

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/" target="_blank">Amazon CloudFront Developer Guide</a>
- <a href="https://docs.aws.amazon.com/waf/latest/developerguide/" target="_blank">AWS WAF Developer Guide</a>
- <a href="https://docs.aws.amazon.com/waf/latest/developerguide/aws-managed-rule-groups-list.html" target="_blank">AWS Managed Rules for WAF</a>
- <a href="https://docs.aws.amazon.com/shield/latest/DeveloperGuide/" target="_blank">AWS Shield Developer Guide</a>

---

## Task 3.2: Design and implement security controls for compute workloads

**Key Skills:**
- Design hardened AMIs and container images
- Apply instance profiles, service roles, execution roles
- Scan compute resources for vulnerabilities
- Deploy patches and maintain compliance
- Configure secure administrative access
- Discover and remediate vulnerabilities in pipelines
- Implement GenAI protections (OWASP Top 10 for LLMs)

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/imagebuilder/latest/userguide/" target="_blank">EC2 Image Builder User Guide</a>
- <a href="https://docs.aws.amazon.com/inspector/latest/user/" target="_blank">Amazon Inspector User Guide</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-patch.html" target="_blank">Systems Manager Patch Manager</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager.html" target="_blank">Systems Manager Session Manager</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-connect-methods.html" target="_blank">EC2 Instance Connect</a>
- <a href="https://docs.aws.amazon.com/codeguru/latest/security-ug/" target="_blank">Amazon CodeGuru Security</a>

---

## Task 3.3: Design and troubleshoot network security controls

**Key Skills:**
- Design network controls (security groups, NACLs, Network Firewall)
- Design secure hybrid/multi-cloud connectivity
- Configure security for hybrid communication
- Design network segmentation
- Identify unnecessary network access

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/vpc-security-groups.html" target="_blank">VPC Security Groups</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html" target="_blank">Network ACLs</a>
- <a href="https://docs.aws.amazon.com/network-firewall/latest/developerguide/" target="_blank">AWS Network Firewall</a>
- <a href="https://docs.aws.amazon.com/vpn/latest/s2svpn/" target="_blank">AWS Site-to-Site VPN</a>
- <a href="https://docs.aws.amazon.com/directconnect/latest/UserGuide/" target="_blank">AWS Direct Connect</a>
- <a href="https://docs.aws.amazon.com/verified-access/latest/ug/" target="_blank">AWS Verified Access</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/reachability/" target="_blank">VPC Network Access Analyzer</a>

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/waf/faqs/" target="_blank">AWS WAF FAQs</a>
- <a href="https://aws.amazon.com/inspector/faqs/" target="_blank">Amazon Inspector FAQs</a>
- <a href="https://aws.amazon.com/network-firewall/faqs/" target="_blank">AWS Network Firewall FAQs</a>
- <a href="https://aws.amazon.com/cloudfront/faqs/" target="_blank">Amazon CloudFront FAQs</a>

---

## Study Tips

1. **Master WAF rules** - AWS Managed Rules, rate-based rules, geo-blocking, bot control, OWASP Top 10 protections, custom rules.

2. **Learn Inspector thoroughly** - Container image scanning (ECR), Lambda function scanning, EC2 network reachability, software vulnerabilities (CVE).

3. **Understand network segmentation** - Public/private subnets, NACLs for subnet-level control, security groups for instance-level, Network Firewall for stateful inspection.

4. **Practice patch management** - Patch Manager baselines, maintenance windows, patch groups, compliance reporting, automated patching.

5. **Study Session Manager** - Secure shell access without SSH, audit trails in CloudTrail, port forwarding, run commands across fleet.

---

**Note:** This is Domain 3 of 6, representing 18% of exam content.
