<div align="center">

# Mattral

**ML Engineer · Distributed Training · LLM Systems · Computer Vision**

*I build things that work at scale  -- and try to understand why they work at all.*

<br>

[![Profile views](https://komarev.com/ghpvc/?username=mattral&color=blueviolet&style=flat-square&label=Profile+views)](https://github.com/Mattral)
[![GitHub followers](https://img.shields.io/github/followers/mattral?style=flat-square&color=blueviolet&label=Followers)](https://github.com/Mattral?tab=followers)

</div>

---

## What I actually do

I work in the gap between ML research and production engineering  -- where the math is clean and the cluster is not.

Day-to-day: Propriety work, distributed training infrastructure, LLM safety systems, and the occasional Triton kernel when PyTorch decides it's done for the day. Most of my production work lives in private repos  -- this is where the side projects land.

**Things I care about technically**
- Large-scale pre-training infrastructure  -- MoE routing, fault-tolerant checkpointing, tensor/pipeline parallelism
- LLM safety and observability  -- keeping models honest at inference time
- The hardware-software boundary: SIMD, CUDA, kernel-level optimization
- Novel architectures worth *deploying*, not just benchmarking

**Things I care about less technically**
- Code that impresses interviewers but breaks on week two
- Benchmarks that only win on synthetic data
- Documentation that describes the happy path and nothing else

---

## Selected work

> Most projects here are built to solve a real problem, not to fill a portfolio.
> I'd rather have three things that work than ten that look good.

| Project | What it is | Status |
|:---|:---|:---|
| [Composed-MoE-Engine](https://github.com/Mattral/Composed-Mixture-of-Experts-Engine) | Sparse MoE training runtime  -- Triton Top-K routing, DP+EP+TP distributed, async sharded checkpointing, TorchElastic fault recovery | Active |
| [GuardRail Studio](https://github.com/Mattral/GuardRail-Studio) | LLM firewall  -- sub-10ms p99 inline guardrails, DistilRoBERTa + ONNX + Triton, continuous drift detection and LoRA retraining | Active |
| [KANX](https://github.com/Mattral/KANX) | Production KAN library  -- TF + PyTorch + ONNX, Docker/K8s ready, published to PyPI | Active · `pip install kanx` |
| [RLHF-PPO-DPO](https://github.com/Mattral/Improving-LLM-Models-with-RLHF-PPO-DPO) | Modular RLHF framework  -- PPO and DPO, reward model training, policy optimization | Active |
| [SIMD Microkernels](https://github.com/Mattral/SIMD-Microkernels-for-ML-Workloads) | C++ AVX2 kernels for ML primitives  -- tiled GEMM, vectorized GeLU, Python bindings | Experimental |
| [ML from scratch](https://github.com/Mattral/ML-AI-Algorithms-from-scratch) | NumPy-only implementations of supervised, unsupervised, RL, and Bayesian methods | Reference |

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

Most of my interesting work happens in private repositories -- production systems at a scale where open-sourcing isn't an option. This GitHub is a public window, not the full picture.

That said: the repos here are held to the same standard as the private ones  -- CI, tests, type checking, real benchmarks. If something is experimental, the README says so. I'd rather write documentation that admits limitations than one that hides them.

I'm particularly interested in the fault-tolerance problems that only appear at real cluster scale, the latency-accuracy tradeoffs in LLM safety systems, and the open question of whether KAN-style architectures will find their niche or stay a curiosity.

---

## Currently

- **Working on:** fixing MoE engine chaos scenario A  -- sudden node failure under expert resharding
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
>
</div>

---

## Stats

<div align="center">

<table>
  <tr>
    <td>
      <img src="https://readmestats.999857.xyz/api?username=mattral&show_icons=true&locale=en&theme=dark&hide_border=true" />
    </td>
    <td>
      <img src="https://streak-stats.demolab.com/?user=mattral&theme=gotham&hide_border=true" />
    </td>
  </tr>
</table>

</div>

---

## 🎶 Current frequency

<div align="center">

<a href="https://spotify-github-profile.kittinanx.com/api/view?uid=313hy6lpcgjlbdfxwmn4mucx576e&cover_image=true&theme=default&show_offline=false&background_color=121212&interchange=false&profanity=true&bar_color_cover=false">
  <img src="https://spotify-github-profile.kittinanx.com/api/view?uid=313hy6lpcgjlbdfxwmn4mucx576e&cover_image=true&theme=default&show_offline=false&background_color=121212&interchange=false&profanity=true&bar_color_cover=false" alt="Spotify now playing" />
</a>

</div>

---

## Rhythm & motion

<div align="center">

<img alt="contribution snake" src="https://github.com/Mattral/mattral/blob/output/github-contribution-grid-snake-dark.svg" />

<br><br>

<img src="profile-3d-contrib/profile-night-view.svg" alt="3D contribution graph" width="100%" />

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

> Outside of work I'm usually reading something I don't fully understand yet,
> listening to music that has no business being that good, and occasionally wondering if the model actually converged or if I just got lucky. I like working with people who say "I don't know" without embarrassment and argue about architecture in good faith.

<div align="center">

**[mattralminn@gmail.com](mailto:mattralminn@gmail.com)** 

<br>

*Open to interesting conversations about distributed training, LLM infrastructure,*
*or any hard ML systems problem worth losing sleep over.*

</div>
