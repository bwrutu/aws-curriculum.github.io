# AWS Certified Machine Learning - Specialty (MLS-C01) Domain 1
## Data Engineering

**Official Exam Guide:** <a href="https://docs.aws.amazon.com/aws-certification/latest/examguides/machine-learning-specialty-01-domain1.html" target="_blank">Domain 1: Data Engineering</a>

**Skill Builder:** <a href="https://skillbuilder.aws/category/exam-prep/machine-learning-specialty-MLS-C01" target="_blank">AWS Certified Machine Learning - Specialty Exam Prep</a>

---

## Domain Overview

Domain 1 (20%) focuses on creating data repositories for ML, implementing data ingestion solutions, and implementing data transformation solutions.

---

## Task 1.1: Create data repositories for ML

**Key Concepts:**
- Identify data sources (content, location, primary sources like user data)
- Determine storage mediums (databases, S3, EFS, EBS)

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/" target="_blank">Amazon S3 User Guide</a>
- <a href="https://docs.aws.amazon.com/efs/latest/ug/" target="_blank">Amazon EFS User Guide</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AmazonEBS.html" target="_blank">Amazon EBS User Guide</a>
- <a href="https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/" target="_blank">Amazon DynamoDB Developer Guide</a>
- <a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/" target="_blank">Amazon RDS User Guide</a>

---

## Task 1.2: Identify and implement a data ingestion solution

**Key Concepts:**
- Data job styles (batch load, streaming)
- Orchestrate data ingestion pipelines (batch-based and streaming-based ML workloads)
- Schedule jobs

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/kinesis/latest/dev/" target="_blank">Amazon Kinesis Data Streams Developer Guide</a>
- <a href="https://docs.aws.amazon.com/firehose/latest/dev/" target="_blank">Amazon Data Firehose Developer Guide</a>
- <a href="https://docs.aws.amazon.com/emr/latest/ManagementGuide/" target="_blank">Amazon EMR Management Guide</a>
- <a href="https://docs.aws.amazon.com/glue/latest/dg/" target="_blank">AWS Glue Developer Guide</a>
- <a href="https://docs.aws.amazon.com/managed-flink/latest/java/what-is.html" target="_blank">Amazon Managed Service for Apache Flink</a>
- <a href="https://docs.aws.amazon.com/lambda/latest/dg/" target="_blank">AWS Lambda Developer Guide</a>

---

## Task 1.3: Identify and implement a data transformation solution

**Key Concepts:**
- Transform data in transit (ETL with AWS Glue, EMR, AWS Batch)
- Handle ML-specific data using MapReduce (Hadoop, Spark, Hive)

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/glue/latest/dg/how-it-works.html" target="_blank">AWS Glue How It Works</a>
- <a href="https://docs.aws.amazon.com/glue/latest/dg/add-job.html" target="_blank">AWS Glue Jobs</a>
- <a href="https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark.html" target="_blank">Apache Spark on Amazon EMR</a>
- <a href="https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-hadoop.html" target="_blank">Apache Hadoop on Amazon EMR</a>
- <a href="https://docs.aws.amazon.com/batch/latest/userguide/" target="_blank">AWS Batch User Guide</a>

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/s3/faqs/" target="_blank">Amazon S3 FAQs</a>
- <a href="https://aws.amazon.com/kinesis/data-streams/faqs/" target="_blank">Amazon Kinesis Data Streams FAQs</a>
- <a href="https://aws.amazon.com/glue/faqs/" target="_blank">AWS Glue FAQs</a>
- <a href="https://aws.amazon.com/emr/faqs/" target="_blank">Amazon EMR FAQs</a>

---

## Study Tips

1. **Master data storage options** - S3 for scalable object storage (training data, model artifacts), EFS for shared file systems, EBS for instance storage, databases for structured data.

2. **Learn streaming vs batch** - Kinesis Data Streams for real-time ingestion, Firehose for delivery to S3/Redshift, Glue for batch ETL, EMR for large-scale processing.

3. **Understand ETL pipelines** - AWS Glue for serverless ETL, EMR with Spark for complex transformations, Glue Data Catalog for metadata management.

4. **Practice data lake architecture** - S3 as data lake storage, Glue crawlers for schema discovery, Athena for SQL queries, Lake Formation for governance.

5. **Study Apache Spark** - DataFrame API, transformations vs actions, lazy evaluation, RDD operations, Spark SQL for ML data preparation.

---

**Note:** This is Domain 1 of 4, representing 20% of exam content.
