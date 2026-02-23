# AWS Certified Solutions Architect Associate (SAA-C03) Domain 4
## Design Cost-Optimized Architectures

**Official Exam Guide:** <a href="https://aws.amazon.com/certification/certified-solutions-architect-associate/" target="_blank">SAA-C03 Exam Guide</a>

---

## Domain Overview

**Domain Weight:** 20% of the exam

This domain tests your ability to design cost-effective storage, compute, database, and networking solutions.

---

## Task 4.1: Design cost-optimized storage solutions

### S3 Storage Optimization

#### S3 Storage Classes

**Selection by Access Pattern:**

| Access Pattern | Storage Class | Use Case |
|---------------|---------------|----------|
| Frequent | S3 Standard | Active data |
| Unknown/changing | S3 Intelligent-Tiering | Unpredictable access |
| Infrequent | S3 Standard-IA | Backups, disaster recovery |
| Infrequent, single AZ | S3 One Zone-IA | Reproducible data |
| Archive | S3 Glacier Instant Retrieval | Quarterly access, milliseconds |
| Archive | S3 Glacier Flexible Retrieval | Minutes to hours retrieval |
| Long-term archive | S3 Glacier Deep Archive | Once/twice per year, 12 hours |

**Cost Optimization:**
- Use Intelligent-Tiering for unknown patterns
- Lifecycle policies to transition objects
- Delete incomplete multipart uploads
- Use S3 Storage Lens for insights
- Request Payer for user-pays scenarios

**AWS Documentation:**
- <a href="https://aws.amazon.com/s3/storage-classes/" target="_blank">S3 Storage Classes</a>

#### S3 Lifecycle Policies

**Example Policy:**
```
Day 0: S3 Standard
Day 30: S3 Standard-IA
Day 90: S3 Glacier Flexible Retrieval
Day 365: S3 Glacier Deep Archive
Day 2555: Delete
```

**Best Practices:**
- Transition to IA after 30 days minimum
- Use filters (prefix, tags)
- Test policies before applying
- Monitor cost savings

### EBS Optimization

**Volume Selection:**
- **gp3** - Most cost-effective general purpose (vs gp2)
- **st1** - Cost-effective throughput (vs io2 for sequential)
- **sc1** - Lowest cost for infrequent access

**Cost Reduction:**
- Delete unattached volumes
- Snapshot old volumes, delete volume
- Delete old snapshots (use lifecycle)
- Use gp3 instead of gp2 (same price, better performance)
- Right-size volumes

**AWS Documentation:**
- <a href="https://aws.amazon.com/ebs/pricing/" target="_blank">EBS Pricing</a>

### EFS Optimization

**Cost Reduction:**
- Enable Lifecycle Management (IA transition)
- Use One Zone storage class when appropriate
- Use Bursting instead of Provisioned throughput
- Delete unused file systems

**AWS Documentation:**
- <a href="https://aws.amazon.com/efs/pricing/" target="_blank">EFS Pricing</a>

---

## Task 4.2: Design cost-optimized compute solutions

### EC2 Purchase Options

#### Pricing Models Comparison

| Model | Cost Savings | Commitment | Best For |
|-------|--------------|------------|----------|
| On-Demand | Baseline (1x) | None | Variable, short-term |
| Reserved (1yr) | ~30-40% | 1 year | Steady state |
| Reserved (3yr) | ~50-60% | 3 years | Long-term predictable |
| Savings Plans | ~30-60% | 1-3 years | Flexible compute |
| Spot | ~50-90% | None | Fault-tolerant workloads |
| Dedicated Hosts | Varies | Varies | Compliance, licensing |

#### Reserved Instances (RIs)

**Types:**
- **Standard RI** - Highest savings, can't change instance type
- **Convertible RI** - Can change instance type, lower savings

**Payment Options:**
- All Upfront (highest savings)
- Partial Upfront
- No Upfront (lowest savings)

**Best Practices:**
- Analyze usage with Cost Explorer
- Buy for steady-state workloads
- Start with 1-year, then 3-year
- Use RI marketplace to sell unused

#### Savings Plans

**Types:**
- **Compute Savings Plans** - Most flexible (EC2, Fargate, Lambda)
- **EC2 Instance Savings Plans** - EC2 only, specific instance family

**Benefits:**
- More flexible than RIs
- Apply automatically
- Combine with Spot for additional savings

#### Spot Instances

**Key Concepts:**
- Up to 90% discount
- Can be interrupted with 2-minute warning
- Spot Fleet manages multiple Spot Instances
- Spot Blocks for defined duration (deprecated)

**Use Cases:**
- Batch processing
- Big data analysis
- CI/CD pipelines
- Containerized workloads
- Fault-tolerant applications

**Best Practices:**
- Use multiple instance types and AZs
- Implement graceful shutdown
- Use Spot Fleet for resilience
- Combine with On-Demand for base capacity

**AWS Documentation:**
- <a href="https://aws.amazon.com/ec2/pricing/" target="_blank">EC2 Pricing</a>

### Instance Right-Sizing

**Optimization Steps:**
1. Enable CloudWatch detailed monitoring
2. Analyze CPU, memory, network utilization
3. Use AWS Compute Optimizer
4. Downsize underutilized instances
5. Use Auto Scaling to match demand

**Tools:**
- AWS Compute Optimizer
- AWS Cost Explorer
- Trusted Advisor

### Lambda Cost Optimization

**Cost Factors:**
- Number of requests
- Duration (GB-seconds)
- Memory allocation

**Optimization:**
- Optimize function memory (affects CPU)
- Reduce package size
- Use ARM (Graviton2) for lower cost
- Reduce execution time
- Use Provisioned Concurrency carefully

**AWS Documentation:**
- <a href="https://aws.amazon.com/lambda/pricing/" target="_blank">Lambda Pricing</a>

### Container Optimization

**ECS/EKS Cost Reduction:**
- Use Fargate Spot for cost savings
- Right-size task definitions
- Use Compute Savings Plans
- Enable Cluster Auto Scaling

**AWS Documentation:**
- <a href="https://aws.amazon.com/fargate/pricing/" target="_blank">Fargate Pricing</a>

---

## Task 4.3: Design cost-optimized database solutions

### RDS Cost Optimization

**Purchase Options:**
- On-Demand - Pay per hour
- Reserved Instances - Up to 69% savings

**Cost Reduction:**
- Use appropriate instance size
- Use read replicas instead of Multi-AZ for read scaling
- Stop instances when not needed (dev/test)
- Use Aurora Serverless for variable workloads
- Delete automated backups for terminated instances
- Use Aurora vs RDS for better performance/cost

**Aurora Serverless:**
- Auto-scales based on load
- Pay per ACU (Aurora Capacity Unit)
- Pause when inactive
- Use case: Infrequent, unpredictable workloads

**AWS Documentation:**
- <a href="https://aws.amazon.com/rds/pricing/" target="_blank">RDS Pricing</a>

### DynamoDB Cost Optimization

**Capacity Modes:**
- **On-Demand** - Pay per request (unpredictable)
- **Provisioned** - Reserve capacity (predictable, lower cost)

**Cost Reduction:**
- Use on-demand for new/unpredictable workloads
- Switch to provisioned for predictable patterns
- Enable auto-scaling for provisioned
- Use Global Tables only when needed
- Delete unused tables and indexes
- Use DynamoDB Standard-IA for infrequent access

**AWS Documentation:**
- <a href="https://aws.amazon.com/dynamodb/pricing/" target="_blank">DynamoDB Pricing</a>

### ElastiCache Cost Optimization

**Cost Reduction:**
- Use appropriate node size
- Use Reserved Nodes for steady workloads
- Scale horizontally with read replicas
- Delete unused clusters

**AWS Documentation:**
- <a href="https://aws.amazon.com/elasticache/pricing/" target="_blank">ElastiCache Pricing</a>

### Redshift Cost Optimization

**Cost Reduction:**
- Use RA3 nodes with managed storage
- Pause and resume clusters (dev/test)
- Use Reserved Nodes
- Concurrency Scaling (pay for peak usage only)
- Use Spectrum for S3 data (avoid loading)

**AWS Documentation:**
- <a href="https://aws.amazon.com/redshift/pricing/" target="_blank">Redshift Pricing</a>

---

## Task 4.4: Design cost-optimized network architectures

### Data Transfer Costs

**Cost Factors:**
- Data IN to AWS: Free
- Data OUT to internet: Charged
- Data between regions: Charged
- Data within same AZ: Free (usually)
- Data between AZs: Charged

**Optimization:**
- Use CloudFront to reduce data transfer
- Keep data in same region when possible
- Use VPC endpoints (no NAT Gateway fees)
- Use Direct Connect for large transfers
- Compress data before transfer

### VPC Endpoints

**Types:**
- Gateway Endpoints (S3, DynamoDB) - Free
- Interface Endpoints (other services) - Hourly + data charge

**Cost Savings:**
- No NAT Gateway fees for S3/DynamoDB
- No data transfer charges to internet
- More secure

**AWS Documentation:**
- <a href="https://aws.amazon.com/privatelink/pricing/" target="_blank">VPC Endpoints</a>

### NAT Gateway vs NAT Instance

**NAT Gateway:**
- Managed, highly available
- ~$30-45/month + data processing
- Recommended for production

**NAT Instance:**
- Self-managed EC2 instance
- Lower cost for small workloads
- Less reliable, requires maintenance

**Cost Optimization:**
- Use VPC endpoints for S3/DynamoDB (avoid NAT)
- Consider NAT instance for dev/test
- One NAT Gateway per AZ (not per subnet)

### CloudFront Cost Optimization

**Cost Factors:**
- Data transfer OUT
- HTTP/HTTPS requests
- Price classes (geographic regions)

**Optimization:**
- Use lower price class if users are regional
- Enable compression
- Cache aggressively
- Use Origin Shield for multiple origins

**AWS Documentation:**
- <a href="https://aws.amazon.com/cloudfront/pricing/" target="_blank">CloudFront Pricing</a>

---

## General Cost Optimization Strategies

### Monitoring and Analysis

**Tools:**
- **AWS Cost Explorer** - Visualize and analyze costs
- **AWS Budgets** - Set custom budgets and alerts
- **AWS Cost Anomaly Detection** - ML-based anomaly detection
- **AWS Trusted Advisor** - Cost optimization recommendations
- **AWS Compute Optimizer** - Right-sizing recommendations

**Best Practices:**
- Tag all resources (cost allocation tags)
- Set up billing alerts
- Review Cost Explorer monthly
- Use Budgets for forecasting
- Enable Cost Anomaly Detection

### Architectural Best Practices

**Design Principles:**
- Right-sizing from the start
- Increase elasticity (Auto Scaling)
- Choose right pricing models
- Optimize over time
- Use managed services when cost-effective

**Common Optimizations:**
- Auto Scaling to match demand
- S3 Lifecycle policies
- Delete unused resources
- Use Spot for fault-tolerant workloads
- Reserved capacity for steady state
- CloudFront for content delivery
- Serverless for variable workloads

---

## Exam Tips

**Common Question Patterns:**

1. **Reduce storage costs** → S3 Lifecycle policies, Intelligent-Tiering
2. **Cost-effective compute for steady workload** → Reserved Instances or Savings Plans
3. **Fault-tolerant batch processing** → Spot Instances
4. **Variable workload database** → Aurora Serverless or DynamoDB On-Demand
5. **Reduce data transfer costs** → CloudFront, VPC endpoints
6. **Dev/test environment** → Start/stop resources, Spot Instances
7. **Long-term archive** → S3 Glacier Deep Archive

**Cost Optimization Framework:**
1. **Measure** - Use Cost Explorer, tags
2. **Analyze** - Identify waste, underutilized resources
3. **Optimize** - Right-size, use appropriate pricing
4. **Monitor** - Set budgets, alerts, review regularly

**Key Principles:**
- Pay only for what you use
- Reduce waste (delete unused resources)
- Use the right resource for the job
- Use Reserved capacity for steady state
- Use Spot for fault-tolerant workloads
- Implement Auto Scaling
- Monitor and optimize continuously

---

## Final Thoughts

Domain 4 (Design Cost-Optimized Architectures) is **20% of the exam**.

**Master these concepts:**
1. EC2 pricing models (On-Demand, Reserved, Savings Plans, Spot)
2. S3 storage classes and lifecycle policies
3. RDS Reserved Instances and Aurora Serverless
4. Data transfer costs and VPC endpoints
5. CloudFront for reducing data transfer
6. Cost monitoring tools (Cost Explorer, Budgets)
7. Right-sizing and Auto Scaling

**Remember:** Cost optimization is continuous, not one-time!
