# AWS Certified Machine Learning - Specialty (MLS-C01) Domain 3
## Modeling

**Official Exam Guide:** <a href="https://docs.aws.amazon.com/aws-certification/latest/examguides/machine-learning-specialty-01-domain3.html" target="_blank">Domain 3: Modeling</a>

**Skill Builder:** <a href="https://skillbuilder.aws/category/exam-prep/machine-learning-specialty-MLS-C01" target="_blank">AWS Certified Machine Learning - Specialty Exam Prep</a>

---

## Domain Overview

Domain 3 (36% - largest domain) focuses on framing business problems as ML problems, selecting appropriate models, training models, hyperparameter optimization, and evaluating models.

---

## Task 3.1: Frame business problems as ML problems

**Key Concepts:**
- Determine when to use/not use ML
- Supervised vs unsupervised learning
- Problem types: classification, regression, forecasting, clustering, recommendation, foundation models

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/algorithms-choose.html" target="_blank">Choose an Algorithm</a>
- <a href="https://docs.aws.amazon.com/machine-learning/latest/dg/types-of-ml-models.html" target="_blank">Types of ML Models</a>

---

## Task 3.2: Select appropriate model(s)

**Key Algorithms:**
- XGBoost, logistic regression, k-means, linear regression, decision trees, random forests
- RNN, CNN, ensemble methods, transfer learning, LLMs
- Express intuition behind models

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/xgboost.html" target="_blank">XGBoost Algorithm</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/linear-learner.html" target="_blank">Linear Learner Algorithm</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/k-means.html" target="_blank">K-Means Algorithm</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/randomcutforest.html" target="_blank">Random Cut Forest</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/deepar.html" target="_blank">DeepAR Forecasting Algorithm</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/image-classification.html" target="_blank">Image Classification Algorithm</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/object-detection.html" target="_blank">Object Detection Algorithm</a>

---

## Task 3.3: Train ML models

**Key Concepts:**
- Split data (training/validation, cross-validation)
- Optimization techniques (gradient descent, loss functions, convergence)
- Compute resources (GPU/CPU, distributed/non-distributed, Spark/non-Spark)
- Model updating (batch, real-time/online)

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/how-it-works-training.html" target="_blank">Train a Model with Amazon SageMaker</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/distributed-training.html" target="_blank">Distributed Training</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/data-parallel.html" target="_blank">SageMaker Data Parallelism</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-parallel.html" target="_blank">SageMaker Model Parallelism</a>

---

## Task 3.4: Perform hyperparameter optimization

**Key Concepts:**
- Regularization (dropout, L1/L2)
- Cross-validation
- Model initialization
- Neural network architecture (layers, nodes, learning rate, activation functions)
- Tree-based models (number of trees, depth)
- Linear models (learning rate)

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/automatic-model-tuning.html" target="_blank">SageMaker Automatic Model Tuning</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/automatic-model-tuning-how-it-works.html" target="_blank">How Hyperparameter Tuning Works</a>

---

## Task 3.5: Evaluate ML models

**Key Concepts:**
- Avoid overfitting/underfitting (bias-variance tradeoff)
- Metrics: AUC-ROC, accuracy, precision, recall, RMSE, F1 score
- Confusion matrices
- Offline and online evaluation (A/B testing)
- Model comparison (training time, quality, engineering costs)
- Cross-validation

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-monitor.html" target="_blank">Amazon SageMaker Model Monitor</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-model-monitor.html" target="_blank">Monitor Models for Data and Model Quality</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/model-dashboard.html" target="_blank">SageMaker Model Dashboard</a>

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/sagemaker/faqs/" target="_blank">Amazon SageMaker FAQs</a>

---

## Study Tips

1. **Master algorithm selection** - Classification (XGBoost, random forest), Regression (linear learner), Clustering (k-means), Forecasting (DeepAR), Computer Vision (CNN), NLP (RNN, transformers).

2. **Learn evaluation metrics** - Classification: accuracy, precision, recall, F1, AUC-ROC. Regression: RMSE, MAE, R². Confusion matrix interpretation.

3. **Understand hyperparameter tuning** - SageMaker automatic model tuning, Bayesian optimization, random search, grid search strategies.

4. **Practice bias-variance tradeoff** - Overfitting (high variance): regularization, more data. Underfitting (high bias): more features, complex model.

5. **Study training optimization** - Distributed training strategies, gradient descent variants (SGD, Adam), learning rate schedules, early stopping.

---

**Note:** This is Domain 3 of 4, representing 36% (largest domain) of exam content.
