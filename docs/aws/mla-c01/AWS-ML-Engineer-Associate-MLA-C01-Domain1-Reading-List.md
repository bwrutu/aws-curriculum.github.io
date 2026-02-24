# AWS Certified Machine Learning Engineer - Associate (MLA-C01) Domain 1
## Data Preparation for Machine Learning (ML)

**Official Exam Guide:** <a href="https://docs.aws.amazon.com/aws-certification/latest/examguides/machine-learning-engineer-associate-01-domain1.html" target="_blank">Domain 1: Data Preparation for Machine Learning</a>  
**Skill Builder:** <a href="https://skillbuilder.aws/category/exam-prep/machine-learning-engineer-associate-MLA-C01" target="_blank">AWS Certified Machine Learning Engineer - Associate (MLA-C01) Exam Prep</a>

Note: Some Skill Builder labs require a subscription.

---

## How to Study This Domain Effectively

### Study Tips

1. **Understand data formats deeply and their ML use cases** - The exam tests your knowledge of when to use each data format based on access patterns and ML requirements. Parquet is columnar and ideal for analytics workloads with selective column reads, CSV is human-readable but inefficient for large datasets, JSON is flexible for nested data, ORC is optimized for Hadoop workloads, Avro supports schema evolution, and RecordIO is SageMaker's native format for efficient training. Practice converting between formats and understanding the performance implications (query speed, storage size, compression ratios). The exam frequently presents scenarios requiring you to select the optimal format based on data access patterns and ML pipeline requirements.

2. **Master feature engineering techniques systematically** - Feature engineering transforms raw data into features that improve model performance and is heavily tested. Understand scaling (Min-Max normalization, standardization), handling missing values (imputation strategies, forward fill, backward fill, mean/median/mode), encoding categorical variables (one-hot for nominal, label encoding for ordinal, target encoding), and handling outliers (detection methods, treatment strategies). Practice with SageMaker Data Wrangler's built-in transformations and understand when to apply each technique. The exam tests scenarios where poor feature engineering causes model performance issues that you must diagnose and remediate.

3. **Learn SageMaker Data Wrangler and Feature Store comprehensively** - These are core AWS ML services for data preparation and feature management. Data Wrangler provides visual data preparation with 300+ built-in transformations, data quality reports, and model explainability. Feature Store provides centralized feature management with online store (low-latency serving) and offline store (training). Understand the workflow: ingest data into Data Wrangler, apply transformations, generate data quality reports, export processed data or directly to Feature Store. The exam tests your knowledge of when to use Data Wrangler versus AWS Glue DataBrew, and how Feature Store enables feature reuse and consistency between training and inference.

4. **Understand bias detection and mitigation deeply** - Identifying and reducing bias in ML datasets is critical for responsible AI and is increasingly tested. Know pre-training bias metrics like Class Imbalance (CI), Difference in Proportions of Labels (DPL), and how to detect selection bias and measurement bias using SageMaker Clarify. Understand mitigation strategies: data augmentation (generating synthetic examples), resampling (oversampling minority class, undersampling majority class), and dataset splitting to ensure representative train/validation/test sets. The exam presents scenarios where biased data leads to unfair model predictions and requires you to identify the bias type and recommend appropriate remediation.

5. **Practice with AWS Glue and ETL patterns** - AWS Glue is essential for large-scale data preparation and transformation. Understand Glue components: Glue Data Catalog (metadata repository), Glue Crawlers (automatic schema discovery), Glue Jobs (ETL with Apache Spark), and Glue DataBrew (visual data preparation). Learn common ETL patterns: batch processing versus streaming, schema evolution handling, partitioning strategies for performance, and cost optimization through job bookmarks. The exam tests scenarios requiring you to design scalable data pipelines that prepare training data efficiently while managing costs.

### Recommended Approach

1. **Start with data ingestion fundamentals** - Begin by understanding AWS data storage services and their ML use cases. Study Amazon S3 (most common data lake storage for ML), Amazon EFS (shared file system for distributed training), Amazon FSx for high-performance workloads, and streaming sources (Kinesis Data Streams, Kinesis Data Firehose). Practice ingesting data into SageMaker from different sources, understanding data transfer options (S3 Transfer Acceleration for large files, Direct Connect for on-premises data). Learn storage optimization strategies (S3 Intelligent-Tiering, S3 Glacier for archival) and when to use each service based on access patterns, performance requirements, and costs.

2. **Master data transformation with hands-on practice** - Create end-to-end data preparation pipelines using SageMaker Data Wrangler and AWS Glue. Start with simple transformations (dropping columns, renaming, type conversion) and progress to complex feature engineering (creating derived features, aggregations, window functions). Practice the complete workflow: connect to data sources, apply transformations, analyze data quality, detect bias, and export to Feature Store or S3. Understand the generated code (PySpark, pandas) so you can customize transformations. This hands-on experience is critical for exam scenarios presenting data quality issues requiring specific transformation techniques.

3. **Deep dive into feature engineering techniques** - Study each feature engineering technique systematically with real examples. For numerical features: scaling (when to use Min-Max versus standardization), handling skewed distributions (log transformation, Box-Cox), and binning (equal-width versus equal-frequency). For categorical features: one-hot encoding (creates sparse features), label encoding (ordinal relationships), target encoding (uses target statistics). For text: tokenization, TF-IDF, embeddings. For images: normalization, augmentation. Practice identifying which techniques apply to different data types and ML problem types (classification, regression, time series).

4. **Learn data quality and bias detection tools** - Master AWS tools for ensuring data quality and detecting bias. Use AWS Glue Data Quality to define and evaluate data quality rules (completeness, uniqueness, validity). Use SageMaker Clarify to detect pre-training bias in datasets and generate bias reports showing CI, DPL, and other metrics. Practice interpreting bias reports and recommending mitigation strategies. Understand that data quality issues discovered early prevent costly model retraining later. The exam tests your ability to diagnose data quality problems from symptoms (poor model performance, unexpected predictions) and recommend appropriate detection and remediation tools.

5. **Study data security and compliance systematically** - Understand encryption (at rest with AWS KMS, in transit with TLS), data classification (public, internal, confidential), anonymization techniques (masking Personally Identifiable Information (PII), k-anonymity, differential privacy), and compliance requirements (General Data Protection Regulation (GDPR), Health Insurance Portability and Accountability Act (HIPAA), data residency). Learn how to use Amazon Macie to discover PII in data lakes, configure SageMaker to encrypt training data and model artifacts, and implement least-privilege access with Identity and Access Management (IAM) policies. The exam tests scenarios requiring you to recommend security controls for sensitive data used in ML pipelines.

---

## Task 1.1: Ingest and store data

### Knowledge Areas & AWS Documentation Reading List

#### 1. Data formats and ingestion mechanisms (for example, validated and non-validated formats, Apache Parquet, JSON, CSV, Apache ORC, Apache Avro, RecordIO)

**Why:** Data format selection directly impacts ML pipeline performance, storage costs, and processing efficiency, making this a fundamental exam topic. Parquet and ORC are columnar formats optimized for analytics workloads with fast selective column reads and excellent compression, ideal for SageMaker Feature Store offline storage. CSV is human-readable but inefficient for large datasets and lacks schema. JSON handles nested data well but is verbose. Avro supports schema evolution essential for evolving ML pipelines. RecordIO is SageMaker's optimized format for distributed training with efficient data loading. The exam tests your ability to select appropriate formats based on access patterns (full row scans versus selective columns), schema requirements (fixed versus evolving), human readability needs, and integration with ML services.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-algo-common-data-formats.html" target="_blank">Data Formats for Amazon SageMaker</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/cdf-training.html" target="_blank">RecordIO Format</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-algo-common-data-formats-parquet.html" target="_blank">Using Parquet Files for Training</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-algo-common-data-formats-csv.html" target="_blank">CSV Format</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-algo-common-data-formats-json.html" target="_blank">JSON Format</a>
- <a href="https://docs.aws.amazon.com/glue/latest/dg/aws-glue-programming-etl-format.html" target="_blank">AWS Glue Data Formats</a>
- <a href="https://docs.aws.amazon.com/athena/latest/ug/supported-serdes.html" target="_blank">Amazon Athena Data Formats</a>

#### 2. How to use the core AWS data sources (for example, Amazon S3, Amazon Elastic File System [Amazon EFS], Amazon FSx for NetApp ONTAP)

**Why:** Understanding AWS storage services and their ML use cases is essential because data storage choice affects training performance, cost, and scalability. S3 is the most common data lake for ML with unlimited scalability, lifecycle policies, and direct integration with SageMaker. EFS provides shared Network File System (NFS) storage for distributed training where multiple instances need concurrent access to the same dataset. FSx for NetApp ONTAP offers high-performance storage with advanced data management features for ML workloads requiring sub-millisecond latency. The exam tests scenarios requiring you to select the appropriate storage based on requirements (access patterns, concurrency, performance, cost) and understand tradeoffs between services.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-train-storage.html" target="_blank">Using Amazon S3 with Amazon SageMaker</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-data-access.html" target="_blank">Amazon S3 for Machine Learning</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-access-training-data.html" target="_blank">Using Amazon EFS with Amazon SageMaker</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-train-storage.html" target="_blank">Choosing a File System</a>
- <a href="https://docs.aws.amazon.com/fsx/latest/ONTAPGuide/what-is-fsx-ontap.html" target="_blank">Amazon FSx for NetApp ONTAP</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-train-storage.html" target="_blank">Storage Options for Machine Learning</a>

#### 3. How to use AWS streaming data sources to ingest data (for example, Amazon Kinesis, Apache Flink, Apache Kafka)

**Why:** Real-time ML applications require streaming data ingestion, and understanding streaming architectures is tested through scenarios involving continuous model updates or real-time predictions. Amazon Kinesis Data Streams provides scalable real-time data streaming with millisecond latency. Kinesis Data Firehose delivers streaming data to destinations (S3, Redshift) for batch ML training. Kinesis Data Analytics (using Apache Flink) processes streaming data with SQL or Java/Scala. Amazon Managed Streaming for Apache Kafka (MSK) provides fully managed Kafka for high-throughput streaming. The exam tests your knowledge of when to use each service based on latency requirements, throughput needs, processing complexity, and integration with ML pipelines.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/streams/latest/dev/" target="_blank">Amazon Kinesis Data Streams</a>
- <a href="https://docs.aws.amazon.com/firehose/latest/dev/" target="_blank">Amazon Kinesis Data Firehose</a>
- <a href="https://docs.aws.amazon.com/kinesisanalytics/latest/dev/" target="_blank">Amazon Kinesis Data Analytics</a>
- <a href="https://docs.aws.amazon.com/msk/latest/developerguide/" target="_blank">Amazon Managed Streaming for Apache Kafka (MSK)</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/inference-streaming.html" target="_blank">Streaming Data Ingestion for ML</a>
- <a href="https://docs.aws.amazon.com/prescriptive-guidance/latest/patterns/build-a-real-time-streaming-solution-using-amazon-kinesis.html" target="_blank">Processing Streaming Data</a>

#### 4. AWS storage options, including use cases and tradeoffs

**Why:** Storage decisions affect ML pipeline performance, cost, and scalability, making this a critical exam topic. Understanding tradeoffs between S3 storage classes (Standard for active data, Intelligent-Tiering for unknown access, Glacier for archival), EBS volumes (gp3, io2 for high-performance training), EFS (shared concurrent access), and FSx (specialized workloads) helps optimize ML infrastructure. The exam tests cost optimization scenarios (using S3 lifecycle policies to move old training data to Glacier), performance optimization (using Provisioned Input/Output Operations Per Second (IOPS) EBS for I/O-intensive training), and architecture decisions (when to use EFS for multi-node training versus S3 for data lake storage).

**AWS Documentation:**
- <a href="https://aws.amazon.com/s3/storage-classes/" target="_blank">Amazon S3 Storage Classes</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html" target="_blank">Amazon EBS Volume Types</a>
- <a href="https://docs.aws.amazon.com/efs/latest/ug/performance.html" target="_blank">Amazon EFS Performance</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-train-storage.html" target="_blank">Storage Best Practices for Machine Learning</a>
- <a href="https://aws.amazon.com/products/storage/" target="_blank">Choosing the Right Storage for Your Workload</a>

### Skills & Corresponding Documentation

#### Extracting data from storage (for example, Amazon S3, Amazon Elastic Block Store [Amazon EBS], Amazon EFS, Amazon RDS, Amazon DynamoDB) by using relevant AWS service options (for example, Amazon S3 Transfer Acceleration, Amazon EBS Provisioned IOPS)

**Why:** Efficiently extracting training data is critical for ML pipeline performance and cost optimization. S3 Transfer Acceleration uses CloudFront edge locations for faster uploads over long distances. EBS Provisioned IOPS (io2 volumes) provides consistent high-performance storage for I/O-intensive training. Understanding when to use each option (Transfer Acceleration for geographically distributed teams, Provisioned IOPS for latency-sensitive training) helps optimize data access. The exam tests scenarios requiring you to troubleshoot slow data loading during training and recommend appropriate service options based on performance bottlenecks.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/transfer-acceleration.html" target="_blank">Amazon S3 Transfer Acceleration</a>
- <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html#EBSVolumeTypes_piops" target="_blank">Amazon EBS Provisioned IOPS Volumes</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-access-training-data.html" target="_blank">Accessing Data in Amazon S3</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-train-storage.html" target="_blank">Optimizing I/O Performance</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-data-access.html" target="_blank">Data Access Patterns</a>

#### Choosing appropriate data formats (for example, Parquet, JSON, CSV, ORC) based on data access patterns

**Why:** Data format selection impacts query performance, storage costs, and ML pipeline efficiency. Parquet excels for analytical queries selecting specific columns, reducing I/O and storage through columnar compression. CSV is simple but inefficient for large datasets. JSON handles nested structures but lacks schema enforcement. The exam tests your ability to analyze data access patterns (reading all columns versus specific columns, schema evolution needs, human readability requirements) and recommend the optimal format. Understanding format conversion techniques and storage savings (Parquet can reduce storage by 75% versus CSV) is essential for cost-optimized ML infrastructure.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/athena/latest/ug/supported-serdes.html" target="_blank">Choosing a Data Format</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-algo-common-data-formats.html" target="_blank">Data Formats for Machine Learning</a>
- <a href="https://docs.aws.amazon.com/glue/latest/dg/aws-glue-programming-etl-format.html" target="_blank">AWS Glue Data Format Support</a>
- <a href="https://docs.aws.amazon.com/glue/latest/dg/aws-glue-programming-etl-format-parquet.html" target="_blank">Converting Data Formats</a>

#### Ingesting data into Amazon SageMaker Data Wrangler and SageMaker Feature Store

**Why:** Data Wrangler and Feature Store are core SageMaker services for data preparation and feature management, making ingestion workflows heavily tested. Data Wrangler connects to multiple sources (S3, Athena, Redshift, Snowflake) and provides visual data profiling and transformation. Feature Store provides centralized feature repository with online store (low-latency real-time serving using DynamoDB) and offline store (historical features for training in S3). The exam tests your knowledge of ingestion workflows (connecting data sources, handling schema mismatches), Feature Store feature group creation (defining feature definitions, record identifier, event time), and the distinction between online versus offline stores for different ML use cases.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/data-wrangler.html" target="_blank">Amazon SageMaker Data Wrangler</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/data-wrangler-import.html" target="_blank">Import Data into Data Wrangler</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/feature-store.html" target="_blank">Amazon SageMaker Feature Store</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/feature-store-create-feature-group.html" target="_blank">Creating a Feature Group</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/feature-store-ingest-data.html" target="_blank">Ingesting Data into Feature Store</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/feature-store-getting-started.html" target="_blank">Feature Store Online and Offline Stores</a>

#### Merging data from multiple sources (for example, by using programming techniques, AWS Glue, Apache Spark)

**Why:** ML projects often require combining data from multiple sources (databases, data lakes, APIs), and understanding merge techniques is essential. AWS Glue provides managed ETL with Apache Spark for scalable joins, unions, and aggregations. Programming techniques (pandas merge, SQL joins) work for smaller datasets. The exam tests scenarios where training data must be enriched with external data (joining customer transactions with demographic data), handling schema mismatches during merges, optimizing join performance (broadcast joins for small tables, partition pruning), and troubleshooting common issues (skewed joins, out-of-memory errors).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/glue/latest/dg/aws-glue-programming-python.html" target="_blank">AWS Glue ETL Programming</a>
- <a href="https://docs.aws.amazon.com/glue/latest/dg/aws-glue-programming-python-transforms-join.html" target="_blank">Joining Data Sources</a>
- <a href="https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark.html" target="_blank">Apache Spark on Amazon EMR</a>
- <a href="https://docs.aws.amazon.com/glue/latest/dg/aws-glue-programming-etl-glue-data-catalog-hive.html" target="_blank">Data Transformation Techniques</a>

#### Troubleshooting and debugging data ingestion and storage issues that involve capacity and scalability

**Why:** Data ingestion issues cause ML pipeline failures, and troubleshooting skills are tested through real-world scenarios. Common problems include throttling (S3 request rate limits, Kinesis shard limits), timeout errors (slow network, large files), insufficient storage (EBS volume full), and out-of-memory errors (processing dataset too large for instance). The exam tests your ability to diagnose issues from error messages and CloudWatch metrics, and recommend solutions (increasing S3 prefix count to distribute load, adding Kinesis shards, using larger instances, implementing data streaming instead of loading entire dataset).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/troubleshooting.html" target="_blank">Troubleshooting Amazon S3</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/optimizing-performance.html" target="_blank">Best Practices for Amazon S3</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-troubleshooting.html" target="_blank">Troubleshooting SageMaker</a>
- <a href="https://docs.aws.amazon.com/glue/latest/dg/monitor-glue.html" target="_blank">Monitoring AWS Glue</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/logging-cloudwatch.html" target="_blank">Amazon CloudWatch Logs for ML Pipelines</a>

#### Making initial storage decisions based on cost, performance, and data structure

**Why:** Storage decisions made early in ML projects affect long-term costs and performance, making this a strategic exam topic. Cost considerations include S3 storage class selection (Standard $0.023/GB versus Glacier Deep Archive $0.00099/GB), data transfer costs (same region free, cross-region charged), and request costs (PUT/GET pricing). Performance factors include latency requirements (milliseconds for online features, seconds for batch acceptable), throughput needs (Gigabytes per second for large model training), and access patterns (sequential versus random reads). The exam tests scenarios requiring you to balance cost and performance (using S3 Intelligent-Tiering for unknown access patterns, EFS for shared training data, FSx for high-performance requirements).

**AWS Documentation:**
- <a href="https://aws.amazon.com/s3/pricing/" target="_blank">Amazon S3 Pricing</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/data-management.html" target="_blank">Storage Cost Optimization</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-train-storage.html" target="_blank">Choosing Storage for ML Workloads</a>
- <a href="https://docs.aws.amazon.com/cost-management/" target="_blank">AWS Cost Management</a>

---

## Task 1.2: Transform data and perform feature engineering

### Knowledge Areas & AWS Documentation Reading List

#### 1. Data cleaning and transformation techniques (for example, detecting and treating outliers, imputing missing data, combining, deduplication)

**Why:** Data quality directly impacts model performance, and cleaning techniques are fundamental to ML engineering. Outlier detection methods (Z-score, Interquartile Range (IQR), isolation forest) identify anomalous values that can skew models. Missing data imputation strategies (mean/median/mode for numerical, most frequent for categorical, forward/backward fill for time series, K-Nearest Neighbors (KNN) for complex patterns) prevent information loss. Deduplication removes exact and approximate duplicates that cause data leakage. The exam tests scenarios where poor data quality causes model issues (overfitting to outliers, biased predictions from missing data patterns) and requires you to identify appropriate cleaning techniques.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/data-wrangler-transform.html" target="_blank">Data Preparation with SageMaker Data Wrangler</a>
- <a href="https://docs.aws.amazon.com/databrew/latest/dg/transformations.html" target="_blank">AWS Glue DataBrew Transformations</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/data-wrangler-transform.html#data-wrangler-transform-handle-missing" target="_blank">Handling Missing Data</a>
- <a href="https://docs.aws.amazon.com/glue/latest/dg/glue-data-quality.html" target="_blank">Data Quality with AWS Glue</a>

#### 2. Feature engineering techniques (for example, data scaling and standardization, feature splitting, binning, log transformation, normalization)

**Why:** Feature engineering creates predictive features from raw data and is one of the most impactful steps in ML workflows. Scaling techniques (Min-Max scales to [0,1], Standardization scales to mean=0 and standard deviation=1) ensure features have comparable ranges for gradient-based algorithms. Feature splitting extracts components (dates into year/month/day, addresses into city/state). Binning converts continuous to categorical (age ranges). Log transformation handles skewed distributions. The exam extensively tests which technique applies to specific data characteristics and model requirements, and how improper feature engineering causes model failures (unconverged training from unscaled features, information loss from inappropriate binning).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/data-wrangler-transform.html" target="_blank">Feature Engineering with Data Wrangler</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/data-wrangler-analyses.html" target="_blank">Built-in Transformations</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/data-wrangler-transform.html#data-wrangler-transform-numeric" target="_blank">Feature Scaling and Normalization</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/feature-store-data-transformations.html" target="_blank">Feature Store Feature Transformations</a>

#### 3. Encoding techniques (for example, one-hot encoding, binary encoding, label encoding, tokenization)

**Why:** Categorical data must be encoded numerically for ML models, and encoding choice affects model performance and training efficiency. One-hot encoding creates binary columns for each category (ideal for nominal variables without ordering, but creates sparse high-dimensional features for high-cardinality categories). Label encoding assigns integers (appropriate for ordinal variables with natural ordering). Target encoding uses target variable statistics (reduces dimensionality but risks overfitting). Tokenization splits text into tokens for NLP. The exam tests scenarios requiring you to select appropriate encoding (one-hot for low-cardinality nominal, target encoding for high-cardinality, label encoding for ordinal) and troubleshoot issues (high-dimensional curse from excessive one-hot encoding).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/data-wrangler-transform.html#data-wrangler-transform-encode-categorical" target="_blank">Encoding Categorical Data</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/data-wrangler-transform.html#data-wrangler-transform-text" target="_blank">Text Transformations</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/data-wrangler-transform.html" target="_blank">Data Wrangler Encoding Options</a>

#### 4. Tools to explore, visualize, or transform data and features (for example, SageMaker Data Wrangler, AWS Glue, AWS Glue DataBrew)

**Why:** AWS provides multiple tools for data transformation, and understanding when to use each is tested. Data Wrangler offers visual interface with 300+ transformations, data quality analysis, and bias detection (ideal for exploration and prototyping). AWS Glue provides scalable Apache Spark-based ETL for production pipelines processing terabytes. DataBrew offers visual data preparation at scale (similar to Data Wrangler but for larger datasets and scheduled jobs). The exam tests tool selection based on requirements (data volume, user technical skills, production versus experimentation, cost optimization) and understanding of how tools integrate in ML workflows.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/data-wrangler.html" target="_blank">Amazon SageMaker Data Wrangler</a>
- <a href="https://docs.aws.amazon.com/glue/latest/dg/aws-glue-programming.html" target="_blank">AWS Glue ETL</a>
- <a href="https://docs.aws.amazon.com/databrew/latest/dg/what-is.html" target="_blank">AWS Glue DataBrew</a>
- <a href="https://aws.amazon.com/big-data/datalakes-and-analytics/" target="_blank">Comparing Data Preparation Tools</a>

#### 5. Services that transform streaming data (for example, AWS Lambda, Spark)

**Why:** Real-time ML applications require transforming streaming data before inference, and understanding streaming transformation architectures is tested. AWS Lambda processes individual records or small batches with millisecond latency (ideal for simple transformations, event-driven architectures). Apache Spark Structured Streaming (on EMR or Kinesis Data Analytics) handles complex transformations on continuous data streams with micro-batch or continuous processing. The exam tests scenarios requiring real-time feature engineering (calculating rolling averages, detecting anomalies in streaming data) and selection of appropriate service based on transformation complexity, latency requirements, and integration with ML inference.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/lambda/latest/dg/with-kinesis.html" target="_blank">AWS Lambda for Data Transformation</a>
- <a href="https://docs.aws.amazon.com/kinesisanalytics/latest/java/" target="_blank">Kinesis Data Analytics with Apache Flink</a>
- <a href="https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-streaming.html" target="_blank">Amazon EMR Spark Streaming</a>
- <a href="https://docs.aws.amazon.com/prescriptive-guidance/latest/patterns/process-streaming-data-from-kinesis-data-streams-using-aws-lambda.html" target="_blank">Real-time Data Processing</a>

#### 6. Data annotation and labeling services that create high-quality labeled datasets

**Why:** Supervised learning requires labeled training data, and understanding labeling services is essential for ML engineering. SageMaker Ground Truth provides managed labeling with human annotators, active learning to reduce labeling costs (only labels informative examples), and built-in labeling workflows for images (bounding boxes, semantic segmentation), text (classification, entity recognition), and video. Amazon Mechanical Turk offers flexible crowdsourcing for custom labeling tasks. The exam tests when to use Ground Truth (quality-controlled, ML-assisted labeling) versus Mechanical Turk (fully custom workflows), understanding of active learning cost benefits, and quality control mechanisms (consensus labeling, audit workflows).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/sms.html" target="_blank">Amazon SageMaker Ground Truth</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/sms-task-types.html" target="_blank">Ground Truth Labeling Workflows</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/gtp.html" target="_blank">Ground Truth Plus</a>
- <a href="https://docs.aws.amazon.com/AWSMechTurk/latest/AWSMechanicalTurkGettingStartedGuide/" target="_blank">Amazon Mechanical Turk</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/sms-automated-labeling.html" target="_blank">Active Learning with Ground Truth</a>

### Skills & Corresponding Documentation

#### Transforming data by using AWS tools (for example, AWS Glue, DataBrew, Spark running on Amazon EMR, SageMaker Data Wrangler)

**Why:** Practical transformation skills using AWS tools are heavily tested through scenarios requiring you to implement specific data preparation workflows. Understanding how to use Data Wrangler's visual interface for rapid prototyping, export Data Wrangler flows to Python/PySpark for production, create Glue jobs for scheduled batch processing, and use DataBrew for larger datasets with visual interface is essential. The exam tests your ability to translate business requirements into transformation logic, troubleshoot transformation failures, and optimize performance (pushing down filters, partitioning data, using appropriate instance types).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/data-wrangler-transform.html" target="_blank">Data Wrangler Transformations</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/data-wrangler-data-export.html" target="_blank">Exporting from Data Wrangler</a>
- <a href="https://docs.aws.amazon.com/glue/latest/dg/aws-glue-programming.html" target="_blank">AWS Glue Job Development</a>
- <a href="https://docs.aws.amazon.com/databrew/latest/dg/recipes.html" target="_blank">DataBrew Recipes</a>
- <a href="https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark.html" target="_blank">EMR Spark for Data Processing</a>

#### Creating and managing features by using AWS tools (for example, SageMaker Feature Store)

**Why:** Feature Store enables feature reuse and consistency between training and inference, making feature management skills critical. Creating feature groups requires defining schema (feature names, types), specifying record identifier and event time, and choosing online/offline store configurations. Managing features includes ingesting features (batch or streaming), querying features (GetRecord API for online, Athena for offline), handling feature versioning, and implementing feature pipelines. The exam tests scenarios requiring you to design feature architectures that prevent training-serving skew, enable feature reuse across multiple models, and maintain feature lineage for model governance.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/feature-store-getting-started.html" target="_blank">Feature Store Getting Started</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/feature-store-create-feature-group.html" target="_blank">Creating Feature Groups</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/feature-store-ingest-data.html" target="_blank">Ingesting Data into Feature Store</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/feature-store-retrieve-data.html" target="_blank">Retrieving Features</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/feature-store-best-practices.html" target="_blank">Feature Store Best Practices</a>

#### Validating and labeling data by using AWS services (for example, SageMaker Ground Truth, Amazon Mechanical Turk)

**Why:** Data validation and labeling skills are tested through scenarios requiring quality-controlled training datasets. Ground Truth workflows include creating labeling jobs (selecting task type, defining UI template, configuring workforce), using automatic labeling with active learning to reduce costs, implementing quality control (requiring multiple annotators per example, audit workflows), and processing labeling outputs for training. The exam tests your knowledge of when automated labeling provides sufficient accuracy, how to configure quality thresholds, and troubleshooting common labeling issues (poor inter-annotator agreement, labeling latency).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/sms-create-labeling-job.html" target="_blank">Creating a Labeling Job</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/sms-workforce-management.html" target="_blank">Ground Truth Workforce Types</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/sms-automated-labeling.html" target="_blank">Automated Data Labeling</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/sms-data-output.html" target="_blank">Labeling Job Output</a>
- <a href="https://docs.aws.amazon.com/glue/latest/dg/glue-data-quality.html" target="_blank">Data Validation Best Practices</a>

---

## Task 1.3: Ensure data integrity and prepare data for modeling

### Knowledge Areas & AWS Documentation Reading List

#### 1. Pre-training bias metrics for numeric, text, and image data (for example, class imbalance [CI], difference in proportions of labels [DPL])

**Why:** Detecting bias before training prevents unfair models and is increasingly tested as responsible AI becomes critical. Class Imbalance (CI) measures if one class is over-represented, causing models to predict majority class disproportionately. Difference in Proportions of Labels (DPL) compares label distributions across different groups (demographic parity). SageMaker Clarify automatically calculates these metrics. The exam tests your ability to interpret bias reports (CI = 0.8 means severe imbalance requiring mitigation), understand which metrics apply to different data types (CI for all classification, DPL for comparing groups), and recommend mitigation strategies based on metric values.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-detect-data-bias.html" target="_blank">Amazon SageMaker Clarify Bias Detection</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-bias-metric-class-imbalance.html" target="_blank">Pre-training Bias Metrics</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-measure-data-bias.html" target="_blank">Measuring Bias</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-data-bias-reports.html" target="_blank">Bias Report Interpretation</a>

#### 2. Strategies to address CI in numeric, text, and image datasets (for example, synthetic data generation, resampling)

**Why:** Mitigating class imbalance improves model performance on minority classes and is heavily tested. Resampling techniques include random oversampling (duplicate minority examples), random undersampling (remove majority examples), Synthetic Minority Over-sampling Technique (SMOTE) generates synthetic minority examples, Adaptive Synthetic (ADASYN) focuses on difficult-to-learn examples. For images, data augmentation creates variations (rotation, flipping, color jittering). For text, back-translation or paraphrasing. The exam tests which technique is appropriate for specific scenarios (SMOTE for numeric data, augmentation for images, synthetic generation for severe imbalance) and understanding tradeoffs (oversampling risks overfitting, undersampling loses information).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-detect-data-bias.html" target="_blank">Balancing Training Data</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/data-wrangler-transform.html" target="_blank">Data Augmentation Techniques</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-data-bias-mitigation.html" target="_blank">Handling Imbalanced Datasets</a>

#### 3. Techniques to encrypt data

**Why:** Protecting sensitive training data is mandatory for regulated industries and is tested through security scenarios. Encryption at rest uses AWS KMS with customer-managed or AWS-managed keys to encrypt S3 buckets, EBS volumes, and Feature Store. Encryption in transit uses TLS 1.2+ for data transfer. SageMaker encrypts training data, model artifacts, and endpoints. The exam tests your knowledge of when to use customer-managed keys (granular access control, key rotation policies), how to configure SageMaker encryption, and troubleshooting permission errors (IAM principal needs kms:Decrypt permission).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/encryption-at-rest.html" target="_blank">Data Encryption in SageMaker</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/key-management.html" target="_blank">Using KMS Keys</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/encryption-at-rest.html" target="_blank">Encrypting Data at Rest</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/encryption-in-transit.html" target="_blank">Encryption in Transit</a>

#### 4. Data classification, anonymization, and masking

**Why:** Protecting PII and sensitive data is critical for compliance and is tested through scenarios involving regulated data. Data classification identifies sensitivity levels (public, internal, confidential). Anonymization techniques include k-anonymity (group records to prevent individual identification), l-diversity (ensure diversity within groups), differential privacy (add statistical noise). Masking hides sensitive values while preserving data utility (replacing with fake data, tokenization). Amazon Macie discovers PII in data lakes. The exam tests when to use each technique (anonymization for training data, masking for non-production environments, deletion for unnecessary PII) and understanding regulatory requirements.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/macie/latest/user/findings-types.html" target="_blank">Amazon Macie for PII Detection</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/data-privacy.html" target="_blank">Data Privacy in Machine Learning</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/data-privacy-and-model-security.html" target="_blank">Protecting Sensitive Data</a>

#### 5. Implications of compliance requirements (for example, personally identifiable information [PII], protected health information [PHI], data residency)

**Why:** Compliance requirements constrain ML implementations and are tested through scenarios requiring compliant architectures. PII regulations (GDPR) mandate consent, right to deletion, and data minimization. PHI (HIPAA) requires Business Associate Agreements (BAAs), encryption, and audit trails. Data residency laws mandate data storage in specific geographic regions. The exam tests your knowledge of which AWS services support compliance (SageMaker HIPAA-eligible, KMS for encryption, CloudTrail for auditing), how to implement compliant architectures (regional endpoints, VPC endpoints to prevent internet transit), and understanding shared responsibility (AWS secures infrastructure, customer protects data).

**AWS Documentation:**
- <a href="https://aws.amazon.com/compliance/hipaa-compliance/" target="_blank">HIPAA Compliance</a>
- <a href="https://aws.amazon.com/compliance/gdpr-center/" target="_blank">GDPR Compliance</a>
- <a href="https://aws.amazon.com/compliance/data-residency/" target="_blank">Data Residency</a>
- <a href="https://aws.amazon.com/sagemaker/compliance/" target="_blank">SageMaker Compliance Programs</a>
- <a href="https://aws.amazon.com/compliance/resources/" target="_blank">Compliance Resources</a>

### Skills & Corresponding Documentation

#### Validating data quality (for example, by using DataBrew and AWS Glue Data Quality)

**Why:** Data quality validation prevents training on corrupt data and is tested through troubleshooting scenarios. AWS Glue Data Quality defines rules (completeness, uniqueness, validity, statistical properties) and evaluates datasets automatically. DataBrew provides data quality reports with recommendations. Validation checks include null counts, duplicate detection, schema compliance, statistical outliers, and data drift detection. The exam tests your ability to interpret quality reports, configure appropriate validation rules for specific ML use cases, and implement automated quality gates in ML pipelines that prevent training on poor-quality data.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/glue/latest/dg/glue-data-quality.html" target="_blank">AWS Glue Data Quality</a>
- <a href="https://docs.aws.amazon.com/glue/latest/dg/dqdl.html" target="_blank">Data Quality Rules</a>
- <a href="https://docs.aws.amazon.com/databrew/latest/dg/data-quality.html" target="_blank">DataBrew Data Quality</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/data-wrangler-data-insights.html" target="_blank">Data Profiling with Data Wrangler</a>

#### Identifying and mitigating sources of bias in data (for example, selection bias, measurement bias) by using AWS tools (for example, SageMaker Clarify)

**Why:** Identifying bias types and implementing mitigation is critical for fair ML and is extensively tested. Selection bias occurs when training data isn't representative of the target population. Measurement bias results from data collection methods systematically favoring certain outcomes. SageMaker Clarify generates bias reports showing metrics like CI and DPL. The exam tests your ability to diagnose bias from model behavior (consistently poor performance on specific demographic), use Clarify to quantify bias, and implement mitigation (collecting additional data for underrepresented groups, reweighting samples, using fairness constraints during training).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-detect-data-bias.html" target="_blank">Detecting Bias with SageMaker Clarify</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-measure-data-bias.html" target="_blank">Bias Metrics and Reports</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-data-bias-mitigation.html" target="_blank">Mitigating Bias</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-fairness-and-explainability.html" target="_blank">Fairness in Machine Learning</a>

#### Preparing data to reduce prediction bias (for example, by using dataset splitting, shuffling, and augmentation)

**Why:** Data preparation techniques directly affect model fairness and are tested through scenarios requiring bias reduction. Dataset splitting creates representative train/validation/test sets (stratified sampling ensures each split has proportional class distribution). Shuffling randomizes data order to prevent models learning spurious temporal patterns. Data augmentation generates synthetic examples for underrepresented classes. The exam tests when to use stratified versus random splitting, how augmentation prevents overfitting to limited data, and troubleshooting scenarios where poor splitting causes optimistic validation performance that doesn't generalize.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/data-wrangler-transform.html" target="_blank">Data Splitting Strategies</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/augmented-manifest.html" target="_blank">Data Augmentation</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-data-bias-mitigation.html" target="_blank">Reducing Bias Through Data Preparation</a>

#### Configuring data to load into the model training resource (for example, Amazon EFS, Amazon FSx)

**Why:** Efficient data loading configuration is critical for training performance and is tested through optimization scenarios. EFS provides shared file system for distributed training where multiple instances read the same data. FSx offers higher throughput for I/O-intensive workloads. S3 with Pipe mode streams data directly to training without downloading to disk (saves time and instance storage). The exam tests your ability to select appropriate storage mode (File mode for small datasets, Pipe mode for large datasets, FSx for maximum performance), configure data loading for distributed training (sharding data across instances), and troubleshoot slow training caused by data loading bottlenecks.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-access-training-data.html" target="_blank">Data Input Modes</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-access-training-data.html#model-access-training-data-efs" target="_blank">Using EFS with SageMaker</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-access-training-data.html#model-access-training-data-fsx" target="_blank">Using FSx with SageMaker</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/your-algorithms-training-algo-running-container.html#your-algorithms-training-algo-running-container-inputdataconfig" target="_blank">File Mode vs Pipe Mode</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-train-storage.html" target="_blank">Optimizing Data Loading</a>

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/sagemaker/faqs/" target="_blank">Amazon SageMaker FAQs</a>
- <a href="https://aws.amazon.com/s3/faqs/" target="_blank">Amazon S3 FAQs</a>
- <a href="https://aws.amazon.com/efs/faq/" target="_blank">Amazon EFS FAQs</a>
- <a href="https://aws.amazon.com/glue/faqs/" target="_blank">AWS Glue FAQs</a>
- <a href="https://aws.amazon.com/glue/databrew/faqs/" target="_blank">AWS Glue DataBrew FAQs</a>
- <a href="https://aws.amazon.com/kinesis/data-streams/faqs/" target="_blank">Amazon Kinesis FAQs</a>
- <a href="https://aws.amazon.com/msk/faqs/" target="_blank">Amazon MSK FAQs</a>
- <a href="https://aws.amazon.com/emr/faqs/" target="_blank">Amazon EMR FAQs</a>
- <a href="https://aws.amazon.com/lambda/faqs/" target="_blank">AWS Lambda FAQs</a>
- <a href="https://aws.amazon.com/macie/faq/" target="_blank">Amazon Macie FAQs</a>

---

## AWS Whitepapers

- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/machine-learning-lens.html" target="_blank">Machine Learning Lens - AWS Well-Architected Framework</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/data-management.html" target="_blank">Data Management in Machine Learning</a>
- <a href="https://aws.amazon.com/architecture/machine-learning/" target="_blank">Best Practices for Machine Learning on AWS</a>
- <a href="https://aws.amazon.com/big-data/datalakes-and-analytics/" target="_blank">Data Lakes and Analytics on AWS</a>
- <a href="https://aws.amazon.com/streaming-data/" target="_blank">Streaming Data Solutions on AWS</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/data-privacy-and-model-security.html" target="_blank">Security Best Practices for Machine Learning</a>

---

## Final Thoughts

Domain 1 establishes the foundation for successful ML engineering by focusing on data preparation - the most time-consuming and critical phase of ML projects. Master data ingestion from multiple sources (S3, streaming, databases), understand storage tradeoffs (cost, performance, accessibility), and become proficient with AWS data transformation tools (SageMaker Data Wrangler for exploration, AWS Glue for production ETL). Feature engineering techniques directly impact model performance, so practice systematically applying scaling, encoding, and transformation methods. SageMaker Feature Store is central to MLOps, enabling feature reuse and preventing training-serving skew. Data quality validation and bias detection using SageMaker Clarify are increasingly important for responsible AI. Success in this domain requires both theoretical knowledge of ML data preparation principles and practical skills implementing data pipelines using AWS services. Invest significant hands-on time with SageMaker Studio, Data Wrangler, and Feature Store to build the muscle memory needed for exam scenarios and real-world ML engineering.
