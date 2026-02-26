# AWS Certified Advanced Networking - Specialty (ANS-C01) Domain 1
## Network Design

**Official Exam Guide:** <a href="https://docs.aws.amazon.com/aws-certification/latest/advanced-networking-specialty-01/advanced-networking-specialty-01-domain1.html" target="_blank">Domain 1: Network Design</a>

**Skill Builder:** <a href="https://skillbuilder.aws/category/exam-prep/advanced-networking-specialty-ANS-C01" target="_blank">AWS Certified Advanced Networking - Specialty Exam Prep</a>

---

## Domain Overview

Domain 1 (30% - largest domain) focuses on edge services, DNS solutions, load balancing, logging/monitoring, hybrid connectivity, and multi-account/multi-Region connectivity.

---

## Task 1.1: Design edge network services for global architectures

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/" target="_blank">Amazon CloudFront Developer Guide</a>
- <a href="https://docs.aws.amazon.com/global-accelerator/latest/dg/" target="_blank">AWS Global Accelerator Developer Guide</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/IntegrationELB.html" target="_blank">CloudFront with ELB Integration</a>

---

## Task 1.2: Design DNS solutions (public, private, hybrid)

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/" target="_blank">Amazon Route 53 Developer Guide</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver.html" target="_blank">Route 53 Resolver</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy.html" target="_blank">Route 53 Routing Policies</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-configuring-dnssec.html" target="_blank">Route 53 DNSSEC</a>

---

## Task 1.3: Design load balancing solutions

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/elasticloadbalancing/latest/application/" target="_blank">Application Load Balancer Guide</a>
- <a href="https://docs.aws.amazon.com/elasticloadbalancing/latest/network/" target="_blank">Network Load Balancer Guide</a>
- <a href="https://docs.aws.amazon.com/elasticloadbalancing/latest/gateway/" target="_blank">Gateway Load Balancer Guide</a>
- <a href="https://kubernetes-sigs.github.io/aws-load-balancer-controller/" target="_blank">AWS Load Balancer Controller for Kubernetes</a>

---

## Task 1.4: Define logging and monitoring requirements

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/" target="_blank">Amazon CloudWatch Monitoring</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/tgw/tgw-network-manager.html" target="_blank">Transit Gateway Network Manager</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/reachability/" target="_blank">VPC Reachability Analyzer</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html" target="_blank">VPC Flow Logs</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/mirroring/" target="_blank">VPC Traffic Mirroring</a>

---

## Task 1.5: Design hybrid connectivity (on-premises to AWS)

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/directconnect/latest/UserGuide/" target="_blank">AWS Direct Connect User Guide</a>
- <a href="https://docs.aws.amazon.com/vpn/latest/s2svpn/" target="_blank">AWS Site-to-Site VPN User Guide</a>
- <a href="https://docs.aws.amazon.com/directconnect/latest/UserGuide/direct-connect-gateways.html" target="_blank">Direct Connect Gateways</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/tgw/tgw-connect.html" target="_blank">Transit Gateway Connect</a>

---

## Task 1.6: Design multi-account/multi-Region/multi-VPC connectivity

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/vpc/latest/tgw/" target="_blank">AWS Transit Gateway User Guide</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/peering/" target="_blank">VPC Peering Guide</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/privatelink/" target="_blank">AWS PrivateLink Guide</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/vpc-sharing.html" target="_blank">VPC Sharing</a>

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/route53/faqs/" target="_blank">Amazon Route 53 FAQs</a>
- <a href="https://aws.amazon.com/directconnect/faqs/" target="_blank">AWS Direct Connect FAQs</a>
- <a href="https://aws.amazon.com/transit-gateway/faqs/" target="_blank">AWS Transit Gateway FAQs</a>
- <a href="https://aws.amazon.com/global-accelerator/faqs/" target="_blank">AWS Global Accelerator FAQs</a>

---

## Study Tips

1. **Master BGP thoroughly** - AS_PATH, MED, Local Preference, communities, route propagation, active/passive configurations.

2. **Learn Transit Gateway patterns** - Hub-and-spoke, segmentation with route tables, peering, Connect attachments for SD-WAN.

3. **Understand Direct Connect** - VIFs (public, private, transit), LAG, MACSec, redundancy patterns, failover to VPN.

4. **Practice DNS design** - Route 53 Resolver endpoints (inbound/outbound), conditional forwarding, split-view DNS.

5. **Study load balancer types** - ALB (Layer 7, HTTP/HTTPS), NLB (Layer 4, TCP/UDP), GWLB (Layer 3, inline appliances).

---

**Note:** This is Domain 1 of 4, representing 30% (largest domain) of exam content.
