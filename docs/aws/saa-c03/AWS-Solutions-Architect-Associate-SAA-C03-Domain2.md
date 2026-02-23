# AWS Certified Solutions Architect Associate (SAA-C03) Domain 2
## Design Resilient Architectures

**Official Exam Guide:** <a href="https://aws.amazon.com/certification/certified-solutions-architect-associate/" target="_blank">SAA-C03 Exam Guide</a>

---

## Domain Overview

**Domain Weight:** 26% of the exam

This domain tests your ability to design scalable, decoupled, and highly available architectures.

---

## Task 2.1: Design scalable and loosely coupled architectures

### Elastic Load Balancing (ELB)

#### Load Balancer Types

**Application Load Balancer (ALB):**
- Layer 7 (HTTP/HTTPS)
- Path-based and host-based routing
- Target: EC2, containers, Lambda, IP addresses
- Use case: Web applications, microservices

**Network Load Balancer (NLB):**
- Layer 4 (TCP/UDP)
- Ultra-low latency, high throughput
- Static IP addresses
- Use case: Gaming, IoT, real-time applications

**Gateway Load Balancer (GWLB):**
- Layer 3 (IP packets)
- Deploy third-party appliances
- Use case: Firewalls, IDS/IPS

**Classic Load Balancer:**
- Legacy (avoid for new applications)

**Key Features:**
- Health checks
- Cross-zone load balancing
- SSL/TLS termination
- Sticky sessions (ALB/CLB)
- Connection draining

**AWS Documentation:**
- <a href="https://aws.amazon.com/elasticloadbalancing/" target="_blank">Elastic Load Balancing</a>

### Auto Scaling

#### EC2 Auto Scaling

**Components:**
- **Launch Template** - EC2 configuration
- **Auto Scaling Group** - Manages instances
- **Scaling Policies** - When to scale

**Scaling Types:**
- **Target Tracking** - Maintain metric at target (e.g., CPU 50%)
- **Step Scaling** - Scale based on CloudWatch alarms
- **Simple Scaling** - Add/remove fixed number
- **Scheduled Scaling** - Scale at specific times
- **Predictive Scaling** - ML-based forecasting

**Best Practices:**
- Use multiple AZs
- Health checks from ELB and EC2
- Scale out early, scale in slowly
- Use lifecycle hooks for graceful shutdown

**AWS Documentation:**
- <a href="https://aws.amazon.com/ec2/autoscaling/" target="_blank">EC2 Auto Scaling</a>

### Decoupling

#### Amazon SQS (Simple Queue Service)

**Key Concepts:**
- **Standard Queue** - At-least-once delivery, best effort ordering
- **FIFO Queue** - Exactly-once delivery, strict ordering
- **Dead Letter Queue** - Handle failed messages
- **Visibility Timeout** - Message processing time
- **Long Polling** - Reduce API calls

**Use Cases:**
- Decouple microservices
- Buffer requests
- Batch processing
- Async communication

**AWS Documentation:**
- <a href="https://aws.amazon.com/sqs/" target="_blank">Amazon SQS</a>

#### Amazon SNS (Simple Notification Service)

**Key Concepts:**
- Pub/Sub messaging
- Fan-out pattern
- Multiple subscribers (SQS, Lambda, email, HTTP)
- Message filtering

**Use Cases:**
- Application alerts
- Push notifications
- Fan-out to multiple queues
- Event-driven architectures

**AWS Documentation:**
- <a href="https://aws.amazon.com/sns/" target="_blank">Amazon SNS</a>

#### AWS Step Functions

**Key Features:**
- Orchestrate workflows
- Visual workflow designer
- Error handling and retries
- State machines

**Use Cases:**
- Complex workflows
- ETL pipelines
- Order processing

**AWS Documentation:**
- <a href="https://aws.amazon.com/step-functions/" target="_blank">AWS Step Functions</a>

### Caching

#### Amazon ElastiCache

**Engines:**
- **Redis** - Advanced features (persistence, pub/sub, replication)
- **Memcached** - Simple, multi-threaded

**Use Cases:**
- Database query caching
- Session storage
- Real-time analytics
- Leaderboards (Redis sorted sets)

**Best Practices:**
- Use for read-heavy workloads
- Cache frequently accessed data
- Set appropriate TTL
- Use Redis for persistence requirements

**AWS Documentation:**
- <a href="https://aws.amazon.com/elasticache/" target="_blank">Amazon ElastiCache</a>

#### Amazon CloudFront

**Key Features:**
- Global CDN
- Edge caching
- SSL/TLS termination
- Lambda@Edge for customization
- Origin failover

**Use Cases:**
- Static content delivery
- Video streaming
- API acceleration
- Dynamic content

**AWS Documentation:**
- <a href="https://aws.amazon.com/cloudfront/" target="_blank">Amazon CloudFront</a>

---

## Task 2.2: Design highly available and fault-tolerant architectures

### Multi-AZ Deployments

#### RDS Multi-AZ

**Key Features:**
- Synchronous replication
- Automatic failover (1-2 minutes)
- Same endpoint after failover
- For high availability, not read scaling

**Use Cases:**
- Production databases
- Applications requiring HA
- Disaster recovery

**AWS Documentation:**
- <a href="https://aws.amazon.com/rds/features/multi-az/" target="_blank">RDS Multi-AZ</a>

#### Aurora Multi-AZ

**Features:**
- 6 copies across 3 AZs
- Self-healing storage
- Fast failover (30 seconds)
- Read replicas (up to 15)

**AWS Documentation:**
- <a href="https://aws.amazon.com/rds/aurora/" target="_blank">Amazon Aurora</a>

### Disaster Recovery

#### Strategies (RTO/RPO order)

**Backup and Restore:**
- Lowest cost
- Highest RTO/RPO
- Use case: Non-critical workloads

**Pilot Light:**
- Core infrastructure always running
- Scale up during disaster
- Moderate cost and RTO

**Warm Standby:**
- Scaled-down copy running
- Quick scale-up
- Higher cost, lower RTO

**Multi-Site Active/Active:**
- Full production in multiple regions
- Highest cost, lowest RTO/RPO
- Zero downtime failover

**AWS Documentation:**
- <a href="https://aws.amazon.com/disaster-recovery/" target="_blank">Disaster Recovery</a>

### High Availability Patterns

#### Multi-Region Architectures

**Route 53 Routing Policies:**
- **Failover** - Primary/secondary
- **Geolocation** - Route by user location
- **Geoproximity** - Route by geographic distance
- **Latency** - Route to lowest latency
- **Weighted** - Distribute traffic by weight
- **Multi-value** - Return multiple healthy targets

**Global Services:**
- CloudFront
- Route 53
- IAM
- WAF

**Regional Services:**
- Most AWS services (EC2, RDS, etc.)
- Need to replicate across regions

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy.html" target="_blank">Route 53 Routing Policies</a>

#### AWS Global Accelerator

**Key Features:**
- Static anycast IPs
- Intelligent routing
- Health checks and failover
- DDoS protection

**vs CloudFront:**
- Global Accelerator: TCP/UDP applications
- CloudFront: Cacheable HTTP/HTTPS content

**AWS Documentation:**
- <a href="https://aws.amazon.com/global-accelerator/" target="_blank">AWS Global Accelerator</a>

---

## Storage Resilience

### S3 Storage Classes

**Durability and Availability:**
- **S3 Standard** - 99.999999999% durability, 99.99% availability
- **S3 Intelligent-Tiering** - Auto-tiering based on access
- **S3 Standard-IA** - Infrequent access
- **S3 One Zone-IA** - Single AZ (lower availability)
- **S3 Glacier** - Archive storage
- **S3 Glacier Deep Archive** - Lowest cost archive

**Resilience Features:**
- Versioning
- Replication (CRR, SRR)
- Object Lock
- Lifecycle policies

**AWS Documentation:**
- <a href="https://aws.amazon.com/s3/storage-classes/" target="_blank">S3 Storage Classes</a>

### EBS Snapshots

**Key Features:**
- Incremental backups
- Stored in S3 (regional)
- Copy across regions
- Encrypted snapshots

**Best Practices:**
- Regular automated snapshots
- Copy critical snapshots to another region
- Test restore procedures

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSSnapshots.html" target="_blank">EBS Snapshots</a>

### EFS Resilience

**Key Features:**
- Automatically replicated across multiple AZs
- No capacity planning
- Highly available and durable
- Supports One Zone storage class

**AWS Documentation:**
- <a href="https://aws.amazon.com/efs/" target="_blank">Amazon EFS</a>

---

## Serverless Architectures

### AWS Lambda

**Key Features:**
- Event-driven execution
- Auto-scaling
- Pay per request
- Multiple runtime support

**Best Practices:**
- Use environment variables
- Separate handler from business logic
- Optimize package size
- Set appropriate memory and timeout
- Use Dead Letter Queues

**Integration:**
- API Gateway (RESTful APIs)
- EventBridge (scheduled events)
- S3 (object events)
- DynamoDB Streams
- SQS/SNS

**AWS Documentation:**
- <a href="https://aws.amazon.com/lambda/" target="_blank">AWS Lambda</a>

### Amazon API Gateway

**Key Features:**
- RESTful and WebSocket APIs
- Throttling and rate limiting
- Caching
- CORS support
- Authentication (IAM, Cognito, Lambda authorizers)

**Integration Types:**
- Lambda proxy
- HTTP proxy
- AWS service integration

**AWS Documentation:**
- <a href="https://aws.amazon.com/api-gateway/" target="_blank">Amazon API Gateway</a>

---

## Exam Tips

**Common Patterns:**

1. **High availability** → Multi-AZ deployments
2. **Decouple components** → SQS between tiers
3. **Distribute traffic** → ELB + Auto Scaling
4. **Cache frequently accessed data** → ElastiCache or CloudFront
5. **Disaster recovery** → Backup, Pilot Light, Warm Standby, or Multi-Site
6. **Lowest latency** → Route 53 latency-based routing
7. **Fan-out messaging** → SNS to multiple SQS queues

**Key Concepts:**
- Multi-AZ vs Multi-Region
- RTO (Recovery Time Objective) vs RPO (Recovery Point Objective)
- Stateless applications (easier to scale)
- Loose coupling (SQS/SNS between components)
- Auto Scaling for elasticity

---

## Final Thoughts

Domain 2 (Design Resilient Architectures) is **26% of the exam**.

**Master these services:**
1. ELB (ALB, NLB) + Auto Scaling
2. SQS + SNS for decoupling
3. RDS Multi-AZ and read replicas
4. Route 53 routing policies
5. Disaster recovery strategies
6. Lambda + API Gateway (serverless)

Resilience = High Availability + Fault Tolerance + Disaster Recovery!
