# AWS Certified AI Practitioner (AIF-C01) Domain 1
## Fundamentals of AI and ML

**Official Exam Guide:** <a href="https://aws.amazon.com/certification/certified-ai-practitioner/" target="_blank">AWS Certified AI Practitioner Exam Guide</a>  
**Skill Builder:** <a href="https://skillbuilder.aws/learning-plans/ai-practitioner" target="_blank">AWS AI Practitioner Learning Plan</a>

---

## Domain Overview

**Domain Weight:** 20% of the exam

This domain tests your understanding of fundamental AI and ML concepts, terminology, and the AWS services that support AI/ML workloads.

---

## How to Study This Domain Effectively

### Study Tips

1. **Understand AI/ML terminology** - Know the difference between AI, ML, deep learning, supervised vs unsupervised learning, classification vs regression, and other fundamental concepts. The exam tests whether you can identify correct definitions and use cases.

2. **Learn the ML workflow** - Understand the complete ML lifecycle: data collection → data preparation → model training → model evaluation → model deployment → monitoring. Questions often ask which step addresses a specific problem.

3. **Know AWS AI/ML services by use case** - Group services by what they do: SageMaker (build/train/deploy), Rekognition (computer vision), Comprehend (NLP), Polly (text-to-speech), etc. Match services to business scenarios.

4. **Understand data requirements** - ML success depends on quality data. Know concepts like data labeling, feature engineering, training/validation/test splits, and data bias. Questions test whether you understand what makes good training data.

5. **Focus on practical applications** - Understand real-world use cases for different ML types (image recognition, sentiment analysis, forecasting, recommendation systems). The exam presents business scenarios and asks you to identify appropriate ML approaches.

### Recommended Approach

1. **Start with AI/ML fundamentals** - Learn basic concepts, terminology, and the difference between AI, ML, and deep learning
2. **Study the ML workflow** - Understand each phase from data preparation through deployment
3. **Learn AWS AI services** - Study Amazon SageMaker, Rekognition, Comprehend, Polly, Translate, Transcribe, Lex, Kendra
4. **Understand model concepts** - Training, inference, overfitting/underfitting, accuracy metrics
5. **Review responsible AI** - Bias, fairness, explainability (connects to Domain 4)

---

## Task 1.1: Define basic AI concepts and terminology

### Knowledge Areas & AWS Documentation

#### 1. Artificial Intelligence (AI), Machine Learning (ML), and Deep Learning

**Why:** Understanding the relationship between AI, ML, and deep learning is fundamental. AI is the broadest concept (machines simulating human intelligence), ML is a subset (systems learning from data), and deep learning is a subset of ML (using neural networks). Exam questions test whether you can identify which term applies to specific scenarios.

**Key Concepts:**
- **AI** - Machines performing tasks that typically require human intelligence
- **ML** - Algorithms that improve through experience/data
- **Deep Learning** - ML using neural networks with multiple layers
- **Neural Networks** - Computing systems inspired by biological neural networks

**AWS Documentation:**
- <a href="https://aws.amazon.com/what-is/artificial-intelligence/" target="_blank">What is Artificial Intelligence?</a>
- <a href="https://aws.amazon.com/what-is/machine-learning/" target="_blank">What is Machine Learning?</a>
- <a href="https://aws.amazon.com/deep-learning/" target="_blank">Deep Learning on AWS</a>
- <a href="https://aws.amazon.com/machine-learning/" target="_blank">Machine Learning on AWS</a>

#### 2. Supervised Learning, Unsupervised Learning, and Reinforcement Learning

**Why:** These are the three main ML approaches, each suited for different problems. Supervised learning uses labeled data (classification, regression), unsupervised learning finds patterns in unlabeled data (clustering), and reinforcement learning learns through trial and error. Exam questions present scenarios and ask which learning type applies.

**Key Concepts:**
- **Supervised Learning** - Training with labeled data (input-output pairs)
  - Classification (categorizing data)
  - Regression (predicting continuous values)
- **Unsupervised Learning** - Finding patterns in unlabeled data
  - Clustering (grouping similar items)
  - Dimensionality reduction
- **Reinforcement Learning** - Learning through rewards and penalties
  - Agent, environment, actions, rewards

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/algorithms-choose.html" target="_blank">Supervised Learning</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/unsupervised-learning.html" target="_blank">Unsupervised Learning</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/reinforcement-learning.html" target="_blank">Amazon SageMaker RL</a>

#### 3. Classification, Regression, Clustering, and Forecasting

**Why:** These are common ML problem types. Understanding the difference helps you identify the right approach for business scenarios. Classification assigns categories (spam/not spam), regression predicts numbers (house prices), clustering groups similar items (customer segments), forecasting predicts future values (sales trends).

**Key Concepts:**
- **Classification** - Predicting categories (binary or multi-class)
- **Regression** - Predicting continuous numerical values
- **Clustering** - Grouping similar data points
- **Forecasting** - Predicting future trends based on historical data

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/algos.html" target="_blank">Amazon SageMaker Built-in Algorithms</a>
- <a href="https://docs.aws.amazon.com/forecast/latest/dg/what-is-forecast.html" target="_blank">Time Series Forecasting</a>

---

## Task 1.2: Identify practical use cases for AI

### Knowledge Areas & AWS Documentation

#### 1. Computer Vision (image and video analysis)

**Why:** Computer vision analyzes visual content. Understanding use cases (object detection, facial recognition, content moderation, medical imaging) helps you identify when to use vision-based AI services like Amazon Rekognition.

**Use Cases:**
- Object and scene detection
- Facial analysis and recognition
- Text extraction from images (OCR)
- Content moderation
- Video analysis

**AWS Services:**
- **Amazon Rekognition** - Image and video analysis
- **Amazon Textract** - Extract text and data from documents

**AWS Documentation:**
- <a href="https://aws.amazon.com/rekognition/" target="_blank">Amazon Rekognition</a>
- <a href="https://aws.amazon.com/textract/" target="_blank">Amazon Textract</a>
- <a href="https://aws.amazon.com/computer-vision/" target="_blank">Computer Vision on AWS</a>

#### 2. Natural Language Processing (NLP)

**Why:** NLP enables machines to understand and generate human language. Use cases include sentiment analysis, translation, chatbots, and text extraction. Understanding NLP applications helps you recommend appropriate services (Comprehend, Translate, Lex).

**Use Cases:**
- Sentiment analysis
- Entity recognition
- Language translation
- Chatbots and virtual assistants
- Document analysis

**AWS Services:**
- **Amazon Comprehend** - NLP service for text analysis
- **Amazon Translate** - Language translation
- **Amazon Lex** - Build conversational interfaces
- **Amazon Transcribe** - Speech to text

**AWS Documentation:**
- <a href="https://aws.amazon.com/comprehend/" target="_blank">Amazon Comprehend</a>
- <a href="https://aws.amazon.com/translate/" target="_blank">Amazon Translate</a>
- <a href="https://aws.amazon.com/lex/" target="_blank">Amazon Lex</a>
- <a href="https://aws.amazon.com/transcribe/" target="_blank">Amazon Transcribe</a>

#### 3. Speech Recognition and Text-to-Speech

**Why:** Converting speech to text and text to speech enables voice interfaces, accessibility features, and automated transcription. Understanding these capabilities helps you identify appropriate solutions for voice-enabled applications.

**Use Cases:**
- Voice assistants
- Transcription services
- Accessibility features
- Call center analytics
- Automated voice responses

**AWS Services:**
- **Amazon Transcribe** - Convert speech to text
- **Amazon Polly** - Convert text to speech

**AWS Documentation:**
- <a href="https://aws.amazon.com/transcribe/" target="_blank">Amazon Transcribe</a>
- <a href="https://aws.amazon.com/polly/" target="_blank">Amazon Polly</a>

#### 4. Recommendations and Personalization

**Why:** Recommendation systems suggest relevant items based on user behavior and preferences. Understanding recommendation use cases helps you identify when to use Amazon Personalize for personalized experiences.

**Use Cases:**
- Product recommendations
- Content recommendations
- Personalized marketing
- User segmentation

**AWS Services:**
- **Amazon Personalize** - ML-based recommendation service

**AWS Documentation:**
- <a href="https://aws.amazon.com/personalize/" target="_blank">Amazon Personalize</a>

#### 5. Fraud Detection and Anomaly Detection

**Why:** Detecting unusual patterns helps identify fraud, security threats, and operational issues. Understanding anomaly detection use cases helps you recognize when ML can improve security and operations.

**Use Cases:**
- Fraud detection in transactions
- Network security monitoring
- Quality control in manufacturing
- System health monitoring

**AWS Services:**
- **Amazon Fraud Detector** - Fraud detection service
- **Amazon Lookout** family - Anomaly detection for various use cases
- **Amazon DevOps Guru** - Operational anomaly detection

**AWS Documentation:**
- <a href="https://aws.amazon.com/fraud-detector/" target="_blank">Amazon Fraud Detector</a>
- <a href="https://aws.amazon.com/lookout-for-metrics/" target="_blank">Amazon Lookout for Metrics</a>

---

## Task 1.3: Describe the ML development lifecycle

### Knowledge Areas & AWS Documentation

#### 1. Data Collection and Preparation

**Why:** Quality data is essential for ML success. Understanding data collection, cleaning, labeling, and preparation is critical. Poor data quality leads to poor models. Exam questions test whether you understand the importance of proper data preparation.

**Key Concepts:**
- Data collection from various sources
- Data cleaning (handling missing values, outliers)
- Data labeling and annotation
- Feature engineering
- Data augmentation

**AWS Services:**
- **Amazon S3** - Store training data
- **AWS Glue** - ETL and data preparation
- **Amazon SageMaker Ground Truth** - Data labeling

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/data-prep.html" target="_blank">Amazon SageMaker Data Preparation</a>
- <a href="https://aws.amazon.com/sagemaker/groundtruth/" target="_blank">SageMaker Ground Truth</a>
- <a href="https://aws.amazon.com/glue/" target="_blank">AWS Glue</a>

#### 2. Model Training

**Why:** Training is where the ML model learns patterns from data. Understanding training concepts (epochs, batch size, learning rate) and the difference between training and validation helps you answer questions about model development.

**Key Concepts:**
- Training data vs validation data vs test data
- Hyperparameters
- Training jobs
- GPU/CPU compute requirements
- Training time and cost considerations

**AWS Services:**
- **Amazon SageMaker** - Build, train, and deploy models
- **SageMaker Training Jobs**
- **SageMaker Automatic Model Tuning**

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/train-model.html" target="_blank">Amazon SageMaker Training</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/how-it-works-training.html" target="_blank">SageMaker Training Jobs</a>

#### 3. Model Evaluation

**Why:** Evaluating model performance ensures it works well on new data. Understanding metrics (accuracy, precision, recall, F1 score) and concepts like overfitting/underfitting helps you identify whether a model is ready for deployment.

**Key Concepts:**
- Accuracy metrics (accuracy, precision, recall, F1)
- Confusion matrix
- Overfitting vs underfitting
- Cross-validation
- Model performance on test data

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-monitor.html" target="_blank">SageMaker Model Evaluation</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-monitor-model-quality.html" target="_blank">Model Quality Metrics</a>

#### 4. Model Deployment

**Why:** Deployment makes models available for predictions (inference). Understanding deployment options (real-time vs batch, endpoints, scaling) helps you recommend appropriate deployment strategies for different use cases.

**Key Concepts:**
- Inference endpoints
- Real-time inference vs batch inference
- Model hosting
- Scaling and performance
- Model versioning

**AWS Services:**
- **SageMaker Endpoints** - Real-time inference
- **SageMaker Batch Transform** - Batch inference
- **SageMaker Serverless Inference**

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/deploy-model.html" target="_blank">SageMaker Deployment</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/realtime-endpoints.html" target="_blank">SageMaker Endpoints</a>

#### 5. Model Monitoring and Retraining

**Why:** Models can degrade over time as data patterns change (model drift). Understanding the need for monitoring and retraining helps you maintain model performance in production.

**Key Concepts:**
- Model drift
- Data drift
- Performance monitoring
- Model retraining
- A/B testing

**AWS Services:**
- **SageMaker Model Monitor** - Monitor deployed models
- **SageMaker Pipelines** - Automate ML workflows

**AWS Documentation:**
- <a href="https://aws.amazon.com/sagemaker/model-monitor/" target="_blank">SageMaker Model Monitor</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-monitor.html" target="_blank">Monitoring Models in Production</a>

---

## Task 1.4: Identify AWS AI and ML services

### Knowledge Areas & AWS Documentation

#### 1. Amazon SageMaker

**Why:** SageMaker is AWS's comprehensive ML service for building, training, and deploying models. Understanding SageMaker capabilities is essential as it's the primary service for custom ML solutions.

**Key Features:**
- SageMaker Studio (IDE for ML)
- Built-in algorithms
- Bring your own algorithm
- Automatic model tuning
- Model deployment and hosting
- SageMaker Canvas (no-code ML)

**AWS Documentation:**
- <a href="https://aws.amazon.com/sagemaker/" target="_blank">Amazon SageMaker</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/whatis.html" target="_blank">SageMaker Developer Guide</a>
- <a href="https://aws.amazon.com/sagemaker/studio/" target="_blank">SageMaker Studio</a>

#### 2. AI Services (Pre-trained AI services)

**Why:** AWS AI services provide pre-trained models for common use cases without requiring ML expertise. Understanding which service solves which problem helps you recommend appropriate solutions.

**Services:**
- **Amazon Rekognition** - Image and video analysis
- **Amazon Comprehend** - NLP and text analysis
- **Amazon Translate** - Language translation
- **Amazon Polly** - Text-to-speech
- **Amazon Transcribe** - Speech-to-text
- **Amazon Lex** - Conversational AI
- **Amazon Kendra** - Intelligent search
- **Amazon Textract** - Document text extraction
- **Amazon Personalize** - Recommendations
- **Amazon Forecast** - Time series forecasting
- **Amazon Fraud Detector** - Fraud detection

**AWS Documentation:**
- <a href="https://aws.amazon.com/machine-learning/ai-services/" target="_blank">AWS AI Services</a>
- Individual service pages (linked above)

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/sagemaker/faqs/" target="_blank">SageMaker FAQs</a>
- <a href="https://aws.amazon.com/rekognition/faqs/" target="_blank">Rekognition FAQs</a>
- <a href="https://aws.amazon.com/comprehend/faqs/" target="_blank">Comprehend FAQs</a>
- <a href="https://aws.amazon.com/lex/faqs/" target="_blank">Lex FAQs</a>
- <a href="https://aws.amazon.com/polly/faqs/" target="_blank">Polly FAQs</a>

---

## AWS Whitepapers

1. **<a href="https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/machine-learning-lens.html" target="_blank">Machine Learning Lens - AWS Well-Architected Framework</a>**
2. **<a href="https://aws.amazon.com/architecture/machine-learning/" target="_blank">AWS Machine Learning Best Practices</a>**
3. **<a href="https://docs.aws.amazon.com/sagemaker/latest/dg/gs.html" target="_blank">Getting Started with Amazon SageMaker</a>**

---

## Final Thoughts on Domain 1

Domain 1 (Fundamentals of AI and ML) represents **20% of the exam** and provides the foundation for understanding AI/ML concepts and AWS services.

### Key Takeaways:

1. **Understand AI/ML terminology** - Know the difference between AI, ML, and deep learning
2. **Learn learning types** - Supervised, unsupervised, reinforcement learning
3. **Know problem types** - Classification, regression, clustering, forecasting
4. **Master the ML lifecycle** - Data → Train → Evaluate → Deploy → Monitor
5. **Match services to use cases** - Know which AWS AI service solves which problem
6. **Understand SageMaker** - It's the core service for custom ML

### Common Exam Patterns:

- **Scenario: Categorize emails** → Classification (supervised learning)
- **Scenario: Predict house prices** → Regression (supervised learning)
- **Scenario: Group customers** → Clustering (unsupervised learning)
- **Scenario: Image recognition** → Amazon Rekognition
- **Scenario: Sentiment analysis** → Amazon Comprehend
- **Scenario: Chatbot** → Amazon Lex

Master these fundamentals - they apply throughout all domains!
