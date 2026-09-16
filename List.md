# Complete GenAI / Agentic AI Interview Topic Map

### Priority legend

* 🔴 **Must know deeply** — very likely / important
* 🟠 **Strong working knowledge** — likely follow-ups
* 🟡 **Know the concepts** — useful breadth
* ⚪ **Optional / specialized**

---

# 1. LLM FUNDAMENTALS

### 1.1 Transformer fundamentals 🔴

* Transformer architecture
* Encoder vs decoder vs encoder-decoder
* Self-attention
* Multi-head attention
* Query / Key / Value
* Causal attention
* Cross-attention
* Positional encoding
* RoPE
* Feed-forward layers
* Layer normalization
* Residual connections
* Autoregressive generation
* Next-token prediction

### 1.2 Tokenization 🔴

* Tokens
* BPE
* SentencePiece
* Token limits
* Context window
* Token counting
* Input vs output tokens
* Tokenization impact on cost
* Tokenization impact on latency

### 1.3 Model behavior 🔴

* Temperature
* Top-k
* Top-p
* Deterministic generation
* Sampling
* Hallucination
* Context limitations
* Reasoning models vs standard LLMs
* Long-context behavior

### 1.4 Model selection 🔴

* Large vs small models
* Open-source vs proprietary
* Quality vs latency vs cost
* Reasoning models
* Multimodal models
* Fine-tuned models
* Model routing
* Model cascading

### 1.5 LLM APIs 🔴

* Chat/completion APIs
* Structured output
* JSON schema
* Streaming
* Tool/function calling
* Batch APIs
* Async inference
* Rate limits
* Context limits
* Error handling

---

# 2. PROMPT ENGINEERING

### 2.1 Prompt fundamentals 🔴

* System prompts
* User prompts
* Developer instructions
* Few-shot prompting
* Zero-shot prompting
* Role prompting
* Output constraints
* Structured prompting

### 2.2 Advanced prompting 🟠

* Prompt decomposition
* Query rewriting
* Self-reflection
* Critic patterns
* Planning prompts
* Routing prompts
* Context construction
* Dynamic prompts
* Prompt templates

### 2.3 Prompt engineering limitations 🔴

* Prompt injection
* Prompt leakage
* Instruction conflicts
* Context poisoning
* Overly long prompts
* Prompt brittleness
* Prompt versioning

**Important interview principle:**

> Prompting is not a substitute for authorization, validation, or business logic.

---

# 3. RAG — RETRIEVAL AUGMENTED GENERATION

This deserves **very deep preparation**.

## 3.1 RAG architecture 🔴

```text
Documents
   ↓
Parsing
   ↓
Chunking
   ↓
Embedding
   ↓
Vector DB
   ↓
Retrieval
   ↓
Reranking
   ↓
Context construction
   ↓
LLM
   ↓
Answer
```

## 3.2 Document ingestion 🔴

* PDF parsing
* HTML
* Word documents
* Excel
* PowerPoint
* Images
* OCR
* Tables
* Metadata extraction
* Document versioning
* Incremental ingestion
* Document deletion
* Deduplication

## 3.3 Chunking 🔴

* Fixed-size chunking
* Semantic chunking
* Recursive chunking
* Parent-child chunking
* Sliding window
* Chunk overlap
* Chunk size tradeoffs
* Structure-aware chunking

## 3.4 Embeddings 🔴

* Embedding models
* Dense embeddings
* Similarity
* Cosine similarity
* Euclidean distance
* Vector dimensions
* Embedding model selection
* Embedding versioning

## 3.5 Retrieval 🔴

* Vector search
* Keyword search
* BM25
* Hybrid search
* Metadata filtering
* Semantic search
* Query expansion
* Multi-query retrieval
* Query rewriting

## 3.6 Reranking 🔴

* Cross-encoder reranking
* Relevance scoring
* Top-K retrieval vs final-K context
* Retrieval precision

## 3.7 Advanced RAG 🟠

* Parent-child retrieval
* Hierarchical retrieval
* Graph RAG
* Agentic RAG
* Corrective RAG
* Self-RAG
* Multi-hop retrieval
* Context compression
* Retrieval routing
* Multiple knowledge sources

## 3.8 RAG quality 🔴

* Retrieval recall
* Retrieval precision
* MRR
* nDCG
* Context relevance
* Faithfulness
* Groundedness
* Citation accuracy
* Answer correctness

## 3.9 RAG failure diagnosis 🔴

Know how to distinguish:

```text
Bad answer
   ↓
Bad retrieval?
   ↓
Bad context?
   ↓
Bad prompt?
   ↓
Bad model?
   ↓
Hallucination?
```

This is **very important for senior interviews**.

---

# 4. VECTOR DATABASES

### 4.1 Fundamentals 🔴

* Vector indexes
* ANN search
* Similarity search
* Metadata filtering
* Top-K
* Distance metrics

### 4.2 Indexing 🟠

* HNSW
* IVF
* PQ
* Flat search
* Recall vs performance

### 4.3 Systems 🟠

Know concepts behind:

* Pinecone
* Weaviate
* Milvus
* Qdrant
* pgvector
* Elasticsearch/OpenSearch

You don't need to memorize every product API.

---

# 5. AGENTIC AI

This is one of your **highest-priority categories**.

## 5.1 Agent fundamentals 🔴

* Agent definition
* Agent vs chatbot
* Agent vs workflow
* Agent vs RAG
* Tool calling
* Planning
* Execution
* Observation
* Iteration
* Termination

## 5.2 Agent loop 🔴

```text
Goal
 ↓
Reason / Decide
 ↓
Select tool
 ↓
Execute
 ↓
Observe result
 ↓
Decide next action
 ↓
Repeat
 ↓
Complete
```

Understand exactly what happens at every stage.

---

# 6. TOOLS / FUNCTION CALLING

### 6.1 Tool fundamentals 🔴

* Tool schemas
* Function calling
* Tool descriptions
* Arguments
* Structured output
* Tool results
* Tool errors

### 6.2 Tool architecture 🔴

* Tool registry
* Tool discovery
* Tool gateway
* Tool permissions
* Tool authentication
* Tool authorization
* Tool validation
* Tool timeout
* Tool retry
* Tool idempotency

### 6.3 Tool safety 🔴

* Least privilege
* Read vs write tools
* Sensitive tools
* Financial tools
* Delete tools
* External side effects
* Approval requirements

**Core principle:**

> LLM proposes the action. The backend decides whether that action is actually allowed.

---

# 7. AGENT RUNTIME / ORCHESTRATION

For you, this should become a **major strength**.

### 7.1 Runtime architecture 🔴

* Agent state
* Execution state
* Task state
* State transitions
* Workflow definition
* Tool execution
* Context management
* Checkpointing
* Resume
* Pause
* Cancellation

### 7.2 State machines 🔴

Understand:

```text
CREATED
   ↓
RUNNING
   ↓
WAITING_FOR_TOOL
   ↓
RUNNING
   ↓
WAITING_FOR_APPROVAL
   ↓
RUNNING
   ↓
COMPLETED
```

And:

```text
FAILED
CANCELLED
TIMEOUT
```

### 7.3 Durable execution 🔴

* Checkpoints
* Persistence
* Worker crash recovery
* Resume
* Replay
* Exactly-once vs at-least-once
* Idempotency

### 7.4 Runtime limits 🔴

* Max iterations
* Max tool calls
* Max execution time
* Token budget
* Cost budget
* Tool budget
* Context budget

---

# 8. AGENT MEMORY

### 8.1 Memory types 🔴

* Short-term memory
* Conversation memory
* Long-term memory
* Episodic memory
* Semantic memory
* Working memory

### 8.2 Memory architecture 🟠

* Memory extraction
* Memory storage
* Memory retrieval
* Memory relevance
* Memory update
* Memory deletion
* Memory expiration

### 8.3 Memory correctness 🔴

* Stale memories
* Conflicting memories
* Incorrect memories
* User preferences
* Source tracking
* Confidence
* Timestamp
* Memory authorization

Important distinction:

> Conversation history ≠ long-term memory ≠ company knowledge.

---

# 9. MULTI-AGENT SYSTEMS

### 9.1 Fundamentals 🔴

* Single agent
* Multiple agents
* Supervisor
* Manager
* Delegation
* Agent-to-agent communication

### 9.2 Architectures 🟠

* Supervisor pattern
* Hierarchical agents
* Peer-to-peer agents
* Pipeline
* Parallel agents
* Debate/critic agents
* Specialist agents

### 9.3 Tradeoffs 🔴

Know why multi-agent can introduce:

* More latency
* More tokens
* More cost
* More context passing
* More failure points
* More difficult debugging
* More complex state

### 9.4 When to use multi-agent 🔴

Use it when there is genuine:

* Domain separation
* Permission separation
* Tool separation
* Reasoning specialization
* Independent execution

Not simply:

> "Because agents are cool."

---

# 10. AGENT VS WORKFLOW

**Extremely likely interview topic.**

Know:

### Deterministic workflow

```text
A → B → C → D
```

Application decides the sequence.

### Agent

```text
A
 ↓
LLM decides
 ↓
B?
C?
D?
 ↓
observe
 ↓
decide again
```

Know when to use each.

And know the middle ground:

> **Agentic decision-making inside a deterministic workflow.**

That's often the production sweet spot.

---

# 11. HUMAN-IN-THE-LOOP

### 11.1 HITL 🔴

* Approval
* Escalation
* Review
* Human intervention
* Approval state
* Resume after approval

### 11.2 Risk-based approval 🔴

Examples:

| Action         | Automation      |
| -------------- | --------------- |
| Search docs    | Automatic       |
| Draft email    | Automatic       |
| Send email     | Conditional     |
| Refund ₹1,000  | Maybe automatic |
| Refund ₹50,000 | Human approval  |
| Delete account | Human approval  |

### 11.3 Approval architecture 🟠

* Async approval
* Persistent state
* Notification
* Approval expiry
* Approval identity
* Audit trail

---

# 12. AI SAFETY & SECURITY

**High priority.**

### 12.1 Prompt injection 🔴

* Direct injection
* Indirect injection
* Tool injection
* Retrieved-document injection
* Email injection
* Web-page injection

### 12.2 Tool security 🔴

* Authentication
* Authorization
* RBAC
* ABAC
* Least privilege
* Tool allowlists
* Tenant isolation
* Permission boundaries

### 12.3 Data security 🔴

* PII
* Secrets
* Credentials
* Data leakage
* Cross-tenant leakage
* Context isolation

### 12.4 AI-specific security 🟠

* Prompt leakage
* Model extraction
* Data exfiltration
* Unsafe tool calls
* Malicious documents
* Untrusted tool outputs

---

# 13. GUARDRAILS

### Input guardrails 🔴

* Content validation
* Prompt injection detection
* PII detection
* Intent validation

### Output guardrails 🔴

* Schema validation
* Policy validation
* Grounding validation
* Sensitive information filtering

### Tool guardrails 🔴

* Authorization
* Parameter validation
* Business rules
* Risk classification

### Important distinction

```text
LLM Guardrail
       +
Deterministic Policy
       +
Backend Authorization
```

Don't rely only on an LLM guardrail.

---

# 14. LLM EVALUATION

**One of your biggest areas to strengthen.**

### 14.1 Evaluation types 🔴

* Offline evaluation
* Online evaluation
* Regression testing
* Human evaluation
* LLM-as-judge
* Golden datasets

### 14.2 RAG evaluation 🔴

* Retrieval recall
* Precision
* MRR
* nDCG
* Context relevance
* Faithfulness
* Groundedness

### 14.3 Agent evaluation 🔴

* Task success
* Tool selection
* Tool arguments
* Number of steps
* Failure rate
* Completion rate
* Policy violations

### 14.4 Production metrics 🔴

* Latency
* Cost
* Tokens
* Success rate
* Error rate
* Escalation rate
* Tool failure rate

---

# 15. OBSERVABILITY

### 15.1 Logging 🔴

* Structured logs
* Correlation ID
* Request ID
* Run ID
* Tenant ID

### 15.2 Distributed tracing 🔴

Understand traces like:

```text
Request
 ├── Retrieval
 ├── LLM call
 │    ├── Tool decision
 │    └── Tool call
 ├── Database
 └── Final response
```

### 15.3 Metrics 🔴

* P50/P95/P99 latency
* Token usage
* Cost
* Tool failures
* Retry count
* Agent iterations
* Task success
* Hallucination rate

### 15.4 AI observability 🟠

* Prompt/version tracking
* Model version
* Retrieval results
* Tool calls
* Agent trajectory
* Evaluation scores

---

# 16. COST OPTIMIZATION

### 16.1 Token cost 🔴

* Prompt size
* Output size
* Context size
* Tool result size

### 16.2 Optimization 🔴

* Smaller models
* Model routing
* Context compression
* Caching
* Semantic caching
* Prompt optimization
* Batch processing
* Fewer agent iterations
* Fewer tool calls

### 16.3 Cost architecture 🟠

* Per-user cost
* Per-tenant cost
* Per-task cost
* Cost budgets
* Alerts
* Usage quotas

---

# 17. LATENCY OPTIMIZATION

### 17.1 Identify bottleneck 🔴

Don't say:

> "LLM is slow."

Measure:

```text
Queue wait
+ Retrieval
+ Reranking
+ LLM
+ Tool
+ DB
+ Network
```

### 17.2 Optimization 🔴

* Streaming
* Parallel tool calls
* Async execution
* Smaller model
* Caching
* Retrieval optimization
* Connection pooling
* Batching
* Reduce context
* Reduce agent iterations

---

# 18. RELIABILITY / FAILURE HANDLING

### 18.1 Failure types 🔴

* LLM timeout
* LLM outage
* Rate limit
* Invalid output
* Tool timeout
* Tool failure
* DB failure
* Queue failure
* Worker crash
* Duplicate execution

### 18.2 Recovery 🔴

* Retry
* Exponential backoff
* Jitter
* Circuit breaker
* Fallback
* Dead-letter queue
* Checkpoint
* Resume
* Human escalation

### 18.3 Retry classification 🔴

Know difference between:

```text
Transient → retry

Invalid input → don't blindly retry

Unauthorized → stop

Policy violation → stop

Timeout → bounded retry

Unknown state → investigate/reconcile
```

---

# 19. MODEL ROUTING & FALLBACK

### 19.1 Routing 🔴

Example:

```text
Simple classification → Small model

Complex reasoning → Large model

Embedding → Embedding model

Safety → Specialized model
```

### 19.2 Fallback 🔴

* Primary model → secondary model
* Provider fallback
* Tool fallback
* Retrieval fallback
* Human fallback
* Deterministic fallback

### 19.3 Fallback principles

Fallback should **fail safely**, not simply try another thing.

---

# 20. STRUCTURED OUTPUT

### Know 🔴

* JSON output
* JSON schema
* Pydantic
* Validation
* Parsing failures
* Schema enforcement
* Retry on malformed output
* Tool argument validation

---

# 21. FINE-TUNING

### 21.1 Fundamentals 🟠

* Fine-tuning
* SFT
* Instruction tuning
* LoRA
* PEFT
* QLoRA

### 21.2 Fine-tuning vs RAG 🔴

Know when to choose:

```text
Knowledge → RAG

Behavior/style → Fine-tuning

Task reasoning → Prompt/model choice

Fresh information → RAG
```

### 21.3 Evaluation 🟠

* Before/after benchmark
* Regression
* Dataset quality
* Overfitting
* Catastrophic forgetting

---

# 22. MULTIMODAL AI

### Know 🟠

* Vision-language models
* Image understanding
* OCR
* Document understanding
* Image + text
* Audio + text
* Video understanding
* Multimodal embeddings

### Production considerations

* Image size
* Tokenization
* Latency
* Cost
* OCR accuracy
* Vision hallucination

---

# 23. MCP / TOOL ECOSYSTEM

Worth knowing well.

### MCP concepts 🟠/🔴

* MCP server
* MCP client
* Tools
* Resources
* Prompts
* Tool discovery
* Tool schemas
* Permission model
* Security implications
* MCP vs traditional APIs

Especially:

> **MCP standardizes how models/agents interact with external capabilities; it doesn't replace your authorization and policy layer.**

---

# 24. AI PLATFORM ARCHITECTURE

This is **Staff-level territory**.

Understand designing:

```text
                 AI Platform
                     |
       ┌─────────────┼─────────────┐
       ↓             ↓             ↓
   Model Gateway   Agent Runtime   RAG
       ↓             ↓             ↓
    Providers       Tools       Vector DB
       ↓             ↓             ↓
    Routing        Policies     Knowledge
```

Topics:

* Model gateway
* Model routing
* Prompt management
* Agent runtime
* Tool registry
* RAG platform
* Evaluation platform
* Observability
* Cost management
* Tenant isolation
* Authentication
* Authorization

---

# 25. MULTI-TENANCY

### 🔴 Know

* Tenant isolation
* Data isolation
* Vector DB isolation
* Metadata filters
* Tenant-specific tools
* Tenant-specific policies
* Tenant-specific memory
* Rate limits
* Cost tracking
* Encryption

Question you should be ready for:

> "How do you prevent Customer A's agent from retrieving Customer B's data?"

---

# 26. DATA ARCHITECTURE

### Know 🟠

* SQL
* NoSQL
* Vector DB
* Object storage
* Cache
* Redis
* Message queues
* Event streams

### AI-specific

* Conversation storage
* Agent state
* Memory store
* Document store
* Embeddings
* Evaluation datasets
* Trace storage

---

# 27. EVENT-DRIVEN AI SYSTEMS

### 🔴

* Kafka
* Pub/Sub
* SQS-like queues
* Event-driven architecture
* Async workers
* Event deduplication
* Exactly-once vs at-least-once
* Backpressure
* DLQ
* Event replay

Very relevant for long-running agents.

---

# 28. API / BACKEND ENGINEERING FOR AI

### 🔴

* REST
* GraphQL
* WebSockets
* SSE
* Async APIs
* Streaming
* Authentication
* Authorization
* Rate limiting
* API gateways
* Connection pooling

### AI-specific

* Long-running requests
* Job APIs
* Async agent execution
* Status endpoints
* Streaming agent events

---

# 29. CONCURRENCY & DISTRIBUTED SYSTEMS

### 🔴

Especially for Staff-level interviews.

Know:

* Race conditions
* Locks
* Distributed locks
* Idempotency
* Duplicate messages
* Worker crashes
* Leader election concepts
* Event ordering
* Backpressure
* Distributed transactions
* Saga pattern
* Eventual consistency

Agent systems are distributed systems with an LLM in the loop.

That's a very useful mental model.

---

# 30. CLOUD / DEPLOYMENT

### 🟠

* Docker
* Kubernetes
* AWS/Azure/GCP
* Load balancing
* Autoscaling
* Serverless
* GPU inference
* CPU workers
* Queues
* Object storage
* Secrets management

### AI infrastructure

* GPU vs API models
* Inference servers
* vLLM
* Quantization
* Model serving
* Batching
* Autoscaling

---

# 31. OPEN-SOURCE LLM STACK

### 🟠

Know the ecosystem:

* Hugging Face
* Transformers
* PEFT
* vLLM
* Ollama
* llama.cpp
* PyTorch
* Accelerate

You don't need to be an ML researcher unless the job requires it.

---

# 32. AI AGENT FRAMEWORKS

### 🔴 Know at least one deeply

**LangGraph** — priority for you.

Understand:

* Graph
* State
* Nodes
* Edges
* Conditional edges
* Checkpointing
* Persistence
* Interrupts
* Human approval
* Streaming
* Tool execution

### 🟠 Understand conceptually

* LangChain
* AutoGen
* CrewAI
* Semantic Kernel
* OpenAI Agents-style SDKs
* LlamaIndex

Don't memorize APIs.

Understand architectural differences.

---

# 33. AI WORKFLOW PATTERNS

### 🔴

Know these patterns:

* Prompt chaining
* Routing
* Parallelization
* Orchestrator-worker
* Evaluator-optimizer
* Generator-critic
* Human-in-the-loop
* Retrieval workflow
* Tool-use loop
* Supervisor pattern

And understand when **not** to use each.

---

# 34. AI PRODUCT ENGINEERING

### 🟠

* UX for AI
* Streaming responses
* Progress indicators
* Agent status
* Human approval UI
* Error messaging
* Explainability
* Citations
* Feedback loops
* User corrections
* Conversation state

---

# 35. AI GOVERNANCE

### 🟡/🟠

Enterprise companies may ask:

* Audit trails
* Data retention
* Privacy
* Model governance
* AI policies
* Access control
* Compliance
* Human oversight
* Explainability
* Risk classification

---

# 36. RESPONSIBLE AI

### 🟡

* Bias
* Fairness
* Toxicity
* Privacy
* Safety
* Transparency
* Human oversight
* Model limitations

Know the concepts; depth depends on company.

---

# 37. AI CODING INTERVIEW

Don't ignore normal engineering.

### 🔴

* Arrays
* Strings
* Hash maps
* Trees
* Graphs
* Queues
* Stacks
* Heaps
* Sorting
* Searching
* BFS/DFS
* Complexity

But for your target roles, also prepare:

### AI/backend coding 🟠

* Async Python
* API implementation
* Retry wrapper
* Rate limiter
* Queue worker
* Streaming
* Tool registry
* Agent loop
* State machine
* Cache
* Concurrent tool execution
* Idempotency

---

# 38. PYTHON / SOFTWARE ENGINEERING

### 🔴

* OOP
* SOLID
* Design patterns
* Type hints
* Pydantic
* AsyncIO
* Concurrency
* Exception handling
* Testing
* Dependency injection
* Logging
* Packaging

### Testing

* Unit tests
* Integration tests
* Contract tests
* Mocking
* End-to-end tests
* AI evaluation tests

---

# 39. SYSTEM DESIGN

This is where you need to become **very strong**.

Practice designs like:

### 🔴

1. Enterprise AI assistant
2. Customer support agent
3. Email agent
4. Agent runtime
5. Multi-agent platform
6. RAG platform
7. Enterprise search
8. AI coding assistant
9. AI customer service platform
10. Document intelligence system
11. AI workflow automation platform
12. Model gateway
13. Evaluation platform
14. AI observability platform
15. Multi-tenant agent platform

For every design, discuss:

```text
Requirements
↓
Architecture
↓
Data flow
↓
State
↓
Scaling
↓
Security
↓
Reliability
↓
Observability
↓
Cost
↓
Tradeoffs
```

---

# 40. AI SYSTEM DESIGN TRADEOFFS

### 🔴

You should be able to discuss:

**RAG vs fine-tuning**

**Agent vs workflow**

**Single agent vs multi-agent**

**Vector DB vs search engine**

**Small model vs large model**

**Sync vs async**

**Managed model vs self-hosted**

**Framework vs custom runtime**

**Cache vs fresh retrieval**

**Automatic action vs human approval**

**Strong consistency vs eventual consistency**

This is what pushes you toward **Staff-level thinking**.

---

# 41. INTERVIEW SCENARIO / DEBUGGING QUESTIONS

### 🔴

Prepare for:

> Agent is looping forever. Diagnose.

> RAG quality dropped. Diagnose.

> Latency increased from 5 sec → 30 sec.

> LLM cost doubled.

> Tool is being called repeatedly.

> Agent sent duplicate emails.

> Agent refunded the wrong customer.

> Retrieval returns documents from another tenant.

> Model generates valid JSON but wrong tool arguments.

> Worker crashes halfway through an agent execution.

> Human approval happens but agent doesn't resume.

> Provider API goes down.

> Vector DB becomes slow.

> Agent gives an answer without evidence.

These are **excellent Senior/Staff questions**.

---

# 42. BEHAVIORAL / LEADERSHIP

For Senior/Staff roles, prepare:

### 🔴

* Architecture decision you made
* Difficult technical tradeoff
* Production incident
* Performance optimization
* Cost reduction
* Disagreement with another engineer
* Technical leadership
* Mentoring
* Cross-team architecture
* Failure
* Project rescue
* Why you chose one technology over another
* How you handle ambiguity

For Staff-level:

* Setting technical direction
* Influencing teams
* Platform thinking
* Standardization
* Long-term architecture

---

# 43. PRINCIPAL / STAFF AI TOPICS

These are the **advanced tier**.

### 🟠 → 🔴 depending on target role

* AI platform strategy
* Model abstraction layer
* Agent platform
* Model gateway
* Organization-wide AI architecture
* Cost governance
* AI security architecture
* Evaluation infrastructure
* AI observability platform
* Multi-tenancy
* Governance
* Standardized tool ecosystem
* Agent lifecycle management
* Model lifecycle management
* AI reliability engineering
* Organizational AI architecture

---

# 44. RESEARCH-LEVEL TOPICS

Only go deep if the company is research-heavy.

### 🟡

* Transformer mathematics
* Attention mathematics
* Pretraining
* RLHF
* DPO
* PPO
* GRPO
* Alignment
* Distillation
* Quantization
* MoE
* Speculative decoding
* KV cache
* Flash Attention
* Distributed training

For normal Senior GenAI application/agent roles, **don't spend months here at the expense of agents, RAG, evals, security, and system design.**

---

# Your actual priority order

If you're preparing for **AI/Agent companies**, I would rank your study like this:

### Tier 1 — MUST MASTER

1. 🔴 **LLM fundamentals**
2. 🔴 **RAG**
3. 🔴 **Tool calling**
4. 🔴 **Agents**
5. 🔴 **Agent vs workflow**
6. 🔴 **Agent runtime**
7. 🔴 **State machines**
8. 🔴 **Memory**
9. 🔴 **HITL**
10. 🔴 **Security / prompt injection**
11. 🔴 **Guardrails**
12. 🔴 **Evals**
13. 🔴 **Observability**
14. 🔴 **Latency**
15. 🔴 **Cost**
16. 🔴 **Reliability / failure handling**
17. 🔴 **System design**

### Tier 2 — STRONG KNOWLEDGE

18. 🟠 Multi-agent
19. 🟠 Model routing
20. 🟠 Fallback
21. 🟠 MCP
22. 🟠 LangGraph
23. 🟠 Fine-tuning
24. 🟠 Multimodal
25. 🟠 Event-driven architecture
26. 🟠 Distributed systems
27. 🟠 AI platform architecture
28. 🟠 Multi-tenancy
29. 🟠 Cloud/deployment
30. 🟠 Open-source models

### Tier 3 — SUPPORTING KNOWLEDGE

31. 🟡 AI governance
32. 🟡 Responsible AI
33. 🟡 Advanced vector DB internals
34. 🟡 Advanced model serving
35. 🟡 Advanced training
36. 🟡 Research papers
37. 🟡 RLHF/DPO/GRPO/etc.

---

# And here's the key for YOU

You **do not need to study these 44 categories equally**.

Your biggest upgrade path is:

```text
              YOU TODAY
                  │
                  ▼
        Strong AI application
          implementation
                  │
                  ▼
          Agent architecture
                  │
                  ▼
          Runtime + state
                  │
                  ▼
       Reliability + security
                  │
                  ▼
          Evals + observability
                  │
                  ▼
         System design/tradeoffs
                  │
                  ▼
        STAFF-LEVEL AI ENGINEER
```
