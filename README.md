<div align="center">

# Mattral

**ML Engineer · Distributed Training · LLM Systems · Computer Vision**

*I build things that work at scale -- and try to understand why they work at all.*

</div>

---

## What I actually do

I work in the space between clean research ideas and the messy reality of clusters that fail, data that drifts, and models that need to stay honest in production.

Day-to-day: cloud-scale ML infrastructure at a hyperscaler, distributed training systems, fault-tolerant checkpointing, LLM safety layers, and the occasional low-level kernel when something needs to be faster or more reliable. The majority of that work lives in private repositories. What you see here are the side projects I chose to open-source because they felt worth sharing.

**Things I care about technically**
- Large-scale pre-training infrastructure -- MoE routing, fault-tolerant checkpointing, tensor/pipeline parallelism
- LLM safety and observability -- keeping models (and the agents built on them) honest at inference time
- The hardware-software boundary: SIMD, CUDA, kernel-level optimization
- Novel architectures worth *deploying*, not just benchmarking

**Things I care about less technically**
- Code that impresses interviewers but breaks on week two
- Benchmarks that only win on synthetic data
- Documentation that describes the happy path and nothing else

---

## Selected work
> Most of these exist because I needed to solve something concrete.
> I'd rather have a few things that are real than many that just look good on a profile.

| Project | What it is | Where it actually stands |
|---------|------------|---------------------------|
| **[Composed-MoE-Engine](https://github.com/Mattral/Composed-Mixture-of-Experts-Engine)** -- [write-up →](https://medium.com/@mattral-lifelong-learning/i-built-a-fault-tolerant-moe-training-engine-from-scratch-heres-what-i-learned-explained-simply-4df162f96e3a) | Training runtime for large Mixture-of-Experts models at hyperscale. Fused Triton top-k router, composable 4D parallelism (DP+EP+TP+PP), strict forward-pass invariants, elastic fault tolerance, async two-tier checkpointing with automatic expert resharding, chaos testing. | Validated on real hardware, not just simulated: **80.1× (T4)** and **58.7× (A100)** kernel speedup, **348 tests**, three hardware-only bugs found and documented. Multi-GPU (8×A100/8×H100) validation in progress. [![Cite](https://img.shields.io/badge/Cite-DOI-brightgreen?style=flat&logo=readthedocs&logoColor=white)](https://doi.org/10.5281/zenodo.20688837) |
| **[KANX](https://github.com/Mattral/KANX)** -- [write-up →](https://medium.com/@mattral-lifelong-learning/i-rebuilt-kan-networks-for-production-what-i-learned-391fd55914e0) | Kolmogorov-Arnold Networks library with PyTorch + TensorFlow backends, verified ONNX export, Docker + Kubernetes + Helm support, FastAPI serving. | `pip install kanx` · **5,000+ downloads** [![Downloads](https://img.shields.io/pepy/dt/kanx?style=flat&color=F87171)](https://pepy.tech/project/kanx) [![Cite](https://img.shields.io/badge/Cite-DOI-brightgreen?style=flat&logo=readthedocs&logoColor=white)](https://doi.org/10.5281/zenodo.20615396) |
| **[guardrail-rs](https://github.com/Mattral/guardrail-rs)** -- [write-up →](https://medium.com/@mattral-lifelong-learning/building-guardrail-rs-a-production-llm-security-proxy-in-rust-and-six-bugs-that-taught-me-more-dba8713cf6b3) | Zero-Python LLM security layer written in Rust. Reverse-proxy that blocks prompt injection, redacts PII, and enforces policy with sub-millisecond overhead. Fails open by design, hot-reloadable config, Docker/K8s ready. | Active. Six real bugs found and written up honestly -- see the write-up. Complements [GuardRail Studio](https://github.com/Mattral/GuardRail-Studio). |
| **[FlashSpec](https://github.com/Mattral/FlashSpec)** -- [write-up →](https://medium.com/@mattral-lifelong-learning/i-built-speculative-decoding-from-a-scratch-heres-what-actually-broke-370cd7f7bb1f) | Adaptive speculative decoding engine with online bandit draft selection and Triton-optimised on-device verification. Preserves target distribution exactly. | `pip install flashspec` [![Downloads](https://img.shields.io/pepy/dt/flashspec?style=flat&color=F87171)](https://pepy.tech/project/flashspec) [![Cite](https://img.shields.io/badge/Cite-DOI-brightgreen?style=flat&logo=readthedocs&logoColor=white)](https://doi.org/10.5281/zenodo.20766119) |
| **[mcp-reliable](https://github.com/Mattral/mcp-reliable)** | Runtime observability and reliability for the MCP ecosystem -- watches MCP servers *while they're running*: health checks, a traffic-observing proxy, schema/output drift detection, webhook + Slack alerting, and an agent-facing MCP interface so an agent can query its own tool reliability directly. CLI + REST API + dashboard, SQLite storage. | **v1.0.0** · **195 tests, none mocked at the protocol level** · architecture fully documented via ADRs. |
| **[ReliableAgent](https://github.com/Mattral/ReliableAgent)** | Reliability-first orchestration framework for agentic systems. Plan → execute → critique → replan loop with guardrails at every boundary, full trajectory reconstruction, checkpoint/resume, quantitative reliability metrics. | v0.2.0 (June 19, 2026) · **140 tests** |
| **[production-vlm-engineering](https://github.com/Mattral/production-vlm-engineering)** | Reproducible pipelines for modern multimodal vision systems: efficient VLM adaptation, embedding-space drift detection, edge inference, robustness & safety. | Active. |
| **[RAG-Multimodal-Financial-Doc-Analysis-and-Recall](https://github.com/Mattral/RAG-Multimodal-Financial-Doc-Analysis-and-Recall)** | Multimodal RAG system for financial documents -- hybrid retrieval, VLM chart understanding, numeric grounding, full observability + CI-gated evaluation. | Active, finance-domain focused. |
| **[PromptCanary](https://github.com/Mattral/promptcanary)** -- [write-up →](https://medium.com/@mattral-lifelong-learning/we-built-promptcanary-to-detect-silent-llm-drift-heres-what-building-it-actually-taught-us-396478713d66) | Detects silent LLM drift. [<img src="https://img.shields.io/badge/Open_in_Colab-Notebooks-7C3AED?style=flat&logo=googlecolab&logoColor=white" alt="Open Notebooks in Colab" width="120">](https://github.com/Mattral/PromptCanary/tree/main/notebooks) | [v0.2.2](https://github.com/Mattral/PromptCanary/releases/tag/v0.2.2) |


---

## Also digging into

Not everything is a shipped tool -- some of it is just a question I wanted a real answer to.

- **Does fine-tuning break a transformer's copy mechanism?** [Write-up →](https://medium.com/@mattral-lifelong-learning/what-i-learned-studying-whether-fine-tuning-breaks-a-transformers-copy-mechanism-31700e58f3aa)

---

## Selected Open Source Contributions

| Project       | Status                  | What was fixed / improved                                      | Link |
|---------------|-------------------------|----------------------------------------------------------------|------|
| **Triton**    | Merged                  | Fixed NaN handling in `tl.argmin`/`tl.argmax` (`tie_break_left=False`) in the interpreter so it matches JIT behavior | [PR #10699](https://github.com/triton-lang/triton/pull/10699) |
| **Megatron-LM** | Merged                | Fixed crash in `get_grad_norm_fp32` when gradient list is empty (common with frozen layers / tensor parallelism) | [PR #5530](https://github.com/NVIDIA/Megatron-LM/pull/5530) |
| **TensorFlow** | Approved by reviewers | `tf.experimental.numpy.swapaxes` now raises clear error on out-of-bounds axis instead of silent normalization or opaque XLA errors | [PR #122544](https://github.com/tensorflow/tensorflow/pull/122544) |

---

## Stack

Not a comprehensive list. Just what I actually reach for.

**Training & inference** &nbsp;
`PyTorch` `TensorFlow` `Triton` `ONNX` `TensorRT` `FSDP2` `TorchElastic`

**LLM ecosystem** &nbsp;
`Transformers` `PEFT / LoRA` `vLLM` `LangChain` `FastAPI` `Triton Inference Server`

**Distributed & infra** &nbsp;
`NCCL` `Kubernetes` `Helm` `Terraform` `Airflow` `Ray`

**Observability** &nbsp;
`Prometheus` `Grafana` `OpenTelemetry` `Weights & Biases`

**Low-level** &nbsp;
`C++` `AVX2 / SIMD` `CUDA` `pybind11`

**Data** &nbsp;
`PostgreSQL` `Qdrant` `MongoDB` `Spark` `Dask`

---

## A few honest notes

Most of my interesting work happens in private repositories -- production systems at cloud scale where open-sourcing isn't an option. This GitHub is a public window, not the full picture.

That said: the repositories here are written to the same standard I use privately: tests, type checking, CI, real (if limited) benchmarks, and documentation that tries to admit what doesn't work yet. When something is experimental or incomplete, the README says so.

I'm especially interested in the kinds of failures that only appear at real cluster scale, the practical trade-offs in LLM safety systems, and whether architectures like KANs will eventually find meaningful production use cases.

My path into this wasn't linear -- it started in mechatronics, building things with real sensors, actuators, and control loops that fail in ways no unit test catches, and later working on ML systems within offshore energy's integrated control and safety systems, where a silent failure has real consequences. That's the actual root of the reliability obsession above, not something picked up from a style guide.

---

## Currently

- **Working on:** the MoE engine's chaos scenario A -- sudden node failure under expert resharding, currently recovering ~85% of the time
- **Reading:** the Megatron-LM codebase and the FlexAttention paper
- **Thinking about:** whether MFU tracking gives you enough signal to catch silent training degradation early

---

## Problem-solving

<div align="center">

<table>
  <tr>
    <td align="center">
      <img src="https://leetcard.jacoblin.cool/MattralDontGiveUp?theme=dark&font=Yuji%20Syuku&hide_border=true" />
    </td>
  </tr>
</table>

>
> *Algorithms are how I warm up. Systems are where I live.*
>

<br><br>
| | |
|:--:|:--:|
| <video src="https://github.com/user-attachments/assets/0aa09936-7d49-463b-8a9d-7389ad4626c3" width="480" controls loop muted playsinline></video> | <img src="profile-3d-contrib/profile-night-view.svg" alt="3D contribution graph" width="100%" /> |
<!-- https://github.com/user-attachments/assets/0d3282d2-809f-4a47-a5c3-deb43e249453 -->
<!-- img src="profile-3d-contrib/profile-night-view.svg" alt="3D contribution graph" width="100%" /> -->
</div>

---

## On the equation that changed everything

<div align="center">

$$\mathbf{h}_t = \sigma\!\left(\mathbf{W}_h\,\mathbf{h}_{t-1} + \mathbf{W}_x\,\mathbf{x}_t + \mathbf{b}\right)$$

*The idea that a machine could hold memory across time --*
*that the past could shape the present through nothing more than a weight matrix --*
*was the moment I understood why this field is worth a lifetime.*

*The equation is simple. What it implies is not.*

</div>

---

## 🎶 Current frequency

<div align="center">

<a href="https://spotify-github-profile.kittinanx.com/api/view?uid=313hy6lpcgjlbdfxwmn4mucx576e&cover_image=true&theme=default&show_offline=false&background_color=121212&interchange=true&profanity=false&hide_remaster=false&bar_color_cover=false">
  <img src="https://spotify-github-profile.kittinanx.com/api/view?uid=313hy6lpcgjlbdfxwmn4mucx576e&cover_image=true&theme=default&show_offline=false&background_color=121212&interchange=true&profanity=false&hide_remaster=false&bar_color_cover=false" alt="Spotify now playing" />
</a>

</div>

---

> Outside of work I'm usually reading something I don't fully understand yet,
> listening to music that has no business being that good, and occasionally wondering if the model actually converged or if I just got lucky. I like working with people who say "I don't know" without embarrassment and argue about architecture in good faith.

<div align="center">

**[mattralminn@gmail.com](mailto:mattralminn@gmail.com)**

<br>

*Open to interesting conversations about distributed training, LLM infrastructure,*
*or any hard ML systems problem worth losing sleep over.*

</div>
