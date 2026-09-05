# Roadmap

Foundry is developed incrementally from low-level AI primitives toward
production-oriented AI systems.

The roadmap is intentionally milestone-driven rather than feature-driven.
Each phase should produce a working artifact, measurable results, and
documented engineering decisions.

---

## Phase 1 — High-Performance Tokenization
**Target: Q4 2026**

Build a BPE training and inference engine from first principles.

### Goals

- Understand BPE deeply through implementation.
- Explore memory-efficient corpus processing.
- Explore parallel frequency counting.
- Build deterministic vocabulary synthesis.
- Establish Foundry's Rust/Python architecture and engineering practices.

### Deliverables

- [ ] `bpe_core` Rust crate
- [ ] `bpe_python` Python bindings
- [ ] `bpe_cli` standalone CLI
- [ ] Memory-mapped corpus reader
- [ ] Parallel pre-tokenization and frequency aggregation
- [ ] BPE mutation engine
- [ ] Deterministic vocabulary generation
- [ ] Encoder / decoder
- [ ] Checkpoint and recovery support
- [ ] Differential correctness tests
- [ ] Benchmark suite
- [ ] Benchmark report

### Success Criteria

- Deterministic output for identical input.
- Correctness validated against a reference implementation.
- No broken arena links after mutation.
- Large corpora can be processed without loading the entire corpus
  into memory.
- Performance and memory characteristics are measured rather than
  assumed.

### Engineering Topics

- Rust ownership and borrowing
- Memory mapping
- Cache locality
- Parallel MapReduce
- Arena allocation
- Binary heaps
- Inverted indexes
- Deterministic algorithms
- FFI with PyO3

---

## Phase 2 — Embeddings and Semantic Search
**Target: Q1 2027**

Extend Foundry from token-level processing to semantic representations.

### Goals

- Understand what embeddings represent.
- Understand the relationship between tokenization, models, and embeddings.
- Build a reproducible embedding and similarity-search pipeline.
- Understand approximate nearest-neighbor search.

### Deliverables

- [ ] Embedding generation pipeline
- [ ] Dataset ingestion pipeline
- [ ] Vector representation and storage layer
- [ ] Cosine / dot-product similarity
- [ ] Exact nearest-neighbor baseline
- [ ] ANN search implementation or integration
- [ ] HNSW-based index
- [ ] Search benchmark suite
- [ ] Recall@K evaluation
- [ ] Latency / throughput / memory benchmarks

### Success Criteria

- Establish an exact-search baseline.
- Quantify the accuracy/performance trade-off of ANN search.
- Reproduce benchmark results from a documented dataset.
- Explain the trade-offs between different vector-search approaches.

### Engineering Topics

- Embeddings
- Similarity metrics
- ANN search
- HNSW
- Index construction
- Recall@K
- Latency/throughput trade-offs
- Vector memory layout

---

## Phase 3 — Retrieval-Augmented Generation
**Target: Q2 2027**

Build a complete retrieval pipeline around an LLM.

### Goals

- Understand RAG as a system rather than a framework abstraction.
- Study document ingestion, chunking, retrieval, ranking, and generation.
- Build an evaluation-driven RAG pipeline.

### Deliverables

- [ ] Document ingestion pipeline
- [ ] Multiple chunking strategies
- [ ] Embedding-based retrieval
- [ ] Metadata filtering
- [ ] Hybrid retrieval
- [ ] Reranking
- [ ] Prompt construction
- [ ] Streaming LLM responses
- [ ] Retrieval evaluation framework
- [ ] End-to-end RAG evaluation
- [ ] Latency and token-cost instrumentation

### Success Criteria

- Retrieval quality can be measured independently from generation quality.
- Different chunking and retrieval strategies can be compared
  quantitatively.
- End-to-end latency and token usage are observable.
- The system can reproduce evaluation results.

### Engineering Topics

- RAG
- Chunking
- Retrieval
- Reranking
- Prompt construction
- LLM APIs
- Evaluation
- Latency
- Token economics

---

## Phase 4 — Agent Runtime
**Target: Q3 2027**

Move from fixed pipelines to systems capable of planning and using tools.

### Goals

- Understand the engineering challenges behind agentic systems.
- Build core agent abstractions rather than relying entirely on
  an existing framework.
- Study state, tool execution, retries, and failure handling.

### Deliverables

- [ ] Tool abstraction
- [ ] Structured tool calling
- [ ] Agent state model
- [ ] Execution loop
- [ ] Tool selection
- [ ] Retry / timeout handling
- [ ] Persistent execution state
- [ ] Human-in-the-loop support
- [ ] Agent tracing
- [ ] Agent evaluation suite

### Success Criteria

- Agent execution is reproducible and observable.
- Tool failures and LLM failures can be handled independently.
- Agent behavior can be evaluated against defined tasks.
- The runtime has clear boundaries between model reasoning,
  orchestration, and tool execution.

### Engineering Topics

- Tool calling
- Agent state
- Workflow orchestration
- Reliability
- Idempotency
- Retries
- Timeouts
- Distributed execution
- Agent evaluation

---

## Phase 5 — AI Security
**Target: Q3–Q4 2027**

Apply the AI systems developed by Foundry to a domain where
existing engineering experience provides a strong advantage.

### Goals

Build an AI-assisted security analysis system that combines
traditional program analysis with LLM-based reasoning.

### Initial Concept

APK

↓

Static analysis

↓

Security findings

↓

Knowledge retrieval

↓

LLM reasoning

↓

Threat explanation

↓

Suggested mitigation

↓

Security report

### Deliverables

- [ ] APK ingestion
- [ ] Android manifest analysis
- [ ] Static analysis integration
- [ ] Security finding representation
- [ ] Security knowledge base
- [ ] RAG over security documentation
- [ ] LLM-assisted analysis
- [ ] Tool-using security agent
- [ ] Structured security reports
- [ ] Evaluation dataset
- [ ] False-positive / false-negative analysis

### Success Criteria

- Traditional static analysis and LLM reasoning have clearly
  separated responsibilities.
- Security findings are traceable to their underlying evidence.
- The system's accuracy can be evaluated against a known dataset.
- AI-generated conclusions are distinguishable from deterministic
  analysis results.

### Engineering Topics

- AI-assisted security analysis
- Program analysis
- Android security
- RAG
- Agents
- Evidence-based generation
- AI evaluation
- Security/reliability trade-offs

---

## Phase 6 — Production AI Systems
**Target: Q4 2027**

Turn the experimental components into a coherent production-oriented
system.

### Goals

- Apply production engineering principles to AI workloads.
- Understand observability, reliability, scalability, and cost.
- Establish Foundry as an end-to-end AI systems laboratory.

### Deliverables

- [ ] Unified Foundry architecture
- [ ] Dockerized services
- [ ] CI/CD pipeline
- [ ] Distributed workload support where justified
- [ ] Metrics
- [ ] Distributed tracing
- [ ] Structured logging
- [ ] Load testing
- [ ] Failure injection
- [ ] AI evaluation pipeline
- [ ] Regression testing
- [ ] Resource/cost monitoring
- [ ] Production architecture documentation

### Success Criteria

- Every major subsystem has measurable performance characteristics.
- AI quality and system performance can be evaluated independently.
- Failures are observable and diagnosable.
- The system can be deployed reproducibly.
- Major architectural decisions are documented.

### Engineering Topics

- AI infrastructure
- Observability
- Distributed systems
- Reliability
- Load testing
- Cost optimization
- Evaluation
- Deployment