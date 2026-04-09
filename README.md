<!-- ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ -->
<!--                       rakulav / rakulav · profile README                   -->
<!-- ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ -->

<div align="center">

<img src="./assets/hero.svg" alt="Rakul Venkatesan · AI Engineer · GenAI, RAG, Agentic Systems" width="100%" />

<br/><br/>

<a href="https://www.linkedin.com/in/rakulav-01/"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/></a>
<a href="mailto:rakulav26@gmail.com"><img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"/></a>
<a href="tel:+14052302654"><img src="https://img.shields.io/badge/+1%20(405)%20230--2654-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" alt="Phone"/></a>
<img src="https://img.shields.io/badge/San%20Jose%2C%20CA-6366F1?style=for-the-badge&logo=googlemaps&logoColor=white" alt="Location"/>

</div>

<br/>

## About

I'm an **AI Engineer with 5+ years** building generative AI and agentic systems for workflows where a hallucination has a dollar cost. Most of my time goes to the unglamorous parts of the LLM stack: retrieval that won't invent policy numbers, eval harnesses that gate every rollout, and inference paths that turn a 2.1s p95 into 780ms without changing the model.

Currently shipping a **LangGraph mortgage-risk agent at Fannie Mae** over a governed policy corpus. Previously owned **fraud detection for QuickBooks Online at Intuit**, serving millions of users on SageMaker.

I care about retrieval that abstains, evals that gate, inference that's cheap, and agents that don't lose the plot at 5K items of context.

<br/>

## Impact at a glance

<img src="./assets/metrics.svg" alt="Impact metrics" width="100%" />

<br/>

## Featured systems

> Each of these solves a problem that doesn't show up in vendor demos.

<br/>

<table>
<tr>
<td width="50%" valign="top">

### 🛰️ CloudPilot
**Autonomous cloud engineer**

A LangGraph agent that scans an AWS account, reasons about misconfigurations across 14 resource types, and proposes least-privilege fixes. The interesting problems were **working memory at scale** and **cost of reasoning**.

**Highlights**

- **Streaming working memory in Qdrant** keeps the agent coherent at 5K+ resources per scan inside a 200K-token budget. Naive approaches overflow at ~800.
- **Two-stage model router.** Haiku 4.5 classifies findings on severity × confidence; only low-confidence cases escalate to Sonnet 4.6. **94% agreement** with a Sonnet-only baseline on a 200-scan eval.
- **Runtime IAM synthesis** via STS AssumeRole. Every proposed fix gets its own least-privilege, action-scoped role. No ambient admin creds.
- **60-second undo window** backed by a state-diff rollback engine that snapshots to Postgres.

```
cost / scan      $0.41  →  $0.09    ▼ 78%
scale            5K+ resources, 200K tok budget
agreement        94% vs Sonnet-only baseline
rollback         60s undo on reversible actions
```

`LangGraph` · `Claude MCP` · `boto3` · `Qdrant` · `FastAPI` · `Postgres` · `Next.js`

</td>
<td width="50%" valign="top">

### 📚 PaperMind
**Personal AI research analyst**

Retrieval over 340 ML papers that knows when not to answer. Built after getting frustrated with RAG demos that confidently cite nonexistent sections.

**Highlights**

- **GROBID structural parsing** instead of token-count chunking. Sections, equations, and tables stay intact. Top-5 precision: **67% → 89%** on a 150-query labeled eval.
- **Two-stage confidence scorer.** A bge-reranker-v2 cross-encoder produces calibrated scores; a Sonnet 4.6 sufficiency judge decides if retrieved context actually answers. Below threshold, the system abstains.
- **Multi-hop LangGraph controller** decomposes comparative queries into parallel sub-queries, fans out hybrid BM25 + dense retrieval, then synthesizes.

```
top-5 precision       67%  →  89%
hallucinations (OOD)  ▼ 74%
in-scope answer rate  91%
multi-hop accuracy    82%  (baseline 34%)
```

`Claude` · `sentence-transformers` · `bge-reranker-v2-m3` · `Qdrant` · `OpenSearch` · `GROBID` · `LangGraph`

</td>
</tr>
</table>

<br/>

## Tech stack

<img src="./assets/stack.svg" alt="Tech stack" width="100%" />

<br/>

## Experience

### **Fannie Mae** · AI Engineer  <sub><sub>Jan 2025 – Dec 2025</sub></sub>

Architected a **LangGraph agent** for mortgage risk analysis that chains document retrieval, policy lookup, and decision tools in a single reasoning loop, processing thousands of documents daily and cutting manual analyst review by **30%**. Designed a hybrid **BM25 + dense retrieval** pipeline in OpenSearch that fixed dense-only hallucinations on policy numbers and lifted factuality by **52%** on a 500-question compliance eval built with underwriters. Fine-tuned a domain-adapted open-weights LLM with **QLoRA** on SageMaker under strict data governance, cutting GPU hours by **60%** vs full fine-tuning. Deployed **vLLM** on EKS with request batching and KV caching, dropping **p95 latency from 2.1s to 780ms** across 10M+ monthly document records. Built an **LLM-as-judge eval harness** with a 200-prompt regression suite that gated every rollout, catching **4 silent regressions across 2 release cycles**.

### **Intuit** · Machine Learning Engineer  <sub><sub>Aug 2021 – Jul 2023</sub></sub>

Owned the end-to-end fraud detection pipeline for **QuickBooks Online** on SageMaker, training XGBoost on **400+ behavioral features** and improving fraud precision by **18%** at fixed recall. Re-architected feature computation with distributed PySpark on EMR, reducing runtime from **6h to 90min** and enabling daily refresh for churn and LTV models. Built causal inference and uplift modeling pipelines with DoWhy/EconML, improving campaign targeting by **15%** over traditional A/B testing. Designed a staged release framework with shadow testing, canary deployments, and automated rollback on drift metrics, reducing production incidents by **25%**.

### **GrayRadiant Data Services** · Software Engineer, ML  <sub><sub>Apr 2019 – Aug 2021</sub></sub>

Built visual search and recommendation pipelines using PyTorch ResNet and OpenCV, improving recommendation **CTR by 15%**. Deployed real-time image classification and visual similarity models behind FastAPI. Engineered PySpark pipelines on EMR, reducing feature computation time by **25%**.

<br/>

## What I think about

> Problems I find genuinely interesting right now. If you're working on any of these, reach out.

**Abstention as a first-class capability.** Most RAG systems optimize answer rate. The interesting metric is _calibrated abstention_ — knowing when retrieved context isn't sufficient and saying so. PaperMind's confidence scorer is my current cut at this. I don't think it's solved.

**Working memory for long-horizon agents.** Context windows keep growing, but throwing everything at the model is the wrong move. I want agents that maintain an external working memory with principled eviction.

**Evals as deployment gates, not dashboards.** An eval suite that runs offline and produces a slide deck is theater. An eval suite that blocks a rollout is infrastructure. The latter is harder and more important.

**Inference cost as a modeling problem.** The gap between "works on one request" and "works at $0.09 across 5K items" is where most of the real engineering lives.

<br/>

## Education & certifications

**M.S. Data Science** · University of Central Oklahoma · 2023 – 2025
**Oracle Cloud Infrastructure Data Science Professional** · 2025
**AWS Machine Learning Specialty**

<br/>

## Let's talk

Best ways to reach me: **[LinkedIn DM](https://www.linkedin.com/in/rakulav-01/)** or **[email](mailto:rakulav26@gmail.com)**. Reply time is usually within 24 hours. I'm open to senior AI engineer roles in the Bay Area or remote.

<br/>

<div align="center">

<sub>

_"Production LLM systems are 10% prompting and 90% retrieval, evaluation, and knowing when to abstain."_

</sub>

</div>
