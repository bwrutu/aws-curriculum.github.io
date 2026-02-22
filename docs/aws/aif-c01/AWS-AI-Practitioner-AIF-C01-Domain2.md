# AWS Certified AI Practitioner (AIF-C01) Domain 2
## Fundamentals of Generative AI

**Official Exam Guide:** <a href="https://aws.amazon.com/certification/certified-ai-practitioner/" target="_blank">AWS Certified AI Practitioner Exam Guide</a>  
**Skill Builder:** <a href="https://skillbuilder.aws/learning-plans/ai-practitioner" target="_blank">AWS AI Practitioner Learning Plan</a>

---

## Domain Overview

**Domain Weight:** 24% of the exam (largest domain)

This domain tests your understanding of generative AI concepts, foundation models, prompt engineering, and AWS services for generative AI.

---

## How to Study This Domain Effectively

### Study Tips

1. **Understand generative AI vs traditional ML** - Know the difference between discriminative models (classify/predict) and generative models (create new content). Exam tests whether you understand when to use generative AI.

2. **Learn foundation models** - Understand what foundation models are, how they're trained (pre-training on massive data), and their capabilities (text, images, code generation). Know the difference between foundation models and traditional ML models.

3. **Master prompt engineering** - Prompting is how you interact with LLMs. Understand techniques like zero-shot, few-shot, chain-of-thought prompting. Questions test whether you can identify effective prompts for specific tasks.

4. **Know AWS generative AI services** - Amazon Bedrock (access foundation models), Amazon Q (business assistant), SageMaker JumpStart. Match services to use cases.

5. **Understand model capabilities and limitations** - LLMs can generate text, answer questions, summarize, translate. But they can also hallucinate (generate incorrect information). Know the strengths and weaknesses.

### Recommended Approach

1. Start with **generative AI fundamentals** - What it is, how it differs from traditional ML
2. Learn **foundation models** - Pre-training, fine-tuning, model types
3. Study **prompt engineering** - Techniques for better outputs
4. Master **Amazon Bedrock** - AWS's primary generative AI service
5. Understand **RAG and model customization** - Improving model outputs

---

## Task 2.1: Explain the basic concepts of generative AI

### Key Concepts

#### 1. Generative AI vs Traditional ML

**Why:** Understanding the difference is fundamental. Traditional ML classifies or predicts based on patterns. Generative AI creates new content (text, images, code, audio).

**Key Differences:**
- **Traditional ML**: Discriminative (classifies, predicts)
- **Generative AI**: Generative (creates new content)

**Use Cases:**
- Traditional ML: Fraud detection, image classification, price prediction
- Generative AI: Content creation, code generation, chatbots, image generation

**AWS Documentation:**
- <a href="https://aws.amazon.com/what-is/generative-ai/" target="_blank">What is Generative AI?</a>
- <a href="https://aws.amazon.com/generative-ai/" target="_blank">Generative AI on AWS</a>

#### 2. Foundation Models (FMs)

**Why:** Foundation models are large models pre-trained on vast data that can be adapted for many tasks. Understanding FMs is central to generative AI.

**Key Concepts:**
- Pre-trained on massive datasets
- Can be fine-tuned for specific tasks
- Transfer learning capabilities
- Types: LLMs (text), vision models (images), multimodal models

**Examples:**
- **Language Models**: Claude, Llama, Titan Text
- **Image Models**: Stable Diffusion, Titan Image
- **Multimodal**: Claude (text + images)

**AWS Documentation:**
- <a href="https://aws.amazon.com/bedrock/foundation-models/" target="_blank">Foundation Models on Amazon Bedrock</a>
- <a href="https://aws.amazon.com/bedrock/titan/" target="_blank">Amazon Titan Models</a>

#### 3. Large Language Models (LLMs)

**Why:** LLMs are the most common type of foundation model. Understanding LLM capabilities (text generation, question answering, summarization, translation) helps you identify appropriate use cases.

**Capabilities:**
- Text generation and completion
- Question answering
- Summarization
- Translation
- Code generation
- Conversational AI

**AWS Documentation:**
- <a href="https://aws.amazon.com/what-is/large-language-model/" target="_blank">Large Language Models on AWS</a>

---

## Task 2.2: Understand prompt engineering

### Key Concepts

#### 1. What is Prompt Engineering?

**Why:** Prompts are how you communicate with LLMs. Better prompts yield better outputs. Understanding prompt engineering helps you get accurate, relevant responses from AI models.

**Key Concepts:**
- Input text that guides model output
- Includes instructions, context, examples
- Quality of prompt affects quality of response

#### 2. Prompt Engineering Techniques

**Why:** Different techniques work for different tasks. Exam tests whether you can identify appropriate prompting strategies.

**Techniques:**
- **Zero-shot**: Task without examples (simple instructions)
- **Few-shot**: Providing examples in the prompt
- **Chain-of-thought**: Step-by-step reasoning
- **Role-playing**: Assigning a role to the model
- **Clear instructions**: Specific, detailed prompts

**Examples:**

**Zero-shot:**
```
Translate this to Spanish: "Hello, how are you?"
```

**Few-shot:**
```
English: cat → Spanish: gato
English: dog → Spanish: perro
English: bird → Spanish: ?
```

**Chain-of-thought:**
```
Let's solve this step by step:
1. First, identify...
2. Then, calculate...
3. Finally, conclude...
```

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/bedrock/latest/userguide/prompt-engineering-guidelines.html" target="_blank">Prompt Engineering Guide</a>

---

## Task 2.3: Identify AWS services for generative AI

### Key Services

#### 1. Amazon Bedrock

**Why:** Bedrock is AWS's primary service for accessing foundation models. Understanding Bedrock is essential for the exam.

**Key Features:**
- Access to multiple foundation models (Anthropic Claude, Meta Llama, Stability AI, Amazon Titan)
- API-based access
- No infrastructure management
- Serverless
- Fine-tuning capabilities
- Model evaluation

**Use Cases:**
- Text generation and summarization
- Conversational AI and chatbots
- Code generation
- Image generation
- Content creation

**AWS Documentation:**
- <a href="https://aws.amazon.com/bedrock/" target="_blank">Amazon Bedrock</a>
- <a href="https://docs.aws.amazon.com/bedrock/latest/userguide/what-is-bedrock.html" target="_blank">Bedrock User Guide</a>
- <a href="https://aws.amazon.com/bedrock/foundation-models/" target="_blank">Bedrock Models</a>

#### 2. Amazon Q

**Why:** Amazon Q is AWS's AI-powered business assistant. It helps with AWS-related questions, code generation, and business intelligence.

**Capabilities:**
- Answer questions about AWS
- Code suggestions and generation
- Troubleshooting assistance
- Data analysis and insights

**AWS Documentation:**
- <a href="https://aws.amazon.com/q/" target="_blank">Amazon Q</a>
- <a href="https://aws.amazon.com/q/developer/" target="_blank">Amazon Q Developer</a>

#### 3. Amazon SageMaker JumpStart

**Why:** JumpStart provides pre-trained models and solutions for quick deployment.

**Features:**
- Access to pre-trained models
- One-click deployment
- Fine-tuning capabilities
- Solution templates

**AWS Documentation:**
- <a href="https://aws.amazon.com/sagemaker/jumpstart/" target="_blank">SageMaker JumpStart</a>

---

## Task 2.4: Understand model customization and improvement

### Key Concepts

#### 1. Retrieval Augmented Generation (RAG)

**Why:** RAG improves LLM responses by providing relevant context from external knowledge sources. This reduces hallucinations and provides up-to-date information.

**How it Works:**
1. User asks a question
2. System retrieves relevant documents
3. Documents are added to the prompt
4. LLM generates response using provided context

**Benefits:**
- Reduces hallucinations
- Provides source attribution
- Access to current information
- Domain-specific knowledge

**AWS Services:**
- Amazon Bedrock Knowledge Bases
- Amazon Kendra (search)
- Vector databases (OpenSearch, RDS pgvector)

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/bedrock/latest/userguide/knowledge-base.html" target="_blank">RAG with Amazon Bedrock</a>

#### 2. Fine-tuning

**Why:** Fine-tuning adapts foundation models to specific tasks or domains using your own data.

**Key Concepts:**
- Continued training on domain-specific data
- Improves performance on specific tasks
- Requires labeled data
- More resource-intensive than RAG

**When to Use:**
- Need specific behavior or style
- Domain-specific terminology
- Consistent output format

**AWS Documentation:**
- <a href="https://docs.aws.amazon.com/bedrock/latest/userguide/custom-models.html" target="_blank">Fine-tuning in Bedrock</a>

#### 3. Prompt Optimization

**Why:** Improving prompts is often the easiest way to get better outputs.

**Techniques:**
- Add context and examples
- Be specific and clear
- Use step-by-step instructions
- Specify output format
- Iterate and refine

---

## Understanding Model Outputs and Limitations

### Hallucinations

**Why:** LLMs can generate plausible-sounding but incorrect information. Understanding this limitation is critical.

**What are Hallucinations:**
- Confident but false statements
- Made-up facts, sources, or data
- Occurs because models predict likely text, not truth

**Mitigation Strategies:**
- Use RAG to ground responses in facts
- Request source citations
- Verify critical information
- Use structured outputs
- Human review for important tasks

### Token Limits

**Why:** Foundation models have maximum context lengths (token limits).

**Key Concepts:**
- Tokens ≈ words (1 token ≈ 0.75 words)
- Context window: Maximum input + output tokens
- Different models have different limits
- Long documents may need chunking

---

## AWS Service FAQs

- <a href="https://aws.amazon.com/bedrock/faqs/" target="_blank">Amazon Bedrock FAQs</a>
- <a href="https://aws.amazon.com/q/faqs/" target="_blank">Amazon Q FAQs</a>
- <a href="https://aws.amazon.com/sagemaker/faqs/" target="_blank">SageMaker JumpStart FAQs</a>

---

## AWS Whitepapers and Resources

1. **<a href="https://aws.amazon.com/generative-ai/" target="_blank">Generative AI on AWS</a>**
2. **<a href="https://catalog.workshops.aws/amazon-bedrock/" target="_blank">Amazon Bedrock Workshop</a>**
3. **<a href="https://docs.aws.amazon.com/bedrock/latest/userguide/prompt-engineering-guidelines.html" target="_blank">Prompt Engineering Guide</a>**

---

## Final Thoughts on Domain 2

Domain 2 (Fundamentals of Generative AI) represents **24% of the exam** - the largest domain.

### Key Takeaways:

1. **Understand generative AI** - Creates new content vs classifies existing content
2. **Master foundation models** - Pre-trained on massive data, adaptable to many tasks
3. **Learn prompt engineering** - Zero-shot, few-shot, chain-of-thought techniques
4. **Know Amazon Bedrock** - Primary AWS service for accessing foundation models
5. **Understand RAG** - Improves accuracy by providing context
6. **Recognize limitations** - Hallucinations, token limits, bias

### Common Exam Patterns:

- **Scenario: Generate marketing copy** → Amazon Bedrock with text generation model
- **Scenario: Reduce hallucinations** → Implement RAG
- **Scenario: Need step-by-step reasoning** → Use chain-of-thought prompting
- **Scenario: Domain-specific responses** → Fine-tune model or use RAG
- **Scenario: AWS-specific questions** → Amazon Q
- **Scenario: Quick model deployment** → SageMaker JumpStart

Master generative AI fundamentals - this is the core of the AI Practitioner exam!
