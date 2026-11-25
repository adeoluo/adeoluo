<div align="center">

# Adeolu Ogunnoiki

**AI Systems, Security and Machine Learning Engineer Who Directs Multi-Agent Workflows**

Bachelor of Computer Science with Distinction (Certificate of Specialization in Data Science), **Dalhousie University**<br/>
Master of Data Science in progress (Focus: Artificial Intelligence and Machine Learning), **Johns Hopkins University**

[**LinkedIn**](https://www.linkedin.com/in/adeolu-ogunnoiki) · [**F5 Labs Author Profile**](https://www.f5.com/labs/authors/adeolu-ogunnoiki)

`Python` · `Rust` · `Go` · `TypeScript`

</div>

---

I build and evaluate systems.

## Published Threat Research

All published by [F5 Labs](https://www.f5.com/labs/authors/adeolu-ogunnoiki).

| Date | Publication | My role |
| --- | --- | --- |
| Nov 2026 | [*Automation leading up to Black Friday*](https://www.f5.com/labs/articles/2026-black-friday-bot-report) ([PDF](https://cdn.sanity.io/files/k6fem79d/translations-production/1d1028afb94e20d907a0b98ef084535e84fc9cd5.pdf)) | Sole author |
| Nov 2024 | [*Black Friday Versus The Bots*](https://www.f5.com/labs/articles/black-friday-versus-the-bots) | Co-author (first of four listed) |
| Nov 2023 | [*Bots Target Retailers for Black Friday Bargains*](https://www.f5.com/labs/articles/bots-target-retailers-for-black-friday-bargains) | Co-author (first of two listed) |
| Nov 2023 | [*2023 Identity Threat Report: The Unpatchables*](https://www.f5.com/labs/articles/2023-identity-threat-report-the-unpatchables) | Co-author (nine listed) |
| Nov 2023 | [*2023 Identity Threat Report: Executive Summary*](https://www.f5.com/labs/articles/2023-identity-threat-report-executive-summary) | Co-author (nine listed) |

The 2026 report studies three Black Friday seasons of retail web traffic. It shows that the
reported rise in automated traffic, from `17.4%` to `28.6%` of transactions between 2023 and
2025, mixes real change with a change in which retailers were measured.

Both articles below discuss my F5 Labs published research report and link to it.

| Outlet | Article | Author | Date |
| --- | --- | --- | --- |
| **Dark Reading** | [*Why Holiday Security Can't Wait for Black Friday*](https://www.darkreading.com/cybersecurity-operations/why-holiday-security-cant-wait-black-friday) | Alexander Culafi, Senior News Writer | Nov 19, 2026 |
| **F5 Executive Blog** | [*The Black Friday automation trend everyone gets wrong*](https://www.f5.com/company/blog/the-black-friday-automation-trend-everyone-gets-wrong) | Sean Murphy, Field CISO (North America), F5 | Nov 19, 2026 |

## Projects

Each repository README gives the full method and results, including the limits.

### AI Security

| Project | What it does | Result |
| --- | --- | --- |
| [model-supply-chain-scanner](https://github.com/adeoluo/model-supply-chain-scanner) | Finds hidden code in AI model files before they are opened. | Highest score of five scanners on the test files the other four publish: 141 of 144 dangerous files caught, with no false alarms. |
| [mcp-security-scanner](https://github.com/adeoluo/mcp-security-scanner) | Finds security flaws in the tool servers that AI assistants connect to. | Found every planted flaw in 365 standard test cases, where the Semgrep code scanner found 0% to 59%. Run over 1,013 public repositories. |
| [prompt-injection-detector](https://github.com/adeoluo/prompt-injection-detector) | Detects text written to take over an AI model's instructions. | Scores a prompt in 27 microseconds, 17 times faster than a scikit-learn model of the same accuracy. |
| [llm-vuln-scanner](https://github.com/adeoluo/llm-vuln-scanner) | Attacks AI applications the way a real attacker would and reports what worked. | 540 attacks against each of five open models, compared with NVIDIA's garak scanner. |
| [agent-sandbox](https://github.com/adeoluo/agent-sandbox) | Controls which commands an AI agent may run, and records every decision. | Blocked all 38 hostile test commands. Rejects a disallowed command in about 8 microseconds. |
| [bot-traffic-econometrics](https://github.com/adeoluo/bot-traffic-econometrics) | Statistical methods for measuring bot traffic on websites. | Rust core 17 to 134 times faster than the Python version, with matching results. |

### Machine Learning Systems

| Project | What it does | Result |
| --- | --- | --- |
| [ml-graph-compiler](https://github.com/adeoluo/ml-graph-compiler) | Turns a trained AI model into fast C code for one computer. | Same predictions as Microsoft's ONNX Runtime on all 3,925 test photos, and up to 1.37 times faster with 8 threads (parallel streams of work). |
| [transformer-from-scratch](https://github.com/adeoluo/transformer-from-scratch) | A small language model built from first principles in NumPy. | Its hand-written training math (all 48 sets of gradients) matches PyTorch to within 0.000000001. |
| [rlhf-reward-model](https://github.com/adeoluo/rlhf-reward-model) | A controlled study of training AI models on human preferences. | Training closed 96.6% of the gap to the best possible behaviour. |
| [prompt-optimizer](https://github.com/adeoluo/prompt-optimizer) | Rewrites the instructions given to AI models with seven published methods. | Raised a small model from 64.7% to 75.0% correct on grade-school math problems. |

### Search, Data and Ranking

| Project | What it does | Result |
| --- | --- | --- |
| [lambdamart-ranking-engine](https://github.com/adeoluo/lambdamart-ranking-engine) | Learns to put the most relevant search results first. | Ties LightGBM, a widely used library, on Microsoft's public search dataset, and has the top score of three libraries on a second dataset. |
| [vectordb-go](https://github.com/adeoluo/vectordb-go) | A database server that finds the most similar items among millions of vectors (lists of numbers that represent text or images). | Answers 1.3 to 2.0 times as many queries per second as the hnswlib library on one million vectors, at nearly the same accuracy, on an Apple M1 laptop. |
| [ann-vector-search-library](https://github.com/adeoluo/ann-vector-search-library) | A library that finds the most similar items quickly, usable from Python. | Same accuracy as hnswlib, a widely used C++ library, on 10,000 vectors. |
| [hybrid-rag](https://github.com/adeoluo/hybrid-rag) | Finds the right documents for an AI model to answer from. | Beats the published search baseline on SciFact, a benchmark of scientific claims (0.687 against 0.665), and runs about 70 times faster than the rank_bm25 Python library. |
| [ad-auction-lab](https://github.com/adeoluo/ad-auction-lab) | Online ad auctions, bidding, budget pacing and click prediction. | Its click model slightly beats the same model built in PyTorch, trained on 9.17 million real ad logs. |
| [corpus-dedup-library](https://github.com/adeoluo/corpus-dedup-library) | Removes near-duplicate documents from very large text collections. | Deduplicated 1.4 million web pages in 30.5 seconds on one laptop. |
| [bpe-tokenizer-library](https://github.com/adeoluo/bpe-tokenizer-library) | Splits text into the pieces (tokens) that language models read. | Encodes batches faster than OpenAI's tiktoken (68.5 against 52.4 MB per second). |

### AI Applications and Infrastructure

| Project | What it does | Result |
| --- | --- | --- |
| [agent-platform](https://github.com/adeoluo/agent-platform) | Runs AI agent jobs for many customers, with each customer's data kept separate. | 554 requests per second with no errors. A job whose worker is killed resumes without repeating a finished step. |
| [llm-gateway](https://github.com/adeoluo/llm-gateway) | Sits between applications and AI model providers, and switches provider when one fails. | 2,000 of 2,000 requests succeeded while the main provider was failing. |
| [evaluation-harness](https://github.com/adeoluo/evaluation-harness) | Statistics for deciding whether one AI model is really better than another. | Agrees with SciPy to about 16 decimal places. |
| [llm-observability](https://github.com/adeoluo/llm-observability) | Records each step of an AI application's work, with its time and cost. | Records about 194,000 steps per second. |
