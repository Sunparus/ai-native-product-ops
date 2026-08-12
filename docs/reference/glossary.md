# Glossary

37 terms, grouped by category. Use your browser's search (or the site search bar) to jump directly to a term.

## Model & Training

| Term | Definition |
|---|---|
| **Foundation Model** | A large model pre-trained on broad data, adaptable to many downstream tasks without task-specific architecture. |
| **Fine-tuning** | Further training a pre-trained model on a narrower, task-specific dataset to specialize its behavior. |
| **LoRA** | Low-Rank Adaptation — a lightweight fine-tuning method that trains small additional weight matrices instead of the full model, cutting cost sharply. |
| **Distillation** | Training a smaller model to mimic a larger one's outputs, trading some capability for lower cost and latency. |
| **Open-weight vs. Closed Model** | Open-weight: downloadable model parameters, can self-host. Closed: accessed only via API, weights never leave the vendor. |
| **RLHF** | Reinforcement Learning from Human Feedback — a training step that aligns model outputs with human preference judgments. |
| **DPO** | Direct Preference Optimization — reformulates preference alignment as a simple classification loss, skipping RLHF's separate reward model and reinforcement-learning loop. The current default starting point for preference alignment in most open fine-tuning pipelines. |
| **Test-Time Compute / Reasoning Models** | Spending extra inference-time compute — generating and evaluating intermediate reasoning steps before answering — to trade latency for accuracy on hard problems. The current dominant trend in AI engineering; see [Test-Time Compute & Reasoning Models](../domains/ai-ml-systems-engineering/test-time-compute.md). |
| **Model Collapse** | Irreversible loss of a model's distributional diversity from training recursively on model-generated (synthetic) content across generations. |

## Inference & Serving

| Term | Definition |
|---|---|
| **Token** | The basic unit a model processes — roughly ¾ of a word in English. Pricing and context limits are measured in tokens. |
| **Context Window** | The maximum amount of text (in tokens) a model can consider at once, including prompt, retrieved data, and history. |
| **Latency** | Time between request and response. Distinguish time-to-first-token from total generation time. |
| **Quantization** | Reducing numerical precision of model weights to shrink memory footprint and speed up inference, at a small accuracy cost. |
| **Batching** | Grouping multiple inference requests to process together, improving throughput at the cost of per-request latency. |
| **Throughput** | Number of requests or tokens a system can process per unit time — the capacity metric for serving infrastructure. |
| **Continuous Batching** | Dynamically grouping requests as they arrive rather than waiting to fill a fixed batch — the current default in serving frameworks like vLLM, replacing older static batching. |
| **Speculative Decoding** | A small, fast "draft" model proposes several tokens ahead, which the larger target model verifies in parallel rather than generating token-by-token — reduces latency with no quality loss when implemented correctly. |
| **KV-Cache** | The key-value cache from attention layers, and the dominant memory cost during generation — how it's allocated, shared, and evicted is a first-class serving-infrastructure concern. |

## Data & Retrieval

| Term | Definition |
|---|---|
| **Embedding** | A numerical vector representation of text (or other data) that captures semantic meaning for similarity search. |
| **Vector Database** | A database optimized to store embeddings and perform fast similarity search over them. |
| **RAG (Retrieval-Augmented Generation)** | Retrieving relevant external data at query time and inserting it into the model's context, rather than relying solely on training data. |
| **Hybrid Search** | Combining sparse retrieval (keyword/BM25) with dense vector similarity, rather than relying on embeddings alone — catches exact-match terms pure vector search misses. |
| **Chunking** | Splitting documents into smaller segments before embedding, to fit retrieval granularity and context limits. |
| **Data Residency** | The physical/legal jurisdiction where data is stored — a compliance requirement distinct from where it is processed. |
| **Data Lineage** | The traceable record of where data originated, what transformations it underwent, and everywhere it's been consumed. Column-level lineage (precise, per-field) is what audits and incident response actually need; table-level (coarse) is what most tools ship by default. |
| **Data Sovereignty** | The principle that data is subject to the laws of the country it is collected or stored in — broader than residency, includes legal access rights. |
| **Active Metadata** | Metadata that is continuously captured and pushed back into producing and consuming tools — schema-change alerts, glossary updates, quality flags — rather than sitting in a catalog updated on a manual review cycle. |
| **Data Catalog** | A searchable inventory of an organization's data assets, combining technical metadata (schema, location) with business context (definitions, ownership, sensitivity). |
| **DCAT** | The W3C Data Catalog Vocabulary — a standardized, interoperable schema for describing datasets and catalogs across systems, reducing lock-in to any single platform's proprietary metadata format. |

## Orchestration & Agents

| Term | Definition |
|---|---|
| **Prompt Engineering** | Structuring instructions and examples given to a model to reliably shape its output. |
| **System Prompt** | A persistent instruction set applied before user input, defining the model's role, constraints, and behavior. |
| **Agent** | A system that uses a model to autonomously plan and execute multi-step actions, often invoking tools. |
| **ReAct** | The foundational agent-loop pattern (Yao et al., 2022): the model interleaves reasoning traces with actions, observes the result, and decides the next step. Most modern agent patterns are a variation on this loop. |
| **Tool Use / Function Calling** | A model's ability to invoke external functions or APIs as part of generating a response. |
| **[MCP (Model Context Protocol)](https://modelcontextprotocol.io/)** | An open protocol standardizing how models connect to external tools and data sources, aimed at reducing custom integration work. |
| **Model Router** | Logic that directs a given request to the most appropriate model based on cost, capability, or task type. |
| **Chain-of-Thought** | Prompting or training a model to expose intermediate reasoning steps before a final answer, generally improving accuracy on complex tasks. |

## Evaluation & Governance

| Term | Definition |
|---|---|
| **Hallucination** | Model output that is fluent but factually incorrect or unsupported by the given context. |
| **Eval / Benchmark** | A structured test set used to measure a model or system's performance on a defined task. |
| **Guardrails** | Rules or secondary models that constrain, filter, or validate inputs/outputs to prevent unsafe or off-policy behavior. |
| **Ground Truth** | Verified correct data used as the reference standard for evaluating model outputs. |
| **Prompt Injection** | An attack where malicious input is crafted to override a model's instructions or extract unintended behavior. |
| **Zero Data Retention** | A vendor commitment not to store or use submitted data beyond the immediate request — a common enterprise contract term. |

## Economics & Ops

| Term | Definition |
|---|---|
| **MLOps** | The discipline of deploying, monitoring, and maintaining machine learning models in production reliably. |
| **LLMOps** | MLOps specialized for large language model systems — includes prompt versioning, eval pipelines, and cost tracking. |
| **FinOps** | Financial operations discipline applied to cloud/AI spend — accountability, forecasting, and chargeback across teams. |
| **SLA** | Service Level Agreement — a contracted commitment on uptime, latency, or support response time. |
| **Vendor Lock-in** | Dependency on a single provider's proprietary APIs or formats that makes switching costly. |
| **DORA Metrics** | Four measures of engineering performance — deployment frequency, lead time for changes, change failure rate, time to recover. The standard way to know if a CI-by-design process is actually working. |
| **Circuit Breaker** | A pattern that automatically disables a failing dependency (e.g. a model or tool call) rather than letting failures cascade through the system. |
| **Blast Radius** | The scope of impact if a component fails — a core resilience design question: how much of the system does one failure actually take down? |
| **Eval Harness** | The automated infrastructure that runs a model or system against its evaluation set on a defined trigger — a code change, a schedule — rather than manually. |
| **Drift Detection** | Monitoring for a change in production data or model performance relative to the distribution the system was built or evaluated against — the mechanism that catches quiet degradation before it's visible in outcomes. |
| **Disparate Impact** | A measurably different outcome rate across groups produced by a system, even when no single input variable is explicitly discriminatory — the core thing bias testing checks for. |
| **AI Maturity Model** | A staged framework (Gartner, MIT CISR, and MITRE each publish one) rating how deeply and effectively an organization uses AI, across dimensions like strategy, governance, data, skills, and measured value — not just tool adoption. |
| **Chargeback Model** | A cost-allocation mechanism that attributes shared AI infrastructure spend back to the specific team or product consuming it, rather than treating it as a single undifferentiated line item. |
