<div align="center">

# Mattral

**ML Systems Engineer · Distributed Training · LLM Infrastructure · Multimodal Systems**

*I build systems that work at scale -- and try to understand why they fail when they do.*

</div>

---

## What I actually do

I work in the space between clean research ideas and the messy reality of clusters that fail, data that drifts, and models that need to stay honest in production.

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
| ------- | ---------- | ------------------------ |
| **[KANX](https://github.com/Mattral/KANX)** | Production-oriented Kolmogorov-Arnold Networks library (PyTorch + TensorFlow + ONNX) | `pip install kanx` · [![Downloads](https://img.shields.io/pepy/dt/kanx?style=flat&color=F87171)](https://pepy.tech/project/kanx) · [Colab](https://colab.research.google.com/github/Mattral/KANX/blob/main/notebooks/quickstart.ipynb) · [write-up](https://blog.devgenius.io/i-rebuilt-kan-networks-for-production-what-i-learned-391fd55914e0) · [DOI](https://doi.org/10.5281/zenodo.20615396) · latest release v0.2.1 |
| **[Composed-MoE-Engine](https://github.com/Mattral/Composed-Mixture-of-Experts-Engine)** | MoE training runtime (research prototype): fused Triton router, 4D parallelism, expert-resharding recovery, async checkpointing | **80.1× (T4)** / **56.0× (A100)** router-kernel forward speedup versus the CPU reference path (no GPU baseline yet) · CPU test suites run on every push (counts in the repo README) · three hardware-only bugs documented · validated on single GPUs (T4, A100) and at 2 ranks · multi-node and 8+ GPU runs open |
| **[filing-qa](https://github.com/Mattral/filing-qa)** | Question answering over financial filings with cited answers (hybrid dense+BM25 retrieval, numeric guardrail, AST-sandboxed calculator; chart extraction not yet tested) | FastAPI + CLI · Helm chart included, not deployed · 119-question golden set · ~30% of questions miss at retrieval · calculation questions are the weakest |
| **[guardrail-rs](https://github.com/Mattral/guardrail-rs)** | Zero-Python LLM security reverse proxy in Rust (prompt injection, PII redaction, policy enforcement) | Regex + PII pipeline adds 5–47 µs on 512 B–8 KB inputs (single local run, pipeline only) · ONNX stages experimental · injection detection measured on a public set (deepset, 263 prompts): pattern rules catch 1.5%, optional ML model 40%; PII detection not yet measured · fails open by default · five crates on crates.io · [Colab](https://colab.research.google.com/github/Mattral/guardrail-rs/blob/main/examples/notebooks/quickstart_colab.ipynb) · [write-up](https://www.towardsdeeplearning.com/building-guardrail-rs-a-production-llm-security-proxy-in-rust-and-six-bugs-that-taught-me-more-dba8713cf6b3) |
| **[FlashSpec](https://github.com/Mattral/FlashSpec)** | Speculative decoding for Hugging Face causal LMs with static-cache CUDA-graph fast path | `pip install flashspec` · [![Downloads](https://img.shields.io/pepy/dt/flashspec?style=flat&color=F87171)](https://pepy.tech/project/flashspec) · v0.3.2 · 1.26–1.67× over compiled HF generate on one T4 (Qwen2.5-1.5B with 0.5B drafter, batch 1, 10 prompts per set) · lossless in float32 CPU tests; fp16 GPU greedy matched on 17 of 20 prompts · still Alpha · bandit draft selection experimental, did not beat the best fixed arm |
| **[simd-ml-kernels](https://github.com/Mattral/simd-ml-kernels)** | Hand-written AVX2/AVX-512/VNNI microkernels for core inference arithmetic | x86-64 only · benchmarked against OpenBLAS, PyTorch and llama.cpp (single thread, mostly one laptop; per-case ratios in the repo) · pre-1.0 (v0.4.0) · educational reference, not a replacement for OpenBLAS, oneDNN or llama.cpp · limitations listed in the README |

---

## Also digging into

Not everything is a shipped tool -- some of it is just a question I wanted a real answer to.

- **Does fine-tuning break a transformer's copy mechanism?** [Write-up →](https://medium.com/towards-artificial-intelligence/what-i-learned-studying-whether-fine-tuning-breaks-a-transformers-copy-mechanism-31700e58f3aa)

---

## Other work

- **[rlpost](https://github.com/Mattral/rlpost)** -- LLM post-training from scratch (SFT, reward model, PPO, DPO); parity-tested against TRL
- **[production-vlm-engineering](https://github.com/Mattral/production-vlm-engineering)** -- Reference scaffold for multimodal vision pipelines (config validation, batching, observability hooks); results are CPU/synthetic proxies
- **[mcp-reliable](https://github.com/Mattral/mcp-reliable)** -- Runtime observability for MCP servers (health, per-tool latency, output-shape drift)
- **[PromptCanary](https://github.com/Mattral/PromptCanary)** -- Detects silent behavioral drift in LLM providers (`pip install promptcanary`)


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

Work I do at my employer is not public. The repositories here are my own projects.

Repository READMEs are being updated to state current status and what has not been validated.

My path into this wasn’t linear. It started in mechatronics -- building systems with real sensors, actuators, and control loops that fail in ways no unit test catches -- and later working on ML systems inside industrial control and safety environments, where a silent failure has real consequences. That background is the root of the reliability focus you see in these projects.

---

## Currently

- **Working on:** the MoE engine’s chaos scenario A -- sudden node failure under expert resharding (recovers in roughly 85% of runs; failures attributed to a Gloo race in containers)
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
