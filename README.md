<p align="center">
<img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=500&size=21&duration=2600&pause=900&color=2DA44E&center=true&vCenter=true&width=800&height=60&lines=%24+whoami;sharayu+%E2%80%94+I+build+the+systems+around+AI+models;%24+ls+~%2Fcurrent;vital-agent%2F++vision-pipeline%2F++smartcache-ai%2F;%24+_" alt="terminal" />
</p>

<h1 align="center">Sharayu Rasal</h1>

<p align="center"><b>I build the systems around AI models — not just the part that calls the model.</b></p>

<p align="center">
<a href="https://sharayu.dev">sharayu.dev</a> · <a href="https://linkedin.com/in/sharayu-rasal-70a030213">LinkedIn</a> · <a href="mailto:srr10019@nyu.edu">Email</a> · <a href="https://vital-agent.vercel.app">VITAL, live</a>
</p>

---

CS master's from NYU, in New York. Most of what I enjoy sits one layer below the demo — the router that decides which agent answers, the queue that absorbs a camera dropping offline, the eval that notices an answer got worse before a user does.

**In a hurry?** The four links above are the whole story. Everything below is detail.

---

## What I'm building

### VITAL — a multi-agent life copilot
**[Live app](https://vital-agent.vercel.app)** · **[Code](https://github.com/Sharayu1418/vital-agent)**
`LangGraph` `Vertex AI` `FastAPI` `Next.js 15` `~480 tests`

Six specialized agents on a stateful graph. Sleep, energy, weather, places and interests go in; a plan you have to approve comes out.

The part I'd defend in an interview: the node that writes to your calendar has exactly one inbound edge, and it comes from your approval. That isn't a rule the model is asked to follow — it's a **path that does not exist**, so no prompt injection can talk its way onto it. Guarantees belong in topology, not in prompts.

Quality is measured rather than asserted. Routing, crisis detection, memory retrieval and answer quality all have evals with gates — routing fails the build below 90%. And the energy forecast is a real model, not a prompt: Borbély's two-process model keyed to your own wake time, reporting a confidence that degrades honestly. With no data it says 10% and tells you the curve isn't yours.

### Real-time multi-camera vision pipeline
**[Code](https://github.com/Sharayu1418/RealTimeComputerVisionPipeline)**
`Kafka` `Triton` `YOLOv8 ONNX` `Prometheus/Grafana`

`RTSP → Kafka → Triton (dynamic batching, gRPC) → tracking → WebSocket dashboard`, with metrics from the first commit.

Built to find out where a streaming CV system actually breaks, which turned out to be nowhere near the model — it breaks at letterbox preprocessing, at batch-window sizing, and at the question of what the rest of the pipeline should do when one camera simply stops answering. The tradeoffs are written down in `DECISIONS.md` rather than lost, including the ones I'd make differently now.

### SmartCache AI
**[Code](https://github.com/Sharayu1418/SmartCache-AI)**
`Django REST` `React` `Redis/Celery` `S3`

A recommender that pre-caches content to S3 *before* you ask for it, for users on connections that can't fetch on demand.

Recommendation systems assume the content is one request away. This one assumes it isn't — which turns "what should we show this user" into "what should already be on their device by the time they open the app." Different question, different architecture, and a cache-hit rate that matters more than a ranking metric.

---

## Receipts

| Number | What it is |
|---:|---|
| **~480** | tests in VITAL, run by CI on every push |
| **9.6s** | median agent turn — down from 37–57s once I found the routing loop |
| **3.3k** | tokens per turn — down from 12–16k, same fix |
| **≥90%** | routing accuracy gate; the eval fails rather than warns |
| **94.6%** | RoBERTa accuracy using **0.7%** of the parameters, via LoRA |
| **<150ms** | inference latency on that model, FastAPI + Docker |
| **12** | pull requests merged into repositories I don't own |

---

## Open source

| Project | What I changed |
|---|---|
| **[spcl/serverless-benchmarks](https://github.com/spcl/serverless-benchmarks/pull/284)** | AWS Lambda Function URLs as an HTTP trigger, sidestepping API Gateway's 29-second ceiling. ETH Zurich's serverless benchmarking suite — 33 comments of review, and worth every one. |
| **[fossamagna/amplify-backend-vscode](https://github.com/fossamagna/amplify-backend-vscode/pull/675)** | Console URL builders for VerifiedPermissions policies and API Gateway REST APIs, with tests. |
| **[delta-io/kafka-delta-ingest](https://github.com/delta-io/kafka-delta-ingest/pull/222)** | Dropped the direct `dynamodb_lock` dependency now that `deltalake` handles S3 locking internally via `S3DynamoDbLogStore`. *Approved, in review.* |

Plus merged fixes to `scorbo2/swing-extras`, `abduznik/myip-obsidian`, `DakotaB75/developer-solutions-lab`, and `philippeabraxas-jpg/Responsible-Alliance-Protocol`.

---

## Toolkit

| | |
|---|---|
| **Languages** | Python · TypeScript · JavaScript · Rust · SQL |
| **Agents & AI** | LangGraph · LangChain · Vertex AI · PyTorch · LoRA · model-graded evals |
| **Backend** | FastAPI · Django REST · Node · SSE · async Python |
| **Data & streaming** | Kafka · Spark · Delta Lake · Triton Inference Server |
| **Cloud** | AWS (Lambda, SQS, DynamoDB, SAM/CDK, OpenSearch) · GCP (Cloud Run, Vertex) · Vercel |
| **Infra** | Docker · Kubernetes · GitHub Actions · Prometheus · Grafana |

---

<p align="center">
I run technical workshops, I read more papers than I finish, and I have opinions about coffee in this city that I will not be defending in writing.
</p>

<p align="center">
<a href="https://sharayu.dev">sharayu.dev</a> · <a href="https://linkedin.com/in/sharayu-rasal-70a030213">LinkedIn</a> · <a href="mailto:srr10019@nyu.edu">srr10019@nyu.edu</a>
</p>

<p align="center"><sub>Open to new-grad software engineering roles in NYC.</sub></p>
