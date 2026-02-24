# AWS Certified SysOps Administrator - Associate (SOA-C03) Domain 2
## Reliability and Business Continuity

**Official Exam Guide:** <a href="https://docs.aws.amazon.com/aws-certification/latest/examguides/sysops-administrator-associate-03-domain2.html" target="_blank">Domain 2: Reliability and Business Continuity</a>  
**Skill Builder:** <a href="https://skillbuilder.aws/category/exam-prep/cloudops-engineer-associate-SOA-C03" target="_blank">AWS Certified SysOps Administrator - Associate (SOA-C03) Exam Prep</a>

Note: Some Skill Builder labs require a subscription.

---

## How to Study This Domain Effectively

### Study Tips

1. **Understand the difference between scalability and elasticity** - Scalability is the ability to handle increased load by adding resources, while elasticity is automatically adding or removing resources based on demand. The exam tests your knowledge of when to use Auto Scaling (elasticity) versus manual scaling (scalability), and how to configure scaling policies (target tracking, step scaling, scheduled scaling) for different scenarios. Practice setting up Auto Scaling groups with different scaling policies to understand their behaviors.

2. **Master Multi-AZ versus Multi-Region architectures** - Know when each provides the appropriate level of availability and disaster recovery. Multi-AZ protects against Availability Zone (AZ) failures within a region (high availability), while Multi-Region protects against region-wide outages (disaster recovery). Exam questions test your ability to design architectures that meet specific Recovery Time Objective (RTO) and Recovery Point Objective (RPO) requirements, so understand how different strategies (backup/restore, pilot light, warm standby, hot standby) map to RTO/RPO targets.

3. **Practice hands-on with AWS Backup** - Set up backup plans, vaults, and test restores for different resource types (EC2, EBS, RDS, DynamoDB, EFS, S3). The exam tests your knowledge of backup frequency, retention policies, lifecycle transitions, and cross-region copy capabilities. Understanding how to configure backup plans using tags versus resource assignments is critical, as is knowing the restore process for each service type.

4. **Learn Elastic Load Balancing (ELB) health check configurations thoroughly** - Understand how health check parameters (interval, timeout, healthy threshold, unhealthy threshold) affect target availability and how misconfigurations cause service disruptions. The exam presents troubleshooting scenarios where instances are being marked unhealthy incorrectly, or unhealthy instances aren't being removed quickly enough. Practice configuring health checks for Application Load Balancer (ALB), Network Load Balancer (NLB), and Gateway Load Balancer (GWLB).

5. **Focus on cost-optimized backup and recovery strategies** - Understand S3 storage classes for backups (S3 Standard-IA, S3 Glacier, S3 Glacier Deep Archive), EBS snapshot lifecycle policies, and RDS automated backup retention. The exam tests scenarios where you must balance cost with recovery requirements. Know how to implement lifecycle policies that automatically transition backups to cheaper storage classes while meeting compliance retention requirements.

### Recommended Approach

1. **Start with Auto Scaling fundamentals** - Study the EC2 Auto Scaling User Guide, focusing on launch templates, Auto Scaling groups, scaling policies, and lifecycle hooks. Understand how Auto Scaling works with load balancers and how health checks determine instance health. Create hands-on labs where you configure target tracking scaling (maintain CPU at 50%), step scaling (add instances based on alarm thresholds), and scheduled scaling (scale for predictable traffic patterns). This foundation is essential for understanding elasticity across all AWS services.

2. **Deep dive into high availability patterns** - Study Multi-AZ deployments for RDS, ElastiCache, EFS, and ELB. Understand how each service implements high availability differently. For example, RDS Multi-AZ uses synchronous replication with automatic failover, while ElastiCache for Redis uses replication groups. Practice configuring these Multi-AZ deployments and understand the failure scenarios they protect against. Learn when Multi-AZ is sufficient versus when you need Multi-Region.

3. **Master load balancer configuration and troubleshooting** - Study all three load balancer types (ALB, NLB, GWLB) and their use cases. Focus heavily on health check configuration, target group settings, and cross-zone load balancing. Practice troubleshooting common issues: targets marked unhealthy, connection timeouts, SSL certificate problems, and sticky session issues. Understand how to interpret load balancer CloudWatch metrics and access logs for troubleshooting.

4. **Comprehensive backup and restore practice** - Use AWS Backup to create backup plans for EC2, EBS, RDS, DynamoDB, EFS, and S3. Practice restoring each resource type and understand the differences in restore procedures. Study point-in-time recovery for RDS and DynamoDB, EBS snapshot restoration, and S3 versioning recovery. Understand cross-region backup copies and how to implement them for disaster recovery. Document RTO and RPO for each backup strategy you implement.

5. **Study disaster recovery strategies systematically** - Learn the four DR strategies (backup/restore, pilot light, warm standby, hot standby/multi-site) in order of increasing cost and decreasing RTO/RPO. For each strategy, understand the AWS services involved, implementation steps, costs, and typical RTO/RPO values. The exam tests your ability to recommend the appropriate DR strategy given specific business requirements (cost constraints, acceptable downtime, data loss tolerance). Practice architecting each DR pattern for a sample application.

---

## Task 2.1: Implement scalability and elasticity

### Skills & Corresponding Documentation

#### Skill 2.1.1: Configure and manage scaling mechanisms in compute environments

**Why:** Auto Scaling is fundamental to achieving elasticity in AWS and is one of the most tested topics in the SysOps exam. You must understand how to configure EC2 Auto Scaling groups, launch templates, scaling policies (target tracking, step scaling, simple scaling, scheduled scaling), and lifecycle hooks. Exam scenarios test your ability to troubleshoot scaling issues (instances not launching, scaling policies not triggering, instances not being replaced), optimize scaling performance (scale-out fast, scale-in slow), and integrate Auto Scaling with load balancers and CloudWatch alarms. Real-world SysOps administrators must design Auto Scaling configurations that handle traffic fluctuations while minimizing costs and maintaining application availability.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/autoscaling/ec2/userguide/" target="_blank">Amazon EC2 Auto Scaling User Guide</a>
- <a href="https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html" target="_blank">What Is Amazon EC2 Auto Scaling?</a>
- <a href="https://docs.aws.amazon.com/autoscaling/ec2/userguide/auto-scaling-groups.html" target="_blank">Auto Scaling Groups</a>
- <a href="https://docs.aws.amazon.com/autoscaling/ec2/userguide/launch-templates.html" target="_blank">Launch Templates</a>
- <a href="https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-scale-based-on-demand.html" target="_blank">Dynamic Scaling for Amazon EC2 Auto Scaling</a>
- <a href="https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-scaling-target-tracking.html" target="_blank">Target Tracking Scaling Policies</a>
- <a href="https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-scaling-simple-step.html" target="_blank">Step and Simple Scaling Policies</a>
- <a href="https://docs.aws.amazon.com/autoscaling/ec2/userguide/ec2-auto-scaling-scheduled-scaling.html" target="_blank">Scheduled Scaling</a>
- <a href="https://docs.aws.amazon.com/autoscaling/ec2/userguide/ec2-auto-scaling-scaling-cooldowns.html" target="_blank">Scaling Cooldowns for Amazon EC2 Auto Scaling</a>
- <a href="https://docs.aws.amazon.com/autoscaling/ec2/userguide/lifecycle-hooks.html" target="_blank">Lifecycle Hooks for Amazon EC2 Auto Scaling</a>
- <a href="https://docs.aws.amazon.com/autoscaling/ec2/userguide/ec2-auto-scaling-health-checks.html" target="_blank">Health Checks for Auto Scaling Instances</a>
- <a href="https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-monitoring-features.html" target="_blank">Monitoring Your Auto Scaling Groups and Instances</a>
- <a href="https://docs.aws.amazon.com/autoscaling/ec2/userguide/ts-as-common-errors.html" target="_blank">Troubleshooting Amazon EC2 Auto Scaling</a>
- <a href="https://docs.aws.amazon.com/autoscaling/plans/userguide/" target="_blank">AWS Auto Scaling User Guide</a>
- <a href="https://docs.aws.amazon.com/AmazonECS/latest/developerguide/service-auto-scaling.html" target="_blank">Scaling Your Amazon ECS Service</a>
- <a href="https://docs.aws.amazon.com/autoscaling/application/userguide/" target="_blank">Application Auto Scaling User Guide</a>

#### Skill 2.1.2: Implement caching by using AWS services to enhance dynamic scalability (for example, Amazon CloudFront, Amazon ElastiCache)

**Why:** Caching is a critical performance optimization and scalability strategy that reduces backend load and improves response times. The exam tests your knowledge of when to use CloudFront (content delivery network for static and dynamic content) versus ElastiCache (in-memory data store for database query results, session data). You must understand CloudFront cache behaviors, Time To Live (TTL) settings, invalidation, and origin failover. For ElastiCache, know when to use Redis (persistence, complex data structures, pub/sub) versus Memcached (simple caching, multi-threading) and how to configure clusters, replication groups, and parameter groups. Understanding caching strategies helps reduce costs by decreasing compute and database load while improving application performance.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/" target="_blank">Amazon CloudFront Developer Guide</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html" target="_blank">What Is Amazon CloudFront?</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/HowCloudFrontWorks.html" target="_blank">How CloudFront Delivers Content</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/ConfiguringCaching.html" target="_blank">Optimizing Caching and Availability</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Expiration.html" target="_blank">Managing How Long Content Stays in the Cache (Expiration)</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Invalidation.html" target="_blank">Invalidating Files</a>
- <a href="https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/high_availability_origin_failover.html" target="_blank">Using CloudFront Origin Groups</a>
- <a href="https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/" target="_blank">Amazon ElastiCache User Guide</a>
- <a href="https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/WhatIs.html" target="_blank">What Is Amazon ElastiCache for Redis?</a>
- <a href="https://docs.aws.amazon.com/AmazonElastiCache/latest/mem-ug/" target="_blank">Amazon ElastiCache for Memcached User Guide</a>
- <a href="https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/SelectEngine.html" target="_blank">Comparing Redis and Memcached</a>
- <a href="https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/Replication.Redis-RedisCluster.html" target="_blank">Replication: Redis (Cluster Mode Disabled) vs. Redis (Cluster Mode Enabled)</a>
- <a href="https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/Scaling.html" target="_blank">Scaling ElastiCache for Redis Clusters</a>
- <a href="https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/Strategies.html" target="_blank">Caching Strategies</a>
- <a href="https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/BestPractices.html" target="_blank">Best Practices for Amazon ElastiCache</a>

#### Skill 2.1.3: Configure and manage scaling in AWS managed databases (for example, Amazon RDS, Amazon DynamoDB)

**Why:** Database scaling is critical for application performance and cost optimization, and the exam extensively tests both vertical (instance size) and horizontal (read replicas, sharding) scaling strategies. For RDS, you must understand how to scale instance types, add read replicas, enable storage autoscaling, and implement Aurora Auto Scaling. For DynamoDB, know the difference between provisioned capacity (with auto scaling) and on-demand capacity, how to use Global Secondary Indexes (GSIs) for query flexibility, and when to implement DynamoDB Accelerator (DAX) for caching. Understanding the scaling characteristics, costs, and limitations of each database service helps you design cost-effective, performant database architectures that meet application requirements.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/" target="_blank">Amazon RDS User Guide</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_CommonTasks.html" target="_blank">Working with DB Instances</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.DBInstance.Modifying.html" target="_blank">Modifying an Amazon RDS DB Instance</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ReadRepl.html" target="_blank">Working with Read Replicas</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Storage.html" target="_blank">Amazon RDS DB Instance Storage</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_PIOPS.StorageTypes.html#USER_PIOPS.Autoscaling" target="_blank">Managing Capacity Automatically with Amazon RDS Storage Autoscaling</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/" target="_blank">Amazon Aurora User Guide</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Integrating.AutoScaling.html" target="_blank">Using Amazon Aurora Auto Scaling</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/aurora-global-database.html" target="_blank">Amazon Aurora Global Database</a>
- <a href="https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/" target="_blank">Amazon DynamoDB Developer Guide</a>
- <a href="https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.ReadWriteCapacityMode.html" target="_blank">Read/Write Capacity Mode</a>
- <a href="https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/AutoScaling.html" target="_blank">Managing Throughput Capacity Automatically with DynamoDB Auto Scaling</a>
- <a href="https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GSI.html" target="_blank">Using Global Secondary Indexes in DynamoDB</a>
- <a href="https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DAX.html" target="_blank">In-Memory Acceleration with DynamoDB Accelerator (DAX)</a>
- <a href="https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GlobalTables.html" target="_blank">DynamoDB Global Tables</a>
- <a href="https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/bp-partition-key-design.html" target="_blank">Best Practices for Designing and Using Partition Keys Effectively</a>

---

## Task 2.2: Implement highly available and resilient environments

### Skills & Corresponding Documentation

#### Skill 2.2.1: Configure and troubleshoot Elastic Load Balancing (ELB) and Amazon Route 53 health checks

**Why:** Load balancer and DNS health checks are fundamental to high availability and are heavily tested through troubleshooting scenarios. You must understand how ELB health check parameters (interval, timeout, healthy/unhealthy thresholds, path, port) determine target health and how misconfigured health checks cause service disruptions. For Route 53, understand health check types (endpoint, calculated, CloudWatch alarm), failover routing policies, and how health checks integrate with DNS records. Exam questions present scenarios where health checks are marking targets as unhealthy incorrectly, failing to detect actual failures, or causing routing problems. Understanding health check mechanics is critical for maintaining application availability and implementing automated failover.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/" target="_blank">Elastic Load Balancing User Guide</a>
- <a href="https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/what-is-load-balancing.html" target="_blank">What Is Elastic Load Balancing?</a>
- <a href="https://docs.aws.amazon.com/elasticloadbalancing/latest/application/" target="_blank">Application Load Balancer Guide</a>
- <a href="https://docs.aws.amazon.com/elasticloadbalancing/latest/network/" target="_blank">Network Load Balancer Guide</a>
- <a href="https://docs.aws.amazon.com/elasticloadbalancing/latest/gateway/" target="_blank">Gateway Load Balancer Guide</a>
- <a href="https://docs.aws.amazon.com/elasticloadbalancing/latest/application/target-group-health-checks.html" target="_blank">Health Checks for Your Target Groups</a>
- <a href="https://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-healthchecks.html" target="_blank">Configure Health Checks for Your Classic Load Balancer</a>
- <a href="https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-monitoring.html" target="_blank">Monitor Your Load Balancers</a>
- <a href="https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-troubleshooting.html" target="_blank">Troubleshoot Your Application Load Balancers</a>
- <a href="https://docs.aws.amazon.com/elasticloadbalancing/latest/network/load-balancer-troubleshooting.html" target="_blank">Troubleshoot Your Network Load Balancers</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/" target="_blank">Amazon Route 53 Developer Guide</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-failover.html" target="_blank">Creating Amazon Route 53 Health Checks and Configuring DNS Failover</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/health-checks-types.html" target="_blank">Types of Amazon Route 53 Health Checks</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-failover-configuring.html" target="_blank">Configuring DNS Failover</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-failover-complex-configs.html" target="_blank">How Health Checks Work in Complex Amazon Route 53 Configurations</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/health-checks-monitoring.html" target="_blank">Monitoring Health Check Status and Getting Notifications</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-test.html" target="_blank">Why Did Route 53 Choose a Particular Resource Record Set?</a>

#### Skill 2.2.2: Configure fault-tolerant systems (for example, Multi-AZ deployments)

**Why:** Multi-AZ deployments are AWS's primary mechanism for achieving high availability within a region and are fundamental to fault-tolerant architecture design. The exam tests your understanding of how different services implement Multi-AZ (RDS synchronous replication with automatic failover, ElastiCache replication groups, EFS automatic replication, ELB distribution across AZs) and when Multi-AZ provides sufficient resilience versus when Multi-Region is required. You must know how to configure Multi-AZ for RDS, Aurora, ElastiCache, and understand the failover process, detection times, and data consistency guarantees. Understanding Multi-AZ architectures is critical for designing systems that tolerate AZ failures without service disruption or data loss.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.MultiAZ.html" target="_blank">High Availability (Multi-AZ) for Amazon RDS</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.MultiAZSingleStandby.html" target="_blank">Amazon RDS Multi-AZ Deployments</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.DBInstance.Modifying.html" target="_blank">Modifying an Amazon RDS DB Instance - Multi-AZ</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_RebootInstance.html" target="_blank">Testing a Multi-AZ Failover</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Overview.html" target="_blank">Amazon Aurora Fault Tolerance</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Replication.html" target="_blank">Replication with Amazon Aurora</a>
- <a href="https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/AutoFailover.html" target="_blank">Multi-AZ for ElastiCache for Redis</a>
- <a href="https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/AutoFailover.html" target="_blank">Minimizing Downtime in ElastiCache for Redis with Multi-AZ</a>
- <a href="https://docs.aws.amazon.com/efs/latest/ug/how-it-works.html#how-it-works-availability" target="_blank">Amazon EFS Availability and Durability</a>
- <a href="https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/how-elastic-load-balancing-works.html#cross-zone-load-balancing" target="_blank">Cross-Zone Load Balancing</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html" target="_blank">Regions and Availability Zones</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/design-principles.html" target="_blank">Designing for Resilience</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/use-fault-isolation-to-protect-your-workload.html" target="_blank">Using Fault Isolation to Protect Your Workload</a>

---

## Task 2.3: Implement backup and restore strategies

### Skills & Corresponding Documentation

#### Skill 2.3.1: Automate snapshots and backups for AWS resources (for example, Amazon EC2 instances, RDS DB instances, Amazon Elastic Block Store [Amazon EBS] volumes, Amazon S3 buckets, DynamoDB tables) by using AWS services (for example, AWS Backup)

**Why:** Automated backups are essential for data protection and disaster recovery, and the exam extensively tests AWS Backup configuration and management. You must understand how to create backup plans with rules (frequency, retention, lifecycle policies), assign resources using tags or resource IDs, configure backup vaults with encryption and access policies, and implement cross-region backup copies. Know the native backup capabilities of each service (RDS automated backups, EBS snapshots, DynamoDB point-in-time recovery) and when AWS Backup provides additional value through centralized management and compliance reporting. Understanding backup automation reduces operational overhead and ensures consistent data protection across your AWS environment.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/aws-backup/latest/devguide/" target="_blank">AWS Backup Developer Guide</a>
- <a href="https://docs.aws.amazon.com/aws-backup/latest/devguide/whatisbackup.html" target="_blank">What Is AWS Backup?</a>
- <a href="https://docs.aws.amazon.com/aws-backup/latest/devguide/creating-a-backup-plan.html" target="_blank">Creating Backup Plans</a>
- <a href="https://docs.aws.amazon.com/aws-backup/latest/devguide/assigning-resources.html" target="_blank">Assigning Resources to a Backup Plan</a>
- <a href="https://docs.aws.amazon.com/aws-backup/latest/devguide/vaults.html" target="_blank">Working with Backup Vaults</a>
- <a href="https://docs.aws.amazon.com/aws-backup/latest/devguide/cross-region-backup.html" target="_blank">AWS Backup Cross-Region Backup</a>
- <a href="https://docs.aws.amazon.com/aws-backup/latest/devguide/cross-account-backup.html" target="_blank">AWS Backup Cross-Account Backup</a>
- <a href="https://docs.aws.amazon.com/aws-backup/latest/devguide/monitoring.html" target="_blank">Monitoring AWS Backup Jobs</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSSnapshots.html" target="_blank">Amazon EBS Snapshots</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/snapshot-lifecycle.html" target="_blank">Automating EBS Snapshot Lifecycle with Data Lifecycle Manager</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithAutomatedBackups.html" target="_blank">Working with Backups in Amazon RDS</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_CommonTasks.BackupRestore.html" target="_blank">Backing Up and Restoring an Amazon RDS DB Instance</a>
- <a href="https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/PointInTimeRecovery.html" target="_blank">Point-in-Time Recovery for DynamoDB</a>
- <a href="https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/BackupRestore.html" target="_blank">On-Demand Backup and Restore for DynamoDB</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/Versioning.html" target="_blank">Using Versioning in S3 Buckets</a>
- <a href="https://docs.aws.amazon.com/aws-backup/latest/devguide/encryption.html" target="_blank">Protecting Data Using Encryption</a>

#### Skill 2.3.2: Use various methods to restore databases (for example, point-in-time restore) to meet recovery time objective (RTO), recovery point objective (RPO), and cost requirements

**Why:** Database restore procedures are critical for disaster recovery and are tested through scenarios requiring you to meet specific RTO and RPO requirements. You must understand the differences between automated backup restoration (creates new instance from backup), snapshot restoration (manual backups), and point-in-time recovery (restore to any second within retention period). Know the restore times for each method, data loss characteristics (RPO), and costs. For DynamoDB, understand the difference between on-demand backups and point-in-time recovery. The exam tests your ability to select the appropriate restore method based on business requirements (how much downtime is acceptable, how much data loss is tolerable, budget constraints).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_RestoreFromSnapshot.html" target="_blank">Restoring from a DB Snapshot</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_PIT.html" target="_blank">Restoring a DB Instance to a Specified Time</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithAutomatedBackups.html" target="_blank">Working with Backups in Amazon RDS</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_CommonTasks.BackupRestore.html" target="_blank">Overview of Backing Up and Restoring an Amazon RDS DB Instance</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Managing.Backups.html" target="_blank">Backup and Restore for Aurora</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/AuroraMySQL.Managing.Backtrack.html" target="_blank">Backtracking an Aurora DB Cluster</a>
- <a href="https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/BackupRestore.html" target="_blank">Restoring a Table from a Backup in DynamoDB</a>
- <a href="https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/PointInTimeRecovery.Tutorial.html" target="_blank">Restoring a DynamoDB Table to a Point in Time</a>
- <a href="https://docs.aws.amazon.com/aws-backup/latest/devguide/restoring-a-backup.html" target="_blank">Performing AWS Backup Restores</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-restoring-volume.html" target="_blank">Restoring from an Amazon EBS Snapshot</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/disaster-recovery-dr-objectives.html" target="_blank">Recovery Time Objective and Recovery Point Objective</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/test-disaster-recovery-implementation.html" target="_blank">Testing Disaster Recovery</a>

#### Skill 2.3.3: Implement versioning for storage services (for example, Amazon S3, Amazon FSx)

**Why:** Versioning provides protection against accidental deletion and overwrites, and the exam tests your understanding of versioning configuration and lifecycle management. For S3, you must know how versioning works (every object modification creates a new version), how to enable/suspend versioning, how versioning affects storage costs (all versions are stored), and how to use lifecycle policies to expire or transition old versions. For FSx, understand automatic daily backups and user-initiated backups. The exam tests scenarios involving recovering deleted objects using versioning, implementing versioning with lifecycle policies to manage costs, and using Multi-Factor Authentication (MFA) Delete for additional protection against accidental deletion.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/Versioning.html" target="_blank">Using Versioning in S3 Buckets</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/manage-versioning-examples.html" target="_blank">Enabling Versioning on Buckets</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/manage-objects-versioned-bucket.html" target="_blank">Working with Objects in a Versioning-Enabled Bucket</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/DeletingObjectVersions.html" target="_blank">Deleting Object Versions from a Versioning-Enabled Bucket</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/RestoringPreviousVersions.html" target="_blank">Restoring Previous Versions</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/MultiFactorAuthenticationDelete.html" target="_blank">Configuring MFA Delete</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lock.html" target="_blank">Using S3 Object Lock</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lifecycle-mgmt.html" target="_blank">Managing the Lifecycle of Objects on S3</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/lifecycle-configuration-examples.html#lifecycle-config-conceptual-ex6" target="_blank">Lifecycle Configuration for a Bucket with Versioning</a>
- <a href="https://docs.aws.amazon.com/fsx/latest/WindowsGuide/using-backups.html" target="_blank">Amazon FSx for Windows File Server Backups</a>
- <a href="https://docs.aws.amazon.com/fsx/latest/LustreGuide/using-backups-fsx.html" target="_blank">Amazon FSx for Lustre Backups</a>
- <a href="https://docs.aws.amazon.com/fsx/latest/ONTAPGuide/using-backups.html" target="_blank">Amazon FSx for NetApp ONTAP Backups</a>
- <a href="https://docs.aws.amazon.com/fsx/latest/OpenZFSGuide/using-backups.html" target="_blank">Amazon FSx for OpenZFS Backups</a>

#### Skill 2.3.4: Follow disaster recovery procedures

**Why:** Disaster recovery planning and execution is critical for business continuity and is tested through scenarios requiring you to design and implement DR strategies. You must understand the four DR strategies (backup and restore, pilot light, warm standby, multi-site active-active) and their characteristics (RTO, RPO, cost, complexity). Know how to implement each strategy using AWS services: backup/restore using AWS Backup and S3, pilot light with pre-provisioned core infrastructure, warm standby with scaled-down production environment, and multi-site using Route 53 for traffic distribution. The exam tests your ability to select the appropriate DR strategy based on business requirements and understand the tradeoffs between cost and recovery time. Understanding DR procedures is essential for minimizing business impact during disasters.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/whitepapers/latest/disaster-recovery-workloads-on-aws/disaster-recovery-workloads-on-aws.html" target="_blank">Disaster Recovery of Workloads on AWS</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/disaster-recovery-workloads-on-aws/disaster-recovery-options-in-the-cloud.html" target="_blank">Disaster Recovery Options in the Cloud</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/plan-for-disaster-recovery-dr.html" target="_blank">Plan for Disaster Recovery (DR)</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/disaster-recovery-workloads-on-aws/disaster-recovery-options-in-the-cloud.html#backup-and-restore" target="_blank">Backup and Restore</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/disaster-recovery-workloads-on-aws/disaster-recovery-options-in-the-cloud.html#pilot-light" target="_blank">Pilot Light</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/disaster-recovery-workloads-on-aws/disaster-recovery-options-in-the-cloud.html#warm-standby" target="_blank">Warm Standby</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/disaster-recovery-workloads-on-aws/disaster-recovery-options-in-the-cloud.html#multi-site-activeactive" target="_blank">Multi-Site Active/Active</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/test-disaster-recovery-implementation.html" target="_blank">Testing Disaster Recovery</a>
- <a href="https://docs.aws.amazon.com/drs/latest/userguide/" target="_blank">AWS Elastic Disaster Recovery</a>
- <a href="https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-failover.html" target="_blank">Using Amazon Route 53 for Disaster Recovery</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/replication.html" target="_blank">Multi-Region Replication for S3</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ReadRepl.html#USER_ReadRepl.XRgn" target="_blank">Cross-Region Read Replicas for RDS</a>
- <a href="https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GlobalTables.html" target="_blank">DynamoDB Global Tables</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/plan-for-disaster-recovery-dr.html" target="_blank">Automating Disaster Recovery</a>

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/ec2/autoscaling/faqs/" target="_blank">Amazon EC2 Auto Scaling FAQs</a>
- <a href="https://aws.amazon.com/autoscaling/faqs/" target="_blank">AWS Auto Scaling FAQs</a>
- <a href="https://aws.amazon.com/cloudfront/faqs/" target="_blank">Amazon CloudFront FAQs</a>
- <a href="https://aws.amazon.com/elasticache/faqs/" target="_blank">Amazon ElastiCache FAQs</a>
- <a href="https://aws.amazon.com/rds/faqs/" target="_blank">Amazon RDS FAQs</a>
- <a href="https://aws.amazon.com/rds/aurora/faqs/" target="_blank">Amazon Aurora FAQs</a>
- <a href="https://aws.amazon.com/dynamodb/faqs/" target="_blank">Amazon DynamoDB FAQs</a>
- <a href="https://aws.amazon.com/elasticloadbalancing/faqs/" target="_blank">Elastic Load Balancing FAQs</a>
- <a href="https://aws.amazon.com/route53/faqs/" target="_blank">Amazon Route 53 FAQs</a>
- <a href="https://aws.amazon.com/backup/faqs/" target="_blank">AWS Backup FAQs</a>
- <a href="https://aws.amazon.com/ebs/faqs/" target="_blank">Amazon EBS FAQs</a>
- <a href="https://aws.amazon.com/s3/faqs/" target="_blank">Amazon S3 FAQs</a>
- <a href="https://aws.amazon.com/fsx/windows/faqs/" target="_blank">Amazon FSx FAQs</a>
- <a href="https://aws.amazon.com/efs/faq/" target="_blank">Amazon EFS FAQs</a>
- <a href="https://aws.amazon.com/disaster-recovery/faqs/" target="_blank">AWS Elastic Disaster Recovery FAQs</a>

---

## AWS Whitepapers

- <a href="https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/welcome.html" target="_blank">Reliability Pillar - AWS Well-Architected Framework</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/disaster-recovery-workloads-on-aws/disaster-recovery-workloads-on-aws.html" target="_blank">Disaster Recovery of Workloads on AWS: Recovery in the Cloud</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/backup-recovery-approaches-using-aws/backup-recovery-approaches-using-aws.html" target="_blank">Backup and Recovery Approaches Using AWS</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/aws-caf-operations-perspective/reliability.html" target="_blank">AWS Cloud Adoption Framework: Reliability Perspective</a>
- <a href="https://docs.aws.amazon.com/whitepapers/latest/building-scalable-secure-multi-vpc-network-infrastructure/welcome.html" target="_blank">Building a Scalable and Secure Multi-VPC AWS Network Infrastructure</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html" target="_blank">Security Pillar - AWS Well-Architected Framework</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/cost-optimization-pillar/welcome.html" target="_blank">Cost Optimization Pillar - AWS Well-Architected Framework</a>

---

## Final Thoughts

Domain 2 focuses on designing and implementing resilient, highly available systems with comprehensive backup and disaster recovery strategies. Success requires deep understanding of Auto Scaling, Multi-AZ architectures, load balancer configurations, and backup/restore procedures across multiple AWS services. Practice implementing each disaster recovery strategy (backup/restore, pilot light, warm standby, multi-site) to understand the tradeoffs between RTO, RPO, and cost. The ability to troubleshoot health checks, configure automated backups, and select appropriate scaling strategies is essential for real-world SysOps operations. Combine documentation study with extensive hands-on practice in configuring resilient architectures that survive failures while meeting business continuity requirements.
