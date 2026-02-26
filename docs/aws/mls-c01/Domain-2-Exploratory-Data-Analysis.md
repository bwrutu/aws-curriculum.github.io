# AWS Certified Machine Learning - Specialty (MLS-C01) Domain 2
## Exploratory Data Analysis

**Official Exam Guide:** <a href="https://docs.aws.amazon.com/aws-certification/latest/examguides/machine-learning-specialty-01-domain2.html" target="_blank">Domain 2: Exploratory Data Analysis</a>

**Skill Builder:** <a href="https://skillbuilder.aws/category/exam-prep/machine-learning-specialty-MLS-C01" target="_blank">AWS Certified Machine Learning - Specialty Exam Prep</a>

---

## Domain Overview

Domain 2 (24%) focuses on sanitizing and preparing data, performing feature engineering, and analyzing and visualizing data for ML.

---

## Task 2.1: Sanitize and prepare data for modeling

**Key Concepts:**
- Identify and handle missing data, corrupt data, stop words
- Format, normalize, augment, and scale data
- Determine if there's sufficient labeled data
- Use data labeling tools (Amazon Mechanical Turk)

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/data-wrangler.html" target="_blank">Amazon SageMaker Data Wrangler</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/sms.html" target="_blank">Amazon SageMaker Ground Truth</a>
- <a href="https://docs.aws.amazon.com/mturk/latest/requester/" target="_blank">Amazon Mechanical Turk</a>

---

## Task 2.2: Perform feature engineering

**Key Concepts:**
- Extract features from text, speech, images, public datasets
- Feature engineering concepts: binning, tokenization, outliers, synthetic features, one-hot encoding, dimensionality reduction

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/data-wrangler-transform.html" target="_blank">SageMaker Data Wrangler Transforms</a>
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/processing-job.html" target="_blank">SageMaker Processing Jobs</a>
- <a href="https://docs.aws.amazon.com/comprehend/latest/dg/" target="_blank">Amazon Comprehend Developer Guide</a>
- <a href="https://docs.aws.amazon.com/rekognition/latest/dg/" target="_blank">Amazon Rekognition Developer Guide</a>

---

## Task 2.3: Analyze and visualize data for ML

**Key Concepts:**
- Create graphs (scatter plots, time series, histograms, box plots)
- Interpret descriptive statistics (correlation, summary statistics, p-value)
- Perform cluster analysis (hierarchical, elbow plot, cluster size)

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-data-bias.html" target="_blank">SageMaker Clarify for Data Bias</a>
- <a href="https://docs.aws.amazon.com/quicksight/latest/user/" target="_blank">Amazon QuickSight User Guide</a>
- <a href="https://docs.aws.amazon.com/athena/latest/ug/" target="_blank">Amazon Athena User Guide</a>

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/sagemaker/data-wrangler/faqs/" target="_blank">SageMaker Data Wrangler FAQs</a>
- <a href="https://aws.amazon.com/sagemaker/groundtruth/faqs/" target="_blank">SageMaker Ground Truth FAQs</a>
- <a href="https://aws.amazon.com/quicksight/resources/faqs/" target="_blank">Amazon QuickSight FAQs</a>

---

## Study Tips

1. **Master data cleaning** - Handle missing values (imputation, deletion), remove outliers, handle duplicates, address class imbalance (SMOTE, undersampling).

2. **Learn feature engineering** - Numeric: normalization, standardization, binning. Text: tokenization, TF-IDF, word embeddings. Categorical: one-hot encoding, label encoding.

3. **Understand dimensionality reduction** - PCA for linear reduction, t-SNE for visualization, feature selection methods (filter, wrapper, embedded).

4. **Practice data visualization** - Histograms for distributions, scatter plots for correlations, box plots for outliers, heatmaps for correlation matrices.

5. **Study descriptive statistics** - Mean, median, mode, standard deviation, correlation coefficients, p-values for hypothesis testing.

---

**Note:** This is Domain 2 of 4, representing 24% of exam content.
