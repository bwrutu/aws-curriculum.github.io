# AWS Certified Advanced Networking - Specialty (ANS-C01) Domain 2
## Network Implementation

**Official Exam Guide:** <a href="https://docs.aws.amazon.com/aws-certification/latest/advanced-networking-specialty-01/advanced-networking-specialty-01-domain2.html" target="_blank">Domain 2: Network Implementation</a>

**Skill Builder:** <a href="https://skillbuilder.aws/category/exam-prep/advanced-networking-specialty-ANS-C01" target="_blank">AWS Certified Advanced Networking - Specialty Exam Prep</a>

---

## Domain Overview

Domain 2 (26%) focuses on implementing hybrid connectivity, multi-account/Region/VPC connectivity, DNS architectures, and network automation.

---

## Task 2.1: Implement hybrid connectivity (on-premises to AWS)

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/directconnect/latest/UserGuide/create-vif.html" target="_blank">Direct Connect Virtual Interfaces</a>
- <a href="https://docs.aws.amazon.com/vpn/latest/s2svpn/VPC_VPN.html" target="_blank">Site-to-Site VPN Connections</a>
- <a href="https://docs.aws.amazon.com/vpn/latest/s2svpn/accelerated-vpn.html" target="_blank">Accelerated Site-to-Site VPN</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/tgw/tgw-connect.html" target="_blank">Transit Gateway Connect for SD-WAN</a>

---

## Task 2.2: Implement multi-account/Region/VPC connectivity

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/vpc/latest/tgw/tgw-getting-started.html" target="_blank">Getting Started with Transit Gateway</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/peering/working-with-vpc-peering.html" target="_blank">Working with VPC Peering</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/privatelink/create-endpoint-service.html" target="_blank">Create VPC Endpoint Services</a>
- <a href="https://docs.aws.amazon.com/ram/latest/userguide/" target="_blank">AWS Resource Access Manager</a>

---

## Task 2.3: Implement complex DNS architectures

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/hosted-zones-private.html" target="_blank">Route 53 Private Hosted Zones</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver-forwarding-outbound-queries.html" target="_blank">Route 53 Resolver Outbound Endpoints</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver-forwarding-inbound-queries.html" target="_blank">Route 53 Resolver Inbound Endpoints</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver-rules-managing.html" target="_blank">Managing Resolver Rules</a>

---

## Task 2.4: Automate network infrastructure

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/" target="_blank">AWS CloudFormation User Guide</a>
- <a href="https://docs.aws.amazon.com/cdk/v2/guide/" target="_blank">AWS CDK Developer Guide</a>
- <a href="https://docs.aws.amazon.com/cli/latest/userguide/" target="_blank">AWS CLI User Guide</a>
- <a href="https://boto3.amazonaws.com/v1/documentation/api/latest/index.html" target="_blank">Boto3 (AWS SDK for Python) Documentation</a>

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/vpc/faqs/" target="_blank">Amazon VPC FAQs</a>
- <a href="https://aws.amazon.com/transit-gateway/faqs/" target="_blank">AWS Transit Gateway FAQs</a>
- <a href="https://aws.amazon.com/privatelink/faqs/" target="_blank">AWS PrivateLink FAQs</a>

---

## Study Tips

1. **Master Transit Gateway configuration** - Route tables, associations, propagations, attachments (VPC, VPN, Direct Connect, peering, Connect).

2. **Learn VIF configuration** - Public VIFs for AWS public services, private VIFs for VPCs, transit VIFs for Transit Gateway.

3. **Understand DNS forwarding** - Outbound endpoints for on-premises DNS queries, inbound endpoints for on-premises to AWS queries, conditional forwarding rules.

4. **Practice IaC** - CloudFormation for network resources, CDK for programmable infrastructure, event-driven automation with Lambda.

5. **Study hub-and-spoke** - Transit Gateway as hub, VPCs as spokes, route table segmentation, inspection VPC patterns.

---

**Note:** This is Domain 2 of 4, representing 26% of exam content.
