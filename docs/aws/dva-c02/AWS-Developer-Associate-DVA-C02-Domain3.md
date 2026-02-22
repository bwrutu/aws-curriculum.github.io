# AWS Certified Developer Associate (DVA-C02) Domain 3
## Deployment

**Official Exam Guide:** [Domain 3: Deployment](https://docs.aws.amazon.com/aws-certification/latest/examguides/developer-associate-02-domain3.html){:target="_blank" rel="noopener noreferrer"}  
**Skill Builder:** [AWS Developer Associate (DVA-C02) Exam Prep](https://skillbuilder.aws/category/exam-prep/developer-associate-DVA-C02){:target="_blank" rel="noopener noreferrer"}

Note: Some Skill Builder labs require a subscription.

---

## How to Study This Domain Effectively

### Study Tips

1. **Build complete CI/CD pipelines from scratch** - The best way to master deployment is to create actual pipelines. Set up CodeCommit repositories, configure CodeBuild projects with buildspec.yml files, create CodeDeploy applications with appspec.yml files, and orchestrate everything with CodePipeline. Deploy a real application through multiple environments (dev, staging, production) using different deployment strategies. Hands-on pipeline creation solidifies concepts that are difficult to grasp from documentation alone.

2. **Master Infrastructure as Code with hands-on practice** - Don't just read about CloudFormation and SAM templates—write them. Create SAM templates that define Lambda functions, API Gateway APIs, and DynamoDB tables. Deploy these templates to different environments using parameters. Practice updating stacks, understanding drift detection, and troubleshooting failed deployments. The exam heavily tests your ability to read and modify IaC templates, so comfort with template syntax is essential.

3. **Experiment with all deployment strategies** - Implement blue/green deployments with CodeDeploy, test canary deployments with API Gateway stages, practice rolling deployments with Lambda aliases and traffic shifting. Observe what happens during failures, how rollbacks work, and how each strategy affects downtime. Understanding the mechanics of each deployment strategy through experimentation prepares you for scenario-based exam questions.

4. **Practice SAM CLI workflow extensively** - Install AWS SAM CLI and use it throughout the development lifecycle: `sam init` to create projects, `sam build` to prepare artifacts, `sam local invoke` to test locally, and `sam deploy` to deploy to AWS. Understanding SAM's local testing capabilities and how it simplifies serverless deployment is critical for exam questions about testing and deployment workflows.

5. **Create a deployment decision matrix** - Build a reference table mapping deployment requirements to strategies: zero downtime required (blue/green), gradual rollout with testing (canary), simple updates (all-at-once), containerized apps (ECS deployment types). Include when to use Lambda versions vs aliases, API Gateway stages, and CodeDeploy deployment configurations. This matrix helps you quickly identify the right deployment approach during exam scenarios.

### Recommended Approach

1. **Start with artifact preparation fundamentals** - Begin by understanding how to structure applications for deployment: managing dependencies with requirements.txt or package.json, organizing directory structures, creating deployment packages for Lambda, and building container images. Learn how configuration differs across environments and how to externalize configuration using environment variables and AWS AppConfig.

2. **Master AWS SAM and CloudFormation** - Study SAM templates in depth since SAM extends CloudFormation for serverless applications. Understand template anatomy (Resources, Parameters, Outputs), pseudo parameters, intrinsic functions (Ref, GetAtt, Sub, Join), and how SAM transforms simplify Lambda and API Gateway definitions. Practice deploying and updating stacks across multiple environments with different parameter values.

3. **Deep dive into CI/CD services** - Study each CI/CD service individually before understanding their integration: CodeCommit for source control, CodeBuild for compilation and testing (buildspec.yml), CodeDeploy for deployment automation (appspec.yml), and CodePipeline for orchestration. Understand how they pass artifacts between stages and how to configure each service for different application types.

4. **Learn deployment strategies comprehensively** - Study each deployment strategy (all-at-once, rolling, blue/green, canary) in detail. Understand CodeDeploy deployment configurations, Lambda traffic shifting with aliases, API Gateway canary releases, and ECS deployment types. Learn when each strategy is appropriate, how to configure them, and how rollback works for each.

5. **Practice testing at every stage** - Learn to test locally with SAM CLI, create integration tests, test APIs using different stages, implement automated testing in CodeBuild, and validate deployments in non-production environments. Complete with practice exams focused on Domain 3 to identify deployment knowledge gaps and reinforce CI/CD concepts.

---

## Task 1: Prepare application artifacts to be deployed to AWS

### Skills & Corresponding Documentation

#### Skill 3.1.1: Manage the dependencies of the code module (for example, environment variables, configuration files, container images) within the package

**Why:** Dependency management is fundamental to successful deployments and is tested through scenarios involving Lambda deployment packages, container image builds, and application configuration. You must understand how to include dependencies in Lambda packages (requirements.txt for Python, package.json for Node.js), build Docker images with proper layers for caching, manage environment-specific configurations, and handle binary dependencies. Exam questions present deployment failures and expect you to identify missing dependencies or incorrect packaging as the root cause.

**AWS Documentation:**
- [AWS Lambda Deployment Packages](https://docs.aws.amazon.com/lambda/latest/dg/gettingstarted-package.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Deployment Package in Python](https://docs.aws.amazon.com/lambda/latest/dg/python-package.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Deployment Package in Node.js](https://docs.aws.amazon.com/lambda/latest/dg/nodejs-package.html){:target="_blank" rel="noopener noreferrer"}
- [Creating Lambda Container Images](https://docs.aws.amazon.com/lambda/latest/dg/images-create.html){:target="_blank" rel="noopener noreferrer"}
- [Managing Lambda Function Dependencies](https://docs.aws.amazon.com/lambda/latest/dg/configuration-layers.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Layers](https://docs.aws.amazon.com/lambda/latest/dg/configuration-layers.html){:target="_blank" rel="noopener noreferrer"}
- [Docker Multi-Stage Builds](https://docs.docker.com/build/building/multi-stage/){:target="_blank" rel="noopener noreferrer"}
- [Amazon ECR - Docker Image Management](https://docs.aws.amazon.com/AmazonECR/latest/userguide/what-is-ecr.html){:target="_blank" rel="noopener noreferrer"}
- [Elastic Beanstalk Application Dependencies](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/applications.html){:target="_blank" rel="noopener noreferrer"}
- [Managing Application Versions](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/applications-versions.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 3.1.2: Organize files and a directory structure for application deployment

**Why:** Proper file organization is tested because deployment tools expect specific directory structures. You must understand Lambda's file structure requirements, SAM project layout (template.yaml, function folders), CodeDeploy's expected structure with appspec.yml, Elastic Beanstalk's .ebextensions directory, and how build tools organize output artifacts. Exam questions may present deployment failures caused by incorrect file placement or missing configuration files.

**AWS Documentation:**
- [AWS SAM Application Structure](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/sam-specification-template-anatomy.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Function Code and Handlers](https://docs.aws.amazon.com/lambda/latest/dg/foundation-progmodel.html){:target="_blank" rel="noopener noreferrer"}
- [CodeDeploy AppSpec File Reference](https://docs.aws.amazon.com/codedeploy/latest/userguide/reference-appspec-file.html){:target="_blank" rel="noopener noreferrer"}
- [AppSpec File Structure](https://docs.aws.amazon.com/codedeploy/latest/userguide/reference-appspec-file-structure.html){:target="_blank" rel="noopener noreferrer"}
- [Elastic Beanstalk Application Structure](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/applications.html){:target="_blank" rel="noopener noreferrer"}
- [Using .ebextensions Configuration Files](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/ebextensions.html){:target="_blank" rel="noopener noreferrer"}
- [CodeBuild Buildspec File Reference](https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html){:target="_blank" rel="noopener noreferrer"}
- [SAM Project Structure Best Practices](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-getting-started.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 3.1.3: Use code repositories in deployment environments

**Why:** Version control integration with deployment pipelines is essential for modern CI/CD workflows. You must understand how to use CodeCommit for source control, integrate GitHub/GitLab with CodePipeline, configure repository triggers, manage branches and pull requests, and use repository webhooks for automated deployments. Exam questions test your knowledge of triggering deployments from repository events and configuring source stages in pipelines.

**AWS Documentation:**
- [AWS CodeCommit User Guide](https://docs.aws.amazon.com/codecommit/latest/userguide/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [Getting Started with CodeCommit](https://docs.aws.amazon.com/codecommit/latest/userguide/getting-started.html){:target="_blank" rel="noopener noreferrer"}
- [Working with Repositories](https://docs.aws.amazon.com/codecommit/latest/userguide/repositories.html){:target="_blank" rel="noopener noreferrer"}
- [CodeCommit Triggers](https://docs.aws.amazon.com/codecommit/latest/userguide/how-to-notify.html){:target="_blank" rel="noopener noreferrer"}
- [Using CodePipeline with CodeCommit](https://docs.aws.amazon.com/codepipeline/latest/userguide/integrations-action-type.html#integrations-source-codecommit){:target="_blank" rel="noopener noreferrer"}
- [CodePipeline Integration with GitHub](https://docs.aws.amazon.com/codepipeline/latest/userguide/integrations-action-type.html#integrations-source-github){:target="_blank" rel="noopener noreferrer"}
- [Branching Strategy for CI/CD](https://docs.aws.amazon.com/prescriptive-guidance/latest/choosing-git-branch-strategy/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [Pull Request Workflows](https://docs.aws.amazon.com/codecommit/latest/userguide/pull-requests.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 3.1.4: Apply application requirements for resources (for example, memory, cores)

**Why:** Resource configuration directly impacts application performance and cost, and is tested through scenarios involving Lambda memory settings, EC2 instance types, ECS task definitions, and capacity planning. You must understand how Lambda memory affects CPU allocation, how to configure ECS task CPU and memory, how to select appropriate EC2 instance types, and how resource limits affect application behavior. Exam questions present performance requirements and expect you to configure appropriate resource allocations.

**AWS Documentation:**
- [Lambda Function Configuration](https://docs.aws.amazon.com/lambda/latest/dg/configuration-function-common.html){:target="_blank" rel="noopener noreferrer"}
- [Configuring Lambda Function Memory](https://docs.aws.amazon.com/lambda/latest/dg/configuration-memory.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Power Tuning](https://docs.aws.amazon.com/lambda/latest/operatorguide/profile-functions.html){:target="_blank" rel="noopener noreferrer"}
- [ECS Task Definition Parameters](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definition_parameters.html){:target="_blank" rel="noopener noreferrer"}
- [ECS Task CPU and Memory](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task-cpu-memory-error.html){:target="_blank" rel="noopener noreferrer"}
- [EC2 Instance Types](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-types.html){:target="_blank" rel="noopener noreferrer"}
- [Elastic Beanstalk Instance Configuration](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features.managing.ec2.html){:target="_blank" rel="noopener noreferrer"}
- [Auto Scaling for Application Resources](https://docs.aws.amazon.com/autoscaling/application/userguide/what-is-application-auto-scaling.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 3.1.5: Prepare application configurations for specific environments (for example, by using AWS AppConfig)

**Why:** Environment-specific configuration is tested because applications need different settings for dev, staging, and production. You must understand AWS AppConfig for dynamic configuration management, Systems Manager Parameter Store for environment variables, how to use CloudFormation parameters for environment differentiation, Lambda environment variables per stage, and API Gateway stage variables. Exam questions present multi-environment deployments and expect you to configure appropriate environment-specific settings.

**AWS Documentation:**
- [AWS AppConfig](https://docs.aws.amazon.com/appconfig/latest/userguide/what-is-appconfig.html){:target="_blank" rel="noopener noreferrer"}
- [Getting Started with AppConfig](https://docs.aws.amazon.com/appconfig/latest/userguide/appconfig-getting-started.html){:target="_blank" rel="noopener noreferrer"}
- [Creating AppConfig Configurations](https://docs.aws.amazon.com/appconfig/latest/userguide/appconfig-creating-configuration-and-profile.html){:target="_blank" rel="noopener noreferrer"}
- [AppConfig Deployment Strategies](https://docs.aws.amazon.com/appconfig/latest/userguide/appconfig-creating-deployment-strategy.html){:target="_blank" rel="noopener noreferrer"}
- [Systems Manager Parameter Store](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-parameter-store.html){:target="_blank" rel="noopener noreferrer"}
- [CloudFormation Parameters](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/parameters-section-structure.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Environment Variables](https://docs.aws.amazon.com/lambda/latest/dg/configuration-envvars.html){:target="_blank" rel="noopener noreferrer"}
- [API Gateway Stage Variables](https://docs.aws.amazon.com/apigateway/latest/developerguide/stage-variables.html){:target="_blank" rel="noopener noreferrer"}
- [Environment-Specific Configuration Best Practices](https://docs.aws.amazon.com/whitepapers/latest/introduction-devops-aws/configuration-management.html){:target="_blank" rel="noopener noreferrer"}

**AWS Service FAQs:**

- [AWS Lambda FAQ](https://aws.amazon.com/lambda/faqs/){:target="_blank" rel="noopener noreferrer"}
- [AWS CodeCommit FAQ](https://aws.amazon.com/codecommit/faqs/){:target="_blank" rel="noopener noreferrer"}
- [AWS AppConfig FAQ](https://aws.amazon.com/systems-manager/faq/#AWS_AppConfig){:target="_blank" rel="noopener noreferrer"}
- [AWS Elastic Beanstalk FAQ](https://aws.amazon.com/elasticbeanstalk/faqs/){:target="_blank" rel="noopener noreferrer"}
- [Amazon ECR FAQ](https://aws.amazon.com/ecr/faqs/){:target="_blank" rel="noopener noreferrer"}

**AWS Whitepapers:**

- [Introduction to DevOps on AWS](https://docs.aws.amazon.com/whitepapers/latest/introduction-devops-aws/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [Practicing Continuous Integration and Continuous Delivery on AWS](https://docs.aws.amazon.com/whitepapers/latest/practicing-continuous-integration-continuous-delivery/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [AWS Serverless Multi-Tier Architectures](https://docs.aws.amazon.com/whitepapers/latest/serverless-multi-tier-architectures-api-gateway-lambda/welcome.html){:target="_blank" rel="noopener noreferrer"}

---

## Task 2: Test applications in development environments

### Skills & Corresponding Documentation

#### Skill 3.2.1: Test deployed code by using AWS services and tools

**Why:** Testing deployed code is essential for validating functionality before production release. You must understand how to test Lambda functions using the console and AWS CLI, invoke functions with test events, use CloudWatch Logs for debugging, test API Gateway endpoints, use X-Ray for distributed tracing, and validate application behavior in AWS environments. Exam questions present testing scenarios and expect you to identify appropriate AWS testing tools and methods.

**AWS Documentation:**
- [Testing Lambda Functions](https://docs.aws.amazon.com/lambda/latest/dg/testing-functions.html){:target="_blank" rel="noopener noreferrer"}
- [Invoking Lambda Functions](https://docs.aws.amazon.com/lambda/latest/dg/lambda-invocation.html){:target="_blank" rel="noopener noreferrer"}
- [AWS SAM Local Testing](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-test-and-debug.html){:target="_blank" rel="noopener noreferrer"}
- [Testing API Gateway APIs](https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-test-method.html){:target="_blank" rel="noopener noreferrer"}
- [Using CloudWatch Logs for Debugging](https://docs.aws.amazon.com/lambda/latest/dg/monitoring-cloudwatchlogs.html){:target="_blank" rel="noopener noreferrer"}
- [AWS X-Ray for Application Tracing](https://docs.aws.amazon.com/xray/latest/devguide/aws-xray.html){:target="_blank" rel="noopener noreferrer"}
- [Using X-Ray with Lambda](https://docs.aws.amazon.com/lambda/latest/dg/services-xray.html){:target="_blank" rel="noopener noreferrer"}
- [CloudWatch Insights for Log Analysis](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/AnalyzingLogData.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 3.2.2: Write integration tests and mock APIs for external dependencies

**Why:** Integration testing is critical for validating component interactions without depending on external services. You must understand how to write integration tests, use mocking libraries to simulate AWS service calls, create mock APIs with API Gateway, use LocalStack for local AWS service emulation, and test service integrations. Exam questions test your knowledge of testing strategies that isolate components and verify integration points.

**AWS Documentation:**
- [Integration Testing Best Practices](https://docs.aws.amazon.com/lambda/latest/dg/testing-functions.html){:target="_blank" rel="noopener noreferrer"}
- [Mocking AWS Services in Tests](https://aws.amazon.com/blogs/developer/mocking-out-aws-sdk-for-javascript-in-unit-tests/){:target="_blank" rel="noopener noreferrer"}
- [API Gateway Mock Integrations](https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-mock-integration.html){:target="_blank" rel="noopener noreferrer"}
- [Creating Mock Endpoints](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-create-api-step-by-step.html){:target="_blank" rel="noopener noreferrer"}
- [Testing with AWS SAM](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-test-and-debug.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Testing Best Practices](https://docs.aws.amazon.com/lambda/latest/dg/lambda-testing.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 3.2.3: Test applications by using development endpoints (for example, configuring stages in Amazon API Gateway)

**Why:** Development endpoints and API stages enable testing without affecting production systems. You must understand API Gateway stages for environment separation, stage variables for environment-specific configuration, Lambda aliases for version testing, and how to configure multiple endpoints for testing. Exam questions present testing requirements and expect you to configure appropriate non-production endpoints.

**AWS Documentation:**
- [API Gateway Stages](https://docs.aws.amazon.com/apigateway/latest/developerguide/stages.html){:target="_blank" rel="noopener noreferrer"}
- [Setting Up API Gateway Stages](https://docs.aws.amazon.com/apigateway/latest/developerguide/set-up-stages.html){:target="_blank" rel="noopener noreferrer"}
- [API Gateway Stage Variables](https://docs.aws.amazon.com/apigateway/latest/developerguide/stage-variables.html){:target="_blank" rel="noopener noreferrer"}
- [Using Stage Variables with Lambda](https://docs.aws.amazon.com/apigateway/latest/developerguide/amazon-api-gateway-using-stage-variables.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Aliases](https://docs.aws.amazon.com/lambda/latest/dg/configuration-aliases.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Versions and Aliases](https://docs.aws.amazon.com/lambda/latest/dg/configuration-versions.html){:target="_blank" rel="noopener noreferrer"}
- [Testing Different Versions](https://docs.aws.amazon.com/lambda/latest/dg/versioning-aliases.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 3.2.4: Deploy application stack updates to existing environments (for example, deploying an AWS SAM template to a different staging environment)

**Why:** Updating existing deployments is fundamental to iterative development and is tested through scenarios involving stack updates, environment promotion, and change management. You must understand CloudFormation stack updates, change sets for previewing changes, SAM deployments to different environments using parameters, and how to manage stack dependencies. Exam questions present update scenarios and expect you to identify safe update strategies and handle update failures.

**AWS Documentation:**
- [Updating CloudFormation Stacks](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks.html){:target="_blank" rel="noopener noreferrer"}
- [CloudFormation Change Sets](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-changesets.html){:target="_blank" rel="noopener noreferrer"}
- [Deploying SAM Applications](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-deploying.html){:target="_blank" rel="noopener noreferrer"}
- [SAM Deploy Command](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/sam-cli-command-reference-sam-deploy.html){:target="_blank" rel="noopener noreferrer"}
- [Using Parameters for Environment-Specific Deployments](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/parameters-section-structure.html){:target="_blank" rel="noopener noreferrer"}
- [CloudFormation Stack Update Behavior](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-update-behaviors.html){:target="_blank" rel="noopener noreferrer"}
- [Rollback on Failure](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stack-failure-options.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 3.2.5: Test event-driven applications

**Why:** Event-driven architectures require specialized testing approaches because components react to asynchronous events. You must understand how to create test events for Lambda, simulate SQS messages, trigger SNS notifications for testing, generate EventBridge events, test Kinesis stream processing, and validate event-driven workflows. Exam questions present event-driven scenarios and expect you to implement appropriate testing strategies.

**AWS Documentation:**
- [Testing Event-Driven Applications](https://docs.aws.amazon.com/lambda/latest/dg/testing-functions.html){:target="_blank" rel="noopener noreferrer"}
- [Creating Lambda Test Events](https://docs.aws.amazon.com/lambda/latest/dg/testing-functions.html#creating-test-events){:target="_blank" rel="noopener noreferrer"}
- [Lambda Event Source Mappings](https://docs.aws.amazon.com/lambda/latest/dg/invocation-eventsourcemapping.html){:target="_blank" rel="noopener noreferrer"}
- [Testing SQS Integration](https://docs.aws.amazon.com/lambda/latest/dg/with-sqs.html){:target="_blank" rel="noopener noreferrer"}
- [Testing EventBridge Rules](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-test-pattern.html){:target="_blank" rel="noopener noreferrer"}
- [Generating Test Events for EventBridge](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-putevents.html){:target="_blank" rel="noopener noreferrer"}
- [Testing Kinesis Stream Processing](https://docs.aws.amazon.com/lambda/latest/dg/with-kinesis.html){:target="_blank" rel="noopener noreferrer"}
- [SAM Local Start Lambda for Event Testing](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-using-start-lambda.html){:target="_blank" rel="noopener noreferrer"}

**AWS Service FAQs:**

- [AWS SAM FAQ](https://aws.amazon.com/serverless/sam/faqs/){:target="_blank" rel="noopener noreferrer"}
- [AWS X-Ray FAQ](https://aws.amazon.com/xray/faqs/){:target="_blank" rel="noopener noreferrer"}
- [Amazon API Gateway FAQ](https://aws.amazon.com/api-gateway/faqs/){:target="_blank" rel="noopener noreferrer"}
- [AWS CloudFormation FAQ](https://aws.amazon.com/cloudformation/faqs/){:target="_blank" rel="noopener noreferrer"}

**AWS Whitepapers:**

- [Serverless Application Lens - Testing](https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/testing.html){:target="_blank" rel="noopener noreferrer"}
- [Best Practices for Developing on AWS Lambda](https://docs.aws.amazon.com/whitepapers/latest/serverless-multi-tier-architectures-api-gateway-lambda/best-practices-for-developing-on-aws-lambda.html){:target="_blank" rel="noopener noreferrer"}

---

## Task 3: Automate deployment testing

### Skills & Corresponding Documentation

#### Skill 3.3.1: Create application test events (for example, JSON payloads for testing AWS Lambda, API Gateway, AWS SAM resources)

**Why:** Test event creation is fundamental for automated testing pipelines. You must understand how to create JSON test events for Lambda functions, structure API Gateway request events, define SAM test events, create EventBridge event patterns, and generate realistic test data. Exam questions may present code that requires testing and expect you to create appropriate test event structures.

**AWS Documentation:**
- [Lambda Test Events](https://docs.aws.amazon.com/lambda/latest/dg/testing-functions.html){:target="_blank" rel="noopener noreferrer"}
- [Sample Events for Lambda](https://docs.aws.amazon.com/lambda/latest/dg/with-s3-example-deployment-pkg.html){:target="_blank" rel="noopener noreferrer"}
- [API Gateway Request Event Format](https://docs.aws.amazon.com/apigateway/latest/developerguide/set-up-lambda-proxy-integrations.html#api-gateway-simple-proxy-for-lambda-input-format){:target="_blank" rel="noopener noreferrer"}
- [EventBridge Event Patterns](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-event-patterns.html){:target="_blank" rel="noopener noreferrer"}
- [Creating Custom Test Events](https://docs.aws.amazon.com/lambda/latest/dg/testing-functions.html#creating-test-events){:target="_blank" rel="noopener noreferrer"}
- [SAM CLI Generate Event](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/sam-cli-command-reference-sam-local-generate-event.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 3.3.2: Deploy API resources to various environments

**Why:** Multi-environment API deployment is tested because APIs need separate instances for development, testing, and production. You must understand how to deploy API Gateway to multiple stages, use stage variables for environment differentiation, configure stage-specific settings, promote APIs between environments, and manage API versions. Exam questions present API deployment scenarios and expect you to configure appropriate multi-environment strategies.

**AWS Documentation:**
- [Deploying REST APIs](https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-deploy-api.html){:target="_blank" rel="noopener noreferrer"}
- [API Gateway Deployments](https://docs.aws.amazon.com/apigateway/latest/developerguide/set-up-deployments.html){:target="_blank" rel="noopener noreferrer"}
- [Managing API Gateway Stages](https://docs.aws.amazon.com/apigateway/latest/developerguide/stages.html){:target="_blank" rel="noopener noreferrer"}
- [Promoting API Changes to Production](https://docs.aws.amazon.com/apigateway/latest/developerguide/canary-release.html){:target="_blank" rel="noopener noreferrer"}
- [API Gateway Stage Variables](https://docs.aws.amazon.com/apigateway/latest/developerguide/stage-variables.html){:target="_blank" rel="noopener noreferrer"}
- [Environment-Specific API Configuration](https://docs.aws.amazon.com/apigateway/latest/developerguide/set-up-stages.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 3.3.3: Create application environments that use approved versions for integration testing (for example, Lambda aliases, container image tags, AWS Amplify branches, AWS Copilot environments)

**Why:** Version management is critical for reliable testing and deployment. You must understand Lambda versions and aliases for traffic management, container image tagging strategies, Amplify branches for frontend environments, and how to maintain multiple environment versions simultaneously. Exam questions test your ability to implement version control strategies that enable safe testing and gradual rollouts.

**AWS Documentation:**
- [Lambda Versions and Aliases](https://docs.aws.amazon.com/lambda/latest/dg/configuration-versions.html){:target="_blank" rel="noopener noreferrer"}
- [Managing Lambda Function Versions](https://docs.aws.amazon.com/lambda/latest/dg/configuration-versions.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Alias Routing Configuration](https://docs.aws.amazon.com/lambda/latest/dg/configuration-aliases.html){:target="_blank" rel="noopener noreferrer"}
- [Container Image Tagging Best Practices](https://docs.aws.amazon.com/AmazonECR/latest/userguide/image-tag-mutability.html){:target="_blank" rel="noopener noreferrer"}
- [ECR Image Tags](https://docs.aws.amazon.com/AmazonECR/latest/userguide/image-push.html){:target="_blank" rel="noopener noreferrer"}
- [AWS Amplify Branches](https://docs.aws.amazon.com/amplify/latest/userguide/multi-environments.html){:target="_blank" rel="noopener noreferrer"}
- [AWS Copilot Environments](https://aws.github.io/copilot-cli/docs/concepts/environments/){:target="_blank" rel="noopener noreferrer"}
- [Semantic Versioning for Applications](https://semver.org/){:target="_blank" rel="noopener noreferrer"}

#### Skill 3.3.4: Implement and deploy infrastructure as code (IaC) templates (for example, AWS SAM templates, AWS CloudFormation templates)

**Why:** Infrastructure as Code is extensively tested because it's the foundation of modern deployment automation. You must understand CloudFormation template structure, SAM template syntax and transforms, template parameters and mappings, intrinsic functions (Ref, GetAtt, Sub), resource dependencies, and stack deployment. Exam questions frequently present IaC templates and expect you to read, modify, or troubleshoot them.

**AWS Documentation:**
- [AWS CloudFormation User Guide](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html){:target="_blank" rel="noopener noreferrer"}
- [CloudFormation Template Anatomy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/template-anatomy.html){:target="_blank" rel="noopener noreferrer"}
- [AWS SAM Specification](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/sam-specification.html){:target="_blank" rel="noopener noreferrer"}
- [SAM Template Anatomy](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/sam-specification-template-anatomy.html){:target="_blank" rel="noopener noreferrer"}
- [CloudFormation Intrinsic Functions](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference.html){:target="_blank" rel="noopener noreferrer"}
- [CloudFormation Parameters](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/parameters-section-structure.html){:target="_blank" rel="noopener noreferrer"}
- [CloudFormation Mappings](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/mappings-section-structure.html){:target="_blank" rel="noopener noreferrer"}
- [Resource Dependencies](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-attribute-dependson.html){:target="_blank" rel="noopener noreferrer"}
- [SAM Policy Templates](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-policy-templates.html){:target="_blank" rel="noopener noreferrer"}
- [Creating and Deploying CloudFormation Stacks](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-console-create-stack.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 3.3.5: Manage environments in individual AWS services (for example, differentiating between development, test, and production in API Gateway)

**Why:** Service-level environment management is tested because different AWS services have different mechanisms for environment separation. You must understand API Gateway stages, Lambda aliases, ECS service environments, Elastic Beanstalk environments, and how to configure service-specific environment settings. Exam questions present multi-environment scenarios and expect you to use appropriate service features for environment separation.

**AWS Documentation:**
- [API Gateway Stage Management](https://docs.aws.amazon.com/apigateway/latest/developerguide/stages.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Environment Variables](https://docs.aws.amazon.com/lambda/latest/dg/configuration-envvars.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Aliases for Environments](https://docs.aws.amazon.com/lambda/latest/dg/configuration-aliases.html){:target="_blank" rel="noopener noreferrer"}
- [Elastic Beanstalk Environments](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features.managing.html){:target="_blank" rel="noopener noreferrer"}
- [Managing Beanstalk Environment Configuration](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/environment-configuration-methods-during.html){:target="_blank" rel="noopener noreferrer"}
- [ECS Service Environments](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/service-configure-auto-scaling.html){:target="_blank" rel="noopener noreferrer"}
- [Environment-Specific Tags](https://docs.aws.amazon.com/general/latest/gr/aws_tagging.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 3.3.6: Use Amazon Q Developer to generate automated tests

**Why:** Amazon Q Developer represents AWS's AI-assisted development approach and is tested as a modern tool for accelerating test creation. You must understand how Q Developer can generate test cases, create unit tests for Lambda functions, suggest test scenarios, and help with test automation. Exam questions may test your knowledge of when and how to leverage Q Developer for testing tasks.

**AWS Documentation:**
- [Amazon Q Developer](https://aws.amazon.com/q/developer/){:target="_blank" rel="noopener noreferrer"}
- [Amazon Q Developer User Guide](https://docs.aws.amazon.com/amazonq/latest/qdeveloper-ug/what-is.html){:target="_blank" rel="noopener noreferrer"}
- [Using Amazon Q Developer for Testing](https://docs.aws.amazon.com/amazonq/latest/qdeveloper-ug/q-features.html){:target="_blank" rel="noopener noreferrer"}
- [Q Developer Code Generation](https://docs.aws.amazon.com/amazonq/latest/qdeveloper-ug/code-recommendations.html){:target="_blank" rel="noopener noreferrer"}
- [Q Developer in IDE](https://docs.aws.amazon.com/amazonq/latest/qdeveloper-ug/q-in-IDE.html){:target="_blank" rel="noopener noreferrer"}

**AWS Service FAQs:**

- [AWS SAM FAQ](https://aws.amazon.com/serverless/sam/faqs/){:target="_blank" rel="noopener noreferrer"}
- [AWS CloudFormation FAQ](https://aws.amazon.com/cloudformation/faqs/){:target="_blank" rel="noopener noreferrer"}
- [AWS Amplify FAQ](https://aws.amazon.com/amplify/faqs/){:target="_blank" rel="noopener noreferrer"}
- [Amazon Q Developer FAQ](https://aws.amazon.com/q/developer/faqs/){:target="_blank" rel="noopener noreferrer"}

**AWS Whitepapers:**

- [Infrastructure as Code](https://docs.aws.amazon.com/whitepapers/latest/introduction-devops-aws/infrastructure-as-code.html){:target="_blank" rel="noopener noreferrer"}
- [Practicing Continuous Integration and Continuous Delivery on AWS](https://docs.aws.amazon.com/whitepapers/latest/practicing-continuous-integration-continuous-delivery/welcome.html){:target="_blank" rel="noopener noreferrer"}

---

## Task 4: Deploy code by using AWS Continuous Integration and Continuous Delivery (CI/CD) services

### Skills & Corresponding Documentation

#### Skill 3.4.1: Describe Lambda deployment packaging options

**Why:** Lambda deployment packaging is tested because different packaging methods suit different scenarios. You must understand .zip file packages for small functions, container images for custom runtimes and large dependencies, Lambda layers for shared code, and deployment package size limits. Exam questions present Lambda deployment requirements and expect you to select the appropriate packaging approach.

**AWS Documentation:**
- [Lambda Deployment Packages](https://docs.aws.amazon.com/lambda/latest/dg/gettingstarted-package.html){:target="_blank" rel="noopener noreferrer"}
- [.zip File Archives for Lambda](https://docs.aws.amazon.com/lambda/latest/dg/configuration-function-zip.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Container Images](https://docs.aws.amazon.com/lambda/latest/dg/images-create.html){:target="_blank" rel="noopener noreferrer"}
- [Creating Container Images for Lambda](https://docs.aws.amazon.com/lambda/latest/dg/images-create.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Layers](https://docs.aws.amazon.com/lambda/latest/dg/configuration-layers.html){:target="_blank" rel="noopener noreferrer"}
- [Creating and Sharing Lambda Layers](https://docs.aws.amazon.com/lambda/latest/dg/configuration-layers.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Deployment Package Size Limits](https://docs.aws.amazon.com/lambda/latest/dg/gettingstarted-limits.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 3.4.2: Describe API Gateway stages and custom domains

**Why:** API Gateway stage and domain management is tested because production APIs require professional URLs and environment separation. You must understand how stages separate environments, stage variables for configuration, custom domain names with certificates, base path mappings for multiple APIs, and API versioning strategies. Exam questions present API publishing requirements and expect you to configure stages and custom domains correctly.

**AWS Documentation:**
- [API Gateway Stages](https://docs.aws.amazon.com/apigateway/latest/developerguide/stages.html){:target="_blank" rel="noopener noreferrer"}
- [Setting Up Custom Domain Names](https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-custom-domains.html){:target="_blank" rel="noopener noreferrer"}
- [Custom Domain Names for REST APIs](https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-custom-domains.html){:target="_blank" rel="noopener noreferrer"}
- [Base Path Mapping](https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-custom-domains.html#how-to-custom-domains-mapping){:target="_blank" rel="noopener noreferrer"}
- [API Gateway Stage Variables](https://docs.aws.amazon.com/apigateway/latest/developerguide/stage-variables.html){:target="_blank" rel="noopener noreferrer"}
- [Using AWS Certificate Manager with API Gateway](https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-custom-domains-prerequisites.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 3.4.3: Update existing IaC templates (for example, AWS SAM templates, CloudFormation templates)

**Why:** Updating IaC templates is fundamental to iterative development and is heavily tested. You must understand how to modify CloudFormation resources, add parameters, update SAM function definitions, handle stack updates and rollbacks, use change sets to preview changes, and manage template versioning. Exam questions present templates that need modification and expect you to make correct changes while avoiding disruption.

**AWS Documentation:**
- [Updating CloudFormation Stacks](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks.html){:target="_blank" rel="noopener noreferrer"}
- [Modifying Stack Templates](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-get-template.html){:target="_blank" rel="noopener noreferrer"}
- [CloudFormation Change Sets](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-changesets.html){:target="_blank" rel="noopener noreferrer"}
- [Updating SAM Applications](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-deploying.html){:target="_blank" rel="noopener noreferrer"}
- [Stack Update Behaviors](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-update-behaviors.html){:target="_blank" rel="noopener noreferrer"}
- [Preventing Updates to Stack Resources](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/protect-stack-resources.html){:target="_blank" rel="noopener noreferrer"}
- [Stack Rollback](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-rollback-triggers.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 3.4.4: Manage application environments by using AWS services

**Why:** Environment management with AWS services is tested through scenarios involving multiple deployment targets. You must understand Elastic Beanstalk environments, ECS clusters and services, Lambda aliases and versions, and how to manage configurations across environments. Exam questions present environment management requirements and expect you to use appropriate AWS services for environment orchestration.

**AWS Documentation:**
- [Elastic Beanstalk Environment Management](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features.managing.html){:target="_blank" rel="noopener noreferrer"}
- [Creating Elastic Beanstalk Environments](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features.environments.html){:target="_blank" rel="noopener noreferrer"}
- [ECS Service Management](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ecs_services.html){:target="_blank" rel="noopener noreferrer"}
- [ECS Clusters](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/clusters.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Environment Management](https://docs.aws.amazon.com/lambda/latest/dg/configuration-envvars.html){:target="_blank" rel="noopener noreferrer"}
- [Managing Multiple Environments](https://docs.aws.amazon.com/prescriptive-guidance/latest/best-practices-cdk-typescript-iac/multiple-environments.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 3.4.5: Deploy an application version by using deployment strategies

**Why:** Deployment strategies are heavily tested because they determine how updates roll out and affect downtime. You must understand all-at-once (simplest, has downtime), rolling (gradual replacement), blue/green (zero downtime, instant rollback), and canary (gradual traffic shift with testing) deployments. Exam questions present deployment requirements (zero downtime, gradual rollout, quick rollback) and expect you to select the appropriate strategy.

**AWS Documentation:**
- [AWS CodeDeploy Deployment Configurations](https://docs.aws.amazon.com/codedeploy/latest/userguide/deployment-configurations.html){:target="_blank" rel="noopener noreferrer"}
- [Blue/Green Deployments](https://docs.aws.amazon.com/codedeploy/latest/userguide/deployments-create-prerequisites.html#deployments-create-prerequisites-blue-green){:target="_blank" rel="noopener noreferrer"}
- [Lambda Deployment Strategies](https://docs.aws.amazon.com/lambda/latest/dg/lambda-traffic-shifting-using-aliases.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Traffic Shifting with Aliases](https://docs.aws.amazon.com/lambda/latest/dg/configuration-aliases.html#configuring-alias-routing){:target="_blank" rel="noopener noreferrer"}
- [API Gateway Canary Releases](https://docs.aws.amazon.com/apigateway/latest/developerguide/canary-release.html){:target="_blank" rel="noopener noreferrer"}
- [ECS Deployment Types](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/deployment-types.html){:target="_blank" rel="noopener noreferrer"}
- [Elastic Beanstalk Deployment Policies](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features.rolling-version-deploy.html){:target="_blank" rel="noopener noreferrer"}
- [CodeDeploy for Lambda](https://docs.aws.amazon.com/codedeploy/latest/userguide/deployment-steps-lambda.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 3.4.6: Commit code to a repository to invoke build, test, and deployment actions

**Why:** Repository-triggered automation is fundamental to CI/CD and is tested through pipeline configuration scenarios. You must understand how CodeCommit triggers start pipelines, how CodePipeline detects source changes, configuring webhooks for GitHub integration, and automating build/test/deploy on commit. Exam questions present CI/CD requirements and expect you to configure automatic pipeline triggers.

**AWS Documentation:**
- [AWS CodePipeline User Guide](https://docs.aws.amazon.com/codepipeline/latest/userguide/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [CodePipeline Pipeline Structure](https://docs.aws.amazon.com/codepipeline/latest/userguide/pipeline-structure.html){:target="_blank" rel="noopener noreferrer"}
- [Source Actions in CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/action-reference-CodeCommit.html){:target="_blank" rel="noopener noreferrer"}
- [CodeCommit Triggers](https://docs.aws.amazon.com/codecommit/latest/userguide/how-to-notify.html){:target="_blank" rel="noopener noreferrer"}
- [GitHub Integration with CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/action-reference-GitHub.html){:target="_blank" rel="noopener noreferrer"}
- [Detecting Changes in CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/pipelines-about-starting.html){:target="_blank" rel="noopener noreferrer"}
- [EventBridge for Repository Events](https://docs.aws.amazon.com/codecommit/latest/userguide/monitoring-events.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 3.4.7: Use orchestrated workflows to deploy code to different environments

**Why:** Multi-stage deployment orchestration is tested because production deployments require progressive rollout through environments. You must understand CodePipeline stages and actions, manual approval actions, cross-account deployments, environment promotion workflows, and parallel execution. Exam questions present complex deployment workflows and expect you to configure appropriate pipeline structures.

**AWS Documentation:**
- [CodePipeline Concepts](https://docs.aws.amazon.com/codepipeline/latest/userguide/concepts.html){:target="_blank" rel="noopener noreferrer"}
- [CodePipeline Stages](https://docs.aws.amazon.com/codepipeline/latest/userguide/concepts-how-it-works.html#concepts-how-it-works-stages){:target="_blank" rel="noopener noreferrer"}
- [Manual Approval Actions](https://docs.aws.amazon.com/codepipeline/latest/userguide/approvals.html){:target="_blank" rel="noopener noreferrer"}
- [Cross-Account Deployments](https://docs.aws.amazon.com/codepipeline/latest/userguide/pipelines-create-cross-account.html){:target="_blank" rel="noopener noreferrer"}
- [Parallel Actions in CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/best-practices.html#best-practices-parallel-actions){:target="_blank" rel="noopener noreferrer"}
- [Multi-Region Deployment](https://docs.aws.amazon.com/codepipeline/latest/userguide/actions-create-cross-region.html){:target="_blank" rel="noopener noreferrer"}
- [Stage Transitions](https://docs.aws.amazon.com/codepipeline/latest/userguide/pipelines-disable-enable.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 3.4.8: Perform application rollbacks by using existing deployment strategies

**Why:** Rollback capability is critical for production reliability and is tested through failure scenarios. You must understand Lambda alias version switching for instant rollback, CodeDeploy automatic rollback on failures, blue/green deployment rollback by redirecting traffic, CloudFormation stack rollback, and how to trigger manual rollbacks. Exam questions present deployment failures and expect you to identify appropriate rollback mechanisms.

**AWS Documentation:**
- [Lambda Rollback](https://docs.aws.amazon.com/lambda/latest/dg/configuration-aliases.html){:target="_blank" rel="noopener noreferrer"}
- [CodeDeploy Rollbacks](https://docs.aws.amazon.com/codedeploy/latest/userguide/deployments-rollback-and-redeploy.html){:target="_blank" rel="noopener noreferrer"}
- [Automatic Rollback Configuration](https://docs.aws.amazon.com/codedeploy/latest/userguide/deployment-groups-configure-advanced-options.html){:target="_blank" rel="noopener noreferrer"}
- [Blue/Green Rollback](https://docs.aws.amazon.com/codedeploy/latest/userguide/deployment-steps-blue-green.html){:target="_blank" rel="noopener noreferrer"}
- [CloudFormation Rollback](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-rollback-triggers.html){:target="_blank" rel="noopener noreferrer"}
- [ECS Circuit Breaker for Rollback](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/deployment-circuit-breaker.html){:target="_blank" rel="noopener noreferrer"}
- [API Gateway Deployment Rollback](https://docs.aws.amazon.com/apigateway/latest/developerguide/set-up-deployments.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 3.4.9: Use labels and branches for version and release management

**Why:** Version control strategies are tested because proper branching enables parallel development and controlled releases. You must understand Git branching strategies (GitFlow, trunk-based), semantic versioning, tagging releases, branch protection rules, and how CI/CD pipelines integrate with branches. Exam questions present version management requirements and expect you to configure appropriate branching and tagging strategies.

**AWS Documentation:**
- [CodeCommit Branches](https://docs.aws.amazon.com/codecommit/latest/userguide/branches.html){:target="_blank" rel="noopener noreferrer"}
- [Working with Branches in CodeCommit](https://docs.aws.amazon.com/codecommit/latest/userguide/how-to-create-branch.html){:target="_blank" rel="noopener noreferrer"}
- [Git Tags in CodeCommit](https://docs.aws.amazon.com/codecommit/latest/userguide/how-to-view-tag-details.html){:target="_blank" rel="noopener noreferrer"}
- [Branch-Based Development](https://docs.aws.amazon.com/prescriptive-guidance/latest/choosing-git-branch-strategy/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [CodePipeline Branch Triggers](https://docs.aws.amazon.com/codepipeline/latest/userguide/action-reference-CodeCommit.html){:target="_blank" rel="noopener noreferrer"}
- [Amplify Branch Deployments](https://docs.aws.amazon.com/amplify/latest/userguide/multi-environments.html){:target="_blank" rel="noopener noreferrer"}
- [Release Management Best Practices](https://docs.aws.amazon.com/whitepapers/latest/practicing-continuous-integration-continuous-delivery/release-management.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 3.4.10: Use existing runtime configurations to create dynamic deployments (for example, using staging variables from API Gateway in Lambda functions)

**Why:** Dynamic configuration enables flexible deployments without code changes. You must understand API Gateway stage variables passed to Lambda, Lambda environment variables per alias, parameter injection in CloudFormation, and how runtime configuration drives behavior across environments. Exam questions present scenarios requiring environment-specific behavior and expect you to use dynamic configuration mechanisms.

**AWS Documentation:**
- [API Gateway Stage Variables](https://docs.aws.amazon.com/apigateway/latest/developerguide/stage-variables.html){:target="_blank" rel="noopener noreferrer"}
- [Using Stage Variables with Lambda](https://docs.aws.amazon.com/apigateway/latest/developerguide/amazon-api-gateway-using-stage-variables.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Environment Variables](https://docs.aws.amazon.com/lambda/latest/dg/configuration-envvars.html){:target="_blank" rel="noopener noreferrer"}
- [CloudFormation Parameters](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/parameters-section-structure.html){:target="_blank" rel="noopener noreferrer"}
- [Dynamic References in CloudFormation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/dynamic-references.html){:target="_blank" rel="noopener noreferrer"}
- [AppConfig for Dynamic Configuration](https://docs.aws.amazon.com/appconfig/latest/userguide/what-is-appconfig.html){:target="_blank" rel="noopener noreferrer"}
- [Systems Manager Parameters in Lambda](https://docs.aws.amazon.com/systems-manager/latest/userguide/ps-integration-lambda-extensions.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 3.4.11: Configure deployment strategies (for example, blue/green, canary, rolling) for application releases

**Why:** Configuring deployment strategies is extensively tested because strategy choice affects risk, downtime, and rollback capability. You must understand how to configure CodeDeploy deployment configurations, Lambda traffic shifting percentages, API Gateway canary settings, ECS deployment controllers, and when each strategy is appropriate. Exam questions present deployment requirements and expect you to configure the right strategy with correct parameters.

**AWS Documentation:**
- [CodeDeploy Deployment Configurations](https://docs.aws.amazon.com/codedeploy/latest/userguide/deployment-configurations.html){:target="_blank" rel="noopener noreferrer"}
- [Predefined Deployment Configurations](https://docs.aws.amazon.com/codedeploy/latest/userguide/deployment-configurations-create.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Canary Deployments](https://docs.aws.amazon.com/lambda/latest/dg/lambda-traffic-shifting-using-aliases.html){:target="_blank" rel="noopener noreferrer"}
- [Configuring Lambda Traffic Shifting](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/automating-updates-to-serverless-apps.html){:target="_blank" rel="noopener noreferrer"}
- [API Gateway Canary Release Settings](https://docs.aws.amazon.com/apigateway/latest/developerguide/canary-release.html){:target="_blank" rel="noopener noreferrer"}
- [ECS Blue/Green Deployment](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/deployment-type-bluegreen.html){:target="_blank" rel="noopener noreferrer"}
- [Elastic Beanstalk Deployment Policies](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features.rolling-version-deploy.html){:target="_blank" rel="noopener noreferrer"}
- [SAM Traffic Shifting Configuration](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/automating-updates-to-serverless-apps.html){:target="_blank" rel="noopener noreferrer"}

**AWS Service FAQs:**

- [AWS CodePipeline FAQ](https://aws.amazon.com/codepipeline/faqs/){:target="_blank" rel="noopener noreferrer"}
- [AWS CodeDeploy FAQ](https://aws.amazon.com/codedeploy/faqs/){:target="_blank" rel="noopener noreferrer"}
- [AWS CodeBuild FAQ](https://aws.amazon.com/codebuild/faqs/){:target="_blank" rel="noopener noreferrer"}
- [AWS CodeCommit FAQ](https://aws.amazon.com/codecommit/faqs/){:target="_blank" rel="noopener noreferrer"}
- [AWS Lambda FAQ](https://aws.amazon.com/lambda/faqs/){:target="_blank" rel="noopener noreferrer"}
- [Amazon API Gateway FAQ](https://aws.amazon.com/api-gateway/faqs/){:target="_blank" rel="noopener noreferrer"}
- [AWS Elastic Beanstalk FAQ](https://aws.amazon.com/elasticbeanstalk/faqs/){:target="_blank" rel="noopener noreferrer"}

**AWS Whitepapers:**

- [Practicing Continuous Integration and Continuous Delivery on AWS](https://docs.aws.amazon.com/whitepapers/latest/practicing-continuous-integration-continuous-delivery/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [Introduction to DevOps on AWS](https://docs.aws.amazon.com/whitepapers/latest/introduction-devops-aws/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [Blue/Green Deployments on AWS](https://docs.aws.amazon.com/whitepapers/latest/blue-green-deployments/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [AWS CI/CD Pipeline Best Practices](https://docs.aws.amazon.com/whitepapers/latest/practicing-continuous-integration-continuous-delivery/pipeline-best-practices.html){:target="_blank" rel="noopener noreferrer"}

---

## Final Thoughts

Domain 3: Deployment is where development meets operations and represents the practical implementation of CI/CD principles on AWS. Success requires hands-on experience building complete deployment pipelines—reading alone is insufficient. Set up actual CodePipeline workflows that pull from CodeCommit, build with CodeBuild, and deploy with CodeDeploy. Practice creating and deploying SAM and CloudFormation templates across multiple environments. Master the different deployment strategies (all-at-once, rolling, blue/green, canary) by implementing each one and observing their behavior during updates and rollbacks. Understanding deployment automation is critical not just for the exam but for professional AWS development work, where reliable, repeatable deployments are essential. The skills you build in this domain—IaC, CI/CD pipelines, automated testing, and deployment strategies—form the foundation of modern DevOps practices and will serve you throughout your AWS career.
