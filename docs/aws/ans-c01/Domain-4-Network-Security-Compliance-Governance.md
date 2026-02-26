# AWS Certified Advanced Networking - Specialty (ANS-C01) Domain 4
## Network Security, Compliance, and Governance

**Official Exam Guide:** <a href="https://docs.aws.amazon.com/aws-certification/latest/advanced-networking-specialty-01/advanced-networking-specialty-01-domain4.html" target="_blank">Domain 4: Network Security, Compliance, and Governance</a>

**Skill Builder:** <a href="https://skillbuilder.aws/category/exam-prep/advanced-networking-specialty-ANS-C01" target="_blank">AWS Certified Advanced Networking - Specialty Exam Prep</a>

---

## Domain Overview

Domain 4 (24%) focuses on implementing network security features, validating/auditing security, and maintaining data confidentiality.

---

## Task 4.1: Implement network security features

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/waf/latest/developerguide/" target="_blank">AWS WAF Developer Guide</a>
- <a href="https://docs.aws.amazon.com/shield/latest/DeveloperGuide/" target="_blank">AWS Shield Developer Guide</a>
- <a href="https://docs.aws.amazon.com/network-firewall/latest/developerguide/" target="_blank">AWS Network Firewall Developer Guide</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/vpc-security-groups.html" target="_blank">VPC Security Groups</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html" target="_blank">Network ACLs</a>
- <a href="https://docs.aws.amazon.com/elasticloadbalancing/latest/gateway/" target="_blank">Gateway Load Balancer</a>

---

## Task 4.2: Validate and audit security

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html" target="_blank">VPC Flow Logs</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/mirroring/" target="_blank">VPC Traffic Mirroring</a>
- <a href="https://docs.aws.amazon.com/awscloudtrail/latest/userguide/" target="_blank">AWS CloudTrail User Guide</a>
- <a href="https://docs.aws.amazon.com/waf/latest/developerguide/fms-chapter.html" target="_blank">AWS Firewall Manager</a>
- <a href="https://docs.aws.amazon.com/awssupport/latest/user/trusted-advisor.html" target="_blank">AWS Trusted Advisor</a>

---

## Task 4.3: Implement confidentiality of data and communications

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/vpn/latest/s2svpn/" target="_blank">AWS Site-to-Site VPN</a>
- <a href="https://docs.aws.amazon.com/directconnect/latest/UserGuide/encryption-in-transit.html" target="_blank">Encryption Over Direct Connect</a>
- <a href="https://docs.aws.amazon.com/acm/latest/userguide/" target="_blank">AWS Certificate Manager User Guide</a>
- <a href="https://docs.aws.amazon.com/privateca/latest/userguide/" target="_blank">AWS Private Certificate Authority</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-configuring-dnssec.html" target="_blank">Configuring DNSSEC</a>

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/waf/faqs/" target="_blank">AWS WAF FAQs</a>
- <a href="https://aws.amazon.com/network-firewall/faqs/" target="_blank">AWS Network Firewall FAQs</a>
- <a href="https://aws.amazon.com/shield/faqs/" target="_blank">AWS Shield FAQs</a>
- <a href="https://aws.amazon.com/certificate-manager/faqs/" target="_blank">AWS Certificate Manager FAQs</a>

---

## Study Tips

1. **Master Network Firewall** - Stateful/stateless rules, Suricata-compatible IPS, domain filtering, traffic flow inspection.

2. **Learn encryption in transit** - IPsec over Direct Connect, MACsec, TLS termination at load balancers, VPN tunnels.

3. **Understand security layers** - NACLs (stateless, subnet-level), security groups (stateful, instance-level), WAF (application-level).

4. **Practice with Flow Logs** - Accepted/rejected traffic, troubleshooting security group rules, identifying patterns, custom fields.

5. **Study DNSSEC** - Chain of trust, KSK/ZSK keys, Route 53 implementation, validation.

---

## Complete Exam Summary

**Exam Format:**
- 65 questions (50 scored + 15 unscored)
- Multiple response, Matching
- Passing score: 700/1000
- 170 minutes

**Domain Weightings:**
- Domain 1: Network Design (30%)
- Domain 2: Network Implementation (26%)
- Domain 3: Network Management and Operation (20%)
- Domain 4: Network Security, Compliance, and Governance (24%)

**Target Candidate:**
- 5+ years networking experience
- 2+ years cloud and hybrid networking experience
- Advanced understanding of networking protocols and architectures

**Key AWS Networking Services:**
- **Connectivity:** VPC, Transit Gateway, Direct Connect, VPN, PrivateLink
- **Edge:** CloudFront, Global Accelerator, Route 53
- **Load Balancing:** ALB, NLB, GWLB
- **Security:** WAF, Shield, Network Firewall, Security Groups, NACLs
- **Monitoring:** VPC Flow Logs, Traffic Mirroring, Reachability Analyzer, CloudWatch
- **DNS:** Route 53, Route 53 Resolver

**Core Networking Concepts:**
- **BGP:** AS_PATH, Local Preference, MED, communities, route propagation
- **Routing:** Static vs dynamic, route tables, propagation, BGP over Direct Connect
- **Hybrid Connectivity:** Direct Connect (VIFs, LAG, MACsec), Site-to-Site VPN, Transit Gateway Connect
- **Multi-Account:** Transit Gateway sharing via RAM, VPC peering, PrivateLink
- **DNS:** Public/private hosted zones, Resolver endpoints, conditional forwarding, DNSSEC
- **Load Balancing:** Layer 3/4/7, target groups, health checks, sticky sessions
- **Security:** Defense in depth, encryption in transit, IPsec, TLS, security groups vs NACLs
- **Performance:** Enhanced networking (ENA, EFA), jumbo frames (MTU), Global Accelerator
- **Monitoring:** Flow logs, traffic mirroring, Reachability Analyzer, CloudWatch

**Study Resources:**
- <a href="https://docs.aws.amazon.com/whitepapers/latest/aws-vpc-connectivity-options/" target="_blank">AWS VPC Connectivity Options Whitepaper</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/hybrid-connectivity/" target="_blank">Hybrid Connectivity Whitepaper</a>
- <a href="https://aws.amazon.com/architecture/networking-content-delivery/" target="_blank">AWS Networking & Content Delivery Architecture</a>

Good luck with your AWS Certified Advanced Networking - Specialty certification!

---

**Note:** This is Domain 4 of 4, representing 24% of exam content.
