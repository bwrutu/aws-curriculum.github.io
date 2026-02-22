# AWS Certified Developer Associate (DVA-C02) Domain 1
## Development with AWS Services

**Official Exam Guide:** [Domain 1: Development with AWS Services](https://docs.aws.amazon.com/aws-certification/latest/examguides/developer-associate-02-domain1.html){:target="_blank" rel="noopener noreferrer"}  
**Skill Builder:** [AWS Developer Associate (DVA-C02) Exam Prep](https://skillbuilder.aws/category/exam-prep/developer-associate-DVA-C02){:target="_blank" rel="noopener noreferrer"}

Note: Some Skill Builder labs require a subscription.

---

## How to Study This Domain Effectively

### Study Tips

1. **Build working code examples for each pattern** - Don't just read about event-driven architectures, microservices, or Lambda functions—actually implement them. Create small projects that demonstrate synchronous vs asynchronous patterns, tightly vs loosely coupled components, and stateful vs stateless designs. Hands-on coding solidifies these concepts far better than passive reading, and the exam frequently tests your ability to identify the right pattern for specific scenarios.

2. **Practice with AWS SDKs in your preferred language** - The exam expects you to understand how to interact with AWS services programmatically. Install the AWS SDK for your language of choice (Python, JavaScript, Java, etc.) and write code that calls various AWS services. Focus on error handling, retry logic, pagination, and authentication patterns that appear consistently across different SDKs.

3. **Master DynamoDB through practical exercises** - DynamoDB is heavily featured in this domain. Create tables with different partition key and sort key combinations, practice query vs scan operations, experiment with Global Secondary Indexes and Local Secondary Indexes, and implement pagination. Understanding DynamoDB's performance characteristics and access patterns is crucial for multiple exam questions.

4. **Set up a local Lambda development environment** - Use AWS SAM CLI or the Serverless Framework to develop and test Lambda functions locally. Practice configuring environment variables, adjusting memory and timeout settings, implementing error handling with destinations and dead-letter queues, and testing event-driven invocations. Local development helps you understand Lambda's execution model without constant deployment delays.

5. **Create an architecture pattern cheat sheet** - Build a visual reference that maps common application patterns (event-driven, microservices, fanout, choreography, orchestration) to their AWS service implementations. Include when to use SQS vs SNS vs EventBridge, how Step Functions orchestrates workflows, and how to implement circuit breakers and retry logic. This reference helps you quickly identify the right architectural approach during exam questions.

### Recommended Approach

1. **Start with foundational architectural concepts** - Begin by understanding the core architectural patterns (monolithic vs microservices, stateful vs stateless, synchronous vs asynchronous, tightly vs loosely coupled). Read the AWS Well-Architected Framework and serverless application lens to understand how these patterns apply to AWS. This foundation is essential for making architectural decisions throughout the exam.

2. **Deep dive into AWS SDK programming** - Study how to use AWS SDKs to interact with services programmatically. Focus on the SDK documentation for your preferred language, learn about credential management, understand pagination for large result sets, and master error handling and retry strategies. Practice writing code that calls EC2, S3, DynamoDB, SQS, and Lambda programmatically.

3. **Master Lambda development and optimization** - Study Lambda configuration options (memory, timeout, concurrency, environment variables, layers, extensions), understand the execution lifecycle, practice implementing error handling with destinations and DLQs, and learn performance optimization techniques. Work through AWS SAM documentation to understand local testing and deployment patterns.

4. **Become proficient with messaging and event services** - Study SQS, SNS, EventBridge, and Kinesis in detail. Understand their use cases, message delivery patterns, error handling mechanisms, and how to implement fanout and event-driven architectures. Practice writing code that sends, receives, and processes messages from these services.

5. **Study data stores and caching strategies** - Focus heavily on DynamoDB (partition keys, sort keys, GSIs, LSIs, query vs scan, consistency models), then expand to ElastiCache, RDS, and specialized stores like OpenSearch. Understand data serialization, caching patterns, and how to choose the right data store based on access patterns. Complete with practice exams focused on Domain 1 to identify knowledge gaps.

---

## Task 1: Develop code for applications hosted on AWS

### Skills & Corresponding Documentation

#### Skill 1.1.1: Describe architectural patterns (for example, event-driven, microservices, monolithic, choreography, orchestration, fanout)

**Why:** The exam tests your ability to identify and implement appropriate architectural patterns for different scenarios. Questions present requirements like scalability needs, component independence, or event processing workflows and expect you to recommend the right pattern. Understanding when to use event-driven architecture vs request-response patterns, microservices vs monolithic designs, and choreography vs orchestration is fundamental for designing AWS applications and appears across multiple exam questions.

**AWS Documentation:**
- [Microservices on AWS](https://aws.amazon.com/microservices/){:target="_blank" rel="noopener noreferrer"}
- [What are Microservices?](https://aws.amazon.com/microservices/){:target="_blank" rel="noopener noreferrer"}
- [Event-Driven Architecture on AWS](https://aws.amazon.com/event-driven-architecture/){:target="_blank" rel="noopener noreferrer"}
- [AWS Well-Architected Framework - Serverless Applications Lens](https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [Implementing Microservices on AWS](https://docs.aws.amazon.com/whitepapers/latest/microservices-on-aws/introduction.html){:target="_blank" rel="noopener noreferrer"}
- [Choreography vs Orchestration](https://aws.amazon.com/blogs/compute/orchestration-vs-choreography-in-the-land-of-serverless/){:target="_blank" rel="noopener noreferrer"}
- [Amazon EventBridge - Event-Driven Applications](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-what-is.html){:target="_blank" rel="noopener noreferrer"}
- [AWS Step Functions - Orchestration](https://docs.aws.amazon.com/step-functions/latest/dg/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [Fanout Pattern with SNS](https://docs.aws.amazon.com/sns/latest/dg/sns-common-scenarios.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.1.2: Describe differences between stateful and stateless concepts

**Why:** Stateful vs stateless application design is tested through scenarios about scalability, session management, and fault tolerance. You must understand that stateless applications can scale horizontally more easily, how to externalize state to services like DynamoDB or ElastiCache, and when stateful designs are appropriate. Exam questions often describe scaling requirements or ask how to maintain user sessions across multiple instances, requiring knowledge of state management strategies.

**AWS Documentation:**
- [Building Stateless Applications](https://docs.aws.amazon.com/whitepapers/latest/running-containerized-microservices/design-for-scalability.html){:target="_blank" rel="noopener noreferrer"}
- [Stateless vs Stateful Applications](https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/stateless-and-stateful-workflows.html){:target="_blank" rel="noopener noreferrer"}
- [Session State Management](https://aws.amazon.com/caching/session-management/){:target="_blank" rel="noopener noreferrer"}
- [Amazon ElastiCache for Session Management](https://docs.aws.amazon.com/elasticache/latest/red-ug/elasticache-use-cases.html#elasticache-use-cases-session-store){:target="_blank" rel="noopener noreferrer"}
- [Amazon DynamoDB for Session State](https://aws.amazon.com/blogs/database/amazon-dynamodb-session-state-store-for-application-scalability/){:target="_blank" rel="noopener noreferrer"}
- [Elastic Load Balancing - Sticky Sessions](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/sticky-sessions.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.1.3: Describe differences between tightly coupled and loosely coupled components

**Why:** Exam questions frequently test your understanding of coupling in distributed systems. You need to know that tightly coupled components have direct dependencies and synchronous communication, while loosely coupled components communicate asynchronously through intermediaries like queues or event buses. Questions present architectural scenarios and ask you to identify coupling levels or recommend services (SQS, SNS, EventBridge) to reduce coupling and improve system resilience.

**AWS Documentation:**
- [Loosely Coupled Architectures](https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/use-loosely-coupled-dependencies.html){:target="_blank" rel="noopener noreferrer"}
- [Building Loosely Coupled, Scalable Systems](https://aws.amazon.com/blogs/compute/building-loosely-coupled-scalable-c-applications-with-amazon-sqs-and-amazon-sns/){:target="_blank" rel="noopener noreferrer"}
- [Decoupling Applications with Amazon SQS](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-basic-architecture.html){:target="_blank" rel="noopener noreferrer"}
- [Microservices - Loose Coupling](https://docs.aws.amazon.com/whitepapers/latest/microservices-on-aws/distributed-systems-components.html){:target="_blank" rel="noopener noreferrer"}
- [Amazon SNS for Application Decoupling](https://docs.aws.amazon.com/sns/latest/dg/welcome.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.1.4: Describe differences between synchronous and asynchronous patterns

**Why:** Understanding synchronous vs asynchronous communication patterns is essential for designing responsive, scalable applications. The exam tests scenarios where you must choose between blocking requests (synchronous) and fire-and-forget patterns (asynchronous), understand the implications for user experience and system scalability, and select appropriate AWS services (API Gateway with Lambda vs SQS with Lambda). This knowledge helps answer questions about system responsiveness and handling variable workload patterns.

**AWS Documentation:**
- [Asynchronous Messaging Patterns](https://aws.amazon.com/blogs/compute/understanding-asynchronous-messaging-for-microservices/){:target="_blank" rel="noopener noreferrer"}
- [AWS Lambda Synchronous vs Asynchronous Invocation](https://docs.aws.amazon.com/lambda/latest/dg/invocation-sync.html){:target="_blank" rel="noopener noreferrer"}
- [Asynchronous Invocation](https://docs.aws.amazon.com/lambda/latest/dg/invocation-async.html){:target="_blank" rel="noopener noreferrer"}
- [Synchronous Request-Response Pattern](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-overview-developer-experience.html){:target="_blank" rel="noopener noreferrer"}
- [Amazon SQS for Asynchronous Processing](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [Event-Driven vs Request-Response](https://aws.amazon.com/blogs/architecture/lets-architect-event-driven-architectures/){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.1.5: Create fault-tolerant and resilient applications in a programming language (for example, Java, C#, Python, JavaScript, TypeScript, Go)

**Why:** Exam questions test your ability to implement resilience patterns in code. You must understand how to implement retry logic with exponential backoff, circuit breakers to prevent cascading failures, graceful degradation when dependencies fail, and timeout handling. Questions present failure scenarios and expect you to identify the correct resilience pattern or recognize code that implements fault tolerance correctly.

**AWS Documentation:**
- [Implementing Health Checks and Graceful Degradation](https://docs.aws.amazon.com/whitepapers/latest/microservices-on-aws/resilient-microservices.html){:target="_blank" rel="noopener noreferrer"}
- [AWS SDK Retry Behavior and Error Handling](https://docs.aws.amazon.com/general/latest/gr/api-retries.html){:target="_blank" rel="noopener noreferrer"}
- [Resilience and Reliability on AWS](https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [AWS SDK for Python (Boto3) - Error Handling](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/error-handling.html){:target="_blank" rel="noopener noreferrer"}
- [AWS SDK for JavaScript - Error Handling](https://docs.aws.amazon.com/sdk-for-javascript/v3/developer-guide/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [AWS SDK for Java - Exception Handling](https://docs.aws.amazon.com/sdk-for-java/latest/developer-guide/java_sdk_error_handling.html){:target="_blank" rel="noopener noreferrer"}
- [Circuit Breaker Pattern](https://aws.amazon.com/builders-library/avoiding-fallback-in-distributed-systems/){:target="_blank" rel="noopener noreferrer"}
- [Timeouts, Retries, and Backoff with Jitter](https://aws.amazon.com/builders-library/timeouts-retries-and-backoff-with-jitter/){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.1.6: Create, extend, and maintain APIs (for example, response/request transformations, enforcing validation rules, overriding status codes)

**Why:** API development is heavily tested because API Gateway is a core service for serverless and microservices architectures. You need to understand request/response transformations using mapping templates, input validation with request validators and models, custom authorization, CORS configuration, and how to override status codes. Exam questions present API requirements and expect you to configure API Gateway features or write transformation code correctly.

**AWS Documentation:**
- [Amazon API Gateway Developer Guide](https://docs.aws.amazon.com/apigateway/latest/developerguide/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [Working with REST APIs](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-rest-api.html){:target="_blank" rel="noopener noreferrer"}
- [Request and Response Data Mappings](https://docs.aws.amazon.com/apigateway/latest/developerguide/request-response-data-mappings.html){:target="_blank" rel="noopener noreferrer"}
- [API Gateway Mapping Templates](https://docs.aws.amazon.com/apigateway/latest/developerguide/models-mappings.html){:target="_blank" rel="noopener noreferrer"}
- [Request Validation in API Gateway](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-method-request-validation.html){:target="_blank" rel="noopener noreferrer"}
- [API Gateway Request Validators](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-method-request-validation.html){:target="_blank" rel="noopener noreferrer"}
- [Setting up Response Status Codes](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-method-settings-method-response.html){:target="_blank" rel="noopener noreferrer"}
- [Enabling CORS for REST APIs](https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-cors.html){:target="_blank" rel="noopener noreferrer"}
- [API Gateway REST API Models](https://docs.aws.amazon.com/apigateway/latest/developerguide/models-mappings-models.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.1.7: Write and run unit tests in development environments (for example, using AWS SAM)

**Why:** Testing is a fundamental development practice that appears throughout the exam. You must understand how to use AWS SAM CLI for local Lambda testing, write unit tests that mock AWS service calls, use frameworks like pytest or Jest for testing, and validate code before deployment. Exam questions test your knowledge of testing strategies, local development tools, and how to validate serverless applications in development environments.

**AWS Documentation:**
- [AWS Serverless Application Model (SAM)](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html){:target="_blank" rel="noopener noreferrer"}
- [Testing Lambda Functions Locally with AWS SAM CLI](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-using-invoke.html){:target="_blank" rel="noopener noreferrer"}
- [AWS SAM CLI - Local Testing](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-test-and-debug.html){:target="_blank" rel="noopener noreferrer"}
- [Unit Testing Best Practices for AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/lambda-testing.html){:target="_blank" rel="noopener noreferrer"}
- [Testing Lambda Functions](https://docs.aws.amazon.com/lambda/latest/dg/testing-functions.html){:target="_blank" rel="noopener noreferrer"}
- [AWS SAM CLI Installation](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/install-sam-cli.html){:target="_blank" rel="noopener noreferrer"}
- [Mocking AWS Services for Testing](https://aws.amazon.com/blogs/developer/mocking-out-aws-sdk-for-javascript-in-unit-tests/){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.1.8: Write code to use messaging services

**Why:** Messaging services are core to decoupled architectures, and the exam extensively tests your ability to write code for SQS, SNS, and EventBridge. You need to understand how to send messages to queues, publish to topics, receive and delete messages, handle message attributes, implement long polling, and process batches. Questions present messaging scenarios and expect you to write or identify correct SDK code for message handling.

**AWS Documentation:**
- [Amazon SQS Developer Guide](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [Sending Messages to Amazon SQS](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-send-message.html){:target="_blank" rel="noopener noreferrer"}
- [Receiving and Deleting Messages from Amazon SQS](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-receive-delete-message.html){:target="_blank" rel="noopener noreferrer"}
- [Amazon SQS Long Polling](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-short-and-long-polling.html){:target="_blank" rel="noopener noreferrer"}
- [Amazon SNS Developer Guide](https://docs.aws.amazon.com/sns/latest/dg/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [Publishing to Amazon SNS Topics](https://docs.aws.amazon.com/sns/latest/dg/sns-publishing.html){:target="_blank" rel="noopener noreferrer"}
- [Amazon SNS Message Attributes](https://docs.aws.amazon.com/sns/latest/dg/sns-message-attributes.html){:target="_blank" rel="noopener noreferrer"}
- [Using Amazon SQS with AWS SDKs](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-api-examples.html){:target="_blank" rel="noopener noreferrer"}
- [SQS Message Visibility Timeout](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-visibility-timeout.html){:target="_blank" rel="noopener noreferrer"}
- [SQS Dead-Letter Queues](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-dead-letter-queues.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.1.9: Write code that interacts with AWS services by using APIs and AWS SDKs

**Why:** This is one of the most fundamental skills tested throughout the exam. You must know how to use AWS SDKs in your programming language to call AWS services, handle authentication with IAM roles and credentials, implement pagination for large result sets, handle API throttling and rate limits, and properly process SDK responses and errors. Nearly every exam question involving code implementation requires understanding of SDK usage patterns.

**AWS Documentation:**
- [AWS SDKs and Tools](https://aws.amazon.com/developer/tools/){:target="_blank" rel="noopener noreferrer"}
- [AWS SDK for Python (Boto3) Documentation](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html){:target="_blank" rel="noopener noreferrer"}
- [AWS SDK for JavaScript v3 Developer Guide](https://docs.aws.amazon.com/sdk-for-javascript/v3/developer-guide/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [AWS SDK for Java Developer Guide](https://docs.aws.amazon.com/sdk-for-java/latest/developer-guide/home.html){:target="_blank" rel="noopener noreferrer"}
- [AWS SDK for .NET Developer Guide](https://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [AWS SDK for Go Developer Guide](https://docs.aws.amazon.com/sdk-for-go/api/){:target="_blank" rel="noopener noreferrer"}
- [Credentials and Authentication](https://docs.aws.amazon.com/sdk-for-javascript/v3/developer-guide/setting-credentials.html){:target="_blank" rel="noopener noreferrer"}
- [Using IAM Roles for EC2 Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html){:target="_blank" rel="noopener noreferrer"}
- [Pagination with AWS SDKs](https://docs.aws.amazon.com/sdk-for-javascript/v3/developer-guide/pagination.html){:target="_blank" rel="noopener noreferrer"}
- [Handling Errors with AWS SDKs](https://docs.aws.amazon.com/sdk-for-javascript/v3/developer-guide/error-handling.html){:target="_blank" rel="noopener noreferrer"}
- [Best Practices for AWS SDK Usage](https://docs.aws.amazon.com/sdk-for-javascript/v3/developer-guide/welcome.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.1.10: Handle streaming data using AWS services

**Why:** Streaming data processing is tested through scenarios involving real-time analytics, log processing, and event streams. You need to understand Kinesis Data Streams for ingesting and processing streaming data, Kinesis Data Firehose for delivery to data stores, and how to write code that produces and consumes streaming data. Exam questions present real-time processing requirements and expect you to select appropriate streaming services and implement correct processing patterns.

**AWS Documentation:**
- [Amazon Kinesis Data Streams Developer Guide](https://docs.aws.amazon.com/streams/latest/dev/introduction.html){:target="_blank" rel="noopener noreferrer"}
- [Writing Data to Amazon Kinesis Data Streams](https://docs.aws.amazon.com/streams/latest/dev/developing-producers-with-sdk.html){:target="_blank" rel="noopener noreferrer"}
- [Reading Data from Amazon Kinesis Data Streams](https://docs.aws.amazon.com/streams/latest/dev/developing-consumers-with-sdk.html){:target="_blank" rel="noopener noreferrer"}
- [Amazon Kinesis Data Firehose Developer Guide](https://docs.aws.amazon.com/firehose/latest/dev/what-is-this-service.html){:target="_blank" rel="noopener noreferrer"}
- [Processing Streaming Data with AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/with-kinesis.html){:target="_blank" rel="noopener noreferrer"}
- [Kinesis Client Library (KCL)](https://docs.aws.amazon.com/streams/latest/dev/shared-throughput-kcl-consumers.html){:target="_blank" rel="noopener noreferrer"}
- [Kinesis Data Streams - Partition Keys](https://docs.aws.amazon.com/streams/latest/dev/key-concepts.html#partition-key){:target="_blank" rel="noopener noreferrer"}
- [Amazon Kinesis Data Analytics](https://docs.aws.amazon.com/kinesisanalytics/latest/dev/what-is.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.1.11: Use Amazon Q Developer to assist with development

**Why:** Amazon Q Developer is a newer service that represents AWS's AI-powered development assistance. Exam questions test your understanding of how Q Developer can help with code generation, debugging, security scanning, and AWS best practices recommendations. You should know when to leverage Q Developer for development tasks, what capabilities it provides, and how it integrates into development workflows.

**AWS Documentation:**
- [Amazon Q Developer](https://aws.amazon.com/q/developer/){:target="_blank" rel="noopener noreferrer"}
- [Amazon Q Developer User Guide](https://docs.aws.amazon.com/amazonq/latest/qdeveloper-ug/what-is.html){:target="_blank" rel="noopener noreferrer"}
- [Getting Started with Amazon Q Developer](https://docs.aws.amazon.com/amazonq/latest/qdeveloper-ug/getting-started.html){:target="_blank" rel="noopener noreferrer"}
- [Amazon Q Developer Features](https://docs.aws.amazon.com/amazonq/latest/qdeveloper-ug/q-features.html){:target="_blank" rel="noopener noreferrer"}
- [Amazon Q Developer IDE Integration](https://docs.aws.amazon.com/amazonq/latest/qdeveloper-ug/q-in-IDE.html){:target="_blank" rel="noopener noreferrer"}
- [Amazon Q Developer Code Recommendations](https://docs.aws.amazon.com/amazonq/latest/qdeveloper-ug/code-recommendations.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.1.12: Use Amazon EventBridge to implement event-driven patterns

**Why:** EventBridge is heavily tested as the central service for event-driven architectures. You must understand how to create event buses, define event rules and patterns, route events to targets, use event schemas for validation, and implement cross-account event routing. Exam questions present event-driven scenarios and expect you to configure EventBridge rules, write event patterns that match specific events, and select appropriate targets for event processing.

**AWS Documentation:**
- [Amazon EventBridge User Guide](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-what-is.html){:target="_blank" rel="noopener noreferrer"}
- [Getting Started with Amazon EventBridge](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-get-started.html){:target="_blank" rel="noopener noreferrer"}
- [EventBridge Event Patterns](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-event-patterns.html){:target="_blank" rel="noopener noreferrer"}
- [Creating EventBridge Rules](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-create-rule.html){:target="_blank" rel="noopener noreferrer"}
- [EventBridge Targets](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-targets.html){:target="_blank" rel="noopener noreferrer"}
- [EventBridge Event Buses](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-event-bus.html){:target="_blank" rel="noopener noreferrer"}
- [EventBridge Schema Registry](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-schema.html){:target="_blank" rel="noopener noreferrer"}
- [Sending Events to EventBridge](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-putevents.html){:target="_blank" rel="noopener noreferrer"}
- [Cross-Account Event Delivery](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-cross-account.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.1.13: Implement resilient application code for third-party service integrations (for example, retry logic, circuit breakers, error handling patterns)

**Why:** Integration with third-party services requires robust error handling because external dependencies can fail unpredictably. Exam questions test your ability to implement retry logic with exponential backoff and jitter, circuit breaker patterns to prevent cascading failures, timeout handling, and graceful degradation. You must understand when each pattern is appropriate and how to code them correctly to ensure application resilience.

**AWS Documentation:**
- [Error Retries and Exponential Backoff](https://docs.aws.amazon.com/general/latest/gr/api-retries.html){:target="_blank" rel="noopener noreferrer"}
- [Timeouts, Retries, and Backoff with Jitter](https://aws.amazon.com/builders-library/timeouts-retries-and-backoff-with-jitter/){:target="_blank" rel="noopener noreferrer"}
- [Implementing Circuit Breakers](https://aws.amazon.com/builders-library/avoiding-fallback-in-distributed-systems/){:target="_blank" rel="noopener noreferrer"}
- [Resilient Systems Design](https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/design-interactions-in-a-distributed-system-to-prevent-failures.html){:target="_blank" rel="noopener noreferrer"}
- [AWS SDK Retry Configuration](https://docs.aws.amazon.com/sdkref/latest/guide/feature-retry-behavior.html){:target="_blank" rel="noopener noreferrer"}
- [Avoiding Overload in Distributed Systems](https://aws.amazon.com/builders-library/avoiding-overload-in-distributed-systems-by-putting-the-smaller-service-in-control/){:target="_blank" rel="noopener noreferrer"}
- [Graceful Degradation Patterns](https://docs.aws.amazon.com/whitepapers/latest/microservices-on-aws/resilient-microservices.html){:target="_blank" rel="noopener noreferrer"}

**AWS Service FAQs:**

- [Amazon API Gateway FAQ](https://aws.amazon.com/api-gateway/faqs/){:target="_blank" rel="noopener noreferrer"}
- [AWS Lambda FAQ](https://aws.amazon.com/lambda/faqs/){:target="_blank" rel="noopener noreferrer"}
- [Amazon SQS FAQ](https://aws.amazon.com/sqs/faqs/){:target="_blank" rel="noopener noreferrer"}
- [Amazon SNS FAQ](https://aws.amazon.com/sns/faqs/){:target="_blank" rel="noopener noreferrer"}
- [Amazon EventBridge FAQ](https://aws.amazon.com/eventbridge/faqs/){:target="_blank" rel="noopener noreferrer"}
- [Amazon Kinesis Data Streams FAQ](https://aws.amazon.com/kinesis/data-streams/faqs/){:target="_blank" rel="noopener noreferrer"}
- [Amazon Kinesis Data Firehose FAQ](https://aws.amazon.com/kinesis/data-firehose/faqs/){:target="_blank" rel="noopener noreferrer"}
- [AWS Step Functions FAQ](https://aws.amazon.com/step-functions/faqs/){:target="_blank" rel="noopener noreferrer"}
- [AWS SAM FAQ](https://aws.amazon.com/serverless/sam/faqs/){:target="_blank" rel="noopener noreferrer"}
- [Amazon Q Developer FAQ](https://aws.amazon.com/q/developer/faqs/){:target="_blank" rel="noopener noreferrer"}

**AWS Whitepapers:**

- [Microservices on AWS](https://docs.aws.amazon.com/whitepapers/latest/microservices-on-aws/introduction.html){:target="_blank" rel="noopener noreferrer"}
- [Serverless Application Lens - AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [Implementing Microservices on AWS](https://docs.aws.amazon.com/whitepapers/latest/microservices-on-aws/microservices-on-aws.html){:target="_blank" rel="noopener noreferrer"}
- [AWS Serverless Multi-Tier Architectures](https://docs.aws.amazon.com/whitepapers/latest/serverless-multi-tier-architectures-api-gateway-lambda/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [Running Containerized Microservices on AWS](https://docs.aws.amazon.com/whitepapers/latest/running-containerized-microservices/welcome.html){:target="_blank" rel="noopener noreferrer"}

---

## Task 2: Develop code for AWS Lambda

### Skills & Corresponding Documentation

#### Skill 1.2.1: Describe the access of private resources in VPCs from Lambda code

**Why:** VPC integration for Lambda functions is frequently tested because many applications need to access private resources like RDS databases or ElastiCache clusters. You must understand how Lambda functions connect to VPCs, the impact on cold start times, how to configure security groups and subnets for Lambda, and that VPC-connected Lambda functions need NAT gateways to access the internet. Exam questions present scenarios involving private resource access and expect you to configure VPC settings correctly.

**AWS Documentation:**
- [Configuring Lambda Functions to Access Resources in a VPC](https://docs.aws.amazon.com/lambda/latest/dg/configuration-vpc.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda VPC Networking](https://docs.aws.amazon.com/lambda/latest/dg/foundation-networking.html){:target="_blank" rel="noopener noreferrer"}
- [Accessing Internet from VPC Lambda Functions](https://aws.amazon.com/premiumsupport/knowledge-center/internet-access-lambda-function/){:target="_blank" rel="noopener noreferrer"}
- [Lambda Security Groups and Network ACLs](https://docs.aws.amazon.com/lambda/latest/dg/configuration-vpc.html#vpc-configuring){:target="_blank" rel="noopener noreferrer"}
- [Best Practices for Lambda VPC Access](https://docs.aws.amazon.com/lambda/latest/dg/best-practices.html#lambda-vpc){:target="_blank" rel="noopener noreferrer"}
- [VPC Endpoints for Lambda](https://docs.aws.amazon.com/lambda/latest/dg/configuration-vpc-endpoints.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.2.2: Configure Lambda functions by defining environment variables and parameters (for example, memory, concurrency, timeout, runtime, handler, layers, extensions, triggers, destinations)

**Why:** Lambda configuration is one of the most heavily tested topics because it directly impacts function behavior, performance, and cost. You must understand how to set memory (which also affects CPU), configure timeout values, use environment variables for configuration, set concurrency limits, choose the appropriate runtime, specify the handler correctly, use layers for shared code, configure extensions for monitoring, define triggers for invocation, and set up destinations for async success/failure routing. Exam questions frequently present scenarios requiring specific configuration changes.

**AWS Documentation:**
- [Configuring AWS Lambda Functions](https://docs.aws.amazon.com/lambda/latest/dg/lambda-functions.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Environment Variables](https://docs.aws.amazon.com/lambda/latest/dg/configuration-envvars.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Function Configuration](https://docs.aws.amazon.com/lambda/latest/dg/configuration-function-common.html){:target="_blank" rel="noopener noreferrer"}
- [Managing Lambda Function Memory](https://docs.aws.amazon.com/lambda/latest/dg/configuration-memory.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Concurrency](https://docs.aws.amazon.com/lambda/latest/dg/configuration-concurrency.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Function Timeout](https://docs.aws.amazon.com/lambda/latest/dg/configuration-timeout.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Runtimes](https://docs.aws.amazon.com/lambda/latest/dg/lambda-runtimes.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Function Handler](https://docs.aws.amazon.com/lambda/latest/dg/foundation-progmodel.html){:target="_blank" rel="noopener noreferrer"}
- [AWS Lambda Layers](https://docs.aws.amazon.com/lambda/latest/dg/configuration-layers.html){:target="_blank" rel="noopener noreferrer"}
- [Using Lambda Extensions](https://docs.aws.amazon.com/lambda/latest/dg/using-extensions.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Event Source Mappings](https://docs.aws.amazon.com/lambda/latest/dg/invocation-eventsourcemapping.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Destinations](https://docs.aws.amazon.com/lambda/latest/dg/invocation-async.html#invocation-async-destinations){:target="_blank" rel="noopener noreferrer"}
- [Reserved Concurrency vs Provisioned Concurrency](https://docs.aws.amazon.com/lambda/latest/dg/configuration-concurrency.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.2.3: Handle the event lifecycle and errors by using code (for example, Lambda Destinations, dead-letter queues)

**Why:** Error handling in Lambda is critical for building reliable serverless applications. Exam questions test your understanding of how to configure Lambda Destinations for routing successful and failed async invocations, use dead-letter queues for failed synchronous invocations, implement retry behavior, and handle partial batch failures with SQS and Kinesis. You must know the difference between destinations and DLQs, when each is appropriate, and how to configure them correctly.

**AWS Documentation:**
- [Lambda Error Handling and Automatic Retries](https://docs.aws.amazon.com/lambda/latest/dg/invocation-retries.html){:target="_blank" rel="noopener noreferrer"}
- [Asynchronous Invocation Configuration](https://docs.aws.amazon.com/lambda/latest/dg/invocation-async.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Destinations for Asynchronous Invocation](https://docs.aws.amazon.com/lambda/latest/dg/invocation-async.html#invocation-async-destinations){:target="_blank" rel="noopener noreferrer"}
- [Lambda Dead-Letter Queues](https://docs.aws.amazon.com/lambda/latest/dg/invocation-async.html#invocation-dlq){:target="_blank" rel="noopener noreferrer"}
- [Error Handling for Stream-Based Event Sources](https://docs.aws.amazon.com/lambda/latest/dg/with-kinesis.html#services-kinesis-errors){:target="_blank" rel="noopener noreferrer"}
- [Handling Lambda Function Errors](https://docs.aws.amazon.com/lambda/latest/dg/lambda-exceptions.html){:target="_blank" rel="noopener noreferrer"}
- [Reporting Batch Item Failures for SQS](https://docs.aws.amazon.com/lambda/latest/dg/with-sqs.html#services-sqs-batchfailurereporting){:target="_blank" rel="noopener noreferrer"}
- [Lambda Retry Behavior](https://docs.aws.amazon.com/lambda/latest/dg/invocation-retries.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.2.4: Write and run test code by using AWS services and tools

**Why:** Testing Lambda functions is essential for ensuring code quality before deployment. You must understand how to use AWS SAM CLI for local testing, create test events in the Lambda console, use CloudWatch Logs to debug, and write unit tests that mock AWS service calls. Exam questions test your knowledge of testing strategies, local development workflows, and how to validate Lambda functions in development environments before production deployment.

**AWS Documentation:**
- [Testing Lambda Functions](https://docs.aws.amazon.com/lambda/latest/dg/testing-functions.html){:target="_blank" rel="noopener noreferrer"}
- [Invoking Lambda Functions Locally with AWS SAM](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-using-invoke.html){:target="_blank" rel="noopener noreferrer"}
- [Testing Serverless Applications Locally](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-test-and-debug.html){:target="_blank" rel="noopener noreferrer"}
- [AWS SAM CLI Test Commands](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/using-sam-cli-test.html){:target="_blank" rel="noopener noreferrer"}
- [Creating Test Events in Lambda Console](https://docs.aws.amazon.com/lambda/latest/dg/testing-functions.html#creating-test-events){:target="_blank" rel="noopener noreferrer"}
- [Unit Testing AWS Lambda with Python](https://docs.aws.amazon.com/lambda/latest/dg/lambda-python.html){:target="_blank" rel="noopener noreferrer"}
- [Using CloudWatch Logs for Lambda Debugging](https://docs.aws.amazon.com/lambda/latest/dg/monitoring-cloudwatchlogs.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.2.5: Integrate Lambda functions with AWS services

**Why:** Lambda integration with other AWS services is extensively tested because serverless architectures depend on service orchestration. You need to know how to configure Lambda triggers from various sources (API Gateway, S3, DynamoDB Streams, EventBridge, SQS, SNS, Kinesis), understand how event source mappings work, configure IAM permissions for cross-service access, and handle service-specific event formats. Exam questions present integration scenarios and expect you to configure triggers and permissions correctly.

**AWS Documentation:**
- [Using AWS Lambda with Other Services](https://docs.aws.amazon.com/lambda/latest/dg/lambda-services.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda with Amazon S3](https://docs.aws.amazon.com/lambda/latest/dg/with-s3.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda with Amazon DynamoDB](https://docs.aws.amazon.com/lambda/latest/dg/with-ddb.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda with Amazon SQS](https://docs.aws.amazon.com/lambda/latest/dg/with-sqs.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda with Amazon SNS](https://docs.aws.amazon.com/lambda/latest/dg/with-sns.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda with Amazon Kinesis](https://docs.aws.amazon.com/lambda/latest/dg/with-kinesis.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda with API Gateway](https://docs.aws.amazon.com/lambda/latest/dg/services-apigateway.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda with EventBridge](https://docs.aws.amazon.com/lambda/latest/dg/services-cloudwatchevents.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Event Source Mappings](https://docs.aws.amazon.com/lambda/latest/dg/invocation-eventsourcemapping.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Execution Role](https://docs.aws.amazon.com/lambda/latest/dg/lambda-intro-execution-role.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Resource-Based Policies](https://docs.aws.amazon.com/lambda/latest/dg/access-control-resource-based.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.2.6: Tune Lambda functions for optimal performance

**Why:** Performance optimization is tested through scenarios requiring you to minimize cold starts, optimize memory allocation for cost and speed, use provisioned concurrency for consistent performance, implement caching strategies, minimize deployment package size, and reduce execution time. You must understand the relationship between memory and CPU allocation, connection reuse best practices, and how to profile Lambda functions. Exam questions present performance requirements and expect you to identify appropriate optimization techniques.

**AWS Documentation:**
- [Lambda Performance Optimization](https://docs.aws.amazon.com/lambda/latest/dg/best-practices.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Cold Starts](https://docs.aws.amazon.com/lambda/latest/dg/foundation-arch.html){:target="_blank" rel="noopener noreferrer"}
- [Optimizing Lambda Function Performance](https://docs.aws.amazon.com/lambda/latest/operatorguide/perf-optimize.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Provisioned Concurrency](https://docs.aws.amazon.com/lambda/latest/dg/provisioned-concurrency.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Power Tuning](https://docs.aws.amazon.com/lambda/latest/operatorguide/profile-functions.html){:target="_blank" rel="noopener noreferrer"}
- [Best Practices for Working with Lambda](https://docs.aws.amazon.com/lambda/latest/dg/best-practices.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Function Scaling](https://docs.aws.amazon.com/lambda/latest/dg/invocation-scaling.html){:target="_blank" rel="noopener noreferrer"}
- [Reducing Lambda Deployment Package Size](https://docs.aws.amazon.com/lambda/latest/dg/gettingstarted-limits.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda /tmp Storage](https://docs.aws.amazon.com/lambda/latest/dg/configuration-filesystem.html){:target="_blank" rel="noopener noreferrer"}
- [Connection Management in Lambda](https://docs.aws.amazon.com/lambda/latest/dg/best-practices.html#lambda-connection-mgmt){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.2.7: Use Lambda functions to process and transform data in near real time

**Why:** Real-time data processing with Lambda is tested through scenarios involving streaming data from Kinesis, processing S3 events as files are uploaded, transforming DynamoDB Streams records, and implementing ETL pipelines. You must understand batch processing for streams, checkpointing mechanisms, how to handle processing failures, and patterns for data transformation. Exam questions present real-time processing requirements and expect you to configure Lambda for stream processing correctly.

**AWS Documentation:**
- [Lambda with Kinesis Data Streams](https://docs.aws.amazon.com/lambda/latest/dg/with-kinesis.html){:target="_blank" rel="noopener noreferrer"}
- [Processing DynamoDB Streams with Lambda](https://docs.aws.amazon.com/lambda/latest/dg/with-ddb.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Event Filtering](https://docs.aws.amazon.com/lambda/latest/dg/invocation-eventfiltering.html){:target="_blank" rel="noopener noreferrer"}
- [Batch Processing with Lambda](https://docs.aws.amazon.com/lambda/latest/dg/with-kinesis.html#services-kinesis-batchwindow){:target="_blank" rel="noopener noreferrer"}
- [Kinesis and Lambda Parallelization](https://docs.aws.amazon.com/lambda/latest/dg/with-kinesis.html#services-kinesis-parallelization){:target="_blank" rel="noopener noreferrer"}
- [Real-Time Stream Processing](https://docs.aws.amazon.com/lambda/latest/dg/with-kinesis-example.html){:target="_blank" rel="noopener noreferrer"}
- [Lambda Tumbling Window for Aggregations](https://docs.aws.amazon.com/lambda/latest/dg/with-kinesis.html#services-kinesis-windows){:target="_blank" rel="noopener noreferrer"}
- [Monitoring Stream-Based Event Sources](https://docs.aws.amazon.com/lambda/latest/dg/monitoring-metrics.html){:target="_blank" rel="noopener noreferrer"}

**AWS Service FAQs:**

- [AWS Lambda FAQ](https://aws.amazon.com/lambda/faqs/){:target="_blank" rel="noopener noreferrer"}
- [AWS SAM FAQ](https://aws.amazon.com/serverless/sam/faqs/){:target="_blank" rel="noopener noreferrer"}
- [Amazon VPC FAQ](https://aws.amazon.com/vpc/faqs/){:target="_blank" rel="noopener noreferrer"}
- [Amazon CloudWatch FAQ](https://aws.amazon.com/cloudwatch/faqs/){:target="_blank" rel="noopener noreferrer"}

**AWS Whitepapers:**

- [Serverless Application Lens - AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [AWS Lambda Operator Guide](https://docs.aws.amazon.com/lambda/latest/operatorguide/intro.html){:target="_blank" rel="noopener noreferrer"}
- [Best Practices for Developing on AWS Lambda](https://docs.aws.amazon.com/whitepapers/latest/serverless-multi-tier-architectures-api-gateway-lambda/best-practices-for-developing-on-aws-lambda.html){:target="_blank" rel="noopener noreferrer"}

---

## Task 3: Use data stores in application development

### Skills & Corresponding Documentation

#### Skill 1.3.1: Describe high-cardinality partition keys for balanced partition access

**Why:** Partition key design is critical for DynamoDB performance and is heavily tested. You must understand that high-cardinality partition keys distribute data evenly across partitions, prevent hot partitions, and enable horizontal scaling. Low-cardinality keys (like status or region) create uneven distribution and performance bottlenecks. Exam questions present table design scenarios and expect you to identify appropriate partition keys that ensure balanced data distribution and optimal throughput.

**AWS Documentation:**
- [DynamoDB Partition Keys](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.html#HowItWorks.CoreComponents.PrimaryKey){:target="_blank" rel="noopener noreferrer"}
- [Choosing the Right DynamoDB Partition Key](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/bp-partition-key-design.html){:target="_blank" rel="noopener noreferrer"}
- [DynamoDB Best Practices for Partition Keys](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/best-practices.html#best-practices-partition-key){:target="_blank" rel="noopener noreferrer"}
- [Understanding DynamoDB Adaptive Capacity](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/bp-partition-key-uniform-load.html){:target="_blank" rel="noopener noreferrer"}
- [Avoiding Hot Partitions in DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/bp-partition-key-sharding.html){:target="_blank" rel="noopener noreferrer"}
- [DynamoDB Partitions and Data Distribution](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.Partitions.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.3.2: Describe database consistency models (for example, strongly consistent, eventually consistent)

**Why:** Consistency models affect data accuracy and read performance, and exam questions test your understanding of when to use each model. You must know that DynamoDB offers eventually consistent reads (default, faster, cheaper) and strongly consistent reads (guaranteed latest data, higher latency, more expensive). You should understand read-after-write consistency, how replication affects consistency, and trade-offs between consistency and performance. Questions present data accuracy requirements and expect you to choose the appropriate consistency level.

**AWS Documentation:**
- [DynamoDB Data Consistency](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.ReadConsistency.html){:target="_blank" rel="noopener noreferrer"}
- [Read Consistency in DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.ReadConsistency.html){:target="_blank" rel="noopener noreferrer"}
- [Eventually Consistent Reads](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.ReadConsistency.html#HowItWorks.ReadConsistency.EventuallyConsistent){:target="_blank" rel="noopener noreferrer"}
- [Strongly Consistent Reads](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.ReadConsistency.html#HowItWorks.ReadConsistency.StronglyConsistent){:target="_blank" rel="noopener noreferrer"}
- [DynamoDB Transactions](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/transaction-apis.html){:target="_blank" rel="noopener noreferrer"}
- [RDS Read Replicas and Consistency](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ReadRepl.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.3.3: Describe differences between query and scan operations

**Why:** Understanding query vs scan is fundamental for DynamoDB performance and cost optimization. You must know that queries retrieve items using partition key and optional sort key (efficient, fast, predictable cost), while scans examine every item in the table (expensive, slow, unpredictable). Exam questions present data retrieval scenarios and expect you to identify when queries are possible versus when scans are necessary, understand filter expressions, and recognize performance implications of each operation.

**AWS Documentation:**
- [DynamoDB Query Operation](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Query.html){:target="_blank" rel="noopener noreferrer"}
- [DynamoDB Scan Operation](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Scan.html){:target="_blank" rel="noopener noreferrer"}
- [Query vs Scan Performance](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/bp-query-scan.html){:target="_blank" rel="noopener noreferrer"}
- [DynamoDB Filter Expressions](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Query.FilterExpression.html){:target="_blank" rel="noopener noreferrer"}
- [Best Practices for Querying and Scanning](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/best-practices.html#best-practices-querying-and-scanning){:target="_blank" rel="noopener noreferrer"}
- [Parallel Scans in DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Scan.html#Scan.ParallelScan){:target="_blank" rel="noopener noreferrer"}
- [DynamoDB Pagination](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Query.Pagination.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.3.4: Define Amazon DynamoDB keys and indexing

**Why:** DynamoDB key structures and indexes are extensively tested because they determine data access patterns and query capabilities. You must understand partition keys and sort keys (composite primary keys), Global Secondary Indexes for alternative access patterns, Local Secondary Indexes for additional sort keys, projection types (ALL, KEYS_ONLY, INCLUDE), and index throughput considerations. Exam questions present access pattern requirements and expect you to design appropriate key structures and indexes.

**AWS Documentation:**
- [DynamoDB Core Components](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.html){:target="_blank" rel="noopener noreferrer"}
- [DynamoDB Primary Keys](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.html#HowItWorks.CoreComponents.PrimaryKey){:target="_blank" rel="noopener noreferrer"}
- [DynamoDB Secondary Indexes](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/SecondaryIndexes.html){:target="_blank" rel="noopener noreferrer"}
- [Global Secondary Indexes](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GSI.html){:target="_blank" rel="noopener noreferrer"}
- [Local Secondary Indexes](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/LSI.html){:target="_blank" rel="noopener noreferrer"}
- [Designing Partition Keys](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/bp-partition-key-design.html){:target="_blank" rel="noopener noreferrer"}
- [Index Projections](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GSI.html#GSI.Projections){:target="_blank" rel="noopener noreferrer"}
- [Sparse Indexes in DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/bp-indexes-general-sparse-indexes.html){:target="_blank" rel="noopener noreferrer"}
- [Best Practices for Secondary Indexes](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/bp-indexes.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.3.5: Serialize and deserialize data to provide persistence to a data store

**Why:** Serialization is tested because applications must convert between programming language objects and storage formats. You need to understand JSON serialization for API communication, how DynamoDB stores different data types, converting objects to/from database records, handling complex data structures, and using SDK type converters. Exam questions may present code that serializes/deserializes data and expect you to identify correct implementations or troubleshoot serialization errors.

**AWS Documentation:**
- [DynamoDB Data Types](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.NamingRulesDataTypes.html){:target="_blank" rel="noopener noreferrer"}
- [DynamoDB Data Type Descriptors](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Programming.LowLevelAPI.html#Programming.LowLevelAPI.DataTypeDescriptors){:target="_blank" rel="noopener noreferrer"}
- [Working with Items in DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/WorkingWithItems.html){:target="_blank" rel="noopener noreferrer"}
- [DynamoDB Document Client (JavaScript)](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/dynamodb-example-document-client.html){:target="_blank" rel="noopener noreferrer"}
- [Boto3 DynamoDB Type Conversion](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/customizations/dynamodb.html){:target="_blank" rel="noopener noreferrer"}
- [JSON in DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Programming.LowLevelAPI.html){:target="_blank" rel="noopener noreferrer"}
- [S3 Object Serialization](https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingObjects.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.3.6: Use, manage, and maintain data stores

**Why:** Data store management is tested through operational scenarios involving backup, restore, monitoring, capacity planning, and maintenance tasks. You must understand DynamoDB on-demand vs provisioned capacity, auto-scaling, point-in-time recovery, global tables for multi-region replication, RDS maintenance windows, automated backups, and read replicas. Exam questions present operational requirements and expect you to configure appropriate management settings.

**AWS Documentation:**
- [Managing DynamoDB Tables](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/WorkingWithTables.html){:target="_blank" rel="noopener noreferrer"}
- [DynamoDB Capacity Modes](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.ReadWriteCapacityMode.html){:target="_blank" rel="noopener noreferrer"}
- [DynamoDB Auto Scaling](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/AutoScaling.html){:target="_blank" rel="noopener noreferrer"}
- [DynamoDB Backup and Restore](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/BackupRestore.html){:target="_blank" rel="noopener noreferrer"}
- [DynamoDB Point-in-Time Recovery](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/PointInTimeRecovery.html){:target="_blank" rel="noopener noreferrer"}
- [DynamoDB Global Tables](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GlobalTables.html){:target="_blank" rel="noopener noreferrer"}
- [Amazon RDS Maintenance](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_UpgradeDBInstance.Maintenance.html){:target="_blank" rel="noopener noreferrer"}
- [RDS Automated Backups](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithAutomatedBackups.html){:target="_blank" rel="noopener noreferrer"}
- [RDS Read Replicas](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ReadRepl.html){:target="_blank" rel="noopener noreferrer"}
- [Amazon S3 Versioning](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Versioning.html){:target="_blank" rel="noopener noreferrer"}
- [S3 Lifecycle Policies](https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lifecycle-mgmt.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.3.7: Manage data lifecycles

**Why:** Data lifecycle management is tested through scenarios involving data retention, archival, and deletion policies. You must understand S3 lifecycle policies to transition objects between storage classes, DynamoDB TTL for automatic item expiration, RDS snapshot retention, and automated cleanup strategies. Exam questions present data retention requirements and expect you to configure lifecycle policies that balance cost and compliance needs.

**AWS Documentation:**
- [Amazon S3 Lifecycle Management](https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lifecycle-mgmt.html){:target="_blank" rel="noopener noreferrer"}
- [S3 Lifecycle Configuration](https://docs.aws.amazon.com/AmazonS3/latest/userguide/how-to-set-lifecycle-configuration-intro.html){:target="_blank" rel="noopener noreferrer"}
- [S3 Lifecycle Transitions](https://docs.aws.amazon.com/AmazonS3/latest/userguide/lifecycle-transition-general-considerations.html){:target="_blank" rel="noopener noreferrer"}
- [DynamoDB Time to Live (TTL)](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/TTL.html){:target="_blank" rel="noopener noreferrer"}
- [Enabling TTL on DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/time-to-live-ttl-how-to.html){:target="_blank" rel="noopener noreferrer"}
- [RDS Snapshot Retention](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithAutomatedBackups.html#USER_WorkingWithAutomatedBackups.BackupRetention){:target="_blank" rel="noopener noreferrer"}
- [S3 Expiration Actions](https://docs.aws.amazon.com/AmazonS3/latest/userguide/lifecycle-expire-general-considerations.html){:target="_blank" rel="noopener noreferrer"}
- [S3 Intelligent-Tiering](https://docs.aws.amazon.com/AmazonS3/latest/userguide/intelligent-tiering.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.3.8: Use data caching services

**Why:** Caching is extensively tested because it's a fundamental performance optimization technique. You must understand ElastiCache for Redis and Memcached, DynamoDB Accelerator (DAX) for single-digit millisecond DynamoDB reads, cache invalidation strategies, cache-aside vs write-through patterns, and when caching provides the most benefit. Exam questions present performance requirements and expect you to select appropriate caching solutions and implement caching patterns correctly.

**AWS Documentation:**
- [Amazon ElastiCache](https://docs.aws.amazon.com/elasticache/){:target="_blank" rel="noopener noreferrer"}
- [ElastiCache for Redis](https://docs.aws.amazon.com/elasticache/latest/red-ug/WhatIs.html){:target="_blank" rel="noopener noreferrer"}
- [ElastiCache for Memcached](https://docs.aws.amazon.com/elasticache/latest/mem-ug/WhatIs.html){:target="_blank" rel="noopener noreferrer"}
- [Caching Strategies](https://docs.aws.amazon.com/elasticache/latest/mem-ug/Strategies.html){:target="_blank" rel="noopener noreferrer"}
- [DynamoDB Accelerator (DAX)](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DAX.html){:target="_blank" rel="noopener noreferrer"}
- [DAX vs ElastiCache](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DAX.html#DAX.vs.elasticache){:target="_blank" rel="noopener noreferrer"}
- [Cache-Aside Pattern](https://docs.aws.amazon.com/whitepapers/latest/database-caching-strategies-using-redis/caching-patterns.html){:target="_blank" rel="noopener noreferrer"}
- [Write-Through Caching](https://docs.aws.amazon.com/whitepapers/latest/database-caching-strategies-using-redis/write-through.html){:target="_blank" rel="noopener noreferrer"}
- [CloudFront Caching](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/ConfiguringCaching.html){:target="_blank" rel="noopener noreferrer"}
- [API Gateway Caching](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-caching.html){:target="_blank" rel="noopener noreferrer"}

#### Skill 1.3.9: Use specialized data stores based on access patterns (for example, Amazon OpenSearch Service)

**Why:** Choosing the right database for specific access patterns is tested through scenarios that require specialized query capabilities. You must understand when to use OpenSearch for full-text search and analytics, DocumentDB for MongoDB-compatible document storage, Neptune for graph databases, Timestream for time-series data, and QLDB for immutable ledger requirements. Exam questions describe access patterns and data characteristics, expecting you to identify the most appropriate specialized data store.

**AWS Documentation:**
- [Amazon OpenSearch Service](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/what-is.html){:target="_blank" rel="noopener noreferrer"}
- [OpenSearch Service Use Cases](https://aws.amazon.com/opensearch-service/){:target="_blank" rel="noopener noreferrer"}
- [Getting Started with Amazon OpenSearch Service](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/gsgcreate-domain.html){:target="_blank" rel="noopener noreferrer"}
- [Amazon DocumentDB](https://docs.aws.amazon.com/documentdb/){:target="_blank" rel="noopener noreferrer"}
- [Amazon Neptune (Graph Database)](https://docs.aws.amazon.com/neptune/){:target="_blank" rel="noopener noreferrer"}
- [Amazon Timestream](https://docs.aws.amazon.com/timestream/){:target="_blank" rel="noopener noreferrer"}
- [Amazon QLDB (Ledger Database)](https://docs.aws.amazon.com/qldb/){:target="_blank" rel="noopener noreferrer"}
- [Choosing the Right Database](https://aws.amazon.com/products/databases/){:target="_blank" rel="noopener noreferrer"}
- [AWS Database Services Overview](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/database.html){:target="_blank" rel="noopener noreferrer"}
- [Purpose-Built Databases](https://aws.amazon.com/products/databases/freedom/){:target="_blank" rel="noopener noreferrer"}

**AWS Service FAQs:**

- [Amazon DynamoDB FAQ](https://aws.amazon.com/dynamodb/faqs/){:target="_blank" rel="noopener noreferrer"}
- [Amazon RDS FAQ](https://aws.amazon.com/rds/faqs/){:target="_blank" rel="noopener noreferrer"}
- [Amazon S3 FAQ](https://aws.amazon.com/s3/faqs/){:target="_blank" rel="noopener noreferrer"}
- [Amazon ElastiCache FAQ](https://aws.amazon.com/elasticache/faqs/){:target="_blank" rel="noopener noreferrer"}
- [DynamoDB Accelerator (DAX) FAQ](https://aws.amazon.com/dynamodb/dax/faqs/){:target="_blank" rel="noopener noreferrer"}
- [Amazon OpenSearch Service FAQ](https://aws.amazon.com/opensearch-service/faqs/){:target="_blank" rel="noopener noreferrer"}
- [Amazon DocumentDB FAQ](https://aws.amazon.com/documentdb/faqs/){:target="_blank" rel="noopener noreferrer"}
- [Amazon Neptune FAQ](https://aws.amazon.com/neptune/faqs/){:target="_blank" rel="noopener noreferrer"}
- [Amazon Aurora FAQ](https://aws.amazon.com/rds/aurora/faqs/){:target="_blank" rel="noopener noreferrer"}

**AWS Whitepapers:**

- [Best Practices for DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/best-practices.html){:target="_blank" rel="noopener noreferrer"}
- [Database Caching Strategies Using Redis](https://docs.aws.amazon.com/whitepapers/latest/database-caching-strategies-using-redis/welcome.html){:target="_blank" rel="noopener noreferrer"}
- [AWS Database Services Overview](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/database.html){:target="_blank" rel="noopener noreferrer"}
- [Reliability Pillar - AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/welcome.html){:target="_blank" rel="noopener noreferrer"}

---

## Final Thoughts

Domain 1: Development with AWS Services is the foundation of the AWS Developer Associate certification and represents the largest portion of the exam. Success requires hands-on coding experience with AWS services—reading documentation alone is insufficient. Set up a development environment with AWS SAM CLI, practice writing Lambda functions in your preferred language, experiment with DynamoDB table designs, and build event-driven applications using SQS, SNS, and EventBridge. Focus heavily on understanding architectural patterns, Lambda configuration and optimization, DynamoDB access patterns and indexing, and SDK usage for programmatic AWS interaction. The skills you build here are directly applicable to real-world serverless development and will serve as the technical foundation for the remaining exam domains.
