# AWS Certified Machine Learning Engineer - Associate (MLA-C01) Domain 2
## ML Model Development

**Official Exam Guide:** <a href="https://docs.aws.amazon.com/aws-certification/latest/examguides/machine-learning-engineer-associate-01-domain2.html" target="_blank">Domain 2: ML Model Development</a>  
**Skill Builder:** <a href="https://skillbuilder.aws/category/exam-prep/machine-learning-engineer-associate-MLA-C01" target="_blank">AWS Certified Machine Learning Engineer - Associate (MLA-C01) Exam Prep</a>

Note: Some Skill Builder labs require a subscription.

---

## How to Study This Domain Effectively

### Study Tips

1. **Understand algorithm selection systematically by problem type** - The exam extensively tests your ability to match algorithms to business problems. For classification (predicting categories), know when to use XGBoost (structured/tabular data, non-linear relationships), linear learner (linearly separable classes, fast training), or neural networks (complex patterns, large datasets). For regression (predicting continuous values), understand linear regression (linear relationships), XGBoost (non-linear), or neural networks (complex patterns). For clustering (grouping similar items), know K-means (spherical clusters, defined K) versus DBSCAN (arbitrary shapes, noise handling). Practice by categorizing real-world problems and justifying algorithm selection based on data characteristics, interpretability needs, and performance requirements.

2. **Master hyperparameter tuning strategies and their tradeoffs** - Hyperparameter optimization significantly impacts model performance and training costs. Random search samples hyperparameter combinations randomly (simple, parallelizable). Grid search exhaustively tests all combinations (thorough but expensive). Bayesian optimization (SageMaker Automatic Model Tuning) uses probabilistic models to intelligently select promising hyperparameters (most efficient, fewer training jobs). Understand hyperparameter effects: learning rate (too high causes divergence, too low causes slow convergence), batch size (larger increases throughput but may reduce generalization), number of layers/trees (more capacity but overfitting risk). The exam tests scenarios requiring you to balance exploration versus exploitation, optimize tuning budgets, and interpret tuning results.

3. **Learn to diagnose and fix overfitting and underfitting** - Model performance issues dominate ML engineering work. Overfitting (low training error, high validation error) indicates the model memorized training data rather than learning generalizable patterns - fix with regularization (L1/L2, dropout), more training data, or simpler model architecture. Underfitting (high training and validation error) means insufficient model capacity - fix with more complex architecture, additional features, or longer training. Practice analyzing learning curves (plotting training/validation loss over epochs) to diagnose issues: diverging curves indicate overfitting, parallel high curves indicate underfitting, converged low curves indicate good fit. The exam presents learning curves and metrics requiring diagnosis and remediation recommendations.

4. **Understand AWS AI services deeply for common use cases** - AWS provides pre-trained AI services eliminating custom model development for common tasks. Amazon Rekognition detects objects, faces, celebrities, text in images (custom labels for specialized detection). Amazon Transcribe converts speech to text (medical, call center variants). Amazon Translate translates text between languages. Amazon Comprehend extracts entities, sentiment, topics from text. Amazon Textract extracts text and structured data from documents. Amazon Bedrock provides foundation models for generative AI tasks. The exam tests when to use AI services (faster time-to-market, no ML expertise required, proven accuracy) versus custom models (unique requirements, specialized domains, data control needs). Know service capabilities, limitations, and integration patterns.

5. **Practice with SageMaker built-in algorithms hands-on** - SageMaker provides 18+ optimized algorithms covering classification, regression, clustering, dimensionality reduction, and specialized tasks. XGBoost is the most versatile for tabular data. Linear Learner provides fast linear models with automatic scaling and regularization. DeepAR forecasts time series. Blazing Text performs text classification and word embeddings. Image Classification fine-tunes deep learning models for custom images. Object Detection identifies and locates objects. Semantic Segmentation performs pixel-level image labeling. The exam tests algorithm selection based on problem type, data format requirements (RecordIO, CSV, Parquet), hyperparameter configuration, and understanding when built-in algorithms are optimal versus custom implementations.

### Recommended Approach

1. **Start with ML fundamentals and problem classification** - Before diving into SageMaker specifics, solidify understanding of supervised learning (labeled data for classification/regression), unsupervised learning (patterns in unlabeled data for clustering/dimensionality reduction), and reinforcement learning (learning through rewards). Understand common problem types: binary classification (yes/no), multi-class classification (one of many categories), multi-label classification (multiple categories simultaneously), regression (continuous values), time series forecasting, anomaly detection, recommendation systems, natural language processing (NLP), and computer vision. Map each problem type to appropriate algorithms and AWS services. This framework helps you quickly categorize exam scenarios and select appropriate solutions.

2. **Master SageMaker training workflows end-to-end** - Create complete training pipelines using SageMaker to build muscle memory. Start with simple built-in algorithms (XGBoost for structured data), progress to script mode with frameworks (TensorFlow, PyTorch, scikit-learn), then experiment with distributed training and hyperparameter tuning. Understand the training workflow: specify algorithm/container, configure data input (S3 location, content type, channels), define instance type and count, set hyperparameters, configure output location, and launch training job. Practice monitoring training with CloudWatch metrics, debugging with SageMaker Debugger, and analyzing results in SageMaker Studio. Hands-on experience prepares you for troubleshooting questions requiring deep workflow knowledge.

3. **Deep dive into regularization and optimization techniques** - Regularization prevents overfitting and is heavily tested. L1 regularization (Lasso) adds absolute value of weights to loss function, encouraging sparse features and feature selection. L2 regularization (Ridge) adds squared weights, encouraging small but non-zero weights. Dropout randomly disables neurons during training, preventing co-adaptation. Early stopping monitors validation performance and stops when it stops improving. Weight decay gradually reduces weights toward zero. Understand when to apply each technique and how to configure regularization strength (lambda/alpha hyperparameters). Practice identifying overfitting symptoms and selecting appropriate regularization strategies based on model architecture and data characteristics.

4. **Learn model evaluation comprehensively for all problem types** - For classification: accuracy (overall correctness), precision (positive predictions that are correct), recall (true positives found), F1 score (harmonic mean of precision/recall), confusion matrix (detailed prediction breakdown), ROC curve and AUC (threshold-independent performance). For regression: Root Mean Square Error (RMSE) penalizes large errors, Mean Absolute Error (MAE) treats all errors equally, R-squared indicates variance explained. For ranking: Mean Average Precision (MAP), Normalized Discounted Cumulative Gain (NDCG). Understand metric selection based on business requirements (precision for medical diagnosis avoiding false positives, recall for fraud detection catching all fraud) and how to interpret tradeoffs.

5. **Study SageMaker Model Registry and MLOps patterns** - Model Registry provides centralized model management with versioning, approval workflows, and deployment tracking. Understand the workflow: register models with metadata (metrics, approval status, description), organize in model packages and groups, track lineage (training data, code, parameters), implement approval workflows (pending → approved → rejected), and integrate with CI/CD pipelines. Learn A/B testing with production variants (traffic splitting between models), shadow mode (testing new models without affecting production), and model monitoring (detecting drift, performance degradation). These MLOps patterns are increasingly tested as ML engineering matures beyond one-time model training to continuous model lifecycle management.

---

## Task 2.1: Choose a modeling approach

### Knowledge Areas & AWS Documentation Reading List

#### 1. Capabilities and appropriate uses of ML algorithms to solve business problems

**Why:** Algorithm selection is fundamental to ML success and is the most tested topic in model development. Understanding which algorithm suits specific problem characteristics determines project success. For supervised learning with structured/tabular data: XGBoost excels at non-linear patterns with mixed data types, linear models are fast and interpretable for linearly separable problems, neural networks handle complex non-linear patterns but require more data. For unstructured data: Convolutional Neural Networks (CNNs) for images, Recurrent Neural Networks (RNNs)/Transformers for sequential data, pre-trained models (transfer learning) for limited training data. For unsupervised learning: K-means for spherical clusters with known K, DBSCAN for arbitrary cluster shapes with noise, Principal Component Analysis (PCA) for dimensionality reduction. The exam tests scenarios presenting business problems and data characteristics requiring you to justify algorithm selection considering accuracy requirements, interpretability needs, training time constraints, and inference latency requirements.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/algos.html" target="_blank">Amazon SageMaker Built-in Algorithms</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/algorithms-choose.html" target="_blank">Choosing the Right Algorithm</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/supervised-learning.html" target="_blank">Supervised Learning Algorithms</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/unsupervised-learning.html" target="_blank">Unsupervised Learning Algorithms</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/xgboost.html" target="_blank">XGBoost Algorithm</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/linear-learner.html" target="_blank">Linear Learner Algorithm</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/k-means.html" target="_blank">K-Means Algorithm</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/image-classification.html" target="_blank">Image Classification Algorithm</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/object-detection.html" target="_blank">Object Detection Algorithm</a>

#### 2. How to use AWS artificial intelligence (AI) services (for example, Amazon Translate, Amazon Transcribe, Amazon Rekognition, Amazon Bedrock) to solve specific business problems

**Why:** AWS AI services provide pre-trained models for common tasks, eliminating lengthy custom model development and training. The exam tests when to use AI services versus custom models. Amazon Rekognition analyzes images and videos (object/scene detection, facial analysis, celebrity recognition, custom labels for specialized detection), Amazon Transcribe converts speech to text (supports multiple languages, custom vocabulary, speaker identification), Amazon Translate provides neural machine translation (90+ languages, custom terminology), Amazon Comprehend extracts insights from text (entity recognition, sentiment analysis, topic modeling), Amazon Textract extracts text and data from documents (forms, tables, handwriting), and Amazon Bedrock provides foundation models for generative AI. Understanding service capabilities, pricing models, and integration patterns helps you recommend appropriate solutions balancing time-to-market, cost, accuracy, and customization needs.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/rekognition/latest/dg/" target="_blank">Amazon Rekognition Developer Guide</a>
- <a href="https://docs.aws.amazon.com/transcribe/latest/dg/" target="_blank">Amazon Transcribe Developer Guide</a>
- <a href="https://docs.aws.amazon.com/translate/latest/dg/" target="_blank">Amazon Translate Developer Guide</a>
- <a href="https://docs.aws.amazon.com/comprehend/latest/dg/" target="_blank">Amazon Comprehend Developer Guide</a>
- <a href="https://docs.aws.amazon.com/textract/latest/dg/" target="_blank">Amazon Textract Developer Guide</a>
- <a href="https://docs.aws.amazon.com/bedrock/latest/userguide/" target="_blank">Amazon Bedrock User Guide</a>
- <a href="https://aws.amazon.com/machine-learning/ai-services/" target="_blank">AWS AI Services Overview</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/ai-services.html" target="_blank">When to Use AI Services</a>

#### 3. How to consider interpretability during model selection or algorithm selection

**Why:** Model interpretability enables stakeholders to understand predictions and is increasingly required for regulated industries and high-stakes decisions. Linear models (linear regression, logistic regression) are highly interpretable with direct feature-to-prediction relationships. Decision trees provide visual rules. Rule-based models offer explicit logic. Neural networks are less interpretable (black boxes) but SageMaker Clarify provides post-hoc explainability. The exam tests scenarios where interpretability is required (medical diagnosis, loan decisions, regulatory compliance) versus where predictive accuracy is prioritized (ad click prediction, recommendation systems). Understanding the accuracy-interpretability tradeoff and methods to gain insights from complex models (SHAP values, feature importance, partial dependence plots) is critical for recommending appropriate solutions.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-model-explainability.html" target="_blank">Model Explainability with SageMaker Clarify</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-shapley-values.html" target="_blank">SHapley Additive exPlanations (SHAP)</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-feature-attribute-baselines.html" target="_blank">Feature Importance</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/model-governance.html" target="_blank">Interpretable Machine Learning</a>

#### 4. Amazon SageMaker AI built-in algorithms and when to apply them

**Why:** SageMaker provides 18+ optimized, scalable built-in algorithms that eliminate infrastructure management and provide production-ready implementations. Understanding when to use built-in algorithms versus custom implementations is critical for efficient ML engineering. Built-in algorithms offer: optimized implementations (GPU acceleration, distributed training), managed infrastructure (automatic scaling, monitoring), and battle-tested reliability. Use built-in algorithms when the problem matches algorithm capabilities (XGBoost for tabular classification/regression, Image Classification for custom image categories, DeepAR for time series forecasting). Use custom implementations when requiring novel architectures, research algorithms, or highly specialized domains. The exam tests algorithm selection based on problem type, input data format requirements, training performance needs, and feature availability in built-in versus custom implementations.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/algos.html" target="_blank">Use Amazon SageMaker Built-in Algorithms</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-algo-common-data-formats.html" target="_blank">Common Data Formats for Built-in Algorithms</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/xgboost.html" target="_blank">XGBoost Algorithm</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/blazingtext.html" target="_blank">BlazingText Algorithm</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/deepar.html" target="_blank">DeepAR Forecasting Algorithm</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/image-classification.html" target="_blank">Image Classification Algorithm</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/semantic-segmentation.html" target="_blank">Semantic Segmentation Algorithm</a>

### Skills & Corresponding Documentation

#### Assessing available data and problem complexity to determine the feasibility of an ML solution

**Why:** Not all business problems are suitable for ML, and assessing feasibility prevents wasted effort. The exam tests your ability to evaluate whether ML is appropriate given data availability, problem characteristics, and business constraints. ML is feasible when: sufficient labeled data exists (thousands to millions of examples depending on complexity), patterns exist in data (not pure random noise), problem is clearly defined with measurable success metrics, and ML provides value over rule-based approaches. ML is not feasible when: insufficient data, problem requires reasoning beyond pattern recognition, or simpler statistical methods suffice. Understanding these criteria and how to communicate tradeoffs to stakeholders is essential for scoping ML projects realistically.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/ml-problem-framing.html" target="_blank">Machine Learning Lens - Problem Framing</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/business-goal-identification.html" target="_blank">Assessing ML Feasibility</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/data-requirements.html" target="_blank">Data Requirements for ML</a>

#### Comparing and selecting appropriate ML models or algorithms to solve specific problems

**Why:** Comparing algorithms systematically ensures optimal selection for specific problems. The exam tests your methodology for comparing algorithms considering: problem type (classification, regression, clustering), data characteristics (structured/unstructured, size, dimensions), performance metrics (accuracy, precision, recall, RMSE), computational requirements (training time, inference latency), interpretability needs, and operational constraints. Create comparison frameworks evaluating algorithms on relevant criteria. For example, for fraud detection: compare XGBoost (high accuracy, fast training), neural networks (potentially higher accuracy, slower training, less interpretable), and rule-based systems (highly interpretable, may miss complex patterns). Understanding systematic comparison prevents selecting algorithms based on familiarity rather than suitability.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/algorithms-choose.html" target="_blank">Choosing an Algorithm</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/algos.html" target="_blank">Algorithm Comparison</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/experiments.html" target="_blank">SageMaker Experiments for Model Comparison</a>

#### Choosing built-in algorithms, foundation models, and solution templates (for example, in SageMaker JumpStart and Amazon Bedrock)

**Why:** SageMaker JumpStart provides pre-trained models and solution templates accelerating ML development. JumpStart offers: foundation models (text generation, image generation, embeddings), task-specific models (sentiment analysis, named entity recognition, object detection), and end-to-end solution templates (fraud detection, predictive maintenance, demand forecasting). Amazon Bedrock provides access to foundation models from AI21 Labs, Anthropic, Cohere, Meta, Stability AI, and Amazon. The exam tests when to use pre-trained models (limited training data, standard tasks, rapid deployment) versus training from scratch (unique domains, proprietary data, specialized requirements), and how to fine-tune pre-trained models with custom data to balance customization and efficiency.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/studio-jumpstart.html" target="_blank">SageMaker JumpStart</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/jumpstart-foundation-models.html" target="_blank">JumpStart Foundation Models</a>
- <a href="https://docs.aws.amazon.com/bedrock/latest/userguide/models-supported.html" target="_blank">Amazon Bedrock Foundation Models</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/jumpstart-solutions.html" target="_blank">Solution Templates in JumpStart</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/jumpstart-fine-tune.html" target="_blank">Fine-tuning Models</a>

#### Selecting models or algorithms based on costs

**Why:** Training and inference costs significantly impact ML project viability and are tested through cost optimization scenarios. Training costs include compute instance hours (GPU instances expensive but faster, CPU instances cheaper but slower), storage costs (training data, model artifacts), and data transfer costs. Inference costs include endpoint instance hours (real-time endpoints run continuously), invocations (serverless inference pay-per-request), and data transfer. The exam tests cost optimization strategies: using Spot instances for training (up to 90% savings, fault-tolerant workloads), serverless inference for infrequent predictions, auto-scaling for variable traffic, smaller models reducing inference costs, and quantization reducing storage and memory. Understanding cost tradeoffs between model complexity, accuracy, and operational expenses is critical for sustainable ML systems.

**AWS Documentation:**
- <a href="https://aws.amazon.com/sagemaker/pricing/" target="_blank">SageMaker Pricing</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-managed-spot-training.html" target="_blank">Managed Spot Training</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/serverless-endpoints.html" target="_blank">Serverless Inference</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/cost-optimization.html" target="_blank">Cost Optimization for ML</a>

#### Selecting AI services to solve common business needs

**Why:** Knowing when AI services provide better solutions than custom models is a strategic decision point tested in the exam. AI services are optimal when: the problem matches service capabilities (image classification, transcription, translation), you need rapid deployment, you lack ML expertise, and you want AWS-managed models with continuous improvements. Custom models are better when: the domain is highly specialized (rare diseases, niche industries), you need full control over model architecture, or you have unique data providing competitive advantage. The exam tests scenarios requiring you to evaluate business requirements (time-to-market, budget, accuracy thresholds, customization needs) and recommend AI services versus custom development, often involving hybrid approaches where AI services handle generic tasks while custom models address specialized requirements.

**AWS Documentation:**
- <a href="https://aws.amazon.com/machine-learning/ai-services/" target="_blank">AI Services Overview</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/ai-services.html" target="_blank">When to Use AI Services vs Custom Models</a>
- <a href="https://docs.aws.amazon.com/architecture-diagrams/latest/ai-ml-services/ai-ml-services.html" target="_blank">Integrating AI Services</a>

---

## Task 2.2: Train and refine models

### Knowledge Areas & AWS Documentation Reading List

#### 1. Elements in the training process (for example, epoch, steps, batch size)

**Why:** Understanding training terminology is fundamental for configuring training jobs and interpreting training progress. An epoch is one complete pass through the entire training dataset. A step (iteration) processes one mini-batch. Batch size determines examples processed per step (larger batches increase training throughput and stability but require more memory; smaller batches provide more frequent updates and better generalization). Total steps = (dataset_size / batch_size) × epochs. The exam tests your understanding of how these parameters affect training: more epochs risk overfitting but ensure convergence, larger batch sizes speed training but may reduce generalization, and step count determines how frequently metrics are logged. Properly configuring these parameters balances training time, memory usage, and model quality.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/training-parameters.html" target="_blank">Training Configuration</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/algos.html" target="_blank">Hyperparameters for Built-in Algorithms</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/training-metrics.html" target="_blank">Understanding Training Metrics</a>

#### 2. Methods to reduce model training time (for example, early stopping, distributed training)

**Why:** Reducing training time lowers costs and accelerates experimentation, making time optimization techniques heavily tested. Early stopping monitors validation metrics and stops training when performance stops improving (prevents overfitting and wasted compute). Distributed training spreads training across multiple instances: data parallelism replicates the model and splits data across workers (most common, scales to many workers), model parallelism splits large models across workers (for models too large for single GPU). SageMaker supports distributed training with Horovod, PyTorch Distributed Data Parallel, and TensorFlow distributed strategies. The exam tests when to use each technique: early stopping for all training jobs, distributed training when single-instance training is too slow or model doesn't fit in memory, and understanding scaling efficiency (2× instances doesn't guarantee 2× speedup due to communication overhead).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/automatic-model-tuning-early-stopping.html" target="_blank">Early Stopping</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/distributed-training.html" target="_blank">Distributed Training</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/data-parallel.html" target="_blank">Data Parallel Training</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-parallel.html" target="_blank">Model Parallel Training</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/training-compiler.html" target="_blank">Training Compiler</a>

#### 3. Factors that influence model size

**Why:** Model size affects storage costs, inference latency, and memory requirements. Factors increasing model size include: more parameters (layers, neurons, trees), higher precision (float32 versus float16), embedding dimensions, and vocabulary size for NLP models. The exam tests strategies to reduce model size: pruning (removing less important weights), quantization (reducing precision from float32 to int8), knowledge distillation (training smaller student model to mimic larger teacher), feature selection (reducing input dimensions), and architecture changes (MobileNet versus ResNet for mobile deployment). Understanding size-accuracy tradeoffs helps you optimize models for deployment constraints (edge devices, latency-sensitive applications) while maintaining acceptable performance.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/neo-edge-devices.html" target="_blank">Model Compression</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/neo.html" target="_blank">SageMaker Neo for Model Optimization</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/neo-compilation-preparing-model.html" target="_blank">Quantization</a>

#### 4. Methods to improve model performance

**Why:** Improving model performance is a core ML engineering skill tested through troubleshooting scenarios. Methods include: gathering more training data (often most effective), feature engineering (creating predictive features), hyperparameter tuning (optimizing learning rate, regularization, architecture), ensembling (combining multiple models), data augmentation (artificially expanding training set), transfer learning (starting from pre-trained models), and architecture improvements (deeper networks, attention mechanisms). The exam tests systematic approaches to improvement: establish baseline performance, identify bottlenecks through analysis (underfitting versus overfitting), hypothesize improvements, implement changes, and measure impact. Understanding which method addresses specific performance issues (more data for overfitting, more capacity for underfitting, better features for poor baseline) is critical.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-train-storage.html" target="_blank">Improving Model Performance</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/automatic-model-tuning.html" target="_blank">Hyperparameter Tuning</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/jumpstart-fine-tune.html" target="_blank">Transfer Learning</a>

#### 5. Benefits of regularization techniques (for example, dropout, weight decay, L1 and L2)

**Why:** Regularization prevents overfitting and is fundamental to generalizable models. L1 regularization (Lasso) adds sum of absolute weights to loss function, encouraging sparsity (many weights become exactly zero), providing automatic feature selection. L2 regularization (Ridge) adds sum of squared weights, encouraging small weights evenly distributed across features. Dropout randomly drops neurons during training, preventing co-adaptation and acting as implicit ensemble. Weight decay gradually reduces weights toward zero during optimization. The exam tests when to apply regularization (overfitting symptoms: large gap between training and validation performance), how to configure strength (lambda/alpha parameters: higher values mean stronger regularization), and understanding tradeoffs (regularization reduces overfitting but may underfit if too strong).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/algos.html" target="_blank">Regularization in SageMaker</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/xgboost-hyperparameters.html" target="_blank">XGBoost Regularization Parameters</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/image-classification-hyperparameters.html" target="_blank">Neural Network Regularization</a>

#### 6. Hyperparameter tuning techniques (for example, random search, Bayesian optimization)

**Why:** Hyperparameter tuning optimizes model performance but can be expensive, making efficient tuning strategies critical. Random search randomly samples hyperparameter combinations (simple, easily parallelizable, surprisingly effective). Grid search exhaustively tests all combinations (thorough but exponentially expensive as dimensions increase). Bayesian optimization uses probabilistic models to predict promising hyperparameters based on previous results (SageMaker Automatic Model Tuning default, most sample-efficient). The exam tests understanding of tuning strategies: Bayesian optimization for expensive training (minimizes training jobs needed), random search for inexpensive training or many hyperparameters, and how to configure tuning ranges (log scale for learning rate, linear for regularization strength). Understanding warm start tuning (starting from previous tuning job results) further optimizes costs.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/automatic-model-tuning.html" target="_blank">Automatic Model Tuning</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/automatic-model-tuning-how-it-works.html" target="_blank">How Hyperparameter Tuning Works</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/automatic-model-tuning-considerations.html" target="_blank">Tuning Strategies</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/automatic-model-tuning-warm-start.html" target="_blank">Warm Start Tuning</a>

#### 7. Model hyperparameters and their effects on model performance (for example, number of trees in a tree-based model, number of layers in a neural network)

**Why:** Hyperparameters control model architecture and training, directly affecting performance, and the exam extensively tests hyperparameter knowledge. For tree-based models: num_trees (more trees improve performance but risk overfitting and slow inference), max_depth (deeper trees capture complex patterns but overfit), min_child_weight (prevents overfitting by requiring minimum samples per leaf). For neural networks: num_layers and num_neurons (more capacity handles complex patterns but overfits with insufficient data), learning_rate (too high causes divergence, too low causes slow convergence), dropout_rate (higher values increase regularization). The exam tests ability to diagnose performance issues from hyperparameter configurations and recommend adjustments (increasing capacity for underfitting, adding regularization for overfitting).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/xgboost-hyperparameters.html" target="_blank">XGBoost Hyperparameters</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/image-classification-hyperparameters.html" target="_blank">Neural Network Hyperparameters</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/ll-hyperparameters.html" target="_blank">Linear Learner Hyperparameters</a>

#### 8. Methods to integrate models that were built outside SageMaker AI into SageMaker AI

**Why:** Organizations often have existing models trained elsewhere (on-premises, other clouds, local development) that need SageMaker deployment benefits (managed infrastructure, auto-scaling, monitoring). Integration methods include: packaging models in Docker containers meeting SageMaker inference specifications, using SageMaker Model Registry to register external models, leveraging bring-your-own-container (BYOC) for custom frameworks, and using multi-model endpoints to host multiple models. The exam tests understanding of container requirements (expose /ping and /invocations endpoints, handle inference requests/responses correctly), model artifact packaging (model files, dependencies, inference code), and deployment patterns that enable using SageMaker's production infrastructure for externally-trained models.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/adapt-inference-container.html" target="_blank">Bring Your Own Container</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/docker-containers.html" target="_blank">Using Docker Containers with SageMaker</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/adapt-inference-container.html" target="_blank">Custom Inference Container Specification</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-registry.html" target="_blank">SageMaker Model Registry</a>

### Skills & Corresponding Documentation

#### Using SageMaker AI built-in algorithms and common ML libraries to develop ML models

**Why:** Practical implementation skills with built-in algorithms are heavily tested. You must know how to configure training jobs specifying algorithm image URI, input data configuration (S3 locations, content types, channels), instance types and counts, hyperparameters, and output locations. Common implementations include XGBoost for tabular classification/regression, Linear Learner for linear models with automatic feature processing, BlazingText for text classification and embeddings, Image Classification for custom image categories, and DeepAR for time series forecasting. The exam tests ability to translate business requirements into training configurations, troubleshoot training failures (wrong data format, incorrect hyperparameters, insufficient resources), and optimize training performance.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/algos.html" target="_blank">Using Built-in Algorithms</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/ex1-train-model.html" target="_blank">Training a Model with a Built-in Algorithm</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-algo-common-data-formats.html" target="_blank">Common Data Formats</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/xgboost-examples.html" target="_blank">XGBoost Example</a>

#### Using SageMaker AI script mode with SageMaker AI supported frameworks to train models (for example, TensorFlow, PyTorch)

**Why:** Script mode enables using popular ML frameworks (TensorFlow, PyTorch, scikit-learn, Hugging Face) with custom training scripts while leveraging SageMaker infrastructure. You provide training script, and SageMaker handles infrastructure provisioning, data loading, distributed training setup, metric logging, and model artifact management. The exam tests understanding of script mode requirements (entry point script structure, handling training data from /opt/ml/input/data, saving models to /opt/ml/model), framework-specific configurations (TensorFlow Estimator, PyTorch Estimator), and debugging scripts that fail in SageMaker but work locally (environment differences, file paths, dependencies).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/frameworks.html" target="_blank">Using Script Mode</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/tf.html" target="_blank">TensorFlow in SageMaker</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/pytorch.html" target="_blank">PyTorch in SageMaker</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/adapt-training-container.html" target="_blank">Adapting Your Training Script</a>
- <a href="https://github.com/aws/sagemaker-training-toolkit" target="_blank">SageMaker Training Toolkit</a>

#### Using custom datasets to fine-tune pre-trained models (for example, Amazon Bedrock, SageMaker JumpStart)

**Why:** Fine-tuning pre-trained models with custom data combines the benefits of transfer learning (leveraging knowledge from large pre-training datasets) with domain-specific adaptation. JumpStart provides fine-tuning workflows for foundation models, computer vision models (ResNet, MobileNet), and NLP models (BERT, GPT). Amazon Bedrock enables fine-tuning foundation models with custom data. The exam tests understanding of fine-tuning workflows (selecting pre-trained model, preparing custom training data in required format, configuring fine-tuning job with appropriate hyperparameters, evaluating fine-tuned model), when fine-tuning provides value versus training from scratch (limited custom data, standard architecture, transfer learning benefits), and cost considerations (fine-tuning is faster and cheaper than full training).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/jumpstart-fine-tune.html" target="_blank">Fine-tuning Models in JumpStart</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/image-classification.html" target="_blank">Transfer Learning</a>
- <a href="https://docs.aws.amazon.com/bedrock/latest/userguide/custom-models.html" target="_blank">Fine-tuning Foundation Models in Bedrock</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/jumpstart-fine-tune.html" target="_blank">Preparing Data for Fine-tuning</a>

#### Performing hyperparameter tuning (for example, by using SageMaker AI automatic model tuning [AMT])

**Why:** Automatic Model Tuning (AMT) optimizes hyperparameters using Bayesian optimization to find the best configuration with minimal training jobs. Configuration includes defining tuning objective (metric to optimize), hyperparameter ranges (continuous, integer, categorical), tuning strategy (Bayesian, random, grid), and resource limits (max training jobs, max parallel jobs). The exam tests understanding of tuning configuration (defining appropriate ranges, selecting objective metric, setting parallel jobs to balance speed and efficiency), interpreting tuning results (best hyperparameters, convergence trends), troubleshooting poor tuning outcomes (ranges too narrow, objective metric issues), and cost optimization (early stopping, warm start).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/automatic-model-tuning.html" target="_blank">Automatic Model Tuning</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/automatic-model-tuning-define-ranges.html" target="_blank">Defining Hyperparameter Ranges</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/automatic-model-tuning-define-metrics.html" target="_blank">Tuning Metrics</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/automatic-model-tuning-considerations.html" target="_blank">Best Practices for Hyperparameter Tuning</a>

#### Integrating automated hyperparameter optimization capabilities

**Why:** Integrating hyperparameter tuning into ML workflows enables systematic model optimization. Integration patterns include launching tuning jobs from SageMaker Studio, using SageMaker Pipelines to automate tuning as part of model development workflows, programmatic tuning job creation using boto3, and incorporating tuning results into model registry for deployment. The exam tests understanding of end-to-end workflows where tuning isn't manual but automated as part of continuous model improvement, how to handle tuning job failures and retries, and implementing approval gates where models are only deployed if tuning achieves performance thresholds.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/automatic-model-tuning.html" target="_blank">Automatic Model Tuning with SageMaker</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/pipelines.html" target="_blank">SageMaker Pipelines</a>
- <a href="https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sagemaker.html#SageMaker.Client.create_hyper_parameter_tuning_job" target="_blank">Boto3 Hyperparameter Tuning API</a>

#### Preventing model overfitting, underfitting, and catastrophic forgetting (for example, by using regularization techniques, feature selection)

**Why:** Preventing performance issues requires understanding root causes and appropriate remediation. Overfitting (model memorizes training data) is addressed with regularization (L1/L2, dropout), more training data, simpler architectures, or early stopping. Underfitting (model too simple for data complexity) requires more model capacity, better features, or longer training. Catastrophic forgetting (model forgets previous tasks when learning new tasks) affects continual learning scenarios and is mitigated with elastic weight consolidation, experience replay, or multi-task learning. The exam tests diagnosing issues from learning curves and metrics, selecting appropriate remediation strategies, and understanding when to apply each technique.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/automatic-model-tuning-early-stopping.html" target="_blank">Preventing Overfitting</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/xgboost-hyperparameters.html" target="_blank">Regularization Techniques</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-feature-attribute-baselines.html" target="_blank">Feature Selection</a>

#### Combining multiple training models to improve performance (for example, ensembling, stacking, boosting)

**Why:** Ensemble methods combine multiple models to improve performance beyond individual models. Bagging (Bootstrap Aggregating) trains multiple models on random subsets and averages predictions (Random Forest). Boosting trains models sequentially where each model corrects previous errors (XGBoost, AdaBoost). Stacking trains meta-model on predictions from base models. The exam tests when ensembles provide value (improved accuracy, reduced variance), understanding tradeoffs (complexity, inference latency, cost), and implementation patterns (SageMaker Inference Pipelines for multi-model inference, combining predictions in application layer).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/xgboost.html" target="_blank">Ensemble Methods</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/inference-pipelines.html" target="_blank">SageMaker Inference Pipelines</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/multi-model-endpoints.html" target="_blank">Multi-Model Endpoints</a>

#### Reducing model size (for example, by altering data types, pruning, updating feature selection, compression)

**Why:** Model size reduction enables deployment to resource-constrained environments (edge devices, mobile) and reduces inference costs. Techniques include quantization (converting float32 to int8 reduces size 75% with minimal accuracy loss), pruning (removing unimportant weights), knowledge distillation (training smaller student model), and architecture changes (MobileNet, EfficientNet for mobile). SageMaker Neo compiles models for specific hardware, optimizing size and performance. The exam tests when size reduction is necessary (edge deployment, latency requirements, cost constraints), selecting appropriate techniques based on accuracy-size tradeoffs, and using Neo for hardware-optimized inference.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/neo.html" target="_blank">SageMaker Neo</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/neo-edge-devices.html" target="_blank">Model Optimization</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/neo-compilation-preparing-model.html" target="_blank">Quantization</a>

#### Managing model versions for repeatability and audits (for example, by using the SageMaker Model Registry)

**Why:** Model versioning enables reproducibility, A/B testing, rollback, and audit trails required for regulated industries. SageMaker Model Registry provides centralized model catalog with version control, approval workflows, lineage tracking, and deployment history. The exam tests model registry workflows (registering models with metadata, creating model packages, organizing in model groups, implementing approval workflows, tracking model lineage from training data through deployment), integration with CI/CD pipelines for automated model deployment, and how versioning enables safe model updates (deploying new version alongside production, validating performance, gradually shifting traffic).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-registry.html" target="_blank">SageMaker Model Registry</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-registry-version.html" target="_blank">Registering a Model Version</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-registry-approve.html" target="_blank">Model Approval</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/lineage-tracking.html" target="_blank">Model Lineage</a>

---

## Task 2.3: Analyze model performance

### Knowledge Areas & AWS Documentation Reading List

#### 1. Model evaluation techniques and metrics (for example, confusion matrix, heat maps, F1 score, accuracy, precision, recall, Root Mean Square Error [RMSE], receiver operating characteristic [ROC], Area Under the ROC Curve [AUC])

**Why:** Selecting and interpreting evaluation metrics is critical for assessing model quality and is extensively tested. For classification: accuracy (overall correctness, misleading for imbalanced datasets), precision (positive predictions that are correct, important when false positives are costly), recall (true positives found, critical when false negatives are costly), F1 score (harmonic mean balancing precision and recall), confusion matrix (detailed breakdown of predictions), ROC curve (visualizing true positive rate versus false positive rate across thresholds), and AUC (threshold-independent performance summary). For regression: RMSE (penalizes large errors more), MAE (equal treatment of all errors), R-squared (variance explained). The exam tests metric selection based on business requirements (medical diagnosis prioritizes recall, spam detection prioritizes precision), interpreting metrics to diagnose issues, and understanding when metrics are misleading (high accuracy on imbalanced data).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-monitor-model-quality.html" target="_blank">Evaluating ML Models</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-monitor-model-quality-metrics.html" target="_blank">Classification Metrics</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-monitor-model-quality-metrics.html" target="_blank">Regression Metrics</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-model-monitor-metrics.html" target="_blank">Understanding Model Metrics</a>

#### 2. Methods to create performance baselines

**Why:** Baselines provide context for evaluating whether model performance is acceptable. Simple baselines include: random guessing (for classification, accuracy = 1/num_classes; for regression, predict mean), majority class prediction (always predict most common class), rule-based systems (domain expert rules), and simple models (linear regression, decision stump). The exam tests understanding that models must significantly outperform baselines to provide value, how to establish realistic performance targets (comparing to human performance, existing systems, business requirements), and using baselines to diagnose issues (if model barely beats random guessing, fundamental problem exists with data or approach).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-monitor-model-quality.html" target="_blank">Model Evaluation</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-monitor-model-quality-baseline.html" target="_blank">Setting Baselines</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/experiments.html" target="_blank">Experiments for Baseline Comparison</a>

#### 3. Methods to identify model overfitting and underfitting

**Why:** Diagnosing fit issues is fundamental to improving models and is tested through learning curve analysis. Overfitting: training performance significantly better than validation performance (large gap), manifests as low training error but high validation/test error. Underfitting: both training and validation performance are poor (parallel high error). Good fit: training and validation curves converge to low error. The exam tests ability to diagnose fit from learning curves, understanding symptoms in metrics (overfitting shows in performance degradation on holdout data), and recommending remediation (regularization for overfitting, more capacity for underfitting).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/training-metrics.html" target="_blank">Analyzing Training Job</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/debugger-training-issues.html" target="_blank">Debugger for Training Issues</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/model-evaluation.html" target="_blank">Model Evaluation Best Practices</a>

#### 4. Metrics available in SageMaker Clarify to gain insights into ML training data and models

**Why:** SageMaker Clarify provides bias detection and model explainability metrics essential for responsible AI. Bias metrics include pre-training (CI, DPL) and post-training bias metrics (disparate impact, equal opportunity difference). Explainability features include SHAP values showing feature importance for individual predictions, partial dependence plots showing feature effects, and feature attributions. The exam tests when to use Clarify (regulated industries, fairness requirements, explainability needs), interpreting Clarify reports (identifying biased features, understanding model reasoning), and integrating Clarify into ML workflows (running bias analysis before training, explainability analysis after training).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify.html" target="_blank">SageMaker Clarify</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-detect-data-bias.html" target="_blank">Bias Detection</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-model-explainability.html" target="_blank">Model Explainability</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-shapley-values.html" target="_blank">SHAP Values</a>

#### 5. Convergence issues

**Why:** Training failures due to convergence issues waste time and resources. Common issues include: diverging loss (loss increases rather than decreases, caused by learning rate too high or gradient explosion), oscillating loss (loss fluctuates wildly, may indicate learning rate too high or batch size too small), stalling (loss stops decreasing, may indicate learning rate too low, local minimum, or vanishing gradients). The exam tests diagnosing convergence issues from training curves, understanding causes (hyperparameter misconfiguration, architecture problems, data issues), and remediation strategies (adjusting learning rate, gradient clipping, batch normalization, different optimizers).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/debugger.html" target="_blank">SageMaker Debugger</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/debugger-training-issues.html" target="_blank">Debugging Training Issues</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/debugger-built-in-rules.html" target="_blank">Built-in Rules</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/debugger-troubleshooting.html" target="_blank">Troubleshooting Training</a>

### Skills & Corresponding Documentation

#### Selecting and interpreting evaluation metrics and detecting model bias

**Why:** Metric selection must align with business objectives and is tested through scenarios presenting business requirements. For fraud detection (rare events, false negatives costly), prioritize recall. For spam detection (false positives annoy users), prioritize precision. For medical diagnosis (serious consequences), require high recall and precision (high F1). For ranking (search results, recommendations), use MAP or NDCG. The exam tests translating business requirements into appropriate metrics, interpreting metric values to understand model behavior, detecting bias in model predictions using Clarify, and recommending remediation when bias or poor performance is detected.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-monitor-model-quality-metrics.html" target="_blank">Model Evaluation Metrics</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-post-training-bias-metric.html" target="_blank">Detecting Post-training Bias</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-measure-post-training-bias.html" target="_blank">SageMaker Clarify Bias Metrics</a>

#### Assessing tradeoffs between model performance, training time, and cost

**Why:** Real-world ML requires balancing multiple objectives: accuracy, speed, and cost. Higher accuracy often requires more complex models (longer training, higher costs), more training data (storage, labeling costs), and more hyperparameter tuning (additional training jobs). The exam tests scenarios requiring you to make tradeoff decisions: deploy simpler model with 90% accuracy and 1-hour training, or complex model with 92% accuracy and 10-hour training? Understanding when marginal accuracy improvements justify additional costs versus when good-enough models suffice enables pragmatic ML engineering decisions. Consider business impact (revenue increase from better predictions), operational costs (training, inference), and time-to-market constraints.

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/cost-optimization.html" target="_blank">Cost Optimization for ML</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/design-principles.html" target="_blank">Performance vs Cost Tradeoffs</a>
- <a href="https://aws.amazon.com/sagemaker/pricing/" target="_blank">SageMaker Pricing</a>

#### Performing reproducible experiments by using AWS services

**Why:** Reproducibility enables systematic experimentation, debugging, and regulatory compliance. SageMaker Experiments tracks training runs with parameters, metrics, and artifacts. Best practices include: version control for code (Git), tracking datasets with checksums, recording all hyperparameters, logging random seeds, using Docker for environment reproducibility, and tagging resources for lineage tracking. The exam tests understanding of why reproducibility matters (validating results, debugging issues, audit requirements), how to implement reproducible workflows (experiment tracking, version control, documentation), and troubleshooting non-reproducible results (random seed not set, data shuffling inconsistent, environment differences).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/experiments.html" target="_blank">SageMaker Experiments</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/experiments-create.html" target="_blank">Track and Compare Experiments</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/lineage-tracking.html" target="_blank">Lineage Tracking</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/model-governance.html" target="_blank">Reproducibility Best Practices</a>

#### Comparing the performance of a shadow variant to the performance of a production variant

**Why:** Shadow mode enables safe model validation by routing copies of production traffic to new models without affecting production responses. Shadow variant receives same inputs as production but responses are logged for analysis, not returned to users. This validates new model performance on real production data before full deployment. The exam tests understanding of shadow mode benefits (detect performance issues before impact, validate on production distribution), configuration (creating shadow variant endpoint, traffic mirroring percentage), analysis (comparing shadow versus production metrics), and deciding when shadow model is ready for production (performance meets thresholds, no unexpected behaviors).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-shadow-deployment.html" target="_blank">Shadow Variants</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-ab-testing.html" target="_blank">Deploying Shadow Tests</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-ab-testing.html" target="_blank">Production Variants</a>

#### Using SageMaker Clarify to interpret model outputs

**Why:** Model interpretability builds trust and satisfies regulatory requirements. Clarify generates explanations showing which features influenced predictions and by how much. SHAP values provide feature attributions for individual predictions (positive values increase prediction, negative decrease). Partial dependence plots show how features affect predictions on average. The exam tests scenarios requiring model explanation (loan rejection explanation, medical diagnosis reasoning, regulatory compliance), understanding explanation outputs (interpreting SHAP values, identifying influential features), and using explainability to improve models (removing uninformative features, detecting data leakage from unexpectedly important features).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-model-explainability.html" target="_blank">Explainability with SageMaker Clarify</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-feature-attribute-shap-baselines.html" target="_blank">SHAP Baselines</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-processing-job-run.html" target="_blank">Generating Explanations</a>

#### Using SageMaker Model Debugger to debug model convergence

**Why:** Debugger automatically detects training issues by monitoring tensors (weights, gradients, outputs) during training. Built-in rules detect: vanishing/exploding gradients, overfitting, poor weight initialization, tensor value issues (NaN, infinity), and stalled training. The exam tests understanding of when to use Debugger (training failures, unexpected poor performance, convergence issues), interpreting Debugger outputs (rule violations, tensor analysis), and remediation strategies based on detected issues (adjust learning rate for exploding gradients, change initialization for dead neurons, add regularization for overfitting).

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/debugger.html" target="_blank">SageMaker Debugger</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/debugger-built-in-rules.html" target="_blank">Built-in Debugger Rules</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/debugger-analyze-data.html" target="_blank">Analyzing Training with Debugger</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/debugger-training-issues.html" target="_blank">Troubleshooting Training Issues</a>

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/sagemaker/faqs/" target="_blank">Amazon SageMaker FAQs</a>
- <a href="https://aws.amazon.com/rekognition/faqs/" target="_blank">Amazon Rekognition FAQs</a>
- <a href="https://aws.amazon.com/transcribe/faqs/" target="_blank">Amazon Transcribe FAQs</a>
- <a href="https://aws.amazon.com/translate/faqs/" target="_blank">Amazon Translate FAQs</a>
- <a href="https://aws.amazon.com/comprehend/faqs/" target="_blank">Amazon Comprehend FAQs</a>
- <a href="https://aws.amazon.com/textract/faqs/" target="_blank">Amazon Textract FAQs</a>
- <a href="https://aws.amazon.com/bedrock/faqs/" target="_blank">Amazon Bedrock FAQs</a>
- <a href="https://aws.amazon.com/sagemaker/faqs/" target="_blank">SageMaker Model Registry FAQs</a>

---

## AWS Whitepapers

- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/machine-learning-lens.html" target="_blank">Machine Learning Lens - AWS Well-Architected Framework</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/model-development.html" target="_blank">Model Development</a>
- <a href="https://aws.amazon.com/architecture/machine-learning/" target="_blank">Best Practices for Machine Learning Model Development</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/hyperparameter-optimization.html" target="_blank">Hyperparameter Optimization</a>
- <a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/model-governance.html" target="_blank">Model Governance</a>
- <a href="https://aws.amazon.com/machine-learning/responsible-ai/" target="_blank">Responsible AI</a>

---

## Final Thoughts

Domain 2 focuses on the core ML engineering skills of model development - selecting appropriate algorithms, training efficiently, and evaluating rigorously. Master algorithm selection by problem type, understanding when built-in SageMaker algorithms are optimal versus custom implementations. Hyperparameter tuning is central to achieving strong model performance, so invest time understanding Bayesian optimization with SageMaker AMT and efficient tuning strategies. Model evaluation requires deep metric knowledge - know when to prioritize precision versus recall, how to interpret learning curves to diagnose overfitting/underfitting, and use SageMaker Clarify for bias detection and explainability. SageMaker Debugger helps troubleshoot training convergence issues that waste resources. Model Registry and Experiments enable reproducible ML engineering and systematic model management. Success in this domain requires both theoretical ML knowledge and practical SageMaker implementation skills, so complement documentation study with extensive hands-on training jobs across different problem types, algorithms, and optimization techniques.
