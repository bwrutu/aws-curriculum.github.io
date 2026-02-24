# AWS Certified Machine Learning Engineer - Associate (MLA-C01) Domain 3
## Deployment and Orchestration of ML Workflows

**Official Exam Guide:** <a href="https://docs.aws.amazon.com/aws-certification/latest/examguides/machine-learning-engineer-associate-01-domain3.html" target="_blank">Domain 3: Deployment and Orchestration of ML Workflows</a>  
**Skill Builder:** <a href="https://skillbuilder.aws/category/exam-prep/machine-learning-engineer-associate-MLA-C01" target="_blank">AWS Certified Machine Learning Engineer - Associate (MLA-C01) Exam Prep</a>

Note: Some Skill Builder labs require a subscription.

---

## How to Study This Domain Effectively

### Study Tips

1. **Master SageMaker endpoint types and their use cases systematically** - Understanding when to use each endpoint type is critical for the exam. Real-time endpoints provide low-latency synchronous inference with persistent instances (use for applications requiring immediate responses like fraud detection, chatbots). Serverless endpoints auto-scale to zero when idle (use for intermittent traffic, development/testing, cost optimization). Asynchronous endpoints queue requests and process them when resources are available (use for large payloads, long processing times, non-critical latency). Batch transform processes entire datasets offline (use for bulk predictions, periodic scoring). The exam extensively tests endpoint selection based on requirements (latency, cost, traffic patterns, payload size) and understanding tradeoffs between options.

2. **Understand deployment strategies deeply with rollback scenarios** - Deployment strategies manage risk when updating models and are heavily tested. Blue/green maintains two complete environments and switches traffic instantly (enables immediate rollback, but doubles infrastructure cost temporarily). Canary gradually shifts traffic to new version while monitoring metrics (detects issues with minimal impact, but requires monitoring infrastructure). Linear deploys incrementally increase new version traffic on schedule (predictable rollout, lower risk than instant switch). The exam tests scenarios requiring you to select appropriate strategies based on risk tolerance, monitoring capabilities, and rollback requirements. Understanding SageMaker's production variant traffic shifting and CloudWatch metrics integration is critical.

3. **Learn Infrastructure as Code (IaC) patterns for ML pipelines** - IaC enables reproducible, version-controlled ML infrastructure and is increasingly tested. CloudFormation uses declarative JSON/YAML templates to provision SageMaker endpoints, training jobs, and supporting infrastructure. AWS Cloud Development Kit (AWS CDK) provides imperative programming (Python, TypeScript) that synthesizes to CloudFormation. The exam tests when to use each (CloudFormation for template sharing and AWS-native workflows, CDK for complex logic and developer-friendly abstractions), how to parameterize templates for environment differences (dev/staging/production), and troubleshooting deployment failures (stack rollback, dependency errors, resource limits).

4. **Practice with SageMaker Pipelines end-to-end** - SageMaker Pipelines orchestrates ML workflows from data preparation through model deployment and is a core exam topic. Pipelines consist of steps (Processing for data transformation, Training for model creation, Evaluation for validation, Condition for approval gates, Model registration for Model Registry, Deployment for endpoint creation). Understanding pipeline definition using Python SDK, parameter passing between steps, caching for efficiency, and pipeline execution monitoring prepares you for workflow orchestration questions. The exam tests designing pipelines for specific ML workflows and troubleshooting pipeline execution failures.

5. **Master CI/CD for ML with AWS services** - MLOps requires automating the complete ML lifecycle from code commit to production deployment. CodePipeline orchestrates stages (source, build, test, deploy). CodeBuild compiles code, runs tests, and builds container images. CodeDeploy automates deployments with blue/green or canary strategies. The exam tests how these services integrate (CodePipeline triggers CodeBuild on Git commit, CodeBuild pushes images to Elastic Container Registry (ECR), CodeDeploy updates SageMaker endpoints), configuring buildspec files for model training/testing, and implementing automated retraining triggered by data drift or schedule. Understanding complete CI/CD workflows distinguishes ML engineers from data scientists.

### Recommended Approach

1. **Start with SageMaker deployment fundamentals** - Master the deployment workflow: train model → create model artifact → register in Model Registry → create endpoint configuration (instance type, count, variants) → deploy endpoint → invoke for predictions. Understand model artifacts (compressed model files in S3), endpoint configurations (infrastructure specification), and endpoint creation. Practice deploying models trained with built-in algorithms and custom frameworks. This foundational knowledge is prerequisite for advanced topics like multi-model endpoints, auto-scaling, and pipeline automation.

2. **Deep dive into endpoint types with cost analysis** - Create each endpoint type to understand behavior and cost implications. Real-time endpoints: always running (charged per instance-hour), suitable for consistent traffic. Serverless: pay-per-invocation plus compute time (no charges when idle), suitable for sporadic traffic. Asynchronous: queues requests (charged for processing time), suitable for high-latency tolerance. Batch transform: processes datasets in S3 (charged for compute time only), suitable for offline scoring. Calculate costs for different traffic patterns to understand when each option is optimal. This practical experience prepares you for cost optimization questions.

3. **Master containerization for ML** - Containers package models with dependencies for consistent deployment. Learn Docker basics (Dockerfile, images, containers), ECR for image storage (pushing/pulling images, lifecycle policies), and bring-your-own-container (BYOC) with SageMaker (implementing inference container requirements: /ping and /invocations endpoints, handling serialization/deserialization). Practice containerizing custom models and deploying to SageMaker. Understanding containers is essential for frameworks not natively supported and for complex inference logic.

4. **Implement complete CI/CD pipeline for ML** - Build end-to-end pipeline: commit code to Git → CodePipeline detects change → CodeBuild runs tests and trains model → conditional approval → deploy to staging endpoint → automated testing → traffic shift to production. This hands-on experience teaches pipeline configuration, stage orchestration, automated testing strategies, and troubleshooting pipeline failures. The exam tests understanding of how components integrate and how to design pipelines meeting specific requirements (automated retraining, approval workflows, gradual rollouts).

5. **Study auto-scaling deeply with monitoring** - Auto-scaling adjusts endpoint capacity based on load, reducing costs while maintaining performance. Configure target tracking scaling (maintain metric at target like 70% invocations per instance), step scaling (add capacity based on alarm thresholds), or scheduled scaling (capacity changes at specific times). Monitor scaling with CloudWatch metrics (ModelLatency, CPUUtilization, Invocations, MemoryUtilization). Practice load testing endpoints while observing scaling behavior. Understanding when instances scale out/in and metric lag effects prepares you for optimization and troubleshooting questions.

---

## Task 3.1: Select deployment infrastructure based on existing architecture and requirements

### Knowledge Areas & AWS Documentation Reading List

#### 1. Deployment best practices (for example, versioning, rollback strategies)

**Why:** Deployment best practices prevent production incidents and enable safe model updates. Model versioning using SageMaker Model Registry tracks all model versions with metadata (metrics, approval status, lineage), enabling rollback to previous versions when issues arise. Rollback strategies include: maintaining previous endpoint configuration for instant reversion, blue/green deployments with traffic routing between old and new endpoints, and canary deployments that gradually shift traffic while monitoring for issues. The exam tests scenarios requiring rollback due to performance degradation or errors, understanding how versioning enables audit trails for compliance, and implementing deployment safeguards (approval workflows, automated testing before production, gradual traffic shifts with monitoring). Production ML requires these practices to maintain service reliability.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/deployment-best-practices.html" target="_blank">SageMaker Deployment Best Practices</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-registry.html" target="_blank">Model Registry</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-registry-version.html" target="_blank">Model Versioning</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/deployment-guardrails.html" target="_blank">Deployment Guardrails</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/deployment-guardrails.html#deployment-guardrails-blue-green" target="_blank">Blue/Green Deployments</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/deployment-guardrails.html#deployment-guardrails-canary" target="_blank">Canary Deployments</a>

#### 2. AWS deployment services (for example, Amazon SageMaker AI)

**Why:** SageMaker provides comprehensive ML deployment capabilities and is the primary exam focus. SageMaker endpoints host models for real-time inference (persistent instances), serverless inference (auto-scaling to zero), and asynchronous inference (queued requests). Batch Transform processes large datasets offline. SageMaker Pipelines orchestrates workflows. Model Registry manages versions. The exam tests when SageMaker is appropriate versus alternatives (Lambda for simple inference, ECS/EKS for complex microservices, edge deployment for IoT), understanding SageMaker's built-in features (auto-scaling, monitoring, A/B testing), and integration patterns with other AWS services.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/" target="_blank">Amazon SageMaker</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/deploy-model.html" target="_blank">Deploy Models for Inference</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/realtime-endpoints.html" target="_blank">SageMaker Endpoints</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/inference-options.html" target="_blank">Inference Options</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/how-it-works-hosting.html" target="_blank">SageMaker Hosting Services</a>

#### 3. Methods to serve ML models in real time and in batches

**Why:** Serving method selection depends on latency requirements and traffic patterns. Real-time serving provides immediate responses through persistent endpoints (use for user-facing applications requiring <100ms latency like recommendations, fraud detection). Batch serving processes datasets asynchronously (use for bulk scoring, periodic predictions like customer churn scoring). Asynchronous serving queues requests (use when latency tolerance is minutes, payload sizes are large). The exam tests selecting serving methods based on business requirements (user experience needs, cost constraints, data volume), understanding infrastructure implications (real-time requires always-on instances, batch spins up compute temporarily), and hybrid approaches (real-time for interactive use cases, batch for analytics).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/realtime-endpoints.html" target="_blank">Real-time Inference</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/batch-transform.html" target="_blank">Batch Transform</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/async-inference.html" target="_blank">Asynchronous Inference</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/serverless-endpoints.html" target="_blank">Serverless Inference</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/deploy-model.html" target="_blank">Choosing an Inference Option</a>

#### 4. How to provision compute resources in production environments and test environments (for example, CPU, GPU)

**Why:** Compute resource selection balances performance, cost, and availability. Central Processing Units (CPUs) (ml.m5, ml.c5) are cost-effective for most inference workloads. Graphics Processing Units (GPUs) (ml.p3, ml.g4dn) accelerate deep learning inference but cost more. Inference-optimized instances (ml.inf1 with AWS Inferentia) provide best cost-performance for supported frameworks. The exam tests selecting instance types based on model characteristics (neural networks benefit from GPUs, tree-based models run efficiently on CPUs), traffic patterns (consistent traffic justifies reserved instances, variable traffic uses on-demand), and cost optimization strategies (starting with smaller instances and scaling up, using Spot for non-critical workloads). Understanding production versus test environment needs (production requires high availability across AZs, testing can use smaller instances) is also tested.

**AWS Documentation:**
- <a href="https://aws.amazon.com/sagemaker/pricing/" target="_blank">SageMaker Instance Types</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/inference-instance-types.html" target="_blank">Choosing Instance Types</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/inference-gpu.html" target="_blank">Inference with GPUs</a>
- <a href="https://aws.amazon.com/machine-learning/inferentia/" target="_blank">AWS Inferentia</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/inference-recommender.html" target="_blank">Inference Recommendations</a>

#### 5. Model and endpoint requirements for deployment endpoints (for example, serverless endpoints, real-time endpoints, asynchronous endpoints, batch inference)

**Why:** Each endpoint type has specific requirements and constraints that determine suitability. Real-time endpoints: support models up to 6GB, maximum payload 6MB, require immediate response, minimum billing per hour. Serverless endpoints: support models up to 10GB, scale to zero when idle, cold start latency for first request, per-invocation billing. Asynchronous endpoints: support large payloads (up to 1GB), maximum processing time 15 minutes, results stored in S3. Batch transform: processes datasets in S3, supports large models, charges only for compute time. The exam tests matching endpoint types to requirements (payload size, latency tolerance, traffic patterns, cost constraints) and understanding limitations that constrain choices.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/realtime-endpoints.html" target="_blank">Real-time Inference Endpoints</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/serverless-endpoints.html" target="_blank">Serverless Inference</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/async-inference.html" target="_blank">Asynchronous Inference</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/batch-transform.html" target="_blank">Batch Transform</a>
- <a href="https://docs.aws.amazon.com/general/latest/gr/sagemaker.html" target="_blank">Inference Quotas</a>

#### 6. How to choose appropriate containers (for example, provided or customized)

**Why:** Container selection determines deployment flexibility and maintenance overhead. SageMaker-provided containers (built-in algorithms, pre-built framework containers for TensorFlow, PyTorch, scikit-learn) offer managed updates, optimizations, and simpler deployment. Custom containers enable using any framework, implementing custom inference logic, or packaging proprietary dependencies. The exam tests when to use provided containers (standard frameworks, minimal customization) versus custom containers (unsupported frameworks, complex preprocessing, specialized hardware requirements), understanding BYOC requirements (implementing /ping and /invocations endpoints, handling serialization), and maintenance tradeoffs (provided containers get automatic updates, custom containers require manual maintenance).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/docker-containers.html" target="_blank">Use Docker Containers with SageMaker</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/pre-built-containers-frameworks-deep-learning.html" target="_blank">Pre-built SageMaker Docker Images</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/adapt-inference-container.html" target="_blank">Adapting Your Own Inference Container</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-monitor-byoc-containers.html" target="_blank">Bring Your Own Container</a>

#### 7. Methods to optimize models on edge devices (for example, SageMaker Neo)

**Why:** Edge deployment requires model optimization for resource-constrained devices (limited memory, CPU, power). SageMaker Neo compiles models for specific hardware targets (ARM Cortex, Intel Atom, NVIDIA Jetson), optimizing for size and performance. Optimizations include operator fusion (combining operations), memory layout optimization, and quantization. The exam tests when edge deployment is appropriate (latency-sensitive applications, limited connectivity, data privacy requirements), understanding Neo's compilation process (input model, target hardware, output optimized model), supported frameworks and hardware, and deployment options (AWS IoT Greengrass, edge devices). Edge inference is increasingly tested as IoT ML applications grow.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/neo.html" target="_blank">SageMaker Neo</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/neo-compilation.html" target="_blank">Compile and Deploy Models with Neo</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/neo-supported-frameworks.html" target="_blank">Neo Supported Frameworks</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/neo-job-compilation.html" target="_blank">Neo Model Compilation</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/neo-edge-devices.html" target="_blank">Deploy Models at the Edge</a>

### Skills & Corresponding Documentation

#### Evaluating performance, cost, and latency tradeoffs

**Why:** Production ML deployment requires balancing competing objectives. Performance (throughput, accuracy) may require powerful instances increasing costs. Low latency demands over-provisioning capacity reducing cost efficiency. The exam tests analyzing scenarios with constraints (must maintain <100ms latency, budget limited to $X/month) and recommending optimal solutions considering all factors. Understanding quantifiable tradeoffs (2x instance size doubles cost but may only reduce latency 30%) enables pragmatic decisions. Real-world examples: using Graviton instances reduces cost 20% with acceptable performance, serverless reduces cost 60% for sporadic traffic despite cold start latency, batch transform is 70% cheaper than real-time for non-urgent predictions.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/inference-cost-optimization.html" target="_blank">Cost Optimization for Inference</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/inference-recommender.html" target="_blank">Inference Recommendations</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/inference-performance.html" target="_blank">Performance Optimization</a>
- <a href="https://aws.amazon.com/sagemaker/pricing/" target="_blank">SageMaker Pricing</a>

#### Choosing the appropriate compute environment for training and inference based on requirements (for example, GPU or CPU specifications, processor family, networking bandwidth)

**Why:** Compute selection significantly impacts cost and performance. Training typically requires more powerful instances than inference (training processes entire datasets, inference handles single predictions). GPUs accelerate neural network training/inference through parallel computation. CPUs suffice for tree-based models and simple neural networks. The exam tests selecting instances based on model characteristics (deep learning benefits from GPUs, XGBoost runs efficiently on CPUs), data characteristics (large images require high-memory instances), networking needs (distributed training requires high network bandwidth), and cost constraints (Spot instances for interruptible training, Reserved for production inference).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/train-compute.html" target="_blank">Choosing Compute for Training</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/inference-instance-types.html" target="_blank">Choosing Instance Types for Inference</a>
- <a href="https://aws.amazon.com/ec2/instance-types/#Accelerated_Computing" target="_blank">GPU Instances</a>
- <a href="https://aws.amazon.com/ec2/instance-types/#Compute_Optimized" target="_blank">Compute-Optimized Instances</a>

#### Selecting the correct deployment orchestrator (for example, Apache Airflow, SageMaker Pipelines)

**Why:** Workflow orchestrators automate ML pipelines from data ingestion through deployment. SageMaker Pipelines provides native integration with SageMaker services (training, processing, tuning, registry) with Python SDK for pipeline definition. Apache Airflow (Amazon Managed Workflows for Apache Airflow - MWAA) offers flexibility for complex workflows across multiple AWS services and third-party systems. The exam tests selecting orchestrators based on requirements (SageMaker Pipelines for SageMaker-centric workflows, Airflow for multi-service orchestration), understanding capabilities (SageMaker Pipelines supports conditional steps and caching, Airflow has rich operator ecosystem), and integration patterns (triggering pipelines on schedule, data changes, or manual invocation).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/pipelines.html" target="_blank">SageMaker Pipelines</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/pipelines-build.html" target="_blank">Create and Manage Pipelines</a>
- <a href="https://docs.aws.amazon.com/mwaa/latest/userguide/" target="_blank">Amazon MWAA (Managed Workflows for Apache Airflow)</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/mlops-workflow-orchestration.html" target="_blank">Orchestrating ML Workflows</a>

#### Selecting multi-model or multi-container deployments

**Why:** Multi-model endpoints host multiple models on a single endpoint, reducing costs by sharing infrastructure. Suitable when: models have similar resource requirements, traffic per model is low, rapid model switching is needed. Multi-container endpoints run multiple containers together for complex inference logic (preprocessing container, model container, postprocessing container). The exam tests when multi-model endpoints provide value (hosting hundreds of personalized models cost-effectively), limitations (all models must use same framework, first invocation loads model causing latency), and when multi-container is appropriate (complex inference pipelines, different framework requirements for preprocessing versus inference).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/multi-model-endpoints.html" target="_blank">Multi-Model Endpoints</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/multi-model-endpoints-how-it-works.html" target="_blank">Hosting Multiple Models</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/multi-container-endpoints.html" target="_blank">Multi-Container Endpoints</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/inference-pipelines.html" target="_blank">Inference Pipelines</a>

#### Selecting the correct deployment target (for example, SageMaker AI endpoints, Kubernetes, Amazon Elastic Container Service [Amazon ECS], Amazon Elastic Kubernetes Service [Amazon EKS], AWS Lambda)

**Why:** Deployment target selection depends on requirements, existing infrastructure, and operational capabilities. SageMaker endpoints provide managed ML inference (auto-scaling, monitoring, A/B testing). Kubernetes (EKS) or ECS offer flexibility for complex microservices architectures. Lambda enables serverless event-driven inference for simple models. The exam tests selecting targets based on: SageMaker for ML-specific features and managed operations, Kubernetes for portability and advanced orchestration, Lambda for event-driven lightweight inference, ECS for container orchestration without Kubernetes complexity. Understanding capabilities and tradeoffs (SageMaker simplifies ML operations, Kubernetes requires more operational expertise but provides flexibility) is critical.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/deploy-model.html" target="_blank">Deploy Models to SageMaker</a>
- <a href="https://docs.aws.amazon.com/eks/latest/userguide/" target="_blank">Amazon EKS</a>
- <a href="https://docs.aws.amazon.com/AmazonECS/latest/developerguide/" target="_blank">Amazon ECS</a>
- <a href="https://docs.aws.amazon.com/lambda/latest/dg/" target="_blank">AWS Lambda</a>
- <a href="https://aws.amazon.com/blogs/machine-learning/" target="_blank">ML Inference on EKS</a>

#### Choosing model deployment strategies (for example, real time, batch)

**Why:** Deployment strategy aligns technical implementation with business requirements. Real-time deployment (always-on endpoints) serves predictions synchronously for user-facing applications requiring immediate responses (recommendation engines, fraud detection, chatbots). Batch deployment processes predictions in bulk asynchronously for analytical workloads (customer churn scoring, demand forecasting). The exam tests identifying appropriate strategies from use case descriptions (user waiting for prediction → real-time, periodic report generation → batch), understanding hybrid approaches (real-time for interactive features, batch for analytics), and cost implications (real-time costs more due to persistent infrastructure, batch only pays for compute time used).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/inference-options.html" target="_blank">Inference Options Overview</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/realtime-endpoints.html" target="_blank">Real-time Inference</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/batch-transform.html" target="_blank">Batch Transform</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/deployment-patterns.html" target="_blank">Deployment Patterns</a>

---

## Task 3.2: Create and script infrastructure based on existing architecture and requirements

### Knowledge Areas & AWS Documentation Reading List

#### 1. Difference between on-demand and provisioned resources

**Why:** Resource provisioning mode affects costs and availability. On-demand resources are created when needed and billed per use (serverless inference, Lambda, Spot instances for training). Provisioned resources run continuously and are billed per time unit (real-time endpoints, Reserved Instances). The exam tests selecting provisioning modes based on usage patterns (consistent traffic justifies provisioned for cost savings, unpredictable traffic suits on-demand), understanding commitment tradeoffs (provisioned requires commitment but costs less per unit, on-demand provides flexibility), and hybrid strategies (provisioned capacity for baseline load, on-demand for burst traffic).

**AWS Documentation:**
- <a href="https://aws.amazon.com/sagemaker/pricing/" target="_blank">SageMaker Pricing</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/inference-cost-optimization.html" target="_blank">On-Demand vs Provisioned Capacity</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/serverless-endpoints-pricing.html" target="_blank">Serverless Inference Pricing</a>
- <a href="https://aws.amazon.com/sagemaker/pricing/" target="_blank">Real-time Inference Pricing</a>

#### 2. How to compare scaling policies

**Why:** Auto-scaling policies adjust capacity based on load, balancing performance and cost. Target tracking maintains a metric at target value (70% InvocationsPerInstance). Step scaling adds capacity based on CloudWatch alarm thresholds (if invocations >100, add 2 instances). Scheduled scaling changes capacity at specific times (scale up before business hours). The exam tests selecting policies based on traffic patterns (target tracking for gradual changes, step scaling for sudden spikes, scheduled for predictable patterns), understanding configuration parameters (cooldown periods prevent thrashing, warmup time waits for instances to be ready), and combining policies for optimal responsiveness.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/endpoint-auto-scaling.html" target="_blank">Automatic Scaling for SageMaker Endpoints</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/endpoint-auto-scaling-add-policy.html" target="_blank">Target Tracking Scaling</a>
- <a href="https://docs.aws.amazon.com/autoscaling/application/userguide/application-auto-scaling-step-scaling-policies.html" target="_blank">Step Scaling Policies</a>
- <a href="https://docs.aws.amazon.com/autoscaling/application/userguide/application-auto-scaling-scheduled-scaling.html" target="_blank">Scheduled Scaling</a>

#### 3. Tradeoffs and use cases of infrastructure as code (IaC) options (for example, AWS CloudFormation, AWS Cloud Development Kit [AWS CDK])

**Why:** IaC enables reproducible, version-controlled infrastructure and is essential for MLOps. CloudFormation uses declarative templates (JSON/YAML) defining desired state, suitable for standard infrastructure patterns and sharing templates. AWS CDK uses imperative code (Python, TypeScript, Java) that synthesizes to CloudFormation, suitable for complex logic, reusable constructs, and developer productivity. The exam tests selecting IaC tools based on requirements (CloudFormation for portability and template sharing, CDK for programming convenience and abstraction), understanding tradeoffs (CloudFormation verbose but explicit, CDK concise but requires framework knowledge), and implementing infrastructure for ML workloads (defining SageMaker endpoints, training jobs, pipelines).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/cloudformation/" target="_blank">AWS CloudFormation</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/AWS_SageMaker.html" target="_blank">CloudFormation for SageMaker</a>
- <a href="https://docs.aws.amazon.com/cdk/v2/guide/" target="_blank">AWS CDK</a>
- <a href="https://docs.aws.amazon.com/cdk/api/v2/docs/aws-sagemaker-readme.html" target="_blank">CDK for SageMaker</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/infrastructure-as-code.html" target="_blank">IaC Best Practices</a>

#### 4. Containerization concepts and AWS container services

**Why:** Containers package models with dependencies for consistent deployment across environments. Docker provides containerization technology (images define environments, containers are running instances). ECR stores container images (push images after build, pull for deployment). ECS orchestrates containers on EC2 or Fargate. EKS provides managed Kubernetes. The exam tests understanding containerization benefits (consistency, isolation, portability), when to use each service (SageMaker BYOC for ML-optimized infrastructure, ECS/EKS for microservices architectures, Lambda for event-driven lightweight containers), and implementing container workflows (build image, push to ECR, deploy to compute platform).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/ecr/" target="_blank">Amazon ECR</a>
- <a href="https://docs.aws.amazon.com/ecs/" target="_blank">Amazon ECS</a>
- <a href="https://docs.aws.amazon.com/eks/" target="_blank">Amazon EKS</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/docker-containers.html" target="_blank">Docker Containers with SageMaker</a>
- <a href="https://docs.aws.amazon.com/AmazonECS/latest/bestpracticesguide/" target="_blank">Container Best Practices</a>

#### 5. How to use SageMaker AI endpoint auto scaling policies to meet scalability requirements (for example, based on demand, time)

**Why:** Auto-scaling ensures endpoints handle traffic variations cost-effectively. Demand-based scaling uses metrics (InvocationsPerInstance, ModelLatency, CPUUtilization) to trigger scaling. Time-based scaling uses schedules for predictable patterns. The exam tests configuring scaling policies (defining min/max instances, target metric and value, cooldown periods), selecting appropriate metrics (InvocationsPerInstance for balanced load distribution, ModelLatency for performance-sensitive applications, custom metrics for specific requirements), troubleshooting scaling issues (instances not scaling despite high load may indicate misconfigured policy or insufficient capacity limits), and optimizing costs (scaling in aggressively when traffic decreases, using Spot instances for additional capacity).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/endpoint-auto-scaling.html" target="_blank">Automatically Scale SageMaker Models</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/endpoint-auto-scaling-add-policy.html" target="_blank">Configure Auto Scaling Policy</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/endpoint-auto-scaling-metrics.html" target="_blank">Auto Scaling Metrics</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/endpoint-scaling-loadtest.html" target="_blank">Testing Auto Scaling</a>

### Skills & Corresponding Documentation

#### Applying best practices to enable maintainable, scalable, and cost-effective ML solutions (for example, automatic scaling on SageMaker AI endpoints, dynamically adding Spot Instances, by using Amazon EC2 instances, by using Lambda behind the endpoints)

**Why:** Production ML requires operational excellence balancing performance, scalability, and cost. Best practices include: implementing auto-scaling to match capacity with demand, using Spot instances for training (up to 90% savings), serverless inference for variable traffic, Lambda for lightweight preprocessing, monitoring and alerting for proactive issue detection, and infrastructure as code for reproducibility. The exam tests identifying best practices for specific scenarios (sporadic traffic → serverless, training jobs → Spot instances, preprocessing → Lambda), understanding tradeoffs (Spot instances can be interrupted, requiring checkpointing), and troubleshooting when best practices aren't followed (hardcoded configuration preventing environment promotion, manual scaling causing cost overruns).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/best-practices.html" target="_blank">ML Best Practices</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/inference-cost-optimization.html" target="_blank">Cost Optimization</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-managed-spot-training.html" target="_blank">Managed Spot Training</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/operational-excellence.html" target="_blank">Operational Excellence</a>

#### Automating the provisioning of compute resources, including communication between stacks (for example, by using CloudFormation, AWS CDK)

**Why:** Automated provisioning enables consistent, repeatable infrastructure deployment. CloudFormation stacks define related resources (endpoint, auto-scaling policy, CloudWatch alarms). Stack outputs enable communication (one stack outputs endpoint name, another stack imports for monitoring configuration). The exam tests implementing multi-stack architectures (networking stack, SageMaker stack, monitoring stack), using parameters and outputs for flexibility, handling stack dependencies (dependent stack waits for prerequisite stack completion), and troubleshooting deployment failures (resource limit exceeded, circular dependencies, insufficient permissions).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacks.html" target="_blank">CloudFormation Stacks</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/outputs-section-structure.html" target="_blank">Stack Outputs</a>
- <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/walkthrough-crossstackref.html" target="_blank">Cross-Stack References</a>
- <a href="https://docs.aws.amazon.com/cdk/v2/guide/stacks.html" target="_blank">CDK Stacks</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/infrastructure-as-code.html" target="_blank">Automating Infrastructure Provisioning</a>

#### Building and maintaining containers (for example, Amazon Elastic Container Registry [Amazon ECR], Amazon EKS, Amazon ECS, by using bring your own container [BYOC] with SageMaker AI)

**Why:** Container skills enable deploying custom inference logic and unsupported frameworks. Building containers involves: writing Dockerfile defining environment, dependencies, and entry point; building image; testing locally; pushing to ECR; deploying to compute platform. For SageMaker BYOC, implement required endpoints (/ping for health checks, /invocations for predictions), handle request/response serialization, and package model artifacts correctly. The exam tests container workflow implementation, troubleshooting build failures (dependency conflicts, incorrect base image), debugging runtime issues (missing dependencies, incorrect paths), and understanding security practices (scanning images for vulnerabilities, using minimal base images, not embedding secrets).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/adapt-inference-container.html" target="_blank">Build Your Own Container</a>
- <a href="https://docs.aws.amazon.com/ecr/" target="_blank">Amazon ECR User Guide</a>
- <a href="https://docs.aws.amazon.com/AmazonECS/latest/bestpracticesguide/dockerfile-best-practices.html" target="_blank">Dockerfile Best Practices</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/docker-containers-create.html" target="_blank">Deploy Custom Containers</a>
- <a href="https://docs.aws.amazon.com/AmazonECS/latest/bestpracticesguide/security.html" target="_blank">Container Security</a>

#### Configuring SageMaker AI endpoints within the VPC network

**Why:** VPC deployment provides network isolation for sensitive ML workloads. Configure endpoints in VPC by: specifying VPC configuration (subnets, security groups) during endpoint creation, ensuring security groups allow traffic from inference clients, configuring VPC endpoints for S3 access (avoiding NAT Gateway costs). The exam tests when VPC deployment is required (compliance requirements, accessing private data sources, network security controls), understanding network configuration (subnets should be in multiple AZs for high availability, security groups control inbound/outbound traffic), troubleshooting connectivity issues (endpoint unreachable may indicate security group misconfiguration, S3 access failures may require VPC endpoint), and cost optimization (VPC endpoints eliminate NAT Gateway costs for S3/DynamoDB access).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/train-vpc.html" target="_blank">Give SageMaker Training Jobs Access to Resources in Your VPC</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/host-vpc.html" target="_blank">Protect Your SageMaker Endpoints with VPC</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/interface-vpc-endpoint.html" target="_blank">VPC Endpoints for SageMaker</a>
- <a href="https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Security.html" target="_blank">VPC Security</a>

#### Deploying and hosting models by using the SageMaker AI SDK

**Why:** SageMaker Python SDK simplifies model deployment programmatically. Deployment workflow: create Model object (specifying image, model data location), create endpoint configuration (instance type, count, variants), deploy endpoint. The SDK abstracts API complexity providing high-level methods. The exam tests implementing deployments programmatically (useful for automation and CI/CD), understanding SDK capabilities (deploying models from training jobs, registering models, creating multi-variant endpoints), troubleshooting deployment failures from error messages, and optimizing deployment code (reusing endpoint configurations, parameterizing deployments for different environments).

**AWS Documentation:**
- <a href="https://sagemaker.readthedocs.io/" target="_blank">SageMaker Python SDK</a>
- <a href="https://sagemaker.readthedocs.io/en/stable/frameworks/tensorflow/using_tf.html#deploy-to-a-sagemaker-endpoint" target="_blank">Deploy Models</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/deploy-model.html" target="_blank">Model Deployment with SDK</a>
- <a href="https://sagemaker.readthedocs.io/en/stable/api/inference/model.html" target="_blank">Endpoint Configuration</a>

#### Choosing specific metrics for auto scaling (for example, model latency, CPU utilization, invocations per instance)

**Why:** Metric selection determines scaling effectiveness. InvocationsPerInstance distributes load evenly across instances (use for most workloads). ModelLatency maintains response time SLAs (use when latency is critical). CPUUtilization prevents compute saturation (use for CPU-intensive models). Custom metrics enable domain-specific scaling (queue depth, error rate). The exam tests selecting metrics based on requirements (latency-sensitive application → ModelLatency target, throughput-focused → InvocationsPerInstance, compute-intensive → CPUUtilization), configuring target values (too low causes excessive scaling costs, too high risks performance degradation), and combining metrics (using both invocations and latency provides comprehensive scaling strategy).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/endpoint-auto-scaling-metrics.html" target="_blank">Scaling Metrics</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/endpoint-auto-scaling-add-policy.html#endpoint-auto-scaling-add-policy-target-tracking" target="_blank">Target Tracking Configuration</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/endpoint-auto-scaling-add-policy.html#endpoint-auto-scaling-add-policy-custom-metric" target="_blank">Custom Metrics for Auto Scaling</a>

---

## Task 3.3: Use automated orchestration tools to set up continuous integration and continuous delivery (CI/CD) pipelines

### Knowledge Areas & AWS Documentation Reading List

#### 1. Capabilities and quotas for AWS CodePipeline, AWS CodeBuild, and AWS CodeDeploy

**Why:** Understanding CI/CD service capabilities and limits prevents design mistakes and enables troubleshooting. CodePipeline orchestrates release process (50 pipelines per region default, can be increased). CodeBuild compiles code and runs tests (containers up to 15GB memory, 2-72 hour timeout). CodeDeploy automates deployments (supports blue/green, canary, linear strategies). The exam tests service selection based on requirements (CodePipeline for multi-stage workflows, CodeBuild for containerized builds, CodeDeploy for gradual deployments), understanding quotas affecting design (pipeline limits require consolidation strategies, build timeout affects long-running jobs), and when to request limit increases.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/codepipeline/" target="_blank">AWS CodePipeline User Guide</a>
- <a href="https://docs.aws.amazon.com/codepipeline/latest/userguide/limits.html" target="_blank">CodePipeline Quotas</a>
- <a href="https://docs.aws.amazon.com/codebuild/" target="_blank">AWS CodeBuild User Guide</a>
- <a href="https://docs.aws.amazon.com/codebuild/latest/userguide/limits.html" target="_blank">CodeBuild Quotas</a>
- <a href="https://docs.aws.amazon.com/codedeploy/" target="_blank">AWS CodeDeploy User Guide</a>
- <a href="https://docs.aws.amazon.com/codedeploy/latest/userguide/limits.html" target="_blank">CodeDeploy Quotas</a>

#### 2. Automation and integration of data ingestion with orchestration services

**Why:** ML pipelines require automated data ingestion triggering workflows when new data arrives. Integration patterns include: S3 event triggering Lambda to start pipeline, scheduled EventBridge rules for periodic data processing, SageMaker Pipelines triggered by data changes. The exam tests designing event-driven architectures (new training data uploaded → automatically train model), scheduling workflows (daily retraining at midnight), chaining pipelines (data ingestion → feature engineering → training), and troubleshooting integration issues (pipeline not triggering may indicate misconfigured event rule, permissions issues preventing cross-service communication).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/pipelines.html" target="_blank">SageMaker Pipelines Automation</a>
- <a href="https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-rules.html" target="_blank">EventBridge Rules</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/NotificationHowTo.html" target="_blank">S3 Event Notifications</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/mlops-workflow-orchestration.html" target="_blank">Automating ML Workflows</a>

#### 3. Version control systems and basic usage (for example, Git)

**Why:** Version control is fundamental to MLOps enabling collaboration, audit trails, and reproducibility. Git tracks code changes (commits record history), branches enable parallel development (feature branches, main branch for production), merging combines changes. The exam tests Git workflows for ML (committing training scripts, branching for experiments, merging approved models), integration with CI/CD (CodePipeline triggered by Git commits), best practices (meaningful commit messages, .gitignore for large model files, Git LFS for large artifacts), and troubleshooting common issues (merge conflicts, accidentally committed sensitive data).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/codecommit/" target="_blank">AWS CodeCommit User Guide</a>
- <a href="https://docs.aws.amazon.com/codecommit/latest/userguide/repos.html" target="_blank">Working with Repositories</a>
- <a href="https://docs.aws.amazon.com/codecommit/latest/userguide/how-to-basic-git.html" target="_blank">Git with AWS CodeCommit</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/version-control.html" target="_blank">Version Control for ML</a>

#### 4. CI/CD principles and how they fit into ML workflows

**Why:** CI/CD principles (continuous integration, continuous delivery, continuous deployment) apply to ML with adaptations. CI: automatically test code on commits (unit tests for data processing, integration tests for pipelines). CD: automatically deploy to staging on tests passing. Continuous deployment: automatically deploy to production on approval. ML-specific considerations: model retraining triggers (data drift, performance degradation, scheduled), model validation (accuracy thresholds, bias detection), gradual rollouts (canary deployments monitoring model performance). The exam tests understanding CI/CD benefits for ML (faster iteration, reduced manual errors, reproducibility), implementing ML-specific pipelines (training, evaluation, deployment gates), and antipatterns (manual deployment causing inconsistencies, no model validation causing production issues).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/mlops-foundations.html" target="_blank">MLOps Foundations</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/continuous-integration-continuous-deployment.html" target="_blank">CI/CD for Machine Learning</a>
- <a href="https://aws.amazon.com/blogs/machine-learning/tag/mlops/" target="_blank">Automating ML Workflows</a>

#### 5. Deployment strategies and rollback actions (for example, blue/green, canary, linear)

**Why:** Deployment strategies manage risk when updating production models. Blue/green: maintain two complete environments (blue=current, green=new), switch traffic when ready, instant rollback by switching back. Canary: gradually increase traffic to new version (10%, 25%, 50%, 100%) while monitoring metrics, roll back if issues detected. Linear: incremental traffic increases on schedule (increase 10% every 5 minutes). The exam tests selecting strategies based on risk tolerance (blue/green for instant rollback capability, canary for gradual validation), configuring deployments (traffic splitting percentages, monitoring periods, automatic rollback triggers), and understanding tradeoffs (blue/green doubles infrastructure cost temporarily, canary requires monitoring infrastructure).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/deployment-guardrails.html" target="_blank">SageMaker Deployment Guardrails</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/deployment-guardrails.html#deployment-guardrails-blue-green" target="_blank">Blue/Green Deployments</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/deployment-guardrails.html#deployment-guardrails-canary" target="_blank">Canary Deployments</a>
- <a href="https://docs.aws.amazon.com/codedeploy/latest/userguide/deployments.html" target="_blank">Deployment Types</a>

#### 6. How code repositories and pipelines work together

**Why:** Integration between code repositories and CI/CD pipelines automates ML workflows. Pipeline triggered by: Git commits (developer pushes code → pipeline runs tests and trains model), pull request merges (approved code → deploy to production), tags (tagging release → deploy specific version). The exam tests configuring triggers (CodePipeline source stage monitors Git repository), understanding webhook versus polling (webhooks faster, require network access), implementing branching strategies (feature branches for development, main branch for production, tags for releases), and troubleshooting pipeline execution issues (pipeline not triggering may indicate webhook misconfiguration, build failing may indicate dependency issues).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/codepipeline/latest/userguide/pipelines-create.html" target="_blank">Create Pipeline with CodePipeline</a>
- <a href="https://docs.aws.amazon.com/codepipeline/latest/userguide/actions-create-source.html" target="_blank">Source Actions in CodePipeline</a>
- <a href="https://docs.aws.amazon.com/codecommit/latest/userguide/how-to-notify.html" target="_blank">CodeCommit Integration</a>
- <a href="https://docs.aws.amazon.com/codepipeline/latest/userguide/connections-github.html" target="_blank">GitHub Integration</a>

### Skills & Corresponding Documentation

#### Configuring and troubleshooting CodeBuild, CodeDeploy, and CodePipeline, including stages

**Why:** Practical CI/CD implementation skills are tested through configuration and troubleshooting scenarios. CodePipeline configuration: defining stages (Source, Build, Test, Deploy), actions within stages, artifacts passing between stages. CodeBuild configuration: buildspec.yml defining commands, environment variables, artifacts. CodeDeploy configuration: deployment groups, deployment configurations. The exam tests implementing complete pipelines, troubleshooting failures (build failing due to missing dependencies, deployment failing due to insufficient permissions, pipeline stuck due to missing manual approval), optimizing performance (caching dependencies in CodeBuild, parallel execution where possible), and cost optimization (using appropriate compute types, minimizing build time).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/codepipeline/latest/userguide/reference-pipeline-structure.html" target="_blank">CodePipeline Pipeline Structure</a>
- <a href="https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html" target="_blank">CodeBuild Buildspec Reference</a>
- <a href="https://docs.aws.amazon.com/codedeploy/latest/userguide/deployment-configurations.html" target="_blank">CodeDeploy Configuration</a>
- <a href="https://docs.aws.amazon.com/codepipeline/latest/userguide/troubleshooting.html" target="_blank">Troubleshooting CodePipeline</a>

#### Applying continuous deployment flow structures to invoke pipelines (for example, Gitflow, GitHub Flow)

**Why:** Git workflows structure collaborative development and release management. Gitflow: long-lived development and main branches, feature branches for new work, release branches for preparing production releases. GitHub Flow: simpler with feature branches merged directly to main, continuous deployment on merge. The exam tests selecting workflows based on team size and release frequency (Gitflow for structured releases, GitHub Flow for continuous deployment), implementing branch protection (requiring pull request reviews, status checks before merge), configuring pipeline triggers (automated testing on pull requests, deployment on merge to main), and understanding tradeoffs (Gitflow more structured but complex, GitHub Flow simpler but requires discipline).

**AWS Documentation:**
- <a href="https://aws.amazon.com/blogs/devops/git-branching-strategies-using-aws-codepipeline/" target="_blank">GitFlow with AWS</a>
- <a href="https://docs.aws.amazon.com/codepipeline/latest/userguide/tutorials-github-gitflow.html" target="_blank">Branch-based Development</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/continuous-deployment.html" target="_blank">Continuous Deployment Patterns</a>

#### Using AWS services to automate orchestration (for example, to deploy ML models, automate model building)

**Why:** Automation eliminates manual steps reducing errors and accelerating iteration. SageMaker Pipelines automates training workflows. EventBridge schedules retraining. Lambda triggers deployments. Step Functions orchestrates complex workflows. The exam tests designing automation (scheduled nightly retraining, deployment triggered by model approval, automatic data pipeline execution), implementing automation using appropriate services (SageMaker Pipelines for ML workflows, CodePipeline for code-driven deployments, EventBridge for scheduling), and troubleshooting automation failures (investigating CloudWatch Logs, understanding state machines in Step Functions, retrying failed pipeline steps).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-projects.html" target="_blank">Automate MLOps with SageMaker Projects</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/pipelines.html" target="_blank">SageMaker Pipelines</a>
- <a href="https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-tutorial-sagemaker.html" target="_blank">EventBridge for ML Automation</a>
- <a href="https://docs.aws.amazon.com/step-functions/latest/dg/concepts-use-cases.html" target="_blank">Step Functions for ML</a>

#### Configuring training and inference jobs (for example, by using Amazon EventBridge rules, SageMaker Pipelines, CodePipeline)

**Why:** Automated job configuration enables reproducible ML workflows. EventBridge rules trigger jobs on schedule or events (daily retraining at 2 AM, training when new data arrives). SageMaker Pipelines orchestrate multi-step workflows (data processing → training → evaluation → deployment). CodePipeline integrates with SageMaker for code-driven workflows. The exam tests implementing job triggers (configuring cron expressions for scheduling, creating event patterns for event-driven execution), parameterizing jobs for flexibility (different hyperparameters for dev versus production), managing job lifecycle (monitoring execution, handling failures with retries, cleaning up resources), and cost optimization (using Spot instances, stopping jobs on completion).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/scheduling-training-jobs.html" target="_blank">Schedule Training Jobs with EventBridge</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/pipelines-build.html" target="_blank">Create SageMaker Pipeline</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-projects-templates-sm.html" target="_blank">Integrate SageMaker with CodePipeline</a>
- <a href="https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-create-rule-schedule.html" target="_blank">EventBridge Cron Expressions</a>

#### Creating automated tests in CI/CD pipelines (for example, integration tests, unit tests, end-to-end tests)

**Why:** Automated testing prevents regressions and validates ML systems. Unit tests verify individual components (data preprocessing functions, feature engineering logic). Integration tests validate component interactions (data pipeline → training). End-to-end tests validate complete workflows (API request → prediction response). Model tests validate performance (accuracy above threshold, inference latency below limit, bias metrics within bounds). The exam tests implementing test strategies (what to test, when to test, how to automate), configuring tests in pipelines (CodeBuild running pytest, SageMaker Pipelines with condition steps for model validation), understanding test pyramid (many unit tests, fewer integration tests, few end-to-end tests), and troubleshooting test failures (analyzing logs, reproducing issues locally).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/codebuild/latest/userguide/test-reporting.html" target="_blank">Testing in CodeBuild</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/build-and-manage-steps.html#step-type-condition" target="_blank">Model Validation in Pipelines</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/automated-testing.html" target="_blank">CI/CD Testing Strategies</a>
- <a href="https://docs.aws.amazon.com/codepipeline/latest/userguide/actions-test.html" target="_blank">Integration Testing</a>

#### Building and integrating mechanisms to retrain models

**Why:** Model retraining maintains performance as data distributions change. Retraining triggers include: scheduled (daily, weekly), performance-based (accuracy drops below threshold), data-driven (significant data drift detected). The exam tests implementing retraining workflows (monitoring model performance → detect degradation → trigger retraining → evaluate new model → deploy if better), configuring triggers (EventBridge scheduled rules, Lambda monitoring metrics, SageMaker Model Monitor detecting drift), designing efficient retraining (incremental training when supported, storing training data efficiently, reusing hyperparameters when appropriate), and validation (new model must outperform production model, bias checks pass, latency requirements met).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/model-retraining.html" target="_blank">MLOps Model Retraining</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-monitor.html" target="_blank">SageMaker Model Monitor</a>
- <a href="https://aws.amazon.com/blogs/machine-learning/tag/mlops/" target="_blank">Automated Model Retraining</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/pipeline-eventbridge.html" target="_blank">Trigger Pipelines with EventBridge</a>

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/sagemaker/faqs/" target="_blank">Amazon SageMaker FAQs</a>
- <a href="https://aws.amazon.com/lambda/faqs/" target="_blank">AWS Lambda FAQs</a>
- <a href="https://aws.amazon.com/ecs/faqs/" target="_blank">Amazon ECS FAQs</a>
- <a href="https://aws.amazon.com/eks/faqs/" target="_blank">Amazon EKS FAQs</a>
- <a href="https://aws.amazon.com/ecr/faqs/" target="_blank">Amazon ECR FAQs</a>
- <a href="https://aws.amazon.com/codepipeline/faqs/" target="_blank">AWS CodePipeline FAQs</a>
- <a href="https://aws.amazon.com/codebuild/faqs/" target="_blank">AWS CodeBuild FAQs</a>
- <a href="https://aws.amazon.com/codedeploy/faqs/" target="_blank">AWS CodeDeploy FAQs</a>
- <a href="https://aws.amazon.com/cloudformation/faqs/" target="_blank">AWS CloudFormation FAQs</a>
- <a href="https://aws.amazon.com/eventbridge/faqs/" target="_blank">Amazon EventBridge FAQs</a>

---

## AWS Whitepapers

- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/machine-learning-lens.html" target="_blank">Machine Learning Lens - AWS Well-Architected Framework</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/mlops-foundations.html" target="_blank">MLOps Foundations</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/deployment-patterns.html" target="_blank">Deployment Strategies</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/infrastructure-as-code.html" target="_blank">Infrastructure as Code</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/continuous-integration-continuous-deployment.html" target="_blank">CI/CD for Machine Learning</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/operational-excellence.html" target="_blank">Operational Excellence for ML</a>

---

## Final Thoughts

Domain 3 focuses on operationalizing ML models through deployment, infrastructure automation, and CI/CD - the critical bridge between model development and production value delivery. Master SageMaker endpoint types comprehensively, understanding when each provides optimal cost-performance tradeoffs for specific use cases. Deployment strategies (blue/green, canary, linear) are essential for safe production updates - practice implementing these with traffic shifting and automatic rollback. Infrastructure as Code skills using CloudFormation or CDK enable reproducible deployments across environments. SageMaker Pipelines and CI/CD services (CodePipeline, CodeBuild, CodeDeploy) automate the complete ML lifecycle from code commit through production deployment. Understanding containerization (Docker, ECR, BYOC) enables deploying custom inference logic. Auto-scaling configuration ensures endpoints handle variable traffic cost-effectively. Success in this domain requires both deep AWS service knowledge and practical MLOps implementation experience, so complement documentation study with building complete end-to-end ML pipelines including automated testing, deployment strategies, monitoring, and retraining workflows.
