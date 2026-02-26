# AWS Certified DevOps Engineer - Professional (DOP-C02) Domain 1
## SDLC Automation

**Official Exam Guide:** <a href="https://docs.aws.amazon.com/aws-certification/latest/examguides/devops-engineer-professional-02-domain1.html" target="_blank">Domain 1: SDLC Automation</a>

**Skill Builder:** <a href="https://skillbuilder.aws/category/exam-prep/devops-engineer-professional-DOP-C02" target="_blank">AWS Certified DevOps Engineer - Professional Exam Prep</a>

---

## Domain Overview

Domain 1 (22% - largest domain) focuses on implementing CI/CD pipelines, integrating automated testing, building and managing artifacts, and implementing deployment strategies.

---

## Task 1.1: Implement CI/CD pipelines

**Knowledge Areas:**
- Software development lifecycle (SDLC) concepts, phases, models
- Pipeline deployment patterns (single and multi-account)

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/codepipeline/latest/userguide/" target="_blank">AWS CodePipeline User Guide</a>
- <a href="https://docs.aws.amazon.com/codebuild/latest/userguide/" target="_blank">AWS CodeBuild User Guide</a>
- <a href="https://docs.aws.amazon.com/codecommit/latest/userguide/" target="_blank">AWS CodeCommit User Guide</a>
- <a href="https://docs.aws.amazon.com/codedeploy/latest/userguide/" target="_blank">AWS CodeDeploy User Guide</a>
- <a href="https://docs.aws.amazon.com/secretsmanager/latest/userguide/" target="_blank">AWS Secrets Manager</a>
- <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-parameter-store.html" target="_blank">AWS Systems Manager Parameter Store</a>

---

## Task 1.2: Integrate automated testing into CI/CD pipelines

**Knowledge Areas:**
- Different test types (unit, integration, acceptance, UI, security scans)
- Appropriate use of tests at different CI/CD stages

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/codebuild/latest/userguide/test-reporting.html" target="_blank">CodeBuild Test Reporting</a>
- <a href="https://docs.aws.amazon.com/codepipeline/latest/userguide/actions-test.html" target="_blank">Test Actions in CodePipeline</a>
- <a href="https://docs.aws.amazon.com/lambda/latest/dg/testing-functions.html" target="_blank">Testing Lambda Functions</a>

---

## Task 1.3: Build and manage artifacts

**Knowledge Areas:**
- Artifact use cases and secure management
- Methods to create and generate artifacts
- Artifact lifecycle considerations

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/codeartifact/latest/ug/" target="_blank">AWS CodeArtifact User Guide</a>
- <a href="https://docs.aws.amazon.com/AmazonECR/latest/userguide/" target="_blank">Amazon ECR User Guide</a>
- <a href="https://docs.aws.amazon.com/imagebuilder/latest/userguide/" target="_blank">EC2 Image Builder User Guide</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/userguide/" target="_blank">Amazon S3 User Guide</a>

---

## Task 1.4: Implement deployment strategies

**Knowledge Areas:**
- Deployment methodologies (EC2, ECS, EKS, Lambda)
- Application storage patterns (EFS, S3, EBS)
- Mutable vs immutable deployment patterns
- Code distribution tools (CodeDeploy, Image Builder)

**Essential Documentation:**
- <a href="https://docs.aws.amazon.com/codedeploy/latest/userguide/deployment-configurations.html" target="_blank">CodeDeploy Deployment Configurations</a>
- <a href="https://docs.aws.amazon.com/codedeploy/latest/userguide/deployment-groups.html" target="_blank">CodeDeploy Deployment Groups</a>
- <a href="https://docs.aws.amazon.com/codedeploy/latest/userguide/deployments.html" target="_blank">CodeDeploy Deployments</a>
- <a href="https://docs.aws.amazon.com/eks/latest/userguide/deployment.html" target="_blank">EKS Deployments</a>

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/codepipeline/faqs/" target="_blank">AWS CodePipeline FAQs</a>
- <a href="https://aws.amazon.com/codebuild/faqs/" target="_blank">AWS CodeBuild FAQs</a>
- <a href="https://aws.amazon.com/codedeploy/faqs/" target="_blank">AWS CodeDeploy FAQs</a>
- <a href="https://aws.amazon.com/ecr/faqs/" target="_blank">Amazon ECR FAQs</a>

---

## Study Tips

1. **Master CI/CD pipeline architecture** - Understand CodePipeline stages (Source, Build, Test, Deploy), integrations with CodeCommit/GitHub, and multi-account deployments.

2. **Learn deployment strategies** - Blue/green (instant switch with rollback), canary (gradual traffic shift), rolling (incremental updates), all-at-once.

3. **Practice artifact management** - CodeArtifact for package management, ECR for container images, S3 for general artifacts, lifecycle policies.

4. **Understand testing integration** - Unit tests in build stage, integration tests pre-deployment, load tests post-deployment, security scans throughout.

5. **Study secrets management** - Secrets Manager for automatic rotation, Parameter Store for configuration, CodeBuild integration, least privilege access.

---

**Note:** This is Domain 1 of 6, representing 22% (largest domain) of exam content.
