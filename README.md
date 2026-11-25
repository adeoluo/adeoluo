<div align="center">

# Adeolu Ogunnoiki

**AI Systems, Security and Machine Learning Engineer Who Directs Multi-Agent Workflows**

Bachelor of Computer Science with Distinction (Certificate of Specialization in Data Science), **Dalhousie University**<br/>
Master of Data Science in progress (Focus: Artificial Intelligence and Machine Learning), **Johns Hopkins University**

[**LinkedIn**](https://www.linkedin.com/in/adeolu-ogunnoiki) · [**F5 Labs Author Profile**](https://www.f5.com/labs/authors/adeolu-ogunnoiki)

`Python` · `Rust` · `Go` · `TypeScript`

</div>

---

I build software in Python, Rust, Go and TypeScript by directing AI coding agents, and I
publish threat research on bots and automated attacks on websites. My latest report was picked
up by F5's North America Field Chief Information Security Officer (CISO) and covered by
*Dark Reading*, a top-tier cybersecurity news publication.

In each software project, I choose the problem and the established tool to compare against.
Every result is checked against that tool and reported together with its losses. None of these
projects has outside users yet.

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

## Selected Projects

- **[model-supply-chain-scanner](https://github.com/adeoluo/model-supply-chain-scanner)** checks AI model files for hidden code without opening
  them. Four other scanner projects publish 181 test files. On these files it catches 141 of
  the 144 dangerous ones with no false alarm; the next best tool catches 139, with 4 false
  alarms. *Limit:* it has not found a previously unknown attack, and its lead is two files.
- **[ml-graph-compiler](https://github.com/adeoluo/ml-graph-compiler)** turns a trained AI model into fast C code. Its predictions match
  ONNX Runtime, Microsoft's standard engine for running models, on all 3,925 test photos. With
  8 processor cores it is 1.23 to 1.37 times faster on three of four models. *Limit:* ONNX
  Runtime is faster with 1 or 4 cores, and all timings come from one laptop.
- **[lambdamart-ranking-engine](https://github.com/adeoluo/lambdamart-ranking-engine)** learns to put the most relevant search results first.
  On Microsoft's public search dataset its ranking quality ties LightGBM, a widely used
  library for this task (0.5029 against 0.5042, not a statistically significant difference).
  *Limit:* LightGBM trains about 1.7 times as fast.
- **[mcp-security-scanner](https://github.com/adeoluo/mcp-security-scanner)** finds security flaws in the tool servers that AI assistants
  connect to. In 432 test servers it found every planted flaw of three common types, where the
  code scanner Semgrep found 59%, 0% and 11%. *Limit:* the test servers were written by me, and
  on real code some alert types were rarely correct (2 of 9 for one type).
- **[prompt-optimizer](https://github.com/adeoluo/prompt-optimizer)** rewrites the instructions given to an AI model with seven
  published methods and measures which ones help. The best method raises a small model's score
  on grade-school math problems from 64.7% to 75.0%. *Limit:* each method was run once, and no
  method helped on a set of hard reasoning tasks.
- **[agent-platform](https://github.com/adeoluo/agent-platform)** runs AI agent jobs for many customers. When a worker is stopped in
  the middle of a job, no finished step runs again. *Limit:* it was tested with a scripted
  stand-in for the AI model, not with a live one.

## All Repositories

Each README opens with **Highlights** (the best checked results and where the project falls
short) and **Key terms** (plain definitions).

| Repository | What it does | Evidence level |
| --- | --- | --- |
| [model-supply-chain-scanner](https://github.com/adeoluo/model-supply-chain-scanner) | Checks AI model files for hidden code before they are opened. | Publicly benchmarked, partly on author-written tests |
| [mcp-security-scanner](https://github.com/adeoluo/mcp-security-scanner) | Finds security flaws in the tool servers that AI assistants connect to. | Publicly benchmarked, partly on author-written tests |
| [prompt-injection-detector](https://github.com/adeoluo/prompt-injection-detector) | Detects text written to take over an AI model's instructions. | Publicly benchmarked |
| [llm-vuln-scanner](https://github.com/adeoluo/llm-vuln-scanner) | Tests language models with attack prompts and reports their weaknesses. | Reference validated |
| [agent-sandbox](https://github.com/adeoluo/agent-sandbox) | Controls which commands an AI agent may run on a computer, and logs every decision. | Unit tested |
| [bot-traffic-econometrics](https://github.com/adeoluo/bot-traffic-econometrics) | Statistical methods for measuring bot traffic, shown on made-up data. | Reference validated |
| [ml-graph-compiler](https://github.com/adeoluo/ml-graph-compiler) | Turns a trained AI model into fast C code for one computer. | Publicly benchmarked |
| [vectordb-go](https://github.com/adeoluo/vectordb-go) | A database server that stores number vectors and finds the most similar ones. | Publicly benchmarked |
| [ann-vector-search-library](https://github.com/adeoluo/ann-vector-search-library) | A library that finds the most similar vectors quickly, usable from Python. | Publicly benchmarked |
| [hybrid-rag](https://github.com/adeoluo/hybrid-rag) | Finds the right documents for an AI model to answer from, using keyword search. | Publicly benchmarked |
| [lambdamart-ranking-engine](https://github.com/adeoluo/lambdamart-ranking-engine) | Learns to put the most relevant search results first. | Publicly benchmarked |
| [ad-auction-lab](https://github.com/adeoluo/ad-auction-lab) | Simulates online ad auctions and tests bidding and click-prediction methods on public data. | Publicly benchmarked |
| [corpus-dedup-library](https://github.com/adeoluo/corpus-dedup-library) | Removes near-duplicate documents from very large text collections. | Publicly benchmarked |
| [bpe-tokenizer-library](https://github.com/adeoluo/bpe-tokenizer-library) | Splits text into the small pieces (tokens) that language models read. | Publicly benchmarked |
| [prompt-optimizer](https://github.com/adeoluo/prompt-optimizer) | Rewrites instructions for AI models automatically and measures which methods help. | Publicly benchmarked |
| [transformer-from-scratch](https://github.com/adeoluo/transformer-from-scratch) | A small teaching version of the model design behind modern language models. | Reference validated |
| [rlhf-reward-model](https://github.com/adeoluo/rlhf-reward-model) | A controlled study of how AI models are trained on human preferences, on made-up data. | Unit tested |
| [agent-platform](https://github.com/adeoluo/agent-platform) | A service that runs AI agent jobs for many customers and recovers from crashes. | Unit tested |
| [llm-gateway](https://github.com/adeoluo/llm-gateway) | Sits between applications and AI model providers. It switches provider when one fails and limits use per customer. | Unit tested |
| [evaluation-harness](https://github.com/adeoluo/evaluation-harness) | Statistics for checking whether one AI model is really better than another. | Reference validated |
| [llm-observability](https://github.com/adeoluo/llm-observability) | Records each step of an AI application's work, with its time and cost. | Unit tested |

## Evidence Levels

Each repository states how strongly its results have been checked.

| Level | Meaning |
| --- | --- |
| **Unit tested** | The behaviour is covered by tests I wrote. |
| **Reference validated** | The outputs match an established tool on small or made-up inputs. |
| **Publicly benchmarked** | Measured on public data or against established tools, with the raw results published. |
| **Independently reproduced** | Someone else has rerun the results. No repository has reached this level yet. |
| **Production observed** | Running for real users. No repository has reached this level yet. |

I ran every benchmark myself, on one laptop.

<details>
<summary><b>How the 21 repositories fit together</b></summary>

<br/>

<p align="center">
  <img src="assets/portfolio-architecture.svg" alt="How the 21 repositories fit together" width="100%">
</p>

</details>
