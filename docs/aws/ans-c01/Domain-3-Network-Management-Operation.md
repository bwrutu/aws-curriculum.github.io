# AWS Certified Advanced Networking - Specialty (ANS-C01) Domain 3
## Network Management and Operation

**Official Exam Guide:** <a href="https://docs.aws.amazon.com/aws-certification/latest/advanced-networking-specialty-01/advanced-networking-specialty-01-domain3.html" target="_blank">Domain 3: Network Management and Operation</a>

**Skill Builder:** <a href="https://skillbuilder.aws/category/exam-prep/advanced-networking-specialty-ANS-C01" target="_blank">AWS Certified Advanced Networking - Specialty Exam Prep</a>

---

## Domain Overview

Domain 3 (20%) focuses on maintaining connectivity, monitoring and troubleshooting network traffic, and optimizing networks for performance, reliability, and cost.

---

## Task 3.1: Maintain routing and connectivity

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/directconnect/latest/UserGuide/routing-and-bgp.html" target="_blank">Direct Connect Routing and BGP</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/tgw/how-transit-gateways-work.html" target="_blank">How Transit Gateways Work</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/privatelink/vpc-endpoints.html" target="_blank">VPC Endpoints</a>
- <a href="https://docs.aws.amazon.com/general/latest/gr/aws-service-information.html" target="_blank">AWS Service Quotas</a>

---

## Task 3.2: Monitor and analyze network traffic

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html" target="_blank">VPC Flow Logs</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/mirroring/" target="_blank">VPC Traffic Mirroring</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/reachability/" target="_blank">VPC Reachability Analyzer</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/tgw/tgw-network-manager.html" target="_blank">Transit Gateway Network Manager</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/" target="_blank">CloudWatch Logs</a>

---

## Task 3.3: Optimize networks for performance, reliability, cost

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/enhanced-networking.html" target="_blank">Enhanced Networking on EC2</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/efa.html" target="_blank">Elastic Fabric Adapter (EFA)</a>
- <a href="https://docs.aws.amazon.com/global-accelerator/latest/dg/" target="_blank">AWS Global Accelerator</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Subnets.html#vpc-resize" target="_blank">VPC Secondary CIDR</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/network_mtu.html" target="_blank">Network MTU for EC2 Instances</a>

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/cloudwatch/faqs/" target="_blank">Amazon CloudWatch FAQs</a>
- <a href="https://aws.amazon.com/global-accelerator/faqs/" target="_blank">AWS Global Accelerator FAQs</a>

---

## Study Tips

1. **Master VPC Flow Logs** - Default format vs custom format, aggregation intervals, flow log fields, filtering, analysis with Athena/CloudWatch Logs Insights.

2. **Learn Reachability Analyzer** - Path analysis, verify connectivity, identify misconfigurations, automate validation.

3. **Understand network interfaces** - ENI (basic), ENA (enhanced networking up to 100 Gbps), EFA (HPC with OS-bypass).

4. **Practice BGP optimization** - AS_PATH prepending, Local Preference, MED, communities for load sharing and active/passive.

5. **Study jumbo frames** - MTU 9001 for VPC, MTU 8500 for Transit Gateway, MTU 1500 for internet gateway.

---

**Note:** This is Domain 3 of 4, representing 20% of exam content.
