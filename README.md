<div align="center">

# Adeolu Ogunnoiki

**AI Systems, Security & ML Engineer Who Directs Multi-Agent Workflows**

Bachelor of Computer Science with Distinction (Certificate of Specialization in Data Science) @ **Dalhousie University**<br/>
Pursuing Master of Data Science (Focus: Artificial Intelligence & Machine Learning) @ **Johns Hopkins University**

[**LinkedIn**](https://www.linkedin.com/in/adeolu-ogunnoiki) · [**F5 Labs Author Profile**](https://www.f5.com/labs/authors/adeolu-ogunnoiki)

`Python` · `Rust` · `Go` · `TypeScript`

</div>

---

I design, build and maintain software across multiple languages (Python, Rust, Go and TypeScript) by directing multiple AI agents and agent workflows, and I publish threat research on bots and automated attacks: five F5 Labs reports and articles since 2023, listed below. My latest report was picked up by F5's North America Field CISO and covered by *Dark Reading*, a top-tier cybersecurity news publication.

The repositories below are that software: ML infrastructure, AI security scanners, ranking engines and agent services. My part is choosing the problem, choosing the well-known tool to beat, and insisting that every result be checked against that tool (**PyTorch, ONNX Runtime, SciPy, FAISS, hnswlib, LightGBM, XGBoost, scikit-learn, tiktoken, Semgrep, picklescan, fickling, garak**) and reported with its losses. None of it has outside users yet, and each repository states its [evidence level](#evidence-levels). Every README opens with a **Highlights** section: what the project is, its best results and where it falls short.

---

## Published Threat Research

All published by [F5 Labs](https://www.f5.com/labs/authors/adeolu-ogunnoiki).

| Date | Publication | My role |
| --- | --- | --- |
| Nov 2026 | [*Automation leading up to Black Friday*](https://www.f5.com/labs/articles/2026-black-friday-bot-report) ([PDF](https://cdn.sanity.io/files/k6fem79d/translations-production/1d1028afb94e20d907a0b98ef084535e84fc9cd5.pdf)) | Sole author |
| Nov 2024 | [*Black Friday Versus The Bots*](https://www.f5.com/labs/articles/black-friday-versus-the-bots) | Co-author (first of four listed) |
| Nov 2023 | [*Bots Target Retailers for Black Friday Bargains*](https://www.f5.com/labs/articles/bots-target-retailers-for-black-friday-bargains) | Co-author (first of two listed) |
| Nov 2023 | [*2023 Identity Threat Report: The Unpatchables*](https://www.f5.com/labs/articles/2023-identity-threat-report-the-unpatchables) | Co-author (nine listed) |
| Nov 2023 | [*2023 Identity Threat Report: Executive Summary*](https://www.f5.com/labs/articles/2023-identity-threat-report-executive-summary) | Co-author (nine listed) |

The 2026 report covers three Black Friday seasons of retail traffic. Its two central points are that the rise in headline automation (`17.4%` to `28.6%` of transactions from 2023 to 2025) has to be separated into change among the same retailers and change in which retailers are measured, and that automation's *share* fell on Black Friday in 2023 and 2024 while its *volume* rose, because human traffic rose faster.

### Industry Coverage of the 2026 Report

Both articles discuss my F5 Labs published research report and link to it.

| Outlet | Article | Author | Date |
| --- | --- | --- | --- |
| **Dark Reading** | [*Why Holiday Security Can't Wait for Black Friday*](https://www.darkreading.com/cybersecurity-operations/why-holiday-security-cant-wait-black-friday) | Alexander Culafi, Senior News Writer | Nov 19, 2026 |
| **F5 Executive Blog** | [*The Black Friday automation trend everyone gets wrong*](https://www.f5.com/company/blog/the-black-friday-automation-trend-everyone-gets-wrong) | Sean Murphy, Field CISO (North America), F5 | Nov 19, 2026 |

---

## Start Here: Six Projects

If you look at six repositories, look at these. Each line says in plain words what the project does, its best checked result, and its main limit.

1. **[model-supply-chain-scanner](https://github.com/adeoluo/model-supply-chain-scanner)** (`Rust`) - checks an AI model file for hidden code **without loading it**. In 7,607 real Hugging Face files it caught all 17 that would run a command when loaded, including 3 that Hugging Face's own scanners did not flag. Three other scanners caught 5 to 7. *Limit:* all 17 were already known (test files or files already flagged), so it has not found a new attack, and outside reviewers got files past it three times (each one fixed and published).
2. **[ml-graph-compiler](https://github.com/adeoluo/ml-graph-compiler)** (`Python`, `C`) - turns a trained AI model into fast code for one machine. It gives the same top answer as ONNX Runtime on all 3,925 test photos, and runs `1.23x` to `1.37x` faster than it on three of four models when using 8 cores. *Limit:* ONNX Runtime is faster with 1 or 4 cores, and all timings are from one M1 laptop.
3. **[lambdamart-ranking-engine](https://github.com/adeoluo/lambdamart-ranking-engine)** (`Rust`, `Python`) - a search ranking engine built from scratch. It ties LightGBM on Microsoft's public search dataset (`0.5029` against `0.5042`, not a real gap) and has the top score of three libraries on a second dataset (`0.7603`). *Limit:* LightGBM trains about twice as fast, and XGBoost scores slightly higher on the Microsoft data (`0.5061`).
4. **[mcp-security-scanner](https://github.com/adeoluo/mcp-security-scanner)** (`Go`) - finds security holes in the tool servers that AI assistants plug into. It found every planted command-injection, path-traversal and SSRF bug in 432 test servers, where Semgrep found 59%, 0% and 11%, and it ran over 1,013 public repositories. *Limit:* the test servers are self-authored, and on real code its SSRF alerts were right `2/9` times and its tool-poisoning text alerts `0/29`.
5. **[prompt-optimizer](https://github.com/adeoluo/prompt-optimizer)** (`Python`) - rewrites prompts automatically with seven published methods and checks which ones truly help. The best one lifts a small local model from `64.7%` to `75.0%` on GSM8K math problems. *Limit:* one optimization seed, and nothing improves BIG-Bench Hard.
6. **[agent-platform](https://github.com/adeoluo/agent-platform)** (`Python`, `TypeScript`) - a service that runs AI agent jobs for many customers and survives crashes: a worker killed mid-job re-runs zero finished steps. *Limit:* tested against a scripted stand-in model, never a live LLM workload.

<details>
<summary><b>Full results and limits for nine systems, with live CI</b></summary>

<br/>

Every row pairs live CI and raw evaluation reports with both where the implementation wins and where reference baselines, public corpora or distribution shifts expose its limits. *(Local benchmarks ran on one 8-core Apple M1: 4 performance + 4 efficiency cores, 8 GB RAM, shared with other work.)*

| System & Live CI | Stack | What It Is | Verified Results & Unflattering Boundaries |
| --- | --- | --- | --- |
| **[model-supply-chain-scanner](https://github.com/adeoluo/model-supply-chain-scanner)**<br/>[![CI](https://github.com/adeoluo/model-supply-chain-scanner/actions/workflows/ci.yml/badge.svg)](https://github.com/adeoluo/model-supply-chain-scanner/actions/workflows/ci.yml)<br/><sub>[eval report](https://github.com/adeoluo/model-supply-chain-scanner/blob/main/docs/EVALUATION_REPORT.md)</sub> | `Rust` · `Python` | Pre-deserialization symbolic pickle VM and static scanner across `pickle`, PyTorch, `joblib`, NumPy, Keras, SavedModel, ONNX, GGUF, and `safetensors` + SARIF | Scanned **7,607 public Hugging Face Hub files across 2,888 repos** in `9.8s` with `31/7,563` non-attack high alerts (the Hub files have no independent ground truth, so this measures alert rate, not recall). On the author-written 194-file corpus it flags `116/116` malicious and `0/78` benign files vs `picklescan` `69/116` and `fickling` `73/116` (`31/78` benign flagged); the gap is mostly formats the others do not read, and the score is a regression gate, not a recall estimate. *What outside reviewers broke:* three rounds of probes found bypasses (`torch.utils.collect_env.run`, a truncated protocol 0 pickle, a pickled Keras `Lambda`, transformers' dynamic module loader), all fixed and [listed with causes](https://github.com/adeoluo/model-supply-chain-scanner#bypasses-found-by-outside-reviewers). A code-running function in a trusted library that is neither cataloged nor named like a loader still passes. |
| **[ml-graph-compiler](https://github.com/adeoluo/ml-graph-compiler)**<br/>[![CI](https://github.com/adeoluo/ml-graph-compiler/actions/workflows/ci.yml/badge.svg)](https://github.com/adeoluo/ml-graph-compiler/actions/workflows/ci.yml)<br/><sub>[eval report](https://github.com/adeoluo/ml-graph-compiler/blob/main/docs/EVALUATION_REPORT.md)</sub> | `Python` · `C` | ONNX-to-SSA graph compiler: fusion & NHWC layout passes, static arena planner (`113.6 -> 3.0 MB` on GPT-2), clang NEON + OpenMP C codegen (`679` LOC in `mgc_kernels.c` + `213` LOC in `mgc_runtime.h`), `mlir-opt`-verified MLIR export | **100% Top-1 parity** with `onnxruntime` (3,925 Imagenette images; 6,400 BERT/GPT-2 token positions). At **8 threads** across the 4P+4E M1 cores (load avg `3.0-8.2`), OpenMP dynamic tile scheduling beats `onnxruntime` CPU by **1.23x - 1.37x** on ResNet-50 (`29.8 vs 40.9 ms`), BERT-base (`72.0 vs 88.8 ms`), and GPT-2 (`109.7 vs 149.4 ms`), and ties MobileNetV2 (`6.0 ms`). *Where it loses:* at **1 thread** (`1.12x - 1.16x`) and **4 P-core threads** (`1.05x - 1.38x`), `onnxruntime` MLAS wins on all 4 models, and PyTorch Apple Accelerate AMX leads on transformers (`1.20x - 1.32x` at 8t; `4.27x - 5.56x` at 1t). |
| **[lambdamart-ranking-engine](https://github.com/adeoluo/lambdamart-ranking-engine)**<br/>[![CI](https://github.com/adeoluo/lambdamart-ranking-engine/actions/workflows/ci.yml/badge.svg)](https://github.com/adeoluo/lambdamart-ranking-engine/actions/workflows/ci.yml)<br/><sub>[eval report](https://github.com/adeoluo/lambdamart-ranking-engine/blob/main/docs/EVALUATION_REPORT.md)</sub> | `Rust` · `Python` | LambdaMART search ranking engine with a Rust histogram tree core, neural rankers, click models, and counterfactual IPW | **0.5029 NDCG@10** over 5 folds of **MSLR-WEB10K** (1.2M docs, 10k queries) - `0.0013` below **LightGBM `0.5042`** (not significant, paired `p = 0.103`) vs **XGBoost `0.5061`**; on **Istella-S** (3.4M pairs), scores **0.7603 NDCG@10** vs LightGBM `0.7595` and XGBoost `0.7554`. *Training speed (500 trees, MSLR):* **LightGBM is fastest at `39.7s`**, ahead of this package (`68.1s`) and XGBoost (`81.5s`). |
| **[mcp-security-scanner](https://github.com/adeoluo/mcp-security-scanner)**<br/>[![CI](https://github.com/adeoluo/mcp-security-scanner/actions/workflows/ci.yml/badge.svg)](https://github.com/adeoluo/mcp-security-scanner/actions/workflows/ci.yml)<br/><sub>[eval report](https://github.com/adeoluo/mcp-security-scanner/blob/main/docs/EVALUATION_REPORT.md)</sub> | `Go` | Static taint analyzer and live protocol prober for Model Context Protocol servers (tool poisoning, injection, traversal, rug-pulls) + SARIF | On 432 author-planted and safe look-alike servers: **0.968 recall at 8.5% FPR** (`1.00 / 0.02` on standard taint tiers vs Semgrep OSS `0.59` injection / `0.00` traversal, but **`0/4` hard command injections** and `0/60` paraphrased poisoning). Across **1,013 public MCP repos** (12.2M LOC), precision on a sample audited by an AI agent against a written rubric is **`0.80 - 1.00`** on CORS/TLS/bind/OAuth, **`0.92` correct / `0.08` actionable** on path traversal, `11/22` on secrets, and **weak on `2/7` command injection, `2/9` SSRF, and `0/29` tool-poisoning text** (no sampled poisoning finding was a real attack). Every finding now carries its rule's audited precision, and high-severity poisoning alarms on that corpus fell from 25 to 15 after three audited false-positive patterns were removed. |
| **[prompt-optimizer](https://github.com/adeoluo/prompt-optimizer)**<br/>[![CI](https://github.com/adeoluo/prompt-optimizer/actions/workflows/ci.yml/badge.svg)](https://github.com/adeoluo/prompt-optimizer/actions/workflows/ci.yml)<br/><sub>[README results](https://github.com/adeoluo/prompt-optimizer#results)</sub> | `Python` | Seven prompt optimizers (MIPROv2, TextGrad, GEPA, OPRO, APE, PromptBreeder, bootstrap) behind one budget contract, on local `Qwen3.5` models, compared with DSPy 3.4.1 | On GSM8K with Qwen3.5-2B, TextGrad-style search lifts test accuracy from `64.7%` to **`75.0%`** (`+10.3` points, CI `4.7` to `16.0`) within 400 task rollouts. *Limits:* no method improves BIG-Bench Hard, the MIPROv2-style optimizer tests below the seed prompt despite tying on validation, and everything rests on one optimization seed. |
| **[agent-platform](https://github.com/adeoluo/agent-platform)**<br/>[![CI](https://github.com/adeoluo/agent-platform/actions/workflows/ci.yml/badge.svg)](https://github.com/adeoluo/agent-platform/actions/workflows/ci.yml)<br/><sub>[benchmarks](https://github.com/adeoluo/agent-platform/tree/main/benchmarks)</sub> | `Python` · `TypeScript` | Multi-tenant service composing safety gateway, OpenAI/Anthropic failover, lexical RAG, stdio MCP server, memory, and fenced SQLite job leases | HMAC-peppered API keys (with non-loopback `AGENT_PLATFORM_KEY_PEPPER` enforcement), strict tenant isolation, and **0 checkpointed steps re-run** under `SIGKILL` worker crashes (at-least-once execution on the interrupted step). *Boundary:* the **516 req/s** cached / **244 req/s** uncached loopback figures (`p99` `48 ms` / `142 ms` across 20 tenants) run against the deterministic offline policy model and hashed-feature vectors (`uv sync` installs all dependencies automatically) to measure SQLite lease and gateway overhead, not live LLM quality. |
| **[vectordb-go](https://github.com/adeoluo/vectordb-go)**<br/>[![CI](https://github.com/adeoluo/vectordb-go/actions/workflows/ci.yml/badge.svg)](https://github.com/adeoluo/vectordb-go/actions/workflows/ci.yml)<br/><sub>[raw results](https://github.com/adeoluo/vectordb-go/tree/main/benchmarks/results)</sub> | `Go` | Standalone concurrent, persistent HNSW vector database server with group-commit checksummed WAL, directory fsyncs, torn-tail truncation, and HTTP API | Race-clean and crash-tested WAL recovery across torn tails and concurrent writers; on **1,000,000 SIFT vectors**, custom ARM64 NEON assembly distance kernels (76 LOC asm) answer **1.3x - 2.0x faster than `hnswlib`** at matched recall for `ef` 32 to 256 (a 3.5x reading at `ef` 16 is discounted as noise). *Boundary:* this holds on ARM64 only, where `hnswlib` has no hand-written NEON SIMD and compiles to scalar C++; on x86 with AVX expect `hnswlib` to win. |
| **[prompt-injection-detector](https://github.com/adeoluo/prompt-injection-detector)**<br/>[![CI](https://github.com/adeoluo/prompt-injection-detector/actions/workflows/ci.yml/badge.svg)](https://github.com/adeoluo/prompt-injection-detector/actions/workflows/ci.yml)<br/><sub>[eval report](https://github.com/adeoluo/prompt-injection-detector/blob/main/docs/EVALUATION_REPORT.md)</sub> | `Rust` · `Python` | Prompt-injection classifier: **27 us** Rust hashed n-gram FTRL core (`17x` faster than `scikit-learn` at `464 us`) + fine-tuned `e5-small` | MinHash-deduplicated split across 13 public datasets (91,089 test prompts): **0.9996 in-distribution AUROC** (`99.5%` TPR at `1%` FPR), which a stock `scikit-learn` hashing+SGD baseline matches (`0.9995`), so the score reflects source style more than modeling. *Limits:* on held-out attack families TPR drops to **`45.3%` (Lakera), `42.1%` (SPML), `22.6%` (deepset)**; leetspeak defeats n-grams (`0.6%`); and **a short injection planted in a 16,000-character benign document is detected `1.65%` of the time** (`0%` before windowed scoring was added). It is a prompt screen, not an indirect-injection detector. |
| **[corpus-dedup-library](https://github.com/adeoluo/corpus-dedup-library)** · **[bpe-tokenizer-library](https://github.com/adeoluo/bpe-tokenizer-library)**<br/>[![CI](https://github.com/adeoluo/corpus-dedup-library/actions/workflows/ci.yml/badge.svg)](https://github.com/adeoluo/corpus-dedup-library/actions/workflows/ci.yml)<br/><sub>[dedup report](https://github.com/adeoluo/corpus-dedup-library/blob/main/docs/EVALUATION_REPORT.md) · [BPE report](https://github.com/adeoluo/bpe-tokenizer-library/blob/main/docs/EVALUATION_REPORT.md)</sub> | `Rust (PyO3)` · `Python` | Bit-exact MinHash/LSH deduplicator and lossless GPT-2 byte-level BPE tokenizer matching Python references token-for-token | `corpus-dedup-library` streams **1.4M C4 docs in 30s** (and runs **13.7x faster** than Python `datasketch` on a 50k-doc head-to-head slice); `bpe-tokenizer-library` trains a 50,257-token vocab on 100 MB C4 in **6.7s** and Rayon batch-encodes at **68.5 vs 52.4 MB/s** vs `tiktoken` (*Boundary:* single-string latency favors `tiktoken`). |

</details>

---

## Evidence Levels

Every README states one of these, so a repository checked against thousands of real images is not mistaken for one checked against a toy fixture because both have an evaluation report.

| Level | Meaning | Repositories |
| --- | --- | --- |
| **Unit tested** | Behaviour is covered by tests the author wrote. | `agent-sandbox`, `agent-platform`, `llm-gateway`, `llm-observability`, `rlhf-reward-model` |
| **Reference validated** | Outputs are checked against an established implementation, on small or synthetic inputs. | `transformer-from-scratch` (PyTorch), `evaluation-harness` (SciPy), `bot-traffic-econometrics` (SciPy), `llm-vuln-scanner` (garak) |
| **Publicly benchmarked** | Measured on public datasets or head-to-head with established tools, with raw results committed. | `ml-graph-compiler`, `vectordb-go`, `lambdamart-ranking-engine`, `prompt-injection-detector`, `corpus-dedup-library`, `bpe-tokenizer-library`, `ann-vector-search-library`, `hybrid-rag`, `ad-auction-lab`, `prompt-optimizer`; with self-authored corpora: `model-supply-chain-scanner`, `mcp-security-scanner` |
| **Independently reproduced** | Someone else has rerun the results. | None yet |
| **Production observed** | Running for real users. | None |

All benchmarks were run by me on one laptop. The two scanners are graded partly on corpora I wrote, and the MCP scanner's precision audit was labeled by an AI agent against a written rubric, not by a human reviewer.

---

## Complete Open-Source Stack & Architectural Boundaries (21 Repositories)

<p align="center">
  <img src="assets/portfolio-architecture.svg" alt="End-to-End AI Infrastructure, Security and Threat Econometrics Stack" width="100%">
</p>

<table>
<tr>
<td width="50%" valign="top">

### 1. Data, Pedagogical Internals & Post-Training
- **[corpus-dedup-library](https://github.com/adeoluo/corpus-dedup-library)** (`Rust` · `Python`) - MinHash/LSH near-deduplication and quality filtering at C4 scale.
- **[bpe-tokenizer-library](https://github.com/adeoluo/bpe-tokenizer-library)** (`Rust` · `Python`) - Lossless GPT-2 byte-level BPE with PyO3 bindings and parallel batch encoding.
- **[prompt-optimizer](https://github.com/adeoluo/prompt-optimizer)** (`Python`) - Seven optimizers (MIPROv2, TextGrad, GEPA, OPRO, APE, PromptBreeder, bootstrap) benchmarked on real local `Qwen3.5` models across GSM8K & BBH vs DSPy 3.4.1.
- **[transformer-from-scratch](https://github.com/adeoluo/transformer-from-scratch)** (`Python`) - *Pedagogical white-box library:* minimal 2-D NumPy reverse-mode autodiff + tiny decoder transformer (copy task + 1,718-char prose slice), with forward logits and all 48 backward gradients verified `< 1e-9` vs PyTorch in CI + 8-seed induction ablation (null result).
- **[rlhf-reward-model](https://github.com/adeoluo/rlhf-reward-model)** (`Python`) - *Controlled synthetic study:* Bradley-Terry reward modeling, PPO vs DPO alignment, and Goodhart over-optimization on a 12-feature synthetic bandit (NumPy gradient parity in CI; no LLM weights).

</td>
<td width="50%" valign="top">

### 2. Compilers, Search & Applied ML
- **[ml-graph-compiler](https://github.com/adeoluo/ml-graph-compiler)** (`Python` · `C`) - ONNX-to-SSA compiler with fusion passes, static arena planning, clang NEON/OpenMP C codegen, and `mlir-opt`-verified MLIR export.
- **[vectordb-go](https://github.com/adeoluo/vectordb-go)** (`Go`) - *Standalone networked server:* concurrent HNSW database with group-commit WAL, fsync crash recovery, and HTTP API.
- **[ann-vector-search-library](https://github.com/adeoluo/ann-vector-search-library)** (`Rust SIMD` · `Python`) - *In-process embeddable library:* PyO3 HNSW index linked directly inside Python retrieval pipelines (`hybrid-rag`, `agent-platform`).
- **[hybrid-rag](https://github.com/adeoluo/hybrid-rag)** (`Python`) - *Lexical retrieval, no embeddings:* inverted-index BM25, TF-IDF, RRF, and reranking (`0.687 nDCG@10` for stemmed BM25 vs `0.665` hybrid fusion on BEIR SciFact; `0.666` hybrid vs `0.663` BM25 on 171k-doc TREC-COVID).
- **[lambdamart-ranking-engine](https://github.com/adeoluo/lambdamart-ranking-engine)** (`Rust` · `Python`) - Histogram LambdaMART, neural rankers, and counterfactual IPW ranking on MSLR-WEB10K (1.2M docs) & Istella-S (3.4M pairs).
- **[ad-auction-lab](https://github.com/adeoluo/ad-auction-lab)** (`Rust` · `Python`) - GSP/VCG/first-price auctions, bid shading, budget pacing, hashed Criteo CTR, and Open Bandit off-policy evaluation.

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 3. AI Security, Sandboxing & Threat Econometrics
- **[bot-traffic-econometrics](https://github.com/adeoluo/bot-traffic-econometrics)** (`Rust` · `Python`) - *Methods library, synthetic examples only:* unbalanced-panel rate decomposition, Shapley surge attribution, Manski bounds under censoring, `O(N*D)` Hawkes MLE (checked against `SciPy`), and an uncalibrated Stackelberg channel game. A companion to my [2026 F5 Labs report](https://www.f5.com/labs/articles/2026-black-friday-bot-report), not its analysis or data.
- **[model-supply-chain-scanner](https://github.com/adeoluo/model-supply-chain-scanner)** (`Rust` · `Python`) - *Static pre-load check:* symbolic pickle VM + 8 model serialization formats inspected before weights touch memory; run over 7,607 Hugging Face Hub files.
- **[mcp-security-scanner](https://github.com/adeoluo/mcp-security-scanner)** (`Go`) - *Protocol & source audit:* taint analysis, rug-pull hash pinning, and live probing evaluated on 432 planted cases + 1,013 public MCP repos (precision per rule from a sample audited by an AI agent against a written rubric).
- **[prompt-injection-detector](https://github.com/adeoluo/prompt-injection-detector)** (`Rust` · `Python`) - *Prompt screening:* `27 us` Rust n-gram FTRL scorer + fine-tuned transformer with leave-one-family-out, adversarial rewrite and long-document evaluations.
- **[llm-vuln-scanner](https://github.com/adeoluo/llm-vuln-scanner)** (`Python` · `Rust`) - *Live model red-teaming:* 540-probe campaigns across local `Qwen3.5`, `Gemma 4`, and `Granite 4.2` mapped to OWASP LLM/Agentic 2026 & MITRE ATLAS vs `garak`.
- **[agent-sandbox](https://github.com/adeoluo/agent-sandbox)** (`Rust`) - *Runtime containment:* declarative policy engine + OS isolation (`Seatbelt` on macOS, `Landlock` on Linux) and hash-chained audit logs. As root, where the kernel ignores `RLIMIT_NPROC`, the process limit comes from a `pids.max` cgroup or a seccomp fork gate, or the command is refused; CI runs the suite as root in a container for each case. No external security audit.

</td>
<td width="50%" valign="top">

### 4. Serving, Multi-Tenant Agents & Telemetry
- **[agent-platform](https://github.com/adeoluo/agent-platform)** (`Python` · `TypeScript`) - *Integrated multi-tenant product:* composes `llm-gateway`, `hybrid-rag` (lexical retrieval), `ann-vector-search-library`, `evaluation-harness`, and `llm-observability` behind hashed API keys, MCP, and fenced SQLite job leases.
- **[llm-gateway](https://github.com/adeoluo/llm-gateway)** (`Python` · `Go`) - *Reliability and policy proxy:* Python gateway + parity-tested Go reverse proxy for OpenAI/Anthropic failover and per-tenant quotas, with rule-based injection screening (10 patterns, a heuristic and not a security boundary, with an ML scorer hook), Luhn-checked PII redaction, and a lexical response cache.
- **[evaluation-harness](https://github.com/adeoluo/evaluation-harness)** (`Python`) - *Standalone statistical grader:* paired bootstrap CIs, exact McNemar, and Cohen's d (`< 1e-15` vs `SciPy` on Cohen's d & McNemar; `0.0014` Monte Carlo diff on 1,000-draw bootstrap CIs), plus n-gram contamination checks.
- **[llm-observability](https://github.com/adeoluo/llm-observability)** (`Python` · `TypeScript`) - *Standalone telemetry stack:* zero-dependency Python span tracer, collector API, cost/SLO engine, and TypeScript trace UI.

</td>
</tr>
</table>
