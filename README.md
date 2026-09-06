<div align="center">

# Mattral

**ML Systems Engineer · Distributed Training · LLM Infrastructure · Multimodal Systems**

*I build systems that work at scale -- and try to understand why they fail when they do.*

</div>

---

## What I actually do

I work in the space between clean research ideas and the messy reality of clusters that fail, data that drifts, and models that need to stay honest in production.

Day-to-day: cloud-scale ML infrastructure, distributed training systems, fault-tolerant checkpointing, LLM safety and observability layers, and the occasional low-level kernel when something needs to be faster or more reliable. The majority of that work lives in private repositories. What you see here are the side projects I chose to open-source because they felt worth sharing.

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

## Upstream contributions

These are small but high-signal fixes in core infrastructure:

| Project | Status | What was fixed | Link |
|---------|--------|----------------|------|
| **Triton** | Merged | Fixed NaN handling in `tl.argmin` / `tl.argmax` so interpreter matches JIT behavior | [PR #10699](https://github.com/triton-lang/triton/pull/10699) · [write-up](https://pub.towardsai.net/inside-pr-10699-how-a-missing-elif-let-nan-win-in-tritons-interpreter-0f6321531d7f?source=friends_link&sk=dfbf6c7f9762f48e30f56085bfe17d40) |
| **TensorFlow** | Merged | `tf.experimental.numpy.swapaxes` now raises a clear error on out-of-bounds axis instead of silent normalization or opaque XLA errors | [PR #122544](https://github.com/tensorflow/tensorflow/pull/122544) · [write-up](https://www.towardsdeeplearning.com/same-input-two-outcomes-debugging-a-silent-eager-xla-divergence-in-tensorflow-ee207832e866) |
| **Megatron-LM** | Merged | Fixed crash in `get_grad_norm_fp32` when gradient list is empty (common with frozen layers / tensor parallelism) | [PR #5530](https://github.com/NVIDIA/Megatron-LM/pull/5530) · [write-up](https://blog.devgenius.io/a-silent-crash-in-megatron-lms-gradient-clipping-and-a-reviewer-who-made-my-fix-better-da1a772a38dc) |

---

## Selected work

> I'd rather have a few things that are real than many that just look good on a profile.

| Project | What it is | Where it actually stands |
|---------|------------|--------------------------|
| **[KANX](https://github.com/Mattral/KANX)** | Production-oriented Kolmogorov-Arnold Networks library (PyTorch + TensorFlow + ONNX) | `pip install kanx` · [![Downloads](https://img.shields.io/pepy/dt/kanx?style=flat&color=F87171)](https://pepy.tech/project/kanx) · [Colab](https://colab.research.google.com/github/Mattral/KANX/blob/main/notebooks/quickstart.ipynb) · [write-up](https://blog.devgenius.io/i-rebuilt-kan-networks-for-production-what-i-learned-391fd55914e0) · [DOI](https://doi.org/10.5281/zenodo.20615396) |
| **[Composed-MoE-Engine](https://github.com/Mattral/Composed-Mixture-of-Experts-Engine)** | Fault-tolerant MoE training runtime with fused Triton router, 4D parallelism, elastic recovery, and async checkpointing | **80.1× (T4)** / **58.7× (A100)** kernel speedup · 348 tests · three hardware-only bugs documented · multi-GPU validation in progress · [DOI](https://doi.org/10.5281/zenodo.20688837) |
| **[guardrail-rs](https://github.com/Mattral/guardrail-rs)** | Zero-Python LLM security reverse proxy in Rust (prompt injection, PII redaction, policy enforcement) | Sub-ms overhead · fails open by design · six real bugs written up · [Colab](https://colab.research.google.com/github/Mattral/guardrail-rs/blob/main/examples/notebooks/quickstart_colab.ipynb) · [write-up](https://www.towardsdeeplearning.com/building-guardrail-rs-a-production-llm-security-proxy-in-rust-and-six-bugs-that-taught-me-more-dba8713cf6b3) |
| **[FlashSpec](https://github.com/Mattral/FlashSpec)** | Adaptive speculative decoding with online bandit draft selection and Triton verification | `pip install flashspec` · [![Downloads](https://img.shields.io/pepy/dt/flashspec?style=flat&color=F87171)](https://pepy.tech/project/flashspec) · [notebooks](https://github.com/Mattral/FlashSpec/tree/main/notebooks) |
| **[PromptCanary](https://github.com/Mattral/PromptCanary)** | Detects silent behavioral drift in LLM providers | `pip install promptcanary` · [![Downloads](https://img.shields.io/pepy/dt/promptcanary?style=flat&color=F87171)](https://pepy.tech/project/promptcanary) · [notebooks](https://github.com/Mattral/PromptCanary/tree/main/notebooks) |

---

## Also digging into

Not everything is a shipped tool -- some of it is just a question I wanted a real answer to.

- **Does fine-tuning break a transformer's copy mechanism?** [Write-up →](https://medium.com/towards-artificial-intelligence/what-i-learned-studying-whether-fine-tuning-breaks-a-transformers-copy-mechanism-31700e58f3aa)

---

## Other work

- **[RAG-Multimodal-Financial-Doc-Analysis-and-Recall](https://github.com/Mattral/RAG-Multimodal-Financial-Doc-Analysis-and-Recall)** -- Multimodal RAG for financial documents (hybrid retrieval, VLM chart understanding, numeric grounding)
- **[production-vlm-engineering](https://github.com/Mattral/production-vlm-engineering)** -- Reproducible pipelines for modern multimodal vision systems
- **[mcp-reliable](https://github.com/Mattral/mcp-reliable)** -- Runtime observability for MCP servers (195 tests, none mocked at protocol level)
- **[ReliableAgent](https://github.com/Mattral/ReliableAgent)** -- Reliability-first agent orchestration

---

## Stack

**Training & inference** -- `PyTorch` `TensorFlow` `Triton` `ONNX` `TensorRT` `FSDP2`  
**LLM** -- `Transformers` `PEFT` `vLLM` `FastAPI`  
**Infra** -- `NCCL` `Kubernetes` `Helm` `Ray`  
**Observability** -- `Prometheus` `Grafana` `OpenTelemetry`  
**Low-level** -- `C++` `CUDA` `SIMD` `pybind11`

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
</div>

---

## A few honest notes

Most of my interesting work happens in private repositories. This GitHub is a public window, not the full picture.

The repositories here are written to the same standard I use privately: tests, type checking, CI, real (if limited) benchmarks, and documentation that tries to admit what doesn’t work yet.

My path into this wasn’t linear. It started in mechatronics -- building systems with real sensors, actuators, and control loops that fail in ways no unit test catches -- and later working on ML systems inside industrial control and safety environments, where a silent failure has real consequences. That background is the root of the reliability focus you see in these projects.

---

## Currently

- **Working on:** the MoE engine’s chaos scenario A -- sudden node failure under expert resharding (currently recovering ~85% of the time)
- **Reading:** the Megatron-LM codebase and the FlexAttention paper
- **Thinking about:** whether MFU tracking gives enough signal to catch silent training degradation early

---

## 🎶 Current frequency

<div align="center">

<a href="https://spotify-github-profile.kittinanx.com/api/view?uid=313hy6lpcgjlbdfxwmn4mucx576e&cover_image=true&theme=default&show_offline=false&background_color=121212&interchange=true&profanity=false&hide_remaster=false&bar_color_cover=false">
  <img src="https://spotify-github-profile.kittinanx.com/api/view?uid=313hy6lpcgjlbdfxwmn4mucx576e&cover_image=true&theme=default&show_offline=false&background_color=121212&interchange=true&profanity=false&hide_remaster=false&bar_color_cover=false" alt="Spotify now playing" />
</a>

</div>

---

> Outside of work I’m usually reading something I don’t fully understand yet, listening to music that has no business being that good, and occasionally wondering if the model actually converged or if I just got lucky. I like working with people who say “I don’t know” without embarrassment and argue about architecture in good faith.
