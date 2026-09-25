<p align="center">
<img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=500&size=21&duration=2600&pause=900&color=2DA44E&center=true&vCenter=true&width=800&height=60&lines=%24+whoami;sharayu+rasal;%24+cat+~%2F.what_i_actually_do;agents%2C+and+checking+whether+they+were+right;%24+ls+~%2Fcurrent;vital-agent%2F++vision-pipeline%2F++smartcache-ai%2F;%24+_" alt="terminal" />
</p>

<h1 align="center">Sharayu Rasal</h1>

<p align="center"><b>Software engineer in New York. I build agent systems, and I spend most of my time on whether their output is actually right.</b></p>

<p align="center">
<a href="https://sharayu.dev">sharayu.dev</a> · <a href="https://linkedin.com/in/sharayu-rasal-70a030213">LinkedIn</a> · <a href="mailto:srr10019@nyu.edu">Email</a> · <a href="https://vital-agent.vercel.app">VITAL, live</a>
</p>

---

<!-- PICTURE SLOT: when the illustration is ready, wrap this About section in a two-column
     HTML table (text left, <img width="300"> right) so it sits alongside instead of above. -->

## About

CS master's from New York University. I write agent systems, and the part I have gotten stubborn about is proving that they work.

That looks less impressive than it sounds. A turn in VITAL (an app I'm currently building) used to take somewhere between 37 and 57 seconds and burn 12 to 16 thousand tokens, and for about a week I assumed that was just what a six-agent graph costs. It was not. The router was looping, and I only caught it because I had traces worth reading. The same fix took it to 9.6 seconds and 3.3k tokens. Routing, crisis detection, memory retrieval and answer quality all have evals now, and routing fails the build under 90%, because a warning is something I would have taught myself to scroll past by week three.

The other habit is writing things down while I still remember why. My vision pipeline carries a `DECISIONS.md` with the calls I made and two I would now undo, which is a less fun file to write than it sounds. And on a side project I keep one test whose only job is to catch a redaction leak, so every so often I sabotage the code on purpose to confirm it still fails. Otherwise I am just trusting a green check.

The tidy version of my background lives on [sharayu.dev](https://sharayu.dev) and [LinkedIn](https://linkedin.com/in/sharayu-rasal-70a030213). This page is closer to the working notes.

---

## What I'm building

### VITAL, a multi-agent life copilot
**[Live app](https://vital-agent.vercel.app)** · **[Code](https://github.com/Sharayu1418/vital-agent)**
`LangGraph` `Vertex AI` `FastAPI` `Next.js 15` `~480 tests`

Six specialized agents on a stateful graph. Sleep, energy, weather, places and interests go in. What comes out is a plan you have to approve before anything touches your calendar.

The approval is not a prompt instruction. The node that writes to your calendar has exactly one inbound edge, and that edge comes from the approval step, so there is no path a prompt injection could take to reach it. I would rather enforce that in the shape of the graph than ask a model nicely.

The energy forecast runs Borbély's two-process model, keyed to your own wake time, and reports a confidence that drops when it has nothing to go on. With no history it says 10% and tells you the curve is not yours yet. That number was harder to ship than a fake one, because an honest low confidence looks like a bug to anyone who has not read the code.

### Real-time multi-camera vision pipeline
**[Code](https://github.com/Sharayu1418/RealTimeComputerVisionPipeline)**
`Kafka` `Triton` `YOLOv8 ONNX` `Prometheus/Grafana`

`RTSP → Kafka → Triton (dynamic batching, gRPC) → tracking → WebSocket dashboard`, with metrics wired in from the first commit.

I built it to find out where a streaming CV system actually gives out under load. The model was never the problem. It gives out at letterbox preprocessing, at the size of the batch window, and at a question nobody asks until it happens: what should the rest of the pipeline do when one camera simply stops answering. Honestly, a good share of the difficulty was getting Triton, Docker and WSL2 to coexist on Windows, which appears in no architecture diagram anywhere. Tradeoffs are in `DECISIONS.md`.

### SmartCache AI, offline content for commutes
**[Code](https://github.com/Sharayu1418/SmartCache-AI)**
`Django REST` `Celery` `Redis` `Channels` `React` `AutoGen` `Ollama`

Pulls podcasts, articles and videos onto a device *before* the commute, so the content is there when the network is not. Team project, seven sprints.

A Celery job ingests feeds on a schedule and pushes media to object storage. A team of AutoGen agents running against a local Ollama model then decides what to pull down, streaming progress to the browser over Django Channels. The agents do the orchestration; the ranking underneath them is still deterministic SQL. I am replacing that with embeddings and cosine similarity over the cached items, which is where it genuinely stands right now.

---

## Receipts

| Number | What it is |
|---:|---|
| **~480** | tests in VITAL, run by CI on every push |
| **9.6s** | median agent turn, down from 37 to 57 seconds once I found the routing loop |
| **3.3k** | tokens per turn, down from 12 to 16k, same fix |
| **≥90%** | routing accuracy gate. The build fails under it |
| **94.6%** | RoBERTa accuracy using **0.7%** of the parameters, via LoRA |
| **<150ms** | inference latency on that model, FastAPI and Docker |
| **12** | pull requests merged into repositories I do not own |

---

## Open source

| Project | What I changed |
|---|---|
| **[spcl/serverless-benchmarks](https://github.com/spcl/serverless-benchmarks/pull/284)** | AWS Lambda Function URLs as an HTTP trigger, which gets around API Gateway's 29 second ceiling. ETH Zurich's serverless benchmarking suite. The review ran 33 comments deep before it landed. |
| **[fossamagna/amplify-backend-vscode](https://github.com/fossamagna/amplify-backend-vscode/pull/675)** | Console URL builders for VerifiedPermissions policies and API Gateway REST APIs, with tests. |
| **[delta-io/kafka-delta-ingest](https://github.com/delta-io/kafka-delta-ingest/pull/222)** | Dropped the direct `dynamodb_lock` dependency now that `deltalake` handles S3 locking internally via `S3DynamoDbLogStore`. *Approved with auto-merge armed, still open behind a rebase.* |

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

The fuller breakdown, plus the research and coursework side of it, is on [sharayu.dev](https://sharayu.dev).

---

<p align="center">
Away from the terminal I run technical workshops, play more board games than is defensible, and lose evenings to Notpron-style puzzle games, which is the same instinct as reading a stack trace with much lower stakes.
</p>

<p align="center">
<a href="https://sharayu.dev">sharayu.dev</a> · <a href="https://linkedin.com/in/sharayu-rasal-70a030213">LinkedIn</a> · <a href="mailto:srr10019@nyu.edu">srr10019@nyu.edu</a>
</p>

<p align="center"><sub>Open to new-grad software engineering and AI engineering roles in NYC.</sub></p>
