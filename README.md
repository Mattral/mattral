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

I work in the space between clean research ideas and the messy reality of clusters that fail, data that drifts, and models that need to stay honest in production.

Day-to-day: cloud-scale ML infrastructure at a hyperscaler, distributed training systems, fault-tolerant checkpointing, LLM safety layers, and the occasional low-level kernel when something needs to be faster or more reliable. The majority of that work lives in private repositories. What you see here are the side projects I chose to open-source because they felt worth sharing.

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

> Most of these exist because I needed to solve something concrete.  
> I’d rather have a few things that are real than many that just look good on a profile.

| Project | What it is | Status |
|---------|------------|--------|
| [Composed-MoE-Engine](https://github.com/Mattral/Composed-Mixture-of-Experts-Engine) | Sparse MoE training runtime with Triton-fused Top-K routing, DP+EP+TP parallelism, async two-tier checkpointing (NVMe → S3/MinIO), and TorchElastic fault recovery. Includes chaos testing and detailed telemetry. | Active<br>Pipeline parallelism and large-scale multi-node validation still in progress |
| [GuardRail Studio](https://github.com/Mattral/GuardRail-Studio) | Inline LLM firewall with measured sub-10 ms p99 latency in load tests. Built with ONNX + Triton, drift detection, LoRA self-updating, and full canary deployment automation. Five documented development phases. | Active<br>Latency numbers from controlled tests; full production hardware validation ongoing |
| [KANX](https://github.com/Mattral/KANX) | Production-grade Kolmogorov-Arnold Networks library with PyTorch + TensorFlow backends, real ONNX export, Docker + Kubernetes support, and FastAPI serving. Includes benchmarks on smooth separable tasks. | Active · `pip install kanx`<br>Paper preprint available |
| [RLHF-PPO-DPO](https://github.com/Mattral/Improving-LLM-Models-with-RLHF-PPO-DPO) | Modular framework for full RLHF pipelines (SFT → reward modeling → PPO and DPO). Includes distributed design with ZeRO-3, async rollouts, and extensive testing. | Active<br>Validated end-to-end on single-GPU toy setups; large-scale distributed runs not yet public |
| [FlashSpec](https://github.com/Mattral/FlashSpec) | Adaptive speculative decoding engine with online bandit draft selection and Triton-optimized verification. Includes throughput benchmarks on Llama-3 models. | Pre-alpha / Active development<br>Some CI and GPU tests currently under refactoring |
| [RAG-Multimodal-Financial-Doc-Analysis-and-Recall](https://github.com/Mattral/RAG-Multimodal-Financial-Doc-Analysis-and-Recall) | Enterprise multimodal RAG system for financial documents (text + tables + charts via GPT). Strong emphasis on async processing, retries, structured observability, and type safety. | Active<br>Finance-domain focused; detailed load benchmarks not yet public |

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

That said: the repositories here are written to the same standard I use privately: tests, type checking, CI, real (if limited) benchmarks, and documentation that tries to admit what doesn’t work yet. When something is experimental or incomplete, the README says so.

I’m especially interested in the kinds of failures that only appear at real cluster scale, the practical trade-offs in LLM safety systems, and whether architectures like KANs will eventually find meaningful production use cases.

My path into this work wasn’t linear. I spent time in data engineering and instrumentation before moving deeper into ML systems. That background still shapes how I think about reliability and observability.


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
