# AWS Certified SysOps Administrator - Associate (SOA-C03) Domain 5
## Networking and Content Delivery

**Official Exam Guide:** <a href="https://docs.aws.amazon.com/aws-certification/latest/examguides/sysops-administrator-associate-03-domain5.html" target="_blank">Domain 5: Networking and Content Delivery</a>  
**Skill Builder:** <a href="https://skillbuilder.aws/category/exam-prep/cloudops-engineer-associate-SOA-C03" target="_blank">AWS Certified SysOps Administrator - Associate (SOA-C03) Exam Prep</a>

Note: Some Skill Builder labs require a subscription.

---

## How to Study This Domain Effectively

### Study Tips

1. **Build VPCs from scratch multiple times** - Don't just read documentation; actually create VPCs with public and private subnets, configure route tables, set up internet gateways and Network Address Translation (NAT) gateways, and implement security groups and Network Access Control Lists (NACLs). The exam tests practical knowledge of how traffic flows through VPC components, and hands-on experience helps you visualize the traffic path when answering troubleshooting questions. Practice common patterns: public subnet with internet gateway for web servers, private subnet with NAT gateway for application servers, database subnet with no internet access.

2. **Master the difference between Security Groups and NACLs** - This is one of the most tested topics. Security Groups are stateful (return traffic automatically allowed), operate at instance level, support allow rules only, and evaluate all rules. NACLs are stateless (must explicitly allow return traffic), operate at subnet level, support allow and deny rules, and process rules in numbered order. Create scenarios where you configure both for defense-in-depth security, and practice troubleshooting scenarios where one is misconfigured causing connectivity issues.

3. **Understand Route 53 routing policies deeply** - Each routing policy serves different use cases and exam questions test your ability to select the appropriate policy. Simple (single resource), Weighted (A/B testing, gradual migration), Latency (performance optimization), Failover (active-passive disaster recovery), Geolocation (content localization), Geoproximity (geographic traffic distribution with bias), and Multi-value (simple load balancing with health checks). Practice configuring each type and understand how health checks affect traffic routing for automated failover.

4. **Learn VPC Flow Logs analysis systematically** - VPC Flow Logs are essential for troubleshooting network connectivity and security issues. Understand the log format (srcaddr, dstaddr, srcport, dstport, protocol, packets, bytes, action), how to filter logs for specific traffic patterns, and common troubleshooting scenarios (REJECT means security group/NACL denied traffic, NODATA means no traffic attempted). Practice using CloudWatch Logs Insights to query flow logs and identify blocked traffic, unusual patterns, or bandwidth consumption.

5. **Practice cost optimization for network architectures** - Networking costs can be significant, and the exam tests knowledge of cost reduction strategies. Understand that data transfer out to the internet is charged, data transfer between Availability Zones (AZs) costs money, NAT Gateway charges per hour plus data processing, and VPC endpoints eliminate NAT Gateway costs for AWS services. Learn when to use VPC endpoints (save on NAT Gateway costs for S3/DynamoDB), PrivateLink (private connectivity to services), and Direct Connect (reduce data transfer costs for large volumes).

### Recommended Approach

1. **Start with VPC fundamentals and build progressively** - Begin with the VPC User Guide, understanding Classless Inter-Domain Routing (CIDR) blocks, subnets (public versus private), route tables (how routes are evaluated), and internet connectivity (Internet Gateway versus NAT Gateway versus Egress-only Internet Gateway for IPv6). Create a simple VPC with one public subnet and one private subnet, then expand to multi-AZ deployments. Understanding traffic flow through VPC components is essential before moving to advanced topics like Transit Gateway, PrivateLink, and VPC peering.

2. **Deep dive into VPC security controls** - Study security groups thoroughly (default deny, stateful behavior, rule evaluation), then Network ACLs (numbered rules, stateless, explicit deny), and understand when to use each. Practice defense-in-depth security by configuring both security groups (granular instance-level control) and NACLs (subnet-level protection, deny rules). Learn common patterns like database security group allowing only application tier security group, web tier in public subnet with NACL allowing HTTP/HTTPS.

3. **Master hybrid connectivity options** - Study AWS Direct Connect (dedicated fiber connection, consistent performance, reduced costs), Site-to-Site VPN (encrypted tunnel over internet, quick setup), Client VPN (remote user access), and Transit Gateway (hub for connecting VPCs and on-premises). Understand when to use each option based on requirements (latency, bandwidth, security, cost, setup time). Practice troubleshooting hybrid connectivity issues using VPC Flow Logs, CloudWatch metrics, and Direct Connect/VPN logs.

4. **Comprehensive Route 53 and CloudFront study** - Learn Route 53 hosted zones (public versus private), record types (A, AAAA, CNAME, ALIAS), routing policies, and health checks. For CloudFront, understand origins (S3, custom HTTP/HTTPS, ALB), cache behaviors (path patterns, TTL settings), invalidations, and signed URLs/cookies for restricted content. Practice configuring CloudFront distributions with custom origins, implementing caching strategies, and troubleshooting cache misses using CloudFront logs and real-time logs.

5. **Practice systematic network troubleshooting** - Develop a methodical approach to troubleshooting network issues: check security groups (most common issue), verify NACL rules (especially return traffic for stateless), examine route tables (correct route to destination), confirm internet/NAT gateway configuration, analyze VPC Flow Logs (identify REJECT actions), and test connectivity using VPC Reachability Analyzer. Create broken network configurations intentionally and practice diagnosing and fixing them using AWS tools.

---

## Task 5.1: Implement and optimize networking features and connectivity

### Skills & Corresponding Documentation

#### Skill 5.1.1: Configure a VPC (for example, subnets, route tables, network ACLs, security groups, NAT gateways, internet gateway, egress-only internet gateway)

**Why:** VPC configuration is absolutely fundamental to AWS networking and is one of the most heavily tested skills in the SysOps exam. You must understand how to design VPCs with appropriate CIDR blocks (avoiding conflicts with on-premises networks), create public subnets (with internet gateway route) and private subnets (with NAT gateway route), configure route tables (main versus custom, route priority evaluation), implement security groups (stateful, allow rules only, rule evaluation), and configure Network ACLs (stateless, numbered rules, allow and deny). The exam extensively tests traffic flow scenarios requiring you to trace the path from source to destination through security groups, NACLs, route tables, and gateways, and troubleshoot why connectivity fails when components are misconfigured.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/" target="_blank">Amazon VPC User Guide</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html" target="_blank">What Is Amazon VPC?</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/how-it-works.html" target="_blank">How Amazon VPC Works</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/configure-your-vpc.html" target="_blank">VPCs and Subnets</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/subnet-sizing.html" target="_blank">Subnet CIDR Blocks</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html" target="_blank">Route Tables</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Internet_Gateway.html" target="_blank">Internet Gateways</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html" target="_blank">NAT Gateways</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/egress-only-internet-gateway.html" target="_blank">Egress-Only Internet Gateways</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html" target="_blank">Control Traffic to Subnets Using Network ACLs</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/security-groups.html" target="_blank">Control Traffic to Resources Using Security Groups</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/security-group-rules.html" target="_blank">Security Group Rules</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html#nacl-rules" target="_blank">Network ACL Rules</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Security.html#VPC_Security_Comparison" target="_blank">Comparison of Security Groups and Network ACLs</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/privatelink/vpc-endpoints.html" target="_blank">VPC Endpoints</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/vpc-examples-intro.html" target="_blank">Example VPC Configurations</a>

#### Skill 5.1.2: Configure private networking connectivity

**Why:** Private connectivity enables secure communication between VPCs, to on-premises networks, and to AWS services without traversing the public internet. The exam tests your knowledge of VPC peering (private connectivity between VPCs, non-transitive), AWS Transit Gateway (hub-and-spoke architecture, transitive routing, connects VPCs and on-premises), AWS PrivateLink (private access to services, powered by VPC endpoints), Direct Connect (dedicated network connection, consistent performance), and Site-to-Site VPN (encrypted IPsec tunnels over internet). Understanding when to use each option based on requirements (latency, bandwidth, security, cost, complexity, transitive routing needs) and how to configure routing for private connectivity is critical for enterprise AWS architectures and disaster recovery scenarios.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/vpc/latest/peering/" target="_blank">VPC Peering</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/peering/what-is-vpc-peering.html" target="_blank">What Is VPC Peering?</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/peering/vpc-peering-basics.html" target="_blank">VPC Peering Basics</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/peering/vpc-peering-basics.html#vpc-peering-limitations" target="_blank">VPC Peering Limitations</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/tgw/" target="_blank">AWS Transit Gateway</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/tgw/what-is-transit-gateway.html" target="_blank">What Is a Transit Gateway?</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/tgw/how-transit-gateways-work.html" target="_blank">How Transit Gateways Work</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/tgw/tgw-route-tables.html" target="_blank">Transit Gateway Route Tables</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/privatelink/" target="_blank">AWS PrivateLink</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/privatelink/what-is-privatelink.html" target="_blank">What Is AWS PrivateLink?</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/privatelink/endpoint-service.html" target="_blank">VPC Endpoint Services (AWS PrivateLink)</a>
- <a href="https://docs.aws.amazon.com/directconnect/latest/UserGuide/" target="_blank">AWS Direct Connect User Guide</a>
- <a href="https://docs.aws.amazon.com/directconnect/latest/UserGuide/Welcome.html" target="_blank">What Is AWS Direct Connect?</a>
- <a href="https://docs.aws.amazon.com/vpn/latest/s2svpn/" target="_blank">AWS Site-to-Site VPN User Guide</a>
- <a href="https://docs.aws.amazon.com/vpn/latest/s2svpn/VPC_VPN.html" target="_blank">What Is AWS Site-to-Site VPN?</a>
- <a href="https://docs.aws.amazon.com/vpn/latest/s2svpn/VPNRoutingTypes.html" target="_blank">VPN Routing Options</a>
- <a href="https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/" target="_blank">AWS Client VPN</a>

#### Skill 5.1.3: Audit AWS network protection services (for example, Amazon Route 53 Resolver DNS Firewall, AWS WAF, AWS Shield, AWS Network Firewall) in a single account

**Why:** Network protection services defend against threats at different layers and the exam tests your understanding of what each service protects and how to audit their configurations. Route 53 Resolver DNS Firewall blocks DNS queries to known malicious domains, AWS WAF (Web Application Firewall) protects web applications from common exploits (SQL injection, cross-site scripting), AWS Shield protects against Distributed Denial of Service (DDoS) attacks (Standard is automatic and free, Advanced provides enhanced protection and DDoS Response Team support), and AWS Network Firewall provides stateful network filtering at the VPC level. Understanding how to review WAF rules, Shield protections, DNS Firewall domain lists, and Network Firewall rule groups to ensure proper protection and compliance is critical for security operations.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver-dns-firewall.html" target="_blank">Route 53 Resolver DNS Firewall</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver-dns-firewall-getting-started.html" target="_blank">Getting Started with Route 53 Resolver DNS Firewall</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver-dns-firewall-rule-groups.html" target="_blank">Managing Rule Groups and Rules</a>
- <a href="https://docs.aws.amazon.com/waf/latest/developerguide/" target="_blank">AWS WAF Developer Guide</a>
- <a href="https://docs.aws.amazon.com/waf/latest/developerguide/what-is-aws-waf.html" target="_blank">What Is AWS WAF?</a>
- <a href="https://docs.aws.amazon.com/waf/latest/developerguide/web-acl.html" target="_blank">AWS WAF Web ACLs</a>
- <a href="https://docs.aws.amazon.com/waf/latest/developerguide/aws-managed-rule-groups.html" target="_blank">AWS Managed Rules for AWS WAF</a>
- <a href="https://docs.aws.amazon.com/waf/latest/developerguide/logging.html" target="_blank">AWS WAF Logging</a>
- <a href="https://docs.aws.amazon.com/waf/latest/developerguide/shield-chapter.html" target="_blank">AWS Shield</a>
- <a href="https://docs.aws.amazon.com/waf/latest/developerguide/ddos-standard.html" target="_blank">AWS Shield Standard</a>
- <a href="https://docs.aws.amazon.com/waf/latest/developerguide/ddos-advanced.html" target="_blank">AWS Shield Advanced</a>
- <a href="https://docs.aws.amazon.com/network-firewall/latest/developerguide/" target="_blank">AWS Network Firewall Developer Guide</a>
- <a href="https://docs.aws.amazon.com/network-firewall/latest/developerguide/what-is-aws-network-firewall.html" target="_blank">What Is AWS Network Firewall?</a>
- <a href="https://docs.aws.amazon.com/network-firewall/latest/developerguide/rule-groups.html" target="_blank">Network Firewall Rule Groups</a>
- <a href="https://docs.aws.amazon.com/network-firewall/latest/developerguide/firewall-policies.html" target="_blank">Network Firewall Policies</a>

#### Skill 5.1.4: Optimize the cost of network architectures

**Why:** Network costs can be substantial in AWS architectures, and the exam tests your knowledge of cost optimization strategies. Understanding data transfer costs is critical: data transfer IN is free, data transfer OUT to internet is charged, data transfer between AZs costs money, data transfer between regions is expensive, and NAT Gateway charges include both hourly costs and data processing fees. VPC endpoints eliminate NAT Gateway costs for accessing S3 and DynamoDB, PrivateLink reduces data transfer costs for service access, Direct Connect offers lower data transfer rates for large volumes, and CloudFront reduces origin requests through caching. The exam tests scenarios requiring you to recommend cost-optimized architectures while maintaining performance and security requirements.

**AWS Documentation:**
- <a href="https://aws.amazon.com/vpc/pricing/" target="_blank">Amazon VPC Pricing</a>
- <a href="https://aws.amazon.com/ec2/pricing/on-demand/#Data_Transfer" target="_blank">Data Transfer Pricing</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html#nat-gateway-pricing" target="_blank">NAT Gateway Pricing</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/privatelink/gateway-endpoints.html" target="_blank">VPC Endpoints - Gateway Endpoints</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/how-aws-pricing-works/data-transfer.html" target="_blank">Reducing Data Transfer Costs</a>
- <a href="https://aws.amazon.com/directconnect/pricing/" target="_blank">AWS Direct Connect Pricing</a>
- <a href="https://aws.amazon.com/cloudfront/pricing/" target="_blank">CloudFront Pricing</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/cost-optimization-pillar/network.html" target="_blank">Optimizing Network Costs</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/vpc-sharing.html" target="_blank">VPC Sharing</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/cost-optimization-pillar/welcome.html" target="_blank">Cost Optimization Best Practices</a>

---

## Task 5.2: Configure domains, DNS services, and content delivery

### Skills & Corresponding Documentation

#### Skill 5.2.1: Configure DNS (for example, Route 53 Resolver)

**Why:** DNS is critical for name resolution and the exam tests your understanding of how Route 53 Resolver enables DNS resolution between VPCs and on-premises networks. Route 53 Resolver provides DNS resolution for VPCs (queries to public DNS and private hosted zones), inbound endpoints enable on-premises networks to resolve AWS resources via DNS queries, and outbound endpoints enable VPCs to forward DNS queries to on-premises DNS servers using forwarding rules. Understanding conditional forwarding rules (forward specific domains to target resolvers) and system rules (automatic queries for AWS services) helps you implement hybrid DNS architectures for seamless name resolution across hybrid environments.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/" target="_blank">Amazon Route 53 Developer Guide</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/Welcome.html" target="_blank">What Is Amazon Route 53?</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver.html" target="_blank">Route 53 Resolver</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver.html" target="_blank">Resolving DNS Queries Between VPCs and Your Network</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver-getting-started.html" target="_blank">Route 53 Resolver Endpoints</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver-forwarding-inbound-queries.html" target="_blank">Forwarding Inbound DNS Queries to Your VPCs</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver-forwarding-outbound-queries.html" target="_blank">Forwarding Outbound DNS Queries to Your Network</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver-rules-managing.html" target="_blank">Managing Forwarding Rules</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/hosted-zones-private.html" target="_blank">Working with Private Hosted Zones</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/vpc-dns.html" target="_blank">DNS Support in Your VPC</a>

#### Skill 5.2.2: Implement Route 53 routing policies, configurations, and query logging

**Why:** Route 53 routing policies control how DNS queries are answered and are heavily tested through scenarios requiring you to select the appropriate policy for specific requirements. Simple routing (single resource), Weighted routing (distribute traffic by percentage for A/B testing or gradual migrations), Latency-based routing (route to lowest latency endpoint), Failover routing (active-passive disaster recovery with health checks), Geolocation routing (route based on user location for content localization), Geoproximity routing (route based on geographic distance with bias adjustment), and Multi-value answer routing (simple load balancing across multiple resources). Query logging captures all DNS queries for troubleshooting and security analysis, helping you identify unusual DNS patterns or validate routing behavior.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/hosted-zones-working-with.html" target="_blank">Working with Hosted Zones</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/rrsets-working-with.html" target="_blank">Working with Records</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy.html" target="_blank">Choosing a Routing Policy</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy-simple.html" target="_blank">Simple Routing</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy-weighted.html" target="_blank">Weighted Routing</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy-latency.html" target="_blank">Latency-Based Routing</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy-failover.html" target="_blank">Failover Routing</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy-geo.html" target="_blank">Geolocation Routing</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy-geoproximity.html" target="_blank">Geoproximity Routing</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy-multivalue.html" target="_blank">Multivalue Answer Routing</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/health-checks-creating.html" target="_blank">Creating Health Checks</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/welcome-health-checks.html" target="_blank">How Health Checks Work</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/query-logs.html" target="_blank">Query Logging</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/monitoring-cloudwatch.html" target="_blank">Monitoring Route 53 with Amazon CloudWatch</a>

#### Skill 5.2.3: Configure content and service distribution (for example, Amazon CloudFront, AWS Global Accelerator)

**Why:** Content delivery networks and global acceleration services improve application performance for distributed users and are tested through configuration and optimization scenarios. CloudFront is a CDN that caches content at edge locations worldwide, supports multiple origin types (S3, custom HTTP/HTTPS, ALB, API Gateway), uses cache behaviors to control caching for different URL patterns, and implements Time To Live (TTL) settings to balance freshness with cache hit ratio. AWS Global Accelerator improves availability and performance using the AWS global network with static anycast IP addresses that route to optimal endpoints based on health and proximity. Understanding when to use CloudFront (cacheable HTTP/HTTPS content) versus Global Accelerator (non-HTTP/UDP/TCP applications, static IPs, instant regional failover) helps you optimize application delivery.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/" target="_blank">Amazon CloudFront Developer Guide</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html" target="_blank">What Is Amazon CloudFront?</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/HowCloudFrontWorks.html" target="_blank">How CloudFront Delivers Content</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/distribution-web-creating.html" target="_blank">Creating a Distribution</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/DownloadDistS3AndCustomOrigins.html" target="_blank">Working with Origins</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/distribution-web-values-specify.html#DownloadDistValuesCacheBehavior" target="_blank">Cache Behaviors</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Expiration.html" target="_blank">Managing How Long Content Stays in Cache</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Invalidation.html" target="_blank">Invalidating Files</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/high_availability_origin_failover.html" target="_blank">Using Origin Failover</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/AccessLogs.html" target="_blank">CloudFront Access Logs</a>
- <a href="https://docs.aws.amazon.com/global-accelerator/latest/dg/" target="_blank">AWS Global Accelerator Developer Guide</a>
- <a href="https://docs.aws.amazon.com/global-accelerator/latest/dg/what-is-global-accelerator.html" target="_blank">What Is AWS Global Accelerator?</a>
- <a href="https://docs.aws.amazon.com/global-accelerator/latest/dg/introduction-how-it-works.html" target="_blank">How AWS Global Accelerator Works</a>
- <a href="https://docs.aws.amazon.com/global-accelerator/latest/dg/about-accelerators.html" target="_blank">Standard Accelerators in AWS Global Accelerator</a>
- <a href="https://docs.aws.amazon.com/global-accelerator/latest/dg/about-endpoints.html" target="_blank">Endpoints for Standard Accelerators</a>

---

## Task 5.3: Troubleshoot network connectivity issues

### Skills & Corresponding Documentation

#### Skill 5.3.1: Troubleshoot VPC configurations (for example, subnets, route tables, network ACLs, security groups, transit gateways, NAT gateways)

**Why:** Network troubleshooting is one of the most tested skills because connectivity issues are common operational problems. The exam presents scenarios with connectivity failures requiring you to systematically diagnose the issue: verify security group rules (most common issue, stateful), check NACL rules (especially return traffic, stateless), examine route tables (correct route exists, most specific route wins), confirm gateway configuration (internet gateway, NAT gateway, transit gateway attachment), and validate subnet associations. Understanding the troubleshooting methodology (test each layer, use VPC Reachability Analyzer, check VPC Flow Logs for REJECT actions) and common misconfigurations (security group missing return rule, NACL blocking ephemeral ports, route table missing default route) is essential for operational efficiency.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/troubleshooting.html" target="_blank">Troubleshoot VPC Connectivity</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/reachability/" target="_blank">VPC Reachability Analyzer</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/reachability/getting-started.html" target="_blank">Getting Started with Reachability Analyzer</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/security-groups-troubleshooting.html" target="_blank">Troubleshoot Security Groups</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html#nacl-troubleshooting" target="_blank">Troubleshoot Network ACLs</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/nat-gateway-troubleshooting.html" target="_blank">Troubleshoot NAT Gateways</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Internet_Gateway.html#IGWTroubleshooting" target="_blank">Troubleshoot Internet Gateway</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/peering/vpc-peering-troubleshooting.html" target="_blank">Troubleshoot VPC Peering</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/tgw/transit-gateway-troubleshooting.html" target="_blank">Troubleshoot Transit Gateway</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Testing.html" target="_blank">Test VPC Network Connectivity</a>

#### Skill 5.3.2: Collect and interpret networking logs to troubleshoot issues (for example, VPC flow logs, Elastic Load Balancing [ELB] access logs, AWS WAF web ACL logs, CloudFront logs, container logs)

**Why:** Network logs provide detailed information about traffic patterns, security events, and connectivity issues, and the exam tests your ability to analyze logs for troubleshooting. VPC Flow Logs capture IP traffic going to and from network interfaces (identify rejected traffic, unusual patterns, bandwidth consumption), ELB access logs record all requests (troubleshoot application errors, analyze traffic patterns), WAF logs show inspected requests and rule matches (identify attack patterns, tune rules), and CloudFront logs detail viewer requests (optimize caching, identify popular content). Understanding log format, how to query logs efficiently using CloudWatch Logs Insights or Amazon Athena, and recognizing common patterns in logs (REJECT actions, error codes, cache misses) is critical for operational troubleshooting and security analysis.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html" target="_blank">VPC Flow Logs</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs-working-with.html" target="_blank">Working with Flow Logs</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs-records.html" target="_blank">Flow Log Records</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs-athena.html" target="_blank">Query Flow Logs Using Amazon Athena</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs-cwl-insights.html" target="_blank">Analyzing Flow Logs with CloudWatch Logs Insights</a>
- <a href="https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-access-logs.html" target="_blank">Access Logs for Application Load Balancers</a>
- <a href="https://docs.aws.amazon.com/elasticloadbalancing/latest/network/load-balancer-access-logs.html" target="_blank">Access Logs for Network Load Balancers</a>
- <a href="https://docs.aws.amazon.com/waf/latest/developerguide/logging.html" target="_blank">Logging Web ACL Traffic Information</a>
- <a href="https://docs.aws.amazon.com/waf/latest/developerguide/logging-examples.html" target="_blank">Analyzing AWS WAF Logs</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/AccessLogs.html" target="_blank">CloudFront Standard Logs</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/real-time-logs.html" target="_blank">CloudFront Real-Time Logs</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/analyzing-logs.html" target="_blank">Analyzing CloudFront Logs</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/ContainerInsights.html" target="_blank">Container Insights for Amazon ECS</a>

#### Skill 5.3.3: Identify and remediate CloudFront caching issues

**Why:** CloudFront caching issues cause performance problems and increased origin costs, and the exam tests troubleshooting scenarios. Common issues include low cache hit ratio (objects not cacheable, TTLs too short, query strings causing unique cache keys), stale content (TTL too long, invalidations not working), and origin overload (cache not working, all requests going to origin). Understanding cache behaviors (path patterns, TTL settings, query string handling), cache statistics (cache hit ratio from CloudWatch metrics), when to use invalidations versus versioned file names, and how cache keys affect caching (headers, cookies, query strings) helps you optimize CloudFront performance and reduce costs by maximizing cache efficiency.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/ConfiguringCaching.html" target="_blank">Optimizing Caching and Availability</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Expiration.html" target="_blank">Managing How Long Content Stays in Cache</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Invalidation.html" target="_blank">Invalidating Files</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/cache-hit-ratio.html" target="_blank">Increasing the Proportion of Requests Served from CloudFront Edge Caches</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/understanding-the-cache-key.html" target="_blank">Understanding the Cache Key</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/reports-billing.html" target="_blank">CloudFront Reports in the Console</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/monitoring-using-cloudwatch.html" target="_blank">Monitoring CloudFront with Amazon CloudWatch</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/troubleshooting-response-errors.html" target="_blank">Troubleshooting CloudFront Error Responses</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Troubleshooting.html" target="_blank">Troubleshooting CloudFront Distribution Issues</a>

#### Skill 5.3.4: Identify and troubleshoot hybrid connectivity issues and private connectivity issues

**Why:** Hybrid connectivity issues affect business operations when on-premises networks cannot communicate with AWS, and the exam tests troubleshooting methodologies. For Direct Connect, common issues include physical connection problems (check port status), Virtual Interface (VIF) configuration errors (VLAN, Border Gateway Protocol (BGP) peering), and routing problems (BGP advertisements, prefix limits). For Site-to-Site VPN, issues include tunnel status (both tunnels down versus one down), IPsec parameters mismatch (phase 1/2 settings), routing configuration (static versus BGP), and firewall blocking (UDP 500, 4500). Understanding how to use Direct Connect alarms, VPN tunnel metrics, and BGP routing tables to diagnose connectivity failures helps you maintain reliable hybrid architectures.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/directconnect/latest/UserGuide/Troubleshooting.html" target="_blank">Troubleshooting AWS Direct Connect</a>
- <a href="https://docs.aws.amazon.com/directconnect/latest/UserGuide/WorkingWithVirtualInterfaces.html" target="_blank">Direct Connect Virtual Interfaces</a>
- <a href="https://docs.aws.amazon.com/directconnect/latest/UserGuide/monitoring-cloudwatch.html" target="_blank">Direct Connect Alarms</a>
- <a href="https://docs.aws.amazon.com/vpn/latest/s2svpn/Troubleshooting.html" target="_blank">Troubleshooting AWS Site-to-Site VPN</a>
- <a href="https://docs.aws.amazon.com/vpn/latest/s2svpn/VPNTunnels.html" target="_blank">VPN Tunnel Status</a>
- <a href="https://docs.aws.amazon.com/vpn/latest/s2svpn/HowToTestEndToEnd_Linux.html" target="_blank">Testing the VPN Connection</a>
- <a href="https://docs.aws.amazon.com/vpn/latest/s2svpn/monitoring-cloudwatch-vpn.html" target="_blank">Site-to-Site VPN CloudWatch Metrics</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/peering/vpc-peering-troubleshooting.html" target="_blank">Troubleshooting VPC Peering</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/tgw/transit-gateway-troubleshooting.html" target="_blank">Troubleshooting Transit Gateway</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/privatelink/troubleshooting.html" target="_blank">Troubleshooting PrivateLink</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Testing.html" target="_blank">Network Connectivity Testing</a>

#### Skill 5.3.5: Configure and analyze Amazon CloudWatch network monitoring services

**Why:** CloudWatch provides network metrics and alarms essential for proactive monitoring and troubleshooting, and the exam tests your ability to configure meaningful monitoring. Network metrics include VPC Flow Logs metrics (rejected packets, bytes), NAT Gateway metrics (connections, bytes processed, error ports), VPN tunnel metrics (tunnel state, data in/out), Direct Connect metrics (connection state, bits in/out), and load balancer metrics (active connections, request count, target response time). Understanding how to create CloudWatch alarms for network issues (VPN tunnel down, NAT Gateway errors, Direct Connect connection state), analyze metrics trends to identify capacity issues, and correlate metrics with application performance helps you maintain reliable network operations and optimize capacity planning.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/monitoring-cloudwatch.html" target="_blank">Monitoring Your VPC Using CloudWatch</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway-cloudwatch.html" target="_blank">Monitoring NAT Gateways Using CloudWatch</a>
- <a href="https://docs.aws.amazon.com/vpn/latest/s2svpn/monitoring-cloudwatch-vpn.html" target="_blank">CloudWatch Metrics for Your VPN Connection</a>
- <a href="https://docs.aws.amazon.com/directconnect/latest/UserGuide/monitoring-cloudwatch.html" target="_blank">Monitoring AWS Direct Connect with CloudWatch</a>
- <a href="https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-cloudwatch-metrics.html" target="_blank">CloudWatch Metrics for Application Load Balancers</a>
- <a href="https://docs.aws.amazon.com/elasticloadbalancing/latest/network/load-balancer-cloudwatch-metrics.html" target="_blank">CloudWatch Metrics for Network Load Balancers</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html" target="_blank">Creating CloudWatch Alarms</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch_Dashboards.html" target="_blank">Using Amazon CloudWatch Dashboards</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/monitoring-network-performance-ena.html" target="_blank">Network Performance Metrics</a>

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/vpc/faqs/" target="_blank">Amazon VPC FAQs</a>
- <a href="https://aws.amazon.com/route53/faqs/" target="_blank">Amazon Route 53 FAQs</a>
- <a href="https://aws.amazon.com/cloudfront/faqs/" target="_blank">Amazon CloudFront FAQs</a>
- <a href="https://aws.amazon.com/directconnect/faqs/" target="_blank">AWS Direct Connect FAQs</a>
- <a href="https://aws.amazon.com/vpn/faqs/" target="_blank">AWS Site-to-Site VPN FAQs</a>
- <a href="https://aws.amazon.com/transit-gateway/faqs/" target="_blank">AWS Transit Gateway FAQs</a>
- <a href="https://aws.amazon.com/privatelink/faqs/" target="_blank">AWS PrivateLink FAQs</a>
- <a href="https://aws.amazon.com/global-accelerator/faqs/" target="_blank">AWS Global Accelerator FAQs</a>
- <a href="https://aws.amazon.com/waf/faqs/" target="_blank">AWS WAF FAQs</a>
- <a href="https://aws.amazon.com/shield/faqs/" target="_blank">AWS Shield FAQs</a>
- <a href="https://aws.amazon.com/network-firewall/faqs/" target="_blank">AWS Network Firewall FAQs</a>
- <a href="https://aws.amazon.com/elasticloadbalancing/faqs/" target="_blank">Elastic Load Balancing FAQs</a>

---

## AWS Whitepapers

- <a href="https://docs.aws.amazon.com/wellarchitected/latest/framework/networking.html" target="_blank">AWS Networking Best Practices</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/building-scalable-secure-multi-vpc-network-infrastructure/welcome.html" target="_blank">Building a Scalable and Secure Multi-VPC AWS Network Infrastructure</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/hybrid-cloud-architecture-for-government/welcome.html" target="_blank">Hybrid Cloud Architecture for Government</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/aws-vpc-connectivity-options/welcome.html" target="_blank">Amazon VPC Connectivity Options</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/how-aws-pricing-works/welcome.html" target="_blank">How AWS Pricing Works</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/performance-efficiency-pillar/welcome.html" target="_blank">Performance Efficiency Pillar - AWS Well-Architected Framework</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/aws-best-practices-ddos-resiliency/welcome.html" target="_blank">AWS Best Practices for DDoS Resiliency</a>

---

## Final Thoughts

Domain 5 combines foundational networking knowledge with AWS-specific implementation and troubleshooting skills essential for every SysOps administrator. VPC configuration and troubleshooting skills are absolutely critical - practice building VPCs from scratch, implementing security controls at multiple layers, and systematically diagnosing connectivity issues using VPC Flow Logs and Reachability Analyzer. Route 53 routing policies and CloudFront caching optimization are heavily tested, so ensure you understand when to use each routing policy and how to maximize cache efficiency. The ability to troubleshoot hybrid connectivity (Direct Connect, VPN) and optimize network costs (VPC endpoints, data transfer patterns) distinguishes experienced SysOps administrators. Master the networking troubleshooting methodology, learn to interpret network logs efficiently, and practice with real scenarios to build the systematic problem-solving skills that the exam and real-world operations demand.
