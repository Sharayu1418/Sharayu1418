[profile-README.md](https://github.com/user-attachments/files/31891880/profile-README.md)
# Hello, I'm Sharayu Rasal
### 👨‍💻 Building Intelligent & Scalable Systems! 💡

Software Engineer | Full-Stack Developer | Applied AI Engineer | Cloud & DevOps Enthusiast
<br>
Python • Django • React • FastAPI • PyTorch • AWS • Docker • Kubernetes

<br>
<h1 align="center">Sharayu Rasal</h1>

<p align="center">
  <b>I build the systems around AI models not just the part that calls the model.</b>
</p>

<p align="center">
  <a href="https://sharayu.dev">sharayu.dev</a> ·
  <a href="https://linkedin.com/in/sharayu-rasal-70a030213">LinkedIn</a> ·
  <a href="mailto:srr10019@nyu.edu">Email</a>
</p>

---

CS master's from NYU, based in New York. Most of what I enjoy sits one layer below the demo — the router that decides which agent answers, the queue that absorbs a camera dropping offline, the eval that notices an answer got worse before a user does.

The two things that taught me the most were both bugs. A supervisor that couldn't tell an agent had already replied, so it re-routed the same message until a guard fired — 5× the latency, invisible until I measured it. And a TSV read through a legacy codepage that quietly renamed a coffee brand in a production catalog, which is how I learned that "the data looks fine" and "the data is fine" are different claims.

**Currently building:** [VITAL](https://github.com/Sharayu1418/vital-agent), and pulling its eval harness out into something other people can run.

---

## Featured projects

### VITAL — a multi-agent life copilot
**[Live app](https://vital-agent.vercel.app) · [Code](https://github.com/Sharayu1418/vital-agent)**

Six specialized agents on a LangGraph state machine, Gemini on Vertex AI, FastAPI with SSE streaming, Next.js 15 front end. Sleep, energy, weather, places and interests go in; a plan you have to approve comes out.

**~480 tests · CI on every push · routing eval gated at ≥90%**

The part I'd defend in an interview: the node that commits a plan to your calendar has exactly one inbound edge, and it comes from the human approval resume. It isn't a rule the model is asked to follow — it's a path that does not exist, so no prompt injection can reach it. Guarantees belong in topology, not in prompts.

The other part: the energy forecast is Borbély's two-process model with constants solved numerically and pinned by tests, and it reports a confidence that degrades honestly. With no data it says 10% and tells you the curve isn't yours.

---

### Real-time multi-camera vision pipeline
**[Code](https://github.com/Sharayu1418/RealTimeComputerVisionPipeline)**

RTSP → Kafka → Triton Inference Server (YOLOv8 ONNX, dynamic batching, gRPC) → tracking → WebSocket dashboard, with Prometheus and Grafana watching it.

**Multi-stream · GPU-batched inference · observability from day one**

Built to find out where a streaming CV system actually breaks, which turned out to be nowhere near the model. Letterbox preprocessing, batch windows, and what happens to the whole pipeline when one camera stops answering — the decisions are written down in `DECISIONS.md` rather than lost.

---

### SmartCache AI
**[Code](https://github.com/Sharayu1418/SmartCache-AI)**

Django REST + React, with a Redis/Celery pipeline running a cosine-similarity recommender that pre-caches content to S3 before a user asks for it.

**Built for the case where the network is the bottleneck, not the model**

Recommendation systems usually assume the content is one request away. This one assumes it isn't — which changes the problem from "what should we show" to "what should already be here."

---

## Open source

Twelve merged pull requests into repositories I don't own:

| Project | What I changed |
|---|---|
| **[spcl/serverless-benchmarks](https://github.com/spcl/serverless-benchmarks/pull/284)** | AWS Lambda Function URLs as an HTTP trigger alternative, avoiding API Gateway's 29-second ceiling. ETH Zurich's serverless benchmarking suite — 33 comments of review, and worth every one. |
| **[fossamagna/amplify-backend-vscode](https://github.com/fossamagna/amplify-backend-vscode/pull/675)** | Console URL builders for VerifiedPermissions policies and API Gateway REST APIs, with tests. |
| **[DiyoWater/diyo-backend](https://github.com/DiyoWater/diyo-backend/pull/186)** | Catalog patch tooling: dry-run by default, `--apply` to write, tests that prove the diff before it touches a row. |
| **[delta-io/kafka-delta-ingest](https://github.com/delta-io/kafka-delta-ingest/pull/222)** | Removed the direct `dynamodb_lock` dependency now that `deltalake` handles S3 locking internally via `S3DynamoDbLogStore`. *(Approved, in review.)* |

Plus merged fixes to `scorbo2/swing-extras`, `abduznik/myip-obsidian`, `DakotaB75/developer-solutions-lab`, and `philippeabraxas-jpg/Responsible-Alliance-Protocol`.

---

## Toolkit

| | |
|---|---|
| **Languages** | Python, TypeScript, JavaScript, Rust, SQL |
| **AI / agents** | LangGraph, LangChain, Vertex AI, PyTorch, LoRA, model-graded evals |
| **Backend** | FastAPI, Django REST, Node, SSE, async Python |
| **Data & streaming** | Kafka, Spark, Hadoop, Delta Lake, Triton Inference Server |
| **Cloud** | AWS (Lambda, SQS, DynamoDB, SAM/CDK, OpenSearch), GCP (Cloud Run, Vertex), Vercel |
| **Infra** | Docker, Kubernetes, GitHub Actions, Prometheus, Grafana, Terraform-adjacent IaC |
| **Frontend** | React, Next.js, Tailwind |

---

## Elsewhere

I run technical workshops, I read more papers than I finish, and I have opinions about coffee in this city that I will not be defending in writing.

<p align="center">
  <a href="https://sharayu.dev">sharayu.dev</a> ·
  <a href="https://linkedin.com/in/sharayu-rasal-70a030213">LinkedIn</a> ·
  <a href="mailto:srr10019@nyu.edu">srr10019@nyu.edu</a>
</p>

<p align="center"><sub>Open to new-grad software engineering roles in NYC.</sub></p>

I'm a **Computer Science Master's student at the New York University** with a passion for building full-stack applications and scalable, production-ready AI systems. I thrive on solving real-world problems at the intersection of distributed systems, MLOps, and product engineering.

<br>

- 🚀 &nbsp; I love building and deploying end-to-end AI/ML applications.
- ☁️ &nbsp; I'm passionate about cloud infrastructure and building efficient, scalable backends.
- 💬 &nbsp; Actively seeking **Software Engineer (SDE) & Applied AI** new grad roles for 2026.

---

## Featured Projects
I believe in learning by building. Here are a few projects I've built from the ground up.

<table>
  <tr>
    <td width="33%" valign="top">
      <h3 align="center">SmartCache AI</h3>
      <p>A full-stack AI content recommender for users in low-connectivity areas. I built the entire system, including a <b>Django REST</b> backend, <b>React</b> frontend, and a <b>Redis/Celery</b> task pipeline to run a cosine-similarity model and proactively cache content on <b>AWS S3</b>.</p>
      <p align="center">
        <code>Python</code> <code>Django</code> <code>React</code> <code>PostgreSQL</code> <code>Redis</code> <code>Celery</code> <code>AWS</code>
      </p>
      <p align="center">
        <a href="https://github.com/Sharayu1418/SE-Team6-Fall2025" target="_blank"><b>View on GitHub &rarr;</b></a>
      </p>
    </td>
    <td width="33%" valign="top">
      <h3 align="center">Efficient NLP: LoRA-RoBERTa</h3>
      <p>Proved that high-accuracy AI can be highly efficient. I fine-tuned a RoBERTa model using <b>LoRA</b> (94.6% accuracy with 0.7% of parameters). I then architected a production-ready <b>FastAPI</b> inference stack, containerized it with <b>Docker</b>, and delivered sub-150ms predictions.</p>
      <p align="center">
        <code>Python</code> <code>PyTorch</code> <code>LoRA</code> <code>FastAPI</code> <code>Docker</code> <code>MLOps</code>
      </p>
      <p align="center">
        <a href="https://github.com/Sharayu1418/LoRA-Fine-Tuning" target="_blank"><b>View on GitHub &rarr;</b></a>
      </p>
    </td>
    <td width="33%" valign="top">
      <h3 align="center">Multimodal Depression Detection</h3>
      <p>A real-time screening platform that analyzes complex, multimodal data. The system combines insights from text (Logistic Regression), physiological signals (1D CNN for HRV), and facial emotions (CNN). I engineered the data-processing pipelines for low-latency inference.</p>
      <p align="center">
        <code>Python</code> <code>TensorFlow</code> <code>OpenCV</code> <code>Scikit-learn</code> <code>FastAPI</code>
      </p>
      <p align="center">
        <a href="https://github.com/Sharayu1418/multimodal-mental-health" target="_blank"><b>View on GitHub &rarr;</b></a>
      </p>
    </td>
  </tr>
</table>

---

## My Toolkit
### Languages
<p>
  <img alt="Python" src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white">
  <img alt="JavaScript" src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black">
  <img alt="TypeScript" src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white">
  <img alt="C++" src="https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=cplusplus&logoColor=white">
  <img alt="SQL" src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white">
</p>

### Backend & APIs
<p>
  <img alt="Django" src="https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white">
  <img alt="FastAPI" src="https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white">
  <img alt="Node.js" src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=node.js&logoColor=white">
  <img alt="Flask" src="https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white">
  <img alt="REST APIs" src="https://img.shields.io/badge/REST_APIs-027E8A?style=for-the-badge&logo=swagger&logoColor=white">
</p>

### Frontend
<p>
  <img alt="React" src="https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black">
  <img alt="HTML5" src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white">
  <img alt="CSS3" src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white">
  <img alt="Bootstrap" src="https://img.shields.io/badge/Bootstrap-7952B3?style=for-the-badge&logo=bootstrap&logoColor=white">
</p>

### AI / ML / Data
<p>
  <img alt="PyTorch" src="https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white">
  <img alt="TensorFlow" src="https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white">
  <img alt="HuggingFace" src="https://img.shields.io/badge/HuggingFace-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black">
  <img alt="Scikit-learn" src="https://img.shields.io/badge/Scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white">
  <img alt="OpenCV" src="https://img.shields.io/badge/OpenCV-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white">
  <img alt="Pandas" src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white">
</p>

### Cloud & DevOps
<p>
  <img alt="AWS" src="https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white">
  <img alt="Docker" src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white">
  <img alt="Kubernetes" src="https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white">
</p>

### Databases & Caching
<p>
  <img alt="PostgreSQL" src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white">
  <img alt="MongoDB" src="https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white">
  <img alt="MySQL" src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white">
  <img alt="Redis" src="https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white">
</p>

---

## ⚡ Fun Fact

> When I'm not coding, you can find me leading technical workshops or trying to find the best cup of coffee in NYC!

---

## Let's Connect
<p align="center">
  <a href="https://linkedin.com/in/sharayu-rasal-70a030213" target="_blank">
    <img alt="LinkedIn" src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white">
  </a>
  <a href="mailto:srr10019@nyu.edu" target="_blank">
    <img alt="Email" src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white">
  </a>
</p>
