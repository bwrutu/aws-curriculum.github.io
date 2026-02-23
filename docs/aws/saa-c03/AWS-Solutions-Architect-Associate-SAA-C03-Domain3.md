# AWS Certified Solutions Architect Associate (SAA-C03) Domain 3
## Design High-Performing Architectures

**Official Exam Guide:** <a href="https://aws.amazon.com/certification/certified-solutions-architect-associate/" target="_blank">SAA-C03 Exam Guide</a>

---

## Domain Overview

**Domain Weight:** 24% of the exam

This domain tests your ability to design high-performing storage, compute, database, and networking solutions.

---

## Task 3.1: Determine high-performing storage solutions

### Storage Types Comparison

**Storage Type Selection:**

| Use Case | Storage Type | Service |
|----------|-------------|---------|
| Object storage | S3 | S3, Glacier |
| Block storage | EBS | EBS volumes |
| File storage | EFS/FSx | EFS, FSx |
| Archive | Glacier | S3 Glacier |
| Temporary | Instance Store | EC2 instance store |

### Amazon S3 Performance

**S3 Performance Optimization:**
- **Multipart Upload** - Files >100MB (required >5GB)
- **Transfer Acceleration** - Edge locations for faster uploads
- **Byte-Range Fetches** - Parallel downloads
- **S3 Select** - Query data in place (reduce transfer)

**Request Rate:**
- 3,500 PUT/COPY/POST/DELETE per prefix per second
- 5,500 GET/HEAD per prefix per second
- Use prefixes to scale

**Best Practices:**
- Randomize key names for high request rates
- Use CloudFront for read-heavy workloads
- Enable Transfer Acceleration for global uploads
- Use multipart for large files

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/optimizing-performance.html" target="_blank">S3 Performance Optimization</a>

### Amazon EBS Performance

**Volume Types:**

**SSD-based:**
- **gp3** - General purpose, 16,000 IOPS, 1,000 MB/s
- **gp2** - General purpose, bursts to 3,000 IOPS
- **io2/io1** - Provisioned IOPS, up to 64,000 IOPS
- **io2 Block Express** - Up to 256,000 IOPS

**HDD-based:**
- **st1** - Throughput optimized, 500 MB/s
- **sc1** - Cold HDD, 250 MB/s

**Selection Criteria:**
- Databases, boot volumes → gp3 or io2
- High IOPS requirements → io2
- Big data, data warehouses → st1
- Infrequent access → sc1

**EBS Optimization:**
- Enable EBS-optimized instances
- Use RAID 0 for increased IOPS
- Snapshots don't impact performance

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html" target="_blank">EBS Volume Types</a>

### Amazon EFS Performance

**Performance Modes:**
- **General Purpose** - Low latency (most use cases)
- **Max I/O** - High aggregate throughput (big data)

**Throughput Modes:**
- **Bursting** - Scales with size
- **Provisioned** - Fixed throughput regardless of size
- **Elastic** - Auto-scales (recommended)

**Storage Classes:**
- **Standard** - Frequently accessed
- **Infrequent Access (IA)** - Lower cost for less accessed files

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/efs/latest/ug/performance.html" target="_blank">EFS Performance</a>

### FSx Family

**FSx for Windows File Server:**
- Native Windows file system
- SMB protocol
- Active Directory integration
- Use case: Windows applications

**FSx for Lustre:**
- High-performance computing (HPC)
- Machine learning workloads
- Sub-millisecond latencies
- Integrates with S3

**FSx for NetApp ONTAP:**
- NetApp features on AWS
- Multi-protocol (NFS, SMB, iSCSI)

**FSx for OpenZFS:**
- OpenZFS file system
- NFS protocol

**AWS Documentation:**
- <a href="https://aws.amazon.com/fsx/" target="_blank">Amazon FSx</a>

---

## Task 3.2: Design high-performing compute solutions

### EC2 Instance Types

**Instance Families:**

**General Purpose (T, M):**
- Balanced compute, memory, networking
- Use case: Web servers, small databases

**Compute Optimized (C):**
- High-performance processors
- Use case: Batch processing, gaming, HPC

**Memory Optimized (R, X, z):**
- Large memory
- Use case: In-memory databases, big data

**Storage Optimized (I, D, H):**
- High sequential read/write
- Use case: NoSQL databases, data warehousing

**Accelerated Computing (P, G, F, Inf):**
- GPU, FPGA
- Use case: ML, graphics rendering

**AWS Documentation:**
- <a href="https://aws.amazon.com/ec2/instance-types/" target="_blank">EC2 Instance Types</a>

### EC2 Placement Groups

**Cluster:**
- Low latency, high throughput
- Same AZ
- Use case: HPC, tightly coupled applications

**Spread:**
- Each instance on different hardware
- Up to 7 instances per AZ
- Use case: Critical instances

**Partition:**
- Groups of instances on separate partitions
- Use case: Hadoop, Cassandra, Kafka

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html" target="_blank">Placement Groups</a>

### Container Services

**Amazon ECS:**
- AWS-native container orchestration
- EC2 or Fargate launch types
- Use case: Docker containers on AWS

**Amazon EKS:**
- Managed Kubernetes
- Use case: Kubernetes workloads

**AWS Fargate:**
- Serverless compute for containers
- No EC2 management
- Use case: Simplified container deployment

**AWS Documentation:**
- <a href="https://aws.amazon.com/ecs/" target="_blank">Amazon ECS</a>
- <a href="https://aws.amazon.com/eks/" target="_blank">Amazon EKS</a>

---

## Task 3.3: Determine high-performing database solutions

### Database Selection

**Database Types:**

**Relational (SQL):**
- **RDS** - Managed MySQL, PostgreSQL, Oracle, SQL Server, MariaDB
- **Aurora** - AWS high-performance database
- Use case: ACID transactions, structured data

**NoSQL:**
- **DynamoDB** - Key-value, document store
- **DocumentDB** - MongoDB-compatible
- **Neptune** - Graph database
- Use case: High scale, flexible schema

**In-Memory:**
- **ElastiCache** - Redis, Memcached
- Use case: Caching, session storage

**Data Warehouse:**
- **Redshift** - Petabyte-scale analytics
- Use case: BI, analytics

**Time-Series:**
- **Timestream** - Time-series data
- Use case: IoT, monitoring

### RDS Performance

**Read Replicas:**
- Asynchronous replication
- Up to 15 replicas (Aurora)
- Cross-region support
- Read scaling, not HA

**Performance Optimization:**
- Use appropriate instance type
- Provision adequate IOPS
- Enable Performance Insights
- Use read replicas for read-heavy workloads
- Cache frequently accessed data

**Aurora Performance:**
- 5x faster than MySQL
- 3x faster than PostgreSQL
- Auto-scaling storage
- Fast cloning
- Aurora Serverless for variable workloads

**AWS Documentation:**
- <a href="https://aws.amazon.com/rds/features/read-replicas/" target="_blank">RDS Read Replicas</a>
- <a href="https://aws.amazon.com/rds/aurora/" target="_blank">Amazon Aurora</a>

### DynamoDB Performance

**Performance Features:**
- Single-digit millisecond latency
- Auto-scaling
- DynamoDB Accelerator (DAX) - microsecond caching
- Global Tables - multi-region replication
- On-demand pricing - no capacity planning

**Optimization:**
- Use partition keys wisely
- Avoid hot partitions
- Use DAX for read-heavy workloads
- Use Global Secondary Indexes (GSI) for query flexibility

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/best-practices.html" target="_blank">DynamoDB Performance</a>

### Redshift Performance

**Performance Features:**
- Columnar storage
- Data compression
- Massively parallel processing (MPP)
- Result caching

**Optimization:**
- Distribution styles (KEY, ALL, EVEN)
- Sort keys for query performance
- Vacuum and analyze regularly
- Concurrency scaling

**AWS Documentation:**
- <a href="https://aws.amazon.com/redshift/" target="_blank">Amazon Redshift</a>

---

## Task 3.4: Determine high-performing networking solutions

### VPC Design

**Subnet Design:**
- Public subnets (internet-facing resources)
- Private subnets (internal resources)
- Use all available AZs
- Plan CIDR blocks for growth

**NAT Gateway:**
- Managed NAT service
- High availability (AZ-level)
- Better than NAT instance
- Place in public subnet

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Scenario2.html" target="_blank">VPC Design</a>

### Connectivity Options

**AWS Direct Connect:**
- Dedicated network connection
- Consistent network performance
- Lower latency than internet
- Use case: Hybrid cloud, large data transfers

**VPN:**
- Encrypted connection over internet
- Quick to set up
- Lower cost than Direct Connect
- Use case: Backup connectivity, temporary needs

**Transit Gateway:**
- Hub-and-spoke network topology
- Connect VPCs and on-premises
- Simplifies complex network architectures

**AWS Documentation:**
- <a href="https://aws.amazon.com/directconnect/" target="_blank">AWS Direct Connect</a>
- <a href="https://aws.amazon.com/transit-gateway/" target="_blank">AWS Transit Gateway</a>

### Content Delivery

**CloudFront:**
- Global CDN
- Edge caching
- Reduces origin load
- SSL/TLS termination
- Lambda@Edge for customization

**Global Accelerator:**
- Static anycast IPs
- Intelligent routing
- For non-HTTP/HTTPS (TCP/UDP)
- Health checks and failover

**AWS Documentation:**
- <a href="https://aws.amazon.com/cloudfront/" target="_blank">Amazon CloudFront</a>

### Enhanced Networking

**Placement Groups:**
- Cluster placement for low latency
- Enhanced networking (SR-IOV)
- Up to 100 Gbps

**Elastic Fabric Adapter (EFA):**
- Network interface for HPC
- OS-bypass for lower latency
- Use case: MPI applications, ML training

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/enhanced-networking.html" target="_blank">Enhanced Networking</a>

---

## Exam Tips

**Common Patterns:**

1. **High IOPS database** → io2 EBS or Aurora
2. **Cache layer** → ElastiCache (Redis/Memcached)
3. **Static content delivery** → CloudFront + S3
4. **Read-heavy database** → RDS read replicas
5. **Low latency between instances** → Cluster placement group
6. **Large file uploads** → S3 multipart upload
7. **Global users** → CloudFront or Global Accelerator
8. **HPC workloads** → Cluster placement + EFA

**Performance Principles:**
- Right-size instances and storage
- Use caching liberally
- Scale horizontally when possible
- Use managed services for auto-scaling
- Leverage edge locations (CloudFront)

---

## Final Thoughts

Domain 3 (Design High-Performing Architectures) is **24% of the exam**.

**Master these concepts:**
1. Storage types and when to use each
2. EBS volume types (gp3, io2, st1)
3. EC2 instance types and placement groups
4. Database selection (RDS, DynamoDB, Redshift)
5. CloudFront for content delivery
6. ElastiCache for caching
7. RDS read replicas vs Multi-AZ

Performance = Right Service + Right Configuration + Caching + Scaling!
