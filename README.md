<div align="center">

# Adeolu Ogunnoiki

**AI Systems, Security and Machine Learning Engineer Who Directs Multi-Agent Workflows**

Bachelor of Computer Science with Distinction (Certificate of Specialization in Data Science), **Dalhousie University**<br/>
Master of Data Science in progress (Focus: Artificial Intelligence and Machine Learning), **Johns Hopkins University**

[**LinkedIn**](https://www.linkedin.com/in/adeolu-ogunnoiki) · [**F5 Labs Author Profile**](https://www.f5.com/labs/authors/adeolu-ogunnoiki)

`Python` · `Rust` · `Go` · `TypeScript`

</div>

---

I design, build and maintain software in four programming languages: Python, Rust, Go and
TypeScript. I do this by directing several AI coding agents and the workflows that connect
them. I also publish threat research on bots (automated programs that act on websites) and on
automated attacks: five F5 Labs reports and articles since 2023, listed below. My latest
report was picked up by F5's North America Field Chief Information Security Officer (CISO) and
covered by *Dark Reading*, a top-tier cybersecurity news publication.

The repositories below are that software. They cover machine learning (ML) infrastructure,
security scanners for AI systems, search ranking engines and services that run AI agents. My
part is to choose the problem, choose the established tool to compare against, and require that
every result is checked against that tool and reported together with its losses. The comparison
tools include PyTorch, ONNX Runtime, SciPy, FAISS, hnswlib, LightGBM, XGBoost, scikit-learn,
tiktoken, Semgrep, picklescan, fickling and garak; each is described under
[Key terms](#key-terms).

None of these projects has outside users yet. Each repository states its
[evidence level](#evidence-levels), which says how strongly its results have been checked.
Every repository README opens with two sections: **Highlights** (what the project is, its best
checked results and where it falls short) and **Key terms** (plain definitions).

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

The 2026 report covers three Black Friday seasons of retail web traffic and makes two central
points. First, the reported rise in automated traffic, from `17.4%` to `28.6%` of transactions
between 2023 and 2025, has two different causes that must be separated: change within the same
retailers, and change in which retailers are measured. Second, on Black Friday in 2023 and 2024
the *share* of automated traffic fell while its *volume* rose, because human traffic grew
faster.

### Industry Coverage of the 2026 Report

Both articles discuss my F5 Labs published research report and link to it.

| Outlet | Article | Author | Date |
| --- | --- | --- | --- |
| **Dark Reading** | [*Why Holiday Security Can't Wait for Black Friday*](https://www.darkreading.com/cybersecurity-operations/why-holiday-security-cant-wait-black-friday) | Alexander Culafi, Senior News Writer | Nov 19, 2026 |
| **F5 Executive Blog** | [*The Black Friday automation trend everyone gets wrong*](https://www.f5.com/company/blog/the-black-friday-automation-trend-everyone-gets-wrong) | Sean Murphy, Field CISO (North America), F5 | Nov 19, 2026 |

---

## Start Here: Six Projects

These six repositories show the work best. Each entry says what the project does, its best
checked result and its main limit.

1. **[model-supply-chain-scanner](https://github.com/adeoluo/model-supply-chain-scanner)** (`Rust`) - checks an AI
   model file for hidden code **without loading it**. A model file can contain code that runs
   the moment the file is opened. Four other scanner projects publish 181 test files: 144
   dangerous and 37 safe. This scanner catches 141 of the 144 dangerous files and raises no
   false alarm on the safe ones. The next best tool, ModelAudit, catches 139 with 4 false
   alarms. In 12,573 real files from Hugging Face (the largest public site for sharing AI
   models), it flagged all 24 files that would run a command or read a file outside the model
   when loaded. Hugging Face's own scanners did not flag 6 of the 24.
   *Limits:* all 24 files were already known as test files or flagged files, so the scanner has
   not found a new attack. Its lead over ModelAudit is two files. On a new sample it had never
   seen, it raised 14 false alarms where picklescan raised 3. Each cause was fixed and published.
2. **[ml-graph-compiler](https://github.com/adeoluo/ml-graph-compiler)** (`Python`, `C`) - turns a trained AI
   model into fast code for one computer. It gives the same top prediction as ONNX Runtime
   (Microsoft's standard engine for running models) on all 3,925 test photos. With 8 processor
   cores, it runs 1.23 to 1.37 times faster than ONNX Runtime on three of four models.
   *Limits:* ONNX Runtime is faster with 1 or 4 cores, and all timings come from one Apple M1
   laptop.
3. **[lambdamart-ranking-engine](https://github.com/adeoluo/lambdamart-ranking-engine)** (`Rust`, `Python`) - a
   search ranking engine built from scratch: it learns to put the most relevant documents
   first. On Microsoft's public web-search dataset, its ranking score is `0.5029` against
   `0.5042` for LightGBM, and that difference is not statistically significant. On a second
   dataset it has the top score of three libraries (`0.7603`). The score is NDCG at 10, which
   rates the order of the top 10 results from 0 to 1 (higher is better).
   *Limits:* LightGBM trains about 1.7 times as fast (39.7 against 68.1 seconds), and XGBoost
   scores slightly higher on the Microsoft data (`0.5061`).
4. **[mcp-security-scanner](https://github.com/adeoluo/mcp-security-scanner)** (`Go`) - finds security flaws in
   the tool servers that AI assistants connect to through the Model Context Protocol (MCP). In
   432 test servers it found every planted flaw of three kinds: command injection (running an
   attacker's commands), path traversal (reading files outside an allowed folder) and
   server-side request forgery (SSRF: making the server fetch an address the attacker chose).
   Semgrep, a widely used code scanner, found 59%, 0% and 11% of them. The scanner also ran over
   1,013 public repositories.
   *Limits:* the test servers were written by the author. On real code, its SSRF alerts were
   correct 2 times out of 9, and its alerts about poisoned tool descriptions 0 times out of 29.
5. **[prompt-optimizer](https://github.com/adeoluo/prompt-optimizer)** (`Python`) - automatically rewrites the
   instructions (prompts) given to an AI language model, using seven published methods, and
   checks which methods truly help. The best method raises a small model's score on GSM8K, a
   set of grade-school math word problems, from `64.7%` to `75.0%` correct. The model runs on
   the laptop itself.
   *Limits:* the results come from one optimization run (one random seed), and no method
   improves scores on BIG-Bench Hard, a set of difficult reasoning tasks.
6. **[agent-platform](https://github.com/adeoluo/agent-platform)** (`Python`, `TypeScript`) - a service that
   runs AI agent jobs for many separate customers and survives crashes. When a worker process
   is killed in the middle of a job, none of the steps that had already finished runs again.
   *Limits:* it was tested against a scripted stand-in for the language model, never with a
   live large language model (LLM).

<details>
<summary><b>Full results and limits for nine systems, with live test status</b></summary>

<br/>

Each row links to the project's automated test status (the badge turns red if the tests fail)
and to its evaluation report. Each row states where the project wins and where established
tools beat it. Local benchmarks ran on one Apple M1 laptop with 8 processor cores (4 fast and
4 energy-saving) and 8 GB of memory, shared with other work.

| Project and test status | Languages | What it is | Checked results and limits |
| --- | --- | --- | --- |
| **[model-supply-chain-scanner](https://github.com/adeoluo/model-supply-chain-scanner)**<br/>[![CI](https://github.com/adeoluo/model-supply-chain-scanner/actions/workflows/ci.yml/badge.svg)](https://github.com/adeoluo/model-supply-chain-scanner/actions/workflows/ci.yml)<br/><sub>[evaluation report](https://github.com/adeoluo/model-supply-chain-scanner/blob/main/docs/EVALUATION_REPORT.md)</sub> | `Rust` · `Python` | Reads AI model files without loading them and reports code that would run on load, files the model would read, and damaged file structure. It covers the pickle, PyTorch, joblib, NumPy, Keras, TensorFlow SavedModel, ONNX, GGUF and safetensors formats, 7z and tar archives, and YAML and JSON configuration files. Results can be written as SARIF, the standard format for code-scanning results. | **Other projects' test files (181):** flags 141 of 144 dangerous files and 0 of 37 safe ones. ModelAudit flags 139 (4 false alarms), picklescan 113 (0) and fickling 107 (6). The two-file lead over ModelAudit is within noise, and these files were the development target. **Real Hugging Face files (12,573 from 4,727 repositories; nobody has confirmed which are dangerous):** flags all 24 files that run a command or read outside the model. In the first sample it raises 6 alerts on 8,495 files that carry no attack (version 0.1 raised 31 on 7,563). **A second sample, scanned before any tuning:** 14 alerts on 4,023 files without an attack (picklescan raised 3), and one proof-of-concept attack rated low. After the fixes it raises 1, which is no longer an unseen result. **Author-written test set (243 files):** 142 of 142 dangerous and 0 of 101 safe; this checks that known cases stay caught, not how many unknown attacks it would catch. *Broken by outside reviewers:* three rounds of tests got files past version 0.1 (for example through `torch.utils.collect_env.run` and a pickled Keras `Lambda` layer). All are fixed and [listed with their causes](https://github.com/adeoluo/model-supply-chain-scanner#bypasses-found-by-outside-reviewers). A class in a trusted library whose constructor runs code, and that is not in the scanner's catalog, still passes. |
| **[ml-graph-compiler](https://github.com/adeoluo/ml-graph-compiler)**<br/>[![CI](https://github.com/adeoluo/ml-graph-compiler/actions/workflows/ci.yml/badge.svg)](https://github.com/adeoluo/ml-graph-compiler/actions/workflows/ci.yml)<br/><sub>[evaluation report](https://github.com/adeoluo/ml-graph-compiler/blob/main/docs/EVALUATION_REPORT.md)</sub> | `Python` · `C` | A compiler for trained models. It reads a model in the ONNX format, merges operations, plans all working memory ahead of time (GPT-2 needs 3.0 MB instead of 113.6 MB), and writes C code that uses the M1's vector instructions (NEON) and several cores (OpenMP). It can also export the model as MLIR, the intermediate format of the LLVM compiler project, checked with the `mlir-opt` tool. | **Same top prediction as ONNX Runtime on 100% of inputs:** 3,925 Imagenette photos, and 6,400 token positions of the BERT and GPT-2 language models. **With 8 threads** across the M1's 4 fast and 4 energy-saving cores, it is 1.23 to 1.37 times faster than ONNX Runtime on ResNet-50 (29.8 against 40.9 milliseconds), BERT-base (72.0 against 88.8 ms) and GPT-2 (109.7 against 149.4 ms), and ties on MobileNetV2 (6.0 ms). *Where it loses:* with 1 thread (by 1.12 to 1.16 times) and with 4 threads on the fast cores (by 1.05 to 1.38 times), ONNX Runtime wins on all 4 models. PyTorch with Apple's Accelerate library is faster on the language models: by 1.20 to 1.32 times with 8 threads and by 4.27 to 5.56 times with 1 thread. |
| **[lambdamart-ranking-engine](https://github.com/adeoluo/lambdamart-ranking-engine)**<br/>[![CI](https://github.com/adeoluo/lambdamart-ranking-engine/actions/workflows/ci.yml/badge.svg)](https://github.com/adeoluo/lambdamart-ranking-engine/actions/workflows/ci.yml)<br/><sub>[evaluation report](https://github.com/adeoluo/lambdamart-ranking-engine/blob/main/docs/EVALUATION_REPORT.md)</sub> | `Rust` · `Python` | Learns to rank search results with LambdaMART, a method that builds many small decision trees, each one correcting the earlier ones. The tree builder is written in Rust. It also includes neural-network rankers, models of how users click, and a correction for the bias in click data (inverse propensity weighting). | Quality is NDCG at 10 (from 0 to 1, higher is better). **MSLR-WEB10K** (Microsoft's dataset: 1.2 million documents, 10,000 queries; average of 5 standard splits): 0.5029, which is 0.0013 below **LightGBM's 0.5042**. That gap is not statistically significant (paired test, p = 0.103). XGBoost scores 0.5061. **Istella-S** (an Italian web-search dataset with 3.4 million query-document pairs): 0.7603, against 0.7595 for LightGBM and 0.7554 for XGBoost. *Training time for 500 trees on MSLR-WEB10K:* **LightGBM is fastest at 39.7 seconds**, ahead of this package (68.1 s) and XGBoost (81.5 s). |
| **[mcp-security-scanner](https://github.com/adeoluo/mcp-security-scanner)**<br/>[![CI](https://github.com/adeoluo/mcp-security-scanner/actions/workflows/ci.yml/badge.svg)](https://github.com/adeoluo/mcp-security-scanner/actions/workflows/ci.yml)<br/><sub>[evaluation report](https://github.com/adeoluo/mcp-security-scanner/blob/main/docs/EVALUATION_REPORT.md)</sub> | `Go` | Checks Model Context Protocol (MCP) servers, the tool servers AI assistants connect to. It follows untrusted input through the source code to dangerous operations (taint analysis), and it also starts servers and probes them over the protocol. It looks for poisoned tool descriptions, injection, path traversal, and tools that change after a user approved them ("rug pulls"). Results can be written as SARIF. | **432 test servers written by the author**, each holding one planted flaw or one safe look-alike: it finds 96.8% of the flaws and wrongly flags 8.5% of the safe servers. On the standard flaw types it finds all of them with 2% false alarms, while Semgrep finds 59% of injections and 0% of traversals. It misses all 4 hard command injections and all 60 reworded poisoning cases. **1,013 public MCP repositories** (12.2 million lines of code): an AI agent checked a sample of the findings against a written rubric. The share of correct findings (precision) is 0.80 to 1.00 for web-server and login settings, 0.92 for path traversal (0.08 would need a fix), 11 of 22 for leaked secrets, and low for command injection (2 of 7), SSRF (2 of 9) and poisoned tool text (0 of 29; no sampled finding was a real attack). Each finding now shows its rule's checked precision. High-severity poisoning alarms on that set fell from 25 to 15 after three checked false-alarm patterns were removed. |
| **[prompt-optimizer](https://github.com/adeoluo/prompt-optimizer)**<br/>[![CI](https://github.com/adeoluo/prompt-optimizer/actions/workflows/ci.yml/badge.svg)](https://github.com/adeoluo/prompt-optimizer/actions/workflows/ci.yml)<br/><sub>[results in the README](https://github.com/adeoluo/prompt-optimizer#results)</sub> | `Python` | Seven methods that rewrite prompts automatically (MIPROv2, TextGrad, GEPA, OPRO, APE, PromptBreeder, and a method that bootstraps worked examples), all held to the same budget of model calls. They run on small Qwen3.5 language models on the laptop and are compared with DSPy 3.4.1, a widely used prompt-optimization library. | **GSM8K** (grade-school math word problems) with Qwen3.5-2B: a TextGrad-style search raises test accuracy from 64.7% to **75.0%**, a gain of 10.3 percentage points (confidence interval 4.7 to 16.0), using 399 task runs. *Limits:* no method improves BIG-Bench Hard; the MIPROv2-style method scores below the starting prompt on the test set although it tied on the validation set; and every result comes from one optimization seed. |
| **[agent-platform](https://github.com/adeoluo/agent-platform)**<br/>[![CI](https://github.com/adeoluo/agent-platform/actions/workflows/ci.yml/badge.svg)](https://github.com/adeoluo/agent-platform/actions/workflows/ci.yml)<br/><sub>[benchmarks](https://github.com/adeoluo/agent-platform/tree/main/benchmarks)</sub> | `Python` · `TypeScript` | A service that runs AI agent jobs for many customers (tenants) at once. It combines a safety gateway, automatic switching between OpenAI and Anthropic models when one fails, keyword-based document search, an MCP tool server, memory, and a job queue in SQLite (a file-based database) whose leases stop two workers from running the same job. | API keys are stored as keyed hashes (HMAC with a secret "pepper"), and the service refuses connections from other machines until that secret is changed from its default value. Each tenant sees only its own data. When a worker is killed with `SIGKILL` (an immediate stop that cannot be caught), **0 already-saved steps run again**; the interrupted step may run twice. *Limit:* the speed figures, **554 requests per second** with caching and **390** without (99% of requests answered within 46 ms and 85 ms; 10,000 requests each across 20 tenants, with at most 256 open files), use a scripted offline stand-in for the model and hashed word features instead of learned embeddings. They measure database and gateway overhead, not the quality of a live LLM. *Broken by an outside reviewer:* versions up to 0.4.1 leaked two file handles per request and stopped answering after about 2,040 requests. This is fixed, with a test that would catch it again. |
| **[vectordb-go](https://github.com/adeoluo/vectordb-go)**<br/>[![CI](https://github.com/adeoluo/vectordb-go/actions/workflows/ci.yml/badge.svg)](https://github.com/adeoluo/vectordb-go/actions/workflows/ci.yml)<br/><sub>[raw results](https://github.com/adeoluo/vectordb-go/tree/main/benchmarks/results)</sub> | `Go` | A standalone vector database server. It stores vectors (lists of numbers that represent items) and finds the nearest ones quickly with an HNSW graph, a layered graph for approximate nearest-neighbor search. Every write goes first to a checksummed write-ahead log (WAL), a journal used to recover after a crash, and several writes share one disk flush. It has an HTTP interface. | Passes Go's race detector (a check for unsafe simultaneous memory access) and crash tests in which the log is cut off mid-write while several writers run. **On 1,000,000 SIFT vectors** (a standard image-feature dataset), its distance code, written in ARM64 assembly language (76 lines), answers queries **1.3 to 2.0 times faster than hnswlib** at the same accuracy, for search widths (`ef`) from 32 to 256. A 3.5 times reading at `ef` 16 is discounted as noise. *Limit:* this holds only on ARM64 processors such as the M1, where hnswlib has no hand-written vector code and runs plain C++. On x86 processors with AVX vector instructions, expect hnswlib to win. |
| **[prompt-injection-detector](https://github.com/adeoluo/prompt-injection-detector)**<br/>[![CI](https://github.com/adeoluo/prompt-injection-detector/actions/workflows/ci.yml/badge.svg)](https://github.com/adeoluo/prompt-injection-detector/actions/workflows/ci.yml)<br/><sub>[evaluation report](https://github.com/adeoluo/prompt-injection-detector/blob/main/docs/EVALUATION_REPORT.md)</sub> | `Rust` · `Python` | Detects prompt injection: text written to take over an AI model's instructions. A fast Rust scorer reads hashed groups of characters (n-grams) and learns online with FTRL; it takes **27 microseconds** per prompt, 17 times faster than scikit-learn (464 microseconds). A small fine-tuned transformer model (`e5-small`) is the second scorer. | **Test set:** 91,089 prompts from 13 public datasets, with near-duplicates removed. On prompts like its training data it scores **0.9996 AUROC** (a ranking score from 0.5 for chance to 1.0 for perfect) and catches 99.5% of attacks while flagging 1% of safe prompts. A standard scikit-learn baseline scores almost the same (0.9995), so the score reflects the writing style of each data source more than the model. *Limits:* on attack families held out of training, the catch rate drops to **45.3%** (Lakera dataset), **42.1%** (SPML) and **22.6%** (deepset). Replacing letters with look-alike symbols (leetspeak) defeats it (0.6% caught). **A short injection hidden inside a 16,384-character safe document is caught 1.65% of the time** (0% before window-by-window scoring was added). It screens prompts; it does not detect injections hidden in documents. |
| **[corpus-dedup-library](https://github.com/adeoluo/corpus-dedup-library)** · **[bpe-tokenizer-library](https://github.com/adeoluo/bpe-tokenizer-library)**<br/>[![CI](https://github.com/adeoluo/corpus-dedup-library/actions/workflows/ci.yml/badge.svg)](https://github.com/adeoluo/corpus-dedup-library/actions/workflows/ci.yml)<br/><sub>[deduplication report](https://github.com/adeoluo/corpus-dedup-library/blob/main/docs/EVALUATION_REPORT.md) · [tokenizer report](https://github.com/adeoluo/bpe-tokenizer-library/blob/main/docs/EVALUATION_REPORT.md)</sub> | `Rust` (PyO3) · `Python` | Two Rust libraries with Python bindings (PyO3). The first removes near-duplicate documents from large text collections with MinHash and locality-sensitive hashing (LSH), and gives exactly the same output as its Python reference. The second is a tokenizer: it splits text into GPT-2's 50,257 sub-word pieces (byte-level byte-pair encoding, BPE) and turns them back into the exact original text, token for token the same as its Python reference. | `corpus-dedup-library` processes **1.4 million C4 documents** (a public web-text dataset) **in 30 seconds**, and is **13.7 times faster** than the Python library datasketch on a 50,000-document comparison. `bpe-tokenizer-library` trains a 50,257-token vocabulary on 100 MB of C4 text in **6.7 seconds**, and encodes batches at **68.5 MB per second** against 52.4 MB per second for tiktoken (OpenAI's tokenizer). *Limit:* on a single thread it is level with tiktoken (within 3%), not ahead. |

</details>

---

## Evidence Levels

Every README states one of these levels. They keep a project checked against thousands of real
images apart from a project checked against a small made-up example, even when both have an
evaluation report.

| Level | Meaning | Repositories |
| --- | --- | --- |
| **Unit tested** | Behaviour is covered by tests the author wrote. | `agent-sandbox`, `agent-platform`, `llm-gateway`, `llm-observability`, `rlhf-reward-model` |
| **Reference validated** | Outputs are checked against an established implementation, on small or synthetic (made-up) inputs. | `transformer-from-scratch` (PyTorch), `evaluation-harness` (SciPy), `bot-traffic-econometrics` (SciPy), `llm-vuln-scanner` (garak) |
| **Publicly benchmarked** | Measured on public datasets, or head-to-head against established tools, with the raw results committed. | `ml-graph-compiler`, `vectordb-go`, `lambdamart-ranking-engine`, `prompt-injection-detector`, `corpus-dedup-library`, `bpe-tokenizer-library`, `ann-vector-search-library`, `hybrid-rag`, `ad-auction-lab`, `prompt-optimizer`; partly on test sets written by the author: `model-supply-chain-scanner`, `mcp-security-scanner` |
| **Independently reproduced** | Someone else has rerun the results. | None yet |
| **Production observed** | Running for real users. | None |

I ran every benchmark myself, on one laptop. The two scanners are graded partly on test sets
I wrote. The precision check of the MCP scanner was labeled by an AI agent following a written
rubric, not by a human reviewer.

---

## All 21 Repositories by Area

<p align="center">
  <img src="assets/portfolio-architecture.svg" alt="End-to-End AI Infrastructure, Security and Threat Econometrics Stack" width="100%">
</p>

<table>
<tr>
<td width="50%" valign="top">

### 1. Training Data, Teaching Libraries and Model Alignment
- **[corpus-dedup-library](https://github.com/adeoluo/corpus-dedup-library)** (`Rust` · `Python`) - removes near-duplicate documents from web-scale text collections (MinHash and LSH) and filters low-quality text, tested on the C4 dataset.
- **[bpe-tokenizer-library](https://github.com/adeoluo/bpe-tokenizer-library)** (`Rust` · `Python`) - a GPT-2 style tokenizer that never loses text, with Python bindings and parallel batch encoding.
- **[prompt-optimizer](https://github.com/adeoluo/prompt-optimizer)** (`Python`) - seven automatic prompt-rewriting methods tested on local Qwen3.5 models with GSM8K math problems and BIG-Bench Hard reasoning tasks, compared with the DSPy 3.4.1 library.
- **[transformer-from-scratch](https://github.com/adeoluo/transformer-from-scratch)** (`Python`) - *a teaching library:* a minimal engine that computes gradients automatically (reverse-mode automatic differentiation in NumPy) and a tiny transformer language model. It is trained only on a copying task and a 1,718-character text sample. Its outputs and all 48 gradient sets match PyTorch within `1e-9` in automated tests. An 8-seed experiment on induction heads (attention patterns that copy earlier text) found no effect.
- **[rlhf-reward-model](https://github.com/adeoluo/rlhf-reward-model)** (`Python`) - *a controlled study on made-up data:* how a reward model learns human preferences (Bradley-Terry model), two methods for training a model on that reward (PPO and DPO), and what happens when a reward is optimized too hard. The task is a 12-feature simulated choice problem; no language model weights are involved.

</td>
<td width="50%" valign="top">

### 2. Compilers, Search and Applied Machine Learning
- **[ml-graph-compiler](https://github.com/adeoluo/ml-graph-compiler)** (`Python` · `C`) - compiles ONNX models into C code for one machine, with operation merging, ahead-of-time memory planning, and an MLIR export checked with `mlir-opt`.
- **[vectordb-go](https://github.com/adeoluo/vectordb-go)** (`Go`) - *a standalone network server:* a vector database with an HNSW search graph, a write-ahead log for crash recovery, and an HTTP interface.
- **[ann-vector-search-library](https://github.com/adeoluo/ann-vector-search-library)** (`Rust` · `Python`) - *a library used inside a program:* an HNSW nearest-neighbor index with Python bindings, used by `hybrid-rag` and `agent-platform`.
- **[hybrid-rag](https://github.com/adeoluo/hybrid-rag)** (`Python`) - *keyword search for retrieval-augmented generation (RAG), no embeddings:* BM25 and TF-IDF keyword search, rank fusion and reranking. On the BEIR SciFact benchmark, BM25 with word stemming scores `0.687` NDCG at 10 against `0.665` for the hybrid of both methods. On TREC-COVID (171,000 documents) the hybrid scores `0.666` against `0.663` for BM25.
- **[lambdamart-ranking-engine](https://github.com/adeoluo/lambdamart-ranking-engine)** (`Rust` · `Python`) - learning to rank with LambdaMART, neural rankers, and correction for bias in click data, on MSLR-WEB10K (1.2 million documents) and Istella-S (3.4 million query-document pairs).
- **[ad-auction-lab](https://github.com/adeoluo/ad-auction-lab)** (`Rust` · `Python`) - online advertising auctions (generalized second-price, Vickrey-Clarke-Groves and first-price), bid shading, budget pacing, click-through-rate prediction on the Criteo dataset, and evaluation of ad policies from logged data with the Open Bandit dataset.

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 3. AI Security, Sandboxing and Bot-Traffic Statistics
- **[bot-traffic-econometrics](https://github.com/adeoluo/bot-traffic-econometrics)** (`Rust` · `Python`) - *statistical methods, shown on made-up data only:* separating changes in bot-traffic rates into their causes, sharing a traffic surge among its causes (Shapley values), bounds when part of the data is hidden (Manski bounds), a fast estimator for self-exciting event models (Hawkes processes, checked against SciPy), and a leader-follower game (Stackelberg game) in which a defender protects two channels, the website and the mobile app interface, and attackers move to the weaker one. The game is not fitted to real data. A companion to my [2026 F5 Labs report](https://www.f5.com/labs/articles/2026-black-friday-bot-report), not its analysis or data.
- **[model-supply-chain-scanner](https://github.com/adeoluo/model-supply-chain-scanner)** (`Rust` · `Python`) - *checks model files before they are loaded:* reads pickle files without running them, plus Keras, TensorFlow SavedModel, ONNX, GGUF and safetensors files, archives and configuration files. Run over 12,573 Hugging Face files.
- **[mcp-security-scanner](https://github.com/adeoluo/mcp-security-scanner)** (`Go`) - *checks AI tool servers:* traces untrusted input through source code, detects tools that change after approval, and probes running servers. Tested on 432 planted cases and 1,013 public MCP repositories (precision per rule from a sample checked by an AI agent against a written rubric).
- **[prompt-injection-detector](https://github.com/adeoluo/prompt-injection-detector)** (`Rust` · `Python`) - *screens prompts for injection:* a 27-microsecond Rust scorer plus a fine-tuned transformer, tested with attack families held out of training, adversarial rewrites and long documents.
- **[llm-vuln-scanner](https://github.com/adeoluo/llm-vuln-scanner)** (`Python` · `Rust`) - *attacks live language models to find weaknesses (red-teaming):* 540-probe test campaigns against local Qwen3.5, Gemma 4 and Granite 4.2 models, mapped to the OWASP 2026 risk lists for LLM and agent applications and to MITRE ATLAS, and compared with the garak scanner.
- **[agent-sandbox](https://github.com/adeoluo/agent-sandbox)** (`Rust`) - *contains what an AI agent may run:* a rule-based policy engine, operating-system isolation (Seatbelt on macOS, Landlock on Linux) and a tamper-evident audit log in which each entry includes the hash of the one before. On Linux as the administrator account (root), where the usual process limit is ignored, it limits processes with a control group (cgroup) or a system-call filter (seccomp), or it refuses to run the command. Automated tests run as root in a container for each case. No outside security audit.

</td>
<td width="50%" valign="top">

### 4. Serving, Multi-Customer Agents and Monitoring
- **[agent-platform](https://github.com/adeoluo/agent-platform)** (`Python` · `TypeScript`) - *a complete service for many customers:* combines `llm-gateway`, `hybrid-rag` (keyword search), `ann-vector-search-library`, `evaluation-harness` and `llm-observability` behind hashed API keys, an MCP server and a SQLite job queue with leases.
- **[llm-gateway](https://github.com/adeoluo/llm-gateway)** (`Python` · `Go`) - *a proxy between applications and language-model providers:* a Python gateway and a Go reverse proxy tested to behave the same. It switches between OpenAI and Anthropic when one fails, enforces per-customer quotas, screens for injection with 10 fixed patterns (a heuristic, not a security boundary, with a hook for a learned scorer), hides card numbers and other personal data (checked with the Luhn checksum), and caches responses by keyword match.
- **[evaluation-harness](https://github.com/adeoluo/evaluation-harness)** (`Python`) - *a statistics toolkit for comparing models:* bootstrap confidence intervals for paired results, the exact McNemar test and Cohen's d effect size, all checked against SciPy (differences below `1e-15` for Cohen's d and McNemar, and `0.0014` for a 1,000-draw bootstrap, which is random by design), plus checks for test data leaked into training data.
- **[llm-observability](https://github.com/adeoluo/llm-observability)** (`Python` · `TypeScript`) - *monitoring for language-model applications:* a Python tracer with no outside dependencies, a collector service, a cost and service-level engine, and a TypeScript screen for browsing traces.

</td>
</tr>
</table>

---

## Key terms

Plain definitions of the terms used on this page.

| Term | Meaning |
| --- | --- |
| Apple M1 | Apple's first laptop processor. It has 4 fast and 4 energy-saving cores. All timings on this page come from one M1 laptop. |
| AUROC | Area under the receiver operating characteristic curve. How well a detector ranks attacks above safe inputs, from 0.5 (chance) to 1.0 (perfect). |
| BERT, GPT-2 | Two well-known language models, from Google and OpenAI. |
| BM25 | A standard formula that scores how well a document matches the words of a search query. |
| Confidence interval | A range that likely holds the true value. A narrower range means a more precise result. |
| Embedding | A list of numbers that represents the meaning of a text, so that similar texts get similar numbers. |
| Evaluation report | A document in each repository with the full method, all measured numbers and how to reproduce them. |
| FAISS, hnswlib | Widely used libraries for fast nearest-neighbor search, from Meta and an open-source project. |
| False alarm (false positive) | A safe item that a scanner or detector wrongly flags. |
| fickling, picklescan, ModelAudit | Other open-source scanners for AI model files, from Trail of Bits, an independent maintainer, and Promptfoo. |
| garak | NVIDIA's open-source scanner that probes language models for weaknesses. |
| GSM8K, BIG-Bench Hard | Public test sets: grade-school math word problems, and difficult reasoning tasks. |
| Hugging Face | The largest public website for sharing AI models and datasets. |
| Imagenette | A 10-class subset of ImageNet, the standard photo-recognition dataset. |
| Language model (LLM) | An AI model trained on text that predicts and writes text. LLM stands for large language model. |
| LightGBM, XGBoost | Widely used libraries that learn from data with many decision trees, from Microsoft and an open-source project. |
| MCP (Model Context Protocol) | An open standard that lets AI assistants call outside tools through tool servers. |
| MITRE ATLAS | A public knowledge base of attack techniques against AI systems. |
| NDCG at 10 | Normalized discounted cumulative gain. A score from 0 to 1 for how well the top 10 search results are ordered. Higher is better. |
| ONNX, ONNX Runtime | ONNX is an open file format for trained models. ONNX Runtime is Microsoft's standard engine for running ONNX models. |
| OWASP | The Open Worldwide Application Security Project. It publishes ranked lists of the main security risks for software, including language-model and agent applications. |
| Pickle | Python's built-in format for saving objects. Opening a pickle file can run code chosen by whoever made the file. |
| Precision | Of the items a tool flags, the share that are truly problems. Higher is better. |
| PyTorch, scikit-learn, SciPy | Standard Python libraries for deep learning, classic machine learning, and scientific computing. |
| Qwen3.5, Gemma 4, Granite 4.2 | Open language models from Alibaba, Google and IBM that can run on a laptop. |
| Recall | Of the true problems, the share that a tool finds. Higher is better. |
| ResNet-50, MobileNetV2 | Two well-known image-recognition models. |
| Seed | The starting number of a random-number generator. Repeating a test with several seeds shows whether a result depends on luck. |
| Semgrep | A widely used open-source tool that scans source code for patterns that indicate bugs. |
| Thread | One task that a processor runs in parallel with others. More threads can use more cores. |
| tiktoken | OpenAI's tokenizer library. |
| Token, tokenizer | A token is a small piece of text, such as a word or part of a word. A tokenizer splits text into tokens. |
| Transformer | The neural-network design behind modern language models. |
